---
title: Rozdział 5 — generowanie buforów śledzenia
description: Ten rozdział zawiera opis sposobu tworzenia buforu zdarzeń usługi Azure RTO TraceX, a także opis źródłowego formatu buforu.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: f296137d23b9f3c1c4fd115947bb50a32b768123
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823425"
---
# <a name="chapter-5---generating-trace-buffers"></a>Rozdział 5 — generowanie buforów śledzenia

Ten rozdział zawiera opis sposobu tworzenia buforu zdarzeń usługi Azure RTO TraceX, a także opis źródłowego formatu buforu.

## <a name="threadx-event-trace-support"></a>Obsługa śledzenia zdarzeń ThreadX

ThreadX zapewnia wbudowaną obsługę śledzenia zdarzeń dla wszystkich usług ThreadX, zmian stanu wątków i zdarzeń zdefiniowanych przez użytkownika. Funkcja śledzenia zdarzeń ThreadX jest przeznaczona głównie do analizowania ostatnich działań "n" w aplikacji. Z tych informacji deweloperzy mogą wychwycić problemy i/lub potencjalne cele optymalizacji.

TraceX graficznie wyświetla bufor śledzenia zdarzeń zbudowany przez ThreadX. Poniżej opisano sposób tworzenia buforu i opisuje podstawowy format buforu.

## <a name="enabling-event-trace"></a>Włączanie śledzenia zdarzeń

Aby włączyć śledzenie zdarzeń, zdefiniuj stałe sygnatur czasowych, skompiluj bibliotekę ThreadX z zdefiniowanym **TX_ENABLE_EVENT_TRACE** i Włącz śledzenie, wywołując funkcję **tx_trace_enable** .

## <a name="defining-time-stamp-constants"></a>Definiowanie Time-Stamp stałych

Stałe sygnatur czasowych zostały zaprojektowane w celu udostępnienia kontrolki dla deweloperów względem sygnatury czasowej używanej w wpisach śledzenia zdarzeń. Dwie stałe sygnatury czasowej i ich wartości domyślne są następujące:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

Powyższe stałe są zdefiniowane w **tx_port. h** i tworzą "fałszywą" sygnaturę czasową, która po prostu zwiększa się o jeden dla każdego zdarzenia. Poniżej znajduje się przykład rzeczywistej definicji sygnatur czasowych:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

Powyższe stałe określają 32-bitowy czasomierz, który jest uzyskiwany poprzez odczytywanie adresu 0x13000004. Większość sygnatur czasowych specyficznych dla aplikacji powinna być skonfigurowana w podobny sposób.

## <a name="exporting-the-trace-buffer"></a>Eksportowanie buforu śledzenia

TraceX potrzebuje buforu śledzenia w formacie pliku binarnego, SZESNASTKOWym Intel lub Motorola S-Record na hoście. Najprostszym sposobem, aby to zrobić, jest zatrzymanie obiektu docelowego i nakazuje debugerowi Zrzut obszaru pamięci dostarczonego do ***tx_trace_enable*** funkcji do pliku na hoście.

> [!WARNING]
>***Należy zachować ostrożność, aby nie zatrzymywać elementu docelowego w samym kodzie zbierania śladu. Wykonanie tej operacji może spowodować nieprawidłowe informacje o śledzeniu. Jeśli program jest zatrzymany w ThreadX, najlepiej wykonać krok przed każdym makrem wstawiania śledzenia przed zatopieniem bufora śledzenia.***

> [!IMPORTANT]
> *Dodatek D pokazuje, jak zrzucić bufor śledzenia z różnych narzędzi programistycznych.*

## <a name="extended-event-trace-api"></a>Rozszerzony interfejs API śledzenia zdarzeń

Po skompilowaniu ThreadX z zdefiniowanymi **TX_ENABLE_EVENT_TRACE** , następujące nowe interfejsy API śledzenia zdarzeń są dostępne dla aplikacji:

- tx_trace_enable: *Włącz śledzenie zdarzeń*
- tx_trace_event_filter: *Filtruj określone zdarzenia*
- tx_trace_event_unfilter: *odfiltruj określone zdarzenia*
- tx_trace_disable: *wyłączanie śledzenia zdarzeń*
- tx_trace_isr_enter_insert: *Wstawianie zdarzenia ISR wprowadź zdarzenie śledzenia*
- tx_trace_isr_exit_insert: *Wstaw zdarzenie śledzenia wyjścia ISR*
- tx_trace_buffer_full_notify: *Rejestrowanie wywołania zwrotnego pełnej aplikacji w buforze śledzenia*
- tx_trace_user_event_insert: *Wstawianie zdarzenia użytkownika*

### <a name="tx_trace_enable"></a>tx_trace_enable

Włącz śledzenie zdarzeń

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a>Opis
Ta usługa umożliwia śledzenie zdarzeń w programie ThreadX. Bufor śledzenia i Maksymalna liczba obiektów ThreadX są dostarczane przez aplikację.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.

#### <a name="input-parameters"></a>Parametry wejściowe

- **trace_buffer_start**: wskaźnik na początku buforu śledzenia dostarczonego przez użytkownika.
- **trace_buffer_size**: całkowita liczba bajtów w pamięci dla buforu śledzenia. Im większy bufor śledzenia, tym większa jest możliwość przechowywania.
- **registry_entries**: liczba obiektów ThreadX aplikacji, które mają być przechowywane w rejestrze śledzenia. Rejestr jest używany do skorelowania adresów obiektów z nazwami obiektów. Jest to bardzo przydatne w przypadku graficznego interfejsu użytkownika narzędzia do analizy śledzenia.

#### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0X00) pomyślne Włączenie śledzenia zdarzeń.
- **TX_SIZE_ERROR** (0X05) określony rozmiar buforu śledzenia jest zbyt mały. Musi być wystarczająco duży dla nagłówka śledzenia, rejestru obiektów i co najmniej jednego wpisu śledzenia.
- Śledzenie zdarzeń **TX_NOT_DONE** (0x20) zostało już włączone.
- System **TX_FEATURE_NOT_ENABLED** (0xFF) nie został skompilowany z włączonym śledzeniem.

#### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

#### <a name="example"></a>Przykład

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_event_filter"></a>tx_trace_event_filter

Filtrowanie określonych zdarzeń

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a>Opis

Ta usługa filtruje określone zdarzenia z wstawienia do aktywnego buforu śledzenia. Należy pamiętać, że domyślnie żadne zdarzenia nie są filtrowane po wywołaniu *tx_trace_enable* .

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.

#### <a name="input-parameters"></a>Parametry wejściowe

- **event_filter_bits**: bity odpowiadające zdarzeniom do filtrowania. Wiele zdarzeń może być filtrowanych przez oring ze sobą odpowiednie stałe. Prawidłowe stałe dla tej zmiennej są zdefiniowane w następujący sposób:

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a>Wartości zwrócone

- Filtr zdarzenia pomyślnego **TX_SUCCESS** (0x00).
- System **TX_FEATURE_NOT_ENABLED** (0xFF) nie został skompilowany z włączonym śledzeniem.

#### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

#### <a name="example"></a>Przykład

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_event_unfilter"></a>tx_trace_event_unfilter

Odfiltruj określone zdarzenia

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a>Opis

Ta usługa umożliwia odfiltrowanie określonych zdarzeń w taki sposób, aby były one wstawiane do aktywnego buforu śledzenia.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.

#### <a name="input-parameters"></a>Parametry wejściowe

- **event_unfilter_bits**: bity odpowiadające zdarzeniom do odfiltrowania. Wiele zdarzeń może być niefiltrowanych przez zwykłe lub, w połączeniu z odpowiednimi stałymi. Prawidłowe stałe dla tej zmiennej są zdefiniowane w następujący sposób:

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a>Wartości zwrócone

- Odfiltrowanie zdarzenia powiodło się **TX_SUCCESS** (0x00).
- System **TX_FEATURE_NOT_ENABLED** (0xFF) nie został skompilowany z włączonym śledzeniem.

#### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

#### <a name="example"></a>Przykład

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_disable"></a>tx_trace_disable

#### <a name="disable-event-tracing"></a>Wyłącz śledzenie zdarzeń

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a>Opis

Ta usługa wyłącza śledzenie zdarzeń wewnątrz ThreadX. Może to być przydatne, jeśli aplikacja chce zablokować bieżący bufor śledzenia zdarzeń i ewentualnie transportować go zewnętrznie w czasie wykonywania. Po wyłączeniu **tx_trace_enable** można wywołać, aby ponownie uruchomić śledzenie.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.

#### <a name="input-parameters"></a>Parametry wejściowe

Brak.

#### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0X00) pomyślne wyłączenie śledzenia zdarzeń.
- Śledzenie zdarzeń **TX_NOT_DONE** (0x20) nie zostało włączone.
- System **TX_FEATURE_NOT_ENABLED** (0xFF) nie został skompilowany z włączonym śledzeniem.

#### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

#### <a name="example"></a>Przykład 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_enter_insert"></a>tx_trace_isr_enter_insert

#### <a name="insert-isr-enter-event"></a>Wstaw zdarzenie przejścia do procedury ISR

#### <a name="prototype"></a>Prototype

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a>Opis

Ta usługa wstawia zdarzenie przejścia ISR do buforu śledzenia zdarzeń. Powinien być wywoływany przez aplikację na początku przetwarzania w ramach procedury ISR. Podany parametr powinien identyfikować konkretne przeisr do aplikacji.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.

#### <a name="input-parameters"></a>Parametry wejściowe 
- **isr_id**: wartość specyficzna dla aplikacji w celu zidentyfikowania procedury ISR.

#### <a name="return-values"></a>Wartości zwrócone

**Brak**

#### <a name="allowed-from"></a>Dozwolone z 

Procedury ISR

#### <a name="example"></a>Przykład

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_exit_insert"></a>tx_trace_isr_exit_insert

#### <a name="insert-isr-exit-event"></a>Wstaw zdarzenie zakończenia procedury ISR

#### <a name="prototype"></a>Prototype

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a>Opis

Ta usługa wstawia zdarzenie wpisu ISR do buforu śledzenia zdarzeń. Powinien być wywoływany przez aplikację na początku przetwarzania w ramach procedury ISR. Podany parametr powinien identyfikować przeisr do aplikacji.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.

#### <a name="input-parameters"></a>Parametry wejściowe 

- **isr_id**: wartość specyficzna dla aplikacji w celu zidentyfikowania procedury ISR.

#### <a name="return-values"></a>Wartości zwrócone

**Brak**

#### <a name="allowed-from"></a>Dozwolone z

Procedury ISR

#### <a name="example"></a>Przykład

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_buffer_full_notify"></a>tx_trace_buffer_full_notify

#### <a name="register-trace-buffer-full-application-callback"></a>Rejestrowanie wywołania zwrotnego pełnej aplikacji w buforze śledzenia

#### <a name="prototype"></a>Prototype

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego aplikacji, która jest wywoływana przez ThreadX, gdy bufor śledzenia zostanie zapełniony. Następnie aplikacja może wybrać wyłączenie śledzenia i/lub prawdopodobnie konfigurację nowego buforu śledzenia.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.

#### <a name="input-parameters"></a>Parametry wejściowe

- **full_buffer_callback**: funkcja aplikacji do wywołania, gdy bufor śledzenia jest pełny. Wartość NULL powoduje wyłączenie wywołania zwrotnego powiadomienia.

#### <a name="return-values"></a>Wartości zwrócone

**Brak**

#### <a name="allowed-from"></a>Dozwolone z

Procedury ISR

#### <a name="example"></a>Przykład

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert

### <a name="tx_trace_user_event_insert"></a>tx_trace_user_event_insert

#### <a name="insert-user-event"></a>Wstaw zdarzenie użytkownika

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a>Opis

Ta usługa wstawia zdarzenie użytkownika do buforu śledzenia. Identyfikatory zdarzeń użytkownika muszą być większe niż stałe **TX_TRACE_USER_EVENT_START**, które jest zdefiniowane jako 4096. Wartość maksymalnego zdarzenia użytkownika jest definiowana przez **TX_TRACE_USER_EVENT_END** stałą, która jest zdefiniowana jako 65535. Wszystkie zdarzenia należące do tego zakresu są dostępne dla aplikacji. Pola informacji są specyficzne dla aplikacji.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.

#### <a name="input-parameters"></a>Parametry wejściowe

- **event_id**: Identyfikacja zdarzeń specyficznych dla aplikacji musi być większa niż **TX_TRACE_USER_EVENT_START** i mniejsza niż lub równa **TX_TRACE_USER_EVENT_END**.
- **info_field_1**: informacje specyficzne dla aplikacji.
- **info_field_2**: informacje specyficzne dla aplikacji.
- **info_field_3**: informacje specyficzne dla aplikacji.
- **info_field_4**: informacje specyficzne dla aplikacji.

#### <a name="return-values"></a>Wartości zwrócone
- **TX_SUCCESS** (0X00) pomyślne Wstawianie zdarzeń przez użytkownika.
- Śledzenie zdarzeń **TX_NOT_DONE** (0x20) nie jest włączone.
- **TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonym śledzeniem.

#### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

#### <a name="example"></a>Przykład

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify