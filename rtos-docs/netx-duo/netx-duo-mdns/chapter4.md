---
title: Rozdział 4 — Opis usług mDNS
description: Ten rozdział zawiera opis wszystkich usług NetX mDNS
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89df0ab5f09be8ad50a27d23bae8b20d71caa0b4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821822"
---
# <a name="chapter-4---description-of-mdns-services"></a>Rozdział 4 — Opis usług mDNS

Ten rozdział zawiera opis wszystkich usług NetX mDNS (wymienionych poniżej).

> [!NOTE]
> W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **NX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone.

## <a name="nx_mdns_create"></a>nx_mdns_create

Tworzenie wystąpienia mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie mDNS dla określonego wystąpienia IP i skojarzonych zasobów. Tworzony jest również wątek do obsługi przychodzących komunikatów mDNS, reagowanie na zapytania i okresowe przesyłanie komunikatów zapytań.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **ip_ptr** Wskaźnik do skojarzonego wystąpienia adresu IP.
- **packet_pool** Wskaźnik do prawidłowej puli pakietów.
- **priorytet** Priorytet wątku mDNS.
- **stack_ptr** Wskaźnik do obszaru stosu dla wątku mDNS
- **stack_size** Rozmiar obszaru stosu.
- **HOST_NAME** Nazwa hosta przypisana do tego węzła.
- **local_service_cache** Miejsce do magazynowania lokalnych usług zarejestrowanych.
- **local_service_cache_size** Rozmiar pamięci podręcznej usługi lokalnej.
- **peer_service_cache** Odebrano miejsce do magazynowania informacji o usłudze
- **peer_service_cache_size** Rozmiar pamięci podręcznej usługi równorzędnej
- **probing_notify** Opcjonalna funkcja wywołania zwrotnego wywołana na końcu operacji sondowania. Powiadamia o tym, czy nazwa hosta (w przypadku włączania usługi mDNS w interfejsie lokalnym), czy nazwa usługi (po zarejestrowaniu usłudze) jest unikatowa.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie utworzył wystąpienie mDNS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a>nx_mdns_delete

Usuwanie wystąpienia programu mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wystąpienie usługi mDNS i zwalnia jego zasoby.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie usunął wystąpienie mDNS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a>nx_mdns_enable

Uruchom usługę mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Opis

Ten interfejs API umożliwia włączenie usługi mDNS w określonym interfejsie fizycznym. Po włączeniu usługi moduł mDNS najpierw sonduje wszystkie unikatowe nazwy usług w sieci przed odpowiedzią na zapytania odebrane w interfejsie.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania wystąpieniem mDNS.
- **interface_index** Indeksowanie do interfejsu, w którym usługa jest włączona

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie włączył usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a>nx_mdns_disable

Wyłącz usługę mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Opis

Ten interfejs API powoduje wyłączenie usługi mDNS w określonym interfejsie fizycznym. Po wyłączeniu usługi Usługa mDNS wysyła komunikaty "pożegnania" dla każdej usługi lokalnej do sieci dołączonej do interfejsu, dzięki czemu węzły sąsiednie zostaną powiadomione.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **interface_index** Indeksowanie do interfejsu, w którym usługa ma zostać wyłączona

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wyłączyła usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a>nx_mdns_cache_notify_set

Instaluje funkcję pełnego powiadamiania pamięci podręcznej mDNS

### <a name="prototype"></a>Prototype

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a>Opis

Ta usługa instaluje funkcję wywołania zwrotnego, która jest wywoływana, gdy lokalna pamięć podręczna lub pamięć podręczna usługi równorzędnej staną się pełne. Gdy pamięć podręczna usługi jest pełna, nie można dodać więcej rekordów zasobów usług mDNS. Należy pamiętać, że pamięć podręczna usługi może stać się pełna w wyniku wewnętrznej fragmentacji, gdy zostaną dodane i usunięte usługi o różnych długościach ciągu. W przypadku odebrania pamięci podręcznej pełnych powiadomień w pamięci podręcznej usługi równorzędnej aplikacja może używać usługi "*nx_mdns_service_cache_clear"* do wymazywania wszystkich wpisów w pamięci podręcznej usługi równorzędnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zainstalował funkcję wywołania zwrotnego powiadomienia pamięci podręcznej mDNS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a>nx_mdns_cache_notify_clear

Wyczyść funkcję pełnego powiadamiania pamięci podręcznej usługi mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Opis

Ta usługa czyści funkcję wywołania zwrotnego powiadomienia pamięci podręcznej usługi przez użytkownika.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wyczyścił funkcję wywołania zwrotnego powiadomienia pamięci podręcznej usługi mDNS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a>nx_mdns_domain_name_set

Ustawia nazwę domeny

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a>Opis

Ta usługa ustawia domyślną nazwę domeny lokalnej. Po utworzeniu wystąpienia programu mDNS domyślna nazwa domeny lokalnej jest ustawiona na wartość ". local". Ten interfejs API umożliwia aplikacji zastąpienie domyślnej nazwy domeny lokalnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **domain_name** Nazwa domeny, która ma zostać użyta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie skonfigurował domenę lokalną.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a>nx_mdns_service_announcement_timing_set

Ustawia parametry czasu dla komunikatów anonsów usługi

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a>Opis

Ta usługa ponownie konfiguruje parametry chronometrażu wykorzystywane przez usługę mDNS podczas wysyłania anonsów usługi. Okres publikacji rozpoczyna się od *t* taktów i może być rozszerzony telescopically z 2 do potęgi współczynnika *k* . Liczba powtórzeń na anonsie to *p*, interwał między każdym powtarzanym anonsem to cykle *interwału* , a liczba okresów anonsu jest max_time. Domyślnie okres początkowy jest ustawiony na 1 sekundę, z k = 1 (okres podwaja się za każdym razem), *p = 1* (bez powtórzenia), retrans_interval = 0 (bez interwału czasu), Period_interval = 0xFFFFFFFF (interwał okresu maksymalnego) i max_time = 3 (liczba anonsów).

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **Liczba** taktów dla okresu początkowego. Wartość domyślna to 100 Takty dla 1 sekundy.
- **Liczba** powtórzeń. Wartość domyślna to 1.
- **TELESCOPIC.** Wartość domyślna to 1.
- **retrans_interval** Liczba taktów oczekiwania przed wysłaniem kolejnych komunikatów powiadomień. Wartość domyślna to 0.
- **period_interval** Liczba znaczników między dwoma okresami anonsu. Wartość domyślna to 0xFFFFFFFF.
- **max_time** Liczba okresów anonsów, które mają być używane w anonsie. Po upływie *max_time* okresy anonsów nie są wysyłane żadne komunikaty o anonsie. Wartość domyślna to 3.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawia wartości chronometrażu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a>nx_mdns_service_add

Dodawanie usługi lokalnej

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a>Opis

Ten interfejs API rejestruje usługę oferowaną przez aplikację. Jeśli flaga *is_unique* jest ustawiona, usługa mDNS sonduje nazwę usługi, aby upewnić się, że jest unikatowa w sieci lokalnej przed rozpoczęciem anonsowania usługi w sieci. *Wystąpienie* jest częścią nazwy usługi. *Usługa* jest częścią nazwy usługi. Na przykład "_http. _tcp" to usługa. Aby opisać usługę z podtypem, obiekt wywołujący musi używać parametru *podtypu* . Na przykład jeśli żądana usługa to "_PRINTER. _sub. _http. _tcp", pole usługi to "_http. _tcp:, a pole podtyp ma wartość" _PRINTER ".

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **wystąpienie** Wskaźnik na nazwę wystąpienia usługi.
- **Usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.
- **priorytet** Priorytet usługi
- **waga** Waga usługi
- **port** Numer portu TCP lub UDP używający usługi
- **tekst** Dodatkowe informacje tekstowe
- **is_unique** Flaga logiczna wskazująca, czy usługa jest udostępniona, czy unikatowa. W przypadku usług zarejestrowanych jako unikatowy usługa mDNS musi sondować usługę w sieci przed rozpoczęciem jej tworzenia.
- **Interface_index** Interfejs fizyczny oferowany przez usługę. W przypadku usługi, która jest oferowana za pomocą dowolnych dołączonych usług, wartość *NX_MDNS_ALL_INTERFACES* jest używana.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zarejestrowała usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a>nx_mdns_service_delete

Usuwanie poprzedniej zarejestrowanej usługi

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a>Opis

Ten interfejs API umożliwia usunięcie poprzedniej zarejestrowanej usługi. Po usunięciu usługi do sieci lokalnej są wysyłane komunikaty "pożegnania", dzięki czemu węzły sąsiednie zostaną powiadomione.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **wystąpienie** Wskaźnik na nazwę wystąpienia usługi.
- **Usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie usunął usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a>nx_mdns_service_one_shot_query

Inicjowanie odnajdywania usługi w jednym zrzucie

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wykonuje jednorazowe zapytanie mDNS. Jeśli określona usługa zostanie znaleziona w pamięci podręcznej usługi równorzędnej, zostanie zwrócone pierwsze wystąpienie. Jeśli żadne usługi nie zostaną znalezione w lokalnej pamięci podręcznej usługi równorzędnej, moduł mDNS wystawia polecenie zapytania i poczeka na odpowiedź. Usługa jest blokowana do momentu odebrania pierwszej odpowiedzi lub przeprowadzenia zapytania.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **wystąpienie** Wskaźnik na nazwę wystąpienia usługi, jeśli ma zastosowanie.
- **Usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie. Aplikacja musi określić typ usługi.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.
- **service_ptr** Wskaźnik podanego przez użytkownika do struktury NX_MDNS_SERVICE, która przechowuje wyniki zapytania.
- **WAIT_OPTION** Ilość czasu (w taktach) oczekiwania na odpowiedź.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie uzyskał informacje o usłudze.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a>nx_mdns_service_continuous_query

Inicjowanie ciągłego odnajdowania usług

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Opis

Ta usługa uruchamia ciągłe zapytanie. Należy pamiętać, że usługa wraca natychmiast. Po wydaniu ciągłego zapytania aplikacja może pobrać rekord usługi przy użyciu *nx_mdns_service_lookup* interfejsu API. Aby zatrzymać ciągłe zapytania, aplikacja może używać interfejsu API *nx_mdns_service_query_stop*

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **wystąpienie** Wskaźnik na nazwę wystąpienia usługi, jeśli ma zastosowanie.
- **Usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie, jeśli ma zastosowanie.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie rozpoczęła zapytanie Kontynuuj.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a>nx_mdns_service_query_stop

Zaniechanie poprzednio wystawionego ciągłego odnajdowania usług

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Opis

Ten interfejs API kończy poprzednie wygenerowane ciągłe odnajdywanie usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **wystąpienie** Wskaźnik na nazwę wystąpienia usługi.
- **Usługa** Wskaźnik do typu usługi mDNS, informacje o podtypie.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zatrzymano zapytanie Kontynuuj.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a>nx_mdns_service_lookup

Pobiera usługę z lokalnej pamięci podręcznej usługi równorzędnej

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyszukuje usługi pasujące do nazwy wystąpienia (jeśli jest podany) i typu usługi w lokalnej pamięci podręcznej usługi równorzędnej. Aplikacja uruchamia wyszukiwanie usługi z *instance_index* ustawiona na zero dla pierwszej usługi w pamięci podręcznej, która jest zgodna z opisem. Aplikacja utrzymuje korzystanie z tej usługi z rosnącą *instance_index* wartością dla dodatkowych usług znalezionych w pamięci podręcznej, aż usługa zwróci *NX_NO_MORE_ENTRIES*, co wskazuje na koniec pamięci podręcznej.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **wystąpienie** Wskaźnik na nazwę wystąpienia usługi, jeśli ma zastosowanie.
- **Usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie, jeśli ma zastosowanie.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma zastosowanie.
- **Instance_index** Numer indeksu do wystąpienia, które ma zostać zwrócone.
- **service_ptr** Wskaźnik podanego przez użytkownika do struktury NX_MDNS_SERVICE, która przechowuje wyniki wyszukiwania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie pobrała usługę
- **NX_NO_MORE_ENTRIES** (0X17) nie znaleziono wpisu usługi o określonym numerze indeksu. Ten kod błędu wskazuje koniec wyszukiwania.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a>nx_mdns_service_ignore_set

Konfiguruje zestaw ignorowanych usług

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a>Opis

Ten interfejs API konfiguruje maskę w celu ignorowania usług określonych przez *service_maską* maskę bitów. Użytkownik może opcjonalnie użyć service_mask, aby wybrać typy usług, które nie mają być buforowane. Lista usług jest definiowana w tabeli *nx_mdns_service_types* w *nxd_mdns. c.* Odpowiednia maska pierwszego typu usługi w nx_mdns_service_types [] jest 0x00000001, maska drugiego typu usługi to 0x00000002 itd.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **service_mask** Typy usług zdefiniowane przez użytkownika do ignorowania. Maska jest 32-bitowym typem ULONG. Każdy bit reprezentuje wpis w tablicy *nx_mdns_service_types* zdefiniowanej przez użytkownika. Jeśli ustawiono bit, odpowiedni typ usługi określony w tablicy *nx_mdns_service_type* nie będzie przechowywany w pamięci podręcznej usługi równorzędnej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie Ustawia maskę ignorowania usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a>nx_mdns_service_notify_set

Konfiguruje funkcję wywołania zwrotnego powiadomienia o zmianie usługi

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a>Opis

Ten interfejs API umożliwia skonfigurowanie funkcji wywołania zwrotnego powiadomienia o zmianie usługi. Ta funkcja wywołania zwrotnego jest wywoływana, gdy usługa oferowana przez inne węzły w sieci zostanie dodana, zmieniona lub nie jest już dostępna. Użytkownik może opcjonalnie użyć service_mask, aby wybrać typy usług, które chcą monitorować. Lista monitorowanych usług jest trwale kodowana w tabeli *nx_mdns_service_types* w *nxd_mdns. c.*

Odpowiednia maska pierwszego typu usługi w nx_mdns_service_types [] jest 0x00000001, maska drugiego typu usługi to 0x00000002 itd.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **service_mask** Zdefiniowane przez użytkownika typy usługi do monitorowania. Maska jest 32-bitowym typem ULONG. Każdy bit reprezentuje wpis w tablicy *nx_mdns_service_types* .
- **service_change_notify** Funkcja wywołania zwrotnego do wywołania, gdy określona usługa zostanie zmieniona. Szczegółowe informacje o usłudze są zwracane w pamięci wskazywanej przez *service_ptr.* Należy zauważyć, że zawartość pamięci jest nieprawidłowa po powrocie z funkcji powiadamiania zwrotnego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zainstalował funkcję wywołania zwrotnego.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a>nx_mdns_service_notify_clear

Wyczyść funkcję wywołania zwrotnego powiadomienia o zmianie usługi

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Opis

Ten interfejs API czyści funkcję wywołania zwrotnego powiadomienia o zmianie usługi i.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS...

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wyczyścił funkcję wywołania zwrotnego.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a>nx_mdns_host_address_get

Pobierz adres hosta

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wykonuje zapytanie mDNS dotyczące adresów IPv4 hosta i IPv6. Jeśli adres określonej nazwy hosta zostanie znaleziony w pamięci podręcznej usługi równorzędnej, zostanie zwrócony adres. Jeśli żaden adres nie zostanie znaleziony w pamięci podręcznej usługi równorzędnej, moduł mDNS wystawia zapytania typu AAAA i i poczeka na odpowiedź. Ten interfejs API blokuje do momentu odebrania odpowiedzi lub przełączenia zapytania.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **HOST_NAME** Wskaźnik na nazwę hosta.
- **ipv4_address** Wskaźnik na adres 4-bajtowy wyrównany do miejsca do magazynowania adresów IPv4. Użytkownik przydziela 4 bajty miejsca na adres IPv4. Adres NX_NULL można przesłać do tego interfejsu API, jeśli aplikacja nie musi pobrać adresu IPv4.
- **ipv6_address** Wskaźnik na adres IPv6 dla miejsca do magazynowania. Użytkownik przydziela 16-bajtowe miejsce dla adresu IPv6. Adres NX_NULL można przesłać do tego interfejsu API, jeśli aplikacja nie musi pobrać adresu IPv6.
- **WAIT_OPTION** Ilość czasu (w taktach) oczekiwania na odpowiedź.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie uzyskał adres hosta.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a>nx_mdns_local_cache_clear

Wymaż wszystkie usługi lokalne

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Opis

Ta usługa czyści wszystkie wpisy w lokalnej pamięci podręcznej usługi po wysłaniu wiadomości do pożegnania.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wymazuje wszystkie wpisy w pamięci podręcznej.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a>nx_mdns_peer_cache_clear

Wymaż wszystkie odnalezione usługi

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Opis

Ta usługa czyści wszystkie wpisy w pamięci podręcznej usługi równorzędnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wymazuje wszystkie wpisy w pamięci podręcznej.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
