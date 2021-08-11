---
title: Rozdział 4 — Opis Azure RTOS NetX
description: Ten rozdział zawiera opis wszystkich usług NetX Azure RTOS kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f1ebbd4d78f96a257fc6cf62474917a1d618524ff6f27f99c108f904589f84fe
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801941"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a>Rozdział 4 — Opis Azure RTOS NetX

Ten rozdział zawiera opis wszystkich usług NetX Azure RTOS kolejności alfabetycznej. Nazwy usług są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem. Na przykład wszystkie usługi ARP znajdują się na początku tego rozdziału.

> [!NOTE]
> *Należy pamiętać, że interfejs API BSD-Compatible Socket jest dostępny dla starszego kodu aplikacji, który nie może w pełni wykorzystać interfejsu API NetX o wysokiej wydajności. Zapoznaj się z dodatkiem D, aby uzyskać więcej informacji na temat interfejsu API BSD-Compatible Socket.*

W sekcji "Wartości zwracane" każdego  opisu opcja NX_DISABLE_ERROR_CHECKING używana do wyłączania sprawdzania błędów interfejsu API nie ma wpływu na wartości z pogrubieniem, a wartości pogrubione są całkowicie wyłączone. Sekcje "Dozwolone z" wskazują, z którego można nazwać każdą usługę NetX.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate

Unieważnij wszystkie wpisy dynamiczne w pamięci podręcznej ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa unieważnia wszystkie dynamiczne wpisy ARP obecnie w pamięci podręcznej ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne unieważnienie pamięci podręcznej ARP.
- **NX_NOT_ENABLED** (0x14) ARP nie jest włączona.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy adres IP.
- **NX_CALLER_ERROR** (0x11) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,
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

Ta usługa przydziela dynamiczny wpis z pamięci podręcznej ARP i konfiguruje określony adres IP do mapowania adresów fizycznych. Jeśli określono zero adresu fizycznego, rzeczywiste żądanie ARP jest wysyłane do sieci w celu rozwiązania adresu fizycznego. Należy również pamiętać, że ten wpis zostanie usunięty, jeśli starzeje się ARP lub jeśli pamięć podręczna ARP zostanie wyczerpana i jest to najdawniej używany wpis ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_address** Adres IP do mapowania.
- **physical_msw** Pierwsze 16 bitów (47–32) adresu fizycznego.
- **physical_lsw** Niższe 32 bity (31-0) adresu fizycznego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Successful ARP dynamic entry set (Pomyślny dynamiczny zestaw wpisów ARP).
- **NX_NO_MORE_ENTRIES** (0x17) W pamięci podręcznej ARP nie są już dostępne żadne wpisy ARP.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wystąpienia adresu IP.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_enable"></a>nx_arp_enable

Włącza protokół rozpoznawania adresów (ARP, Address Resolution Protocol).

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a>Opis

Ta usługa inicjuje składnik ARP netx dla określonego wystąpienia adresu IP. Inicjowanie ARP obejmuje konfigurowanie pamięci podręcznej ARP i różnych procedur przetwarzania ARP niezbędnych do wysyłania i odbierania komunikatów ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **arp_cache_memory** Wskaźnik do obszaru pamięci, w którym ma być umieszczana pamięć podręczna ARP.
- **arp_cache_size** Każdy wpis ARP wynosi 52 bajty, a więc łączna liczba wpisów ARP jest podzielona przez 52.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne włączenie ARP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik pamięci IP lub pamięci podręcznej.
- **NX_SIZE_ERROR** (0x09) Pamięć podręczna ARP dostarczona przez użytkownika jest za mała.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_ALREADY_ENABLED** (0x15) Ten składnik został już włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send

Wysyłanie bezgotowego żądania ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Opis

Ta usługa przechodzi przez wszystkie interfejsy fizyczne, aby przesyłać zbędne żądania ARP, o ile adres IP interfejsu jest prawidłowy. Jeśli odpowiedź ARP zostanie następnie odebrana, zostanie wywołana dostarczona procedura obsługi odpowiedzi, aby przetworzyć odpowiedź na niesądową odpowiedź ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **response_handler** Wskaźnik do funkcji obsługi odpowiedzi. Jeśli NX_NULL zostanie podany, odpowiedzi są ignorowane.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne pomyślne wysłanie wiadomości ARP.
- **NX_NO_PACKET** (0x01) Brak dostępnych pakietów.
- **NX_NOT_ENABLED** (0x14) ARP nie jest włączona.
- **NX_IP_ADDRESS_ERROR** (0x21) Bieżący adres IP jest nieprawidłowy.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,
- nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find

Lokalizowanie fizycznego adresu sprzętowego na danym adresie IP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a>Opis

Ta usługa próbuje znaleźć fizyczny adres sprzętowy w pamięci podręcznej ARP, która jest skojarzona z dostarczonym adresem IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_address** Adres IP do wyszukania.
- **physical_msw** Wskaźnik do zmiennej do zwracania 16 bitów górnego adresu fizycznego (47–32).
- **physical_lsw** Wskaźnik do zmiennej do zwracania niższych 32 bitów (31-0) adresu fizycznego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne znalezienie adresu sprzętowego ARP.
- **NX_ENTRY_NOT_FOUND** (0x16) Mapowanie nie zostało znalezione w pamięci podręcznej ARP.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP lub pamięci.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,
- nx_arp_ip_address_find, nx_arp_static_entries_delete,
- nx_arp_static_entry_create, nx_arp_static_entry_delete

## <a name="nx_arp_info_get"></a>nx_arp_info_get

Pobieranie informacji o działaniach ARP

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

*Jeśli wskaźnik docelowy jest NX_NULL, te konkretne informacje nie są zwracane do wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **arp_requests_sent** Wskaźnik do miejsca docelowego dla wszystkich żądań ARP wysłanych z tego wystąpienia adresu IP.
- **arp_requests_received** Wskaźnik do miejsca docelowego dla wszystkich żądań ARP odebranych z sieci.
- **arp_responses_sent** Wskaźnik do miejsca docelowego dla łącznej liczby odpowiedzi ARP wysłanych z tego wystąpienia adresu IP.
- **arp_responses_received** Wskaźnik do miejsca docelowego dla łącznej liczby odpowiedzi ARP otrzymanych z sieci.
- **arp_dynamic_entries** Wskaźnik do miejsca docelowego dla bieżącej liczby dynamicznych wpisów ARP.
- **arp_static_entries** Wskaźnik do miejsca docelowego dla bieżącej liczby statycznych wpisów ARP.
- **arp_aged_entries** Wskaźnik do miejsca docelowego całkowitej liczby wpisów ARP, które zostały przejrzane i stały się nieprawidłowe.
- **arp_invalid_messages** Wskaźnik do miejsca docelowego łącznej liczby odebranych nieprawidłowych komunikatów ARP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne pobieranie informacji ORP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Lokalizowanie adresu IP na danym adresie fizycznym

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a>Opis

Ta usługa próbuje znaleźć adres IP w pamięci podręcznej ARP, która jest skojarzona z dostarczonym adresem fizycznym.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_address** Wskaźnik do zwracania adresu IP, jeśli zostanie znaleziony, który został zamapowany.
- **physical_msw** Pierwsze 16 bitów (47–32) adresu fizycznego do wyszukania.
- **physical_lsw** Niższe 32 bity (31–0) adresu fizycznego do wyszukania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne znalezienie adresu IP protokołu ARP
- **NX_ENTRY_NOT_FOUND** (0x16) Mapowanie nie zostało znalezione w pamięci podręcznej ARP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP lub pamięci.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw i physical_lsw są 0.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Usuwanie wszystkich statycznych wpisów ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wszystkie wpisy statyczne w pamięci podręcznej ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Wpisy statyczne są usuwane.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy ip_ptr wskaźnika.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Tworzenie mapowania statycznego adresu IP na sprzęt w pamięci podręcznej usługi ARP

### <a name="prototype"></a>Prototype

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Opis

Ta usługa tworzy mapowanie statycznych adresów IP na fizyczne w pamięci podręcznej protokołu ARP dla określonego wystąpienia adresu IP. Statyczne wpisy ARP nie podlegają okresowym aktualizacjom ARP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_address** Adres IP do mapowania.
- **physical_msw** Pierwsze 16 bitów (47–32) adresu fizycznego do mapowania.
- **physical_lsw** Niższe 32 bity (31-0) adresu fizycznego do mapowania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie wpisu statycznego ARP.
- **NX_NO_MORE_ENTRIES** (0x17) W pamięci podręcznej ARP nie są dostępne żadne więcej wpisów ARP.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw i physical_lsw są 0.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Usuwanie mapowania statycznego adresu IP na sprzęt w pamięci podręcznej usługi ARP


### <a name="prototype"></a>Prototype

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a>Opis

Ta usługa znajduje i usuwa wcześniej utworzone mapowanie statycznych adresów IP na fizyczne w pamięci podręcznej ARP dla określonego wystąpienia adresu IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_address** Adres IP, który został zamapowany statycznie.
- **physical_msw** Pierwsze 16 bitów (47–32) adresu fizycznego, które zostało zamapowane statycznie.
- **physical_lsw** Niższe 32 bity (31–0) adresu fizycznego, który został zamapowany statycznie.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie wpisu statycznego ARP.
- **NX_ENTRY_NOT_FOUND** (0x16) Statyczny wpis ARP nie został znaleziony w pamięci podręcznej ARP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP.
- **NX_INVALID_PARAMETERS** (0x4D) Physical_msw i physical_lsw są 0.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Włączanie protokołu ICMP (Internet Control Message Protocol)

### <a name="prototype"></a>Prototype

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza składnik ICMP dla określonego wystąpienia adresu IP.
Składnik ICMP jest odpowiedzialny za obsługę internetowych komunikatów o błędach oraz żądań ping i odpowiedzi.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne włączenie ICMP.
- **NX_ALREADY_ENABLED** (0x15) ICMP jest już włączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o działaniach ICMP

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

Ta usługa pobiera informacje o działaniach protokołu ICMP dla określonego wystąpienia adresu IP.

*Jeśli wskaźnik docelowy jest NX_NULL, te konkretne informacje nie są zwracane do wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **pings_sent** Wskaźnik do miejsca docelowego całkowitej liczby wysłanych ping.
- **ping_timeouts** Wskaźnik do miejsca docelowego dla całkowitej liczby limitów czasu ping.
- **ping_threads_suspended** Wskaźnik do miejsca docelowego całkowitej liczby wątków zawieszonych na żądaniach ping.
- **ping_responses_received** Wskaźnik do wartości całkowitej liczby odebranych odpowiedzi ping.
- **icmp_checksum_errors** Wskaźnik do miejsca docelowego całkowitej liczby błędów sumy kontrolnej ICMP.
- **icmp_unhandled_messages** Wskaźnik do wartości całkowitej liczby nieobjętych komunikatów ICMP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pobieranie informacji ICMP powiodło się.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Wysyłanie żądania ping na określony adres IP

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

Ta usługa wysyła żądanie ping na określony adres IP i czeka przez określony czas na komunikat odpowiedzi ping. Jeśli nie zostanie odebrana żadna odpowiedź, zostanie zwrócony błąd. W przeciwnym razie cały komunikat odpowiedzi jest zwracany w zmiennej wskazywanej przez response_ptr.

*Jeśli NX_SUCCESS zwracany, aplikacja jest odpowiedzialna za zwalnianie odebranego pakietu, gdy nie jest już potrzebny.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_address** Adres IP w kolejności bajtów hosta na polecenie ping. data Pointer to data area for ping message (Wskaźnik danych do obszaru danych dla komunikatu ping).
- **data_size** Liczba bajtów w danych ping
- **response_ptr** Wskaźnik do wskaźnika pakietu, aby zwrócić komunikat odpowiedzi ping w.
- **wait_option** Definiuje czas oczekiwania na odpowiedź ping. Opcje oczekiwania są zdefiniowane w następujący sposób:

  - NX_NO_WAIT (0x00000000)
  - NX_WAIT_FOREVER (0xFFFFFFFF)
  - wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne polecenie ping. Wskaźnik komunikatu odpowiedzi został umieszczony w zmiennej wskazywanej przez response_ptr.
- **NX_NO_PACKET** (0x01) Nie można przydzielić pakietu żądania ping.
- **NX_OVERFLOW** (0x03) Określony obszar danych przekracza domyślny rozmiar pakietu dla tego wystąpienia adresu IP.
- **NX_NO_RESPONSE** (0x29) Żądany adres IP nie odpowiedział.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik adresu IP lub odpowiedzi.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Włączanie protokołu IGMP (Internet Group Management Protocol)

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza składnik IGMP w określonym wystąpieniu adresu IP.
Składnik IGMP jest odpowiedzialny za zapewnienie obsługi operacji zarządzania grupą multiemisji IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne włączenie IGMP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_ALREADY_ENABLED** (0x15) Ten składnik został już włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o działaniach IGMP

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

Ta usługa pobiera informacje o działaniach IGMP dla określonego wystąpienia adresu IP.

*Jeśli wskaźnik docelowy jest NX_NULL, te konkretne informacje nie są zwracane do wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **igmp_reports_sent** Wskaźnik do miejsca docelowego całkowitej liczby wysłanych raportów ICMP.
- **igmp_queries_received** Wskaźnik do miejsca docelowego dla całkowitej liczby zapytań odebranych przez router multiemisji.
- **igmp_checksum_errors** Wskaźnik do miejsca docelowego całkowitej liczby błędów sumy kontrolnej IGMP w odbieranych pakietach.
- **current_groups_joined** Wskaźnik do miejsca docelowego bieżącej liczby grup przyłączone za pośrednictwem tego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pobieranie informacji IGMP powiodło się.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Wyłączanie sprzężenia zwrotnego IGMP

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza sprzężenia zwrotne IGMP dla wszystkich kolejnych przyłączone do grup multiemisji.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne wyłączenie sprzężenia zwrotnego IGMP.
- **NX_NOT_ENABLED** (0x14) IGMP nie jest włączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) nie jest wątkiem ani inicjowaniem.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a>Zobacz też

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable

Włączanie sprzężenia zwrotnego IGMP

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia sprzężenia zwrotnego IGMP dla wszystkich kolejnych przyłączone grupy multiemisji.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne wyłączenie sprzężenia zwrotnego IGMP.
- **NX_NOT_ENABLED** (0x14) IGMP nie jest włączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) nie jest wątkiem ani inicjowaniem.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a>Zobacz też

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_multicast_interface_join, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join

Przyłącz wystąpienie adresu IP do określonej grupy multiemisji za pośrednictwem interfejsu

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa dołącza wystąpienie adresu IP do określonej grupy multiemisji za pośrednictwem określonego interfejsu sieciowego. Licznik wewnętrzny jest utrzymywany w celu śledzenia, ile razy ta sama grupa została dołączenia. Po dołączeniu do grupy multiemisji składnik IGMP zezwoli na odbiór pakietów IP z tym adresem grupy za pośrednictwem określonego interfejsu sieciowego, a także zgłasza routerom, że ten adres IP jest członkiem tej grupy multiemisji. Komunikaty dołączania do członkostwa IGMP, zgłaszania i opuszczania są również wysyłane za pośrednictwem określonego interfejsu sieciowego.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **group_address** Adres ip grupy multiemisji klasy D do przyłączenia w kolejności bajtów hosta.
- **interface_index** Indeks interfejsu dołączonego do wystąpienia NetX.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przyłączenie do grupy multiemisji.
- **NX_NO_MORE_ENTRIES** (0x17) Nie można łączyć więcej grup multiemisji, przekroczono maksymalną liczbę grup.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_INVALID_INTERFACE** (0x4C) Indeks urządzenia wskazuje nieprawidłowy interfejs sieciowy.
- **NX_IP_ADDRESS_ERROR** (0x21) Podany adres grupy multiemisji nie jest prawidłowym adresem klasy D.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) obsługa multiemisji ip nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join

Przyłącz wystąpienie adresu IP do określonej grupy multiemisji

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Opis

Ta usługa dołącza wystąpienie adresu IP do określonej grupy multiemisji. Licznik wewnętrzny jest utrzymywany w celu śledzenia, ile razy ta sama grupa została dołączenia. Sterownik jest polecany w celu wysłania raportu IGMP, jeśli jest to pierwsze żądanie dołączenia do sieci wskazujące na zamiar dołączenia hosta do grupy. Po dołączeniu składnik IGMP umożliwi odbiór pakietów IP z tym adresem grupy i zgłasza routerom, że ten adres IP jest elementem członkowskim tej grupy multiemisji.

> [!NOTE]
> *Aby dołączyć grupę multiemisji na urządzeniu innym niż podstawowe, użyj usługi **nx_igmp_multicast_interface_join.***

- **Parametry**

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **group_address** Adres IP grupy multiemisji klasy D do przyłączenia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przyłączenie do grupy multiemisji.
- **NX_NO_MORE_ENTRIES** (0x17) Nie można łączyć więcej grup multiemisji, przekroczono maksymalną liczbę grup.
- **NX_INVALID_INTERFACE** (0x4C) Indeks urządzenia wskazuje nieprawidłowy interfejs sieciowy.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP grupy.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave

Spowodować, że wystąpienie adresu IP opuści określoną grupę multiemisji

### <a name="prototype"></a>Prototype

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a>Opis

Ta usługa powoduje, że wystąpienie adresu IP opuszcza określoną grupę multiemisji, jeśli liczba żądań opuszczenia odpowiada liczbie żądań sprzężenia. W przeciwnym razie liczba sprzęzeń wewnętrznych jest po prostu zmniejszana.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **group_address** Grupa multiemisji do opuszczenia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przyłączenie do grupy multiemisji.
- **NX_ENTRY_NOT_FOUND** (0x16) Nie znaleziono poprzedniego żądania dołączenia.
- **NX_INVALID_INTERFACE** (0x4C) Indeks urządzenia wskazuje nieprawidłowy interfejs sieciowy.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP grupy.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,
- nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,
- nx_igmp_multicast_join

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy

Powiadamianie aplikacji o zmianie adresu IP


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję powiadomień aplikacji, która jest wywoływana przy każdej zmianie adresu IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **change_notify** Wskaźnik do funkcji powiadamiania o zmianie adresu IP. Jeśli ten parametr jest NX_NULL, powiadomienie o zmianie adresu IP jest wyłączone.
- **additional_info** Wskaźnik do opcjonalnych dodatkowych informacji, które są również dostarczane do funkcji powiadomień po zmianie adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Powiadomienie o pomyślnej zmianie adresu IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
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

Ta usługa pobiera adres IP i jego maskę podsieci podstawowego interfejsu sieciowego.

*Aby uzyskać informacje o urządzeniu pomocniczym, użyj usługi
- **nx_ip_interface_address_get**.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_address** Wskaźnik do miejsca docelowego dla adresu IP.
- **network_mask** Wskaźnik do miejsca docelowego maski sieci.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie adresu IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy adres IP lub zwracany wskaźnik zmiennej.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
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

*Aby ustawić adres IP i maskę sieci dla urządzenia pomocniczego, użyj usługi **nx_ip_interface_address_set**.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_address** Nowy adres IP.
- **network_mask** Nowa maska sieci.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw pomyślnych adresów IP.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
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

Ta usługa tworzy wystąpienie adresu IP z dostarczonym przez użytkownika adresem IP i sterownikem sieciowym. Ponadto aplikacja musi podać wcześniej utworzoną pulę pakietów dla wystąpienia adresu IP do użycia na użytek wewnętrznej alokacji pakietów. Należy pamiętać, że dostarczony sterownik sieciowy aplikacji nie jest wywoływany, dopóki nie zostanie wykonany wątek tego adresu IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do bloku sterowania w celu utworzenia nowego wystąpienia adresu IP.
- **name (nazwa)** Nazwa nowego wystąpienia adresu IP.
- **ip_address** Adres IP dla tego nowego wystąpienia adresu IP.
- **network_mask** Maskuj, aby odszybować część sieciową adresu IP do zastosowań podsieci i supersieć.
- **default_pool** Wskaźnik do bloku sterowania wcześniej utworzonej puli pakietów NetX.
- **ip_network_driver** Sterownik sieciowy dostarczony przez użytkownika używany do wysyłania i odbierania pakietów IP.
- **memory_ptr** Wskaźnik do obszaru pamięci dla obszaru stosu wątku pomocnika IP.
- **memory_size** Liczba bajtów w obszarze pamięci stosu wątku pomocnika IP.
- **priorytet** Priorytet wątku pomocnika IP.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne utworzenie wystąpienia adresu IP.
- **NX_NOT_IMPLEMENTED** (0x4A) biblioteki NetX jest niepoprawnie skonfigurowana.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy adres IP, wskaźnik funkcji sterownika sieci, pula pakietów lub wskaźnik pamięci.
- **NX_SIZE_ERROR** (0x09) Rozmiar podanego stosu jest zbyt mały.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_IP_ADDRESS_ERROR** (0x21) Podany adres IP jest nieprawidłowy.
- **NX_OPTION_ERROR** (0x21) Podany priorytet wątku IP jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_delete"></a>nx_ip_delete

Usuwanie wcześniej utworzonego wystąpienia adresu IP


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone wystąpienie adresu IP i zwalnia wszystkie zasoby systemowe należące do wystąpienia adresu IP.

### <a name="parameters"></a>Parametry
- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie adresu IP.
- **NX_SOCKETS_BOUND** (0x28) To wystąpienie adresu IP nadal ma powiązane gniazda UDP lub TCP. Wszystkie gniazda muszą być niepowiązane i usunięte przed usunięciem wystąpienia adresu IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Tak

### <a name="example"></a>Przykład

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,
- nx_system_initialize

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command

Wydawanie polecenia do sterownika sieciowego

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Opis

Ta usługa udostępnia interfejs bezpośredni do podstawowego sterownika interfejsu sieciowego aplikacji określonego podczas ***nx_ip_create*** wywołania.

Można użyć poleceń specyficznych dla aplikacji, jeśli ich wartość liczbowa jest większa lub równa NX_LINK_USER_COMMAND.

*Aby wydać polecenie dla urządzenia pomocniczego, użyj **nx_ip_driver_interface_direct_command** usługi.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **polecenie** Numeryczny kod polecenia. Polecenia standardowe są zdefiniowane w następujący sposób:

- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)

- **return_value_ptr** Wskaźnik do zwracania zmiennej w wywołującym.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne bezpośrednie polecenie sterownika sieciowego.
- **NX_UNHANDLED_COMMAND** (0x44) Nieobsłużone lub niezaplementowane polecenie sterownika sieciowego.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy adres IP lub wskaźnik wartości zwracanej.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_INVALID_INTERFACE** (0x4C) Nieprawidłowy indeks interfejsu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

- **Możliwe wywłasznia**

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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command

Wydawanie polecenia do sterownika sieciowego

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a>Opis

Ta usługa udostępnia bezpośrednie polecenie do sterownika urządzenia sieciowego aplikacji w wystąpieniu adresu IP. Polecenia specyficzne dla aplikacji mogą być używane, jeśli ich wartość liczbowa jest większa lub równa NX_LINK_USER_COMMAND *.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **polecenie** Kod polecenia numerycznego. Standardowe polecenia są zdefiniowane w następujący sposób:
- NX_LINK_GET_STATUS (10)
- NX_LINK_GET_SPEED (11)
- NX_LINK_GET_DUPLEX_TYPE (12)
- NX_LINK_GET_ERROR_COUNT (13)
- NX_LINK_GET_RX_COUNT (14)
- NX_LINK_GET_TX_COUNT (15)
- NX_LINK_GET_ALLOC_ERRORS (16)
- NX_LINK_USER_COMMAND (50)
- **interface_index** Indeks interfejsu sieciowego, do których należy wysłać polecenie.
- **return_value_ptr** Wskaźnik do zwracania zmiennej w wywołującym.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne bezpośrednie polecenie sterownika sieciowego.
- **NX_UNHANDLED_COMMAND** (0x44) Nieobsłużone lub niezaplementowane polecenie sterownika sieciowego.
- **NX_INVALID_INTERFACE** (0x4C) Nieprawidłowy indeks interfejsu
- **NX_PTR_ERROR** (0x07) Nieprawidłowy adres IP lub wskaźnik wartości zwracanej.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_forwarding_disable, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable

Wyłącz przekazywanie pakietów IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza przekazywanie pakietów IP wewnątrz składnika NetX IP. Podczas tworzenia zadania adresu IP ta usługa jest automatycznie wyłączana.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Wyłączanie pomyślnego przekazywania adresów IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable

Włączanie przekazywania pakietów IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia przekazywanie pakietów IP wewnątrz składnika NETX IP. Podczas tworzenia zadania adresu IP ta usługa jest automatycznie wyłączana.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne przekazywanie ip.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable

Wyłączanie fragmentowania pakietów IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza fragmentowanie pakietów IP i funkcję ponownego assemblingu. W przypadku pakietów oczekujących na ponowne zseparowane usługa zwalnia te pakiety. Po utworzeniu zadania adresu IP ta usługa jest automatycznie wyłączona.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne wyłączenie fragmentu adresu IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) fragmentacja adresów IP nie jest włączona w wystąpieniu adresu IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable

Włączanie fragmentowania pakietów IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia fragmentowanie pakietów IP i ponowne ocenianie funkcji. Po utworzeniu zadania adresu IP ta usługa jest automatycznie wyłączona.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Włączenie pomyślnego fragmentu adresu IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) fragmentacji adresów IP nie są kompilowane w języku NetX.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,
- nx_ip_status_check, nx_system_initialize

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set

Ustawianie adresu IP bramy

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a>Opis

Ta usługa ustawia adres IP bramy IP. Cały ruch poza siecią jest przekierowyny do tej bramy w celu transmisji. Brama musi być bezpośrednio dostępna za pośrednictwem jednego z interfejsów sieciowych.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_address** Adres IP bramy.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślny adres IP bramy.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wystąpienia adresu IP.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątek

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o działaniach ip

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

Ta usługa pobiera informacje o działaniach protokołu IP dla określonego wystąpienia adresu IP.

*Jeśli wskaźnik docelowy jest NX_NULL, te konkretne informacje nie są zwracane do wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **ip_total_packets_sent** Wskaźnik do miejsca docelowego całkowitej liczby wysłanych pakietów IP.
- **ip_total_bytes_sent** Wskaźnik do miejsca docelowego całkowitej liczby wysłanych bajtów.
- **ip_total_packets_received** Wskaźnik do miejsca docelowego całkowitej liczby pakietów odbieranych przez adres IP.
- **ip_total_bytes_received** Wskaźnik do miejsca docelowego całkowitej liczby odebranych bajtów IP.
- **ip_invalid_packets** Wskaźnik do miejsca docelowego całkowitej liczby nieprawidłowych pakietów IP.
- **ip_receive_packets_dropped** Wskaźnik do miejsca docelowego całkowitej liczby porzuconych pakietów odbieranych.
- **ip_receive_checksum_errors** Wskaźnik do miejsca docelowego całkowitej liczby błędów sumy kontrolnej w odbieranych pakietach.
- **ip_send_packets_dropped** Wskaźnik do miejsca docelowego całkowitej liczby porzuconych pakietów wysyłania.
- **ip_total_fragments_sent** Wskaźnik do miejsca docelowego całkowitej liczby wysłanych fragmentów.
- **ip_total_fragments_received** Wskaźnik do miejsca docelowego całkowitej liczby odebranych fragmentów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pobieranie informacji o adresie IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
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

Ta usługa pobiera adres IP określonego interfejsu sieciowego.

*Określone urządzenie, jeśli nie jest urządzeniem podstawowym, musi być wcześniej dołączone do wystąpienia adresu IP.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **interface_index** Indeks interfejsu, taka sama wartość jak indeks do interfejsu sieciowego dołączonego do wystąpienia adresu IP.
- **ip_address** Wskaźnik do miejsca docelowego dla adresu IP interfejsu urządzenia.
- **network_mask** Wskaźnik do miejsca docelowego maski sieci interfejsu urządzenia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne uzyskiwanie adresu IP.
- **NX_INVALID_INTERFACE** (0x4C) Określony interfejs sieciowy jest nieprawidłowy.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ustawianie adresu IP interfejsu i maski sieci

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

*Określony interfejs musi być wcześniej dołączony do wystąpienia adresu IP.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **interface_index** Indeks interfejsu dołączonego do wystąpienia NetX.
- **ip_address** Nowy adres IP interfejsu sieciowego.
- **network_mask** Nowa maska sieci interfejsu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw pomyślnych adresów IP.
- **NX_INVALID_INTERFACE** (0x4C) Określony interfejs sieciowy jest nieprawidłowy.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_PTR_ERROR** (0x07) Nieprawidłowe wskaźniki.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Dołączanie interfejsu sieciowego do wystąpienia adresu IP

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

Ta usługa dodaje fizyczny interfejs sieciowy do interfejsu IP. Zwróć uwagę, że wystąpienie adresu IP jest tworzone przy użyciu interfejsu podstawowego, więc każdy dodatkowy interfejs jest pomocniczy dla interfejsu podstawowego. Całkowita liczba interfejsów sieciowych dołączonych do wystąpienia adresu IP (w tym interfejsu podstawowego) nie może **przekraczać NX_MAX_PHYSICAL_INTERFACES**.

Jeśli wątek IP nie został jeszcze uruchomiony, interfejsy pomocnicze zostaną zainicjowane w ramach procesu uruchamiania wątku IP, który inicjuje wszystkie interfejsy fizyczne.

Jeśli wątek IP nie jest jeszcze uruchomiony, interfejs pomocniczy jest inicjowany jako ***część nx_ip_interface_attach*** usługi.

*ip_ptr musi wskazać prawidłową strukturę adresów IP NetX.*

- ***NX_MAX_PHYSICAL_INTERFACES** należy skonfigurować dla liczby interfejsów sieciowych dla wystąpienia adresu IP. Wartość domyślna to jedna.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **interface_name** Wskaźnik do ciągu nazwy interfejsu.
- **ip_address** Adres IP urządzenia w kolejności bajtów hosta.
- **network_mask** Maska sieci urządzenia w kolejności bajtów hosta.
- **ip_link_driver** Sterownik Ethernet dla interfejsu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Entry jest dodawany do tabeli routingu statycznego.
- **NX_NO_MORE_ENTRIES** (0x17) Maksymalna liczba interfejsów.
- **NX_MAX_PHYSICAL_INTERFACES** zostanie przekroczony.
- **NX_DUPLICATED_ENTRY** (0x52) Podany adres IP jest już używany w tym wystąpieniu adresu IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowe dane wejściowe adresu IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie parametrów interfejsu sieciowego


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

*ip_ptr musi wskazać prawidłową strukturę adresów IP NetX. Określony interfejs, jeśli nie interfejs podstawowy, musi być wcześniej dołączony do wystąpienia adresu IP.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **interface_index** Indeks określający interfejs sieciowy.
- **interface_name** Wskaźnik do buforu, który zawiera nazwę interfejsu sieciowego.
- **ip_address** Wskaźnik do miejsca docelowego adresu IP interfejsu.
- **network_mask** Wskaźnik do miejsca docelowego maski sieci.
- **mtu_size** Wskaźnik do miejsca docelowego dla maksymalnej jednostki transferu dla tego interfejsu.
- **physical_address_msw** Wskaźnik do miejsca docelowego dla 16 bitów górnego adresu MAC urządzenia.
- **physical_address_lsw** Wskaźnik do miejsca docelowego dla niższych 32 bitów adresu MAC urządzenia.


### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Interfejs zostały uzyskane.
- **NX_PTR_ERROR** (0x07) Nieprawidłowe dane wejściowe wskaźnika.
- **NX_INVALID_INTERFACE** (0x4C) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Usługa nie jest wywoływana z inicjowania systemu lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Sprawdzanie stanu wystąpienia adresu IP


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
- **needed_status** Żądany stan adresu IP zdefiniowany w postaci mapy bitowej w następujący sposób:
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
- **wait_option** Definiuje zachowanie usługi, jeśli żądane bity stanu są niedostępne. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - NX_NO_WAIT (0x00000000)
    - NX_WAIT_FOREVER (0xFFFFFFFF)
    - wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Sprawdzanie stanu adresu IP powiodło się.
- **NX_NOT_SUCCESSFUL** (0x43) Żądanie stanu nie zostało spełnione w określonym czasie.
- **NX_PTR_ERROR** (0x07) wskaźnik IP jest lub stał się nieprawidłowy lub rzeczywisty wskaźnik stanu jest nieprawidłowy.
- **NX_OPTION_ERROR** (0x0a) Nieprawidłowa potrzebna opcja stanu.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_INVALID_INTERFACE** (0x4C) Interface_index jest poza zakresem. lub interfejs jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ustawianie funkcji wywołania zwrotnego powiadamiania o zmianie stanu linku

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a>Opis

Ta usługa konfiguruje funkcję wywołania zwrotnego powiadamiania o zmianie stanu łącza. Procedura zarządzania  link_status_change_notify jest wywoływana, gdy zmienia się stan interfejsu podstawowego lub pomocniczego (na przykład adres IP jest zmieniany). Jeśli *link_status_change_notify* ma wartość NULL, funkcja powiadamiania o zmianie stanu linku jest wyłączona.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku sterowania ip
- **link_status_change_notify** Funkcja wywołania zwrotnego dostarczana przez użytkownika, która ma być wywoływana po zmianie interfejsu fizycznego.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw pomyślny
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik bloku sterowania IP lub nowy wskaźnik adresu fizycznego
- **NX_CALLER_ERROR** (0x11) Usługa nie jest wywoływana z inicjowania systemu lub kontekstu wątku.


### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Wyłączanie wysyłania/odbierania nieprzetworzonych pakietów


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza przesyłanie i odbiór nieprzetworzonych pakietów IP dla tego wystąpienia adresu IP. Jeśli usługa pakietów pierwotnych została wcześniej włączona, a w kolejce odbierania znajdują się nieprzetworzone pakiety, usługa ta zwalnia wszystkie odebrane nieprzetworzone pakiety.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wyłączenie nieprzetworzonych pakietów IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Włączanie przetwarzania nieprzetworzonych pakietów


### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia przesyłanie i odbiór nieprzetworzonych pakietów IP dla tego wystąpienia adresu IP. Przychodzące pakiety TCP, UDP, ICMP i IGMP są nadal przetwarzane przez netX. Pakiety z nieznanymi typami protokołów górnej warstwy są przetwarzane przez nieprzetworzoną procedurę odbioru pakietów.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Włączenie pakietu nieprzetworzonych adresów IP pomyślne.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Wysyłanie nieprzetworzonych pakietów IP za pośrednictwem określonego interfejsu sieciowego

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

Ta usługa wysyła nieprzetworzony pakiet IP do docelowego adresu IP przy użyciu określonego lokalnego adresu IP jako adresu źródłowego i za pośrednictwem skojarzonego interfejsu sieciowego. Należy zauważyć, że ta procedura zwraca natychmiast i dlatego nie jest wiadomo, czy pakiet IP został rzeczywiście wysłany. Sterownik sieciowy będzie odpowiedzialny za zwolnienie pakietu po zakończeniu transmisji. Ta usługa różni się od innych usług tym, że nie ma możliwości, aby sprawdzić, czy pakiet został rzeczywiście wysłany. Może on zostać zgubiony w Internecie.

*Należy pamiętać, że przetwarzanie nieprzetworzonych adresów IP musi być włączone.*

*Ta usługa jest podobna do **nx_ip_raw_packet_send**, z tą różnicą, że ta usługa umożliwia aplikacji wysyłanie nieprzetworzonych pakietów IP z określonych interfejsów fizycznych.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego zadania adresu IP.
- **packet_ptr** Wskaźnik do pakietu, który ma być przesyłany.
- **destination_ip** Adres IP do wysyłania pakietów.
- **address_index** Indeks adresu interfejsu do wysyłania pakietów.
- **type_of_service** Typ usługi pakietu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pakiet został pomyślnie przesłany.
- **NX_IP_ADDRESS_ERROR** (0x21) Brak odpowiedniego interfejsu wychodzącego.
- **NX_NOT_ENABLED** (0x14) Nieprzetworzone przetwarzanie pakietów IP nie jest włączone.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik wejściowy.
- **NX_OPTION_ERROR** (0x0A) Określono nieprawidłowy typ usługi.
- **NX_OVERFLOW** (0x03) Wskaźnik zawiera nieprawidłowy pakiet.
- **NX_UNDERFLOW** (0x02) Nieprawidłowy wskaźnik wstępnie dołączanych pakietów.
- **NX_INVALID_INTERFACE** (0x4C) Określono nieprawidłowy indeks interfejsu.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Odbieranie nieprzetworzonych pakietów IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa odbiera nieprzetworzone pakiety IP z określonego wystąpienia adresu IP. Jeśli w kolejce odbierania nieprzetworzonych pakietów znajdują się pakiety IP, pierwszy (najstarszy) pakiet jest zwracany do wywołującego. W przeciwnym razie, jeśli pakiety nie są dostępne, wywołujący może wstrzymać określone przez opcję oczekiwania.

*Jeśli NX_SUCCESS, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebny.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **packet_ptr** Wskaźnik do wskaźnika do miejsca odebranego nieprzetworzonych pakietów IP.
- **wait_option** Definiuje zachowanie usługi w przypadku, gdy nie ma dostępnych nieprzetworzonych pakietów IP. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne odbieranie nieprzetworzonych pakietów IP.
- **NX_NO_PACKET** (0x01) Żaden pakiet nie był dostępny.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy adres IP lub wskaźnik pakietów powrotnych.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Wysyłanie nieprzetworzonych pakietów IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a>Opis

Ta usługa wysyła nieprzetworzonych pakietów IP do docelowego adresu IP. Należy pamiętać, że ta procedura zwraca się natychmiast i dlatego nie wiadomo, czy pakiet IP został rzeczywiście wysłany. Sterownik sieciowy będzie odpowiedzialny za zwolnienie pakietu po zakończeniu transmisji.

W przypadku systemu wieloadresowego netX używa docelowego adresu IP do znalezienia odpowiedniego interfejsu sieciowego i używa adresu IP interfejsu jako adresu źródłowego. Jeśli docelowy adres IP jest rozgłaszany lub multiemisja, używany jest pierwszy prawidłowy interfejs. W tym ***nx_ip_raw_packet_interface_send*** aplikacje używają tej funkcji.

*Jeśli nie zostanie zwrócony błąd, aplikacja nie powinna zwalniać pakietu po tym wywołaniu. Spowoduje to nieprzewidywalne wyniki, ponieważ sterownik sieciowy zwolni pakiet po zakończeniu transmisji.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **packet_ptr** Wskaźnik do nieprzetworzonych pakietów IP do wysłania.
- **destination_ip** Docelowy adres IP, który może być określonym adresem IP hosta, emisji sieciowej, wewnętrznej pętli zwrotnej lub adresu multiemisji.
- **type_of_service** Definiuje typ usługi transmisji, a wartości prawne są następujące:
- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zainicjowano wysyłanie nieprzetworzonych pakietów IP pomyślnie.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP.
- **NX_NOT_ENABLED** (0x14) Nieprzetworzone adresy IP nie są włączone.
- **NX_OPTION_ERROR** (0x0A) Nieprawidłowy typ usługi.
- **NX_UNDERFLOW** (0x02) Za mało miejsca na dołączanie nagłówka IP pakietu.
- **NX_OVERFLOW** (0x03) Wskaźnik dołączania pakietów jest nieprawidłowy.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy adres IP lub wskaźnik pakietu.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ta usługa dodaje wpis do tabeli routingu statycznego. Należy *pamiętać, że next_hop* musi być bezpośrednio dostępny z jednego z lokalnych urządzeń sieciowych.

*Pamiętaj, ip_ptr musi wskazać prawidłową strukturę adresów IP NetX, a biblioteka NetX musi zostać s zbudowana przy użyciu NX_ENABLE_IP_STATIC_ROUTING, aby można było korzystać z tej usługi. Domyślnie netx jest łączona bez NX_ENABLE_IP_STATIC_ROUTING zdefiniowanych.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **network_address** Docelowy adres sieciowy w kolejności bajtów hosta
- **net_mask** Docelowa maska sieci w kolejności bajtów hosta
- **next_hop** Adres następnego przeskoku dla sieci docelowej w kolejności bajtów hosta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Entry jest dodawany do tabeli routingu statycznego.
- **NX_OVERFLOW** (0x03) Statyczna tabela routingu jest pełna.
- **NX_NOT_SUPPORTED** (0x4B) Ta funkcja nie jest kompilowana.
- **NX_IP_ADDRESS_ERROR** (0x21) Następny przeskok nie jest bezpośrednio dostępny za pośrednictwem interfejsów lokalnych.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy ip_ptr wskaźnika.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Usuwanie trasy statycznej z tabeli routingu

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a>Opis

Ta usługa usuwa wpis z tabeli routingu statycznego.

*Pamiętaj, ip_ptr musi wskazać prawidłową strukturę adresów IP NetX, a biblioteka NetX musi zostać s zbudowana przy użyciu NX_ENABLE_IP_STATIC_ROUTING, aby można było korzystać z tej usługi. Domyślnie netx jest łączona bez NX_ENABLE_IP_STATIC_ROUTING zdefiniowanych.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **network_address** Docelowy adres sieciowy w kolejności bajtów hosta.
- **net_mask** Docelowa maska sieci w kolejności bajtów hosta.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Sprawdzanie stanu wystąpienia adresu IP

### <a name="prototype"></a>Prototype

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa sprawdza i opcjonalnie czeka na określony stan podstawowego interfejsu sieciowego utworzonego wcześniej wystąpienia adresu IP. Aby uzyskać stan w interfejsach pomocniczych, aplikacje muszą używać usługi ***nx_ip_interface_status_check.***

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **needed_status** Żądany stan adresu IP zdefiniowany w postaci mapy bitowej w następujący sposób:
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
- **wait_option** Definiuje zachowanie usługi, jeśli żądane bity stanu są niedostępne. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Sprawdzanie stanu adresu IP powiodło się.
- **NX_NOT_SUCCESSFUL** (0x43) Stan nie został spełniony w określonym czasie.
- **NX_PTR_ERROR** (0x07) wskaźnik IP jest lub stał się nieprawidłowy lub rzeczywisty wskaźnik stanu jest nieprawidłowy.
- **NX_OPTION_ERROR** (0x0a) Nieprawidłowa potrzebna opcja stanu.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize

## <a name="nx_packet_allocate"></a>nx_packet_allocate

Przydzielanie pakietu z określonej puli

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa przydziela pakiet z określonej puli i dostosowuje dołączany wskaźnik w pakiecie zgodnie z określonym typem pakietu. Jeśli pakiet nie jest dostępny, usługa jest wstrzymywana zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów.
- **packet_ptr** Wskaźnik do wskaźnika wskaźnika przydzielonego pakietu.
- **packet_type** Definiuje typ żądanego pakietu. Listę obsługiwanych typów pakietów można znaleźć w części "Pule pakietów" na stronie 49 w rozdziale 3.
- **wait_option** Definiuje czas oczekiwania w taktach, jeśli w puli pakietów nie ma dostępnych pakietów. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne przydzielenie pakietu.
- **NX_NO_PACKET** (0x01) Brak dostępnych pakietów.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) Rozmiar pakietu nie obsługuje protokołu.
- **NX_OPTION_ERROR** (0x0A) Nieprawidłowy typ pakietu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik powrotu puli lub pakietu.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowa opcja oczekiwania z nieprzeczytanego.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr (sterowniki sieciowe aplikacji). Opcja oczekiwania musi być NX_NO_WAIT używana w isr lub w kontekście czasomierza.

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy

Kopiowanie pakietu

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa kopiuje informacje zawarte w dostarczonym pakiecie do co najmniej jednego nowego pakietu przydzielonego z podanej puli pakietów. Jeśli to się powiedzie, wskaźnik do nowego pakietu jest zwracany w miejscu docelowym wskazywanym przez new_packet_ptr **.**

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu źródłowego.
- **new_packet_ptr** Wskaźnik do miejsca docelowego, gdzie ma być zwracany wskaźnik do nowej kopii pakietu.
- **pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów używanej do przydzielania co najmniej jednego pakietu dla kopii.
- **wait_option** Definiuje, jak usługa czeka, jeśli nie ma dostępnych pakietów. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne skopiowanie pakietu.
- **NX_NO_PACKET** (0x01) nie jest dostępny do kopiowania.
- **NX_INVALID_PACKET** (0x12) Pusty pakiet źródłowy lub kopiowanie nie powiodło się.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_INVALID_PARAMETERS** (0x4D) Rozmiar pakietu nie obsługuje protokołu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowa pula, pakiet lub wskaźnik docelowy.
- **NX_UNDERFLOW** (0x02) Nieprawidłowy wskaźnik dołączany do pakietu.
- **NX_OVERFLOW** (0x03) Nieprawidłowy wskaźnik dołączania pakietów.
- **NX_CALLER_ERROR** (0x11) Opcja oczekiwania została określona podczas inicjowania lub w isr.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append

Dołączanie danych na końcu pakietu

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

Ta usługa dołącza dane na końcu określonego pakietu. Podany obszar danych jest kopiowany do pakietu. Jeśli nie ma wystarczającej ilości pamięci, a funkcja pakietów łańcuchowych jest włączona, co najmniej jeden pakiet zostanie przydzielony w celu spełnienia żądania. Jeśli funkcja pakietów łańcuchowych nie jest włączona, *NX_SIZE_ERROR* zwracana.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik pakietu.
- **data_start** Wskaźnik do początku obszaru danych użytkownika, aby dołączyć do pakietu.
- **data_size** Rozmiar obszaru danych użytkownika.
- **pool_ptr** Wskaźnik do puli pakietów, z której ma być przydzielany inny pakiet, jeśli w bieżącym pakiecie nie ma wystarczającej ilości miejsca.
- **wait_option** Definiuje zachowanie usługi, jeśli nie ma dostępnych pakietów. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne dołączanie pakietów.
- **NX_NO_PACKET** (0x01) Brak dostępnych pakietów.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort *.*
- **NX_INVALID_PARAMETERS** (0x4D) Rozmiar pakietu nie obsługuje protokołu.
- **NX_UNDERFLOW** (0x02) Wskaźnik dołączany jest mniejszy niż początek ładunku.
- **NX_OVERFLOW** (0x03) Wskaźnik dołączania jest większy niż koniec ładunku.
- **NX_PTR_ERROR** (0x07) Nieprawidłowa pula, pakiet lub wskaźnik danych.
- **NX_SIZE_ERROR** (0x09) Nieprawidłowy rozmiar danych.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowa opcja oczekiwania z nieprzeczytanego.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR (sterowniki sieciowe aplikacji)

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset

Wyodrębnianie danych z pakietu za pośrednictwem przesunięcia

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

Ta usługa kopiuje dane z pakietu NetX (lub łańcucha pakietów) rozpoczynając od określonego przesunięcia od wskaźnika o określonym rozmiarze w bajtach do określonego buforu. Liczba rzeczywiście skopiowanych bajtów jest zwracana w *bytes_copied.* Ta usługa nie usuwa danych z pakietu ani nie dostosowuje wstępnie zawartego wskaźnika ani innych informacji o stanie wewnętrznym.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu do wyodrębnienia
- **przesunięcie** Przesunięcie od bieżącego wstępnie otwartego wskaźnika.
- **buffer_start** Wskaźnik do rozpoczęcia zapisywania buforu
- **buffer_length** Liczba bajtów do skopiowania
- **bytes_copied** Liczba rzeczywiście skopiowanych bajtów

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne kopiowanie pakietów
- **NX_PACKET_OFFSET_ERROR** (0x53) Po określono nieprawidłową wartość przesunięcia
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik pakietu lub wskaźnik buforu

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,
- nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,
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

Ta usługa kopiuje dane z dostarczonego pakietu do podanego buforu. Rzeczywista liczba skopiowanych bajtów jest zwracana w miejscu docelowym wskazywanym przez bytes_copied **.**

Należy pamiętać, że ta usługa nie zmienia stanu wewnętrznego pakietu. Pobierane dane są nadal dostępne w pakiecie.

*Bufor docelowy musi być wystarczająco duży, aby pomieścić zawartość pakietu. Jeśli nie, pamięć zostanie uszkodzona, co spowoduje nieprzewidywalne wyniki.*

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu źródłowego.
- **buffer_start** Wskaźnik do początku obszaru buforu.
- **bytes_copied** Wskaźnik do miejsca docelowego dla liczby skopiowanych bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pobieranie danych pakietów powiodło się.
- **NX_INVALID_PACKET** (0x12) Nieprawidłowy pakiet.
- **NX_PTR_ERROR** (0x07) Wskaźnik nieprawidłowy pakiet, uruchamianie buforu lub bajty skopiowane.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_length_get,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get

Uzyskiwanie długości danych pakietów

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a>Opis

Ta usługa pobiera długość danych w określonym pakiecie.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu.
- **długość** Miejsce docelowe dla długości pakietu.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release,
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create

Tworzenie puli pakietów w określonym obszarze pamięci

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

- **pool_ptr** Wskaźnik do bloku sterowania puli pakietów.
- **name (nazwa)** Wskaźnik do nazwy aplikacji dla puli pakietów.
- **payload_size** Liczba bajtów w każdym pakiecie w puli. Ta wartość musi mieć co najmniej 40 bajtów, a także musi być podzielna równomiernie przez 4.
- **memory_ptr** Wskaźnik do obszaru pamięci, w którym ma być umieszczana pula pakietów. Wskaźnik powinien być wyrównany na granicy ULONG.
- **memory_size** Rozmiar obszaru pamięci puli.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie puli pakietów.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik puli lub pamięci.
- **NX_SIZE_ERROR** (0x09) Nieprawidłowy rozmiar bloku lub pamięci.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete

Usuwanie wcześniej utworzonej puli pakietów

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzoną pulę pakietów. NetX sprawdza wszystkie wątki, które są obecnie wstrzymane w pakietach w puli pakietów, i czyszczy zawieszenie.

### <a name="parameters"></a>Parametry

- **pool_ptr** Wskaźnik bloku sterowania pulą pakietów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie puli pakietów.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik puli.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Tak

### <a name="example"></a>Przykład

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
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

*Jeśli wskaźnik docelowy jest NX_NULL, te konkretne informacje nie są zwracane do wywołującego.*

### <a name="parameters"></a>Parametry

- **pool_ptr** Wskaźnik do wcześniej utworzonej puli pakietów.
- **total_packets** Wskaźnik do miejsca docelowego całkowitej liczby pakietów w puli.
- **free_packets** Wskaźnik do miejsca docelowego całkowitej liczby obecnie wolnych pakietów.
- **empty_pool_requests** Wskaźnik do miejsca docelowego całkowitej liczby żądań alokacji, gdy pula była pusta.
- **empty_pool_suspensions** Wskaźnik do miejsca docelowego całkowitej liczby pustych zawieszenia puli.
- **invalid_packet_releases** Wskaźnik do miejsca docelowego całkowitej liczby nieprawidłowych wydań pakietów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pobieranie informacji o puli pakietów powiodło się.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete
- nx_packet_release, nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release

Zwolnij wcześniej przydzielony pakiet

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwalnia pakiet, w tym wszelkie dodatkowe pakiety łańcuchowe do określonego pakietu. Jeśli inny wątek zostanie zablokowany podczas alokacji pakietów, zostanie mu nadany pakiet i wznowiony.

*Aplikacja musi zapobiegać wydaniu pakietu więcej niż raz, ponieważ spowoduje to nieprzewidywalne wyniki.*

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik pakietu.


### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne wydanie pakietu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik pakietu.
- **NX_UNDERFLOW** (0x02) Dołączany wskaźnik jest mniejszy niż początek ładunku.
- **NX_OVERFLOW** (0x03) Wskaźnik dołączania jest większy niż koniec ładunku.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr (sterowniki sieciowe aplikacji)

### <a name="preemption-possible"></a>Możliwe wywłasznia

Tak

### <a name="example"></a>Przykład

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a>Zobacz też

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release

Zwalnianie przesyłanego pakietu

### <a name="prototype"></a>Prototype

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Opis

W przypadku pakietów innych niż TCP ta usługa zwalnia przesłany pakiet, w tym wszelkie dodatkowe pakiety łańcuchowe do określonego pakietu. Jeśli inny wątek zostanie zablokowany podczas alokacji pakietów, zostanie mu nadany pakiet i wznowiony. W przypadku przesyłanego pakietu TCP pakiet jest oznaczony jako przesyłany, ale nie jest zwalniany do momentu potwierdzenia pakietu. Ta usługa jest zwykle wywoływana ze sterownika sieciowego aplikacji po przesłaniu pakietu.

*Sterownik sieciowy powinien usunąć nagłówek nośnika fizycznego i dostosować długość pakietu przed wywołaniem tej usługi.*

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik pakietu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wydanie pakietu przesyłania.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik pakietu.
- **NX_UNDERFLOW** (0x02) Dołączany wskaźnik jest mniejszy niż początek ładunku.
- **NX_OVERFLOW** (0x03) Wskaźnik dołączania jest większy niż koniec ładunku.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze, sterowniki sieciowe aplikacji (w tym sterowniki ISR)

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_packet_allocate, nx_packet_copy, nx_packet_data_append,
- nx_packet_data_extract_offset, nx_packet_data_retrieve,
- nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,
- nx_packet_pool_info_get, nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable

Wyłącz protokół RARP (Reverse Address Resolution Protocol)

### <a name="prototype"></a>Prototype

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza składnik RARP netx dla określonego wystąpienia adresu IP. W przypadku systemu wieloadresowego ta usługa wyłącza funkcję RARP we wszystkich interfejsach.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wyłączenie rarp.
- **NX_NOT_ENABLED** (0x14) RARP nie został włączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Włączanie protokołu RARP (Reverse Address Resolution Protocol)

### <a name="prototype"></a>Prototype

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia składnikOWI RARP netx dla określonego wystąpienia adresu IP. Składniki RARP przeszukuje wszystkie dołączone interfejsy sieciowe w poszukiwaniu zerowego adresu IP. Zerowy adres IP wskazuje, że interfejs nie ma jeszcze przypisania adresu IP. Protokół RARP próbuje rozpoznać adres IP, włączając proces RARP w tym interfejsie.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne włączenie funkcji RARP.
- **NX_IP_ADDRESS_ERROR** (0x21) adres IP jest już prawidłowy.
- **NX_ALREADY_ENABLED** (0x15) RARP została już włączona.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o działaniach RARP

### <a name="prototype"></a>Prototype

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach RARP dla określonego wystąpienia adresu IP.

*Jeśli wskaźnik docelowy jest NX_NULL, te konkretne informacje nie są zwracane do wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **rarp_requests_sent** Wskaźnik do miejsca docelowego całkowitej liczby wysłanych żądań RARP.
- **rarp_responses_received** Wskaźnik do miejsca docelowego dla całkowitej liczby odebranych odpowiedzi RARP.
- **rarp_invalid_messages** Wskaźnik do miejsca docelowego całkowitej liczby nieprawidłowych komunikatów.


### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pobieranie informacji RARP powiodło się.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Inicjowanie systemu NetX

### <a name="prototype"></a>Prototype

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a>Opis

Ta usługa inicjuje podstawowe zasoby systemowe NetX w ramach przygotowania do użycia. Powinien on być wywoływany przez aplikację podczas inicjowania i przed każdym innym wywołaniem NetX.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

Brak

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze, isr

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,
- nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,
- nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,
- nx_ip_forwarding_enable, nx_ip_fragment_disable,
- nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind

Wiązanie gniazda TCP klienta z portem TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wiąże wcześniej utworzone gniazdo klienta TCP z określonym portem TCP. Prawidłowe gniazda TCP zakres od 0 do 0xFFFF. Jeśli określony port TCP jest niedostępny, usługa wstrzymuje się zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **port** Numer portu do powiązania (od 1 do 0xFFFF). Jeśli numer portu jest NX_ANY_PORT (0x0000), wystąpienie adresu IP wyszuka następny bezpłatny port i użyje go dla powiązania.
- **wait_option** Definiuje zachowanie usługi, jeśli port jest już powiązany z innym gniazdem. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne powiązanie gniazda.
- **NX_ALREADY_BOUND** (0x22) To gniazdo jest już powiązane z innym portem TCP.
- **NX_PORT_UNAVAILABLE** (0x23) port jest już powiązany z innym gniazdem.
- **NX_NO_FREE_PORTS** (0x45) Brak bezpłatnego portu.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort *.*
- **NX_INVALID_PORT** (0x46) Nieprawidłowy port.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect

Połączenie tcp klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa łączy wcześniej utworzone i powiązane gniazdo klienta TCP z portem określonego serwera. Prawidłowe porty serwera TCP mają zakres od 0 do 0xFFFF. Jeśli połączenie nie zostanie nawiązaniu natychmiast, usługa zostanie wstrzymana zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **server_ip** Adres IP serwera.
- **server_port** Numer portu serwera, z którym ma nawiązać połączenie (od 1 do 0xFFFF).
- **wait_option** Definiuje sposób, w jaki usługa zachowuje się podczas nawiązynia połączenia. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne połączenie gniazda.
- **NX_NOT_BOUND** (0x24) Gniazda nie jest powiązana.
- **NX_NOT_CLOSED** (0x35) Gniazdo nie jest w stanie zamkniętym.
- **NX_IN_PROGRESS** (0x37) Nie określono oczekiwania, próba połączenia jest w toku.
- **NX_INVALID_INTERFACE** (0x4C) Podany nieprawidłowy interfejs.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP serwera.
- **NX_INVALID_PORT** (0x46) Nieprawidłowy port.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get

Uzyskiwanie numeru portu powiązanego z gniazdem TCP klienta

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a>Opis

Ta usługa pobiera numer portu skojarzony z gniazdem, co jest przydatne do znalezienia portu przydzielonego przez netx w sytuacjach, NX_ANY_PORT został określony w czasie, gdy gniazdo zostało powiązane.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **port_ptr** Wskaźnik do miejsca docelowego dla numeru portu powrotu. Prawidłowe numery portów to (od 1 do 0xFFFF).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne powiązanie gniazda.
- **NX_NOT_BOUND** (0x24) To gniazdo nie jest powiązane z portem.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda lub wskaźnik powrotu portu.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind

Unbind TCP client socket from TCP port (Odłącz gniazdo klienta TCP od portu TCP)

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwalnia powiązanie między gniazdem klienta TCP i portem TCP. Jeśli inne wątki oczekują na powiązanie innego gniazda z tym samym numerem portu, pierwszy zawieszony wątek jest następnie powiązany z tym portem.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne powiązycie gniazda.
- **NX_NOT_BOUND** (0x24) nie zostało powiązane z żadnym portem.
- **NX_NOT_CLOSED** (0x35) nie zostało odłączone.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,
- nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_enable"></a>nx_tcp_enable

Włączanie składnika TCP netx

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia Transmission Control Protocol (TCP) netx. Po włączeniu połączenia TCP mogą zostać nawiązane przez aplikację.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne włączenie protokołu TCP.
- **NX_ALREADY_ENABLED** (0x15) TCP jest już włączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find

Znajdowanie następnego dostępnego portu TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a>Opis

Ta usługa próbuje zlokalizować bezpłatny port TCP (niepowiązany) rozpoczynający się od portu dostarczonego przez aplikację. Logika wyszukiwania opakuje się, jeśli wyszukiwanie osiągnie maksymalną wartość portu 0xFFFF. Jeśli wyszukiwanie powiedzie się, bezpłatny port jest zwracany w zmiennej wskazywanej przez free_port_ptr *.*

*Tę usługę można wywołać z innego wątku i zwrócić ten sam port. Aby zapobiec takiej sytuacji wyścigu, aplikacja może chcieć umieścić tę usługę i rzeczywiste powiązanie gniazda klienta w ramach ochrony obiektu mutex.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **port** Numer portu do rozpoczęcia wyszukiwania od (od 1 do 0xFFFF).
- **free_port_ptr** Wskaźnik do wartości zwracanej wolnego portu docelowego.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne znalezienie bezpłatnego portu.
- **NX_NO_FREE_PORTS** (0x45) Nie znaleziono wolnych portów.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.
- **NX_INVALID_PORT** (0x46) Określony numer portu jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get

Pobieranie informacji o działaniach TCP

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

Ta usługa pobiera informacje o działaniach TCP dla określonego wystąpienia adresu IP.

*Jeśli wskaźnik docelowy jest NX_NULL, te konkretne informacje nie są zwracane do wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **tcp_packets_sent** Wskaźnik do miejsca docelowego całkowitej liczby wysłanych pakietów TCP.
- **tcp_bytes_sent** Wskaźnik do miejsca docelowego całkowitej liczby wysłanych bajtów TCP.
- **tcp_packets_received** Wskaźnik do miejsca docelowego całkowitej liczby odebranych pakietów TCP.
- **tcp_bytes_received** Wskaźnik do miejsca docelowego całkowitej liczby odebranych bajtów TCP.
- **tcp_invalid_packets** Wskaźnik do miejsca docelowego całkowitej liczby nieprawidłowych pakietów TCP.
- **tcp_receive_packets_dropped** Wskaźnik do miejsca docelowego całkowitej liczby porzuconych pakietów odbieranych przez protokół TCP.
- **tcp_checksum_errors** Wskaźnik do miejsca docelowego całkowitej liczby pakietów TCP z błędami sumy kontrolnej.
- **tcp_connections** Wskaźnik do miejsca docelowego całkowitej liczby połączeń TCP.
- **tcp_disconnections** Wskaźnik do miejsca docelowego całkowitej liczby rozłączeń TCP.
- **tcp_connections_dropped** Wskaźnik do miejsca docelowego całkowitej liczby porzuconych połączeń TCP.
- **tcp_retransmit_packets** Wskaźnik do miejsca docelowego całkowitej liczby ponownie emitowanych pakietów TCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pobieranie informacji TCP powiodło się.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept

Akceptowanie połączenia TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa akceptuje (lub przygotowuje do zaakceptowania) żądanie połączenia gniazda klienta TCP dla portu, który został wcześniej ustawiony do nasłuchiwania. Ta usługa może być wywoływana natychmiast po wywołaniu przez aplikację usługi nasłuchiwać lub ponownego nasłuchiwać lub po wywołaniu procedury wywołania zwrotnego nasłuchiwać, gdy połączenie klienta jest rzeczywiście obecne. Jeśli nie można od razu nawiązanego połączenia, usługa wstrzymuje się zgodnie z podaną opcją oczekiwania.

*Aplikacja musi **wywołać** nx_tcp_server_socket_unaccept gdy połączenie nie będzie już potrzebne do usunięcia powiązania gniazda serwera z portem serwera.*

*Procedury wywołania zwrotnego aplikacji są wywoływane z poziomu wątku pomocnika adresu IP.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do bloku sterowania gniazda serwera TCP.
- **wait_option** Definiuje sposób, w jaki usługa zachowuje się podczas nawiązynia połączenia. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)


### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Akceptowanie pomyślnego gniazda serwera TCP (połączenie pasywne).
- **NX_NOT_LISTEN_STATE** (0x36) Dostarczone gniazdo serwera nie jest w stanie nasłuchiwać.
- **NX_IN_PROGRESS** (0x37) Nie określono oczekiwania, próba połączenia jest w toku.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort *.*
- **NX_PTR_ERROR** (0x07) Błąd wskaźnika gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
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

Ta usługa umożliwia nasłuchiwanie żądania połączenia klienta na określonym porcie TCP. Po otrzymaniu żądania połączenia klienta podane gniazdo serwera jest powiązane z określonym portem i wywoływana jest podana funkcja wywołania zwrotnego nasłuchiwać.

Przetwarzanie procedury wywołania zwrotnego nasłuchiwać jest całkowicie do aplikacji. Może ona zawierać logikę wznawiania wątku aplikacji, który następnie wykonuje operację akceptowania. Jeśli aplikacja ma już wątek zawieszony podczas akceptowania przetwarzania dla tego gniazda, procedura wywołania zwrotnego nasłuchiwać może nie być potrzebna.

Jeśli aplikacja chce obsługiwać dodatkowe połączenia klienta na  tym samym porcie, nx_tcp_server_socket_relisten musi zostać wywołana przy użyciu dostępnego gniazda (gniazda w stanie ZAMKNIĘTY) dla następnego połączenia. Dopóki usługa ponownego nasłuchiwać nie zostanie wywołana, dodatkowe połączenia klienta są kolejkowane. Po przekroczeniu maksymalnej głębokości kolejki najstarsze żądanie połączenia jest porzucane na rzecz kolejkowania nowego żądania połączenia. Maksymalna głębokość kolejki jest określana przez tę usługę.

*Procedury wywołania zwrotnego aplikacji są wywoływane z wewnętrznego wątku pomocnika IP.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **port** Numer portu do nasłuchiwać (od 1 do 0xFFFF).
- **socket_ptr** Wskaźnik do gniazda do użycia dla połączenia.
- **listen_queue_size** Liczba żądań połączenia klienta, które mogą być w kolejce.
- **listen_callback** Funkcja Application do wywołania po otrzymaniu połączenia. Jeśli określono wartość NULL, funkcja wywołania zwrotnego nasłuchiwać jest wyłączona.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne włączenie nasłuchiwać portów TCP.
- **NX_MAX_LISTEN** (0x33) Nie są dostępne żadne struktury żądań nasłuchiwać. Stała w NX_MAX_LISTEN_REQUESTS w nx_api.h definiuje, ile aktywnych żądań nasłuchiwać jest możliwych.
- **NX_NOT_CLOSED** (0x35) Podane gniazdo serwera nie jest w stanie zamkniętym.
- **NX_ALREADY_BOUND** (0x22) Podane gniazdo serwera jest już powiązane z portem.
- **NX_DUPLICATE_LISTEN** (0x34) Istnieje już aktywne żądanie nasłuchiwać dla tego portu.
- **NX_INVALID_PORT** (0x46) Określono nieprawidłowy port.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP lub gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten

Ponowne nasłuchiwać połączenia klienta na porcie TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa jest wywoływana po otrzymaniu połączenia na porcie, który był wcześniej konfigurował nasłuchiwanie. Głównym celem tej usługi jest zapewnienie nowego gniazda serwera na potrzeby następnego połączenia klienta. Jeśli żądanie połączenia jest w kolejce, połączenie zostanie przetworzone natychmiast podczas tego wywołania usługi.

*Ta sama procedura wywołania zwrotnego określona przez oryginalne żądanie nasłuchiwu jest również wywoływana, gdy połączenie jest obecne dla tego nowego gniazda serwera.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **port** Numer portu do ponownego nasłuchiwać (od 1 do 0xFFFF).
- **socket_ptr** Gniazdo do użycia dla następnego połączenia klienta.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne ponowne nasłuchiwać portu TCP.
- **NX_NOT_CLOSED** (0x35) Podane gniazdo serwera nie jest w stanie zamkniętym.
- **NX_ALREADY_BOUND** (0x22) Podane gniazdo serwera jest już powiązane z portem.
- **NX_INVALID_RELISTEN** (0x47) Istnieje już prawidłowy wskaźnik gniazda dla tego portu lub określony port nie ma aktywnego żądania nasłuchiwać.
- **NX_CONNECTION_PENDING** (0x48) To samo co NX_SUCCESS, z wyjątkiem żądania połączenia w kolejce, które zostało przetworzone podczas tego wywołania.
- **NX_INVALID_PORT** (0x46) Określono nieprawidłowy port.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy adres IP lub wskaźnik wywołania zwrotnego nasłuchiwać.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,
- nx_tcp_socket_bytes_available, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept

Usuwanie skojarzenia gniazda z portem nasłuchiwania

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa skojarzenie między tym gniazdem serwera i określonym portem serwera. Aplikacja musi wywołać tę usługę po rozłączeniu lub po nieudanym wywołaniu akceptowania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do poprzednio konfiguracji wystąpienia gniazda serwera.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne coakceptuj gniazda serwera.
- **NX_NOT_LISTEN_STATE** (0x36) Serwer jest w nieprawidłowym stanie i prawdopodobnie nie jest odłączony.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,
- nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,
- nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
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

- **NX_SUCCESS** (0x00) Pomyślne wyłączenie nasłuchiwać TCP.
- **NX_ENTRY_NOT_FOUND** (0x16) Nasłuchiwanie nie zostało włączone dla określonego portu.
- **NX_INVALID_PORT** (0x46) Określono nieprawidłowy port.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
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

Ta usługa uzyskuje liczbę bajtów dostępnych do pobrania w określonym gnieździe TCP. Należy pamiętać, że gniazdo TCP musi być już połączone.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego i połączonego gniazda TCP.
- **bytes_available** Wskaźnik do miejsca docelowego dla dostępnych bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Service zostanie pomyślnie wykonany. Liczba bajtów dostępnych do odczytu jest zwracana do wywołującego.
- **NX_NOT_CONNECTED** (0x38) Socket nie jest w stanie połączenia.
- **NX_PTR_ERROR** (0x07) Nieprawidłowe wskaźniki.
- **NX_NOT_ENABLED** (0x14) TCP nie jest włączony.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_create,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create

Tworzenie klienta TCP lub gniazda serwera

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

Ta usługa tworzy klienta TCP lub gniazdo serwera dla określonego wystąpienia adresu IP.

*Procedury wywołania zwrotnego aplikacji są wywoływane z wątku skojarzonego z tym wystąpieniem adresu IP.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **socket_ptr** Wskaźnik do nowego bloku sterowania gniazda TCP.
- **name (nazwa)** Nazwa aplikacji dla tego gniazda TCP.
- **type_of_service** Definiuje typ usługi transmisji, a wartości prawne są następujące:

- NX_IP_NORMAL (0x00000000)
- NX_IP_MIN_DELAY (0x00100000)
- NX_IP_MAX_DATA (0x00080000)
- NX_IP_MAX_RELIABLE (0x00040000)
- NX_IP_MIN_COST (0x00020000)

- **fragment**  Określa, czy fragmentowanie adresów IP jest dozwolone. Jeśli NX_FRAGMENT_OKAY (0x0) jest określony, fragmentowanie adresów IP jest dozwolone. Jeśli NX_DONT_FRAGMENT (0x4000) jest określony, fragmentowanie adresów IP jest wyłączone.
- **time_to_live** Określa wartość 8-bitową, która definiuje liczbę routerów, które pakiet może przekazać, zanim zostanie wyrzucony. Wartość domyślna jest określana przez NX_IP_TIME_TO_LIVE.
- **window_size** Określa maksymalną dozwoloną liczbę bajtów w kolejce odbierania dla tego gniazda
- **urgent_data_callback** Funkcja aplikacji wywoływana za każdym razem, gdy w strumieniu odbierania zostaną wykryte pilne dane. Jeśli ta wartość jest NX_NULL, pilne dane są ignorowane.
- **disconnect_callback** Funkcja aplikacji wywoływana za każdym razem, gdy gniazdo na drugim końcu połączenia wystawia rozłączenie. Jeśli ta wartość jest NX_NULL, funkcja wywołania zwrotnego rozłączenia jest wyłączona.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne utworzenie gniazda klienta TCP.
- **NX_OPTION_ERROR** (0x0A) Nieprawidłowy typ usługi, fragment, nieprawidłowy rozmiar okna lub opcja czasu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP lub gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,
- nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete

Usuwanie gniazda TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone gniazdo TCP. Jeśli gniazdo jest nadal powiązane lub połączone, usługa zwraca kod błędu.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wcześniej utworzone gniazdo TCP

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie gniazda.
- **NX_NOT_CREATED** (0x27) Nie utworzono gniazda.
- **NX_STILL_BOUND** (0x42) Gniazdo jest nadal powiązane.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
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

Ta usługa rozłącza nawiązane połączenie klienta lub gniazda serwera. Po odłączeniu gniazda serwera powinno nasłonić żądanie nieakceptowane, a odłączone gniazdo klienta pozostaje w stanie gotowym na inne żądanie połączenia. Jeśli proces rozłączania nie może zakończyć się natychmiast, usługa zostanie wstrzymana zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego klienta lub wystąpienia gniazda serwera.
- **wait_option** Określa, jak usługa zachowuje się, gdy rozłączenie jest w toku. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne rozłączenie gniazda.
- **NX_NOT_CONNECTED** (0x38) Określone gniazdo nie jest połączone.
- **NX_IN_PROGRESS** (0x37) Rozłączanie jest w toku, nie określono oczekiwania.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify

Instalowanie pełnej funkcji wywołania zwrotnego powiadamiania o rozłączeniu protokołu TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana po zakończeniu operacji rozłączenia gniazda. Funkcja kompletnego wywołania zwrotnego rozłączenia gniazda TCP jest dostępna, jeśli netx jest sbudowaną opcją

- ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** zdefiniowane.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego klienta lub wystąpienia gniazda serwera.
- **tcp_disconnect_complete_notify** Funkcja wywołania zwrotnego do zainstalowania.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślnie zarejestrowano funkcję wywołania zwrotnego.
- **NX_NOT_SUPPORTED** (0x4B) Funkcja rozszerzonego powiadamiania nie jest wbudowana w bibliotekę NetX
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) TCP nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,
- nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,
- nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,
- nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,
- nx_tcp_socket_transmit_configure,
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify

Ustawianie funkcji wywołania zwrotnego powiadamiania protokołu TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana po nawiązaniu połączenia przez gniazdo TCP. Funkcja wywołania zwrotnego establish gniazda TCP jest dostępna,  jeśli netx jest budowy z NX_ENABLE_EXTENDED_NOTIFY_SUPPORT opcją.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego klienta lub wystąpienia gniazda serwera.
- **tcp_establish_notify** Funkcja wywołania zwrotnego wywoływana po nawiązaniu połączenia TCP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie ustawia funkcję notify.
- **NX_NOT_SUPPORTED** (0x4B) Funkcja rozszerzonego powiadamiania nie jest wbudowana w bibliotekę NetX
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) TCP nie został włączony przez aplikację.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o działaniach gniazda TCP

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

*Jeśli wskaźnik docelowy jest NX_NULL, te konkretne informacje nie są zwracane do wywołującego.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **tcp_packets_sent** Wskaźnik do miejsca docelowego całkowitej liczby pakietów TCP wysyłanych na gniazdo.
- **tcp_bytes_sent** Wskaźnik do miejsca docelowego całkowitej liczby bajtów TCP wysłanych na gniazdo.
- **tcp_packets_received** Wskaźnik do miejsca docelowego całkowitej liczby pakietów TCP odebranych na gnieździe.
- **tcp_bytes_received** Wskaźnik do miejsca docelowego całkowitej liczby bajtów TCP odebranych na gnieździe.
- **tcp_retransmit_packets** Wskaźnik do miejsca docelowego całkowitej liczby ponownych transmisji pakietów TCP.
- **tcp_packets_queued** Wskaźnik do miejsca docelowego całkowitej liczby pakietów TCP w kolejce na gnieździe.
- **tcp_checksum_errors** Wskaźnik do miejsca docelowego całkowitej liczby pakietów TCP z błędami sumy kontrolnej na gnieździe.
- **tcp_socket_state** Wskaźnik do miejsca docelowego bieżącego stanu gniazda.
- **tcp_transmit_queue_depth** Wskaźnik do miejsca docelowego całkowitej liczby pakietów przesyłanych nadal w kolejce oczekujących na ACK.
- **tcp_transmit_window** Wskaźnik do miejsca docelowego bieżącego rozmiaru okna przesyłania.
- **tcp_receive_window** Wskaźnik do miejsca docelowego bieżącego rozmiaru okna odbierania.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pobieranie informacji o pomyślnym gnieździe TCP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

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

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get

Uzyskiwanie usługi MSS gniazda

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Opis

Ta usługa pobiera lokalny maksymalny rozmiar segmentu (MSS) określonego gniazda.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda.
- **mss** Miejsce docelowe zwracania usługi MSS.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie pobierz mss.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda lub miejsca docelowego MSS.
- **NX_NOT_ENABLED** (0x14) TCP nie jest włączony.
- **NX_CALLER_ERROR** (0x11) nie jest wątkiem ani inicjowaniem.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie usługi MSS równorzędnego gniazda TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a>Opis

Ta usługa pobiera maksymalny rozmiar segmentu (MSS) anonsowany przez gniazdo równorzędne.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego i połączonego gniazda.
- **mss** Miejsce docelowe zwracania usługi MSS.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślny równorzędny dostęp do usługi MSS.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda lub miejsca docelowego MSS.
- **NX_NOT_ENABLED** (0x14) TCP nie jest włączony.
- **NX_CALLER_ERROR** (0x11) nie jest wątkiem ani inicjowaniem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ustawianie zestawu MSS gniazda

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a>Opis

Ta usługa ustawia maksymalny rozmiar segmentu określonego gniazda (MSS). Należy pamiętać, że wartość MSS musi znajdować się w obrębie jednostki MTU ip interfejsu sieciowego, co pozwala na miejsce na nagłówki IP i TCP.

Ta usługa powinna być używana przed rozpoczęciem procesu połączenia przez gniazdo TCP. Jeśli usługa jest używana po nawiązaniu połączenia TCP, nowa wartość nie ma wpływu na połączenie.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda.
- **mss** Wartość MSS do ustawienia.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Zestaw MSS pomyślnie.
- **NX_SIZE_ERROR** (0x09) Określona wartość MSS jest zbyt duża.
- **NX_NOT_CONNECTED** (0x38) TCP nie zostało nawiązane
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_NOT_ENABLED** (0x14) TCP nie jest włączony.
- **NX_CALLER_ERROR** (0x11) nie jest wątkiem ani inicjowaniem.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o równorzędnych gniazdach TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o adresie IP elementu równorzędnego i porcie dla połączonego gniazda TCP za pośrednictwem sieci IP.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda TCP.
- **peer_ip_address** Wskaźnik do miejsca docelowego dla adresu IP elementu równorzędnego w kolejności bajtów hosta.
- **peer_port** Wskaźnik do miejsca docelowego dla numeru portu elementu równorzędnego w kolejności bajtów hosta.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Service zostanie pomyślnie wykonany. Adres IP elementu równorzędnego i numer portu są zwracane do elementu wywołującego.
- **NX_NOT_CONNECTED** (0x38) Gniazda nie jest w stanie połączenia.
- **NX_PTR_ERROR** (0x07) Nieprawidłowe wskaźniki.
- **NX_NOT_ENABLED** (0x14) TCP nie jest włączony.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ta usługa odbiera dane TCP z określonego gniazda. Jeśli żadne dane nie są kolejkowane na określonym gnieździe, wywołujący wstrzymuje się na podstawie podanej opcji oczekiwania.

*Jeśli NX_SUCCESS zwracany, aplikacja jest odpowiedzialna za zwalnianie odebranego pakietu, gdy nie jest już potrzebny.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **packet_ptr** Wskaźnik do wskaźnika pakietów TCP.
- **wait_option** Definiuje zachowanie usługi, jeśli żadne dane nie są obecnie w kolejce na tym gnieździe. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślne odbieranie danych gniazda.
- **NX_NOT_BOUND** (0x24) Socket nie jest jeszcze powiązany.
- **NX_NO_PACKET** (0x01) Nie odebrano żadnych danych.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_NOT_CONNECTED** (0x38) Gniazdo nie jest już połączone.
- **NX_PTR_ERROR** (0x07) Nieprawidłowe gniazdo lub wskaźnik pakietów powrotnych.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

/* Odbierz pakiet z wcześniej utworzonego i połączonego gniazda klienta TCP. Jeśli pakiet nie jest dostępny, zaczekaj na 200 takt czasomierzy przed rezygnacją. */ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* Jeśli stan jest NX_SUCCESS, odebrany pakiet jest wskazywany przez "packet_ptr". */

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,
- nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,
- nx_tcp_socket_send, nx_tcp_socket_state_wait

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify

Powiadamianie aplikacji o odebranych pakietach


### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa konfiguruje wskaźnik funkcji receive notify z funkcją wywołania zwrotnego określoną przez aplikację. Ta funkcja wywołania zwrotnego jest następnie wywoływana za każdym razem, gdy co najmniej jeden pakiet zostanie odebrany w gnieździe. Jeśli zostanie NX_NULL wskaźnik, funkcja notify zostanie wyłączona.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do gniazda TCP.
- **tcp_receive_notify** Wskaźnik funkcji wywołania zwrotnego aplikacji wywoływany po otrzymaniu co najmniej jednego pakietu w gnieździe.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Powiadomienie o pomyślnym otrzymaniu gniazda.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) TCP nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ta usługa wysyła dane TCP za pośrednictwem wcześniej połączonego gniazda TCP. Jeśli rozmiar okna ostatnio anonsowanego odbiornika jest mniejszy niż to żądanie, usługa opcjonalnie wstrzymuje się na podstawie określonej opcji oczekiwania. Ta usługa gwarantuje, że żadne dane pakietu większe niż MSS są wysyłane do warstwy ip.

*Jeśli nie zostanie zwrócony błąd, aplikacja nie powinna zwalniać pakietu po tym wywołaniu. Spowoduje to nieprzewidywalne wyniki, ponieważ sterownik sieciowy spróbuje również zwolnić pakiet po zakończeniu transmisji.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia gniazda TCP.
- **packet_ptr** Wskaźnik pakietu danych TCP.
- **wait_option** Definiuje zachowanie usługi, jeśli żądanie jest większe niż rozmiar okna odbiornika. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wysłanie gniazda.
- **NX_NOT_BOUND** (0x24) Gniazdo nie zostało powiązane z żadnym portem.
- **NX_NO_INTERFACE_ADDRESS** (0x50) Nie znaleziono odpowiedniego interfejsu wychodzącego.
- **NX_NOT_CONNECTED** (0x38) Socket is no longer connected (Gniazdo (0x38) nie jest już połączone.
- **NX_WINDOW_OVERFLOW** (0x39) Jest większe niż rozmiar okna anonsowanego odbiornika w bajtach.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_INVALID_PACKET** (0x12) pakiet nie jest przydzielony.
- **NX_TX_QUEUE_DEPTH** (0x49) Osiągnięto maksymalną głębokość kolejki przesyłania.
- **NX_OVERFLOW** (0x03) Wskaźnik dołączania pakietów jest nieprawidłowy.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.
- **NX_UNDERFLOW** (0x02) Wskaźnik dołączany pakiet jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait

### <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait

Oczekiwanie na wprowadzenie określonego stanu przez gniazdo TCP

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa czeka na wprowadzenie żądanego stanu gniazda. Jeśli gniazdo nie jest w żądanym stanie, usługa wstrzymuje się zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia gniazda TCP.
- **desired_state** Żądany stan TCP. Prawidłowe stany gniazd TCP są zdefiniowane w następujący sposób:
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
- **wait_option** Definiuje zachowanie usługi, jeśli żądany stan nie istnieje. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Oczekiwanie na powodzenie stanu.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_NOT_SUCCESSFUL** (0x43) Stan nie występuje w określonym czasie oczekiwania.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.
- **NX_OPTION_ERROR** (0x0A) Żądany stan gniazda jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
- nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,
- nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,
- nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,
- nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,
- nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,
- nx_tcp_socket_info_get, nx_tcp_socket_receive,
- nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback

Instalowanie wywołania zwrotnego dla stanu oczekiwania z czasem

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana, gdy gniazdo TCP jest w stanie oczekiwania z czasem. Aby można było korzystać z tej usługi, biblioteka NetX musi zostać s zbudowana przy użyciu ***NX_ENABLE_EXTENDED_NOTIFY*** zdefiniowanej opcji.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego klienta lub wystąpienia gniazda serwera.
- **tcp_timed_wait_callback** Funkcja wywołania zwrotnego oczekiwania z czasem

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślnie rejestruje gniazdo funkcji wywołania zwrotnego
- **NX_NOT_SUPPORTED** (0x4B) biblioteka NetX jest łączona bez włączonej funkcji rozszerzonego powiadamiania.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) TCP nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Konfigurowanie parametrów przesyłania gniazda

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

Ta usługa konfiguruje różne parametry przesyłania określonego gniazda TCP.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do gniazda TCP.
- **max_queue_depth** Maksymalna liczba pakietów, które mogą być w kolejce do transmisji.
- **limit czasu** Liczba znaczników czasomierza ThreadX, na które czeka ACK, zanim pakiet zostanie wysłany ponownie.
- **max_retries** Dozwolona maksymalna liczba ponownych prób.
- **timeout_shift** Wartość do zmiany limitu czasu dla każdej kolejnej próby ponownego wykonania. Wartość 0 powoduje ten sam limit czasu między kolejnymi próbami. Wartość 1 podwaja limit czasu między ponownych prób.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Pomyślna konfiguracja gniazda przesyłania.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_OPTION_ERROR** (0x0a) Nieprawidłowa opcja głębokości kolejki.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) TCP nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Powiadamianie aplikacji o aktualizacjach rozmiaru okna

### <a name="prototype"></a>Prototype

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa instaluje procedurę wywołania zwrotnego aktualizacji okna gniazda. Ta procedura jest wywoływana automatycznie za każdym razem, gdy określone gniazdo odbiera pakiet wskazujący wzrost rozmiaru okna hosta zdalnego.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda TCP.
- **tcp_window_update_notify** Procedura wywołania zwrotnego, która ma być wywoływana po zmianie rozmiaru okna. Wartość NULL wyłącza aktualizację zmiany okna.

### <a name="return-values"></a>Wartości zwrócone
- **NX_SUCCESS** (0x00) Procedura wywołania zwrotnego jest zainstalowana na gnieździe.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_PTR_ERROR** (0x07) Nieprawidłowe wskaźniki.
- **NX_NOT_ENABLED** (0x14) TCP nie jest włączona.


### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Włączanie składnika UDP netx

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa włącza składnik protokołu UDP (User Datagram Protocol) netx. Po włączeniu można wysyłać i odbierać datagramy protokołu UDP przez aplikację.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne włączenie protokołu UDP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_ALREADY_ENABLED** (0x15) Ten składnik został już włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find

Znajdowanie następnego dostępnego portu UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyszukuje bezpłatny port UDP (niepowiązany) rozpoczynający się od numeru portu podanego przez aplikację. Logika wyszukiwania zawinie się, jeśli wyszukiwanie osiągnie maksymalną wartość portu 0xFFFF. Jeśli wyszukiwanie powiedzie się, bezpłatny port jest zwracany w zmiennej wskazywanej przez free_port_ptr *.*

*Ta usługa może być wywoływana z innego wątku i może mieć zwrócony ten sam port. Aby zapobiec sytuacji wyścigu, aplikacja może chcieć umieścić tę usługę i rzeczywiste powiązanie gniazda pod ochroną obiektu mutex.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **port** Numer portu do rozpoczęcia wyszukiwania (od 1 do 0xFFFF).
- **free_port_ptr** Wskaźnik do zmiennej zwracania wolnego portu docelowego.


### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne znalezienie bezpłatnego portu.
- **NX_NO_FREE_PORTS** (0x45) Nie znaleziono wolnych portów.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.
- **NX_INVALID_PORT** (0x46) Określony numer portu jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get

Pobieranie informacji o działaniach UDP

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

Ta usługa pobiera informacje o działaniach UDP dla określonego wystąpienia adresu IP.

*Jeśli wskaźnik docelowy jest NX_NULL, te konkretne informacje nie są zwracane do wywołującego.*

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **udp_packets_sent** Wskaźnik do miejsca docelowego całkowitej liczby wysłanych pakietów UDP.
- **udp_bytes_sent** Wskaźnik do miejsca docelowego całkowitej liczby wysłanych bajtów UDP.
- **udp_packets_received** Wskaźnik do miejsca docelowego całkowitej liczby odebranych pakietów UDP.
- **udp_bytes_received** Wskaźnik do miejsca docelowego całkowitej liczby odebranych bajtów UDP.
- **udp_invalid_packets** Wskaźnik do miejsca docelowego całkowitej liczby nieprawidłowych pakietów UDP.
- **udp_receive_packets_dropped** Wskaźnik do miejsca docelowego całkowitej liczby porzuconych pakietów odbieranych przez UDP.
- **udp_checksum_errors** Wskaźnik do miejsca docelowego całkowitej liczby pakietów UDP z błędami sumy kontrolnej.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pobieranie informacji protokołu UDP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik IP.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.


### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract

Wyodrębnianie parametrów sieciowych z pakietu UDP

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

Ta usługa wyodrębnia parametry sieci, takie jak adres IP, numer portu równorzędnego, typ protokołu (ta usługa zawsze zwraca typ UDP) z pakietu odebranego w interfejsie przychodzącym.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu.
- **ip_address** Wskaźnik do adresu IP nadawcy.
- **protokół** Wskaźnik do protokołu (UDP).
- **port** Wskaźnik do numeru portu nadawcy.
- **interface_index** Wskaźnik do odbierania indeksu interfejsu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Dane interfejsu pakietu zostały pomyślnie wyodrębnione.
- **NX_INVALID_PACKET** (0x12) Pakiet nie zawiera ramki IP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowe dane wejściowe wskaźnika
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_socket_bind, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind

Wiązanie gniazda UDP z portem UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a>Opis

Ta usługa wiąże wcześniej utworzone gniazdo UDP z określonym portem UDP. Prawidłowe gniazda UDP zakres od 0 do 0xFFFF. Jeśli żądany numer portu jest powiązany z innym gniazdem, ta usługa czeka przez określony czas, aż gniazdo zostanie odłączone od numeru portu.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.
- **port** Numer portu do powiązania (od 1 do 0xFFFF). Jeśli numer portu jest NX_ANY_PORT (0x0000), wystąpienie adresu IP wyszuka następny bezpłatny port i użyje go dla powiązania.
- **wait_option** Definiuje zachowanie usługi, jeśli port jest już powiązany z innym gniazdem. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne powiązanie gniazda.
- **NX_ALREADY_BOUND** (0x22) To gniazdo jest już powiązane z innym portem.
- **NX_PORT_UNAVAILABLE** (0x23) port jest już powiązany z innym gniazdem.
- **NX_NO_FREE_PORTS** (0x45) Brak bezpłatnego portu.
- **NX_WAIT_ABORTED** (0x1A) Żądanie zawieszenia zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_INVALID_PORT** (0x46) Określono nieprawidłowy port.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bytes_available,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
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

Ta usługa pobiera liczbę bajtów dostępnych do odbioru w określonym gnieździe UDP.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda UDP.
- **bytes_available** Wskaźnik do miejsca docelowego dla dostępnych bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Dostępne bajty pomyślne.
- **NX_NOT_SUCCESSFUL** (0x43) nie jest powiązane z portem.
- **NX_PTR_ERROR** (0x07) Nieprawidłowe wskaźniki.
- **NX_NOT_ENABLED** (0x14) UDP nie jest włączona.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable

Wyłączanie sumy kontrolnej dla gniazda UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza logikę sumy kontrolnej wysyłania i odbierania pakietów na określonym gnieździe UDP. Gdy logika sumy kontrolnej jest wyłączona, wartość zero jest ładowana do pola sumy kontrolnej nagłówka UDP dla wszystkich pakietów wysyłanych przez to gniazdo. Wartość sumy kontrolnej o wartości zerowej w nagłówku UDP sygnalizuje odbiornikowi, że dla tego pakietu nie jest obliczana wartość sumy kontrolnej.

Należy również zauważyć, że nie ma to wpływu, jeśli ***NX_DISABLE_UDP_RX_CHECKSUM** _ i _ *_NX_DISABLE_UDP_TX_CHECKSUM_** są zdefiniowane podczas odbierania i wysyłania pakietów UDP odpowiednio.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Wyłączenie sumy kontrolnej pomyślnego gniazda.
- **NX_NOT_BOUND** (0x24) Gniazda nie jest powiązana.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierz

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable

Włączanie sumy kontrolnej dla gniazda UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa umożliwia logikę sumy kontrolnej wysyłania i odbierania pakietów na określonym gnieździe UDP. Sumy kontrolne obejmują cały obszar danych UDP oraz nagłówek pseudo-IP.

Należy również zauważyć, że nie ma to wpływu, **jeśli NX_DISABLE_UDP_RX_CHECKSUM** i **NX_DISABLE_UDP_TX_CHECKSUM** są zdefiniowane podczas odbierania i wysyłania pakietów UDP.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Włączenie sumy kontrolnej pomyślnego gniazda.
- **NX_NOT_BOUND** (0x24) Gniazda nie jest powiązana.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierz

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,
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

Ta usługa tworzy gniazdo UDP dla określonego wystąpienia adresu IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **socket_ptr** Wskaźnik do nowego bloku sterowania gniazdami UDP.
- **name (nazwa)** Nazwa aplikacji dla tego gniazda UDP.
- **type_of_service** Definiuje typ usługi transmisji, a wartości prawne są następujące:
    - NX_IP_NORMAL (0x00000000)
    - NX_IP_MIN_DELAY (0x00100000)
    - NX_IP_MAX_DATA (0x00080000)
    - NX_IP_MAX_RELIABLE (0x00040000)
    - NX_IP_MIN_COST (0x00020000)
- **fragment** Określa, czy fragmentowanie adresów IP jest dozwolone. Jeśli NX_FRAGMENT_OKAY (0x0) jest określony, fragmentowanie adresów IP jest dozwolone. Jeśli NX_DONT_FRAGMENT (0x4000) jest określony, fragmentowanie adresów IP jest wyłączone.
- **time_to_live** Określa wartość 8-bitową, która definiuje liczbę routerów, które pakiet może przekazać, zanim zostanie wyrzucony. Wartość domyślna jest określana przez NX_IP_TIME_TO_LIVE.
- **queue_maximum** Definiuje maksymalną liczbę datagramów protokołu UDP, które można dodać do kolejki dla tego gniazda. Po osiągnięciu limitu kolejki dla każdego odebranego nowego pakietu zwalniany jest najstarszy pakiet UDP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne utworzenie gniazda UDP.
- **NX_OPTION_ERROR** (0x0A) Nieprawidłowa opcja typu usługi, fragmentu lub czasu eksploatacji.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy adres IP lub wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_delete,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete

Usuwanie gniazda UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzone gniazdo UDP. Jeśli gniazdo zostało powiązane z portem, najpierw musi być niepowiązane.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne usunięcie gniazda.
- **NX_STILL_BOUND** (0x42) gniazdo jest nadal powiązane.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_info_get, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get

Pobieranie informacji o działaniach gniazd UDP

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

*Jeśli wskaźnik docelowy jest NX_NULL, te konkretne informacje nie są zwracane do wywołującego.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do utworzonego wcześniej wystąpienia gniazda UDP.
- **udp_packets_sent** Wskaźnik do miejsca docelowego całkowitej liczby pakietów UDP wysyłanych na gniazdo.
- **udp_bytes_sent** Wskaźnik do miejsca docelowego całkowitej liczby bajtów UDP wysłanych na gniazdo.
- **udp_packets_received** Wskaźnik do miejsca docelowego całkowitej liczby pakietów UDP odebranych na gnieździe.
- **udp_bytes_received** Wskaźnik do miejsca docelowego całkowitej liczby bajtów UDP odebranych na gnieździe.
- **udp_packets_queued** Wskaźnik do miejsca docelowego całkowitej liczby pakietów UDP w kolejce na gnieździe.
- **udp_receive_packets_dropped** Wskaźnik do miejsca docelowego całkowitej liczby pakietów odbierania UDP porzucanych dla gniazda z powodu przekroczenia rozmiaru kolejki.
- **udp_checksum_errors** Wskaźnik do miejsca docelowego całkowitej liczby pakietów UDP z błędami sumy kontrolnej na gnieździe.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne pobieranie informacji o gniazdach UDP.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_port_get,
- nx_udp_socket_receive, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get

Odbiór numeru portu powiązanego z gniazdem UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a>Opis

Ta usługa pobiera numer portu skojarzony z gniazdem, co jest przydatne do znalezienia portu przydzielonego przez netx w sytuacjach, NX_ANY_PORT został określony w czasie, gdy gniazdo zostało powiązane.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.
- **port_ptr** Wskaźnik do miejsca docelowego dla numeru portu powrotu. Prawidłowe numery portów to (od 1 do 0xFFFF).

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne powiązanie gniazda.
- **NX_NOT_BOUND** (0x24) To gniazdo nie jest powiązane z portem.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda lub wskaźnik powrotu portu.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Nie

### <a name="example"></a>Przykład

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
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

Ta usługa odbiera datagram UDP z określonego gniazda. Jeśli na określonym gnieździe nie ma żadnego datagramu, wywołujący wstrzymuje się na podstawie podanej opcji oczekiwania.

*Jeśli NX_SUCCESS zostanie zwrócony, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebny.*

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.
- **packet_ptr** Wskaźnik do wskaźnika pakietu datagramu UDP.
- **wait_option** Definiuje zachowanie usługi, jeśli datagram nie jest obecnie w kolejce na tym gnieździe. Opcje oczekiwania są zdefiniowane w następujący sposób:
- NX_NO_WAIT (0x00000000)
- NX_WAIT_FOREVER (0xFFFFFFFF)
- wartość limitu czasu w taktach (0x00000001 do 0xFFFFFFFE)

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive_notify,
- nx_udp_socket_send, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify

Powiadamianie aplikacji o każdym odebranym pakiecie

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a>Opis

Ta usługa ustawia wskaźnik funkcji odbierania powiadomienia do funkcji wywołania zwrotnego określonej przez aplikację. Ta funkcja wywołania zwrotnego jest następnie wywoływana za każdym razem, gdy na gnieździe zostanie odebrany pakiet. Jeśli zostanie NX_NULL, funkcja powiadamiania o odbierania jest wyłączona.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do gniazda UDP.
- **udp_receive_notify** Wskaźnik funkcji wywołania zwrotnego aplikacji, który jest wywoływany po otrzymaniu pakietu na gnieździe.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind,
- nx_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send

Wysyłanie datagramów UDP

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a>Opis

Ta usługa wysyła datagram UDP za pośrednictwem wcześniej utworzonego i powiązanego gniazda UDP. NetX znajduje odpowiedni lokalny adres IP jako adres źródłowy na podstawie docelowego adresu IP. Aby określić określony interfejs i źródłowy adres IP, aplikacja powinna używać **nx_udp_socket_interface_send** ip.

Należy pamiętać, że ta usługa zwraca natychmiast, niezależnie od tego, czy datagram protokołu UDP został pomyślnie wysłany.

Gniazdo musi być powiązane z portem lokalnym.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP
- **packet_ptr** Wskaźnik pakietu datagramu UDP
- **ip_address** Docelowy adres IP
- **port** Prawidłowy numer portu docelowego od 1 do 0xFFFF) w kolejności bajtów hosta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wysłanie gniazda UDP
- **NX_NOT_BOUND** (0x24) nie jest powiązane z żadnym portem
- **NX_NO_INTERFACE_ADDRESS** (0x50) Nie można znaleźć odpowiedniego interfejsu wychodzącego.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP serwera
- **NX_UNDERFLOW** (0x02) Za mało miejsca dla nagłówka UDP w pakiecie
- **NX_OVERFLOW** (0x03) Wskaźnik dołączania pakietów jest nieprawidłowy
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę
- **NX_NOT_ENABLED** (0x14) UDP nie został włączony
- **NX_INVALID_PORT** (0x46) Numer portu nie znajduje się w prawidłowym zakresie

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_interface_send,
- nx_udp_socket_unbind, nx_udp_source_extract

## <a name="nx_udp_socket_interface_send"></a>nx_udp_socket_interface_send

Wysyłanie datagramu za pośrednictwem gniazda UDP.

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

Ta usługa wysyła datagram UDP za pośrednictwem wcześniej utworzonego i powiązanego gniazda UDP za pośrednictwem interfejsu sieciowego z określonym adresem IP jako adresem źródłowym. Należy pamiętać, że usługa zwraca natychmiast, niezależnie od tego, czy datagram UDP został pomyślnie wysłany.

### <a name="parameters"></a>Parametry

- **socket_ptr** Gniazdo do przesyłania pakietu na zewnątrz.
- **packet_ptr** Wskaźnik do pakietu, który ma być przesyłany.
- **ip_address** Docelowy adres IP do wysłania pakietu.
- **port** Port docelowy.
- **address_index** Indeks adresu skojarzonego z interfejsem do wysyłania pakietów.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pakiet został pomyślnie wysłany.
- **NX_NOT_BOUND** (0x24) socket nie jest powiązany z portem.
- **NX_IP_ADDRESS_ERROR** (0x21) Nieprawidłowy adres IP.
- **NX_NOT_ENABLED** (0x14) UDP nie jest włączone.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik.
- **NX_OVERFLOW** (0x03) Nieprawidłowy wskaźnik dołączania pakietów.
- **NX_UNDERFLOW** (0x02) Nieprawidłowy wskaźnik wstępnie dołączanych pakietów.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_INVALID_INTERFACE** (0x4C) Nieprawidłowy indeks adresów.
- **NX_INVALID_PORT** (0x46) Numer portu przekracza maksymalną liczbę portów.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_unbind

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind

Odłącz gniazdo UDP od portu UDP.

### <a name="prototype"></a>Prototype

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwalnia powiązanie między gniazdem UDP i portem UDP. Wszystkie odebrane pakiety przechowywane w kolejce odbierania są zwalniane w ramach operacji bez wiązania.

Jeśli istnieją inne wątki oczekujące na powiązanie innego gniazda z portem niepowiązanych, pierwszy wstrzymany wątek jest następnie powiązany z nowo niepowiązaną portem.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne powiązycie gniazda.
- **NX_NOT_BOUND** (0x24) nie zostało powiązane z żadnym portem.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0x11) Nieprawidłowy wywołujący tę usługę.
- **NX_NOT_ENABLED** (0x14) Ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

Tak

### <a name="example"></a>Przykład

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract

Wyodrębnianie adresu IP i wysyłanie portu z datagramu UDP

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
- **ip_address** Prawidłowy wskaźnik do zmiennej zwracanych adresów IP.
- **port** Prawidłowy wskaźnik do zmiennej portu powrotu.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) Pomyślne wyodrębnianie źródłowego adresu IP/portu.
- **NX_INVALID_PACKET** (0x12) Podany pakiet jest nieprawidłowy.
- **NX_PTR_ERROR** (0x07) Nieprawidłowy pakiet, adres IP lub port docelowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze, ISR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

- nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,
- nx_udp_packet_info_extract, nx_udp_socket_bind,
- nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,
- nx_udp_socket_checksum_enable, nx_udp_socket_create,
- nx_udp_socket_delete, nx_udp_socket_info_get,
- nx_udp_socket_port_get, nx_udp_socket_receive,
- nx_udp_socket_receive_notify, nx_udp_socket_send,
- nx_udp_socket_interface_send, nx_udp_socket_unbind