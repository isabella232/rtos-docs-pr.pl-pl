---
title: Rozdział 1 — wprowadzenie do serwera DHCP usługi Azure RTO NetX Duo
description: W NetX Duo adres IP aplikacji jest jednym z podanych parametrów wywołania usługi *nx_ip_create* .
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 678b9ed77f07d0b526525c740f0fae7adc6d2c95
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822020"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcp-server"></a>Rozdział 1 — wprowadzenie do serwera DHCP usługi Azure RTO NetX Duo

W NetX Duo adres IP aplikacji jest jednym z podanych parametrów wywołania usługi *nx_ip_create* . Dostarczenie adresu IP nie powoduje żadnych problemów, jeśli adres IP jest znany aplikacji, statycznie lub przez konfigurację użytkownika. Istnieją jednak pewne wystąpienia, w których aplikacja nie wie ani nie ponosi jego adresu IP. W takich sytuacjach do funkcji *nx_ip_create* należy dostarczyć zerowy adres IP, a aplikacja nawiązuje komunikację ze swoim serwerem DHCP w celu dynamicznego żądania i uzyskiwania adresu IP.

## <a name="dynamic-ip-address-assignment"></a>Dynamiczne przypisywanie adresów IP

Podstawowa usługa używana do uzyskiwania dynamicznego adresu IP z sieci to protokół odwrotnego rozpoznawania adresów (RARP). Ten protokół jest podobny do protokołu ARP, z tą różnicą, że został zaprojektowany w celu uzyskania adresu IP dla samego siebie zamiast wyszukiwania adresu MAC dla innego węzła sieci. Komunikat RARP niskiego poziomu jest emitowany w sieci lokalnej i jest odpowiedzialny za serwer w sieci, aby odpowiedzieć na odpowiedź z RARP, która zawiera dynamicznie przydzieloną adres IP.

Mimo że usługa RARP udostępnia usługę dynamicznego przydzielania adresów IP, ma kilka wad. Większość niedoborów odblasku polega na tym, że RARP zapewnia tylko dynamiczną alokację adresu IP. W większości sytuacji więcej informacji jest konieczna, aby urządzenie mogło prawidłowo uczestniczyć w sieci. Oprócz adresu IP większość urządzeń wymaga maski sieci i adresu IP bramy. Może być również wymagany adres IP serwera DNS i inne informacje o sieci. RARP nie ma możliwości podania tych informacji.

## <a name="rarp-alternatives"></a>RARP alternatywy

W celu pokonania wad RARP pracownicy opracowanli bardziej kompleksowy mechanizm alokacji adresów IP o nazwie protokół Bootstrap (BOOTP). Ten protokół ma możliwość dynamicznego przydzielenia adresu IP, a także zapewnienia dodatkowych ważnych informacji o sieci. Jednak protokół BOOTP ma wady, które są przeznaczone do konfiguracji sieci statycznych. Nie zezwala na szybkie lub automatyczne przypisywanie adresów.

Jest to miejsce, w którym Dynamic Host Configuration Protocol (DHCP) jest niezwykle przydatna. Usługa DHCP została zaprojektowana w celu rozbudowania podstawowych funkcji protokołu BOOTP w taki sposób, aby obejmowały całkowicie zautomatyzowaną alokację serwera IP i całkowicie dynamiczną alokację adresów IP za pomocą "dzierżawy" adresu IP do klienta przez określony czas. Protokół DHCP można również skonfigurować tak, aby przydzielał adresy IP w sposób statyczny, jak w przypadku protokołu BOOTP.

## <a name="dhcp-messages"></a>Komunikaty DHCP

Mimo że usługa DHCP znacznie rozszerza funkcjonalność protokołu BOOTP, protokół DHCP używa tego samego formatu komunikatów co BOOTP i obsługuje te same opcje dostawcy co protokół BOOTP. Aby można było wykonać swoją funkcję, usługa DHCP wprowadza siedem nowych opcji specyficznych dla protokołu DHCP w następujący sposób:

- ODNAJDYWAnie (1) (wysyłane przez klienta DHCP)
- Oferta (2) (wysłana przez serwer DHCP)
- ŻĄDANIE (3) (wysyłane przez klienta DHCP)
- Odrzuć (4) (Wysłany przez klienta DHCP)
- ACK (5) (wysyłany przez serwer DHCP)
- NACK (6) (wysyłanych przez serwer DHCP)
- WYDANIE (7) (wysyłane przez klienta DHCP)
- Informowanie (8) (wysyłane przez klienta DHCP)
- FORCERENEW (9) (wysyłane przez klienta DHCP)

## <a name="dhcp-communication"></a>Komunikacja DHCP

Serwer DHCP korzysta z protokołu UDP do odbierania żądań klientów DHCP i przesyłania odpowiedzi. Przed przystąpieniem do adresu IP komunikaty UDP przenoszące informacje DHCP są wysyłane i odbierane przy użyciu adresu IP o wartości 255.255.255.255. Jeśli jednak klient zna adres serwera DHCP, może wysyłać komunikaty protokołu DHCP przy użyciu komunikatów emisji pojedynczej.

## <a name="dhcp-server-state-machine"></a>Komputer stanu serwera DHCP

Serwer DHCP jest zaimplementowany jako wieloetapowy komputer stanu przetworzony przez wewnętrzny wątek DHCP, który jest tworzony podczas przetwarzania *nx_dhcp_server_create* . Główne Stany serwera DHCP to 1) otrzymywanie komunikatu ODNAJDOWAnia od klienta DHCP i 2) otrzymującego komunikat żądania.

Poniżej znajdują się odpowiednie Stany klienta DHCP:

- **NX_DHCP_STATE_BOOT** Począwszy od poprzedniego adresu IP
- **NX_DHCP_STATE_INIT** Rozpoczynając od braku poprzedniej wartości adresu IP
- **NX_DHCP_STATE_SELECTING** Oczekiwanie na odpowiedź z dowolnego serwera DHCP
- **NX_DHCP_STATE_REQUESTING** Zidentyfikowano serwer DHCP, wysłane żądanie adresu IP
- **NX_DHCP_STATE_BOUND** Ustanowiono dzierżawę adresu IP DHCP
- **NX_DHCP_STATE_RENEWING** Upłynął czas odnawiania dzierżawy adresu IP DHCP, żądanie odnowienia
- **NX_DHCP_STATE_REBINDING** Upłynął czas ponownego wiązania dzierżawy adresu IP DHCP, żądanie odnowienia
- **NX_DHCP_STATE_FORCERENEW** Ustanowiono dzierżawę adresu IP DHCP, Wymuś odnowienie przez serwer lub aplikację
- **NX_DHCP_STATE_FAILED** Nie znaleziono żadnego serwera lub nie odebrano odpowiedzi z serwera

## <a name="dhcp-additional-parameters"></a>Dodatkowe parametry protokołu DHCP

Serwer DHCP z systemem NetX Duo ma domyślną listę parametrów opcji ustawionych w opcji konfigurowalne NX_DHCP_DEFAULT_SERVER_OPTION_LIST w *nxd_dhcp_server. h* , aby udostępnić klientom DHCP typowe/krytyczne parametry konfiguracji sieci, np. router lub adres bramy oraz serwer DNS dla klienta DHCP.

## <a name="dhcp-rfcs"></a>Specyfikacje RFC protokołu DHCP

Serwer DHCP NetX Duo jest zgodny z RFC2132, RFC2131 i powiązanymi specyfikacjami RFC.
