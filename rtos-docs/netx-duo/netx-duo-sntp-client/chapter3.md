---
title: Rozdział 3 — Opis Azure RTOS klienta NetX Duo SNTP
description: Ten rozdział zawiera opis wszystkich usług klienta NetX Duo SNTP (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7aee18642e480ec61488515164c8a6816753dca86eb8f6d146ea22d4956e037a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791673"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a>Rozdział 3 — Opis Azure RTOS klienta NetX Duo SNTP

Ten rozdział zawiera opis wszystkich usług Azure RTOS NetX Duo SNTP (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

- **nx_sntp_client_create:** tworzenie *klienta SNTP*
- **nx_sntp_client_delete:** *usuwanie klienta SNTP*
- **nx_sntp_client_get_local_time:** uzyskiwanie *czasu lokalnego klienta SNTP*
- **nx_sntp_client_get_local_time_extended:** Uzyskiwanie *czasu lokalnego klienta SNTP*
- **nx_sntp_client_initialize_broadcast:** *inicjowanie klienta dla operacji emisji IPv4*
- **nxd_sntp_client_initialize_broadcast:** inicjowanie klienta dla operacji emisji *IPv6 lub IPv4*
- **nx_sntp_client_initialize_unicast:** *inicjowanie klienta dla operacji emisji pojedynczej protokołu IPv4*
- **nxd_sntp_client_initialize_unicast:** inicjowanie klienta dla operacji emisji pojedynczej *IPv4 lub IPv6*
- **nx_sntp_client_receiving_udpates:** Klient *obecnie otrzymuje prawidłowe aktualizacje SNTP*
- **nx_sntp_client_request_unicast_time:** wyślij *żądanie emisji pojedynczej bezpośrednio do serwera NTP*
- **nx_sntp_client_run_broadcast:** uruchamianie *klienta w trybie emisji*
- **nx_sntp_client_run_unicast:** uruchamianie *klienta w trybie emisji pojedynczej*
- **nx_sntp_client_set_local_time:** ustaw *początkowy czas lokalny* klienta SNTP
- **nx_sntp_client_set_time_update_notify:** ustaw *wywołanie zwrotne aktualizacji SNTP*
- **nx_sntp_client_stop:** *zatrzymaj wątek klienta SNTP*
- **nx_sntp_client_utility_display_date_and_time:** Wyświetl *czas NTP w sekundach*
- **nx_sntp_client_utility_msecs_to_fraction:** *konwertowanie milisekund na składnik ułamkowy NTP*
- **nx_sntp_client_utility_usecs_to_fraction:** *konwertowanie mikrosekund na składnik ułamkowy NTP*
- **nx_sntp_client_utility_fraction_to_usecs:** *konwertowanie składnika ułamkowego NTP na mikrosekundy*


## <a name="nx_sntp_client_create"></a>nx_sntp_client_create

Tworzenie klienta SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta SNTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

- **ip_ptr** Wskaźnik do wystąpienia adresu IP klienta

- **iface_index** Indeksowanie do interfejsu sieciowego SNTP

- **packet_pool_ptr** Wskaźnik do puli pakietów klienta

- **leap_second_handler** Wywołanie zwrotne odpowiedzi aplikacji na zbliżającą się sekundę przestępną

- **kiss_of_death_handler** Wywołanie zwrotne odpowiedzi aplikacji na odebranie pakietu Zniechęć do zgonu

- **random_number_generator** Wywołanie zwrotne do usługi generatora liczb losowych

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klienta

- **NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Nieprawidłowe dane wejściowe bez wskaźnika

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a>nx_sntp_client_delete

Usuwanie klienta SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wystąpienie klienta SNTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klienta

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a>nx_sntp_client_get_local_time

Uzyskiwanie czasu lokalnego klienta SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a>Opis

Ta usługa pobiera czas lokalny klienta SNTP z danymi wejściowymi wskaźnika buforu opcji w celu odbierania danych w formacie komunikatu ciągu.

Ta usługa jest przestarzała. Zachęcamy deweloperów do migracji do *nx_sntp_client_get_local_time_extended*().

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

- **sekundy** Wskaźnik do lokalnego czasu w sekundach

- **ułamek** Składnik ułamka czasu lokalnego

- **bufor** Wskaźnik do buforu do zapisu danych czasu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klienta

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a>nx_sntp_client_get_local_time_extended

Uzyskiwanie rozszerzonego czasu lokalnego klienta SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a>Opis

Ta usługa pobiera rozszerzony czas lokalny klienta SNTP z danymi wejściowymi wskaźnika buforu opcji w celu odbierania danych w formacie komunikatu ciągu.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

- **sekundy** Wskaźnik do lokalnego czasu w sekundach

- **ułamek** Wskaźnik do składnika ułamkowego

- **bufor** Wskaźnik do buforu do zapisu danych czasu

- **buffer_size** Długość buforu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klienta

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę

- NX_SIZE_ERROR (0x09) Sprawdzanie buffer_size nie powiodło się

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a>nx_sntp_client_initialize_broadcast

Inicjowanie klienta dla operacji emisji

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a>Opis

Ta usługa inicjuje operację klienta do emisji, ustawiając adres IP serwera SNTP oraz inicjjąc parametry uruchamiania SNTP i limity czasu. Jeśli adresy multiemisji i emisji nie mają wartości null, jest wybierany adres multiemisji. Jeśli oba adresy mają wartość null, zwracany jest błąd. Należy pamiętać, że obsługuje tylko adresy serwerów IPv4.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

- **multicast_server_address** Adres multiemisji SNTP

- **broadcast_time_server** Adres emisji serwera SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie klienta

- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a>nxd_sntp_client_initialize_broadcast

Inicjowanie klienta dla operacji emisji IPv4 lub IPv6

### <a name="prototype"></a>Prototype

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a>Opis

Ta usługa inicjuje operację klienta dla emisji, ustawiając adres IP serwera SNTP oraz inicjjąc parametry uruchamiania SNTP i limity czasu. Jeśli wskaźniki adresów emisji i multiemisji nie mają wartości null, jest wybierany adres multiemisji. Jeśli oba wskaźniki adresów mają wartość null, zwracany jest błąd. Obsługuje to zarówno typy adresów IPv4, jak i IPv6. Należy pamiętać, że protokół IPv6 nie obsługuje emisji, więc wskaźnik adresu emisji jest ustawiony na IPv6, zwracany jest błąd.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

- **multicast_server_address** Adres multiemisji serwera SNTP

- **broadcast_server_address** Adres emisji serwera SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Client successfully initialized (Klient usługi 0x00) został pomyślnie zainicjowany

- NX_SNTP_PARAM_ERROR (0xD0D) Nieprawidłowe dane wejściowe bez wskaźnika

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę


### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a>nx_sntp_client_initialize_unicast

Konfigurowanie klienta SNTP do uruchamiania w emisji pojedynczej

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a>Opis

Ta usługa inicjuje operację emisji pojedynczej klienta przez ustawienie adresu IP serwera SNTP oraz zainicjowanie parametrów uruchamiania SNTP i limitów czasu. Należy pamiętać, że obsługuje tylko adresy serwerów IPv4.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

- **unicast_time_server** Adres IP serwera SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Client successfully initialized (Klient usługi 0x00) został pomyślnie zainicjowany

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a>nxd_sntp_client_initialize_unicast

Konfigurowanie klienta SNTP do uruchamiania w emisji pojedynczej IPv4 lub IPv6

### <a name="prototype"></a>Prototype

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a>Opis

Ta usługa inicjuje operację emisji pojedynczej klienta przez skonfigurowanie adresu IP serwera SNTP oraz zainicjowanie parametrów uruchamiania SNTP i przecięć limitu czasu. Obsługuje to zarówno typy adresów IPv4, jak i IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

- **unicast_time_server** Adres IP serwera SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Client successfully initialized (Klient usługi 0x00) został pomyślnie zainicjowany

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowe dane wejściowe bez wskaźnika

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a>nx_sntp_client_receiving_updates

Wskazanie, czy klient otrzymuje prawidłowe aktualizacje

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a>Opis

Ta usługa wskazuje, czy klient otrzymuje prawidłowe aktualizacje SNTP. Jeśli zostanie przekroczony maksymalny czas bez ważnej aktualizacji lub limitu kolejnych nieprawidłowych aktualizacji, stan odbierania jest zwracany jako false. Należy pamiętać, że klient SNTP jest nadal uruchomiony i jeśli aplikacja chce ponownie uruchomić klienta SNTP z innym serwerem emisji pojedynczej lub emisji/multiemisji, musi zatrzymać klienta SNTP przy użyciu usługi *nx_sntp_client_stop,* ponownie zainicjować klienta przy użyciu jednej z usług inicjowania z innym serwerem.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP.

- **receive_status** Wskaźnik do wskaźnika, jeśli klient otrzymuje prawidłowe aktualizacje.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Klient pomyślnie odebrał stan aktualizacji

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a>nx_sntp_client_request_unicast_time

Wysyłanie żądania emisji pojedynczej bezpośrednio do serwera NTP


### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji bezpośrednie wysyłanie żądania emisji pojedynczej do serwera NTP asynchronicznie z zadania wątku klienta SNTP. Opcja oczekiwania określa, jak długo czekać na odpowiedź. Jeśli to się powiedzie, aplikacja może użyć innych usług klienta SNTP w celu uzyskania najnowszej wersji. Aby uzyskać więcej informacji, zobacz sekcję **SNTP Asynchronous Unicast Requests** (Asynchroniczne żądania emisji pojedynczej SNTP).

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP.

- **Wait_option** Opcja oczekiwania na odpowiedź NTP w taktach czasomierza.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Klient pomyślnie wysyła i odbiera aktualizację emisji pojedynczej

- **NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Wątek klienta nie został uruchomiony

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a>nx_sntp_client_run_broadcast

Uruchamianie klienta w trybie emisji

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia klienta w trybie emisji, w którym będzie czekać na odbieranie emisji z serwera SNTP. Jeśli zostanie odebrany prawidłowy komunikat SNTP emisji, zostanie zresetowany limit czasu klienta SNTP dla maksymalnej wartości bez aktualizacji i liczba odebranych kolejnych nieprawidłowych komunikatów. Jeśli którykolwiek z tych limitów zostanie przekroczony, klient SNTP ustawia stan serwera na nieprawidłowy, mimo że nadal będzie czekać na otrzymanie aktualizacji. Aplikacja może sondować zadanie klienta SNTP pod temat stanu serwera, a w przypadku nieprawidłowego zatrzymania klienta SNTP i ponownego zainicjowania go przy użyciu innego adresu emisji SNTP. Można również przełączyć się na serwer SNTP emisji pojedynczej.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP.

### <a name="return-values"></a>Wartości zwrócone

- **stan** -------- stan ukończenia

- **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client już uruchomiony

- **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized (Klient nie zainicjowany)

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a>nx_sntp_client_run_unicast

Uruchamianie klienta w trybie emisji pojedynczej

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa uruchamia klienta w trybie emisji pojedynczej, gdzie okresowo wysyła żądanie emisji pojedynczej do serwera SNTP w celu aktualizacji czasu. Jeśli zostanie odebrany prawidłowy komunikat SNTP, limit czasu klienta SNTP dla maksymalnej liczby bez aktualizacji, początkowy interwał sondowania i liczba kolejnych odebranych nieprawidłowych komunikatów są resetowane. Jeśli którykolwiek z tych limitów zostanie przekroczony, klient SNTP ustawia stan serwera na nieprawidłowy, mimo że nadal będzie sondować i czekać na otrzymanie aktualizacji. Aplikacja może sondować zadanie klienta SNTP pod temat stanu serwera, a w przypadku nieprawidłowego zatrzymania klienta SNTP i ponownego zainicjowania go przy użyciu innego adresu emisji pojedynczej SNTP. Może również przełączyć się na serwer SNTP emisji.

.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uruchomiliśmy klienta w trybie emisji pojedynczej

- **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client już uruchomiony

- **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized (Klient nie zainicjowany)

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy wywołujący usługę


### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a>nx_sntp_client_set_local_time

Ustawianie czasu lokalnego klienta SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a>Opis

Ta usługa ustawia czas lokalny klienta SNTP na czas wejściowy w formacie SNTP, np. sekundy i "ułamek", który jest formatem do umieszczania ułamków sekundy w formacie szesnastkowym. Jest on przeznaczony do aktualizowania czasu lokalnego klienta SNTP z niezależnego strażnika czasu, np. zegara czasu rzeczywistego. Protokół SNTP jest przeznaczony dla aktualizacji czasu SNTP zachować czas zegara lokalnego "dryfowania". Aktualizacje czasu serwera SNTP mogą być, ale nie są przeznaczone do wyłącznego wprowadzania czasu lokalnego klienta SNTP, jeśli na urządzeniu aplikacji nie ma niezależnego strażnika czasu.

Za pomocą tego interfejsu API można również zapewnić klientowi SNTP czas podstawowy przed uruchomieniem wątku klienta SNTP. Czas lokalny klienta SNTP jest porównywany z odebranych aktualizacji dla danych prawidłowego czasu. Po pierwszym otrzymaniu aktualizacji mogą wystąpić bardzo duże rozbieżności. W związku z tym istnieje możliwość ignorowania rozbieżności w pierwszej aktualizacji przez klienta SNTP. W ten sposób klient SNTP może uruchomić się bez czasu podstawowego. Czas wejściowy można uzyskać ze znanych czasów epok (zazwyczaj dostępnych w Internecie) i są obliczane jako liczba sekund od 1 stycznia 1900 r. (do 2036 r., gdy zostanie uruchomiona nowa "epoka".

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

- **sekundy** Składnik sekund danych wejściowych czasu

- **ułamek** Składnik Subseconds w formacie ułamkowym SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie ustawiono czas lokalny

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja

### <a name="example"></a>Przykład

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a>nx_sntp_client_set_time_update_notify

Ustawianie wywołania zwrotnego aktualizacji SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a>Opis

Ta usługa ustawia wywołanie zwrotne, aby powiadomić aplikację, gdy klient SNTP odbierze aktualizację prawidłowego czasu. Dostarcza rzeczywisty komunikat SNTP i czas lokalny klienta SNTP (zazwyczaj taki sam) w formacie NTP. Aplikacja może bezpośrednio używać danych NTP lub wywołać usługę nx_sntp_client_utility_display_date_time, aby *przekonwertować* czas na format czytelny dla człowieka.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

- **time_update_cb** Wskaźnik do funkcji wywołania zwrotnego

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie ustaw wywołanie zwrotne

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja

### <a name="example"></a>Przykład

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a>nx_sntp_client_stop

Zatrzymywanie wątku klienta SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa zatrzymuje wątek klienta SNTP. Zadania wątków klienta SNTP, które są uruchamiane w nieskończonej pętli, wstrzymują się przy każdej iteracji, aby zwolnić kontrolę stanu klienta SNTP i umożliwić aplikacjom wykonywanie wywołań interfejsu API na kliencie SNTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku sterowania klienta SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie zatrzymany wątek klienta

- **NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP Client thread not started (Nie uruchomiliśmy wątku klienta SNTP)

- NX_PTR_ERROR (0x07) Nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a>nx_sntp_client_utility_display_date_time

Konwertowanie ntp czasu na ciąg daty i czasu

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a>Opis

Ta usługa konwertuje czas lokalny klienta SNTP na format daty miesiąca roku i zwraca datę w dostarczonym buforze. Ta NX_SNTP_CURRENT_YEAR nie musi być tym samym rokiem co bieżący czas klienta, ale musi być zdefiniowana.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr wskaźnik do klienta SNTP**

- **bufor** Wskaźnik do buforu do przechowywania daty

- **długość** Rozmiar buforu wejściowego

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna konwersja

- **NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR zdefiniowany lub nie określono czasu klienta lokalnego

- **NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Niewystarczająca długość buforu


### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a>nx_sntp_client_utility_msecs_to_fraction

Konwertowanie milisekund na składnik ułamkowy NTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a>Opis

Ta usługa konwertuje milisekundy wejściowe na składnik ułamka NTP. Jest on przeznaczony do użytku z aplikacjami, które mają początkowy czas podstawowy dla klienta SNTP, ale nie w formacie NTP sekund/ułamków. Aby można było zrobić prawidłowy ułamek, liczba milisekund musi być mniejsza niż 1000.

### <a name="input-parameters"></a>Parametry wejściowe

- **milisekundy (w milisekundach) do konwersji**

- **ułamek** Wskaźnik do milisekund przekonwertowany na ułamek

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna konwersja

- **NX_SNTP_OVERFLOW_ERROR** (0xD32) Błąd podczas konwertowania czasu na datę

- NX_SNTP_INVALID_TIME (0xD30) Nieprawidłowe dane wejściowe SNTP

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a>nx_sntp_client_utility_usecs_to_fraction

Konwertowanie mikrosekund na składnik ułamkowy NTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a>Opis

Ta usługa konwertuje mikrosekundy wejściowe na składnik ułamkowy NTP. Jest on przeznaczony do użytku z aplikacjami, które mają początkowy czas podstawowy dla klienta SNTP, ale nie w formacie NTP sekund/ułamków. Liczba mikrosekund musi być mniejsza niż 1000000, aby można było dokonać prawidłowego ułamka.

### <a name="input-parameters"></a>Parametry wejściowe

- **mikrosekundy** Mikrosekundy do konwersji

- **ułamek** Wskaźnik do mikrosekund przekonwertowany na ułamek

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna konwersja

- **NX_SNTP_OVERFLOW_ERROR** (0xD32) Błąd podczas konwertowania czasu na datę

- NX_SNTP_INVALID_TIME (0xD30) Nieprawidłowe dane wejściowe SNTP

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a>nx_sntp_client_utility_fraction_to_usecs

Konwertowanie składnika ułamkowego NTP na mikrosekundy

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a>Opis

Ta usługa konwertuje wejściowy składnik ułamkowy NTP na mikrosekundy.

### <a name="input-parameters"></a>Parametry wejściowe

- **fraction Fraction do konwersji**

- **mikrosekundy** Wskaźnik do ułamka przekonwertowany na mikrosekundy

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślna konwersja

- NX_SNTP_INVALID_TIME (0xD30) Nieprawidłowe dane wejściowe SNTP

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```