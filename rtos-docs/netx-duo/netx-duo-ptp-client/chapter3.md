---
title: Rozdział 3 — Opis usługi Azure RTO NetX Duo PTP Client Services
description: Ten rozdział zawiera opis wszystkich usług klienta PTP NetX Duo w kolejności alfabetycznej.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821708"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a>Rozdział 3 — Opis usługi Azure RTO NetX Duo PTP Client Services

Ten rozdział zawiera opis wszystkich usług klienta PTP NetX Duo (wymienionych poniżej) w kolejności alfabetycznej.

[!NOTE]
> *W sekcji **wartości zwracane** w poniższych opisach funkcji interfejsu API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.*

## <a name="nx_ptp_client_create"></a>nx_ptp_client_create

Utwórz wystąpienie klienta programu PTP.

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

Ta usługa tworzy wystąpienie klienta programu PTP.

Należy pamiętać, że aplikacja musi najpierw utworzyć wystąpienie IP i pulę pakietów dla klienta protokołu PTP do przesyłania pakietów. W przypadku puli pakietów aplikacja może używać tej samej puli pakietów w wystąpieniu IP. lub można utworzyć dedykowaną pulę pakietów dla klienta PTP.  Rozwiązanie dedykowanej puli pakietów ma zalety używania małych pakietów (128 bajtów pakietów, jeśli używany jest protokół IPv6 lub 108 bajtów tylko dla protokołu IPv4).

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do programu PTP Client do utworzenia
* **ip_ptr** Wskaźnik do wystąpienia adresu IP
* **interface_index** Indeks interfejsu sieciowego PTP
* **packet_pool_ptr** Wskaźnik do puli pakietów klienta
* **thread_priority**  Priorytet wątku PTP
* **thread_stack** Wskaźnik do stosu wątków
* **stack_size** Rozmiar stosu wątków
* **clock_callback** Wywołanie zwrotne zegara PTP
* **clock_callback_data** Dane dla wywołania zwrotnego zegara

### <a name="return-values"></a>Wartości zwrócone
* Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)
* Ładunek pakietu **NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) jest za mały
* Błąd wywołania zwrotnego zegara **NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05)
* **stan** Kończenie stanu NetX Duo i wywołań usługi ThreadX
* NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego
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

Usuwa wystąpienie klienta programu PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wystąpienie klienta programu PTP.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do usunięcia klienta programu PTP

### <a name="return-values"></a>Wartości zwrócone
* Pomyślnie usunięto klienta **NX_SUCCESS** (0x00)
* NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a>nx_ptp_client_master_info_get

Pobierz informacje o zegarze głównym.

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
Ta usługa pobiera informacje o zegarze głównym. Blok kontroli wzorca jest przesyłany do aplikacji użytkownika za pomocą funkcji wywołania zwrotnego zdarzenia.

### <a name="input-parameters"></a>Parametry wejściowe
* **master_ptr** Wskaźnik do zegara wzorca PTP
* **adres** Adres zegara głównego
* **port_identity** Port i tożsamość wzorca PTP
* **port_identity_length** Długość portu i tożsamości wzorca PTP
* **priority1** Priority1 zegara głównego programu PTP
* **priority2** Priority2 zegara głównego programu PTP
* **clock_class** Klasa zegara głównego programu PTP
* **clock_accuracy** Dokładność zegara wzorca PTP
* **clock_variance** WARIANCJA zegara głównego programu PTP
* **grandmaster_identity** Tożsamość zegara Grandmaster
* **grandmaster_identity_length** Długość tożsamości Grandmaster
* **steps_removed** Kroki usunięte z nagłówka PTP
* **time_source** Źródło czasomierza używane przez zegar Grandmaster

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0x00) pomyślnie Pobierz informacje o zegarze głównym
* NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

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

Powiadamiaj klienta PTP o sygnaturze czasowej pakietu.

### <a name="prototype"></a>Prototype

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a>Opis
Ta usługa powiadamia klienta programu PTP o tym, że pakiet jest przesyłany z sygnaturą czasową. Ta usługa jest przeznaczona dla sterownika sieci i wywoływana podczas przesyłania pakietu. Sygnatura czasowa jest zwykle generowana przez sprzęt.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do programu PTP Client do utworzenia
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

Implementacja oprogramowania zegara protokołu PTP.

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
Ta funkcja wywołania zwrotnego służy jako symulowane Źródło zegara niskiej rozdzielczości dla programu PTP. Ta procedura jest udostępniana jako odwołanie i nie może być używana w środowisku produkcyjnym.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do programu PTP Client do utworzenia
* **operacja** Operacja wywołania zwrotnego, prawidłowe wartości są zdefiniowane jako:
  * **NX_PTP_CLIENT_CLOCK_INIT** Zainicjuj zegar.
  * **NX_PTP_CLIENT_CLOCK_SET** Ustaw bieżącą sygnaturę czasową określoną przez `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_GET** Zwróć bieżącą sygnaturę czasową do `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** Wyodrębnij sygnaturę czasową z `packet_ptr` do `time_ptr` .
  * **NX_PTP_CLIENT_CLOCK_ADJUST** Dostosuj bieżącą sygnaturę czasową mniejszą niż *1* sekunda.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** Oznacz, `packet_ptr` które są wymagane do powiadomienia klienta PTP o sygnaturze czasowej podczas przesyłania.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** Aktualizuj czasomierz elastyczny. Może być ignorowany przez zegar sprzętu.
* **time_ptr** Wskaźnik do sygnatury czasowej.
* **packet_ptr** Wskaźnik do pakietu.
* **callback_data** Wskaźnik na nieprzezroczyste dane wywołania zwrotnego.

### <a name="return-values"></a>Wartości zwrócone
* Operacja **NX_SUCCESS** (0x00) zakończyła się pomyślnie
* **NX_PTP_PARAM_ERROR** (0XD03) nieprawidłowy parametr

### <a name="allowed-from"></a>Dozwolone z
Wewnętrzne PTP

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
Ta usługa uruchamia wcześniej utworzone wystąpienie klienta programu PTP.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do programu PTP Client do utworzenia
* **client_port_identity_ptr** Wskaźnik do portu i tożsamości klienta, może mieć wartość NULL
* **client_port_identity_length** Długość portu i tożsamości klienta. Musi mieć wartość 0, jeśli client_port_identity_ptr ma wartość NULL lub NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)
* **domena** Domena zegara PTP
* **transport_specific** 4 bity specyficzne dla transportu
* **event_callback** Wywołana funkcja wywołania zwrotnego dla zdarzenia
* **event_callback_data** Dane wywołania zwrotnego zdarzenia

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0x00) — pomyślnie uruchomiono klienta
* Klient PTP **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) jest już uruchomiony
* **stan** Kończenie stanu NetX Duo i wywołań usługi ThreadX
* NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a>nx_ptp_client_stop

Zatrzymaj klienta PTP.  Po zatrzymaniu klienta programu PTP nie przetwarza on pakietów PTP ani nie przesyła pakietów PTP.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Opis
Ta usługa przerywa poprzednio utworzone i uruchomione wystąpienie klienta programu PTP.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do zatrzymania klienta programu PTP

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0X00) klient został pomyślnie zatrzymany
* Klient **NX_PTP_CLIENT_NOT_STARTED** (0xD01) nie został uruchomiony
* NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

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
Ta usługa pobiera informacje o komunikacie synchronizacji. Blok kontroli synchronizacji jest przesyłany do aplikacji użytkownika za pomocą funkcji wywołania zwrotnego zdarzenia.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do programu PTP Client do utworzenia
* **flagi** Flagi w komunikacie synchronizacji
* **utc_offset** Przesunięcie między TAI i UTC

### <a name="return-values"></a>Wartości zwrócone
* **NX_SUCCESS** (0x00) pomyślnie Pobierz informacje o synchronizacji
* NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

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

Pobierz bieżącą godzinę.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Opis
Ta usługa pobiera bieżącą wartość zegara PTP. Jest on dostępny niezależnie od tego, że klient PTP jest synchronizowany z zegarem głównym.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do programu PTP Client do utworzenia
* **time_ptr** Wskaźnik do czasu PTP

### <a name="return-values"></a>Wartości zwrócone
* Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)
* NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a>nx_ptp_client_time_set

Ustaw bieżącą godzinę.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Opis
Ta usługa ustawia bieżącą wartość zegara PTP. Musi być wywoływana przed uruchomieniem klienta PTP.

### <a name="input-parameters"></a>Parametry wejściowe
* **client_ptr** Wskaźnik do programu PTP Client do utworzenia
* **time_ptr** Wskaźnik do czasu PTP

### <a name="return-values"></a>Wartości zwrócone
* Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)
* Klient PTP **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) jest już uruchomiony
* NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a>nx_ptp_client_utility_convert_time_to_date

Konwertuj czas PTP na datę i godzinę UTC.

### <a name="prototype"></a>Prototype

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a>Opis
Ta usługa konwertuje czas PTP na datę i godzinę UTC.

### <a name="input-parameters"></a>Parametry wejściowe
* **time_ptr** Wskaźnik do czasu PTP
* **przesunięcie** Drugie przesunięcie podpisane w celu dodania czasu PTP
* **date_time_ptr** Wskaźnik do daty wyników

### <a name="return-values"></a>Wartości zwrócone
* Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)
* **Wskaźnik do daty otrzymanej** (0XD03) nieprawidłowy parametr wejściowy
* NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a>nx_ptp_client_utility_time_diff

Dwa razy.

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
* Pomyślnie utworzono klienta **NX_SUCCESS** (0x00)
* NX_PTR_ERROR (0x07) nieprawidłowy parametr wskaźnika wejściowego

### <a name="allowed-from"></a>Dozwolone z
Wątki

### <a name="example"></a>Przykład
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```