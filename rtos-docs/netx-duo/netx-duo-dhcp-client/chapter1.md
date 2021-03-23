---
title: Rozdział 1 — wprowadzenie do klienta DHCP usługi Azure RTO NetX Duo
description: W przypadku klienta DHCP usługi Azure RTO NetX Duo adres IP aplikacji jest jednym z podanych parametrów wywołania usługi *nx_ip_create* .
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f5b2f2ef7b440e2f2ee8aa6a9bd6ed199eaf13fb
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822039"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-dhcp-client"></a>Rozdział 1 — wprowadzenie do klienta DHCP usługi Azure RTO NetX Duo

W przypadku klienta DHCP usługi Azure RTO NetX Duo adres IP aplikacji jest jednym z podanych parametrów wywołania usługi *nx_ip_create* . Dostarczenie adresu IP nie powoduje żadnych problemów, jeśli adres IP jest znany aplikacji, statycznie lub przez konfigurację użytkownika. Istnieją jednak pewne wystąpienia, w których aplikacja nie wie ani nie ponosi jego adresu IP. W takich sytuacjach do funkcji *nx_ip_create* należy dostarczyć zerowy adres IP, a protokół klienta DHCP powinien być używany do dynamicznego uzyskiwania adresu IP.

## <a name="dynamic-ip-address-assignment"></a>Dynamiczne przypisywanie adresów IP

Podstawowa usługa używana do uzyskiwania dynamicznego adresu IP z sieci to protokół odwrotnego rozpoznawania adresów (RARP). Ten protokół jest podobny do protokołu ARP, z tą różnicą, że został zaprojektowany w celu uzyskania adresu IP dla samego siebie zamiast wyszukiwania adresu MAC dla innego węzła sieci. Komunikat RARP niskiego poziomu jest emitowany w sieci lokalnej i jest odpowiedzialny za serwer w sieci, aby odpowiedzieć na odpowiedź z RARP, która zawiera dynamicznie przydzieloną adres IP.

Mimo że usługa RARP udostępnia usługę dynamicznego przydzielania adresów IP, ma kilka wad. Większość niedoborów odblasku polega na tym, że RARP zapewnia tylko dynamiczną alokację adresu IP. W większości sytuacji więcej informacji jest konieczna, aby urządzenie mogło prawidłowo uczestniczyć w sieci. Oprócz adresu IP większość urządzeń wymaga maski sieci i adresu IP bramy. Może być również wymagany adres IP serwera DNS i inne informacje o sieci. RARP nie ma możliwości podania tych informacji.

## <a name="rarp-alternatives"></a>RARP alternatywy

Aby sprostać brakom RARP, badacze opracowały bardziej kompleksowy mechanizm alokacji adresów IP o nazwie protokół paska rozruchowego (BOOTP). Ten protokół ma możliwość dynamicznego przydzielenia adresu IP, a także zapewnienia dodatkowych ważnych informacji o sieci. Jednak protokół BOOTP ma wady, które są przeznaczone do konfiguracji sieci statycznych. Nie zezwala na szybkie lub automatyczne przypisywanie adresów.

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

Protokół DHCP korzysta z protokołu UDP do wysyłania żądań i odpowiedzi pól. Przed przystąpieniem do adresu IP komunikaty UDP przenoszące informacje DHCP są wysyłane i odbierane przy użyciu adresu IP o wartości 255.255.255.255.

## <a name="dhcp-client-state-machine"></a>Komputer stanu klienta DHCP

Klient DHCP jest zaimplementowany jako komputer stanu. Komputer stanu jest przetwarzany przez wewnętrzny wątek DHCP, który jest tworzony podczas przetwarzania *nx_dhcp_create* . Główne Stany klienta DHCP są następujące:

- **NX_DHCP_STATE_BOOT** Począwszy od poprzedniego adresu IP
- **NX_DHCP_STATE_INIT** Rozpoczynając od braku poprzedniej wartości adresu IP
- **NX_DHCP_STATE_SELECTING** Oczekiwanie na odpowiedź z dowolnego serwera DHCP
- **NX_DHCP_STATE_REQUESTING** Zidentyfikowano serwer DHCP, wysłane żądanie adresu IP
- **NX_DHCP_STATE_BOUND** Ustanowiono dzierżawę adresu IP DHCP
- **NX_DHCP_STATE_RENEWING** Upłynął czas odnawiania dzierżawy adresu IP DHCP, żądanie odnowienia
- **NX_DHCP_STATE_REBINDING** Upłynął czas ponownego wiązania dzierżawy adresu IP DHCP, żądanie odnowienia
- **NX_DHCP_STATE_FORCERENEW** Ustanowiono dzierżawę adresu IP DHCP, Wymuś odnowienie przez serwer (obecnie nie jest to obsługiwane) lub przez aplikację wywołującą nx_dhcp_force_renew
- **NX_DHCP_STATE_ADDRESS_PROBING** Badanie adresu IP DHCP, Wyślij sondę ARP w celu wykrycia konfliktu adresów IP.

## <a name="dhcp-client-multiple-interface-support"></a>Obsługa wielu interfejsów klienta DHCP

Klient DHCP został wcześniej zaimplementowany do uruchomienia tylko na jednym interfejsie sieciowym. Zachowanie domyślne to (i nadal), aby klient DHCP był uruchamiany w interfejsie podstawowym. Wywołując *nx_dhcp_set_interface_index*, aplikacja może (i nadal może) uruchomić usługę DHCP na pomocniczym interfejsie sieciowym, a nie w interfejsie podstawowym.

Teraz obsługuje protokół DHCP działający w wielu interfejsach równolegle. Zobacz **klienta DHCP na wielu interfejsach jednocześnie** w rozdziale dwa, aby uzyskać szczegółowe informacje dotyczące sposobu uruchamiania klienta DHCP w więcej niż jednym interfejsie fizycznym.

## <a name="dhcp-user-request"></a>Żądanie użytkownika DHCP

Gdy serwer DHCP przydzieli adres IP, przetwarzanie klienta DHCP może żądać dodatkowych parametrów — pojedynczo — przy użyciu usługi *nx_dhcp_user_option_request* .

## <a name="dhcp-client-socket-queue"></a>Kolejka gniazda klienta DHCP 

Klient DHCP automatycznie czyści pakiety emisji z serwerów DHPC przeznaczonych dla innych klientów DHCP z kolejki odbioru gniazda podczas oczekiwania na odpowiedź serwera do samego siebie. W przypadku zajętej sieci nie może to spowodować porzucenia pakietów przeznaczonych dla klienta.

## <a name="dhcp-rfcs"></a>Specyfikacje RFC protokołu DHCP

Klient DHCP NetX Duo jest zgodny z RFC2132, RFC2131 i powiązanymi specyfikacjami RFC.