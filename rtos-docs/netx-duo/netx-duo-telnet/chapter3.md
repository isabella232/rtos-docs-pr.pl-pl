---
title: Rozdział 3 — Opis usług Telnet usługi Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług Telnet usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821618"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a>Rozdział 3 — Opis usług Telnet usługi Azure RTO NetX Duo

Ten rozdział zawiera opis wszystkich usług Telnet usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nx_telnet_client_connect**: *łączenie klienta Telnet z adresem IPv4*
- **nxd_telnet_client_connect**: *łączenie klienta Telnet IPv6 z adresem IPv6*
- **nx_telnet_client_create**: *Tworzenie klienta Telnet*
- **nx_telnet_client_delete**: *Usuwanie klienta Telnet*
- **nx_telnet_client_disconnect**: *Rozłączanie klienta Telnet*
- **nx_telnet_client_packet_receive**: *otrzymywanie pakietu za pośrednictwem klienta Telnet*
- **nx_telnet_client_packet_send**: *Wyślij pakiet za pośrednictwem klienta Telnet*
- **nx_telnet_server_create**: *Tworzenie serwera Telnet*
- **nx_telnet_server_delete**: *usuwanie serwera Telnet*
- **nx_telnet_server_disconnect**: *Rozłączanie klienta Telnet*
- **nx_telnet_server_get_open_connection_count**: *pobieranie liczby otwartych połączeń*
- **nx_telnet_server_packet_send**: *Wyślij pakiet przez połączenie klienta*
- **nx_telnet_server_packet_pool_set**: *Ustaw pulę pakietów jako pulę pakietów serwera Telnet*
- **nx_telnet_server_start**: *Uruchamianie serwera Telnet*
- **nx_telnet_server_stop**: *zatrzymywanie serwera Telnet*

## <a name="nx_telnet_client_connect"></a>nx_telnet_client_connect

Łączenie klienta Telnet z adresem IPv4

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje połączyć wcześniej utworzone wystąpienie klienta programu Telnet z serwerem w określonym adresie IP i porcie przy użyciu adresu IPv4 serwera Telnet. Ta usługa w rzeczywistości wstawia adres IP serwera ULONG w bloku sterowania NXD_ADDRESS i ustawia wersję protokołu IP na 4 przed wywołaniem usługi *nxd_telnet_client_connect* opisanej poniżej.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do bloku kontroli klienta Telnet.
- **server_IP**: adres IPv4 serwera Telnet.
- **SERVER_PORT**: port TCP serwera (serwer Telnet jest portem 23).
- **WAIT_OPTION**: określa, jak długo usługa będzie czekać na połączenie klienta Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:

    - **wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnego nawiązania połączenia z klientem.
- **NX_TELNET_NOT_DISCONNECTED**: (0XF4) klient jest już połączony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.
- NX_IP_ADDRESS_ERROR: (0x21) nieprawidłowy adres IP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a>nxd_telnet_client_connect

Łączenie klienta Telnet z adresem IPv6 lub IPv4

### <a name="prototype"></a>Prototype

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje połączyć wcześniej utworzone wystąpienie klienta programu Telnet z serwerem w określonym adresie IP i porcie przy użyciu adresu IPv6 serwera Telnet. Ta usługa może przyjmować adres IPv4 lub IPv6, ale musi być zawarta w server_ip_address zmiennej NXD_ADDRESS *.*

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do bloku kontroli klienta Telnet.
- **server_ip_address**: adres IP serwera.
- **SERVER_PORT**: port TCP serwera (serwer Telnet jest portem 23).
- **WAIT_OPTION**: określa, jak długo usługa będzie czekać na połączenie klienta Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:

    - **wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) pomyślnego nawiązania połączenia z klientem.
- **NX_TELNET_ERROR**: (0xF0) błąd połączenia z klientem.
- **NX_TELNET_NOT_DISCONNECTED**: (0XF4) klient jest już połączony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.
- NX_TELNET_INVALID_PARAMETER: (0xF5) nieprawidłowe dane wejściowe bez wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a>nx_telnet_client_create

Tworzenie klienta Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do bloku kontroli klienta Telnet.
- **CLIENT_NAME**: nazwa wystąpienia klienta.
- **ip_ptr**: wskaźnik do wystąpienia adresu IP.
- **window_size**: rozmiar okna odbierania protokołu TCP dla tego klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne utworzenie klienta.
- Błąd tworzenia gniazda **NX_TELNET_ERROR**: (0xF0).
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta lub adresu IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a>nx_telnet_client_delete

Usuwanie klienta Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie klienta programu Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do bloku kontroli klienta Telnet.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne usunięcie klienta.
- **NX_TELNET_NOT_DISCONNECTED**: (0XF4) klient jest nadal połączony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a>nx_telnet_client_disconnect

Rozłączanie klienta Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa rozłącza połączenie z wcześniej połączonym wystąpieniem klienta programu Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do bloku kontroli klienta Telnet.
- **WAIT_OPTION**: określa, jak długo usługa będzie oczekiwać na rozłączenie przez klienta Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:

    - **wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne rozłączenie klienta.
- **NX_TELNET_NOT_CONNECTED**: (0XF3) klient nie jest połączony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.


### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a>nx_telnet_client_packet_receive

Odbieranie pakietu za pośrednictwem klienta Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa odbiera pakiet z wcześniej połączonego wystąpienia klienta programu Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do bloku kontroli klienta Telnet.
- **packet_ptr**: wskaźnik do miejsca docelowego dla odebranego pakietu.
- **WAIT_OPTION**: określa, jak długo usługa będzie oczekiwać na odebranie pakietu klienta Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0x00) odbieranie pakietu klienta powiodło się.
- NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a>nx_telnet_client_packet_send

Wyślij pakiet za pośrednictwem klienta Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet za pośrednictwem wcześniej połączonego wystąpienia klienta programu Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr**: wskaźnik do bloku kontroli klienta Telnet.
- **packet_ptr**: wskaźnik do pakietu do wysłania.
- **WAIT_OPTION**: określa, jak długo usługa będzie czekać na wysłanie pakietu klienta Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne wysłanie pakietu klienta.
- **NX_TELNET_ERROR**: (0XF0) wysyłanie pakietu nie powiodło się — obiekt wywołujący jest odpowiedzialny za wydanie pakietu.
- NX_PTR_ERROR: (0x07) nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a>nx_telnet_server_create

Tworzenie serwera Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie serwera Telnet na określonym wystąpieniu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.
- **server_name**: nazwa wystąpienia serwera Telnet.
- **ip_ptr**: wskaźnik do skojarzonego wystąpienia adresu IP.
- **stack_ptr**: wskaźnik do stosu dla wewnętrznego wątku serwera.
- **sack_size**: rozmiar stosu w bajtach.
- **new_connection**: wskaźnik funkcji procedury wywołania zwrotnego aplikacji. Ta procedura jest wywoływana za każdym razem, gdy na serwerze zostanie wykryte nowe żądanie połączenia klienta programu Telnet.
- **receive_data**: wskaźnik funkcji procedury wywołania zwrotnego aplikacji. Ta procedura jest wywoływana za każdym razem, gdy w ramach połączenia są obecne nowe dane klienta programu Telnet. Ta procedura jest odpowiedzialna za wydanie pakietu.
- **end_connection**: wskaźnik funkcji procedury wywołania zwrotnego aplikacji. Ta procedura jest wywoływana za każdym razem, gdy połączenie z klientem Telnet zostanie odłączone przez klienta lub przekroczenie limitu czasu połączenia klienta ("limit czasu aktywności"). Serwer można także rozłączyć za pośrednictwem usługi *nx_telnet_server_disconnect* opisanej poniżej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne utworzenie serwera.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik wywołania zwrotnego serwera, adresu IP, stosu lub aplikacji.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a>nx_telnet_server_delete

Usuwanie serwera Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie serwera Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne usunięcie serwera.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a>nx_telnet_server_disconnect

Rozłączanie klienta Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a>Opis

Ta usługa rozłącza wcześniej połączony klient z tym wystąpieniem serwera Telnet. Ta procedura jest zazwyczaj wywoływana z funkcji wywołania zwrotnego odbierania danych aplikacji w odpowiedzi na warunek wykryty w odebranych danych.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.
- **logical_connection**: połączenie logiczne odpowiada połączeniu z klientem na tym serwerze. Prawidłowy zakres wartości z zakresu od 0 do NX_TELENET_MAX_CLIENTS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne rozłączenie serwera.
- **NX_TELNET_ERROR**: (0xF0) rozłączenie serwera nie powiodło się.
- NX_OPTION_ERROR: (0x0A) nieprawidłowe połączenie logiczne.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a>nx_telnet_server_get_open_connection_count

Zwróć liczbę aktualnie otwartych połączeń

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a>Opis

Ta usługa zwraca liczbę aktualnie połączonych klientów Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.
- **Connection_count**: wskaźnik do pamięci, aby przechowywać liczbę połączeń

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne zakończenie.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a>nx_telnet_server_packet_send

Wyślij pakiet przez połączenie klienta

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet do połączenia klienta w tym wystąpieniu serwera Telnet. Ta procedura jest zazwyczaj wywoływana z funkcji wywołania zwrotnego odbierania danych aplikacji w odpowiedzi na warunek wykryty w odebranych danych.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.
- **logical_connection**: połączenie logiczne odpowiada połączeniu z klientem na tym serwerze. Prawidłowy zakres wartości z zakresu od 0 do NX_TELENET_MAX_CLIENTS.
- **packet_ptr**: wskaźnik do odebranego pakietu.
- **WAIT_OPTION**: określa, jak długo usługa będzie czekać na wysłanie pakietu serwera Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **wartość limitu czasu**: (0X00000001 przez 0XFFFFFFFE) wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER**: (0Xffffffff) wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu, aż serwer Telnet odpowie na żądanie. 

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślne wysłanie pakietu.
- **NX_TELNET_FAILED**: (0xF2) wysyłanie gniazda TCP nie powiodło się.
- NX_OPTION_ERROR: (0x0A) nieprawidłowe połączenie logiczne.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a>nx_telnet_server_packet_pool_set

Ustaw wcześniej utworzoną pulę pakietów jako pulę serwerów Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a>Opis

Ta usługa ustawia wcześniej utworzoną pulę pakietów jako pulę pakietów serwera Telnet, jeśli NX_TELNET_SERVER_USER_CREATE_PACKET_POOL jest zdefiniowana. Wymaga również, aby nie NX_TELNET_SERVER_OPTION_DISABLE być zdefiniowany, aby serwer Telnet mógł przesyłać opcje Telnet do klientów Telnet.

Pozwala to aplikacjom na tworzenie puli pakietów w innej pamięci, np. Brak pamięci podręcznej, niż stos serwera Telnet. Należy pamiętać, że jeśli ta funkcja nie sprawdza, czy pula pakietów serwera Telnet została już ustawiona. Jeśli zostanie wywołana dla wskaźnika puli pakietów serwera Telnet o wartości innej niż null, spowoduje to zastąpienie i zastąpienie istniejącej puli pakietów pulą pakietów wskazywanym przez wskaźnik wejściowy.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr**: wskaźnik do bloku sterowania serwerem Telnet
- **packet_pool_ptr**: wskaźnik do wcześniej utworzonej puli pakietów

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) pomyślnie ustawił pulę.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.

### <a name="allowed-from"></a>Dozwolone z

Init, wątki

### <a name="example"></a>Przykład

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a>nx_telnet_server_start

Uruchom serwer Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a>Opis

Ta usługa uruchamia wcześniej utworzone wystąpienie serwera Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) zostało pomyślnie rozpoczęte.
- **NX_TELNET_NO_PACKET_POOL**: (0XF6) brak zestawu puli pakietów
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a>nx_telnet_server_stop

Zatrzymaj serwer Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Opis

Ta usługa przerywa poprzednio utworzone i uruchomione wystąpienie serwera Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr**: wskaźnik do bloku sterowania serwerem Telnet.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS**: (0X00) zostało pomyślnie zatrzymane
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy obiekt wywołujący usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```