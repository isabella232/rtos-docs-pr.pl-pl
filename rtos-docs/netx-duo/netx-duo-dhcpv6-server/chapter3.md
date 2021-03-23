---
title: Rozdział 3 — opcje konfiguracji serwera DHCPv6 w systemie Azure RTO NetX Duo
description: Ten rozdział zawiera opis opcji konfiguracji serwera DHCPv6 usługi Azure RTO NetX Duo.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 30f6e1c657eb62ebec48d6bb8caafac320727146
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822908"
---
# <a name="chapter-3---azure-rtos-netx-duo-dhcpv6-server-configuration-options"></a>Rozdział 3 — opcje konfiguracji serwera DHCPv6 w systemie Azure RTO NetX Duo

Istnieje kilka opcji konfiguracji do kompilowania aplikacji serwera DHCPv6 NetX Duo. Poniższa lista zawiera szczegółowy opis:
  
- **NX_DISABLE_ERROR_CHECKING** Ta opcja usuwa sprawdzanie błędów DHCPv6. Jest ona zazwyczaj włączona, gdy aplikacja jest debugowana.  
  
- **NX_DHCPV6_SERVER_THREAD_STACK_SIZE** Definiuje rozmiar stosu wątków protokołu DHCPv6. Domyślnie rozmiarem jest 4096 bajtów, co jest większe niż wystarczające dla większości aplikacji NetX Duo.

- **NX_DHCPV6_SERVER_THREAD_PRIORITY** Definiuje priorytet wątku DHCPv6Server. Ta wartość powinna być niższa niż priorytet zadania wątku IP serwera DHCPv6. Wartość domyślna to 2.

- **NX_DHCPV6_IP_LEASE_TIMER_INTERVAL** Interwał czasomierza w sekundach, gdy funkcja wpisu czasomierza dzierżawy jest wywoływana przez harmonogram ThreadX. Funkcja entry ustawia flagę dla serwera DHCPv6, aby zwiększyć czas narastania wszystkich klientów w dzierżawie przez interwał czasomierza. Wartość domyślna to 60.

- **NX_DHCPV6_SESSION_TIMER_INTERVAL** Interwał czasomierza w sekundach, gdy funkcja wejścia czasomierza sesji jest wywoływana przez harmonogram ThreadX. Funkcja entry ustawia flagę dla serwera DHCPv6, aby zwiększyć cały aktywny czas sesji klienta naliczany przez interwał czasomierza. Domyślnie ta wartość to 3.

Następujące definicje mają zastosowanie do typu komunikatu opcja stanu i komunikat konfigurowalny przez użytkownika. Opcja stan wskazuje wynik żądania klienta:

- **NX_DHCPV6_STATUS_MESSAGE_SUCCESS** *"przyznanych opcji" IA "*

- **NX_DHCPV6_STATUS_NO_ADDRS_AVAILABLE** *"nie udzielono opcji" IA — Brak dostępnych adresów "*

- **NX_DHCPV6_STATUS_MESSAGE_NO_BINDING** *"nie udzielono opcji" IA-Nieprawidłowe żądanie klienta "*

- **NX_DHCPV6_STATUS_MESSAGE_NOT_ON_LINK** *"nie udzielono opcji" IA-klient nie jest połączony "*

- **NX_DHCPV6_STATUS_MESSAGE_USE_MULTICAST** *"nie udzielono opcji" IA-klient musi używać multiemisji "*

- Opcja **NX_DHCPV6_STATUS_MESSAGE_NO_ADDRS_AVAILABLE** *IA nie została udzielona — Brak dostępnych adresów*

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID** Utwórz serwer identyfikatora DUID z przypisanym IDENTYFIKATORem dostawcy. Uwaga Typ identyfikatora DUID musi być ustawiony NX_DHCPV6_DUID_TYPE_VENDOR_ASSIGNED.

- **NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_LENGTH** Ustawia górny limit identyfikatora przypisanego przez dostawcę. Wartość domyślna to 48.

- **NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID** Ustawia typ przedsiębiorstwa dla identyfikatora DUID na typ dostawcy prywatnego.

- **NX_DHCPV6_PACKET_WAIT_OPTION** Definiuje opcję oczekiwania dla wywołania *Nx_udp_socket_receive* serwera. Jest to perfunctory, ponieważ gniazdo ma powiadomienie o wywołaniu zwrotnym z NetX Duo, więc pakiet jest już w kolejce, gdy serwer DHCPv6 wywoła funkcję Receive. Wartość domyślna to 1 sekunda (1 * NX_IP_PERIODIC_RATE).

- **NX_DHCPV6_SERVER_DUID_TYPE** Definiuje typ identyfikatora DUID serwera, który serwer zawiera we wszystkich komunikatach do klientów. Wartością domyślną jest warstwa łącza i czas (NX_DHCPV6_SERVER_DUID_TYPE_LINK_TIME).

- **NX_DHCPV6_SERVER_HW_TYPE** Definiuje typ sprzętu w warstwie łącza identyfikatora DUID i warstwy łącza oraz opcje czasu. Wartość domyślna to NX_DHCPV6_SERVER_HARDWARE_TYPE_ETHERNET.

- **NX_DHCPV6_PREFERENCE_VALUE** Definiuje wartość opcji preferencji z przedziału od 0 do 255, gdzie wyższa wartość jest wyższa od preferencji, w opcji DHCPv6 o tej samej nazwie. Oznacza to, że preferencja powinna zostać umieszczona na tym serwerze, gdzie wiele serwerów DHCPv6 jest dostępnych do przypisywania adresów IP. Wartość 255 powoduje, że klient wybierze ten serwer. Wartość zero oznacza, że klient jest bezpłatny do wyboru. Wartość domyślna to zero.

- **NX_DHCPV6_MAX_OPTION_REQUEST_OPTIONS** Definiuje ona maksymalną liczbę żądań opcji w żądaniu klienta, które można zapisać do rekordu klienta. Wartość domyślna to 6.

- **NX_DHCPV6_DEFAULT_T1_TIME** Czas (w sekundach) przypisany przez serwer w dzierżawie adresu klienta dla, gdy klient powinien rozpocząć odnawianie jego adresu IP. Wartość domyślna to 2000 sekund.

- **NX_DHCPV6_DEFAULT_T2_TIME** Czas (w sekundach) przypisany przez serwer w dzierżawie adresu klienta dla, gdy klient powinien zacząć ponownie powiązać swój adres IP przy założeniu, że próba odnowienia nie powiodła się. Wartość domyślna to 3000 sekund.

- **NX_DHCPV6_DEFAULT_PREFERRED_TIME** Definiuje czas (w sekundach) przypisany do serwera bythe, gdy dzierżawa przypisanego adresu IP klienta jest przestarzała. Wartość domyślna to 2 NX_DHCPV6_DEFAULT_T1_TIME.

- **NX_DHCPV6_DEFAULT_VALID_TIME** Definiuje czas wygaśnięcia (w sekundach) przypisany przez serwer w dzierżawie przypisanego adresu IP klienta. Po upływie tego czasu adres IP klienta jest nieprawidłowy. Wartość domyślna to 2 NX_DHCPV6_DEFAULT_PREFERRED_TIME.

- **NX_DHCPV6_STATUS_MESSAGE_MAX** Określa maksymalny rozmiar komunikatu serwera w polu komunikat o stanie. Wartość domyślna to 100 bajtów.

- **NX_DHCPV6_MAX_LEASES** Określa rozmiar tabeli dzierżaw IP serwera (np. Maksymalna liczba adresów IPv6 dostępnych dla dzierżawy, które mogą być przechowywane). Wartość domyślna to 100.

- **NX_DHCPV6_MAX_CLIENTS** Określa rozmiar tabeli rekordów klientów serwera (np. Maksymalna liczba klientów, które mogą być przechowywane). Ta wartość powinna być mniejsza lub równa wartości NX_DHCPV6_MAX_LEASES. Wartość domyślna to 120.

- **NX_DHCPV6_PACKET_TIME_OUT** Definiuje opcję oczekiwania w taktach czasomierza dla serwera DHCPv6 Zaczekaj na alokacje pakietów. Wartość domyślna to 3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND.

- **NX_DHCPV6_PACKET_RECEIVE_WAIT** Definiuje opcję oczekiwania w wywołaniach alokacji pakietów w puli pakietów serwera. Wartość domyślna to (3 * NX_DHCPV6_SERVER_TICKS_PER_SECOND) lub 3 s.

- **NX_DHCPV6_PACKET_SIZE** Definiuje ładunek pakietu pakietów puli pakietów serwera. Wartość domyślna to 500 bajtów.

- **NX_DHCPV6_PACKET_POOL_SIZE** Określa rozmiar puli pakietów serwera dla pakietów przydzielanych przez serwer do wysyłania komunikatów DHCPv6. Wartość domyślna to (10 * NX_DHCPV6_PACKET_SIZE).

- **NX_DHCPV6_TYPE_OF_SERVICE** Definiuje typ usługi do transmisji pakietów UDP. Domyślnie ta wartość jest NX_IP_NORMAL.

- **NX_DHCPV6_FRAGMENT_OPTION** Definiuje opcję fragmentacji gniazda serwera. Wartość domyślna to NX_DON "T_FRAGMENT

- **NX_DHCPV6_TIME_TO_LIVE** Określa liczbę routerów, które pakiety DHCPv6 z serwera mogą być przekazywane przed odrzuceniem pakietów. Wartość domyślna to 0x80.

- **NX_DHCPV6_QUEUE_DEPTH** Określa liczbę pakietów, które mają być przechowywane w kolejce odbierania w gnieździe UDP serwera zanim NetX Duo odrzuca pakiety.