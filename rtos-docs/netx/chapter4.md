---
title: Rozdział 4 — Opis usług Azure RTO NetX Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO NetX w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821546"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a>Rozdział 4 — Opis usług Azure RTO NetX Services

Ten rozdział zawiera opis wszystkich usług Azure RTO NetX w porządku alfabetycznym. Nazwy usług są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem. Na przykład wszystkie usługi ARP znajdują się na początku tego rozdziału.

> [!NOTE]
> *Należy pamiętać, że interfejs API usługi BSD-Compatible Socket jest dostępny dla starszego kodu aplikacji, który nie może w pełni korzystać z interfejsu API NetX o wysokiej wydajności. Aby uzyskać więcej informacji na temat interfejsu API BSD-Compatible gniazda, zobacz Dodatek D.*

W sekcji "wartości zwracane" w każdym opisie wartości **pogrubione** nie wpływają na wartość opcji NX_DISABLE_ERROR_CHECKING używanej do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości w trybie niepogrubionym są całkowicie wyłączone. Sekcje "dozwolone od" wskazują, z których można wywołać każdą usługę NetX.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

Unieważnienie wszystkich wpisów dynamicznych w pamięci podręcznej ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa unieważnia wszystkie dynamiczne wpisy ARP znajdujące się obecnie w pamięci podręcznej ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne unieważnienie pamięci podręcznej ARP.
- **NX_NOT_ENABLED** (0X14) ARP nie jest włączona.
- **NX_PTR_ERROR** (0X07) nieprawidłowy adres IP.
- Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set

Ustawianie dynamicznego wpisu ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Opis

Ta usługa przydziela dynamiczny wpis z pamięci podręcznej ARP i konfiguruje określony adres IP na potrzeby mapowania adresów fizycznych. Jeśli określony jest zerowy adres fizyczny, do sieci wysyłane jest rzeczywiste żądanie ARP w celu rozpoznania adresu fizycznego. Należy również zauważyć, że ten wpis zostanie usunięty, jeśli przedawnienie ARP jest aktywne lub jeśli pamięć podręczna ARP jest wyczerpana i jest to najmniej ostatnio używany wpis ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Adres IP do zamapowania.
- **physical_msw** Pierwsze 16 bitów (47-32) adresu fizycznego.
- **physical_lsw** Mniejsza 32 bitów (31-0) adresu fizycznego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie dynamiczny zestaw wpisów ARP.
- **NX_NO_MORE_ENTRIES** (0X17) nie ma więcej wpisów ARP w pamięci podręcznej ARP.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wystąpienia adresu IP.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate, nx_arp_enable,
- nx_arp_gratuitous_send, nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_enable"></a>nx_arp_enable

Włącza protokół ARP (Address Resolution Protocol).

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a>Opis

Ta usługa inicjuje składnik ARP NetX dla określonego wystąpienia IP. Inicjowanie protokołu ARP obejmuje skonfigurowanie pamięci podręcznej ARP i różnych procedur przetwarzania ARP niezbędnych do wysyłania i otrzymywania wiadomości ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **arp_cache_memory** Wskaźnik do obszaru pamięci, w którym ma zostać umieszczona pamięć podręczna ARP.
- **arp_cache_size** Każdy wpis ARP o rozmiarze 52 bajtów, Łączna liczba wpisów ARP, w związku z tym rozmiar podzielony przez 52.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne włączenie protokołu ARP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pamięci podręcznej.
- **NX_SIZE_ERROR** (0x09) podana przez użytkownika pamięć podręczna ARP jest za mała.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_ALREADY_ENABLED** (0X15) ten składnik został już włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_gratuitous_send, nx_arp_hardware_address_find,
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

Wyślij żądanie żądania ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Opis

Ta usługa przechodzi przez wszystkie interfejsy fizyczne, aby przesyłać żądania żądań ARP, o ile adres IP interfejsu jest prawidłowy. Jeśli odpowiedź ARP zostanie następnie odebrana, dostarczona procedura obsługi odpowiedzi jest wywoływana, aby przetworzyć odpowiedź na żądanie w ramach protokołu ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **response_handler** Wskaźnik do funkcji obsługi odpowiedzi. Jeśli podano NX_NULL, odpowiedzi są ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysyłanie bezpłatnego protokołu ARP.
- **NX_NO_PACKET** (0X01) Brak dostępnego pakietu.
- **NX_NOT_ENABLED** (0X14) ARP nie jest włączona.
- **NX_IP_ADDRESS_ERROR** (0X21) bieżący adres IP jest nieprawidłowy.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

Lokalizowanie fizycznego adresu sprzętowego danego adresu IP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a>Opis

Ta usługa próbuje znaleźć fizyczny adres sprzętowy w pamięci podręcznej ARP, która jest skojarzona z podanym adresem IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Adres IP do wyszukania.
- **physical_msw** Wskaźnik do zmiennej w celu zwrócenia pierwszych 16 bitów (47-32) adresu fizycznego.
- **physical_lsw** Wskaźnik do zmiennej zwraca niższą 32 bitów (31-0) adresu fizycznego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne znalezienie adresu sprzętowego ARP.
- W pamięci podręcznej ARP nie znaleziono mapowania **NX_ENTRY_NOT_FOUND** (0x16).
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pamięci.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_info_get"></a>nx_arp_info_get

Pobierz informacje o działaniach ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach ARP dla skojarzonego wystąpienia adresu IP.

*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **arp_requests_sent** Wskaźnik do miejsca docelowego dla łącznej liczby żądań ARP wysyłanych z tego wystąpienia IP.
- **arp_requests_received** Wskaźnik do miejsca docelowego dla łącznej liczby odebranych żądań ARP od sieci.
- **arp_responses_sent** Wskaźnik do miejsca docelowego dla łącznej liczby odpowiedzi ARP wysyłanych z tego wystąpienia IP.
- **arp_responses_received** Wskaźnik do miejsca docelowego dla łącznej odpowiedzi ARP odebranych z sieci.
- **arp_dynamic_entries** Wskaźnik do lokalizacji docelowej dla bieżącej liczby dynamicznych wpisów ARP.
- **arp_static_entries** Wskaźnik do lokalizacji docelowej dla bieżącej liczby statycznych wpisów ARP.
- **arp_aged_entries** Wskaźnik do lokalizacji docelowej łącznej liczby wpisów ARP, które mają przestarzałe i stały się nieprawidłowe.
- **arp_invalid_messages** Wskaźnik do lokalizacji docelowej całkowitej liczby odebranych komunikatów ARP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobranie informacji o ARP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
    &arp_requests_received,
    &arp_responses_sent,
    &arp_responses_received,
    &arp_dynamic_entries,
    &arp_static_entries,
    &arp_aged_entries,
    &arp_invalid_messages);
/* If status is NX_SUCCESS, the ARP information has been stored in
    the supplied variables. */
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_ip_address_find,
- nx_arp_static_entries_delete, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find

Zlokalizuj adres IP przy użyciu adresu fizycznego

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a>Opis

Ta usługa próbuje znaleźć adres IP w pamięci podręcznej ARP, która jest skojarzona z podanym adresem fizycznym.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Wskaźnik do zwracanego adresu IP, jeśli został znaleziony, który został zamapowany.
- **physical_msw** Pierwsze 16 bitów (47-32) adresu fizycznego do wyszukania.
- **physical_lsw** Niższy 32 bitów (31-0) adresu fizycznego do wyszukania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne Znajdowanie adresu IP ARP
- W pamięci podręcznej ARP nie znaleziono mapowania **NX_ENTRY_NOT_FOUND** (0x16).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pamięci.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw i physical_lsw są równe 0.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_static_entries_delete, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete

Usuń wszystkie statyczne wpisy ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wszystkie wpisy statyczne w pamięci podręcznej ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- Wpisy statyczne **NX_SUCCESS** (0x00) są usuwane.
- **NX_PTR_ERROR** (0X07) nieprawidłowy wskaźnik ip_ptr.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entry_create,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create

Tworzenie statycznego adresu IP na potrzeby mapowania sprzętowego w pamięci podręcznej ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Opis

Ta usługa tworzy statyczne mapowanie adresów IP na fizyczne w pamięci podręcznej ARP dla określonego wystąpienia IP. Statyczne wpisy ARP nie podlegają okresowym aktualizacji protokołu ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Adres IP do zamapowania.
- **physical_msw** Pierwsze 16 bitów (47-32) adresu fizycznego do mapowania.
- **physical_lsw** Mniejsza 32 bitów (31-0) adresu fizycznego do mapowania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne utworzenie wpisu statycznego ARP.
- **NX_NO_MORE_ENTRIES** (0X17) nie ma więcej wpisów ARP w pamięci podręcznej ARP.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw i physical_lsw są równe 0.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_delete

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete

Usuń statyczny adres IP do mapowania sprzętowego w pamięci podręcznej ARP


### <a name="prototype"></a>Prototype

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Opis

Ta usługa wyszukuje i usuwa wcześniej utworzone mapowanie statycznego adresu IP na adres fizyczny w pamięci podręcznej ARP dla określonego wystąpienia IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Statyczny adres IP.
- **physical_msw** 16 najważniejszych bitów (47 – 32) adresów fizycznych, które zostały zmapowane statycznie.
- **physical_lsw** Niższy 32 bitów (31-0) adresu fizycznego, który został zamapowany statycznie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie wpisu statycznego ARP.
- W pamięci podręcznej ARP nie znaleziono wpisu statycznego ARP **NX_ENTRY_NOT_FOUND** (0x16).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw i physical_lsw są równe 0.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_gratuitous_send,
- nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create

## <a name="nx_icmp_enable"></a>nx_icmp_enable

Włącz protokół ICMP (Internet Control Message Protocol)

### <a name="prototype"></a>Prototype

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza składnik ICMP dla określonego wystąpienia IP.
Składnik ICMP jest odpowiedzialny za obsługę internetowych komunikatów o błędach i żądań ping i odpowiedzi.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne włączenie protokołu ICMP.
- **NX_ALREADY_ENABLED** (0X15) Protokół ICMP jest już włączony.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a>Zobacz też

- nx_icmp_info_get, nx_icmp_ping

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get

Pobierz informacje o działaniach ICMP

### <a name="prototype"></a>Prototype

```C
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach ICMP dla określonego wystąpienia IP.

*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **pings_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych pakietów ping.
- **ping_timeouts** Wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu polecenia ping.
- **ping_threads_suspended** Wskaźnik do lokalizacji docelowej łącznej liczby wątków zawieszonych w żądaniach ping.
- **ping_responses_received** Wskaźnik do Estination o całkowitej liczbie odebranych odpowiedzi ping.
- **icmp_checksum_errors** Wskaźnik do lokalizacji docelowej łącznej liczby błędów sumy kontrolnej protokołu ICMP.
- **icmp_unhandled_messages** Wskaźnik do Estination całkowitej liczby nieobsłużonych komunikatów ICMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobranie informacji protokołu ICMP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_icmp_enable, nx_icmp_ping

## <a name="nx_icmp_ping"></a>nx_icmp_ping

Wyślij żądanie ping do określonego adresu IP

### <a name="prototype"></a>Prototype

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła żądanie ping do określonego adresu IP i czeka przez określony czas dla komunikatu odpowiedzi na polecenie ping. Jeśli odpowiedź nie zostanie odebrana, zwracany jest błąd. W przeciwnym razie cały komunikat odpowiedzi jest zwracany w zmiennej wskazywanej przez response_ptr.

*Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Adres IP w kolejności bajtów hosta do ping. Wskaźnik danych do obszaru danych dla wiadomości ping.
- **data_size** Liczba bajtów w danych ping
- **response_ptr** Wskaźnik na wskaźnik pakietu, aby przywrócić komunikat odpowiedzi ping w.
- **WAIT_OPTION** Określa czas oczekiwania na odpowiedź na polecenie ping. Opcje oczekiwania są zdefiniowane w następujący sposób:

  - NX_NO_WAIT (0x00000000)
  - NX_WAIT_FOREVER (0xFFFFFFFF)
  - wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne polecenie ping. Wskaźnik komunikatu odpowiedzi został umieszczony w zmiennej wskazywanej przez response_ptr.
- **NX_NO_PACKET** (0X01) nie może przydzielić pakietu żądania ping.
- **NX_OVERFLOW** (0X03) określony obszar danych przekracza domyślny rozmiar pakietu dla tego wystąpienia IP.
- **NX_NO_RESPONSE** (0X29) żądany adres IP nie odpowiedział.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub odpowiedzi.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
    Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
    &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
    address 1.2.3.5 and the response packet is contained in the
    packet pointed to by response_ptr. It should have the same "abcd"
    four bytes of data. */
```

### <a name="see-also"></a>Zobacz też

- nx_icmp_enable, nx_icmp_info_get

## <a name="nx_igmp_enable"></a>nx_igmp_enable

Włącz protokół IGMP (Internet Group Management Protocol)

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza składnik IGMP w określonym wystąpieniu IP.
Składnik IGMP jest odpowiedzialny za zapewnienie wsparcia dla operacji zarządzania grupami multiemisji IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne włączenie protokołu IGMP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_ALREADY_ENABLED** (0X15) ten składnik został już włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a>Zobacz też

- nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get

Pobierz informacje o działaniach IGMP

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach IGMP dla określonego wystąpienia IP.

*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **igmp_reports_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych raportów ICMP.
- **igmp_queries_received** Wskaźnik do miejsca docelowego dla łącznej liczby zapytań odebranych przez router multiemisji.
- **igmp_checksum_errors** Wskaźnik do lokalizacji docelowej łącznej liczby błędów sumy kontrolnej IGMP dla pakietów odebranych.
- **current_groups_joined** Wskaźnik do lokalizacji docelowej bieżącej liczby grup przyłączonych za pomocą tego wystąpienia IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie pobiera informacje o protokole IGMP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_igmp_enable, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join, nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable

Wyłącz sprzężenie zwrotne protokołu IGMP

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza sprzężenie zwrotne protokołu IGMP dla wszystkich kolejnych grup multiemisji przyłączonych.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślne wyłączenie sprzężenia zwrotnego protokołu IGMP.
- **NX_NOT_ENABLED** (0X14) protokół IGMP nie jest włączony.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem lub inicjalizacją.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a>Zobacz też

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

Włączanie sprzężenia zwrotnego IGMP

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza sprzężenie zwrotne protokołu IGMP dla wszystkich kolejnych grup multiemisji przyłączonych.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślne wyłączenie sprzężenia zwrotnego protokołu IGMP.
- **NX_NOT_ENABLED** (0X14) protokół IGMP nie jest włączony.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem lub inicjalizacją.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a>Zobacz też

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join

Dołącz wystąpienie IP do określonej grupy multiemisji za pośrednictwem interfejsu

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa sprzęga wystąpienie IP z określoną grupą multiemisji za pośrednictwem określonego interfejsu sieciowego. Wewnętrzny licznik jest konserwowany, aby śledzić liczbę przypadków, gdy ta sama Grupa została przyłączona. Po dołączeniu do grupy multiemisji składnik IGMP zezwoli na odbieranie pakietów IP z tym adresem grupy za pośrednictwem określonego interfejsu sieciowego, a także zgłaszanie do routerów, do których ten adres IP jest członkiem tej grupy multiemisji. Komunikaty przyłączenia do członkostwa w protokole IGMP, raport i opuszczenie są również wysyłane za pośrednictwem określonego interfejsu sieciowego.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **group_address** Adres grupy multiemisji IP klasy D do przyłączenia w kolejności bajtów hosta.
- **interface_index** Indeks interfejsu dołączonego do wystąpienia NetX.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dołączenie do grupy multiemisji.
- **NX_NO_MORE_ENTRIES** (0X17) nie można przyłączyć więcej grup multiemisji, Przekroczono maksymalną liczbę.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- Indeks urządzenia **NX_INVALID_INTERFACE** (0x4C) wskazuje nieprawidłowy interfejs sieciowy.
- Podany adres grupy multiemisji **NX_IP_ADDRESS_ERROR** (0x21) nie jest prawidłowym adresem klasy D.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0x14) obsługa multiemisji IP nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a>Zobacz też

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

Dołącz wystąpienie adresu IP do określonej grupy multiemisji

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Opis

Ta usługa sprzęga wystąpienie IP z określoną grupą multiemisji. Wewnętrzny licznik jest konserwowany, aby śledzić liczbę przypadków, gdy ta sama Grupa została przyłączona. Sterownik jest poleceniem, aby wysłać raport IGMP, jeśli jest to pierwsze połączenie w sieci wskazujące zamiar hosta do przyłączenia do grupy. Po dołączeniu składnik IGMP zezwoli na odbieranie pakietów IP z tym adresem grupy i raport na routerach, do których ten adres IP jest członkiem tej grupy multiemisji.

> [!NOTE]
> *Aby dołączyć do grupy multiemisji na urządzeniu niebędącym podstawowym, należy użyć **nx_igmp_multicast_interface_join usługi.***

- **Parametry**

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **group_address** Adres grupy multiemisji IP klasy D do przyłączenia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dołączenie do grupy multiemisji.
- **NX_NO_MORE_ENTRIES** (0X17) nie można przyłączyć więcej grup multiemisji, Przekroczono maksymalną liczbę.
- Indeks urządzenia **NX_INVALID_INTERFACE** (0x4C) wskazuje nieprawidłowy interfejs sieciowy.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres grupy adresów IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a>Zobacz też

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

Przyczyna opuszczenia określonej grupy multiemisji przez wystąpienie protokołu IP

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Opis

Ta usługa powoduje, że wystąpienie IP opuszcza określoną grupę multiemisji, jeśli liczba żądań opuszczenia jest zgodna z liczbą żądań dołączenia. W przeciwnym razie wewnętrzna liczba sprzężeń jest po prostu zmniejszana.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **group_address** Grupa multiemisji do opuszczenia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dołączenie do grupy multiemisji.
- Nie znaleziono poprzedniego żądania Join **NX_ENTRY_NOT_FOUND** (0x16).
- Indeks urządzenia **NX_INVALID_INTERFACE** (0x4C) wskazuje nieprawidłowy interfejs sieciowy.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres grupy adresów IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy

Powiadamiaj aplikację, jeśli zmienią się adresy IP


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję powiadamiania aplikacji, która jest wywoływana za każdym razem, gdy adres IP zostanie zmieniony.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **CHANGE_NOTIFY** Wskaźnik na funkcję powiadamiania o zmianie adresu IP. Jeśli ten parametr jest NX_NULL, powiadomienie o zmianie adresu IP jest wyłączone.
- **additional_info** Wskaźnik do opcjonalnych dodatkowych informacji, które są również dostarczane do funkcji powiadomień, gdy adres IP zostanie zmieniony.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne powiadomienie o zmianie adresu IP **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,
- nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_address_get"></a>nx_ip_address_get

Pobieranie adresu IP i maski sieci

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Opis

Ta usługa Pobiera adres IP i maskę podsieci podstawowego interfejsu sieciowego.

* Aby uzyskać informacje na temat urządzenia pomocniczego, Użyj usługi
- **nx_ip_interface_address_get**. *

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Wskaźnik do miejsca docelowego dla adresu IP.
- **network_mask** Wskaźnik do miejsca docelowego dla maski sieci.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie adresu IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub zmiennej Return.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check
- nx_system_initialize

## <a name="nx_ip_address_set"></a>nx_ip_address_set

Ustawianie adresu IP i maski sieci

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP i maskę sieci dla podstawowego interfejsu sieciowego.

*Aby ustawić adres IP i maskę sieci dla urządzenia pomocniczego, użyj **nx_ip_interface_address_set** usługi.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Nowy adres IP.
- **network_mask** Nowa maska sieci.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślny zestaw adresów IP **NX_SUCCESS** (0x00).
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check
- nx_system_initialize

## <a name="nx_ip_create"></a>nx_ip_create

Tworzenie wystąpienia adresu IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a>Opis

Ta usługa tworzy wystąpienie IP przy użyciu adresu IP i sterownika sieci dostarczonego przez użytkownika. Ponadto aplikacja musi dostarczyć wcześniej utworzoną pulę pakietów dla wystąpienia IP, które ma być używane na potrzeby wewnętrznej alokacji pakietów. Należy pamiętać, że podany sterownik sieciowy aplikacji nie jest wywoływany do momentu wykonania wątku tego adresu IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do bloku sterującego, aby utworzyć nowe wystąpienie adresu IP.
- **Nazwa** Nazwa nowego wystąpienia IP.
- **IP_address** Adres IP dla tego nowego wystąpienia IP.
- **network_mask** Maskowanie, aby odróżnić część sieci adresu IP dla podsieci i użycia w ramach wykorzystania pamięci masowej.
- **default_pool** Wskaźnik sterujący blokiem utworzonej wcześniej puli pakietów NetX.
- **ip_network_driver** Sterownik sieciowy dostarczony przez użytkownika używany do wysyłania i odbierania pakietów IP.
- **memory_ptr** Wskaźnik do obszaru pamięci dla obszaru stosu wątku pomocnika IP.
- **memory_size** Liczba bajtów w obszarze pamięci dla stosu wątku pomocnika IP.
- **priorytet** Priorytet wątku pomocnika adresów IP.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślne utworzenie wystąpienia adresu IP.
- Biblioteka NetX **NX_NOT_IMPLEMENTED** (0x4A) jest niepoprawnie skonfigurowana.
- **NX_PTR_ERROR** (0X07) nieprawidłowy adres IP, wskaźnik funkcji sterownika sieci, Pula pakietów lub wskaźnik pamięci.
- **NX_SIZE_ERROR** (0x09) podany rozmiar stosu jest zbyt mały.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_IP_ADDRESS_ERROR** (0x21) podany adres IP jest nieprawidłowy.
- **NX_OPTION_ERROR** (0x21) podany priorytet wątku IP jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check
- nx_system_initialize

## <a name="nx_ip_delete"></a>nx_ip_delete

Usuń poprzednio utworzone wystąpienie adresu IP


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie protokołu IP i zwalnia wszystkie zasoby systemowe należące do wystąpienia IP.

### <a name="parameters"></a>Parametry
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie usunięto adres IP **NX_SUCCESS** (0x00).
- **NX_SOCKETS_BOUND** (0X28) to wystąpienie protokołu IP nadal ma powiązane z nim gniazda UDP lub TCP. Przed usunięciem wystąpienia adresu IP wszystkie gniazda muszą zostać anulowane i usunięte.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check
- nx_system_initialize

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

Wydaj polecenie do sterownika sieciowego

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Opis

Ta usługa udostępnia interfejs bezpośredni do podstawowego sterownika interfejsu sieciowego aplikacji określonego podczas wywołania ***nx_ip_create*** .

Polecenia specyficzne dla aplikacji mogą służyć do podawania wartości liczbowych, które są większe lub równe NX_LINK_USER_COMMAND.

*Aby wydać polecenie dla urządzenia pomocniczego, Użyj usługi **nx_ip_driver_interface_direct_command** .*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **polecenie** Kod polecenia numerycznego. Polecenia standardowe są zdefiniowane w następujący sposób:

- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)

- **return_value_ptr** Wskaźnik do zwrócenia zmiennej w obiekcie wywołującym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne polecenie sterownika sieci.
- **NX_UNHANDLED_COMMAND** (0x44) nieobsłużone lub niezaimplementowane polecenie sterownika sieciowego.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub wartości zwracanej.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy indeks interfejsu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

- **Możliwe przeprowadzenie**

Nie

### <a name="example"></a>Przykład

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command

Wydaj polecenie do sterownika sieciowego

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Opis

Ta usługa udostępnia bezpośrednie polecenie do sterownika urządzenia sieciowego aplikacji w wystąpieniu protokołu IP. Polecenia specyficzne dla aplikacji mogą służyć do podawania wartości liczbowych, które są większe lub równe *NX_LINK_USER_COMMAND*.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **polecenie** Kod polecenia numerycznego. Polecenia standardowe są zdefiniowane w następujący sposób:
- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)
- **interface_index** Indeks interfejsu sieciowego, do którego ma zostać wysłane polecenie.
- **return_value_ptr** Wskaźnik do zwrócenia zmiennej w obiekcie wywołującym.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślne polecenie sterownika sieci.
- **NX_UNHANDLED_COMMAND** (0x44) nieobsłużone lub niezaimplementowane polecenie sterownika sieciowego.
- **NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy indeks interfejsu
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub wartości zwracanej.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;
    status = nx_ip_driver_interface_direct_command(&ip_0,
    NX_LINK_GET_STATUS,
    interface_index,
    &link_status);
/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

Wyłącz przekazywanie pakietów IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza przekazywanie pakietów IP wewnątrz składnika IP NetX. Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wyłączenie przekazywania adresów IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

Włączanie przekazywania pakietów IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia przekazywanie pakietów IP w składniku IP NetX. Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślne włączenie przekazywania adresów IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

Wyłącz fragmentację pakietu IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza funkcję fragmentacji i ponownego składania pakietów IP. W przypadku pakietów, które oczekują na ponowną złożenie, ta usługa zwalnia te pakiety. Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) — wyłączono pomyślne fragmenty adresów IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) fragmentacja IP nie jest włączona w wystąpieniu adresu IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

Włącz fragmentację pakietów IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia fragmentację i remontowanie pakietów IP. Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00), pomyślne włączenie FRAGMENTU adresu IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- Funkcje fragmentacji adresów IP **NX_NOT_ENABLED** (0x14) nie są kompilowane do NetX.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

Ustaw adres IP bramy

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP bramy IP. Cały ruch poza siecią jest kierowany do tej bramy na potrzeby transmisji. Brama musi być bezpośrednio dostępna za pomocą jednego z interfejsów sieciowych.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Adres IP bramy.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślny zbiór adresów IP bramy.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wystąpienia adresu IP.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątek

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete

## <a name="nx_ip_info_get"></a>nx_ip_info_get

Pobierz informacje o działaniach IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach IP dla określonego wystąpienia IP.

*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_total_packets_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych pakietów IP.
- **ip_total_bytes_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych bajtów.
- **ip_total_packets_received** Wskaźnik do lokalizacji docelowej całkowitej liczby pakietów odbioru adresów IP.
- **ip_total_bytes_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych bajtów IP.
- **ip_invalid_packets** Wskaźnik do lokalizacji docelowej całkowitej liczby nieprawidłowych pakietów IP.
- **ip_receive_packets_dropped** Wskaźnik do lokalizacji docelowej całkowitej liczby porzuconych pakietów odebranych.
- **ip_receive_checksum_errors** Wskaźnik do lokalizacji docelowej łącznej liczby błędów sumy kontrolnej w pakietach odbierania.
- **ip_send_packets_dropped** Wskaźnik do lokalizacji docelowej całkowitej liczby porzuconych pakietów do wysłania.
- **ip_total_fragments_sent** Wskaźnik do lokalizacji docelowej łącznej liczby wysłanych fragmentów.
- **ip_total_fragments_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych fragmentów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie informacji o adresie IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Retrieve IP information from previously created IP
Instance 0. */
status = nx_ip_info_get(&ip_0,
    &ip_total_packets_sent,
    &ip_total_bytes_sent,
    &ip_total_packets_received,
    &ip_total_bytes_received,
    &ip_invalid_packets,
    &ip_receive_packets_dropped,
    &ip_receive_checksum_errors,
    &ip_send_packets_dropped,
    &ip_total_fragments_sent,
    &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get

Pobieranie adresu IP interfejsu

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a>Opis

Ta usługa Pobiera adres IP określonego interfejsu sieciowego.

*Określone urządzenie, jeśli nie urządzenie podstawowe, musi być wcześniej dołączone do wystąpienia IP.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **interface_index** Indeks interfejsu, taka sama jak wartość indeksu do interfejsu sieciowego dołączonego do wystąpienia protokołu IP.
- **IP_address** Wskaźnik do miejsca docelowego dla adresu IP interfejsu urządzenia.
- **network_mask** Wskaźnik do miejsca docelowego dla maski sieci interfejsu urządzenia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie adresu IP.
- **NX_INVALID_INTERFACE** (0X4C) określony interfejs sieciowy jest nieprawidłowy.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_set, nx_ip_interface_attach,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set

Ustaw adres IP interfejsu i maskę sieci

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP i maskę sieci dla określonego interfejsu IP.

*Określony interfejs musi być wcześniej dołączony do wystąpienia IP.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **interface_index** Indeks interfejsu dołączonego do wystąpienia NetX.
- **IP_address** Nowy adres IP interfejsu sieciowego.
- **network_mask** Nowa maska sieci interfejsu.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślny zestaw adresów IP **NX_SUCCESS** (0x00).
- **NX_INVALID_INTERFACE** (0X4C) określony interfejs sieciowy jest nieprawidłowy.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get, nx_ip_interface_attach,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach

Dołącz interfejs sieciowy do wystąpienia protokołu IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a>Opis

Ta usługa dodaje fizyczny interfejs sieciowy do interfejsu IP. Należy zauważyć, że wystąpienie IP jest tworzone przy użyciu interfejsu podstawowego, więc każdy dodatkowy interfejs jest pomocniczy dla interfejsu podstawowego. Łączna liczba interfejsów sieciowych dołączonych do wystąpienia IP (łącznie z interfejsem podstawowym) nie może przekroczyć **NX_MAX_PHYSICAL_INTERFACES**.

Jeśli wątek IP nie został jeszcze uruchomiony, interfejsy pomocnicze zostaną zainicjowane w ramach procesu uruchamiania wątku IP, który inicjuje wszystkie interfejsy fizyczne.

Jeśli wątek IP nie jest jeszcze uruchomiony, interfejs pomocniczy jest inicjowany w ramach usługi ***nx_ip_interface_attach*** .

*ip_ptr musi wskazywać prawidłową strukturę adresu IP NetX.*

- *Należy skonfigurować **NX_MAX_PHYSICAL_INTERFACES** dla liczby interfejsów sieciowych dla wystąpienia protokołu IP. Wartość domyślna to 1.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **INTERFACE_NAME** Wskaźnik do ciągu nazwy interfejsu.
- **IP_address** Adres IP urządzenia w kolejności bajtów hosta.
- **network_mask** Maska sieci urządzenia w kolejności bajtów hosta.
- **ip_link_driver** Sterownik Ethernet dla interfejsu.

### <a name="return-values"></a>Wartości zwrócone

- Wpis **NX_SUCCESS** (0x00) jest dodawany do statycznej tabeli routingu.
- **NX_NO_MORE_ENTRIES** (0X17) Maksymalna liczba interfejsów.
- Przekroczono **NX_MAX_PHYSICAL_INTERFACES** .
- **NX_DUPLICATED_ENTRY** (0x52) podany adres IP jest już używany w tym wystąpieniu adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowe dane wejściowe adresu IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Attach secondary device for device IP address 192.168.1.68 with
    the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
    IP_ADDRESS(192,168,1,68),
    0xFFFFFF00UL,
    nx_etherDriver);
/* If status is NX_SUCCESS the interface was successfully added to
    the IP instance interface table. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_info_get, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get

Pobierz parametry interfejsu sieciowego


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o parametrach sieci dla określonego interfejsu sieciowego. Wszystkie dane są pobierane w kolejności bajtów hosta.

*ip_ptr musi wskazywać prawidłową strukturę adresu IP NetX. Określony interfejs, jeśli nie jest interfejsem podstawowym, musi być wcześniej dołączony do wystąpienia IP.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **interface_index** Indeks określający interfejs sieciowy.
- **INTERFACE_NAME** Wskaźnik do buforu, który zawiera nazwę interfejsu sieciowego.
- **IP_address** Wskaźnik do lokalizacji docelowej dla adresu IP interfejsu.
- **network_mask** Wskaźnik do miejsca docelowego dla maski sieci.
- **mtu_size** Wskaźnik do miejsca docelowego dla maksymalnej jednostki transferu dla tego interfejsu.
- **physical_address_msw** Wskaźnik do miejsca docelowego dla pierwszych 16 bitów adresu MAC urządzenia.
- **physical_address_lsw** Wskaźnik do miejsca docelowego dla niższych 32 bitów adresu MAC urządzenia.


### <a name="return-values"></a>Wartości zwrócone
- Uzyskano informacje o interfejsie **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.
- **NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy wskaźnik adresu IP.
- Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Retrieve interface parameters for the specified interface (index
    1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1

status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
    &name_ptr, &ip_address,
    &network_mask,
    &mtu_size,
    &physical_address_msw,
    &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
    successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_status_check,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check

Sprawdź stan wystąpienia adresu IP


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa sprawdza i opcjonalnie czeka na określony stan interfejsu sieciowego utworzonego wcześniej wystąpienia adresu IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **interface_index** Numer indeksu interfejsu
- **needed_status** Żądany stan adresu IP, zdefiniowany w postaci mapy bitowej, w następujący sposób:
    - NX_IP_INITIALIZE_DONE (0x0001)
    - NX_IP_ADDRESS_RESOLVED (0x0002)
    - NX_IP_LINK_ENABLED (0x0004)
    - NX_IP_ARP_ENABLED (0x0008)
    - NX_IP_UDP_ENABLED (0x0010)
    - NX_IP_TCP_ENABLED (0x0020)
    - NX_IP_IGMP_ENABLED (0x0040)
    - NX_IP_RARP_COMPLETE (0x0080)
    - NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **actual_status** Wskaźnik do miejsca docelowego rzeczywistego zestawu bitów.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądane bity stanu są niedostępne. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - NX_NO_WAIT (0x00000000)
    - NX_WAIT_FOREVER (0xFFFFFFFF)
    - wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- Sprawdzanie stanu IP **NX_SUCCESS** (0x00) powiodło się.
- Żądanie stanu **NX_NOT_SUCCESSFUL** (0x43) nie było spełnione w określonym limicie czasu.
- Wskaźnik IP **NX_PTR_ERROR** (0x07) ma wartość lub jest nieprawidłowy lub rzeczywisty wskaźnik stanu jest nieprawidłowy.
- **NX_OPTION_ERROR** (0X0a) Nieprawidłowa opcja stanu.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_INVALID_INTERFACE** (0x4C) Interface_index jest poza zakresem. lub interfejs jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_info_get,
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set

Ustaw funkcję wywołania zwrotnego powiadomienia o zmianie stanu łącza

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a>Opis

Ta usługa umożliwia skonfigurowanie funkcji wywołania zwrotnego powiadomienia o zmianie stanu łącza. Procedura *link_status_change_notify* podana przez użytkownika jest wywoływana, gdy zostanie zmieniony stan podstawowego lub pomocniczego interfejsu (na przykład adres IP jest zmieniany). Jeśli *link_status_change_notify* ma wartość null, funkcja wywołania zwrotnego powiadomienia o zmianie stanu łącza jest wyłączona.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **link_status_change_notify** Funkcja wywołania zwrotnego dostarczonego przez użytkownika, która ma być wywoływana po zmianie interfejsu fizycznego.


### <a name="return-values"></a>Wartości zwrócone

- Pomyślne ustawienie **NX_SUCCESS** (0x00)
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP lub Nowy wskaźnik adresu fizycznego
- Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.


### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get, nx_ip_interface_address_set,
- nx_ip_interface_attach, nx_ip_interface_info_get,
- nx_ip_interface_status_check

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable

Wyłącz wysyłanie/otrzymywanie pakietów pierwotnych


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza przekazywanie i odbieranie nieprzetworzonych pakietów IP dla tego wystąpienia IP. Jeśli usługa pakietów RAW była wcześniej włączona, a w kolejce odbierania istnieją pakiety RAW, ta usługa zwolni wszystkie Odebrane pakiety pierwotne.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wyłączono pakiet pierwotny IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable

Włącz przetwarzanie pakietów nieprzetworzonych


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia przekazywanie i odbieranie nieprzetworzonych pakietów IP dla tego wystąpienia IP. Przychodzące pakiety TCP, UDP, ICMP i IGMP są nadal przetwarzane przez NetX. Pakiety z nieznanymi typami protokołów warstwy wyższej są przetwarzane przez nieprzetworzoną procedurę odbierania pakietów.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne włączenie pakietów pierwotnych adresów IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_interface_send"></a>nx_ip_raw_packet_interface_send

Wyślij pakiet Raw IP za poorednictwem określonego interfejsu sieciowego

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet pierwotnego adresu IP do docelowego adresu IP przy użyciu określonego lokalnego adresu IP jako adresu źródłowego i za pośrednictwem skojarzonego interfejsu sieciowego. Należy zauważyć, że ta procedura wraca natychmiast, a tym samym nie wiadomo, czy pakiet IP został faktycznie wysłany. Sterownik sieciowy będzie odpowiedzialny za wydanie pakietu, gdy transmisja zostanie zakończona. Ta usługa różni się od innych usług, ponieważ nie ma możliwości znajomości, czy pakiet został faktycznie wysłany. Może on zostać utracony przez Internet.

*Należy pamiętać, że przetwarzanie Raw IP musi być włączone.*

*Ta usługa jest podobna do **nx_ip_raw_packet_send**, z tą różnicą, że ta usługa umożliwia aplikacji wysyłanie pakietów pierwotnych adresów IP z określonych interfejsów fizycznych.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego zadania IP.
- **packet_ptr** Wskaźnik do pakietu do przesłania.
- **destination_ip** Adres IP do wysłania pakietu.
- **address_index** Indeks adresu interfejsu, dla którego ma zostać wysłany pakiet.
- **Type_of_Service** Typ usługi dla pakietu.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie przesłano pakiet **NX_SUCCESS** (0x00).
- **NX_IP_ADDRESS_ERROR** (0X21) nie jest dostępny odpowiedni interfejs wychodzący.
- **NX_NOT_ENABLED** (0x14) przetwarzanie pakietów Raw IP nie jest włączone.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.
- **NX_OPTION_ERROR** (0x0A) określono nieprawidłowy typ usługi.
- **NX_OVERFLOW** (0X03) Nieprawidłowy wskaźnik dołączania do pakietu.
- **NX_UNDERFLOW** (0X02) Nieprawidłowy wskaźnik dołączania do pakietu.
- **NX_INVALID_INTERFACE** (0x4C) określono nieprawidłowy indeks interfejsu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive

Odbierz pakiet pierwotnego adresu IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa odbiera pakiet Raw IP od określonego wystąpienia IP. Jeśli istnieją pakiety IP w kolejce odbierania pakietów nieprzetworzonych, pierwszy (najstarszy) pakiet jest zwracany do obiektu wywołującego. W przeciwnym razie, jeśli żaden pakiet nie jest dostępny, obiekt wywołujący może zawiesić się zgodnie z opcją oczekiwania.

*Jeśli NX_SUCCESS, jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **packet_ptr** Wskaźnik do wskaźnika, aby umieścić odebrany pakiet pierwotnego adresu IP w programie.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli nie ma dostępnych pakietów pierwotnych adresów IP. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) odbieranie nieprzetworzonych pakietów IP.
- **NX_NO_PACKET** (0X01) Brak dostępnego pakietu.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pakietu zwrotnego.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send

Wyślij pakiet Raw IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a>Opis

Ta usługa wysyła pakiet Raw IP do docelowego adresu IP. Należy zauważyć, że ta procedura wraca natychmiast i dlatego nie wiadomo, czy pakiet IP został faktycznie wysłany. Sterownik sieciowy będzie odpowiedzialny za wydanie pakietu, gdy transmisja zostanie zakończona.

W przypadku systemu wielodostępnego NetX używa docelowego adresu IP do znalezienia odpowiedniego interfejsu sieciowego i używa adresu IP interfejsu jako adresu źródłowego. Jeśli docelowy adres IP jest emisji lub multiemisji, używany jest pierwszy prawidłowy interfejs. Aplikacje używają ***nx_ip_raw_packet_interface_send*** w tym przypadku.

*Jeśli błąd nie zostanie zwrócony, aplikacja nie powinna zwolnić pakietu po tym wywołaniu. Wykonanie tej operacji spowoduje nieprzewidywalne wyniki, ponieważ sterownik sieciowy zwolni pakiet po przekazaniu.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **packet_ptr** Wskaźnik na pakiet Raw IP do wysłania.
- **destination_ip** Docelowy adres IP, który może być określonym adresem IP hosta, emisją sieci, pętlą wewnętrzną lub adresem multiemisji.
- **Type_of_Service** Definiuje typ usługi do transmisji, wartości prawne są następujące:
- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie zainicjowano wysyłanie pakietów pierwotnych adresów IP.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.
- Funkcja Raw IP **NX_NOT_ENABLED** (0x14) nie jest włączona.
- **NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ usługi.
- **NX_UNDERFLOW** (0X02) nie ma wystarczającej ilości miejsca do dołączania nagłówka IP do pakietu.
- Wskaźnik dołączania pakietu **NX_OVERFLOW** (0x03) jest nieprawidłowy.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pakietu.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,
- nx_ip_raw_packet_receive, nx_ip_raw_packet_send,
- nx_ip_raw_packet_interface_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add

Dodawanie trasy statycznej do tabeli routingu

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a>Opis

Ta usługa dodaje wpis do statycznej tabeli routingu. Należy pamiętać, że adres *next_hop* musi być bezpośrednio dostępny z jednego z lokalnych urządzeń sieciowych.

*Należy zauważyć, że ip_ptr musi wskazywać prawidłową strukturę IP NetX, a Biblioteka NetX musi być skompilowana przy użyciu NX_ENABLE_IP_STATIC_ROUTING zdefiniowanej do korzystania z tej usługi. Domyślnie NetX jest zbudowany bez zdefiniowanego NX_ENABLE_IP_STATIC_ROUTING.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **network_address** Docelowy adres sieciowy w kolejności bajtów hosta
- **net_mask** Docelowa maska sieci w kolejności bajtów hosta
- **next_hop** Adres następnego skoku dla sieci docelowej w kolejności bajtów hosta

### <a name="return-values"></a>Wartości zwrócone

- Wpis **NX_SUCCESS** (0x00) jest dodawany do statycznej tabeli routingu.
- Tabela routingu statycznego **NX_OVERFLOW** (0x03) jest pełna.
- **NX_NOT_SUPPORTED** (0X4B) Ta funkcja nie jest skompilowana w programie.
- **NX_IP_ADDRESS_ERROR** (0X21) następnym przeskokiem nie jest bezpośrednio dostępny za pośrednictwem interfejsów lokalnych.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_PTR_ERROR** (0X07) nieprawidłowy wskaźnik ip_ptr.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete

Usuń trasę statyczną z tabeli routingu

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a>Opis

Ta usługa usuwa wpis z statycznej tabeli routingu.

*Należy zauważyć, że ip_ptr musi wskazywać prawidłową strukturę IP NetX, a Biblioteka NetX musi być skompilowana przy użyciu NX_ENABLE_IP_STATIC_ROUTING zdefiniowanej do korzystania z tej usługi. Domyślnie NetX jest zbudowany bez zdefiniowanego NX_ENABLE_IP_STATIC_ROUTING.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **network_address** Docelowy adres sieciowy w kolejności bajtów hosta.
- **net_mask** Docelowa maska sieci w kolejności bajtów hosta.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add

## <a name="nx_ip_status_check"></a>nx_ip_status_check

Sprawdź stan wystąpienia adresu IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa sprawdza i opcjonalnie czeka na określony stan podstawowego interfejsu sieciowego utworzonego wcześniej wystąpienia adresu IP. Aby uzyskać stan w interfejsach pomocniczych, aplikacje używają ***nx_ip_interface_status_check usługi.***

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **needed_status** Żądany stan adresu IP, zdefiniowany w postaci mapy bitowej, w następujący sposób:
- NX_IP_INITIALIZE_DONE (0x0001)
- NX_IP_ADDRESS_RESOLVED (0x0002)
- NX_IP_LINK_ENABLED (0x0004)
- NX_IP_ARP_ENABLED (0x0008)
- NX_IP_UDP_ENABLED (0x0010)
- NX_IP_TCP_ENABLED (0x0020)
- NX_IP_IGMP_ENABLED (0x0040)
- NX_IP_RARP_COMPLETE (0x0080)
- NX_IP_INTERFACE_LINK_ENABLED (0x0100)
- **actual_status** Wskaźnik do miejsca docelowego rzeczywistego zestawu bitów.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądane bity stanu są niedostępne. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- Sprawdzanie stanu IP **NX_SUCCESS** (0x00) powiodło się.
- Żądanie stanu **NX_NOT_SUCCESSFUL** (0x43) nie było spełnione w określonym limicie czasu.
- Wskaźnik IP **NX_PTR_ERROR** (0x07) ma wartość lub jest nieprawidłowy lub rzeczywisty wskaźnik stanu jest nieprawidłowy.
- **NX_OPTION_ERROR** (0X0a) Nieprawidłowa opcja stanu.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize

## <a name="nx_packet_allocate"></a>nx_packet_allocate

Przydziel pakiet z określonej puli

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa przydziela pakiet z określonej puli i dostosowuje wskaźnik dołączania w pakiecie zgodnie z typem określonego pakietu. Jeśli pakiet nie jest dostępny, usługa zawiesza się zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów.
- **packet_ptr** Wskaźnik do wskaźnika przydzieloną wskaźnik pakietu.
- **packet_type** Definiuje typ żądanego pakietu. Zobacz sekcję "pule pakietów" na stronie 49 w rozdziale 3, aby zapoznać się z listą obsługiwanych typów pakietów.
- **WAIT_OPTION** Definiuje czas oczekiwania w taktach, jeśli w puli pakietów nie ma dostępnych pakietów. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna alokacja pakietu **NX_SUCCESS** (0x00).
- **NX_NO_PACKET** (0X01) Brak dostępnego pakietu.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.
- **NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ pakietu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa Pula lub wskaźnik powrotu pakietu.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowa opcja oczekiwania z niewątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR (sterowniki sieciowe aplikacji). Opcja oczekiwania musi być NX_NO_WAIT, gdy jest używana w trybie ISR lub w kontekście czasomierza.

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy

Kopiuj pakiet

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa kopiuje informacje z dostarczonego pakietu do jednego lub kilku nowych pakietów, które są przydzielono z dostarczonej puli pakietów. Jeśli to się powiedzie, wskaźnik do nowego pakietu jest zwracany w miejscu docelowym wskazywanym przez **new_packet_ptr**.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik na pakiet źródłowy.
- **new_packet_ptr** Wskaźnik do miejsca docelowego, do którego ma zostać zwrócony wskaźnik do nowej kopii pakietu.
- **pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów, która jest używana do przydzielenia jednego lub większej liczby pakietów do kopiowania.
- **WAIT_OPTION** Definiuje, w jaki sposób usługa czeka, jeśli nie ma dostępnych pakietów. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone
- Pomyślna kopia pakietu **NX_SUCCESS** (0x00).
- Pakiet **NX_NO_PACKET** (0x01) nie jest dostępny do kopiowania.
- **NX_INVALID_PACKET** (0X12) pusty pakiet źródłowy lub kopiowanie nie powiodło się.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa Pula, pakiet lub wskaźnik docelowy.
- **NX_UNDERFLOW** (0X02) Nieprawidłowy wskaźnik dołączania do pakietu.
- **NX_OVERFLOW** (0X03) Nieprawidłowy wskaźnik dołączania pakietu.
- **NX_CALLER_ERROR** (0x11) opcja oczekiwania została określona w inicjalizacji lub w ramach procedury ISR.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append

Dołącz dane do końca pakietu

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa dołącza dane na końcu określonego pakietu. Dostarczony obszar danych jest kopiowany do pakietu. Jeśli jest za mało dostępnej pamięci, a funkcja pakiet łańcucha jest włączona, co najmniej jeden pakiet zostanie przydzielony do spełnienia żądania. Jeśli funkcja pakietu łańcucha nie jest włączona, zostanie zwrócona *NX_SIZE_ERROR* .

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik pakietu.
- **data_start** Wskaźnik na początek obszaru danych użytkownika do dołączenia do pakietu.
- **data_size** Rozmiar obszaru danych użytkownika.
- **pool_ptr** Wskaźnik do puli pakietów, z której ma zostać przydzielony inny pakiet, jeśli w bieżącym pakiecie nie ma wystarczającej ilości miejsca.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli nie ma dostępnych pakietów. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnego dołączenia do pakietu.
- **NX_NO_PACKET** (0X01) Brak dostępnego pakietu.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie *tx_thread_wait_abort*.
- Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.
- Wskaźnik prefiksu **NX_UNDERFLOW** (0x02) jest mniejszy niż początek ładunku.
- **NX_OVERFLOW** (0x03) dołączany wskaźnik jest większy niż koniec ładunku.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa Pula, pakiet lub wskaźnik danych.
- **NX_SIZE_ERROR** (0X09) Nieprawidłowy rozmiar danych.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowa opcja oczekiwania z niewątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR (sterowniki sieciowe aplikacji)

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset

Wyodrębnij dane z pakietu za pośrednictwem przesunięcia

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a>Opis

Ta usługa kopiuje dane z pakietu NetX (lub łańcucha pakietów), rozpoczynając od określonego przesunięcia od wskaźnika dołączania pakietu o określonym rozmiarze w bajtach do określonego buforu. Liczba bajtów w rzeczywistości kopiowanych jest zwracana w *bytes_copied.* Ta usługa nie usuwa danych z pakietu ani nie dostosowuje wskaźnika dołączania ani innych informacji o stanie wewnętrznym.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu do wyodrębnienia
- **przesunięcie** Przesunięcie od bieżącego wskaźnika dołączania.
- **buffer_start** Wskaźnik do początku zapisu bufora
- **BUFFER_LENGTH** Liczba bajtów do skopiowania
- **bytes_copied** Liczba bajtów rzeczywiście skopiowanych

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna kopia pakietu **NX_SUCCESS** (0x00)
- **NX_PACKET_OFFSET_ERROR** (0x53) podano nieprawidłową wartość przesunięcia
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik pakietu lub wskaźnik buforu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve

Pobieranie danych z pakietu

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a>Opis

Ta usługa kopiuje dane z dostarczonego pakietu do podanego buforu. Rzeczywista liczba skopiowanych bajtów jest zwracana w miejscu docelowym wskazywanym przez **bytes_copied**.

Należy zauważyć, że ta usługa nie zmienia wewnętrznego stanu pakietu. Pobierane dane są nadal dostępne w pakiecie.

*Bufor docelowy musi być wystarczająco duży, aby można było przechowywać zawartość pakietu. W przeciwnym razie pamięć zostanie uszkodzona, powodując nieprzewidywalne wyniki.*

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik na pakiet źródłowy.
- **buffer_start** Wskaźnik na początek obszaru bufora.
- **bytes_copied** Wskaźnik do miejsca docelowego dla liczby kopiowanych bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobranie danych pakietu.
- **NX_INVALID_PACKET** (0X12) nieprawidłowy pakiet.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik skopiowanego pakietu, uruchomienia buforu lub bajtów.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_length_get,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get

Pobierz długość danych pakietu

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a>Opis

Ta usługa Pobiera długość danych w określonym pakiecie.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu.
- **Długość** Wartość docelowa dla długości pakietu.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create

Utwórz pulę pakietów w określonym obszarze pamięci

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy pulę pakietów o określonym rozmiarze pakietu w obszarze pamięci dostarczonym przez użytkownika.

### <a name="parameters"></a>Parametry

- **pool_ptr** Wskaźnik do bloku kontroli puli pakietów.
- **Nazwa** Wskaźnik do nazwy aplikacji dla puli pakietów.
- **payload_size** Liczba bajtów w każdym pakiecie w puli. Ta wartość musi być równa co najmniej 40 bajtów i musi być również niewidoczna przez 4.
- **memory_ptr** Wskaźnik do obszaru pamięci, w którym ma zostać umieszczona Pula pakietów. Wskaźnik powinien być wyrównany na granicy ULONG.
- **memory_size** Rozmiar obszaru pamięci puli.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie utworzono pulę pakietów.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik puli lub pamięci.
- **NX_SIZE_ERROR** (0X09) Nieprawidłowy rozmiar bloku lub pamięci.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

Usuń wcześniej utworzoną pulę pakietów

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzoną pulę pakietów. NetX sprawdza, czy wszystkie wątki są aktualnie zawieszone w pakietach w puli pakietów i czyści zawieszenie.

### <a name="parameters"></a>Parametry

- **pool_ptr** Wskaźnik bloku kontroli puli pakietów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie puli pakietów.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik puli.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get

Pobieranie informacji o puli pakietów

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o określonej puli pakietów.

*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*

### <a name="parameters"></a>Parametry

- **pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów.
- **total_packets** Wskaźnik do miejsca docelowego dla łącznej liczby pakietów w puli.
- **free_packets** Wskaźnik do miejsca docelowego dla łącznej liczby aktualnie bezpłatnych pakietów.
- **empty_pool_requests** Wskaźnik do lokalizacji docelowej łącznej liczby żądań alokacji, gdy pula była pusta.
- **empty_pool_suspensions** Wskaźnik do lokalizacji docelowej łącznej liczby pustych zawieszeń puli.
- **invalid_packet_releases** Wskaźnik do lokalizacji docelowej całkowitej liczby nieprawidłowych wersji pakietu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pobieranie informacji o puli pakietów powiodło się.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
    &total_packets,
    &free_packets,
    &empty_pool_requests,
    &empty_pool_suspensions,
    &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
    retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release

Zwolnij wcześniej przydzieloną pakietów

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwalnia pakiet, w tym wszystkie dodatkowe pakiety powiązane z określonym pakietem. Jeśli inny wątek jest blokowany w alokacji pakietów, otrzymuje pakiet i został wznowiony.

*Aplikacja musi uniemożliwiać zwolnienie pakietu więcej niż raz, ponieważ takie działanie spowoduje nieprzewidywalne wyniki.*

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik pakietu.


### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślne wydanie pakietu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik pakietu.
- Wskaźnik prefiksu **NX_UNDERFLOW** (0x02) jest mniejszy niż początek ładunku.
- **NX_OVERFLOW** (0x03) dołączany wskaźnik jest większy niż koniec ładunku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR (sterowniki sieciowe aplikacji)

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_pool_info_get, nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

Zwolnij przesłany pakiet

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

W przypadku pakietów innych niż TCP ta usługa zwalnia przesyłany pakiet, w tym wszystkie dodatkowe pakiety połączone z określonym pakietem. Jeśli inny wątek jest blokowany w alokacji pakietów, otrzymuje pakiet i został wznowiony. W przypadku przesyłanego pakietu TCP pakiet jest oznaczany jako przesyłany, ale nie jest uwalniany do momentu potwierdzenia pakietu. Ta usługa jest zwykle wywoływana ze sterownika sieci aplikacji po przesłaniu pakietu.

*Sterownik sieciowy powinien usunąć nagłówek nośnika fizycznego i dostosować długość pakietu przed wywołaniem tej usługi.*

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik pakietu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślna transmisja pakietów.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik pakietu.
- Wskaźnik prefiksu **NX_UNDERFLOW** (0x02) jest mniejszy niż początek ładunku.
- **NX_OVERFLOW** (0x03) dołączany wskaźnik jest większy niż koniec ładunku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, sterowniki sieciowe aplikacji (w tym procedury ISR)

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_pool_info_get, nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable

Wyłącz protokół odwrotnego rozpoznawania adresów (RARP)

### <a name="prototype"></a>Prototype

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza składnik RARP elementu NetX dla określonego wystąpienia IP. W przypadku systemu wielodomowego ta usługa wyłącza RARP na wszystkich interfejsach.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) POMYŚLNE wyłączenie RARP.
- Nie włączono **NX_NOT_ENABLED** (0X14) RARP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a>Zobacz też

- nx_rarp_enable, nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable

Włącz protokół odwrotnego rozpoznawania adresów (RARP)

### <a name="prototype"></a>Prototype

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza składnik RARP NetX dla określonego wystąpienia IP. Składniki RARP przeszukują wszystkie podłączone interfejsy sieciowe dla zerowego adresu IP. Zerowy adres IP wskazuje, że interfejs nie ma jeszcze przypisywania adresów IP. RARP próbuje rozpoznać adres IP, włączając proces RARP w tym interfejsie.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) POMYŚLNE włączenie RARP.
- Adres IP **NX_IP_ADDRESS_ERROR** (0x21) jest już prawidłowy.
- **NX_ALREADY_ENABLED** (0X15) RARP został już włączony.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a>Zobacz też

- nx_rarp_disable, nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get

Pobierz informacje o działaniach RARP

### <a name="prototype"></a>Prototype

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach RARP dla określonego wystąpienia IP.

*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **rarp_requests_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych żądań RARP.
- **rarp_responses_received** Wskaźnik do miejsca docelowego dla łącznej liczby odebranych odpowiedzi RARP.
- **rarp_invalid_messages** Wskaźnik do lokalizacji docelowej całkowitej liczby nieprawidłowych komunikatów.


### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślnie RARP pobieranie informacji.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_rarp_disable, nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize

Zainicjuj system NetX

### <a name="prototype"></a>Prototype

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a>Opis

Ta usługa inicjuje podstawowe zasoby systemowe NetX w przygotowaniu do użycia. Powinien być wywoływany przez aplikację podczas inicjowania i przed innymi wywołaniami NetX.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

Brak

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

Powiąż gniazdo TCP klienta z portem TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wiąże wcześniej utworzone gniazdo klienta TCP z określonym portem TCP. Prawidłowy zakres TCP Sockets należy do zakresu od 0 do 0xFFFF. Jeśli określony port TCP jest niedostępny, usługa zawiesza się zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **port** Numer portu do powiązania (od 1 do 0xFFFF). Jeśli numer portu to NX_ANY_PORT (0x0000), wystąpienie protokołu IP wyszuka następny bezpłatny port i użyje go do powiązania.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli port jest już powiązany z innym gniazdem. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnego powiązania gniazda.
- **NX_ALREADY_BOUND** (0X22) to gniazdo jest już powiązane z innym portem TCP.
- Port **NX_PORT_UNAVAILABLE** (0x23) jest już powiązany z innym gniazdem.
- **NX_NO_FREE_PORTS** (0X45) brak wolnego portu.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie *tx_thread_wait_abort*.
- **NX_INVALID_PORT** (0X46) nieprawidłowy port.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

Połącz gniazdo TCP klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa łączy wcześniej utworzone i powiązane gniazdo klienta TCP z portem określonego serwera. Prawidłowe porty serwera TCP mieszczą się w zakresie od 0 do 0xFFFF. Jeśli połączenie nie zakończy się natychmiast, usługa zawiesza się zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **server_IP** Adres IP serwera.
- **SERVER_PORT** Numer portu serwera, z którym ma zostać nawiązane połączenie (od 1 do 0xFFFF).
- **WAIT_OPTION** Definiuje sposób zachowania usługi podczas ustanawiania połączenia. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnego nawiązania połączenia z gniazdem.
- Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane.
- Gniazdo **NX_NOT_CLOSED** (0x35) nie jest w stanie zamkniętym.
- **NX_IN_PROGRESS** (0X37) nie określono oczekiwania, próba połączenia jest w toku.
- **NX_INVALID_INTERFACE** (0x4C) podano nieprawidłowy interfejs.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP serwera.
- **NX_INVALID_PORT** (0X46) nieprawidłowy port.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

Pobieranie numeru portu powiązanego z gniazdem TCP klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a>Opis

Ta usługa Pobiera numer portu skojarzony z gniazdem, który jest przydatny do znajdowania portu przydzielonego przez NetX w sytuacjach, w których NX_ANY_PORT został określony w momencie powiązania gniazda.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **port_ptr** Wskaźnik do miejsca docelowego dla numeru portu powrotu. Prawidłowe numery portów to (od 1 do 0xFFFF).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnego powiązania gniazda.
- **NX_NOT_BOUND** (0X24) to gniazdo nie jest powiązane z portem.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda lub zwracany przez port wskaźnik.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

Usuń powiązanie gniazda klienta TCP z portu TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwalnia powiązanie między gniazdem klienta TCP i portem TCP. Jeśli istnieją inne wątki oczekujące na powiązanie innego gniazda z tym samym numerem portu, pierwszy zawieszony wątek zostanie powiązany z tym portem.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) odpinanie gniazda zakończone powodzeniem.
- Gniazdo **NX_NOT_BOUND** (0x24) nie zostało powiązane z żadnym portem.
- Gniazdo **NX_NOT_CLOSED** (0x35) nie zostało odłączone.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_enable"></a>nx_tcp_enable

Włącz składnik TCP elementu NetX

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza składnik Transmission Control Protocol (TCP) NetX. Po włączeniu połączenia TCP mogą być nawiązywane przez aplikację.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne włączenie protokołu TCP.
- **NX_ALREADY_ENABLED** (0X15) TCP jest już włączony.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

Znajdź następny dostępny port TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a>Opis

Ta usługa próbuje zlokalizować bezpłatny port TCP (niepowiązany), rozpoczynając od portu dostarczonego przez aplikację. Logika wyszukiwania zostanie zawinięty, jeśli wyszukiwanie nastąpi do osiągnięcia maksymalnej wartości maksymalnego portu. Jeśli wyszukiwanie zakończyło się pomyślnie, port wolny jest zwracany w zmiennej wskazywanej przez *free_port_ptr*.

*Ta usługa może być wywoływana z innego wątku i ma ten sam port. Aby uniknąć tego warunku wyścigu, aplikacja może chcieć umieścić tę usługę i rzeczywiste powiązanie gniazda klienta w ramach ochrony obiektu mutex.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **port** Numer portu, aby rozpocząć wyszukiwanie (od 1 do 0xFFFF).
- **free_port_ptr** Wskaźnik na wartość zwrotną wolnego portu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne znalezienie bezpłatnego portu.
- **NX_NO_FREE_PORTS** (0X45) nie znaleziono wolnych portów.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.
- **NX_INVALID_PORT** (0x46) określony numer portu jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get

Pobierz informacje o działaniach TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach TCP dla określonego wystąpienia IP.

*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **tcp_packets_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych pakietów TCP.
- **tcp_bytes_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych bajtów TCP.
- **tcp_packets_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych pakietów TCP.
- **tcp_bytes_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych bajtów TCP.
- **tcp_invalid_packets** Wskaźnik do lokalizacji docelowej całkowitej liczby nieprawidłowych pakietów TCP.
- **tcp_receive_packets_dropped** Wskaźnik do lokalizacji docelowej całkowitej liczby porzuconych pakietów TCP odbioru.
- **tcp_checksum_errors** Wskaźnik do lokalizacji docelowej całkowitej liczby pakietów TCP z błędami sumy kontrolnej.
- **tcp_connections** Wskaźnik do lokalizacji docelowej łącznej liczby połączeń TCP.
- **tcp_disconnections** Wskaźnik do lokalizacji docelowej łącznej liczby odniesień protokołu TCP.
- **tcp_connections_dropped** Wskaźnik do lokalizacji docelowej całkowitej liczby porzuconych połączeń TCP.
- **tcp_retransmit_packets** Wskaźnik do lokalizacji docelowej całkowitej liczby przesłanych pakietów TCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie informacji TCP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
status = nx_tcp_info_get(&ip_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_invalid_packets,
    &tcp_receive_packets_dropped,
    &tcp_checksum_errors,
    &tcp_connections,
    &tcp_disconnections
    &tcp_connections_dropped,
    &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

Zaakceptuj połączenie TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa akceptuje (lub przygotowuje do akceptowania) żądanie połączenia gniazda klienta TCP dla portu, który został wcześniej skonfigurowany do nasłuchiwania. Ta usługa może być wywoływana natychmiast po wywołaniu przez aplikację nasłuchiwania lub ponownego nasłuchiwania albo gdy wywoływana jest procedura wywołania zwrotnego Listen, gdy połączenie z klientem jest rzeczywiście obecne. Jeśli połączenie nie może być od razu ustanowione, usługa zawiesza się zgodnie z podaną opcją oczekiwania.

*Aplikacja musi wywoływać **nx_tcp_server_socket_unaccept** , gdy połączenie nie jest już potrzebne do usunięcia powiązania gniazda serwera z portem serwera.*

*Procedury wywołania zwrotnego aplikacji są wywoływane z wewnątrz wątku pomocnika IP.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do bloku sterowania gniazda serwera TCP.
- **WAIT_OPTION** Definiuje sposób zachowania usługi podczas ustanawiania połączenia. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)


### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślne zaakceptowanie gniazda serwera TCP (połączenie pasywne).
- **NX_NOT_LISTEN_STATE** (0x36) dostarczony gniazdo serwera nie jest w stanie nasłuchiwania.
- **NX_IN_PROGRESS** (0X37) nie określono oczekiwania, próba połączenia jest w toku.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie *tx_thread_wait_abort*.
- Błąd wskaźnika gniazda **NX_PTR_ERROR** (0x07).
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;
    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
                message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
            again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen

Włącz nasłuchiwanie połączenia klienta na porcie TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a>Opis

Ta usługa umożliwia nasłuchiwanie żądania połączenia klienta na określonym porcie TCP. Po odebraniu żądania połączenia z klientem podane gniazdo serwera jest powiązane z określonym portem i wywoływana funkcja wywołania zwrotnego nasłuchiwania.

Przetwarzanie procedury wywołania zwrotnego Listen jest całkowicie do aplikacji. Może on zawierać logikę do wznowienia wątku aplikacji, który następnie wykonuje operację akceptacji. Jeśli aplikacja ma już zawieszony wątek przy akceptowaniu przetwarzania dla tego gniazda, procedura wywołania zwrotnego odbiornika może nie być wymagana.

Jeśli aplikacja chce obsługiwać dodatkowe połączenia klientów na tym samym porcie, ***nx_tcp_server_socket_relisten*** musi zostać wywołana z dostępnym gniazdem (gniazdo w stanie zamkniętym) dla następnego połączenia. Do momentu wywołania usługi ponownego nasłuchiwania dodatkowe połączenia klienckie są umieszczane w kolejce. Po przekroczeniu maksymalnej głębokości kolejki żądanie najstarszego połączenia zostanie porzucone na rzecz kolejkowania nowego żądania połączenia. Maksymalna głębokość kolejki jest określona przez tę usługę.

*Procedury wywołania zwrotnego aplikacji są wywoływane z wątku pomocnika wewnętrznego adresu IP.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **port** Numer portu, na którym nasłuchuje nasłuchiwanie (od 1 do 0xFFFF).
- **socket_ptr** Wskaźnik do gniazda, który ma być używany w połączeniu.
- **listen_queue_size** Liczba żądań połączenia klienta, które można umieścić w kolejce.
- **listen_callback** Funkcja aplikacji do wywołania po odebraniu połączenia. Jeśli określono wartość NULL, funkcja wywołania zwrotnego Listen jest wyłączona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne włączenie nasłuchiwania portu TCP.
- **NX_MAX_LISTEN** (0X33) nie ma więcej dostępnych struktur żądań nasłuchiwania. Stała NX_MAX_LISTEN_REQUESTS w nx_api. h definiuje liczbę aktywnych żądań nasłuchiwania.
- **NX_NOT_CLOSED** (0x35) dostarczony gniazdo serwera nie jest w stanie zamkniętym.
- **NX_ALREADY_BOUND** (0x22) dostarczony gniazdo serwera jest już powiązany z portem.
- **NX_DUPLICATE_LISTEN** (0X34) istnieje już aktywne żądanie nasłuchiwania dla tego portu.
- **NX_INVALID_PORT** (0x46) określono nieprawidłowy port.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket.
        This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created
        and the link is enabled "my_pool" packet pool has already
        been created.
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
        Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

    /* Wait for 200 ticks for the client socket connection
        to complete. */
    status = nx_tcp_server_socket_accept(&server_socket, 200);

    /* Check for a successful connection. */
    if (status == NX_SUCCESS)
    {
        /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
        nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
            NX_WAIT_FOREVER);

        /* Place "Hello_and_Goodbye" in the packet. */
        nx_packet_data_append(my_packet, "Hello_and_Goodbye",
            sizeof("Hello_and_Goodbye"),
            &my_pool,
            NX_WAIT_FOREVER);

        /* Send "Hello_and_Goodbye" to client. */
        nx_tcp_socket_send(&server_socket, my_packet, 200);

        /* Check for an error. */
        if (status)
        {
            /* Error, release the packet. */
            nx_packet_release(my_packet);
        }
        /* Now disconnect the server socket from the client. */
        nx_tcp_socket_disconnect(&server_socket, 200);
    }

    /* Unaccept the server socket. Note that unaccept is called
        even if disconnect or accept fails. */
    nx_tcp_server_socket_unaccept(&server_socket);

    /* Setup server socket for listening with this socket
    again. */
    nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
}

/* We are now done so unlisten on server port 12. */
nx_tcp_server_socket_unlisten(&my_ip, 12);

/* Delete the server socket. */
nx_tcp_socket_delete(&server_socket);
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

Ponowne nasłuchiwanie połączenia klienta na porcie TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa jest wywoływana po odebraniu połączenia na porcie, który został wcześniej skonfigurowany do nasłuchiwania. Głównym celem tej usługi jest udostępnienie nowego gniazda serwera dla następnego połączenia z klientem. Jeśli żądanie połączenia jest kolejkowane, połączenie zostanie przetworzone natychmiast w trakcie tego wywołania usługi.

*Ta sama procedura wywołania zwrotnego określona przez oryginalne żądanie Listen jest również wywoływana, gdy istnieje połączenie dla tego nowego gniazda serwera.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **port** Numer portu do ponownego nasłuchiwania (od 1 do 0xFFFF).
- **socket_ptr** Gniazdo do użycia dla następnego połączenia z klientem.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślne ponowne nasłuchiwanie portu TCP.
- **NX_NOT_CLOSED** (0x35) dostarczony gniazdo serwera nie jest w stanie zamkniętym.
- **NX_ALREADY_BOUND** (0x22) dostarczony gniazdo serwera jest już powiązany z portem.
- **NX_INVALID_RELISTEN** (0X47) istnieje już prawidłowy wskaźnik gniazda dla tego portu lub określony port nie ma aktywnego żądania listen.
- **NX_CONNECTION_PENDING** (0X48) taka sama jak NX_SUCCESS, z wyjątkiem tego, że wystąpiło żądanie połączenia w kolejce i zostało przetworzone w trakcie tego wywołania.
- **NX_INVALID_PORT** (0x46) określono nieprawidłowy port.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wywołania zwrotnego adresu IP lub nasłuchiwania.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
    }

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
    "port_12_semaphore" has already been created with an initial
        count of 0.
        "my_ip" has already been created and the link is enabled.
        "my_pool" packet pool has already been created. */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);
    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
        complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is
        called even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
        again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

Usuń skojarzenie gniazda z portem nasłuchiwania

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa skojarzenie między tym gniazdem serwera i określonym portem serwera. Aplikacja musi wywołać tę usługę po rozwiązaniu lub po niepomyślnym wywołaniu.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej instalacyjnego wystąpienia gniazda serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne nieakceptowanie gniazda serwera.
- Gniazdo serwera **NX_NOT_LISTEN_STATE** (0x36) jest w niewłaściwym stanie i prawdopodobnie nie jest odłączone.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
        */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request
            is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet,
                "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called even
            if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten

Wyłącz nasłuchiwanie połączenia klienta na porcie TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a>Opis

Ta usługa wyłącza nasłuchiwanie żądania połączenia klienta na określonym porcie TCP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **port** Liczba portów do wyłączenia nasłuchiwania (od 0 do 0xFFFF).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — wyłączanie nasłuchiwania protokołu TCP.
- Nasłuchiwanie **NX_ENTRY_NOT_FOUND** (0x16) nie zostało włączone dla określonego portu.
- **NX_INVALID_PORT** (0x46) określono nieprawidłowy port.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request is
            present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"), &my_pool,
                NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }
            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }
        /* Unaccept the server socket. Note that unaccept is called even if
        disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available

Pobiera liczbę bajtów dostępnych do pobrania

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Opis

Ta usługa uzyskuje liczbę bajtów dostępnych do pobrania w określonym gnieździe TCP. Należy pamiętać, że gniazdo TCP musi już być połączone.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego i połączonego gniazda TCP.
- **bytes_available** Wskaźnik do miejsca docelowego dla dostępnych bajtów.

### <a name="return-values"></a>Wartości zwrócone

- Usługa **NX_SUCCESS** (0x00) została wykonana pomyślnie. Liczba bajtów dostępnych do odczytu jest zwracana do obiektu wywołującego.
- Gniazdo **NX_NOT_CONNECTED** (0x38) nie jest w stanie połączonym.
- **NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.
- **NX_NOT_ENABLED** (0X14) TCP nie jest włączona.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

Utwórz klienta TCP lub gniazdo serwera

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa tworzy gniazdo klienta TCP lub serwera dla określonego wystąpienia IP.

*Procedury wywołania zwrotnego aplikacji są wywoływane z wątku skojarzonego z tym wystąpieniem adresu IP.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **socket_ptr** Wskaźnik do nowego bloku sterowania gniazdem TCP.
- **Nazwa** Nazwa aplikacji dla tego gniazda TCP.
- **Type_of_Service** Definiuje typ usługi do transmisji, wartości prawne są następujące:

- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)

- **fragment**  Określa, czy jest dozwolone fragmentacja adresów IP. Jeśli określono NX_FRAGMENT_OKAY (0x0), jest dozwolone fragmentacja adresów IP. Jeśli określono NX_DONT_FRAGMENT (0x4000), fragmentacja adresów IP jest wyłączona.
- **time_to_live** Określa 8-bitową wartość, która definiuje liczbę routerów, które ten pakiet może przekazać przed wyrzucaniem. Wartość domyślna jest określana przez NX_IP_TIME_TO_LIVE.
- **window_size** Określa maksymalną dozwoloną liczbę bajtów w kolejce odbierania dla tego gniazda
- **urgent_data_callback** Funkcja aplikacji, która jest wywoływana za każdym razem, gdy w strumieniu odbioru zostanie wykryte pilne dane. Jeśli ta wartość jest NX_NULL, pilne dane zostaną zignorowane.
- **disconnect_callback** Funkcja aplikacji, która jest wywoływana za każdym razem, gdy łącznik zostanie wystawiony przez gniazdo na drugim końcu połączenia. Jeśli ta wartość jest NX_NULL, funkcja odłączania wywołania zwrotnego jest wyłączona.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślnie utworzono gniazdo klienta TCP.
- **NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ usługi, fragment, nieprawidłowy rozmiar okna lub opcja czasu tolive.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Create a TCP client socket on the previously created IP instance,
    with normal delivery, IP fragmentation enabled, 0x80 time to
    live, a 200-byte receive window, no urgent callback routine, and
    the "client_disconnect" routine to handle disconnection initiated
    from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
    "Client Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY,
    0x80, 200, NX_NULL
    client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
    to be bound. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

Usuń gniazdo TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone gniazdo TCP. Jeśli gniazdo jest nadal powiązane lub połączone, usługa zwraca kod błędu.

### <a name="parameters"></a>Parametry

- **socket_ptr** Poprzednio utworzone gniazdo TCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie gniazda.
- Gniazdo **NX_NOT_CREATED** (0x27) nie zostało utworzone.
- Gniazdo **NX_STILL_BOUND** (0x42) jest nadal powiązane.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect

Rozłączanie połączeń klienta i gniazda serwera

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa rozłącza ustanowione połączenie z gniazdem klienta lub serwera. Po rozłączeniu gniazda serwera powinno następować żądanie nieakceptowane, a gniazdo klienta, które zostało odłączone, pozostaje w stanie gotowym do innego żądania połączenia. Jeśli proces rozłączenia nie może zakończyć się natychmiast, usługa zawiesza się zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, gdy trwa odłączanie. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne rozłączenie gniazda.
- Określone gniazdo **NX_NOT_CONNECTED** (0x38) nie jest połączone.
- **NX_IN_PROGRESS** (0x37) rozłączenie jest w toku, nie określono oczekiwania.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify

Zainstaluj funkcję wywołania zwrotnego powiadomienia o rozłączeniu protokołu TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana po zakończeniu operacji rozłączenia gniazda. Funkcja wywołania zwrotnego rozłączenia gniazda TCP jest dostępna, jeśli NetX jest skompilowana przy użyciu opcji

- Zdefiniowano ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** .

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.
- **tcp_disconnect_complete_notify** Funkcja wywołania zwrotnego do zainstalowania.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0X00) pomyślnie zarejestrował funkcję wywołania zwrotnego.
- **NX_NOT_SUPPORTED** (0x4B) Funkcja rozszerzonego powiadamiania nie jest wbudowana w bibliotekę NetX
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify

Ustaw funkcję wywołania zwrotnego powiadomienia o ustanowieniu protokołu TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana po nawiązaniu połączenia przez gniazdo TCP. Funkcja wywołania zwrotnego gniazda TCP jest dostępna, jeśli NetX jest skompilowana przy użyciu opcji zdefiniowanej ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** .

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.
- **tcp_establish_notify** Wywoływanie funkcji wywołania zwrotnego po nawiązaniu połączenia TCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawia funkcję powiadamiania.
- **NX_NOT_SUPPORTED** (0x4B) Funkcja rozszerzonego powiadamiania nie jest wbudowana w bibliotekę NetX
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) TCP nie został włączony przez aplikację.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get

Pobierz informacje o działaniach gniazda TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach gniazda TCP dla określonego wystąpienia gniazda TCP.

*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **tcp_packets_sent** Wskaźnik do miejsca docelowego dla łącznej liczby pakietów TCP wysłanych w gnieździe.
- **tcp_bytes_sent** Wskaźnik do miejsca docelowego dla łącznej liczby bajtów TCP wysłanych w gnieździe.
- **tcp_packets_received** Wskaźnik do miejsca docelowego całkowitej liczby pakietów TCP odebranych w gnieździe.
- **tcp_bytes_received** Wskaźnik do lokalizacji docelowej łącznej liczby bajtów TCP odebranych w gnieździe.
- **tcp_retransmit_packets** Wskaźnik do lokalizacji docelowej łącznej liczby ponownych transmisji pakietów TCP.
- **tcp_packets_queued** Wskaźnik do lokalizacji docelowej łącznej liczby pakietów TCP umieszczonych w kolejce w gnieździe.
- **tcp_checksum_errors** Wskaźnik do miejsca docelowego całkowitej liczby pakietów TCP z błędami sumy kontrolnej w gnieździe.
- **tcp_socket_state** Wskaźnik do miejsca docelowego bieżącego stanu gniazda.
- **tcp_transmit_queue_depth** Wskaźnik do miejsca docelowego całkowitej liczby pakietów nadawczych oczekujących w kolejce na potwierdzenie.
- **tcp_transmit_window** Wskaźnik do miejsca docelowego bieżącego rozmiaru okna wysyłania.
- **tcp_receive_window** Wskaźnik do miejsca docelowego bieżącego rozmiaru okna odbierania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie informacji o gnieździe TCP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="return-values"></a>Wartości zwrócone

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

Pobierz rozmiar pasma gniazda

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Opis

Ta usługa pobiera lokalny maksymalny rozmiar segmentu określonego gniazda (Maximum).

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda.
-  rozmiar/rozmiar Miejsce docelowe zwracające rozmiar urządzenia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik miejsca docelowego gniazda lub wskaźnika.
- **NX_NOT_ENABLED** (0X14) TCP nie jest włączona.
- Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem lub inicjalizacją.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get

Pobierz rozmiar pasma równorzędnego gniazda TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Opis

Ta usługa pobiera maksymalny rozmiar segmentu (Maximum) anonsowany przez gniazdo równorzędne.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego i połączonego gniazda.
-  rozmiar/rozmiar Miejsce docelowe zwracające rozmiar tego samego poziomu.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie elementu równorzędnego.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik miejsca docelowego gniazda lub wskaźnika.
- **NX_NOT_ENABLED** (0X14) TCP nie jest włączona.
- Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem lub inicjalizacją.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set

Ustaw rozmiar pasma gniazda

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a>Opis

Ta usługa ustawia maksymalny rozmiar segmentu określonego gniazda (Maximum). Należy pamiętać, że wartość parametru/limit musi znajdować się w zakresie jednostki MTU interfejsu sieciowego, co pozwala na pozostawienie miejsca na nagłówki IP i TCP.

Ta usługa powinna zostać użyta, zanim gniazdo TCP rozpocznie proces nawiązywania połączenia. Jeśli usługa jest używana po nawiązaniu połączenia TCP, Nowa wartość nie ma wpływu na połączenie.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda.
-  rozmiar/rozmiar Wartość parametru o wartości do ustawienia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — zestaw o pomyślnym przeprowadzeniu.
- Wartość parametru **NX_SIZE_ERROR** (0x09) jest zbyt duża.
- **NX_NOT_CONNECTED** (0x38) połączenie TCP nie zostało nawiązane
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_NOT_ENABLED** (0X14) TCP nie jest włączona.
- Obiekt wywołujący **NX_CALLER_ERROR** (0x11) nie jest wątkiem lub inicjalizacją.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get

Pobierz informacje o gnieździe równorzędnym TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o adresie IP i porcie elementu równorzędnego dla połączonego gniazda TCP przez sieć IP.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda TCP.
- **peer_ip_address** Wskaźnik do lokalizacji docelowej dla adresu IP elementu równorzędnego w kolejności bajtów hosta.
- **peer_port** Wskaźnik do lokalizacji docelowej dla numeru portu elementu równorzędnego w kolejności bajtów hosta.

### <a name="return-values"></a>Wartości zwrócone

- Usługa **NX_SUCCESS** (0x00) została wykonana pomyślnie. Adres IP i numer portu elementu równorzędnego są zwracane do obiektu wywołującego.
- Gniazdo **NX_NOT_CONNECTED** (0x38) nie jest w stanie połączonym.
- **NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.
- **NX_NOT_ENABLED** (0X14) TCP nie jest włączona.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive

Odbieranie danych z gniazda TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa odbiera dane TCP z określonego gniazda. Jeśli żadne dane nie są umieszczane w określonym gnieździe, obiekt wywołujący zawiesza się na podstawie podanej opcji oczekiwania.

*Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **packet_ptr** Wskaźnik na wskaźnik pakietu TCP.
- **WAIT_OPTION** Definiuje, jak działa usługa, jeśli żadne dane nie są obecnie umieszczane w kolejce w tym gnieździe. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) odbieranie danych gniazda zakończone powodzeniem.
- Gniazdo **NX_NOT_BOUND** (0x24) nie jest jeszcze powiązane.
- **NX_NO_PACKET** (0X01) nie odebrano żadnych danych.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_NOT_CONNECTED** (0x38) gniazdo nie jest już połączone.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik lub pakiet zwrotny pakietu.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

/* Odbieraj pakiet z wcześniej utworzonego i połączonego gniazda klienta TCP. Jeśli żaden pakiet nie jest dostępny, poczekaj na 200 Takty czasomierza przed pokazaniem. */status = nx_tcp_socket_receive (&client_socket, &packet_ptr, 200);

/* Jeśli stan jest NX_SUCCESS, otrzymany pakiet jest wskazywany przez "packet_ptr". */

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

Powiadamiaj aplikację o odebranych pakietach


### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa konfiguruje wskaźnik Odbierz funkcję powiadamiania za pomocą funkcji wywołania zwrotnego określonego przez aplikację. Ta funkcja wywołania zwrotnego jest następnie wywoływana za każdym razem, gdy co najmniej jeden pakiet jest odbierany w gnieździe. Jeśli zostanie dostarczony NX_NULL wskaźnik, funkcja powiadamiania jest wyłączona.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik na gniazdo TCP.
- **tcp_receive_notify** Wskaźnik funkcji wywołania zwrotnego aplikacji, który jest wywoływany, gdy co najmniej jeden pakiet jest odbierany w gnieździe.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) powiadomienie o pomyślnym odebraniu gniazda.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send

Wysyłanie danych za pośrednictwem gniazda TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wysyła dane TCP za pośrednictwem wcześniej połączonego gniazda TCP. Jeśli rozmiar okna o ostatnio anonsowanym odbiorniku jest mniejszy niż to żądanie, usługa opcjonalnie zawiesza się na podstawie podanej opcji oczekiwania. Ta usługa gwarantuje, że do warstwy IP nie są wysyłane żadne dane pakietu o rozmiarze większym niż wartość maksymalna.

*Jeśli błąd nie zostanie zwrócony, aplikacja nie powinna zwolnić pakietu po tym wywołaniu. Wykonanie tej operacji spowoduje nieprzewidywalne wyniki, ponieważ sterownik sieciowy podejmie również próbę zwolnienia pakietu po transmisji.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia gniazda TCP.
- **packet_ptr** Wskaźnik pakietu danych TCP.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądanie jest większe niż rozmiar okna odbiornika. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie gniazda.
- Gniazdo **NX_NOT_BOUND** (0x24) nie zostało powiązane z żadnym portem.
- **NX_NO_INTERFACE_ADDRESS** (0X50) nie znaleziono odpowiedniego interfejsu wychodzącego.
- Gniazdo **NX_NOT_CONNECTED** (0x38) nie jest już połączone.
- Żądanie **NX_WINDOW_OVERFLOW** (0x39) jest większe niż anonsowany rozmiar okna odbiornika w bajtach.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- Pakiet **NX_INVALID_PACKET** (0x12) nie jest przydzielony.
- Osiągnięto maksymalną głębokość kolejki przesyłania **NX_TX_QUEUE_DEPTH** (0x49).
- Wskaźnik dołączania pakietu **NX_OVERFLOW** (0x03) jest nieprawidłowy.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.
- Wskaźnik dołączania pakietu **NX_UNDERFLOW** (0x02) jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait

### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

Poczekaj, aż gniazdo TCP przeniesie określony stan

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa czeka, aż gniazdo przejdzie do żądanego stanu. Jeśli gniazdo nie jest w żądanym stanie, usługa zawiesza się zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia gniazda TCP.
- **desired_state** Żądany stan protokołu TCP. Prawidłowe Stany gniazda TCP są zdefiniowane w następujący sposób:
- NX_TCP_CLOSED (0x01)
- NX_TCP_LISTEN_STATE (0x02)
- NX_TCP_SYN_SENT (0x03)
- NX_TCP_SYN_RECEIVED (0x04)
- NX_TCP_ESTABLISHED (0x05)
- NX_TCP_CLOSE_WAIT (0x06)
- NX_TCP_FIN_WAIT_1 (0x07)
- NX_TCP_FIN_WAIT_2 (0x08)
- NX_TCP_CLOSING (0x09)
- NX_TCP_TIMED_WAIT (0x0A)
- NX_TCP_LAST_ACK (0x0B)
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądany stan nie jest obecny. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone
- Zaczekanie na **NX_SUCCESS** (0x00).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_NOT_SUCCESSFUL** (0x43) nie występuje w określonym czasie oczekiwania.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.
- **NX_OPTION_ERROR** (0x0A) żądany stan gniazda jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback

Instalacja wywołania zwrotnego dla stanu oczekiwania, który upłynął

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana, gdy gniazdo TCP jest w stanie oczekiwania. Aby można było korzystać z tej usługi, biblioteka NetX musi być skompilowana przy użyciu opcji zdefiniowanej ***NX_ENABLE_EXTENDED_NOTIFY*** .

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.
- **tcp_timed_wait_callback** Funkcja wywołania zwrotnego czasu oczekiwania

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie rejestruje gniazdo funkcji wywołania zwrotnego
- **NX_NOT_SUPPORTED** (0X4B) NetX Library została skompilowana bez włączonej funkcji rozszerzonego powiadamiania.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure

Konfiguruj parametry transmisji gniazda

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a>Opis

Ta usługa konfiguruje różne parametry transmisji określonego gniazda TCP.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik na gniazdo TCP.
- **max_queue_depth** Maksymalna liczba pakietów, które mogą być umieszczone w kolejce na potrzeby transmisji.
- **limit czasu** Liczba czasomierzy ThreadXa jest oczekiwana przez potwierdzenie przed ponownym wysłaniem pakietu.
- **max_retries** Maksymalna dozwolona liczba ponownych prób.
- **timeout_shift** Wartość służąca do zmiany limitu czasu dla każdej kolejnej próby. Wartość 0 powoduje ten sam limit czasu między kolejnymi próbami. Wartość 1 powoduje podwojony limit czasu między ponownymi próbami.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) pomyślna Konfiguracja gniazda transmisji.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_OPTION_ERROR** (0X0a) Nieprawidłowa opcja głębokości kolejki.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set

Powiadamianie o aktualizacjach rozmiaru okna

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa instaluje procedurę wywołania zwrotnego aktualizacji okna gniazda. Ta procedura jest wywoływana automatycznie za każdym razem, gdy określone gniazdo odbierze pakiet wskazujący wzrost rozmiaru okna hosta zdalnego.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda TCP.
- **tcp_window_update_notify** Procedura wywołania zwrotnego, która ma zostać wywołana, gdy zmienia się rozmiar okna. Wartość NULL powoduje wyłączenie zmiany okna.

### <a name="return-values"></a>Wartości zwrócone
- Procedura wywołania zwrotnego **NX_SUCCESS** (0x00) jest instalowana w gnieździe.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.
- Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.


### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create,
- nx_tcp_socket_disconnect_complete_notify,
- nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,
- nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,
- nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,
- nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable

Włącz składnik UDP elementu NetX

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza składnik UDP (User Datagram Protocol) NetX. Po włączeniu protokołu UDP datagramy mogą być wysyłane i odbierane przez aplikację.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne włączenie protokołu UDP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_ALREADY_ENABLED** (0X15) ten składnik został już włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

Znajdź następny dostępny port UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a>Opis

Ta usługa szuka bezpłatnego portu UDP (niepowiązanego) rozpoczynającego się od dostarczonej przez aplikację numeru portu. Logika wyszukiwania zostanie zawinięty, jeśli wyszukiwanie osiągnie maksymalną wartość dla wartości 0xFFFF. Jeśli wyszukiwanie zakończyło się pomyślnie, port wolny jest zwracany w zmiennej wskazywanej przez *free_port_ptr*.

*Ta usługa może być wywoływana z innego wątku i może mieć ten sam port. Aby uniknąć tego warunku wyścigu, aplikacja może chcieć umieścić tę usługę i rzeczywiste powiązanie gniazda w ramach ochrony obiektu mutex.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **port** Numer portu do rozpoczęcia wyszukiwania (od 1 do 0xFFFF).
- **free_port_ptr** Wskaźnik na zmienną zwrotną wolnego portu docelowego.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne znalezienie bezpłatnego portu.
- **NX_NO_FREE_PORTS** (0X45) nie znaleziono wolnych portów.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.
- **NX_INVALID_PORT** (0X46) określony numer portu jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get

Pobierz informacje o działaniach UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach UDP dla określonego wystąpienia IP.

*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **udp_packets_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych pakietów UDP.
- **udp_bytes_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych bajtów UDP.
- **udp_packets_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych pakietów UDP.
- **udp_bytes_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych bajtów UDP.
- **udp_invalid_packets** Wskaźnik do lokalizacji docelowej całkowitej liczby nieprawidłowych pakietów UDP.
- **udp_receive_packets_dropped** Wskaźnik do lokalizacji docelowej całkowitej liczby porzuconych pakietów protokołu UDP.
- **udp_checksum_errors** Wskaźnik do lokalizacji docelowej całkowitej liczby pakietów UDP z błędami sumy kontrolnej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobieranie informacji o UDP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.


### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_invalid_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract

Wyodrębnij parametry sieci z pakietu UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a>Opis

Ta usługa wyodrębnia parametry sieci, takie jak adres IP, numer portu równorzędnego, typ protokołu (usługa zawsze zwraca typ UDP) z pakietu otrzymanego w interfejsie przychodzącym.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu.
- **IP_address** Wskaźnik na adres IP nadawcy.
- **Protokół** Wskaźnik do protokołu UDP.
- **port** Wskaźnik na numer portu nadawcy.
- **interface_index** Wskaźnik do odbioru indeksu interfejsu.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie wyodrębniono dane interfejsu pakietu **NX_SUCCESS** (0x00).
- Pakiet **NX_INVALID_PACKET** (0x12) nie zawiera ramki adresu IP.
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

Powiąż gniazdo UDP z portem UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wiąże wcześniej utworzone gniazdo UDP z określonym portem UDP. Prawidłowy zakres UDP wynosi od 0 do 0xFFFF. Jeśli żądany numer portu jest powiązany z innym gniazdem, ta usługa czeka przez określony czas, w którym gniazdo ma usunąć powiązanie z numerem portu.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.
- **port** Numer portu, z którym ma zostać utworzone powiązanie (od 1 do 0xFFFF). Jeśli numer portu to NX_ANY_PORT (0x0000), wystąpienie protokołu IP wyszuka następny bezpłatny port i użyje go do powiązania.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli port jest już powiązany z innym gniazdem. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnego powiązania gniazda.
- **NX_ALREADY_BOUND** (0X22) to gniazdo jest już powiązane z innym portem.
- Port **NX_PORT_UNAVAILABLE** (0x23) jest już powiązany z innym gniazdem.
- **NX_NO_FREE_PORTS** (0X45) brak wolnego portu.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_INVALID_PORT** (0x46) określono nieprawidłowy port.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available

Pobiera liczbę bajtów dostępnych do pobrania

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a>Opis

Ta usługa Pobiera liczbę bajtów dostępnych do odbioru w określonym gnieździe UDP.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda UDP.
- **bytes_available** Wskaźnik do miejsca docelowego dla dostępnych bajtów.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne pobieranie odebranych bajtów **NX_SUCCESS** (0x00).
- Gniazdo **NX_NOT_SUCCESSFUL** (0x43) nie jest powiązane z portem.
- **NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.
- Funkcja UDP **NX_NOT_ENABLED** (0x14) nie jest włączona.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

Wyłącz sumę kontrolną dla gniazda UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza logikę sumy kontrolnej na potrzeby wysyłania i otrzymywania pakietów w określonym gnieździe UDP. Gdy logika sum kontrolnych jest wyłączona, wartość zero jest ładowana do pola sumy kontrolnej nagłówka UDP dla wszystkich pakietów wysyłanych za pomocą tego gniazda. Wartość sumy kontrolnej zero wartości w nagłówku UDP sygnalizuje odbiornikowi, że suma kontrolna nie jest obliczana dla tego pakietu.

Należy również zauważyć, że nie ma to żadnego efektu, jeśli ***NX_DISABLE_UDP_RX_CHECKSUM** _ i _ *_NX_DISABLE_UDP_TX_CHECKSUM_** są zdefiniowane podczas otrzymywania i wysyłania pakietów UDP odpowiednio.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — Wyłącz sumę kontrolną gniazda.
- Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierz

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

Włącz sumę kontrolną dla gniazda UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia logikę sumy kontrolnej na potrzeby wysyłania i otrzymywania pakietów w określonym gnieździe UDP. Suma kontrolna obejmuje cały obszar danych UDP oraz nagłówek pseudo IP.

Należy również pamiętać, że nie ma to wpływu, jeśli **NX_DISABLE_UDP_RX_CHECKSUM** i **NX_DISABLE_UDP_TX_CHECKSUM** są zdefiniowane podczas otrzymywania i wysyłania pakietów UDP odpowiednio.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) włączono pomyślne włączenie sumy kontrolnej gniazda.
- Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierz

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create

Utwórz gniazdo UDP.

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a>Opis

Ta usługa tworzy gniazdo UDP dla określonego wystąpienia IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **socket_ptr** Wskaźnik do nowej kontrolki gniazda UDP blo.
- **Nazwa** Nazwa aplikacji dla tego gniazda UDP.
- **Type_of_Service** Definiuje typ usługi do transmisji, wartości prawne są następujące:
    - NX_IP_NORMAL (0x00000000)
    - NX_IP_MIN_DELAY (0x00100000)
    - NX_IP_MAX_DATA (0x00080000)
    - NX_IP_MAX_RELIABLE (0x00040000)
    - NX_IP_MIN_COST (0x00020000)
- **fragment** Określa, czy jest dozwolone fragmentacja adresów IP. Jeśli określono NX_FRAGMENT_OKAY (0x0), jest dozwolone fragmentacja adresów IP. Jeśli określono NX_DONT_FRAGMENT (0x4000), fragmentacja adresów IP jest wyłączona.
- **time_to_live** Określa 8-bitową wartość, która definiuje liczbę routerów, które ten pakiet może przekazać przed wyrzucaniem. Wartość domyślna jest określana przez NX_IP_TIME_TO_LIVE.
- **queue_maximum** Określa maksymalną liczbę datagramów UDP, która może być umieszczona w kolejce dla tego gniazda. Po osiągnięciu limitu kolejki dla każdego nowego pakietu odebrano najstarszy pakiet UDP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie utworzono gniazdo UDP.
- **NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ usługi, fragmentu lub opcji Time-to-Live.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_delete,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete

Usuń gniazdo UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone gniazdo UDP. Jeśli gniazdo zostało powiązane z portem, gniazdo musi być najpierw niepowiązane.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne usunięcie gniazda.
- Gniazdo **NX_STILL_BOUND** (0x42) jest nadal powiązane.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get

Pobierz informacje o działaniach gniazda UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach gniazda UDP dla określonego wystąpienia gniazda UDP.

*Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.
- **udp_packets_sent** Wskaźnik do miejsca docelowego dla łącznej liczby pakietów UDP wysłanych w gnieździe.
- **udp_bytes_sent** Wskaźnik do miejsca docelowego dla łącznej liczby bajtów UDP wysłanych w gnieździe.
- **udp_packets_received** Wskaźnik do miejsca docelowego całkowitej liczby pakietów UDP odebranych w gnieździe.
- **udp_bytes_received** Wskaźnik do lokalizacji docelowej łącznej liczby bajtów UDP odebranych w gnieździe.
- **udp_packets_queued** Wskaźnik do lokalizacji docelowej całkowitej liczby pakietów UDP umieszczonych w kolejce w gnieździe.
- **udp_receive_packets_dropped** Wskaźnik do lokalizacji docelowej łącznej liczby pakietów odbioru protokołu UDP porzuconych dla gniazda z powodu przekroczenia rozmiaru kolejki.
- **udp_checksum_errors** Wskaźnik do lokalizacji docelowej całkowitej liczby pakietów UDP z błędami sumy kontrolnej w gnieździe.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne pobranie informacji o gnieździe UDP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
    &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_queued_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

Wybierz numer portu powiązany z gniazdem UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a>Opis

Ta usługa Pobiera numer portu skojarzony z gniazdem, który jest przydatny do znajdowania portu przydzielonego przez NetX w sytuacjach, w których NX_ANY_PORT został określony w momencie powiązania gniazda.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.
- **port_ptr** Wskaźnik do miejsca docelowego dla numeru portu powrotu. Prawidłowe numery portów to (1-0xFFFF).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnego powiązania gniazda.
- **NX_NOT_BOUND** (0X24) to gniazdo nie jest powiązane z portem.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda lub zwracany przez port wskaźnik.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive

Odbieranie datagramu z gniazda UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa odbiera datagram UDP od określonego gniazda. Jeśli żaden datagram nie jest umieszczony w określonym gnieździe, obiekt wywołujący zawiesza się na podstawie podanej opcji oczekiwania.

*Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.
- **packet_ptr** Wskaźnik na wskaźnik pakietu datagramu UDP.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli datagram nie jest obecnie umieszczony w tym gnieździe. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 przez 0xFFFFFFFE)

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

Powiadamiaj aplikację o każdym odebranym pakiecie

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa ustawia wskaźnik funkcji Odbierz powiadomienie na funkcję wywołania zwrotnego określonego przez aplikację. Ta funkcja wywołania zwrotnego jest wywoływana za każdym razem, gdy pakiet jest odbierany w gnieździe. Jeśli zostanie dostarczony NX_NULL wskaźnik, funkcja Odbierz powiadomienie jest wyłączona.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik na gniazdo UDP.
- **udp_receive_notify** Wskaźnik funkcji wywołania zwrotnego aplikacji, który jest wywoływany, gdy pakiet jest odbierany w gnieździe.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send

Wysyłanie datagramu UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a>Opis

Ta usługa wysyła datagram UDP przy użyciu wcześniej utworzonego i powiązanego gniazda UDP. NetX znajduje odpowiedni lokalny adres IP jako adres źródłowy na podstawie docelowego adresu IP. Aby określić konkretny interfejs i źródłowy adres IP, aplikacja powinna używać usługi **nx_udp_socket_interface_send** .

Należy zauważyć, że ta usługa wraca natychmiast niezależnie od tego, czy datagram UDP został pomyślnie wysłany.

Gniazdo musi być powiązane z portem lokalnym.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP
- **packet_ptr** Wskaźnik pakietu datagramu UDP
- **IP_address** Docelowy adres IP
- **port** Prawidłowy numer portu docelowego z zakresu od 1 do 0xFFFF) w kolejności bajtów hosta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie gniazda UDP
- Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane z żadnym portem
- **NX_NO_INTERFACE_ADDRESS** (0X50) nie można znaleźć odpowiedniego interfejsu wychodzącego.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP serwera
- **NX_UNDERFLOW** (0X02) nie ma wystarczającej ilości miejsca na nagłówek UDP w pakiecie
- Wskaźnik dołączania pakietu **NX_OVERFLOW** (0x03) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- Nie włączono protokołu UDP **NX_NOT_ENABLED** (0x14)
- Numer portu **NX_INVALID_PORT** (0x46) nie należy do prawidłowego zakresu

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
    server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
    the packet out the UDP socket to its peer. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_interface_send"></a>nx_udp_socket_interface_send

Wyślij datagram za poorednictwem gniazda UDP.

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a>Opis

Ta usługa wysyła datagram UDP przy użyciu wcześniej utworzonego i powiązanego gniazda UDP za pomocą interfejsu sieciowego z określonym adresem IP jako adresem źródłowym. Należy pamiętać, że usługa wraca natychmiast, niezależnie od tego, czy datagram UDP został pomyślnie wysłany.

### <a name="parameters"></a>Parametry

- **socket_ptr** Gniazdo umożliwiające przesłanie pakietu.
- **packet_ptr** Wskaźnik do pakietu do przesłania.
- **IP_address** Docelowy adres IP do wysłania pakietu.
- **port** Port docelowy.
- **address_index** Indeks adresu skojarzonego z interfejsem, na którym ma zostać wysłany pakiet.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie wysłano pakiet **NX_SUCCESS** (0x00).
- Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane z portem.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.
- Nie włączono przetwarzania UDP **NX_NOT_ENABLED** (0x14).
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik.
- **NX_OVERFLOW** (0X03) Nieprawidłowy wskaźnik dołączania pakietu.
- **NX_UNDERFLOW** (0X02) Nieprawidłowy wskaźnik dołączania do pakietu.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy indeks adresu.
- **NX_INVALID_PORT** (0x46) numer portu przekracza maksymalny numer portu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_unbind

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

Usuń powiązanie gniazda UDP z portu UDP.

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwalnia powiązanie między gniazdem UDP i portem UDP. Wszystkie odebrane pakiety przechowywane w kolejce odbierania zostaną wydane jako część operacji usuwania powiązania.

Jeśli istnieją inne wątki oczekujące na powiązanie innego gniazda z niezwiązanym portem, pierwszy zawieszony wątek zostaje następnie powiązany z nowym niezwiązanym portem.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) odpinanie gniazda zakończone powodzeniem.
- Gniazdo **NX_NOT_BOUND** (0x24) nie zostało powiązane z żadnym portem.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract

Wyodrębnij adres IP i Wyślij port z datadatagramu UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a>Opis

Ta usługa wyodrębnia adres IP i numer portu nadawcy z nagłówków IP i UDP dostarczonego datagramu UDP.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik pakietu datagramu UDP.
- **IP_address** Prawidłowy wskaźnik do zmiennej zwracanego adresu IP.
- **port** Prawidłowy wskaźnik do zmiennej portu powrotu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne oddzielenie adresu IP/portu.
- **NX_INVALID_PACKET** (0x12) podany pakiet jest nieprawidłowy.
- **NX_PTR_ERROR** (0X07) nieprawidłowy pakiet lub adres IP lub port docelowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind