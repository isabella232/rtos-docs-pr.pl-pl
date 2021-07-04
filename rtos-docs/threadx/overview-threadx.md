---
title: Opis Azure RTOS ThreadX
description: Azure ThreadX to zaawansowany system operacyjny w czasie rzeczywistym (RTOS) zaprojektowany specjalnie z myślą o aplikacjach głęboko osadzonych.
author: philmea
ms.author: philmea
ms.date: 6/9/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0fb861c2291046c2ac6edf1d03014996daa09a8e
ms.sourcegitcommit: c1b00341e0c5ab71372f3d9cc4ee3bdd3702b805
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111988366"
---
# <a name="overview-of-azure-rtos-threadx"></a><span data-ttu-id="a09a7-103">Omówienie Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a09a7-103">Overview of Azure RTOS ThreadX</span></span>

<span data-ttu-id="a09a7-104">Azure RTOS ThreadX to zaawansowany system operacyjny Real-Time klasy przemysłowej (RTOS) firmy Microsoft zaprojektowany specjalnie z myślą o aplikacjach głęboko osadzonych, działających w czasie rzeczywistym i IoT.</span><span class="sxs-lookup"><span data-stu-id="a09a7-104">Azure RTOS ThreadX is Microsoft's advanced industrial grade Real-Time Operating System (RTOS) designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="a09a7-105">Azure RTOS ThreadX zapewnia zaawansowane funkcje planowania, komunikacji, synchronizacji, czasomierza, zarządzania pamięcią i zarządzania przerwami.</span><span class="sxs-lookup"><span data-stu-id="a09a7-105">Azure RTOS ThreadX provides advanced scheduling, communication, synchronization, timer, memory management, and interrupt management facilities.</span></span> <span data-ttu-id="a09a7-106">Ponadto system Azure RTOS ThreadX ma wiele zaawansowanych funkcji, takich jak picokernel™ architektura, próg wywłaszczania™ planowanie, łańcuch zdarzeń, profilowanie wykonywania ™, metryki wydajności i śledzenie zdarzeń systemu.</span><span class="sxs-lookup"><span data-stu-id="a09a7-106">In addition, Azure RTOS ThreadX has many advanced features, including its picokernel™ architecture, preemption-threshold™ scheduling, event-chaining,™ execution profiling, performance metrics, and system event tracing.</span></span> <span data-ttu-id="a09a7-107">W połączeniu z doskonałą łatwością obsługi Azure RTOS ThreadX jest idealnym wyborem dla najbardziej wymagających aplikacji osadzonych.</span><span class="sxs-lookup"><span data-stu-id="a09a7-107">Combined with its superior ease-of-use, Azure RTOS ThreadX is the ideal choice for the most demanding of embedded applications.</span></span> <span data-ttu-id="a09a7-108">Od 2017 r. Azure RTOS ThreadX ma ponad 6,2 miliarda wdrożeń w wielu różnych produktach, w tym urządzeniach konsumenckich, urządzeniach elektronicznych i przemysłowych urządzeniach sterujących.</span><span class="sxs-lookup"><span data-stu-id="a09a7-108">As of 2017, Azure RTOS ThreadX has over 6.2 billion deployments, in a wide variety of products, including consumer devices, medical electronics, and industrial control equipment.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="a09a7-109">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="a09a7-109">API Protocols</span></span>

### <a name="azure-rtos-threadx-services"></a><span data-ttu-id="a09a7-110">Azure RTOS ThreadX Services</span><span class="sxs-lookup"><span data-stu-id="a09a7-110">Azure RTOS ThreadX Services</span></span>

* <span data-ttu-id="a09a7-111">Dynamiczne tworzenie wątku</span><span class="sxs-lookup"><span data-stu-id="a09a7-111">Dynamic thread creation</span></span>
* <span data-ttu-id="a09a7-112">Brak limitów liczby wątków</span><span class="sxs-lookup"><span data-stu-id="a09a7-112">No limits on the number of threads</span></span>
* <span data-ttu-id="a09a7-113">Interfejsy API wątków głównych obejmują:</span><span class="sxs-lookup"><span data-stu-id="a09a7-113">Main thread APIs include:</span></span>
  * <span data-ttu-id="a09a7-114">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="a09a7-114">tx_thread_create</span></span>
  * <span data-ttu-id="a09a7-115">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="a09a7-115">tx_thread_delete</span></span>
  * <span data-ttu-id="a09a7-116">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="a09a7-116">tx_thread_preemption_change</span></span>
  * <span data-ttu-id="a09a7-117">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="a09a7-117">tx_thread_priority_change</span></span>
  * <span data-ttu-id="a09a7-118">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="a09a7-118">tx_thread_relinquish</span></span>
  * <span data-ttu-id="a09a7-119">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="a09a7-119">tx_thread_reset</span></span>
  * <span data-ttu-id="a09a7-120">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="a09a7-120">tx_thread_resume</span></span>
  * <span data-ttu-id="a09a7-121">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="a09a7-121">tx_thread_sleep</span></span>
  * <span data-ttu-id="a09a7-122">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="a09a7-122">tx_thread_suspend</span></span>
  * <span data-ttu-id="a09a7-123">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="a09a7-123">tx_thread_terminate</span></span>
  * <span data-ttu-id="a09a7-124">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="a09a7-124">tx_thread_wait_abort</span></span>
* <span data-ttu-id="a09a7-125">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="a09a7-125">Additional information and performance APIs</span></span>

### <a name="message-queues"></a><span data-ttu-id="a09a7-126">Kolejki komunikatów</span><span class="sxs-lookup"><span data-stu-id="a09a7-126">Message Queues</span></span>

* <span data-ttu-id="a09a7-127">Dynamiczne tworzenie kolejek</span><span class="sxs-lookup"><span data-stu-id="a09a7-127">Dynamic queue creation</span></span>
* <span data-ttu-id="a09a7-128">Brak limitów liczby kolejek</span><span class="sxs-lookup"><span data-stu-id="a09a7-128">No limits on the number of queues</span></span>
* <span data-ttu-id="a09a7-129">Komunikaty skopiowane przez wartość (lub przez odwołanie za pośrednictwem wskaźnika)</span><span class="sxs-lookup"><span data-stu-id="a09a7-129">Messages copied by value (or by reference via pointer)</span></span>
* <span data-ttu-id="a09a7-130">Rozmiary komunikatów od 1 do 16 słów 32-bitowych</span><span class="sxs-lookup"><span data-stu-id="a09a7-130">Message sizes from 1 to 16 32-bit words</span></span>
* <span data-ttu-id="a09a7-131">Opcjonalne zawieszenie wątku na pustym i pełnym</span><span class="sxs-lookup"><span data-stu-id="a09a7-131">Optional thread suspension on empty and full</span></span>
* <span data-ttu-id="a09a7-132">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="a09a7-132">Optional timeout on all suspension</span></span>
* <span data-ttu-id="a09a7-133">Interfejsy API kolejki komunikatów głównych obejmują:</span><span class="sxs-lookup"><span data-stu-id="a09a7-133">Main message queue APIs include:</span></span>
  * <span data-ttu-id="a09a7-134">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="a09a7-134">tx_queue_create</span></span>
  * <span data-ttu-id="a09a7-135">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="a09a7-135">tx_queue_delete</span></span>
  * <span data-ttu-id="a09a7-136">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="a09a7-136">tx_queue_flush</span></span>
  * <span data-ttu-id="a09a7-137">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="a09a7-137">tx_queue_front_send</span></span>
  * <span data-ttu-id="a09a7-138">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="a09a7-138">tx_queue_receive</span></span>
  * <span data-ttu-id="a09a7-139">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="a09a7-139">tx_queue_send_notify</span></span>
* <span data-ttu-id="a09a7-140">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="a09a7-140">Additional information and performance APIs</span></span>

### <a name="counting-semaphores"></a><span data-ttu-id="a09a7-141">Zliczanie semaforów</span><span class="sxs-lookup"><span data-stu-id="a09a7-141">Counting Semaphores</span></span>

* <span data-ttu-id="a09a7-142">Dynamiczne tworzenie semafora</span><span class="sxs-lookup"><span data-stu-id="a09a7-142">Dynamic semaphore creation</span></span>
* <span data-ttu-id="a09a7-143">Brak limitów liczby semaforów</span><span class="sxs-lookup"><span data-stu-id="a09a7-143">No limits on the number of semaphores</span></span>
* <span data-ttu-id="a09a7-144">32-bitowe zliczanie semaforów (od 0 do 4 294 967 295)</span><span class="sxs-lookup"><span data-stu-id="a09a7-144">32-bit counting semaphores (0 to 4,294,967,295)</span></span>
* <span data-ttu-id="a09a7-145">Obsługuje ochronę producentów i zasobów konsumentów</span><span class="sxs-lookup"><span data-stu-id="a09a7-145">Supports consumer-producer or resource protection</span></span>
* <span data-ttu-id="a09a7-146">Opcjonalne zawieszenie wątku, gdy semafor jest niedostępny</span><span class="sxs-lookup"><span data-stu-id="a09a7-146">Optional thread suspension when semaphore unavailable</span></span>
* <span data-ttu-id="a09a7-147">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="a09a7-147">Optional timeout on all suspension</span></span>
* <span data-ttu-id="a09a7-148">Główne interfejsy API semaforów obejmują:</span><span class="sxs-lookup"><span data-stu-id="a09a7-148">Main semaphore APIs include:</span></span>
  * <span data-ttu-id="a09a7-149">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="a09a7-149">tx_semaphore_create</span></span>
  * <span data-ttu-id="a09a7-150">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="a09a7-150">tx_semaphore_delete</span></span>
  * <span data-ttu-id="a09a7-151">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="a09a7-151">tx_semaphore_get</span></span>
  * <span data-ttu-id="a09a7-152">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="a09a7-152">tx_semaphore_put</span></span>
  * <span data-ttu-id="a09a7-153">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="a09a7-153">tx_semaphore_put_notify</span></span>
* <span data-ttu-id="a09a7-154">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="a09a7-154">Additional information and performance APIs</span></span>

### <a name="mutexes"></a><span data-ttu-id="a09a7-155">Muteksy</span><span class="sxs-lookup"><span data-stu-id="a09a7-155">Mutexes</span></span>

* <span data-ttu-id="a09a7-156">Dynamiczne tworzenie mutex</span><span class="sxs-lookup"><span data-stu-id="a09a7-156">Dynamic mutex creation</span></span>
* <span data-ttu-id="a09a7-157">Brak limitów liczby mutexes</span><span class="sxs-lookup"><span data-stu-id="a09a7-157">No limits on the number of mutexes</span></span>
* <span data-ttu-id="a09a7-158">Ochrona zagnieżdżonych zasobów jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="a09a7-158">Nested resource protection supported</span></span>
* <span data-ttu-id="a09a7-159">Obsługiwane jest opcjonalne dziedziczenie priorytetów</span><span class="sxs-lookup"><span data-stu-id="a09a7-159">Optional priority inheritance supported</span></span>
* <span data-ttu-id="a09a7-160">Opcjonalne zawieszenie wątku, gdy element mutex jest niedostępny</span><span class="sxs-lookup"><span data-stu-id="a09a7-160">Optional thread suspension when mutex unavailable</span></span>
* <span data-ttu-id="a09a7-161">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="a09a7-161">Optional timeout on all suspension</span></span>
* <span data-ttu-id="a09a7-162">Główne interfejsy API mutex obejmują:</span><span class="sxs-lookup"><span data-stu-id="a09a7-162">Main mutex APIs include:</span></span>
  * <span data-ttu-id="a09a7-163">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="a09a7-163">tx_mutex_create</span></span>
  * <span data-ttu-id="a09a7-164">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="a09a7-164">tx_mutex_delete</span></span>
  * <span data-ttu-id="a09a7-165">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="a09a7-165">tx_mutex_get</span></span>
  * <span data-ttu-id="a09a7-166">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="a09a7-166">tx_mutex_put</span></span>
* <span data-ttu-id="a09a7-167">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="a09a7-167">Additional information and performance APIs</span></span>

### <a name="event-flags"></a><span data-ttu-id="a09a7-168">Flagi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a09a7-168">Event Flags</span></span>

* <span data-ttu-id="a09a7-169">Dynamiczne tworzenie grupy flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a09a7-169">Dynamic event flag group creation</span></span>
* <span data-ttu-id="a09a7-170">Brak limitów liczby grup flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a09a7-170">No limits on the number of event flag groups</span></span>
* <span data-ttu-id="a09a7-171">Synchronizacja jednego wątku lub wielu wątków</span><span class="sxs-lookup"><span data-stu-id="a09a7-171">Synchronization of one thread or multiple threads</span></span>
* <span data-ttu-id="a09a7-172">Niepodzielne uzyskiwanie i wyczyść obsługiwane</span><span class="sxs-lookup"><span data-stu-id="a09a7-172">Atomic get and clear supported</span></span>
* <span data-ttu-id="a09a7-173">Opcjonalne zawieszenie wielowątkowe dla zestawu zdarzeń AND/OR</span><span class="sxs-lookup"><span data-stu-id="a09a7-173">Optional multithread suspension on AND/OR set of events</span></span>
* <span data-ttu-id="a09a7-174">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="a09a7-174">Optional timeout on all suspension</span></span>
* <span data-ttu-id="a09a7-175">Interfejsy API flagi zdarzenia głównego obejmują:</span><span class="sxs-lookup"><span data-stu-id="a09a7-175">Main event flag APIs include:</span></span>
  * <span data-ttu-id="a09a7-176">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="a09a7-176">tx_event_flags_create</span></span>
  * <span data-ttu-id="a09a7-177">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="a09a7-177">tx_event_flags_delete</span></span>
  * <span data-ttu-id="a09a7-178">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="a09a7-178">tx_event_flags_get</span></span>
  * <span data-ttu-id="a09a7-179">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="a09a7-179">tx_event_flags_set</span></span>
  * <span data-ttu-id="a09a7-180">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="a09a7-180">tx_event_flags_set_notify</span></span>
* <span data-ttu-id="a09a7-181">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="a09a7-181">Additional information and performance APIs</span></span>

### <a name="block-memory-pools"></a><span data-ttu-id="a09a7-182">Blokuj pule pamięci</span><span class="sxs-lookup"><span data-stu-id="a09a7-182">Block Memory Pools</span></span>

* <span data-ttu-id="a09a7-183">Dynamiczne tworzenie puli bloków</span><span class="sxs-lookup"><span data-stu-id="a09a7-183">Dynamic block pool creation</span></span>
* <span data-ttu-id="a09a7-184">Brak limitów liczby pul bloków</span><span class="sxs-lookup"><span data-stu-id="a09a7-184">No limits on the number of block pools</span></span>
* <span data-ttu-id="a09a7-185">Brak limitów rozmiaru bloków o stałym rozmiarze lub rozmiaru puli</span><span class="sxs-lookup"><span data-stu-id="a09a7-185">No limits on size of fixed-size blocks or size of pool</span></span>
* <span data-ttu-id="a09a7-186">Najszybsza możliwa alokacja pamięci/deal-location</span><span class="sxs-lookup"><span data-stu-id="a09a7-186">Fastest possible memory allocation/deal-location</span></span>
* <span data-ttu-id="a09a7-187">Opcjonalne zawieszenie wątku w pustej puli</span><span class="sxs-lookup"><span data-stu-id="a09a7-187">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="a09a7-188">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="a09a7-188">Optional timeout on all suspension</span></span>
* <span data-ttu-id="a09a7-189">Główne interfejsy API puli bloków obejmują:</span><span class="sxs-lookup"><span data-stu-id="a09a7-189">Main block pool APIs include:</span></span>
  * <span data-ttu-id="a09a7-190">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="a09a7-190">tx_block_pool_create</span></span>
  * <span data-ttu-id="a09a7-191">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="a09a7-191">tx_block_pool_delete</span></span>
  * <span data-ttu-id="a09a7-192">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="a09a7-192">tx_block_allocate</span></span>
  * <span data-ttu-id="a09a7-193">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="a09a7-193">tx_block_release</span></span>
* <span data-ttu-id="a09a7-194">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="a09a7-194">Additional information and performance APIs</span></span>

### <a name="byte-memory-pools"></a><span data-ttu-id="a09a7-195">Bajtowe pule pamięci</span><span class="sxs-lookup"><span data-stu-id="a09a7-195">Byte Memory Pools</span></span>

* <span data-ttu-id="a09a7-196">Dynamiczne tworzenie puli bajtów</span><span class="sxs-lookup"><span data-stu-id="a09a7-196">Dynamic byte pool creation</span></span>
* <span data-ttu-id="a09a7-197">Brak limitów liczby pul bajtów</span><span class="sxs-lookup"><span data-stu-id="a09a7-197">No limits on the number of byte pools</span></span>
* <span data-ttu-id="a09a7-198">Brak limitów rozmiaru puli bajtów</span><span class="sxs-lookup"><span data-stu-id="a09a7-198">No limits on size of byte pool</span></span>
* <span data-ttu-id="a09a7-199">Najbardziej elastyczna alokacja/coklokacja pamięci o zmiennej długości</span><span class="sxs-lookup"><span data-stu-id="a09a7-199">Most flexible variable-length memory allocation/deallocation</span></span>
* <span data-ttu-id="a09a7-200">Obsługiwana lokalność rozmiaru alokacji</span><span class="sxs-lookup"><span data-stu-id="a09a7-200">Allocation size locality supported</span></span>
* <span data-ttu-id="a09a7-201">Opcjonalne zawieszenie wątku w pustej puli</span><span class="sxs-lookup"><span data-stu-id="a09a7-201">Optional thread suspension on empty pool</span></span>
* <span data-ttu-id="a09a7-202">Opcjonalny limit czasu dla całego zawieszenia</span><span class="sxs-lookup"><span data-stu-id="a09a7-202">Optional timeout on all suspension</span></span>
* <span data-ttu-id="a09a7-203">Interfejsy API puli bajtów głównych obejmują:</span><span class="sxs-lookup"><span data-stu-id="a09a7-203">Main byte pool APIs include:</span></span>
  * <span data-ttu-id="a09a7-204">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="a09a7-204">tx_byte_pool_create</span></span>
  * <span data-ttu-id="a09a7-205">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="a09a7-205">tx_byte_pool_delete</span></span>
  * <span data-ttu-id="a09a7-206">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="a09a7-206">tx_byte_allocate</span></span>
  * <span data-ttu-id="a09a7-207">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="a09a7-207">tx_byte_release</span></span>
* <span data-ttu-id="a09a7-208">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="a09a7-208">Additional information and performance APIs</span></span>

### <a name="application-timers"></a><span data-ttu-id="a09a7-209">Czasomierze aplikacji</span><span class="sxs-lookup"><span data-stu-id="a09a7-209">Application Timers</span></span>

* <span data-ttu-id="a09a7-210">Dynamiczne tworzenie czasomierza</span><span class="sxs-lookup"><span data-stu-id="a09a7-210">Dynamic timer creation</span></span>
* <span data-ttu-id="a09a7-211">Brak limitów liczby czasomierzy</span><span class="sxs-lookup"><span data-stu-id="a09a7-211">No limits on the number of timers</span></span>
* <span data-ttu-id="a09a7-212">Obsługiwane czasomierze okresowe lub czasomierze z jednym rzutem</span><span class="sxs-lookup"><span data-stu-id="a09a7-212">Periodic or one-shot timers supported</span></span>
* <span data-ttu-id="a09a7-213">Czasomierze okresowe mogą mieć inną wartość początkowego wygaśnięcia</span><span class="sxs-lookup"><span data-stu-id="a09a7-213">Periodic timers may have different initial expiration value</span></span>
* <span data-ttu-id="a09a7-214">Brak wyszukiwania aktywacji lub dezaktywacji czasomierza</span><span class="sxs-lookup"><span data-stu-id="a09a7-214">No searching on timer activation or deactivation</span></span>
* <span data-ttu-id="a09a7-215">Wszystkie czasomierze sterowane przez jedno sprzętowe przerwanie czasomierza</span><span class="sxs-lookup"><span data-stu-id="a09a7-215">All timers driven from one hardware timer interrupt</span></span>
* <span data-ttu-id="a09a7-216">Główne interfejsy API czasomierza obejmują:</span><span class="sxs-lookup"><span data-stu-id="a09a7-216">Main timer APIs include:</span></span>
  * <span data-ttu-id="a09a7-217">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="a09a7-217">tx_timer_create</span></span>
  * <span data-ttu-id="a09a7-218">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="a09a7-218">tx_timer_delete</span></span>
  * <span data-ttu-id="a09a7-219">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="a09a7-219">tx_timer_activate</span></span>
  * <span data-ttu-id="a09a7-220">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="a09a7-220">tx_timer_change</span></span>
  * <span data-ttu-id="a09a7-221">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="a09a7-221">tx_timer_deactivate</span></span>
* <span data-ttu-id="a09a7-222">Dodatkowe informacje i interfejsy API wydajności</span><span class="sxs-lookup"><span data-stu-id="a09a7-222">Additional information and performance APIs</span></span>

### <a name="azure-rtos-threadx-core-scheduler"></a><span data-ttu-id="a09a7-223">Azure RTOS ThreadX Core Scheduler</span><span class="sxs-lookup"><span data-stu-id="a09a7-223">Azure RTOS ThreadX Core Scheduler</span></span>

* <span data-ttu-id="a09a7-224">Minimalna ilość pamięci FLASH 2 KB, 1 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="a09a7-224">Minimal 2KB FLASH,1KB RAM footprint</span></span>
* <span data-ttu-id="a09a7-225">Szybki, podrzędny mikrosekundowy przełącznik kontekstowy</span><span class="sxs-lookup"><span data-stu-id="a09a7-225">Fast, sub-microsecond context-switch</span></span>
* <span data-ttu-id="a09a7-226">W pełni deterministyczne, niezależnie od liczby wątków</span><span class="sxs-lookup"><span data-stu-id="a09a7-226">Fully deterministic regardless of number of threads</span></span>
* <span data-ttu-id="a09a7-227">Oparte na priorytetach, w pełni wywłaszczujące planowanie</span><span class="sxs-lookup"><span data-stu-id="a09a7-227">Priority-based, fully preemptive-scheduling</span></span>
* <span data-ttu-id="a09a7-228">32 domyślne poziomy priorytetów, opcjonalnie do 1024 poziomów</span><span class="sxs-lookup"><span data-stu-id="a09a7-228">32 default priority levels, optionally up to 1024 levels</span></span>
* <span data-ttu-id="a09a7-229">Planowanie wspólne na poziomie priorytetu (FIFO)</span><span class="sxs-lookup"><span data-stu-id="a09a7-229">Cooperative scheduling within priority level (FIFO)</span></span>
* <span data-ttu-id="a09a7-230">Technologia progu wywłaszczenia</span><span class="sxs-lookup"><span data-stu-id="a09a7-230">Preemption-threshold technology</span></span>
* <span data-ttu-id="a09a7-231">Opcjonalne usługi czasomierza, w tym:</span><span class="sxs-lookup"><span data-stu-id="a09a7-231">Optional timer services, including:</span></span>
  * <span data-ttu-id="a09a7-232">Opcjonalny wycinek czasu dla każdego wątku</span><span class="sxs-lookup"><span data-stu-id="a09a7-232">Per-thread optional time-slice</span></span>
  * <span data-ttu-id="a09a7-233">Opcjonalny limit czasu dla wszystkich blokad</span><span class="sxs-lookup"><span data-stu-id="a09a7-233">Optional timeout on all blocking</span></span>
  * <span data-ttu-id="a09a7-234">Interfejsy API wymagają przerwania czasomierza sprzętowego</span><span class="sxs-lookup"><span data-stu-id="a09a7-234">APIs Requires on hardware timer interrupt</span></span>
* <span data-ttu-id="a09a7-235">Profilowanie wykonywania</span><span class="sxs-lookup"><span data-stu-id="a09a7-235">Execution profiling</span></span>
* <span data-ttu-id="a09a7-236">Śledzenie na poziomie systemu</span><span class="sxs-lookup"><span data-stu-id="a09a7-236">System-level Trace</span></span>
* <span data-ttu-id="a09a7-237">Bezpieczeństwo certyfikowane przez wiele standardów</span><span class="sxs-lookup"><span data-stu-id="a09a7-237">Safety certified to many standards</span></span>

## <a name="most-deployed-rtos"></a><span data-ttu-id="a09a7-238">Najczęściej wdrożony system RTOS</span><span class="sxs-lookup"><span data-stu-id="a09a7-238">Most deployed RTOS</span></span>

<span data-ttu-id="a09a7-239">Azure RTOS ThreadX ma ponad 6,2 miliarda wdrożeń na całym świecie, zgodnie z wiodącymi firmami analizy rynku M2M, VDC Research.</span><span class="sxs-lookup"><span data-stu-id="a09a7-239">Azure RTOS ThreadX has over 6.2 billion deployments worldwide, according to the leading M2M market intelligence firm, VDC Research.</span></span> <span data-ttu-id="a09a7-240">Popularność technologii Azure RTOS ThreadX jest bardzo duża dla jej niezawodności, jakości, rozmiaru, wydajności, zaawansowanych funkcji, łatwości użycia i ogólnych zalet czasu do rynku.</span><span class="sxs-lookup"><span data-stu-id="a09a7-240">The popularity of Azure RTOS ThreadX is a testament to its reliability, quality, size, performance, advanced features, ease-of-use, and overall time-to-market advantages.</span></span>

> <span data-ttu-id="a09a7-241">*"Obserwowaliśmy trajektorię rozwoju THREADX na rynkach bezprzewodowych i IoT od momentu jej rozwoju i jesteśmy coraz bardziej pod wrażeniem powszechnego przyjęcia technologii THREADX w branży".*</span><span class="sxs-lookup"><span data-stu-id="a09a7-241">*“We have followed the growth trajectory of THREADX in the wireless and IoT markets since the company’s founding, and are increasingly impressed by the widespread industry adoption of THREADX.”*</span></span> <span data-ttu-id="a09a7-242">— Chris Rommel, wiceprezes ds. badań VDC</span><span class="sxs-lookup"><span data-stu-id="a09a7-242">– Chris Rommel, Executive Vice President, VDC Research</span></span>

## <a name="small-footprint"></a><span data-ttu-id="a09a7-243">Małe zużycie pamięci</span><span class="sxs-lookup"><span data-stu-id="a09a7-243">Small footprint</span></span>

<span data-ttu-id="a09a7-244">Azure RTOS ThreadX wymaga bardzo małego obszaru instrukcji 2KB i 1 KB pamięci RAM w celu jego minimalnego zużycie.</span><span class="sxs-lookup"><span data-stu-id="a09a7-244">Azure RTOS ThreadX requires a remarkably small 2KB instruction area and 1KB of RAM for its minimal footprint.</span></span> <span data-ttu-id="a09a7-245">Wynika to głównie z niewarstwowej architektury picokernel™ automatycznego skalowania.</span><span class="sxs-lookup"><span data-stu-id="a09a7-245">This is largely due to its non-layered picokernel™ architecture and automatic scaling.</span></span> <span data-ttu-id="a09a7-246">Automatyczne skalowanie oznacza, że w końcowej ilustracji w czasie łączenia uwzględniane są tylko usługi (i infrastruktura obsługująca) używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="a09a7-246">Automatic scaling means that only the services (and supporting infrastructure) used by the application are included in the final image at link time.</span></span>

<span data-ttu-id="a09a7-247">Oto kilka typowych cech Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a09a7-247">Here are some typical Azure RTOS ThreadX size characteristics.</span></span>

|<span data-ttu-id="a09a7-248">Azure RTOS ThreadX Service</span><span class="sxs-lookup"><span data-stu-id="a09a7-248">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="a09a7-249">Typowy rozmiar w bajtach</span><span class="sxs-lookup"><span data-stu-id="a09a7-249">Typical Size in Bytes</span></span>  |
|---------|---------|
|<span data-ttu-id="a09a7-250">Usługi podstawowe (wymagaj)</span><span class="sxs-lookup"><span data-stu-id="a09a7-250">Core Services (Require)</span></span> |<span data-ttu-id="a09a7-251">2000</span><span class="sxs-lookup"><span data-stu-id="a09a7-251">2,000</span></span>  |
|<span data-ttu-id="a09a7-252">Queue Services</span><span class="sxs-lookup"><span data-stu-id="a09a7-252">Queue Services</span></span>  |<span data-ttu-id="a09a7-253">900</span><span class="sxs-lookup"><span data-stu-id="a09a7-253">900</span></span>  |
|<span data-ttu-id="a09a7-254">Event Flag Services</span><span class="sxs-lookup"><span data-stu-id="a09a7-254">Event Flag Services</span></span>  |<span data-ttu-id="a09a7-255">900</span><span class="sxs-lookup"><span data-stu-id="a09a7-255">900</span></span>  |
|<span data-ttu-id="a09a7-256">Semaphore Services</span><span class="sxs-lookup"><span data-stu-id="a09a7-256">Semaphore Services</span></span>  |<span data-ttu-id="a09a7-257">450</span><span class="sxs-lookup"><span data-stu-id="a09a7-257">450</span></span>  |
|<span data-ttu-id="a09a7-258">Usługi Mutex</span><span class="sxs-lookup"><span data-stu-id="a09a7-258">Mutex Services</span></span>  |<span data-ttu-id="a09a7-259">1200</span><span class="sxs-lookup"><span data-stu-id="a09a7-259">1,200</span></span>  |
|<span data-ttu-id="a09a7-260">Blokuj usługi pamięci</span><span class="sxs-lookup"><span data-stu-id="a09a7-260">Block Memory Services</span></span>  |<span data-ttu-id="a09a7-261">550</span><span class="sxs-lookup"><span data-stu-id="a09a7-261">550</span></span>  |
|<span data-ttu-id="a09a7-262">Usługi pamięci bajtowej</span><span class="sxs-lookup"><span data-stu-id="a09a7-262">Byte Memory Services</span></span>  |<span data-ttu-id="a09a7-263">900</span><span class="sxs-lookup"><span data-stu-id="a09a7-263">900</span></span>  |

## <a name="fast-execution"></a><span data-ttu-id="a09a7-264">Szybkie wykonywanie</span><span class="sxs-lookup"><span data-stu-id="a09a7-264">Fast execution</span></span>

<span data-ttu-id="a09a7-265">Azure RTOS ThreadX osiąga przełącznik kontekstu podrzędnego mikrosekund na najpopularniejszych procesorach i jest znacznie szybszy ogólnie niż inne komercyjne cele RTOS.</span><span class="sxs-lookup"><span data-stu-id="a09a7-265">Azure RTOS ThreadX achieves a sub-microsecond context switch on most popular processors and is significantly faster overall than other commercial RTOSes.</span></span> <span data-ttu-id="a09a7-266">Oprócz tego, że jest ona szybka, Azure RTOS ThreadX jest również wysoce deterministyczna.</span><span class="sxs-lookup"><span data-stu-id="a09a7-266">In addition to being fast, Azure RTOS ThreadX is also highly deterministic.</span></span> <span data-ttu-id="a09a7-267">Zapewnia ona taką samą szybkość działania niezależnie od tego, czy jest gotowych 200 wątków, czy tylko jeden.</span><span class="sxs-lookup"><span data-stu-id="a09a7-267">It achieves the same fast performance whether there are 200 threads ready, or just one.</span></span>

<span data-ttu-id="a09a7-268">Poniżej podano niektóre typowe charakterystyki wydajności Azure RTOS ThreadX:</span><span class="sxs-lookup"><span data-stu-id="a09a7-268">Here are some typical performance characteristics of Azure RTOS ThreadX:</span></span>

* <span data-ttu-id="a09a7-269">Szybki rozruch: Azure RTOS ThreadX uruchamia się w mniej niż 120 cyklach.</span><span class="sxs-lookup"><span data-stu-id="a09a7-269">Fast Boot: Azure RTOS ThreadX boots in less than 120 cycles.</span></span>
* <span data-ttu-id="a09a7-270">Opcjonalne usunięcie podstawowego sprawdzania błędów: podstawowe Azure RTOS sprawdzania błędów ThreadX można pominąć w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a09a7-270">Optional Removal of basic error checking: Basic Azure RTOS ThreadX error checking can be skipped at compile time.</span></span> <span data-ttu-id="a09a7-271">Może to być przydatne, gdy kod aplikacji jest weryfikowany i nie wymaga już sprawdzania błędów dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="a09a7-271">This can be useful when the application code is verified and no longer requires error checking on each parameter.</span></span> <span data-ttu-id="a09a7-272">Należy pamiętać, że można to zrobić w jednostce kompilacji, a nie w całym systemie.</span><span class="sxs-lookup"><span data-stu-id="a09a7-272">Note that this can be done on a compilation unit, rather than system-wide.</span></span>
* <span data-ttu-id="a09a7-273">Picokernel™ Design: Usługi nie są nakładane na siebie, eliminując niepotrzebne obciążenia wywołań funkcji.</span><span class="sxs-lookup"><span data-stu-id="a09a7-273">Picokernel™ Design: Services are not layered on each other, thus eliminating unnecessary function call overhead.</span></span>
* <span data-ttu-id="a09a7-274">\*Zoptymalizowane przetwarzanie przerwań: tylko rejestry scratch są zapisywane/przywracane podczas wejścia/wyjścia isr, chyba że wywłaszczenie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="a09a7-274">\*Optimized Interrupt Processing: Only scratch registers are saved/restored upon ISR entry/exit, unless preemption is necessary.</span></span>
* <span data-ttu-id="a09a7-275">Zoptymalizowane przetwarzanie interfejsu API:</span><span class="sxs-lookup"><span data-stu-id="a09a7-275">Optimized API Processing:</span></span>

    |<span data-ttu-id="a09a7-276">Azure RTOS ThreadX Service</span><span class="sxs-lookup"><span data-stu-id="a09a7-276">Azure RTOS ThreadX Service</span></span>  |<span data-ttu-id="a09a7-277">Czas usługi w mikrosekundach\*</span><span class="sxs-lookup"><span data-stu-id="a09a7-277">Service Time in Microseconds\*</span></span>  |
    |---------|---------|
    |<span data-ttu-id="a09a7-278">Wstrzymywanie wątku</span><span class="sxs-lookup"><span data-stu-id="a09a7-278">Thread Suspend</span></span>  |<span data-ttu-id="a09a7-279">0,6</span><span class="sxs-lookup"><span data-stu-id="a09a7-279">0.6</span></span>  |
    |<span data-ttu-id="a09a7-280">Wznawianie wątku</span><span class="sxs-lookup"><span data-stu-id="a09a7-280">Thread Resume</span></span>  |<span data-ttu-id="a09a7-281">0,6</span><span class="sxs-lookup"><span data-stu-id="a09a7-281">0.6</span></span>  |
    |<span data-ttu-id="a09a7-282">Wysyłanie w kolejce</span><span class="sxs-lookup"><span data-stu-id="a09a7-282">Queue Send</span></span>  |<span data-ttu-id="a09a7-283">0.3</span><span class="sxs-lookup"><span data-stu-id="a09a7-283">0.3</span></span>  |
    |<span data-ttu-id="a09a7-284">Odbieranie w kolejce</span><span class="sxs-lookup"><span data-stu-id="a09a7-284">Queue Receive</span></span>  |<span data-ttu-id="a09a7-285">0.3</span><span class="sxs-lookup"><span data-stu-id="a09a7-285">0.3</span></span>  |
    |<span data-ttu-id="a09a7-286">Uzyskiwanie Semafora</span><span class="sxs-lookup"><span data-stu-id="a09a7-286">Get Semaphore</span></span>  |<span data-ttu-id="a09a7-287">0,2</span><span class="sxs-lookup"><span data-stu-id="a09a7-287">0.2</span></span>  |
    |<span data-ttu-id="a09a7-288">Umieść Semafor</span><span class="sxs-lookup"><span data-stu-id="a09a7-288">Put Semaphore</span></span>  |<span data-ttu-id="a09a7-289">0,2</span><span class="sxs-lookup"><span data-stu-id="a09a7-289">0.2</span></span>  |
    |<span data-ttu-id="a09a7-290">Przełącznik kontekstu</span><span class="sxs-lookup"><span data-stu-id="a09a7-290">Context Switch</span></span>  |<span data-ttu-id="a09a7-291">0,4</span><span class="sxs-lookup"><span data-stu-id="a09a7-291">0.4</span></span>  |
    |<span data-ttu-id="a09a7-292">Odpowiedź na przerwanie</span><span class="sxs-lookup"><span data-stu-id="a09a7-292">Interrupt Response</span></span>  |<span data-ttu-id="a09a7-293">0.0 – 0.6</span><span class="sxs-lookup"><span data-stu-id="a09a7-293">0.0 – 0.6</span></span>  |

    <span data-ttu-id="a09a7-294">\**Wartości wydajności oparte na typowym procesorze z częstotliwością 200 MHz.*</span><span class="sxs-lookup"><span data-stu-id="a09a7-294">\**Performance figures based on typical processor running at 200MHz*.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="a09a7-295">Zaawansowana technologia</span><span class="sxs-lookup"><span data-stu-id="a09a7-295">Advanced technology</span></span>

<span data-ttu-id="a09a7-296">Azure RTOS ThreadX to zaawansowana technologia, której najbardziej charakterystyczną funkcją jest planowanie próg wywłaszczania.</span><span class="sxs-lookup"><span data-stu-id="a09a7-296">Azure RTOS ThreadX is advanced technology whose most notable feature is preemption-threshold scheduling.</span></span> <span data-ttu-id="a09a7-297">Ta funkcja jest unikatowa dla Azure RTOS ThreadX i była przedmiotem rozległych badań akademickich.</span><span class="sxs-lookup"><span data-stu-id="a09a7-297">This feature is unique to Azure RTOS ThreadX and has been the subject of extensive academic research.</span></span> <span data-ttu-id="a09a7-298">Zobacz na przykład [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf)(Planowanie zadań przy użyciu progu wywłaszczenia), a ich imieniu jest Yun Wang z Uniwersytetu Wanga i Manas Saksena z Uniwersytetu Pittsburgh.</span><span class="sxs-lookup"><span data-stu-id="a09a7-298">For example, see [Scheduling Fixed-Priority Tasks with Preemption Threshold](https://www.cs.utah.edu/~regehr/reading/open_papers/preempt_thresh.pdf), by Yun Wang, Concordia University, and Manas Saksena, University of Pittsburgh.</span></span>

<span data-ttu-id="a09a7-299">Weź pod uwagę możliwości Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a09a7-299">Consider the capabilities of Azure RTOS ThreadX.</span></span>

* <span data-ttu-id="a09a7-300">Kompletne i kompleksowe obiekty wielozadaniowości</span><span class="sxs-lookup"><span data-stu-id="a09a7-300">Complete and Comprehensive Multitasking Facilities</span></span>
  * <span data-ttu-id="a09a7-301">Wątki, czasomierze aplikacji, kolejki komunikatów, zliczanie semaforów, mutexów, flag zdarzeń, blokowych i bajtowych pul pamięci</span><span class="sxs-lookup"><span data-stu-id="a09a7-301">Threads, application timers, message queues, counting semaphores, mutexes, event flags, block and byte memory pools</span></span>
* <span data-ttu-id="a09a7-302">Priority-Based Planowanie wywłaszcze</span><span class="sxs-lookup"><span data-stu-id="a09a7-302">Priority-Based Preemptive Scheduling</span></span>
* <span data-ttu-id="a09a7-303">Elastyczność priorytetu — do 1024 poziomów priorytetów</span><span class="sxs-lookup"><span data-stu-id="a09a7-303">Priority Flexibility – Up to 1024 Priority Levels</span></span>
* <span data-ttu-id="a09a7-304">Planowanie kooperatywne</span><span class="sxs-lookup"><span data-stu-id="a09a7-304">Cooperative Scheduling</span></span>
* <span data-ttu-id="a09a7-305">Próg wywłaszczania™ — unikatowy dla Azure RTOS ThreadX, pomaga zmniejszyć przełączniki kontekstu i pomóc w zagwarantowaniu możliwości planowania (na badania akademickie)</span><span class="sxs-lookup"><span data-stu-id="a09a7-305">Preemption-Threshold™ – Unique to Azure RTOS ThreadX, helps reduce context switches and help guarantee schedulability (per academic research)</span></span>
* <span data-ttu-id="a09a7-306">Ochrona pamięci za pośrednictwem Azure RTOS ThreadX MODULES</span><span class="sxs-lookup"><span data-stu-id="a09a7-306">Memory Protection via Azure RTOS ThreadX MODULES</span></span>
* <span data-ttu-id="a09a7-307">W pełni deterministyczny</span><span class="sxs-lookup"><span data-stu-id="a09a7-307">Fully Deterministic</span></span>
* <span data-ttu-id="a09a7-308">Śledzenie zdarzeń — przechwytywanie *ostatnich n* zdarzeń systemu/aplikacji</span><span class="sxs-lookup"><span data-stu-id="a09a7-308">Event Trace – Capture last *n* system/application events</span></span>
* <span data-ttu-id="a09a7-309">Łańcuch zdarzeń™ — rejestrowanie funkcji wywołania zwrotnego "notify" specyficznej dla aplikacji dla każdego obiektu komunikacji lub synchronizacji Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a09a7-309">Event Chaining™ – Register an application-specific “notify” callback function for each Azure RTOS ThreadX communication or synchronization object</span></span>
* <span data-ttu-id="a09a7-310">Azure RTOS ThreadX MODULES z opcjonalną ochroną pamięci</span><span class="sxs-lookup"><span data-stu-id="a09a7-310">Azure RTOS ThreadX MODULES with Optional Memory Protection</span></span>
* <span data-ttu-id="a09a7-311">Run-Time metryki wydajności</span><span class="sxs-lookup"><span data-stu-id="a09a7-311">Run-Time Performance Metrics</span></span>
  * <span data-ttu-id="a09a7-312">Liczba wznowień wątków</span><span class="sxs-lookup"><span data-stu-id="a09a7-312">Number of thread resumptions</span></span>
  * <span data-ttu-id="a09a7-313">Liczba wstrzymanych wątków</span><span class="sxs-lookup"><span data-stu-id="a09a7-313">Number of thread suspensions</span></span>
  * <span data-ttu-id="a09a7-314">Liczba wywłaszków wątków na żądanie</span><span class="sxs-lookup"><span data-stu-id="a09a7-314">Number of solicited thread preemptions</span></span>
  * <span data-ttu-id="a09a7-315">Liczba asynchronicznych wywłaszków przerwań wątków</span><span class="sxs-lookup"><span data-stu-id="a09a7-315">Number of asynchronous thread interrupt preemptions</span></span>
  * <span data-ttu-id="a09a7-316">Liczba inversions priorytetów wątków</span><span class="sxs-lookup"><span data-stu-id="a09a7-316">Number of thread priority inversions</span></span>
  * <span data-ttu-id="a09a7-317">Liczba wątków</span><span class="sxs-lookup"><span data-stu-id="a09a7-317">Number of thread relinquishes</span></span>
* <span data-ttu-id="a09a7-318">Execution Profile Kit (EPK)</span><span class="sxs-lookup"><span data-stu-id="a09a7-318">Execution Profile Kit (EPK)</span></span>
* <span data-ttu-id="a09a7-319">Oddzielny stos przerwań</span><span class="sxs-lookup"><span data-stu-id="a09a7-319">Separate Interrupt Stack</span></span>
* <span data-ttu-id="a09a7-320">Run-Time Stack Analysis</span><span class="sxs-lookup"><span data-stu-id="a09a7-320">Run-Time Stack Analysis</span></span>
* <span data-ttu-id="a09a7-321">Zoptymalizowane przetwarzanie przerwań czasomierza</span><span class="sxs-lookup"><span data-stu-id="a09a7-321">Optimized Timer Interrupt Processing</span></span>

## <a name="multicore-support-amp--smp"></a><span data-ttu-id="a09a7-322">Obsługa wielu rdzeni (AMP & SMP)</span><span class="sxs-lookup"><span data-stu-id="a09a7-322">Multicore support (AMP & SMP)</span></span>

<span data-ttu-id="a09a7-323">Standard Azure RTOS ThreadX jest często używany w asymetrycznym przetwarzaniu wieloprocesorowym (AMP), gdzie oddzielna kopia pliku Azure RTOS ThreadX i aplikacja (lub Linux) są wykonywane na każdym rdzeniu i komunikują się ze sobą za pośrednictwem pamięci współdzielonego lub mechanizmu komunikacji między procesorami, takiego jak OpenAMP (Azure RTOS ThreadX obsługuje openAMP).</span><span class="sxs-lookup"><span data-stu-id="a09a7-323">Standard Azure RTOS ThreadX is often used in an Asymmetric Multiprocessing (AMP) fashion, where a separate copy of Azure RTOS ThreadX and the application (or Linux) execute on each core and communicate with each other via shared memory or an inter-processor communication mechanism such as OpenAMP (Azure RTOS ThreadX supports OpenAMP).</span></span> <span data-ttu-id="a09a7-324">Jest to najbardziej typowa konfiguracja wielordzeniowa korzystająca z Azure RTOS ThreadX i może być najbardziej wydajna, jeśli aplikacja jest w stanie efektywnie załadować procesory.</span><span class="sxs-lookup"><span data-stu-id="a09a7-324">This is the most typical multicore configuration using Azure RTOS ThreadX and can be the most efficient if the application is able to effectively load the processors.</span></span>

<span data-ttu-id="a09a7-325">W środowiskach, w których ładowanie procesorów jest wysoce dynamiczne, Azure RTOS Symetric Multiprocessing (SMP) ThreadX jest dostępny dla następujących rodzin procesorów:</span><span class="sxs-lookup"><span data-stu-id="a09a7-325">For environments where loading the processors is highly dynamic, Azure RTOS ThreadX Symetric Multiprocessing (SMP) is available for the following processor families:</span></span>

* <span data-ttu-id="a09a7-326">Arm Cortex-Ax</span><span class="sxs-lookup"><span data-stu-id="a09a7-326">ARM Cortex-Ax</span></span>
* <span data-ttu-id="a09a7-327">Arm Cortex-Rx</span><span class="sxs-lookup"><span data-stu-id="a09a7-327">ARM Cortex-Rx</span></span>
* <span data-ttu-id="a09a7-328">Arm Cortex-A5x 64-bitowy</span><span class="sxs-lookup"><span data-stu-id="a09a7-328">ARM Cortex-A5x 64-bit</span></span>
* <span data-ttu-id="a09a7-329">MIPS 34K, 1004K i interAptiv</span><span class="sxs-lookup"><span data-stu-id="a09a7-329">MIPS 34K, 1004K, and interAptiv</span></span>
* <span data-ttu-id="a09a7-330">PowerPC</span><span class="sxs-lookup"><span data-stu-id="a09a7-330">PowerPC</span></span>
* <span data-ttu-id="a09a7-331">Synopsys ARC HS</span><span class="sxs-lookup"><span data-stu-id="a09a7-331">Synopsys ARC HS</span></span>
* <span data-ttu-id="a09a7-332">x86</span><span class="sxs-lookup"><span data-stu-id="a09a7-332">x86</span></span>

<span data-ttu-id="a09a7-333">Azure RTOS ThreadX SMP przeprowadza dynamiczne równoważenie obciążenia między *n* procesorami i umożliwia wszystkim zasobom Azure RTOS ThreadX (kolejkom, semaforom, flagom zdarzeń, pulom pamięci itp.) dostęp do dowolnego wątku na dowolnym rdzeniu.</span><span class="sxs-lookup"><span data-stu-id="a09a7-333">Azure RTOS ThreadX SMP performs dynamic load balancing across *n* processors and allows all Azure RTOS ThreadX resources (queues, semaphores, event flags, memory pools, etc.) to be accessed by any thread on any core.</span></span> <span data-ttu-id="a09a7-334">Azure RTOS ThreadX SMP umożliwia pełną obsługę interfejsu API Azure RTOS ThreadX na wszystkich rdzeniach i wprowadza następujące nowe interfejsy API dotyczące operacji SMP:</span><span class="sxs-lookup"><span data-stu-id="a09a7-334">Azure RTOS ThreadX SMP enables the complete Azure RTOS ThreadX API on all cores and introduces the following new API’s applicable to SMP operation:</span></span>

* `UINT tx_thread_smp_core_exclude(TX_THREAD *thread_ptr, ULONG exclusion_map);`
* `UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr, ULONG *exclusion_map_ptr);`
* `UINT tx_thread_smp_core_get(void);`
* `UINT tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);`
* `UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr, ULONG *exclusion_map_ptr);`

## <a name="memory-protection-via-azure-rtos-threadx-modules"></a><span data-ttu-id="a09a7-335">Ochrona pamięci za pośrednictwem Azure RTOS ThreadX</span><span class="sxs-lookup"><span data-stu-id="a09a7-335">Memory protection via Azure RTOS ThreadX Modules</span></span>

<span data-ttu-id="a09a7-336">Produkt dodatku o nazwie Azure RTOS ThreadX MODULES umożliwia dołączanie co najmniej jednego wątków aplikacji do "modułu", który może być dynamicznie ładowany i uruchamiany (lub wykonywany w miejscu) w miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="a09a7-336">An add-on product called Azure RTOS ThreadX MODULES enables one or more application threads to be bundled into a “Module” that can be dynamically loaded and run (or executed in place) on the target.</span></span>

<span data-ttu-id="a09a7-337">Moduły umożliwiają uaktualnianie pól, naprawianie usterek i partycjonowanie programów, aby umożliwić dużym aplikacjom zajmowanie tylko pamięci wymaganej przez aktywne wątki.</span><span class="sxs-lookup"><span data-stu-id="a09a7-337">Modules enable field upgrade, bug fixing, and program partitioning to allow large applications to occupy only the memory needed by active threads.</span></span>

<span data-ttu-id="a09a7-338">Moduły mają również całkowicie oddzieloną przestrzeń adresową od Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a09a7-338">Modules also have a completely separate address space from Azure RTOS ThreadX itself.</span></span> <span data-ttu-id="a09a7-339">Dzięki temu Azure RTOS ThreadX może chronić pamięć (za pośrednictwem modułu MPU lub MMU), tak aby przypadkowy dostęp poza modułem nie mógł uszkodzić żadnego innego składnika oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="a09a7-339">This enables Azure RTOS ThreadX to place memory protection (via MPU or MMU) around the Module such that accidental access outside the module will not be able to corrupt any other software component.</span></span>

## <a name="misra-compliant"></a><span data-ttu-id="a09a7-340">Zgodne ze standardem MISRA</span><span class="sxs-lookup"><span data-stu-id="a09a7-340">MISRA compliant</span></span>

<span data-ttu-id="a09a7-341">Azure RTOS ThreadX Azure RTOS kod źródłowy SMP ThreadX jest zgodny ze standardem MISRA-C:2004 i MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="a09a7-341">Azure RTOS ThreadX and Azure RTOS ThreadX SMP souce code is MISRA-C:2004 and MISRA C:2012 compliant.</span></span> <span data-ttu-id="a09a7-342">MISRA C to zestaw wytycznych programistycznych dla systemów o krytycznym znaczeniu korzystających z języka programowania C.</span><span class="sxs-lookup"><span data-stu-id="a09a7-342">MISRA C is a set of programming guidelines for critical systems using the C programming language.</span></span> <span data-ttu-id="a09a7-343">Oryginalne wytyczne MISRA C były przeznaczone głównie dla aplikacji w przemyśle samochodowym; Jednak język MISRA C jest teraz powszechnie uznawany za stosowany do każdej aplikacji o krytycznym znaczeniu dla bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="a09a7-343">The original MISRA C guidelines were primarily targeted toward automotive applications; however, MISRA C is now widely recognized as being applicable to any safety-critical application.</span></span> <span data-ttu-id="a09a7-344">Azure RTOS ThreadX jest zgodny ze wszystkimi wymaganymi i obowiązkowymi regułami MISRA-C:2004 i MISRA C:2012.</span><span class="sxs-lookup"><span data-stu-id="a09a7-344">Azure RTOS ThreadX is compliant with all required and mandatory rules of MISRA-C:2004 and MISRA C:2012.</span></span>

:::image type="content" source="media/overview-threadx/misra-logo-certification.png" alt-text="Certyfikacja Misra":::

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="a09a7-346">Obsługuje najpopularniejsze architektury</span><span class="sxs-lookup"><span data-stu-id="a09a7-346">Supports most popular architectures</span></span>

<span data-ttu-id="a09a7-347">Azure RTOS ThreadX działa na najpopularniejszych mikroprocesorach 32/64-bitowych, które są obecnie w pełni przetestowane i w pełni obsługiwane, w tym na następujących:</span><span class="sxs-lookup"><span data-stu-id="a09a7-347">Azure RTOS ThreadX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

* <span data-ttu-id="a09a7-348">Urządzenia analogiczne: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="a09a7-348">Analog Devices: SHARC, Blackfin, CM4xx</span></span>
* <span data-ttu-id="a09a7-349">Andes Core: RISC-V</span><span class="sxs-lookup"><span data-stu-id="a09a7-349">Andes Core: RISC-V</span></span>
* <span data-ttu-id="a09a7-350">Ambiqmicro: Mikroujmiejki mcu</span><span class="sxs-lookup"><span data-stu-id="a09a7-350">Ambiqmicro: Apollo MCUs</span></span>
* <span data-ttu-id="a09a7-351">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bitowy/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="a09a7-351">ARM: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>
* <span data-ttu-id="a09a7-352">Cadence: Xtensa, Diamond</span><span class="sxs-lookup"><span data-stu-id="a09a7-352">Cadence: Xtensa, Diamond</span></span>
* <span data-ttu-id="a09a7-353">C DOSTĘP: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span><span class="sxs-lookup"><span data-stu-id="a09a7-353">CEVA: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>
* <span data-ttu-id="a09a7-354">Ksess: RISC-V</span><span class="sxs-lookup"><span data-stu-id="a09a7-354">Cypress: RISC-V</span></span>
* <span data-ttu-id="a09a7-355">EnSilica: eSi-RISC</span><span class="sxs-lookup"><span data-stu-id="a09a7-355">EnSilica: eSi-RISC</span></span>
* <span data-ttu-id="a09a7-356">Infineon: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="a09a7-356">Infineon: XMC1000, XMC4000, TriCore</span></span>
* <span data-ttu-id="a09a7-357">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II,Lgne, Arria 10</span><span class="sxs-lookup"><span data-stu-id="a09a7-357">Intel & Intel FPGA: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>
* <span data-ttu-id="a09a7-358">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="a09a7-358">Microchip: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>
* <span data-ttu-id="a09a7-359">Microsemi: RISC-V</span><span class="sxs-lookup"><span data-stu-id="a09a7-359">Microsemi: RISC-V</span></span>
* <span data-ttu-id="a09a7-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="a09a7-360">NXP: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>
* <span data-ttu-id="a09a7-361">Renesas: SH, HS, V850, RX, RZ, Kod</span><span class="sxs-lookup"><span data-stu-id="a09a7-361">Renesas: SH, HS, V850, RX, RZ, Synergy</span></span>
* <span data-ttu-id="a09a7-362">Silicon Labs: EFM32</span><span class="sxs-lookup"><span data-stu-id="a09a7-362">Silicon Labs: EFM32</span></span>
* <span data-ttu-id="a09a7-363">Synopsys: ARC 600, 700, ARC EM, ARC HS</span><span class="sxs-lookup"><span data-stu-id="a09a7-363">Synopsys: ARC 600, 700, ARC EM, ARC HS</span></span>
* <span data-ttu-id="a09a7-364">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="a09a7-364">ST: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>
* <span data-ttu-id="a09a7-365">Tl: C5xxx, C6xxx, Placówris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="a09a7-365">Tl: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>
* <span data-ttu-id="a09a7-366">Przetwarzanie falowe: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span><span class="sxs-lookup"><span data-stu-id="a09a7-366">Wave Computing: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>
* <span data-ttu-id="a09a7-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="a09a7-367">Xilinx: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

## <a name="supports-most-popular-tools"></a><span data-ttu-id="a09a7-368">Obsługuje najpopularniejsze narzędzia</span><span class="sxs-lookup"><span data-stu-id="a09a7-368">Supports most popular tools</span></span>

<span data-ttu-id="a09a7-369">Azure RTOS ThreadX obsługuje najpopularniejsze osadzone narzędzia programskie, w tym embedded workbench™ systemu IAR, który ma również najbardziej kompleksową świadomość jądra Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="a09a7-369">Azure RTOS ThreadX supports most popular embedded development tools, including IAR’s Embedded Workbench™, which also has the most comprehensive Azure RTOS ThreadX kernel awareness available.</span></span> <span data-ttu-id="a09a7-370">Dodatkowa integracja narzędzi obejmuje GNU (GCC), ARM DS-5/uVision®, GreenRow MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore i wszystkie urządzenia analogiczne.</span><span class="sxs-lookup"><span data-stu-id="a09a7-370">Additional tool integration includes GNU (GCC), ARM DS-5/uVision®, Green Hills MULTI®, Wind River Workbench™, Imagination Codescape, Renesas e2studio, Metaware SeeCode™, NXP CodeWarrior, Lauterbach TRACE32®, TI Code-Composer Studio, CrossCore and all analog devices.</span></span>

## <a name="adaptation-layer-for-threadx"></a><span data-ttu-id="a09a7-371">Warstwa adaptacji dla ThreadX</span><span class="sxs-lookup"><span data-stu-id="a09a7-371">Adaptation layer for ThreadX</span></span>

<span data-ttu-id="a09a7-372">System ThreadX usługi Azure RTOS to zaawansowany system operacyjny czasu rzeczywistego zaprojektowany specjalnie pod kątem głęboko osadzonych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a09a7-372">Azure RTOS ThreadX is an advanced real-time operating system (RTOS) designed specifically for deeply embedded applications.</span></span> <span data-ttu-id="a09a7-373">Aby ułatwić migrację aplikacji do systemu Auzre RTOS, ThreadX zapewnia warstwy adaptacji dla różnych starszych interfejsów API RTOS (FreeRTOS, POSIX, OSEK itp.) [](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers)</span><span class="sxs-lookup"><span data-stu-id="a09a7-373">To help ease application migration to Auzre RTOS, ThreadX provides [adaption layers](https://github.com/azure-rtos/threadx/tree/master/utility/rtos_compatibility_layers) for various legacy RTOS APIs (FreeRTOS, POSIX, OSEK, etc.)</span></span>
