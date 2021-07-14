---
title: Opis Azure RTOS ThreadX
description: Azure ThreadX to zaawansowany system operacyjny czasu rzeczywistego (RTOS) zaprojektowany specjalnie z myślą o aplikacjach głęboko osadzonych.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 938619170ef51d354fa970134328c17407ae846a
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754866"
---
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="689f2-103">Omówienie Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="689f2-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="689f2-104">Azure RTOS ThreadX to zaawansowany system operacyjny Real-Time klasy przemysłowej (RTOS) firmy Microsoft zaprojektowany specjalnie z myślą o aplikacjach głęboko osadzonych, działających w czasie rzeczywistym i IoT.</span><span class="sxs-lookup"><span data-stu-id="689f2-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="689f2-105">Azure RTOS ThreadX zapewnia zaawansowane funkcje planowania, komunikacji, synchronizacji, czasomierza, zarządzania pamięcią i zarządzania przerwami.</span><span class="sxs-lookup"><span data-stu-id="689f2-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="689f2-106">Ponadto system Azure RTOS ThreadX ma wiele zaawansowanych funkcji, takich jak picokernel™ architektura, próg wywłaszczania™ planowanie, łańcuch zdarzeń, profilowanie wykonywania ™, metryki wydajności i śledzenie zdarzeń systemu.</span><span class="sxs-lookup"><span data-stu-id="689f2-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="689f2-107">W połączeniu z doskonałą łatwością użycia, Azure RTOS ThreadX jest idealnym wyborem dla najbardziej wymagających aplikacji osadzonych.</span><span class="sxs-lookup"><span data-stu-id="689f2-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="689f2-108">Od 2017 r. firma Azure RTOS ThreadX ma ponad 6,2 miliarda wdrożeń w wielu różnych produktach, w tym urządzeniach konsumenckich, urządzeniach elektronicznych i przemysłowych urządzeniach sterujących.</span><span class="sxs-lookup"><span data-stu-id="689f2-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="689f2-109">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="689f2-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="689f2-110">Azure RTOS ThreadX Services</span><span class="sxs-lookup"><span data-stu-id="689f2-110">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="689f2-111">Dynamiczne tworzenie wątku</span><span class="sxs-lookup"><span data-stu-id="689f2-111">Dynamic thread creation</span></span>
* <span data-ttu-id="689f2-112">Brak limitów liczby wątków</span><span class="sxs-lookup"><span data-stu-id="689f2-112">No limits on the number of threads</span></span>
* <span data-ttu-id="689f2-113">Interfejsy API głównego wątku obejmują:</span><span class="sxs-lookup"><span data-stu-id="689f2-113">Main thread APIs include:</span></span>
  * <span data-ttu-id="689f2-114">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="689f2-114">tx_thread_create</span></span>
  * <span data-ttu-id="689f2-115">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="689f2-115">tx_thread_delete</span></span>
  * <span data-ttu-id="689f2-116">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="689f2-116">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="689f2-117">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="689f2-117">tx_thread_priority_change</span></span>
  * <span data-ttu-id="689f2-118">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="689f2-118">tx_thread_relinquish</span></span>
  * <span data-ttu-id="689f2-119">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="689f2-119">tx_thread_reset</span></span>
  * <span data-ttu-id="689f2-120">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="689f2-120">tx_thread_resume</span></span>
  * <span data-ttu-id="689f2-121">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="689f2-121">tx_thread_sleep</span></span>
  * <span data-ttu-id="689f2-122">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="689f2-122">tx_thread_suspend</span></span>
  * <span data-ttu-id="689f2-123">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="689f2-123">tx_thread_terminate</span></span>
  * <span data-ttu-id="689f2-124">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="689f2-124">tx_thread_wait_abort</span></span>
* <span data-ttu-id="689f2-125">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="689f2-125">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="689f2-126">Kolejki komunikatów</span><span class="sxs-lookup"><span data-stu-id="689f2-126">Message Queues</span></span>

* <span data-ttu-id="689f2-127">Dynamiczne tworzenie kolejki</span><span class="sxs-lookup"><span data-stu-id="689f2-127">Dynamic queue creation</span></span>
* <span data-ttu-id="689f2-128">Brak limitów liczby kolejek</span><span class="sxs-lookup"><span data-stu-id="689f2-128">No limits on the number of queues</span></span>
* <span data-ttu-id="689f2-129">Komunikaty skopiowane przez wartość (lub przez odwołanie za pośrednictwem wskaźnika)</span><span class="sxs-lookup"><span data-stu-id="689f2-129">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="689f2-130">Rozmiary komunikatów od 1 do 16 słów 32-bitowych</span><span class="sxs-lookup"><span data-stu-id="689f2-130">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="689f2-131">Opcjonalne wstrzymanie wątku przy pustym i pełnym</span><span class="sxs-lookup"><span data-stu-id="689f2-131">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="689f2-132">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="689f2-132">Optional timeout on all suspension</span></span>
* <span data-ttu-id="689f2-133">Interfejsy API kolejki komunikatów głównych obejmują:</span><span class="sxs-lookup"><span data-stu-id="689f2-133">Main message queue APIs include:</span></span>
  * <span data-ttu-id="689f2-134">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="689f2-134">tx_queue_create</span></span>
  * <span data-ttu-id="689f2-135">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="689f2-135">tx_queue_delete</span></span>
  * <span data-ttu-id="689f2-136">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="689f2-136">tx_queue_flush</span></span>
  * <span data-ttu-id="689f2-137">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="689f2-137">tx_queue_front_send</span></span>
  * <span data-ttu-id="689f2-138">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="689f2-138">tx_queue_receive</span></span>
  * <span data-ttu-id="689f2-139">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="689f2-139">tx_queue_send_notify</span></span>
* <span data-ttu-id="689f2-140">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="689f2-140">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="689f2-141">Zliczanie semaforów</span><span class="sxs-lookup"><span data-stu-id="689f2-141">Counting Semaphores</span></span>

* <span data-ttu-id="689f2-142">Dynamiczne tworzenie semaforów</span><span class="sxs-lookup"><span data-stu-id="689f2-142">Dynamic semaphore creation</span></span>
* <span data-ttu-id="689f2-143">Brak limitów liczby semaforów</span><span class="sxs-lookup"><span data-stu-id="689f2-143">No limits on the number of semaphores</span></span>
* <span data-ttu-id="689f2-144">32-bitowe zliczanie semaforów (od 0 do 4 294 967 295)</span><span class="sxs-lookup"><span data-stu-id="689f2-144">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="689f2-145">Obsługuje ochronę konsumentów i producentów zasobów</span><span class="sxs-lookup"><span data-stu-id="689f2-145">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="689f2-146">Opcjonalne zawieszenie wątku, gdy semafor jest niedostępny</span><span class="sxs-lookup"><span data-stu-id="689f2-146">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="689f2-147">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="689f2-147">Optional timeout on all suspension</span></span>
* <span data-ttu-id="689f2-148">Główne interfejsy API semaforów obejmują:</span><span class="sxs-lookup"><span data-stu-id="689f2-148">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="689f2-149">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="689f2-149">tx_semaphore_create</span></span>
  * <span data-ttu-id="689f2-150">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="689f2-150">tx_semaphore_delete</span></span>
  * <span data-ttu-id="689f2-151">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="689f2-151">tx_semaphore_get</span></span>
  * <span data-ttu-id="689f2-152">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="689f2-152">tx_semaphore_put</span></span>
  * <span data-ttu-id="689f2-153">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="689f2-153">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="689f2-154">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="689f2-154">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="689f2-155">Muteksy</span><span class="sxs-lookup"><span data-stu-id="689f2-155">Mutexes</span></span>

* <span data-ttu-id="689f2-156">Dynamiczne tworzenie obiektu mutex</span><span class="sxs-lookup"><span data-stu-id="689f2-156">Dynamic mutex creation</span></span>
* <span data-ttu-id="689f2-157">Brak limitów liczby mutexes</span><span class="sxs-lookup"><span data-stu-id="689f2-157">No limits on the number of mutexes</span></span>
* <span data-ttu-id="689f2-158">Obsługiwana ochrona zagnieżdżonych zasobów</span><span class="sxs-lookup"><span data-stu-id="689f2-158">Nested resource protection supported</span></span>
* <span data-ttu-id="689f2-159">Obsługiwane opcjonalne dziedziczenie priorytetów</span><span class="sxs-lookup"><span data-stu-id="689f2-159">Optional priority inheritance supported</span></span>
* <span data-ttu-id="689f2-160">Opcjonalne zawieszenie wątku, gdy element mutex jest niedostępny</span><span class="sxs-lookup"><span data-stu-id="689f2-160">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="689f2-161">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="689f2-161">Optional timeout on all suspension</span></span>
* <span data-ttu-id="689f2-162">Główne interfejsy API mutex obejmują:</span><span class="sxs-lookup"><span data-stu-id="689f2-162">Main mutex APIs include:</span></span>
  * <span data-ttu-id="689f2-163">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="689f2-163">tx_mutex_create</span></span>
  * <span data-ttu-id="689f2-164">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="689f2-164">tx_mutex_delete</span></span>
  * <span data-ttu-id="689f2-165">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="689f2-165">tx_mutex_get</span></span>
  * <span data-ttu-id="689f2-166">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="689f2-166">tx_mutex_put</span></span>
* <span data-ttu-id="689f2-167">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="689f2-167">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="689f2-168">Flagi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="689f2-168">Event Flags</span></span>

* <span data-ttu-id="689f2-169">Dynamiczne tworzenie grupy flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="689f2-169">Dynamic event flag group creation</span></span>
* <span data-ttu-id="689f2-170">Brak limitów liczby grup flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="689f2-170">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="689f2-171">Synchronizacja jednego wątku lub wielu wątków</span><span class="sxs-lookup"><span data-stu-id="689f2-171">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="689f2-172">Niepodzielne uzyskiwanie i wyczyść obsługiwane</span><span class="sxs-lookup"><span data-stu-id="689f2-172">Atomic get and clear supported</span></span>
* <span data-ttu-id="689f2-173">Opcjonalne zawieszenie wielowątkowe dla zestawu zdarzeń AND/OR</span><span class="sxs-lookup"><span data-stu-id="689f2-173">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="689f2-174">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="689f2-174">Optional timeout on all suspension</span></span>
* <span data-ttu-id="689f2-175">Główne interfejsy API flag zdarzeń obejmują:</span><span class="sxs-lookup"><span data-stu-id="689f2-175">Main event flag APIs include:</span></span>
  * <span data-ttu-id="689f2-176">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="689f2-176">tx_event_flags_create</span></span>
  * <span data-ttu-id="689f2-177">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="689f2-177">tx_event_flags_delete</span></span>
  * <span data-ttu-id="689f2-178">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="689f2-178">tx_event_flags_get</span></span>
  * <span data-ttu-id="689f2-179">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="689f2-179">tx_event_flags_set</span></span>
  * <span data-ttu-id="689f2-180">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="689f2-180">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="689f2-181">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="689f2-181">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="689f2-182">Blokuj pule pamięci</span><span class="sxs-lookup"><span data-stu-id="689f2-182">Block Memory Pools</span></span>

* <span data-ttu-id="689f2-183">Dynamiczne tworzenie puli bloków</span><span class="sxs-lookup"><span data-stu-id="689f2-183">Dynamic block pool creation</span></span>
* <span data-ttu-id="689f2-184">Brak limitów liczby pul bloków</span><span class="sxs-lookup"><span data-stu-id="689f2-184">No limits on the number of block pools</span></span>
* <span data-ttu-id="689f2-185">Brak limitów rozmiaru bloków o stałym rozmiarze lub rozmiaru puli</span><span class="sxs-lookup"><span data-stu-id="689f2-185">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="689f2-186">Najszybsza możliwa alokacja pamięci/deal-location</span><span class="sxs-lookup"><span data-stu-id="689f2-186">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="689f2-187">Opcjonalne zawieszenie wątku w pustej puli</span><span class="sxs-lookup"><span data-stu-id="689f2-187">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="689f2-188">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="689f2-188">Optional timeout on all suspension</span></span>
* <span data-ttu-id="689f2-189">Główne interfejsy API puli bloków obejmują:</span><span class="sxs-lookup"><span data-stu-id="689f2-189">Main block pool APIs include:</span></span>
  * <span data-ttu-id="689f2-190">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="689f2-190">tx_block_pool_create</span></span>
  * <span data-ttu-id="689f2-191">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="689f2-191">tx_block_pool_delete</span></span>
  * <span data-ttu-id="689f2-192">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="689f2-192">tx_block_allocate</span></span>
  * <span data-ttu-id="689f2-193">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="689f2-193">tx_block_release</span></span>
* <span data-ttu-id="689f2-194">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="689f2-194">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="689f2-195">Pule pamięci bajtów</span><span class="sxs-lookup"><span data-stu-id="689f2-195">Byte Memory Pools</span></span>

* <span data-ttu-id="689f2-196">Dynamiczne tworzenie puli bajtów</span><span class="sxs-lookup"><span data-stu-id="689f2-196">Dynamic byte pool creation</span></span>
* <span data-ttu-id="689f2-197">Brak limitów liczby pul bajtów</span><span class="sxs-lookup"><span data-stu-id="689f2-197">No limits on the number of byte pools</span></span>
* <span data-ttu-id="689f2-198">Brak limitów rozmiaru puli bajtów</span><span class="sxs-lookup"><span data-stu-id="689f2-198">No limits on size of byte pool</span></span>
* <span data-ttu-id="689f2-199">Najbardziej elastyczna alokacja pamięci o zmiennej długości/co deallocation</span><span class="sxs-lookup"><span data-stu-id="689f2-199">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="689f2-200">Obsługiwana lokalizacja rozmiaru alokacji</span><span class="sxs-lookup"><span data-stu-id="689f2-200">Allocation size locality supported</span></span>
* <span data-ttu-id="689f2-201">Opcjonalne zawieszenie wątku w pustej puli</span><span class="sxs-lookup"><span data-stu-id="689f2-201">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="689f2-202">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="689f2-202">Optional timeout on all suspension</span></span>
* <span data-ttu-id="689f2-203">Interfejsy API puli bajtów głównych obejmują:</span><span class="sxs-lookup"><span data-stu-id="689f2-203">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="689f2-204">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="689f2-204">tx_byte_pool_create</span></span>
  * <span data-ttu-id="689f2-205">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="689f2-205">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="689f2-206">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="689f2-206">tx_byte_allocate</span></span>
  * <span data-ttu-id="689f2-207">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="689f2-207">tx_byte_release</span></span>
* <span data-ttu-id="689f2-208">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="689f2-208">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="689f2-209">Czasomierze aplikacji</span><span class="sxs-lookup"><span data-stu-id="689f2-209">Application Timers</span></span>

* <span data-ttu-id="689f2-210">Dynamiczne tworzenie czasomierza</span><span class="sxs-lookup"><span data-stu-id="689f2-210">Dynamic timer creation</span></span>
* <span data-ttu-id="689f2-211">Brak limitów liczby czasomierzy</span><span class="sxs-lookup"><span data-stu-id="689f2-211">No limits on the number of timers</span></span>
* <span data-ttu-id="689f2-212">Obsługiwane czasomierze okresowe lub czasomierze jednozmijowe</span><span class="sxs-lookup"><span data-stu-id="689f2-212">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="689f2-213">Czasomierze okresowe mogą mieć inną wartość początkowego wygaśnięcia</span><span class="sxs-lookup"><span data-stu-id="689f2-213">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="689f2-214">Brak wyszukiwania w przypadku aktywacji lub dezaktywacji czasomierza</span><span class="sxs-lookup"><span data-stu-id="689f2-214">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="689f2-215">Wszystkie czasomierze sterowane przez jedno sprzętowe przerwanie czasomierza</span><span class="sxs-lookup"><span data-stu-id="689f2-215">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="689f2-216">Główne interfejsy API czasomierza obejmują:</span><span class="sxs-lookup"><span data-stu-id="689f2-216">Main timer APIs include:</span></span>
  * <span data-ttu-id="689f2-217">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="689f2-217">tx_timer_create</span></span>
  * <span data-ttu-id="689f2-218">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="689f2-218">tx_timer_delete</span></span>
  * <span data-ttu-id="689f2-219">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="689f2-219">tx_timer_activate</span></span>
  * <span data-ttu-id="689f2-220">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="689f2-220">tx_timer_change</span></span>
  * <span data-ttu-id="689f2-221">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="689f2-221">tx_timer_deactivate</span></span>
* <span data-ttu-id="689f2-222">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="689f2-222">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="689f2-223">Azure RTOS ThreadX Core Scheduler</span><span class="sxs-lookup"><span data-stu-id="689f2-223">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="689f2-224">Minimalna ilość pamięci FLASH 2 KB, 1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="689f2-224">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="689f2-225">Szybki, podrzędny mikrosekundowy przełącznik kontekstowy</span><span class="sxs-lookup"><span data-stu-id="689f2-225">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="689f2-226">W pełni deterministyczne, niezależnie od liczby wątków</span><span class="sxs-lookup"><span data-stu-id="689f2-226">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="689f2-227">Oparte na priorytetach, w pełni wywłaszczujące planowanie</span><span class="sxs-lookup"><span data-stu-id="689f2-227">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="689f2-228">32 domyślne poziomy priorytetów, opcjonalnie do 1024 poziomów</span><span class="sxs-lookup"><span data-stu-id="689f2-228">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="689f2-229">Planowanie wspólne na poziomie priorytetu (FIFO)</span><span class="sxs-lookup"><span data-stu-id="689f2-229">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="689f2-230">Technologia progu wywłaszczenia</span><span class="sxs-lookup"><span data-stu-id="689f2-230">Preemption-threshold technology</span></span>
* <span data-ttu-id="689f2-231">Opcjonalne usługi czasomierza, w tym:</span><span class="sxs-lookup"><span data-stu-id="689f2-231">Optional timer services, including:</span></span>
  * <span data-ttu-id="689f2-232">Opcjonalny wycinek czasu dla każdego wątku</span><span class="sxs-lookup"><span data-stu-id="689f2-232">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="689f2-233">Opcjonalny limit czasu dla wszystkich blokad</span><span class="sxs-lookup"><span data-stu-id="689f2-233">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="689f2-234">Interfejsy API wymagają przerwania czasomierza sprzętowego</span><span class="sxs-lookup"><span data-stu-id="689f2-234">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="689f2-235">Profilowanie wykonywania</span><span class="sxs-lookup"><span data-stu-id="689f2-235">Execution profiling</span></span>
* <span data-ttu-id="689f2-236">Śledzenie na poziomie systemu</span><span class="sxs-lookup"><span data-stu-id="689f2-236">System-level Trace</span></span>
* <span data-ttu-id="689f2-237">Bezpieczeństwo certyfikowane przez wiele standardów</span><span class="sxs-lookup"><span data-stu-id="689f2-237">Safety certified to many standards</span></span>

## <a name="threadx-footprint"></a><span data-ttu-id="689f2-238">Ślad ThreadX</span><span class="sxs-lookup"><span data-stu-id="689f2-238">ThreadX footprint</span></span>

<span data-ttu-id="689f2-239">Azure RTOS ThreadX wymaga bardzo małego obszaru instrukcji 2KB i 1 KB pamięci RAM w celu jego minimalnego zużycie.</span><span class="sxs-lookup"><span data-stu-id="689f2-239">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="689f2-240">Wynika to głównie z niewarstwowej architektury picokernel™ automatycznego skalowania.</span><span class="sxs-lookup"><span data-stu-id="689f2-240">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="689f2-241">Automatyczne skalowanie oznacza, że w końcowym obrazie w czasie łączenia uwzględniane są tylko usługi (i infrastruktura obsługująca) używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="689f2-241">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="689f2-242">Oto kilka typowych cech Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="689f2-242">Here are some typical Azure RTOS ThreadX size characteristics.</span></span>

|<span data-ttu-id="689f2-243">Azure RTOS ThreadX Service</span><span class="sxs-lookup"><span data-stu-id="689f2-243">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="689f2-244">Typowy rozmiar w bajtach</span><span class="sxs-lookup"><span data-stu-id="689f2-244">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="689f2-245">Usługi podstawowe (wymagaj)</span><span class="sxs-lookup"><span data-stu-id="689f2-245">Core Services (Require)</span></span> |<span data-ttu-id="689f2-246">2000</span><span class="sxs-lookup"><span data-stu-id="689f2-246">2,000</span></span>  |
|<span data-ttu-id="689f2-247">Queue Services</span><span class="sxs-lookup"><span data-stu-id="689f2-247">Queue Services</span></span>  |<span data-ttu-id="689f2-248">900</span><span class="sxs-lookup"><span data-stu-id="689f2-248">900</span></span>  |
|<span data-ttu-id="689f2-249">Event Flag Services</span><span class="sxs-lookup"><span data-stu-id="689f2-249">Event Flag Services</span></span>  |<span data-ttu-id="689f2-250">900</span><span class="sxs-lookup"><span data-stu-id="689f2-250">900</span></span>  |
|<span data-ttu-id="689f2-251">Semaphore Services</span><span class="sxs-lookup"><span data-stu-id="689f2-251">Semaphore Services</span></span>  |<span data-ttu-id="689f2-252">450</span><span class="sxs-lookup"><span data-stu-id="689f2-252">450</span></span>  |
|<span data-ttu-id="689f2-253">Usługi Mutex</span><span class="sxs-lookup"><span data-stu-id="689f2-253">Mutex Services</span></span>  |<span data-ttu-id="689f2-254">1200</span><span class="sxs-lookup"><span data-stu-id="689f2-254">1,200</span></span>  |
|<span data-ttu-id="689f2-255">Blokuj usługi pamięci</span><span class="sxs-lookup"><span data-stu-id="689f2-255">Block Memory Services</span></span>  |<span data-ttu-id="689f2-256">550</span><span class="sxs-lookup"><span data-stu-id="689f2-256">550</span></span>  |
|<span data-ttu-id="689f2-257">Usługi pamięci bajtowej</span><span class="sxs-lookup"><span data-stu-id="689f2-257">Byte Memory Services</span></span>  |<span data-ttu-id="689f2-258">900</span><span class="sxs-lookup"><span data-stu-id="689f2-258">900</span></span>  |

## <a name="threadx-execution-speed"></a><span data-ttu-id="689f2-259">Szybkość wykonywania threadX</span><span class="sxs-lookup"><span data-stu-id="689f2-259">ThreadX execution speed</span></span>

<span data-ttu-id="689f2-260">Azure RTOS ThreadX osiąga przełącznik kontekstu podrzędnego mikrosekund na najpopularniejszych procesorach i jest znacznie szybszy ogólnie niż inne komercyjne cele RTOS.</span><span class="sxs-lookup"><span data-stu-id="689f2-260">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="689f2-261">Oprócz tego, że jest ona szybka, Azure RTOS ThreadX jest również wysoce deterministyczna.</span><span class="sxs-lookup"><span data-stu-id="689f2-261">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="689f2-262">Zapewnia ona taką samą wydajność, niezależnie od tego, czy jest gotowych 200 wątków, czy tylko jeden.</span><span class="sxs-lookup"><span data-stu-id="689f2-262">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="689f2-263">Poniżej podano niektóre typowe charakterystyki wydajności Azure RTOS ThreadX:</span><span class="sxs-lookup"><span data-stu-id="689f2-263">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="689f2-264">Szybki rozruch: Azure RTOS ThreadX uruchamia się w mniej niż 120 cyklach.</span><span class="sxs-lookup"><span data-stu-id="689f2-264">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="689f2-265">Opcjonalne usunięcie podstawowego sprawdzania błędów: podstawowe Azure RTOS sprawdzania błędów ThreadX można pominąć w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="689f2-265">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="689f2-266">Może to być przydatne, gdy kod aplikacji jest weryfikowany i nie wymaga już sprawdzania błędów dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="689f2-266">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="689f2-267">Należy pamiętać, że można to zrobić w jednostce kompilacji, a nie w całym systemie.</span><span class="sxs-lookup"><span data-stu-id="689f2-267">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="689f2-268">Picokernel™ Design: Usługi nie są nakładane na siebie, eliminując niepotrzebne obciążenia wywołań funkcji.</span><span class="sxs-lookup"><span data-stu-id="689f2-268">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="689f2-269">\*Zoptymalizowane przetwarzanie przerwań: tylko rejestry scratch są zapisywane/przywracane podczas wejścia/wyjścia isr, chyba że wywłaszczenie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="689f2-269">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="689f2-270">Zoptymalizowane przetwarzanie interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="689f2-270">Optimized API Processing:</span></span>

    |<span data-ttu-id="689f2-271">Azure RTOS ThreadX Service</span><span class="sxs-lookup"><span data-stu-id="689f2-271">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="689f2-272">Czas usługi w mikrosekundach\*</span><span class="sxs-lookup"><span data-stu-id="689f2-272">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="689f2-273">Wstrzymywanie wątku</span><span class="sxs-lookup"><span data-stu-id="689f2-273">Thread Suspend</span></span>  |<span data-ttu-id="689f2-274">0,6</span><span class="sxs-lookup"><span data-stu-id="689f2-274">0.6</span></span>  |
    |<span data-ttu-id="689f2-275">Wznawianie wątku</span><span class="sxs-lookup"><span data-stu-id="689f2-275">Thread Resume</span></span>  |<span data-ttu-id="689f2-276">0,6</span><span class="sxs-lookup"><span data-stu-id="689f2-276">0.6</span></span>  |
    |<span data-ttu-id="689f2-277">Wysyłanie w kolejce</span><span class="sxs-lookup"><span data-stu-id="689f2-277">Queue Send</span></span>  |<span data-ttu-id="689f2-278">0.3</span><span class="sxs-lookup"><span data-stu-id="689f2-278">0.3</span></span>  |
    |<span data-ttu-id="689f2-279">Odbieranie w kolejce</span><span class="sxs-lookup"><span data-stu-id="689f2-279">Queue Receive</span></span>  |<span data-ttu-id="689f2-280">0.3</span><span class="sxs-lookup"><span data-stu-id="689f2-280">0.3</span></span>  |
    |<span data-ttu-id="689f2-281">Uzyskiwanie Semafora</span><span class="sxs-lookup"><span data-stu-id="689f2-281">Get Semaphore</span></span>  |<span data-ttu-id="689f2-282">0,2</span><span class="sxs-lookup"><span data-stu-id="689f2-282">0.2</span></span>  |
    |<span data-ttu-id="689f2-283">Umieść Semafor</span><span class="sxs-lookup"><span data-stu-id="689f2-283">Put Semaphore</span></span>  |<span data-ttu-id="689f2-284">0,2</span><span class="sxs-lookup"><span data-stu-id="689f2-284">0.2</span></span>  |
    |<span data-ttu-id="689f2-285">Przełącznik kontekstu</span><span class="sxs-lookup"><span data-stu-id="689f2-285">Context Switch</span></span>  |<span data-ttu-id="689f2-286">0,4</span><span class="sxs-lookup"><span data-stu-id="689f2-286">0.4</span></span>  |
    |<span data-ttu-id="689f2-287">Odpowiedź na przerwanie</span><span class="sxs-lookup"><span data-stu-id="689f2-287">Interrupt Response</span></span>  |<span data-ttu-id="689f2-288">0.0 – 0.6</span><span class="sxs-lookup"><span data-stu-id="689f2-288">0.0 – 0.6</span></span>  |

    <span data-ttu-id="689f2-289">\**Wartości wydajności oparte na typowym procesorze z częstotliwością 200 MHz.*</span><span class="sxs-lookup"><span data-stu-id="689f2-289">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="689f2-290">Zaawansowana technologia</span><span class="sxs-lookup"><span data-stu-id="689f2-290">Advanced technology</span></span>

<span data-ttu-id="689f2-291">Azure RTOS ThreadX to zaawansowana technologia, której najważniejszą funkcją jest planowanie próg wywłaszczania.</span><span class="sxs-lookup"><span data-stu-id="689f2-291">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="689f2-292">Ta funkcja jest unikatowa dla Azure RTOS ThreadX i była przedmiotem rozległych badań akademickich.</span><span class="sxs-lookup"><span data-stu-id="689f2-292">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="689f2-293">Zobacz na przykład [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)(Planowanie zadań z progiem wywłaściwości), a ich autorstwa: Yun Wang, University Of Ichia University i Manas Saksena z Uniwersytetu Pittsburgh.</span><span class="sxs-lookup"><span data-stu-id="689f2-293">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="689f2-294">Weź pod uwagę możliwości Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="689f2-294">Consider the capabilities of Azure RTOS ThreadX.</span></span>

* <span data-ttu-id="689f2-295">Kompletne i kompleksowe obiekty wielozadaniowości</span><span class="sxs-lookup"><span data-stu-id="689f2-295">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="689f2-296">Wątki, czasomierze aplikacji, kolejki komunikatów, zliczanie semaforów, mutexów, flag zdarzeń, blokowych i bajtowych pul pamięci</span><span class="sxs-lookup"><span data-stu-id="689f2-296">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="689f2-297">Priority-Based planowanie wywłaszcze</span><span class="sxs-lookup"><span data-stu-id="689f2-297">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="689f2-298">Elastyczność priorytetu — do 1024 poziomów priorytetów</span><span class="sxs-lookup"><span data-stu-id="689f2-298">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="689f2-299">Wspólne planowanie</span><span class="sxs-lookup"><span data-stu-id="689f2-299">Cooperative Scheduling</span></span>
* <span data-ttu-id="689f2-300">Próg wywłaszczania™ — unikatowy dla Azure RTOS ThreadX, pomaga ograniczyć przełączniki kontekstu i pomóc w zagwarantowaniu możliwości planowania (na badania akademickie)</span><span class="sxs-lookup"><span data-stu-id="689f2-300">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="689f2-301">Ochrona pamięci za pośrednictwem Azure RTOS ThreadX MODULES</span><span class="sxs-lookup"><span data-stu-id="689f2-301">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="689f2-302">W pełni deterministyczny</span><span class="sxs-lookup"><span data-stu-id="689f2-302">Fully Deterministic</span></span>
* <span data-ttu-id="689f2-303">Śledzenie zdarzeń — przechwytywanie *ostatnich n* zdarzeń systemu/aplikacji</span><span class="sxs-lookup"><span data-stu-id="689f2-303">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="689f2-304">Łańcuch zdarzeń™ — rejestrowanie funkcji wywołania zwrotnego "notify" specyficznej dla aplikacji dla każdego obiektu komunikacji lub synchronizacji Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="689f2-304">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="689f2-305">Azure RTOS moduły ThreadX z opcjonalną ochroną pamięci</span><span class="sxs-lookup"><span data-stu-id="689f2-305">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="689f2-306">Run-Time metryk wydajności</span><span class="sxs-lookup"><span data-stu-id="689f2-306">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="689f2-307">Liczba wznowień wątków</span><span class="sxs-lookup"><span data-stu-id="689f2-307">Number of thread resumptions</span></span>
  * <span data-ttu-id="689f2-308">Liczba zawieszenia wątków</span><span class="sxs-lookup"><span data-stu-id="689f2-308">Number of thread suspensions</span></span>
  * <span data-ttu-id="689f2-309">Liczba wywłaszczeń wątków na żądanie</span><span class="sxs-lookup"><span data-stu-id="689f2-309">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="689f2-310">Liczba asynchronicznych wywłaszcze przerwań wątków</span><span class="sxs-lookup"><span data-stu-id="689f2-310">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="689f2-311">Liczba inwersji priorytetów wątków</span><span class="sxs-lookup"><span data-stu-id="689f2-311">Number of thread priority inversions</span></span>
  * <span data-ttu-id="689f2-312">Liczba wątków</span><span class="sxs-lookup"><span data-stu-id="689f2-312">Number of thread relinquishes</span></span>
* <span data-ttu-id="689f2-313">Execution Profile Kit (EPK)</span><span class="sxs-lookup"><span data-stu-id="689f2-313">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="689f2-314">Oddzielny stos przerwań</span><span class="sxs-lookup"><span data-stu-id="689f2-314">Separate Interrupt Stack</span></span>
* <span data-ttu-id="689f2-315">Run-Time Stack Analysis</span><span class="sxs-lookup"><span data-stu-id="689f2-315">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="689f2-316">Zoptymalizowane przetwarzanie przerwań czasomierza</span><span class="sxs-lookup"><span data-stu-id="689f2-316">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="689f2-317">Obsługa wielu rdzeni (AMP & SMP)</span><span class="sxs-lookup"><span data-stu-id="689f2-317">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="689f2-318">Standard Azure RTOS ThreadX jest często używany w asymetrycznym wieloprocesorowym przetwarzaniu (AMP), gdzie oddzielna kopia pliku Azure RTOS ThreadX i aplikacji (lub Linux) jest wykonywana na każdym rdzeniu i komunikuje się ze sobą za pośrednictwem pamięci współdzielonego lub mechanizmu komunikacji między procesorami, takiego jak OpenAMP (Azure RTOS ThreadX obsługuje openAMP).</span><span class="sxs-lookup"><span data-stu-id="689f2-318">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="689f2-319">Jest to najbardziej typowa konfiguracja wielordzeniowa korzystająca z Azure RTOS ThreadX i może być najbardziej wydajna, jeśli aplikacja jest w stanie efektywnie załadować procesory.</span><span class="sxs-lookup"><span data-stu-id="689f2-319">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="689f2-320">W środowiskach, w których ładowanie procesorów jest bardzo dynamiczne, Azure RTOS ThreadX Symetric Multiprocessing (SMP) jest dostępny dla następujących rodzin procesorów:</span><span class="sxs-lookup"><span data-stu-id="689f2-320">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="689f2-321">Arm Cortex-Ax</span><span class="sxs-lookup"><span data-stu-id="689f2-321">ARM Cortex-Ax</span></span>
* <span data-ttu-id="689f2-322">Arm Cortex-Rx</span><span class="sxs-lookup"><span data-stu-id="689f2-322">ARM Cortex-Rx</span></span>
* <span data-ttu-id="689f2-323">Arm Cortex-A5x 64-bitowy</span><span class="sxs-lookup"><span data-stu-id="689f2-323">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="689f2-324">MIPS 34K, 1004K i interAptiv</span><span class="sxs-lookup"><span data-stu-id="689f2-324">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="689f2-325">PowerPC</span><span class="sxs-lookup"><span data-stu-id="689f2-325">PowerPC</span></span>
* <span data-ttu-id="689f2-326">Synopsys ARC HS</span><span class="sxs-lookup"><span data-stu-id="689f2-326">Synopsys ARC HS</span></span>
* <span data-ttu-id="689f2-327">x86</span><span class="sxs-lookup"><span data-stu-id="689f2-327">x86</span></span>

<span data-ttu-id="689f2-328">Azure RTOS ThreadX SMP wykonuje dynamiczne równoważenie obciążenia między *n* procesorami i umożliwia dostęp do wszystkich zasobów Azure RTOS ThreadX (kolejek, semaforów, flag zdarzeń, pul pamięci itp.) przez dowolny wątek na dowolnym rdzeniu.</span><span class="sxs-lookup"><span data-stu-id="689f2-328">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="689f2-329">Azure RTOS ThreadX SMP umożliwia pełny interfejs API Azure RTOS ThreadX na wszystkich rdzeniach i wprowadza następujące nowe interfejsy API dotyczące operacji SMP:</span><span class="sxs-lookup"><span data-stu-id="689f2-329">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="689f2-330">Ochrona pamięci za pośrednictwem Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="689f2-330">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="689f2-331">Dodatek o nazwie Azure RTOS ThreadX MODULES umożliwia dołączanie co najmniej jednego wątków aplikacji do "modułu", który może być dynamicznie ładowany i uruchamiany (lub wykonywany w miejscu) w miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="689f2-331">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="689f2-332">Moduły umożliwiają uaktualnianie pól, naprawianie usterek i partycjonowanie programów, aby umożliwić dużym aplikacjom zajmowanie tylko pamięci wymaganej przez aktywne wątki.</span><span class="sxs-lookup"><span data-stu-id="689f2-332">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="689f2-333">Moduły mają również całkowicie oddzieloną przestrzeń adresową od Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="689f2-333">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="689f2-334">Dzięki temu Azure RTOS ThreadX może chronić pamięć (za pośrednictwem modułu MPU lub MMU) w taki sposób, że przypadkowy dostęp poza modułem nie będzie mógł uszkodzić żadnego innego składnika oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="689f2-334">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>

## <a name="misra-compliant"></a><span data-ttu-id="689f2-335">Zgodne ze standardem MISRA</span><span class="sxs-lookup"><span data-stu-id="689f2-335">MISRA compliant</span></span>

<span data-ttu-id="689f2-336">Azure RTOS ThreadX i Azure RTOS SMP ThreadX są zgodne ze standardem MISRA-C:2004 i MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="689f2-336">Azure RTOS ThreadX and Azure RTOS ThreadX SMP source code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="689f2-337">MISRA C to zestaw wytycznych dotyczących programowania dla systemów krytycznych korzystających z języka programowania C.</span><span class="sxs-lookup"><span data-stu-id="689f2-337">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="689f2-338">Oryginalne wytyczne MISRA C były przeznaczone głównie dla aplikacji samochodowych. Jednak język MISRA C jest teraz powszechnie uznawany za stosowany do wszystkich aplikacji o krytycznym znaczeniu dla bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="689f2-338">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="689f2-339">Azure RTOS ThreadX jest zgodny ze wszystkimi wymaganymi i obowiązkowymi regułami MISRA-C:2004 i MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="689f2-339">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certyfikacja Misra":::

## <a name="supports-most-popular-tools"></a><span data-ttu-id="689f2-341">Obsługuje najpopularniejsze narzędzia</span><span class="sxs-lookup"><span data-stu-id="689f2-341">Supports most popular tools</span></span>

<span data-ttu-id="689f2-342">Azure RTOS ThreadX obsługuje najpopularniejsze osadzone narzędzia programowe, w tym embedded Workbench™ systemu IAR, który ma również najbardziej kompleksową świadomość jądra Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="689f2-342">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="689f2-343">Dodatkowa integracja narzędzi obejmuje GNU (GCC), ARM DS-5/uVision®, GreenRow MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore i wszystkie urządzenia analogiczne.</span><span class="sxs-lookup"><span data-stu-id="689f2-343">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>

## <a name="adaptation-layer-for-threadx"></a><span data-ttu-id="689f2-344">Warstwa adaptacji dla ThreadX</span><span class="sxs-lookup"><span data-stu-id="689f2-344">Adaptation layer for ThreadX</span></span>

<span data-ttu-id="689f2-345">System ThreadX usługi Azure RTOS to zaawansowany system operacyjny czasu rzeczywistego zaprojektowany specjalnie pod kątem głęboko osadzonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="689f2-345">Azure RTOS ThreadX is an advanced real-time operating system (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="689f2-346">Aby ułatwić migrację aplikacji do systemu Auzre RTOS, ThreadX udostępnia warstwy adaptacji dla różnych starszych interfejsów API RTOS (FreeRTOS, POSIX, OSEK itp.) [](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers)</span><span class="sxs-lookup"><span data-stu-id="689f2-346">To help ease application migration to Auzre RTOS, ThreadX provides [adaption layers](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) for various legacy RTOS APIs (FreeRTOS, POSIX, OSEK, etc.)</span></span>
