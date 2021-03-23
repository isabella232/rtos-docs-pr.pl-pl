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
# <a name="chapter-5---generating-trace-buffers"></a><span data-ttu-id="71256-103">Rozdział 5 — generowanie buforów śledzenia</span><span class="sxs-lookup"><span data-stu-id="71256-103">Chapter 5 - Generating trace buffers</span></span>

<span data-ttu-id="71256-104">Ten rozdział zawiera opis sposobu tworzenia buforu zdarzeń usługi Azure RTO TraceX, a także opis źródłowego formatu buforu.</span><span class="sxs-lookup"><span data-stu-id="71256-104">This chapter contains a description about how to build a Azure RTOS TraceX event buffer and also describes the underlying format of the buffer.</span></span>

## <a name="threadx-event-trace-support"></a><span data-ttu-id="71256-105">Obsługa śledzenia zdarzeń ThreadX</span><span class="sxs-lookup"><span data-stu-id="71256-105">ThreadX Event Trace Support</span></span>

<span data-ttu-id="71256-106">ThreadX zapewnia wbudowaną obsługę śledzenia zdarzeń dla wszystkich usług ThreadX, zmian stanu wątków i zdarzeń zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="71256-106">ThreadX provides built-in event trace support for all ThreadX services, thread state changes, and user-defined events.</span></span> <span data-ttu-id="71256-107">Funkcja śledzenia zdarzeń ThreadX jest przeznaczona głównie do analizowania ostatnich działań "n" w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71256-107">The ThreadX event-trace capability is primarily designed as a post-mortem tool to analyze the last "n" activities in the application.</span></span> <span data-ttu-id="71256-108">Z tych informacji deweloperzy mogą wychwycić problemy i/lub potencjalne cele optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="71256-108">From this information, the developer may spot problems and/or potential targets of optimization.</span></span>

<span data-ttu-id="71256-109">TraceX graficznie wyświetla bufor śledzenia zdarzeń zbudowany przez ThreadX.</span><span class="sxs-lookup"><span data-stu-id="71256-109">TraceX graphically displays the event trace buffer built by ThreadX.</span></span> <span data-ttu-id="71256-110">Poniżej opisano sposób tworzenia buforu i opisuje podstawowy format buforu.</span><span class="sxs-lookup"><span data-stu-id="71256-110">The following describes how to build the buffer and describes the underlying format of the buffer.</span></span>

## <a name="enabling-event-trace"></a><span data-ttu-id="71256-111">Włączanie śledzenia zdarzeń</span><span class="sxs-lookup"><span data-stu-id="71256-111">Enabling Event Trace</span></span>

<span data-ttu-id="71256-112">Aby włączyć śledzenie zdarzeń, zdefiniuj stałe sygnatur czasowych, skompiluj bibliotekę ThreadX z zdefiniowanym **TX_ENABLE_EVENT_TRACE** i Włącz śledzenie, wywołując funkcję **tx_trace_enable** .</span><span class="sxs-lookup"><span data-stu-id="71256-112">To enable event trace, define the time-stamp constants, build the ThreadX library with **TX_ENABLE_EVENT_TRACE** defined, and enable tracing by calling the **tx_trace_enable** function.</span></span>

## <a name="defining-time-stamp-constants"></a><span data-ttu-id="71256-113">Definiowanie Time-Stamp stałych</span><span class="sxs-lookup"><span data-stu-id="71256-113">Defining Time-Stamp Constants</span></span>

<span data-ttu-id="71256-114">Stałe sygnatur czasowych zostały zaprojektowane w celu udostępnienia kontrolki dla deweloperów względem sygnatury czasowej używanej w wpisach śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="71256-114">The time-stamp constants are designed to provide the developer control over the time-stamp used in the event trace entries.</span></span> <span data-ttu-id="71256-115">Dwie stałe sygnatury czasowej i ich wartości domyślne są następujące:</span><span class="sxs-lookup"><span data-stu-id="71256-115">The two time-stamp constants and their default values are as follows:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

<span data-ttu-id="71256-116">Powyższe stałe są zdefiniowane w **tx_port. h** i tworzą "fałszywą" sygnaturę czasową, która po prostu zwiększa się o jeden dla każdego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="71256-116">The above constants are defined in **tx_port.h** and create a "fake" time-stamp that simply increments by one on each event.</span></span> <span data-ttu-id="71256-117">Poniżej znajduje się przykład rzeczywistej definicji sygnatur czasowych:</span><span class="sxs-lookup"><span data-stu-id="71256-117">The following is an example of an actual timestamp definition:</span></span>

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

<span data-ttu-id="71256-118">Powyższe stałe określają 32-bitowy czasomierz, który jest uzyskiwany poprzez odczytywanie adresu 0x13000004.</span><span class="sxs-lookup"><span data-stu-id="71256-118">The above constants specify a 32-bit timer that is obtained by reading the address 0x13000004.</span></span> <span data-ttu-id="71256-119">Większość sygnatur czasowych specyficznych dla aplikacji powinna być skonfigurowana w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="71256-119">Most application specific time-stamps should be setup in a similar fashion.</span></span>

## <a name="exporting-the-trace-buffer"></a><span data-ttu-id="71256-120">Eksportowanie buforu śledzenia</span><span class="sxs-lookup"><span data-stu-id="71256-120">Exporting the Trace Buffer</span></span>

<span data-ttu-id="71256-121">TraceX potrzebuje buforu śledzenia w formacie pliku binarnego, SZESNASTKOWym Intel lub Motorola S-Record na hoście.</span><span class="sxs-lookup"><span data-stu-id="71256-121">TraceX needs the trace buffer in a binary, Intel HEX, or Motorola S-Record file format on the host.</span></span> <span data-ttu-id="71256-122">Najprostszym sposobem, aby to zrobić, jest zatrzymanie obiektu docelowego i nakazuje debugerowi Zrzut obszaru pamięci dostarczonego do ***tx_trace_enable*** funkcji do pliku na hoście.</span><span class="sxs-lookup"><span data-stu-id="71256-122">The easiest way to accomplish this is to stop the target and instruct your debugger to dump the memory area you supplied to ***tx_trace_enable*** function into a file on the host.</span></span>

> [!WARNING]
><span data-ttu-id="71256-123">***Należy zachować ostrożność, aby nie zatrzymywać elementu docelowego w samym kodzie zbierania śladu. Wykonanie tej operacji może spowodować nieprawidłowe informacje o śledzeniu. Jeśli program jest zatrzymany w ThreadX, najlepiej wykonać krok przed każdym makrem wstawiania śledzenia przed zatopieniem bufora śledzenia.***</span><span class="sxs-lookup"><span data-stu-id="71256-123">***Be careful not to stop the target within a trace gathering code itself. Doing so can cause invalid trace information. If the program is halted within ThreadX, it is best to step over any trace insert macro before dumping the trace buffer.***</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71256-124">*Dodatek D pokazuje, jak zrzucić bufor śledzenia z różnych narzędzi programistycznych.*</span><span class="sxs-lookup"><span data-stu-id="71256-124">*Appendix D shows how to dump the trace buffer from within a variety of development tools.*</span></span>

## <a name="extended-event-trace-api"></a><span data-ttu-id="71256-125">Rozszerzony interfejs API śledzenia zdarzeń</span><span class="sxs-lookup"><span data-stu-id="71256-125">Extended Event Trace API</span></span>

<span data-ttu-id="71256-126">Po skompilowaniu ThreadX z zdefiniowanymi **TX_ENABLE_EVENT_TRACE** , następujące nowe interfejsy API śledzenia zdarzeń są dostępne dla aplikacji:</span><span class="sxs-lookup"><span data-stu-id="71256-126">When ThreadX is built with **TX_ENABLE_EVENT_TRACE** defined, the following new event trace APIs are available to the application:</span></span>

- <span data-ttu-id="71256-127">tx_trace_enable: *Włącz śledzenie zdarzeń*</span><span class="sxs-lookup"><span data-stu-id="71256-127">tx_trace_enable: *Enable event tracing*</span></span>
- <span data-ttu-id="71256-128">tx_trace_event_filter: *Filtruj określone zdarzenia*</span><span class="sxs-lookup"><span data-stu-id="71256-128">tx_trace_event_filter: *Filter specified event(s)*</span></span>
- <span data-ttu-id="71256-129">tx_trace_event_unfilter: *odfiltruj określone zdarzenia*</span><span class="sxs-lookup"><span data-stu-id="71256-129">tx_trace_event_unfilter: *Unfilter specified event(s)*</span></span>
- <span data-ttu-id="71256-130">tx_trace_disable: *wyłączanie śledzenia zdarzeń*</span><span class="sxs-lookup"><span data-stu-id="71256-130">tx_trace_disable: *Disable event tracing*</span></span>
- <span data-ttu-id="71256-131">tx_trace_isr_enter_insert: *Wstawianie zdarzenia ISR wprowadź zdarzenie śledzenia*</span><span class="sxs-lookup"><span data-stu-id="71256-131">tx_trace_isr_enter_insert: *Insert ISR enter trace event*</span></span>
- <span data-ttu-id="71256-132">tx_trace_isr_exit_insert: *Wstaw zdarzenie śledzenia wyjścia ISR*</span><span class="sxs-lookup"><span data-stu-id="71256-132">tx_trace_isr_exit_insert: *Insert ISR exit trace event*</span></span>
- <span data-ttu-id="71256-133">tx_trace_buffer_full_notify: *Rejestrowanie wywołania zwrotnego pełnej aplikacji w buforze śledzenia*</span><span class="sxs-lookup"><span data-stu-id="71256-133">tx_trace_buffer_full_notify: *Register trace buffer full application callback*</span></span>
- <span data-ttu-id="71256-134">tx_trace_user_event_insert: *Wstawianie zdarzenia użytkownika*</span><span class="sxs-lookup"><span data-stu-id="71256-134">tx_trace_user_event_insert: *Insert user event*</span></span>

### <a name="tx_trace_enable"></a><span data-ttu-id="71256-135">tx_trace_enable</span><span class="sxs-lookup"><span data-stu-id="71256-135">tx_trace_enable</span></span>

<span data-ttu-id="71256-136">Włącz śledzenie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="71256-136">Enable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="71256-137">Prototype</span><span class="sxs-lookup"><span data-stu-id="71256-137">Prototype</span></span>

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a><span data-ttu-id="71256-138">Opis</span><span class="sxs-lookup"><span data-stu-id="71256-138">Description</span></span>
<span data-ttu-id="71256-139">Ta usługa umożliwia śledzenie zdarzeń w programie ThreadX.</span><span class="sxs-lookup"><span data-stu-id="71256-139">This service enables event tracing inside ThreadX.</span></span> <span data-ttu-id="71256-140">Bufor śledzenia i Maksymalna liczba obiektów ThreadX są dostarczane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="71256-140">The trace buffer and the maximum number of ThreadX objects are supplied by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71256-141">Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.</span><span class="sxs-lookup"><span data-stu-id="71256-141">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="71256-142">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71256-142">Input Parameters</span></span>

- <span data-ttu-id="71256-143">**trace_buffer_start**: wskaźnik na początku buforu śledzenia dostarczonego przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="71256-143">**trace_buffer_start**: Pointer to the start of the user-supplied trace buffer.</span></span>
- <span data-ttu-id="71256-144">**trace_buffer_size**: całkowita liczba bajtów w pamięci dla buforu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71256-144">**trace_buffer_size**: Total number of bytes in the memory for the trace buffer.</span></span> <span data-ttu-id="71256-145">Im większy bufor śledzenia, tym większa jest możliwość przechowywania.</span><span class="sxs-lookup"><span data-stu-id="71256-145">The larger the trace buffer, the more entries it is able to store.</span></span>
- <span data-ttu-id="71256-146">**registry_entries**: liczba obiektów ThreadX aplikacji, które mają być przechowywane w rejestrze śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71256-146">**registry_entries**: Number of application ThreadX objects to keep in the trace registry.</span></span> <span data-ttu-id="71256-147">Rejestr jest używany do skorelowania adresów obiektów z nazwami obiektów.</span><span class="sxs-lookup"><span data-stu-id="71256-147">The registry is used to correlate object addresses with object names.</span></span> <span data-ttu-id="71256-148">Jest to bardzo przydatne w przypadku graficznego interfejsu użytkownika narzędzia do analizy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71256-148">This is highly useful for GUI trace analysis tools.</span></span>

#### <a name="return-values"></a><span data-ttu-id="71256-149">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71256-149">Return Values</span></span>

- <span data-ttu-id="71256-150">**TX_SUCCESS** (0X00) pomyślne Włączenie śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="71256-150">**TX_SUCCESS** (0x00) Successful event trace enable.</span></span>
- <span data-ttu-id="71256-151">**TX_SIZE_ERROR** (0X05) określony rozmiar buforu śledzenia jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="71256-151">**TX_SIZE_ERROR** (0x05) Specified trace buffer size is too small.</span></span> <span data-ttu-id="71256-152">Musi być wystarczająco duży dla nagłówka śledzenia, rejestru obiektów i co najmniej jednego wpisu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71256-152">It must be large enough for the trace header, the object registry, and at least one trace entry.</span></span>
- <span data-ttu-id="71256-153">Śledzenie zdarzeń **TX_NOT_DONE** (0x20) zostało już włączone.</span><span class="sxs-lookup"><span data-stu-id="71256-153">**TX_NOT_DONE** (0x20) Event tracing was already enabled.</span></span>
- <span data-ttu-id="71256-154">System **TX_FEATURE_NOT_ENABLED** (0xFF) nie został skompilowany z włączonym śledzeniem.</span><span class="sxs-lookup"><span data-stu-id="71256-154">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="71256-155">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71256-155">Allowed From</span></span>

<span data-ttu-id="71256-156">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="71256-156">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="71256-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="71256-157">Example</span></span>

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a><span data-ttu-id="71256-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71256-158">See Also</span></span>

<span data-ttu-id="71256-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="71256-159">tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_filter"></a><span data-ttu-id="71256-160">tx_trace_event_filter</span><span class="sxs-lookup"><span data-stu-id="71256-160">tx_trace_event_filter</span></span>

<span data-ttu-id="71256-161">Filtrowanie określonych zdarzeń</span><span class="sxs-lookup"><span data-stu-id="71256-161">Filter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="71256-162">Prototype</span><span class="sxs-lookup"><span data-stu-id="71256-162">Prototype</span></span>

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a><span data-ttu-id="71256-163">Opis</span><span class="sxs-lookup"><span data-stu-id="71256-163">Description</span></span>

<span data-ttu-id="71256-164">Ta usługa filtruje określone zdarzenia z wstawienia do aktywnego buforu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71256-164">This service filters the specified event(s) from being inserted into the active trace buffer.</span></span> <span data-ttu-id="71256-165">Należy pamiętać, że domyślnie żadne zdarzenia nie są filtrowane po wywołaniu *tx_trace_enable* .</span><span class="sxs-lookup"><span data-stu-id="71256-165">Note that by default no events are filtered after *tx_trace_enable* is called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71256-166">Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.</span><span class="sxs-lookup"><span data-stu-id="71256-166">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="71256-167">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71256-167">Input Parameters</span></span>

- <span data-ttu-id="71256-168">**event_filter_bits**: bity odpowiadające zdarzeniom do filtrowania.</span><span class="sxs-lookup"><span data-stu-id="71256-168">**event_filter_bits**: Bits that correspond to events to filter.</span></span> <span data-ttu-id="71256-169">Wiele zdarzeń może być filtrowanych przez oring ze sobą odpowiednie stałe.</span><span class="sxs-lookup"><span data-stu-id="71256-169">Multiple events may be filtered by simply oring together the appropriate constants.</span></span> <span data-ttu-id="71256-170">Prawidłowe stałe dla tej zmiennej są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="71256-170">Valid constants for this variable are defined as follows:</span></span>

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

#### <a name="return-values"></a><span data-ttu-id="71256-171">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71256-171">Return Values</span></span>

- <span data-ttu-id="71256-172">Filtr zdarzenia pomyślnego **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="71256-172">**TX_SUCCESS** (0x00) Successful event filter.</span></span>
- <span data-ttu-id="71256-173">System **TX_FEATURE_NOT_ENABLED** (0xFF) nie został skompilowany z włączonym śledzeniem.</span><span class="sxs-lookup"><span data-stu-id="71256-173">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="71256-174">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71256-174">Allowed From</span></span>

<span data-ttu-id="71256-175">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="71256-175">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="71256-176">Przykład</span><span class="sxs-lookup"><span data-stu-id="71256-176">Example</span></span>

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="71256-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71256-177">See Also</span></span>

<span data-ttu-id="71256-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="71256-178">tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_event_unfilter"></a><span data-ttu-id="71256-179">tx_trace_event_unfilter</span><span class="sxs-lookup"><span data-stu-id="71256-179">tx_trace_event_unfilter</span></span>

<span data-ttu-id="71256-180">Odfiltruj określone zdarzenia</span><span class="sxs-lookup"><span data-stu-id="71256-180">Unfilter specified events</span></span>

#### <a name="prototype"></a><span data-ttu-id="71256-181">Prototype</span><span class="sxs-lookup"><span data-stu-id="71256-181">Prototype</span></span>

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a><span data-ttu-id="71256-182">Opis</span><span class="sxs-lookup"><span data-stu-id="71256-182">Description</span></span>

<span data-ttu-id="71256-183">Ta usługa umożliwia odfiltrowanie określonych zdarzeń w taki sposób, aby były one wstawiane do aktywnego buforu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71256-183">This service unfilters the specified event(s) such that they will be inserted into the active trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71256-184">Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.</span><span class="sxs-lookup"><span data-stu-id="71256-184">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="71256-185">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71256-185">Input Parameters</span></span>

- <span data-ttu-id="71256-186">**event_unfilter_bits**: bity odpowiadające zdarzeniom do odfiltrowania.</span><span class="sxs-lookup"><span data-stu-id="71256-186">**event_unfilter_bits**: Bits that correspond to events to unfilter.</span></span> <span data-ttu-id="71256-187">Wiele zdarzeń może być niefiltrowanych przez zwykłe lub, w połączeniu z odpowiednimi stałymi.</span><span class="sxs-lookup"><span data-stu-id="71256-187">Multiple events may be unfiltered by simply or-ing together the appropriate constants.</span></span> <span data-ttu-id="71256-188">Prawidłowe stałe dla tej zmiennej są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="71256-188">Valid constants for this variable are defined as follows:</span></span>

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

#### <a name="return-values"></a><span data-ttu-id="71256-189">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71256-189">Return Values</span></span>

- <span data-ttu-id="71256-190">Odfiltrowanie zdarzenia powiodło się **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="71256-190">**TX_SUCCESS** (0x00) Successful event unfilter.</span></span>
- <span data-ttu-id="71256-191">System **TX_FEATURE_NOT_ENABLED** (0xFF) nie został skompilowany z włączonym śledzeniem.</span><span class="sxs-lookup"><span data-stu-id="71256-191">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="71256-192">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71256-192">Allowed From</span></span>

<span data-ttu-id="71256-193">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="71256-193">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="71256-194">Przykład</span><span class="sxs-lookup"><span data-stu-id="71256-194">Example</span></span>

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a><span data-ttu-id="71256-195">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71256-195">See Also</span></span>

<span data-ttu-id="71256-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="71256-196">tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_disable"></a><span data-ttu-id="71256-197">tx_trace_disable</span><span class="sxs-lookup"><span data-stu-id="71256-197">tx_trace_disable</span></span>

#### <a name="disable-event-tracing"></a><span data-ttu-id="71256-198">Wyłącz śledzenie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="71256-198">Disable event tracing</span></span>

#### <a name="prototype"></a><span data-ttu-id="71256-199">Prototype</span><span class="sxs-lookup"><span data-stu-id="71256-199">Prototype</span></span>

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a><span data-ttu-id="71256-200">Opis</span><span class="sxs-lookup"><span data-stu-id="71256-200">Description</span></span>

<span data-ttu-id="71256-201">Ta usługa wyłącza śledzenie zdarzeń wewnątrz ThreadX.</span><span class="sxs-lookup"><span data-stu-id="71256-201">This service disables event tracing inside ThreadX.</span></span> <span data-ttu-id="71256-202">Może to być przydatne, jeśli aplikacja chce zablokować bieżący bufor śledzenia zdarzeń i ewentualnie transportować go zewnętrznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="71256-202">This can be useful if the application wants to freeze the current event trace buffer and possibly transport it externally during run-time.</span></span> <span data-ttu-id="71256-203">Po wyłączeniu **tx_trace_enable** można wywołać, aby ponownie uruchomić śledzenie.</span><span class="sxs-lookup"><span data-stu-id="71256-203">Once disabled, the **tx_trace_enable** can be called to start tracing again.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71256-204">Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.</span><span class="sxs-lookup"><span data-stu-id="71256-204">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="71256-205">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71256-205">Input Parameters</span></span>

<span data-ttu-id="71256-206">Brak.</span><span class="sxs-lookup"><span data-stu-id="71256-206">None.</span></span>

#### <a name="return-values"></a><span data-ttu-id="71256-207">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71256-207">Return Values</span></span>

- <span data-ttu-id="71256-208">**TX_SUCCESS** (0X00) pomyślne wyłączenie śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="71256-208">**TX_SUCCESS** (0x00) Successful event trace disable.</span></span>
- <span data-ttu-id="71256-209">Śledzenie zdarzeń **TX_NOT_DONE** (0x20) nie zostało włączone.</span><span class="sxs-lookup"><span data-stu-id="71256-209">**TX_NOT_DONE** (0x20) Event tracing was not enabled.</span></span>
- <span data-ttu-id="71256-210">System **TX_FEATURE_NOT_ENABLED** (0xFF) nie został skompilowany z włączonym śledzeniem.</span><span class="sxs-lookup"><span data-stu-id="71256-210">**TX_FEATURE_NOT_ENABLED** (0xFF) System was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="71256-211">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71256-211">Allowed From</span></span>

<span data-ttu-id="71256-212">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="71256-212">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="71256-213">Przykład</span><span class="sxs-lookup"><span data-stu-id="71256-213">Example</span></span> 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a><span data-ttu-id="71256-214">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71256-214">See Also</span></span>

<span data-ttu-id="71256-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="71256-215">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_enter_insert"></a><span data-ttu-id="71256-216">tx_trace_isr_enter_insert</span><span class="sxs-lookup"><span data-stu-id="71256-216">tx_trace_isr_enter_insert</span></span>

#### <a name="insert-isr-enter-event"></a><span data-ttu-id="71256-217">Wstaw zdarzenie przejścia do procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71256-217">Insert ISR enter event</span></span>

#### <a name="prototype"></a><span data-ttu-id="71256-218">Prototype</span><span class="sxs-lookup"><span data-stu-id="71256-218">Prototype</span></span>

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="71256-219">Opis</span><span class="sxs-lookup"><span data-stu-id="71256-219">Description</span></span>

<span data-ttu-id="71256-220">Ta usługa wstawia zdarzenie przejścia ISR do buforu śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="71256-220">This service inserts the ISR enter event into the event trace buffer.</span></span> <span data-ttu-id="71256-221">Powinien być wywoływany przez aplikację na początku przetwarzania w ramach procedury ISR.</span><span class="sxs-lookup"><span data-stu-id="71256-221">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="71256-222">Podany parametr powinien identyfikować konkretne przeisr do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71256-222">The supplied parameter should identify the specific ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71256-223">Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.</span><span class="sxs-lookup"><span data-stu-id="71256-223">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="71256-224">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71256-224">Input Parameters</span></span> 
- <span data-ttu-id="71256-225">**isr_id**: wartość specyficzna dla aplikacji w celu zidentyfikowania procedury ISR.</span><span class="sxs-lookup"><span data-stu-id="71256-225">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="71256-226">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71256-226">Return Values</span></span>

<span data-ttu-id="71256-227">**Brak**</span><span class="sxs-lookup"><span data-stu-id="71256-227">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="71256-228">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71256-228">Allowed From</span></span> 

<span data-ttu-id="71256-229">Procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71256-229">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="71256-230">Przykład</span><span class="sxs-lookup"><span data-stu-id="71256-230">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="71256-231">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71256-231">See Also</span></span>

<span data-ttu-id="71256-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="71256-232">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_isr_exit_insert"></a><span data-ttu-id="71256-233">tx_trace_isr_exit_insert</span><span class="sxs-lookup"><span data-stu-id="71256-233">tx_trace_isr_exit_insert</span></span>

#### <a name="insert-isr-exit-event"></a><span data-ttu-id="71256-234">Wstaw zdarzenie zakończenia procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71256-234">Insert ISR exit event</span></span>

#### <a name="prototype"></a><span data-ttu-id="71256-235">Prototype</span><span class="sxs-lookup"><span data-stu-id="71256-235">Prototype</span></span>

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a><span data-ttu-id="71256-236">Opis</span><span class="sxs-lookup"><span data-stu-id="71256-236">Description</span></span>

<span data-ttu-id="71256-237">Ta usługa wstawia zdarzenie wpisu ISR do buforu śledzenia zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="71256-237">This service inserts the ISR entry event into the event trace buffer.</span></span> <span data-ttu-id="71256-238">Powinien być wywoływany przez aplikację na początku przetwarzania w ramach procedury ISR.</span><span class="sxs-lookup"><span data-stu-id="71256-238">It should be called by the application at the beginning of ISR processing.</span></span> <span data-ttu-id="71256-239">Podany parametr powinien identyfikować przeisr do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71256-239">The supplied parameter should identify the ISR to the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71256-240">Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.</span><span class="sxs-lookup"><span data-stu-id="71256-240">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="71256-241">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71256-241">Input Parameters</span></span> 

- <span data-ttu-id="71256-242">**isr_id**: wartość specyficzna dla aplikacji w celu zidentyfikowania procedury ISR.</span><span class="sxs-lookup"><span data-stu-id="71256-242">**isr_id**: Application specific value to identify the ISR.</span></span>

#### <a name="return-values"></a><span data-ttu-id="71256-243">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71256-243">Return Values</span></span>

<span data-ttu-id="71256-244">**Brak**</span><span class="sxs-lookup"><span data-stu-id="71256-244">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="71256-245">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71256-245">Allowed From</span></span>

<span data-ttu-id="71256-246">Procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71256-246">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="71256-247">Przykład</span><span class="sxs-lookup"><span data-stu-id="71256-247">Example</span></span>

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="71256-248">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71256-248">See Also</span></span>

<span data-ttu-id="71256-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="71256-249">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_buffer_full_notify"></a><span data-ttu-id="71256-250">tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="71256-250">tx_trace_buffer_full_notify</span></span>

#### <a name="register-trace-buffer-full-application-callback"></a><span data-ttu-id="71256-251">Rejestrowanie wywołania zwrotnego pełnej aplikacji w buforze śledzenia</span><span class="sxs-lookup"><span data-stu-id="71256-251">Register trace buffer full application callback</span></span>

#### <a name="prototype"></a><span data-ttu-id="71256-252">Prototype</span><span class="sxs-lookup"><span data-stu-id="71256-252">Prototype</span></span>

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a><span data-ttu-id="71256-253">Opis</span><span class="sxs-lookup"><span data-stu-id="71256-253">Description</span></span>

<span data-ttu-id="71256-254">Ta usługa rejestruje funkcję wywołania zwrotnego aplikacji, która jest wywoływana przez ThreadX, gdy bufor śledzenia zostanie zapełniony.</span><span class="sxs-lookup"><span data-stu-id="71256-254">This service registers an application callback function that is called by ThreadX when the trace buffer becomes full.</span></span> <span data-ttu-id="71256-255">Następnie aplikacja może wybrać wyłączenie śledzenia i/lub prawdopodobnie konfigurację nowego buforu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71256-255">The application can then choose to disable tracing and/or possibly setup a new trace buffer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71256-256">Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.</span><span class="sxs-lookup"><span data-stu-id="71256-256">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="71256-257">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71256-257">Input Parameters</span></span>

- <span data-ttu-id="71256-258">**full_buffer_callback**: funkcja aplikacji do wywołania, gdy bufor śledzenia jest pełny.</span><span class="sxs-lookup"><span data-stu-id="71256-258">**full_buffer_callback**: Application function to call when the trace buffer is full.</span></span> <span data-ttu-id="71256-259">Wartość NULL powoduje wyłączenie wywołania zwrotnego powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="71256-259">A value of NULL disables the notification callback.</span></span>

#### <a name="return-values"></a><span data-ttu-id="71256-260">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71256-260">Return Values</span></span>

<span data-ttu-id="71256-261">**Brak**</span><span class="sxs-lookup"><span data-stu-id="71256-261">**None**</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="71256-262">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71256-262">Allowed From</span></span>

<span data-ttu-id="71256-263">Procedury ISR</span><span class="sxs-lookup"><span data-stu-id="71256-263">ISRs</span></span>

#### <a name="example"></a><span data-ttu-id="71256-264">Przykład</span><span class="sxs-lookup"><span data-stu-id="71256-264">Example</span></span>

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a><span data-ttu-id="71256-265">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71256-265">See Also</span></span>

<span data-ttu-id="71256-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="71256-266">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert</span></span>

### <a name="tx_trace_user_event_insert"></a><span data-ttu-id="71256-267">tx_trace_user_event_insert</span><span class="sxs-lookup"><span data-stu-id="71256-267">tx_trace_user_event_insert</span></span>

#### <a name="insert-user-event"></a><span data-ttu-id="71256-268">Wstaw zdarzenie użytkownika</span><span class="sxs-lookup"><span data-stu-id="71256-268">Insert user event</span></span>

#### <a name="prototype"></a><span data-ttu-id="71256-269">Prototype</span><span class="sxs-lookup"><span data-stu-id="71256-269">Prototype</span></span>

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a><span data-ttu-id="71256-270">Opis</span><span class="sxs-lookup"><span data-stu-id="71256-270">Description</span></span>

<span data-ttu-id="71256-271">Ta usługa wstawia zdarzenie użytkownika do buforu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="71256-271">This service inserts the user event into the trace buffer.</span></span> <span data-ttu-id="71256-272">Identyfikatory zdarzeń użytkownika muszą być większe niż stałe **TX_TRACE_USER_EVENT_START**, które jest zdefiniowane jako 4096.</span><span class="sxs-lookup"><span data-stu-id="71256-272">User event IDs must be greater than the constant **TX_TRACE_USER_EVENT_START**, which is defined to be 4096.</span></span> <span data-ttu-id="71256-273">Wartość maksymalnego zdarzenia użytkownika jest definiowana przez **TX_TRACE_USER_EVENT_END** stałą, która jest zdefiniowana jako 65535.</span><span class="sxs-lookup"><span data-stu-id="71256-273">The maximum user event is defined by the constant **TX_TRACE_USER_EVENT_END**, which is defined to be 65535.</span></span> <span data-ttu-id="71256-274">Wszystkie zdarzenia należące do tego zakresu są dostępne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71256-274">All events within this range are available to the application.</span></span> <span data-ttu-id="71256-275">Pola informacji są specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71256-275">The information fields are application specific.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="71256-276">Aby można było używać śledzenia zdarzeń, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem **TX_ENABLE_EVENT_TRACE** zdefiniowanej.</span><span class="sxs-lookup"><span data-stu-id="71256-276">The ThreadX library and application must be built with **TX_ENABLE_EVENT_TRACE** defined in order to use event tracing.</span></span>

#### <a name="input-parameters"></a><span data-ttu-id="71256-277">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="71256-277">Input Parameters</span></span>

- <span data-ttu-id="71256-278">**event_id**: Identyfikacja zdarzeń specyficznych dla aplikacji musi być większa niż **TX_TRACE_USER_EVENT_START** i mniejsza niż lub równa **TX_TRACE_USER_EVENT_END**.</span><span class="sxs-lookup"><span data-stu-id="71256-278">**event_id**: Application-specific event identification and must start be greater than **TX_TRACE_USER_EVENT_START** and less than or equal to **TX_TRACE_USER_EVENT_END**.</span></span>
- <span data-ttu-id="71256-279">**info_field_1**: informacje specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71256-279">**info_field_1**: Application-specific information field.</span></span>
- <span data-ttu-id="71256-280">**info_field_2**: informacje specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71256-280">**info_field_2**: Application-specific information field.</span></span>
- <span data-ttu-id="71256-281">**info_field_3**: informacje specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71256-281">**info_field_3**: Application-specific information field.</span></span>
- <span data-ttu-id="71256-282">**info_field_4**: informacje specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="71256-282">**info_field_4**: Application-specific information field.</span></span>

#### <a name="return-values"></a><span data-ttu-id="71256-283">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="71256-283">Return Values</span></span>
- <span data-ttu-id="71256-284">**TX_SUCCESS** (0X00) pomyślne Wstawianie zdarzeń przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="71256-284">**TX_SUCCESS** (0x00) Successful user event insert.</span></span>
- <span data-ttu-id="71256-285">Śledzenie zdarzeń **TX_NOT_DONE** (0x20) nie jest włączone.</span><span class="sxs-lookup"><span data-stu-id="71256-285">**TX_NOT_DONE** (0x20) Event tracing is not enabled.</span></span>
- <span data-ttu-id="71256-286">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonym śledzeniem.</span><span class="sxs-lookup"><span data-stu-id="71256-286">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with trace enabled.</span></span>

#### <a name="allowed-from"></a><span data-ttu-id="71256-287">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="71256-287">Allowed From</span></span>

<span data-ttu-id="71256-288">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="71256-288">Initialization and threads</span></span>

#### <a name="example"></a><span data-ttu-id="71256-289">Przykład</span><span class="sxs-lookup"><span data-stu-id="71256-289">Example</span></span>

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a><span data-ttu-id="71256-290">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71256-290">See Also</span></span>

<span data-ttu-id="71256-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span><span class="sxs-lookup"><span data-stu-id="71256-291">tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify</span></span>