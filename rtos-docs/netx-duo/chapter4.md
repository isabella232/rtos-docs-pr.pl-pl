---
title: Rozdział 4 — Opis usług Azure RTO NetX Duo
description: Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Duo w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 85617aadab7f484a4f4e467fd13f815f4d8b5609
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822950"
---
# <a name="chapter-4---description-of-azure-rtos-netx-duo-services"></a>Rozdział 4 — Opis usług Azure RTO NetX Duo

Ten rozdział zawiera opis wszystkich usług Azure RTO NetX Duo w porządku alfabetycznym. Nazwy usług są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem. Na przykład wszystkie usługi ARP znajdują się na początku tego rozdziału. 

W NetX Duo wprowadzono liczne nowe usługi do obsługi protokołów i operacji opartych na protokole IPv6. Usługi z obsługą protokołu IPv6 w sieci .NET Duo mają prefiks ***NXD**, * wskazujący, że są przeznaczone do operacji dwustosowych protokołów IPv4 i IPv6.

Istniejące usługi w NetX są w pełni obsługiwane w NetX Duo. Aplikacje NetX można migrować do NetX Duo z minimalnym nakładem pracy.

> [!NOTE]
> *Należy pamiętać, że interfejs API usługi BSD-Compatible Socket jest dostępny dla starszego kodu aplikacji, który nie może w pełni korzystać z interfejsu API NetX Duo o wysokiej wydajności. Aby uzyskać więcej informacji na temat interfejsu API BSD-Compatible gniazda, zobacz Dodatek D*.

W sekcji "wartości zwracane" w każdym opisie wartości **pogrubione** nie wpływają na wartość opcji NX_DISABLE_ERROR_CHECKING używanej do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości w trybie niepogrubionym są całkowicie wyłączone. Sekcje "dozwolone od" wskazują, z których można wywołać każdą usługę NetX Duo.

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate   
Unieważnienie wszystkich wpisów dynamicznych w pamięci podręcznej ARP

### <a name="prototype"></a>Prototype     

```c
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

/* If status is NX_SUCCESS the dynamic ARP entries were
   successfully invalidated. */
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set  
Ustawianie dynamicznego wpisu ARP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Setup a dynamic ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
                                  0x1022, 0x1234);

/* If status is NX_SUCCESS, there is now a dynamic mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   10:22:00:00:12:34. */
```
### <a name="see-also"></a>Zobacz też 

- nx_arp_dynamic_entries_invalidate
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_enable"></a>nx_arp_enable  
Włączanie protokołu ARP (Address Resolution Protocol)

### <a name="prototype"></a>Prototype    

```c
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory,
    ULONG arp_cache_size);
```

### <a name="description"></a>Opis

Ta usługa inicjuje składnik ARP programu NetX Duo dla określonego wystąpienia IP. Inicjowanie protokołu ARP obejmuje skonfigurowanie pamięci podręcznej ARP i różnych procedur przetwarzania ARP niezbędnych do wysyłania i otrzymywania wiadomości ARP.

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

```c
/* Enable ARP and supply 1024 bytes of ARP cache memory for
   previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);

/* If status is NX_SUCCESS, ARP was successfully enabled for this IP
instance.*/
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_entry_delete"></a>nx_arp_entry_delete   
Usuwanie wpisu ARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_entry_delete(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>Opis

Ta usługa usuwa wpis ARP dla danego adresu IP z tabeli wewnętrznej protokołu ARP protokołu IP.

### <a name="parameters"></a>Parametry  

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Wpis ARP o określonym adresie IP powinien zostać usunięty.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne włączenie protokołu ARP.
- **NX_ENTRY_NOT_FOUND** (0X16) nie można znaleźć wpisu o określonym adresie IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub pamięci podręcznej.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_IP_ADDRESS_ERROR** (0X21) określony adres IP jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z  
Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie  
Nie

### <a name="example"></a>Przykład

```c
/* Delete the ARP entry with the IP address 1.2.3.4. */
status = nx_arp_entry_delete(&ip_0, IP_ADDRESS(1, 2, 3, 4));

/* If status is NX_SUCCESS, ARP entry with the specified IP address
   is deleted.*/
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send   
Wyślij żądanie żądania ARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler)(NX_IP *ip_ptr, NX_PACKET *packet_ptr));
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

```
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully
   sent. */
```

### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find
Lokalizowanie fizycznego adresu sprzętowego danego adresu IP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Search for the hardware address associated with the IP address of
   1.2.3.4 in the ARP cache of the previously created IP
   Instance 0. */
status = nx_arp_hardware_address_find(&ip_0, IP_ADDRESS(1,2,3,4),
                                      &physical_msw,
                                      &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
   physical_lsw contain the hardware address.*/
```   
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_info_get"></a>nx_arp_info_get
Pobierz informacje o działaniach ARP

### <a name="prototype"></a>Prototype  

```c
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

> [!NOTE]
> *Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego*.

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

```c
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(&ip_0, &arp_requests_sent,
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

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find
Zlokalizuj adres IP przy użyciu adresu fizycznego

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Search for the IP address associated with the hardware address of
   0x0:0x01234 in the ARP cache of the previously created IP
   Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
   associated IP address. */
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete
Usuń wszystkie statyczne wpisy ARP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Delete all the static ARP entries for IP Instance 0, assuming
   "ip_0" is the NX_IP structure for IP Instance 0. */
status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
   have been deleted. */
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create
Tworzenie statycznego adresu IP na potrzeby mapowania sprzętowego w pamięci podręcznej ARP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Create a static ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   0x00:0x1234. */
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete 
Usuń statyczny adres IP do mapowania sprzętowego w pamięci podręcznej ARP

### <a name="prototype"></a>Prototype  

```c
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
- **physical_msw** 16 najważniejszych bitów (47-* * 32) adresów fizycznych, które zostały zmapowane statycznie.
- **physical_lsw** Niższy 32 bitów (31-* * 0) adresu fizycznego, który został zamapowany statycznie.

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

```c
/* Delete a static ARP entry on the previously created IP
   instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, the previously created static ARP entry
   was successfully deleted. */
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_icmp_enable"></a>nx_icmp_enable
Włącz protokół ICMP (Internet Control Message Protocol)

### <a name="prototype"></a>Prototype  

```c
UINT nx_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa włącza składnik ICMP dla określonego wystąpienia IP. Składnik ICMP jest odpowiedzialny za obsługę internetowych komunikatów o błędach i żądań ping i odpowiedzi. 

> [!IMPORTANT]  
> *Ta usługa włącza tylko protokół ICMP dla usługi IPv4. Aby włączyć zarówno ICMPv4, jak i ICMPv6, aplikacje używają usługi **nxd_icmp_enable***.

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

```c
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```
### <a name="see-also"></a>Zobacz też

- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get
Pobierz informacje o działaniach ICMP

### <a name="prototype"></a>Prototype  

```c
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

> [!NOTE]  
> *Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego*.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **pings_sent** Wskaźnik do miejsca docelowego dla łącznej liczby wysłanych pakietów ping.
- **ping_timeouts** Wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu polecenia ping.
- **ping_threads_suspended** Wskaźnik do lokalizacji docelowej łącznej liczby wątków zawieszonych w żądaniach ping.
- **ping_responses_received** Wskaźnik do lokalizacji docelowej łącznej liczby odebranych odpowiedzi ping.
- **icmp_checksum_errors** Wskaźnik do lokalizacji docelowej łącznej liczby błędów sumy kontrolnej protokołu ICMP.
- **icmp_unhandled_messages** Wskaźnik do miejsca docelowego całkowitej liczby nieobsłużonych komunikatów ICMP.

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

```c
/* Retrieve ICMP information from previously created IP
   instance ip_0. */
status = nx_icmp_info_get(&ip_0, &pings_sent, &ping_timeouts,
                          &ping_threads_suspended,
                          &ping_responses_received,
                          &icmp_checksum_errors,
                          &icmp_unhandled_messages);
/* If status is NX_SUCCESS, ICMP information was retrieved. */
```
### <a name="see-also"></a>Zobacz też

- nx_icmp_enable
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_ping"></a>nx_icmp_ping  
Wyślij żądanie ping do określonego adresu IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa wysyła żądanie ping do określonego adresu IP i czeka przez określony czas dla komunikatu odpowiedzi na polecenie ping. Jeśli odpowiedź nie zostanie odebrana, zwracany jest błąd. W przeciwnym razie cały komunikat odpowiedzi jest zwracany w zmiennej wskazywanej przez response_ptr. 

Aby wysłać żądanie ping do docelowego adresu IPv6, aplikacje używają usługi ***nxd_icmp_ping** _ lub _ *_nxd_icmp_source_ping_**.

> [!WARNING]  
> *Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne*.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **IP_address** Adres IP w kolejności bajtów hosta do ping.
- **dane** Wskaźnik do obszaru danych dla wiadomości ping.
- **data_size** Liczba bajtów w danych ping
- **response_ptr** Wskaźnik na wskaźnik pakietu, aby przywrócić komunikat odpowiedzi ping w.
- **WAIT_OPTION** Definiuje liczbę cykli czasomierza ThreadX, które oczekują na odpowiedź ping. Opcje oczekiwania są zdefiniowane w następujący sposób:

| Opcja oczekiwania            | Wartość                           |
| -----------------------|---------------------------------|
| NX_NO_WAIT             | 0x00000000                    |
| wartość limitu czasu w taktach | (0x00000001 przez 0xFFFFFFFE) |
| NX_WAIT_FOREVER        | 0xFFFFFFFF                      |

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

```c
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

- nx_icmp_enable
- nx_icmp_info_get
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_igmp_enable"></a>nx_igmp_enable
Włącz protokół IGMP (Internet Group Management Protocol)

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa włącza składnik IGMP w określonym wystąpieniu IP. Składnik IGMP jest odpowiedzialny za zapewnienie wsparcia dla operacji zarządzania grupami multiemisji IP.

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

```c
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get
Pobierz informacje o działaniach IGMP

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach IGMP dla określonego wystąpienia IP.

> [!IMPORTANT]  
> *Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego*.

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

```c
/* Retrieve IGMP information from previously created IP Instance ip_0. */
status = nx_igmp_info_get(&ip_0, &igmp_reports_sent,
                          &igmp_queries_received,
                          &igmp_checksum_errors,
                          &current_groups_joined);

/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable
Wyłącz sprzężenie zwrotne protokołu IGMP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Disable IGMP loopback for all subsequent multicast groups
   joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable
Włączanie sprzężenia zwrotnego IGMP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Enable IGMP loopback for all subsequent multicast
   groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join
Dołącz wystąpienie IP do określonej grupy multiemisji za pośrednictwem interfejsu

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Opis

Ta usługa sprzęga wystąpienie IP z określoną grupą multiemisji za pośrednictwem określonego interfejsu sieciowego. Wewnętrzny licznik jest konserwowany, aby śledzić liczbę przypadków, gdy ta sama Grupa została przyłączona. Po dołączeniu do grupy multiemisji składnik IGMP zezwoli na odbieranie pakietów IP z tym adresem grupy za pośrednictwem określonego interfejsu sieciowego, a także zgłaszanie do routerów, do których ten adres IP jest członkiem tej grupy multiemisji. Komunikaty przyłączenia do członkostwa w protokole IGMP, raport i opuszczenie są również wysyłane za pośrednictwem określonego interfejsu sieciowego. Aby dołączyć do grupy multiemisji IPv4 bez wysyłania raportu o członkostwie w grupie IGMP, aplikacja używa ***nx_ipv4_multicast_interface_join*** usługi.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **group_address** Adres grupy multiemisji IP klasy D do przyłączenia w kolejności bajtów hosta.
- **interface_index** Indeks interfejsu dołączonego do wystąpienia NetX Duo.

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

```c
/* Previously created IP Instance joins the multicast group
   244.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
                                 (&ip IP_ADDRESS(244,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```   
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_leave"></a>nx_igmp_multicast_interface_leave
Pozostaw określoną grupę multiemisji za pośrednictwem interfejsu

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Opis

Ta usługa pozostawia określoną grupę multiemisji za pośrednictwem określonego interfejsu sieciowego. Wewnętrzny licznik jest konserwowany, aby śledzić liczbę przypadków, gdy ta sama Grupa jest członkiem. Po opuszczeniu grupy multiemisji składnik IGMP wyśle odpowiedni raport dotyczący członkostwa i może opuścić grupę, jeśli nie ma żadnych członków z tego węzła. Aby opuścić grupę multiemisji IPv4 bez wysyłania raportu o członkostwie w grupie IGMP, aplikacja używa ***nx_ipv4_multicast_interface_leave*** usługi.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **group_address** Adres grupy multiemisji IP klasy D do opuszczenia. Adres IP znajduje się w kolejności bajtów hosta.
- **interface_index** Indeks interfejsu dołączonego do wystąpienia NetX Duo.

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0X00) pomyślne dołączenie do grupy multiemisji.
- **NX_ENTRY_NOT_FOUND** (0x16) nie można odnaleźć określonego adresu grupy multiemisji w lokalnej tabeli multiemisji.
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

```c
/* Leave the multicast group 244.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_leave
                                (&ip IP_ADDRESS(244,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join
Dołącz wystąpienie adresu IP do określonej grupy multiemisji

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>Opis

Ta usługa sprzęga wystąpienie IP z określoną grupą multiemisji. Wewnętrzny licznik jest konserwowany, aby śledzić liczbę przypadków, gdy ta sama Grupa została przyłączona. Sterownik jest poleceniem, aby wysłać raport IGMP, jeśli jest to pierwsze połączenie w sieci wskazujące zamiar hosta do przyłączenia do grupy. Po dołączeniu składnik IGMP zezwoli na odbieranie pakietów IP z tym adresem grupy i raport na routerach, do których ten adres IP jest członkiem tej grupy multiemisji. Aby dołączyć do grupy multiemisji IPv4 bez wysyłania raportu o członkostwie w grupie IGMP, aplikacja używa ***nx_ipv4_multicast_interface_join*** usługi.

> [!NOTE]  
> *Aby dołączyć do grupy multiemisji na urządzeniu niebędącym podstawowym, należy użyć **nx_igmp_multicast_interface_join usługi.***

### <a name="parameters"></a>Parametry

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

```c
/* Previously created IP Instance ip_0 joins the multicast group
   224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully
   joined the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave
Przyczyna opuszczenia określonej grupy multiemisji przez wystąpienie protokołu IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>Opis

Ta usługa powoduje, że wystąpienie IP opuszcza określoną grupę multiemisji, jeśli liczba urlopów equests jest zgodna z liczbą żądań dołączenia. W przeciwnym razie wewnętrzna liczba sprzężeń jest po prostu zmniejszana. Aby opuścić grupę multiemisji IPv4 bez wysyłania raportu o członkostwie w grupie IGMP, aplikacja używa ***nx_ipv4_multicast_interface_leave*** usługi.

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

```c
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
   the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy
Powiadamiaj aplikację, jeśli zmienią się adresy IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *, VOID *),
    VOID *additional_info);
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję powiadamiania aplikacji, która jest wywoływana za każdym razem, gdy adres IPv4 zostanie zmieniony.

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

```c
/* Register the function "my_ip_changed" to be called whenever the
   IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed,
                                      NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
   called whenever the IP address changes. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_get"></a>nx_ip_address_get
Pobieranie adresu IPv4 i maski sieci

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>Opis

Ta usługa Pobiera adres IPv4 i jego maskę podsieci podstawowego interfejsu sieciowego.

> [!IMPORTANT]   
> * Aby uzyskać informacje na temat urządzenia pomocniczego, Użyj usługi * * nx_ip_interface_address_get * * *.

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

```c
/* Get the IP address and network mask from the previously created
   IP Instance ip_0. */
status = nx_ip_address_get(&ip_0, &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
   network_mask contain the IP and network mask respectively. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_set"></a>nx_ip_address_set
Ustaw adres IPv4 i maskę sieci

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>Opis

Ta usługa ustawia adres IPv4 i maskę sieci dla podstawowego interfejsu sieciowego.

> [!IMPORTANT]  
> * Aby ustawić adres IP i maskę sieci dla urządzenia pomocniczego, Użyj usługi * * nx_ip_interface_address_set * * *.

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

```c
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00 for
   the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4),
                           0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address of
   1.2.3.4 and a network mask of 0xFFFFFF00. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_auxiliary_packet_pool_set"></a>nx_ip_auxiliary_packet_pool_set
Konfigurowanie pomocniczej puli pakietów

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_auxiliary_packet_pool_set(
    NX_IP *ip_ptr,
    NX_PACKET_POOL *aux_pool);
```
### <a name="description"></a>Opis

Ta usługa konfiguruje pomocniczą pulę pakietów w wystąpieniu IP. W przypadku systemu z ograniczoną ilością pamięci użytkownik może zwiększyć wydajność pamięci przez utworzenie domyślnej puli pakietów o rozmiarze jednostki MTU i utworzenie pomocniczej puli pakietów o mniejszym rozmiarze pakietu dla wątku IP do przesyłania małych pakietów przy użyciu programu. Zalecany rozmiar pakietu dla puli pomocniczej to 256 bajtów, przy założeniu, że protokół IPv6 i protokół IPsec są włączone.

Domyślnie wystąpienie protokołu IP nie akceptuje pomocniczej puli pakietów. Aby włączyć tę funkcję, należy zdefiniować *NX_DUAL_PACKET_POOL_ENABLE* podczas kompilowania biblioteki NetX Duo.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **aux_pool** Pomocnicza Pula pakietów, która ma zostać skonfigurowana dla wystąpienia protokołu IP.

### <a name="return-values"></a>Wartości zwrócone 

- Pomyślny zestaw adresów IP **NX_SUCCESS** (0x00).
- **NX_NOT_SUPPORTED** (0x4B) funkcja podwójnej puli pakietów nie została skompilowana w bibliotece.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub wskaźnika puli.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie  

Nie

### <a name="example"></a>Przykład

```c
#define SMALL_PAYLOAD_SIZE 256
NX_PACKET small_pool;

nx_packet_pool_create(&small_pool, "small pool", SMALL_PAYLOAD_SIZE,
                       small_pool_memory_ptr, small_pool_size);

/* Add the small packet pool to the IP instance. */
status = nx_ip_auxiliary_packet_pool_set(&ip_0, &small_pool);

/* If status is NX_SUCCESS, the IP instance now is able to use the
   small pool for transmitting small datagram. */
```
### <a name="see-also"></a>Zobacz też

- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_ip_create"></a>nx_ip_create
Tworzenie wystąpienia adresu IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, ULONG ip_address,
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
- **default_pool** Wskaźnik sterujący blokiem wcześniej utworzonej puli pakietów NetX Duo.
- **ip_network_driver** Sterownik sieciowy dostarczony przez użytkownika używany do wysyłania i odbierania pakietów IP.
- **memory_ptr** Wskaźnik do obszaru pamięci dla obszaru stosu wątku pomocnika IP.
- **memory_size** Liczba bajtów w obszarze pamięci dla stosu wątku pomocnika IP.
- **priorytet** Priorytet wątku pomocnika adresów IP.

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) pomyślne utworzenie wystąpienia adresu IP.
- Biblioteka **NX_NOT_IMPLEMENTED** (0X4A) NetX Duo jest nieprawidłowo skonfigurowana.
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

```c
/* Create an IP instance with an IP address of 1.2.3.4 and a network
   mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
   point of the application specific network driver and the
   "stack_memory_ptr" specifies the start of a 1024 byte memory
   area that is used for this IP instance’s helper thread. */
status = nx_ip_create(&ip_0, "NetX IP Instance ip_0",
                      IP_ADDRESS(1, 2, 3, 4),
                      0xFFFFFF00UL, &pool_0, ethernet_driver,
                      stack_memory_ptr, 1024, 1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_delete"></a>nx_ip_delete
Usuń poprzednio utworzone wystąpienie adresu IP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>Zobacz też 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command
Wydaj polecenie do sterownika sieciowego

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_driver_direct_command
    (NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```
### <a name="description"></a>Opis

Ta usługa udostępnia interfejs bezpośredni do podstawowego sterownika interfejsu sieciowego aplikacji określonego podczas wywołania ***nx_ip_create*** . Polecenia specyficzne dla aplikacji mogą służyć do podawania wartości liczbowych, które są większe lub równe NX_LINK_USER_COMMAND.

> [!IMPORTANT]  
> *Aby wydać polecenie dla urządzenia pomocniczego, Użyj usługi **nx_ip_driver_interface_direct_command***.

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

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Make a direct call to the application-specific network driver
   for the previously created IP instance. For this example, the
   network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(&ip_0, NX_LINK_GET_STATUS,
                                     &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
   NX_TRUE or NX_FALSE value representing the status of the
   physical link. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command
Wydaj polecenie do sterownika sieciowego

### <a name="prototype"></a>Prototype  

```c
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

```c
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

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable  
Wyłącz przekazywanie pakietów IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa wyłącza przekazywanie pakietów IP w składniku IP NetX Duo. Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.

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

```c
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>Zobacz też  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable
Włączanie przekazywania pakietów IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa umożliwia przekazywanie pakietów IP w składniku IP NetX Duo. Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.

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

```c
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>Zobacz też 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable
Wyłącz fragmentację pakietu IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa wyłącza funkcję fragmentacji i tworzenia pakietów IPv4 i IPv6. W przypadku pakietów, które oczekują na ponowną złożenie, ta usługa zwalnia te pakiety. Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.

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

```c
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
   previously created IP instance. */
```

### <a name="see-also"></a>Zobacz też  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable
Włącz fragmentację pakietów IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa umożliwia fragmentację i remontowanie pakietów IPv4 i IPv6. Po utworzeniu zadania IP ta usługa zostanie automatycznie wyłączona.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0x00), pomyślne włączenie FRAGMENTU adresu IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- Funkcje fragmentacji adresów IP **NX_NOT_ENABLED** (0x14) nie są kompilowane do NetX Duo.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>Zobacz też  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_gateway_address_clear"></a>nx_ip_gateway_address_clear
Wyczyść adres bramy IPv4

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_gateway_address_clear(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa czyści adres bramy IPv4 skonfigurowany w wystąpieniu. Aby wyczyścić domyślnie zewnętrzny adres IPv6 z wystąpienia IP, aplikacje używają ***nxd_ipv6_default_router_delete usługi.***

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) pomyślnie wyczyścił adres bramy IP.
- **NX_PTR_ERROR** (0X07) nieprawidłowy blok kontroli adresów IP
- Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Clear the gateway address of IP instance. */
status = nx_ip_gateway_address_clear(&ip_0);

/* If status == NX_SUCCESS, the gateway address was successfully
   cleared from the IP instance. */
```
### <a name="see-also"></a>Zobacz też

-nx_ip_gateway_address_get-nx_ip_gateway_address_set-nx_ip_info_get-nx_ip_static_route_add-nx_ip_static_route_delete-nxd_ipv6_default_router_add-nxd_ipv6_default_router_delete-nxd_ipv6_default_router_entry_get-nxd_ipv6_default_router_get-nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_get"></a>nx_ip_gateway_address_get
Pobierz adres bramy IPv4

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_gateway_address_get(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>Opis

Ta usługa Pobiera adres bramy IPv4 skonfigurowany w wystąpieniu IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **IP_address** Wskaźnik do pamięci, w której jest przechowywany adres bramy

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne uzyskanie 
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresu IP lub wskaźnik adresu IP
- Nie znaleziono adresu bramy **NX_NOT_FOUND** (0x4E)
- Nie wywołano **NX_CALLER_ERROR** (0X11) S nazwa z inicjalizacji systemowej lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
ULONG ip_address;

/* Get the gateway address of IP instance. */
status = nx_ip_gateway_address_get(&ip_0, &ip_address);

/* If status == NX_SUCCESS, the gateway address was successfully
   got. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set
Ustaw adres IP bramy

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>Opis

Ta usługa ustawia adres IP bramy IPv4. Cały ruch poza siecią jest kierowany do tej bramy na potrzeby transmisji. Brama musi być bezpośrednio dostępna za pomocą jednego z interfejsów sieciowych. Aby skonfigurować adres bramy IPv6, należy użyć ***nxd_ipv6_default_router_add usługi.*** 

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

```c
/* Setup the Gateway address for previously created IP
   Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99);

/* If status is NX_SUCCESS, all out-of-network send requests are
   routed to 1.2.3.99. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_info_get"></a>nx_ip_info_get
Pobierz informacje o działaniach IP

### <a name="prototype"></a>Prototype  

```c
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

> [!NOTE]  
> *Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego*.

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

```c
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

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get
Pobieranie adresu IP interfejsu

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>Opis

Ta usługa Pobiera adres IPv4 określonego interfejsu sieciowego. Aby można było pobrać adres IPv6, aplikacja używa usługi ***nxd_ipv6_address_get***

> [!CAUTION]  
> *Określone urządzenie, jeśli nie urządzenie podstawowe, musi być wcześniej dołączone do wystąpienia IP*.

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

```c
#define INTERFACE_INDEX 1

/* Get device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
                                     &ip_address,
                                     &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
   retrieved. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_mapping_configure"></a>nx_ip_interface_address_mapping_configure
Skonfiguruj, czy jest wymagana mapowanie adresów

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_address_mapping_configure(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT mapping_needed);
```
### <a name="description"></a>Opis

Ta usługa określa, czy adres IP do mapowania adresów MAC jest wymagany dla określonego interfejsu sieciowego. Ta usługa jest zwykle wywoływana z sterownika urządzenia interfejsu w celu powiadomienia stosu IP, czy źródłowy interfejs wymaga adresu IP do mapowania na dwie warstwy (MAC).

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **interface_index** Indeksowanie do interfejsu sieciowego
- **mapping_needed** NX_TRUE — mapowanie adresów jest zbędne NX_FALSE--nie jest wymagana mapowanie adresu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne skonfigurowanie
- Indeks urządzenia **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Thread

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0
UCHAR mapping_needed = NX_TRUE;

/* Configure address mapping needed specified interface. */
status = nx_ip_interface_address_mapping_configure(&ip_0,
                                             PRIMARY_INTERFACE,
                                             mapping_needed);

/* If status == NX_SUCCESS, the address mapping needed was
   successfully configured. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set
Ustaw adres IP interfejsu i maskę sieci

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>Opis

Ta usługa ustawia adres IPv4 i maskę sieci dla określonego interfejsu IP. Aby skonfigurować adres interfejsu IPv6, aplikacja używa ***nxd_ipv6_address_set*** usługi. 
 
> [!WARNING]  
> *Określony interfejs musi być wcześniej dołączony do wystąpienia IP*. 

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **interface_index** Indeks interfejsu dołączonego do wystąpienia NetX Duo.
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

```c
#define INTERFACE_INDEX 1

/* Set device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
                                     ip_address,
                                     network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
   successfully set. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach
Dołącz interfejs sieciowy do wystąpienia protokołu IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)(struct NX_IP_DRIVER_STRUCT *));
```
### <a name="description"></a>Opis

Ta usługa dodaje fizyczny interfejs sieciowy do interfejsu IP. Należy zauważyć, że wystąpienie IP jest tworzone przy użyciu interfejsu podstawowego, więc każdy dodatkowy interfejs jest pomocniczy dla interfejsu podstawowego. Łączna liczba interfejsów sieciowych dołączonych do wystąpienia IP (łącznie z interfejsem podstawowym) nie może przekroczyć **NX_MAX_PHYSICAL_INTERFACES**.

Jeśli wątek IP nie został jeszcze uruchomiony, interfejsy pomocnicze zostaną zainicjowane w ramach procesu uruchamiania wątku IP, który inicjuje wszystkie interfejsy fizyczne.

Jeśli wątek IP nie jest jeszcze uruchomiony, interfejs pomocniczy jest inicjowany w ramach usługi ***nx_ip_interface_attach*** .

> [!WARNING]  
> *ip_ptr musi wskazywać prawidłową strukturę IP NetX Duo. Należy skonfigurować **NX_MAX_PHYSICAL_INTERFACES** dla liczby interfejsów sieciowych dla wystąpienia protokołu IP. Wartość domyślna to 1*.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **INTERFACE_NAME** Wskaźnik do ciągu nazwy interfejsu.
- **IP_address** Adres IP urządzenia w kolejności bajtów hosta.
- **network_mask** Maska sieci urządzenia w kolejności bajtów hosta.
- **ip_link_driver** Sterownik Ethernet dla interfejsu.

### <a name="return-values"></a>Wartości zwrócone  

- Wpis **NX_SUCCESS** (0x00) jest dodawany do statycznej tabeli routingu.
- **NX_NO_MORE_ENTRIES** (0X17) Maksymalna liczba interfejsów. Przekroczono NX_MAX_PHYSICAL_INTERFACES. Jeśli jest włączony protokół IPv6, ten błąd może również wskazywać, że sterownik może nie mieć wystarczającej ilości zasobów, aby obsłużyć operacje multiemisji IPv6.
- **NX_DUPLICATED_ENTRY** (0x52) podany adres IP jest już używany w tym wystąpieniu adresu IP.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wejściowy.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowe dane wejściowe adresu IP.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
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

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_get"></a>nx_ip_interface_capability_get
Pobierz możliwości sprzętowe interfejsu

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_capability_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *interface_capability_flag);
```
### <a name="description"></a>Opis

Ta usługa Pobiera flagę możliwości z określonego interfejsu sieciowego. Aby można było korzystać z tej usługi, biblioteka NetX Duo musi być skompilowana przy użyciu opcji ***NX_ENABLE_INTERFACE_CAPABILITY*** włączone.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **interface_index** Indeks interfejsu sieciowego
- **interface_capability_flag** Wskaźnik do przestrzeni pamięci dla flagi możliwości

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie uzyskał informacje o możliwościach interfejsu.
- Funkcja interfejsu **NX_NOT_SUPPORTED** (0x4B) nie jest obsługiwana w tej kompilacji.
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresu IP lub nieprawidłowy wskaźnik flagi możliwości
- Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0
ULONG       capability_flag;

/* Get the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_get(&ip_0,
                                        PRIMARY_INTERFACE,
                                        &capability_flag);

/* If status == NX_SUCCESS, the capability flag from the primary
   interface was successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_set"></a>nx_ip_interface_capability_set
Ustaw flagę możliwości sprzętu

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_capability_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG interface_capability_flag);
```                           
### <a name="description"></a>Opis

Ta usługa jest używana przez sterownik urządzenia sieciowego do konfigurowania flagi możliwości dla określonego interfejsu sieciowego. Aby można było korzystać z tej usługi, biblioteka NetX Duo musi być skompilowana z użyciem opcji ***NX_ENABLE_INTERFACE_CAPABILITY*** zdefiniowanej.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **interface_index** Indeks interfejsu sieciowego
- **interface_capability_flag** Flaga możliwości dla danych wyjściowych

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił flagę możliwości sprzętowych interfejsu.
- Funkcja interfejsu **NX_NOT_SUPPORTED** (0x4B) nie jest obsługiwana w tej kompilacji.
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy 
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP 
- Nie wywołano **NX_CALLER_ERROR** (0X11) S nazwa z inicjalizacji systemowej lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0
ULONG capability_flag = \
                 NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM |\
                 NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM;
UINT device_index = 0;

/* Set the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_set(&ip_0,
                                        PRIMARY_INTERFACE,
                                        capability_flag);

/* If status == NX_SUCCESS, the hardware capability flag was
   successfully set. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_detach"></a>nx_ip_interface_detach
Odłączanie określonego interfejsu z wystąpienia adresu IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr, 
    UINT index);
```
### <a name="description"></a>Opis

Ta usługa odłącza określony interfejs IP od wystąpienia IP. Po odłączeniu interfejsu wszystkie zamknięte połączone gniazda TCP oraz wpisy pamięci podręcznej i ARP dla tego interfejsu zostaną usunięte z odpowiednich tabel. Członkostwa IGMP dla tego interfejsu są usuwane.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **indeks** Indeks interfejsu, który ma zostać usunięty.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie usunął interfejs fizyczny.
- **NX_INVALID_INTERFACE** (0X4C) określony interfejs sieciowy jest nieprawidłowy.
- **NX_PTR_ERROR** (0X07) nieprawidłowe wskaźniki.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define INTERFACE_INDEX 1

/* Detach interface 1. */
status = nx_ip_interface_detach(&IP_0, INTERFACE_INDEX);

/* If status is NX_SUCCESS the interface is successfully detached
   from the IP instance. */
```

### <a name="see-also"></a>Zobacz też  

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get
Pobierz parametry interfejsu sieciowego

### <a name="prototype"></a>Prototype  

```c
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

> [!WARNING]  
> *ip_ptr musi wskazywać prawidłową strukturę IP NetX Duo. Określony interfejs, jeśli nie jest interfejsem podstawowym, musi być wcześniej dołączony do wystąpienia IP*.

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

```c
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

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_mtu_set"></a>nx_ip_interface_mtu_set
Ustawianie wartości MTU interfejsu sieciowego

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_mtu_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG mtu_size);
```
### <a name="description"></a>Opis

Ta usługa jest używana przez sterownik urządzenia do konfigurowania wartości IP jednostki MTU dla określonego interfejsu sieciowego.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **interface_index** Indeksowanie do interfejsu sieciowego
- **mtu_size** Rozmiar jednostki MTU protokołu IP

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) pomyślnie ustawił wartość MTU
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0
ULONG       mtu_size = 1500;

/* Set the MTU size of specified interface. */
status = nx_ip_interface_mtu_set(&ip_0,
                                 PRIMARY_INTERFACE, mtu_size);

/* If status == NX_SUCCESS, the MTU size was successfully set. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_get"></a>nx_ip_interface_physical_address_get
Pobieranie adresu fizycznego urządzenia sieciowego

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_physical_address_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *physical_msw,
    ULONG *physical_lsw);
```
### <a name="description"></a>Opis

Ta usługa Pobiera adres fizyczny interfejsu sieciowego z wystąpienia IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **interface_index** Indeks interfejsu sieciowego
- **physical_msw** Wskaźnik do miejsca docelowego dla pierwszych 16 bitów adresu MAC urządzenia
- **physical_lsw** Wskaźnik do miejsca docelowego dla niższych 32 bitów adresu MAC urządzenia

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) — pomyślne uzyskanie
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku lub adresu fizycznego kontroli adresu IP
- Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0
ULONG   physical_msw;
ULONG   physical_lsw;

/* Get the physical address of specified interface. */
status = nx_ip_interface_physical_address_get(&ip_0,
                                              PRIMARY_INTERFACE,
                                              &physical_msw,
                                              &physical_lsw);

/* If status == NX_SUCCESS, the physical address was successfully
   retrieved. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_set"></a>nx_ip_interface_physical_address_set
Ustaw adres fizyczny dla określonego interfejsu sieciowego

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_interface_physical_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT update_driver);
```
### <a name="description"></a>Opis

Ta usługa jest używana przez aplikację lub sterownik urządzenia w celu skonfigurowania adresu fizycznego adresu MAC określonego interfejsu sieciowego. Nowy adres MAC jest stosowany do bloku sterowania struktury interfejsu. Jeśli flaga ***update_driver*** jest ustawiona, zostanie wystawione polecenie poziomu sterownika, aby sterownik urządzenia mógł zaktualizować swój adres MAC zaprogramowany do kontrolera Ethernet.

W typowym przypadku ta usługa jest wywoływana ze sterownika urządzenia interfejsu podczas fazy inicjalizacji w celu powiadomienia stosu IP swojego adresu MAC. W takim przypadku flaga ***update_driver*** nie powinna być ustawiona.

Tę procedurę można również wywołać z poziomu aplikacji użytkownika, aby ponownie skonfigurować adres MAC interfejsu w czasie wykonywania. W tym przypadku użycia flaga ***update_driver*** powinna być ustawiona, aby nowy adres MAC mógł zostać zastosowany do sterownika urządzenia.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **interface_index** Indeksowanie do interfejsu sieciowego
- **physical_msw** Wskaźnik do miejsca docelowego dla pierwszych 16 bitów adresu MAC urządzenia
- **physical_lsw** Wskaźnik do miejsca docelowego dla niższych 32 bitów adresu MAC urządzenia

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne ustawienie **NX_SUCCESS** (0x00)
- Polecenie **NX_UNHANDLED_COMMAND** (0x4B) nie zostało rozpoznane przez sterownik
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0
ULONG       physical_msw = 0x00CF;
ULONG       physical_lsw = 0x01020304;

/* Set the physical address of specified device. */
status = nx_ip_interface_physical_address_set(&ip_0,
                                              PRIMARY_INTERFACE,
                                              physical_msw,
                                              physical_lsw,
                                              NX_TRUE);

/* If status == NX_SUCCESS, the physical address was successfully
   set. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check
Sprawdź stan wystąpienia adresu IP

### <a name="prototype"></a>Prototype  

```c
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
- **interface_index** Numer indeksu interfejsu needed_status żądany stan adresu IP, zdefiniowany w postaci mapy bitowej w następujący sposób:
  - **NX_IP_INITIALIZE_DONE** (0x0001)
  - **NX_IP_ADDRESS_RESOLVED** (0x0002)
  - **NX_IP_LINK_ENABLED** (0x0004)
  - **NX_IP_ARP_ENABLED** (0x0008)
  - **NX_IP_UDP_ENABLED** (0x0010)
  - **NX_IP_TCP_ENABLED** (0x0020)
  - **NX_IP_IGMP_ENABLED** (0x0040)
  - **NX_IP_RARP_COMPLETE** (0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED** (0x0100)
- **actual_status** Wskaźnik do miejsca docelowego rzeczywistego zestawu bitów. wait_option definiuje, w jaki sposób działa usługa, jeśli żądane bity stanu są niedostępne. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **NX_NO_WAIT** (0x00000000)
  - **wartość limitu czasu** (0X00000001 przez 0xFFFFFFFE)
  - **NX_WAIT_FOREVER** 0xFFFFFFFF

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

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
                                      &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
   instance is up. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set
Ustaw funkcję wywołania zwrotnego powiadomienia o zmianie stanu łącza

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID(*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
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

```c
/* Configure a callback function to be used when the physical
   interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0,
                                             my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
   is set. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check

## <a name="nx_ip_max_payload_size_find"></a>nx_ip_max_payload_size_find
Maksymalna liczba ładunków danych pakietów obliczeniowych

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_max_payload_size_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *dest_address,
    UINT if_index,
    UINT src_port,
    UINT dest_port,
    ULONG protocol,
    ULONG *start_offset_ptr,
    ULONG *payload_length_ptr);
```
### <a name="description"></a>Opis

Ta usługa umożliwia znalezienie maksymalnego rozmiaru ładunku aplikacji, który nie wymaga fragmentacji adresów IP w celu uzyskania dostępu do miejsca docelowego; na przykład ładunek jest mniejszy lub niższy od rozmiaru jednostki MTU interfejsu lokalnego. (lub wartość MTU ścieżki uzyskana za pośrednictwem odnajdowania MTU ścieżki IPv6). Rozmiar nagłówka i górnego nagłówka aplikacji (TCP lub UDP) jest odejmowany od łącznego ładunku. Jeśli zasady zabezpieczeń IPsec NetX Duo dotyczą tego punktu końcowego, nagłówki protokołu IPsec (ESP/AH) i skojarzone obciążenie, takie jak wektor początkowy, są również odejmowane od jednostki MTU. Ta usługa ma zastosowanie zarówno do pakietów IPv4, jak i IPv6.

Parametr *if_index* określa interfejs, który ma być używany do wysyłania pakietu. W przypadku systemu wielostronicowego wywołujący musi określić parametr *if_index* , jeśli miejscem docelowym jest emisja (tylko IPv4), Multiemisja lub adres IPv6 połączenia lokalnego.

Ta usługa zwraca dwie wartości do obiektu wywołującego:

1) start_offset_ptr: to jest lokalizacja po nagłówkach TCP/UDP/IP/IPsec;
2) payload_length_ptr: ilość danych może być transferowana bez przekraczania jednostki MTU.

Nie istnieje równoważna usługa NetX.

### <a name="restrictions"></a>Ograniczenia 

Należy wcześniej utworzyć wystąpienie adresu IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wystąpienia adresu IP
- **dest_address** Wskaźnik do docelowego adresu pakietu
- **if_index** Wskazuje indeks interfejsu do użycia
- **src_port** Numer portu źródłowego
- **dest_port** Numer portu docelowego
- **Protokół** Protokół warstwy wyższej do użycia
- **start_offset_ptr** Wskaźnik do początku danych dla maksymalnego ładunku pakietu
- **payload_length_ptr** Wskaźnik do rozmiaru ładunku z wykluczeniem nagłówków

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie obliczono ładunek **NX_SUCCESS** (0x00)
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy lub interfejs jest nieprawidłowy.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IP.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub nieprawidłowy adres docelowy
- **NX_IP_ADDRESS_ERROR** (0x21) podano nieprawidłowy adres 
- **NX_NOT_SUPPORTED** (0X4B) nieprawidłowy protokół (nie UDP lub TCP)
- Usługa **NX_CALLER_ERROR** (0x11) nie jest wywoływana z inicjalizacji systemu lub kontekstu wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* The following example determines the maximum payload for UDP
   packet to remote host. */
#define PRIMARY_INTERFACE 0
status = nx_ip_max_payload_size_find(&ip_0,
                                     &dest_ipv6_address,
                                     PRIMARY_INTERFACE,
                                     source_port,
                                     dest_port, NX_PROTOCOL_UDP,
                                     &start_offset,
                                     &payload_length);

/* A return value of NX_SUCCESS indicates the packet payload
   payload_length starting at the offset start_offset is
   successfully computed. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable
Wyłącz wysyłanie/otrzymywanie pakietów pierwotnych

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);
/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been disabled for the previously created IP instance. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable
Włącz przetwarzanie pakietów nieprzetworzonych

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa umożliwia przekazywanie i odbieranie nieprzetworzonych pakietów IP dla tego wystąpienia IP. Pakiety przychodzące TCP, UDP, ICMP i IGMP są nadal przetwarzane przez NetX Duo. Pakiety z nieznanymi typami protokołów warstwy wyższej są przetwarzane przez nieprzetworzoną procedurę odbierania pakietów.

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

```c
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been enabled for the previously created IP instance. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_filter_set"></a>nx_ip_raw_packet_filter_set
Ustaw filtr pakietów Raw IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_filter_set(
    NX_IP *ip_ptr,
    UINT (*raw_packet_filter)(NX_IP *, ULONG, NX_PACKET *));
```
### <a name="description"></a>Opis

Ta usługa konfiguruje filtr pakietów RAW protokołu IP. Funkcja nieprzetworzonych filtrów pakietów wdrożona przez aplikację użytkownika umożliwia aplikacji otrzymywanie pakietów pierwotnych na podstawie kryteriów dostarczonych przez użytkownika. Należy pamiętać, że warstwa otoki BSD NetX Duo korzysta z funkcji nieprzetworzonego filtru pakietów do obsługi nieprzetworzonego gniazda w warstwie BSD. Aby można było korzystać z tej usługi, biblioteka NetX Duo musi być skompilowana przy użyciu opcji ***NX_ENABLE_IP_RAW_PACKET_FILTER*** zdefiniowanej.

### <a name="parameters"></a>Parametry  

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **raw_packet_filter** Wskaźnik funkcji nieprzetworzonego filtru pakietów

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) pomyślnie ustawił procedurę filtru pakietów RAW
- Obsługa pakietów nieprzetworzonych w programie **NX_NOT_SUPPORT** (0x4B) jest niedostępna
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
UINT raw_packet_filter(NX_IP *ip_ptr, ULONG protocol,
                       NX_PACKET *packet_ptr)
{

/* Simply filter protocol. */
if(protocol == NX_IP_RAW)
   return NX_SUCCESS;
else
   return NX_NOT_SUCCESSFUL;
}

void raw_packet_thread_entry(ULONG id)
{

/* Set the raw packet filter of IP instance. */
status = nx_ip_raw_packet_filter_set(&ip_0,
                                     raw_packet_filter);

/* If status == NX_SUCCESS, the raw packet filter of IP instance
   was successfully set. */
}
```
### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive
Odbierz pakiet pierwotnego adresu IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa odbiera pakiet Raw IP od określonego wystąpienia IP. Jeśli istnieją pakiety IP w kolejce odbierania pakietów nieprzetworzonych, pierwszy (najstarszy) pakiet jest zwracany do obiektu wywołującego. W przeciwnym razie, jeśli żaden pakiet nie jest dostępny, obiekt wywołujący może zawiesić się zgodnie z opcją oczekiwania.

> [!CAUTION]   
> *Jeśli NX_SUCCESS, jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne*.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **packet_ptr** Wskaźnik do wskaźnika, aby umieścić odebrany pakiet pierwotnego adresu IP w programie.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli pakiety są niedostępne. Opcje oczekiwania są zdefiniowane w następujący sposób:
   - **NX_NO_WAIT** (0x00000000)
   - **NX_WAIT_FOREVER** (0xffffffff)
   - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

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

```c
/* Receive a raw IP packet for this IP instance, wait for a maximum
   of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
   variable packet_ptr. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send
Wyślij pakiet Raw IP

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```
### <a name="description"></a>Opis

Ta usługa wysyła nieprzetworzony pakiet IPv4 do docelowego adresu IP. Należy zauważyć, że ta procedura wraca natychmiast i dlatego nie wiadomo, czy pakiet IP został faktycznie wysłany. Sterownik sieciowy będzie odpowiedzialny za wydanie pakietu, gdy transmisja zostanie zakończona.

W przypadku systemu wielodostępnego NetX Duo używa docelowego adresu IP do znalezienia odpowiedniego interfejsu sieciowego i używa adresu IP interfejsu jako adresu źródłowego. Jeśli docelowy adres IP jest emisji lub multiemisji, używany jest pierwszy prawidłowy interfejs. Aplikacje używają ***nx_ip_raw_packet_source_send*** w tym przypadku.

Aby wysłać nieprzetworzony pakiet IPv6, aplikacja używa usługi ***nxd_ip_raw_packet_send,** _ lub _ *_nxd_ip_raw_packet_source_send._**

> [!WARNING]  
> *Jeśli błąd nie zostanie zwrócony, aplikacja nie powinna zwolnić pakietu po tym wywołaniu. Wykonanie tej operacji spowoduje nieprzewidywalne wyniki, ponieważ sterownik sieciowy zwolni pakiet po przekazaniu*.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **packet_ptr** Wskaźnik na pakiet Raw IP do wysłania.
- **destination_ip** Docelowy adres IP, który może być określonym adresem IP hosta, emisją sieci, pętlą wewnętrzną lub adresem multiemisji.
- **Type_of_Service** Definiuje typ usługi do transmisji, wartości prawne są następujące:
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)

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

```c
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
                               IP_ADDRESS(1,2,3,5),
                               NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
   packet_ptr has been sent. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_source_send"></a>nx_ip_raw_packet_source_send
Wyślij pakiet Raw IP za poorednictwem określonego interfejsu sieciowego

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```
### <a name="description"></a>Opis

Ta usługa wysyła pakiet pierwotnego adresu IP do docelowego adresu IP przy użyciu określonego lokalnego adresu IPv4 jako adresu źródłowego i za pośrednictwem skojarzonego interfejsu sieciowego. Należy zauważyć, że ta procedura wraca natychmiast, a tym samym nie wiadomo, czy pakiet IP został faktycznie wysłany. Sterownik sieciowy będzie odpowiedzialny za wydanie pakietu, gdy transmisja zostanie zakończona. Ta usługa różni się od innych usług, ponieważ nie ma możliwości znajomości, czy pakiet został faktycznie wysłany. Może on zostać utracony przez Internet.

> [!CAUTION]  
> Należy *pamiętać, że przetwarzanie Raw IP musi być włączone*.

> [!WARNING]  
> *Ta usługa jest podobna do **nx_ip_raw_packet_send,** z tą różnicą, że ta usługa umożliwia aplikacji wysyłanie pierwotnego pakietu IPv4 z określonych interfejsów fizycznych*.

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

```c
#define ADDRESS_IDNEX 1

/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_source_send(ip_ptr, packet_ptr,
                                      destination_ip,
                                      ADDRESS_INDEX,
                                      NX_IP_NORMAL);

/* If status is NX_SUCCESS the packet was successfully
   transmitted. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_receive_queue_max_set"></a>nx_ip_raw_receive_queue_max_set
Ustaw maksymalny rozmiar nieprzetworzonej kolejki odbierania

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_raw_receive_queue_max_set(
    NX_IP *ip_ptr, 
    ULONG queue_max);
```
### <a name="description"></a>Opis

Ta usługa określa maksymalną głębokość kolejki odbierania pakietów pierwotnych adresów IP. Należy zauważyć, że kolejka odbierania pakietów RAW protokołu IP jest współdzielona z pakietami IPv4 i IPv6. Gdy kolejka odbierania pakietów nieprzetworzonych osiągnie maksymalną głębokość userconfigured, nowo odebrane pakiety RAW są usuwane. Domyślna głębokość kolejki odbierania pakietów pierwotnych adresów IP wynosi 20.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **queue_max** Nowa wartość dla rozmiaru kolejki

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie ustawił maksymalną głębokość kolejki odbierania nieprzetworzonego
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
ULONG queue_max = 10;

/* Set the maximum size of the IP raw packet receive queue. */
status = nx_ip_raw_receive_queue_max_set (&ip_0,
                                          queue_max);

/* If status == NX_SUCCESS, the maximum size of the IP raw packet
   receive queue was successfully set. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add
Dodawanie trasy statycznej do tabeli routingu

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```
### <a name="description"></a>Opis

Ta usługa dodaje wpis do statycznej tabeli routingu. Należy pamiętać, że adres *next_hop* musi być bezpośrednio dostępny z jednego z lokalnych urządzeń sieciowych.

> [!CAUTION]  
> Należy *zauważyć, że ip_ptr musi wskazywać prawidłową strukturę IP NetX Duo, a Biblioteka NetX Duo musi być skompilowana przy użyciu NX_ENABLE_IP_STATIC_ROUTING zdefiniowanych do korzystania z tej usługi. Domyślnie NetX Duo jest zbudowany bez zdefiniowanego NX_ENABLE_IP_STATIC_ROUTING*.

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

```c
/* Specify the next hop for 192.168.1.68 through the gateway
   192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,1,0),
                                0xFFFFFF00UL,
                                IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
   static routing table. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete
Usuń trasę statyczną z tabeli routingu

### <a name="prototype"></a>Prototype  

```c
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask);
```
### <a name="description"></a>Opis

Ta usługa usuwa wpis z statycznej tabeli routingu.

> [!WARNING]  
> Należy *zauważyć, że ip_ptr musi wskazywać prawidłową strukturę IP NetX Duo, a Biblioteka NetX Duo musi być skompilowana przy użyciu NX_ENABLE_IP_STATIC_ROUTING zdefiniowanych do korzystania z tej usługi. Domyślnie NetX Duo jest zbudowany bez zdefiniowanego NX_ENABLE_IP_STATIC_ROUTING*.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **network_address** Docelowy adres sieciowy w kolejności bajtów hosta.
- **net_mask** Docelowa maska sieci w kolejności bajtów hosta.

### <a name="return-values"></a>Wartości zwrócone  

- Pomyślnie usunięto **NX_SUCCESS** (0x00) z statycznej tabeli routingu.
- Nie można odnaleźć wpisu **NX_NOT_SUCCESSFUL** (0x43) w tabeli routingu.
- **NX_NOT_SUPPORTED** (0X4B) Ta funkcja nie jest skompilowana w programie.
- **NX_PTR_ERROR** (0X07) nieprawidłowy wskaźnik ip_ptr.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Remove the static route for 192.168.1.68 from the routing
   table.*/
status = nx_ip_static_route_delete(ip_ptr,
                                   IP_ADDRESS(192,168,1,0),
                                   0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
   the static routing table. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_status_check"></a>nx_ip_status_check
Sprawdź stan wystąpienia adresu IP

### <a name="prototype"></a>Prototype  

```c
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
  - **NX_IP_INITIALIZE_DONE** (0x0001)
  - **NX_IP_ADDRESS_RESOLVED** (0x0002)
  - **NX_IP_LINK_ENABLED** (0x0004)
  - **NX_IP_ARP_ENABLED** (0x0008)
  - **NX_IP_UDP_ENABLED** (0x0010)
  - **NX_IP_TCP_ENABLED** (0x0020)
  - **NX_IP_IGMP_ENABLED** (0x0040)
  - **NX_IP_RARP_COMPLETE** (0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED** (0x0100)
- **actual_status** Wskaźnik do miejsca docelowego rzeczywistego zestawu bitów.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądane bity stanu są niedostępne. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **NX_NO_WAIT** 0x00000000)
  - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)
  - **NX_WAIT_FOREVER** 0xFFFFFFFF

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

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
                            &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
   is up. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ipv4_multicast_interface_join"></a>nx_ipv4_multicast_interface_join
Dołącz wystąpienie IP do określonej grupy multiemisji za pośrednictwem interfejsu

### <a name="prototype"></a>Prototype  

```c
UINT nx_ipv4_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Opis

Ta usługa sprzęga wystąpienie IP z określoną grupą multiemisji za pośrednictwem określonego interfejsu sieciowego. Gdy wystąpienie protokołu IP zostanie przyłączone do grupy multiemisji, logika odbierania IP rozpocznie przekazywanie pakietów danych z grupy nadawanie multiemisji do górnej warstwy. Należy zauważyć, że ta usługa przyłącza grupę multiemisji bez wysyłania raportów IGMP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **group_address** Adres grupy multiemisji IP klasy D do przyłączenia w kolejności bajtów hosta.
- **interface_index** Indeks interfejsu dołączonego do wystąpienia NetX Duo.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne dołączenie do grupy multiemisji.
- **NX_NO_MORE_ENTRIES** (0X17) nie można przyłączyć więcej grup multiemisji, Przekroczono maksymalną liczbę.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do wystąpienia adresu IP lub nieprawidłowe wystąpienie adresu IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_EANABLED** (0X14) protokół IGMP nie jest włączony w tym wystąpieniu protokołu IP
- Podany adres grupy multiemisji **NX_IP_ADDRESS_ERROR** (0x21) nie jest prawidłowym adresem klasy D.
- Indeks urządzenia **NX_INVALID_INTERFACE** (0x4C) wskazuje nieprawidłowy interfejs sieciowy.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Previously created IP Instance joins the multicast group
   224.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_join
                                 (&ip IP_ADDRESS(224,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ipv4_multicast_interface_leave"></a>nx_ipv4_multicast_interface_leave
Pozostaw określoną grupę multiemisji za pośrednictwem interfejsu

### <a name="prototype"></a>Prototype  

```c
UINT nx_ipv4_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>Opis

Ta usługa pozostawia określoną grupę multiemisji za pośrednictwem określonego interfejsu sieciowego. Po opuszczeniu grupy ta usługa nie wyzwala komunikatów IGMP, które są generowane.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **group_address** Adres grupy multiemisji IP klasy D do opuszczenia. Adres IP znajduje się w kolejności bajtów hosta.
- **interface_index** Indeks interfejsu dołączonego do wystąpienia NetX Duo.

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) pomyślne dołączenie do grupy multiemisji.
- **NX_ENTRY_NOT_FOUND** (0x16) nie można odnaleźć określonego adresu grupy multiemisji w lokalnej tabeli multiemisji.
- Indeks urządzenia **NX_INVALID_INTERFACE** (0x4C) wskazuje nieprawidłowy interfejs sieciowy.
- Podany adres grupy multiemisji **NX_IP_ADDRESS_ERROR** (0x21) nie jest prawidłowym adresem klasy D.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do wystąpienia adresu IP lub nieprawidłowe wystąpienie adresu IP

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Leave the multicast group 224.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_leave
                                (&ip, IP_ADDRESS(224,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_packet_allocate"></a>nx_packet_allocate
Przydziel pakiet z określonej puli

### <a name="prototype"></a>Prototype  

```c
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
- **packet_type** Definiuje typ żądanego pakietu. Zobacz sekcję "pule pakietów" na stronie 63 w rozdziale 3, aby zapoznać się z listą obsługiwanych typów pakietów.
- **WAIT_OPTION** Definiuje czas oczekiwania w taktach, jeśli w puli pakietów nie ma dostępnych pakietów. Opcje oczekiwania są zdefiniowane w następujący sposób:
  - **NX_NO_WAIT** (0x00000000)
  - **NX_WAIT_FOREVER** (0xffffffff)
  - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone 

- Pomyślna alokacja pakietu **NX_SUCCESS** (0x00).
- **NX_NO_PACKET** (0X01) Brak dostępnego pakietu.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- Rozmiar pakietu **NX_INVALID_PARAMETERS** (0x4D) nie może obsługiwać protokołu.
- **NX_OPTION_ERROR** (0X0a) Nieprawidłowy typ pakietu.
- **NX_PTR_ERROR** (0X07) Nieprawidłowa Pula lub wskaźnik powrotu pakietu.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowa opcja oczekiwania z niewątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR (sterowniki sieciowe aplikacji). Opcja oczekiwania musi być *NX_NO_WAIT* , gdy jest używana w trybie ISR lub w kontekście czasomierza.

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Allocate a new UDP packet from the previously created packet pool
   and suspend for a maximum of 5 timer ticks if the pool is
   empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr,
                            NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
   found in the variable packet_ptr. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy
Kopiuj pakiet

### <a name="prototype"></a>Prototype  

```c
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
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xffffffff)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

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

```c
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
   previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append
Dołącz dane do końca pakietu

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, ULONG data_size,
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
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xffffffff)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnego dołączenia do pakietu.
- **NX_NO_PACKET** (0X01) Brak dostępnego pakietu.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
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

```c
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
   been appended to the packet. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release


## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset
Wyodrębnij dane z pakietu za pośrednictwem przesunięcia

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```
### <a name="description"></a>Opis

Ta usługa kopiuje dane z pakietu NetX Duo (lub łańcucha pakietów), rozpoczynając od określonego przesunięcia od wskaźnika dołączania pakietu o określonym rozmiarze (w bajtach) do określonego buforu. Liczba bajtów w rzeczywistości kopiowanych jest zwracana w *bytes_copied.* Ta usługa nie usuwa danych z pakietu ani nie dostosowuje wskaźnika dołączania ani innych informacji o stanie wewnętrznym.

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

```c
/* Extract 10 bytes from the start of the received packet buffer
   into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
                                       &bytes_copied) ;
/* If status is NX_SUCCESS, 10 bytes were successfully copied into
   the data buffer. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve
Pobieranie danych z pakietu

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start,
    ULONG *bytes_copied);
```
### <a name="description"></a>Opis

Ta usługa kopiuje dane z dostarczonego pakietu do podanego buforu. Rzeczywista liczba skopiowanych bajtów jest zwracana w miejscu docelowym wskazywanym przez **bytes_copied**.

Należy zauważyć, że ta usługa nie zmienia wewnętrznego stanu pakietu. Pobierane dane są nadal dostępne w pakiecie. 

> [!CAUTION]  
> *Bufor docelowy musi być wystarczająco duży, aby można było przechowywać zawartość pakietu. W przeciwnym razie pamięć zostanie uszkodzona, powodując nieprzewidywalne wyniki*.

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

```c
UCHAR                 buffer[512];
ULONG                 bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
   packet, the size of which is contained in "bytes_copied." */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get
Pobierz długość danych pakietu

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```
### <a name="description"></a>Opis

Ta usługa Pobiera długość danych w określonym pakiecie.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu.
- **Długość** Wartość docelowa dla długości pakietu.

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0x00) pomyślna długość pakietu get.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik pakietu.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create
Utwórz pulę pakietów w określonym obszarze pamięci

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Create a packet pool of 32000 bytes starting at physical
   address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
                               (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
   created. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete
Usuń wcześniej utworzoną pulę pakietów

### <a name="prototype"></a>Prototype  

```c
UINT  nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzoną pulę pakietów. NetX Duo sprawdza wszystkie wątki aktualnie zawieszone w pakietach w puli pakietów i czyści zawieszenie.

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

```c
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
   deleted. */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get
Pobieranie informacji o puli pakietów

### <a name="prototype"></a>Prototype  

```c
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

> [!IMPORTANT]  
> *Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego*.

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

```c
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

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_low_watermark_set"></a>nx_packet_pool_low_watermark_set
Ustaw dolny limit puli pakietów

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_pool_low_watermark_set(
    NX_PACKET_POOL *pool_ptr,
    ULONG low_watermark);
```
### <a name="description"></a>Opis

Ta usługa konfiguruje dolny limit dla określonej puli pakietów. Po ustawieniu wartości niskiego limitu protokół TCP lub UDP nie będzie kolejkować odebranych pakietów, jeśli liczba dostępnych pakietów w puli pakietów jest mniejsza niż Dolny znak wodny puli pakietów, co uniemożliwi puli pakietów Starved pakietów. Ta usługa jest dostępna, jeśli biblioteka NetX Duo została skompilowana z użyciem opcji ***NX_ENABLE_LOW_WATERMARK*** zdefiniowanej.

### <a name="parameters"></a>Parametry

- **pool_ptr** Wskaźnik do bloku kontroli puli pakietów.
- **low_watermark** Wartość dolnego limitu do skonfigurowania

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0X00) pomyślnie ustawił wartość dolnego limitu.
- **NX_NOT_SUPPORTED** (0x4B) funkcja dolnego limitu nie jest wbudowana w NetX Duo.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik puli.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Set pool_0 low watermark value to 2. */
status = nx_packet_pool_create(&pool_0, 2);

/* If status is NX_SUCCESS, the low watermark value is set for
   pool_0.*/
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release
Zwolnij wcześniej przydzieloną pakietów

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>Opis

Ta usługa zwalnia pakiet, w tym wszystkie dodatkowe pakiety powiązane z określonym pakietem. Jeśli inny wątek jest blokowany w alokacji pakietów, otrzymuje pakiet i został wznowiony.

> [!NOTE]  
> *Aplikacja musi uniemożliwiać zwolnienie pakietu więcej niż raz, ponieważ takie działanie spowoduje nieprzewidywalne wyniki*.

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

```c
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
   packet pool it was allocated from. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release
Zwolnij przesłany pakiet

### <a name="prototype"></a>Prototype  

```c
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>Opis

W przypadku pakietów innych niż TCP ta usługa zwalnia przesyłany pakiet, w tym wszystkie dodatkowe pakiety połączone z określonym pakietem. Jeśli inny wątek jest blokowany w alokacji pakietów, otrzymuje pakiet i został wznowiony. W przypadku przesyłanego pakietu TCP pakiet jest oznaczany jako przesyłany, ale nie jest uwalniany do momentu potwierdzenia pakietu. Ta usługa jest zwykle wywoływana ze sterownika sieci aplikacji po przesłaniu pakietu.

> [!WARNING] 
> *Sterownik sieciowy powinien usunąć nagłówek nośnika fizycznego i dostosować długość pakietu przed wywołaniem tej usługi*.

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

```c
/* Release a previously allocated packet that was just transmitted
   from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
   returned to the packet pool it was allocated from. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable
Wyłącz protokół odwrotnego rozpoznawania adresów (RARP)

### <a name="prototype"></a>Prototype  

```c
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyłącza składnik RARP programu NetX Duo dla określonego wystąpienia adresu IP. W przypadku systemu wielodomowego ta usługa wyłącza RARP na wszystkich interfejsach.

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

```c
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```
### <a name="see-also"></a>Zobacz też

- nx_rarp_enable
- nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable
Włącz protokół odwrotnego rozpoznawania adresów (RARP)

### <a name="prototype"></a>Prototype  

```c
UINT nx_rarp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa włącza składnik RARP programu NetX Duo dla określonego wystąpienia adresu IP. Składniki RARP przeszukują wszystkie podłączone interfejsy sieciowe dla zerowego adresu IP. Zerowy adres IP wskazuje, że interfejs nie ma jeszcze przypisywania adresów IP. RARP próbuje rozpoznać adres IP, włączając proces RARP w tym interfejsie.

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

```c
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
   resolve this IP instance’s address by querying the network. */
```
### <a name="see-also"></a>Zobacz też

- nx_rarp_disable
- nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get
Pobierz informacje o działaniach RARP

### <a name="prototype"></a>Prototype  

```c
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o działaniach RARP dla określonego wystąpienia IP.

> [!IMPORTANT]  
> *Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego*.

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

```c
/* Retrieve RARP information from previously created IP
   Instance 0. */
status = nx_rarp_info_get(&ip_0,
                          &rarp_requests_sent,
                          &rarp_responses_received,
                          &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```
### <a name="see-also"></a>Zobacz też

- nx_rarp_disable
- nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize
Zainicjuj system NetX Duo

### <a name="prototype"></a>Prototype  

```c
VOID nx_system_initialize(VOID);
```
### <a name="description"></a>Opis

Ta usługa inicjuje podstawowe zasoby systemu NetX Duo w przygotowaniu do użycia. Powinien być wywoływany przez aplikację podczas inicjowania i przed innymi wywołaniami NetX Duo.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

Brak

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze, procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

Zarządzanie systemem

### <a name="example"></a>Przykład

```c
/* Initialize NetX Duo for operation. */
nx_system_initialize();

/* At this point, NetX Duo is ready for IP creation and all
   subsequent network operations. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind
Powiąż gniazdo TCP klienta z portem TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa wiąże wcześniej utworzone gniazdo klienta TCP z określonym portem TCP. Prawidłowy zakres TCP Sockets należy do zakresu od 0 do 0xFFFF. Jeśli określony port TCP jest niedostępny, usługa zawiesza się zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- Numer **portu portu** do powiązania (od 1 do 0xFFFF). Jeśli numer portu to NX_ANY_PORT (0x0000), wystąpienie protokołu IP wyszuka następny bezpłatny port i użyje go do powiązania.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli port jest już powiązany z innym gniazdem. Opcje oczekiwania są zdefiniowane w następujący sposób:
- **NX_NO_WAIT** (0x00000000)
- **NX_WAIT_FOREVER** (0xffffffff)
- **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0x00) pomyślnego powiązania gniazda.
- **NX_ALREADY_BOUND** (0X22) to gniazdo jest już powiązane z innym portem TCP.
- Port **NX_PORT_UNAVAILABLE** (0x23) jest już powiązany z innym gniazdem.
- **NX_NO_FREE_PORTS** (0X45) brak wolnego portu.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_INVALID_PORT** (0X46) nieprawidłowy port.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Bind a previously created client socket to port 12 and wait for 7
   timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
   bound to port 12 on the associated IP instance. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect
Połącz gniazdo TCP klienta

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa łączy poprzednio utworzone i powiązane gniazdo klienta TCP z portem określonego serwera. Prawidłowe porty serwera TCP mieszczą się w zakresie od 0 do 0xFFFF. Jeśli połączenie nie zakończy się natychmiast, usługa zawiesza się zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **server_IP** Adres IP serwera.
- **SERVER_PORT** Numer portu serwera do połączenia * * (od 1 do 0xFFFF).
- **WAIT_OPTION** Definiuje sposób zachowania usługi podczas ustanawiania połączenia. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xffffffff)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

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

```c
/* Initiate a TCP connection from a previously created and bound
   client socket. The connection requested in this example is to
   port 12 on the server with the IP address of 1.2.3.5. This
   service will wait 300 timer ticks for the connection to take
   place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
                                      IP_ADDRESS(1,2,3,5),
                                      12, 300);

/* If status is NX_SUCCESS, the previously created and bound
   client_socket is connected to port 12 on IP 1.2.3.5. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get
Pobieranie numeru portu powiązanego z gniazdem TCP klienta

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>Opis

Ta usługa Pobiera numer portu skojarzony z gniazdem, który jest przydatny do znajdowania portu przydzielonego przez NetX Duo w sytuacjach, w których NX_ANY_PORT został określony w momencie powiązania gniazda.

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

```c
/* Get the port number of previously created and bound client
   socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind
Usuń powiązanie gniazda klienta TCP z portu TCP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
   bound. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_enable"></a>nx_tcp_enable
Włącz składnik TCP elementu NetX Duo

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa włącza składnik Transmission Control Protocol (TCP) NetX Duo. Po włączeniu połączenia TCP mogą być nawiązywane przez aplikację.

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

```c
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find
Znajdź następny dostępny port TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>Opis

Ta usługa próbuje zlokalizować bezpłatny port TCP (niepowiązany), rozpoczynając od portu dostarczonego przez aplikację. Logika wyszukiwania zostanie zawinięty, jeśli wyszukiwanie nastąpi do osiągnięcia maksymalnej wartości maksymalnego portu. Jeśli wyszukiwanie zakończyło się pomyślnie, port wolny jest zwracany w zmiennej wskazywanej przez *free_port_ptr*.

> [!WARNING]  
> *Ta usługa może być wywoływana z innego wątku i ma ten sam port. Aby uniknąć tego warunku wyścigu, aplikacja może chcieć umieścić tę usługę i rzeczywiste powiązanie gniazda klienta w ramach ochrony obiektu mutex*.

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

```c
/* Locate a free TCP port, starting at port 12, on a previously
   created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
   on the IP instance. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get
Pobierz informacje o działaniach TCP

### <a name="prototype"></a>Prototype  

```c
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

> [!IMPORTANT]  
> *Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego*.

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

```c
/* Retrieve TCP information from previously created IP Instance
   ip_0. */
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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept
Zaakceptuj połączenie TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa akceptuje (lub przygotowuje do akceptowania) żądanie połączenia gniazda klienta TCP dla portu, który został wcześniej skonfigurowany do nasłuchiwania. Ta usługa może być wywoływana natychmiast po wywołaniu przez aplikację nasłuchiwania lub ponownego nasłuchiwania albo gdy wywoływana jest procedura wywołania zwrotnego Listen, gdy połączenie z klientem jest rzeczywiście obecne. Jeśli połączenie nie może być od razu ustanowione, usługa zawiesza się zgodnie z podaną opcją oczekiwania.

> [!WARNING]  
> *Aplikacja musi wywoływać **nx_tcp_server_socket_unaccept** , gdy połączenie nie jest już potrzebne do usunięcia powiązania gniazda serwera z portem serwera*.

> [!IMPORTANT]  
> *Procedury wywołania zwrotnego aplikacji są wywoływane z wewnątrz wątku pomocnika IP*.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do bloku sterowania gniazda serwera TCP.
- **WAIT_OPTION** Definiuje sposób zachowania usługi podczas ustanawiania połączenia. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xffffffff)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) pomyślne zaakceptowanie gniazda serwera TCP (połączenie pasywne).
- **NX_NOT_LISTEN_STATE** (0x36) dostarczony gniazdo serwera nie jest w stanie nasłuchiwania.
- **NX_IN_PROGRESS** (0X37) nie określono oczekiwania, próba połączenia jest w toku.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- Błąd wskaźnika gniazda **NX_PTR_ERROR** (0x07).
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
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
        created
    */

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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen
Włącz nasłuchiwanie połączenia klienta na porcie TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```
### <a name="description"></a>Opis

Ta usługa umożliwia nasłuchiwanie żądania połączenia klienta na określonym porcie TCP. Po odebraniu żądania połączenia z klientem podane gniazdo serwera jest powiązane z określonym portem i wywoływana funkcja wywołania zwrotnego nasłuchiwania.

Przetwarzanie procedury wywołania zwrotnego Listen jest całkowicie do aplikacji. Może on zawierać logikę do wznowienia wątku aplikacji, który następnie wykonuje operację akceptacji. Jeśli aplikacja ma już zawieszony wątek przy akceptowaniu przetwarzania dla tego gniazda, procedura wywołania zwrotnego odbiornika może nie być wymagana.

Jeśli aplikacja chce obsługiwać dodatkowe połączenia klientów na tym samym porcie, ***nx_tcp_server_socket_relisten*** musi zostać wywołana z dostępnym gniazdem (gniazdo w stanie zamkniętym) dla następnego połączenia. Do momentu wywołania usługi ponownego nasłuchiwania dodatkowe połączenia klienckie są umieszczane w kolejce. Po przekroczeniu maksymalnej głębokości kolejki żądanie najstarszego połączenia zostanie porzucone na rzecz kolejkowania nowego żądania połączenia. Maksymalna głębokość kolejki jest określona przez tę usługę.

> [!IMPORTANT]  
> *Procedury wywołania zwrotnego aplikacji są wywoływane z wątku pomocnika wewnętrznego adresu IP*.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **port** Numer portu, na którym nasłuchuje nasłuchiwanie (od 1 do 0xFFFF).
- **socket_ptr** Wskaźnik do gniazda, który ma być używany w połączeniu.
- **listen_queue_size** Liczba żądań połączenia klienta, które można umieścić w kolejce.
- **listen_callback** Funkcja aplikacji do wywołania po odebraniu połączenia. Jeśli określono wartość NULL, funkcja wywołania zwrotnego Listen jest wyłączona.

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0X00) pomyślne włączenie nasłuchiwania portu TCP.
- **NX_MAX_LISTEN** (0X33) nie ma więcej dostępnych struktur żądań nasłuchiwania. Stała NX_MAX_LISTEN_REQUESTS w **_nx_api. h_** definiuje liczbę aktywnych żądań nasłuchiwania.
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

```c
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
}
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten
Ponowne nasłuchiwanie połączenia klienta na porcie TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>Opis

Ta usługa jest wywoływana po odebraniu połączenia na porcie, który został wcześniej skonfigurowany do nasłuchiwania. Głównym celem tej usługi jest udostępnienie nowego gniazda serwera dla następnego połączenia z klientem. Jeśli żądanie połączenia jest kolejkowane, połączenie zostanie przetworzone natychmiast w trakcie tego wywołania usługi.

> [!IMPORTANT]  
> Ta *sama procedura wywołania zwrotnego określona przez oryginalne żądanie Listen jest również wywoływana, gdy istnieje połączenie dla tego nowego gniazda serwera*.

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

```c
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
   nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
                                 NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                 NX_IP_TIME_TO_LIVE, 100,
                                 NX_NULL, port_12_disconnect_request);

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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept
Usuń skojarzenie gniazda z portem nasłuchiwania

### <a name="prototype"></a>Prototype  

```c
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

```c
NX_PACKET_POOL        my_pool;
NX_IP                 my_ip;
NX_TCP_SOCKET         server_socket;
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

NX_PACKET  *my_packet;
UINT       status, i;

   /* Assuming that:
     "port_12_semaphore" has already been created with an initial count
      of 0 "my_ip" has already been created and the link is enabled
     "my_pool" packet pool has already been created
   */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
                         Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                         NX_IP_TIME_TO_LIVE, 100,NX_NULL,
                         port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
       to
       each client and then disconnecting. */
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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten
Wyłącz nasłuchiwanie połączenia klienta na porcie TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_server_socket_unlisten(
    NX_IP *ip_ptr, 
    UINT port);
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

```c
NX_PACKET_POOL       my_pool;
NX_IP                my_ip;
NX_TCP_SOCKET        server_socket;

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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available
Pobiera liczbę bajtów dostępnych do pobrania

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,&bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
   bytes_available. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create
Utwórz klienta TCP lub gniazdo serwera

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, 
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Opis

Ta usługa tworzy gniazdo klienta TCP lub serwera dla określonego wystąpienia IP.

> [!NOTE]  
> *Procedury wywołania zwrotnego aplikacji są wywoływane z wątku skojarzonego z tym wystąpieniem adresu IP*.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **socket_ptr** Wskaźnik do nowego bloku sterowania gniazdem TCP.
- **Nazwa** Nazwa aplikacji dla tego gniazda TCP.
- **Type_of_Service** Definiuje typ usługi do transmisji, wartości prawne są następujące:
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)
- **fragment** Określa, czy jest dozwolone fragmentacja adresów IP. Jeśli określono NX_FRAGMENT_OKAY * * (0x0), jest dozwolone fragmentacja adresów IP. Jeśli określono NX_DONT_FRAGMENT (0x4000), fragmentacja adresów IP jest wyłączona.
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

```c
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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete
Usuń gniazdo TCP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect
Rozłączanie połączeń klienta i gniazda serwera

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa rozłącza ustanowione połączenie z gniazdem klienta lub serwera. Po rozłączeniu gniazda serwera powinno następować żądanie nieakceptowane, a gniazdo klienta, które zostało odłączone, pozostaje w stanie gotowym do innego żądania połączenia. Jeśli proces rozłączenia nie może zakończyć się natychmiast, usługa zawiesza się zgodnie z podaną opcją oczekiwania.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, gdy trwa odłączanie. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xffffffff)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

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

```c
/* Disconnect from a previously established connection and wait a
   maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
   as a result of the client socket connect or the server accept) is
   disconnected. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify
Zainstaluj funkcję wywołania zwrotnego powiadomienia o rozłączeniu protokołu TCP
 
### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana po zakończeniu operacji rozłączenia gniazda. Funkcja wywołania zwrotnego rozłączenia gniazda TCP jest dostępna, jeśli NetX Duo jest skompilowany przy użyciu opcji zdefiniowanej ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** .

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.
- **tcp_disconnect_complete_notify** Funkcja wywołania zwrotnego do zainstalowania.

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) pomyślnie zarejestrował funkcję wywołania zwrotnego.
- **NX_NOT_SUPPORTED** (0x4B) Funkcja rozszerzonego powiadamiania nie jest wbudowana w bibliotece NetX Duo NX_PTR_ERROR * * (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
                                                  callback);
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_setnx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify
Ustaw funkcję wywołania zwrotnego powiadomienia o ustanowieniu protokołu TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana po nawiązaniu połączenia przez gniazdo TCP. Funkcja wywołania zwrotnego gniazda TCP jest dostępna, jeśli NetX Duo jest skompilowany przy użyciu opcji ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** zdefiniowanej.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.
- **tcp_establish_notify** Wywoływanie funkcji wywołania zwrotnego po nawiązaniu połączenia TCP.

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0X00) pomyślnie ustawia funkcję powiadamiania.
- **NX_NOT_SUPPORTED** (0x4B) Funkcja rozszerzonego powiadamiania nie jest wbudowana w bibliotece NetX Duo 
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) TCP nie został włączony przez aplikację.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Set the function pointer "callback" as the notify function NetX
   Duo will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get
Pobierz informacje o działaniach gniazda TCP

### <a name="prototype"></a>Prototype  

```c
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

> [!NOTE]  
> *Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego*.

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

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Retrieve TCP socket information from previously created
   socket_0.*/
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

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get
Pobierz rozmiar pasma gniazda

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket's current MSS value. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get
Pobierz rozmiar pasma równorzędnego gniazda TCP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket peer’s advertised MSS value. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set
Ustaw rozmiar pasma gniazda

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get
Pobierz informacje o gnieździe równorzędnym TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o adresie IP i porcie elementu równorzędnego dla połączonego gniazda TCP za pośrednictwem sieci IPv4. Równoważna usługa, która również obsługuje sieci IPv6, jest ***nxd_tcp_socket_peer_info_get.***

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

```c
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
                                     &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_queue_depth_notify_set"></a>nx_tcp_socket_queue_depth_notify_set
Ustaw funkcję powiadamiania kolejki transmisji protokołu TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_queue_depth_notify_set(
              NX_TCP_SOCKET *socket_ptr,
              VOID(*tcp_socket_queue_depth_notify)(NX_TCP_SOCKET *));
```
### <a name="description"></a>Opis

Ta usługa ustawia funkcję powiadamiania o aktualizacji głębokości kolejki przesyłania określona przez aplikację, która jest wywoływana za każdym razem, gdy określone gniazdo określa, że wydano pakiety z kolejki transmisji, tak że głębokość kolejki nie przekracza już limitu. Jeśli aplikacja zostanie zablokowana przy przesyłaniu ze względu na głębokość kolejki, funkcja wywołania zwrotnego służy jako powiadomienie do aplikacji, którą może ponownie rozpocząć transmitowanie. Ta usługa jest dostępna tylko wtedy, gdy biblioteka NetX Duo została skompilowana przy użyciu opcji ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY*** zdefiniowanej.

### <a name="parameters"></a>Parametry 

- **socket_ptr** Wskaźnik do struktury gniazda 
- **tcp_socket_queue_depth_notify** Funkcja powiadamiania, która ma zostać zainstalowana

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0X00) pomyślnie zainstalował funkcję powiadamiania
- **NX_NOT_SUPPORTED** (0x4B) funkcja powiadamiania o głębokości kolejki gniazda TCP nie jest wbudowana w bibliotekę NetX Duo
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do bloku sterowania gniazdem lub funkcji powiadamiania
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
VOID tcp_socket_queue_depth_notify(NX_TCP_SOCKET *socket_ptr)
{
   /* Notify the application to resume sending. */

}
/* Install the TCP transmit queue notify function .*/
status = nxd_tcp_socket_queue_depth_notify_set(&tcp_socket,
                                  tcp_socket_queue_depth_notify);

/* If status == NX_SUCCESS, the callback function is successfully
   installed. */
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive
Odbieranie danych z gniazda TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa odbiera dane TCP z określonego gniazda. Jeśli dane nie są umieszczane w kolejce w określonym gnieździe, obiekt wywołujący zawiesza się na podstawie podanej opcji oczekiwania.

> [!CAUTION]  
> *Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne*.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda TCP.
- **packet_ptr** Wskaźnik na wskaźnik pakietu TCP.
- **WAIT_OPTION** Definiuje sposób zachowania usługi, jeśli dane są obecnie umieszczane w kolejce w tym gnieździe. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xffffffff)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

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

```c
/* Receive a packet from the previously created and connected TCP
   client socket. If no packet is available, wait for 200 timer
   ticks before giving up. */
status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* If status is NX_SUCCESS, the received packet is pointed to by
   "packet_ptr". */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify
Powiadamiaj aplikację o odebranych pakietach

### <a name="prototype"></a>Prototype   

```c
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr, 
    VOID (*tcp_receive_notify)(NX_TCP_SOCKET *socket_ptr));
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

```c
/* Setup a receive packet callback function for the "client_socket"
   socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever one or more packets are received for
   "client_socket". */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send
Wysyłanie danych za pośrednictwem gniazda TCP

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa wysyła dane TCP za pośrednictwem wcześniej połączonego gniazda TCP. Jeśli rozmiar okna o ostatnio anonsowanym odbiorniku jest mniejszy niż to żądanie, usługa opcjonalnie zawiesza się na podstawie podanej opcji oczekiwania. Ta usługa gwarantuje, że do warstwy IP nie są wysyłane żadne dane pakietu o rozmiarze większym niż wartość maksymalna. 

> [!WARNING]  
> *Jeśli błąd nie zostanie zwrócony, aplikacja nie powinna zwolnić pakietu po tym wywołaniu. Wykonanie tej operacji spowoduje nieprzewidywalne wyniki, ponieważ sterownik sieciowy podejmie również próbę zwolnienia pakietu po transmisji*.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia gniazda TCP.
- **packet_ptr** Wskaźnik pakietu danych TCP.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądanie jest większe niż rozmiar okna odbiornika. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xffffffff)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

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

```c
/* Send a packet out on the previously created and connected TCP
   socket. If the receive window on the other side of the connection
   is less than the packet size, wait 200 timer ticks before giving
   up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait
Poczekaj, aż gniazdo TCP przeniesie określony stan

### <a name="prototype"></a>Prototype  

```c
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
    - **NX_TCP_CLOSED** (0x01)
    - **NX_TCP_LISTEN_STATE** (0x02)
    - **NX_TCP_SYN_SENT** (0x03)
    - **NX_TCP_SYN_RECEIVED** (0x04)
    - **NX_TCP_ESTABLISHED** (0x05)
    - **NX_TCP_CLOSE_WAIT** (0x06)
    - **NX_TCP_FIN_WAIT_1** (0x07)
    - **NX_TCP_FIN_WAIT_2** (0x08)
    - **NX_TCP_CLOSING** (0x09)
    - **NX_TCP_TIMED_WAIT** (0x0A)
    - **NX_TCP_LAST_ACK** (0x0B)
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli żądany stan nie jest obecny. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **wartość limitu czasu w taktach** (0X00000001 do 0xffffffff)

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

```c
/* Wait 300 timer ticks for the previously created socket to enter
   the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
                                  NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
   state! */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback
Instalacja wywołania zwrotnego dla stanu oczekiwania, który upłynął

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego, która jest wywoływana, gdy gniazdo TCP jest w stanie oczekiwania. Aby można było korzystać z tej usługi, biblioteka NetX Duo musi być skompilowana przy użyciu opcji ***NX_ENABLE_EXTENDED_NOTIFY*** zdefiniowanej.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej połączonego wystąpienia klienta lub gniazda serwera.
- **tcp_timed_wait_callback** Funkcja wywołania zwrotnego czasu oczekiwania

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) pomyślnie rejestruje gniazdo funkcji wywołania zwrotnego
- Biblioteka **NX_NOT_SUPPORTED** (0X4B) NetX Duo została skompilowana bez włączonej funkcji rozszerzonego powiadamiania.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- Funkcja TCP **NX_NOT_ENABLED** (0x14) nie jest włączona.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure
Konfiguruj parametry transmisji gniazda

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Configure the "client_socket" for a maximum transmit queue depth of
   12, 100 tick timeouts, a maximum of 20 retries, and a timeout double
   on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,12,100,20,1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
   configured. */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set
Powiadamianie o aktualizacjach rozmiaru okna

### <a name="prototype"></a>Prototype  

```c
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_window_update_notify)(NX_TCP_SOCKET *socket_ptr));
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

```c
/* Set the function pointer to the windows update callback after creating the
   socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
                                                my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(&data_socket)
{

/* Process update on increase TCP transmit socket window size. */
   return;
}
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable
Włącz składnik UDP elementu NetX Duo

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa włącza składnik UDP (User Datagram Protocol) programu NetX Duo. Po włączeniu protokołu UDP datagramy mogą być wysyłane i odbierane przez aplikację.

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

```c
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
   instance. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find
Znajdź następny dostępny port UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>Opis

Ta usługa szuka bezpłatnego portu UDP (niepowiązanego) rozpoczynającego się od dostarczonej przez aplikację numeru portu. Logika wyszukiwania zostanie zawinięty, jeśli wyszukiwanie osiągnie maksymalną wartość dla wartości 0xFFFF. Jeśli wyszukiwanie zakończyło się pomyślnie, port wolny jest zwracany w zmiennej wskazywanej przez free_port_ptr.

> [!WARNING]  
> *Ta usługa może być wywoływana z innego wątku i może mieć ten sam port. Aby uniknąć tego warunku wyścigu, aplikacja może chcieć umieścić tę usługę i rzeczywiste powiązanie gniazda w ramach ochrony obiektu mutex*.

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

```c
/* Locate a free UDP port, starting at port 12, on a previously
   created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
   free UDP port on the IP instance. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get
Pobierz informacje o działaniach UDP

### <a name="prototype"></a>Prototype  

```c
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

> [!IMPORTANT]  
> *Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego*.

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

```c
/* Retrieve UDP information from previously created IP Instance
   ip_0. */
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

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract
Wyodrębnij parametry sieci z pakietu UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>Opis

Ta usługa wyodrębnia parametry sieci, takie jak adres IPv4, numer portu równorzędnego, typ protokołu (usługa zawsze zwraca typ UDP) z pakietu otrzymanego w interfejsie przychodzącym. Aby uzyskać informacje na temat pakietu przychodzącego z sieci IPv4 lub IPv6, aplikacja używa nxd_udp_packet_info_extract usługi ***.***

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu.
- **IP_address** Wskaźnik na adres IP nadawcy.
- **Protokół** Wskaźnik do protokołu UDP.
- **port** Wskaźnik na numer portu nadawcy.
- **interface_index** Wskaźnik do odbioru indeksu interfejsu.

### <a name="return-values"></a>Wartości zwrócone  

- Pomyślnie wyodrębniono dane interfejsu pakietu **NX_SUCCESS** (0x00).
- Pakiet **NX_INVALID_PACKET** (0x12) nie zawiera ramki IPv4.
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract(packet_ptr, &ip_address,
                                     &protocol, &port,
                                     &interface_index);

/* If status is NX_SUCCESS packet data was successfully
   retrieved. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind
Powiąż gniazdo UDP z portem UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa wiąże wcześniej utworzone gniazdo UDP z określonym portem UDP. Prawidłowy zakres UDP wynosi od 0 do 0xFFFF. Jeśli żądany numer portu jest powiązany z innym gniazdem, ta usługa czeka przez określony czas, w którym gniazdo ma usunąć powiązanie z numerem portu.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.
- **port** Numer portu do powiązania * * (od 1 do 0xFFFF). Jeśli numer portu to NX_ANY_PORT * * (0x0000), wystąpienie protokołu IP przeszuka następny bezpłatny port i użyje go do powiązania.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli port jest już powiązany z innym gniazdem. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xffffffff)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

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

```c
/* Bind the previously created UDP socket to port 12 on the
   previously created IP instance. If the port is already bound,
   wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
   port 12.*/
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available
Pobiera liczbę bajtów dostępnych do pobrania

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket,
                                       &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
   retrieved.*/
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable
Wyłącz sumę kontrolną dla gniazda UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Opis

Ta usługa wyłącza logikę sumy kontrolnej na potrzeby wysyłania i otrzymywania pakietów w określonym gnieździe UDP. Gdy logika sum kontrolnych jest wyłączona, wartość zero jest ładowana do pola sumy kontrolnej nagłówka UDP dla wszystkich pakietów wysyłanych za pomocą tego gniazda. Wartość sumy kontrolnej zero wartości w nagłówku UDP sygnalizuje odbiornikowi, że suma kontrolna nie jest obliczana dla tego pakietu.

Należy również zauważyć, że nie ma to wpływu, jeśli **NX_DISABLE_UDP_RX_CHECKSUM** i **NX_DISABLE_UDP_TX_CHECKSUM** są zdefiniowane podczas otrzymywania i wysyłania pakietów UDP odpowiednio,

Należy pamiętać, że ta usługa nie ma wpływu na pakiety w sieci IPv6, ponieważ suma kontrolna UDP jest obowiązkowa dla protokołu IPv6.

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

```c
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
   calculated. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable
Włącz sumę kontrolną dla gniazda UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>Opis

Ta usługa umożliwia logikę sumy kontrolnej na potrzeby wysyłania i otrzymywania pakietów w określonym gnieździe UDP. Suma kontrolna obejmuje cały obszar danych UDP oraz nagłówek pseudo IP.

Należy również pamiętać, że nie ma to wpływu, jeśli **NX_DISABLE_UDP_RX_CHECKSUM** i **NX_DISABLE_UDP_TX_CHECKSUM** są zdefiniowane podczas otrzymywania i wysyłania pakietów UDP odpowiednio.

Należy zauważyć, że ta usługa nie ma wpływu na pakiety w sieci IPv6. Suma kontrolna UDP jest obowiązkowa w protokole IPv6.

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

```c
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
   calculated. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create
Utwórz gniazdo UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, 
    CHAR *name,
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG queue_maximum);
```
### <a name="description"></a>Opis

Ta usługa tworzy gniazdo UDP dla określonego wystąpienia IP.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP.
- **socket_ptr** Wskaźnik do nowej kontrolki gniazda UDP blo.
- **Nazwa** Nazwa aplikacji dla tego gniazda UDP.
- **Type_of_Service** Definiuje typ usługi do transmisji, wartości prawne są następujące:
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)
- **fragment określa** , czy jest dozwolone fragmentacja adresów IP. Jeśli określono NX_FRAGMENT_OKAY (0x0), jest dozwolone fragmentacja adresów IP. Jeśli określono NX_DONT_FRAGMENT (0x4000), fragmentacja adresów IP jest wyłączona.
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

```c
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
                              NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80,
                              30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
   is ready for binding. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete
Usuń gniazdo UDP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
   been deleted. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get
Pobierz informacje o działaniach gniazda UDP

### <a name="prototype"></a>Prototype  

```c
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

> [!IMPORTANT]  
> *Jeśli wskaźnik docelowy jest NX_NULL, to konkretne informacje nie są zwracane do obiektu wywołującego*.

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

```c
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

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get
Wybierz numer portu powiązany z gniazdem UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_port_get(
    NX_UDP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>Opis

Ta usługa Pobiera numer portu skojarzony z gniazdem, który jest przydatny do znajdowania portu przydzielonego przez NetX Duo w sytuacjach, w których NX_ANY_PORT został określony w momencie powiązania gniazda.

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

```c
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive
Odbieranie datagramu z gniazda UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa odbiera datagram UDP od określonego gniazda. Jeśli żaden datagram nie jest umieszczony w określonym gnieździe, obiekt wywołujący zawiesza się na podstawie podanej opcji oczekiwania.

> [!CAUTION]  
> *Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne*.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP.
- **packet_ptr** Wskaźnik na wskaźnik pakietu datagramu UDP.
- **WAIT_OPTION** Definiuje, w jaki sposób działa usługa, jeśli datagram nie jest obecnie umieszczony w tym gnieździe. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xffffffff)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0x00) odbieranie w gnieździe zakończone powodzeniem.
- Gniazdo **NX_NOT_BOUND** (0x24) nie zostało powiązane z żadnym portem.
- **NX_NO_PACKET** (0x01) brak datagramu UDP do odebrania.
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik powrotu gniazda lub pakietu.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi.
- **NX_NOT_ENABLED** (0X14) ten składnik nie został włączony.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Receive a packet from a previously created and bound UDP socket.
   If no packets are currently available, wait for 500 timer ticks
   before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
   packet_ptr. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify
Powiadamiaj aplikację o każdym odebranym pakiecie

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)(NX_UDP_SOCKET *socket_ptr));
```
### <a name="description"></a>Opis 

Ta usługa ustawia wskaźnik funkcji Odbierz powiadomienie na funkcję wywołania zwrotnego określonego przez aplikację. Ta funkcja wywołania zwrotnego jest wywoływana za każdym razem, gdy pakiet jest odbierany w gnieździe. Jeśli zostanie dostarczony NX_NULL wskaźnik, funkcja Odbierz powiadomienie jest wyłączona.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik na gniazdo UDP.
- **udp_receive_notify** Wskaźnik funkcji wywołania zwrotnego aplikacji, który jest wywoływany, gdy pakiet jest odbierany w gnieździe.

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0X00) pomyślnie ustawił funkcję powiadamiania odbioru gniazda.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Setup a receive packet callback function for the "udp_socket"
   socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever a packet is received for
   "udp_socket". */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send
Wysyłanie datagramu UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address, 
    UINT port);
```
### <a name="description"></a>Opis

Ta usługa wysyła datagram UDP za pomocą poprzednio utworzonego i powiązanego gniazda UDP dla sieci IPv4. NetX Duo znajduje odpowiedni lokalny adres IP jako adres źródłowy na podstawie docelowego adresu IP. Aby określić konkretny interfejs i źródłowy adres IP, aplikacja powinna używać usługi  **nxd_udp_socket_source_send** .

Należy zauważyć, że ta usługa wraca natychmiast niezależnie od tego, czy datagram UDP został pomyślnie wysłany. Odpowiednik usługi NetX Duo (IPv4/IPv6) jest ***nxd_udp_socket_send***.

Gniazdo musi być powiązane z portem lokalnym.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP
- **packet_ptr** Wskaźnik pakietu datagramu UDP
- **IP_address** Docelowy adres IPv4
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

```c
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

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_source_send"></a>nx_udp_socket_source_send
Wyślij datagram za poorednictwem gniazda UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```
### <a name="description"></a>Opis

Ta usługa wysyła datagram UDP przy użyciu wcześniej utworzonego i powiązanego gniazda UDP za pomocą interfejsu sieciowego z określonym adresem IP jako adresem źródłowym. Należy pamiętać, że usługa wraca natychmiast, niezależnie od tego, czy datagram UDP został pomyślnie wysłany. ***nxd_udp_socket_source_send*** działa zarówno dla sieci IPv4, jak i IPv6.

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

```c
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
   interface at index 1 in the IP task interface list. */
status = nx_udp_socket_source_send(socket_ptr, packet_ptr,
                                   destination_ip, 80,
                                   ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind
Usuń powiązanie gniazda UDP z portu UDP

### <a name="prototype"></a>Prototype  

```c
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

```c
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
   unbound. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract
Wyodrębnij adres IP i Wyślij port z datadatagramu UDP

### <a name="prototype"></a>Prototype  

```c
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, 
    UINT *port);
```
### <a name="description"></a>Opis

Ta usługa wyodrębnia adres IP i numer portu nadawcy z nagłówków IP i UDP dostarczonego datagramu UDP. Należy pamiętać, że usługa ***nxd_udp_source_extract*** współpracuje z pakietami z sieci IPv4 lub IPv6.

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

```c
/* Extract the IP and port information from the sender of the UPD packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address, &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has been stored
   in sender_ip_address and sender_port respectively.*/
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_icmp_enable"></a>nxd_icmp_enable
Włączanie usług ICMPv4 i ICMPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa włącza zarówno usługi ICMPv4, jak i ICMPv6 i może być wywoływana tylko po utworzeniu wystąpienia adresu IP. Usługę można włączyć albo przed lub po włączeniu protokołu IPv6 (zobacz *nxd_ipv6_enable*). Usługi ICMPv4 obejmują żądanie echa/odpowiedź. Usługi ICMPv6 obejmują żądanie echa/odpowiedź, odnajdywanie sąsiadów, wykrywanie zduplikowanych adresów, odnajdywanie routera i Autokonfiguracja adresu bezstanowego. Odpowiednik protokołu IPv4 w NetX jest *nx_icmp_enable*.

> [!NOTE] 
> *Jeśli adres IPv6 został ręcznie skonfigurowany przed włączeniem protokołu ICMPv6, ręcznie skonfigurowany protokół IPv6 nie podlega procesowi wykrywania zduplikowanych adresów*.

*nx_icmp_enable* uruchamia usługi ICMP tylko dla operacji IPv4. Aplikacje korzystające z usług ICMPv6 muszą używać *nxd_icmp_enable* zamiast *nx_icmp_enable*.

Aby można było użyć żądania routera IPv6 i bezstanowej automatycznej konfiguracji protokołu IPv6, należy włączyć protokół ICMPv6.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0x00) usługi ICMP zostały pomyślnie włączone
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Enable ICMP on the IP instance. */
status = nxd_icmp_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for ICMP services. */
```
### <a name="see-also"></a>Zobacz też

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_ping"></a>nxd_icmp_ping
Wykonywanie żądań echa ICMPv4 lub ICMPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_icmp_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr, 
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa wysyła pakiet żądania echa ICMP za pośrednictwem odpowiedniego interfejsu fizycznego i czeka na odpowiedź ECHA z hosta docelowego. NetX Duo określa odpowiedni interfejs na podstawie adresu docelowego, aby wysłać wiadomość ping. Aplikacje używają ***nxd_icmp_source_ping*** usługi, aby określić interfejs fizyczny i dokładny źródłowy adres IP, który ma być używany na potrzeby przesyłania pakietów.

Należy utworzyć wystąpienie protokołu IP, a usługi ICMPv4/ICMPv6 muszą być włączone (zobacz ***nxd_icmp_enable***).

> [!WARNING]  
> Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wystąpienia adresu IP
- **IP_address** Docelowy adres IP do ping w kolejności bajtów hosta
- **data_ptr** Wskaźnik do polecenia ping dla obszaru danych pakietu
- **data_size** Liczba bajtów danych ping
- **response_ptr** Wskaźnik do odpowiedzi na wskaźnik pakietu
- **WAIT_OPTION** Czas oczekiwania na odpowiedź. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **wartość limitu czasu w taktach** (0x00000001 przez 
    - **NX_WAIT_FOREVER** 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie wysłano i otrzymano polecenie ping
- **NX_NOT_SUPPORTED** (0X4B) protokół IPv6 nie jest włączony
- Dane ping **NX_OVERFLOW** (0x03) przekraczają ładunek pakietu
- Host docelowy **NX_NO_RESPONSE** (0x29) nie odpowiedział
- **NX_WAIT_ABORTED** (0X1A) żądanie zawieszenia zostało przerwane przez tx_thread_wait_abort
- **NX_NO_INTERFACE_ADDRESS** (0X50) nie można znaleźć odpowiedniego interfejsu wychodzącego.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub odpowiedzi
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- **NX_NOT_ENABLED** (0x14) nie włączono składnika IP lub protokołu ICMP
- **NX_IP_ADDRESS_ERROR** (0X21) wejściowy adres IP jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* The following two examples illustrate how to use this API to send
   ping packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   2001:1234:5678::1 */
   
/* Declare variable address to hold the destination address. */
NXD_ADDRESS ip_address;

char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0x20011234;
ip_address.nxd_ip_address.v6[1]    = 0x56780000;
ip_address.nxd_ip_address.v6[2]    = 0;
ip_address.nxd_ip_address.v6[3]    = 1;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr,
                       NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been
   received from IP address 2001:1234:5678::1 and the response
   packet is contained in the packet pointed to by response_ptr.It
   should have the same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4[0]    = 0x01020304;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr, 10);

/* A return value of NX_SUCCESS indicates a ping reply was received
   from IP address 1.2.3.4 and the response packet is contained in
   the packet pointed to by response_ptr. It should have the same
   “abcd” four bytes of data. */
```
### <a name="see-also"></a>Zobacz też

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_source_ping"></a>nxd_icmp_source_ping
Wykonywanie żądań echa ICMPv4 lub ICMPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_icmp_source_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    UINT address_index,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa wysyła pakiet żądania echa protokołu ICMP przy użyciu określonego indeksu adresu IPv4 lub IPv6 oraz za pośrednictwem interfejsu sieciowego, z którym jest skojarzony adres źródłowy, i czeka na odpowiedź ECHA z hosta docelowego. Ta usługa działa z adresami IPv4 i IPv6. Parametr *address_index* wskazuje źródłowy adres IPv4 lub IPv6 do użycia. W przypadku adresu IPv4 *address_index* jest tym samym indeksem do dołączonego interfejsu sieciowego. W przypadku protokołu IPv6 *address_index* wskazuje wpis w tabeli adresów IPv6.

Należy utworzyć wystąpienie protokołu IP, a usługi ICMPv4 i ICMPv6 muszą być włączone (zobacz *nxd_icmp_enable*).

> [!CAUTION] 
> *Jeśli NX_SUCCESS jest zwracana, aplikacja jest odpowiedzialna za zwolnienie odebranego pakietu, gdy nie jest już potrzebne*.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wystąpienia adresu IP
- **IP_address** Docelowy adres IP do ping w kolejności bajtów hosta
- **address_index** Wskazuje adres IP, który ma być używany jako adres źródłowy
- **data_ptr** Wskaźnik do polecenia ping dla obszaru danych pakietu
- **data_size** Liczba bajtów danych ping
- **response_ptr** Wskaźnik do odpowiedzi na wskaźnik pakietu
- **WAIT_OPTION** Czas oczekiwania na odpowiedź. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE
    - **NX_WAIT_FOREVER** 0xffffffff)

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0X00) pomyślnie wysłano i otrzymano polecenie ping
- **NX_NOT_SUPPORTED** (0X4B) protokół IPv6 nie jest włączony
- Dane ping **NX_OVERFLOW** (0x03) przekraczają ładunek pakietu
- Host docelowy **NX_NO_RESPONSE** (0x29) nie odpowiedział
- **NX_WAIT_ABORTED** (0X1A) żądanie zawieszenia zostało przerwane przez tx_thread_wait_abort
- **NX_NO_INTERFACE_ADDRESS** (0X50) nie można znaleźć odpowiedniego interfejsu wychodzącego
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub odpowiedzi
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- **NX_NOT_ENABLED** (0x14) nie włączono składnika IP lub protokołu ICMP
- **NX_IP_ADDRESS_ERROR** (0X21) wejściowy adres IP jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* The following two examples illustrate how to use this API to send ping
   packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   FE80::411:7B23:40dc:f181 */

/* Declare variable address to hold the destination address. */

#define PRIMARY_INTERFACE 0
#define GLOBAL_IPv6_ADDRESS 1

NXD_ADDRESS ip_address;
char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0xFE800000;
ip_address.nxd_ip_address.v6[1]    = 0x00000000;
ip_address.nxd_ip_address.v6[2]    = 0x04117B23;
ip_address.nxd_ip_address.v6[3]    = 0x40DCF181;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              GLOBAL_IPv6_ADDRESS,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been received
   from IP address FE80::411:7B23:40dc:f181 and the response packet is
   contained in the packet pointed to by response_ptr. It should have the
   same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4       = 0x01020304;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              PRIMARY_INTERFACE,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply was received from
   IP address 1.2.3.4 and the response packet is contained in the packet
   pointed to by response_ptr. It should have the same “abcd” four bytes
   of data. */
```

### <a name="see-also"></a>Zobacz też

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmpv6_ra_flag_callback_set"></a>nxd_icmpv6_ra_flag_callback_set
Ustaw funkcję wywołania zwrotnego zmiany flagi urzędu rejestrowania ICMPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_icmpv6_ra_flag_callback_set(
    NX_IP *ip_ptr, 
    VOID(*ra_callback)(NX_IP*ip_ptr, UINT ra_flag));
```
### <a name="description"></a>Opis

Ta usługa ustawia funkcję wywołania zwrotnego dla flagi anons routera ICMPv6. Funkcja wywołania zwrotnego dostarczonego przez użytkownika jest wywoływana, gdy NetX Duo odbiera komunikat anonsu routera.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wystąpienia adresu IP
- **ra_callback** Funkcja wywołania zwrotnego dostarczonego przez użytkownika

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) pomyślnie ustawiono funkcję wywołania zwrotnego flagi urzędu rejestrowania
- **NX_NOT_SUPPORTED** (0X4B) protokół IPv6 nie jest włączony
- **NX_PTR_ERROR** (0X07) nieprawidłowy adres IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
VOID icmpv6_ra_flag_callback(NX_IP *ip_ptr, UINT ra_flag)
{
   /* RA flag has changed. The updated value is passed in via the
      ra_flag parameter. */
}

/* Configure the user-defined ICMPv6 RA flag change callback
   function. */
status = nxd_icmpv6_ra_flag_callback_set(&ip_0,
                                         icmpv6_ra_flag_callback);

/* A status return of NX_SUCCESS indicates the callback function has
   been successfully configured. */
```
### <a name="see-also"></a>Zobacz też

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping

## <a name="nxd_ip_raw_packet_send"></a>nxd_ip_raw_packet_send
Wyślij pakiet Raw IP

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ip_raw_packet_send(
    NX_IP *ip_ptr, 
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination
    ULONG protocol, 
    UINT ttl, 
    ULONG tos);
```
### <a name="description"></a>Opis

Ta usługa wysyła nieprzetworzony pakiet IPv4 lub IPv6 (bez nagłówków protokołu warstwy transportu). Jeśli system nie może określić odpowiedniego interfejsu w systemie wielosystemowym (na przykład jeśli docelowy adres IP to adres IPv4 emisji, Multiemisja lub IPv6), urządzenie podstawowe jest zaznaczone. Usługa ***nxd_ip_raw_packet_source_send** _ może służyć do określania interfejsu wychodzącego. Odpowiednik NetX jest _ *_nx_ip_raw_packet_send_.**

Należy wcześniej utworzyć wystąpienie protokołu IP, a obsługa pakietów pierwotnych adresów IP musi być włączona za pomocą usługi ***nx_ip_raw_packet_enable*** .

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **packet_ptr** Wskaźnik do pakietu do przesłania
- **destination_ip** Wskaźnik na adres docelowy
- **Protokół** Protokół pakietu przechowywany w nagłówku protokołu IP
- **czas wygaśnięcia** Wartość dla limitu czasu wygaśnięcia lub przeskoku
- **OT** Wartość dla OT lub klasy ruchu i etykiety przepływu

### <a name="return-value"></a>Wartość zwracana 

- **NX_SUCCESS** (0X00) pierwotny pakiet protokołu IP został pomyślnie wysłany
- **NX_NO_INTERFACE_ADDRESS** (0X50) nie można znaleźć odpowiedniego interfejsu wychodzącego
- Niewłączona obsługa pierwotnych adresów IP **NX_NOT_ENABLED** (0x14)
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IPv4 lub IPv6
- **NX_UNDERFLOW** (0X02) nie ma wystarczającej ilości miejsca dla nagłówka IPv4 lub IPv6 w pakiecie
- Wskaźnik dołączania pakietu **NX_OVERFLOW** (0x03) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP lub wskaźnika pakietu
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- **NX_INVALID_PARAMETERS** (0x4D) nieprawidłowe dane wejściowe adresu IPv6

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
NXD_ADDRESS dest_address;

/* Set the destination address,in this case an IPv6 address. */
dest_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
dest_address.nxd_ip_address.v6[0]    = 0x20011234;
dest_address.nxd_ip_address.v6[1]    = 0x56780000;
dest_address.nxd_ip_address.v6[2]    = 0;
dest_address.nxd_ip_address.v6[3]    = 1;

UINT ttl, tos;

ttl = 128;

tos = 0;

/* Enable RAW IP handling on the previously created IP instance.*/
status = nx_raw_ip_packet_enable(&ip_0);

/* Allocate a packet pointed to by packet_ptr from the IP packet
   pool. */
/* Then transmit the packet to the destination address. */

status = nxd_ip_raw_packet_send(&ip_0, packet_ptr, dest_address,
                                NX_PROTOCOL_UDP, ttl, tos);

/* A status return of NX_SUCCESS indicates the packet was
   successfully transmitted. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_source_send

## <a name="nxd_ip_raw_packet_source_send"></a>nxd_ip_raw_packet_source_send
Wyślij pakiet pierwotny przy użyciu określonego adresu źródłowego

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination_ip,
    UINT address_index,
    ULONG protocol,
    UINT ttl,
    ULONG tos);
```
### <a name="description"></a>Opis

Ta usługa wysyła nieprzetworzony pakiet IPv4 lub IPv6 przy użyciu określonego adresu IPv4 lub IPv6 jako adresu źródłowego. Ta usługa jest zwykle używana w systemie wielosystemowym, jeśli system nie może określić odpowiedniego interfejsu (na przykład jeśli docelowy adres IP to adres IPv4 emisji, multiemisji lub multiemisji IPv6). Parametr *address_index* umożliwia aplikacji określenie adresu źródłowego do użycia podczas wysyłania tego pierwotnego pakietu.

Należy wcześniej utworzyć wystąpienie protokołu IP, a obsługa pakietów pierwotnych adresów IP musi być włączona za pomocą usługi ***nx_ip_raw_packet_enable*** .

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik wystąpienia adresu IP
- **packet_ptr** Wskaźnik do pakietu do wysłania
- **destination_ip** Docelowy adres IP
- **address_index** Indeks adresów IPv4 lub IPv6, które mają być używane jako adresy źródłowe.
- **Protokół** Wartość pola protokół
- **czas wygaśnięcia** Wartość dla limitu czasu wygaśnięcia lub przeskoku
- **OT** Wartość dla OT lub klasy ruchu i etykiety przepływu

### <a name="return-values"></a>Wartości zwrócone 

- Pomyślnie wysłano pakiet **NX_SUCCESS** (0x00)
- **NX_UNDERFLOW** (0X02) nie ma wystarczającej ilości miejsca dla nagłówka IPv4 lub IPv6 w pakiecie
- Wskaźnik dołączania pakietu **NX_OVERFLOW** (0x03) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik do bloku kontroli IP, pakietu lub destination_ip
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- Przetwarzanie nieprzetworzone **NX_NOT_ENABLED** (0x14) nie jest włączone
- Błąd adresu **NX_IP_ADDRESS_ERROR** (0x21)
- **NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy indeks interfejsu
- **NX_INVALID_PARAMETERS** (0x4D) nieprawidłowe dane wejściowe adresu IPv6

### <a name="allowed-from"></a>Dozwolone z

Thread

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define SOURCE_ADDRESS_INDEX 2

/* Send a raw packet from specified interface. */
status = nxd_ip_raw_packet_source_send(&ip_0, packet_ptr,
                                       dest_ip,
                                       SOURCE_ADDRESS_INDEX,
                                       NX_IP_RAW,
                                       NX_IP_TIME_TO_LIVE,
                                       NX_IP_NORMAL);

/* If status == NX_SUCCESS, raw packet has been sent out on the
   specified interface. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send

## <a name="nxd_ipv6_address_change_notify"></a>nxd_ipv6_address_change_notify
Ustaw powiadomienie o zmianie adresu IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_address_change_notify(
    NX_IP *ip_ptr,
    VOID (*ip_address_change_notify)(NX_IP *, UINT, UINT, UINT, ULONG *));
```
### <a name="description"></a>Opis

Ta usługa rejestruje procedurę wywołania zwrotnego aplikacji, która NetX Duo w przypadku zmiany adresu IPv6.

Ta usługa jest dostępna, jeśli NetX Duo jest skompilowana, opcja ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY*** zdefiniowana.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **ip_address_change_notify** Funkcja wywołania zwrotnego aplikacji

### <a name="return-values"></a>Wartości zwrócone  

- Pomyślne ustawienie **NX_SUCCESS** (0x00)
- Funkcja powiadamiania o zmianie adresu IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotekę NetX Duo
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- Powiadomienie o zmianie adresu IPv6 **NX_NOT_ENABLED** (0x14) nie jest kompilowane

### <a name="allowed-from"></a>Dozwolone z

Thread

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
VOID ip_address_change_notify(NX_IP *ip_ptr, UINT status,
                              UINT interface_index,
                              UINT address_index,
                              ULONG *ip_address)
{

   /* Do something when ip address changed. */
}

void ip_address_thread_entry(ULONG id)
{

   /* Set the ip address change notify of IP instance. */
   status = nxd_ipv6_address_change_notify (&ip_0, ip_address_change_notify);

/* If status == NX_SUCCESS, the ip address change notify of IP
   instance was successfully set. */
}
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_delete"></a>nxd_ipv6_address_delete
Usuń adres IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_address_delete(
    NX_IP *ip_ptr, 
    UINT address_index);
```
### <a name="description"></a>Opis

Ta usługa usuwa adres IPv6 o określonym indeksie w tabeli adresów IPv6 określonego wystąpienia IP. Nie istnieje odpowiednik NetX.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **address_index** Indeksowanie tabeli adresów IPv6 wystąpienia adresu IP

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie usunięto adres **NX_SUCCESS** (0x00)
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotece NetX Duo
- **NX_NO_INTERFACE_ADDRESS** (0X50) nie można znaleźć odpowiedniego interfejsu wychodzącego
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
NXD_ADDRESS ip_address;
UINT        address_index;

/* Delete the IPv6 address at the specified address table index. */
address_index = 1;
status = nxd_ipv6_address_delete(&ip_0, address_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully deleted. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_get"></a>nxd_ipv6_address_get
Pobieranie adresu IPv6 i prefiksu

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_address_get(
    NX_IP *ip_ptr, 
    UINT address_index, 
    NXD_ADDRESS *ip_address,
    ULONG *prefix_length,
    UINT *interface_index);
```
### <a name="description"></a>Opis

Ta usługa Pobiera adres IPv6 i prefiks o określonym indeksie w tabeli adresów określonego wystąpienia IP. Indeks interfejsu fizycznego, z którym skojarzony jest adres IPv6, jest zwracany na *interface_index* wskaźniku. NetX równoważne usługi są ***nx_ip_address_get** _ i _ *_nx_ip_interface_address_get_* *.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **address_index** Indeksowanie tabeli adresów IP wystąpień
- **IP_address** Wskaźnik na adres, który ma zostać ustawiony
- **PREFIX_LENGTH** Długość prefiksu adresu (Maska podsieci)
- **interface_index** Wskaźnik do indeksu interfejsu

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) protokół IPv6 został pomyślnie włączony
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotekę NetX Duo.
- **NX_NO_INTERFACE_ADDRESS** (0X50) brak adresu interfejsu lub nieprawidłowy address_index
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
NXD_ADDRESS ip_address;
UINT        address_index;
ULONG       prefix_length;
UINT        interface_index;

/* Get the IPv6 address at the specified address table index. If
   found, the address network interface is returned in the
   interface_index input, as well as the address prefix in the
   prefix_length input. */

address_index = 1;
status = nxd_ipv6_address_get(&ip_0, address_index, &ip_address,
                              &prefix_length, &interface_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_set"></a>nxd_ipv6_address_set
Ustawianie adresu IPv6 i prefiksu

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_address_set(
    NX_IP *ip_ptr, 
    UINT interface_index,
    NXD_ADDRESS *ip_address,
    ULONG prefix_length,
    UINT *address_index);
```
### <a name="description"></a>Opis

Ta usługa ustawia podany adres IPv6 i prefiks do określonego wystąpienia IP. Jeśli argument *address_index* nie ma wartości null, zwracany jest indeks tabeli adresów IPv6, w której został wstawiony adres. NetX równoważne usługi są ***nx_ip_address_set** _ i _ *_nx_ip_interface_address_set_* *.

### <a name="parameters"></a>Parametry  

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **interface_index** Indeks do interfejsu, z którym jest skojarzony adres IPv6
- **IP_address** Wskaźnik na adres, który ma zostać ustawiony
- **PREFIX_LENGTH** Długość prefiksu adresu (Maska podsieci)
- **address_index** Wskaźnik do indeksu w tabeli adresów, w której został wstawiony adres

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) protokół IPv6 został pomyślnie włączony
- **NX_NO_MORE_ENTRIES** (0x15) tabela adresów IP jest pełna
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotekę NetX Duo.
- **NX_DUPLICATED_ENTRY** (0x52) podany adres IP jest już używany w tym wystąpieniu adresu IP
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IPv6
- Interfejs **NX_INVALID_INTERFACE** (0x4C) wskazuje nieprawidłowy interfejs sieciowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
NXD_ADDRESS ip_address;
UINT        address_index;
UINT        interface_index;

ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                     IP_ADDRESS(1,2,3,4),
                     0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                     pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* Set the IPv6 address (a global address as indicated by the 64 bit
   prefix) using the IPv6 address just created on the primary device
   (index zero). The index into the address table is returned in
   address_index. */
interface_index = 0;
status = nxd_ipv6_address_set(&ip_0, interface_index, &ip_address,
                              64,&address_index);

/* A status return of NX_SUCCESS indicates that the IPv6 address is
   successfully assigned to the primary interface (interface 0). */
```

### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add
Dodawanie routera IPv6 do tabeli routera domyślnego

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_default_router_add(
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address,
    ULONG router_lifetime,
    UINT index_index);
```
### <a name="description"></a>Opis

Ta usługa dodaje domyślny router IPv6 w określonym interfejsie fizycznym do tabeli routera domyślnego. Równoważna usługa NetX IPv4 jest ***nx_ip_gateway_address_set***.

*router_address* musi wskazywać prawidłowy adres IPv6, a router musi być bezpośrednio dostępny w określonym interfejsie fizycznym.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **router_address** Wskaźnik do domyślnego adresu routera w kolejności bajtów hosta
- **router_lifetime** Domyślny czas trwania routera (w sekundach). Prawidłowe wartości:
    - **0xFFFF:** Bez limitu czasu
    - **0 — 0xFFFE:** Wartość limitu czasu (w sekundach)
- **index_index** Wskaźnik do prawidłowej lokalizacji pamięci dla indeksu indeksu sieci, za pomocą którego można uzyskać dostęp do routera

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0x00) Router domyślny został pomyślnie dodany
- **NX_NO_MORE_ENTRIES** (0X17) nie ma więcej wpisów dostępnych w domyślnej tabeli routerów.
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IPv6
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotekę NetX Duo.
- **NX_INVALID_PARAMETERS** (0x4D) nieprawidłowe dane wejściowe adresu IPv6
- **NX_PTR_ERROR** (0X07) nieprawidłowe wystąpienie adresu IP lub miejsce do magazynowania
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- **NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy indeks interfejsu routera

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* This example adds a default router for the primary interface at
   fe80::1219:B9FF:FE37:ac to the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;

/* Set the router address version to IPv6 */
router_address.nxd_ip_version   = NX_IP_VERSION_V6;

/* Set the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Set IPv6 default router. */
status = nxd_ipv6_default_router_add(ip_ptr, &router_address,
                                     0xFFFF, PRIMARY_INTERFACE);

/* Unless invalid pointer input is detected by the error checking
   Service, status return is always NX_SUCCESS. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete
Usuń Router IPv6 z domyślnej tabeli routera

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_default_router_delete (
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address);
```
### <a name="description"></a>Opis

Ta usługa usuwa Router domyślny IPv6 z tabeli routera domyślnego. Równoważna usługa NetX IPv4 jest ***nx_ip_gateway_address_clear***.

### <a name="restrictions"></a>Ograniczenia

Wystąpienie adresu IP zostało utworzone. *router_address* musi wskazywać prawidłowe informacje.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **router_address** Wskaźnik na adres domyślnej bramy IPv6

### <a name="return-values"></a>Wartości zwrócone 

- Pomyślnie usunięto router **NX_SUCCESS** (0x00)
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotekę NetX Duo.
- **NX_NOT_FOUND** (0x4E) nie można znaleźć wpisu routera
- **NX_PTR_ERROR** (0X07) nieprawidłowe wystąpienie adresu IP lub miejsce do magazynowania
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- **NX_INVALID_PARAMETERS** (0X82) Nieprawidłowa wejściowa niebędąca wskaźnikiem

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/*This example removes a default router:fe80::1219:B9FF:FE37:ac */

NXD_ADDRESS router_address;

/* Set the router_address version to IPv6 */
router_address.nxd_ip_version = NX_IP_VERSION_V6;

/* Program the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Delete the IPv6 default router. */
nxd_ipv6_default_router_delete(ip_ptr, &router_address);
```
### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_clearnx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_getnx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_entry_get"></a>nxd_ipv6_default_router_entry_get
Pobierz domyślny wpis routera

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_default_router_entry_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT entry_index,
    NXD_ADDRESS *router_addr,
    ULONG *router_lifetime,
    ULONG *prefix_length,
    ULONG *configuration_method);
```
### <a name="description"></a>Opis

Ta usługa pobiera wpis routera z domyślnej tabeli routingu IPv6, która jest dołączona do określonego urządzenia sieciowego.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **interface_index** Indeks interfejsu sieciowego
- **entry_index** Indeks wpisu
- **router_addr** Adres IPv6 routera
- **router_lifetime** Wskaźnik do czasu życia routera
- **PREFIX_LENGTH** Wskaźnik do długości prefiksu
- **configuration_method** Wskaźnik do informacji na temat sposobu skonfigurowania wpisu

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0x00) — pomyślne uzyskanie
- Nie znaleziono wpisu routera **NX_NOT_FOUND** (0x4E)
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0
NXD_ADDRESS            router_addr;
ULONG                  router_lifetime;
ULONG                  prefix_length;
ULONG                  configuration_method;

/* Get the router entry of specified interface. */
status = nxd_ipv6_default_router_entry_get (&ip_0,
                                            PRIMARY_INTERFACE,
                                            entry_index,
                                            &router_addr,
                                            &router_lifetime,
                                            &prefix_length,
                                            &configuration_method);

/* If status == NX_SUCCESS, the router entry was successfully
   got. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_get"></a>nxd_ipv6_default_router_get
Pobieranie routera IPv6 z tabeli routera domyślnego

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_default_router_get(
    NX_IP *ip_ptr, 
    UINT interface_index
    NXD_ADDRESS *router_address,
    ULONG *router_lifetime,
    ULONG *prefix_length);
```
### <a name="description"></a>Opis

Ta usługa Pobiera domyślny adres routera IPv6, okres istnienia i długość prefiksu w określonym interfejsie fizycznym z tabeli routera domyślnego. Równoważna usługa NetX IPv4 to ***nx_ip_gateway_address_get *.**

*router_address* musi wskazywać prawidłową strukturę NXD_ADDRESS, dzięki czemu ta usługa może wypełnić adres IPv6 routera domyślnego.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **interface_index** Indeks interfejsu sieciowego, za pomocą którego jest dostęp do routera
- **router_address** Wskaźnik do miejsca do magazynowania dla wartości zwracanej przez domyślny adres routera w kolejności bajtów hosta.
- **router_lifetime** Wskaźnik okresu istnienia routera
- **PREFIX_LENGTH** Wskaźnik na długość prefiksu adresu routera

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0x00) Router domyślny został pomyślnie dodany
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotekę NetX Duo.
- Nie znaleziono domyślnego routera **NX_NOT_FOUND** (0x4E)
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- **NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy indeks interfejsu routera
- **NX_PTR_ERROR** (0X07) nieprawidłowe wystąpienie adresu IP lub miejsce do magazynowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* This example retrieves a default router for the primary device
   from the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;
ULONG       router_lifetime;
ULONG       prefix_length;

/* Get IPv6 default router. */
status = nxd_ipv6_default_router_get(ip_ptr, PRIMARY_INTERFACE,
                                     &router_address,
                                     &router_lifetime,
                                     &prefix_length);

/* If status returns NX_SUCCESS, the router address and related
   information is returned successfully. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_number_of_entries_get"></a>nxd_ipv6_default_router_number_of_entries_get
Pobierz liczbę domyślnych routerów IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_default_router_number_of_entries_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT *num_entries);
```
### <a name="description"></a>Opis

Ta usługa Pobiera liczbę domyślnych routerów IPv6 skonfigurowanych dla danego interfejsu sieciowego.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik bloku kontroli adresów IP
- **interface_index** Indeks interfejsu sieciowego
- **num_entries** Miejsce docelowe dla liczby routerów IPv6 na określonym urządzeniu sieciowym

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0x00) — pomyślne uzyskanie
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotekę NetX Duo.
- Wartość indeksu urządzenia **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowa
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresu IP lub wskaźnik num_entries

### <a name="allowed-from"></a>Dozwolone z

Thread

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0
UINT                   num_entries;

/* Get the router entries of specified interface. */
status = nxd_ipv6_default_router_number_of_entries_get(&ip_0,
                                                       PRIMARY_INTERFACE,
                                                       &num_entries);

/* If status == NX_SUCCESS, the router entries was successfully
   retrieved. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get

## <a name="nxd_ipv6_disable"></a>nxd_ipv6_disable
Wyłącz funkcję IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa wyłącza protokół IPv6 dla określonego wystąpienia IP. Czyści również domyślną tabelę routera, pamięć podręczną i tabelę adresów IPv6, opuszcza wszystkie grupy multiemisji i resetuje zmienne żądania routera. Ta usługa nie działa, jeśli protokół IPv6 nie jest włączony.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik wystąpienia adresu IP

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0x00) — pomyślne wyłączenie
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotekę NetX Duo.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- Moduł IPv6 **NX_NOT_SUPPORT** (0x4B) nie został skompilowany
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Disable IPv6 feature on this IP instance. */
status = nxd_ipv6_disable(&ip_0);

/* If status == NX_SUCCESS, disables IPv6 feature on IP instance.*/
```
### <a name="see-also"></a>Zobacz też 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable
Włącz usługi IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa umożliwia korzystanie z usług IPv6. Po włączeniu usług IPv6 wystąpienie protokołu IP jest przyłączane do grupy multiemisji wszystkie węzły (FF02:: 1). Ta usługa nie ustawia adresu lokalnego ani adresu globalnego linku. Aplikacje powinny używać *nxd_ipv6_address_set* do konfigurowania adresów sieciowych urządzeń. Nie istnieje odpowiednik NetX.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) protokół IPv6 został pomyślnie włączony
- **NX_ALREADY_ENABLED** (0X15) protokół IPv6 jest już włączony
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotekę NetX Duo.
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik adresu IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                      IP_ADDRESS(1,2,3,4),
                      0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                      pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for IPv6 services. */
```
### <a name="see-also"></a>Zobacz też

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_multicast_interface_join"></a>nxd_ipv6_multicast_interface_join
Dołącz do grupy multiemisji IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_multicast_interface_join(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```

### <a name="description"></a>Opis

Ta usługa umożliwia aplikacji dołączenie do określonego adresu multiemisji IPv6 w określonym interfejsie sieciowym. Sterownik linku zostanie powiadomiony o konieczności dodania adresu multiemisji. Ta usługa jest dostępna, jeśli biblioteka NetX Duo została skompilowana z użyciem opcji ***NX_ENABLE_IPV6_MULTICAST*** zdefiniowanej.

### <a name="parameters"></a>Parametry  

- **ip_ptr** Wskaźnik wystąpienia adresu IP
- **group_address** Adres multiemisji IPv6
- **interface_index** Indeks interfejsu sieciowego skojarzonego z grupą multiemisji

### <a name="return-values"></a>Wartości zwrócone  

- **NX_SUCCESS** (0X00) pomyślnie włącza otrzymywanie przy adresie multiemisji IPv6
- **NX_NO_MORE_ENTRIES** (0X17) nie ma więcej wpisów w tabeli multiemisji IPv6.
- **NX_OVERFLOW** (0X03) nie ma więcej dostępnych adresów grupy w sterowniku urządzenia
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) lub funkcja multiemisji IPv6 nie jest wbudowana w bibliotekę NetX Duo
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IPv6
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0

/* Join multicast group on this IP instance. */
status = nxd_ipv6_multicast_interface_join(&ip_0,
                                           &group_address,
                                           PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, interface of index on IP instance
   has joined the multicast group. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_leave

## <a name="nxd_ipv6_multicast_interface_leave"></a>nxd_ipv6_multicast_interface_leave
Opuszczanie grupy multiemisji IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_multicast_interface_leave(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```
### <a name="description"></a>Opis

Ta usługa usuwa określony adres multiemisji IPv6 z określonego urządzenia sieciowego. Sterownik łącza jest również powiadamiany o usunięciu adresu multiemisji IPv6. Ta usługa jest dostępna, jeśli biblioteka NetX Duo została skompilowana z użyciem opcji ***NX_ENABLE_IPV6_MULTICAST*** zdefiniowanej.

### <a name="parameters"></a>Parametry  

- **ip_ptr** Wskaźnik wystąpienia adresu IP
- **group_address** Adres multiemisji IPv6
- **interface_index** Indeks interfejsu sieciowego skojarzonego z grupą

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0X00) pomyślne opuszczenie multiemisji
- Nie znaleziono wpisu **NX_ENTRY_NOT_FOUND** (0x16)
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) lub funkcja multiemisji IPv6 nie jest wbudowana w bibliotekę NetX Duo
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IPv6
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0

/* Leave multicast address on this IP instance. */
status = nxd_ipv6_multicast_interface_leave(&ip_0,
                                            &group_address,
                                            primary_interface);

/* If status == NX_SUCCESS, interface of index on IP instance
   has left the multicast group. */
```
### <a name="see-also"></a>Zobacz też

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join

## <a name="nxd_ipv6_stateless_address_autoconfig_disable"></a>nxd_ipv6_stateless_address_autoconfig_disable
Wyłącz autokonfigurację adresów bezstanowych

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_stateless_address_autoconfig_disable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>Opis

Ta usługa wyłącza funkcję automatycznej konfiguracji adresów IPv6 na określonym urządzeniu sieciowym. Nie ma żadnego efektu, jeśli adres IPv6 został skonfigurowany.

Ta usługa jest dostępna, jeśli biblioteka NetX Duo została skompilowana z użyciem opcji ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL*** zdefiniowanej.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik wystąpienia adresu IP
- **interface_index** Indeks interfejsu sieciowego, który ma być wyłączony Autokonfiguracja adresu IPv6.

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0X00) pomyślnie wyłącza funkcję autokonfigurowania adresów bezstanowych.
- Funkcja **NX_NOT_SUPPORTED** (0X4B) IPv6 lub funkcja kontroli konfiguracji bezstanowego adresu IPv6 nie jest wbudowana w bibliotekę NetX Duo
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE 0

/* Disable stateless address auto configuration on this IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_disable(&ip_0,
                                                       PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, disables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>Zobacz też 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_stateless_address_autoconfig_enable"></a>nxd_ipv6_stateless_address_autoconfig_enable
Włącz bezstanową autokonfigurację adresu

### <a name="prototype"></a>Prototype  

```c
UINT nxd_ipv6_stateless_address_autoconfig_enable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>Opis

Ta usługa włącza funkcję automatycznej konfiguracji adresów IPv6 na określonym urządzeniu sieciowym.

Ta usługa jest dostępna, jeśli biblioteka NetX Duo została skompilowana z użyciem opcji ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL*** zdefiniowanej.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik wystąpienia adresu IP
- **interface_index** Indeks interfejsu sieciowego, który powinien być włączony Autokonfiguracja adresów IPv6.

### <a name="return-values"></a>Wartości zwrócone 

- **NX_SUCCESS** (0X00) pomyślnie włącza funkcję autokonfiguracji adresu bezstanowego.
- **NX_ALREADY_ENABLED** (0x15) jest już włączona
- Funkcja **NX_NOT_SUPPORTED** (0X4B) IPv6 lub funkcja kontroli konfiguracji bezstanowego adresu IPv6 nie jest wbudowana w bibliotekę NetX Duo
- Indeks interfejsu **NX_INVALID_INTERFACE** (0x4C) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik bloku kontroli adresów IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
#define PRIMARY_INTERFACE

/* Enable stateless address auto configuration on this
   IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_enable(&ip_0,
                                                      PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, enables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>Zobacz też 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable

## <a name="nxd_nd_cache_entry_delete"></a>nxd_nd_cache_entry_delete
Usuwanie wpisu adresu IPv6 w pamięci podręcznej sąsiadów

### <a name="prototype"></a>Prototype  

```c
UINT nxd_nd_cache_entry_delete(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>Opis

Ta usługa usuwa wpis pamięci podręcznej odnajdywania sąsiadów IPv6 dla podanego adresu IP. Równoważna funkcja NetX IPv4 jest ***nx_arp_static_entry_delete***.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **IP_address** Wskaźnik do adresu IPv6 do usunięcia w kolejności bajtów hosta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie usunął adres
- Nie znaleziono adresu **NX_ENTRY_NOT_FOUND** (0x16) w pamięci podręcznej sąsiadów IPv6
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotece NetX Duo
- **NX_PTR_ERROR** (0X07) nieprawidłowe wystąpienie adresu IP lub miejsce do magazynowania
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* This example deletes an entry from the neighbor cache table. */

NXD_ADDRESS ip_address;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Delete an entry in the neighbor cache table with the specified IPv6
   address and hardware address. */
status = nxd_nd_cache_entry_delete(&ip_0,
                                   &ip_address.nxd_ip_address.v6[0]);

/* If status == NX_SUCCESS, the entry was deleted from the neighbor cache
   table. */
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set
Dodaj mapowanie adresów IPv6/MAC do pamięci podręcznej sąsiadów

### <a name="prototype"></a>Prototype  

```c
UINT nxd_nd_cache_entry_set(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *dest_ip,
    UINT interface_index, 
    char *mac);
```

### <a name="description"></a>Opis

Ta usługa dodaje wpis do pamięci podręcznej odnajdywania sąsiadów dla określonego adresu IP *IP_address* mapowany na sprzętowy adres MAC w określonym indeksie interfejsu sieciowego (interface_index). Równoważna usługa NetX IPv4 jest ***nx_arp_static_entry_create***.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **dest_ip** Wskaźnik do wystąpienia adresu IPv6
- **interface_index** Indeks określający fizyczny interfejs sieciowy, do którego można skontaktować się z docelowym adresem IPv6 
- komputer **Mac** Wskaźnik na adres sprzętowy.

### <a name="return-values"></a>Wartości zwrócone 

- Pomyślnie dodano wpis **NX_SUCCESS** (0x00)
- **NX_NOT_SUCCESSFUL** (0X43) Nieprawidłowa pamięć podręczna lub brak dostępnych wpisów pamięci podręcznej sąsiadów
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotece NetX Duo
- **NX_PTR_ERROR** (0X07) nieprawidłowe wystąpienie adresu IP lub miejsce do magazynowania
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- **NX_INVALID_INTERFACE** (0X4C) Nieprawidłowa wartość indeksu interfejsu.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* This example adds an entry on the primary network interface to
   the neighbor cache table. */

#define PRIMARY_INTEFACE 0

NXD_ADDRESS ip_address;
UCHAR hw_address[6] = {0x0, 0xcf,0x01,0x02, 0x03, 0x04};
CHAR  *mac;

mac = (CHAR *)&hw_address[0];

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Create an entry in the neighbor cache table with the specified
   IPv6 address and hardware address. */
status = nxd_nd_cache_entry_set(&ip_0,
                                &ip_address.nxd_ip_address.v6[0],
                                PRIMARY_INTERFACE, mac);

/* If status == NX_SUCCESS, the entry was added to the neighbor
   cache table. */
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_hardware_address_find"></a>nxd_nd_cache_hardware_address_find
Lokalizowanie adresu sprzętowego dla adresu IPv6

### <a name="prototype"></a>Prototype  

```c
UINT nxd_nd_cache_hardware_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG *physical_msw,
    ULONG *physical_lsw
    UINT *interface_index);
```
### <a name="description"></a>Opis

Ta usługa próbuje znaleźć fizyczny adres sprzętowy w pamięci podręcznej odnajdowania sąsiadów IPv6, która jest skojarzona z podanym adresem IPv6. Indeks interfejsu sieciowego, za pomocą którego można osiągnąć sąsiada, jest również zwracany w parametrze *interface_index.* Równoważna usługa NetX IPv4 jest ***nx_arp_hardware_address_find***.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **IP_address** Wskaźnik na adres IP do znalezienia, kolejność bajtów hosta
- **physical_msw** Wskaźnik do pierwszych 16 bitów (47-32) adresu fizycznego w kolejności bajtów hosta 
- **physical_lsw** Wskaźnik do dolnej 32 bitów (31-0) adresu fizycznego w kolejności bajtów hosta
- **interface_index** Wskaźnik do prawidłowej lokalizacji pamięci dla indeksu interfejsu określającego urządzenie sieciowe, na którym można uzyskać dostęp do adresu IPv6.

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie odnalazł adres
- Mapowanie **NX_ENTRY_NOT_FOUND** (0x16) nie znajduje się w pamięci podręcznej sąsiadów
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotece NetX Duo
- **NX_INVALID_PARAMETERS** (0x4D) podany adres IP nie jest w wersji 6.
- **NX_PTR_ERROR** (0X07) nieprawidłowe wystąpienie adresu IP lub miejsce do magazynowania
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* This example inputs an IP address on the primary network in order
   to obtain the hardware address it is mapped to in the neighbor
   cache able. */

NXD_ADDRESS  ip_address;
ULONG physical_msw, physical_lsw;
UINT  interface_index;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Obtain the hardware address mapped to the supplied global IPv6
   address. */
status = nxd_nd_cache_hardware_address_find(&ip_0, &ip_address,
                                            &physical_msw,
                                            &physical_lsw
                                            &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the hardware address returned in
   variables physical_msw and physical_lsw, the index of the network
   interface through which the neighbor can be reached is stored in
   interface_index. */
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate
Unieważnianie pamięci podręcznej odnajdywania sąsiadów

### <a name="prototype"></a>Prototype  

```c
UINT nxd_nd_cache_invalidate(NX_IP *ip_ptr);
```
### <a name="description"></a>Opis

Ta usługa unieważnia całą pamięć podręczną odnajdywania sąsiadów IPv6. Tę usługę można wywołać przed włączeniem protokołu ICMPv6 lub po nim. Ta usługa nie ma zastosowania do łączności IPv4, więc nie istnieje NetX równoważna usługa.

### <a name="parameters"></a>Parametry

- **ip_ptr** Wskaźnik do wystąpienia adresu IP

### <a name="return-values"></a>Wartości zwrócone

- Pamięć podręczna **NX_SUCCESS** (0x00) została pomyślnie unieważniona
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotece NetX Duo
- **NX_PTR_ERROR** (0X07) nieprawidłowe wystąpienie adresu IP
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* This example invalidates the host neighbor cache table. */

/* Invalidate the cache table bound to the IP instance. */
status = nxd_nd_cache_invalidate (&ip_0);

/* If status == NX_SUCCESS, all entries in the neighbor cache table
   are invalidated. */
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find
Pobieranie adresu IPv6 dla adresu fizycznego

### <a name="prototype"></a>Prototype  

```c
UINT nxd_nd_cache_ip_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT *interface_index);
```
### <a name="description"></a>Opis

Ta usługa próbuje znaleźć adres IPv6 w pamięci podręcznej odnajdowania sąsiadów IPv6, która jest skojarzona z podanym adresem fizycznym. Zwracany jest również indeks interfejsu sieciowego, za pomocą którego można osiągnąć sąsiada. Równoważna usługa NetX IPv4 jest ***nx_arp_ip_address_find***.

### <a name="parameters"></a>Parametry 

- **ip_ptr** Wskaźnik do wcześniej utworzonego wystąpienia adresu IP
- **IP_address** Wskaźnik do prawidłowej struktury NXD_ADDRESS
- **physical_msw** Pierwsze 16 bitów (47-32) adresów fizycznych do znalezienia, kolejność bajtów hosta
- **physical_lsw** Niższa 32 bitów (31-0) adresu fizycznego do znalezienia, kolejność bajtów hosta
- **interface_index** Wskaźnik do indeksu urządzeń sieciowych, za pomocą którego można skontaktować się z adresem IPv6

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślnie odnalazł adres
- Nie znaleziono adresu fizycznego **NX_ENTRY_NOT_FOUND** (0x16) w pamięci podręcznej sąsiadów
- Funkcja IPv6 **NX_NOT_SUPPORTED** (0x4B) nie jest wbudowana w bibliotece NetX Duo
- **NX_PTR_ERROR** (0X07) nieprawidłowe wystąpienie adresu IP lub miejsce do magazynowania
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi 
- Adres MAC **NX_INVALID_PARAMETERS** (0x4D) to zero.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* This example inputs a hardware address to search on for the
   matching IPv6 global address in the neighbor cache table. */

NXD_ADDRESS ip_address;
ULONG physical_msw = 0xcf;
ULONG physical_lsw = 0x01020304;
UINT  interface_index;

/* Obtain the IPv6 address mapped to the supplied hardware
   Address on the primary device. */
status = nxd_nd_cache_ip_address_find(&ip_0, &ip_address,
                                      physical_msw, physical_lsw,
                                      &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the global IPv6 address returned in
   variable ip_address. */
```
### <a name="see-also"></a>Zobacz też

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate

## <a name="nxd_tcp_client_socket_connect"></a>nxd_tcp_client_socket_connect
Nawiązywanie połączenia TCP

### <a name="prototype"></a>Prototype  

```c
UINT nxd_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr
    NXD_ADDRESSS *server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa nawiązuje połączenie TCP przy użyciu wcześniej utworzonego gniazda klienta TCP na port określonego serwera. Ta usługa działa w sieciach IPv4 lub IPv6. Prawidłowe porty serwera TCP mieszczą się w zakresie od 0 do 0xFFFF. NetX Duo określa odpowiedni interfejs fizyczny na podstawie adresu IP serwera. Odpowiednik NetX IPv4 jest ***nx_tcp_client_socket_connect***.

Gniazdo musi być powiązane z portem lokalnym.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego gniazda TCP
- **server_IP** Wskaźnik do adresu docelowego IPv4 lub IPv6 w kolejności bajtów hosta
- **SERVER_PORT** Numer portu serwera, z którym ma zostać nawiązane połączenie (od 1 do 0xFFFF) w kolejności bajtów hosta
- **WAIT_OPTION** Opcja oczekiwania podczas ustanawiania połączenia. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xffffffff)
    - **wartość limitu czasu w taktach** (0X00000001 przez 0xFFFFFFFE)

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne połączenie gniazda
- Zażądane zawieszenie **NX_WAIT_ABORTED** (0x1A) zostało przerwane przez wywołanie tx_thread_wait_abort
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IPv4 lub IPv6 serwera
- Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane
- Gniazdo **NX_NOT_CLOSED** (0x35) nie jest w stanie zamkniętym
- **NX_IN_PROGRESS** (0X37) nie określono oczekiwania, próba połączenia jest w toku
- **NX_INVALID_INTERFACE** (0X4C) Nieprawidłowy indeks interfejsu.
- **NX_NO_INTERFACE_ADDRESS** (0x50) interfejs sieciowy nie ma prawidłowego adresu IPv6
- **NX_NOT_ENABLED** (0X14) TCP nie jest włączony
- **NX_INVALID_PORT** (0X46) nieprawidłowy port
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- Połączenie **NX_NOT_CONNECTED** (0x38) nie powiedzie się.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
NXD_ADDRESS peer_ip_address;
ULONG       peer_port;

/* Set Peer IPv6 address */
peer_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
peer_ip_address.nxd_ip_address.v6[0] = 0x20010000;
peer_ip_address.nxd_ip_address.v6[1] = 0;
peer_ip_address.nxd_ip_address.v6[2] = 0;
peer_ip_address.nxd_ip_address.v6[3] = 0x101;

/* Set peer port number */
peer_port = 2563;

/* Connect to the peer */
status = nxd_tcp_client_socket_connect(socket_ptr,
                                       &peer_ip_address,
                                       peer_port, NX_WAIT_FOREVER);
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_socket_peer_info_get

## <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get
Pobiera adres IP i numer portu równorzędnego gniazda TCP

### <a name="prototype"></a>Prototype  

```c
UINT nxd_tcp_socket_peer_info_get
    (NX_TCP_SOCKET *socket_ptr,
    NXD_ADDRESS *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o adresie IP i porcie elementu równorzędnego dla połączonego gniazda TCP za pośrednictwem sieci IPv4 lub IPv6. Równoważna usługa NetX IPv4 jest ***nx_tcp_socket_peer_info_get***.

Należy pamiętać, że *socket_ptr* musi wskazywać gniazdo TCP, które jest już w stanie połączonym.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do gniazda TCP połączonego z hostem równorzędnym
- **peer_ip_address** Wskaźnik na adres IPv4 lub IPv6. Zwrócony adres IP znajduje się w kolejności bajtów hosta.
- **peer_port** Wskaźnik do numeru portu elementu równorzędnego. Zwrócony numer portu znajduje się w kolejności bajtów hosta.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie pobrano informacje o gnieździe **NX_SUCCESS** (0x00)
- Gniazdo **NX_NOT_CONNECTED** (0x38) nie jest połączone z elementem równorzędnym
- **NX_NOT_ENABLED** (0X14) TCP nie jest włączony
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
NXD_ADDRESS  peer_ip_address;
ULONG        peer_port;

/* Get TCP socket information. */
status = nxd_tcp_socket_peer_info_get(socket_ptr, &peer_ip_address,
                                      &peer_port);

/* If status == NX_SUCCESS, the service returns valid peer info: */
if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V4)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v4 */

if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V6)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v6 */
```
### <a name="see-also"></a>Zobacz też

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect

## <a name="nxd_udp_packet_info_extract"></a>nxd_udp_packet_info_extract
Wyodrębnij parametry sieci z pakietu UDP

### <a name="prototype"></a>Prototype  

```c
UINT nxd_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>Opis

Ta usługa wyodrębnia parametry sieci z pakietu otrzymanego w sieciach IPv4 lub IPv6. NetX równoważna usługa jest ***nx_udp_packet_info_extract.***

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do pakietu.
- **IP_address** Wskaźnik na adres IP nadawcy.
- **Protokół** Wskaźnik do protokołu do zwrócenia.
- **port** Wskaźnik na numer portu nadawcy.
- **interface_index** Wskaźnik do indeksu interfejsu sieciowego, z którego otrzymuje się ten pakiet

### <a name="return-values"></a>Wartości zwrócone 

- Pomyślnie wyodrębniono dane interfejsu pakietu **NX_SUCCESS** (0x00).
- Pakiet **NX_INVALID_PACKET** (0x12) nie jest IPv4 ani IPv6.
- **NX_PTR_ERROR** (0X07) nieprawidłowe dane wejściowe wskaźnika
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Extract network data from UDP packet interface.*/
status = nxd_udp_packet_info_extract(packet_ptr, &ip_address,
                                    &protocol, &port,
                                    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved.*/
```
### <a name="see-also"></a>Zobacz też 

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send
Wysyłanie datagramu UDP

### <a name="prototype"></a>Prototype  

```c
UINT nxd_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port);
```
### <a name="description"></a>Opis

Ta usługa wysyła datagram UDP przy użyciu wcześniej utworzonego i powiązanego gniazda UDP dla sieci IPv4 lub IPv6. NetX Duo znajduje odpowiedni lokalny adres IP jako adres źródłowy na podstawie docelowego adresu IP. Aby określić konkretny interfejs i źródłowy adres IP, aplikacja powinna używać usługi ***nxd_udp_socket_source_send*** .

Należy zauważyć, że ta usługa wraca natychmiast niezależnie od tego, czy datagram UDP został pomyślnie wysłany. Odpowiednik usługi NetX (IPv4) jest ***nx_udp_socket_send***.

Gniazdo musi być powiązane z portem lokalnym.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP
- **packet_ptr** Wskaźnik pakietu datagramu UDP
- **IP_address** Wskaźnik do docelowego adresu IPv4 lub IPv6
- **port** Prawidłowy numer portu docelowego z zakresu od 1 do 0xFFFF) w kolejności bajtów hosta

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie gniazda UDP
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IPv4 lub IPv6 serwera
- Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane z żadnym portem
- **NX_NO_INTERFACE_ADDRESS** (0X50) nie można znaleźć odpowiedniego interfejsu wychodzącego.
- **NX_UNDERFLOW** (0X02) nie ma wystarczającej ilości miejsca na nagłówek UDP w pakiecie
- Wskaźnik dołączania pakietu **NX_OVERFLOW** (0x03) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda, wskaźnik adresu lub wskaźnik pakietu.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- Nie włączono protokołu UDP **NX_NOT_ENABLED** (0x14)
- Numer portu **NX_INVALID_PORT** (0x46) nie należy do prawidłowego zakresu

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
NXD_ADDRESS ip_address, server_address;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the
   IPv6 address just created on the primary device (index 0). We
   don’t need the index into the address table, so the last argument
   is set to null. */

interface_index = 0;
status = nxd_ipv6_address_set(&client_ip, interface_index,
                              &ip_address, 64, NX_NULL);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_send(&client_socket, packet_ptr,
                             &server_address, 12);

/* If status == NX_SUCCESS, the UDP host successfully transmitted
   the packet out the UDP socket to the server. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_source_send"></a>nxd_udp_socket_source_send
Wysyłanie datagramu UDP

### <a name="prototype"></a>Prototype  

```c
UINT nxd_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port, 
    UINT address_index);
```
### <a name="description"></a>Opis

Ta usługa wysyła datagram UDP przy użyciu wcześniej utworzonego i powiązanego gniazda UDP dla sieci IPv4 lub IPv6. Parametr *address_index* Określa źródłowy adres IP, który ma być używany dla pakietu wychodzącego. Należy zauważyć, że funkcja zwraca natychmiast bez względu na to, czy datagram UDP został pomyślnie wysłany.

Gniazdo musi być powiązane z portem lokalnym.

Odpowiednik usługi NetX (IPv4) jest ***nx_udp_socket_source_send***.

### <a name="parameters"></a>Parametry

- **socket_ptr** Wskaźnik do wcześniej utworzonego wystąpienia gniazda UDP
- **packet_ptr** Wskaźnik pakietu datagramu UDP
- **IP_address** Wskaźnik do docelowego portu adresów IPv4 lub IPv6 prawidłowy numer portu docelowego z zakresu od 1 do 0xFFFF) w kolejności bajtów hosta
- **address_index** Indeks określający adres źródłowy do użycia w pakiecie

### <a name="return-values"></a>Wartości zwrócone

- **NX_SUCCESS** (0X00) pomyślne wysłanie gniazda UDP
- **NX_IP_ADDRESS_ERROR** (0X21) nieprawidłowy adres IPv4 lub IPv6 serwera
- Gniazdo **NX_NOT_BOUND** (0x24) nie jest powiązane z żadnym portem
- **NX_NO_INTERFACE_ADDRESS** (0X50) nie można znaleźć odpowiedniego interfejsu wychodzącego.
- **NX_NOT_FOUND** (0X4E) nie można znaleźć odpowiedniego interfejsu
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda, adresu lub wskaźnika pakietu.
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi
- Nie włączono protokołu UDP **NX_NOT_ENABLED** (0x14)
- Numer portu **NX_INVALID_PORT** (0x46) nie należy do prawidłowego zakresu.
- **NX_INVALID_INTERFACE** (0X4C) określony interfejs sieciowy jest prawidłowy
- **NX_UNDERFLOW** (0X02) nie ma wystarczającej ilości miejsca na nagłówek UDP w pakiecie
- Wskaźnik dołączania pakietu **NX_OVERFLOW** (0x03) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
NXD_ADDRESS ip_address, server_address;
UINT address_index;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the IPv6
   address just created on the primary device (index 0). The address index
   is needed for nxd_udp_socket_source_send. */

status = nxd_ipv6_address_set(&client_ip, 0,
                              &ip_address, 64, &address_index);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_source_send(&client_socket, packet_ptr,
                                    &server_address, 12, address_index);

/* If status == NX_SUCCESS, the UDP host successfully transmitted the
   packet out the UDP socket to the server. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_source_extract

## <a name="nxd_udp_source_extract"></a>nxd_udp_source_extract
Pobierz informacje źródłowe pakietu UPD

### <a name="prototype"></a>Prototype  

```c
UINT nxd_udp_source_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address, 
    UINT *port);
```
### <a name="description"></a>Opis

Ta usługa wyodrębnia źródłowy adres IP i numer portu z pakietu UDP otrzymanego za pośrednictwem gniazda UDP hosta. Odpowiednik NetX (IPv4) jest ***nx_udp_source_extract***.

### <a name="parameters"></a>Parametry

- **packet_ptr** Wskaźnik do odebranego pakietu UDP
- **IP_address** Wskaźnik do NXD_ADDRESS struktury do przechowywania źródłowego adresu IP pakietu
- **port** Wskaźnik do numeru portu gniazda UDP

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne wyodrębnienie źródła **NX_SUCCESS** (0x00)
- Pakiet **NX_INVALID_PACKET** (0x12) jest nieprawidłowy
- **NX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik gniazda
- **NX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej usługi

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
NXD_ADDRESS ip_address;
UINT         port;

/* Create the UDP socket client_socket and
   allocate the packet pointed to by packet_ptr (not shown). */

/* Extract the IP address and port of the packet received on the UDP
   socket specified in the packet interface. */
status = nxd_udp_source_extract(&packet_ptr, &ip_address, &port);

/* If status == NX_SUCCESS, the source IP address and port of the
   packet received on the UDP socket was successfully extracted. */
```
### <a name="see-also"></a>Zobacz też

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send