---
title: Rozdział 1 — Wprowadzenie do Azure RTOS DHCP NetX
description: Aplikacja nawiązuje komunikację ze swoim serwerem Azure RTOS DHCP NetX w celu dynamicznego żądania i uzyskiwania adresu IP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f7a286118caf9bca9876d40ecdd176a3f4cb711e9cba39325808bfb6c09c2644
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799561"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-dhcp-server"></a>Rozdział 1 — Wprowadzenie do Azure RTOS DHCP NetX

W programie NetX adres IP aplikacji jest jednym z parametrów dostarczonych do wywołania *nx_ip_create* usługi. Podanie adresu IP nie stanowi problemu, jeśli adres IP jest znany aplikacji statycznie lub za pośrednictwem konfiguracji użytkownika. Istnieją jednak wystąpienia, w których aplikacja nie wie lub nie wie, jaki jest jej adres IP. W takich sytuacjach do funkcji nx_ip_create powinien zostać podany zerowy adres *IP, a* aplikacja nawiązuje komunikację ze swoim serwerem DHCP netx Azure RTOS w celu dynamicznego żądania i uzyskania adresu IP.

## <a name="dynamic-ip-address-assignment"></a>Dynamiczne przypisywanie adresów IP

Podstawową usługą używaną do uzyskiwania dynamicznego adresu IP z sieci jest protokół RARP (Reverse Address Resolution Protocol). Ten protokół jest podobny do protokołu ARP, z tą różnicą, że jest przeznaczony do uzyskiwania adresu IP zamiast znajdowania adresu MAC dla innego węzła sieciowego. Komunikat RARP niskiego poziomu jest emitowany w sieci lokalnej i odpowiada serwer w sieci za odpowiadanie za pomocą odpowiedzi RARP, która zawiera dynamicznie przydzielany adres IP.

Mimo że protokół RARP zapewnia usługę dynamicznej alokacji adresów IP, ma kilka wad. Najbardziej niedobór na płycie jest taki, że protokół RARP zapewnia tylko dynamiczną alokację adresu IP. W większości przypadków do prawidłowego uczestnictwa urządzenia w sieci jest potrzebnych więcej informacji. Oprócz adresu IP większość urządzeń potrzebuje maski sieci i adresu IP bramy. Może być również potrzebny adres IP serwera DNS i inne informacje o sieci. RaRP nie ma możliwości podania tych informacji.

## <a name="rarp-alternatives"></a>Alternatywy RARP

Aby wyeliminować braki rarp, badacze opracowali bardziej kompleksowy mechanizm alokacji adresów IP o nazwie Bootstrap Protocol (BOOTP). Ten protokół umożliwia dynamiczne przydzielanie adresu IP, a także zapewnia dodatkowe ważne informacje o sieci. Jednak bootp ma wadę jest zaprojektowane dla konfiguracji sieci statycznej. Nie zezwala na szybkie ani automatyczne przypisywanie adresów.

Jest to miejsce, Dynamic Host Configuration Protocol (DHCP) jest bardzo przydatne. Protokół DHCP został zaprojektowany w celu rozszerzenia podstawowych funkcji bootp, aby obejmował całkowicie zautomatyzowaną alokację serwera IP i całkowicie dynamiczną alokację adresów IP przez "dzierżawienie" adresu IP klientowi na określony czas. Protokół DHCP można również skonfigurować do przydzielania adresów IP w sposób statyczny, taki jak BOOTP.

## <a name="dhcp-messages"></a>Komunikaty DHCP

Mimo że protokół DHCP znacznie zwiększa funkcjonalność rozruchu, DHCP używa tego samego formatu komunikatów co bootp i obsługuje takie same opcje dostawcy jak bootp. W celu wykonania tej funkcji protokół DHCP wprowadza siedem nowych opcji specyficznych dla protokołu DHCP w następujący sposób:

| Opcja     | Wartość | Origin                |
| ---------- | ----- | --------------------- |
| Odkryj   | (1)   | (wysyłane przez klienta DHCP) |
| Oferta      | (2)   | (wysyłane przez serwer DHCP) |
| Żądanie    | (3)   | (wysyłane przez klienta DHCP) |
| Spadek    | (4)   | (wysyłane przez klienta DHCP) |
| Ack        | (5)   | (wysyłane przez serwer DHCP) |
| Nack       | (6)   | (wysyłane przez serwer DHCP) |
| Wydania    | (7)   | (wysyłane przez klienta DHCP) |
| O wcześniejsze poinformowanie obiektu     | (8)   | (wysyłane przez klienta DHCP) |
| FORCERENEW | (9)   | (wysyłane przez klienta DHCP) |

## <a name="dhcp-communication"></a>Komunikacja DHCP

Serwer DHCP używa protokołu UDP do odbierania żądań klientów DHCP i przesyłania odpowiedzi. Przed posiadaniem adresu IP komunikaty UDP z informacjami DHCP są wysyłane i odbierane przy użyciu adresu emisji IP 255.255.255.255. Jeśli jednak klient zna adres serwera DHCP, może wysyłać komunikaty DHCP przy użyciu komunikatów emisji pojedynczej.

## <a name="dhcp-server-state-machine"></a>Komputer stanu serwera DHCP

Serwer DHCP jest implementowany jako dwuetapowy komputer stanu przetwarzany przez wewnętrzny wątek DHCP, który jest tworzony *nx_dhcp_server_create* przetwarzania. Główne stany serwera DHCP to 1) odebranie komunikatu DISCOVER od klienta DHCP i 2) odebranie komunikatu REQUEST.

Poniżej przedstawiono odpowiednie stany klienta DHCP:

- **NX_DHCP_STATE_BOOT:** począwszy od poprzedniego adresu IP
- **NX_DHCP_STATE_INIT:** począwszy od żadnej poprzedniej wartości adresu IP
- **NX_DHCP_STATE_SELECTING:** Oczekiwanie na odpowiedź z dowolnego serwera DHCP
- **NX_DHCP_STATE_REQUESTING:** serwer DHCP zidentyfikowany, wysłane żądanie adresu IP
- **NX_DHCP_STATE_BOUND:** ustanowiona dzierżawa adresu IP DHCP
- **NX_DHCP_STATE_RENEWING:** upłynął czas odnowienia dzierżawy adresu IP DHCP, zażądano odnowienia
- **NX_DHCP_STATE_REBINDING:** upłynął czas ponownego wiązania dzierżawy adresu IP DHCP, zażądano odnowienia
- **NX_DHCP_STATE_FORCERENEW:** ustanowiona dzierżawa adresu IP DHCP, wymusz odnawianie przez serwer lub przez aplikację
- **NX_DHCP_STATE_FAILED:** nie znaleziono serwera lub nie odebrano odpowiedzi z serwera

## <a name="dhcp-additional-parameters"></a>Dodatkowe parametry DHCP

Serwer DHCP NetX ma domyślną listę parametrów opcji, które są ustawiane w konfigurowalnej opcji NX_DHCP_DEFAULT_SERVER_OPTION_LISTin *nx_dhcp_server.h,* aby dostarczać klientom DHCP typowe/krytyczne parametry konfiguracji sieci, np. adres routera lub bramy i serwer DNS dla klienta DHCP.

## <a name="dhcp-rfcs"></a>RFC DHCP

Serwer DHCP NetX jest zgodny z RFC2132, RFC2131 i powiązanymi RFC.
