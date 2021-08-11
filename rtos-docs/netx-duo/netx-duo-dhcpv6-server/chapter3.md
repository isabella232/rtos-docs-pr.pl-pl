---
title: Rozdział 3 — Azure RTOS konfiguracji serwera NetX Duo DHCPv6
description: Ten rozdział zawiera opis opcji konfiguracji Azure RTOS NetX Duo DHCPv6.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1dc0d6e41118a2f67fe98758f1f31f84d074d7af342b9db93162ffe6354077ea
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116792132"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-server-configuration-options"></a>Rozdział 3 — Azure RTOS konfiguracji serwera NetX Duo DHCPv6

Istnieje kilka opcji konfiguracji tworzenia aplikacji NetX Duo DHCPv6 Server. Na poniższej liście szczegółowo opisano poszczególne z nich:
  
- **NX_DISABLE_ERROR_CHECKING** Ta opcja usuwa sprawdzanie błędów protokołu DHCPv6. Jest ona zwykle włączona podczas debugowania aplikacji.  
  
- **NX_DHCPV6_SERVER_THREAD_STACK_SIZE** Określa rozmiar stosu wątków DHCPv6. Domyślnie rozmiar to 4096 bajtów, co jest więcej niż wystarczające dla większości aplikacji NetX Duo.

- **NX_DHCPV6_SERVER_THREAD_PRIORITY** Definiuje priorytet wątku DHCPv6Server. Ta powinna być niższa niż priorytet zadania wątku IP serwera DHCPv6. Wartość domyślna to 2.

- **NX_DHCPV6_IP_LEASE_TIMER_INTERVAL** Interwał czasomierza w sekundach, gdy funkcja wprowadzania czasomierza dzierżawy jest wywoływana przez harmonogram ThreadX. Funkcja entry ustawia flagę dla serwera DHCPv6 w celu inkrementowania czasu naliczania dzierżawy przez wszystkich klientów przez interwał czasomierza. Domyślnie ta wartość to 60.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL** Interwał czasomierza w sekundach, gdy funkcja wprowadzania czasomierza sesji jest wywoływana przez harmonogram ThreadX. Funkcja entry ustawia flagę dla serwera DHCPv6, aby zwiększyć cały czas aktywnej sesji klienta naliczany przez interwał czasomierza. Domyślnie ta wartość to 3.

Poniższe definicje dotyczą typu komunikatu opcji stanu i komunikatu konfigurowalnego przez użytkownika. Opcja stanu wskazuje wynik żądania klienta:

- **NX_DHCPV6_STATUS_MESSAGE_SUCCESS** *"UDZIELONO OPCJI IA"*

- **NX_DHCPV6_STATUS_NO_ADDRS_AVAILABLE** *"NIE UDZIELONO OPCJI IA — BRAK DOSTĘPNYCH ADRESÓW"*

- **NX_DHCPV6_STATUS_MESSAGE_NO_BINDING** *"NIE UDZIELONO OPCJI IA — NIEPRAWIDŁOWE ŻĄDANIE KLIENTA"*

- **NX_DHCPV6_STATUS_MESSAGE_NOT_ON_LINK** *"NIE UDZIELONO OPCJI IA-CLIENT NOT ON LINK"*

- **NX_DHCPV6_STATUS_MESSAGE_USE_MULTICAST** *"NIE UDZIELONO OPCJI IA KLIENT MUSI UŻYWAĆ MULTIEMISJI"*

- **NX_DHCPV6_STATUS_MESSAGE_NO_ADDRS_AVAILABLE** *IA NIE UDZIELONO ŻADNYCH ADRESÓW*

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID** Utwórz identyfikator DUID serwera z identyfikatorem przypisanym do dostawcy. Należy pamiętać, że typ DUID musi być NX_DHCPV6_DUID_TYPE_VENDOR_ASSIGNED.

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_LENGTH** Ustawia górny limit identyfikatora przypisanego dostawcy. Wartość domyślna to 48.

- **NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID** Ustawia typ przedsiębiorstwa DUID dostawcy prywatnego typu.

- **NX_DHCPV6_PACKET_WAIT_OPTION** Spowoduje to zdefiniowanie opcji oczekiwania dla wywołania *nx_udp_socket_receive* Serwera. Jest to funkcja perfunctory, ponieważ gniazdo ma wywołanie zwrotne powiadomienia o odbierania z netX Duo, więc pakiet jest już w kolejkach, gdy serwer DHCPv6 wywołuje funkcję receive. Wartość domyślna to 1 sekunda (1 * NX_IP_PERIODIC_RATE).

- **NX_DHCPV6_SERVER_DUID_TYPE** Definiuje typ DUID serwera, który serwer zawiera we wszystkich komunikatach do klientów. Wartość domyślna to warstwa połączenia plus czas (NX_DHCPV6_SERVER_DUID_TYPE_LINK_TIME).

- **NX_DHCPV6_SERVER_HW_TYPE** Definiuje typ sprzętu w warstwie łącza DUID i warstwy łącza oraz opcje czasu. Wartość domyślna to NX_DHCPV6_SERVER_HARDWARE_TYPE_ETHERNET.

- **NX_DHCPV6_PREFERENCE_VALUE** Definiuje wartość opcji preferencji z zakresu od 0 do 255, gdzie im wyższa wartość, tym wyższa wartość preferencji, w opcji DHCPv6 o tej samej nazwie. Informuje to klienta, jakie preferencje należy umieścić w ofercie tego serwera, gdzie wiele serwerów DHCPv6 są dostępne do przypisywania adresów IP. Wartość 255 powoduje, że klient wybierze ten serwer. Wartość zero oznacza, że klient może wybrać. Wartość domyślna to zero.

- **NX_DHCPV6_MAX_OPTION_REQUEST_OPTIONS** Określa maksymalną liczbę żądań opcji w żądaniu klienta, które można zapisać w rekordzie klienta. Wartość domyślna to 6.

- **NX_DHCPV6_DEFAULT_T1_TIME** Czas w sekundach przypisany przez serwer w dzierżawie adresu klienta dla czasu, w którym klient powinien rozpocząć odnawianie swojego adresu IP. Wartość domyślna to 2000 sekund.

- **NX_DHCPV6_DEFAULT_T2_TIME** Czas w sekundach przypisany przez serwer w dzierżawie adresu klienta dla, kiedy klient powinien zacząć ponownie powiązywał swój adres IP przy założeniu, że próba odnowienia nie powiodła się. Wartość domyślna to 3000 sekund.

- **NX_DHCPV6_DEFAULT_PREFERRED_TIME** Określa czas w sekundach przypisany przez serwer dla, gdy przypisana dzierżawa adresu IP klienta jest przestarzała. Wartość domyślna to 2 NX_DHCPV6_DEFAULT_T1_TIME.

- **NX_DHCPV6_DEFAULT_VALID_TIME** Definiuje to czas wygaśnięcia w sekundach przypisany przez serwer w przypisanej dzierżawie adresu IP klienta. Po upływie tego czasu adres IP klienta jest nieprawidłowy. Wartość domyślna to 2 NX_DHCPV6_DEFAULT_PREFERRED_TIME.

- **NX_DHCPV6_STATUS_MESSAGE_MAX** Definiuje maksymalny rozmiar komunikatu serwera w polu komunikatu opcji stanu . Wartość domyślna to 100 bajtów.

- **NX_DHCPV6_MAX_LEASES** Definiuje rozmiar tabeli dzierżawy adresów IP serwera (np. maksymalną liczbę adresów IPv6 dostępnych do dzierżawy, które mogą być przechowywane). Domyślnie ta wartość to 100.

- **NX_DHCPV6_MAX_CLIENTS** Definiuje rozmiar tabeli rekordów Klienta serwera (np. maksymalną liczbę klientów, którzy mogą być przechowywani). Ta wartość powinna być mniejsza lub równa wartości NX_DHCPV6_MAX_LEASES. Domyślnie ta wartość to 120.

- **NX_DHCPV6_PACKET_TIME_OUT** Definiuje opcję oczekiwania w taktach czasomierza dla serwera DHCPv6 oczekiwania na alokacje pakietów. Wartość domyślna to 3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND.

- **NX_DHCPV6_PACKET_RECEIVE_WAIT** Definiuje opcję oczekiwania w wywołaniach przydzielania pakietów w puli pakietów serwera. Wartość domyślna to (3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND) lub 3 sekundy.

- **NX_DHCPV6_PACKET_SIZE** To definiuje ładunek pakietu pakietów puli pakietów serwera. Wartość domyślna to 500 bajtów.

- **NX_DHCPV6_PACKET_POOL_SIZE** Definiuje rozmiar puli pakietów serwera dla pakietów przydzielanych przez serwer w celu wysyłania komunikatów DHCPv6. Wartość domyślna to (10 * NX_DHCPV6_PACKET_SIZE).

- **NX_DHCPV6_TYPE_OF_SERVICE** Definiuje typ usługi transmisji pakietów UDP. Domyślnie ta wartość jest NX_IP_NORMAL.

- **NX_DHCPV6_FRAGMENT_OPTION** Spowoduje to zdefiniowanie opcji fragmentacji gniazda serwera. Wartość domyślna to NX_DON T_FRAGMENT

- **NX_DHCPV6_TIME_TO_LIVE** Określa liczbę routerów DHCPv6 pakiety z serwera może "przeskoku" przed pakiety są odrzucane. Wartość domyślna to 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Określa liczbę pakietów do utrzymania w kolejce odbierania gniazda UDP serwera, zanim netX Duo odrzuci pakiety.