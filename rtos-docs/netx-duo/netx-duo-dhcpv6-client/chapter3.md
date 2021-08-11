---
title: Rozdział 3 — Azure RTOS konfiguracji NetX Duo DHCPv6
description: Istnieje kilka opcji konfiguracji budowania Azure RTOS NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 129d1421215452448b1de4626fdeda530a5466bd63ed0c758676c3ad60f9d6fb
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782425"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-configuration-options"></a>Rozdział 3 — Azure RTOS konfiguracji NetX Duo DHCPv6

Istnieje kilka opcji konfiguracji budowania Azure RTOS NetX Duo DHCPv6. Na poniższej liście szczegółowo opisano poszczególne z nich:  
  
  
- **NX_DHCPV6_THREAD_PRIORITY** Priorytet wątku klienta. Domyślnie ta wartość określa, że wątek klienta jest uruchamiany z priorytetem 2.

- **NX_DHCPV6_MUTEX_WAIT** Opcja przechyłek czasu uzyskania blokady na wyłączność na mutex klienta DHCPv6. Wartość domyślna to TX_WAIT_FOREVER.

- **NX_DHCPV6_TICKS_PER_SECOND** Stosunek takt do sekund. Jest to zależne od procesora. Wartość domyślna to 100.

- **NX_DHCPV6_IP_LIFETIME_TIMER_INTERVAL**  Interwał czasu w sekundach, w którym czasomierz okresu istnienia adresu IP aktualizuje czas przypisania bieżącego adresu IP do klienta. Domyślnie ta wartość to 1.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL**  Interwał czasu w sekundach, w którym czasomierz sesji aktualizuje czas, przez jaki klient komunikuje się z serwerem. Domyślnie ta wartość to 1.

- **NX_DHCPV6_MAX_IA_ADDRESS** Maksymalna liczba adresów IA, które można dodać do rekordu Klienta. Wartość domyślna to 1. 

- **NX_DHCPV6_NUM_DNS_SERVERS** Liczba serwerów DNS do przechowywania w rekordzie klienta. Wartość domyślna to 2.

- **NX_DHCPV6_NUM_TIME_SERVERS** Liczba serwerów czasu, które mają być przechowywane w rekordzie klienta. Wartość domyślna to 1.

- **NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE**  Rozmiar buforu w rekordzie Klient do przechowywania nazwy domeny sieciowej klienta. Wartość domyślna to 30.

- **NX_DHCPV6_TIME_ZONE_BUFFER_SIZE**  Rozmiar buforu w rekordzie Klienta do przechowywania strefy czasowej klienta. Wartość domyślna to 10.

- **NX_DHCPV6_MAX_MESSAGE_SIZE** Rozmiar buforu w rekordzie klienta do przechowywania komunikatu o stanie opcji w odpowiedzi serwera. Wartość domyślna to 100 bajtów.

- **NX_DHCPV6_PACKET_TIME_OUT** W sekundach utracą czas przydzielania pakietu z puli pakietów klienta. Wartość domyślna to 3 sekundy.

- **NX_DHCPV6_TYPE_OF_SERVICE** Definiuje typ usługi transmisji pakietów UDP z gniazda klienta DHCPv6. Wartość domyślna to **NX_IP_NORMAL**.

- **NX_DHCPV6_TIME_TO_LIVE** Ile razy pakiet klienta jest przesyłany dalej przez router sieciowy, zanim pakiet zostanie odrzucony. Wartość domyślna to 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Określa liczbę pakietów do utrzymania w kolejce odbierania gniazda UDP klienta, zanim netX Duo odrzuci pakiety. Wartość domyślna to 5.

## <a name="dhcpv6-message-transmission"></a>Transmisja komunikatów DHCPv6

Istnieje zestaw opcji klienta DHCPv6 do ustawiania parametrów transmisji komunikatów DHCPv6. Są to: 

  - początkowy limit czasu

  - maksymalne opóźnienie przy pierwszej transmisji

  - maksymalny limit czasu retransmisji 

  - maksymalna liczba retransmisji 

  - maksymalny czas oczekiwania na odpowiedź serwera

Te parametry mają zastosowanie do każdego z komunikatów klienta DHCPv6:

- Uzyskania

- Żądanie

- Odnowić

- REBIND

- Wydania

- Spadek

- Potwierdzić

- O wcześniejsze poinformowanie obiektu

Poniżej znajduje się pełna lista tych konfigurowalnych opcji i ich domyślnych ustawień 

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

Aby nie ograniczyć limitu czasu ponownej transmisji, ustaw liczbę retransmisji komunikatu na 0. Aby nie ograniczyć liczby ponownego przesłania komunikatu klienta DHCPv6 (ponownych prób), ustaw liczbę ponownych transmisji komunikatów na 0.

> [!NOTE]
> Niezależnie od limitu czasu lub liczby ponownych prób, po wygaśnięciu prawidłowego okresu istnienia adresu IPv6 jest on usuwany z tabeli adresów IP i nie może być już używany przez klienta. Klient NetX Duo DHCPv6 automatycznie rozpocznie wysyłanie komunikatów SOLICIT żądających nowego adresu IPv6.