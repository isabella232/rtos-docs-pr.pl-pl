---
title: Rozdział 5 — Generowanie buforów śledzenia
description: Ten rozdział zawiera opis sposobu tworzenia buforu zdarzeń Azure RTOS TraceX oraz podstawowy format buforu.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 7d5c90675728fc7e374d625f5a9ae27340268ca8398200c68fb7113a84aa2983
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801788"
---
# <a name="chapter-5---generating-trace-buffers"></a>Rozdział 5 — Generowanie buforów śledzenia

Ten rozdział zawiera opis sposobu tworzenia buforu zdarzeń Azure RTOS TraceX oraz podstawowy format buforu.

## <a name="threadx-event-trace-support"></a>Obsługa śledzenia zdarzeń ThreadX

ThreadX zapewnia wbudowaną obsługę śledzenia zdarzeń dla wszystkich usług ThreadX, zmian stanu wątku i zdarzeń zdefiniowanych przez użytkownika. Funkcja śledzenia zdarzeń ThreadX została zaprojektowana głównie jako narzędzie post mortem do analizowania ostatnich "n" działań w aplikacji. Na tych informacjach deweloper może wykryć problemy i/lub potencjalne cele optymalizacji.

TraceX wyświetla graficznie bufor śledzenia zdarzeń sbudowaną przez ThreadX. Poniżej opisano sposób kompilowania buforu i opisano podstawowy format buforu.

## <a name="enabling-event-trace"></a>Włączanie śledzenia zdarzeń

Aby włączyć śledzenie zdarzeń, zdefiniuj stałe sygnatury  czasowej, skompilować bibliotekę ThreadX przy użyciu TX_ENABLE_EVENT_TRACE i włączyć śledzenie, wywołując **funkcję tx_trace_enable.**

## <a name="defining-time-stamp-constants"></a>Definiowanie Time-Stamp stałych

Stałe sygnatury czasowej są przeznaczone do zapewnienia deweloperowi kontroli nad sygnaturą czasową używaną w wpisach śledzenia zdarzeń. Dwie stałe sygnatury czasowej i ich wartości domyślne są następujące:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

Powyższe stałe są definiowane w **tx_port.h** i tworzą "fałszywy" znacznik czasu, który po prostu zwiększa się o jeden dla każdego zdarzenia. Poniżej przedstawiono przykład rzeczywistej definicji znacznika czasu:

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

Powyższe stałe określają czasomierz 32-bitowy uzyskany przez odczytanie adresu 0x13000004. Większość znaczników czasu specyficznych dla aplikacji powinna być konfigurowana w podobny sposób.

## <a name="exporting-the-trace-buffer"></a>Eksportowanie buforu śledzenia

TraceX wymaga buforu śledzenia w formacie binarnym Intel HEX lub Csv S-Record na hoście. Najprostszym sposobem osiągnięcia tego celu jest zatrzymanie obiektu docelowego i poinstruuj debuger, aby zrzucił obszar pamięci dostarczony do funkcji ***tx_trace_enable*** do pliku na hoście.

> [!WARNING]
>***Należy uważać, aby nie zatrzymywać obiektu docelowego w obrębie samego kodu zbierania śladów. Może to spowodować nieprawidłowe informacje śledzenia. Jeśli program zostanie zatrzymany w threadX, przed zrzucaniem buforu śledzenia najlepiej przestępować przez dowolne makro wstawiania śledzenia.***

> [!IMPORTANT]
> *Dodatek D pokazuje, jak zrzucić bufor śledzenia z różnych narzędzi programistów.*

## <a name="extended-event-trace-api"></a>Rozszerzony interfejs API śledzenia zdarzeń

Gdy threadX jest **budowany TX_ENABLE_EVENT_TRACE** zdefiniowane, następujące nowe interfejsy API śledzenia zdarzeń są dostępne dla aplikacji:

- tx_trace_enable: Włączanie *śledzenia zdarzeń*
- tx_trace_event_filter: *Filtrowanie określonych zdarzeń*
- tx_trace_event_unfilter: *Niefiltruj określone zdarzenia*
- tx_trace_disable: Wyłączanie *śledzenia zdarzeń*
- tx_trace_isr_enter_insert: *Wstawianie zdarzenia śledzenia przez isr*
- tx_trace_isr_exit_insert: Wstaw *zdarzenie śledzenia zakończenia isr*
- tx_trace_buffer_full_notify: Rejestrowanie *pełnego wywołania zwrotnego aplikacji buforu śledzenia*
- tx_trace_user_event_insert: *Wstawianie zdarzenia użytkownika*

### <a name="tx_trace_enable"></a>tx_trace_enable

Włączanie śledzenia zdarzeń

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a>Opis
Ta usługa umożliwia śledzenie zdarzeń wewnątrz ThreadX. Bufor śledzenia i maksymalna liczba obiektów ThreadX są dostarczane przez aplikację.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą **TX_ENABLE_EVENT_TRACE** zdefiniowane za pomocą funkcji śledzenia zdarzeń.

#### <a name="input-parameters"></a>Parametry wejściowe

- **trace_buffer_start:** wskaźnik na początek buforu śledzenia dostarczonego przez użytkownika.
- **trace_buffer_size:** łączna liczba bajtów w pamięci buforu śledzenia. Im większy bufor śledzenia, tym więcej wpisów jest w stanie przechowywać.
- **registry_entries:** liczba obiektów ThreadX aplikacji do utrzymania w rejestrze śledzenia. Rejestr służy do korelowania adresów obiektów z nazwami obiektów. Jest to bardzo przydatne w przypadku narzędzi do analizy śledzenia graficznego interfejsu użytkownika.

#### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0x00) Włączanie śledzenia zdarzeń pomyślne.
- **TX_SIZE_ERROR** (0x05) Określony rozmiar buforu śledzenia jest zbyt mały. Musi być wystarczająco duży dla nagłówka śledzenia, rejestru obiektów i co najmniej jednego wpisu śledzenia.
- **TX_NOT_DONE** (0x20) Śledzenie zdarzeń zostało już włączone.
- **TX_FEATURE_NOT_ENABLED** (0xFF) System nie został skompilowany z włączonym śledzeniem.

#### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

Ta usługa filtruje określone zdarzenia przed wstawieniu do aktywnego buforu śledzenia. Należy pamiętać, że domyślnie po wywołaniu tx_trace_enable nie *są filtrowane* żadne zdarzenia.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą **TX_ENABLE_EVENT_TRACE** zdefiniowane za pomocą funkcji śledzenia zdarzeń.

#### <a name="input-parameters"></a>Parametry wejściowe

- **event_filter_bits:** bity, które odpowiadają zdarzeniam do filtrowania. Wiele zdarzeń można filtrować przez proste lub wspólne odpowiednie stałe. Prawidłowe stałe dla tej zmiennej są zdefiniowane w następujący sposób:

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

- **TX_SUCCESS** (0x00) Filtr zdarzeń Powodzenie.
- **TX_FEATURE_NOT_ENABLED** (0xFF) System nie został skompilowany z włączonym śledzeniem.

#### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

#### <a name="example"></a>Przykład

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_event_unfilter"></a>tx_trace_event_unfilter

Niefiltruj określone zdarzenia

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a>Opis

Ta usługa odfiltruje określone zdarzenia, tak aby zostały wstawione do aktywnego buforu śledzenia.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą **TX_ENABLE_EVENT_TRACE** zdefiniowane za pomocą funkcji śledzenia zdarzeń.

#### <a name="input-parameters"></a>Parametry wejściowe

- **event_unfilter_bits:** bity, które odpowiadają zerowym warunkom filtrowania. Wiele zdarzeń może być niefiltrowanych przez proste lub ing razem odpowiednie stałe. Prawidłowe stałe dla tej zmiennej są zdefiniowane w następujący sposób:

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

- **TX_SUCCESS** (0x00) Niefiltrowane pomyślne zdarzenie.
- **TX_FEATURE_NOT_ENABLED** (0xFF) System nie został skompilowany z włączonym śledzeniem.

#### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

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

#### <a name="disable-event-tracing"></a>Wyłączanie śledzenia zdarzeń

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a>Opis

Ta usługa wyłącza śledzenie zdarzeń wewnątrz ThreadX. Może to być przydatne, jeśli aplikacja chce zablokować bieżący bufor śledzenia zdarzeń i prawdopodobnie transportować go zewnętrznie w czasie działania. Po wyłączeniu **tx_trace_enable,** aby ponownie rozpocząć śledzenie.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą **TX_ENABLE_EVENT_TRACE** zdefiniowane za pomocą funkcji śledzenia zdarzeń.

#### <a name="input-parameters"></a>Parametry wejściowe

Brak.

#### <a name="return-values"></a>Wartości zwrócone

- **TX_SUCCESS** (0x00) Wyłączenie śledzenia zdarzeń pomyślne.
- **TX_NOT_DONE** (0x20) Śledzenie zdarzeń nie zostało włączone.
- **TX_FEATURE_NOT_ENABLED** (0xFF) System nie został skompilowany z włączonym śledzeniem.

#### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

#### <a name="example"></a>Przykład 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_enter_insert"></a>tx_trace_isr_enter_insert

#### <a name="insert-isr-enter-event"></a>Wstawianie zdarzenia wprowadzania isr

#### <a name="prototype"></a>Prototype

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a>Opis

Ta usługa wstawia zdarzenie wprowadzania isr do buforu śledzenia zdarzeń. Powinien on być wywoływany przez aplikację na początku przetwarzania isr. Podany parametr powinien identyfikować specyficzny dla aplikacji isr.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą **TX_ENABLE_EVENT_TRACE** zdefiniowane za pomocą funkcji śledzenia zdarzeń.

#### <a name="input-parameters"></a>Parametry wejściowe 
- **isr_id:** Wartość specyficzna dla aplikacji do identyfikowania isr.

#### <a name="return-values"></a>Wartości zwrócone

**Brak**

#### <a name="allowed-from"></a>Dozwolone z 

Isrs

#### <a name="example"></a>Przykład

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_isr_exit_insert"></a>tx_trace_isr_exit_insert

#### <a name="insert-isr-exit-event"></a>Wstaw zdarzenie zakończenia isr

#### <a name="prototype"></a>Prototype

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a>Opis

Ta usługa wstawia zdarzenie wpisu ISR do buforu śledzenia zdarzeń. Powinien on być wywoływany przez aplikację na początku przetwarzania isr. Podany parametr powinien identyfikować usługę ISR dla aplikacji.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą **TX_ENABLE_EVENT_TRACE** zdefiniowane za pomocą funkcji śledzenia zdarzeń.

#### <a name="input-parameters"></a>Parametry wejściowe 

- **isr_id:** Wartość specyficzna dla aplikacji do identyfikowania isr.

#### <a name="return-values"></a>Wartości zwrócone

**Brak**

#### <a name="allowed-from"></a>Dozwolone z

Isrs

#### <a name="example"></a>Przykład

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert

### <a name="tx_trace_buffer_full_notify"></a>tx_trace_buffer_full_notify

#### <a name="register-trace-buffer-full-application-callback"></a>Rejestrowanie pełnego wywołania zwrotnego aplikacji bufora śledzenia

#### <a name="prototype"></a>Prototype

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a>Opis

Ta usługa rejestruje funkcję wywołania zwrotnego aplikacji, która jest wywoływana przez threadX, gdy bufor śledzenia jest pełny. Następnie aplikacja może wyłączyć śledzenie i/lub ewentualnie skonfigurować nowy bufor śledzenia.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą **TX_ENABLE_EVENT_TRACE** zdefiniowane za pomocą funkcji śledzenia zdarzeń.

#### <a name="input-parameters"></a>Parametry wejściowe

- **full_buffer_callback:** funkcja aplikacji do wywołania, gdy bufor śledzenia jest pełny. Wartość NULL wyłącza wywołanie zwrotne powiadomień.

#### <a name="return-values"></a>Wartości zwrócone

**Brak**

#### <a name="allowed-from"></a>Dozwolone z

Isrs

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

#### <a name="insert-user-event"></a>Wstawianie zdarzenia użytkownika

#### <a name="prototype"></a>Prototype

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a>Opis

Ta usługa wstawia zdarzenie użytkownika do buforu śledzenia. Identyfikatory zdarzeń użytkownika muszą być większe niż stała **TX_TRACE_USER_EVENT_START**, która jest zdefiniowana jako 4096. Maksymalne zdarzenie użytkownika jest definiowane przez **stałą TX_TRACE_USER_EVENT_END**, która jest zdefiniowana jako 65535. Wszystkie zdarzenia w tym zakresie są dostępne dla aplikacji. Pola informacji są specyficzne dla aplikacji.

> [!IMPORTANT]
> Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą **TX_ENABLE_EVENT_TRACE** zdefiniowane za pomocą funkcji śledzenia zdarzeń.

#### <a name="input-parameters"></a>Parametry wejściowe

- **event_id:** identyfikacja zdarzeń specyficzna dla aplikacji i musi być większa niż **TX_TRACE_USER_EVENT_START** i mniejsza niż lub równa TX_TRACE_USER_EVENT_END **.**
- **info_field_1:** pole informacji specyficzne dla aplikacji.
- **info_field_2:** pole informacji specyficzne dla aplikacji.
- **info_field_3:** pole informacji specyficzne dla aplikacji.
- **info_field_4:** pole informacji specyficzne dla aplikacji.

#### <a name="return-values"></a>Wartości zwrócone
- **TX_SUCCESS** (0x00) Pomyślne wstawianie zdarzenia użytkownika.
- **TX_NOT_DONE** (0x20) Śledzenie zdarzeń nie jest włączone.
- **TX_FEATURE_NOT_ENABLED** (0xFF) System nie został skompilowany z włączonym śledzeniem.

#### <a name="allowed-from"></a>Dozwolone z

Inicjowanie i wątki

#### <a name="example"></a>Przykład

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a>Zobacz też

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify