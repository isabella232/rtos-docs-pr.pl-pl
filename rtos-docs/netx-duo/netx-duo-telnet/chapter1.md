---
title: Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo Telnet
description: Azure RTO NetX Duo Telnet to protokół przeznaczony do przesyłania poleceń i odpowiedzi między dwoma węzłami w Internecie.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d25f5ca4a7bf1ecf4c3d0c68ef6c8aeda7800098
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821637"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-telnet"></a>Rozdział 1 — wprowadzenie do usługi Azure RTO NetX Duo Telnet

Azure RTO NetX Duo Telnet to protokół przeznaczony do przesyłania poleceń i odpowiedzi między dwoma węzłami w Internecie. Telnet to prosty protokół, który wykorzystuje niezawodne usługi Transmission Control Protocol (TCP) do wykonywania funkcji transferu. W związku z tym Telnet jest protokołem transferu o wysokim poziomie niezawodności. Telnet jest również jednym z najczęściej używanych protokołów aplikacji.

## <a name="telnet-requirements"></a>Wymagania dotyczące programu Telnet

Aby zapewnić prawidłowe działanie, pakiet Telnet NetX Duo wymaga, aby wystąpienie adresu IP NetX zostało już utworzone. Ponadto należy włączyć protokół TCP dla tego samego wystąpienia IP. Część klienta Telnet pakietu Telnet NetX Duo nie ma żadnych dalszych wymagań.

Część serwera Telnet pakietu Telnet NetX Duo ma jedno dodatkowe wymaganie. Wymaga pełnego dostępu do *dobrze znanego portu* TCP, aby obsłużyć wszystkie żądania klienta Telnet.

## <a name="telnet-constraints"></a>Ograniczenia programu Telnet 

Protokół Telnet NetX Duo implementuje Standard Telnet. Jednak interpretacja i odpowiedź poleceń Telnet, wskazywanych przez bajt o wartości 255, jest odpowiedzialna za aplikację. Różne polecenia i parametry polecenia programu Telnet są zdefiniowane w plikach *nxd_telnet_client. h i nxd_telnet_server. h* .

## <a name="telnet-communication"></a>Komunikacja Telnet

Jak wspomniano wcześniej, serwer Telnet używa *dobrze znanego portu TCP 23* do obsługi żądań klientów. Klienci Telnet mogą korzystać z dowolnego dostępnego portu TCP.

## <a name="telnet-authentication"></a>Uwierzytelnianie Telnet

Uwierzytelnianie za pomocą programu Telnet jest odpowiedzialne za funkcję wywołania zwrotnego serwera Telnet aplikacji. Wywołanie zwrotne "nowe połączenie" serwera Telnet aplikacji zwykle monituje klienta o podanie nazwy i/lub hasła. Klient będzie następnie odpowiedzialny za podanie informacji. Następnie serwer przetworzy informacje w wywołaniu zwrotnym "odbieranie danych". Jest to miejsce, w którym kod serwera aplikacji musi uwierzytelniać informacje i decydować, czy jest on prawidłowy.

## <a name="telnet-new-connection-callback"></a>Wywołanie zwrotne nowego połączenia Telnet

Serwer Telnet NetX Duo wywołuje funkcję wywołania zwrotnego aplikacji przy każdym odebraniu nowego żądania klienta programu Telnet. Aplikacja określa funkcję wywołania zwrotnego, gdy serwer Telnet jest tworzony za pomocą funkcji ***nx_telnet_server_create*** . Typowe działania wywołania zwrotnego "nowe połączenie" obejmują wysyłanie transparentu lub monitu do klienta. Może to bardzo dobrze obejmować monit o podanie informacji logowania.

### <a name="prototype"></a>Prototype

```c
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr**: wskaźnik do wywołującego serwera Telnet.
- **logical_connection**: wewnętrzne połączenie logiczne dla serwera Telnet. Ta aplikacja może być używana przez aplikację jako indeks do buforów i/lub struktur danych specyficznych dla każdego połączenia z klientem. Wartość z zakresu od 0 do NX_TELNET_MAX_CLIENTS-1.

## <a name="telnet-receive-data-callback"></a>Wywołanie zwrotne odbierania danych przez Telnet

Serwer Telnet NetX Duo wywołuje funkcję wywołania zwrotnego aplikacji za każdym razem, gdy zostanie odebrane nowe dane klienta programu Telnet. Aplikacja określa funkcję wywołania zwrotnego, gdy serwer Telnet jest tworzony za pomocą funkcji ***nx_telnet_server_create*** . Typowe działania wywołania zwrotnego "nowe połączenie" obejmują echo danych z powrotem i/lub analizowanie danych oraz dostarczanie danych w wyniku interpretacji polecenia z klienta.

Należy zauważyć, że ta procedura wywołania zwrotnego musi również zwolnić dostarczony pakiet.

### <a name="prototype"></a>Prototype

```c
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, 
                          UINT logical_connection, NX_PACKET *packet_ptr);
```
### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr**: wskaźnik do wywołującego serwera Telnet.
- **logical_connection**: wewnętrzne połączenie logiczne dla serwera Telnet. Ta aplikacja może być używana przez aplikację jako indeks do buforów i/lub struktur danych specyficznych dla każdego połączenia z klientem. Wartość z zakresu od 0 do NX_TELNET_MAX_CLIENTS-1.
- **packet_ptr**: wskaźnik do pakietu zawierającego dane z klienta.

## <a name="telnet-end-connection-callback"></a>Wywołanie zwrotne zakończenia połączenia Telnet

Serwer Telnet NetX Duo wywołuje funkcję wywołania zwrotnego aplikacji za każdym razem, gdy klient Telnet skończy połączenie. Aplikacja określa funkcję wywołania zwrotnego, gdy serwer Telnet jest tworzony za pomocą funkcji ***nx_telnet_server_create*** . Typowe działania wywołania zwrotnego "End Connection" obejmują czyszczenie wszystkich struktur danych specyficznych dla klienta skojarzonych z połączeniem logicznym.

### <a name="prototype"></a>Prototype
```c
void  telnet_end_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr** Wskaźnik na wywołujący serwer Telnet.
- **logical_connection** Wewnętrzne połączenie logiczne dla serwera Telnet. Ta aplikacja może być używana przez aplikację jako indeks do buforów i/lub struktur danych specyficznych dla każdego połączenia z klientem. Wartość z zakresu od 0 do NX_TELNET_MAX_CLIENTS-1.

## <a name="telnet-option-negotiation"></a>Negocjowanie opcji Telnet

Serwer Telnet NetX Duo obsługuje ograniczony zestaw opcji programu Telnet, echo i pomijanie.

Aby włączyć tę funkcję, NX_TELNET_SERVER_OPTION_DISABLE nie może być zdefiniowana. Domyślnie nie jest on zdefiniowany. Serwer Telnet tworzy pulę pakietów w usłudze *nx_telnet_server_create* , z której przydziela pakiety do wysyłania żądań opcji programu Telnet do klienta. Aby ustawić ładunek pakietów (NX_TELNET_SERVER_PACKET_PAYLOAD) i rozmiar puli pakietów (NX_TELNET_SERVER_PACKET_POOL_SIZE) dla tej puli pakietów, zobacz "Opcje konfiguracji". Ta Pula pakietów zostanie usunięta, gdy zostanie wywołana usługa *nx_telnet_server_delete* .

Po nawiązaniu połączenia z klientem Telnet wyśle ten zestaw opcji programu Telnet do klienta, jeśli nie otrzymał żądań opcji od klienta:

- będzie echo
- nie echo
- zostanie SGA

Gdy odbierze dane Telnet z klienta, serwer Telnet sprawdza, czy pierwszy bajt jest kodem "IAC". Jeśli tak, będzie przetwarzać wszystkie opcje w pakiecie klienta. Opcje, których nie ma na powyższej liście, są ignorowane.

Domyślnie serwer Telnet tworzy własną wewnętrzną pulę pakietów, jeśli NX_TELNET_SERVER_OPTION_DISABLE nie jest zdefiniowana i musi przesłać polecenia opcji Telnet. Pula pakietów serwera Telnet jest definiowana przez NX_TELNET_SERVER_PACKET_PAYLOAD i NX_TELNET_SERVER_PACKET_POOLSIZE. Jeśli jednak NX_TELNET_SERVER_USER_CREATE_PACKET_POOL jest zdefiniowany, aplikacja musi utworzyć pulę pakietów serwera Telnet i ustawić ją jako pulę pakietów serwera Telnet, wywołując *_nx_telnet_server_packet_pool_set*. Aby uzyskać więcej informacji na temat tej funkcji, zobacz rozdział 3 "Opis usług Telnet".

W przeciwieństwie do serwera Telnet NetX Duo, wątek zadania klienta Telnet NetX Duo nie wysyła automatycznie i nie odpowiada na odebrane opcje z serwera Telnet. Należy to zrobić przez aplikację kliencką Telnet.

## <a name="telnet-multi-thread-support"></a>Obsługa wielowątkowości w programie Telnet

Usługi klienta Telnet NetX Duo można wywołać z wielu wątków jednocześnie. Jednak żądania odczytu lub zapisu dla określonego wystąpienia klienta programu Telnet powinny być wykonywane w kolejności z tego samego wątku.

## <a name="telnet-rfcs"></a>Specyfikacje RFC programu Telnet

NetX Duo Telnet jest zgodny z RFC854 i pokrewnymi specyfikacjami RFC.
