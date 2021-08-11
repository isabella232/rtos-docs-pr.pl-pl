---
title: Rozdział 3 — opis Azure RTOS klienta NetX Duo PTP
description: Ten rozdział zawiera opis wszystkich usług klienta NetX Duo PTP w kolejności alfabetycznej.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 686db68181e3712f9f6a09a9f471626eff610fd7f45ec5b83ba56f8b7aa378cc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798014"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a>Rozdział 3 — opis Azure RTOS klienta NetX Duo PTP

Ten rozdział zawiera opis wszystkich usług klienckich NetX Duo PTP (wymienionych poniżej) w kolejności alfabetycznej.

[!NOTE]
> *W sekcji **Wartości** zwracane w poniższych opisach funkcji interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, podczas gdy wartości bez pogrubienia są całkowicie wyłączone.*

## <a name="nx_ptp_client_create"></a>nx_ptp_client_create

Utwórz wystąpienie klienta PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie klienta PTP.

Należy pamiętać, że aplikacja musi najpierw utworzyć wystąpienie adresu IP i pulę pakietów dla klienta PTP w celu przesyłania pakietów. W przypadku puli pakietów aplikacja może używać tej samej puli pakietów w wystąpieniu adresu IP; lub może utworzyć dedykowaną pulę pakietów dla klienta PTP.  Zaletą metody dedykowanej puli pakietów jest użycie małych pakietów (128 bajtów, jeśli jest używany protokół IPv6, lub 108 bajtów tylko dla protokołu IPv4).

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do klienta PTP do utworzenia
* **ip_ptr** Wskaźnik do wystąpienia adresu IP
* **interface_index** Indeks interfejsu sieciowego PTP
* **packet_pool_ptr** Wskaźnik do puli pakietów klienta
* **thread_priority**  Priorytet wątku PTP
* **thread_stack** Wskaźnik do stosu wątków
* **stack_size** Rozmiar stosu wątków
* **clock_callback** Wywołanie zwrotne zegara PTP
* **clock_callback_data** Dane dla wywołania zwrotnego zegara

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0x00) Pomyślnie utworzono klienta
* **NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) Ładunek pakietu jest za mały
* **NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) przy wywołaniu zwrotnym zegara
* **stan** Uzupełnianie stanu wywołań usług NetX Duo i ThreadX
* NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego
* NX_INVALID_INTERFACE (0x4C) Nieprawidłowy interfejs

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a>nx_ptp_client_delete

Usuwa wystąpienie klienta PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wystąpienie klienta PTP.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do klienta PTP do usunięcia

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0x00) Pomyślnie usunięto klienta
* NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a>nx_ptp_client_master_info_get

Pobierz informacje zegara głównego.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a>Opis
Ta usługa pobiera informacje o zegarze głównym. Główny blok sterowania jest przekazywany do aplikacji użytkownika za pośrednictwem funkcji wywołania zwrotnego zdarzeń.

### <a name="input-parameters"></a>Parametry wejściowe
* **master_ptr** Wskaźnik do zegara głównego PTP
* **adres** Adres zegara głównego
* **port_identity** Główny port i tożsamość PTP
* **port_identity_length** Długość portu głównego PTP i tożsamości
* **priority1** Priority1 zegara głównego PTP
* **priority2** Priority2 zegara głównego PTP
* **clock_class** Klasa zegara głównego PTP
* **clock_accuracy** Dokładność zegara głównego PTP
* **clock_variance** Wariancja zegara głównego PTP
* **grandmaster_identity** Tożsamość zegara arcymastera
* **grandmaster_identity_length** Długość tożsamości arcymastera
* **steps_removed** Kroki usunięte z nagłówka PTP
* **time_source** Źródło czasomierza używanego przez zegar arcykapłanowy

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0x00) Pomyślnie pobierz informacje o zegarze głównym
* NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a>nx_ptp_client_packet_timestamp_notify

Powiadom klienta PTP o sygnaturze czasowej pakietu.

### <a name="prototype"></a>Prototype

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a>Opis
Ta usługa powiadamia klienta PTP, że pakiet jest przesyłany ze znacznikiem czasu. Ta usługa jest przeznaczona dla sterownika sieciowego i wywoływana podczas transmitowania pakietu. Sygnatura czasowa jest zwykle generowana przez sprzęt.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do klienta PTP do utworzenia
* **packet_ptr** Wskaźnik do przesyłanego pakietu PTP
* **timestamp_ptr** Wskaźnik do sygnatury czasowej pakietu PTP

### <a name="return-values"></a>Wartości zwrócone
Brak

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a>nx_ptp_client_soft_clock_callback

Implementacja oprogramowania zegara PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a>Opis
Ta funkcja wywołania zwrotnego służy jako symulowane źródło zegara o niskiej rozdzielczości dla PTP. Ta procedura jest dostarczana jako odwołanie i nie można jej używać w środowisku produkcyjnym.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do klienta PTP do utworzenia
* **operacja** Operacja wywołania zwrotnego prawidłowe wartości są zdefiniowane jako:
  * **NX_PTP_CLIENT_CLOCK_INIT** Zaimicjuj zegar.
  * **NX_PTP_CLIENT_CLOCK_SET** Ustaw bieżący znacznik czasu określony przez `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_GET** Zwróć bieżący znacznik czasu do `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Wyodrębnij znacznik czasu z `packet_ptr` do `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Dostosuj bieżący znacznik czasu krótszy niż *1* sekundę.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Oznacz znacznik , który wymaga powiadomienia klienta PTP o `packet_ptr` sygnaturze czasowej, gdy jest przesyłany.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Aktualizowanie czasomierza nie czasomierza. Można ją zignorować za pomocą zegara sprzętowego.
* **time_ptr** Wskaźnik do znacznika czasu.
* **packet_ptr** Wskaźnik do pakietu.
* **callback_data** Wskaźnik do nieprzezroczystych danych wywołania zwrotnego.

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0x00) Pomyślnie
* **NX_PTP_PARAM_ERROR** (0xD03) Nieprawidłowy parametr

### <a name="allowed-from"></a>Dozwolone z
PTP wewnętrzne

### <a name="example"></a>Przykład
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a>nx_ptp_client_start

Uruchom klienta PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a>Opis
Ta usługa uruchamia utworzone wcześniej wystąpienie klienta PTP.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do klienta PTP do utworzenia
* **client_port_identity_ptr** Wskaźnik do portu klienta i tożsamości, może mieć wartość NULL
* **client_port_identity_length** Długość portu i tożsamości klienta. Musi być 0, jeśli client_port_identity_ptr ma wartość NULL lub NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)
* **domena** Domena zegara PTP
* **transport_specific** 4 bity specyficznego dla transportu
* **event_callback** Wywoływana funkcja wywołania zwrotnego w przypadku zdarzenia
* **event_callback_data** Dane dla wywołania zwrotnego zdarzenia

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0x00) Client successfully started
* **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started
* **stan** Uzupełnianie stanu wywołań usług NetX Duo i ThreadX
* NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a>nx_ptp_client_stop

Zatrzymaj klienta PTP.  Po zatrzymaniu klienta PTP nie przetwarza pakietów PTP ani nie przesyła pakietów PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis
Ta usługa zatrzymuje utworzone wcześniej i uruchomione wystąpienie klienta PTP.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do klienta PTP do zatrzymania

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0x00) Client successfully stopped (Klient usługi 0x00) został pomyślnie zatrzymany
* **NX_PTP_CLIENT_NOT_STARTED** (0xD01) Klient nie został uruchomiony
* NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a>nx_ptp_client_sync_info_get

Pobierz informacje o synchronizacji.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a>Opis
Ta usługa pobiera informacje o komunikacie synchronizacji. Blok kontroli synchronizacji jest przekazywany do aplikacji użytkownika za pośrednictwem funkcji wywołania zwrotnego zdarzeń.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do klienta PTP do utworzenia
* **flagi** Flagi w komunikacie synchronizacji
* **utc_offset** Przesunięcie między wartościami TAI i UTC

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0x00) Pomyślnie pobierz informacje o synchronizacji
* NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a>nx_ptp_client_time_get

Pobierz bieżącą czas.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Opis
Ta usługa pobiera bieżącą wartość zegara PTP. Jest on dostępny niezależnie od tego, czy klient PTP jest synchronizowany z zegarem głównym, czy nie.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do klienta PTP do utworzenia
* **time_ptr** Wskaźnik do czasu PTP

### <a name="return-values"></a>Wartości zwrócone
* NX_SUCCESS (0x00) Client successfully created (Pomyślnie utworzono klienta programu **0x00)**
* NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a>nx_ptp_client_time_set

Ustaw bieżącą wartość czasu.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Opis
Ta usługa ustawia bieżącą wartość zegara PTP. Należy go wywołać przed rozpoczęciem klienta PTP.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do klienta PTP do utworzenia
* **time_ptr** Wskaźnik do czasu PTP

### <a name="return-values"></a>Wartości zwrócone
* NX_SUCCESS (0x00) Client successfully created (Pomyślnie utworzono klienta programu **0x00)**
* **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) PTP client already started
* NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a>nx_ptp_client_utility_convert_time_to_date

Przekonwertuj czas PTP na datę i czas UTC.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a>Opis
Ta usługa konwertuje czas PTP na datę i godzina UTC.

### <a name="input-parameters"></a>Parametry wejściowe
* **time_ptr** Wskaźnik do czasu PTP
* **przesunięcie** Drugie przesunięcie ze podpisem w celu dodania czasu PTP
* **date_time_ptr** Wskaźnik do wynikowej daty

### <a name="return-values"></a>Wartości zwrócone
* NX_SUCCESS (0x00) Client successfully created (Pomyślnie utworzono klienta programu **0x00)**
* **Wskaźnik do wynikowej daty** (0xD03) Nieprawidłowy parametr wejściowy
* NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a>nx_ptp_client_utility_time_diff

Różnica dwóch razy PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a>Opis
Ta usługa oblicza różnicę między dwoma czasami PTP.

### <a name="input-parameters"></a>Parametry wejściowe
* **time1_ptr** Wskaźnik do pierwszego czasu PTP
* **time2_ptr** Wskaźnik do drugiego czasu PTP
* **result_ptr** Wskaźnik do wyniku time1-time2

### <a name="return-values"></a>Wartości zwrócone
* NX_SUCCESS (0x00) Client successfully created (Pomyślnie utworzono klienta programu **0x00)**
* NX_PTR_ERROR (0x07) Nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```