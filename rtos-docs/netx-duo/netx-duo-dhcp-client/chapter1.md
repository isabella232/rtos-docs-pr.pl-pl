---
title: Rozdział 1 — Wprowadzenie do klienta DHCP Azure RTOS NetX Duo
description: W Azure RTOS DHCP NetX Duo adres IP aplikacji jest jednym z parametrów dostarczonych do wywołania *nx_ip_create* usługi.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 57a47e94701527096af24e1a4b49b3ecd704b3930f49549bbb97be2c716bcfe2
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790534"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-dhcp-client"></a>Rozdział 1 — Wprowadzenie do klienta DHCP Azure RTOS NetX Duo

W Azure RTOS DHCP NetX Duo adres IP aplikacji jest jednym z parametrów dostarczonych do wywołania *nx_ip_create* usługi. Podanie adresu IP nie stanowi problemu, jeśli adres IP jest znany aplikacji statycznie lub za pośrednictwem konfiguracji użytkownika. Istnieją jednak wystąpienia, w których aplikacja nie wie lub nie wie, jaki jest jej adres IP. W takich sytuacjach należy dostarczyć zerowy adres IP do funkcji *nx_ip_create, a* protokół klienta DHCP powinien być używany do dynamicznego uzyskiwania adresu IP.

## <a name="dynamic-ip-address-assignment"></a>Dynamiczne przypisywanie adresów IP

Podstawową usługą używaną do uzyskiwania dynamicznego adresu IP z sieci jest protokół rarp (Reverse Address Resolution Protocol). Ten protokół jest podobny do protokołu ARP, z tą różnicą, że jest przeznaczony do uzyskiwania adresu IP zamiast znajdowania adresu MAC dla innego węzła sieciowego. Komunikat RARP niskiego poziomu jest emitowany w sieci lokalnej i odpowiada serwer w sieci za odpowiadanie za pomocą odpowiedzi RARP, która zawiera dynamicznie przydzielany adres IP.

Mimo że protokół RARP zapewnia usługę dynamicznego przydzielania adresów IP, ma kilka wad. Najbardziej niedobór jest taki, że protokół RARP zapewnia tylko dynamiczną alokację adresu IP. W większości sytuacji, aby urządzenie prawidłowo uczestniczyło w sieci, konieczne jest więcej informacji. Oprócz adresu IP większość urządzeń potrzebuje maski sieci i adresu IP bramy. Może być również potrzebny adres IP serwera DNS i inne informacje o sieci. RaRP nie ma możliwości podania tych informacji.

## <a name="rarp-alternatives"></a>Alternatywy RARP

Aby wyeliminować braki rarp, badacze opracowali bardziej kompleksowy mechanizm przydzielania adresów IP o nazwie BOOTP (bootp). Ten protokół ma możliwość dynamicznego przydzielania adresu IP oraz podania dodatkowych ważnych informacji o sieci. Jednak bootp ma wadę jest zaprojektowane dla konfiguracji sieci statycznej. Nie zezwala na szybkie ani automatyczne przypisywanie adresów.

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

Protokół DHCP używa protokołu UDP do wysyłania żądań i odpowiedzi pól. Przed posiadaniem adresu IP komunikaty UDP z informacjami DHCP są wysyłane i odbierane przy użyciu adresu emisji IP 255.255.255.255.

## <a name="dhcp-client-state-machine"></a>Komputer stanu klienta DHCP

Klient DHCP jest implementowane jako maszyna stanu. Maszyna stanu jest przetwarzana przez wewnętrzny wątek DHCP, który jest tworzony *nx_dhcp_create* przetwarzania. Główne stany klienta DHCP są następujące:

- **NX_DHCP_STATE_BOOT** Zaczynając od poprzedniego adresu IP
- **NX_DHCP_STATE_INIT** Począwszy od żadnej poprzedniej wartości adresu IP
- **NX_DHCP_STATE_SELECTING** Oczekiwanie na odpowiedź z dowolnego serwera DHCP
- **NX_DHCP_STATE_REQUESTING** Zidentyfikowany serwer DHCP, wysłane żądanie adresu IP
- **NX_DHCP_STATE_BOUND** Ustanowiono dzierżawę adresu IP PROTOKOŁU DHCP
- **NX_DHCP_STATE_RENEWING** Upłynął czas odnowienia dzierżawy adresu IP PROTOKOŁU DHCP, zażądano odnowienia
- **NX_DHCP_STATE_REBINDING** Upłynął czas ponownego wiązania dzierżawy adresu IP PROTOKOŁU DHCP, żądanie odnowienia
- **NX_DHCP_STATE_FORCERENEW** Ustanowiona dzierżawa adresu IP PROTOKOŁU DHCP, wymuszanie odnawiania przez serwer (obecnie nie jest obsługiwane) lub przez aplikację wywołującą nx_dhcp_force_renew
- **NX_DHCP_STATE_ADDRESS_PROBING** Sondowanie adresu IP PROTOKOŁU DHCP, wysyłanie sondy ARP w celu wykrycia konfliktu adresów IP.

## <a name="dhcp-client-multiple-interface-support"></a>Obsługa wielu interfejsów klienta DHCP

Klient DHCP został wcześniej zaimplementowany do uruchamiania tylko na jednym interfejsie sieciowym. Domyślnym zachowaniem było (i nadal jest) uruchamianie klienta DHCP w interfejsie podstawowym. Wywołując *nx_dhcp_set_interface_index*, aplikacja może (i nadal może) uruchamiać protokół DHCP na pomocniczym interfejsie sieciowym zamiast w interfejsie podstawowym.

Teraz obsługuje ona protokół DHCP uruchomiony równolegle na wielu interfejsach. Aby **uzyskać szczegółowe informacje na** temat jednoczesnego uruchamiania klienta DHCP na więcej niż jednym interfejsie fizycznym, zobacz Klient DHCP na wielu interfejsach jednocześnie w rozdziale 2.

## <a name="dhcp-user-request"></a>Żądanie użytkownika DHCP

Gdy serwer DHCP udziela adresu IP, przetwarzanie klienta DHCP może żądać dodatkowych parametrów — po jednym naraz — przy użyciu *nx_dhcp_user_option_request* usługi.

## <a name="dhcp-client-socket-queue"></a>Kolejka gniazd klienta DHCP 

Klient DHCP automatycznie usuwa pakiety emisji z serwerów DHPC przeznaczonych dla innych klientów DHCP z kolejki odbierania gniazda podczas oczekiwania na odpowiedź serwera. W sieci zajętej nie można tego zrobić, co może spowodować porzucanie pakietów przeznaczonych dla klienta.

## <a name="dhcp-rfcs"></a>Dhcp RFC

Klient DHCP NetX Duo jest zgodny ze specyfikacjami RFC2132, RFC2131 i powiązanymi RFC.