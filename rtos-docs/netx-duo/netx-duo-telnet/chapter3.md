---
title: Rozdział 3 — Opis Azure RTOS NetX Duo Telnet
description: Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX Duo Telnet (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 70bf4016793572d7327d12be182750316659c3c4260d2f7db8acddbba00c5601
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791996"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a>Rozdział 3 — Opis Azure RTOS NetX Duo Telnet

Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX Duo Telnet (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

- **nx_telnet_client_connect:** Połączenie *klienta Telnet z adresem IPv4*
- **nxd_telnet_client_connect:** Połączenie *klienta Telnet IPv6 z adresem IPv6*
- **nx_telnet_client_create:** tworzenie *klienta Telnet*
- **nx_telnet_client_delete:** usuwanie *klienta Telnet*
- **nx_telnet_client_disconnect:** *rozłączanie klienta Telnet*
- **nx_telnet_client_packet_receive:** odbieranie *pakietów za pośrednictwem klienta Telnet*
- **nx_telnet_client_packet_send:** wysyłanie *pakietów za pośrednictwem klienta Telnet*
- **nx_telnet_server_create:** tworzenie *serwera Telnet*
- **nx_telnet_server_delete:** usuwanie *serwera Telnet*
- **nx_telnet_server_disconnect:** *rozłączanie klienta Telnet*
- **nx_telnet_server_get_open_connection_count:** Pobieranie *liczby otwartych połączeń*
- **nx_telnet_server_packet_send:** Wysyłanie *pakietów za pośrednictwem połączenia klienta*
- **nx_telnet_server_packet_pool_set:** ustaw *pulę pakietów jako pulę pakietów serwera Telnet*
- **nx_telnet_server_start:** *uruchamianie serwera Telnet*
- **nx_telnet_server_stop:** *zatrzymywanie serwera Telnet*

## <a name="nx_telnet_client_connect"></a>nx_telnet_client_connect

Połączenie klienta Telnet z adresem IPv4

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje połączyć wcześniej utworzone wystąpienie klienta Telnet z serwerem pod określonym adresem IP i portem przy użyciu adresu IPv4 dla serwera Telnet. Ta usługa wstawia adres IP serwera ULONG w bloku sterowania programu NXD_ADDRESS i ustawia wersję adresu IP na 4 przed wywołaniem usługi *nxd_telnet_client_connect* opisanej poniżej.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** wskaźnik do bloku sterowania klienta Telnet.
- **server_ip:** adres IPv4 serwera Telnet.
- **server_port:** port TCP serwera (serwer Telnet to port 23).
- **wait_option:** określa, jak długo usługa będzie czekać na połączenie klienta Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:

    - **Wartość** limitu czasu: (0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (od 1 do 0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF)Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer Telnet nie odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne połączenie klienta.
- **NX_TELNET_NOT_DISCONNECTED:**(0xF4) Klient jest już połączony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.
- NX_IP_ADDRESS_ERROR: (0x21) Nieprawidłowy adres IP.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący usługę.

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

Połączenie klienta Telnet z adresem IPv6 lub IPv4

### <a name="prototype"></a>Prototype

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa próbuje połączyć wcześniej utworzone wystąpienie klienta Telnet z serwerem pod określonym adresem IP i portem przy użyciu adresu IPv6 serwera Telnet. Ta usługa może przyjmować adres IPv4 lub IPv6, ale musi być zawarta w NXD_ADDRESS zmiennej *server_ip_address.*

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** wskaźnik do bloku sterowania klienta Telnet.
- **server_ip_address:** adres IP serwera.
- **server_port:** port TCP serwera (serwer Telnet to port 23).
- **wait_option:** określa, jak długo usługa będzie czekać na połączenie klienta Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:

    - **Wartość** limitu czasu: (0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (od 1 do 0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer Telnet nie odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne połączenie klienta.
- **NX_TELNET_ERROR:**(0xF0) Błąd połączenia klienta.
- **NX_TELNET_NOT_DISCONNECTED:**(0xF4) Klient jest już połączony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący usługę.
- NX_TELNET_INVALID_PARAMETER: (0xF5) Nieprawidłowe dane wejściowe bez wskaźnika

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

- **client_ptr:** wskaźnik do bloku sterowania klienta Telnet.
- **client_name:** nazwa wystąpienia klienta.
- **ip_ptr:** Wskaźnik do wystąpienia adresu IP.
- **window_size:** rozmiar okna odbierania TCP dla tego klienta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne utworzenie klienta.
- **NX_TELNET_ERROR:**(0xF0) Błąd tworzenia gniazda.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta lub adresu IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

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

Ta usługa usuwa utworzone wcześniej wystąpienie klienta Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** wskaźnik do bloku sterowania klienta Telnet.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne usunięcie klienta.
- **NX_TELNET_NOT_DISCONNECTED:**(0xF4) Klient nadal jest połączony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

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

Ta usługa rozłącza wcześniej połączone wystąpienie klienta Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** wskaźnik do bloku sterowania klienta Telnet.
- **wait_option:** określa, jak długo usługa będzie czekać na rozłączenie klienta Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:

    - **Wartość** limitu czasu: (0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (od 1 do 0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer Telnet nie odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne rozłączenie klienta.
- **NX_TELNET_NOT_CONNECTED:**(0xF3) Klient nie jest połączony.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik klienta.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.


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

Ta usługa odbiera pakiet z wcześniej połączonego wystąpienia klienta Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** wskaźnik do bloku sterowania klienta Telnet.
- **packet_ptr:** wskaźnik do miejsca docelowego odebranego pakietu.
- **wait_option:** określa, jak długo usługa będzie czekać na odbieranie pakietu klienta Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **Wartość** limitu czasu: (0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (od 1 do 0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer Telnet nie odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne odbieranie pakietu klienta.
- NX_PTR_ERROR: (0x07) Nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący usługę.

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

Wysyłanie pakietu za pośrednictwem klienta Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet za pośrednictwem wcześniej połączonego wystąpienia klienta Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr:** wskaźnik do bloku sterowania klienta Telnet.
- **packet_ptr:** Wskaźnik do pakietu do wysłania.
- **wait_option:** określa, jak długo usługa będzie czekać na wysłanie pakietu klienta Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **Wartość** limitu czasu: (0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (od 1 do 0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki serwer Telnet nie odpowie na żądanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne wysłanie pakietu klienta.
- **NX_TELNET_ERROR:**(0xF0) Wysyłanie pakietu nie powiodło się — wywołujący odpowiada za zwolnienie pakietu.
- NX_PTR_ERROR: (0x07) Nieprawidłowe dane wejściowe wskaźnika
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący usługę.

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

Ta usługa tworzy wystąpienie serwera Telnet w określonym wystąpieniu adresu IP.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr:** wskaźnik do bloku sterowania serwera Telnet.
- **server_name:** nazwa wystąpienia serwera Telnet.
- **ip_ptr:** Wskaźnik do skojarzonego wystąpienia adresu IP.
- **stack_ptr:** wskaźnik do stosu dla wewnętrznego wątku serwera.
- **sack_size:** rozmiar stosu w bajtach.
- **new_connection:** Wskaźnik funkcji procedury wywołania zwrotnego aplikacji. Ta procedura jest wywoływana za każdym razem, gdy serwer wykrywa nowe żądanie połączenia klienta Telnet.
- **receive_data:** Wskaźnik funkcji procedury wywołania zwrotnego aplikacji. Ta procedura jest wywoływana za każdym razem, gdy nowe dane klienta Telnet są obecne w połączeniu. Ta procedura jest odpowiedzialna za zwalnianie pakietu.
- **end_connection:** Wskaźnik funkcji procedury wywołania zwrotnego aplikacji. Ta procedura jest wywoływana za każdym razem, gdy połączenie klienta Telnet zostanie rozłączone przez klienta lub upłynie limit czasu połączenia klienta ("limit czasu działania" wygasa). Serwer można również rozłączyć za *pośrednictwem usługi nx_telnet_server_disconnect* opisanej poniżej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne utworzenie serwera.
- NX_PTR_ERROR: (0x07) Nieprawidłowe wskaźniki wywołania zwrotnego serwera, adresu IP, stosu lub aplikacji.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

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

Ta usługa usuwa utworzone wcześniej wystąpienie serwera Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr:** wskaźnik do bloku sterowania serwera Telnet.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne usunięcie serwera.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

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

Ta usługa rozłącza wcześniej połączonego klienta w tym wystąpieniu serwera Telnet. Ta procedura jest zwykle wywoływana z funkcji wywołania zwrotnego odbierania danych aplikacji w odpowiedzi na warunek wykryty w odebranych danych.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr:** wskaźnik do bloku sterowania serwera Telnet.
- **logical_connection:** połączenie logiczne odpowiadające połączeniu klienta na tym serwerze. Prawidłowa wartość zakresu od 0 do NX_TELENET_MAX_CLIENTS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne rozłączenie serwera.
- **NX_TELNET_ERROR:**(0xF0) Rozłączanie serwera nie powiodło się.
- NX_OPTION_ERROR: (0x0A) Nieprawidłowe połączenie logiczne.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

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

Zwracana liczba aktualnie otwartych połączeń

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a>Opis

Ta usługa zwraca liczbę aktualnie połączonych klientów Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr:** wskaźnik do bloku sterowania serwera Telnet.
- **Connection_count:** wskaźnik do pamięci do przechowywania liczby połączeń

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne ukończenie.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a>nx_telnet_server_packet_send

Wysyłanie pakietów za pośrednictwem połączenia klienta

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet do połączenia klienta w tym wystąpieniu serwera Telnet. Ta procedura jest zwykle wywoływana z funkcji wywołania zwrotnego odbierania danych aplikacji w odpowiedzi na warunek wykryty w odebranych danych.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr:** wskaźnik do bloku sterowania serwera Telnet.
- **logical_connection:** połączenie logiczne odpowiadające połączeniu klienta na tym serwerze. Prawidłowa wartość zakresu od 0 do NX_TELENET_MAX_CLIENTS.
- **packet_ptr:** wskaźnik do odebranego pakietu.
- **wait_option:** określa, jak długo usługa będzie czekać na wysłanie pakietu serwera Telnet. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **Wartość** limitu czasu: (0x00000001 do 0xFFFFFFFE) Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na odpowiedź serwera Telnet.
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF) Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony, dopóki serwer Telnet nie odpowie na żądanie. 

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślne wysyłanie pakietów.
- **NX_TELNET_FAILED:** wysyłanie gniazda TCP 0xF2 (0xF2) nie powiodło się.
- NX_OPTION_ERROR: (0x0A) Nieprawidłowe połączenie logiczne.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący usługę.

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

Ta usługa ustawia wcześniej utworzoną pulę pakietów jako pulę pakietów serwera Telnet, NX_TELNET_SERVER_USER_CREATE_PACKET_POOL jest zdefiniowana. Wymaga również, aby NX_TELNET_SERVER_OPTION_DISABLE zdefiniowane w taki sposób, że serwer Telnet wymaga puli pakietów do przesyłania opcji Telnet do klientów Telnet.

Dzięki temu aplikacje mogą tworzyć pule pakietów w innej pamięci, np. bez pamięci podręcznej, niż stos serwera Telnet. Należy pamiętać, że jeśli ta funkcja nie sprawdza, czy pula pakietów serwera Telnet jest już ustawiona. Jeśli zostanie wywołana na wskaźniku puli pakietów serwera Telnet o wartości innych niż null, zastąpi ją i zastąpi istniejącą pulę pakietów pulą pakietów wskazywaną przez wskaźnik wejściowy.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr:** wskaźnik do bloku sterowania serwera Telnet
- **packet_pool_ptr:** Wskaźnik do wcześniej utworzonej puli pakietów

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślnie ustawiono pulę.
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.

### <a name="allowed-from"></a>Dozwolone z

Init, Threads

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

Uruchamianie serwera Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a>Opis

Ta usługa uruchamia utworzone wcześniej wystąpienie serwera Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr:** wskaźnik do bloku sterowania serwera Telnet.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślnie rozpoczęto.
- **NX_TELNET_NO_PACKET_POOL:**(0xF6) Brak ustawionej puli pakietów
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a>nx_telnet_server_stop

Zatrzymywanie serwera Telnet

### <a name="prototype"></a>Prototype

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje utworzone wcześniej i uruchomione wystąpienie serwera Telnet.

### <a name="input-parameters"></a>Parametry wejściowe

- **server_ptr:** wskaźnik do bloku sterowania serwera Telnet.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS:**(0x00) Pomyślnie zatrzymane
- NX_PTR_ERROR: (0x07) Nieprawidłowy wskaźnik serwera.
- NX_CALLER_ERROR: (0x11) Nieprawidłowy wywołujący usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```