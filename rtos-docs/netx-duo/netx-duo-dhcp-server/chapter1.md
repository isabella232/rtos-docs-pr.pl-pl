---
title: Rozdział 1 — Wprowadzenie do serwera DHCP Azure RTOS NetX Duo
description: W aplikacji NetX Duo adres IP aplikacji jest jednym z parametrów dostarczonych do wywołania *nx_ip_create* usługi.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a56f692059cbd3e2a72d64cf80ee90a917b80987add8130d3a1df70b3b0c3a71
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788477"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcp-server"></a>Rozdział 1 — Wprowadzenie do serwera DHCP Azure RTOS NetX Duo

W aplikacji NetX Duo adres IP aplikacji jest jednym z parametrów dostarczonych do wywołania *nx_ip_create* usługi. Podanie adresu IP nie stanowi problemu, jeśli adres IP jest znany aplikacji statycznie lub za pośrednictwem konfiguracji użytkownika. Istnieją jednak wystąpienia, w których aplikacja nie wie lub nie wie, jaki jest jej adres IP. W takich sytuacjach do funkcji nx_ip_create powinien zostać podany zerowy adres *IP, a* aplikacja nawiązuje komunikację z serwerem DHCP w celu dynamicznego żądania i uzyskania adresu IP.

## <a name="dynamic-ip-address-assignment"></a>Dynamiczne przypisywanie adresów IP

Podstawową usługą używaną do uzyskiwania dynamicznego adresu IP z sieci jest protokół rarp (Reverse Address Resolution Protocol). Ten protokół jest podobny do protokołu ARP, z tą różnicą, że jest przeznaczony do uzyskiwania adresu IP zamiast znajdowania adresu MAC dla innego węzła sieciowego. Komunikat RARP niskiego poziomu jest emitowany w sieci lokalnej i odpowiada serwer w sieci za odpowiadanie za pomocą odpowiedzi RARP, która zawiera dynamicznie przydzielany adres IP.

Mimo że protokół RARP zapewnia usługę dynamicznego przydzielania adresów IP, ma kilka wad. Najbardziej niedobór jest taki, że protokół RARP zapewnia tylko dynamiczną alokację adresu IP. W większości sytuacji, aby urządzenie prawidłowo uczestniczyło w sieci, konieczne jest więcej informacji. Oprócz adresu IP większość urządzeń potrzebuje maski sieci i adresu IP bramy. Może być również potrzebny adres IP serwera DNS i inne informacje o sieci. RaRP nie ma możliwości podania tych informacji.

## <a name="rarp-alternatives"></a>Alternatywy RARP

Aby wyeliminować braki rarp, badacze opracowali bardziej kompleksowy mechanizm przydzielania adresów IP o nazwie Bootstrap Protocol (BOOTP). Ten protokół ma możliwość dynamicznego przydzielania adresu IP oraz podania dodatkowych ważnych informacji o sieci. Jednak bootp ma wadę jest zaprojektowane dla konfiguracji sieci statycznej. Nie zezwala na szybkie ani automatyczne przypisywanie adresów.

Jest to miejsce, w Dynamic Host Configuration Protocol (DHCP) jest bardzo przydatne. Protokół DHCP został zaprojektowany tak, aby rozszerzyć podstawową funkcjonalność bootp o całkowicie zautomatyzowaną alokację serwera IP i całkowicie dynamiczną alokację adresów IP przez "dzierżawienie" adresu IP klientowi na określony czas. Protokół DHCP można również skonfigurować do przydzielania adresów IP w sposób statyczny, taki jak BOOTP.

## <a name="dhcp-messages"></a>Komunikaty DHCP

Mimo że protokół DHCP znacznie zwiększa funkcjonalność bootp, DHCP używa tego samego formatu komunikatów jako BOOTP i obsługuje te same opcje dostawcy jako BOOTP. W celu wykonania tej funkcji protokół DHCP wprowadza siedem nowych opcji specyficznych dla protokołu DHCP w następujący sposób:

- ODNAJDYWANIE (1) (wysyłane przez klienta DHCP)
- OFFER (2) (wysyłane przez serwer DHCP)
- REQUEST (3) (wysyłane przez klienta DHCP)
- ODRZUĆ (4) (wysyłane przez klienta DHCP)
- ACK (5) (wysyłane przez serwer DHCP)
- NACK (6) (wysyłane przez serwer DHCP)
- RELEASE (7) (wysyłane przez klienta DHCP)
- INFORM (8) (wysyłane przez klienta DHCP)
- FORCERENEW (9) (wysyłane przez klienta DHCP)

## <a name="dhcp-communication"></a>Komunikacja DHCP

Serwer DHCP używa protokołu UDP do odbierania żądań klientów DHCP i przesyłania odpowiedzi. Przed posiadaniem adresu IP komunikaty UDP z informacjami DHCP są wysyłane i odbierane przy użyciu adresu emisji IP 255.255.255.255. Jeśli jednak klient zna adres serwera DHCP, może wysyłać komunikaty DHCP przy użyciu komunikatów emisji pojedynczej.

## <a name="dhcp-server-state-machine"></a>Komputer stanu serwera DHCP

Serwer DHCP jest implementowany jako dwuetapowa maszyna stanu przetwarzana przez wewnętrzny wątek DHCP, który jest tworzony *podczas nx_dhcp_server_create* przetwarzania. Główne stany serwera DHCP to 1) odbieranie komunikatu DISCOVER od klienta DHCP i 2) odbieranie komunikatu REQUEST.

Poniżej przedstawiono odpowiednie stany klienta DHCP:

- **NX_DHCP_STATE_BOOT** Zaczynając od poprzedniego adresu IP
- **NX_DHCP_STATE_INIT** Począwszy od żadnej poprzedniej wartości adresu IP
- **NX_DHCP_STATE_SELECTING** Oczekiwanie na odpowiedź z dowolnego serwera DHCP
- **NX_DHCP_STATE_REQUESTING** Zidentyfikowany serwer DHCP, wysłane żądanie adresu IP
- **NX_DHCP_STATE_BOUND** Ustanowiono dzierżawę adresu IP PROTOKOŁU DHCP
- **NX_DHCP_STATE_RENEWING** Upłynął czas odnowienia dzierżawy adresu IP PROTOKOŁU DHCP, zażądano odnowienia
- **NX_DHCP_STATE_REBINDING** Upłynął czas ponownego wiązania dzierżawy adresu IP PROTOKOŁU DHCP, żądanie odnowienia
- **NX_DHCP_STATE_FORCERENEW** Nawiązyliśmy dzierżawę adresu IP PROTOKOŁU DHCP, wymusz odnawianie według serwera lub aplikacji
- **NX_DHCP_STATE_FAILED** Nie znaleziono serwera lub nie odebrano odpowiedzi z serwera

## <a name="dhcp-additional-parameters"></a>Dodatkowe parametry DHCP

Serwer DHCP NetX Duo ma domyślną listę parametrów opcji, które są ustawiane w konfigurowalnej opcji NX_DHCP_DEFAULT_SERVER_OPTION_LIST w *programie nxd_dhcp_server.h,* aby dostarczać klientom DHCP typowe/krytyczne parametry konfiguracji sieci, np. adres routera lub bramy i serwer DNS dla klienta DHCP.

## <a name="dhcp-rfcs"></a>Dhcp RFC

Serwer DHCP NetX Duo jest zgodny ze specyfikacjami RFC2132, RFC2131 i powiązanymi RFC.
