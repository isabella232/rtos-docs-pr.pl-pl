---
title: Rozdział 4 — Opis Azure RTOS SMP ThreadX
description: Ten rozdział zawiera opis wszystkich usług SMP Azure RTOS ThreadX w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 71b964963968b0ec6fa3c8cc70cc46576e8ff33e2cfad0315182afe1f1afcc5b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802162"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-smp-services"></a>Rozdział 4 — Opis Azure RTOS SMP ThreadX

Ten rozdział zawiera opis wszystkich usług SMP Azure RTOS ThreadX w kolejności alfabetycznej. Ich nazwy zostały zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem. W sekcji "Wartości zwracane" w poniższych  opisach wartości  z poGRUBIENIEM nie mają wpływu na wartość zdefiniowaną przez TX_DISABLE_ERROR_CHECKING używaną do wyłączania sprawdzania błędów interfejsu API; Wartość jest całkowicie wyłączona, natomiast wartości wyświetlane w wartościach innych niżbold. Ponadto "**Tak**" wymieniony w nagłówku **"Możliwe** wywłaszcz" wskazuje, że wywołanie usługi może wznowić wątek o wyższym priorytecie, w ten sposób wywłaszając wątek wywołujący.

- **tx_block_allocate:** *przydzielanie bloku pamięci o stałym rozmiarze* 
- **tx_block_pool_create:** Tworzenie *puli bloków pamięci o stałym rozmiarze* 
- **tx_block_pool_delete:** Usuwanie *puli bloków pamięci* 
- **tx_block_pool_info_get:** Pobieranie *informacji o puli bloków* 
- **tx_block_pool_performance_info_get:** Uzyskiwanie *informacji o wydajności puli bloków* 
- **tx_block_pool_performance_system_info_get:** Uzyskiwanie *informacji o wydajności systemu puli bloków* 
- **tx_block_pool_prioritize:** Określanie *priorytetów listy wstrzymania puli bloków* 
- **tx_block_release:** *zwolnij blok pamięci o stałym rozmiarze*
- **tx_byte_allocate:** *przydzielanie bajtów pamięci* 
- **tx_byte_pool_create:** tworzenie *puli pamięci bajtów* 
- **tx_byte_pool_delete:** Usuwanie *puli bajtów pamięci* 
- **tx_byte_pool_info_get:** pobieranie *informacji o puli bajtów* 
- **tx_byte_pool_performance_info_get:** uzyskiwanie *informacji o wydajności puli bajtów* 
- **tx_byte_pool_performance_system_info_get:** uzyskiwanie *informacji o wydajności systemu puli bajtów* 
- **tx_byte_pool_prioritize:** Określanie *priorytetów listy wstrzymania puli bajtów* 
- **tx_byte_release:** *Zwolnij bajty z powrotem do puli pamięci* 
- **tx_event_flags_create:** *tworzenie grupy flag zdarzeń* 
- **tx_event_flags_delete:** Usuwanie *grupy flag zdarzeń* 
- **tx_event_flags_get:** pobierz *flagi zdarzeń z grupy flag zdarzeń* 
- **tx_event_flags_info_get:** pobieranie *informacji o grupie flag zdarzeń* 
- **tx_event_flags_performance_info_get:** Uzyskiwanie *informacji o wydajności grupy flag zdarzeń* 
- **tx_event_flags_performance_system_info_get:** pobieranie *informacji o systemie wydajności* 
- **tx_event_flags_set:** ustaw *flagi zdarzeń w grupie flag zdarzeń* 
- **tx_event_flags_set_notify:** *powiadamianie aplikacji o ustawionych flagach zdarzeń*
- **tx_interrupt_control:** Włączanie *i wyłączanie przerwań* 
- **tx_mutex_create:** *Tworzenie wzajemnego wykluczania mutex* 
- **tx_mutex_delete:** Usuwanie *wzajemnego wykluczania mutex* 
- **tx_mutex_get:** Uzyskiwanie *własności obiektu mutex* 
- **tx_mutex_info_get:** *pobieranie informacji o mutex* 
- **tx_mutex_performance_info_get:** Uzyskiwanie *informacji o wydajności obiektu mutex* 
- **tx_mutex_performance_system_info_get:** Uzyskiwanie *informacji o wydajności systemu mutex* 
- **tx_mutex_prioritize:** Określanie *priorytetów listy zawieszenia mutex* 
- **tx_mutex_put:** *Zwolnij własność obiektu mutex* 
- **tx_queue_create:** Tworzenie *kolejki komunikatów* 
- **tx_queue_delete:** Usuwanie *kolejki komunikatów* 
- **tx_queue_flush:** Puste *komunikaty w kolejce komunikatów* 
- **tx_queue_front_send:** Wysyłanie *komunikatu na przód kolejki* 
- **tx_queue_info_get:** pobieranie *informacji o kolejce* 
- **tx_queue_performance_info_get:** uzyskiwanie *informacji o wydajności kolejki* 
- **tx_queue_performance_system_info_get:** Uzyskiwanie *informacji o wydajności systemu kolejek*
- **tx_queue_prioritize:** Określanie *priorytetów listy wstrzymania kolejki* 
- **tx_queue_receive:** Uzyskiwanie *komunikatu z kolejki komunikatów* 
- **tx_queue_send:** Wysyłanie *komunikatu do kolejki komunikatów* 
- **tx_queue_send_notify:** *powiadamianie aplikacji o wysłaniu komunikatu do kolejki* 
- **tx_semaphore_ceiling_put:** *Umieść wystąpienie w zliczeniu semafora z limitem* 
- **tx_semaphore_create:** Tworzenie *zliczania semafora* 
- **tx_semaphore_delete:** Usuwanie *zliczania semafora* 
- **tx_semaphore_get:** *uzyskiwanie wystąpienia z zliczania semafora* 
- **tx_semaphore_info_get:** pobieranie *informacji o semaforze* 
- **tx_semaphore_performance_info_get:** Uzyskiwanie *informacji o wydajności semafora* 
- **tx_semaphore_performance_system_info_get:** Uzyskiwanie *informacji o wydajności systemu semaforów* 
- **tx_semaphore_prioritize:** Określanie *priorytetów listy zawieszenia semafora* 
- **tx_semaphore_put:** Umieść *wystąpienie w zliczeniu semafora* 
- **tx_semaphore_put_notify:** *powiadamianie aplikacji o zastosowaniu semafora* 
- **tx_thread_create:** Tworzenie *wątku aplikacji* 
- **tx_thread_delete:** Usuwanie *wątku aplikacji*
- **tx_thread_entry_exit_notify:** *Powiadom aplikację przy wejściu wątku i zakończeniu* 
- **tx_thread_identify:** *pobiera wskaźnik do aktualnie wykonywanego wątku* 
- **tx_thread_info_get:** pobieranie *informacji o wątku* 
- **tx_thread_performance_info_get:** *uzyskiwanie informacji o wydajności wątku* 
- **tx_thread_performance_system_info_get:** Uzyskiwanie *informacji o wydajności systemu wątków* 
- **tx_thread_preemption_change:** Zmiana *progu wywłaszczenia wątku aplikacji* 
- **tx_thread_priority_change:** *zmiana priorytetu wątku aplikacji* 
- **tx_thread_relinquish:** *Wywłaszczaj kontrolkę do innych wątków aplikacji* 
- **tx_thread_reset:** *Resetowanie wątku* 
- **tx_thread_resume:** *Wznawianie zawieszonego wątku aplikacji* 
- **tx_thread_sleep:** *Wstrzymywanie bieżącego wątku na określony czas* 
- **tx_thread_smp_core_exclude:** *Wykluczanie wykonywania wątków na zestawie rdzeni* 
- **tx_thread_smp_core_exclude_get:** pobiera *bieżące wykluczenie podstawowe wątku* 
- **tx_thread_smp_core_get:** *pobieranie aktualnie wykonywanego rdzenia wywołującego* 
- **tx_thread_stack_error_notify:** rejestrowanie *wywołania zwrotnego powiadomienia o błędzie stosu wątków* 
- **tx_thread_suspend:** *Wstrzymywanie wątku aplikacji*
- **tx_thread_terminate:** *kończy wątek aplikacji* 
- **tx_thread_time_slice_change:** *zmienia wycinek czasu wątku aplikacji* 
- **tx_thread_wait_abort:** przerwać *zawieszenie określonego wątku* 
- **tx_time_get:** pobiera *bieżący czas* 
- **tx_time_set:** ustawia *bieżący czas* 
- **tx_timer_activate:** *Aktywowanie czasomierza aplikacji* 
- **tx_timer_change:** Zmiana *czasomierza aplikacji* 
- **tx_timer_create:** Tworzenie *czasomierza aplikacji* 
- **tx_timer_deactivate:** *Dezaktywacja czasomierza aplikacji* 
- **tx_timer_delete:** Usuwanie *czasomierza aplikacji* 
- **tx_timer_info_get:** pobieranie *informacji o czasomierzu aplikacji* 
- **tx_timer_performance_info_get:** *uzyskiwanie informacji o wydajności czasomierza* 
- **tx_timer_performance_system_info_get:** *uzyskiwanie informacji o wydajności systemu czasomierza* 
- **tx_timer_smp_core_exclude:** *Wykluczanie wykonywania czasomierza na zestawie rdzeni* 
- **tx_timer_smp_core_exclude_get:** pobiera *bieżące wykluczenie podstawowe czasomierza*

## <a name="tx_block_allocate"></a>tx_block_allocate
Przydzielanie bloku pamięci o stałym rozmiarze

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

- **pool_ptr:** wskaźnik do wcześniej utworzonej puli bloków pamięci.
- **block_ptr:** wskaźnik do docelowego wskaźnika bloku. Po pomyślnej alokacji adres przydzielonego bloku pamięci jest umieszczany w miejscu, w którym wskazuje ten parametr.
- **wait_option:** definiuje sposób zachowania usługi w przypadku braku dostępnych bloków pamięci. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT:**(0x00000000)
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF)
    - wartość limitu czasu: (0x00000001 do 0xFFFFFFFE)  
    
    Wybranie TX_NO_WAIT powoduje natychmiastowy zwrot z tej usługi niezależnie od tego, czy została ona pomyślna, czy nie. Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z nie wątku; np. inicjalizacja, czasomierz lub ISR.

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony do momentu, aż blok pamięci będzie dostępny.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na blok pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna alokacja bloku pamięci.
- **TX_DELETED:**(0x01) Pula bloków pamięci została usunięta, gdy wątek został zawieszony.
- **TX_NO_MEMORY:**(0x10) Usługa nie mogła przydzielić bloku pamięci w określonym czasie oczekiwania.
- **TX_WAIT_ABORTED:**(0x1A) Zawieszenie zostało przerwane przez inny wątek, czasomierz lub isr.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do wskaźnika docelowego.
- TX_WAIT_ERROR: (0x04) Opcja oczekiwania inna niż TX_NO_WAIT została określona dla wywołania z nieprzeczytanego.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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
Tworzenie puli bloków pamięci o stałym rozmiarze

### <a name="prototype"></a>Prototype

```C
UINT tx_block_pool_create(TX_BLOCK_POOL *pool_ptr,
                          CHAR *name_ptr, ULONG block_size,
                          VOID *pool_start, ULONG pool_size);
```
### <a name="description"></a>Opis

Ta usługa tworzy pulę bloków pamięci o stałym rozmiarze. Określony obszar pamięci jest podzielony na jak najwięcej bloków pamięci o stałym rozmiarze przy użyciu formuły:    
**total blocks** = (**total bytes**) / (**block size** + sizeof(void *))

> [!IMPORTANT]
> Każdy blok pamięci zawiera jeden wskaźnik obciążenia, który jest niewidoczny dla użytkownika i jest reprezentowany przez "sizeof(void *)" w poprzedniej formule.

### <a name="parameters"></a>Parametry

- **pool_ptr:** Wskaźnik do bloku sterowania puli bloków pamięci.
- **name_ptr:** wskaźnik do nazwy puli bloków pamięci.
- **block_size:** liczba bajtów w każdym bloku pamięci.
- **pool_start:** początkowy adres puli bloków pamięci. Adres początkowy musi być wyrównany do rozmiaru typu danych ULONG.
- **pool_size:** łączna liczba bajtów dostępnych dla puli bloków pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne utworzenie puli bloków pamięci.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci. Wskaźnik ma wartość NULL lub pula jest już utworzona.
- TX_PTR_ERROR: (0x03) Nieprawidłowy adres początkowy puli.
- TX_SIZE_ERROR: (0x05) Rozmiar puli jest nieprawidłowy.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Usuwanie puli bloków pamięci

### <a name="prototype"></a>Prototype

```C
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określoną pulę blokowej pamięci. Wszystkie wątki wstrzymane w oczekiwaniu na blok pamięci z tej puli są wznawiane i TX_DELETED zwracany stan.

> [!IMPORTANT]
> Aplikacja odpowiada za zarządzanie obszarem pamięci skojarzonym z pulą, który jest dostępny po zakończeniu tej usługi. Ponadto aplikacja musi uniemożliwić korzystanie z usuniętej puli lub jej bloków pamięci.

### <a name="parameters"></a>Parametry

- **pool_ptr:** wskaźnik do wcześniej utworzonej puli bloków pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne usunięcie puli bloków pamięci.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o puli bloków

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

- **pool_ptr:** wskaźnik do wcześniej utworzonej puli bloków pamięci.
- **name**: Wskaźnik do miejsca docelowego dla wskaźnika do nazwy puli bloków.
- **dostępne:** wskaźnik do miejsca docelowego dla liczby dostępnych bloków w puli bloków.
- **total_blocks:** wskaźnik do miejsca docelowego dla łącznej liczby bloków w puli bloków.
- **first_suspended:** Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszenia tej puli bloków.
- **suspended_count:** Wskaźnik do miejsca docelowego dla liczby wątków aktualnie zawieszonych w tej puli bloków.
- **next_pool:** Wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej puli bloków.

> [!IMPORTANT]
> Dostarczenie parametru TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pobieranie informacji o puli bloków powiodło się.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

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

Uzyskiwanie informacji o wydajności puli bloków

### <a name="prototype"></a>Prototype

```c
UINT tx_block_pool_performance_info_get(TX_BLOCK_POOL *pool_ptr,
       ULONG *allocates, ULONG *releases,
       ULONG *suspensions, ULONG *timeouts));
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności określonej puli bloków pamięci.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o wydajności, biblioteka i aplikacja ThreadX SMP muszą **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** z definicją.

### <a name="parameters"></a>Parametry

- **pool_ptr:** wskaźnik do wcześniej utworzonej puli bloków pamięci.
- **allocates**: wskaźnik do miejsca docelowego dla liczby żądań alokacji wykonanych w tej puli.
- **releases:** wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.
- **suspensions**: wskaźnik do miejsca docelowego dla liczby zawieszenia alokacji wątku w tej puli.
- **limity czasu:** wskaźnik do miejsca docelowego dla liczby limitów czasu wstrzymania przydziału w tej puli.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności puli bloków.
- **TX_PTR_ERROR:**(0x03) Nieprawidłowy wskaźnik puli bloków.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

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

Uzyskiwanie informacji o wydajności systemu puli bloków

### <a name="prototype"></a>Prototype

```C
UINT tx_block_pool_performance_system_info_get(ULONG *allocates,
       ULONG *releases, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich pul bloków pamięci w aplikacji.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o wydajności, biblioteka i aplikacja ThreadX SMP muszą **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** z definicją.

### <a name="parameters"></a>Parametry

- **allocates**: wskaźnik do miejsca docelowego dla łącznej liczby żądań alokacji wykonanych we wszystkich pulach bloków.
- **releases:** wskaźnik do miejsca docelowego dla łącznej liczby żądań wydania wykonanych na wszystkich pulach bloków.
- **suspensions**:Wskaźnik do miejsca docelowego dla całkowitej liczby zawieszenia alokacji wątku we wszystkich pulach bloków.
- **limity czasu:** wskaźnik do miejsca docelowego dla całkowitej liczby limitów czasu wstrzymania przydziału we wszystkich pulach bloków.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności systemu puli bloków.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

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

Określanie priorytetów listy wstrzymania puli bloków

### <a name="prototype"></a>Prototype

```C
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wątek o najwyższym priorytecie zawieszony dla bloku pamięci w tej puli na początku listy zawieszenia. Wszystkie inne wątki pozostają w tej samej kolejności FIFO, w których zostały wstrzymane.

### <a name="parameters"></a>Parametry 

- **pool_ptr:** Wskaźnik do bloku sterowania puli bloków pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne określanie priorytetów puli bloków.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ta usługa zwalnia wcześniej przydzielony blok z powrotem do skojarzonej puli pamięci. Jeśli co najmniej jeden wątek jest zawieszony w oczekiwaniu na bloki pamięci z tej puli, pierwszy wątek jest zawieszony i wznawiany.

> [!IMPORTANT]
> Aplikacja musi uniemożliwić korzystanie z obszaru bloku pamięci po zwolnieniu go z powrotem do puli.

### <a name="parameters"></a>Parametry

- **block_ptr:** wskaźnik do wcześniej przydzielonego bloku pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne wydanie bloku pamięci.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do bloku pamięci.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Przydzielanie bajtów pamięci

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
> Wydajność tej usługi jest funkcją rozmiaru bloku i wielkości fragmentacji w puli. W związku z tym ta usługa nie powinna być używana podczas wykonywania wątków krytycznych dla czasu.

### <a name="parameters"></a>Parametry

- **pool_ptr:** wskaźnik do wcześniej utworzonej puli pamięci.
- **memory_ptr:** wskaźnik do docelowego wskaźnika pamięci. Po pomyślnej alokacji adres przydzielonego obszaru pamięci jest umieszczany w miejscu, na który wskazuje ten parametr.
- **memory_size:** liczba żądanych bajtów.
- **wait_option:** definiuje sposób zachowania usługi w przypadku braku wystarczającej ilości pamięci. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT:**(0x00000000)
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF)
    - wartość limitu czasu: (0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowy zwrot z tej usługi niezależnie od tego, czy to się powiodło. *Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z inicjowania.*

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony do momentu, gdy dostępna będzie wystarczająca ilość pamięci.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na pamięć.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna alokacja pamięci.
- **TX_DELETED:**(0x01) Pula pamięci została usunięta, gdy wątek został zawieszony.
- **TX_NO_MEMORY:**(0x10) Usługa nie mogła przydzielić pamięci w określonym czasie oczekiwania.
- **TX_WAIT_ABORTED:**(0x1A) Zawieszenie zostało przerwane przez inny wątek, czasomierz lub isr.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do wskaźnika docelowego.
- TX_SIZE_ERROR: (0X05) Żądany rozmiar jest zero lub większy niż pula.
- TX_WAIT_ERROR: (0x04) Opcja oczekiwania inna niż TX_NO_WAIT została określona dla wywołania z niewątkowego.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Tworzenie puli pamięci bajtów

### <a name="prototype"></a>Prototype

```C
UINT tx_byte_pool_create(TX_BYTE_POOL *pool_ptr,
                          CHAR *name_ptr, VOID *pool_start,
                          ULONG pool_size);
```
### <a name="description"></a>Opis

Ta usługa tworzy pulę bajtów pamięci w określonym obszarze. Początkowo pula składa się z jednego bardzo dużego wolnego bloku. Jednak pula jest dzielana na mniejsze bloki w przypadku alokacji.

### <a name="parameters"></a>Parametry

- **pool_ptr:** wskaźnik do bloku sterowania puli pamięci.
- **name_ptr:** Wskaźnik do nazwy puli pamięci.
- **pool_start:** początkowy adres puli pamięci. Adres początkowy musi być dopasowany do rozmiaru typu danych ULONG.
- **pool_size:** łączna liczba bajtów dostępnych dla puli pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne utworzenie puli pamięci.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci. Wskaźnik ma wartość NULL lub pula została już utworzona.
- TX_PTR_ERROR: (0x03) Nieprawidłowy adres początkowy puli.
- TX_SIZE_ERROR: (0x05) Rozmiar puli jest nieprawidłowy.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ta usługa usuwa określoną pulę bajtów pamięci. Wszystkie wątki wstrzymane w oczekiwaniu na pamięć z tej puli są wznawiane i nadaj TX_DELETED zwracany stan.

> [!IMPORTANT]
> Aplikacja odpowiada za zarządzanie obszarem pamięci skojarzonym z pulą, który jest dostępny po zakończeniu pracy tej usługi. Ponadto aplikacja musi uniemożliwić korzystanie z wcześniej przydzielonej puli lub pamięci.

### <a name="parameters"></a>Parametry 

- **pool_ptr:** wskaźnik do wcześniej utworzonej puli pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne usunięcie puli pamięci.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o puli bajtów

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

- **pool_ptr:** Wskaźnik do wcześniej utworzonej puli pamięci.
- **name**: Wskaźnik do miejsca docelowego dla wskaźnika do nazwy puli bajtów.
- **dostępne:** wskaźnik do miejsca docelowego dla liczby dostępnych bajtów w puli.
- **fragmentów:** wskaźnik do miejsca docelowego całkowitej liczby fragmentów pamięci w puli bajtów.
- **first_suspended:** Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszenia tej puli bajtów.
- **suspended_count:** wskaźnik do miejsca docelowego dla liczby wątków aktualnie zawieszonych w tej puli bajtów.
- **next_pool:** wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej puli bajtów.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pobieranie informacji o puli pomyślnych.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie informacji o wydajności puli bajtów

### <a name="prototype"></a>Prototype

```C
UINT tx_byte_pool_performance_info_get(TX_BYTE_POOL *pool_ptr,
        ULONG *allocates, ULONG *releases,
        ULONG *fragments_searched, ULONG *merges, ULONG *splits,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności określonej puli bajtów pamięci.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o  wydajności, biblioteka i aplikacja ThreadX SMP TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO muszą być sbudowaną za pomocą zdefiniowanej biblioteki SMP ThreadX.

### <a name="parameters"></a>Parametry

- **pool_ptr:** wskaźnik do wcześniej utworzonej puli bajtów pamięci.
- **allocates**: wskaźnik do miejsca docelowego dla liczby żądań alokacji wykonanych w tej puli.
- **releases:** wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.
- **fragments_searched:** wskaźnik do miejsca docelowego dla liczby fragmentów pamięci wewnętrznej przeszukiwanych podczas żądań alokacji w tej puli.
- **merges:** wskaźnik do miejsca docelowego dla liczby bloków pamięci wewnętrznej scalonych podczas żądań alokacji w tej puli.
- **splits**: wskaźnik do miejsca docelowego dla liczby podziałów (fragmentów) bloków pamięci wewnętrznej podczas żądań alokacji w tej puli.
- **suspensions**: wskaźnik do miejsca docelowego dla liczby zawieszenia alokacji wątku w tej puli.
- **limity czasu:** wskaźnik do miejsca docelowego dla liczby limitów czasu wstrzymania przydziału w tej puli.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- TX_SUCCESS: (0x00) Pomyślne uzyskiwanie wydajności puli bajtów.
- **TX_PTR_ERROR:**(0x03) Nieprawidłowy wskaźnik puli bajtów.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Uzyskiwanie informacji o wydajności systemu puli bajtów

### <a name="prototype"></a>Prototype

```C
UINT  tx_byte_pool_performance_system_info_get(ULONG *allocates,
        ULONG *releases, ULONG *fragments_searched, ULONG *merges,
        ULONG *splits, ULONG *suspensions, ULONG *timeouts);;
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich pul bajtów pamięci w systemie.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o wydajności, biblioteka i aplikacja SMP **ThreadX** muszą TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO za pomocą zdefiniowanej definicji.

### <a name="parameters"></a>Parametry

- **allocates**: wskaźnik do miejsca docelowego dla liczby żądań alokacji wykonanych w tej puli.
- **releases:** wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.
- **fragments_searched:** wskaźnik do miejsca docelowego dla łącznej liczby fragmentów pamięci wewnętrznej przeszukiwanych podczas żądań alokacji we wszystkich pulach bajtów.
- **merges**: wskaźnik do miejsca docelowego dla całkowitej liczby wewnętrznych bloków pamięci scalonych podczas żądań alokacji we wszystkich pulach bajtów.
- **splits**: wskaźnik do miejsca docelowego dla całkowitej liczby podziałów (fragmentów) bloków pamięci wewnętrznej utworzonych podczas żądań alokacji we wszystkich pulach bajtów.
- **suspensions**: wskaźnik do miejsca docelowego dla całkowitej liczby zawieszeń alokacji wątków we wszystkich pulach bajtów.
- **limity czasu:** wskaźnik do miejsca docelowego dla całkowitej liczby limitów czasu wstrzymania przydziału we wszystkich pulach bajtów.

> [!IMPORTANT]
> Dostarczenie parametru TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności puli bajtów.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Określanie priorytetów listy zawieszenia puli bajtów

### <a name="prototype"></a>Prototype

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wątek o najwyższym priorytecie zawieszony dla pamięci w tej puli na początku listy zawieszenia. Wszystkie inne wątki pozostają w tej samej kolejności FIFO, w których zostały wstrzymane.

### <a name="parameters"></a>Parametry 

- **pool_ptr:** wskaźnik do bloku sterowania puli pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Priorytet puli pamięci powodzenie.
- TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Zwalnianie bajtów z powrotem do puli pamięci

### <a name="prototype"></a>Prototype

```C
UINT tx_byte_release(VOID *memory_ptr);
```
### <a name="description"></a>Opis

Ta usługa zwalnia wcześniej przydzielony obszar pamięci z powrotem do skojarzonej puli. Jeśli co najmniej jeden wątek jest zawieszony w oczekiwaniu na pamięć z tej puli, każdy zawieszony wątek ma nadaną pamięć i jest wznawiany do momentu wyczerpania pamięci lub do momentu, gdy nie będzie już wstrzymanych wątków. Ten proces przydzielania pamięci do zawieszonych wątków zawsze rozpoczyna się od pierwszego wstrzymanego wątku.

> [!IMPORTANT]
> Aplikacja musi uniemożliwić korzystanie z obszaru pamięci po jego zwolnieniu.

### <a name="parameters"></a>Parametry

- **memory_ptr:** wskaźnik do poprzednio przydzielonego obszaru pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne wydanie pamięci.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik obszaru pamięci.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Tworzenie grupy flag zdarzeń

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_create(TX_EVENT_FLAGS_GROUP *group_ptr,
                          CHAR *name_ptr);
```
### <a name="description"></a>Opis

Ta usługa tworzy grupę 32 flag zdarzeń. Wszystkie 32 flagi zdarzeń w grupie są inicjowane do zera. Każda flaga zdarzenia jest reprezentowana przez pojedynczy bit.

### <a name="parameters"></a>Parametry

- **group_ptr:** wskaźnik do bloku sterowania grupy flag zdarzeń. 
- **name_ptr:** wskaźnik do nazwy grupy flag zdarzeń.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne utworzenie grupy zdarzeń.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy zdarzeń. Wskaźnik ma wartość NULL lub grupa zdarzeń została już utworzona.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Usuwanie grupy flag zdarzeń

### <a name="prototype"></a>Prototype

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określoną grupę flag zdarzeń. Wszystkie wątki wstrzymane w oczekiwaniu na zdarzenia z tej grupy są wznawiane i nadaj TX_DELETED zwracany stan.

> [!IMPORTANT]
> Aplikacja musi upewnić się, że wywołanie zwrotne powiadomienia zestawu dla tej grupy flag zdarzeń zostało ukończone (lub wyłączone) przed usunięciem grupy flag zdarzeń. Ponadto aplikacja musi uniemożliwić w przyszłości korzystanie z usuniętej grupy flag zdarzeń.

### <a name="parameters"></a>Parametry 

- **group_ptr:** wskaźnik do wcześniej utworzonej grupy flag zdarzeń.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne usunięcie grupy flag zdarzeń.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy flag zdarzeń.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ta usługa pobiera flagi zdarzeń z określonej grupy flag zdarzeń. Każda grupa flag zdarzeń zawiera 32 flagi zdarzeń. Każda flaga jest reprezentowana przez pojedynczy bit. Ta usługa może pobrać różne kombinacje flag zdarzeń wybrane przez parametry wejściowe.

### <a name="parameters"></a>Parametry

- **group_ptr:** wskaźnik do wcześniej utworzonej grupy flag zdarzeń.
- **requested_flags:** 32-bitowa zmienna bez nazwy reprezentująca żądane flagi zdarzeń.
- **get_option:** Określa, czy wymagane są wszystkie lub dowolne z żądanych flag zdarzeń. Poniżej przedstawiono prawidłowe opcje wyboru:
    - **TX_AND:**(0x02)
    - **TX_AND_CLEAR:**(0x03)
    - **TX_OR:**(0x00)
    - **TX_OR_CLEAR:**(0x01)

    Wybranie TX_AND lub TX_AND_CLEAR określa, że wszystkie flagi zdarzeń muszą być obecne w grupie. Wybranie TX_OR lub TX_OR_CLEAR określa, że każda flaga zdarzenia jest zadowalająca. Flagi zdarzeń spełniające żądanie są czyszowane (ustawione na zero), jeśli TX_AND_CLEAR lub TX_OR_CLEAR są określone.

- **actual_flags_ptr:** wskaźnik do miejsca docelowego, w którym znajdują się pobrane flagi zdarzeń. Należy pamiętać, że rzeczywiste uzyskane flagi mogą zawierać flagi, których nie zażądano.
- **wait_option:** definiuje sposób zachowania usługi, jeśli wybrane flagi zdarzeń nie są ustawione. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT:**(0x00000000)
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF)
    - wartość limitu czasu: (0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowy zwrot z tej usługi niezależnie od tego, czy to się powiodło. Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątkowego; np. inicjalizacja, czasomierz lub ISR.

    Wybranie TX_WAIT_FOREVER powoduje zawieszanie wątku wywołującego na czas nieokreślony do momentu, gdy flagi zdarzeń będą dostępne.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na flagi zdarzeń.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie flag zdarzeń.
- **TX_DELETED:**(0x01) Grupa flag zdarzeń została usunięta, gdy wątek został zawieszony.
- **TX_NO_EVENTS:**(0x07) Usługa nie mogła pobrać określonych zdarzeń w określonym czasie oczekiwania.
- **TX_WAIT_ABORTED:**(0x1A) Zawieszenie zostało przerwane przez inny wątek, czasomierz lub isr.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy flag zdarzeń.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik dla rzeczywistych flag zdarzeń.
- TX_WAIT_ERROR: (0x04) Opcja oczekiwania inna niż TX_NO_WAIT została określona dla wywołania z niewątkowego.
- TX_OPTION_ERROR: (0x08) Określono nieprawidłową opcję get-option.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o grupie flag zdarzeń

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

- **group_ptr:** wskaźnik do bloku sterowania grupy flag zdarzeń.
- **name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy grupy flag zdarzeń.
- **current_flags:** wskaźnik do miejsca docelowego dla bieżących flag zestawu w grupie flag zdarzeń.
- **first_suspended:** wskaźnik do miejsca docelowego dla wskaźnika do wątku, który znajduje się jako pierwszy na liście zawieszania tej grupy flag zdarzeń.
- **suspended_count:** wskaźnik do miejsca docelowego dla liczby wątków aktualnie zawieszonych w tej grupie flag zdarzeń.
- **next_group:** wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej grupy flag zdarzeń.

> [!IMPORTANT]
> Dostarczenie parametru TX_NULL parametru oznacza, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pobieranie informacji o grupie zdarzeń powiodło się.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy zdarzeń.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie informacji o wydajności grupy flag zdarzeń

### <a name="prototype"></a>Prototype

```C
UINT tx_event_flags_performance_info_get(TX_EVENT_FLAGS_GROUP
                        *group_ptr, ULONG *sets, ULONG *gets,
                        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności określonej grupy flag zdarzeń.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o wydajności, biblioteka i aplikacja SMP ThreadX muszą **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** z definicją.

### <a name="parameters"></a>Parametry

- **group_ptr:** wskaźnik do wcześniej utworzonej grupy flag zdarzeń.
- **sets**: wskaźnik do miejsca docelowego dla liczby żądań zestawu flag zdarzeń wykonanych dla tej grupy.
- **pobiera**: wskaźnik do miejsca docelowego dla liczby flag zdarzeń get żądań wykonywanych w tej grupie.
- **suspensions**: wskaźnik do miejsca docelowego dla liczby flag zdarzeń wątku jest zawieszany w tej grupie.
- **limity czasu:** wskaźnik do miejsca docelowego dla liczby flag zdarzeń ma limity czasu wstrzymania w tej grupie.

> [!IMPORTANT]
> Dostarczenie parametru TX_NULL parametru oznacza, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne flagi zdarzeń, uzyskiwanie wydajności grupy.
- **TX_PTR_ERROR:**(0x03) Nieprawidłowy wskaźnik grupy flag zdarzeń.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Pobieranie informacji o systemie wydajności

### <a name="prototype"></a>Prototype

```c
UINT  tx_event_flags_performance_system_info_get(ULONG *sets,
        ULONG *gets,ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności dotyczące wszystkich grup flag zdarzeń w systemie.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o wydajności, biblioteka i aplikacja SMP ThreadX muszą **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** z definicją.

### <a name="parameters"></a>Parametry

- **sets:** wskaźnik do miejsca docelowego dla łącznej liczby żądań zestawu flag zdarzeń wykonanych dla wszystkich grup.
- **pobiera**: wskaźnik do miejsca docelowego dla całkowitej liczby flag zdarzeń, które pobierają żądania wykonywane dla wszystkich grup.
- **suspensions**: wskaźnik do miejsca docelowego dla całkowitej liczby flag zdarzeń wątku jest zawieszany we wszystkich grupach.
- **limity czasu:** wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń otrzyma limity czasu wstrzymania dla wszystkich grup.

> [!IMPORTANT]
> Dostarczenie parametru TX_NULL parametru oznacza, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne zdarzenie flaguje wydajność systemu.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Ta usługa ustawia lub czyszczy flagi zdarzeń w grupie flag zdarzeń, w zależności od określonej opcji set-option. Wszystkie wstrzymane wątki, których żądanie flag zdarzeń jest teraz spełnione, zostaną wznowione.

### <a name="parameters"></a>Parametry

- **group_ptr:** wskaźnik do wcześniej utworzonego bloku sterowania grupy flag zdarzeń.
- **flags_to_set:** określa flagi zdarzeń do ustawienia lub wyczyszczenia na podstawie wybranej opcji zestawu.
- **set_option:** Określa, czy określone flagi zdarzeń są ANDed lub ORed do bieżących flag zdarzeń grupy. Poniżej przedstawiono prawidłowe opcje wyboru:
    - **TX_AND:**(0x02)
    - **TX_OR:**(0x00) Wybranie TX_AND określa, że określone flagi zdarzeń są i **są** ed do bieżących flag zdarzeń w grupie. Ta opcja jest często używana do wyczyszczenia flag zdarzeń w grupie. W przeciwnym razie TX_OR, określone flagi zdarzeń są **LUB** ed z bieżącym zdarzeniem w grupie.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Zestaw flag zdarzeń pomyślnych.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik do grupy flag zdarzeń.
- TX_OPTION_ERROR: (0x08) Określona nieprawidłowa opcja zestawu.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Powiadamianie aplikacji o ustawionych flagach zdarzeń

### <a name="prototype"></a>Prototype

```C
UINT tx_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr,
       VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego powiadomień, która jest wywoływana za każdym razem, gdy co najmniej jedna flaga zdarzenia jest ustawiona w określonej grupie flag zdarzeń. Przetwarzanie wywołania zwrotnego powiadomień jest definiowane przez aplikację.

> [!NOTE]
> Wywołanie zwrotne powiadomień zestawu flag zdarzeń aplikacji nie może wywołać żadnego interfejsu API SMP ThreadX z opcją zawieszenia.

### <a name="parameters"></a>Parametry 
- **group_ptr:** wskaźnik do wcześniej utworzonej grupy flag zdarzeń.
- **events_set_notify:** wskaźnik do funkcji powiadomień zestawu flag zdarzeń aplikacji. Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna rejestracja powiadomienia zestawu flag zdarzeń.
- TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy flag zdarzeń.
- TX_FEATURE_NOT_ENABLED: (0xFF) System został skompilowany z wyłączonymi możliwościami powiadomień.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

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
> Jeśli ta usługa jest wywoływana z wątku aplikacji, czas przerwania pozostaje częścią kontekstu tego wątku. Jeśli na przykład wątek wywołuje tę procedurę w celu wyłączenia przerwań, a następnie wstrzymuje działanie, po wznowieniu przerwania zostaną ponownie wyłączone.

> [!WARNING]
> Tej usługi nie należy używać do włączania przerwań podczas inicjowania. Może to spowodować nieprzewidywalne wyniki.

### <a name="parameters"></a>Parametry

- **new_posture:** ten parametr określa, czy przerwania są wyłączone, czy włączone. Wartości prawne obejmują **TX_INT_DISABLE i TX_INT_ENABLE.** Rzeczywiste wartości tych parametrów są specyficzne dla portu. Ponadto niektóre architektury przetwarzania mogą obsługiwać dodatkowe przerwania, które wyłączą możliwości. Aby uzyskać więcej **_informacji,readme_threadx.txt_** uzyskać więcej informacji na temat awarii podanych na dysku dystrybucji.

### <a name="return-values"></a>Wartości zwrócone

- poprzednia postawa: Ta usługa zwraca poprzednią postawę przerwania do wywołującego. Dzięki temu użytkownicy usługi mogą przywrócić poprzednią postawę po wyłączeniu przerwań.

### <a name="allowed-from"></a>Dozwolone z

Wątki, czasomierze i isr

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Tworzenie wzajemnego wykluczania mutex

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_create(TX_MUTEX *mutex_ptr,
                          CHAR *name_ptr, UINT priority_inherit);
```
### <a name="description"></a>Opis
    
Ta usługa tworzy wierzchołek dla wzajemnego wykluczania międzywątkowego w celu ochrony zasobów.

### <a name="parameters"></a>Parametry

- **mutex_ptr:** wskaźnik do bloku sterowania mutex.
- **name_ptr:** Wskaźnik do nazwy mutex.
- **priority_inherit:** określa, czy ten wierzchołek obsługuje dziedziczenie priorytetów. Jeśli ta wartość jest TX_INHERIT, obsługiwane jest dziedziczenie priorytetów. Jeśli jednak określono TX_NO_INHERIT, dziedziczenie priorytetów nie jest obsługiwane przez ten wierzchołek mutex.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne utworzenie obiektu mutex.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik mutex. Wskaźnik ma wartość NULL lub już utworzono mutex.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.
- TX_INHERIT_ERROR: (0x1F) Nieprawidłowy priorytet dziedziczy parametr.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Usuwanie wzajemnego wykluczania mutex

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określony mutex. Wszystkie wątki wstrzymane w oczekiwaniu na mutex są wznawiane i nadaj TX_DELETED stanu powrotu.

> [!IMPORTANT]
> Aplikacja odpowiada za zapobieganie używaniu usuniętego mutexu.

### <a name="parameters"></a>Parametry

- **mutex_ptr:** wskaźnik do wcześniej utworzonego obiektu mutex.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne usunięcie elementów mutex.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik mutex.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie własności obiektu mutex

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_get(TX_MUTEX *mutex_ptr, ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa próbuje uzyskać wyłączną własność określonego mutex. Jeśli wątek wywołujący jest już właścicielem obiektu mutex, zwiększa się licznik wewnętrzny i jest zwracany stan powodzenia.

Jeśli mutex jest własnością innego wątku i ten wątek ma wyższy priorytet, a dziedziczenie priorytetu zostało określone podczas tworzenia mutex, priorytet wątku o niższym priorytecie zostanie tymczasowo podniesiony do tego wątku wywołującego.

> [!IMPORTANT]
> Priorytet wątku o niższym priorytecie, który jest właścicielem mutex o priorytecie, nigdy nie powinien być modyfikowany przez wątek zewnętrzny podczas własności mutex.

### <a name="parameters"></a>Parametry

- **mutex_ptr:** wskaźnik do wcześniej utworzonego obiektu mutex.
- **wait_option:** definiuje sposób zachowania usługi, jeśli mutex jest już własnością innego wątku. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT:**(0x00000000)
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF)
    - wartość limitu czasu: (0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowy zwrot z tej usługi, niezależnie od tego, czy to się powiodło. *Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z inicjowania.*

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony do momentu, gdy będzie dostępny mutex.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na wierzchołek.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna operacja mutex get.
- **TX_DELETED:**(0x01) Mutex został usunięty, gdy wątek został zawieszony.
- **TX_NOT_AVAILABLE:**(0x1D) Usługa nie mogła uzyskać własności obiektu mutex w określonym czasie oczekiwania.
- **TX_WAIT_ABORTED:**(0x1A) Zawieszenie zostało przerwane przez inny wątek, czasomierz lub ISR.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik mutex.
- TX_WAIT_ERROR: (0x04) Opcja oczekiwania inna niż TX_NO_WAIT została określona dla wywołania z nieprzeczytanego.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie oraz wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o mutex

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_info_get(TX_MUTEX *mutex_ptr, CHAR **name,
                          ULONG *count, TX_THREAD **owner,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count, TX_MUTEX **next_mutex);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje z określonego mutex.

### <a name="parameters"></a>Parametry

- **mutex_ptr:** Wskaźnik do bloku sterowania mutex.
- **name**: Wskaźnik do miejsca docelowego dla wskaźnika do nazwy mutex.
- **count:** wskaźnik do miejsca docelowego dla liczby własności mutex.
- **owner:** wskaźnik do miejsca docelowego dla wskaźnika wątku, który jest właścicielem.
- **first_suspended:** Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszenia tego obiektu mutex.
- **suspended_count:** wskaźnik do miejsca docelowego dla liczby wątków aktualnie zawieszonych na tym mutexie.
- **next_mutex:** Wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego obiektu mutex.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne pobieranie informacji o mutex.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik mutex.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie informacji o wydajności obiektu mutex

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_performance_info_get(TX_MUTEX *mutex_ptr, ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts,
       ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności określonego mutex.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o  wydajności, biblioteka i aplikacja ThreadX SMP TX_MUTEX_ENABLE_PERFORMANCE_INFO muszą zostać sbudowaną za pomocą zdefiniowanej biblioteki SMP ThreadX.

### <a name="parameters"></a>Parametry

- **mutex_ptr:** wskaźnik do wcześniej utworzonego obiektu mutex.
- **puts:** wskaźnik do miejsca docelowego dla liczby żądań put wykonanych na tym mutexie.
- **pobiera**: wskaźnik do miejsca docelowego dla liczby żądań get wykonanych dla tego obiektu mutex.
- **suspensions**: wskaźnik do miejsca docelowego dla liczby wątków, w których są zawieszane elementy mutex.
- **limity czasu:** wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia get mutex w tym mutex.
- **inversions:** wskaźnik do miejsca docelowego dla liczby inversions priorytetów wątku w tym mutex.
- **inheritances:** wskaźnik do miejsca docelowego dla liczby operacji dziedziczenia priorytetu wątku w tym mutex.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności mutex. 
- **TX_PTR_ERROR:**(0x03) Nieprawidłowy wskaźnik mutex.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

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

Uzyskiwanie informacji o wydajności systemu mutex

### <a name="prototype"></a>Prototype

```C
UINT  tx_mutex_performance_system_info_get(ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts,
        ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności dotyczące wszystkich mutex w systemie.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o wydajności, biblioteka i aplikacja SMP **ThreadX** muszą TX_MUTEX_ENABLE_PERFORMANCE_INFO z definicją.

### <a name="parameters"></a>Parametry

- **puts:** wskaźnik do miejsca docelowego dla łącznej liczby żądań put wykonanych na wszystkich mutexes.
- **pobiera**: wskaźnik do miejsca docelowego dla łącznej liczby żądań get wykonanych na wszystkich mutexes.
- **suspensions**: wskaźnik do miejsca docelowego dla całkowitej liczby wątków mutex uzyskać zawieszenie na wszystkich mutexes.
- **limity czasu:** wskaźnik do miejsca docelowego dla łącznej liczby mutex get limity czasu zawieszenia na wszystkich mutexes.
- **inversions**: wskaźnik do miejsca docelowego dla całkowitej liczby inversions priorytetów wątku we wszystkich mutexes.
- **inheritances:** wskaźnik do miejsca docelowego dla łącznej liczby operacji dziedziczenia priorytetu wątku we wszystkich mutexach.

> [!IMPORTANT]
> Dostarczenie parametru TX_NULL parametru oznacza, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności systemu mutex.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Określanie priorytetów listy zawieszenia mutex

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wątek o najwyższym priorytecie zawieszony na własność mutex na początku listy zawieszenia. Wszystkie inne wątki pozostają w tej samej kolejności FIFO, w których zostały wstrzymane.

### <a name="parameters"></a>Parametry 

- **mutex_ptr:** wskaźnik do wcześniej utworzonego obiektu mutex.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne określanie priorytetów mutex.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik mutex.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Zwolnij własność obiektu mutex

### <a name="prototype"></a>Prototype

```C
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a>Opis

Ta usługa zmniejsza liczbę własności określonego obiektu mutex. Jeśli liczba własności wynosi zero, zostanie udostępnione mutex.

> [!IMPORTANT]
> Jeśli podczas tworzenia mutex wybrano dziedziczenie priorytetu, priorytet zwalniającego wątku zostanie przywrócony do priorytetu, który miał, gdy pierwotnie uzyskał własność mutex. Wszelkie inne zmiany priorytetu wprowadzone do zwalniającego wątku podczas własności obiektu mutex mogą zostać cofnięte.

### <a name="parameters"></a>Parametry

- **mutex_ptr:** wskaźnik do wcześniej utworzonego obiektu mutex.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne wydanie mutex.
- **TX_NOT_OWNED:**(0x1E) Mutex nie jest własnością obiektu wywołującego.
- TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik do mutex.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie oraz wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Tworzenie kolejki komunikatów

### <a name="prototype"></a>Prototype

```c
UINT tx_queue_create(TX_QUEUE *queue_ptr, CHAR *name_ptr,
                          UINT message_size,
                          VOID *queue_start, ULONG queue_size);
```
### <a name="description"></a>Opis

Ta usługa tworzy kolejkę komunikatów, która jest zwykle używana do komunikacji międzywątkowej. Łączna liczba komunikatów jest obliczana na podstawie określonego rozmiaru komunikatu i całkowitej liczby bajtów w kolejce.

> [!IMPORTANT]
> Jeśli całkowita liczba bajtów określona w obszarze pamięci kolejki nie jest równomiernie podzielna przez określony rozmiar komunikatu, pozostałe bajty w obszarze pamięci nie są używane.

### <a name="parameters"></a>Parametry

- **queue_ptr:** wskaźnik do bloku sterowania kolejki komunikatów.
- **name_ptr:** Wskaźnik do nazwy kolejki komunikatów.
- **message_size:** określa rozmiar każdego komunikatu w kolejce. Rozmiary komunikatów to od 1 słowa 32-bitowego do 16 słów 32-bitowych. Prawidłowe opcje rozmiaru komunikatu to wartości liczbowe od 1 do 16 włącznie.
- **queue_start:** początkowy adres kolejki komunikatów. Adres początkowy musi być dopasowany do rozmiaru typu danych ULONG.
- **queue_size:** łączna liczba bajtów dostępnych dla kolejki komunikatów.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne utworzenie kolejki komunikatów.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów. Wskaźnik ma wartość NULL lub kolejka została już utworzona.
- TX_PTR_ERROR: (0x03) Nieprawidłowy adres początkowy kolejki komunikatów.
- TX_SIZE_ERROR: (0x05) Rozmiar kolejki komunikatów jest nieprawidłowy.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Usuwanie kolejki komunikatów

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określoną kolejkę komunikatów. Wszystkie wątki wstrzymane w oczekiwaniu na komunikat z tej kolejki są wznawiane i na TX_DELETED zwracany stan.

> [!IMPORTANT]
> Aplikacja musi upewnić się, że każde wywołanie zwrotne powiadomienia o wysłaniu dla tej kolejki zostało ukończone (lub wyłączone) przed usunięciem kolejki. Ponadto aplikacja musi uniemożliwić korzystanie z usuniętej kolejki w przyszłości.

*Aplikacja jest również odpowiedzialna za zarządzanie obszarem pamięci skojarzonym z kolejką, który jest dostępny po zakończeniu tej usługi.*

### <a name="parameters"></a>Parametry 

- **queue_ptr:** Wskaźnik do wcześniej utworzonej kolejki komunikatów.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne usunięcie kolejki komunikatów.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Puste komunikaty w kolejce komunikatów

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa wszystkie komunikaty przechowywane w określonej kolejce komunikatów. Jeśli kolejka jest pełna, komunikaty wszystkich zawieszonych wątków są odrzucane. Każdy zawieszony wątek jest następnie wznawiany ze stanem powrotu wskazującym, że wysyłanie komunikatu powiodło się. Jeśli kolejka jest pusta, ta usługa nic nie robi.

### <a name="parameters"></a>Parametry 

- **queue_ptr:** Wskaźnik do wcześniej utworzonej kolejki komunikatów.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne opróżnienie kolejki komunikatów.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Wysyłanie komunikatu na przód kolejki

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_front_send(TX_QUEUE *queue_ptr,
                           VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa wysyła komunikat do lokalizacji frontowej określonej kolejki komunikatów. Komunikat jest **kopiowany na** przód kolejki z obszaru pamięci określonego przez wskaźnik źródłowy.

### <a name="parameters"></a>Parametry

- **queue_ptr:** wskaźnik do bloku sterowania kolejki komunikatów.
- **source_ptr:** wskaźnik do komunikatu.
- **wait_option:** definiuje sposób zachowania usługi, jeśli kolejka komunikatów jest pełna. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT:**(0x00000000)
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF)
    - wartość limitu czasu: (0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT skutkuje natychmiastowym zwrotem z tej usługi niezależnie od tego, czy to się powiodło. *Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z nie wątku; np. inicjalizacja, czasomierz lub isr.*

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki nie będzie miejsca w kolejce.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na miejsce w kolejce.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne wysłanie komunikatu.
- **TX_DELETED:**(0x01) Kolejka komunikatów została usunięta, gdy wątek został zawieszony.
- **TX_QUEUE_FULL:**(0x0B) Usługa nie mogła wysłać komunikatu, ponieważ kolejka była pełna przez określony czas oczekiwania.
- **TX_WAIT_ABORTED:**(0x1A) Zawieszenie zostało przerwane przez inny wątek, czasomierz lub ISR.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik źródła komunikatu.
- TX_WAIT_ERROR: (0x04) Opcja oczekiwania inna niż TX_NO_WAIT została określona dla wywołania z nieprzeczytanego.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o kolejce

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

- **queue_ptr:** Wskaźnik do wcześniej utworzonej kolejki komunikatów.
- **name:** Wskaźnik do miejsca docelowego dla wskaźnika do nazwy kolejki.
- **enqueued:** wskaźnik do miejsca docelowego dla liczby komunikatów aktualnie w kolejce.
- **available_storage:** Wskaźnik do miejsca docelowego dla liczby komunikatów, dla których kolejka aktualnie ma miejsce.
- **first_suspended:** Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszenia tej kolejki.
- **suspended_count:** Wskaźnik do miejsca docelowego dla liczby wątków aktualnie zawieszonych w tej kolejce.
- **next_queue:** Wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej kolejki.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie informacji o kolejce.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie informacji o wydajności kolejki

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
> Aby ta usługa zwracała informacje o  wydajności, biblioteka i aplikacja ThreadX SMP TX_QUEUE_ENABLE_PERFORMANCE_INFO muszą zostać sbudowaną za pomocą zdefiniowanej biblioteki SMP ThreadX.

### <a name="parameters"></a>Parametry

- **queue_ptr:** wskaźnik do wcześniej utworzonej kolejki.
- **messages_sent:** wskaźnik do miejsca docelowego dla liczby żądań wysyłania wykonanych w tej kolejce.
- **messages_received:** wskaźnik do miejsca docelowego dla liczby żądań odbierania wykonanych w tej kolejce.
- **empty_suspensions:** Wskaźnik do miejsca docelowego dla liczby pustych zawieszenia kolejki w tej kolejce.
- **full_suspensions:** Wskaźnik do miejsca docelowego dla liczby pełnych zawieszenia kolejki w tej kolejce.
- **full_errors:** Wskaźnik do miejsca docelowego dla liczby pełnych błędów kolejki w tej kolejce.
- **limity czasu:** wskaźnik do miejsca docelowego dla liczby limitów czasu wstrzymania wątku w tej kolejce.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności kolejki.
- **TX_PTR_ERROR:**(0x03) Nieprawidłowy wskaźnik kolejki.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Uzyskiwanie informacji o wydajności systemu kolejek

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
> Aby ta usługa zwracała informacje o  wydajności, biblioteka i aplikacja ThreadX SMP TX_QUEUE_ENABLE_PERFORMANCE_INFO muszą zostać sbudowaną za pomocą zdefiniowanej biblioteki SMP ThreadX.

### <a name="parameters"></a>Parametry

- **messages_sent:** wskaźnik do miejsca docelowego dla łącznej liczby żądań wysyłania wykonanych we wszystkich kolejkach.
- **messages_received:** wskaźnik do miejsca docelowego dla łącznej liczby żądań odbierania wykonanych we wszystkich kolejkach.
- **empty_suspensions:** Wskaźnik do miejsca docelowego dla całkowitej liczby pustych zawieszenia kolejki we wszystkich kolejkach.
- **full_suspensions:** Wskaźnik do miejsca docelowego dla całkowitej liczby pełnych zawieszenia kolejki we wszystkich kolejkach.
- **full_errors:** Wskaźnik do miejsca docelowego dla łącznej liczby pełnych błędów kolejki we wszystkich kolejkach.
- **limity czasu:** wskaźnik do miejsca docelowego dla całkowitej liczby limitów czasu wstrzymania wątku we wszystkich kolejkach.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności systemu kolejek.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Określanie priorytetów listy wstrzymania kolejki

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Opis

Ta usługa umieszcza wątek o najwyższym priorytecie zawieszony dla komunikatu (lub umieścić komunikat) w tej kolejce na początku listy zawieszenia. Wszystkie inne wątki pozostają w tej samej kolejności FIFO, w których zostały wstrzymane.

### <a name="parameters"></a>Parametry 

- **queue_ptr:** Wskaźnik do wcześniej utworzonej kolejki komunikatów.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne określanie priorytetów kolejki.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie komunikatu z kolejki komunikatów

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_receive(TX_QUEUE *queue_ptr,
                          VOID *destination_ptr, ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa pobiera komunikat z określonej kolejki komunikatów. Pobrany komunikat jest **kopiowany** z kolejki do obszaru pamięci określonego przez wskaźnik docelowy. Ten komunikat jest następnie usuwany z kolejki.

> [!WARNING]
> Określony docelowy obszar pamięci musi być wystarczająco duży, aby można było przechowywać komunikat. oznacza to, że miejsce docelowe  komunikatu wskazywane przez destination_ptr musi być co najmniej tak duże, jak rozmiar komunikatu dla tej kolejki. W przeciwnym razie, jeśli miejsce docelowe nie jest wystarczająco duże, uszkodzenie pamięci występuje w następującym obszarze pamięci.

### <a name="parameters"></a>Parametry

- **queue_ptr:** Wskaźnik do wcześniej utworzonej kolejki komunikatów.
- **destination_ptr:** lokalizacja miejsca kopiowania komunikatu.
- **wait_option:** definiuje sposób zachowania usługi, jeśli kolejka komunikatów jest pusta. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT:**(0x00000000) 
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF) 
    - wartość limitu czasu: (0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowy zwrot z tej usługi, niezależnie od tego, czy to się powiodło. Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z nie wątku; np. inicjalizacja, czasomierz lub ISR.

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się na czas nieokreślony do momentu, gdy komunikat będzie dostępny.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na komunikat.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne pobranie komunikatu.
- **TX_DELETED:**(0x01) Kolejka komunikatów została usunięta, gdy wątek został zawieszony.
- **TX_QUEUE_EMPTY:**(0x0A) Usługa nie mogła pobrać komunikatu, ponieważ kolejka była pusta przez czas oczekiwania przez określony czas.
- **TX_WAIT_ABORTED:**(0x1A) Zawieszenie zostało przerwane przez inny wątek, czasomierz lub ISR.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik docelowy komunikatu.
- TX_WAIT_ERROR: (0x04) Opcja oczekiwania inna niż TX_NO_WAIT została określona dla wywołania z nieprzeczytanego.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Wysyłanie komunikatu do kolejki komunikatów

### <a name="prototype"></a>Prototype

```C
UINT tx_queue_send(TX_QUEUE *queue_ptr,
                          VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a>Opis

Ta usługa wysyła komunikat do określonej kolejki komunikatów. Wysłany komunikat jest **kopiowany do** kolejki z obszaru pamięci określonego przez wskaźnik źródłowy.

### <a name="parameters"></a>Parametry

- **queue_ptr:** Wskaźnik do wcześniej utworzonej kolejki komunikatów.
- **source_ptr:** Wskaźnik do komunikatu.
- **wait_option:** definiuje sposób zachowania usługi, jeśli kolejka komunikatów jest pełna. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT:**(0x00000000)
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF)
    - wartość limitu czasu: (0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowy zwrot z tej usługi, niezależnie od tego, czy to się powiodło. *Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z nie wątku; np. inicjalizacja, czasomierz lub ISR.*

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony, dopóki nie będzie miejsca w kolejce.

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na miejsce w kolejce.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne wysłanie komunikatu.
- **TX_DELETED:**(0x01) Kolejka komunikatów została usunięta, gdy wątek został zawieszony.
- **TX_QUEUE_FULL:**(0x0B) Usługa nie mogła wysłać komunikatu, ponieważ kolejka była pełna przez określony czas oczekiwania.
- **TX_WAIT_ABORTED:**(0x1A) Zawieszenie zostało przerwane przez inny wątek, czasomierz lub ISR.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik źródła komunikatu.
- TX_WAIT_ERROR: (0x04) Opcja oczekiwania inna niż TX_NO_WAIT została określona dla wywołania z nieprzeczytanego.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Powiadamianie aplikacji o wysłaniu komunikatu do kolejki

### <a name="prototype"></a>Prototype

```C
UINT  tx_queue_send_notify(TX_QUEUE *queue_ptr,
        VOID (*queue_send_notify)(TX_QUEUE *));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego powiadomień, która jest wywoływana za każdym razem, gdy komunikat jest wysyłany do określonej kolejki. Przetwarzanie wywołania zwrotnego powiadomień jest definiowane przez aplikację.

> [!NOTE]
> Wywołanie zwrotne powiadomienia o wysłaniu w kolejce aplikacji nie może wywołać żadnego interfejsu API SMP ThreadX z opcją zawieszenia.

### <a name="parameters"></a>Parametry 

- **queue_ptr:** wskaźnik do wcześniej utworzonej kolejki.
- **queue_send_notify:** wskaźnik do funkcji wysyłania powiadomień w kolejce aplikacji. Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna rejestracja powiadomienia o wysłaniu kolejki.
- TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki.
- TX_FEATURE_NOT_ENABLED: (0xFF) System został skompilowany z wyłączonymi możliwościami powiadomień.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Umieść wystąpienie w zliczeniu semafora za pomocą limitu

### <a name="prototype"></a>Prototype

```C
UINT  tx_semaphore_ceiling_put(TX_SEMAPHORE *semaphore_ptr,
        ULONG ceiling);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wystąpienie w określonym zliczeniu semafora, który w rzeczywistości zwiększa zliczanie semafora o jeden. Jeśli bieżąca wartość zliczania semafora jest większa lub równa określonej wartości limitu, wystąpienie nie zostanie wprowadzone i zostanie TX_CEILING_EXCEEDED błąd.

### <a name="parameters"></a>Parametry 

- **semaphore_ptr:** Wskaźnik do wcześniej utworzonego semafora.
- **ceiling:** maksymalny limit dozwolony dla semafora (prawidłowe wartości z zakresu od 1 do 0xFFFFFFFF).

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Successful semaphore ceiling put (Pomyślny limit semafora).
- **TX_CEILING_EXCEEDED:**(0x21) Żądanie put przekracza limit.
- TX_INVALID_CEILING: (0x22) Dla limitu podano nieprawidłową wartość zero.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Ta usługa tworzy semafor zliczania dla synchronizacji międzywątkowej. Początkowa liczba semaforów jest określana jako parametr wejściowy.

### <a name="parameters"></a>Parametry 

- **semaphore_ptr:** Wskaźnik do bloku sterowania semafora. 
- **name_ptr:** Wskaźnik do nazwy semafora.
- **initial_count:** określa początkową liczbę dla tego semafora. Wartości prawne mogą być różne 0x00000000 do 0xFFFFFFFF.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne utworzenie semafora.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora. Wskaźnik ma wartość NULL lub semafor został już utworzony.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Usuwanie semafora zliczania

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określony semafor zliczania. Wszystkie wątki wstrzymane w oczekiwaniu na wystąpienie semafora są wznawiane i mają TX_DELETED zwracany stan.

> [!IMPORTANT]
> Aplikacja musi upewnić się, że wywołanie zwrotne powiadomienia put dla tego semafora zostało ukończone (lub wyłączone) przed usunięciem semafora. Ponadto aplikacja musi zapobiegać wszystkiemu przyszłemu użyciu usuniętego semafora.

### <a name="parameters"></a>Parametry 

- **semaphore_ptr:** wskaźnik do wcześniej utworzonego semafora.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne zliczanie usunięcia semafora.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik zliczania semafora.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie wystąpienia z zliczania semafora

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_get(TX_SEMAPHORE *semaphore_ptr,
                          ULONG wait_option)
```
### <a name="description"></a>Opis

Ta usługa pobiera wystąpienie (pojedynczą liczbę) z określonego zliczania semafora. W związku z tym liczba określonego semafora jest zmniejszana o jeden.

### <a name="parameters"></a>Parametry

- **semaphore_ptr:** Wskaźnik do utworzonego wcześniej zliczania semafora.
- **wait_option:** definiuje sposób zachowania usługi, jeśli nie ma dostępnych wystąpień semafora; tj. liczba semaforów wynosi zero. Opcje oczekiwania są zdefiniowane w następujący sposób:
    - **TX_NO_WAIT:**(0x00000000)
    - **TX_WAIT_FOREVER:**(0xFFFFFFFF)
    - wartość limitu czasu: (0x00000001 do 0xFFFFFFFE)

    Wybranie TX_NO_WAIT powoduje natychmiastowy zwrot z tej usługi, niezależnie od tego, czy to się powiodło. *Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z nie wątku; np. inicjalizacja, czasomierz lub isr.*

    Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez czas nieokreślony do momentu, aż wystąpienie semafora będzie dostępne. 

    Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę takt czasomierzy, które mają pozostać wstrzymane podczas oczekiwania na wystąpienie semafora.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne pobranie wystąpienia semafora.
- **TX_DELETED:**(0x01) Zliczanie semafora zostało usunięte, gdy wątek został zawieszony.
- **TX_NO_INSTANCE:**(0x0D) Usługa nie mogła pobrać wystąpienia zliczania semafora (liczba semaforów wynosi zero w określonym czasie oczekiwania).
- **TX_WAIT_ABORTED:**(0x1A) Zawieszenie zostało przerwane przez inny wątek, czasomierz lub ISR.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik zliczania semafora.
- TX_WAIT_ERROR: (0x04) Opcja oczekiwania inna niż TX_NO_WAIT została określona dla wywołania z niewątkowej.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o semaforze

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

- **semaphore_ptr:** Wskaźnik do bloku sterowania semafora.
- **name**: Wskaźnik do miejsca docelowego dla wskaźnika do nazwy semafora.
- **current_value:** Wskaźnik do miejsca docelowego dla bieżącej liczby semaforów.
- **first_suspended:** Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszenia tego semafora.
- **suspended_count:** wskaźnik do miejsca docelowego dla liczby wątków aktualnie zawieszonych na tym semaforze.
- **next_semaphore:** Wskaźnik do miejsca docelowego wskaźnika następnego utworzonego semafora.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne pobieranie informacji o semaforach.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie informacji o wydajności semafora

### <a name="prototype"></a>Prototype

```C
UINT  tx_semaphore_performance_info_get(TX_SEMAPHORE *semaphore_ptr,
        ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności określonego semafora.

> [!NOTE]
> Aby ta usługa zwracała informacje o wydajności, biblioteka i aplikacja ThreadX SMP muszą **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** z definicją.

### <a name="parameters"></a>Parametry

- **semaphore_ptr:** Wskaźnik do wcześniej utworzonego semafora.
- **puts:** wskaźnik do miejsca docelowego dla liczby żądań put wykonanych na tym semaforze.
- **pobiera**: wskaźnik do miejsca docelowego dla liczby żądań get wykonanych na tym semaforze.
- **suspensions**: wskaźnik do miejsca docelowego dla liczby zawieszenia wątków na tym semaforze.
- **limity czasu:** wskaźnik do miejsca docelowego dla liczby limitów czasu wstrzymania wątku w tym semaforze.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności semafora.
- **TX_PTR_ERROR:**(0x03) Nieprawidłowy wskaźnik semafora.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Uzyskiwanie informacji o wydajności systemu semafora

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_performance_system_info_get(ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich semaforów w systemie.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o wydajności, biblioteka i aplikacja ThreadX SMP muszą **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** z definicją.

### <a name="parameters"></a>Parametry

- **puts:** wskaźnik do miejsca docelowego całkowitej liczby żądań put wykonanych na wszystkich semaforach.
- **pobiera**: wskaźnik do miejsca docelowego dla łącznej liczby żądań get wykonanych na wszystkich semaforach.
- **suspensions**: wskaźnik do miejsca docelowego całkowitej liczby zawieszenia wątków na wszystkich semaforach.
- **limity czasu:** wskaźnik do miejsca docelowego dla całkowitej liczby limitów czasu wstrzymania wątku we wszystkich semaforach.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- TX_SUCCESS: (0x00) Pomyślne uzyskiwanie wydajności systemu semaforów.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Określanie priorytetów listy zawieszenia semafora

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wątek o najwyższym priorytecie zawieszony dla wystąpienia semafora na początku listy zawieszenia. Wszystkie inne wątki pozostają w tej samej kolejności FIFO, w których zostały wstrzymane.

### <a name="parameters"></a>Parametry 

- **semaphore_ptr:** Wskaźnik do wcześniej utworzonego semafora.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Priorytetyzowanie pomyślnych semaforów.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik zliczania semafora.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Umieść wystąpienie w zliczeniu semafora

### <a name="prototype"></a>Prototype

```C
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wystąpienie w określonym zliczeniu semafora, który w rzeczywistości zwiększa zliczanie semafora o jeden.

> [!IMPORTANT]
> Jeśli ta usługa jest wywoływana, gdy semafor to wszystkie jedynki (OxFFFFFFFF), nowa operacja put spowoduje zresetowanie semafora do zera.

### <a name="parameters"></a>Parametry

- **semaphore_ptr:** wskaźnik do wcześniej utworzonego bloku sterowania zliczanych semaforów.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Successful semaphore put (Pomyślne put semafora).
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik do zliczania semafora.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Powiadamianie aplikacji o zastosowaniu semafora

### <a name="prototype"></a>Prototype

```C
UINT  tx_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr,
        VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego powiadomień, która jest wywoływana za każdym razem, gdy jest umieszczany określony semafor. Przetwarzanie wywołania zwrotnego powiadomień jest definiowane przez aplikację.

> [!NOTE]
> Wywołanie zwrotne powiadomienia semafora aplikacji nie może wywołać żadnego interfejsu API SMP ThreadX z opcją zawieszenia.

### <a name="parameters"></a>Parametry 

- **semaphore_ptr:** Wskaźnik do wcześniej utworzonego semafora.
- **semaphore_put_notify:** Wskaźnik do funkcji powiadamiania put put aplikacji. Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna rejestracja powiadomienia put semafora.
- TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System został skompilowany z wyłączonymi możliwościami powiadomień.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Tworzenie wątku aplikacji

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

Ta usługa tworzy wątek aplikacji, który rozpoczyna wykonywanie w określonej funkcji wpisu zadania. Stos, priorytet, próg wywłaszczenia i wycinek czasu należą do atrybutów określonych przez parametry wejściowe. Ponadto określono również początkowy stan wykonywania wątku.

### <a name="parameters"></a>Parametry

- **thread_ptr:** wskaźnik do bloku sterowania wątku.
- **name_ptr:** Wskaźnik do nazwy wątku.
- **entry_function:** określa początkową funkcję języka C do wykonywania wątku. Gdy wątek wraca z tej funkcji wpisu, jest umieszczany w stanie ukończonym i zawieszony na czas nieokreślony.
- **entry_input:** wartość 32-bitowa, która jest przekazywana do funkcji wpisu wątku podczas jego pierwszego wykonania. Użycie tych danych wejściowych jest określane wyłącznie przez aplikację.
- **stack_start:** początkowy adres obszaru pamięci stosu. 
- **stack_size:** liczba bajtów w obszarze pamięci stosu. Obszar stosu wątku musi być wystarczająco duży, aby obsłużyć zagnieżdżanie wywołań funkcji najgorszego przypadku i użycie zmiennych lokalnych.
- **priority:** priorytet numeryczny wątku. Wartości prawne wahają się od 0 do (TX_MAX_PRIORITES-1), gdzie wartość 0 reprezentuje najwyższy priorytet.
- **preempt_threshold:** najwyższy poziom priorytetu (od 0 do (TX_MAX_PRIORITIES-1)) wyłączonego wywłaszenia. Tylko priorytety wyższe niż ten poziom mogą wywłaszczeć ten wątek. Ta wartość musi być mniejsza lub równa podanej wartości priorytetu. Wartość równa priorytetowi wątku wyłącza próg wywłaszczenia.
- **time_slice:** Liczba znaczników czasomierza, które może uruchomić ten wątek, zanim inne gotowe wątki o tym samym priorytecie będą mogły uruchomić. Należy pamiętać, że użycie progu wywłaszczenia wyłącza próg czasu. Prawne wartości przedziału czasu mogą być od 1 do 0xFFFFFFFF (włącznie). Wartość TX_NO_TIME_SLICE **(wartość** 0) wyłącza czas cing tego wątku.

    > [!IMPORTANT]
    > Użycie funkcji licowania w czasie powoduje niewielkie obciążenie systemu. Ponieważ fragmentowanie czasu jest przydatne tylko w przypadkach, gdy wiele wątków ma ten sam priorytet, wątki o unikatowym priorytecie nie powinny mieć przypisanego fragmentu czasu.

- **auto_start:** Określa, czy wątek rozpoczyna się natychmiast, czy jest umieszczany w stanie zawieszenia. Opcje prawne to **TX_AUTO_START** (0x01) **i TX_DONT_START** (0x00). Jeśli TX_DONT_START, aplikacja musi później wywołać tx_thread_resume, aby wątek został uruchomiony.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne utworzenie wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik sterowania wątkami. Wskaźnik ma wartość NULL lub wątek został już utworzony.
- TX_PTR_ERROR: (0x03) Nieprawidłowy adres początkowy punktu wejścia lub obszar stosu jest nieprawidłowy, zazwyczaj null.
- TX_SIZE_ERROR: (0x05) Rozmiar obszaru stosu jest nieprawidłowy. Wątki muszą mieć co najmniej **TX_MINIMUM_STACK** bajtów do wykonania.
- TX_PRIORITY_ERROR: (0x0F) Nieprawidłowy priorytet wątku, który jest wartością spoza zakresu od (od 0 do (TX_MAX_PRIORITIES-1)).
- TX_THRESH_ERROR: (0x18) Określono nieprawidłowy wywłaszczyn. Ta wartość musi być prawidłowym priorytetem mniejszym lub równym początkowego priorytetu wątku.
- TX_START_ERROR: (0x10) Nieprawidłowy wybór automatycznego uruchamiania.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Usuwanie wątku aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa określony wątek aplikacji. Ponieważ określony wątek musi być w stanie zakończonym lub zakończonym, nie można wywołać tej usługi z wątku próbującego usunąć samą siebie.

> [!IMPORTANT]
> Aplikacja odpowiada za zarządzanie obszarem pamięci skojarzonym ze stosem wątku, który jest dostępny po zakończeniu tej usługi. Ponadto aplikacja musi uniemożliwić korzystanie z usuniętego wątku.

### <a name="parameters"></a>Parametry

- **thread_ptr:** wskaźnik do wcześniej utworzonego wątku aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne usunięcie wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- **TX_DELETE_ERROR:**(0x11) Określony wątek nie jest w stanie zakończenia lub zakończenia.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Powiadamianie aplikacji o wejściu i zakończeniu wątku

### <a name="prototype"></a>Prototype

```C
UINT  tx_thread_entry_exit_notify(TX_THREAD *thread_ptr,
        VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego powiadomień, która jest wywoływana za każdym razem, gdy określony wątek jest wprowadzany lub kończy działanie. Przetwarzanie wywołania zwrotnego powiadomień jest definiowane przez aplikację.

> [!NOTE]
> Wywołanie zwrotne powiadomień o wątkowym wejściu/wyjściu aplikacji nie może wywołać żadnego interfejsu API SMP ThreadX z opcją zawieszenia.

### <a name="parameters"></a>Parametry

- **thread_ptr:** Wskaźnik do wcześniej utworzonego wątku.
- **entry_exit_notify:** wskaźnik do funkcji powiadamiania o wątkowym wejściu/wyjściu aplikacji. Drugi parametr funkcji powiadamiania o wejściu/wyjściu wyznacza, jeśli istnieje wpis lub wyjście. Wartość TX_THREAD_ENTRY (0x00) wskazuje, że wątek został wprowadzony, a wartość TX_THREAD_EXIT (0x01) wskazuje, że wątek został exited. Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna rejestracja funkcji powiadamiania o wejściu/wyjściu wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.
- **TX_FEATURE_NOT_ENABLED(0xFF)** System został skompilowany z wyłączonymi możliwościami powiadomień.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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
> Jeśli ta usługa jest wywoływana z isr, wartość zwracana reprezentuje wątek uruchomiony przed wykonywaniem procedury obsługi przerwań.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

- wskaźnik wątku: wskaźnik do aktualnie wykonującego wątku. Jeśli żaden wątek nie jest wykonywany, zwracana wartość jest TX_NULL.

### <a name="allowed-from"></a>Dozwolone z

Wątki i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o wątku

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

- **thread_ptr:** Wskaźnik do bloku sterowania wątkami.
- **name:** wskaźnik do miejsca docelowego dla wskaźnika do nazwy wątku.
- **state:** wskaźnik do miejsca docelowego dla bieżącego stanu wykonywania wątku. Dopuszczalne są następujące wartości:
    - **TX_READY:**(0x00)
    - **TX_COMPLETED:**(0x01)
    - **TX_TERMINATED:**(0x02)
    - **TX_SUSPENDED:**(0x03)
    - **TX_SLEEP:**(0x04)
    - **TX_QUEUE_SUSP:**(0x05)
    - **TX_SEMAPHORE_SUSP:**(0x06)
    - **TX_EVENT_FLAG:**(0x07)
    - **TX_BLOCK_MEMORY:**(0x08)
    - **TX_BYTE_MEMORY:**(0x09)
    - **TX_MUTEX_SUSP:**(0x0D)

- **run_count:** wskaźnik do miejsca docelowego dla liczby przebiegów wątku. 
- **priority:** wskaźnik do miejsca docelowego priorytetu wątku.
- **preemption_threshold:** wskaźnik do miejsca docelowego dla progu wywłaszczenia wątku.
- **time_slice:** wskaźnik do miejsca docelowego dla wycinka czasu wątku. 
- **next_thread:** Wskaźnik do miejsca docelowego dla następnego utworzonego wskaźnika wątku.
- **suspended_thread:** Wskaźnik do miejsca docelowego dla wskaźnika do następnego wątku na liście zawieszenia.

> [!IMPORTANT]
> Dostarczenie parametru TX_NULL parametru oznacza, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne pobieranie informacji o wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik sterowania wątkami.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie informacji o wydajności wątku

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

Ta usługa pobiera informacje o wydajności określonego wątku.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o  wydajności, biblioteka i aplikacja SMP ThreadX muszą być TX_THREAD_ENABLE_PERFORMANCE_INFO zdefiniowane za pomocą zdefiniowanej biblioteki SMP ThreadX.

### <a name="parameters"></a>Parametry 

- **thread_ptr:** wskaźnik do wcześniej utworzonego wątku.
- **resumptions:** wskaźnik do miejsca docelowego dla liczby wznowień tego wątku.
- **suspensions**(zawieszenie): wskaźnik do miejsca docelowego dla liczby zawieszenia tego wątku.
- **solicited_preemptions:** wskaźnik do miejsca docelowego dla liczby wywłaszczeń w wyniku wywołania usługi interfejsu API ThreadX wykonanego przez ten wątek.
- **interrupt_preemptions:** wskaźnik do miejsca docelowego dla liczby wywłaszczeń tego wątku w wyniku przetwarzania przerwań.
- **priority_inversions:** wskaźnik do miejsca docelowego dla liczby inwersji priorytetów tego wątku.
- **time_slices:** wskaźnik do miejsca docelowego dla liczby razy tego wątku.
- **relinquishes:** Wskaźnik do miejsca docelowego dla liczby wątków wywłaszczanych przez ten wątek.
- **limity czasu:** wskaźnik do miejsca docelowego dla liczby limitów czasu wstrzymania w tym wątku.
- **wait_aborts:** Wskaźnik do miejsca docelowego dla liczby przerywań oczekiwania wykonanych w tym wątku.
- **last_preempted_by:** wskaźnik do miejsca docelowego wskaźnika wątku, który ostatnio wywłaszował ten wątek.

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności wątku.
- **TX_PTR_ERROR:**(0x03) Nieprawidłowy wskaźnik wątku.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

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

Uzyskiwanie informacji o wydajności systemu wątków

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
> Aby ta usługa zwracała informacje o  wydajności, biblioteka i aplikacja ThreadX SMP muszą TX_THREAD_ENABLE_PERFORMANCE_INFO z definicją.

### <a name="parameters"></a>Parametry

- **resumptions:** wskaźnik do miejsca docelowego dla całkowitej liczby wznowień wątków.
- **suspensions (zawieszenie):** wskaźnik do miejsca docelowego całkowitej liczby zawieszenia wątków.
- **solicited_preemptions:** wskaźnik do miejsca docelowego całkowitej liczby wywłaszczeń wątków w wyniku wywołania przez wątek usługi interfejsu API ThreadX.
- **interrupt_preemptions:** wskaźnik do miejsca docelowego całkowitej liczby wywłaszczeń wątków w wyniku przetwarzania przerwań.
- **priority_inversions:** wskaźnik do miejsca docelowego dla całkowitej liczby inversions priorytetów wątku.
- **time_slices:** wskaźnik do miejsca docelowego dla całkowitej liczby wycinków czasu wątku.
- **relinquishes:** Wskaźnik do miejsca docelowego dla całkowitej liczby wątków wywłaszcza.
- **limity czasu:** wskaźnik do miejsca docelowego dla całkowitej liczby limitów czasu wstrzymania wątku.
- **wait_aborts:** wskaźnik do miejsca docelowego dla całkowitej liczby przerywanych oczekiwania wątku. 
- **non_idle_returns:** wskaźnik do miejsca docelowego dla liczby powrotów wątku do systemu, gdy inny wątek jest gotowy do wykonania. 
- **idle_returns:** wskaźnik do miejsca docelowego dla liczby powrotów wątku do systemu, gdy żaden inny wątek nie jest gotowy do wykonania (system bezczynny).

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności systemu wątków.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

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

Zmiana progu wywłaszczenia wątku aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_preemption_change(TX_THREAD *thread_ptr,
                          UINT new_threshold, UINT *old_threshold);
```
### <a name="description"></a>Opis

Ta usługa zmienia próg wywłaszczenia określonego wątku. Próg wywłaszczenia zapobiega wywłaszczeniu określonego wątku przez wątki równe lub mniejsze niż wartość progowa wywłaszczenia.

> [!IMPORTANT]
> Użycie progu wywłaszczenia powoduje wyłączenie czasowego cing dla określonego wątku.

### <a name="parameters"></a>Parametry

- **thread_ptr:** wskaźnik do wcześniej utworzonego wątku aplikacji.
- **new_threshold:** nowy poziom priorytetu progu wywłaszczenia (od 0 do (TX_MAX_PRIORITIES-1)).
- **old_threshold:** Wskaźnik do lokalizacji, aby zwrócić poprzedni próg wywłaszczenia.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna zmiana progu wywłaszczenia.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- **TX_THRESH_ERROR:**(0x18) Określony nowy próg wywłaszczenia nie jest prawidłowym priorytetem wątku (wartość inną niż (od 0 do (TX_MAX_PRIORITIES-1)) lub jest większa niż (niższy priorytet) niż bieżący priorytet wątku.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do poprzedniej wywłaszczeniowej lokalizacji przechowywania.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Zmienianie priorytetu wątku aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_priority_change(TX_THREAD *thread_ptr,
                          UINT new_priority, UINT *old_priority);
```
### <a name="description"></a>Opis

Ta usługa zmienia priorytet określonego wątku. Prawidłowe priorytety z zakresu od 0 do (TX_MAX_PRIORITES-1), gdzie 0 reprezentuje najwyższy poziom priorytetu.

> [!IMPORTANT]
> Próg wywłaszczenia określonego wątku jest automatycznie ustawiany na nowy priorytet. Jeśli jest wymagany nowy próg, **tx_thread_preemption_change** musi być używana po tym wywołaniu.

### <a name="parameters"></a>Parametry

- **thread_ptr:** wskaźnik do wcześniej utworzonego wątku aplikacji.
- **new_priority:** nowy poziom priorytetu wątku (od 0 do (TX_MAX_PRIORITIES-1)).
- **old_priority:** wskaźnik do lokalizacji, aby zwrócić poprzedni priorytet wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna zmiana priorytetu.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- TX_PRIORITY_ERROR: (0x0F) Określony nowy priorytet jest nieprawidłowy (wartość inna niż (od 0 do (TX_MAX_PRIORITIES-1)).
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do poprzedniej lokalizacji przechowywania o priorytecie.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ponowne wymaganie kontrolki do innych wątków aplikacji

### <a name="prototype"></a>Prototype

```C
VOID tx_thread_relinquish(VOID);
```
### <a name="description"></a>Opis

Ta usługa zapewnia kontrolę procesora innym gotowym do uruchomienia wątkom o tym samym lub wyższym priorytecie.

> [!IMPORTANT]
> Oprócz rezygnacji z kontroli dla wątków o tym samym priorytecie, ta usługa również zwalnia kontrolę z wątku o najwyższym priorytecie, który nie może być wykonywania z powodu ustawienia progu wywłaszczania bieżącego wątku.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

Brak

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Resetowanie wątku

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Opis

Ta usługa resetuje określony wątek do wykonania w punkcie wejścia zdefiniowanym podczas tworzenia wątku. Wątek musi być w stanie **TX_COMPLETED** **lub TX_TERMINATED,** aby można go było zresetować

> [!IMPORTANT]
> Aby wątek został ponownie wykonany, należy go wznowić.

### <a name="parameters"></a>Parametry 

- **thread_ptr:** wskaźnik do wcześniej utworzonego wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne zresetowanie wątku.
- **TX_NOT_DONE:**(0x20) Określony wątek nie jest w stanie TX_COMPLETED lub TX_TERMINATED.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

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

Wznawianie wstrzymanego wątku aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Opis

Ta usługa wznawia lub przygotowuje do wykonania wątek, który został wcześniej wstrzymany przez ***tx_thread_suspend*** wywołania. Ponadto ta usługa wznawia wątki, które zostały utworzone bez automatycznego uruchamiania.

### <a name="parameters"></a>Parametry

- **thread_ptr:** Wskaźnik do zawieszonego wątku aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne wznowienie wątku.
- **TX_SUSPEND_LIFTED:**(0x19) Wcześniej ustawione opóźnione zawieszenie zostało podniesione.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- **TX_RESUME_ERROR:**(0x12) Określony wątek nie jest wstrzymany lub został wcześniej wstrzymany przez usługę inną **_niż tx_thread_suspend_**.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Wstrzymywanie bieżącego wątku na określony czas

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_sleep(ULONG timer_ticks);
```
### <a name="description"></a>Opis

Ta usługa powoduje wstrzymanie wątku wywołującego dla określonej liczby takt czasomierza. Czas fizyczny skojarzony z taktą czasomierza jest specyficzny dla aplikacji. Ta usługa może być wywoływana tylko z wątku aplikacji.

### <a name="parameters"></a>Parametry

- **timer_ticks:** liczba takt czasomierzy w celu wstrzymania wywołującego wątku aplikacji, od 0 do 0xFFFFFFFF. Jeśli określono wartość 0, usługa natychmiast zwraca wartość .

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uśpienie wątku.
- **TX_WAIT_ABORTED:**(0x1A) Zawieszenie zostało przerwane przez inny wątek, czasomierz lub isr.
- **TX_CALLER_ERROR:**(0x13) Wywoływana z niewątkowego.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Wykluczanie wykonywania wątku na zestawie rdzeni

### <a name="prototype"></a>Prototype

```C
UINT  tx_thread_smp_core_exclude(TX_THREAD *thread_ptr,
                          ULONG exclusion_map);
```
### <a name="description"></a>Opis

Ta funkcja wyklucza określony wątek z wykonywania na rdzeniach określonych w mapie bitów o nazwie "*exclusion_map."* Każdy bit w "*exclusion_map*" reprezentuje rdzeń (bit 0 reprezentuje rdzeń 0 itp.). Jeśli bit jest ustawiony, odpowiedni rdzeń jest wykluczony z wykonywania określonego wątku.

> [!IMPORTANT]
> Użycie wykluczenia procesora może spowodować dodatkowe przetwarzanie w logice mapowania wątku do rdzenia w celu znalezienia optymalnego dopasowania. To przetwarzanie jest ograniczone przez liczbę gotowych wątków.

### <a name="parameters"></a>Parametry 

- **thread_ptr:** Wskaźnik do wątku, aby zmienić podstawowe wykluczenie.
- **exclusion_map:** mapa bitowa, na której bit sytowy wskazuje, że rdzeń jest wykluczony. Po podaniem wartości 0 wątek może być wykonywany na dowolnym rdzeniu (ustawienie domyślne).

### <a name="return-values"></a>Wartości zwrócone

- TX_SUCCESS: (0x00) Pomyślne wykluczenie podstawowe.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, isr, wątki i czasomierze

### <a name="example"></a>Przykład

```C
/* Exclude core 0 for "Thread 0". */
tx_thread_smp_core_exclude(&thread_0, 0x01);
```

### <a name="see-also"></a>Zobacz też

- tx_thread_smp_core_exclude_get
- tx_thread_smp_core_get

## <a name="tx_thread_smp_core_exclude_get"></a>tx_thread_smp_core_exclude_get

Pobiera bieżące wykluczenie podstawowe wątku

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a>Opis

Ta funkcja zwraca bieżącą listę wykluczeń podstawowych.

### <a name="parameters"></a>Parametry

- **thread_ptr:** wskaźnik do wątku, z którego ma zostać pobrane wykluczenie podstawowe.
- **exclusion_map_ptr:** miejsce docelowe dla bieżącej mapy bitów wykluczenia podstawowego.

### <a name="return-values"></a>Wartości zwrócone

- TX_SUCCESS: (0x00) Pomyślne pobieranie wykluczenia podstawowego wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik miejsca docelowego wykluczenia.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, isr, wątki i czasomierze

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

Pobieranie aktualnie wykonywanego rdzenia wywołującego

### <a name="prototype"></a>Prototype

```C
UINT  tx_thread_smp_core_get(void);
```
### <a name="description"></a>Opis

Ta funkcja zwraca podstawowy identyfikator rdzenia wykonującego tę usługę.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

- core_id: identyfikator aktualnie wykonywanego rdzenia (od 0 do TX_THREAD_SMP_MAX_CORES-1)

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, isr, wątki i czasomierze

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

Rejestrowanie wywołania zwrotnego powiadomienia o błędzie stosu wątków

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```
### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego powiadomień do obsługi błędów stosu wątków. Gdy threadX SMP wykryje błąd stosu wątku podczas wykonywania, wywoła tę funkcję powiadomienia, aby przetworzyć błąd. Przetwarzanie błędu jest całkowicie zdefiniowane przez aplikację. Może zostać wykonane cokolwiek, od wstrzymania wątku naruszającego prawo do zresetowania całego systemu.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje  o wydajności, biblioteka SMP ThreadX musi TX_ENABLE_STACK_CHECKING z definicją.

### <a name="parameters"></a>Parametry

- **error_handler:** Wskaźnik do funkcji obsługi błędów stosu aplikacji. Jeśli ta wartość jest TX_NULL, powiadomienie zostanie wyłączone.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne zresetowanie wątku.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Ta usługa wstrzymuje określony wątek aplikacji. Wątek może wywołać tę usługę, aby samodzielnie wstrzymać.

> [!IMPORTANT]
> Jeśli określony wątek jest już zawieszony z innego powodu, to zawieszenie jest przechowywane wewnętrznie do momentu uniesienia wcześniejszego zawieszenia. W takim przypadku jest wykonywane to bezwarunkowe zawieszenie określonego wątku. Dalsze żądania wstrzymania bezwarunkowego nie mają żadnego efektu.

Po wstrzymaniu wątek musi zostać wznowiony przez ***tx_thread_resume*** do wykonania ponownie.

## <a name="parameters"></a>Parametry

- **thread_ptr:** wskaźnik do wątku aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne wstrzymanie wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- **TX_SUSPEND_ERROR:**(0x14) Określony wątek jest w stanie zakończenia lub zakończenia.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isr

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ta usługa kończy określony wątek aplikacji niezależnie od tego, czy wątek jest wstrzymany, czy nie. Wątek może wywołać tę usługę, aby zakończyć działanie.

> [!IMPORTANT]
> Po zakończeniu wątek musi zostać zresetowany, aby został ponownie wykonany.

> [!WARNING]
> Aplikacja odpowiada za zapewnienie, że wątek jest w stanie odpowiednim do zakończenia. Na przykład wątek nie powinien być przerywany podczas krytycznego przetwarzania aplikacji lub wewnątrz innych składników oprogramowania pośredniczącego, gdzie takie przetwarzanie może pozostawić w nieznanym stanie.

### <a name="parameters"></a>Parametry

- **thread_ptr:** Wskaźnik do wątku aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne zakończenie wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Zmienia fragment czasu wątku aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_time_slice_change(TX_THREAD *thread_ptr,
                          ULONG new_time_slice, ULONG *old_time_slice);
```
### <a name="description"></a>Opis

Ta usługa zmienia wycinek czasu określonego wątku aplikacji. Wybranie wycinka czasu dla wątku zapewnia, że nie będzie on wykonywany więcej niż określona liczba takt czasomierza, zanim inne wątki o tych samych lub wyższych priorytetach będą mieć możliwość wykonania.

> [!IMPORTANT]
> Użycie progu wywłaszczenia powoduje wyłączenie czasowego cing dla określonego wątku.

### <a name="parameters"></a>Parametry

- **thread_ptr:** Wskaźnik do wątku aplikacji.
- **new_time_slice:** Nowa wartość wycinka czasu. Wartości prawne obejmują TX_NO_TIME_SLICE i liczbowe od 1 do 0xFFFFFFFF.
- **old_time_slice:** wskaźnik do lokalizacji do przechowywania poprzedniej wartości czasu określonego wątku.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Prawdopodobieństwo pomyślnego fragmentu czasu.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do poprzedniej lokalizacji przechowywania w wycinku czasu.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki i czasomierze

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Przerwać zawieszenie określonego wątku

### <a name="prototype"></a>Prototype

```C
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Opis

Ta usługa przerywa tryb uśpienia lub wszelkie inne zawieszenie obiektu określonego wątku. Jeśli oczekiwanie zostało przerwane, TX_WAIT_ABORTED jest zwracana z usługi, na która oczekiwano wątku.

> [!IMPORTANT]
> Ta usługa nie zwalnia jawnego zawieszenia, które jest dokonywane przez tx_thread_suspend usługi.

### <a name="parameters"></a>Parametry

- **thread_ptr:** wskaźnik do wcześniej utworzonego wątku aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Przerwanie pomyślnego oczekiwania wątku.
- TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.
- **TX_WAIT_ABORT_ERROR:**(0x1B) Określony wątek nie jest w stanie oczekiwania.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobiera bieżący czas

### <a name="prototype"></a>Prototype

```C
ULONG tx_time_get(VOID);
```
### <a name="description"></a>Opis

Ta usługa zwraca zawartość wewnętrznego zegara systemowego. Każdy timertick zwiększa wewnętrzny zegar systemowy o jeden. Zegar systemowy jest ustawiony na zero podczas inicjowania i może zostać zmieniony na określoną wartość przez usługę ***tx_time_set***.

> [!IMPORTANT]
> Rzeczywista godzina, która reprezentuje każdy znacznik czasomierza, jest specyficzna dla aplikacji.

### <a name="parameters"></a>Parametry

Brak

### <a name="return-values"></a>Wartości zwrócone

- takty zegara systemu: wartość wewnętrznego, wolnego uruchamiania, zegar systemowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Ustawia bieżący czas

### <a name="prototype"></a>Prototype

```C
VOID tx_time_set(ULONG new_time);
```
### <a name="description"></a>Opis

Ta usługa ustawia wewnętrzny zegar systemowy na określoną wartość. Każdy znacznik czasomierza zwiększa wewnętrzny zegar systemowy o jeden.

> [!IMPORTANT]
> Rzeczywista godzina, która reprezentuje każdy znacznik czasomierza, jest specyficzna dla aplikacji.

### <a name="parameters"></a>Parametry

- **new_time:** nowy czas, aby umieścić w zegarze systemowym, wartości prawne z zakresu od 0 do 0xFFFFFFFF.

### <a name="return-values"></a>Wartości zwrócone

Brak

### <a name="allowed-from"></a>Dozwolone z

Wątki, czasomierze i isr

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Aktywowanie czasomierza aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```
### <a name="description"></a>Opis

Ta usługa aktywuje czasomierz określonej aplikacji. Procedury wygasania czasomierzy, które wygasają w tym samym czasie, są wykonywane w kolejności, w których zostały aktywowane.

> [!NOTE]
> Wygasły czasomierz jednozmijowy musi zostać zresetowany za **pośrednictwem tx_timer_change,** zanim będzie można go ponownie aktywować.

### <a name="parameters"></a>Parametry

- **timer_ptr:** wskaźnik do wcześniej utworzonego czasomierza aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna aktywacja czasomierza aplikacji.
- **TX_TIMER_ERROR:**(0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.
- **TX_ACTIVATE_ERROR:**(0x17) Czasomierz był już aktywny lub jest czasomierzem jednozmiejscowy, który już wygasł.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Zmiana czasomierza aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_change(TX_TIMER *timer_ptr,
                          ULONG initial_ticks, ULONG reschedule_ticks);
```
### <a name="description"></a>Opis

Ta usługa zmienia charakterystykę wygasania określonego czasomierza aplikacji. Czasomierz musi zostać zdezaktywowany przed wywołaniem tej usługi.

> [!IMPORTANT]
> Wywołanie usługi **tx_timer_activate** jest wymagane po tej usłudze, aby ponownie uruchomić czasomierz.

### <a name="parameters"></a>Parametry

- **timer_ptr:** Wskaźnik do bloku sterowania czasomierza.
- **initial_ticks:** określa początkową liczbę takt dla wygaśnięcia czasomierza. Wartości prawne wahają się od 1 do 0xFFFFFFFF.
- **reschedule_ticks:** określa liczbę takt dla wszystkich wygasa czasomierza po pierwszym. Wartość zero dla tego parametru sprawia, że czasomierz jest czasomierzem jednozdniowym. W przeciwnym razie w przypadku czasomierzy okresowych wartości prawne mogą być od 1 do 0xFFFFFFFF.

   > [!NOTE]
   > Wygasły czasomierz jednozdresowy musi zostać zresetowany za **pośrednictwem tx_timer_change,** zanim będzie można go ponownie aktywować.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna zmiana czasomierza aplikacji.
- TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.
- TX_TICK_ERROR: (0x16) Nieprawidłowa wartość (zero) dostarczona dla początkowych takt.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki, czasomierze i isr

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Tworzenie czasomierza aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_create(TX_TIMER *timer_ptr, CHAR *name_ptr,
                          VOID (*expiration_function)(ULONG),
                          ULONG expiration_input, ULONG initial_ticks,
                          ULONG reschedule_ticks, UINT auto_activate)
```
### <a name="description"></a>Opis

Ta usługa tworzy czasomierz aplikacji z określoną funkcją wygasania i okresową.

### <a name="parameters"></a>Parametry

- **timer_ptr:** wskaźnik do bloku kontrolki czasomierza
- **name_ptr:** Wskaźnik do nazwy czasomierza.
- **expiration_function:** funkcja aplikacji do wywołania po wygaśnięciu czasomierza.
- **expiration_input:** dane wejściowe do przekazania do funkcji wygasania po upływie czasu.
- **initial_ticks:** określa początkową liczbę takt dla wygaśnięcia czasomierza. Wartości prawne wahają się od 1 do 0xFFFFFFFF.
- **reschedule_ticks:** określa liczbę takt dla wszystkich wygasa czasomierza po pierwszym. Wartość zero dla tego parametru sprawia, że czasomierz jest czasomierzem jednozdniowym. W przeciwnym razie w przypadku czasomierzy okresowych wartości prawne mogą być od 1 do 0xFFFFFFFF.

   > [!NOTE]
   > Po wygaśnięciu czasomierza z jednym rzutem musi on zostać zresetowany za pośrednictwem tx_timer_change, zanim będzie można go ponownie aktywować.

- **auto_activate:** określa, czy czasomierz jest automatycznie aktywowany podczas tworzenia. Jeśli ta wartość jest **TX_AUTO_ACTIVATE** (0x01), czasomierz jest aktywny. W przeciwnym razie, **jeśli TX_NO_ACTIVATE** (0x00) jest wybrana, czasomierz jest tworzony w stanie nieaktywna. W takim przypadku kolejne wywołanie **_usługi tx_timer_activate_** jest niezbędne do faktycznie uruchomionego czasomierza.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne utworzenie czasomierza aplikacji.
- TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji. Wskaźnik ma wartość NULL lub czasomierz został już utworzony.
- TX_TICK_ERROR: (0x16) Nieprawidłowa wartość (zero) dostarczona dla początkowych takt.
- TX_ACTIVATE_ERROR: (0x17) Wybrana nieprawidłowa aktywacja.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Dezaktywacja czasomierza aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Opis

Ta usługa dezaktywuje czasomierz określonej aplikacji. Jeśli czasomierz jest już zdezaktywowany, ta usługa nie ma żadnego efektu.

### <a name="parameters"></a>Parametry 

- **timer_ptr:** wskaźnik do wcześniej utworzonego czasomierza aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślna dezaktywacja czasomierza aplikacji.
- TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Usuwanie czasomierza aplikacji

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```
### <a name="description"></a>Opis

Ta usługa usuwa czasomierz określonej aplikacji.

> [!IMPORTANT]
> Aplikacja odpowiada za zapobieganie używaniu usuniętego czasomierza.

### <a name="parameters"></a>Parametry 

- **timer_ptr:** wskaźnik do wcześniej utworzonego czasomierza aplikacji.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne usunięcie czasomierza aplikacji.
- TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.
- TX_CALLER_ERROR: (0x13) Nieprawidłowy wywołujący tę usługę.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Pobieranie informacji o czasomierzu aplikacji

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

- **timer_ptr:** wskaźnik do wcześniej utworzonego czasomierza aplikacji.
- **name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy czasomierza.
- **active:** wskaźnik do miejsca docelowego dla aktywnego wskazania czasomierza. Jeśli czasomierz jest nieaktywny lub ta usługa jest wywoływana z samego czasomierza, zwracana jest TX_FALSE wartość. W przeciwnym razie, jeśli czasomierz jest aktywny, TX_TRUE zwracana jest wartość.
- **remaining_ticks:** wskaźnik do miejsca docelowego dla liczby takt czasomierza, które pozostały przed wygaśnięciem czasomierza.
- **reschedule_ticks:** wskaźnik do miejsca docelowego dla liczby takt czasomierzy, które będą używane do automatycznego ponownego edukacji tego czasomierza. Jeśli wartość wynosi zero, czasomierz jest jednym rzutem i nie będzie ponownie mierzony.
- **next_timer:** Wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego czasomierza aplikacji.

> [!NOTE]
> Dostarczenie parametru TX_NULL parametru oznacza, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne pobieranie informacji o czasomierzu.
- TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

### <a name="preemption-possible"></a>Możliwe wywłasznia

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

Uzyskiwanie informacji o wydajności czasomierza

### <a name="prototype"></a>Prototype

```C
UINT  tx_timer_performance_info_get(TX_TIMER *timer_ptr,
        ULONG *activates, ULONG *reactivates,
        ULONG *deactivates, ULONG *expirations,
        ULONG *expiration_adjusts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności określonego czasomierza aplikacji.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o wydajności, biblioteka i aplikacja SMP **ThreadX** muszą TX_TIMER_ENABLE_PERFORMANCE_INFO za pomocą zdefiniowanych dla tej usługi.

### <a name="parameters"></a>Parametry 

- **timer_ptr:** wskaźnik do wcześniej utworzonego czasomierza.
- **aktywuje**: wskaźnik do miejsca docelowego dla liczby żądań aktywacji wykonanych na tym czasomierzu.
- **reaktywacja:** wskaźnik do miejsca docelowego dla liczby automatycznych ponownych aktywacji wykonywanych na tym czasomierzu okresowym.
- **dezaktywuje**: wskaźnik do miejsca docelowego dla liczby żądań dezaktywacji wykonanych na tym czasomierzu.
- **expirations**: wskaźnik do miejsca docelowego dla liczby wygaśnięcia tego czasomierza.
- **expiration_adjusts:** Wskaźnik do miejsca docelowego dla liczby wewnętrznych korekt wygaśnięcia wykonywanych na tym czasomierzu. Te korekty są wykonywane w przetwarzaniu przerwań czasomierza dla czasomierzy większych niż domyślny rozmiar listy czasomierzy (domyślnie czasomierze z wygaśnięciami większymi niż 32 takty).

> [!IMPORTANT]
> Dostarczenie parametru TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności czasomierza.
- **TX_PTR_ERROR:**(0x03) Nieprawidłowy wskaźnik czasomierza.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Uzyskiwanie informacji o wydajności systemu czasomierza

### <a name="prototype"></a>Prototype

```C
UINT  tx_timer_performance_system_info_get(ULONG *activates,
        ULONG *reactivates, ULONG *deactivates,
        ULONG *expirations, ULONG *expiration_adjusts);
```
### <a name="description"></a>Opis

Ta usługa pobiera informacje o wydajności wszystkich czasomierzy aplikacji w systemie.

> [!IMPORTANT]
> Aby ta usługa zwracała informacje o wydajności, biblioteka i aplikacja ThreadX SMP muszą **TX_TIMER_ENABLE_PERFORMANCE_INFO** z definicją.

### <a name="parameters"></a>Parametry

- **aktywuje:** wskaźnik do miejsca docelowego dla łącznej liczby żądań aktywacji wykonanych na wszystkich czasomierzach.
- **reaktywacja:** wskaźnik do miejsca docelowego dla całkowitej liczby automatycznych ponownych aktywacji wykonywanych na wszystkich czasomierzach okresowych.
- **deactivates**: wskaźnik do miejsca docelowego dla łącznej liczby żądań dezaktywacji wykonanych na wszystkich czasomierzach.
- **expirations**: wskaźnik do miejsca docelowego dla całkowitej liczby wygaśnięcia na wszystkich czasomierzach.
- **expiration_adjusts:** Wskaźnik do miejsca docelowego dla całkowitej liczby wewnętrznych korekt wygaśnięcia wykonanych na wszystkich czasomierzach. Te korekty są wykonywane w przetwarzaniu przerwań czasomierza dla czasomierzy, które są większe niż domyślny rozmiar listy czasomierzy (domyślnie czasomierze z wygaśnięciami większymi niż 32 takty).

> [!IMPORTANT]
> Dostarczenie wartości TX_NULL parametru wskazuje, że parametr nie jest wymagany.

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS:**(0x00) Pomyślne uzyskiwanie wydajności systemu czasomierza.
- **TX_FEATURE_NOT_ENABLED:**(0xFF) System nie został skompilowany z włączonymi informacjami o wydajności.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki, czasomierze i isR

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

Wykluczanie wykonywania czasomierza na zestawie rdzeni

### <a name="prototype"></a>Prototype

```C
UINT  tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);
```
### <a name="description"></a>Opis

Ta funkcja wyklucza określony czasomierz z wykonywania na rdzeniach określonych w mapie bitowej o nazwie "*exclusion_map."* Każdy bit w "*exclusion_map*" reprezentuje rdzeń (bit 0 reprezentuje rdzeń 0 itp.). Jeśli bit jest ustawiony, odpowiedni rdzeń jest wykluczony z wykonywania określonego czasomierza.

> [!IMPORTANT]
> Użycie wykluczenia procesora może spowodować dodatkowe przetwarzanie w logice mapowania wątku do rdzenia w celu znalezienia optymalnego dopasowania. To przetwarzanie jest ograniczone przez liczbę gotowych wątków.

### <a name="parameters"></a>Parametry

- **timer_ptr:** Wskaźnik do czasomierza w celu zmiany wykluczenia podstawowego.
- **exclusion_map:** mapa bitowa, na której bit sycowy wskazuje, że rdzeń jest wykluczony. Po podaniem wartości 0 czasomierz może być wykonywany na dowolnym rdzeniu (ustawienie domyślne).

### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0x00) Pomyślne wykluczenie podstawowe.
- **TX_TIMER_ERROR** (0x0E) Nieprawidłowy wskaźnik czasomierza.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, isr, wątki i czasomierze

### <a name="example"></a>Przykład

```C
/* Exclude core 0 for "Timer 0". */
tx_timer_smp_core_exclude(&timer_0, 0x01);
```

### <a name="see-also"></a>Zobacz też

- tx_timer_smp_core_exclude_get

## <a name="tx_timer_smp_core_exclude_get"></a>tx_timer_smp_core_exclude_get

Pobiera bieżące wykluczenie podstawowe czasomierza

### <a name="prototype"></a>Prototype

```C
UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a>Opis

Ta funkcja zwraca bieżącą listę wykluczeń podstawowych.

### <a name="parameters"></a>Parametry

- **timer_ptr:** wskaźnik do czasomierza, z którego ma zostać pobrane wykluczenie podstawowe.
- **exclusion_map_ptr:** miejsce docelowe dla bieżącej mapy bitów wykluczenia podstawowego.

### <a name="return-values"></a>Wartości zwrócone

- TX_SUCCESS: (0x00) Pomyślne pobranie wykluczenia podstawowego czasomierza.
- TX_TIMER_ERROR: (0x0E) Nieprawidłowy wskaźnik czasomierza.
- TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik miejsca docelowego wykluczenia.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, isr, wątki i czasomierze

### <a name="example"></a>Przykład

```C
ULONGexcluded_cores;

/* Retrieve the core exclusion for "Timer 0". */
tx_timer_smp_core_exclude_get(&timer_0,&excluded_cores);
```
### <a name="see-also"></a>Zobacz też

- tx_timer_smp_core_exclude