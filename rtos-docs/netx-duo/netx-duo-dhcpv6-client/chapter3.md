---
title: Rozdział 3 — opcje konfiguracji protokołu DHCPv6 w systemie Azure RTO NetX Duo
description: Istnieje kilka opcji konfiguracji do kompilowania protokołu DHCPv6 platformy Azure RTO NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e5396b1c04581b5f79d337462368c4718ba9bb16
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821991"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a>Rozdział 3 — opcje konfiguracji protokołu DHCPv6 w systemie Azure RTO NetX Duo

Istnieje kilka opcji konfiguracji do kompilowania protokołu DHCPv6 platformy Azure RTO NetX Duo. Poniższa lista zawiera szczegółowy opis:  
  
  
- **NX_DHCPV6_THREAD_PRIORITY** Priorytet wątku klienta. Domyślnie ta wartość określa, że wątek klienta działa o priorytecie 2.

- **NX_DHCPV6_MUTEX_WAIT** Opcja przekroczenia limitu czasu w celu uzyskania blokady na wyłączność dla klienta DHCPv6. Wartość domyślna to TX_WAIT_FOREVER.

- **NX_DHCPV6_TICKS_PER_SECOND** Stosunek taktów do sekund. Jest to zależne od procesora. Wartość domyślna to 100.

- **NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Przedział czasu (w sekundach), w którym czasomierz okresu istnienia IP aktualizuje czas, przez jaki bieżący adres IP został przypisany do klienta. Domyślnie ta wartość jest równa 1.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL**  Przedział czasu (w sekundach), po upływie którego czasomierz sesji aktualizuje czas sesji komunikacji klienta z serwerem. Domyślnie ta wartość jest równa 1.

- **NX_DHCPV6_MAX_IA_ADDRESS** Maksymalna liczba adresów (IA), które można dodać do rekordu klienta. Wartość domyślna to 1. 

- **NX_DHCPV6_NUM_DNS_SERVERS** Liczba serwerów DNS, które mają być przechowywane w rekordzie klienta. Wartość domyślna to 2.

- **NX_DHCPV6_NUM_TIME_SERVERS** Liczba serwerów czasu do zapisania w rekordzie klienta. Wartość domyślna to 1.

- **NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Rozmiar buforu w rekordzie klienta do przechowywania nazwy domeny sieciowej klienta. Wartość domyślna to 30.

- **NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Rozmiar buforu w rekordzie klienta, aby pomieścić strefę czasową klienta. Wartość domyślna to 10.

- **NX_DHCPV6_MAX_MESSAGE_SIZE** Rozmiar buforu w rekordzie klienta do przechowywania opcji komunikatu o stanie w odpowiedzi serwera. Wartość domyślna to 100 bajtów.

- **NX_DHCPV6_PACKET_TIME_OUT** Limit czasu w sekundach na przydzielenie pakietu z puli pakietów klienta. Wartość domyślna to 3 sekundy.

- **NX_DHCPV6_TYPE_OF_SERVICE** Definiuje typ usługi do transmisji pakietów UDP z gniazda klienta DHCPv6. Wartość domyślna to **NX_IP_NORMAL**.

- **NX_DHCPV6_TIME_TO_LIVE** Liczba przypadków, gdy pakiet klienta jest przesyłany przez router sieciowy przed odrzuconym pakietem. Wartość domyślna to 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Określa liczbę pakietów, które mają być przechowywane w kolejce odbierania w gnieździe UDP klienta zanim NetX Duo odrzuca pakiety. Wartość domyślna to 5.

## <a name="dhcpv6-message-transmission"></a>Transmisja komunikatów protokołu DHCPv6

Istnieje zestaw opcji klienta protokołu DHCPv6 do ustawiania parametrów w transmisji komunikatów DHCPv6. Są to: 

  - początkowy limit czasu

  - Maksymalne opóźnienie w pierwszej transmisji

  - maksymalny limit czasu retransmisji 

  - Maksymalna liczba ponownych transmisji 

  - Maksymalny czas oczekiwania na odpowiedź serwera

Te parametry mają zastosowanie do każdego z komunikatów klienta DHCPv6:

- NIECHCIAN

- ŻĄDAJĄC

- JĄ

- REBIND

- Usuwanie

- ZAPROSZENIE

- SPRAWDZENIA

- POINFORMOWAĆ

Poniżej znajduje się pełna lista tych konfigurowalnych opcji i ich domyślnych 

values:

```C
NX_DHCPV6_FIRST_SOL_MAX_DELAY                   (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_INIT_SOL_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_TIMEOUT        (120 *
                                                NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_SOL_RETRANSMISSION_COUNT          0
NX_DHCPV6_MAX_SOL_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_REQ_TRANSMISSION_TIMEOUT         (1 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_TIMEOUT        (30 * NX_DHCPV6_TICKS_PER_SECOND) 
NX_DHCPV6_MAX_REQ_RETRANSMISSION_COUNT          10
NX_DHCPV6_MAX_REQ_RETRANSMISSION_DURATION       0

NX_DHCPV6_INIT_RENEW_TRANSMISSION_TIMEOUT       (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_TIMEOUT      (600*   
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_RENEW_RETRANSMISSION_COUNT        0

NX_DHCPV6_INIT_REBIND_TRANSMISSION_TIMEOUT      (10*NX_DHCPV6_TICKS_PER_SECOND)     
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_TIMEOUT     (600*  
                                                NX_DHCPV6_TICKS_PER_SECOND)  
NX_DHCPV6_MAX_REBIND_RETRANSMISSION_COUNT       0 

NX_DHCPV6_INIT_RELEASE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_TIMEOUT    0 
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_RELEASE_RETRANSMISSION_DURATION   0

NX_DHCPV6_INIT_DECLINE_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_TIMEOUT    0
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_COUNT      5  
NX_DHCPV6_MAX_DECLINE_RETRANSMISSION_DURATION   0
NX_DHCPV6_FIRST_CONFIRM_MAX_DELAY               (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_CONFIRM_TRANSMISSION_TIMEOUT     (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_TIMEOUT    (4*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_COUNT      0  
NX_DHCPV6_MAX_CONFIRM_RETRANSMISSION_DURATION   10

NX_DHCPV6_FIRST_INFORM_MAX_DELAY                (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_INIT_INFORM_TRANSMISSION_TIMEOUT      (1*NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_TIMEOUT     (120*   
                                                NX_DHCPV6_TICKS_PER_SECOND)
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_COUNT       0 
NX_DHCPV6_MAX_INFORM_RETRANSMISSION_DURATION    0
```

Aby nie ograniczyć limitu czasu ponownej transmisji, należy ustawić liczbę ponownych transmisji komunikatów na 0. W przypadku braku limitu liczby ponownych prób wysłania komunikatu klienta protokołu DHCPv6 (ponawianie), ustaw liczbę retransmisji wiadomości na 0.

> [!NOTE]
> Bez względu na długość limitu czasu lub liczbę ponownych prób w przypadku wygaśnięcia prawidłowego okresu istnienia adresu IPv6 jest on usuwany z tabeli adresów IP i nie może być już używany przez klienta. Klient DHCPv6 NetX Duo rozpocznie automatyczne wysyłanie komunikatów żądania, które żądają nowego adresu IPv6.