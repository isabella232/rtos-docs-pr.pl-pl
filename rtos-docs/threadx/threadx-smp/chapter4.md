---
title: Rozdział 4 — Opis usług SMP usługi Azure RTO ThreadX
description: Ten rozdział zawiera opis wszystkich usług SMP usługi Azure RTO ThreadX w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4432001b773b4ef4f99b1b34193e90863966aad4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823928"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-smp-services"></a>Rozdział 4 — Opis usług SMP usługi Azure RTO ThreadX

Ten rozdział zawiera opis wszystkich usług SMP usługi Azure RTO ThreadX w porządku alfabetycznym. Ich nazwy są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem. W sekcji "wartości zwracane" w następujących opisach wartości **pogrubienia** nie mają wpływać na **TX_DISABLE_ERROR_CHECKING** Definiowanie używane do wyłączania sprawdzania błędów interfejsu API; podczas gdy wartości wyświetlane w trybie niepogrubionym są całkowicie wyłączone. Ponadto słowo "**Yes**" wymienione w nagłówku "**możliwe** przeprowadzenie" wskazuje, że wywołanie usługi może wznowić wątek o wyższym priorytecie, w rezultacie przeszedł wątek wywołujący.

- **tx_block_allocate**: *przydzielanie bloku o stałym rozmiarze pamięci* 
- **tx_block_pool_create**: *Utwórz pulę bloków pamięci o stałym rozmiarze* 
- **tx_block_pool_delete**: *Usuwanie puli bloków pamięci* 
- **tx_block_pool_info_get**: *pobieranie informacji o puli blokowej* 
- **tx_block_pool_performance_info_get**: *Uzyskiwanie informacji o wydajności puli bloku* 
- **tx_block_pool_performance_system_info_get**: *Uzyskaj informacje o wydajności systemu puli blokowej* 
- **tx_block_pool_prioritize**: *określanie priorytetów listy zawieszania puli bloków* 
- **tx_block_release**: *Zwolnij blok pamięci o stałym rozmiarze*
- **tx_byte_allocate**: *Przydziel bajty pamięci* 
- **tx_byte_pool_create**: *Utwórz pulę pamięci bajtów* 
- **tx_byte_pool_delete**: *Usuwanie puli bajtów pamięci* 
- **tx_byte_pool_info_get**: *pobieranie informacji o puli bajtów* 
- **tx_byte_pool_performance_info_get**: *pobieranie informacji o wydajności puli bajtów* 
- **tx_byte_pool_performance_system_info_get**: *pobieranie informacji o wydajności systemu puli bajtów* 
- **tx_byte_pool_prioritize**: *priorytetyzacja listy zawieszania puli bajtów* 
- **tx_byte_release**: *wydawanie bajtów z powrotem do puli pamięci* 
- **tx_event_flags_create**: *Utwórz grupę flag zdarzeń* 
- **tx_event_flags_delete**: *Usuwanie grupy flag zdarzeń* 
- **tx_event_flags_get**: *Pobierz flagi zdarzeń z grupy flag zdarzeń* 
- **tx_event_flags_info_get**: *Pobierz informacje o grupie flag zdarzeń* 
- **tx_event_flags_performance_info_get**: *Uzyskiwanie informacji o wydajności grupy flag zdarzeń* 
- **tx_event_flags_performance_system_info_get**: *pobieranie informacji o systemie wydajności* 
- **tx_event_flags_set**: *Ustaw flagi zdarzeń w grupie flag zdarzeń* 
- **tx_event_flags_set_notify**: *Powiadamiaj aplikację, gdy są ustawione flagi zdarzeń*
- **tx_interrupt_control**: *włączać i wyłączać przerwania* 
- **tx_mutex_create**: *Utwórz element mutex wzajemnego wykluczania* 
- **tx_mutex_delete**: *usuwanie obiektu mutex wzajemnego wykluczania* 
- **tx_mutex_get**: *Uzyskaj własność obiektu mutex* 
- **tx_mutex_info_get**: *Pobierz informacje o muteksie* 
- **tx_mutex_performance_info_get**: *pobieranie informacji o wydajności muteksu* 
- **tx_mutex_performance_system_info_get**: *pobieranie informacji o wydajności systemu muteksu* 
- **tx_mutex_prioritize**: *określanie priorytetów listy zawieszeń muteksu* 
- **tx_mutex_put**: *Zwolnij własność elementu mutex* 
- **tx_queue_create**: *Tworzenie kolejki komunikatów* 
- **tx_queue_delete**: *usuwanie kolejki komunikatów* 
- **tx_queue_flush**: *puste wiadomości w kolejce komunikatów* 
- **tx_queue_front_send**: *Wyślij komunikat z przodu kolejki* 
- **tx_queue_info_get**: *pobieranie informacji o kolejce* 
- **tx_queue_performance_info_get**: *Uzyskiwanie informacji o wydajności kolejki* 
- **tx_queue_performance_system_info_get**: *pobieranie informacji o wydajności systemu kolejkowania*
- **tx_queue_prioritize**: *priorytetyzacja listy zawieszania kolejki* 
- **tx_queue_receive**: *Pobierz komunikat z kolejki komunikatów* 
- **tx_queue_send**: *Wyślij komunikat do kolejki komunikatów* 
- **tx_queue_send_notify**: *Powiadamiaj aplikację, gdy wiadomość jest wysyłana do kolejki* 
- **tx_semaphore_ceiling_put**: *Umieść wystąpienie w zliczaniu semafora z pułapem* 
- **tx_semaphore_create**: *Tworzenie semafora zliczania* 
- **tx_semaphore_delete**: *usuwanie semafora zliczania* 
- **tx_semaphore_get**: *Pobieranie wystąpienia z zliczania semafora* 
- **tx_semaphore_info_get**: *pobieranie informacji na temat semafora* 
- **tx_semaphore_performance_info_get**: *Uzyskiwanie informacji o wydajności semaforów* 
- **tx_semaphore_performance_system_info_get**: *Uzyskiwanie informacji o wydajności systemu semaforów* 
- **tx_semaphore_prioritize**: *określanie priorytetów listy zawieszania semafora* 
- **tx_semaphore_put**: *Umieść wystąpienie w zliczaniu semafora* 
- **tx_semaphore_put_notify**: *Powiadamiaj aplikację, gdy zostanie umieszczony semafor* 
- **tx_thread_create**: *Utwórz wątek aplikacji* 
- **tx_thread_delete**: *usuwanie wątku aplikacji*
- **tx_thread_entry_exit_notify**: *Powiadamiaj aplikację przy wejściu i wyjściu wątku* 
- **tx_thread_identify**: *Pobiera wskaźnik do aktualnie wykonywanego wątku* 
- **tx_thread_info_get**: *pobieranie informacji o wątku* 
- **tx_thread_performance_info_get**: *Uzyskiwanie informacji o wydajności wątków* 
- **tx_thread_performance_system_info_get**: *pobieranie informacji o wydajności systemu wątków* 
- **tx_thread_preemption_change**: zmiana przekroczenia *— próg wątku aplikacji* 
- **tx_thread_priority_change**: *Zmień priorytet wątku aplikacji* 
- **tx_thread_relinquish**: *zwalnianie kontroli do innych wątków aplikacji* 
- **tx_thread_reset**: *Resetowanie wątku* 
- **tx_thread_resume**: *Wznów wątek zawieszonej aplikacji* 
- **tx_thread_sleep**: *Zawieś bieżący wątek dla określonego czasu* 
- **tx_thread_smp_core_exclude**: *wykluczanie wykonywania wątku na zestawie rdzeni* 
- **tx_thread_smp_core_exclude_get**: *Pobiera bieżące wykluczenie rdzenia wątku* 
- **tx_thread_smp_core_get**: *Pobierz aktualnie wykonywany rdzeń elementu wywołującego* 
- **tx_thread_stack_error_notify**: *Rejestrowanie wywołania zwrotnego powiadomień o błędzie stosu wątku* 
- **tx_thread_suspend**: *wstrzymywanie wątku aplikacji*
- **tx_thread_terminate**: *przerywa wątek aplikacji* 
- **tx_thread_time_slice_change**: *zmienia czas wycinka wątku aplikacji* 
- **tx_thread_wait_abort**: *Przerwij zawieszenie określonego wątku* 
- **tx_time_get**: *Pobiera bieżący czas* 
- **tx_time_set**: *ustawia bieżącą godzinę* 
- **tx_timer_activate**: *Aktywuj czasomierz aplikacji* 
- **tx_timer_change**: *Zmień czasomierz aplikacji* 
- **tx_timer_create**: *Utwórz czasomierz aplikacji* 
- **tx_timer_deactivate**: *Dezaktywuj czasomierz aplikacji* 
- **tx_timer_delete**: *usuwanie czasomierza aplikacji* 
- **tx_timer_info_get**: *pobieranie informacji o czasomierzu aplikacji* 
- **tx_timer_performance_info_get**: *Uzyskiwanie informacji o wydajności czasomierza* 
- **tx_timer_performance_system_info_get**: *Uzyskiwanie informacji o wydajności systemu czasomierza* 
- **tx_timer_smp_core_exclude**: *wykluczanie wykonywania czasomierza na zestawie rdzeni* 
- **tx_timer_smp_core_exclude_get**: *Pobiera bieżące wykluczenie rdzenia czasomierza*

## <a name="tx_block_allocate"></a>tx_block_allocate
Przydzielanie bloku o ustalonym rozmiarze pamięci

### <a name="prototype"></a>Prototype

```C
UINT tx_block_allocate(TX_BLOCK_POOL *pool_ptr, VOID **block_ptr,
                          ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa przydziela blok pamięci o stałym rozmiarze z określonej puli pamięci. Rzeczywisty rozmiar bloku pamięci jest określany podczas tworzenia puli pamięci.

> [!WARNING]
> Ważne jest, aby upewnić się, że kod aplikacji nie zapisuje poza przydzielonym blokiem pamięci. W takim przypadku uszkodzenie występuje w sąsiednim (zazwyczaj kolejnym) bloku pamięci. Wyniki są nieprzewidywalne i często są krytyczne!

### <a name="parameters"></a>Parametry

- **pool_ptr**: wskaźnik do wcześniej utworzonej puli bloków pamięci.
- **block_ptr**: wskaźnik do docelowego wskaźnika bloku. Po pomyślnym przydzieleniu adres przydzielonego bloku pamięci jest umieszczany w miejscu, w którym wskazuje ten parametr.
- **WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli nie ma dostępnych bloków pamięci. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xffffffff)
    - wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)  
    
    Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się pomyślnie, czy nie. Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu udostępnienia bloku pamięci.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na blok pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna alokacja bloku pamięci.
- **TX_DELETED**: (0x01) Pula bloków pamięci została usunięta podczas wstrzymania wątku.
- **TX_NO_MEMORY**: usługa (0x10) nie może przydzielić bloku pamięci w określonym czasie, aby oczekiwania.
- Zawieszanie **TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, CZASOMIERZ lub ISR.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do wskaźnika docelowego.
- TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```c
TX_BLOCK_POOL   my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a memory block from my_pool. Assume that the
   pool has already been created with a call to
   tx_block_pool_create. */
status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
                               TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated block of memory. */
```

### <a name="see-also"></a>Zobacz też

- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_create"></a>tx_block_pool_create
Utwórz pulę bloków pamięci o stałym rozmiarze

### <a name="prototype"></a>Prototype

```C
UINT tx_block_pool_create(TX_BLOCK_POOL *pool_ptr,
                          CHAR *name_ptr, ULONG block_size,
                          VOID *pool_start, ULONG pool_size);
```
### <a name="description"></a>Opis

Ta usługa tworzy pulę bloków pamięci o stałym rozmiarze. Określony obszar pamięci jest podzielony na tyle bloków pamięci o stałym rozmiarze, jak to możliwe, przy użyciu formuły:    
**łączna liczba bloków** = (**całkowita liczba bajtów**)/(**rozmiar bloku** + sizeof (void *))

> [!IMPORTANT]
> Każdy blok pamięci zawiera jeden wskaźnik obciążenia, który jest niewidoczny dla użytkownika i jest reprezentowany przez "sizeof (void *)" w poprzedniej formule.

### <a name="parameters"></a>Parametry

- **pool_ptr**: wskaźnik do bloku sterującego puli blok pamięci.
- **name_ptr**: wskaźnik do nazwy puli bloków pamięci.
- **block_size**: liczba bajtów w każdym bloku pamięci.
- **pool_start**: adres początkowy puli bloków pamięci. Adres początkowy musi być wyrównany do rozmiaru typu danych ULONG.
- **pool_size**: całkowita liczba bajtów dostępnych dla puli bloków pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślnie utworzono pulę bloków pamięci.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci. Wskaźnik ma wartość NULL lub pula została już utworzona.
- TX_PTR_ERROR: (0x03) nieprawidłowy adres początkowy puli.
- TX_SIZE_ERROR: (0x05) rozmiar puli jest nieprawidłowy.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_BLOCK_POOL  my_pool;
UINT           status;

/* Create a memory pool whose total size is 1000 bytes
   starting at address 0x100000. Each block in this
   pool is defined to be 50 bytes long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
               50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18
   memory blocks of 50 bytes each. The reason
   there are not 20 blocks in the pool is
   because of the one overhead pointer associated with each
   block. */
```
### <a name="see-also"></a>Zobacz też

- tx_block_allocate
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_delete"></a>tx_block_pool_delete

Usuń pulę bloków pamięci

### <a name="prototype"></a>Prototype

```C
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określoną pulę bloków pamięci. Wszystkie wątki zawieszają się, czekając na wznowienie bloku pamięci z tej puli i z uwzględnieniem TX_DELETED stanu powrotu.

> [!IMPORTANT]
> Jest on odpowiedzialny za zarządzanie obszarem pamięci skojarzonym z pulą, która jest dostępna po zakończeniu tej usługi. Ponadto aplikacja musi uniemożliwić korzystanie z usuniętej puli lub jej poprzednich bloków pamięci.

### <a name="parameters"></a>Parametry

- **pool_ptr**: wskaźnik do wcześniej utworzonej puli bloków pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślnie usunięto pulę bloków pamięci.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_BLOCK_POOLmy_pool;
UINT           status;

    /* Delete entire memory block pool. Assume that the pool
      has already been created with a call to
      tx_block_pool_create. */
    status =  tx_block_pool_delete(&my_pool);

    /* If status equals TX_SUCCESS, the memory block pool is
       deleted. */
```
### <a name="see-also"></a>Zobacz też

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

Pobierz informacje o puli blokowej

### <a name="prototype"></a>Prototype

```C
UINT tx_block_pool_info_get(TX_BLOCK_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *total_blocks,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BLOCK_POOL **next_pool);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o określonej puli pamięci blokowej.

### <a name="parameters"></a>Parametry

- **pool_ptr**: wskaźnik do wcześniej utworzonej puli bloków pamięci.
- **name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy puli blokowej.
- **dostępne**: wskaźnik do miejsca docelowego dla liczby dostępnych bloków w puli blokowej.
- **total_blocks**: wskaźnik do miejsca docelowego dla łącznej liczby bloków w puli bloków.
- **first_suspended**: wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tej puli blokowej.
- **suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej puli blokowej.
- **next_pool**: wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej puli blokowej.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobranie informacji o puli blokowych.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_BLOCK_POOL    my_pool;
CHAR             *name;
ULONG            available;
ULONG            total_blocks;
TX_THREAD        *first_suspended;
ULONG            suspended_count;
TX_BLOCK_POOL    *next_pool;
UINT             status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
                &available,&total_blocks,
                &first_suspended, &suspended_count,
                &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a>Zobacz też

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

Uzyskaj informacje o wydajności puli bloku

### <a name="prototype"></a>Prototype

```c
UINT tx_block_pool_performance_info_get(TX_BLOCK_POOL *pool_ptr,
       ULONG *allocates, ULONG *releases,
       ULONG *suspensions, ULONG *timeouts));
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności dotyczące określonej puli bloków pamięci.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **pool_ptr**: wskaźnik do wcześniej utworzonej puli bloków pamięci.
- **przypisuje**: wskaźnik do miejsca docelowego dla liczby żądań przydzielenia wykonanych w tej puli.
- **wersje**: wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.
- **zawieszenia**: wskaźnik do miejsca docelowego dla liczby zawieszeń alokacji wątku w tej puli.
- **limity czasu**: wskaźnik do miejsca docelowego dla liczby limitów przydziału zawieszeń w tej puli.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności puli blokowych.
- **TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik puli bloku.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_BLOCK_POOL     my_pool;
ULONG             allocates;
ULONG             releases;
ULONG             suspensions;
ULONG             timeouts;

/* Retrieve performance information on the previously created block
   pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
                                            &releases,
                &suspensions,
                &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

Uzyskaj informacje o wydajności systemu puli blokowej

### <a name="prototype"></a>Prototype

```C
UINT tx_block_pool_performance_system_info_get(ULONG *allocates,
       ULONG *releases, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich pul bloków pamięci w aplikacji.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **przypisuje**: wskaźnik do miejsca docelowego dla łącznej liczby żądań alokacji wykonanych dla wszystkich pul bloku.
- **wersje**: wskaźnik do miejsca docelowego dla łącznej liczby żądań zwolnienia wykonanych na wszystkich pulach bloku.
- **zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń alokacji wątku dla wszystkich pul bloku.
- **limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia przydziału dla wszystkich pul bloku.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne zablokowanie wydajności systemu puli.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all the block pools in
   the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
                     &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

Ustawianie priorytetu listy zawieszania puli bloków

### <a name="prototype"></a>Prototype

```C
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wątek o najwyższym priorytecie dla bloku pamięci w tej puli na początku listy zawieszeń. Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.

### <a name="parameters"></a>Parametry 

- **pool_ptr**: wskaźnik do bloku sterującego puli blok pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna priorytetyzacja puli zablokowanych.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_BLOCK_POOL my_pool;
UINT          status;

/* Ensure that the highest priority thread will receive
   the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_block_release call will wake up this thread. */
```
### <a name="see-also"></a>Zobacz też

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_release"></a>tx_block_release

Zwolnij blok pamięci o stałym rozmiarze

### <a name="prototype"></a>Prototype

```C
UINT tx_block_release(VOID *block_ptr);
```
### <a name="description"></a>Opis

Ta usługa zwalnia wcześniej przydzieloną blokadę z powrotem do skojarzonej puli pamięci. Jeśli istnieje co najmniej jeden wątek, który zawiesił oczekiwanie na bloki pamięci z tej puli, ten blok pamięci zostanie zawieszony i wznowiony.

> [!IMPORTANT]
> Aplikacja musi uniemożliwić korzystanie z obszaru blokowego pamięci po jego wydaniu z powrotem do puli.

### <a name="parameters"></a>Parametry

- **block_ptr**: wskaźnik do wcześniej przydzielony blok pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna wersja bloku pamięci.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do bloku pamięci.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_BLOCK_POOLmy_pool;
unsigned char*memory_ptr;
UINT         status;

/* Release a memory block back to my_pool. Assume that the
   pool has been created and the memory block has been
   allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
   to by memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a>Zobacz też

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize

## <a name="tx_byte_allocate"></a>tx_byte_allocate

Przydziel bajty pamięci

### <a name="prototype"></a>Prototype

```C
UINT tx_byte_allocate(TX_BYTE_POOL *pool_ptr,
                          VOID **memory_ptr, ULONG memory_size,
                          ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa przydziela określoną liczbę bajtów z określonej puli bajtów pamięci.

> [!WARNING]
> Ważne jest, aby upewnić się, że kod aplikacji nie zapisuje poza przydzielonym blokiem pamięci. W takim przypadku uszkodzenie występuje w sąsiednim (zazwyczaj kolejnym) bloku pamięci. Wyniki są nieprzewidywalne i często są krytyczne!

> [!IMPORTANT]
> Wydajność tej usługi jest funkcją rozmiaru bloku i ilością fragmentacji w puli. W związku z tym ta usługa nie powinna być używana w wątkach o krytycznym czasie wykonywania.

### <a name="parameters"></a>Parametry

- **pool_ptr**: wskaźnik do wcześniej utworzonej puli pamięci.
- **memory_ptr**: wskaźnik do wskaźnika pamięci docelowej. Po pomyślnym przydzieleniu adres przydzielonego obszaru pamięci jest umieszczany w miejscu, do którego wskazuje ten parametr.
- **memory_size**: Liczba żądanych bajtów.
- **WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli nie jest dostępna wystarczająca ilość pamięci. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xffffffff)
    - wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem. *Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z inicjacji.*

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu udostępnienia wystarczającej ilości pamięci.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na pamięć.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna alokacja pamięci.
- **TX_DELETED**: (0x01) Pula pamięci została usunięta podczas wstrzymania wątku.
- **TX_NO_MEMORY**: usługa (0x10) nie może przydzielić pamięci w określonym czasie, aby czekać.
- **TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do wskaźnika docelowego.
- TX_SIZE_ERROR: (0X05) żądany rozmiar jest równy zero lub większy niż Pula.
- TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT         status;

/* Allocate a 112 byte memory area from my_pool. Assume
   that the pool has already been created with a call to
   tx_byte_pool_create. */
status =  tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
                       112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
   address of the allocated memory area. */
```
### <a name="see-also"></a>Zobacz też

- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_create"></a>tx_byte_pool_create

Utwórz pulę pamięci bajtów

### <a name="prototype"></a>Prototype

```C
UINT tx_byte_pool_create(TX_BYTE_POOL *pool_ptr,
                          CHAR *name_ptr, VOID *pool_start,
                          ULONG pool_size);
```
### <a name="description"></a>Opis

Ta usługa tworzy pulę bajtów pamięci w określonym obszarze. Początkowo Pula składa się z zasadniczo jednego bardzo dużego bezpłatnego bloku. Jednak Pula jest dzielona na mniejsze bloki w miarę dokonywania alokacji.

### <a name="parameters"></a>Parametry

- **pool_ptr**: wskaźnik do bloku kontroli puli pamięci.
- **name_ptr**: wskaźnik do nazwy puli pamięci.
- **pool_start**: początkowy adres puli pamięci. Adres początkowy musi być wyrównany do rozmiaru typu danych ULONG.
- **pool_size**: Łączna liczba bajtów dostępnych dla puli pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne utworzenie puli pamięci.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci. Wskaźnik ma wartość NULL lub pula została już utworzona.
- TX_PTR_ERROR: (0x03) nieprawidłowy adres początkowy puli.
- TX_SIZE_ERROR: (0x05) rozmiar puli jest nieprawidłowy.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Create a memory pool whose total size is 2000 bytes
   starting at address 0x500000. */
status =  tx_byte_pool_create(&my_pool, "my_pool_name",
             (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
   allocating memory. */
```
### <a name="see-also"></a>Zobacz też

- tx_byte_allocate
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

Usuwanie puli bajtów pamięci

### <a name="prototype"></a>Prototype

```C
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określoną pulę bajtów pamięci. Wszystkie wątki zostały zawieszone, oczekując na wznowienie pamięci z tej puli i z uwzględnieniem TX_DELETED stanu powrotu.

> [!IMPORTANT]
> Jest on odpowiedzialny za zarządzanie obszarem pamięci skojarzonym z pulą, która jest dostępna po zakończeniu tej usługi. Ponadto aplikacja musi uniemożliwić korzystanie z usuniętej puli lub pamięci, która została wcześniej przypisana.

### <a name="parameters"></a>Parametry 

- **pool_ptr**: wskaźnik do wcześniej utworzonej puli pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne usunięcie puli pamięci.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Delete entire memory pool. Assume that the pool has already
   been created with a call to tx_byte_pool_create. */
status =   tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```
### <a name="see-also"></a>Zobacz też

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

Pobierz informacje o puli bajtów

### <a name="prototype"></a>Prototype

```C
UINT tx_byte_pool_info_get(TX_BYTE_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *fragments,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BYTE_POOL **next_pool);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o określonej puli bajtów pamięci.

### <a name="parameters"></a>Parametry

- **pool_ptr**: wskaźnik do wcześniej utworzonej puli pamięci.
- **name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy puli bajtów.
- **dostępne**: wskaźnik do miejsca docelowego dla liczby dostępnych bajtów w puli.
- **fragmenty**: wskaźnik do miejsca docelowego dla łącznej liczby fragmentów pamięci w puli bajtów.
- **first_suspended**: wskaźnik do miejsca docelowego dla wskaźnika do wątku, który najpierw znajduje się na liście zawieszeń tej puli bajtów.
- **suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej puli bajtów.
- **next_pool**: wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej puli bajtów.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobranie informacji o puli.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_BYTE_POOL my_pool;
CHAR         *name;
ULONG        available;
ULONG        fragments;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_BYTE_POOL *next_pool;
UINT         status;

/* Retrieve information about the previously created
   block pool "my_pool." */
status =  tx_byte_pool_info_get(&my_pool, &name,
             &available, &fragments,
             &first_suspended, &suspended_count,
             &next_pool);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a>Zobacz też

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_info_get"></a>tx_byte_pool_performance_info_get

Pobierz informacje o wydajności puli bajtów

### <a name="prototype"></a>Prototype

```C
UINT tx_byte_pool_performance_info_get(TX_BYTE_POOL *pool_ptr,
        ULONG *allocates, ULONG *releases,
        ULONG *fragments_searched, ULONG *merges, ULONG *splits,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności dotyczące określonej puli bajtów pamięci.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **pool_ptr**: wskaźnik do wcześniej utworzonej puli bajtów pamięci.
- **przypisuje**: wskaźnik do miejsca docelowego dla liczby żądań przydzielenia wykonanych w tej puli.
- **wersje**: wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.
- **fragments_searched**: wskaźnik do miejsca docelowego dla liczby fragmentów pamięci wewnętrznej przeszukanych podczas żądania alokacji w tej puli.
- **scalenia**: wskaźnik do miejsca docelowego dla liczby wewnętrznych bloków pamięci scalonych podczas żądań alokacji w tej puli.
- **Splits**: wskaźnik do miejsca docelowego dla liczby wewnętrznych bloków pamięci podzielonej (fragmenty) utworzonych podczas żądania alokacji w tej puli.
- **zawieszenia**: wskaźnik do miejsca docelowego dla liczby zawieszeń alokacji wątku w tej puli.
- **limity czasu**: wskaźnik do miejsca docelowego dla liczby limitów przydziału zawieszeń w tej puli.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- TX_SUCCESS: (0x00) pomyślne pobieranie wydajności puli bajtów.
- **TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik puli bajtów.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_BYTE_POOL     my_pool;
ULONG            fragments_searched;
ULONG            merges;
ULONG            splits;
ULONG            allocates;
ULONG            releases;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created byte
   pool.  */
status =  tx_byte_pool_performance_info_get(&my_pool,
                &fragments_searched,
                &merges, &splits,
                &allocates, &releases,
                      &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

Pobierz informacje o wydajności systemu puli bajtów

### <a name="prototype"></a>Prototype

```C
UINT  tx_byte_pool_performance_system_info_get(ULONG *allocates,
        ULONG *releases, ULONG *fragments_searched, ULONG *merges,
        ULONG *splits, ULONG *suspensions, ULONG *timeouts);;
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich pul bajtów pamięci w systemie.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **przypisuje**: wskaźnik do miejsca docelowego dla liczby żądań przydzielenia wykonanych w tej puli.
- **wersje**: wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.
- **fragments_searched**: wskaźnik do miejsca docelowego dla łącznej liczby fragmentów pamięci wewnętrznej przeszukanych podczas żądania alokacji we wszystkich pulach bajtów.
- **scalenia**: wskaźnik do miejsca docelowego dla łącznej liczby bloków pamięci wewnętrznej scalonych podczas żądania alokacji we wszystkich pulach bajtów.
- **Splits**: wskaźnik do miejsca docelowego dla łącznej liczby bloków pamięci wewnętrznej Split (fragmenty) utworzonych podczas żądania alokacji dla wszystkich pul bajtów.
- **zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń alokacji wątku dla wszystkich pul bajtów.
- **limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia przydziału dla wszystkich pul bajtów.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności puli bajtów.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
ULONG         fragments_searched;
ULONG         merges;
ULONG         splits;
ULONG         allocates;
ULONG         releases;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all byte pools in the
   system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
                &merges, &splits, &allocates, &releases,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

Ustawianie priorytetu listy zawieszania puli bajtów

### <a name="prototype"></a>Prototype

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wątek o najwyższym priorytecie dla pamięci w tej puli na początku listy zawieszeń. Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.

### <a name="parameters"></a>Parametry 

- **pool_ptr**: wskaźnik do bloku kontroli puli pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna priorytetyzacja puli pamięci.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
TX_BYTE_POOL my_pool;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_byte_release call will wake up this thread,
   if there is enough memory to satisfy its request. */
```
### <a name="see-also"></a>Zobacz też

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_release

## <a name="tx_byte_release"></a>tx_byte_release

Wydawanie bajtów z powrotem do puli pamięci

### <a name="prototype"></a>Prototype

```C
UINT tx_byte_release(VOID *memory_ptr);
```
### <a name="description"></a>Opis

Ta usługa zwalnia wcześniej przydzieloną przestrzeń pamięci z powrotem do skojarzonej puli. Jeśli istnieje co najmniej jeden wątek, który wstrzymał oczekiwanie na pamięć z tej puli, przybierana jest pamięć i wznawiana do momentu wyczerpania pamięci lub do momentu, gdy nie będzie już można wstrzymać wątków. Ten proces przydzielania pamięci do zawieszonych wątków zawsze zaczyna się od pierwszego wątku zawieszonego.

> [!IMPORTANT]
> Aplikacja musi uniemożliwić korzystanie z obszaru pamięci po jego udostępnieniu.

### <a name="parameters"></a>Parametry

- **memory_ptr**: wskaźnik do wcześniej przydzieloną obszaru pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne wydanie pamięci.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik obszaru pamięci.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
unsigned char    *memory_ptr;
UINT             status;

/* Release a memory back to my_pool. Assume that the memory
   area was previously allocated from my_pool. */
status =  tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
   memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a>Zobacz też

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize

## <a name="tx_event_flags_create"></a>tx_event_flags_create

Utwórz grupę flag zdarzeń

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_create(TX_EVENT_FLAGS_GROUP *group_ptr,
                          CHAR *name_ptr);
```
### <a name="description"></a>Opis

Ta usługa tworzy grupę flag zdarzeń 32. Wszystkie flagi zdarzeń 32 w grupie są inicjowane na zero. Każda flaga zdarzenia jest reprezentowana przez jeden bit.

### <a name="parameters"></a>Parametry

- **group_ptr**: wskaźnik do bloku sterowania grupą flag zdarzeń. 
- **name_ptr**: wskaźnik do nazwy grupy flag zdarzeń.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne utworzenie grupy zdarzeń.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy zdarzeń. Wskaźnik ma wartość NULL lub grupa zdarzeń została już utworzona.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_EVENT_FLAGS_GROUP my_event_group;
UINT         status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
            "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
   for get and set services. */
```
### <a name="see-also"></a>Zobacz też

- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_delete"></a>tx_event_flags_delete

Usuń grupę flag zdarzeń

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określoną grupę flag zdarzeń. Wszystkie wątki zawieszone w trakcie oczekiwania na zdarzenia z tej grupy są wznawiane i mają TX_DELETED stanu powrotu.

> [!IMPORTANT]
> Aplikacja musi upewnić się, że ustawione wywołanie zwrotne powiadomień dla tej grupy flag zdarzeń zostanie ukończone (lub wyłączone) przed usunięciem grupy flag zdarzeń. Ponadto aplikacja musi uniemożliwić wszystkie przyszłe użycie grupy flag zdarzeń usuniętych.

### <a name="parameters"></a>Parametry 

- **group_ptr**: wskaźnik do wcześniej utworzonej grupy flag zdarzeń.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) usunięcie grupy flag zdarzeń zakończonych powodzeniem.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy flag zdarzeń.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT                 status;

/* Delete event flags group. Assume that the group has
   already been created with a call to
   tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
   deleted. */
```
### <a name="see-also"></a>Zobacz też

- tx_event_flags_create
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_get"></a>tx_event_flags_get

Pobierz flagi zdarzeń z grupy flag zdarzeń

### <a name="prototype"></a>Prototype

```C
UINT tx_event_flags_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG requested_flags, UINT get_option,
                          ULONG *actual_flags_ptr, ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa pobiera flagi zdarzeń z określonej grupy flag zdarzeń. Każda grupa flag zdarzeń zawiera 32 flag zdarzeń. Każda flaga jest reprezentowana przez jeden bit. Ta usługa może pobrać różne kombinacje flag zdarzeń wybrane przez parametry wejściowe.

### <a name="parameters"></a>Parametry

- **group_ptr**: wskaźnik do wcześniej utworzonej grupy flag zdarzeń.
- **requested_flags**: 32-bitowa zmienna bez znaku reprezentująca żądane flagi zdarzeń.
- **get_option**: określa, czy są wymagane wszystkie lub wszystkie wymagane flagi zdarzeń. Następujące opcje są prawidłowe:
    - **TX_AND**: (0x02)
    - **TX_AND_CLEAR**: (0x03)
    - **TX_OR**: (0x00)
    - **TX_OR_CLEAR**: (0x01)

    Wybranie opcji TX_AND lub TX_AND_CLEAR określa, że wszystkie flagi zdarzeń muszą znajdować się w grupie. Wybór TX_OR lub TX_OR_CLEAR określa, że każda flaga zdarzenia jest zadowalająca. Flagi zdarzeń, które spełniają żądanie, są wyczyszczone (Ustaw wartość zero), jeśli określono TX_AND_CLEAR lub TX_OR_CLEAR.

- **actual_flags_ptr**: wskaźnik do lokalizacji docelowej, do której są umieszczone pobrane flagi zdarzeń. Należy zauważyć, że uzyskane bieżące flagi mogą zawierać flagi, które nie zostały zażądane.
- **WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli wybrane flagi zdarzeń nie są ustawione. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xffffffff)
    - wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem. Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu udostępnienia flag zdarzeń.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na flagi zdarzeń.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne flagi zdarzeń get.
- Grupa flag zdarzeń **TX_DELETED**: (0x01) została usunięta podczas wstrzymania wątku.
- **TX_NO_EVENTS**: usługa (0x07) nie może pobrać określonych zdarzeń w określonym czasie oczekiwania.
- **TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy flag zdarzeń.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik dla rzeczywistych flag zdarzeń.
- TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.
- TX_OPTION_ERROR: (0x08) określono nieprawidłową opcję Get-Option.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG         actual_events;
UINT          status;

/* Request that event flags 0, 4, and 8 are all set. Also,
   if they are set they should be cleared. If the event
   flags are not set, this service suspends for a maximum of
   20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
                      TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
   actual events obtained. */
```
### <a name="see-also"></a>Zobacz też

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

Pobierz informacje o grupie flag zdarzeń

### <a name="prototype"></a>Prototype

```C
UINT tx_event_flags_info_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                         CHAR **name, ULONG *current_flags,
                         TX_THREAD **first_suspended,
                         ULONG *suspended_count,
                         TX_EVENT_FLAGS_GROUP **next_group);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o określonej grupie flag zdarzeń.

### <a name="parameters"></a>Parametry

- **group_ptr**: wskaźnik do bloku sterowania grupą flag zdarzeń.
- **name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy grupy flag zdarzeń.
- **current_flags**: wskaźnik do miejsca docelowego dla bieżących flag ustawionych w grupie flag zdarzeń.
- **first_suspended**: wskaźnik do elementu docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tej grupy flag zdarzeń.
- **suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej grupie flag zdarzeń.
- **next_group**: wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej grupy flag zdarzeń.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobieranie informacji o grupie zdarzeń.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy zdarzeń.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
TX_EVENT_FLAGS_GROUPmy_event_group;
CHAR          *name;
ULONG         current_flags;
TX_THREAD     *first_suspended;
ULONG         suspended_count;
TX_EVENT_FLAGS_GROUP*next_group;
UINT          status;

/* Retrieve information about the previously created
   event flags group "my_event_group." */
status =  tx_event_flags_info_get(&my_event_group, &name,
             &current_flags,
             &first_suspended, &suspended_count,
             &next_group);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a>Zobacz też

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_performance-info_get"></a>tx_event_flags_performance info_get

Pobierz informacje o wydajności grupy flag zdarzeń

### <a name="prototype"></a>Prototype

```C
UINT tx_event_flags_performance_info_get(TX_EVENT_FLAGS_GROUP
                        *group_ptr, ULONG *sets, ULONG *gets,
                        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności dotyczące określonej grupy flag zdarzeń.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **group_ptr**: wskaźnik do wcześniej utworzonej grupy flag zdarzeń.
- **zestawy**: wskaźnik do miejsca docelowego dla liczby flag zdarzeń ustawia żądania wykonane dla tej grupy.
- **Pobiera**: wskaźnik do miejsca docelowego dla liczby flag zdarzeń Pobiera żądania wykonane dla tej grupy.
- **zawieszenia**: wskaźnik do miejsca docelowego dla liczby flag zdarzeń wątku uzyskuje zawieszenie dla tej grupy.
- **limity czasu**: wskaźnik do miejsca docelowego dla liczby flag zdarzeń uzyskuje limity czasu zawieszenia dla tej grupy.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne flagi zdarzeń grupy get.
- **TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik grupy flag zdarzeń.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_EVENT_FLAGS_GROUPmy_event_flag_group;
ULONG           sets;
ULONG           gets;
ULONG           suspensions;
ULONG           timeouts;

/* Retrieve performance information on the previously created event
   flag group. */
status =  tx_event_flags_performance_info_get(&my_event_flag_group,
   &sets, &gets, &suspensions,
   &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
   retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

Pobierz informacje o systemie wydajności

### <a name="prototype"></a>Prototype

```c
UINT  tx_event_flags_performance_system_info_get(ULONG *sets,
        ULONG *gets,ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich grup flag zdarzeń w systemie.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **zestawy**: wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń ustawionych żądania dla wszystkich grup.
- **Pobiera**: wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń pobieranie żądań wykonanych dla wszystkich grup.
- **zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń wątku uzyskuje zawieszenie dla wszystkich grup.
- **limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń pobieranie limitów czasu zawieszenia dla wszystkich grup.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne flagi zdarzeń wydajność systemu.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c
ULONG         sets;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created event
   flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
                &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_set"></a>tx_event_flags_set

Ustawianie flag zdarzeń w grupie flag zdarzeń

### <a name="prototype"></a>Prototype

```C
UINT tx_event_flags_set(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG  flags_to_set,UINT set_option);
```
### <a name="description"></a>Opis

Ta usługa ustawia lub czyści flagi zdarzeń w grupie flag zdarzeń, w zależności od określonego zestawu opcji. Wszystkie zawieszone wątki, których żądanie flag zdarzeń jest teraz spełnione, są wznawiane.

### <a name="parameters"></a>Parametry

- **group_ptr**: wskaźnik do wcześniej utworzonego bloku kontroli grupy flag zdarzeń.
- **flags_to_set**: określa flagi zdarzeń do ustawienia lub wyczyszczenia w zależności od wybranej opcji zestawu.
- **set_option**: określa, czy określone flagi zdarzeń są ANDed lub logicznie do bieżących flag zdarzenia w grupie. Następujące opcje są prawidłowe:
    - **TX_AND**: (0x02)
    - **TX_OR**: (0X00) wybranie pozycji TX_AND określa, że określone flagi zdarzeń są **i** są wbudowane w bieżące flagi zdarzenia w grupie. Ta opcja jest często używana do czyszczenia flag zdarzeń w grupie. W przeciwnym razie, jeśli określono TX_OR, określone flagi zdarzeń są **lub** Ed bieżącym zdarzeniem w grupie.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) ustawiono flag zdarzeń zakończonych powodzeniem.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik do grupy flag zdarzeń.
- TX_OPTION_ERROR: (0x08) określono nieprawidłową opcję Set.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_EVENT_FLAGS_GROUPmy_event_flags_group;
UINT         status;

/* Set event flags 0, 4, and 8. */
status =  tx_event_flags_set(&my_event_flags_group,
                           0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
   set and any suspended thread whose request was satisfied
   has been resumed. */
```
### <a name="see-also"></a>Zobacz też

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set_notify

## <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

Powiadamiaj aplikację, gdy są ustawione flagi zdarzeń

### <a name="prototype"></a>Prototype

```C
UINT tx_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr,
       VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy jedna lub więcej flag zdarzeń jest ustawionych w określonej grupie flag zdarzeń. Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.

> [!NOTE]
> Flagi zdarzeń aplikacji ustawiające wywołanie zwrotne powiadomienia nie mogą wywoływać żadnego interfejsu API SMP ThreadX z opcją zawieszenia.

### <a name="parameters"></a>Parametry 
- **group_ptr**: wskaźnik do wcześniej utworzonej grupy flag zdarzeń.
- **events_set_notify**: wskaźnik do flag zdarzeń aplikacji ustawia funkcję powiadomień. Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna Rejestracja flag zdarzeń ustawionych dla powiadomienia.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy flag zdarzeń.
- TX_FEATURE_NOT_ENABLED: (0xFF) system został skompilowany z wyłączonymi funkcjami powiadomień.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_EVENT_FLAGS_GROUPmy_group;

/* Register the "my_event_flags_set_notify" function for monitoring
   event flags set in the event flags group "my_group." */
status =  tx_event_flags_set_notify(&my_group,
                my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
   was successfully registered. */

void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)
   /* One or more event flags was set in this group! */
```
### <a name="see-also"></a>Zobacz też

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set

## <a name="tx_interrupt_control"></a>tx_interrupt_control

Włączanie i wyłączanie przerwań

### <a name="prototype"></a>Prototype

```C
UINT tx_interrupt_control(UINT new_posture);
```
### <a name="description"></a>Opis

Ta usługa włącza lub wyłącza przerwania określone przez parametr wejściowy **new_posture**.

> [!IMPORTANT]
> Jeśli ta usługa jest wywoływana z wątku aplikacji, przerwa stan pozostaje częścią kontekstu tego wątku. Na przykład jeśli wątek wywołuje tę procedurę w celu wyłączenia przerwań, a następnie zawiesza się po wznowieniu, przerwania zostaną wyłączone ponownie.

> [!WARNING]
> Ta usługa nie powinna być używana do włączania przerwań podczas inicjacji. Wykonanie tej operacji może spowodować nieprzewidywalne wyniki.

### <a name="parameters"></a>Parametry

- **new_posture**: ten parametr określa, czy przerwania są wyłączone czy włączone. Wartości prawne obejmują **TX_INT_DISABLE i TX_INT_ENABLE.** Rzeczywiste wartości tych parametrów są specyficzne dla portów. Ponadto niektóre architektury przetwarzania mogą obsługiwać dodatkowe przerwania postures. Aby uzyskać więcej informacji, zapoznaj się z informacjami dotyczącymi **_readme_threadx.txt_** na dysku dystrybucyjnym.

### <a name="return-values"></a>Wartości zwrócone

- Poprzedni stan: Ta usługa zwraca poprzednie przerwanie stan do obiektu wywołującego. Dzięki temu użytkownicy usługi mogą przywrócić poprzednią stan po wyłączeniu przerwań.

### <a name="allowed-from"></a>Dozwolone z

Wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture =  tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
   locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```
### <a name="see-also"></a>Zobacz też

Brak

## <a name="tx_mutex_create"></a>tx_mutex_create

Utwórz element mutex wzajemnego wykluczania

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_create(TX_MUTEX *mutex_ptr,
                          CHAR *name_ptr, UINT priority_inherit);
```
### <a name="description"></a>Opis
    
Ta usługa tworzy element mutex do wzajemnego wykluczania między wątkami na potrzeby ochrony zasobów.

### <a name="parameters"></a>Parametry

- **mutex_ptr**: wskaźnik do bloku sterowania muteksem.
- **name_ptr**: wskaźnik do nazwy obiektu mutex.
- **priority_inherit**: określa, czy ten element mutex obsługuje dziedziczenie priorytetów. Jeśli ta wartość jest TX_INHERIT, jest obsługiwane dziedziczenie priorytetu. Jeśli jednak określono TX_NO_INHERIT, dziedziczenie priorytetu nie jest obsługiwane przez ten mutex.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne utworzenie obiektu mutex.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik muteksu. Wskaźnik ma wartość NULL lub element mutex został już utworzony.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.
- TX_INHERIT_ERROR: (0x1F) nieprawidłowy priorytet dziedziczenia parametru.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Create a mutex to provide protection over a
   common resource. */
status =  tx_mutex_create(&my_mutex,"my_mutex_name",
                           TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
   use. */
```
### <a name="see-also"></a>Zobacz też

- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_delete"></a>tx_mutex_delete

Usuń element mutex wzajemnego wykluczania

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określony element mutex. Wszystkie wątki zawieszone w trakcie oczekiwania na element mutex są wznawiane i nadano TX_DELETED stanu powrotu.

> [!IMPORTANT]
> Jest to odpowiedzialność aplikacji, aby uniemożliwić korzystanie z usuniętego obiektu mutex.

### <a name="parameters"></a>Parametry

- **mutex_ptr**: wskaźnik do wcześniej utworzonego obiektu mutex.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne usunięcie obiektu mutex.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik muteksu.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Delete a mutex. Assume that the mutex
   has already been created. */
status =  tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
   deleted. */
```
### <a name="see-also"></a>Zobacz też

- tx_mutex_create
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_get"></a>tx_mutex_get

Uzyskaj własność obiektu mutex

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_get(TX_MUTEX *mutex_ptr, ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa próbuje uzyskać wyłączną własność określonego obiektu mutex. Jeśli wątek wywołujący jest już właścicielem obiektu mutex, licznik wewnętrzny jest zwiększany i zwracany jest stan pomyślny.

Jeśli element mutex jest własnością innego wątku, a ten wątek ma wyższy priorytet, a dziedziczenie priorytetów zostało określone w elemencie mutex Create, priorytet wątku o niższym priorytecie zostanie tymczasowo podniesiony do tego wątku wywołującego.

> [!IMPORTANT]
> Priorytet wątku o niższym priorytecie będącego właścicielem obiektu mutex z priorityinheritance nigdy nie powinien być modyfikowany przez wątek zewnętrzny podczas własności obiektu mutex.

### <a name="parameters"></a>Parametry

- **mutex_ptr**: wskaźnik do wcześniej utworzonego obiektu mutex.
- **WAIT_OPTION**: określa, jak działa usługa, jeśli element mutex jest już własnością innego wątku. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xffffffff)
    - wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem. *Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z inicjacji.*

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu udostępnienia elementu mutex.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na mutex.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna operacja pobrania obiektu mutex.
- **TX_DELETED**: (0x01) element mutex został usunięty podczas wstrzymania wątku.
- **TX_NOT_AVAILABLE**: usługa (0x1D) nie może pobrać własności obiektu mutex w określonym czasie w celu oczekiwania.
- **TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik muteksu.
- TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki oraz czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Obtain exclusive ownership of the mutex "my_mutex".
   If the mutex "my_mutex" is not available, suspend until it
   becomes available. */
status =  tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```
### <a name="see-also"></a>Zobacz też

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_info_get"></a>tx_mutex_info_get

Pobierz informacje o muteksie

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_info_get(TX_MUTEX *mutex_ptr, CHAR **name,
                          ULONG *count, TX_THREAD **owner,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count, TX_MUTEX **next_mutex);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje z określonego obiektu mutex.

### <a name="parameters"></a>Parametry

- **mutex_ptr**: wskaźnik do bloku sterowania muteksem.
- **name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy obiektu mutex.
- **Count**: wskaźnik do miejsca docelowego dla liczby własności obiektu mutex.
- **Owner**: wskaźnik do miejsca docelowego dla wskaźnika wątku będącego właścicielem.
- **first_suspended**: wskaźnik do elementu docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tego obiektu mutex.
- **suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tym elemencie mutex.
- **next_mutex**: wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego obiektu mutex.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobieranie informacji o muteksie.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik muteksu.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_MUTEX     my_mutex;
CHAR         *name;
ULONG        count;
TX_THREAD    *owner;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_MUTEX     *next_mutex;
UINT         status;

/* Retrieve information about the previously created
   mutex "my_mutex." */
status =  tx_mutex_info_get(&my_mutex, &name,
                          &count, &owner,
                          &first_suspended, &suspended_count,
                          &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a>Zobacz też

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

Pobierz informacje o wydajności muteksu

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_performance_info_get(TX_MUTEX *mutex_ptr, ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts,
       ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności dotyczące określonego obiektu mutex.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_MUTEX_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **mutex_ptr**: wskaźnik do wcześniej utworzonego obiektu mutex.
- Put **: wskaźnik** do miejsca docelowego dla liczby żądań PUT wykonanych dla tego obiektu mutex.
- **Pobiera**: wskaźnik do miejsca docelowego dla liczby żądań GET wykonanych dla tego obiektu mutex.
- **zawieszenia**: wskaźnik do miejsca docelowego dla liczby elementów mutex wątku dla tego obiektu mutex.
- **limity czasu**: wskaźnik do miejsca docelowego dla liczby przekroczeń limitu czasu zawieszenia dla tego obiektu mutex.
- **Inversions**: wskaźnik do miejsca docelowego dla liczby wersji priorytetu wątku dla tego obiektu mutex.
- **dziedziczenia**: wskaźnik do miejsca docelowego dla liczby operacji dziedziczenia priorytetu wątku dla tego obiektu mutex.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pobieranie pomyślnej wydajności obiektu mutex. 
- **TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik muteksu.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_MUTEX     my_mutex;
ULONG        puts;
ULONG        gets;
ULONG        suspensions;
ULONG        timeouts;
ULONG        inversions;
ULONG        inheritances;

/* Retrieve performance information on the previously created
   mutex. */
status =  tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
                &suspensions, &timeouts, &inversions,
                &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

Pobierz informacje o wydajności systemu muteksu

### <a name="prototype"></a>Prototype

```C
UINT  tx_mutex_performance_system_info_get(ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts,
        ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich muteksów w systemie.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_MUTEX_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- Put **: wskaźnik** do miejsca docelowego dla łącznej liczby żądań PUT wykonanych dla wszystkich muteksów.
- **Pobiera**: wskaźnik do miejsca docelowego dla łącznej liczby żądań GET wykonanych dla wszystkich muteksów.
- **zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń elementu mutex wątku dla wszystkich muteksów.
- **limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia dla wszystkich muteksów.
- **Inversions**: wskaźnik do miejsca docelowego dla łącznej liczby wersji priorytetu wątku dla wszystkich muteksów.
- **dziedziczenia**: wskaźnik do miejsca docelowego dla łącznej liczby operacji dziedziczenia priorytetu wątku dla wszystkich muteksów.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności systemu muteksu.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;
ULONG         inversions;
ULONG         inheritances;

/* Retrieve performance information on all previously created
   mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
                &suspensions, &timeouts,
                &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

Ustawianie priorytetów listy zawieszeń muteksu

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wątek o najwyższym priorytecie na własność obiektu mutex na początku listy zawieszeń. Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.

### <a name="parameters"></a>Parametry 

- **mutex_ptr**: wskaźnik do wcześniej utworzonego obiektu mutex.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna priorytetyzacja obiektu mutex.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik muteksu.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Ensure that the highest priority thread will receive
   ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_mutex_put call that releases ownership of the
   mutex will give ownership to this thread and wake it
   up. */
```
### <a name="see-also"></a>Zobacz też

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_put

## <a name="tx_mutex_put"></a>tx_mutex_put

Zwolnij własność elementu mutex

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a>Opis

Ta usługa zmniejsza liczbę własności określonego obiektu mutex. Jeśli liczba własności wynosi zero, element mutex zostanie udostępniony.

> [!IMPORTANT]
> W przypadku wybrania dziedziczenia priorytetu podczas tworzenia obiektu mutex priorytet zwalnianego wątku zostanie przywrócony do priorytetu, który miał po raz pierwszy uzyskać własność obiektu mutex. Wszystkie inne zmiany priorytetu w wątku zwalniania mogą być cofnięte.

### <a name="parameters"></a>Parametry

- **mutex_ptr**: wskaźnik do wcześniej utworzonego obiektu mutex.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne wydanie muteksu.
- **TX_NOT_OWNED**: (0X1E) mutex nie należy do obiektu wywołującego.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik do elementu MUTEX.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki oraz czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_MUTEX         my_mutex;
UINT             status;
/* Release ownership of "my_mutex." */
status =  tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
   count has been decremented and if zero, released. */
```
### <a name="see-also"></a>Zobacz też

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize

## <a name="tx_queue_create"></a>tx_queue_create

Utwórz kolejkę komunikatów

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_create(TX_QUEUE *queue_ptr, CHAR *name_ptr,
                          UINT message_size,
                          VOID *queue_start, ULONG queue_size);
```
### <a name="description"></a>Opis

Ta usługa tworzy kolejkę komunikatów, która jest zwykle używana do komunikacji międzywątkowej. Całkowita liczba komunikatów jest obliczana na podstawie określonego rozmiaru komunikatu i całkowitej liczby bajtów w kolejce.

> [!IMPORTANT]
> Jeśli łączna liczba bajtów określona w obszarze pamięci kolejki nie jest równo podzielna przez określony rozmiar komunikatu, pozostałe bajty w obszarze pamięci nie są używane.

### <a name="parameters"></a>Parametry

- **queue_ptr**: wskaźnik do bloku sterowania kolejki komunikatów.
- **name_ptr**: wskaźnik na nazwę kolejki komunikatów.
- **message_size**: Określa rozmiar każdej wiadomości w kolejce. Rozmiary komunikatów mieszczą się w zakresie od 1 32-bitowego wyrazu do 16 32-bitowych wyrazów. Prawidłowe opcje rozmiaru komunikatu to wartości numeryczne z przestawu od 1 do 16 włącznie.
- **queue_start**: adres początkowy kolejki komunikatów. Adres początkowy musi być wyrównany do rozmiaru typu danych ULONG.
- **queue_size**: całkowita liczba bajtów dostępnych dla kolejki komunikatów.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne utworzenie kolejki komunikatów.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów. Wskaźnik ma wartość NULL lub kolejka została już utworzona.
- TX_PTR_ERROR: (0x03) nieprawidłowy adres początkowy kolejki komunikatów.
- TX_SIZE_ERROR: (0x05) rozmiar kolejki komunikatów jest nieprawidłowy.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_QUEUE     my_queue;
UINT         status;

/* Create a message queue whose total size is 2000 bytes
   starting at address 0x300000. Each message in this
   queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
            4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
   for storing 125 messages (2000 bytes/ 16 bytes per
   message). */
```
### <a name="see-also"></a>Zobacz też

- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_delete"></a>tx_queue_delete

Usuń kolejkę komunikatów

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określoną kolejkę komunikatów. Wszystkie wątki zawieszają się, dopóki komunikat z tej kolejki zostanie wznowiony i nastąpi TX_DELETED stanu powrotu.

> [!IMPORTANT]
> Aplikacja musi upewnić się, że wszystkie wywołania zwrotne powiadomień o wysłaniu dla tej kolejki zostaną zakończone (lub wyłączone) przed usunięciem kolejki. Ponadto aplikacja musi uniemożliwić wszelkie przyszłe użycie usuniętej kolejki.

*Jest również odpowiedzialna za zarządzanie obszarem pamięci skojarzonym z kolejką, która jest dostępna po zakończeniu tej usługi.*

### <a name="parameters"></a>Parametry 

- **queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne usunięcie kolejki komunikatów.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_QUEUE     my_queue;
UINT         status;

/* Delete entire message queue. Assume that the queue
   has already been created with a call to
   tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
   deleted. */
```
### <a name="see-also"></a>Zobacz też

- tx_queue_create
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_flush"></a>tx_queue_flush

Puste wiadomości w kolejce komunikatów

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa wszystkie komunikaty przechowywane w określonej kolejce komunikatów. Jeśli kolejka jest pełna, komunikaty wszystkich zawieszonych wątków są odrzucane. Każdy zawieszony wątek zostanie wznowiony ze stanem powrotu, który wskazuje, że wiadomość została wysłana pomyślnie. Jeśli kolejka jest pusta, ta usługa nie robi nic.

### <a name="parameters"></a>Parametry 

- **queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne Opróżnianie kolejki komunikatów.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```c
TX_QUEUE     my_queue;
UINT         status;

/* Flush out all pending messages in the specified message
   queue. Assume that the queue has already been created
   with a call to tx_queue_create. */
status =  tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
    empty. */
```
### <a name="see-also"></a>Zobacz też

- tx_queue_create
- tx_queue_delete
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_front_send"></a>tx_queue_front_send

Wyślij wiadomość na przednią kolejkę

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_front_send(TX_QUEUE *queue_ptr,
                           VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa wysyła komunikat do lokalizacji frontonu określonej kolejki komunikatów. Wiadomość jest **kopiowana** na przód kolejki z obszaru pamięci określonego przez wskaźnik źródła.

### <a name="parameters"></a>Parametry

- **queue_ptr**: wskaźnik do bloku sterowania kolejki komunikatów.
- **source_ptr**: wskaźnik do komunikatu.
- **WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli kolejka komunikatów jest pełna. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xffffffff)
    - wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem. *Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.*

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, w którym znajduje się w kolejce.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na pokój w kolejce.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne wysłanie komunikatu.
- **TX_DELETED**: (0x01) Kolejka komunikatów została usunięta podczas wstrzymania wątku.
- **TX_QUEUE_FULL**: usługa (0x0B) nie może wysłać komunikatu, ponieważ kolejka była zapełniona przez czas oczekiwania przez określony czas.
- **TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik źródła komunikatu.
- TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG        my_message[4];

/* Send a message to the front of "my_queue." Return
   immediately, regardless of success. This wait
   option is used for calls from initialization, timers,
   and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
            TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
   of the specified queue. */
```
### <a name="see-also"></a>Zobacz też

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_info_get"></a>tx_queue_info_get

Pobierz informacje o kolejce

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_info_get(TX_QUEUE *queue_ptr, CHAR **name,
        ULONG *enqueued, ULONG *available_storage
        TX_THREAD **first_suspended, ULONG *suspended_count,
        TX_QUEUE **next_queue);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o określonej kolejce komunikatów.

### <a name="parameters"></a>Parametry

- **queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.
- **name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy kolejki.
- w **kolejce**: wskaźnik do miejsca docelowego dla liczby komunikatów znajdujących się obecnie w kolejce.
- **available_storage**: wskaźnik do miejsca docelowego dla liczby komunikatów, dla których w kolejce znajduje się obecnie miejsce.
- **first_suspended**: wskaźnik do elementu docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tej kolejki.
- **suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej kolejce.
- **next_queue**: wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej kolejki.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) informacje o kolejce zakończone powodzeniem.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_QUEUE     my_queue;
CHAR         *name;
ULONG        enqueued;
ULONG        available_storage;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_QUEUE     *next_queue;
UINT         status;

/* Retrieve information about the previously created
   message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
            &enqueued, &available_storage,
            &first_suspended, &suspended_count,
            &next_queue);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a>Zobacz też

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

Pobierz informacje o wydajności kolejki

### <a name="prototype"></a>Prototype

```C
UINT  tx_queue_performance_info_get(TX_QUEUE *queue_ptr,
        ULONG *messages_sent, ULONG *messages_received,
        ULONG *empty_suspensions, ULONG *full_suspensions,
        ULONG *full_errors, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności określonej kolejki.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_QUEUE_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **queue_ptr**: wskaźnik do wcześniej utworzonej kolejki.
- **messages_sent**: wskaźnik do miejsca docelowego dla liczby żądań wysłania wykonanych dla tej kolejki.
- **messages_received**: wskaźnik do miejsca docelowego dla liczby żądań odbioru wykonanych dla tej kolejki.
- **empty_suspensions**: wskaźnik do miejsca docelowego dla liczby pustych zawieszeń kolejki w tej kolejce.
- **full_suspensions**: wskaźnik do miejsca docelowego dla liczby pełnych zawieszeń kolejki w tej kolejce.
- **full_errors**: wskaźnik do miejsca docelowego dla liczby pełnych błędów kolejki w tej kolejce.
- **limity czasu**: wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia wątku w tej kolejce.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności kolejki.
- **TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik kolejki.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_QUEUE     my_queue;
ULONG        messages_sent;
ULONG        messages_received;
ULONG        empty_suspensions;
ULONG        full_suspensions;
ULONG        full_errors;
ULONG        timeouts;

/* Retrieve performance information on the previously created
   queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

Pobierz informacje o wydajności systemu kolejkowania

### <a name="prototype"></a>Prototype

```C
UINT  tx_queue_performance_system_info_get(ULONG *messages_sent,
        ULONG *messages_received, ULONG *empty_suspensions,
        ULONG *full_suspensions, ULONG *full_errors,
        ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich kolejek w systemie.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_QUEUE_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **messages_sent**: wskaźnik do miejsca docelowego dla łącznej liczby żądań wysłania wykonanych na wszystkich kolejkach.
- **messages_received**: wskaźnik do miejsca docelowego dla łącznej liczby żądań odbioru wykonanych dla wszystkich kolejek.
- **empty_suspensions**: wskaźnik do miejsca docelowego dla łącznej liczby pustych zawieszeń kolejki we wszystkich kolejkach.
- **full_suspensions**: wskaźnik do miejsca docelowego dla łącznej liczby pełnych zawieszeń kolejki we wszystkich kolejkach.
- **full_errors**: wskaźnik do miejsca docelowego dla łącznej liczby pełnych błędów kolejki dla wszystkich kolejek.
- **limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia wątku we wszystkich kolejkach.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna Kolejka wydajności systemu get.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c
ULONG         messages_sent;
ULONG         messages_received;
ULONG         empty_suspensions;
ULONG         full_suspensions;
ULONG         full_errors;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
            &messages_received, &empty_suspensions,
            &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_prioritize"></a>tx_queue_prioritize

Ustawianie priorytetu listy zawieszania kolejki

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Opis

Ta usługa umieszcza wątek o najwyższym priorytecie dla komunikatu (lub umieszcza komunikat) w tej kolejce na początku listy zawieszeń. Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.

### <a name="parameters"></a>Parametry 

- **queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna priorytetyzacja kolejki.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_QUEUE     my_queue;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_queue_send or tx_queue_front_send call made
   to this queue will wake up this thread. */
```
### <a name="see-also"></a>Zobacz też

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_receive"></a>tx_queue_receive

Pobierz komunikat z kolejki komunikatów

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_receive(TX_QUEUE *queue_ptr,
                          VOID *destination_ptr, ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa pobiera komunikat z określonej kolejki komunikatów. Pobrany komunikat jest **kopiowany** z kolejki do obszaru pamięci określonego przez wskaźnik docelowy. Ten komunikat zostanie następnie usunięty z kolejki.

> [!WARNING]
> Określony obszar pamięci docelowej musi być wystarczająco duży, aby pomieścić komunikat; oznacza to, że miejsce docelowe komunikatu wskazywane przez **destination_ptr** musi być co najmniej tak duże, jak rozmiar komunikatu dla tej kolejki. W przeciwnym razie, jeśli miejsce docelowe nie jest wystarczająco duże, uszkodzenie pamięci występuje w następującym obszarze pamięci.

### <a name="parameters"></a>Parametry

- **queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.
- **destination_ptr**: Lokalizacja lokalizacji, w której ma zostać skopiowana wiadomość.
- **WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli kolejka komunikatów jest pusta. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT**: (0x00000000) 
    - **TX_WAIT_FOREVER**: (0xffffffff) 
    - wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem. Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu udostępnienia komunikatu.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na komunikat.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobranie komunikatu.
- **TX_DELETED**: (0x01) Kolejka komunikatów została usunięta podczas wstrzymania wątku.
- **TX_QUEUE_EMPTY**: (0X0a) usługa nie mogła pobrać komunikatu, ponieważ kolejka była pusta przez czas oczekiwania przez określony czas.
- **TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik docelowy dla komunikatu.
- TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_QUEUE     my_queue;
UINT         status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
   empty, suspend until a message is present. Note that
   this suspension is only possible from application
   threads. */
status =  tx_queue_receive(&my_queue, my_message,
                          TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
   "my_message." */
```
### <a name="see-also"></a>Zobacz też

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_send"></a>tx_queue_send

Wyślij komunikat do kolejki komunikatów

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_send(TX_QUEUE *queue_ptr,
                          VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa wysyła komunikat do określonej kolejki komunikatów. Wysłany komunikat jest **kopiowany** do kolejki z obszaru pamięci określonego przez wskaźnik źródła.

### <a name="parameters"></a>Parametry

- **queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.
- **source_ptr**: wskaźnik do komunikatu.
- **WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli kolejka komunikatów jest pełna. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xffffffff)
    - wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem. *Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.*

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, w którym znajduje się w kolejce.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na pokój w kolejce.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne wysłanie komunikatu.
- **TX_DELETED**: (0x01) Kolejka komunikatów została usunięta podczas wstrzymania wątku.
- **TX_QUEUE_FULL**: usługa (0x0B) nie może wysłać komunikatu, ponieważ kolejka była zapełniona przez czas oczekiwania przez określony czas.
- **TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik źródła komunikatu.
- TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
   regardless of success. This wait option is used for
   calls from initialization, timers, and ISRs. */
status =  tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
   queue. */
```
### <a name="see-also"></a>Zobacz też

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send_notify

## <a name="tx_queue_send_notify"></a>tx_queue_send_notify 

Powiadamiaj aplikację, gdy wiadomość jest wysyłana do kolejki

### <a name="prototype"></a>Prototype

```C
UINT  tx_queue_send_notify(TX_QUEUE *queue_ptr,
        VOID (*queue_send_notify)(TX_QUEUE *));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy komunikat zostanie wysłany do określonej kolejki. Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.

> [!NOTE]
> Wywołanie zwrotne powiadomienia o wysłaniu kolejki aplikacji nie może wywołać żadnego ThreadX interfejsu API SMP z opcją zawieszenia.

### <a name="parameters"></a>Parametry 

- **queue_ptr**: wskaźnik do wcześniej utworzonej kolejki.
- **queue_send_notify**: wskaźnik do funkcji powiadomień o wysyłaniu do kolejki aplikacji. Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna Rejestracja powiadomienia o wysłaniu kolejki.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki.
- TX_FEATURE_NOT_ENABLED: (0xFF) system został skompilowany z wyłączonymi funkcjami powiadomień.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_QUEUE         my_queue;

/* Register the "my_queue_send_notify" function for monitoring
   messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
   successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
/* A message was just sent to this queue! */
}
```
### <a name="see-also"></a>Zobacz też

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send

## <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put 

Umieść wystąpienie w zliczaniu semafora z pułapem

### <a name="prototype"></a>Prototype

```C
UINT  tx_semaphore_ceiling_put(TX_SEMAPHORE *semaphore_ptr,
        ULONG ceiling);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wystąpienie w określonym semaforze zliczania, który w rzeczywistości zwiększa semafor zliczania o jeden. Jeśli bieżąca wartość semafora zliczania jest większa lub równa określonej granicy, wystąpienie nie zostanie umieszczone i zostanie zwrócony błąd TX_CEILING_EXCEEDED.

### <a name="parameters"></a>Parametry 

- **semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora.
- **granica**: maksymalny limit dozwolony dla semafora (wartości z zakresu od 1 do 0xffffffff).

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślny pułap semafora.
- **TX_CEILING_EXCEEDED**: (0x21) żądanie Put przekracza limit.
- TX_INVALID_CEILING: (0x22) podano nieprawidłową wartość zero dla pułapu.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c
TX_SEMAPHORE     my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
   that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
```
### <a name="see-also"></a>Zobacz też

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_create"></a>tx_semaphore_create

Tworzenie semafora zliczania

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_create(TX_SEMAPHORE *semaphore_ptr,
                           CHAR *name_ptr, ULONG initial_count);
```
### <a name="description"></a>Opis

Ta usługa tworzy semafor zliczania dla synchronizacji między wątkami. Początkowa liczba semaforów jest określana jako parametr wejściowy.

### <a name="parameters"></a>Parametry 

- **semaphore_ptr**: wskaźnik do bloku sterowania semaforem. 
- **name_ptr**: wskaźnik do nazwy semafora.
- **initial_count**: określa początkową liczbę dla tego semafora. Wartości prawne mieszczą się w zakresie od 0x00000000 do 0xFFFFFFFF.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne utworzenie semafora.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora. Wskaźnik ma wartość NULL lub semafor został już utworzony.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Create a counting semaphore whose initial value is 1.
   This is typically the technique used to make a binary
   semaphore. Binary semaphores are used to provide
   protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
            "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
   use. */
```
### <a name="see-also"></a>Zobacz też

- tx_semaphore_ceiling_put
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_delete"></a>tx_semaphore_delete

Usuń semafor zliczania

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określony semafor zliczania. Wszystkie wątki zawieszone w trakcie oczekiwania na wystąpienie semafora są wznawiane i nadawane TX_DELETED stanie powrotu.

> [!IMPORTANT]
> Aplikacja musi zapewnić ukończenie wywołania zwrotnego powiadomienia dla tego semafora (lub wyłączone) przed usunięciem semafora. Ponadto aplikacja musi uniemożliwić wszystkie przyszłe użycie usuniętego semafora.

### <a name="parameters"></a>Parametry 

- **semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne zliczanie usunięcia semafora.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik zliczania semafora.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Delete counting semaphore. Assume that the counting
   semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
   deleted. */
```
### <a name="see-also"></a>Zobacz też

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_get"></a>tx_semaphore_get

Pobierz wystąpienie z zliczania semafora

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_get(TX_SEMAPHORE *semaphore_ptr,
                          ULONG wait_option)
```
### <a name="description"></a>Opis

Ta usługa Pobiera wystąpienie (pojedyncza liczba) z określonego semafora zliczania. W związku z tym liczba określonych semaforów zostanie zmniejszona o jeden.

### <a name="parameters"></a>Parametry

- **semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora zliczania.
- **WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli nie ma dostępnych wystąpień semafora; oznacza to, że liczba semaforów jest równa zero. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT**: (0x00000000)
    - **TX_WAIT_FOREVER**: (0xffffffff)
    - wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem. *Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.*

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu dostępności wystąpienia semafora. 

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na wystąpienie semafora.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobranie wystąpienia semafora.
- **TX_DELETED**: (0X01) zliczanie semafora został usunięty, gdy wątek został wstrzymany.
- **TX_NO_INSTANCE**: usługa (0x0D) nie może pobrać wystąpienia semafora zliczania (liczba semaforów wynosi zero w określonym czasie oczekiwania).
- **TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik zliczania semafora.
- TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```c
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Get a semaphore instance from the semaphore
   "my_semaphore." If the semaphore count is zero,
   suspend until an instance becomes available.
   Note that this suspension is only possible from
   application threads. */
status =  tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
   an instance of the semaphore. */
```
### <a name="see-also"></a>Zobacz też

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semahore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

Pobierz informacje o semaforze

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_info_get(TX_SEMAPHORE *semaphore_ptr,
                          CHAR **name, ULONG *current_value,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_SEMAPHORE **next_semaphore)
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o określonym semaforze.

### <a name="parameters"></a>Parametry

- **semaphore_ptr**: wskaźnik do bloku sterowania semaforem.
- **name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy semafora.
- **current_value**: wskaźnik do miejsca docelowego dla licznika bieżącego semafora.
- **first_suspended**: wskaźnik do elementu docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tego semafora.
- **suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tym semaforze.
- **next_semaphore**: wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego semafora.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobranie informacji semafora.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
TX_SEMAPHORE my_semaphore;
CHAR         *name;
ULONG        current_value;
TX_THREAD    *first_suspended;
ULONG        suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT         status;

/* Retrieve information about the previously created
   semaphore "my_semaphore." */
status =  tx_semaphore_info_get(&my_semaphore, &name,
                      &current_value,
                      &first_suspended, &suspended_count,
                      &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a>Zobacz też

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get 

Pobierz informacje o wydajności semafora

### <a name="prototype"></a>Prototype

```C
UINT  tx_semaphore_performance_info_get(TX_SEMAPHORE *semaphore_ptr,
        ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności dotyczące określonego semafora.

> [!NOTE]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora.
- Put **: wskaźnik** do miejsca docelowego dla liczby żądań PUT wykonanych dla tego semafora.
- **Pobiera**: wskaźnik do miejsca docelowego dla liczby żądań GET wykonanych dla tego semafora.
- **zawieszenia**: wskaźnik do miejsca docelowego dla liczby zawieszeń wątku w tym semaforze.
- **limity czasu**: wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia wątku dla tego semafora.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności semafora.
- **TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik semafora.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_SEMAPHORE     my_semaphore;
ULONG            puts;
ULONG            gets;
ULONG            suspensions;
ULONG            timeouts;

/* Retrieve performance information on the previously created
   semaphore. */
status =  tx_semaphore_performance_info_get(&my_semaphore, &puts,
               &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get 

Pobierz informacje o wydajności systemu semafora

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_performance_system_info_get(ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności dotyczące wszystkich semaforów w systemie.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- Put **: wskaźnik** do miejsca docelowego dla łącznej liczby żądań PUT wykonanych na wszystkich semaforach.
- **Pobiera**: wskaźnik do miejsca docelowego dla łącznej liczby żądań GET wykonanych na wszystkich semaforach.
- **zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń wątku na wszystkich semaforach.
- **limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia wątku dla wszystkich semaforów.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- TX_SUCCESS: (0x00) pomyślne pobieranie wydajności systemu semafora.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
ULONG         puts;
ULONG         gets;
ULONG         suspensions;
ULONG         timeouts;

/* Retrieve performance information on all previously created
   semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
               &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

Ustawianie priorytetu listy zawieszania semafora

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wątek o najwyższym priorytecie w przypadku wystąpienia semafora na początku listy zawieszeń. Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.

### <a name="parameters"></a>Parametry 

- **semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna priorytetyzacja semafora.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik zliczania semafora.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Ensure that the highest priority thread will receive
   the next instance of this semaphore. */
status =  tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
   suspended thread is at the front of the list. The
   next tx_semaphore_put call made to this semaphore will
   wake up this thread. */
```
### <a name="see-also"></a>Zobacz też

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_put

## <a name="tx_semaphore_put"></a>tx_semaphore_put

Umieść wystąpienie w zliczaniu semafora

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wystąpienie w określonym semaforze zliczania, który w rzeczywistości zwiększa semafor zliczania o jeden.

> [!IMPORTANT]
> Jeśli ta usługa jest wywoływana, gdy semafor ma wszystkie (OxFFFFFFFF), Nowa operacja Put spowoduje, że semafor zostanie zresetowany do zera.

### <a name="parameters"></a>Parametry

- **semaphore_ptr**: wskaźnik do wcześniej utworzonego bloku sterowania semaforem zliczania.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne umieszczenie semafora.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik do zliczania semafora.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_SEMAPHORE     my_semaphore;
UINT             status;

/* Increment the counting semaphore "my_semaphore." */
status =  tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
   been incremented. Of course, if a thread was waiting,
   it was given the semaphore instance and resumed. */
```
### <a name="see-also"></a>Zobacz też

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_get
- tx_semaphore_put_notify

## <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

Powiadamiaj aplikację po umieszczeniu semafora

### <a name="prototype"></a>Prototype

```C
UINT  tx_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr,
        VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy określony semafor jest umieszczony. Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.

> [!NOTE]
> Wywołanie zwrotne powiadomienia semafora aplikacji nie może wywołać żadnego ThreadXego interfejsu API SMP z opcją zawieszenia.

### <a name="parameters"></a>Parametry 

- **semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora.
- **semaphore_put_notify**: wskaźnik do funkcji powiadamiania o wykorzystaniu semafora aplikacji. Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna Rejestracja powiadomienia o wprowadzeniu semafora.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system został skompilowany z wyłączonymi funkcjami powiadomień.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_SEMAPHORE     my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
   the put operations on the semaphore "my_semaphore." */
status =  tx_semaphore_put_notify(&my_semaphore,
                my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
   was successfully registered. */

void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
   /* The semaphore was just put! */
}
```
### <a name="see-also"></a>Zobacz też

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put

## <a name="tx_thread_create"></a>tx_thread_create

Utwórz wątek aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_create(TX_THREAD *thread_ptr,
                          CHAR *name_ptr, VOID (*entry_function)(ULONG),
                          ULONG entry_input, VOID *stack_start,
                          ULONG stack_size, UINT priority,
                          UINT preempt_threshold, ULONG time_slice,
                          UINT auto_start);
```
### <a name="description"></a>Opis

Ta usługa tworzy wątek aplikacji, który uruchamia wykonywanie w określonej funkcji wprowadzania zadań. Stos, priorytet, wartość progowa i wycinek czasu są wśród atrybutów określonych przez parametry wejściowe. Ponadto jest również określony początkowy stan wykonywania wątku.

### <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do bloku sterującego wątku.
- **name_ptr**: wskaźnik do nazwy wątku.
- **entry_function**: określa początkową funkcję C do wykonania wątku. Gdy wątek wraca z tej funkcji wejścia, jest on umieszczany w stanie ukończenia i zawieszony czasowo.
- **entry_input**: wartość 32-bitowa, która jest przesyłana do funkcji wejścia wątku podczas pierwszego wykonania. Użycie tego danych wejściowych jest określane wyłącznie przez aplikację.
- **stack_start**: adres początkowy obszaru pamięci stosu. 
- **stack_size**: liczba bajtów w obszarze pamięci stosu. Obszar stosu wątku musi być wystarczająco duży, aby obsługiwał jego najgorszą metodę użycia.
- **priorytet**: liczbowy priorytet wątku. Wartości prawne mieszczą się w zakresie od 0 do (TX_MAX_PRIORITES-1), gdzie wartość 0 reprezentuje najwyższy priorytet.
- **preempt_threshold**: najwyższy poziom priorytetu (od 0 do (TX_MAX_PRIORITIES-1)) wyłączono przechodzenie. Tylko priorytety wyższe niż ten poziom mogą przewagę tego wątku. Ta wartość nie może być większa niż określony priorytet. Wartość równa priorytetu wątku powoduje wyłączenie progu zastępujący.
- **time_slice**: liczba czasomierzy, przez jaką ten wątek może działać, zanim inne gotowe wątki o takim samym priorytecie mają szansę uruchomienia. Należy pamiętać, że użycie wartości progowej przekroczenia powoduje wyłączenie tworzenia wycinków czasu. Dozwolone wartości wycinków czasu mieszczą się w zakresie od 1 do 0xFFFFFFFF (włącznie). Wartość **TX_NO_TIME_SLICE** (wartość 0) powoduje wyłączenie wycinka czasu dla tego wątku.

    > [!IMPORTANT]
    > Korzystanie z wycinków czasu powoduje niewielkie obciążenie systemu. Ponieważ podział czasu jest przydatny tylko w przypadkach, gdy wiele wątków ma ten sam priorytet, wątki mające unikatowy priorytet nie powinny mieć przypisanego wycinka czasowego.

- **auto_start**: określa, czy wątek zaczyna się od razu czy jest umieszczony w stanie wstrzymania. Opcje prawne są **TX_AUTO_START** (0x01) i **TX_DONT_START** (0x00). Jeśli TX_DONT_START jest określony, aplikacja musi później wywołać tx_thread_resume w celu uruchomienia wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne utworzenie wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik kontrolny wątku. Wskaźnik ma wartość NULL lub wątek został już utworzony.
- TX_PTR_ERROR: (0x03) nieprawidłowy adres początkowy punktu wejścia lub obszar stosu jest nieprawidłowy, zazwyczaj ma wartość NULL.
- TX_SIZE_ERROR: (0x05) rozmiar obszaru stosu jest nieprawidłowy. Wątki muszą mieć co najmniej **TX_MINIMUM_STACK** bajtów do wykonania.
- TX_PRIORITY_ERROR: (0x0F) nieprawidłowy priorytet wątku, który jest wartością spoza zakresu (od 0 do (TX_MAX_PRIORITIES-1)).
- TX_THRESH_ERROR: (0x18) określono nieprawidłowy preemptionthreshold. Ta wartość musi być prawidłowym priorytetem nie większym niż początkowy priorytet wątku.
- TX_START_ERROR: (0x10) nieprawidłowy wybór autostartu.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_THREAD     my_thread;
UINT          status;

/* Create a thread of priority 15 whose entry point is
   "my_thread_entry". This thread’s stack area is 1000
   bytes in size, starting at address 0x400000. The
   preemption-threshold is setup to allow preemption of threads
   with priorities ranging from 0 through 14. Time-slicing is
   disabled. This thread is automatically put into a ready
   condition. */
status =  tx_thread_create(&my_thread, "my_thread_name",
                my_thread_entry, 0x1234,
                (VOID *) 0x400000, 1000,
                15, 15, TX_NO_TIME_SLICE,
                TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
   for execution! */
...

/* Thread’s entry function. When "my_thread" actually
   begins execution, control is transferred to this
   function. */
VOID my_thread_entry (ULONG initial_input)
{

    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */

    /* The real work of the thread, including calls to
    other function should be called from here! */

    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```
### <a name="see-also"></a>Zobacz też

- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_delete"></a>tx_thread_delete

Usuń wątek aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określony wątek aplikacji. Ponieważ określony wątek musi być w stanie zakończony lub zakończony, ta usługa nie może zostać wywołana z wątku próbującego usunąć sam siebie.

> [!IMPORTANT]
> Jest on odpowiedzialny za zarządzanie obszarem pamięci skojarzonym ze stosem wątku, który jest dostępny po zakończeniu tej usługi. Ponadto aplikacja musi uniemożliwić korzystanie z usuniętego wątku.

### <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do wcześniej utworzonego wątku aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne usunięcie wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- **TX_DELETE_ERROR**: (0X11) określony wątek nie jest w stanie przerwania lub zakończenia.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_THREAD     my_thread;
UINT          status;

/* Delete an application thread whose control block is
   "my_thread". Assume that the thread has already been
   created with a call to tx_thread_create. */
status =  tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   deleted. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

Powiadamiaj aplikację przy wejściu i wyjściu wątku

### <a name="prototype"></a>Prototype

```C
UINT  tx_thread_entry_exit_notify(TX_THREAD *thread_ptr,
        VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy określony wątek zostanie wprowadzony lub zostanie zakończony. Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.

> [!NOTE]
> Wywołanie zwrotne powiadomienia o wejściu/wyjściu dla aplikacji nie może wywołać żadnego ThreadXego interfejsu API SMP z opcją zawieszenia.

### <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do wcześniej utworzonego wątku.
- **entry_exit_notify**: wskaźnik do funkcji powiadomienia o wejściu/wyjściu wątku aplikacji. Drugi parametr funkcji powiadomień o wejściu/wyjściu określa, czy jest obecny wpis lub wyjście. Wartość TX_THREAD_ENTRY (0x00) wskazuje, że wątek został wprowadzony, podczas gdy wartość TX_THREAD_EXIT (0x01) wskazuje, że wątek został zakończony. Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna Rejestracja funkcji powiadomień o wejściu/wyjściu wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.
- **TX_FEATURE_NOT_ENABLED (0xFF)** System został skompilowany z wyłączonymi funkcjami powiadomień.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_THREAD         my_thread;

/* Register the "my_entry_exit_notify" function for monitoring
   the entry/exit of the thread "my_thread." */
status =  tx_thread_entry_exit_notify(&my_thread,
                my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
   successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{

    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
                 /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
         /* Thread exit! */
}
```

### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_identify"></a>tx_thread_identify

Pobiera wskaźnik do aktualnie wykonywanego wątku

### <a name="prototype"></a>Prototype

```C
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a>Opis

Ta usługa zwraca wskaźnik do aktualnie wykonywanego wątku. Jeśli żaden wątek nie jest wykonywany, ta usługa zwraca wskaźnik o wartości null.

> [!IMPORTANT]
> Jeśli ta usługa jest wywoływana przez funkcję ISR, wartość zwracana reprezentuje wątek uruchomiony przed wykonaniem procedury obsługi przerwań.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

- wskaźnik wątku: wskaźnik do aktualnie wykonywanego wątku. Jeśli żaden wątek nie jest wykonywany, wartość zwracana jest TX_NULL.

### <a name="allowed-from"></a>Dozwolone z

Wątki i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_THREAD     *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr =  tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
   from that thread or an ISR that interrupted that thread.
   Otherwise, this service was called
   from an ISR when no thread was running when the
   interrupt occurred.  */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_info_get"></a>tx_thread_info_get

Pobierz informacje o wątku

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_info_get(TX_THREAD *thread_ptr, CHAR **name,
                          UINT *state, ULONG *run_count,
                          UINT *priority,
                          UINT *preemption_threshold,
                          ULONG *time_slice,
                          TX_THREAD **next_thread,
                          TX_THREAD **suspended_thread);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o określonym wątku.

### <a name="parameters"></a>Parametry 

- **thread_ptr**: wskaźnik do bloku sterowania wątkiem.
- **name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy wątku.
- **State**: wskaźnik do miejsca docelowego dla bieżącego stanu wykonywania wątku. Dopuszczalne są następujące wartości:
    - **TX_READY**: (0x00)
    - **TX_COMPLETED**: (0x01)
    - **TX_TERMINATED**: (0x02)
    - **TX_SUSPENDED**: (0x03)
    - **TX_SLEEP**: (0x04)
    - **TX_QUEUE_SUSP**: (0x05)
    - **TX_SEMAPHORE_SUSP**: (0x06)
    - **TX_EVENT_FLAG**: (0x07)
    - **TX_BLOCK_MEMORY**: (0x08)
    - **TX_BYTE_MEMORY**: (0x09)
    - **TX_MUTEX_SUSP**: (0x0D)

- **run_count**: wskaźnik do miejsca docelowego dla liczby uruchomień wątku. 
- **priorytet**: wskaźnik do miejsca docelowego dla priorytetu wątku.
- **preemption_threshold**: wskaźnik do miejsca docelowego dla progu zastępujący wątek.
- **time_slice**: wskaźnik do miejsca docelowego dla wycinka czasu wątku. 
- **next_thread**: wskaźnik do miejsca docelowego dla następnego utworzonego wskaźnika wątku.
- **suspended_thread**: wskaźnik do miejsca docelowego dla wskaźnika do następnego wątku na liście zawieszeń.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobranie informacji wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik kontrolny wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
   thread "my_thread." */
status =  tx_thread_info_get(&my_thread, &name,
                  &state, &run_count,
            &priority, &preemption_threshold,
                  &time_slice, &next_thread,&suspended_thread);
/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get 

Pobierz informacje o wydajności wątków

### <a name="prototype"></a>Prototype

```C
UINT  tx_thread_performance_info_get(TX_THREAD *thread_ptr,
        ULONG *resumptions, ULONG *suspensions,
        ULONG *solicited_preemptions, ULONG *interrupt_preemptions,
        ULONG *priority_inversions, ULONG *time_slices,
        ULONG *relinquishes, ULONG *timeouts, ULONG *wait_aborts,
        TX_THREAD **last_preempted_by);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności dotyczące określonego wątku.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_THREAD_ENABLE_PERFORMANCE_INFO** zdefiniowanych w celu zwrócenia informacji o wydajności przez tę usługę.

### <a name="parameters"></a>Parametry 

- **thread_ptr**: wskaźnik do wcześniej utworzonego wątku.
- **wznawiania**: wskaźnik do miejsca docelowego dla liczby wznowień tego wątku.
- **zawieszenia**: wskaźnik do miejsca docelowego dla liczby zawieszeń tego wątku.
- **solicited_preemptions**: wskaźnik do miejsca docelowego dla liczby przeniesień w wyniku wywołania usługi API ThreadX wykonanego przez ten wątek.
- **interrupt_preemptions**: wskaźnik do miejsca docelowego dla liczby przeniesień tego wątku w wyniku przetwarzania przerwań.
- **priority_inversions**: wskaźnik do miejsca docelowego dla liczby niewersji priorytetu tego wątku.
- **time_slices**: wskaźnik do miejsca docelowego dla liczby timeslices tego wątku.
- **zwalnia**: wskaźnik do miejsca docelowego dla liczby operacji zwalniania wątku wykonywanych przez ten wątek.
- **limity czasu**: wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia dla tego wątku.
- **wait_aborts**: wskaźnik do miejsca docelowego dla liczby przerwań oczekiwania wykonanych w tym wątku.
- **last_preempted_by**: wskaźnik do miejsca docelowego dla wskaźnika wątku, który ostatnio zastępują ten wątek.

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności wątku.
- **TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik wątku.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```c
TX_THREAD     my_thread;
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
TX_THREAD     *last_preempted_by;

/* Retrieve performance information on the previously created
   thread. */
status = tx_thread_performance_info_get(&my_thread, &resumptions,
               &suspensions,
               &solicited_preemptions, &interrupt_preemptions,
               &priority_inversions, &time_slices,
               &relinquishes, &timeouts,
               &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get 

Pobierz informacje o wydajności systemu wątków

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_performance_system_info_get(ULONG *resumptions,
       ULONG *suspensions, ULONG *solicited_preemptions,
       ULONG *interrupt_preemptions, ULONG *priority_inversions,
       ULONG *time_slices, ULONG *relinquishes, ULONG *timeouts,
       ULONG *wait_aborts, ULONG *non_idle_returns,
       ULONG *idle_returns);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich wątków w systemie.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_THREAD_ENABLE_PERFORMANCE_INFO** zdefiniowanych w celu zwrócenia informacji o wydajności przez tę usługę.

### <a name="parameters"></a>Parametry

- **wznawiania**: wskaźnik do miejsca docelowego dla łącznej liczby wznowień wątków.
- **zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń wątku.
- **solicited_preemptions**: wskaźnik do miejsca docelowego dla łącznej liczby zastępujący wątków w wyniku wątku wywołującego usługę interfejsu API ThreadX.
- **interrupt_preemptions**: wskaźnik do miejsca docelowego dla łącznej liczby przeniesień wątków w wyniku przetwarzania przerwań.
- **priority_inversions**: wskaźnik do miejsca docelowego dla łącznej liczby niewersji priorytetu wątku.
- **time_slices**: wskaźnik do miejsca docelowego dla łącznej liczby wycinków czasu wątku.
- **zwalnia**: wskaźnik do miejsca docelowego dla łącznej liczby wyniesień wątków.
- **limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia wątku.
- **wait_aborts**: wskaźnik do miejsca docelowego dla łącznej liczby przerwań oczekiwania wątku. 
- **non_idle_returns**: wskaźnik do miejsca docelowego dla czasu, przez który wątek wraca do systemu, gdy inny wątek jest gotowy do wykonania. 
- **idle_returns**: wskaźnik do miejsca docelowego dla czasu, przez który wątek wraca do systemu, gdy żaden inny wątek nie jest gotowy do wykonania (bezczynny system).

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności systemu wątku.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
ULONG         resumptions;
ULONG         suspensions;
ULONG         solicited_preemptions;
ULONG         interrupt_preemptions;
ULONG         priority_inversions;
ULONG         time_slices;
ULONG         relinquishes;
ULONG         timeouts;
ULONG         wait_aborts;
ULONG         non_idle_returns;
ULONG         idle_returns;

/* Retrieve performance information on all previously created
   thread. */
status = tx_thread_performance_system_info_get(&resumptions,
                &suspensions,
                &solicited_preemptions, &interrupt_preemptions,
                &priority_inversions, &time_slices, &relinquishes,
                &timeouts, &wait_aborts, &non_idle_returns,
                &idle_returns);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

Zmiana zastępujący — próg wątku aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_preemption_change(TX_THREAD *thread_ptr,
                          UINT new_threshold, UINT *old_threshold);
```
### <a name="description"></a>Opis

Ta usługa zmienia próg przekroczenia określonego wątku. Próg zastępujący uniemożliwia przestawianie określonego wątku przez wątki równe lub mniejsze od wartości progowej przekroczenia.

> [!IMPORTANT]
> Użycie wartości progowej przekroczenia powoduje wyłączenie wycinka czasu dla określonego wątku.

### <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do wcześniej utworzonego wątku aplikacji.
- **new_threshold**: nowy przekroczenie — poziom priorytetu progu (od 0 do (TX_MAX_PRIORITIES-1)).
- **old_threshold**: wskaźnik do lokalizacji, aby przywrócić poprzedni próg zastępujący.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne przekroczenie — zmiana progowa.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- **TX_THRESH_ERROR**: (0X18) określony nowy próg przechodzenia nie jest prawidłowym priorytetem wątku (wartość inna niż (od 0 do (TX_MAX_PRIORITIES-1)) lub jest większa niż (niższy priorytet) niż bieżący priorytet wątku.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do poprzedniej lokalizacji magazynu preemptionthreshold.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```c
TX_THREAD     my_thread;
UINT          my_old_threshold;
UINT          status;

/* Disable all preemption of the specified thread. The
   current preemption-threshold is returned in
   "my_old_threshold". Assume that "my_thread" has
   already been created. */
status = tx_thread_preemption_change(&my_thread,
                             0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
   non-preemptable by another thread. Note that ISRs are
   not prevented by preemption disabling. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_priority_change"></a>tx_thread_priority_change

Zmień priorytet wątku aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_priority_change(TX_THREAD *thread_ptr,
                          UINT new_priority, UINT *old_priority);
```
### <a name="description"></a>Opis

Ta usługa zmienia priorytet określonego wątku. Prawidłowy zakres priorytetów należy do zakresu od 0 do (TX_MAX_PRIORITES-1), gdzie 0 oznacza najwyższy poziom priorytetu.

> [!IMPORTANT]
> Próg przekroczenia określonego wątku jest automatycznie ustawiany na nowy priorytet. W przypadku pożądanego nowego progu należy użyć usługi **tx_thread_preemption_change** po tym wywołaniu.

### <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do wcześniej utworzonego wątku aplikacji.
- **new_priority**: nowy poziom priorytetu wątku (od 0 do (TX_MAX_PRIORITIES-1)).
- **old_priority**: wskaźnik do lokalizacji, aby przywrócić poprzedni priorytet wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna zmiana priorytetu.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- TX_PRIORITY_ERROR: (0x0F) określony nowy priorytet jest nieprawidłowy (wartość inna niż (od 0 do (TX_MAX_PRIORITIES-1)).
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do lokalizacji magazynu o poprzednim priorytecie.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_THREAD     my_thread;
UINT          my_old_priority;
UINT          status;

/* Change the thread represented by "my_thread" to priority
   0. */
status = tx_thread_priority_change(&my_thread,
                            0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
   now at the highest priority level in the system. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_relinquish"></a>tx_thread_relinquish

Zwalnianie kontroli do innych wątków aplikacji

### <a name="prototype"></a>Prototype

```C
VOID tx_thread_relinquish(VOID);
```
### <a name="description"></a>Opis

Ta usługa zrzeka kontrolę procesora do innych gotowych do uruchomienia wątków o tym samym lub wyższym priorytecie.

> [!IMPORTANT]
> Oprócz przepisywania kontroli do wątków o takim samym priorytecie, ta usługa również zwalnia z wykonywania kontroli nad wątkiem o najwyższym priorytecie z powodu ustawienia progu przekroczenia bieżącego wątku.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

Brak

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
ULONG run_counter_1 =  0;
ULONG run_counter_2 =  0;

/* Example of two threads relinquishing control to
   each other in an infinite loop. Assume that
   both of these threads are ready and have the same
   priority. The run counters will always stay within one
   of each other. */

VOID  my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {

        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_reset"></a>tx_thread_reset

Zresetuj wątek

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Opis

Ta usługa resetuje określony wątek do wykonania w punkcie wejścia zdefiniowanym podczas tworzenia wątku. Aby można było zresetować wątek, musi on być w stanie **TX_COMPLETED** lub **TX_TERMINATED**

> [!IMPORTANT]
> Wątek należy wznowić, aby można było wykonać operację ponownie.

### <a name="parameters"></a>Parametry 

- **thread_ptr**: wskaźnik do wcześniej utworzonego wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne zresetowanie wątku.
- **TX_NOT_DONE**: (0X20) określony wątek nie jest w stanie TX_COMPLETED lub TX_TERMINATED.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
TX_THREAD     my_thread;

/* Reset the previously created thread "my_thread." */
status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_resume"></a>tx_thread_resume

Wznów zawieszony wątek aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Opis

Ta usługa wznawia lub przygotowuje do wykonania wątek, który został wcześniej zawieszony przez wywołanie ***tx_thread_suspend*** . Ponadto ta usługa wznawia wątki, które zostały utworzone bez automatycznego uruchamiania.

### <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do zawieszonego wątku aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne wznowienie wątku.
- **TX_SUSPEND_LIFTED**: (0X19) poprzednio ustawione opóźnione zawieszenie zostało zniesione.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- **TX_RESUME_ERROR**: (0X12) określony wątek nie jest wstrzymany lub został wcześniej zawieszony przez usługę inną niż **_tx_thread_suspend_**.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_THREAD     my_thread;
UINT          status;

/* Resume the thread represented by "my_thread". */
status =  tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   now ready to execute. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_sleep"></a>tx_thread_sleep

Zawieś bieżący wątek przez określony czas

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_sleep(ULONG timer_ticks);
```
### <a name="description"></a>Opis

Ta usługa powoduje zawieszenie wątku wywołującego dla określonej liczby taktów czasomierza. Czas fizyczny skojarzony z cyklem czasomierza jest specyficzny dla aplikacji. Ta usługa może być wywoływana tylko z wątku aplikacji.

### <a name="parameters"></a>Parametry

- **timer_ticks**: liczba cykli czasomierza wstrzymania wątku aplikacji wywołującej, od 0 do 0xffffffff. Jeśli określono wartość 0, usługa wraca natychmiast.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) powodzenie uśpienia wątku.
- **TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.
- **TX_CALLER_ERROR**: (0x13) wywołana z niewątku.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
UINT status;

/* Make the calling thread sleep for 100
   timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
   application thread slept for the specified number of
   timer-ticks. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_smp_core_exclude"></a>tx_thread_smp_core_exclude

Wyklucz wykonywanie wątku na zestawie rdzeni

### <a name="prototype"></a>Prototype

```C
UINT  tx_thread_smp_core_exclude(TX_THREAD *thread_ptr,
                          ULONG exclusion_map);
```
### <a name="description"></a>Opis

Ta funkcja wyklucza określony wątek z wykonywania na rdzeniach określonych w mapie bitowej o nazwie "*exclusion_map*". Każdy bit w "*exclusion_map*" reprezentuje rdzeń (bit 0 reprezentuje rdzeń 0 itd.). Jeśli bit jest ustawiony, odpowiadający rdzeń jest wykluczony z wykonywania określonego wątku.

> [!IMPORTANT]
> Użycie wykluczenia procesora może spowodować dodatkowe przetwarzanie w wątku do podstawowej logiki mapowania, aby znaleźć optymalne dopasowanie. To przetwarzanie jest ograniczone przez liczbę gotowych wątków.

### <a name="parameters"></a>Parametry 

- **thread_ptr**: wskaźnik do wątku, aby zmienić wykluczenia rdzenia.
- **exclusion_map**: Mapa bitowa, gdzie bit Sit wskazuje, że rdzeń jest wykluczony. Dostarczenie wartości 0 powoduje, że wątek będzie wykonywany na dowolnym rdzeń (domyślnie).

### <a name="return-values"></a>Wartości zwrócone

- TX_SUCCESS: (0x00) pomyślne wykluczenie rdzenia.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, procedury ISR, wątki i czasomierze

### <a name="example"></a>Przykład

```C
/* Exclude core 0 for "Thread 0". */
tx_thread_smp_core_exclude(&thread_0, 0x01);
```

### <a name="see-also"></a>Zobacz też

- tx_thread_smp_core_exclude_get
- tx_thread_smp_core_get

## <a name="tx_thread_smp_core_exclude_get"></a>tx_thread_smp_core_exclude_get

Pobiera wykluczenie rdzenia bieżącego wątku

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a>Opis

Ta funkcja zwraca bieżącą listę wykluczeń rdzeni.

### <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do wątku, z którego ma zostać pobrany rdzeń wykluczenia.
- **exclusion_map_ptr**: miejsce docelowe dla bieżącej mapy bitowej wykluczeń podstawowych.

### <a name="return-values"></a>Wartości zwrócone

- TX_SUCCESS: (0x00) pomyślne pobranie wykluczenia rdzenia wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik docelowy wykluczenia.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, procedury ISR, wątki i czasomierze

### <a name="example"></a>Przykład

```C
ULONGexcluded_cores;
/* Retrieve the core exclusion for "Thread 0". */
tx_thread_smp_core_exclude_get(&thread_0, &excluded_cores);
```

### <a name="see-also"></a>Zobacz też

- tx_thread_smp_core_exclude
- tx_thread_smp_core_get

## <a name="tx_thread_smp_core_get"></a>tx_thread_smp_core_get

Pobierz aktualnie wykonywane rdzeń obiektu wywołującego

### <a name="prototype"></a>Prototype

```C
UINT  tx_thread_smp_core_get(void);
```
### <a name="description"></a>Opis

Ta funkcja zwraca podstawowy identyfikator rdzenia wykonującego tę usługę.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

- core_id: Identyfikator aktualnie wykonywanej klasy rdzeń (od 0 do TX_THREAD_SMP_MAX_CORES-1)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, procedury ISR, wątki i czasomierze

### <a name="example"></a>Przykład

```C
UINTcore;
/* Pickup the currently executing core. */
core = tx_thread_smp_core_get();

/* At this point, “core” contains the executing core ID. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_smp_core_exclude
- tx_thread_smp_core_exclude_get

## <a name="tx_thread_stack_error_notify"></a>tx_thread_stack_error_notify

Wywołanie zwrotne powiadomienia o błędzie stosu rejestracji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia do obsługi błędów stosu wątków. Gdy ThreadX SMP wykryje błąd stosu wątku podczas wykonywania, wywoła tę funkcję powiadamiania w celu przetworzenia błędu. Przetwarzanie błędu jest całkowicie zdefiniowane przez aplikację. Wszystkie elementy od zawieszenia naruszenia wątku w celu zresetowania całego systemu mogą zostać wykonane.

> [!IMPORTANT]
> Biblioteka SMP ThreadX musi być skompilowana przy użyciu **TX_ENABLE_STACK_CHECKING** zdefiniowanej w celu zwrócenia informacji o wydajności przez tę usługę.

### <a name="parameters"></a>Parametry

- **error_handler**: wskaźnik do funkcji obsługi błędów stosu aplikacji. Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne zresetowanie wątku.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX SMP
   so that thread stack errors can be handled by the application. */
status =  tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_suspend"></a>tx_thread_suspend

Wstrzymywanie wątku aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Opis

Ta usługa wstrzymuje określony wątek aplikacji. Wątek może wywołać tę usługę, aby zawiesić się.

> [!IMPORTANT]
> Jeśli określony wątek został już zawieszony z innego powodu, to zawieszenie jest przechowywane wewnętrznie do momentu zniesienia wcześniejszego zawieszenia. W takim przypadku wykonywane jest niewarunkowe zawieszenie określonego wątku. Dalsze niewarunkowe żądania zawieszenia nie mają żadnego wpływu.

Po wstrzymaniu wątek musi zostać wznowiony przez ***tx_thread_resume*** , aby wykonać operację ponownie.

## <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do wątku aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne wstrzymanie wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- **TX_SUSPEND_ERROR**: (0X14) określony wątek jest w stanie przerwana lub ukończona.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_THREAD     my_thread;
UINT          status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   unconditionally suspended. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_terminate"></a>tx_thread_terminate

Przerywa wątek aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Opis

Ta usługa przerywa określony wątek aplikacji niezależnie od tego, czy wątek jest wstrzymany, czy nie. Wątek może wywoływać tę usługę, aby zakończyć działanie.

> [!IMPORTANT]
> Po zakończeniu należy zresetować wątek, aby można było wykonać operację ponownie.

> [!WARNING]
> Jest on odpowiedzialny za zapewnienie, że wątek jest w stanie odpowiednim do zakończenia. Na przykład wątek nie powinien być zakończony podczas krytycznego przetwarzania aplikacji lub wewnątrz innych składników oprogramowania pośredniczącego, w którym może to spowodować, że przetwarzanie jest nieznane.

### <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do wątku aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne zakończenie wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_THREAD     my_thread;
UINT          status;

/* Terminate the thread represented by "my_thread". */
status =  tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
   and cannot execute again until it is reset. */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

Zmienia czas wycinka wątku aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_time_slice_change(TX_THREAD *thread_ptr,
                          ULONG new_time_slice, ULONG *old_time_slice);
```
### <a name="description"></a>Opis

Ta usługa zmienia wycinek czasu określonego wątku aplikacji. Wybranie wycinka czasu dla wątku polega na tym, że nie będzie działać więcej niż określona liczba taktów czasomierza, zanim inne wątki o tych samych lub wyższych priorytetach mają szansę na wykonanie.

> [!IMPORTANT]
> Użycie wartości progowej przekroczenia powoduje wyłączenie wycinka czasu dla określonego wątku.

### <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do wątku aplikacji.
- **new_time_slice**: Nowa wartość wycinka czasu. Wartości prawne obejmują TX_NO_TIME_SLICE i wartości liczbowe z przedziału od 1 do 0xFFFFFFFF.
- **old_time_slice**: wskaźnik do lokalizacji przechowywania poprzedniej wartości timeslice określonego wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) czas pomyślnego odtworzenia wycinka.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do poprzedniej lokalizacji przechowywania wycinków czasu.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_THREAD     my_thread;
ULONG         my_old_time_slice;
UINT          status;

/* Change the time-slice of the thread associated with
   "my_thread" to 20. This will mean that "my_thread"
   can only run for 20 timer-ticks consecutively before
   other threads of equal or higher priority get a chance
   to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
                             &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
   has been changed to 20 and the previous time-slice is
   in "my_old_time_slice." */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_wait_abort

## <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

Przerwij zawieszenie określonego wątku

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Opis

Ta usługa przerywa pracę w stanie uśpienia lub dowolnego innego obiektu zawieszania określonego wątku. W przypadku przerwania oczekiwania zostanie zwrócona wartość TX_WAIT_ABORTED z usługi, w której wątek oczekiwał.

> [!IMPORTANT]
> Ta usługa nie zwalnia jawnego zawieszenia wykonywanego przez usługę tx_thread_suspend.

### <a name="parameters"></a>Parametry

- **thread_ptr**: wskaźnik do wcześniej utworzonego wątku aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne przerwanie oczekiwania wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- **TX_WAIT_ABORT_ERROR**: (0X1b) określony wątek nie jest w stanie oczekiwania.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Tak

### <a name="example"></a>Przykład

```C
TX_THREAD     my_thread;
UINT          status;

/* Abort the suspension condition of "my_thread." */
status =  tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
   again, with a return value showing its suspension
   was aborted (TX_WAIT_ABORTED). */
```
### <a name="see-also"></a>Zobacz też

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change

## <a name="tx_time_get"></a>tx_time_get

Pobiera bieżącą godzinę

### <a name="prototype"></a>Prototype

```C
ULONG tx_time_get(VOID);
```
### <a name="description"></a>Opis

Ta usługa zwraca zawartość wewnętrznego zegara systemowego. Każdy timertick zwiększa wewnętrzny zegar systemowy o jeden. Zegar systemowy jest ustawiany na zero podczas inicjowania i można go zmienić na określoną wartość przez ***tx_time_set*** usługi.

> [!IMPORTANT]
> Rzeczywisty czas, jaki jest reprezentowany przez cykl czasomierza, jest specyficzny dla aplikacji.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

- Takty zegara systemowego: wartość wewnętrznego, wolnego, uruchomionego zegara systemowego.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time =  tx_time_get();

/* Current time now contains a copy of the internal system
   clock. */
```
### <a name="see-also"></a>Zobacz też

- tx_time_set

## <a name="tx_time_set"></a>tx_time_set

Ustawia bieżącą godzinę

### <a name="prototype"></a>Prototype

```C
VOID tx_time_set(ULONG new_time);
```
### <a name="description"></a>Opis

Ta usługa ustawia wewnętrzny zegar systemowy do określonej wartości. Każdy czasomierz czasu wydłuża zegar systemu wewnętrznego o jeden.

> [!IMPORTANT]
> Rzeczywisty czas, jaki jest reprezentowany przez cykl czasomierza, jest specyficzny dla aplikacji.

### <a name="parameters"></a>Parametry

- **new_time**: nowy czas do umieszczenia w zegarze systemowym, wartości prawne mieszczą się w zakresie od 0 do 0xffffffff.

### <a name="return-values"></a>Wartości zwrócone

Brak

### <a name="allowed-from"></a>Dozwolone z

Wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
   interrupt. */
```
### <a name="see-also"></a>Zobacz też

- tx_time_get

## <a name="tx_timer_activate"></a>tx_timer_activate

Aktywuj czasomierz aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```
### <a name="description"></a>Opis

Ta usługa aktywuje określony czasomierz aplikacji. Procedury wygasania czasomierzy, które wygasają w tym samym czasie, są wykonywane w kolejności, w jakiej zostały aktywowane.

> [!NOTE]
> Aby można było ponownie aktywować czasomierz, który wygasł, należy zresetować za pomocą **tx_timer_change** .

### <a name="parameters"></a>Parametry

- **timer_ptr**: wskaźnik do wcześniej utworzonego czasomierza aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna aktywacja czasomierza aplikacji.
- **TX_TIMER_ERROR**: (0X15) Nieprawidłowy wskaźnik czasomierza aplikacji.
- Czasomierz **TX_ACTIVATE_ERROR**: (0x17) był już aktywny lub jest już wygasłym czasomierzem.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_TIMER     my_timer;
UINT         status;

/* Activate an application timer. Assume that the
   application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now active. */
```
### <a name="see-also"></a>Zobacz też

- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_change"></a>tx_timer_change

Zmień czasomierz aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_change(TX_TIMER *timer_ptr,
                          ULONG initial_ticks, ULONG reschedule_ticks);
```
### <a name="description"></a>Opis

Ta usługa zmienia charakterystykę wygaśnięcia określonego czasomierza aplikacji. Czasomierz należy dezaktywować przed wywołaniem tej usługi.

> [!IMPORTANT]
> Przed ponownym uruchomieniem czasomierza wymagane jest wywołanie usługi **tx_timer_activate** .

### <a name="parameters"></a>Parametry

- **timer_ptr**: wskaźnik do bloku sterowania czasomierzem.
- **initial_ticks**: określa początkową liczbę taktów dla wygaśnięcia czasomierza. Wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.
- **reschedule_ticks**: określa liczbę taktów dla wszystkich wygasających czasomierzy po pierwszej. Wartość zerowa dla tego parametru powoduje, że czasomierz ma czasomierz jednorazowy. W przeciwnym razie dla okresowych czasomierzy wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.

   > [!NOTE]
   > Aby można było ponownie aktywować czasomierz, który wygasł, należy zresetować za pomocą **tx_timer_change** .

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślnie przeprowadzono zmianę czasomierza aplikacji.
- TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.
- TX_TICK_ERROR: (0x16) Nieprawidłowa wartość (zero) dostarczona dla początkowych taktów.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_TIMER         my_timer;
UINT             status;

/* Change a previously created and now deactivated timer
   to expire every 50 timer ticks, including the initial
   expiration. */
status =  tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
   changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```
### <a name="see-also"></a>Zobacz też

- tx_timer_activate
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_create"></a>tx_timer_create

Utwórz czasomierz aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_create(TX_TIMER *timer_ptr, CHAR *name_ptr,
                          VOID (*expiration_function)(ULONG),
                          ULONG expiration_input, ULONG initial_ticks,
                          ULONG reschedule_ticks, UINT auto_activate)
```
### <a name="description"></a>Opis

Ta usługa tworzy czasomierz aplikacji z określoną funkcją wygaśnięcia i okresowo.

### <a name="parameters"></a>Parametry

- **timer_ptr**: wskaźnik do bloku sterowania czasomierzem
- **name_ptr**: wskaźnik do nazwy czasomierza.
- **expiration_function**: funkcja aplikacji do wywołania po wygaśnięciu czasomierza.
- **expiration_input**: dane wejściowe do przekazania do funkcji wygaśnięcia po wygaśnięciu czasomierza.
- **initial_ticks**: określa początkową liczbę taktów dla wygaśnięcia czasomierza. Wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.
- **reschedule_ticks**: określa liczbę taktów dla wszystkich wygasających czasomierzy po pierwszej. Wartość zerowa dla tego parametru powoduje, że czasomierz ma czasomierz jednorazowy. W przeciwnym razie dla okresowych czasomierzy wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.

   > [!NOTE]
   > Po wygaśnięciu czasomierza z jednym zrzutem należy zresetować go za pomocą tx_timer_change, zanim będzie można go ponownie aktywować.

- **Auto_Activate**: określa, czy czasomierz jest automatycznie uaktywniany podczas tworzenia. Jeśli ta wartość jest **TX_AUTO_ACTIVATE** (0x01), czasomierz jest aktywny. W przeciwnym razie, jeśli wybrano wartość **TX_NO_ACTIVATE** (0x00), czasomierz zostanie utworzony w stanie nieaktywnym. W takim przypadku kolejne wywołanie usługi **_tx_timer_activate_** jest niezbędne do uruchomienia czasomierza w rzeczywistości.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne utworzenie czasomierza aplikacji.
- TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji. Wskaźnik ma wartość NULL lub czasomierz został już utworzony.
- TX_TICK_ERROR: (0x16) Nieprawidłowa wartość (zero) dostarczona dla początkowych taktów.
- TX_ACTIVATE_ERROR: (0x17) wybrano nieprawidłową aktywację.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_TIMER     my_timer;
UINT         status;

/* Create an application timer that executes
   "my_timer_function" after 100 ticks initially and then
   after every 25 ticks. This timer is specified to start
   immediately! */
status =  tx_timer_create(&my_timer,"my_timer_name",
                my_timer_function, 0x1234, 100, 25,
                TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
   be called 100 timer ticks later and then called every
   25 timer ticks. Note that the value 0x1234 is passed to
   my_timer_function every time it is called. */
```
### <a name="see-also"></a>Zobacz też

- tx_timer_activate
- tx_timer_change
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_deactivate"></a>tx_timer_deactivate

Dezaktywuj czasomierz aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Opis

Ta usługa dezaktywuje określony czasomierz aplikacji. Jeśli czasomierz został już zdezaktywowany, ta usługa nie ma wpływu.

### <a name="parameters"></a>Parametry 

- **timer_ptr**: wskaźnik do wcześniej utworzonego czasomierza aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0x00) pomyślna dezaktywacja czasomierza aplikacji.
- TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_TIMER     my_timer;
UINT         status;

/* Deactivate an application timer. Assume that the
   application timer has already been created. */
status =  tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now deactivated. */
```
### <a name="see-also"></a>Zobacz też

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_delete"></a>tx_timer_delete

Usuń czasomierz aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określony czasomierz aplikacji.

> [!IMPORTANT]
> Jest to odpowiedzialność aplikacji, aby uniemożliwić korzystanie z usuniętego czasomierza.

### <a name="parameters"></a>Parametry 

- **timer_ptr**: wskaźnik do wcześniej utworzonego czasomierza aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne usunięcie czasomierza aplikacji.
- TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```c
TX_TIMER     my_timer;
UINT         status;

/* Delete application timer. Assume that the application
   timer has already been created. */
status =  tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   deleted. */
```
### <a name="see-also"></a>Zobacz też

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_info_get"></a>tx_timer_info_get

Pobierz informacje o czasomierzu aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_info_get(TX_TIMER *timer_ptr, CHAR **name,
                          UINT *active, ULONG *remaining_ticks,
                          ULONG *reschedule_ticks,
                          TX_TIMER **next_timer)
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o określonym czasomierzu aplikacji.

### <a name="parameters"></a>Parametry

- **timer_ptr**: wskaźnik do wcześniej utworzonego czasomierza aplikacji.
- **name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy czasomierza.
- **aktywny**: wskaźnik do miejsca docelowego dla aktywnego wskaźnika czasomierza. Jeśli czasomierz jest nieaktywny lub ta usługa jest wywoływana z samego czasomierza, zwracana jest wartość TX_FALSE. W przeciwnym razie, jeśli czasomierz jest aktywny, zwracana jest wartość TX_TRUE.
- **remaining_ticks**: wskaźnik do miejsca docelowego dla liczby cykli czasomierza pozostawionych przed wygaśnięciem czasomierza.
- **reschedule_ticks**: wskaźnik do miejsca docelowego dla liczby taktów czasomierza, który zostanie użyty do automatycznego ponownego zaplanowania tego czasomierza. Jeśli wartość jest równa zero, czasomierz jest jednorazowy i nie zostanie ponownie zaplanowany.
- **next_timer**: wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego czasomierza aplikacji.

> [!NOTE]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobranie informacji czasomierza.
- TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="preemption-possible"></a>Możliwe przeprowadzenie

Nie

### <a name="example"></a>Przykład

```C
TX_TIMER     my_timer;
CHAR         *name;
UINT         active;
ULONG        remaining_ticks;
ULONG        reschedule_ticks;
TX_TIMER     *next_timer;
UINT         status;

/* Retrieve information about the previously created
   application timer "my_timer." */
status =  tx_timer_info_get(&my_timer, &name,
                          &active,&remaining_ticks,
                &reschedule_ticks,
                         &next_timer);

/* If status equals TX_SUCCESS, the information requested is
   valid. */
```
### <a name="see-also"></a>Zobacz też

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get 

Pobierz informacje o wydajności czasomierza

### <a name="prototype"></a>Prototype

```C
UINT  tx_timer_performance_info_get(TX_TIMER *timer_ptr,
        ULONG *activates, ULONG *reactivates,
        ULONG *deactivates, ULONG *expirations,
        ULONG *expiration_adjusts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności dotyczące określonego czasomierza aplikacji.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_TIMER_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry 

- **timer_ptr**: wskaźnik do wcześniej utworzonego czasomierza.
- **aktywuje**: wskaźnik do miejsca docelowego dla liczby żądań aktywacji wykonanych dla tego czasomierza.
- **reactivates**: wskaźnik do miejsca docelowego dla liczby automatycznych ponownych aktywacji wykonanych na tym cyklicznym czasomierzu.
- **dezaktywuje**: wskaźnik do miejsca docelowego dla liczby żądań dezaktywacji wykonanych dla tego czasomierza.
- **wygaśnięcia**: wskaźnik do miejsca docelowego dla liczby wygaśnięć tego czasomierza.
- **expiration_adjusts**: wskaźnik do miejsca docelowego dla liczby wewnętrznych korekt wygaśnięcia wykonanych dla tego czasomierza. Te korekty są wykonywane w ramach przetwarzania przerwań czasomierza dla czasomierzy, które są większe niż domyślny rozmiar listy czasomierza (domyślnie czasomierze o wygasaniu większym niż 32 taktów).

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności czasomierza.
- **TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik czasomierza.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
TX_TIMER     my_timer;
ULONG        activates;
ULONG        reactivates;
ULONG        deactivates;
ULONG        expirations;
ULONG        expiration_adjusts;

/* Retrieve performance information on the previously created
   timer.  */
status =  tx_timer_performance_info_get(&my_timer, &activates,
                &reactivates,&deactivates, &expirations,
                &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get 

Pobierz informacje o wydajności systemu czasomierza

### <a name="prototype"></a>Prototype

```C
UINT  tx_timer_performance_system_info_get(ULONG *activates,
        ULONG *reactivates, ULONG *deactivates,
        ULONG *expirations, ULONG *expiration_adjusts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich czasomierzy aplikacji w systemie.

> [!IMPORTANT]
> Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_TIMER_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.

### <a name="parameters"></a>Parametry

- **aktywuje**: wskaźnik do miejsca docelowego dla łącznej liczby żądań aktywacji wykonanych na wszystkich czasomierzach.
- **reactivates**: wskaźnik do miejsca docelowego dla łącznej liczby automatycznych ponownych aktywacji wykonanych na wszystkich okresowych czasomierzach.
- **dezaktywuje**: wskaźnik do miejsca docelowego dla łącznej liczby żądań dezaktywacji wykonanych na wszystkich czasomierzach.
- **wygaśnięcia**: wskaźnik do miejsca docelowego dla łącznej liczby wygaśnięć dla wszystkich czasomierzy.
- **expiration_adjusts**: wskaźnik do miejsca docelowego dla łącznej liczby wewnętrznych korekt wygaśnięcia wykonanych na wszystkich czasomierzach. Te korekty są wykonywane w ramach przetwarzania przerwań czasomierza dla czasomierzy, które są większe niż domyślny rozmiar listy czasomierza (domyślnie czasomierze o wygasaniu większym niż 32 taktów).

> [!IMPORTANT]
> Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS**: (0X00) pomyślne uzyskanie czasomierza wydajności systemu.
- **TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki, czasomierze i procedury ISR

### <a name="example"></a>Przykład

```C
ULONG     activates;
ULONG     reactivates;
ULONG     deactivates;
ULONG     expirations;
ULONG     expiration_adjusts;

/* Retrieve performance information on all previously created
   timers.  */
status =  tx_timer_performance_system_info_get(&activates,
                &reactivates, &deactivates, &expirations,
                &expiration_adjusts);
/* If status is TX_SUCCESS the performance information was
   successfully retrieved. */
```
### <a name="see-also"></a>Zobacz też

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get

## <a name="tx_timer_smp_core_exclude"></a>tx_timer_smp_core_exclude

Wyklucz wykonywanie czasomierza na zestawie rdzeni

### <a name="prototype"></a>Prototype

```C
UINT  tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);
```
### <a name="description"></a>Opis

Ta funkcja wyklucza określony czasomierz z wykonywania na rdzeniach określonych w mapie bitowej o nazwie "*exclusion_map*". Każdy bit w "*exclusion_map*" reprezentuje rdzeń (bit 0 reprezentuje rdzeń 0 itd.). Jeśli bit jest ustawiony, odpowiadający rdzeń jest wykluczony z wykonywania określonego czasomierza.

> [!IMPORTANT]
> Użycie wykluczenia procesora może spowodować dodatkowe przetwarzanie w wątku do podstawowej logiki mapowania, aby znaleźć optymalne dopasowanie. To przetwarzanie jest ograniczone przez liczbę gotowych wątków.

### <a name="parameters"></a>Parametry

- **timer_ptr**: wskaźnik do czasomierza, aby zmienić wykluczenia rdzenia.
- **exclusion_map**: Mapa bitowa, gdzie bit Sit wskazuje, że rdzeń jest wykluczony. Dostarczenie wartości 0 powoduje, że czasomierz będzie wykonywany na dowolnym rdzeniu (domyślnie).

### <a name="return-values"></a>Wartości zwrócone

- Wykluczenie rdzenia **TX_SUCCESS** (0x00).
- **TX_TIMER_ERROR** (0X0E) Nieprawidłowy wskaźnik czasomierza.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, procedury ISR, wątki i czasomierze

### <a name="example"></a>Przykład

```C
/* Exclude core 0 for "Timer 0". */
tx_timer_smp_core_exclude(&timer_0, 0x01);
```

### <a name="see-also"></a>Zobacz też

- tx_timer_smp_core_exclude_get

## <a name="tx_timer_smp_core_exclude_get"></a>tx_timer_smp_core_exclude_get

Pobiera bieżące wykluczenie rdzenia czasomierza

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a>Opis

Ta funkcja zwraca bieżącą listę wykluczeń rdzeni.

### <a name="parameters"></a>Parametry

- **timer_ptr**: wskaźnik do czasomierza, z którego ma zostać pobrane podstawowe wykluczenie.
- **exclusion_map_ptr**: miejsce docelowe dla bieżącej mapy bitowej wykluczeń podstawowych.

### <a name="return-values"></a>Wartości zwrócone

- TX_SUCCESS: (0x00) pomyślne pobranie wykluczenia rdzenia czasomierza.
- TX_TIMER_ERROR: (0x0E) Nieprawidłowy wskaźnik czasomierza.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik docelowy wykluczenia.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, procedury ISR, wątki i czasomierze

### <a name="example"></a>Przykład

```C
ULONGexcluded_cores;

/* Retrieve the core exclusion for "Timer 0". */
tx_timer_smp_core_exclude_get(&timer_0,&excluded_cores);
```
### <a name="see-also"></a>Zobacz też

- tx_timer_smp_core_exclude