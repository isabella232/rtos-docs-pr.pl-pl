---
title: Rozdział 4 — Opis usług mDNS
description: Ten rozdział zawiera opis wszystkich usług NetX mDNS
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6e37698ac6023b4cff6cb4fc05330a73b678ef3d2a813a706c9b821381e123db
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797572"
---
# <a name="chapter-4---description-of-mdns-services"></a>Rozdział 4 — Opis usług mDNS

Ten rozdział zawiera opis wszystkich usług NetX mDNS (wymienionych poniżej).

> [!NOTE]
> W sekcji "Wartości zwracane" w poniższych  opisach interfejsu API definicje interfejsu **NX_DISABLE_ERROR_CHECKING,** które są używane do wyłączania sprawdzania błędów interfejsu API, nie mają wpływu na wartości z pogrubieniem, a wartości bez pogrubienia są całkowicie wyłączone.

## <a name="nx_mdns_create"></a>nx_mdns_create

Tworzenie wystąpienia sieci mDNS

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

Ta usługa tworzy wystąpienie sieci mDNS dla określonego wystąpienia adresu IP i skojarzonych zasobów. Wątek jest również tworzony w celu obsługi przychodzących komunikatów mDNS, odpowiadania na zapytania i okresowego przesyłania komunikatów zapytań.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **ip_ptr** Wskaźnik do skojarzonego wystąpienia adresu IP.
- **packet_pool** Wskaźnik do prawidłowej puli pakietów.
- **priorytet** Priorytet wątku mDNS.
- **stack_ptr** Wskaźnik do obszaru stosu dla wątku mDNS
- **stack_size** Rozmiar obszaru stosu.
- **host_name** Nazwa hosta przypisana do tego węzła.
- **local_service_cache** Storage dla usług zarejestrowanych lokalnie.
- **local_service_cache_size** Rozmiar lokalnej pamięci podręcznej usługi.
- **peer_service_cache** Storage miejsca na odebrane informacje o usłudze
- **peer_service_cache_size** Rozmiar pamięci podręcznej usługi równorzędnej
- **probing_notify** Opcjonalna funkcja wywołania zwrotnego wywoływana na końcu operacji sondowania. Powiadamia ona aplikację, czy nazwa hosta (podczas włączania sieci mDNS w interfejsie lokalnym) lub nazwa usługi (po zarejestrowaniu usługi) jest unikatowa.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie utworzono wystąpienie sieci mDNS.

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

Usuwanie wystąpienia sieci mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wystąpienie sieci mDNS i usuwa jego zasoby.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku kontrolki mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie usunięto wystąpienie sieci mDNS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a>nx_mdns_enable

Uruchamianie usługi mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Opis

Ten interfejs API umożliwia korzystanie z usługi mDNS w określonym interfejsie fizycznym. Po włączeniu usługi moduł mDNS najpierw sonduje wszystkie swoje unikatowe nazwy usług w sieci przed udzieleniem odpowiedzi na zapytania odebrane w interfejsie.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania wystąpienia mDNS.
- **interface_index** Indeksowanie do interfejsu, w którym ma być włączona usługa

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie włączono usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a>nx_mdns_disable

Wyłączanie usługi mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>Opis

Ten interfejs API wyłącza usługę mDNS w określonym interfejsie fizycznym. Po wyłączeniu usługi sieci mDNS wysyłają komunikaty "do odień" dla każdej usługi lokalnej do sieci, która jest dołączona do interfejsu, dzięki czemu sąsiednie węzły są powiadamiane.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **interface_index** Indeksowanie do interfejsu, w którym usługa ma być wyłączona

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie wyłączono usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a>nx_mdns_cache_notify_set

Instaluje funkcję pełnej powiadamiania pamięci podręcznej mDNS

### <a name="prototype"></a>Prototype

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a>Opis

Ta usługa instaluje funkcję wywołania zwrotnego dostarczoną przez użytkownika, która jest wywoływana, gdy lokalna pamięć podręczna usługi lub pamięć podręczna usługi równorzędnej zostanie zapełniona. Gdy pamięć podręczna usługi jest pełna, nie można dodać już rekordu zasobu mDNS. Pamiętaj, że pamięć podręczna usługi może stać się pełna w wyniku fragmentacji wewnętrznej, gdy usługi o różnych długościach ciągów są dodawane i usuwane. Po otrzymaniu pełnego powiadomienia pamięci podręcznej w pamięci podręcznej usługi równorzędnej aplikacja może użyć usługi *"nx_mdns_service_cache_clear",* aby wymazać wszystkie wpisy z pamięci podręcznej usługi równorzędnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku kontrolki mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie zainstalowano funkcję wywołania zwrotnego powiadamiania pamięci podręcznej mDNS.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a>nx_mdns_cache_notify_clear

Wyczyść funkcję pełnej powiadamiania pamięci podręcznej usługi mDNS

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Opis

Ta usługa czyszczy funkcję powiadamiania zwrotnego pamięci podręcznej dostarczanej przez użytkownika.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku kontrolki mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie wyczyszczysz funkcję wywołania zwrotnego powiadamiania pamięci podręcznej usługi mDNS.

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

Ta usługa konfiguruje domyślną nazwę domeny lokalnej. Po utworzeniu wystąpienia sieci mDNS domyślna nazwa domeny lokalnej jest ustawiana na ".local". Ten interfejs API umożliwia aplikacji zastąpienie domyślnej nazwy domeny lokalnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **domain_name** Nazwa domeny, która ma być używana.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie skonfigurowano domenę lokalną.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a>nx_mdns_service_announcement_timing_set

Ustawia parametry chronometrażu dla komunikatów o anonsach usług

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a>Opis

Ta usługa ponownie konfiguruje parametry chronometrażu stosowane przez sieci mDNS podczas wysyłania powiadomień o usłudze. Okres publikowania rozpoczyna *się od t* takt i może być rozszerzany telecznie z 2 do potęgi współczynnika *k.* Liczba powtórzeń na anons wynosi *p*, interwał  między każdym powtórzeniem anonsu to takty interwału, a liczba okresów anonsowania wynosi max_time. Domyślnie początkowy okres jest ustawiony na 1 sekundę, z k = 1 (okres podwaja się za każdym razem), *p = 1* (brak powtórzenia), retrans_interval = 0 (brak interwału czasu), period_interval = 0xFFFFFFFF(maksymalny interwał okresu) i max_time = 3 (liczba anonsów).

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **t** liczba takt dla początkowego okresu. Wartość domyślna to 100 takt na 1 sekundę.
- **p** Liczba powtórzeń. Wartość domyślna to 1.
- **k** Czynnik telegraficzny. Wartość domyślna to 1.
- **retrans_interval** Liczba znaczników oczekiwania przed wysłaniem powtarzających się komunikatów o anonsach. Wartość domyślna to 0.
- **period_interval** Liczba takt między dwoma okresami anonsu. Wartość domyślna to 0xFFFFFFFF.
- **max_time** Liczba okresów anonsów do użycia na użytek anonsu. Po upływie *max_time* okresów anonsów nie są wysyłane żadne komunikaty z anonsami. Wartość domyślna to 3.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie ustawia wartości chronometrażu.

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

Ten interfejs API rejestruje usługę oferowaną przez aplikację. Jeśli *flaga is_unique* ustawiona, usługa mDNS sonduje nazwę usługi, aby upewnić się, że jest unikatowa w sieci lokalnej przed rozpoczęciem ogłaszania usługi w sieci. *Wystąpienie* jest częścią wystąpienia nazwy usługi. Usługa *jest* częścią nazwy usługi. Na przykład "_http._tcp" jest usługą. Aby opisać usługę z podtypem, wywołujący musi użyć *parametru podtypu.* Jeśli na przykład żądana usługa to "_printer._sub._http._tcp", pole usługi to "_http._tcp:, a pole podtypu to "_printer".

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **wystąpienie** Wskaźnik do nazwy wystąpienia usługi.
- **usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma to zastosowanie.
- **priorytet** Priorytet usługi
- **waga** Waga usługi
- **port** Numer portu TCP lub UDP używany przez usługę
- **text (tekst)** Dodatkowe informacje tekstowe
- **is_unique** Flaga logiczna wskazująca, czy usługa jest udostępniona, czy unikatowa. W przypadku usług zarejestrowanych jako unikatowe sieci mDNS muszą sondować usługę w sieci przed rozpoczęciem jej oferowania.
- **Interface_index** Interfejs fizyczny, za pośrednictwem który jest oferowana usługa. W przypadku usługi oferowanej za pośrednictwem dowolnej z dołączonych usług używana jest wartość *NX_MDNS_ALL_INTERFACES* .

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie zarejestrowano usługę.

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

Ten interfejs API usuwa wcześniej zarejestrowaną usługę. Gdy usługa zostanie usunięta, komunikaty "do widzenia" są wysyłane do sieci lokalnej, aby sąsiednie węzły były powiadamiane.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **wystąpienie** Wskaźnik do nazwy wystąpienia usługi.
- **usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma to zastosowanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie usunięto usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a>nx_mdns_service_one_shot_query

Inicjowanie odnajdywania usługi jedno zrzutu ekranu

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wykonuje jednostrzałowe zapytanie mDNS. Jeśli określona usługa zostanie znaleziona w pamięci podręcznej usługi równorzędnej, zwracane jest pierwsze wystąpienie. Jeśli w lokalnej pamięci podręcznej usługi równorzędnej nie zostaną znalezione żadne usługi, moduł mDNS wydaje polecenie zapytania i czeka na odpowiedź. Usługa jest blokowana do momentu, gdy zostanie odebrana pierwsza odpowiedź lub gdy zostanie umysz zapytanie.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **wystąpienie** Wskaźnik do nazwy wystąpienia usługi, jeśli ma to zastosowanie.
- **usługa** Wskaźnik do typu usługi mDNS, z wyłączeniem informacji o podtypie. Aplikacja musi określić typ usługi.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma to zastosowanie.
- **service_ptr** Użytkownik podał wskaźnik NX_MDNS_SERVICE struktury, która przechowuje wyniki zapytania.
- **wait_option** Czas oczekiwania na odpowiedź w taktach.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uzyskano informacje o usłudze.

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

Inicjowanie ciągłego odnajdywania usług

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Opis

Ta usługa uruchamia ciągłe zapytanie. Zwróć uwagę, że usługa natychmiast zwraca dane. Po wydaniu zapytania ciągłego aplikacja może pobrać rekord usługi przy użyciu interfejsu *API* nx_mdns_service_lookup . Aby zatrzymać ciągłe zapytanie, aplikacja może używać interfejsu API *nx_mdns_service_query_stop*

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku kontrolki mDNS.
- **wystąpienie** Wskaźnik do nazwy wystąpienia usługi, jeśli ma to zastosowanie.
- **usługa** Wskaźnik do typu usługi mDNS z wyłączeniem informacji o podtypie, jeśli ma to zastosowanie.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma to zastosowanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie rozpoczęte kontynuuje zapytanie.

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

Zaprzestanie wcześniej wystawionego ciągłego odnajdywania usług

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>Opis

Ten interfejs API kończy poprzednią wystawioną ciągłą odnajdywanie usług.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku kontrolki mDNS.
- **wystąpienie** Wskaźnik do nazwy wystąpienia usługi.
- **usługa** Wskaźnik do typu usługi mDNS, informacje o podtypie.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma to zastosowanie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie zatrzymane kontynuuje zapytanie.

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

Ta usługa wyszukuje usługi zgodne z nazwą wystąpienia (jeśli podano) i typem usługi w lokalnej pamięci podręcznej usługi równorzędnej. Aplikacja musi uruchomić wyszukiwania usługi z *wartością instance_index* ustawioną na zero dla pierwszej usługi w pamięci podręcznej, która odpowiada opisowi. Aplikacja powinna nadal korzystać  z tej usługi wraz instance_index wartością dodatkowych usług znalezionych w pamięci podręcznej, dopóki usługa nie zwróci wartości *NX_NO_MORE_ENTRIES*, która wskazuje koniec pamięci podręcznej.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku kontrolki mDNS.
- **wystąpienie** Wskaźnik do nazwy wystąpienia usługi, jeśli ma to zastosowanie.
- **usługa** Wskaźnik do typu usługi mDNS z wyłączeniem informacji o podtypie, jeśli ma to zastosowanie.
- **podtyp** Wskaźnik do części podtypu usługi mDNS, jeśli ma to zastosowanie.
- **Instance_index** Numer indeksu wystąpienia, które ma zostać zwrócone.
- **service_ptr** Użytkownik podał wskaźnik do NX_MDNS_SERVICE, która przechowuje wyniki wyszukiwania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie pobrano usługę
- **NX_NO_MORE_ENTRIES** (0x17) Nie znaleziono wpisu usługi pod określonym numerem indeksu. Ten kod błędu wskazuje koniec wyszukiwania.

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

Ten interfejs API konfiguruje maskę tak, aby ignorować usługi *określone przez service_mask* bitmask. Użytkownik może opcjonalnie użyć service_mask, aby wybrać typy usług, które nie mają być buforowane. Lista usług jest zdefiniowana w tabeli *nx_mdns_service_types* w *nxd_mdns.c.* Odpowiadająca maska pierwszego typu usługi w nx_mdns_service_types[] jest 0x00000001, maska drugiego typu usługi jest 0x00000002 i tak dalej.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku kontrolki mDNS.
- **service_mask** Zdefiniowane przez użytkownika typy usług do zignorowania. Maska jest 32-bitowym typem ULONG. Każdy bit reprezentuje wpis w zdefiniowanej przez użytkownika *tablicy nx_mdns_service_types* tablicy. Jeśli bit jest ustawiony, odpowiedni typ usługi określony w tablicy *nx_mdns_service_type* nie będzie zapisywany w pamięci podręcznej usługi równorzędnej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie ustawia usługę ignoruj maskę.

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

Konfiguruje funkcję wywołania zwrotnego powiadamiania o zmianie usługi

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a>Opis

Ten interfejs API konfiguruje funkcję wywołania zwrotnego powiadamiania o zmianie usługi. Ta funkcja wywołania zwrotnego jest wywoływana, gdy usługa oferowana przez inne węzły w sieci jest dodawana, zmieniana lub nie jest już dostępna. Użytkownik może opcjonalnie użyć service_mask, aby wybrać typy usług, które chce monitorować. Lista monitorowanych usług jest zakodowana w tabeli nx_mdns_service_types *w* *nxd_mdns.c.*

Odpowiadająca maska pierwszego typu usługi w nx_mdns_service_types[] jest 0x00000001, maska drugiego typu usługi jest 0x00000002 i tak dalej.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku kontrolki mDNS.
- **service_mask** Zdefiniowane przez użytkownika typy usług do monitorowania. Maska jest 32-bitowym typem ULONG. Każdy bit reprezentuje wpis w *tablicy nx_mdns_service_types* tablicy.
- **service_change_notify** Funkcja wywołania zwrotnego, która ma zostać wywołana po zmianie określonej usługi. Szczegółowe informacje o usłudze są zwracane w pamięci wskazywanej przez *service_ptr.* Należy pamiętać, że zawartość w pamięci jest nieprawidłowa po zwróceniu z funkcji wywołania zwrotnego powiadomienia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie zainstalowano funkcję wywołania zwrotnego.

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

Wyczyść funkcję wywołania zwrotnego powiadamiania o zmianie usługi

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Opis

Ten interfejs API umożliwia wyczyszczenie funkcji wywołania zwrotnego powiadamiania o zmianie usługi i funkcji .

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie wyczyszczysz funkcję wywołania zwrotnego.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a>nx_mdns_host_address_get

Uzyskiwanie adresu hosta

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wykonuje zapytanie mDNS na adresach IPv4 i IPv6 hosta. Jeśli adres określonej nazwy hosta zostanie znaleziony w pamięci podręcznej usługi równorzędnej, adres zostanie zwrócony. Jeśli w pamięci podręcznej usługi równorzędnej nie zostanie znaleziony żaden adres, moduł mDNS wysyła zapytania typu A i AAAA i czeka na odpowiedź. Ten interfejs API blokuje dostęp do momentu, gdy zostanie odebrana odpowiedź lub zostanie przeo jej czas.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.
- **host_name** Wskaźnik do nazwy hosta.
- **ipv4_address** Wskaźnik na 4-bajtowy adres wyrównany dla przestrzeni dyskowej adresów IPv4. Użytkownik musi przydzielić 4 bajty miejsca dla adresu IPv4. NX_NULL może zostać przekazany do tego interfejsu API, jeśli aplikacja nie musi pobierać adresu IPv4.
- **ipv6_address** Wskaźnik do wyrównanych 4-bajtowych adresów dla przestrzeni dyskowej adresów IPv6. Użytkownik musi przydzielić 16 bajtów miejsca dla adresu IPv6. NX_NULL może zostać przekazany do tego interfejsu API, jeśli aplikacja nie musi pobierać adresu IPv6.
- **wait_option** Czas oczekiwania na odpowiedź w takt.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie uzyskany adres hosta.

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

Wymazywanie wszystkich usług lokalnych

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyczyści wszystkie wpisy w lokalnej pamięci podręcznej usługi po wysłaniu komunikatu Żegnanie.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie wymazane wszystkie wpisy w pamięci podręcznej.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a>nx_mdns_peer_cache_clear

Wymazywanie wszystkich odnalezionych usług

### <a name="prototype"></a>Prototype

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyczyści wszystkie wpisy w pamięci podręcznej usługi równorzędnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **mdns_ptr** Wskaźnik do bloku sterowania mDNS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie wymazane wszystkie wpisy w pamięci podręcznej.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
