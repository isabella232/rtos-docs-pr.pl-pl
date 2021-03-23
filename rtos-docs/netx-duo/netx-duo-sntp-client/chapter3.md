---
title: Rozdział 3 — Opis usług klienta usługi Azure RTO NetX Duo (SNTP)
description: Ten rozdział zawiera opis wszystkich usług klienta SNTP NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821649"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a>Rozdział 3 — Opis usług klienta usługi Azure RTO NetX Duo (SNTP)

Ten rozdział zawiera opis wszystkich usług klienta usługi Azure RTO NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

- **nx_sntp_client_create**: *Tworzenie klienta SNTP*
- **nx_sntp_client_delete**: *Usuwanie klienta SNTP*
- **nx_sntp_client_get_local_time**: *pobieranie czasu lokalnego klienta SNTP*
- **nx_sntp_client_get_local_time_extended**: *pobieranie czasu lokalnego klienta SNTP*
- **nx_sntp_client_initialize_broadcast**: *zainicjuj klienta dla operacji emisji IPv4*
- **nxd_sntp_client_initialize_broadcast**: *zainicjuj klienta dla operacji emisji IPv6 lub IPv4*
- **nx_sntp_client_initialize_unicast**: *zainicjuj klienta dla operacji IPv4 emisji pojedynczej*
- **nxd_sntp_client_initialize_unicast**: *zainicjuj klienta dla operacji IPv4 lub IPv6 emisji pojedynczej*
- **nx_sntp_client_receiving_udpates**: *klient otrzymuje obecnie prawidłowe aktualizacje SNTP*
- **nx_sntp_client_request_unicast_time**: *Wyślij żądanie emisji pojedynczej bezpośrednio do serwera NTP*
- **nx_sntp_client_run_broadcast**: *Uruchamianie klienta w trybie emisji*
- **nx_sntp_client_run_unicast**: *Uruchamianie klienta w trybie emisji pojedynczej*
- **nx_sntp_client_set_local_time**: *Ustaw początkowy czas lokalny klienta SNTP*
- **nx_sntp_client_set_time_update_notify**: *Ustaw wywołanie ZWROTne aktualizacji SNTP*
- **nx_sntp_client_stop**: *Zatrzymywanie wątku klienta SNTP*
- **nx_sntp_client_utility_display_date_and_time**: *Wyświetlanie czasu NTP w sekundach*
- **nx_sntp_client_utility_msecs_to_fraction**: *konwertowanie MILISEKUND na składnik NTP*
- **nx_sntp_client_utility_usecs_to_fraction**: *Konwertuj mikrosekundy na składnik ułamka NTP*
- **nx_sntp_client_utility_fraction_to_usecs**: *konwertowanie składnika częściowego NTP na mikrosekundy*


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

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

- **ip_ptr** Wskaźnik do wystąpienia adresu IP klienta

- **iface_index** Indeksowanie do interfejsu sieciowego SNTP

- **packet_pool_ptr** Wskaźnik do puli pakietów klienta

- **leap_second_handler** Wywołanie zwrotne dla odpowiedzi aplikacji w trakcie oczekiwania na sekundę

- **kiss_of_death_handler** Wywołanie zwrotne dla odpowiedzi aplikacji do odebrania pakietu zgonu

- **random_number_generator** Wywołanie zwrotne do usługi generatora liczb losowych

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie klienta

- **NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0XD2A) Nieprawidłowa wejściowa niebędąca wskaźnikiem

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie klienta

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi

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

Pobieranie czasu lokalnego klienta SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a>Opis

Ta usługa Pobiera czas lokalny klienta SNTP z wejściem wskaźnika buforu opcji w celu odbierania danych w formacie ciągu wiadomości.

Ta usługa jest przestarzała. Deweloperzy są zachęcani do migracji do *nx_sntp_client_get_local_time_extended*().

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

- **sekund** Wskaźnik na czas lokalny w sekundach

- **ułamek** Składnik lokalnej części czasu

- **bufor** Wskaźnik do buforu w celu zapisania danych czasu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie klienta

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi

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

Pobieranie rozszerzonego czasu lokalnego klienta SNTP

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

Ta usługa pobiera rozszerzony czas lokalny klienta SNTP z wejściem wskaźnika buforu opcji w celu odbierania danych w formacie ciągu wiadomości.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

- **sekund** Wskaźnik na czas lokalny w sekundach

- **ułamek** Wskaźnik do składnika ułamkowego

- **bufor** Wskaźnik do buforu w celu zapisania danych czasu

- **buffer_size** Długość buforu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie klienta

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi

- Sprawdzanie NX_SIZE_ERROR (0x09) nie powiodło się buffer_size

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

Zainicjuj klienta dla operacji emisji

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a>Opis

Ta usługa inicjuje klienta na potrzeby operacji emisji, ustawiając adres IP serwera SNTP i inicjując parametry uruchamiania i limity czasu usługi SNTP. Jeśli adresy multiemisji i emisji są inne niż null, wybierany jest adres multiemisji. Jeśli oba adresy mają wartość null, zwracany jest błąd. Zwróć uwagę na to, że obsługuje tylko adresy serwera IPv4.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

- **multicast_server_address** Adres multiemisji SNTP

- **broadcast_time_server** Adres emisji serwera SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie klienta

- **NX_INVALID_PARAMETERS** (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a>nxd_sntp_client_initialize_broadcast

Zainicjuj klienta dla operacji emisji IPv4 lub IPv6

### <a name="prototype"></a>Prototype

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a>Opis

Ta usługa inicjuje klienta na potrzeby operacji emisji przez skonfigurowanie adresu IP serwera SNTP i Inicjowanie parametrów uruchamiania i limitów czasu usługi SNTP. Jeśli wskaźniki emisji i adresów multiemisji nie mają wartości null, wybierany jest adres multiemisji. Jeśli oba wskaźniki adresów mają wartość null, zwracany jest błąd. Obsługuje to zarówno typy adresów IPv4, jak i IPv6. Należy zauważyć, że protokół IPv6 nie obsługuje emisji, więc wskaźnik adresu emisji jest ustawiony na wartość IPv6, zwracany jest błąd.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

- **multicast_server_address** Adres multiemisji serwera SNTP

- **broadcast_server_address** Adres emisji serwera SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślnie zainicjowano klienta

- NX_SNTP_PARAM_ERROR (0xD0D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi


### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa inicjuje klienta dla operacji emisji pojedynczej, ustawiając adres IP serwera SNTP i inicjując parametry uruchamiania i limity czasu usługi SNTP. Zwróć uwagę na to, że obsługuje tylko adresy serwera IPv4.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

- **unicast_time_server** Adres IP serwera SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślnie zainicjowano klienta

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a>nxd_sntp_client_initialize_unicast

Konfigurowanie klienta SNTP do uruchamiania w protokole IPv4 lub IPv6 emisji pojedynczej

### <a name="prototype"></a>Prototype

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a>Opis

Ta usługa inicjuje klienta dla operacji emisji pojedynczej przez skonfigurowanie adresu IP serwera SNTP i Inicjowanie parametrów uruchamiania i limitów czasu usługi SNTP. Obsługuje to zarówno typy adresów IPv4, jak i IPv6.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

- **unicast_time_server** Adres IP serwera SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślnie zainicjowano klienta

- NX_INVALID_PARAMETERS (0x4D) Nieprawidłowa wejściowa niebędąca wskaźnikiem

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Wskaż, czy klient otrzymuje prawidłowe aktualizacje

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a>Opis

Ta usługa wskazuje, czy klient otrzymuje prawidłowe aktualizacje SNTP. Jeśli maksymalny czas przestanie obowiązywać bez prawidłowej aktualizacji lub limitu kolejnych nieprawidłowych aktualizacji, stan odbierania zostanie zwrócony jako FAŁSZ. Należy pamiętać, że klient protokołu SNTP nadal działa i jeśli aplikacja chce ponownie uruchomić klienta SNTP z innym emisją pojedynczą lub serwerem emisji/multiemisji, musi zatrzymać klienta protokołu SNTP przy użyciu usługi *nx_sntp_client_stop* , ponownie zainicjować klienta przy użyciu jednej z zainicjowanych usług z innym serwerem.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP.

- **receive_status** Wskaźnik do wskaźnika, jeśli klient otrzymuje prawidłowe aktualizacje.

### <a name="return-values"></a>Wartości zwrócone

- Klient **NX_SUCCESS** (0x00) pomyślnie otrzymał stan aktualizacji

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Wyślij żądanie emisji pojedynczej bezpośrednio do serwera NTP


### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji bezpośrednie wysyłanie żądania emisji pojedynczej do serwera NTP asynchronicznie z zadania wątku klienta SNTP. Opcja oczekiwania określa czas oczekiwania na odpowiedź. Jeśli to się powiedzie, aplikacja może używać innych usług klienta SNTP do uzyskania najnowszego czasu. Aby uzyskać więcej informacji, zobacz sekcję **żądania asynchronicznej emisji pojedynczej** .

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP.

- **Wait_option** Opcja oczekiwania dla odpowiedzi NTP w taktach czasomierza.

### <a name="return-values"></a>Wartości zwrócone

- Klient **NX_SUCCESS** (0x00) pomyślnie wysyła i odbiera aktualizację emisji pojedynczej

- Wątek klienta **NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) nie został uruchomiony

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi

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

Ta usługa uruchamia klienta w trybie rozgłaszania, w którym będzie czekać na odebranie emisji z serwera SNTP. Jeśli zostanie odebrany prawidłowy komunikat protokołu SNTP, limit czasu klienta protokołu SNTP dla maksymalnego wygaśnięcia bez aktualizacji i liczby kolejnych nieprawidłowych komunikatów odebranych są resetowane. W przypadku przekroczenia jednego z tych limitów klient SNTP ustawia stan serwera na nieprawidłowy, mimo że nadal będzie czekać na otrzymywanie aktualizacji. Aplikacja może sondować zadanie klienta SNTP dla stanu serwera, a jeśli jest nieprawidłowa, Zatrzymaj klienta SNTP i ponownie zainicjuj go przy użyciu innego adresu emisji protokołu SNTP. Może również przełączać się na serwer SNTP emisji pojedynczej.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP.

### <a name="return-values"></a>Wartości zwrócone

- **stan--------rzeczywisty** stan ukończenia

- Klient **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) jest już uruchomiony

- Nie zainicjowano klienta **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01)

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi

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

Ta usługa uruchamia klienta w trybie emisji pojedynczej, w którym okresowo wysyła żądanie emisji pojedynczej do serwera SNTP w celu zaktualizowania czasu. Jeśli zostanie odebrany prawidłowy komunikat SNTP, zostanie zresetowany limit czasu klienta SNTP dla maksymalnego wygaśnięcia bez aktualizacji, początkowy interwał sondowania oraz liczba kolejnych nieprawidłowych komunikatów odebranych. W przypadku przekroczenia jednego z tych limitów klient SNTP ustawia stan serwera na nieprawidłowy, mimo że nadal będzie sondował i czekał na otrzymywanie aktualizacji. Aplikacja może sondować zadanie klienta SNTP dla stanu serwera, a jeśli jest nieprawidłowa, Zatrzymaj klienta SNTP i ponownie zainicjuj go przy użyciu innego adresu SNTP emisji pojedynczej. Może również przełączać się na serwer emisji SNTP.

.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie uruchomił klienta w trybie emisji pojedynczej

- Klient **NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) jest już uruchomiony

- Nie zainicjowano klienta **NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01)

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

- NX_CALLER_ERROR (0x11) Nieprawidłowy obiekt wywołujący usługi


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

Ta usługa ustawia czas lokalny klienta SNTP z czasem wejścia w formacie SNTP, np. sekund i "ułamek", który jest formatem do umieszczania ułamków sekundy w formacie szesnastkowym. Jest on przeznaczony do aktualizowania czasu lokalnego klienta SNTP z niezależnego, na przykład zegara czasu rzeczywistego. Protokół SNTP jest przeznaczony do aktualizacji czasu SNTP, aby zachować czas lokalnego zegara od "dryfing". Aktualizacje czasu serwera SNTP mogą być, ale nie mają być jedynym wejściem do czasu lokalnego klienta SNTP, jeśli na urządzeniu aplikacji nie ma niezależnego czasu.

Tego interfejsu API można również użyć, aby nadać klientowi SNTP czas podstawowy przed uruchomieniem wątku klienta SNTP. Czas lokalny klienta SNTP jest porównywany z otrzymanymi aktualizacjami prawidłowych danych czasu. Po pierwszym odebraniu aktualizacji może wystąpić bardzo duża rozbieżność. W związku z tym istnieje możliwość, że klient SNTP zignoruje niezgodność z pierwszą aktualizacją. W ten sposób klient SNTP można uruchomić bez czasu podstawowego. Czas wejścia można uzyskać od znanych czasów epoki (zwykle dostępnych w Internecie) i są one obliczane jako liczba sekund od 1 stycznia 1900 (do 2036, gdy zostanie rozpoczęte nowe "Epoka").

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

- **sekund** Składnik sekund danych wejściowych czasu

- **ułamek** Składnik podsekund w formacie ułameku SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił czas lokalny

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

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

Ta usługa ustawia wywołanie zwrotne w celu powiadomienia aplikacji, gdy klient SNTP otrzymuje prawidłową aktualizację czasu. Dostarcza rzeczywisty komunikat protokołu SNTP i czas lokalny klienta SNTP (zwykle taki sam) w formacie NTP. Aplikacja może korzystać z danych NTP bezpośrednio lub wywołać *usługę nx_sntp_client_utility_display_date_time* , aby przekonwertować czas na czytelny format.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

- **time_update_cb** Wskaźnik do funkcji wywołania zwrotnego

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił wywołanie zwrotne

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

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

Zatrzymaj wątek klienta SNTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa przerywa wątek klienta SNTP. Zadania wątku klienta SNTP, które są uruchamiane w pętli nieskończonej, wstrzymują wszystkie iteracje w celu wydania kontroli stanu klienta SNTP i zezwalają aplikacjom na wykonywanie wywołań interfejsu API na kliencie SNTP.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr** Wskaźnik do bloku kontroli klienta SNTP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zatrzymano wątek klienta

- **NX_SNTP_CLIENT_NOT_STARTED** (0xDB) wątek klienta SNTP nie został uruchomiony

- NX_PTR_ERROR (0x07) nieprawidłowe dane wejściowe wskaźnika

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a>nx_sntp_client_utility_display_date_time

Konwertowanie czasu NTP na ciąg daty i godziny

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a>Opis

Ta usługa konwertuje czas lokalny klienta SNTP na format daty miesiąca roku i zwraca datę z podanego buforu. NX_SNTP_CURRENT_YEAR nie może być tym samym rokiem co bieżący czas klienta, ale musi być zdefiniowany.

### <a name="input-parameters"></a>Parametry wejściowe

- **client_ptr wskaźnik do klienta SNTP**

- **bufor** Wskaźnik do buforu do przechowywania daty

- **Długość** Rozmiar buforu wejściowego

### <a name="return-values"></a>Wartości zwrócone

- Konwersja **NX_SUCCESS** (0x00)

- **NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) nie NX_SNTP_CURRENT_YEAR zdefiniowany lub nie został określony czas lokalnego klienta

- **NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) niewystarczająca długość buforu


### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a>nx_sntp_client_utility_msecs_to_fraction

Konwertuj milisekundy na składnik datafrakcji NTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a>Opis

Ta usługa konwertuje dane wejściowe w milisekundach na składnik NTP. Jest ona przeznaczona do użycia z aplikacjami, które mają początkowy czas podstawowy dla klienta SNTP, ale nie w formacie sekundy NTP/ułamek. Liczba milisekund musi być mniejsza niż 1000, aby można było wprowadzić prawidłowy ułamek.

### <a name="input-parameters"></a>Parametry wejściowe

- **milisekundy do przekonwertowania**

- **ułamek** Wskaźnik do milisekund przekonwertowanych na ułamek

### <a name="return-values"></a>Wartości zwrócone

- Konwersja **NX_SUCCESS** (0x00)

- Błąd **NX_SNTP_OVERFLOW_ERROR** (0XD32) podczas konwertowania czasu na datę

- NX_SNTP_INVALID_TIME (0xD30) nieprawidłowe dane wejściowe SNTP

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a>nx_sntp_client_utility_usecs_to_fraction

Konwertuj mikrosekundy na składnik część ułamka NTP

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a>Opis

Ta usługa konwertuje mikrosekundy wejściowe na składnik część ułamka NTP. Jest ona przeznaczona do użycia z aplikacjami, które mają początkowy czas podstawowy dla klienta SNTP, ale nie w formacie sekundy NTP/ułamek. Liczba mikrosekund musi być mniejsza niż 1000000, aby można było wprowadzić prawidłowy ułamek.

### <a name="input-parameters"></a>Parametry wejściowe

- **mikrosekundy** Mikrosekundy do przekonwertowania

- **ułamek** Wskaźnik do mikrosekund przekonwertowany na ułamek

### <a name="return-values"></a>Wartości zwrócone

- Konwersja **NX_SUCCESS** (0x00)

- Błąd **NX_SNTP_OVERFLOW_ERROR** (0XD32) podczas konwertowania czasu na datę

- NX_SNTP_INVALID_TIME (0xD30) nieprawidłowe dane wejściowe SNTP

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a>nx_sntp_client_utility_fraction_to_usecs

Konwertuj składnik część ułamka NTP na mikrosekundy

### <a name="prototype"></a>Prototype

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a>Opis

Ta usługa konwertuje wejściowy składnik NTP do mikrosekund.

### <a name="input-parameters"></a>Parametry wejściowe

- **ułamek dziesiętny do przekonwertowania**

- **mikrosekundy** Wskaźnik do ułamka konwertowany na mikrosekundy

### <a name="return-values"></a>Wartości zwrócone

- Konwersja **NX_SUCCESS** (0x00)

- NX_SNTP_INVALID_TIME (0xD30) nieprawidłowe dane wejściowe SNTP

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```