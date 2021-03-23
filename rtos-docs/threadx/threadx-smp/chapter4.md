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
# <a name="chapter-4---description-of-azure-rtos-threadx-smp-services"></a><span data-ttu-id="8bb39-103">Rozdział 4 — Opis usług SMP usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="8bb39-103">Chapter 4 - Description of Azure RTOS ThreadX SMP Services</span></span>

<span data-ttu-id="8bb39-104">Ten rozdział zawiera opis wszystkich usług SMP usługi Azure RTO ThreadX w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="8bb39-104">This chapter contains a description of all Azure RTOS ThreadX SMP services in alphabetic order.</span></span> <span data-ttu-id="8bb39-105">Ich nazwy są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="8bb39-106">W sekcji "wartości zwracane" w następujących opisach wartości **pogrubienia** nie mają wpływać na **TX_DISABLE_ERROR_CHECKING** Definiowanie używane do wyłączania sprawdzania błędów interfejsu API; podczas gdy wartości wyświetlane w trybie niepogrubionym są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-106">In the “Return Values” section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="8bb39-107">Ponadto słowo "**Yes**" wymienione w nagłówku "**możliwe** przeprowadzenie" wskazuje, że wywołanie usługi może wznowić wątek o wyższym priorytecie, w rezultacie przeszedł wątek wywołujący.</span><span class="sxs-lookup"><span data-stu-id="8bb39-107">In addition, a “**Yes**” listed under the “**Preemption Possible**” heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

- <span data-ttu-id="8bb39-108">**tx_block_allocate**: *przydzielanie bloku o stałym rozmiarze pamięci*</span><span class="sxs-lookup"><span data-stu-id="8bb39-108">**tx_block_allocate**: *Allocate fixed-size block of memory*</span></span> 
- <span data-ttu-id="8bb39-109">**tx_block_pool_create**: *Utwórz pulę bloków pamięci o stałym rozmiarze*</span><span class="sxs-lookup"><span data-stu-id="8bb39-109">**tx_block_pool_create**: *Create pool of fixed-size memory blocks*</span></span> 
- <span data-ttu-id="8bb39-110">**tx_block_pool_delete**: *Usuwanie puli bloków pamięci*</span><span class="sxs-lookup"><span data-stu-id="8bb39-110">**tx_block_pool_delete**: *Delete memory block pool*</span></span> 
- <span data-ttu-id="8bb39-111">**tx_block_pool_info_get**: *pobieranie informacji o puli blokowej*</span><span class="sxs-lookup"><span data-stu-id="8bb39-111">**tx_block_pool_info_get**: *Retrieve information about block pool*</span></span> 
- <span data-ttu-id="8bb39-112">**tx_block_pool_performance_info_get**: *Uzyskiwanie informacji o wydajności puli bloku*</span><span class="sxs-lookup"><span data-stu-id="8bb39-112">**tx_block_pool_performance_info_get**: *Get block pool performance information*</span></span> 
- <span data-ttu-id="8bb39-113">**tx_block_pool_performance_system_info_get**: *Uzyskaj informacje o wydajności systemu puli blokowej*</span><span class="sxs-lookup"><span data-stu-id="8bb39-113">**tx_block_pool_performance_system_info_get**: *Get block pool system performance information*</span></span> 
- <span data-ttu-id="8bb39-114">**tx_block_pool_prioritize**: *określanie priorytetów listy zawieszania puli bloków*</span><span class="sxs-lookup"><span data-stu-id="8bb39-114">**tx_block_pool_prioritize**: *Prioritize block pool suspension list*</span></span> 
- <span data-ttu-id="8bb39-115">**tx_block_release**: *Zwolnij blok pamięci o stałym rozmiarze*</span><span class="sxs-lookup"><span data-stu-id="8bb39-115">**tx_block_release**: *Release fixed-size block of memory*</span></span>
- <span data-ttu-id="8bb39-116">**tx_byte_allocate**: *Przydziel bajty pamięci*</span><span class="sxs-lookup"><span data-stu-id="8bb39-116">**tx_byte_allocate**: *Allocate bytes of memory*</span></span> 
- <span data-ttu-id="8bb39-117">**tx_byte_pool_create**: *Utwórz pulę pamięci bajtów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-117">**tx_byte_pool_create**: *Create memory pool of bytes*</span></span> 
- <span data-ttu-id="8bb39-118">**tx_byte_pool_delete**: *Usuwanie puli bajtów pamięci*</span><span class="sxs-lookup"><span data-stu-id="8bb39-118">**tx_byte_pool_delete**: *Delete memory byte pool*</span></span> 
- <span data-ttu-id="8bb39-119">**tx_byte_pool_info_get**: *pobieranie informacji o puli bajtów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-119">**tx_byte_pool_info_get**: *Retrieve information about byte pool*</span></span> 
- <span data-ttu-id="8bb39-120">**tx_byte_pool_performance_info_get**: *pobieranie informacji o wydajności puli bajtów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-120">**tx_byte_pool_performance_info_get**: *Get byte pool performance information*</span></span> 
- <span data-ttu-id="8bb39-121">**tx_byte_pool_performance_system_info_get**: *pobieranie informacji o wydajności systemu puli bajtów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-121">**tx_byte_pool_performance_system_info_get**: *Get byte pool system performance information*</span></span> 
- <span data-ttu-id="8bb39-122">**tx_byte_pool_prioritize**: *priorytetyzacja listy zawieszania puli bajtów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-122">**tx_byte_pool_prioritize**: *Prioritize byte pool suspension list*</span></span> 
- <span data-ttu-id="8bb39-123">**tx_byte_release**: *wydawanie bajtów z powrotem do puli pamięci*</span><span class="sxs-lookup"><span data-stu-id="8bb39-123">**tx_byte_release**: *Release bytes back to memory pool*</span></span> 
- <span data-ttu-id="8bb39-124">**tx_event_flags_create**: *Utwórz grupę flag zdarzeń*</span><span class="sxs-lookup"><span data-stu-id="8bb39-124">**tx_event_flags_create**: *Create event flags group*</span></span> 
- <span data-ttu-id="8bb39-125">**tx_event_flags_delete**: *Usuwanie grupy flag zdarzeń*</span><span class="sxs-lookup"><span data-stu-id="8bb39-125">**tx_event_flags_delete**: *Delete event flags group*</span></span> 
- <span data-ttu-id="8bb39-126">**tx_event_flags_get**: *Pobierz flagi zdarzeń z grupy flag zdarzeń*</span><span class="sxs-lookup"><span data-stu-id="8bb39-126">**tx_event_flags_get**: *Get event flags from event flags group*</span></span> 
- <span data-ttu-id="8bb39-127">**tx_event_flags_info_get**: *Pobierz informacje o grupie flag zdarzeń*</span><span class="sxs-lookup"><span data-stu-id="8bb39-127">**tx_event_flags_info_get**: *Retrieve information about event flags group*</span></span> 
- <span data-ttu-id="8bb39-128">**tx_event_flags_performance_info_get**: *Uzyskiwanie informacji o wydajności grupy flag zdarzeń*</span><span class="sxs-lookup"><span data-stu-id="8bb39-128">**tx_event_flags_performance_info_get**: *Get event flags group performance information*</span></span> 
- <span data-ttu-id="8bb39-129">**tx_event_flags_performance_system_info_get**: *pobieranie informacji o systemie wydajności*</span><span class="sxs-lookup"><span data-stu-id="8bb39-129">**tx_event_flags_performance_system_info_get**: *Retrieve performance system information*</span></span> 
- <span data-ttu-id="8bb39-130">**tx_event_flags_set**: *Ustaw flagi zdarzeń w grupie flag zdarzeń*</span><span class="sxs-lookup"><span data-stu-id="8bb39-130">**tx_event_flags_set**: *Set event flags in an event flags group*</span></span> 
- <span data-ttu-id="8bb39-131">**tx_event_flags_set_notify**: *Powiadamiaj aplikację, gdy są ustawione flagi zdarzeń*</span><span class="sxs-lookup"><span data-stu-id="8bb39-131">**tx_event_flags_set_notify**: *Notify application when event flags are set*</span></span>
- <span data-ttu-id="8bb39-132">**tx_interrupt_control**: *włączać i wyłączać przerwania*</span><span class="sxs-lookup"><span data-stu-id="8bb39-132">**tx_interrupt_control**: *Enable and disable interrupts*</span></span> 
- <span data-ttu-id="8bb39-133">**tx_mutex_create**: *Utwórz element mutex wzajemnego wykluczania*</span><span class="sxs-lookup"><span data-stu-id="8bb39-133">**tx_mutex_create**: *Create mutual exclusion mutex*</span></span> 
- <span data-ttu-id="8bb39-134">**tx_mutex_delete**: *usuwanie obiektu mutex wzajemnego wykluczania*</span><span class="sxs-lookup"><span data-stu-id="8bb39-134">**tx_mutex_delete**: *Delete mutual exclusion mutex*</span></span> 
- <span data-ttu-id="8bb39-135">**tx_mutex_get**: *Uzyskaj własność obiektu mutex*</span><span class="sxs-lookup"><span data-stu-id="8bb39-135">**tx_mutex_get**: *Obtain ownership of mutex*</span></span> 
- <span data-ttu-id="8bb39-136">**tx_mutex_info_get**: *Pobierz informacje o muteksie*</span><span class="sxs-lookup"><span data-stu-id="8bb39-136">**tx_mutex_info_get**: *Retrieve information about mutex*</span></span> 
- <span data-ttu-id="8bb39-137">**tx_mutex_performance_info_get**: *pobieranie informacji o wydajności muteksu*</span><span class="sxs-lookup"><span data-stu-id="8bb39-137">**tx_mutex_performance_info_get**: *Get mutex performance information*</span></span> 
- <span data-ttu-id="8bb39-138">**tx_mutex_performance_system_info_get**: *pobieranie informacji o wydajności systemu muteksu*</span><span class="sxs-lookup"><span data-stu-id="8bb39-138">**tx_mutex_performance_system_info_get**: *Get mutex system performance information*</span></span> 
- <span data-ttu-id="8bb39-139">**tx_mutex_prioritize**: *określanie priorytetów listy zawieszeń muteksu*</span><span class="sxs-lookup"><span data-stu-id="8bb39-139">**tx_mutex_prioritize**: *Prioritize mutex suspension list*</span></span> 
- <span data-ttu-id="8bb39-140">**tx_mutex_put**: *Zwolnij własność elementu mutex*</span><span class="sxs-lookup"><span data-stu-id="8bb39-140">**tx_mutex_put**: *Release ownership of mutex*</span></span> 
- <span data-ttu-id="8bb39-141">**tx_queue_create**: *Tworzenie kolejki komunikatów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-141">**tx_queue_create**: *Create message queue*</span></span> 
- <span data-ttu-id="8bb39-142">**tx_queue_delete**: *usuwanie kolejki komunikatów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-142">**tx_queue_delete**: *Delete message queue*</span></span> 
- <span data-ttu-id="8bb39-143">**tx_queue_flush**: *puste wiadomości w kolejce komunikatów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-143">**tx_queue_flush**: *Empty messages in message queue*</span></span> 
- <span data-ttu-id="8bb39-144">**tx_queue_front_send**: *Wyślij komunikat z przodu kolejki*</span><span class="sxs-lookup"><span data-stu-id="8bb39-144">**tx_queue_front_send**: *Send message to the front of queue*</span></span> 
- <span data-ttu-id="8bb39-145">**tx_queue_info_get**: *pobieranie informacji o kolejce*</span><span class="sxs-lookup"><span data-stu-id="8bb39-145">**tx_queue_info_get**: *Retrieve information about queue*</span></span> 
- <span data-ttu-id="8bb39-146">**tx_queue_performance_info_get**: *Uzyskiwanie informacji o wydajności kolejki*</span><span class="sxs-lookup"><span data-stu-id="8bb39-146">**tx_queue_performance_info_get**: *Get queue performance information*</span></span> 
- <span data-ttu-id="8bb39-147">**tx_queue_performance_system_info_get**: *pobieranie informacji o wydajności systemu kolejkowania*</span><span class="sxs-lookup"><span data-stu-id="8bb39-147">**tx_queue_performance_system_info_get**: *Get queue system performance information*</span></span>
- <span data-ttu-id="8bb39-148">**tx_queue_prioritize**: *priorytetyzacja listy zawieszania kolejki*</span><span class="sxs-lookup"><span data-stu-id="8bb39-148">**tx_queue_prioritize**: *Prioritize queue suspension list*</span></span> 
- <span data-ttu-id="8bb39-149">**tx_queue_receive**: *Pobierz komunikat z kolejki komunikatów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-149">**tx_queue_receive**: *Get message from message queue*</span></span> 
- <span data-ttu-id="8bb39-150">**tx_queue_send**: *Wyślij komunikat do kolejki komunikatów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-150">**tx_queue_send**: *Send message to message queue*</span></span> 
- <span data-ttu-id="8bb39-151">**tx_queue_send_notify**: *Powiadamiaj aplikację, gdy wiadomość jest wysyłana do kolejki*</span><span class="sxs-lookup"><span data-stu-id="8bb39-151">**tx_queue_send_notify**: *Notify application when message is sent to queue*</span></span> 
- <span data-ttu-id="8bb39-152">**tx_semaphore_ceiling_put**: *Umieść wystąpienie w zliczaniu semafora z pułapem*</span><span class="sxs-lookup"><span data-stu-id="8bb39-152">**tx_semaphore_ceiling_put**: *Place an instance in counting semaphore with ceiling*</span></span> 
- <span data-ttu-id="8bb39-153">**tx_semaphore_create**: *Tworzenie semafora zliczania*</span><span class="sxs-lookup"><span data-stu-id="8bb39-153">**tx_semaphore_create**: *Create counting semaphore*</span></span> 
- <span data-ttu-id="8bb39-154">**tx_semaphore_delete**: *usuwanie semafora zliczania*</span><span class="sxs-lookup"><span data-stu-id="8bb39-154">**tx_semaphore_delete**: *Delete counting semaphore*</span></span> 
- <span data-ttu-id="8bb39-155">**tx_semaphore_get**: *Pobieranie wystąpienia z zliczania semafora*</span><span class="sxs-lookup"><span data-stu-id="8bb39-155">**tx_semaphore_get**: *Get instance from counting semaphore*</span></span> 
- <span data-ttu-id="8bb39-156">**tx_semaphore_info_get**: *pobieranie informacji na temat semafora*</span><span class="sxs-lookup"><span data-stu-id="8bb39-156">**tx_semaphore_info_get**: *Retrieve information about semaphore*</span></span> 
- <span data-ttu-id="8bb39-157">**tx_semaphore_performance_info_get**: *Uzyskiwanie informacji o wydajności semaforów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-157">**tx_semaphore_performance_info_get**: *Get semaphore performance information*</span></span> 
- <span data-ttu-id="8bb39-158">**tx_semaphore_performance_system_info_get**: *Uzyskiwanie informacji o wydajności systemu semaforów*</span><span class="sxs-lookup"><span data-stu-id="8bb39-158">**tx_semaphore_performance_system_info_get**: *Get semaphore system performance information*</span></span> 
- <span data-ttu-id="8bb39-159">**tx_semaphore_prioritize**: *określanie priorytetów listy zawieszania semafora*</span><span class="sxs-lookup"><span data-stu-id="8bb39-159">**tx_semaphore_prioritize**: *Prioritize semaphore suspension list*</span></span> 
- <span data-ttu-id="8bb39-160">**tx_semaphore_put**: *Umieść wystąpienie w zliczaniu semafora*</span><span class="sxs-lookup"><span data-stu-id="8bb39-160">**tx_semaphore_put**: *Place an instance in counting semaphore*</span></span> 
- <span data-ttu-id="8bb39-161">**tx_semaphore_put_notify**: *Powiadamiaj aplikację, gdy zostanie umieszczony semafor*</span><span class="sxs-lookup"><span data-stu-id="8bb39-161">**tx_semaphore_put_notify**: *Notify application when semaphore is put*</span></span> 
- <span data-ttu-id="8bb39-162">**tx_thread_create**: *Utwórz wątek aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-162">**tx_thread_create**: *Create application thread*</span></span> 
- <span data-ttu-id="8bb39-163">**tx_thread_delete**: *usuwanie wątku aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-163">**tx_thread_delete**: *Delete application thread*</span></span>
- <span data-ttu-id="8bb39-164">**tx_thread_entry_exit_notify**: *Powiadamiaj aplikację przy wejściu i wyjściu wątku*</span><span class="sxs-lookup"><span data-stu-id="8bb39-164">**tx_thread_entry_exit_notify**: *Notify application upon thread entry and exit*</span></span> 
- <span data-ttu-id="8bb39-165">**tx_thread_identify**: *Pobiera wskaźnik do aktualnie wykonywanego wątku*</span><span class="sxs-lookup"><span data-stu-id="8bb39-165">**tx_thread_identify**: *Retrieves pointer to currently executing thread*</span></span> 
- <span data-ttu-id="8bb39-166">**tx_thread_info_get**: *pobieranie informacji o wątku*</span><span class="sxs-lookup"><span data-stu-id="8bb39-166">**tx_thread_info_get**: *Retrieve information about thread*</span></span> 
- <span data-ttu-id="8bb39-167">**tx_thread_performance_info_get**: *Uzyskiwanie informacji o wydajności wątków*</span><span class="sxs-lookup"><span data-stu-id="8bb39-167">**tx_thread_performance_info_get**: *Get thread performance information*</span></span> 
- <span data-ttu-id="8bb39-168">**tx_thread_performance_system_info_get**: *pobieranie informacji o wydajności systemu wątków*</span><span class="sxs-lookup"><span data-stu-id="8bb39-168">**tx_thread_performance_system_info_get**: *Get thread system performance information*</span></span> 
- <span data-ttu-id="8bb39-169">**tx_thread_preemption_change**: zmiana przekroczenia *— próg wątku aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-169">**tx_thread_preemption_change**: *Change preemption-threshold of application thread*</span></span> 
- <span data-ttu-id="8bb39-170">**tx_thread_priority_change**: *Zmień priorytet wątku aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-170">**tx_thread_priority_change**: *Change priority of application thread*</span></span> 
- <span data-ttu-id="8bb39-171">**tx_thread_relinquish**: *zwalnianie kontroli do innych wątków aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-171">**tx_thread_relinquish**: *Relinquish control to other application threads*</span></span> 
- <span data-ttu-id="8bb39-172">**tx_thread_reset**: *Resetowanie wątku*</span><span class="sxs-lookup"><span data-stu-id="8bb39-172">**tx_thread_reset**: *Reset thread*</span></span> 
- <span data-ttu-id="8bb39-173">**tx_thread_resume**: *Wznów wątek zawieszonej aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-173">**tx_thread_resume**: *Resume suspended application thread*</span></span> 
- <span data-ttu-id="8bb39-174">**tx_thread_sleep**: *Zawieś bieżący wątek dla określonego czasu*</span><span class="sxs-lookup"><span data-stu-id="8bb39-174">**tx_thread_sleep**: *Suspend current thread for specified time*</span></span> 
- <span data-ttu-id="8bb39-175">**tx_thread_smp_core_exclude**: *wykluczanie wykonywania wątku na zestawie rdzeni*</span><span class="sxs-lookup"><span data-stu-id="8bb39-175">**tx_thread_smp_core_exclude**: *Exclude thread execution on a set of cores*</span></span> 
- <span data-ttu-id="8bb39-176">**tx_thread_smp_core_exclude_get**: *Pobiera bieżące wykluczenie rdzenia wątku*</span><span class="sxs-lookup"><span data-stu-id="8bb39-176">**tx_thread_smp_core_exclude_get**: *Gets the thread's current core exclusion*</span></span> 
- <span data-ttu-id="8bb39-177">**tx_thread_smp_core_get**: *Pobierz aktualnie wykonywany rdzeń elementu wywołującego*</span><span class="sxs-lookup"><span data-stu-id="8bb39-177">**tx_thread_smp_core_get**: *Retrieve currently executing core of caller*</span></span> 
- <span data-ttu-id="8bb39-178">**tx_thread_stack_error_notify**: *Rejestrowanie wywołania zwrotnego powiadomień o błędzie stosu wątku*</span><span class="sxs-lookup"><span data-stu-id="8bb39-178">**tx_thread_stack_error_notify**: *Register thread stack error notification callback*</span></span> 
- <span data-ttu-id="8bb39-179">**tx_thread_suspend**: *wstrzymywanie wątku aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-179">**tx_thread_suspend**: *Suspend application thread*</span></span>
- <span data-ttu-id="8bb39-180">**tx_thread_terminate**: *przerywa wątek aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-180">**tx_thread_terminate**: *Terminates application thread*</span></span> 
- <span data-ttu-id="8bb39-181">**tx_thread_time_slice_change**: *zmienia czas wycinka wątku aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-181">**tx_thread_time_slice_change**: *Changes time-slice of application thread*</span></span> 
- <span data-ttu-id="8bb39-182">**tx_thread_wait_abort**: *Przerwij zawieszenie określonego wątku*</span><span class="sxs-lookup"><span data-stu-id="8bb39-182">**tx_thread_wait_abort**: *Abort suspension of specified thread*</span></span> 
- <span data-ttu-id="8bb39-183">**tx_time_get**: *Pobiera bieżący czas*</span><span class="sxs-lookup"><span data-stu-id="8bb39-183">**tx_time_get**: *Retrieves the current time*</span></span> 
- <span data-ttu-id="8bb39-184">**tx_time_set**: *ustawia bieżącą godzinę*</span><span class="sxs-lookup"><span data-stu-id="8bb39-184">**tx_time_set**: *Sets the current time*</span></span> 
- <span data-ttu-id="8bb39-185">**tx_timer_activate**: *Aktywuj czasomierz aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-185">**tx_timer_activate**: *Activate application timer*</span></span> 
- <span data-ttu-id="8bb39-186">**tx_timer_change**: *Zmień czasomierz aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-186">**tx_timer_change**: *Change application timer*</span></span> 
- <span data-ttu-id="8bb39-187">**tx_timer_create**: *Utwórz czasomierz aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-187">**tx_timer_create**: *Create application timer*</span></span> 
- <span data-ttu-id="8bb39-188">**tx_timer_deactivate**: *Dezaktywuj czasomierz aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-188">**tx_timer_deactivate**: *Deactivate application timer*</span></span> 
- <span data-ttu-id="8bb39-189">**tx_timer_delete**: *usuwanie czasomierza aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-189">**tx_timer_delete**: *Delete application timer*</span></span> 
- <span data-ttu-id="8bb39-190">**tx_timer_info_get**: *pobieranie informacji o czasomierzu aplikacji*</span><span class="sxs-lookup"><span data-stu-id="8bb39-190">**tx_timer_info_get**: *Retrieve information about an application timer*</span></span> 
- <span data-ttu-id="8bb39-191">**tx_timer_performance_info_get**: *Uzyskiwanie informacji o wydajności czasomierza*</span><span class="sxs-lookup"><span data-stu-id="8bb39-191">**tx_timer_performance_info_get**: *Get timer performance information*</span></span> 
- <span data-ttu-id="8bb39-192">**tx_timer_performance_system_info_get**: *Uzyskiwanie informacji o wydajności systemu czasomierza*</span><span class="sxs-lookup"><span data-stu-id="8bb39-192">**tx_timer_performance_system_info_get**: *Get timer system performance information*</span></span> 
- <span data-ttu-id="8bb39-193">**tx_timer_smp_core_exclude**: *wykluczanie wykonywania czasomierza na zestawie rdzeni*</span><span class="sxs-lookup"><span data-stu-id="8bb39-193">**tx_timer_smp_core_exclude**: *Exclude timer execution on a set of cores*</span></span> 
- <span data-ttu-id="8bb39-194">**tx_timer_smp_core_exclude_get**: *Pobiera bieżące wykluczenie rdzenia czasomierza*</span><span class="sxs-lookup"><span data-stu-id="8bb39-194">**tx_timer_smp_core_exclude_get**: *Gets the timer's current core exclusion*</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="8bb39-195">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-195">tx_block_allocate</span></span>
<span data-ttu-id="8bb39-196">Przydzielanie bloku o ustalonym rozmiarze pamięci</span><span class="sxs-lookup"><span data-stu-id="8bb39-196">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-197">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-197">Prototype</span></span>

```C
UINT tx_block_allocate(TX_BLOCK_POOL *pool_ptr, VOID **block_ptr,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="8bb39-198">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-198">Description</span></span>

<span data-ttu-id="8bb39-199">Ta usługa przydziela blok pamięci o stałym rozmiarze z określonej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-199">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="8bb39-200">Rzeczywisty rozmiar bloku pamięci jest określany podczas tworzenia puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-200">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!WARNING]
> <span data-ttu-id="8bb39-201">Ważne jest, aby upewnić się, że kod aplikacji nie zapisuje poza przydzielonym blokiem pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-201">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="8bb39-202">W takim przypadku uszkodzenie występuje w sąsiednim (zazwyczaj kolejnym) bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-202">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="8bb39-203">Wyniki są nieprzewidywalne i często są krytyczne!</span><span class="sxs-lookup"><span data-stu-id="8bb39-203">The results are unpredictable and are often fatal!</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-204">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-204">Parameters</span></span>

- <span data-ttu-id="8bb39-205">**pool_ptr**: wskaźnik do wcześniej utworzonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-205">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="8bb39-206">**block_ptr**: wskaźnik do docelowego wskaźnika bloku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-206">**block_ptr**: Pointer to a destination block pointer.</span></span> <span data-ttu-id="8bb39-207">Po pomyślnym przydzieleniu adres przydzielonego bloku pamięci jest umieszczany w miejscu, w którym wskazuje ten parametr.</span><span class="sxs-lookup"><span data-stu-id="8bb39-207">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="8bb39-208">**WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli nie ma dostępnych bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-208">**wait_option**: Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="8bb39-209">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8bb39-209">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8bb39-210">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8bb39-210">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="8bb39-211">**TX_WAIT_FOREVER**: (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="8bb39-211">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="8bb39-212">wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8bb39-212">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>  
    
    <span data-ttu-id="8bb39-213">Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się pomyślnie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-213">Selecting TX_NO_WAIT results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="8bb39-214">Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-214">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="8bb39-215">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu udostępnienia bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-215">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a memory block is available.</span></span>

    <span data-ttu-id="8bb39-216">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na blok pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-216">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-217">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-217">Return Values</span></span>

- <span data-ttu-id="8bb39-218">**TX_SUCCESS**: (0x00) pomyślna alokacja bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-218">**TX_SUCCESS**: (0x00) Successful memory block allocation.</span></span>
- <span data-ttu-id="8bb39-219">**TX_DELETED**: (0x01) Pula bloków pamięci została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-219">**TX_DELETED**: (0x01) Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8bb39-220">**TX_NO_MEMORY**: usługa (0x10) nie może przydzielić bloku pamięci w określonym czasie, aby oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-220">**TX_NO_MEMORY**: (0x10) Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="8bb39-221">Zawieszanie **TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, CZASOMIERZ lub ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-221">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="8bb39-222">TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-222">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="8bb39-223">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do wskaźnika docelowego.</span><span class="sxs-lookup"><span data-stu-id="8bb39-223">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="8bb39-224">TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-224">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-225">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-225">Allowed From</span></span>

<span data-ttu-id="8bb39-226">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-226">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-227">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-227">Preemption Possible</span></span>

<span data-ttu-id="8bb39-228">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-228">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-229">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-229">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8bb39-230">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-230">See Also</span></span>

- <span data-ttu-id="8bb39-231">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-231">tx_block_pool_create</span></span>
- <span data-ttu-id="8bb39-232">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-232">tx_block_pool_delete</span></span>
- <span data-ttu-id="8bb39-233">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-233">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8bb39-234">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-234">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-235">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-235">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-236">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-236">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-237">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-237">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="8bb39-238">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-238">tx_block_pool_create</span></span>
<span data-ttu-id="8bb39-239">Utwórz pulę bloków pamięci o stałym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="8bb39-239">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-240">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-240">Prototype</span></span>

```C
UINT tx_block_pool_create(TX_BLOCK_POOL *pool_ptr,
                          CHAR *name_ptr, ULONG block_size,
                          VOID *pool_start, ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="8bb39-241">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-241">Description</span></span>

<span data-ttu-id="8bb39-242">Ta usługa tworzy pulę bloków pamięci o stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="8bb39-242">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="8bb39-243">Określony obszar pamięci jest podzielony na tyle bloków pamięci o stałym rozmiarze, jak to możliwe, przy użyciu formuły:</span><span class="sxs-lookup"><span data-stu-id="8bb39-243">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>    
<span data-ttu-id="8bb39-244">**łączna liczba bloków** = (**całkowita liczba bajtów**)/(**rozmiar bloku** + sizeof (void \*))</span><span class="sxs-lookup"><span data-stu-id="8bb39-244">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-245">Każdy blok pamięci zawiera jeden wskaźnik obciążenia, który jest niewidoczny dla użytkownika i jest reprezentowany przez "sizeof (void \*)" w poprzedniej formule.</span><span class="sxs-lookup"><span data-stu-id="8bb39-245">Each memory block contains one pointer of overhead that is invisible to the user and is represented by the “sizeof(void \*)” in the preceding formula.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-246">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-246">Parameters</span></span>

- <span data-ttu-id="8bb39-247">**pool_ptr**: wskaźnik do bloku sterującego puli blok pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-247">**pool_ptr**: Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="8bb39-248">**name_ptr**: wskaźnik do nazwy puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-248">**name_ptr**: Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="8bb39-249">**block_size**: liczba bajtów w każdym bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-249">**block_size**: Number of bytes in each memory block.</span></span>
- <span data-ttu-id="8bb39-250">**pool_start**: adres początkowy puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-250">**pool_start**: Starting address of the memory block pool.</span></span> <span data-ttu-id="8bb39-251">Adres początkowy musi być wyrównany do rozmiaru typu danych ULONG.</span><span class="sxs-lookup"><span data-stu-id="8bb39-251">The starting address must be aligned to the size of the ULONG data type..</span></span>
- <span data-ttu-id="8bb39-252">**pool_size**: całkowita liczba bajtów dostępnych dla puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-252">**pool_size**: Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-253">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-253">Return Values</span></span>

- <span data-ttu-id="8bb39-254">**TX_SUCCESS**: (0X00) pomyślnie utworzono pulę bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-254">**TX_SUCCESS**: (0x00) Successful memory block pool creation.</span></span>
- <span data-ttu-id="8bb39-255">TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-255">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span> <span data-ttu-id="8bb39-256">Wskaźnik ma wartość NULL lub pula została już utworzona.</span><span class="sxs-lookup"><span data-stu-id="8bb39-256">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="8bb39-257">TX_PTR_ERROR: (0x03) nieprawidłowy adres początkowy puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-257">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="8bb39-258">TX_SIZE_ERROR: (0x05) rozmiar puli jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-258">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="8bb39-259">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-259">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-260">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-260">Allowed From</span></span>

<span data-ttu-id="8bb39-261">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-261">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-262">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-262">Preemption Possible</span></span>

<span data-ttu-id="8bb39-263">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-263">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-264">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-264">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-265">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-265">See Also</span></span>

- <span data-ttu-id="8bb39-266">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-266">tx_block_allocate</span></span>
- <span data-ttu-id="8bb39-267">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-267">tx_block_pool_delete</span></span>
- <span data-ttu-id="8bb39-268">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-268">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8bb39-269">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-269">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-270">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-270">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-271">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-271">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-272">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-272">tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="8bb39-273">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-273">tx_block_pool_delete</span></span>

<span data-ttu-id="8bb39-274">Usuń pulę bloków pamięci</span><span class="sxs-lookup"><span data-stu-id="8bb39-274">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-275">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-275">Prototype</span></span>

```C
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-276">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-276">Description</span></span>

<span data-ttu-id="8bb39-277">Ta usługa usuwa określoną pulę bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-277">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="8bb39-278">Wszystkie wątki zawieszają się, czekając na wznowienie bloku pamięci z tej puli i z uwzględnieniem TX_DELETED stanu powrotu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-278">All threads suspended waiting for a memory block from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-279">Jest on odpowiedzialny za zarządzanie obszarem pamięci skojarzonym z pulą, która jest dostępna po zakończeniu tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-279">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="8bb39-280">Ponadto aplikacja musi uniemożliwić korzystanie z usuniętej puli lub jej poprzednich bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-280">In addition, the application must prevent use of a deleted pool or its former memory blocks.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-281">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-281">Parameters</span></span>

- <span data-ttu-id="8bb39-282">**pool_ptr**: wskaźnik do wcześniej utworzonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-282">**pool_ptr**: Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-283">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-283">Return Values</span></span>

- <span data-ttu-id="8bb39-284">**TX_SUCCESS**: (0X00) pomyślnie usunięto pulę bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-284">**TX_SUCCESS**: (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="8bb39-285">TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-285">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="8bb39-286">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-286">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-287">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-287">Allowed From</span></span>

<span data-ttu-id="8bb39-288">Wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-288">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-289">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-289">Preemption Possible</span></span>

<span data-ttu-id="8bb39-290">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-290">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-291">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-291">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-292">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-292">See Also</span></span>

- <span data-ttu-id="8bb39-293">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-293">tx_block_allocate</span></span>
- <span data-ttu-id="8bb39-294">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-294">tx_block_pool_create</span></span>
- <span data-ttu-id="8bb39-295">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-295">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8bb39-296">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-296">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-297">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-297">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-298">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-298">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-299">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-299">tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="8bb39-300">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-300">tx_block_pool_info_get</span></span>

<span data-ttu-id="8bb39-301">Pobierz informacje o puli blokowej</span><span class="sxs-lookup"><span data-stu-id="8bb39-301">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-302">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-302">Prototype</span></span>

```C
UINT tx_block_pool_info_get(TX_BLOCK_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *total_blocks,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BLOCK_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="8bb39-303">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-303">Description</span></span>

<span data-ttu-id="8bb39-304">Ta usługa pobiera informacje o określonej puli pamięci blokowej.</span><span class="sxs-lookup"><span data-stu-id="8bb39-304">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-305">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-305">Parameters</span></span>

- <span data-ttu-id="8bb39-306">**pool_ptr**: wskaźnik do wcześniej utworzonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-306">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="8bb39-307">**name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="8bb39-307">**name**: Pointer to destination for the pointer to the block pool’s name.</span></span>
- <span data-ttu-id="8bb39-308">**dostępne**: wskaźnik do miejsca docelowego dla liczby dostępnych bloków w puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="8bb39-308">**available**: Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="8bb39-309">**total_blocks**: wskaźnik do miejsca docelowego dla łącznej liczby bloków w puli bloków.</span><span class="sxs-lookup"><span data-stu-id="8bb39-309">**total_blocks**: Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="8bb39-310">**first_suspended**: wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tej puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="8bb39-310">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="8bb39-311">**suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="8bb39-311">**suspended_count**: Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="8bb39-312">**next_pool**: wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="8bb39-312">**next_pool**: Pointer to destination for the pointer of the next created block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-313">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-313">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-314">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-314">Return Values</span></span>

- <span data-ttu-id="8bb39-315">**TX_SUCCESS**: (0X00) pomyślne pobranie informacji o puli blokowych.</span><span class="sxs-lookup"><span data-stu-id="8bb39-315">**TX_SUCCESS**: (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="8bb39-316">TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-316">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-317">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-317">Allowed From</span></span>

<span data-ttu-id="8bb39-318">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-318">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-319">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-319">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-320">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-320">See Also</span></span>

- <span data-ttu-id="8bb39-321">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-321">tx_block_allocate</span></span>
- <span data-ttu-id="8bb39-322">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-322">tx_block_pool_create</span></span>
- <span data-ttu-id="8bb39-323">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-323">tx_block_pool_delete</span></span>
- <span data-ttu-id="8bb39-324">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-324">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8bb39-325">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-325">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-326">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-326">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-327">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-327">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-328">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-328">tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="8bb39-329">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-329">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="8bb39-330">Uzyskaj informacje o wydajności puli bloku</span><span class="sxs-lookup"><span data-stu-id="8bb39-330">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-331">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-331">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(TX_BLOCK_POOL *pool_ptr,
       ULONG *allocates, ULONG *releases,
       ULONG *suspensions, ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="8bb39-332">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-332">Description</span></span>

<span data-ttu-id="8bb39-333">Ta usługa pobiera informacje o wydajności dotyczące określonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-333">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-334">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-334">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-335">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-335">Parameters</span></span>

- <span data-ttu-id="8bb39-336">**pool_ptr**: wskaźnik do wcześniej utworzonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-336">**pool_ptr**: Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="8bb39-337">**przypisuje**: wskaźnik do miejsca docelowego dla liczby żądań przydzielenia wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-337">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="8bb39-338">**wersje**: wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-338">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="8bb39-339">**zawieszenia**: wskaźnik do miejsca docelowego dla liczby zawieszeń alokacji wątku w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-339">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="8bb39-340">**limity czasu**: wskaźnik do miejsca docelowego dla liczby limitów przydziału zawieszeń w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-340">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-341">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-341">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-342">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-342">Return Values</span></span>

- <span data-ttu-id="8bb39-343">**TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności puli blokowych.</span><span class="sxs-lookup"><span data-stu-id="8bb39-343">**TX_SUCCESS**: (0x00) Successful block pool performance get.</span></span>
- <span data-ttu-id="8bb39-344">**TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik puli bloku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-344">**TX_PTR_ERROR**: (0x03) Invalid block pool pointer.</span></span>
- <span data-ttu-id="8bb39-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-345">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-346">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-346">Allowed From</span></span>

<span data-ttu-id="8bb39-347">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-347">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-348">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-348">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-349">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-349">See Also</span></span>

- <span data-ttu-id="8bb39-350">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-350">tx_block_allocate</span></span>
- <span data-ttu-id="8bb39-351">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-351">tx_block_pool_create</span></span>
- <span data-ttu-id="8bb39-352">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-352">tx_block_pool_delete</span></span>
- <span data-ttu-id="8bb39-353">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-353">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8bb39-354">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-354">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-355">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-355">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-356">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-356">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="8bb39-357">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-357">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="8bb39-358">Uzyskaj informacje o wydajności systemu puli blokowej</span><span class="sxs-lookup"><span data-stu-id="8bb39-358">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-359">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-359">Prototype</span></span>

```C
UINT tx_block_pool_performance_system_info_get(ULONG *allocates,
       ULONG *releases, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="8bb39-360">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-360">Description</span></span>

<span data-ttu-id="8bb39-361">Ta usługa pobiera informacje o wydajności wszystkich pul bloków pamięci w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-361">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-362">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-362">The ThreadX SMP library and application must be built with **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-363">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-363">Parameters</span></span>

- <span data-ttu-id="8bb39-364">**przypisuje**: wskaźnik do miejsca docelowego dla łącznej liczby żądań alokacji wykonanych dla wszystkich pul bloku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-364">**allocates**: Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="8bb39-365">**wersje**: wskaźnik do miejsca docelowego dla łącznej liczby żądań zwolnienia wykonanych na wszystkich pulach bloku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-365">**releases**: Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="8bb39-366">**zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń alokacji wątku dla wszystkich pul bloku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-366">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="8bb39-367">**limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia przydziału dla wszystkich pul bloku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-367">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-368">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-368">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-369">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-369">Return Values</span></span>

- <span data-ttu-id="8bb39-370">**TX_SUCCESS**: (0X00) pomyślne zablokowanie wydajności systemu puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-370">**TX_SUCCESS**: (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="8bb39-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-371">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-372">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-372">Allowed From</span></span>

<span data-ttu-id="8bb39-373">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-373">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-374">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-374">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-375">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-375">See Also</span></span>

- <span data-ttu-id="8bb39-376">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-376">tx_block_allocate</span></span>
- <span data-ttu-id="8bb39-377">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-377">tx_block_pool_create</span></span>
- <span data-ttu-id="8bb39-378">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-378">tx_block_pool_delete</span></span>
- <span data-ttu-id="8bb39-379">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-379">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8bb39-380">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-380">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-381">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-381">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-382">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-382">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="8bb39-383">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-383">tx_block_pool_prioritize</span></span>

<span data-ttu-id="8bb39-384">Ustawianie priorytetu listy zawieszania puli bloków</span><span class="sxs-lookup"><span data-stu-id="8bb39-384">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-385">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-385">Prototype</span></span>

```C
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-386">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-386">Description</span></span>

<span data-ttu-id="8bb39-387">Ta usługa umieszcza wątek o najwyższym priorytecie dla bloku pamięci w tej puli na początku listy zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-387">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="8bb39-388">Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-388">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-389">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-389">Parameters</span></span> 

- <span data-ttu-id="8bb39-390">**pool_ptr**: wskaźnik do bloku sterującego puli blok pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-390">**pool_ptr**: Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-391">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-391">Return Values</span></span>

- <span data-ttu-id="8bb39-392">**TX_SUCCESS**: (0x00) pomyślna priorytetyzacja puli zablokowanych.</span><span class="sxs-lookup"><span data-stu-id="8bb39-392">**TX_SUCCESS**: (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="8bb39-393">TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-393">TX_POOL_ERROR: (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-394">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-394">Allowed From</span></span>

<span data-ttu-id="8bb39-395">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-395">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-396">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-396">Preemption Possible</span></span>

<span data-ttu-id="8bb39-397">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-397">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-398">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-398">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-399">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-399">See Also</span></span>

- <span data-ttu-id="8bb39-400">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-400">tx_block_allocate</span></span>
- <span data-ttu-id="8bb39-401">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-401">tx_block_pool_create</span></span>
- <span data-ttu-id="8bb39-402">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-402">tx_block_pool_delete</span></span>
- <span data-ttu-id="8bb39-403">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-403">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8bb39-404">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-404">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-405">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-405">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-406">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-406">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="8bb39-407">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-407">tx_block_release</span></span>

<span data-ttu-id="8bb39-408">Zwolnij blok pamięci o stałym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="8bb39-408">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-409">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-409">Prototype</span></span>

```C
UINT tx_block_release(VOID *block_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-410">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-410">Description</span></span>

<span data-ttu-id="8bb39-411">Ta usługa zwalnia wcześniej przydzieloną blokadę z powrotem do skojarzonej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-411">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="8bb39-412">Jeśli istnieje co najmniej jeden wątek, który zawiesił oczekiwanie na bloki pamięci z tej puli, ten blok pamięci zostanie zawieszony i wznowiony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-412">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-413">Aplikacja musi uniemożliwić korzystanie z obszaru blokowego pamięci po jego wydaniu z powrotem do puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-413">The application must prevent using a memory block area after it has been released back to the pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-414">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-414">Parameters</span></span>

- <span data-ttu-id="8bb39-415">**block_ptr**: wskaźnik do wcześniej przydzielony blok pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-415">**block_ptr**: Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-416">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-416">Return Values</span></span>

- <span data-ttu-id="8bb39-417">**TX_SUCCESS**: (0x00) pomyślna wersja bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-417">**TX_SUCCESS**: (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="8bb39-418">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-418">TX_PTR_ERROR: (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-419">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-419">Allowed From</span></span>

<span data-ttu-id="8bb39-420">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-420">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-421">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-421">Preemption Possible</span></span>

<span data-ttu-id="8bb39-422">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-422">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-423">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-423">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-424">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-424">See Also</span></span>

- <span data-ttu-id="8bb39-425">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-425">tx_block_allocate</span></span>
- <span data-ttu-id="8bb39-426">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-426">tx_block_pool_create</span></span>
- <span data-ttu-id="8bb39-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-427">tx_block_pool_delete</span></span>
- <span data-ttu-id="8bb39-428">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-428">tx_block_pool_info_get</span></span>
- <span data-ttu-id="8bb39-429">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-429">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-430">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-430">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-431">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-431">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="8bb39-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-432">tx_byte_allocate</span></span>

<span data-ttu-id="8bb39-433">Przydziel bajty pamięci</span><span class="sxs-lookup"><span data-stu-id="8bb39-433">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-434">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-434">Prototype</span></span>

```C
UINT tx_byte_allocate(TX_BYTE_POOL *pool_ptr,
                          VOID **memory_ptr, ULONG memory_size,
                          ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="8bb39-435">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-435">Description</span></span>

<span data-ttu-id="8bb39-436">Ta usługa przydziela określoną liczbę bajtów z określonej puli bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-436">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!WARNING]
> <span data-ttu-id="8bb39-437">Ważne jest, aby upewnić się, że kod aplikacji nie zapisuje poza przydzielonym blokiem pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-437">It is important to ensure application code does not write outside the allocated memory block.</span></span> <span data-ttu-id="8bb39-438">W takim przypadku uszkodzenie występuje w sąsiednim (zazwyczaj kolejnym) bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-438">If this happens, corruption occurs in an adjacent (usually subsequent) memory block.</span></span> <span data-ttu-id="8bb39-439">Wyniki są nieprzewidywalne i często są krytyczne!</span><span class="sxs-lookup"><span data-stu-id="8bb39-439">The results are unpredictable and are often fatal!</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-440">Wydajność tej usługi jest funkcją rozmiaru bloku i ilością fragmentacji w puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-440">The performance of this service is a function of the block size and the amount of fragmentation in the pool.</span></span> <span data-ttu-id="8bb39-441">W związku z tym ta usługa nie powinna być używana w wątkach o krytycznym czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-441">Hence, this service should not be used during time-critical threads of execution.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-442">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-442">Parameters</span></span>

- <span data-ttu-id="8bb39-443">**pool_ptr**: wskaźnik do wcześniej utworzonej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-443">**pool_ptr**: Pointer to a previously created memory pool.</span></span>
- <span data-ttu-id="8bb39-444">**memory_ptr**: wskaźnik do wskaźnika pamięci docelowej.</span><span class="sxs-lookup"><span data-stu-id="8bb39-444">**memory_ptr**: Pointer to a destination memory pointer.</span></span> <span data-ttu-id="8bb39-445">Po pomyślnym przydzieleniu adres przydzielonego obszaru pamięci jest umieszczany w miejscu, do którego wskazuje ten parametr.</span><span class="sxs-lookup"><span data-stu-id="8bb39-445">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="8bb39-446">**memory_size**: Liczba żądanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-446">**memory_size**: Number of bytes requested.</span></span>
- <span data-ttu-id="8bb39-447">**WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli nie jest dostępna wystarczająca ilość pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-447">**wait_option**: Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="8bb39-448">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8bb39-448">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8bb39-449">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8bb39-449">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="8bb39-450">**TX_WAIT_FOREVER**: (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="8bb39-450">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="8bb39-451">wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8bb39-451">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="8bb39-452">Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-452">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8bb39-453">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z inicjacji.*</span><span class="sxs-lookup"><span data-stu-id="8bb39-453">*This is the only valid option if the service is called from initialization.*</span></span>

    <span data-ttu-id="8bb39-454">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu udostępnienia wystarczającej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-454">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until enough memory is available.</span></span>

    <span data-ttu-id="8bb39-455">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na pamięć.</span><span class="sxs-lookup"><span data-stu-id="8bb39-455">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-456">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-456">Return Values</span></span>

- <span data-ttu-id="8bb39-457">**TX_SUCCESS**: (0x00) pomyślna alokacja pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-457">**TX_SUCCESS**: (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="8bb39-458">**TX_DELETED**: (0x01) Pula pamięci została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-458">**TX_DELETED**: (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8bb39-459">**TX_NO_MEMORY**: usługa (0x10) nie może przydzielić pamięci w określonym czasie, aby czekać.</span><span class="sxs-lookup"><span data-stu-id="8bb39-459">**TX_NO_MEMORY**: (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="8bb39-460">**TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-460">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8bb39-461">TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-461">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="8bb39-462">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do wskaźnika docelowego.</span><span class="sxs-lookup"><span data-stu-id="8bb39-462">TX_PTR_ERROR: (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="8bb39-463">TX_SIZE_ERROR: (0X05) żądany rozmiar jest równy zero lub większy niż Pula.</span><span class="sxs-lookup"><span data-stu-id="8bb39-463">TX_SIZE_ERROR: (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="8bb39-464">TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-464">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="8bb39-465">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-465">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-466">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-466">Allowed From</span></span>

<span data-ttu-id="8bb39-467">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-467">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-468">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-468">Preemption Possible</span></span>

<span data-ttu-id="8bb39-469">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-469">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-470">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-470">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-471">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-471">See Also</span></span>

- <span data-ttu-id="8bb39-472">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-472">tx_byte_pool_create</span></span>
- <span data-ttu-id="8bb39-473">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-473">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8bb39-474">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-474">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8bb39-475">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-475">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-476">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-476">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-477">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-477">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-478">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-478">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="8bb39-479">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-479">tx_byte_pool_create</span></span>

<span data-ttu-id="8bb39-480">Utwórz pulę pamięci bajtów</span><span class="sxs-lookup"><span data-stu-id="8bb39-480">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-481">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-481">Prototype</span></span>

```C
UINT tx_byte_pool_create(TX_BYTE_POOL *pool_ptr,
                          CHAR *name_ptr, VOID *pool_start,
                          ULONG pool_size);
```
### <a name="description"></a><span data-ttu-id="8bb39-482">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-482">Description</span></span>

<span data-ttu-id="8bb39-483">Ta usługa tworzy pulę bajtów pamięci w określonym obszarze.</span><span class="sxs-lookup"><span data-stu-id="8bb39-483">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="8bb39-484">Początkowo Pula składa się z zasadniczo jednego bardzo dużego bezpłatnego bloku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-484">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="8bb39-485">Jednak Pula jest dzielona na mniejsze bloki w miarę dokonywania alokacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-485">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-486">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-486">Parameters</span></span>

- <span data-ttu-id="8bb39-487">**pool_ptr**: wskaźnik do bloku kontroli puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-487">**pool_ptr**: Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="8bb39-488">**name_ptr**: wskaźnik do nazwy puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-488">**name_ptr**: Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="8bb39-489">**pool_start**: początkowy adres puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-489">**pool_start**: Starting address of the memory pool.</span></span> <span data-ttu-id="8bb39-490">Adres początkowy musi być wyrównany do rozmiaru typu danych ULONG.</span><span class="sxs-lookup"><span data-stu-id="8bb39-490">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="8bb39-491">**pool_size**: Łączna liczba bajtów dostępnych dla puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-491">**pool_size**: Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-492">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-492">Return Values</span></span>

- <span data-ttu-id="8bb39-493">**TX_SUCCESS**: (0X00) pomyślne utworzenie puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-493">**TX_SUCCESS**: (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="8bb39-494">TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-494">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="8bb39-495">Wskaźnik ma wartość NULL lub pula została już utworzona.</span><span class="sxs-lookup"><span data-stu-id="8bb39-495">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="8bb39-496">TX_PTR_ERROR: (0x03) nieprawidłowy adres początkowy puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-496">TX_PTR_ERROR: (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="8bb39-497">TX_SIZE_ERROR: (0x05) rozmiar puli jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-497">TX_SIZE_ERROR: (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="8bb39-498">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-498">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-499">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-499">Allowed From</span></span>

<span data-ttu-id="8bb39-500">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-500">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-501">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-501">Preemption Possible</span></span>

<span data-ttu-id="8bb39-502">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-502">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-503">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-503">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-504">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-504">See Also</span></span>

- <span data-ttu-id="8bb39-505">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-505">tx_byte_allocate</span></span>
- <span data-ttu-id="8bb39-506">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-506">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8bb39-507">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-507">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8bb39-508">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-508">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-509">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-509">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-510">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-510">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-511">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-511">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="8bb39-512">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-512">tx_byte_pool_delete</span></span>

<span data-ttu-id="8bb39-513">Usuwanie puli bajtów pamięci</span><span class="sxs-lookup"><span data-stu-id="8bb39-513">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-514">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-514">Prototype</span></span>

```C
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-515">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-515">Description</span></span>

<span data-ttu-id="8bb39-516">Ta usługa usuwa określoną pulę bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-516">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="8bb39-517">Wszystkie wątki zostały zawieszone, oczekując na wznowienie pamięci z tej puli i z uwzględnieniem TX_DELETED stanu powrotu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-517">All threads suspended waiting for memory from this pool are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-518">Jest on odpowiedzialny za zarządzanie obszarem pamięci skojarzonym z pulą, która jest dostępna po zakończeniu tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-518">It is the application’s responsibility to manage the memory area associated with the pool, which is available after this service completes.</span></span> <span data-ttu-id="8bb39-519">Ponadto aplikacja musi uniemożliwić korzystanie z usuniętej puli lub pamięci, która została wcześniej przypisana.</span><span class="sxs-lookup"><span data-stu-id="8bb39-519">In addition, the application must prevent use of a deleted pool or memory previously allocated from it.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-520">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-520">Parameters</span></span> 

- <span data-ttu-id="8bb39-521">**pool_ptr**: wskaźnik do wcześniej utworzonej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-521">**pool_ptr**: Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-522">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-522">Return Values</span></span>

- <span data-ttu-id="8bb39-523">**TX_SUCCESS**: (0X00) pomyślne usunięcie puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-523">**TX_SUCCESS**: (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="8bb39-524">TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-524">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="8bb39-525">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-525">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-526">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-526">Allowed From</span></span>

<span data-ttu-id="8bb39-527">Wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-527">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-528">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-528">Preemption Possible</span></span>

<span data-ttu-id="8bb39-529">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-530">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-530">Example</span></span>

```C
TX_BYTE_POOL my_pool;
UINT         status;

/* Delete entire memory pool. Assume that the pool has already
   been created with a call to tx_byte_pool_create. */
status =   tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-531">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-531">See Also</span></span>

- <span data-ttu-id="8bb39-532">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-532">tx_byte_allocate</span></span>
- <span data-ttu-id="8bb39-533">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-533">tx_byte_pool_create</span></span>
- <span data-ttu-id="8bb39-534">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-534">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8bb39-535">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-535">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-536">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-536">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-537">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-537">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-538">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-538">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="8bb39-539">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-539">tx_byte_pool_info_get</span></span>

<span data-ttu-id="8bb39-540">Pobierz informacje o puli bajtów</span><span class="sxs-lookup"><span data-stu-id="8bb39-540">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-541">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-541">Prototype</span></span>

```C
UINT tx_byte_pool_info_get(TX_BYTE_POOL *pool_ptr, CHAR **name,
                          ULONG *available, ULONG *fragments,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_BYTE_POOL **next_pool);
```
### <a name="description"></a><span data-ttu-id="8bb39-542">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-542">Description</span></span>

<span data-ttu-id="8bb39-543">Ta usługa pobiera informacje o określonej puli bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-543">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-544">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-544">Parameters</span></span>

- <span data-ttu-id="8bb39-545">**pool_ptr**: wskaźnik do wcześniej utworzonej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-545">**pool_ptr**: Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="8bb39-546">**name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-546">**name**: Pointer to destination for the pointer to the byte pool’s name.</span></span>
- <span data-ttu-id="8bb39-547">**dostępne**: wskaźnik do miejsca docelowego dla liczby dostępnych bajtów w puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-547">**available**: Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="8bb39-548">**fragmenty**: wskaźnik do miejsca docelowego dla łącznej liczby fragmentów pamięci w puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-548">**fragments**: Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="8bb39-549">**first_suspended**: wskaźnik do miejsca docelowego dla wskaźnika do wątku, który najpierw znajduje się na liście zawieszeń tej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-549">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="8bb39-550">**suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-550">**suspended_count**: Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="8bb39-551">**next_pool**: wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-551">**next_pool**: Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-552">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-552">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-553">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-553">Return Values</span></span>

- <span data-ttu-id="8bb39-554">**TX_SUCCESS**: (0X00) pomyślne pobranie informacji o puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-554">**TX_SUCCESS**: (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="8bb39-555">TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-555">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-556">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-556">Allowed From</span></span>

<span data-ttu-id="8bb39-557">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-557">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-558">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-558">Preemption Possible</span></span>

<span data-ttu-id="8bb39-559">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-559">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-560">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-560">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-561">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-561">See Also</span></span>

- <span data-ttu-id="8bb39-562">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-562">tx_byte_allocate</span></span>
- <span data-ttu-id="8bb39-563">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-563">tx_byte_pool_create</span></span>
- <span data-ttu-id="8bb39-564">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-564">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8bb39-565">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-565">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-566">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-566">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-567">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-567">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-568">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-568">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="8bb39-569">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-569">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="8bb39-570">Pobierz informacje o wydajności puli bajtów</span><span class="sxs-lookup"><span data-stu-id="8bb39-570">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-571">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-571">Prototype</span></span>

```C
UINT tx_byte_pool_performance_info_get(TX_BYTE_POOL *pool_ptr,
        ULONG *allocates, ULONG *releases,
        ULONG *fragments_searched, ULONG *merges, ULONG *splits,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="8bb39-572">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-572">Description</span></span>

<span data-ttu-id="8bb39-573">Ta usługa pobiera informacje o wydajności dotyczące określonej puli bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-573">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-574">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-574">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-575">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-575">Parameters</span></span>

- <span data-ttu-id="8bb39-576">**pool_ptr**: wskaźnik do wcześniej utworzonej puli bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-576">**pool_ptr**: Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="8bb39-577">**przypisuje**: wskaźnik do miejsca docelowego dla liczby żądań przydzielenia wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-577">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="8bb39-578">**wersje**: wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-578">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="8bb39-579">**fragments_searched**: wskaźnik do miejsca docelowego dla liczby fragmentów pamięci wewnętrznej przeszukanych podczas żądania alokacji w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-579">**fragments_searched**: Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="8bb39-580">**scalenia**: wskaźnik do miejsca docelowego dla liczby wewnętrznych bloków pamięci scalonych podczas żądań alokacji w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-580">**merges**: Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="8bb39-581">**Splits**: wskaźnik do miejsca docelowego dla liczby wewnętrznych bloków pamięci podzielonej (fragmenty) utworzonych podczas żądania alokacji w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-581">**splits**: Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="8bb39-582">**zawieszenia**: wskaźnik do miejsca docelowego dla liczby zawieszeń alokacji wątku w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-582">**suspensions**: Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="8bb39-583">**limity czasu**: wskaźnik do miejsca docelowego dla liczby limitów przydziału zawieszeń w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-583">**timeouts**: Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-584">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-584">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-585">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-585">Return Values</span></span>

- <span data-ttu-id="8bb39-586">TX_SUCCESS: (0x00) pomyślne pobieranie wydajności puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-586">TX_SUCCESS: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="8bb39-587">**TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-587">**TX_PTR_ERROR**: (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="8bb39-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-588">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-589">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-589">Allowed From</span></span>

<span data-ttu-id="8bb39-590">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-590">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-591">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-591">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-592">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-592">See Also</span></span>

- <span data-ttu-id="8bb39-593">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-593">tx_byte_allocate</span></span>
- <span data-ttu-id="8bb39-594">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-594">tx_byte_pool_create</span></span>
- <span data-ttu-id="8bb39-595">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-595">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8bb39-596">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-596">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8bb39-597">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-597">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-598">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-598">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-599">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-599">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="8bb39-600">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-600">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="8bb39-601">Pobierz informacje o wydajności systemu puli bajtów</span><span class="sxs-lookup"><span data-stu-id="8bb39-601">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-602">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-602">Prototype</span></span>

```C
UINT  tx_byte_pool_performance_system_info_get(ULONG *allocates,
        ULONG *releases, ULONG *fragments_searched, ULONG *merges,
        ULONG *splits, ULONG *suspensions, ULONG *timeouts);;
```
### <a name="description"></a><span data-ttu-id="8bb39-603">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-603">Description</span></span>

<span data-ttu-id="8bb39-604">Ta usługa pobiera informacje o wydajności wszystkich pul bajtów pamięci w systemie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-604">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-605">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-605">The ThreadX SMP library and application must be built with **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-606">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-606">Parameters</span></span>

- <span data-ttu-id="8bb39-607">**przypisuje**: wskaźnik do miejsca docelowego dla liczby żądań przydzielenia wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-607">**allocates**: Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="8bb39-608">**wersje**: wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-608">**releases**: Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="8bb39-609">**fragments_searched**: wskaźnik do miejsca docelowego dla łącznej liczby fragmentów pamięci wewnętrznej przeszukanych podczas żądania alokacji we wszystkich pulach bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-609">**fragments_searched**: Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="8bb39-610">**scalenia**: wskaźnik do miejsca docelowego dla łącznej liczby bloków pamięci wewnętrznej scalonych podczas żądania alokacji we wszystkich pulach bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-610">**merges**: Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="8bb39-611">**Splits**: wskaźnik do miejsca docelowego dla łącznej liczby bloków pamięci wewnętrznej Split (fragmenty) utworzonych podczas żądania alokacji dla wszystkich pul bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-611">**splits**: Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="8bb39-612">**zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń alokacji wątku dla wszystkich pul bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-612">**suspensions**: Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="8bb39-613">**limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia przydziału dla wszystkich pul bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-613">**timeouts**: Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-614">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-614">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-615">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-615">Return Values</span></span>

- <span data-ttu-id="8bb39-616">**TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-616">**TX_SUCCESS**: (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="8bb39-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-617">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-618">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-618">Allowed From</span></span>

<span data-ttu-id="8bb39-619">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-619">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-620">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-620">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-621">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-621">See Also</span></span>

- <span data-ttu-id="8bb39-622">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-622">tx_byte_allocate</span></span>
- <span data-ttu-id="8bb39-623">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-623">tx_byte_pool_create</span></span>
- <span data-ttu-id="8bb39-624">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-624">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8bb39-625">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-625">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8bb39-626">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-626">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-627">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-627">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="8bb39-628">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-628">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="8bb39-629">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-629">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="8bb39-630">Ustawianie priorytetu listy zawieszania puli bajtów</span><span class="sxs-lookup"><span data-stu-id="8bb39-630">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-631">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-631">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-632">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-632">Description</span></span>

<span data-ttu-id="8bb39-633">Ta usługa umieszcza wątek o najwyższym priorytecie dla pamięci w tej puli na początku listy zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-633">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="8bb39-634">Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-634">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-635">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-635">Parameters</span></span> 

- <span data-ttu-id="8bb39-636">**pool_ptr**: wskaźnik do bloku kontroli puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-636">**pool_ptr**: Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-637">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-637">Return Values</span></span>

- <span data-ttu-id="8bb39-638">**TX_SUCCESS**: (0x00) pomyślna priorytetyzacja puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-638">**TX_SUCCESS**: (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="8bb39-639">TX_POOL_ERROR: (0x02) Nieprawidłowy wskaźnik puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-639">TX_POOL_ERROR: (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-640">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-640">Allowed From</span></span>

<span data-ttu-id="8bb39-641">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-641">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-642">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-642">Preemption Possible</span></span>

<span data-ttu-id="8bb39-643">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-643">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-644">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-644">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-645">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-645">See Also</span></span>

- <span data-ttu-id="8bb39-646">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-646">tx_byte_allocate</span></span>
- <span data-ttu-id="8bb39-647">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-647">tx_byte_pool_create</span></span>
- <span data-ttu-id="8bb39-648">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-648">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8bb39-649">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-649">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8bb39-650">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-650">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-651">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-651">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-652">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-652">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="8bb39-653">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="8bb39-653">tx_byte_release</span></span>

<span data-ttu-id="8bb39-654">Wydawanie bajtów z powrotem do puli pamięci</span><span class="sxs-lookup"><span data-stu-id="8bb39-654">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-655">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-655">Prototype</span></span>

```C
UINT tx_byte_release(VOID *memory_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-656">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-656">Description</span></span>

<span data-ttu-id="8bb39-657">Ta usługa zwalnia wcześniej przydzieloną przestrzeń pamięci z powrotem do skojarzonej puli.</span><span class="sxs-lookup"><span data-stu-id="8bb39-657">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="8bb39-658">Jeśli istnieje co najmniej jeden wątek, który wstrzymał oczekiwanie na pamięć z tej puli, przybierana jest pamięć i wznawiana do momentu wyczerpania pamięci lub do momentu, gdy nie będzie już można wstrzymać wątków.</span><span class="sxs-lookup"><span data-stu-id="8bb39-658">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="8bb39-659">Ten proces przydzielania pamięci do zawieszonych wątków zawsze zaczyna się od pierwszego wątku zawieszonego.</span><span class="sxs-lookup"><span data-stu-id="8bb39-659">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-660">Aplikacja musi uniemożliwić korzystanie z obszaru pamięci po jego udostępnieniu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-660">The application must prevent using the memory area after it is released.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-661">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-661">Parameters</span></span>

- <span data-ttu-id="8bb39-662">**memory_ptr**: wskaźnik do wcześniej przydzieloną obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-662">**memory_ptr**: Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-663">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-663">Return Values</span></span>

- <span data-ttu-id="8bb39-664">**TX_SUCCESS**: (0X00) pomyślne wydanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-664">**TX_SUCCESS**: (0x00) Successful memory release.</span></span>
- <span data-ttu-id="8bb39-665">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-665">TX_PTR_ERROR: (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="8bb39-666">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-666">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-667">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-667">Allowed From</span></span>

<span data-ttu-id="8bb39-668">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-668">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-669">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-669">Preemption Possible</span></span>

<span data-ttu-id="8bb39-670">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-670">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-671">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-671">Example</span></span>

```C
unsigned char    *memory_ptr;
UINT             status;

/* Release a memory back to my_pool. Assume that the memory
   area was previously allocated from my_pool. */
status =  tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
   memory_ptr has been returned to the pool. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-672">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-672">See Also</span></span>

- <span data-ttu-id="8bb39-673">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="8bb39-673">tx_byte_allocate</span></span>
- <span data-ttu-id="8bb39-674">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-674">tx_byte_pool_create</span></span>
- <span data-ttu-id="8bb39-675">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-675">tx_byte_pool_delete</span></span>
- <span data-ttu-id="8bb39-676">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-676">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="8bb39-677">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-677">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="8bb39-678">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-678">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-679">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-679">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="8bb39-680">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-680">tx_event_flags_create</span></span>

<span data-ttu-id="8bb39-681">Utwórz grupę flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8bb39-681">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-682">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-682">Prototype</span></span>

```c
UINT tx_event_flags_create(TX_EVENT_FLAGS_GROUP *group_ptr,
                          CHAR *name_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-683">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-683">Description</span></span>

<span data-ttu-id="8bb39-684">Ta usługa tworzy grupę flag zdarzeń 32.</span><span class="sxs-lookup"><span data-stu-id="8bb39-684">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="8bb39-685">Wszystkie flagi zdarzeń 32 w grupie są inicjowane na zero.</span><span class="sxs-lookup"><span data-stu-id="8bb39-685">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="8bb39-686">Każda flaga zdarzenia jest reprezentowana przez jeden bit.</span><span class="sxs-lookup"><span data-stu-id="8bb39-686">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-687">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-687">Parameters</span></span>

- <span data-ttu-id="8bb39-688">**group_ptr**: wskaźnik do bloku sterowania grupą flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-688">**group_ptr**: Pointer to an event flags group control block.</span></span> 
- <span data-ttu-id="8bb39-689">**name_ptr**: wskaźnik do nazwy grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-689">**name_ptr**: Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-690">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-690">Return Values</span></span>

- <span data-ttu-id="8bb39-691">**TX_SUCCESS**: (0X00) pomyślne utworzenie grupy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-691">**TX_SUCCESS**: (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="8bb39-692">TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-692">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="8bb39-693">Wskaźnik ma wartość NULL lub grupa zdarzeń została już utworzona.</span><span class="sxs-lookup"><span data-stu-id="8bb39-693">Either the pointer is NULL or the event group is already created.</span></span>
- <span data-ttu-id="8bb39-694">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-694">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-695">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-695">Allowed From</span></span>

<span data-ttu-id="8bb39-696">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-696">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-697">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-697">Preemption Possible</span></span>

<span data-ttu-id="8bb39-698">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-698">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-699">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-699">Example</span></span>

```C
TX_EVENT_FLAGS_GROUP my_event_group;
UINT         status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
            "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
   for get and set services. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-700">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-700">See Also</span></span>

- <span data-ttu-id="8bb39-701">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-701">tx_event_flags_delete</span></span>
- <span data-ttu-id="8bb39-702">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-702">tx_event_flags_get</span></span>
- <span data-ttu-id="8bb39-703">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-703">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8bb39-704">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-704">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8bb39-705">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-705">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-706">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8bb39-706">tx_event_flags_set</span></span>
- <span data-ttu-id="8bb39-707">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-707">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="8bb39-708">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-708">tx_event_flags_delete</span></span>

<span data-ttu-id="8bb39-709">Usuń grupę flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8bb39-709">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-710">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-710">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-711">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-711">Description</span></span>

<span data-ttu-id="8bb39-712">Ta usługa usuwa określoną grupę flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-712">This service deletes the specified event flags group.</span></span> <span data-ttu-id="8bb39-713">Wszystkie wątki zawieszone w trakcie oczekiwania na zdarzenia z tej grupy są wznawiane i mają TX_DELETED stanu powrotu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-713">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-714">Aplikacja musi upewnić się, że ustawione wywołanie zwrotne powiadomień dla tej grupy flag zdarzeń zostanie ukończone (lub wyłączone) przed usunięciem grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-714">The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group.</span></span> <span data-ttu-id="8bb39-715">Ponadto aplikacja musi uniemożliwić wszystkie przyszłe użycie grupy flag zdarzeń usuniętych.</span><span class="sxs-lookup"><span data-stu-id="8bb39-715">In addition, the application must prevent all future use of a deleted event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-716">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-716">Parameters</span></span> 

- <span data-ttu-id="8bb39-717">**group_ptr**: wskaźnik do wcześniej utworzonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-717">**group_ptr**: Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-718">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-718">Return Values</span></span>

- <span data-ttu-id="8bb39-719">**TX_SUCCESS**: (0x00) usunięcie grupy flag zdarzeń zakończonych powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-719">**TX_SUCCESS**: (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="8bb39-720">TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-720">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="8bb39-721">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-721">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-722">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-722">Allowed From</span></span>

<span data-ttu-id="8bb39-723">Wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-723">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-724">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-724">Preemption Possible</span></span>

<span data-ttu-id="8bb39-725">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-725">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-726">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-726">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-727">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-727">See Also</span></span>

- <span data-ttu-id="8bb39-728">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-728">tx_event_flags_create</span></span>
- <span data-ttu-id="8bb39-729">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-729">tx_event_flags_get</span></span>
- <span data-ttu-id="8bb39-730">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-730">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8bb39-731">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-731">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8bb39-732">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-732">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-733">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8bb39-733">tx_event_flags_set</span></span>
- <span data-ttu-id="8bb39-734">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-734">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="8bb39-735">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-735">tx_event_flags_get</span></span>

<span data-ttu-id="8bb39-736">Pobierz flagi zdarzeń z grupy flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8bb39-736">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-737">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-737">Prototype</span></span>

```C
UINT tx_event_flags_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG requested_flags, UINT get_option,
                          ULONG *actual_flags_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="8bb39-738">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-738">Description</span></span>

<span data-ttu-id="8bb39-739">Ta usługa pobiera flagi zdarzeń z określonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-739">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="8bb39-740">Każda grupa flag zdarzeń zawiera 32 flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-740">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="8bb39-741">Każda flaga jest reprezentowana przez jeden bit.</span><span class="sxs-lookup"><span data-stu-id="8bb39-741">Each flag is represented by a single bit.</span></span> <span data-ttu-id="8bb39-742">Ta usługa może pobrać różne kombinacje flag zdarzeń wybrane przez parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="8bb39-742">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-743">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-743">Parameters</span></span>

- <span data-ttu-id="8bb39-744">**group_ptr**: wskaźnik do wcześniej utworzonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-744">**group_ptr**: Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="8bb39-745">**requested_flags**: 32-bitowa zmienna bez znaku reprezentująca żądane flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-745">**requested_flags**: 32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="8bb39-746">**get_option**: określa, czy są wymagane wszystkie lub wszystkie wymagane flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-746">**get_option**: Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="8bb39-747">Następujące opcje są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="8bb39-747">The following are valid selections:</span></span>
    - <span data-ttu-id="8bb39-748">**TX_AND**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="8bb39-748">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="8bb39-749">**TX_AND_CLEAR**: (0x03)</span><span class="sxs-lookup"><span data-stu-id="8bb39-749">**TX_AND_CLEAR**: (0x03)</span></span>
    - <span data-ttu-id="8bb39-750">**TX_OR**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="8bb39-750">**TX_OR**: (0x00)</span></span>
    - <span data-ttu-id="8bb39-751">**TX_OR_CLEAR**: (0x01)</span><span class="sxs-lookup"><span data-stu-id="8bb39-751">**TX_OR_CLEAR**: (0x01)</span></span>

    <span data-ttu-id="8bb39-752">Wybranie opcji TX_AND lub TX_AND_CLEAR określa, że wszystkie flagi zdarzeń muszą znajdować się w grupie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-752">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="8bb39-753">Wybór TX_OR lub TX_OR_CLEAR określa, że każda flaga zdarzenia jest zadowalająca.</span><span class="sxs-lookup"><span data-stu-id="8bb39-753">Selecting TX_OR or TX_OR_CLEAR specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="8bb39-754">Flagi zdarzeń, które spełniają żądanie, są wyczyszczone (Ustaw wartość zero), jeśli określono TX_AND_CLEAR lub TX_OR_CLEAR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-754">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="8bb39-755">**actual_flags_ptr**: wskaźnik do lokalizacji docelowej, do której są umieszczone pobrane flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-755">**actual_flags_ptr**: Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="8bb39-756">Należy zauważyć, że uzyskane bieżące flagi mogą zawierać flagi, które nie zostały zażądane.</span><span class="sxs-lookup"><span data-stu-id="8bb39-756">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="8bb39-757">**WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli wybrane flagi zdarzeń nie są ustawione.</span><span class="sxs-lookup"><span data-stu-id="8bb39-757">**wait_option**: Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="8bb39-758">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8bb39-758">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8bb39-759">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8bb39-759">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="8bb39-760">**TX_WAIT_FOREVER**: (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="8bb39-760">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="8bb39-761">wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8bb39-761">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="8bb39-762">Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-762">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8bb39-763">Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-763">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="8bb39-764">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu udostępnienia flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-764">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>

    <span data-ttu-id="8bb39-765">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-765">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-766">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-766">Return Values</span></span>

- <span data-ttu-id="8bb39-767">**TX_SUCCESS**: (0X00) pomyślne flagi zdarzeń get.</span><span class="sxs-lookup"><span data-stu-id="8bb39-767">**TX_SUCCESS**: (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="8bb39-768">Grupa flag zdarzeń **TX_DELETED**: (0x01) została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-768">**TX_DELETED**: (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8bb39-769">**TX_NO_EVENTS**: usługa (0x07) nie może pobrać określonych zdarzeń w określonym czasie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-769">**TX_NO_EVENTS**: (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="8bb39-770">**TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-770">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8bb39-771">TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-771">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="8bb39-772">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik dla rzeczywistych flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-772">TX_PTR_ERROR: (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="8bb39-773">TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-773">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="8bb39-774">TX_OPTION_ERROR: (0x08) określono nieprawidłową opcję Get-Option.</span><span class="sxs-lookup"><span data-stu-id="8bb39-774">TX_OPTION_ERROR: (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-775">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-775">Allowed From</span></span>

<span data-ttu-id="8bb39-776">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-776">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-777">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-777">Preemption Possible</span></span>

<span data-ttu-id="8bb39-778">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-778">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-779">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-779">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-780">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-780">See Also</span></span>

- <span data-ttu-id="8bb39-781">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-781">tx_event_flags_create</span></span>
- <span data-ttu-id="8bb39-782">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-782">tx_event_flags_delete</span></span>
- <span data-ttu-id="8bb39-783">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-783">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8bb39-784">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-784">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8bb39-785">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-785">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-786">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8bb39-786">tx_event_flags_set</span></span>
- <span data-ttu-id="8bb39-787">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-787">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_info_get"></a><span data-ttu-id="8bb39-788">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-788">tx_event_flags_info_get</span></span>

<span data-ttu-id="8bb39-789">Pobierz informacje o grupie flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8bb39-789">Retrieve information about event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-790">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-790">Prototype</span></span>

```C
UINT tx_event_flags_info_get(TX_EVENT_FLAGS_GROUP *group_ptr,
                         CHAR **name, ULONG *current_flags,
                         TX_THREAD **first_suspended,
                         ULONG *suspended_count,
                         TX_EVENT_FLAGS_GROUP **next_group);
```
### <a name="description"></a><span data-ttu-id="8bb39-791">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-791">Description</span></span>

<span data-ttu-id="8bb39-792">Ta usługa pobiera informacje o określonej grupie flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-792">This service retrieves information about the specified event flags group.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-793">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-793">Parameters</span></span>

- <span data-ttu-id="8bb39-794">**group_ptr**: wskaźnik do bloku sterowania grupą flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-794">**group_ptr**: Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="8bb39-795">**name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-795">**name**: Pointer to destination for the pointer to the event flags group’s name.</span></span>
- <span data-ttu-id="8bb39-796">**current_flags**: wskaźnik do miejsca docelowego dla bieżących flag ustawionych w grupie flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-796">**current_flags**: Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="8bb39-797">**first_suspended**: wskaźnik do elementu docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-797">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="8bb39-798">**suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej grupie flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-798">**suspended_count**: Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="8bb39-799">**next_group**: wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-799">**next_group**: Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-800">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-800">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-801">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-801">Return Values</span></span>

- <span data-ttu-id="8bb39-802">**TX_SUCCESS**: (0X00) pomyślne pobieranie informacji o grupie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-802">**TX_SUCCESS**: (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="8bb39-803">TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-803">TX_GROUP_ERROR: (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-804">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-804">Allowed From</span></span>

<span data-ttu-id="8bb39-805">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-805">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-806">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-806">Preemption Possible</span></span>

<span data-ttu-id="8bb39-807">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-807">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-808">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-808">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-809">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-809">See Also</span></span>

- <span data-ttu-id="8bb39-810">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-810">tx_event_flags_create</span></span>
- <span data-ttu-id="8bb39-811">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-811">tx_event_flags_delete</span></span>
- <span data-ttu-id="8bb39-812">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-812">tx_event_flags_get</span></span>
- <span data-ttu-id="8bb39-813">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-813">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8bb39-814">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-814">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-815">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8bb39-815">tx_event_flags_set</span></span>
- <span data-ttu-id="8bb39-816">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-816">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance-info_get"></a><span data-ttu-id="8bb39-817">tx_event_flags_performance info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-817">tx_event_flags_performance info_get</span></span>

<span data-ttu-id="8bb39-818">Pobierz informacje o wydajności grupy flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8bb39-818">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-819">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-819">Prototype</span></span>

```C
UINT tx_event_flags_performance_info_get(TX_EVENT_FLAGS_GROUP
                        *group_ptr, ULONG *sets, ULONG *gets,
                        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="8bb39-820">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-820">Description</span></span>

<span data-ttu-id="8bb39-821">Ta usługa pobiera informacje o wydajności dotyczące określonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-821">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-822">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-822">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-823">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-823">Parameters</span></span>

- <span data-ttu-id="8bb39-824">**group_ptr**: wskaźnik do wcześniej utworzonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-824">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="8bb39-825">**zestawy**: wskaźnik do miejsca docelowego dla liczby flag zdarzeń ustawia żądania wykonane dla tej grupy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-825">**sets**: Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="8bb39-826">**Pobiera**: wskaźnik do miejsca docelowego dla liczby flag zdarzeń Pobiera żądania wykonane dla tej grupy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-826">**gets**: Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="8bb39-827">**zawieszenia**: wskaźnik do miejsca docelowego dla liczby flag zdarzeń wątku uzyskuje zawieszenie dla tej grupy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-827">**suspensions**: Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="8bb39-828">**limity czasu**: wskaźnik do miejsca docelowego dla liczby flag zdarzeń uzyskuje limity czasu zawieszenia dla tej grupy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-828">**timeouts**: Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-829">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-829">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-830">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-830">Return Values</span></span>

- <span data-ttu-id="8bb39-831">**TX_SUCCESS**: (0X00) pomyślne flagi zdarzeń grupy get.</span><span class="sxs-lookup"><span data-stu-id="8bb39-831">**TX_SUCCESS**: (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="8bb39-832">**TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-832">**TX_PTR_ERROR**: (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="8bb39-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-833">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-834">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-834">Allowed From</span></span>

<span data-ttu-id="8bb39-835">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-835">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-836">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-836">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-837">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-837">See Also</span></span>

- <span data-ttu-id="8bb39-838">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-838">tx_event_flags_create</span></span>
- <span data-ttu-id="8bb39-839">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-839">tx_event_flags_delete</span></span>
- <span data-ttu-id="8bb39-840">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-840">tx_event_flags_get</span></span>
- <span data-ttu-id="8bb39-841">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-841">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8bb39-842">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-842">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-843">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8bb39-843">tx_event_flags_set</span></span>
- <span data-ttu-id="8bb39-844">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-844">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="8bb39-845">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-845">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="8bb39-846">Pobierz informacje o systemie wydajności</span><span class="sxs-lookup"><span data-stu-id="8bb39-846">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-847">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-847">Prototype</span></span>

```c
UINT  tx_event_flags_performance_system_info_get(ULONG *sets,
        ULONG *gets,ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="8bb39-848">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-848">Description</span></span>

<span data-ttu-id="8bb39-849">Ta usługa pobiera informacje o wydajności wszystkich grup flag zdarzeń w systemie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-849">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-850">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-850">ThreadX SMP library and application must be built with **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-851">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-851">Parameters</span></span>

- <span data-ttu-id="8bb39-852">**zestawy**: wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń ustawionych żądania dla wszystkich grup.</span><span class="sxs-lookup"><span data-stu-id="8bb39-852">**sets**: Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="8bb39-853">**Pobiera**: wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń pobieranie żądań wykonanych dla wszystkich grup.</span><span class="sxs-lookup"><span data-stu-id="8bb39-853">**gets**: Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="8bb39-854">**zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń wątku uzyskuje zawieszenie dla wszystkich grup.</span><span class="sxs-lookup"><span data-stu-id="8bb39-854">**suspensions**: Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="8bb39-855">**limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń pobieranie limitów czasu zawieszenia dla wszystkich grup.</span><span class="sxs-lookup"><span data-stu-id="8bb39-855">**timeouts**: Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-856">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-856">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-857">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-857">Return Values</span></span>

- <span data-ttu-id="8bb39-858">**TX_SUCCESS**: (0X00) pomyślne flagi zdarzeń wydajność systemu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-858">**TX_SUCCESS**: (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="8bb39-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-859">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-860">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-860">Allowed From</span></span>

<span data-ttu-id="8bb39-861">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-861">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-862">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-862">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-863">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-863">See Also</span></span>

- <span data-ttu-id="8bb39-864">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-864">tx_event_flags_create</span></span>
- <span data-ttu-id="8bb39-865">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-865">tx_event_flags_delete</span></span>
- <span data-ttu-id="8bb39-866">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-866">tx_event_flags_get</span></span>
- <span data-ttu-id="8bb39-867">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-867">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8bb39-868">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-868">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8bb39-869">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8bb39-869">tx_event_flags_set</span></span>
- <span data-ttu-id="8bb39-870">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-870">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="8bb39-871">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8bb39-871">tx_event_flags_set</span></span>

<span data-ttu-id="8bb39-872">Ustawianie flag zdarzeń w grupie flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8bb39-872">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-873">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-873">Prototype</span></span>

```C
UINT tx_event_flags_set(TX_EVENT_FLAGS_GROUP *group_ptr,
                          ULONG  flags_to_set,UINT set_option);
```
### <a name="description"></a><span data-ttu-id="8bb39-874">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-874">Description</span></span>

<span data-ttu-id="8bb39-875">Ta usługa ustawia lub czyści flagi zdarzeń w grupie flag zdarzeń, w zależności od określonego zestawu opcji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-875">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="8bb39-876">Wszystkie zawieszone wątki, których żądanie flag zdarzeń jest teraz spełnione, są wznawiane.</span><span class="sxs-lookup"><span data-stu-id="8bb39-876">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-877">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-877">Parameters</span></span>

- <span data-ttu-id="8bb39-878">**group_ptr**: wskaźnik do wcześniej utworzonego bloku kontroli grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-878">**group_ptr**: Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="8bb39-879">**flags_to_set**: określa flagi zdarzeń do ustawienia lub wyczyszczenia w zależności od wybranej opcji zestawu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-879">**flags_to_set**: Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="8bb39-880">**set_option**: określa, czy określone flagi zdarzeń są ANDed lub logicznie do bieżących flag zdarzenia w grupie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-880">**set_option**: Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="8bb39-881">Następujące opcje są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="8bb39-881">The following are valid selections:</span></span>
    - <span data-ttu-id="8bb39-882">**TX_AND**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="8bb39-882">**TX_AND**: (0x02)</span></span>
    - <span data-ttu-id="8bb39-883">**TX_OR**: (0X00) wybranie pozycji TX_AND określa, że określone flagi zdarzeń są **i** są wbudowane w bieżące flagi zdarzenia w grupie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-883">**TX_OR**: (0x00) Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="8bb39-884">Ta opcja jest często używana do czyszczenia flag zdarzeń w grupie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-884">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="8bb39-885">W przeciwnym razie, jeśli określono TX_OR, określone flagi zdarzeń są **lub** Ed bieżącym zdarzeniem w grupie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-885">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-886">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-886">Return Values</span></span>

- <span data-ttu-id="8bb39-887">**TX_SUCCESS**: (0x00) ustawiono flag zdarzeń zakończonych powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-887">**TX_SUCCESS**: (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="8bb39-888">TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik do grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-888">TX_GROUP_ERROR: (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="8bb39-889">TX_OPTION_ERROR: (0x08) określono nieprawidłową opcję Set.</span><span class="sxs-lookup"><span data-stu-id="8bb39-889">TX_OPTION_ERROR: (0x08) Invalid set-option specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-890">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-890">Allowed From</span></span>

<span data-ttu-id="8bb39-891">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-891">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-892">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-892">Preemption Possible</span></span>

<span data-ttu-id="8bb39-893">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-893">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-894">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-894">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-895">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-895">See Also</span></span>

- <span data-ttu-id="8bb39-896">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-896">tx_event_flags_create</span></span>
- <span data-ttu-id="8bb39-897">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-897">tx_event_flags_delete</span></span>
- <span data-ttu-id="8bb39-898">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-898">tx_event_flags_get</span></span>
- <span data-ttu-id="8bb39-899">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-899">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8bb39-900">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-900">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8bb39-901">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-901">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-902">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-902">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="8bb39-903">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-903">tx_event_flags_set_notify</span></span>

<span data-ttu-id="8bb39-904">Powiadamiaj aplikację, gdy są ustawione flagi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8bb39-904">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-905">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-905">Prototype</span></span>

```C
UINT tx_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr,
       VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```
### <a name="description"></a><span data-ttu-id="8bb39-906">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-906">Description</span></span>

<span data-ttu-id="8bb39-907">Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy jedna lub więcej flag zdarzeń jest ustawionych w określonej grupie flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-907">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="8bb39-908">Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8bb39-908">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="8bb39-909">Flagi zdarzeń aplikacji ustawiające wywołanie zwrotne powiadomienia nie mogą wywoływać żadnego interfejsu API SMP ThreadX z opcją zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-909">The application’s event flags set notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-910">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-910">Parameters</span></span> 
- <span data-ttu-id="8bb39-911">**group_ptr**: wskaźnik do wcześniej utworzonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-911">**group_ptr**: Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="8bb39-912">**events_set_notify**: wskaźnik do flag zdarzeń aplikacji ustawia funkcję powiadomień.</span><span class="sxs-lookup"><span data-stu-id="8bb39-912">**events_set_notify**: Pointer to application’s event flags set notification function.</span></span> <span data-ttu-id="8bb39-913">Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-913">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-914">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-914">Return Values</span></span>

- <span data-ttu-id="8bb39-915">**TX_SUCCESS**: (0x00) pomyślna Rejestracja flag zdarzeń ustawionych dla powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-915">**TX_SUCCESS**: (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="8bb39-916">TX_GROUP_ERROR: (0x06) Nieprawidłowy wskaźnik grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-916">TX_GROUP_ERROR: (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="8bb39-917">TX_FEATURE_NOT_ENABLED: (0xFF) system został skompilowany z wyłączonymi funkcjami powiadomień.</span><span class="sxs-lookup"><span data-stu-id="8bb39-917">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-918">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-918">Allowed From</span></span>

<span data-ttu-id="8bb39-919">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-919">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-920">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-920">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-921">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-921">See Also</span></span>

- <span data-ttu-id="8bb39-922">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-922">tx_event_flags_create</span></span>
- <span data-ttu-id="8bb39-923">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-923">tx_event_flags_delete</span></span>
- <span data-ttu-id="8bb39-924">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-924">tx_event_flags_get</span></span>
- <span data-ttu-id="8bb39-925">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-925">tx_event_flags_info_get</span></span>
- <span data-ttu-id="8bb39-926">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-926">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="8bb39-927">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-927">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-928">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="8bb39-928">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="8bb39-929">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="8bb39-929">tx_interrupt_control</span></span>

<span data-ttu-id="8bb39-930">Włączanie i wyłączanie przerwań</span><span class="sxs-lookup"><span data-stu-id="8bb39-930">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-931">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-931">Prototype</span></span>

```C
UINT tx_interrupt_control(UINT new_posture);
```
### <a name="description"></a><span data-ttu-id="8bb39-932">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-932">Description</span></span>

<span data-ttu-id="8bb39-933">Ta usługa włącza lub wyłącza przerwania określone przez parametr wejściowy **new_posture**.</span><span class="sxs-lookup"><span data-stu-id="8bb39-933">This service enables or disables interrupts as specified by the input parameter **new_posture**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-934">Jeśli ta usługa jest wywoływana z wątku aplikacji, przerwa stan pozostaje częścią kontekstu tego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-934">If this service is called from an application thread, the interrupt posture remains part of that thread’s context.</span></span> <span data-ttu-id="8bb39-935">Na przykład jeśli wątek wywołuje tę procedurę w celu wyłączenia przerwań, a następnie zawiesza się po wznowieniu, przerwania zostaną wyłączone ponownie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-935">For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.</span></span>

> [!WARNING]
> <span data-ttu-id="8bb39-936">Ta usługa nie powinna być używana do włączania przerwań podczas inicjacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-936">This service should not be used to enable interrupts during initialization!</span></span> <span data-ttu-id="8bb39-937">Wykonanie tej operacji może spowodować nieprzewidywalne wyniki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-937">Doing so could cause unpredictable results.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-938">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-938">Parameters</span></span>

- <span data-ttu-id="8bb39-939">**new_posture**: ten parametr określa, czy przerwania są wyłączone czy włączone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-939">**new_posture**: This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="8bb39-940">Wartości prawne obejmują **TX_INT_DISABLE i TX_INT_ENABLE.**</span><span class="sxs-lookup"><span data-stu-id="8bb39-940">Legal values include **TX_INT_DISABLE and TX_INT_ENABLE.**</span></span> <span data-ttu-id="8bb39-941">Rzeczywiste wartości tych parametrów są specyficzne dla portów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-941">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="8bb39-942">Ponadto niektóre architektury przetwarzania mogą obsługiwać dodatkowe przerwania postures.</span><span class="sxs-lookup"><span data-stu-id="8bb39-942">In addition, some processing architectures might support additional interrupt disable postures.</span></span> <span data-ttu-id="8bb39-943">Aby uzyskać więcej informacji, zapoznaj się z informacjami dotyczącymi **_readme_threadx.txt_** na dysku dystrybucyjnym.</span><span class="sxs-lookup"><span data-stu-id="8bb39-943">Please see the **_readme_threadx.txt_** information supplied on the distribution disk for more details.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-944">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-944">Return Values</span></span>

- <span data-ttu-id="8bb39-945">Poprzedni stan: Ta usługa zwraca poprzednie przerwanie stan do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8bb39-945">previous posture: This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="8bb39-946">Dzięki temu użytkownicy usługi mogą przywrócić poprzednią stan po wyłączeniu przerwań.</span><span class="sxs-lookup"><span data-stu-id="8bb39-946">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-947">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-947">Allowed From</span></span>

<span data-ttu-id="8bb39-948">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-948">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-949">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-949">Preemption Possible</span></span>

<span data-ttu-id="8bb39-950">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-950">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-951">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-951">Example</span></span>

```C
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture =  tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
   locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```
### <a name="see-also"></a><span data-ttu-id="8bb39-952">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-952">See Also</span></span>

<span data-ttu-id="8bb39-953">Brak</span><span class="sxs-lookup"><span data-stu-id="8bb39-953">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="8bb39-954">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-954">tx_mutex_create</span></span>

<span data-ttu-id="8bb39-955">Utwórz element mutex wzajemnego wykluczania</span><span class="sxs-lookup"><span data-stu-id="8bb39-955">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-956">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-956">Prototype</span></span>

```C
UINT tx_mutex_create(TX_MUTEX *mutex_ptr,
                          CHAR *name_ptr, UINT priority_inherit);
```
### <a name="description"></a><span data-ttu-id="8bb39-957">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-957">Description</span></span>
    
<span data-ttu-id="8bb39-958">Ta usługa tworzy element mutex do wzajemnego wykluczania między wątkami na potrzeby ochrony zasobów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-958">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-959">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-959">Parameters</span></span>

- <span data-ttu-id="8bb39-960">**mutex_ptr**: wskaźnik do bloku sterowania muteksem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-960">**mutex_ptr**: Pointer to a mutex control block.</span></span>
- <span data-ttu-id="8bb39-961">**name_ptr**: wskaźnik do nazwy obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-961">**name_ptr**: Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="8bb39-962">**priority_inherit**: określa, czy ten element mutex obsługuje dziedziczenie priorytetów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-962">**priority_inherit**: Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="8bb39-963">Jeśli ta wartość jest TX_INHERIT, jest obsługiwane dziedziczenie priorytetu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-963">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="8bb39-964">Jeśli jednak określono TX_NO_INHERIT, dziedziczenie priorytetu nie jest obsługiwane przez ten mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-964">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-965">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-965">Return Values</span></span>

- <span data-ttu-id="8bb39-966">**TX_SUCCESS**: (0X00) pomyślne utworzenie obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-966">**TX_SUCCESS**: (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="8bb39-967">TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-967">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="8bb39-968">Wskaźnik ma wartość NULL lub element mutex został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-968">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="8bb39-969">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-969">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="8bb39-970">TX_INHERIT_ERROR: (0x1F) nieprawidłowy priorytet dziedziczenia parametru.</span><span class="sxs-lookup"><span data-stu-id="8bb39-970">TX_INHERIT_ERROR: (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-971">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-971">Allowed From</span></span>

<span data-ttu-id="8bb39-972">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-972">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-973">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-973">Preemption Possible</span></span>

<span data-ttu-id="8bb39-974">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-974">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-975">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-975">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-976">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-976">See Also</span></span>

- <span data-ttu-id="8bb39-977">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-977">tx_mutex_delete</span></span>
- <span data-ttu-id="8bb39-978">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-978">tx_mutex_get</span></span>
- <span data-ttu-id="8bb39-979">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-979">tx_mutex_info_get</span></span>
- <span data-ttu-id="8bb39-980">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-980">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8bb39-981">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-981">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-982">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-982">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8bb39-983">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-983">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="8bb39-984">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-984">tx_mutex_delete</span></span>

<span data-ttu-id="8bb39-985">Usuń element mutex wzajemnego wykluczania</span><span class="sxs-lookup"><span data-stu-id="8bb39-985">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-986">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-986">Prototype</span></span>

```C
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-987">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-987">Description</span></span>

<span data-ttu-id="8bb39-988">Ta usługa usuwa określony element mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-988">This service deletes the specified mutex.</span></span> <span data-ttu-id="8bb39-989">Wszystkie wątki zawieszone w trakcie oczekiwania na element mutex są wznawiane i nadano TX_DELETED stanu powrotu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-989">All threads suspended waiting for the mutex are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-990">Jest to odpowiedzialność aplikacji, aby uniemożliwić korzystanie z usuniętego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-990">It is the application’s responsibility to prevent use of a deleted mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-991">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-991">Parameters</span></span>

- <span data-ttu-id="8bb39-992">**mutex_ptr**: wskaźnik do wcześniej utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-992">**mutex_ptr**: Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-993">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-993">Return Values</span></span>

- <span data-ttu-id="8bb39-994">**TX_SUCCESS**: (0X00) pomyślne usunięcie obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-994">**TX_SUCCESS**: (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="8bb39-995">TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-995">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="8bb39-996">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-996">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-997">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-997">Allowed From</span></span>

<span data-ttu-id="8bb39-998">Wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-998">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-999">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-999">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1000">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1000">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1001">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1001">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Delete a mutex. Assume that the mutex
   has already been created. */
status =  tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-1002">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1002">See Also</span></span>

- <span data-ttu-id="8bb39-1003">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1003">tx_mutex_create</span></span>
- <span data-ttu-id="8bb39-1004">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1004">tx_mutex_get</span></span>
- <span data-ttu-id="8bb39-1005">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1005">tx_mutex_info_get</span></span>
- <span data-ttu-id="8bb39-1006">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1006">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1007">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1007">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1008">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1008">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8bb39-1009">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1009">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="8bb39-1010">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1010">tx_mutex_get</span></span>

<span data-ttu-id="8bb39-1011">Uzyskaj własność obiektu mutex</span><span class="sxs-lookup"><span data-stu-id="8bb39-1011">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1012">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1012">Prototype</span></span>

```C
UINT tx_mutex_get(TX_MUTEX *mutex_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="8bb39-1013">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1013">Description</span></span>

<span data-ttu-id="8bb39-1014">Ta usługa próbuje uzyskać wyłączną własność określonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1014">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="8bb39-1015">Jeśli wątek wywołujący jest już właścicielem obiektu mutex, licznik wewnętrzny jest zwiększany i zwracany jest stan pomyślny.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1015">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="8bb39-1016">Jeśli element mutex jest własnością innego wątku, a ten wątek ma wyższy priorytet, a dziedziczenie priorytetów zostało określone w elemencie mutex Create, priorytet wątku o niższym priorytecie zostanie tymczasowo podniesiony do tego wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1016">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread’s priority will be temporarily raised to that of the calling thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1017">Priorytet wątku o niższym priorytecie będącego właścicielem obiektu mutex z priorityinheritance nigdy nie powinien być modyfikowany przez wątek zewnętrzny podczas własności obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1017">The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1018">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1018">Parameters</span></span>

- <span data-ttu-id="8bb39-1019">**mutex_ptr**: wskaźnik do wcześniej utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1019">**mutex_ptr**: Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="8bb39-1020">**WAIT_OPTION**: określa, jak działa usługa, jeśli element mutex jest już własnością innego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1020">**wait_option**: Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="8bb39-1021">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8bb39-1021">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8bb39-1022">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1022">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="8bb39-1023">**TX_WAIT_FOREVER**: (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1023">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="8bb39-1024">wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1024">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="8bb39-1025">Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1025">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8bb39-1026">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z inicjacji.*</span><span class="sxs-lookup"><span data-stu-id="8bb39-1026">*This is the only valid option if the service is called from Initialization.*</span></span>

    <span data-ttu-id="8bb39-1027">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu udostępnienia elementu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1027">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the mutex is available.</span></span>

    <span data-ttu-id="8bb39-1028">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1028">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1029">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1029">Return Values</span></span>

- <span data-ttu-id="8bb39-1030">**TX_SUCCESS**: (0x00) pomyślna operacja pobrania obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1030">**TX_SUCCESS**: (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="8bb39-1031">**TX_DELETED**: (0x01) element mutex został usunięty podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1031">**TX_DELETED**: (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8bb39-1032">**TX_NOT_AVAILABLE**: usługa (0x1D) nie może pobrać własności obiektu mutex w określonym czasie w celu oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1032">**TX_NOT_AVAILABLE**: (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="8bb39-1033">**TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1033">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8bb39-1034">TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1034">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="8bb39-1035">TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1035">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="8bb39-1036">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1036">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1037">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1037">Allowed From</span></span>

<span data-ttu-id="8bb39-1038">Inicjowanie i wątki oraz czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-1038">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1039">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1039">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1040">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1040">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1041">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1041">Example</span></span>

```C
TX_MUTEX     my_mutex;
UINT         status;

/* Obtain exclusive ownership of the mutex "my_mutex".
   If the mutex "my_mutex" is not available, suspend until it
   becomes available. */
status =  tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```
### <a name="see-also"></a><span data-ttu-id="8bb39-1042">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1042">See Also</span></span>

- <span data-ttu-id="8bb39-1043">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1043">tx_mutex_create</span></span>
- <span data-ttu-id="8bb39-1044">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1044">tx_mutex_delete</span></span>
- <span data-ttu-id="8bb39-1045">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1045">tx_mutex_info_get</span></span>
- <span data-ttu-id="8bb39-1046">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1046">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1047">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1047">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1048">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1048">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8bb39-1049">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1049">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="8bb39-1050">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1050">tx_mutex_info_get</span></span>

<span data-ttu-id="8bb39-1051">Pobierz informacje o muteksie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1051">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1052">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1052">Prototype</span></span>

```C
UINT tx_mutex_info_get(TX_MUTEX *mutex_ptr, CHAR **name,
                          ULONG *count, TX_THREAD **owner,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count, TX_MUTEX **next_mutex);
```
### <a name="description"></a><span data-ttu-id="8bb39-1053">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1053">Description</span></span>

<span data-ttu-id="8bb39-1054">Ta usługa pobiera informacje z określonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1054">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1055">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1055">Parameters</span></span>

- <span data-ttu-id="8bb39-1056">**mutex_ptr**: wskaźnik do bloku sterowania muteksem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1056">**mutex_ptr**: Pointer to mutex control block.</span></span>
- <span data-ttu-id="8bb39-1057">**name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1057">**name**: Pointer to destination for the pointer to the mutex’s name.</span></span>
- <span data-ttu-id="8bb39-1058">**Count**: wskaźnik do miejsca docelowego dla liczby własności obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1058">**count**: Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="8bb39-1059">**Owner**: wskaźnik do miejsca docelowego dla wskaźnika wątku będącego właścicielem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1059">**owner**: Pointer to destination for the owning thread’s pointer.</span></span>
- <span data-ttu-id="8bb39-1060">**first_suspended**: wskaźnik do elementu docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1060">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="8bb39-1061">**suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tym elemencie mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1061">**suspended_count**: Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="8bb39-1062">**next_mutex**: wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1062">**next_mutex**: Pointer to destination for the pointer of the next created mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1063">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1063">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1064">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1064">Return Values</span></span>

- <span data-ttu-id="8bb39-1065">**TX_SUCCESS**: (0X00) pomyślne pobieranie informacji o muteksie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1065">**TX_SUCCESS**: (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="8bb39-1066">TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1066">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1067">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1067">Allowed From</span></span>

<span data-ttu-id="8bb39-1068">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1068">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1069">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1069">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1070">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1070">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1071">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1071">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1072">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1072">See Also</span></span>

- <span data-ttu-id="8bb39-1073">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1073">tx_mutex_create</span></span>
- <span data-ttu-id="8bb39-1074">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1074">tx_mutex_delete</span></span>
- <span data-ttu-id="8bb39-1075">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1075">tx_mutex_get</span></span>
- <span data-ttu-id="8bb39-1076">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1076">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1077">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1077">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1078">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1078">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8bb39-1079">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1079">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="8bb39-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1080">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="8bb39-1081">Pobierz informacje o wydajności muteksu</span><span class="sxs-lookup"><span data-stu-id="8bb39-1081">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1082">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1082">Prototype</span></span>

```C
UINT tx_mutex_performance_info_get(TX_MUTEX *mutex_ptr, ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts,
       ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="8bb39-1083">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1083">Description</span></span>

<span data-ttu-id="8bb39-1084">Ta usługa pobiera informacje o wydajności dotyczące określonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1084">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1085">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_MUTEX_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1085">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1086">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1086">Parameters</span></span>

- <span data-ttu-id="8bb39-1087">**mutex_ptr**: wskaźnik do wcześniej utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1087">**mutex_ptr**: Pointer to previously created mutex.</span></span>
- <span data-ttu-id="8bb39-1088">Put **: wskaźnik** do miejsca docelowego dla liczby żądań PUT wykonanych dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1088">**puts**: Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="8bb39-1089">**Pobiera**: wskaźnik do miejsca docelowego dla liczby żądań GET wykonanych dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1089">**gets**: Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="8bb39-1090">**zawieszenia**: wskaźnik do miejsca docelowego dla liczby elementów mutex wątku dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1090">**suspensions**: Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="8bb39-1091">**limity czasu**: wskaźnik do miejsca docelowego dla liczby przekroczeń limitu czasu zawieszenia dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1091">**timeouts**: Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="8bb39-1092">**Inversions**: wskaźnik do miejsca docelowego dla liczby wersji priorytetu wątku dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1092">**inversions**: Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="8bb39-1093">**dziedziczenia**: wskaźnik do miejsca docelowego dla liczby operacji dziedziczenia priorytetu wątku dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1093">**inheritances**: Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1094">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1094">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1095">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1095">Return Values</span></span>

- <span data-ttu-id="8bb39-1096">**TX_SUCCESS**: (0x00) pobieranie pomyślnej wydajności obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1096">**TX_SUCCESS**: (0x00) Successful mutex performance get.</span></span> 
- <span data-ttu-id="8bb39-1097">**TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1097">**TX_PTR_ERROR**: (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="8bb39-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1098">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1099">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1099">Allowed From</span></span>

<span data-ttu-id="8bb39-1100">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1100">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1101">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1101">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1102">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1102">See Also</span></span>

- <span data-ttu-id="8bb39-1103">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1103">tx_mutex_create</span></span>
- <span data-ttu-id="8bb39-1104">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1104">tx_mutex_delete</span></span>
- <span data-ttu-id="8bb39-1105">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1105">tx_mutex_get</span></span>
- <span data-ttu-id="8bb39-1106">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1106">tx_mutex_info_get</span></span>
- <span data-ttu-id="8bb39-1107">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1107">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1108">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1108">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8bb39-1109">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1109">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="8bb39-1110">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1110">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="8bb39-1111">Pobierz informacje o wydajności systemu muteksu</span><span class="sxs-lookup"><span data-stu-id="8bb39-1111">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1112">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1112">Prototype</span></span>

```C
UINT  tx_mutex_performance_system_info_get(ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts,
        ULONG *inversions, ULONG *inheritances);
```
### <a name="description"></a><span data-ttu-id="8bb39-1113">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1113">Description</span></span>

<span data-ttu-id="8bb39-1114">Ta usługa pobiera informacje o wydajności wszystkich muteksów w systemie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1114">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1115">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_MUTEX_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1115">The ThreadX SMP library and application must be built with **TX_MUTEX_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1116">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1116">Parameters</span></span>

- <span data-ttu-id="8bb39-1117">Put **: wskaźnik** do miejsca docelowego dla łącznej liczby żądań PUT wykonanych dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1117">**puts**: Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="8bb39-1118">**Pobiera**: wskaźnik do miejsca docelowego dla łącznej liczby żądań GET wykonanych dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1118">**gets**: Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="8bb39-1119">**zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń elementu mutex wątku dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1119">**suspensions**: Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="8bb39-1120">**limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1120">**timeouts**: Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="8bb39-1121">**Inversions**: wskaźnik do miejsca docelowego dla łącznej liczby wersji priorytetu wątku dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1121">**inversions**: Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="8bb39-1122">**dziedziczenia**: wskaźnik do miejsca docelowego dla łącznej liczby operacji dziedziczenia priorytetu wątku dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1122">**inheritances**: Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1123">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1123">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1124">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1124">Return Values</span></span>

- <span data-ttu-id="8bb39-1125">**TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności systemu muteksu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1125">**TX_SUCCESS**: (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="8bb39-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1126">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1127">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1127">Allowed From</span></span>

<span data-ttu-id="8bb39-1128">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1128">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1129">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1129">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1130">See Also</span></span>

- <span data-ttu-id="8bb39-1131">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1131">tx_mutex_create</span></span>
- <span data-ttu-id="8bb39-1132">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1132">tx_mutex_delete</span></span>
- <span data-ttu-id="8bb39-1133">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1133">tx_mutex_get</span></span>
- <span data-ttu-id="8bb39-1134">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1134">tx_mutex_info_get</span></span>
- <span data-ttu-id="8bb39-1135">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1135">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1136">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1136">tx_mutex_prioritize</span></span>
- <span data-ttu-id="8bb39-1137">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1137">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="8bb39-1138">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1138">tx_mutex_prioritize</span></span>

<span data-ttu-id="8bb39-1139">Ustawianie priorytetów listy zawieszeń muteksu</span><span class="sxs-lookup"><span data-stu-id="8bb39-1139">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1140">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1140">Prototype</span></span>

```C
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-1141">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1141">Description</span></span>

<span data-ttu-id="8bb39-1142">Ta usługa umieszcza wątek o najwyższym priorytecie na własność obiektu mutex na początku listy zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1142">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="8bb39-1143">Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1143">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1144">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1144">Parameters</span></span> 

- <span data-ttu-id="8bb39-1145">**mutex_ptr**: wskaźnik do wcześniej utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1145">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1146">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1146">Return Values</span></span>

- <span data-ttu-id="8bb39-1147">**TX_SUCCESS**: (0x00) pomyślna priorytetyzacja obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1147">**TX_SUCCESS**: (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="8bb39-1148">TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1148">TX_MUTEX_ERROR: (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1149">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1149">Allowed From</span></span>

<span data-ttu-id="8bb39-1150">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1150">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1151">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1151">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1152">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1152">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1153">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1153">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1154">See Also</span></span>

- <span data-ttu-id="8bb39-1155">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1155">tx_mutex_create</span></span>
- <span data-ttu-id="8bb39-1156">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1156">tx_mutex_delete</span></span>
- <span data-ttu-id="8bb39-1157">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1157">tx_mutex_get</span></span>
- <span data-ttu-id="8bb39-1158">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1158">tx_mutex_info_get</span></span>
- <span data-ttu-id="8bb39-1159">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1159">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1160">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1160">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1161">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1161">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="8bb39-1162">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1162">tx_mutex_put</span></span>

<span data-ttu-id="8bb39-1163">Zwolnij własność elementu mutex</span><span class="sxs-lookup"><span data-stu-id="8bb39-1163">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1164">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1164">Prototype</span></span>

```C
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-1165">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1165">Description</span></span>

<span data-ttu-id="8bb39-1166">Ta usługa zmniejsza liczbę własności określonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1166">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="8bb39-1167">Jeśli liczba własności wynosi zero, element mutex zostanie udostępniony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1167">If the ownership count is zero, the mutex is made available.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1168">W przypadku wybrania dziedziczenia priorytetu podczas tworzenia obiektu mutex priorytet zwalnianego wątku zostanie przywrócony do priorytetu, który miał po raz pierwszy uzyskać własność obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1168">If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex.</span></span> <span data-ttu-id="8bb39-1169">Wszystkie inne zmiany priorytetu w wątku zwalniania mogą być cofnięte.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1169">Any other priority changes made to the releasing thread during ownership of the mutex may be undone.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1170">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1170">Parameters</span></span>

- <span data-ttu-id="8bb39-1171">**mutex_ptr**: wskaźnik do wcześniej utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1171">**mutex_ptr**: Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1172">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1172">Return Values</span></span>

- <span data-ttu-id="8bb39-1173">**TX_SUCCESS**: (0X00) pomyślne wydanie muteksu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1173">**TX_SUCCESS**: (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="8bb39-1174">**TX_NOT_OWNED**: (0X1E) mutex nie należy do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1174">**TX_NOT_OWNED**: (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="8bb39-1175">TX_MUTEX_ERROR: (0x1C) Nieprawidłowy wskaźnik do elementu MUTEX.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1175">TX_MUTEX_ERROR: (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="8bb39-1176">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1176">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1177">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1177">Allowed From</span></span>

<span data-ttu-id="8bb39-1178">Inicjowanie i wątki oraz czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-1178">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1179">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1179">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1180">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1180">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1181">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1181">Example</span></span>

```C
TX_MUTEX         my_mutex;
UINT             status;
/* Release ownership of "my_mutex." */
status =  tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
   count has been decremented and if zero, released. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-1182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1182">See Also</span></span>

- <span data-ttu-id="8bb39-1183">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1183">tx_mutex_create</span></span>
- <span data-ttu-id="8bb39-1184">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1184">tx_mutex_delete</span></span>
- <span data-ttu-id="8bb39-1185">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1185">tx_mutex_get</span></span>
- <span data-ttu-id="8bb39-1186">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1186">tx_mutex_info_get</span></span>
- <span data-ttu-id="8bb39-1187">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1187">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1188">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1188">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1189">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1189">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="8bb39-1190">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1190">tx_queue_create</span></span>

<span data-ttu-id="8bb39-1191">Utwórz kolejkę komunikatów</span><span class="sxs-lookup"><span data-stu-id="8bb39-1191">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1192">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1192">Prototype</span></span>

```c
UINT tx_queue_create(TX_QUEUE *queue_ptr, CHAR *name_ptr,
                          UINT message_size,
                          VOID *queue_start, ULONG queue_size);
```
### <a name="description"></a><span data-ttu-id="8bb39-1193">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1193">Description</span></span>

<span data-ttu-id="8bb39-1194">Ta usługa tworzy kolejkę komunikatów, która jest zwykle używana do komunikacji międzywątkowej.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1194">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="8bb39-1195">Całkowita liczba komunikatów jest obliczana na podstawie określonego rozmiaru komunikatu i całkowitej liczby bajtów w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1195">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1196">Jeśli łączna liczba bajtów określona w obszarze pamięci kolejki nie jest równo podzielna przez określony rozmiar komunikatu, pozostałe bajty w obszarze pamięci nie są używane.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1196">If the total number of bytes specified in the queue’s memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1197">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1197">Parameters</span></span>

- <span data-ttu-id="8bb39-1198">**queue_ptr**: wskaźnik do bloku sterowania kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1198">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="8bb39-1199">**name_ptr**: wskaźnik na nazwę kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1199">**name_ptr**: Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="8bb39-1200">**message_size**: Określa rozmiar każdej wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1200">**message_size**: Specifies the size of each message in the queue.</span></span> <span data-ttu-id="8bb39-1201">Rozmiary komunikatów mieszczą się w zakresie od 1 32-bitowego wyrazu do 16 32-bitowych wyrazów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1201">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="8bb39-1202">Prawidłowe opcje rozmiaru komunikatu to wartości numeryczne z przestawu od 1 do 16 włącznie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1202">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="8bb39-1203">**queue_start**: adres początkowy kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1203">**queue_start**: Starting address of the message queue.</span></span> <span data-ttu-id="8bb39-1204">Adres początkowy musi być wyrównany do rozmiaru typu danych ULONG.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1204">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="8bb39-1205">**queue_size**: całkowita liczba bajtów dostępnych dla kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1205">**queue_size**: Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1206">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1206">Return Values</span></span>

- <span data-ttu-id="8bb39-1207">**TX_SUCCESS**: (0X00) pomyślne utworzenie kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1207">**TX_SUCCESS**: (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="8bb39-1208">TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1208">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="8bb39-1209">Wskaźnik ma wartość NULL lub kolejka została już utworzona.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1209">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="8bb39-1210">TX_PTR_ERROR: (0x03) nieprawidłowy adres początkowy kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1210">TX_PTR_ERROR: (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="8bb39-1211">TX_SIZE_ERROR: (0x05) rozmiar kolejki komunikatów jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1211">TX_SIZE_ERROR: (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="8bb39-1212">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1212">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1213">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1213">Allowed From</span></span>

<span data-ttu-id="8bb39-1214">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-1214">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1215">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1215">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1216">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1216">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1217">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1217">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1218">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1218">See Also</span></span>

- <span data-ttu-id="8bb39-1219">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1219">tx_queue_delete</span></span>
- <span data-ttu-id="8bb39-1220">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1220">tx_queue_flush</span></span>
- <span data-ttu-id="8bb39-1221">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1221">tx_queue_front_send</span></span>
- <span data-ttu-id="8bb39-1222">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1222">tx_queue_info_get</span></span>
- <span data-ttu-id="8bb39-1223">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1223">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1224">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1224">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1225">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1225">tx_queue_prioritize</span></span>
- <span data-ttu-id="8bb39-1226">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1226">tx_queue_receive</span></span>
- <span data-ttu-id="8bb39-1227">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1227">tx_queue_send</span></span>
- <span data-ttu-id="8bb39-1228">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1228">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="8bb39-1229">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1229">tx_queue_delete</span></span>

<span data-ttu-id="8bb39-1230">Usuń kolejkę komunikatów</span><span class="sxs-lookup"><span data-stu-id="8bb39-1230">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1231">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1231">Prototype</span></span>

```C
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-1232">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1232">Description</span></span>

<span data-ttu-id="8bb39-1233">Ta usługa usuwa określoną kolejkę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1233">This service deletes the specified message queue.</span></span> <span data-ttu-id="8bb39-1234">Wszystkie wątki zawieszają się, dopóki komunikat z tej kolejki zostanie wznowiony i nastąpi TX_DELETED stanu powrotu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1234">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1235">Aplikacja musi upewnić się, że wszystkie wywołania zwrotne powiadomień o wysłaniu dla tej kolejki zostaną zakończone (lub wyłączone) przed usunięciem kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1235">The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue.</span></span> <span data-ttu-id="8bb39-1236">Ponadto aplikacja musi uniemożliwić wszelkie przyszłe użycie usuniętej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1236">In addition, the application must prevent any future use of a deleted queue.</span></span>

<span data-ttu-id="8bb39-1237">*Jest również odpowiedzialna za zarządzanie obszarem pamięci skojarzonym z kolejką, która jest dostępna po zakończeniu tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="8bb39-1237">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1238">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1238">Parameters</span></span> 

- <span data-ttu-id="8bb39-1239">**queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1239">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1240">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1240">Return Values</span></span>

- <span data-ttu-id="8bb39-1241">**TX_SUCCESS**: (0X00) pomyślne usunięcie kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1241">**TX_SUCCESS**: (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="8bb39-1242">TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1242">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="8bb39-1243">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1243">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1244">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1244">Allowed From</span></span>

<span data-ttu-id="8bb39-1245">Wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-1245">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1246">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1246">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1247">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1247">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1248">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1248">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1249">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1249">See Also</span></span>

- <span data-ttu-id="8bb39-1250">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1250">tx_queue_create</span></span>
- <span data-ttu-id="8bb39-1251">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1251">tx_queue_flush</span></span>
- <span data-ttu-id="8bb39-1252">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1252">tx_queue_front_send</span></span>
- <span data-ttu-id="8bb39-1253">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1253">tx_queue_info_get</span></span>
- <span data-ttu-id="8bb39-1254">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1254">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1255">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1255">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1256">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1256">tx_queue_prioritize</span></span>
- <span data-ttu-id="8bb39-1257">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1257">tx_queue_receive</span></span>
- <span data-ttu-id="8bb39-1258">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1258">tx_queue_send</span></span>
- <span data-ttu-id="8bb39-1259">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1259">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="8bb39-1260">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1260">tx_queue_flush</span></span>

<span data-ttu-id="8bb39-1261">Puste wiadomości w kolejce komunikatów</span><span class="sxs-lookup"><span data-stu-id="8bb39-1261">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1262">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1262">Prototype</span></span>

```C
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-1263">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1263">Description</span></span>

<span data-ttu-id="8bb39-1264">Ta usługa usuwa wszystkie komunikaty przechowywane w określonej kolejce komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1264">This service deletes all messages stored in the specified message queue.</span></span> <span data-ttu-id="8bb39-1265">Jeśli kolejka jest pełna, komunikaty wszystkich zawieszonych wątków są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1265">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="8bb39-1266">Każdy zawieszony wątek zostanie wznowiony ze stanem powrotu, który wskazuje, że wiadomość została wysłana pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1266">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="8bb39-1267">Jeśli kolejka jest pusta, ta usługa nie robi nic.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1267">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1268">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1268">Parameters</span></span> 

- <span data-ttu-id="8bb39-1269">**queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1269">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1270">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1270">Return Values</span></span>

- <span data-ttu-id="8bb39-1271">**TX_SUCCESS**: (0X00) pomyślne Opróżnianie kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1271">**TX_SUCCESS**: (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="8bb39-1272">TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1272">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1273">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1273">Allowed From</span></span>

<span data-ttu-id="8bb39-1274">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1274">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1275">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1275">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1276">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1276">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1277">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1277">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1278">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1278">See Also</span></span>

- <span data-ttu-id="8bb39-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1279">tx_queue_create</span></span>
- <span data-ttu-id="8bb39-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1280">tx_queue_delete</span></span>
- <span data-ttu-id="8bb39-1281">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1281">tx_queue_front_send</span></span>
- <span data-ttu-id="8bb39-1282">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1282">tx_queue_info_get</span></span>
- <span data-ttu-id="8bb39-1283">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1283">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="8bb39-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1286">tx_queue_receive</span></span>
- <span data-ttu-id="8bb39-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1287">tx_queue_send</span></span>
- <span data-ttu-id="8bb39-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="8bb39-1289">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1289">tx_queue_front_send</span></span>

<span data-ttu-id="8bb39-1290">Wyślij wiadomość na przednią kolejkę</span><span class="sxs-lookup"><span data-stu-id="8bb39-1290">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1291">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1291">Prototype</span></span>

```C
UINT tx_queue_front_send(TX_QUEUE *queue_ptr,
                           VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="8bb39-1292">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1292">Description</span></span>

<span data-ttu-id="8bb39-1293">Ta usługa wysyła komunikat do lokalizacji frontonu określonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1293">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="8bb39-1294">Wiadomość jest **kopiowana** na przód kolejki z obszaru pamięci określonego przez wskaźnik źródła.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1294">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1295">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1295">Parameters</span></span>

- <span data-ttu-id="8bb39-1296">**queue_ptr**: wskaźnik do bloku sterowania kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1296">**queue_ptr**: Pointer to a message queue control block.</span></span>
- <span data-ttu-id="8bb39-1297">**source_ptr**: wskaźnik do komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1297">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="8bb39-1298">**WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli kolejka komunikatów jest pełna.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1298">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="8bb39-1299">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8bb39-1299">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8bb39-1300">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1300">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="8bb39-1301">**TX_WAIT_FOREVER**: (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1301">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="8bb39-1302">wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1302">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="8bb39-1303">Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1303">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8bb39-1304">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.*</span><span class="sxs-lookup"><span data-stu-id="8bb39-1304">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="8bb39-1305">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, w którym znajduje się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1305">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="8bb39-1306">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na pokój w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1306">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1307">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1307">Return Values</span></span>

- <span data-ttu-id="8bb39-1308">**TX_SUCCESS**: (0X00) pomyślne wysłanie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1308">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="8bb39-1309">**TX_DELETED**: (0x01) Kolejka komunikatów została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1309">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8bb39-1310">**TX_QUEUE_FULL**: usługa (0x0B) nie może wysłać komunikatu, ponieważ kolejka była zapełniona przez czas oczekiwania przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1310">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="8bb39-1311">**TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1311">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8bb39-1312">TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1312">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="8bb39-1313">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik źródła komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1313">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="8bb39-1314">TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1314">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1315">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1315">Allowed From</span></span>

<span data-ttu-id="8bb39-1316">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1316">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1317">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1317">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1318">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1318">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1319">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1319">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1320">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1320">See Also</span></span>

- <span data-ttu-id="8bb39-1321">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1321">tx_queue_create</span></span>
- <span data-ttu-id="8bb39-1322">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1322">tx_queue_delete</span></span>
- <span data-ttu-id="8bb39-1323">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1323">tx_queue_flush</span></span>
- <span data-ttu-id="8bb39-1324">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1324">tx_queue_info_get</span></span>
- <span data-ttu-id="8bb39-1325">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1325">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1326">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1326">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1327">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1327">tx_queue_prioritize</span></span>
- <span data-ttu-id="8bb39-1328">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1328">tx_queue_receive</span></span>
- <span data-ttu-id="8bb39-1329">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1329">tx_queue_send</span></span>
- <span data-ttu-id="8bb39-1330">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1330">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="8bb39-1331">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1331">tx_queue_info_get</span></span>

<span data-ttu-id="8bb39-1332">Pobierz informacje o kolejce</span><span class="sxs-lookup"><span data-stu-id="8bb39-1332">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1333">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1333">Prototype</span></span>

```C
UINT tx_queue_info_get(TX_QUEUE *queue_ptr, CHAR **name,
        ULONG *enqueued, ULONG *available_storage
        TX_THREAD **first_suspended, ULONG *suspended_count,
        TX_QUEUE **next_queue);
```
### <a name="description"></a><span data-ttu-id="8bb39-1334">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1334">Description</span></span>

<span data-ttu-id="8bb39-1335">Ta usługa pobiera informacje o określonej kolejce komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1335">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1336">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1336">Parameters</span></span>

- <span data-ttu-id="8bb39-1337">**queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1337">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="8bb39-1338">**name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1338">**name**: Pointer to destination for the pointer to the queue’s name.</span></span>
- <span data-ttu-id="8bb39-1339">w **kolejce**: wskaźnik do miejsca docelowego dla liczby komunikatów znajdujących się obecnie w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1339">**enqueued**: Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="8bb39-1340">**available_storage**: wskaźnik do miejsca docelowego dla liczby komunikatów, dla których w kolejce znajduje się obecnie miejsce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1340">**available_storage**: Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="8bb39-1341">**first_suspended**: wskaźnik do elementu docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1341">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="8bb39-1342">**suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1342">**suspended_count**: Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="8bb39-1343">**next_queue**: wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1343">**next_queue**: Pointer to destination for the pointer of the next created queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1344">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1344">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1345">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1345">Return Values</span></span>

- <span data-ttu-id="8bb39-1346">**TX_SUCCESS**: (0x00) informacje o kolejce zakończone powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1346">**TX_SUCCESS**: (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="8bb39-1347">TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1347">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1348">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1348">Allowed From</span></span>

<span data-ttu-id="8bb39-1349">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1349">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1350">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1350">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1351">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1352">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1352">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1353">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1353">See Also</span></span>

- <span data-ttu-id="8bb39-1354">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1354">tx_queue_create</span></span>
- <span data-ttu-id="8bb39-1355">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1355">tx_queue_delete</span></span>
- <span data-ttu-id="8bb39-1356">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1356">tx_queue_flush</span></span>
- <span data-ttu-id="8bb39-1357">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1357">tx_queue_front_send</span></span>
- <span data-ttu-id="8bb39-1358">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1358">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1359">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1359">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1360">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1360">tx_queue_prioritize</span></span>
- <span data-ttu-id="8bb39-1361">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1361">tx_queue_receive</span></span>
- <span data-ttu-id="8bb39-1362">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1362">tx_queue_send</span></span>
- <span data-ttu-id="8bb39-1363">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1363">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="8bb39-1364">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1364">tx_queue_performance_info_get</span></span>

<span data-ttu-id="8bb39-1365">Pobierz informacje o wydajności kolejki</span><span class="sxs-lookup"><span data-stu-id="8bb39-1365">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1366">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1366">Prototype</span></span>

```C
UINT  tx_queue_performance_info_get(TX_QUEUE *queue_ptr,
        ULONG *messages_sent, ULONG *messages_received,
        ULONG *empty_suspensions, ULONG *full_suspensions,
        ULONG *full_errors, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="8bb39-1367">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1367">Description</span></span>

<span data-ttu-id="8bb39-1368">Ta usługa pobiera informacje o wydajności określonej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1368">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1369">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_QUEUE_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1369">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1370">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1370">Parameters</span></span>

- <span data-ttu-id="8bb39-1371">**queue_ptr**: wskaźnik do wcześniej utworzonej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1371">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="8bb39-1372">**messages_sent**: wskaźnik do miejsca docelowego dla liczby żądań wysłania wykonanych dla tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1372">**messages_sent**: Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="8bb39-1373">**messages_received**: wskaźnik do miejsca docelowego dla liczby żądań odbioru wykonanych dla tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1373">**messages_received**: Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="8bb39-1374">**empty_suspensions**: wskaźnik do miejsca docelowego dla liczby pustych zawieszeń kolejki w tej kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1374">**empty_suspensions**: Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="8bb39-1375">**full_suspensions**: wskaźnik do miejsca docelowego dla liczby pełnych zawieszeń kolejki w tej kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1375">**full_suspensions**: Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="8bb39-1376">**full_errors**: wskaźnik do miejsca docelowego dla liczby pełnych błędów kolejki w tej kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1376">**full_errors**: Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="8bb39-1377">**limity czasu**: wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia wątku w tej kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1377">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1378">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1378">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1379">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1379">Return Values</span></span>

- <span data-ttu-id="8bb39-1380">**TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1380">**TX_SUCCESS**: (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="8bb39-1381">**TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1381">**TX_PTR_ERROR**: (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="8bb39-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1382">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1383">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1383">Allowed From</span></span>

<span data-ttu-id="8bb39-1384">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1384">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1385">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1385">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1386">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1386">See Also</span></span>

- <span data-ttu-id="8bb39-1387">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1387">tx_queue_create</span></span>
- <span data-ttu-id="8bb39-1388">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1388">tx_queue_delete</span></span>
- <span data-ttu-id="8bb39-1389">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1389">tx_queue_flush</span></span>
- <span data-ttu-id="8bb39-1390">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1390">tx_queue_front_send</span></span>
- <span data-ttu-id="8bb39-1391">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1391">tx_queue_info_get</span></span>
- <span data-ttu-id="8bb39-1392">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1392">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1393">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1393">tx_queue_prioritize</span></span>
- <span data-ttu-id="8bb39-1394">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1394">tx_queue_receive</span></span>
- <span data-ttu-id="8bb39-1395">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1395">tx_queue_send</span></span>
- <span data-ttu-id="8bb39-1396">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1396">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="8bb39-1397">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1397">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="8bb39-1398">Pobierz informacje o wydajności systemu kolejkowania</span><span class="sxs-lookup"><span data-stu-id="8bb39-1398">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1399">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1399">Prototype</span></span>

```C
UINT  tx_queue_performance_system_info_get(ULONG *messages_sent,
        ULONG *messages_received, ULONG *empty_suspensions,
        ULONG *full_suspensions, ULONG *full_errors,
        ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="8bb39-1400">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1400">Description</span></span>

<span data-ttu-id="8bb39-1401">Ta usługa pobiera informacje o wydajności wszystkich kolejek w systemie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1401">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1402">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_QUEUE_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1402">The ThreadX SMP library and application must be built with **TX_QUEUE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1403">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1403">Parameters</span></span>

- <span data-ttu-id="8bb39-1404">**messages_sent**: wskaźnik do miejsca docelowego dla łącznej liczby żądań wysłania wykonanych na wszystkich kolejkach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1404">**messages_sent**: Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="8bb39-1405">**messages_received**: wskaźnik do miejsca docelowego dla łącznej liczby żądań odbioru wykonanych dla wszystkich kolejek.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1405">**messages_received**: Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="8bb39-1406">**empty_suspensions**: wskaźnik do miejsca docelowego dla łącznej liczby pustych zawieszeń kolejki we wszystkich kolejkach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1406">**empty_suspensions**: Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="8bb39-1407">**full_suspensions**: wskaźnik do miejsca docelowego dla łącznej liczby pełnych zawieszeń kolejki we wszystkich kolejkach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1407">**full_suspensions**: Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="8bb39-1408">**full_errors**: wskaźnik do miejsca docelowego dla łącznej liczby pełnych błędów kolejki dla wszystkich kolejek.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1408">**full_errors**: Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="8bb39-1409">**limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia wątku we wszystkich kolejkach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1409">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1410">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1410">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1411">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1411">Return Values</span></span>

- <span data-ttu-id="8bb39-1412">**TX_SUCCESS**: (0x00) pomyślna Kolejka wydajności systemu get.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1412">**TX_SUCCESS**: (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="8bb39-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1413">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1414">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1414">Allowed From</span></span>

<span data-ttu-id="8bb39-1415">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1415">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1416">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1416">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1417">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1417">See Also</span></span>

- <span data-ttu-id="8bb39-1418">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1418">tx_queue_create</span></span>
- <span data-ttu-id="8bb39-1419">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1419">tx_queue_delete</span></span>
- <span data-ttu-id="8bb39-1420">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1420">tx_queue_flush</span></span>
- <span data-ttu-id="8bb39-1421">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1421">tx_queue_front_send</span></span>
- <span data-ttu-id="8bb39-1422">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1422">tx_queue_info_get</span></span>
- <span data-ttu-id="8bb39-1423">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1423">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1424">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1424">tx_queue_prioritize</span></span>
- <span data-ttu-id="8bb39-1425">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1425">tx_queue_receive</span></span>
- <span data-ttu-id="8bb39-1426">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1426">tx_queue_send</span></span>
- <span data-ttu-id="8bb39-1427">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1427">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="8bb39-1428">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1428">tx_queue_prioritize</span></span>

<span data-ttu-id="8bb39-1429">Ustawianie priorytetu listy zawieszania kolejki</span><span class="sxs-lookup"><span data-stu-id="8bb39-1429">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1430">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1430">Prototype</span></span>

```C
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="8bb39-1431">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1431">Description</span></span>

<span data-ttu-id="8bb39-1432">Ta usługa umieszcza wątek o najwyższym priorytecie dla komunikatu (lub umieszcza komunikat) w tej kolejce na początku listy zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1432">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span> <span data-ttu-id="8bb39-1433">Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1433">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1434">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1434">Parameters</span></span> 

- <span data-ttu-id="8bb39-1435">**queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1435">**queue_ptr**: Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1436">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1436">Return Values</span></span>

- <span data-ttu-id="8bb39-1437">**TX_SUCCESS**: (0x00) pomyślna priorytetyzacja kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1437">**TX_SUCCESS**: (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="8bb39-1438">TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1438">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1439">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1439">Allowed From</span></span>

<span data-ttu-id="8bb39-1440">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1440">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1441">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1441">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1442">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1442">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1443">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1443">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1444">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1444">See Also</span></span>

- <span data-ttu-id="8bb39-1445">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1445">tx_queue_create</span></span>
- <span data-ttu-id="8bb39-1446">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1446">tx_queue_delete</span></span>
- <span data-ttu-id="8bb39-1447">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1447">tx_queue_flush</span></span>
- <span data-ttu-id="8bb39-1448">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1448">tx_queue_front_send</span></span>
- <span data-ttu-id="8bb39-1449">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1449">tx_queue_info_get</span></span>
- <span data-ttu-id="8bb39-1450">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1450">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1451">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1451">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1452">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1452">tx_queue_receive</span></span>
- <span data-ttu-id="8bb39-1453">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1453">tx_queue_send</span></span>
- <span data-ttu-id="8bb39-1454">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1454">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="8bb39-1455">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1455">tx_queue_receive</span></span>

<span data-ttu-id="8bb39-1456">Pobierz komunikat z kolejki komunikatów</span><span class="sxs-lookup"><span data-stu-id="8bb39-1456">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1457">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1457">Prototype</span></span>

```C
UINT tx_queue_receive(TX_QUEUE *queue_ptr,
                          VOID *destination_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="8bb39-1458">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1458">Description</span></span>

<span data-ttu-id="8bb39-1459">Ta usługa pobiera komunikat z określonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1459">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="8bb39-1460">Pobrany komunikat jest **kopiowany** z kolejki do obszaru pamięci określonego przez wskaźnik docelowy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1460">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="8bb39-1461">Ten komunikat zostanie następnie usunięty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1461">That message is then removed from the queue.</span></span>

> [!WARNING]
> <span data-ttu-id="8bb39-1462">Określony obszar pamięci docelowej musi być wystarczająco duży, aby pomieścić komunikat; oznacza to, że miejsce docelowe komunikatu wskazywane przez **destination_ptr** musi być co najmniej tak duże, jak rozmiar komunikatu dla tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1462">The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by **destination_ptr** must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="8bb39-1463">W przeciwnym razie, jeśli miejsce docelowe nie jest wystarczająco duże, uszkodzenie pamięci występuje w następującym obszarze pamięci.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1463">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1464">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1464">Parameters</span></span>

- <span data-ttu-id="8bb39-1465">**queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1465">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="8bb39-1466">**destination_ptr**: Lokalizacja lokalizacji, w której ma zostać skopiowana wiadomość.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1466">**destination_ptr**: Location of where to copy the message.</span></span>
- <span data-ttu-id="8bb39-1467">**WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli kolejka komunikatów jest pusta.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1467">**wait_option**: Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="8bb39-1468">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8bb39-1468">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8bb39-1469">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1469">**TX_NO_WAIT**: (0x00000000)</span></span> 
    - <span data-ttu-id="8bb39-1470">**TX_WAIT_FOREVER**: (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1470">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span> 
    - <span data-ttu-id="8bb39-1471">wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1471">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="8bb39-1472">Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1472">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8bb39-1473">Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1473">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>

    <span data-ttu-id="8bb39-1474">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu udostępnienia komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1474">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>

    <span data-ttu-id="8bb39-1475">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na komunikat.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1475">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1476">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1476">Return Values</span></span>

- <span data-ttu-id="8bb39-1477">**TX_SUCCESS**: (0X00) pomyślne pobranie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1477">**TX_SUCCESS**: (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="8bb39-1478">**TX_DELETED**: (0x01) Kolejka komunikatów została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1478">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8bb39-1479">**TX_QUEUE_EMPTY**: (0X0a) usługa nie mogła pobrać komunikatu, ponieważ kolejka była pusta przez czas oczekiwania przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1479">**TX_QUEUE_EMPTY**: (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="8bb39-1480">**TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1480">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8bb39-1481">TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1481">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="8bb39-1482">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik docelowy dla komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1482">TX_PTR_ERROR: (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="8bb39-1483">TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1483">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1484">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1484">Allowed From</span></span>

<span data-ttu-id="8bb39-1485">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1485">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1486">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1486">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1487">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1487">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1488">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1488">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1489">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1489">See Also</span></span>

- <span data-ttu-id="8bb39-1490">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1490">tx_queue_create</span></span>
- <span data-ttu-id="8bb39-1491">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1491">tx_queue_delete</span></span>
- <span data-ttu-id="8bb39-1492">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1492">tx_queue_flush</span></span>
- <span data-ttu-id="8bb39-1493">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1493">tx_queue_front_send</span></span>
- <span data-ttu-id="8bb39-1494">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1494">tx_queue_info_get</span></span>
- <span data-ttu-id="8bb39-1495">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1495">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1496">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1496">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1497">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1497">tx_queue_prioritize</span></span>
- <span data-ttu-id="8bb39-1498">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1498">tx_queue_send</span></span>
- <span data-ttu-id="8bb39-1499">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1499">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="8bb39-1500">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1500">tx_queue_send</span></span>

<span data-ttu-id="8bb39-1501">Wyślij komunikat do kolejki komunikatów</span><span class="sxs-lookup"><span data-stu-id="8bb39-1501">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1502">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1502">Prototype</span></span>

```C
UINT tx_queue_send(TX_QUEUE *queue_ptr,
                          VOID *source_ptr, ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="8bb39-1503">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1503">Description</span></span>

<span data-ttu-id="8bb39-1504">Ta usługa wysyła komunikat do określonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1504">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="8bb39-1505">Wysłany komunikat jest **kopiowany** do kolejki z obszaru pamięci określonego przez wskaźnik źródła.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1505">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1506">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1506">Parameters</span></span>

- <span data-ttu-id="8bb39-1507">**queue_ptr**: wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1507">**queue_ptr**: Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="8bb39-1508">**source_ptr**: wskaźnik do komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1508">**source_ptr**: Pointer to the message.</span></span>
- <span data-ttu-id="8bb39-1509">**WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli kolejka komunikatów jest pełna.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1509">**wait_option**: Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="8bb39-1510">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8bb39-1510">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8bb39-1511">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1511">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="8bb39-1512">**TX_WAIT_FOREVER**: (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1512">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="8bb39-1513">wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1513">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="8bb39-1514">Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1514">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8bb39-1515">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.*</span><span class="sxs-lookup"><span data-stu-id="8bb39-1515">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="8bb39-1516">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, w którym znajduje się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1516">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>

    <span data-ttu-id="8bb39-1517">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na pokój w kolejce.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1517">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1518">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1518">Return Values</span></span>

- <span data-ttu-id="8bb39-1519">**TX_SUCCESS**: (0X00) pomyślne wysłanie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1519">**TX_SUCCESS**: (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="8bb39-1520">**TX_DELETED**: (0x01) Kolejka komunikatów została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1520">**TX_DELETED**: (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8bb39-1521">**TX_QUEUE_FULL**: usługa (0x0B) nie może wysłać komunikatu, ponieważ kolejka była zapełniona przez czas oczekiwania przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1521">**TX_QUEUE_FULL**: (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="8bb39-1522">**TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1522">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8bb39-1523">TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1523">TX_QUEUE_ERROR: (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="8bb39-1524">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik źródła komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1524">TX_PTR_ERROR: (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="8bb39-1525">TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1525">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1526">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1526">Allowed From</span></span>

<span data-ttu-id="8bb39-1527">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1527">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1528">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1528">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1529">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1529">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1530">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1530">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1531">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1531">See Also</span></span>

- <span data-ttu-id="8bb39-1532">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1532">tx_queue_create</span></span>
- <span data-ttu-id="8bb39-1533">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1533">tx_queue_delete</span></span>
- <span data-ttu-id="8bb39-1534">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1534">tx_queue_flush</span></span>
- <span data-ttu-id="8bb39-1535">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1535">tx_queue_front_send</span></span>
- <span data-ttu-id="8bb39-1536">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1536">tx_queue_info_get</span></span>
- <span data-ttu-id="8bb39-1537">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1537">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1538">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1538">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1539">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1539">tx_queue_prioritize</span></span>
- <span data-ttu-id="8bb39-1540">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1540">tx_queue_receive</span></span>
- <span data-ttu-id="8bb39-1541">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1541">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="8bb39-1542">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1542">tx_queue_send_notify</span></span> 

<span data-ttu-id="8bb39-1543">Powiadamiaj aplikację, gdy wiadomość jest wysyłana do kolejki</span><span class="sxs-lookup"><span data-stu-id="8bb39-1543">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1544">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1544">Prototype</span></span>

```C
UINT  tx_queue_send_notify(TX_QUEUE *queue_ptr,
        VOID (*queue_send_notify)(TX_QUEUE *));
```
### <a name="description"></a><span data-ttu-id="8bb39-1545">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1545">Description</span></span>

<span data-ttu-id="8bb39-1546">Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy komunikat zostanie wysłany do określonej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1546">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="8bb39-1547">Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1547">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="8bb39-1548">Wywołanie zwrotne powiadomienia o wysłaniu kolejki aplikacji nie może wywołać żadnego ThreadX interfejsu API SMP z opcją zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1548">The application’s queue send notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1549">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1549">Parameters</span></span> 

- <span data-ttu-id="8bb39-1550">**queue_ptr**: wskaźnik do wcześniej utworzonej kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1550">**queue_ptr**: Pointer to previously created queue.</span></span>
- <span data-ttu-id="8bb39-1551">**queue_send_notify**: wskaźnik do funkcji powiadomień o wysyłaniu do kolejki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1551">**queue_send_notify**: Pointer to application’s queue send notification function.</span></span> <span data-ttu-id="8bb39-1552">Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1552">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1553">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1553">Return Values</span></span>

- <span data-ttu-id="8bb39-1554">**TX_SUCCESS**: (0x00) pomyślna Rejestracja powiadomienia o wysłaniu kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1554">**TX_SUCCESS**: (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="8bb39-1555">TX_QUEUE_ERROR: (0x09) Nieprawidłowy wskaźnik kolejki.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1555">TX_QUEUE_ERROR: (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="8bb39-1556">TX_FEATURE_NOT_ENABLED: (0xFF) system został skompilowany z wyłączonymi funkcjami powiadomień.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1556">TX_FEATURE_NOT_ENABLED: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1557">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1557">Allowed From</span></span>

<span data-ttu-id="8bb39-1558">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1558">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1559">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1559">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1560">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1560">See Also</span></span>

- <span data-ttu-id="8bb39-1561">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1561">tx_queue_create</span></span>
- <span data-ttu-id="8bb39-1562">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1562">tx_queue_delete</span></span>
- <span data-ttu-id="8bb39-1563">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="8bb39-1563">tx_queue_flush</span></span>
- <span data-ttu-id="8bb39-1564">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1564">tx_queue_front_send</span></span>
- <span data-ttu-id="8bb39-1565">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1565">tx_queue_info_get</span></span>
- <span data-ttu-id="8bb39-1566">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1566">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1567">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1567">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1568">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1568">tx_queue_prioritize</span></span>
- <span data-ttu-id="8bb39-1569">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="8bb39-1569">tx_queue_receive</span></span>
- <span data-ttu-id="8bb39-1570">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="8bb39-1570">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="8bb39-1571">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1571">tx_semaphore_ceiling_put</span></span> 

<span data-ttu-id="8bb39-1572">Umieść wystąpienie w zliczaniu semafora z pułapem</span><span class="sxs-lookup"><span data-stu-id="8bb39-1572">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1573">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1573">Prototype</span></span>

```C
UINT  tx_semaphore_ceiling_put(TX_SEMAPHORE *semaphore_ptr,
        ULONG ceiling);
```
### <a name="description"></a><span data-ttu-id="8bb39-1574">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1574">Description</span></span>

<span data-ttu-id="8bb39-1575">Ta usługa umieszcza wystąpienie w określonym semaforze zliczania, który w rzeczywistości zwiększa semafor zliczania o jeden.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1575">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="8bb39-1576">Jeśli bieżąca wartość semafora zliczania jest większa lub równa określonej granicy, wystąpienie nie zostanie umieszczone i zostanie zwrócony błąd TX_CEILING_EXCEEDED.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1576">If the counting semaphore’s current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1577">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1577">Parameters</span></span> 

- <span data-ttu-id="8bb39-1578">**semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1578">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="8bb39-1579">**granica**: maksymalny limit dozwolony dla semafora (wartości z zakresu od 1 do 0xffffffff).</span><span class="sxs-lookup"><span data-stu-id="8bb39-1579">**ceiling**: Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1580">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1580">Return Values</span></span>

- <span data-ttu-id="8bb39-1581">**TX_SUCCESS**: (0x00) pomyślny pułap semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1581">**TX_SUCCESS**: (0x00) Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="8bb39-1582">**TX_CEILING_EXCEEDED**: (0x21) żądanie Put przekracza limit.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1582">**TX_CEILING_EXCEEDED**: (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="8bb39-1583">TX_INVALID_CEILING: (0x22) podano nieprawidłową wartość zero dla pułapu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1583">TX_INVALID_CEILING: (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="8bb39-1584">TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1584">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1585">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1585">Allowed From</span></span>

<span data-ttu-id="8bb39-1586">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1586">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1587">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1587">Example</span></span>

```c
TX_SEMAPHORE     my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
   that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
```
### <a name="see-also"></a><span data-ttu-id="8bb39-1588">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1588">See Also</span></span>

- <span data-ttu-id="8bb39-1589">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1589">tx_semaphore_create</span></span>
- <span data-ttu-id="8bb39-1590">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1590">tx_semaphore_delete</span></span>
- <span data-ttu-id="8bb39-1591">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1591">tx_semaphore_get</span></span>
- <span data-ttu-id="8bb39-1592">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1592">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8bb39-1593">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1593">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1594">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1594">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1595">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1595">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8bb39-1596">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1596">tx_semaphore_put</span></span>
- <span data-ttu-id="8bb39-1597">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1597">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="8bb39-1598">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1598">tx_semaphore_create</span></span>

<span data-ttu-id="8bb39-1599">Tworzenie semafora zliczania</span><span class="sxs-lookup"><span data-stu-id="8bb39-1599">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1600">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1600">Prototype</span></span>

```C
UINT tx_semaphore_create(TX_SEMAPHORE *semaphore_ptr,
                           CHAR *name_ptr, ULONG initial_count);
```
### <a name="description"></a><span data-ttu-id="8bb39-1601">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1601">Description</span></span>

<span data-ttu-id="8bb39-1602">Ta usługa tworzy semafor zliczania dla synchronizacji między wątkami.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1602">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="8bb39-1603">Początkowa liczba semaforów jest określana jako parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1603">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1604">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1604">Parameters</span></span> 

- <span data-ttu-id="8bb39-1605">**semaphore_ptr**: wskaźnik do bloku sterowania semaforem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1605">**semaphore_ptr**: Pointer to a semaphore control block.</span></span> 
- <span data-ttu-id="8bb39-1606">**name_ptr**: wskaźnik do nazwy semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1606">**name_ptr**: Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="8bb39-1607">**initial_count**: określa początkową liczbę dla tego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1607">**initial_count**: Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="8bb39-1608">Wartości prawne mieszczą się w zakresie od 0x00000000 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1608">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1609">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1609">Return Values</span></span>

- <span data-ttu-id="8bb39-1610">**TX_SUCCESS**: (0X00) pomyślne utworzenie semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1610">**TX_SUCCESS**: (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="8bb39-1611">TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1611">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="8bb39-1612">Wskaźnik ma wartość NULL lub semafor został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1612">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="8bb39-1613">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1613">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1614">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1614">Allowed From</span></span>

<span data-ttu-id="8bb39-1615">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-1615">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1616">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1616">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1617">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1617">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1618">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1618">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1619">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1619">See Also</span></span>

- <span data-ttu-id="8bb39-1620">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1620">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8bb39-1621">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1621">tx_semaphore_delete</span></span>
- <span data-ttu-id="8bb39-1622">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1622">tx_semaphore_get</span></span>
- <span data-ttu-id="8bb39-1623">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1623">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8bb39-1624">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1624">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1625">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1625">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1626">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1626">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8bb39-1627">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1627">tx_semaphore_put</span></span>
- <span data-ttu-id="8bb39-1628">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1628">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="8bb39-1629">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1629">tx_semaphore_delete</span></span>

<span data-ttu-id="8bb39-1630">Usuń semafor zliczania</span><span class="sxs-lookup"><span data-stu-id="8bb39-1630">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1631">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1631">Prototype</span></span>

```C
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-1632">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1632">Description</span></span>

<span data-ttu-id="8bb39-1633">Ta usługa usuwa określony semafor zliczania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1633">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="8bb39-1634">Wszystkie wątki zawieszone w trakcie oczekiwania na wystąpienie semafora są wznawiane i nadawane TX_DELETED stanie powrotu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1634">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1635">Aplikacja musi zapewnić ukończenie wywołania zwrotnego powiadomienia dla tego semafora (lub wyłączone) przed usunięciem semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1635">The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore.</span></span> <span data-ttu-id="8bb39-1636">Ponadto aplikacja musi uniemożliwić wszystkie przyszłe użycie usuniętego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1636">In addition, the application must prevent all future use of a deleted semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1637">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1637">Parameters</span></span> 

- <span data-ttu-id="8bb39-1638">**semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1638">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1639">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1639">Return Values</span></span>

- <span data-ttu-id="8bb39-1640">**TX_SUCCESS**: (0X00) pomyślne zliczanie usunięcia semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1640">**TX_SUCCESS**: (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="8bb39-1641">TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik zliczania semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1641">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="8bb39-1642">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1642">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1643">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1643">Allowed From</span></span>

<span data-ttu-id="8bb39-1644">Wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-1644">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1645">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1645">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1646">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1646">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1647">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1647">Example</span></span>

```C
TX_SEMAPHORE my_semaphore;
UINT         status;

/* Delete counting semaphore. Assume that the counting
   semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-1648">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1648">See Also</span></span>

- <span data-ttu-id="8bb39-1649">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1649">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8bb39-1650">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1650">tx_semaphore_create</span></span>
- <span data-ttu-id="8bb39-1651">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1651">tx_semaphore_get</span></span>
- <span data-ttu-id="8bb39-1652">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1652">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8bb39-1653">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1653">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1654">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1654">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1655">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1655">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8bb39-1656">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1656">tx_semaphore_put</span></span>
- <span data-ttu-id="8bb39-1657">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1657">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="8bb39-1658">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1658">tx_semaphore_get</span></span>

<span data-ttu-id="8bb39-1659">Pobierz wystąpienie z zliczania semafora</span><span class="sxs-lookup"><span data-stu-id="8bb39-1659">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1660">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1660">Prototype</span></span>

```C
UINT tx_semaphore_get(TX_SEMAPHORE *semaphore_ptr,
                          ULONG wait_option)
```
### <a name="description"></a><span data-ttu-id="8bb39-1661">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1661">Description</span></span>

<span data-ttu-id="8bb39-1662">Ta usługa Pobiera wystąpienie (pojedyncza liczba) z określonego semafora zliczania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1662">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="8bb39-1663">W związku z tym liczba określonych semaforów zostanie zmniejszona o jeden.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1663">As a result, the specified semaphore’s count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1664">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1664">Parameters</span></span>

- <span data-ttu-id="8bb39-1665">**semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora zliczania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1665">**semaphore_ptr**: Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="8bb39-1666">**WAIT_OPTION**: określa, w jaki sposób działa usługa, jeśli nie ma dostępnych wystąpień semafora; oznacza to, że liczba semaforów jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1666">**wait_option**: Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="8bb39-1667">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8bb39-1667">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="8bb39-1668">**TX_NO_WAIT**: (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1668">**TX_NO_WAIT**: (0x00000000)</span></span>
    - <span data-ttu-id="8bb39-1669">**TX_WAIT_FOREVER**: (0xffffffff)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1669">**TX_WAIT_FOREVER**: (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="8bb39-1670">wartość limitu czasu: (od 0x00000001 do 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="8bb39-1670">timeout value: (0x00000001 through 0xFFFFFFFE)</span></span>

    <span data-ttu-id="8bb39-1671">Wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1671">Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="8bb39-1672">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.*</span><span class="sxs-lookup"><span data-stu-id="8bb39-1672">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>

    <span data-ttu-id="8bb39-1673">Wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu dostępności wystąpienia semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1673">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span> 

    <span data-ttu-id="8bb39-1674">Wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na wystąpienie semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1674">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1675">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1675">Return Values</span></span>

- <span data-ttu-id="8bb39-1676">**TX_SUCCESS**: (0X00) pomyślne pobranie wystąpienia semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1676">**TX_SUCCESS**: (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="8bb39-1677">**TX_DELETED**: (0X01) zliczanie semafora został usunięty, gdy wątek został wstrzymany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1677">**TX_DELETED**: (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="8bb39-1678">**TX_NO_INSTANCE**: usługa (0x0D) nie może pobrać wystąpienia semafora zliczania (liczba semaforów wynosi zero w określonym czasie oczekiwania).</span><span class="sxs-lookup"><span data-stu-id="8bb39-1678">**TX_NO_INSTANCE**: (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="8bb39-1679">**TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1679">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8bb39-1680">TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik zliczania semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1680">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="8bb39-1681">TX_WAIT_ERROR: (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1681">TX_WAIT_ERROR: (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1682">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1682">Allowed From</span></span>

<span data-ttu-id="8bb39-1683">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1683">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1684">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1684">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1685">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1685">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1686">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1686">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1687">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1687">See Also</span></span>

- <span data-ttu-id="8bb39-1688">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1688">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8bb39-1689">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1689">tx_semaphore_create</span></span>
- <span data-ttu-id="8bb39-1690">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1690">tx_semahore_delete</span></span>
- <span data-ttu-id="8bb39-1691">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1691">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8bb39-1692">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1692">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1693">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1693">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8bb39-1694">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1694">tx_semaphore_put</span></span>
- <span data-ttu-id="8bb39-1695">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1695">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="8bb39-1696">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1696">tx_semaphore_info_get</span></span>

<span data-ttu-id="8bb39-1697">Pobierz informacje o semaforze</span><span class="sxs-lookup"><span data-stu-id="8bb39-1697">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1698">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1698">Prototype</span></span>

```C
UINT tx_semaphore_info_get(TX_SEMAPHORE *semaphore_ptr,
                          CHAR **name, ULONG *current_value,
                          TX_THREAD **first_suspended,
                          ULONG *suspended_count,
                          TX_SEMAPHORE **next_semaphore)
```
### <a name="description"></a><span data-ttu-id="8bb39-1699">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1699">Description</span></span>

<span data-ttu-id="8bb39-1700">Ta usługa pobiera informacje o określonym semaforze.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1700">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1701">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1701">Parameters</span></span>

- <span data-ttu-id="8bb39-1702">**semaphore_ptr**: wskaźnik do bloku sterowania semaforem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1702">**semaphore_ptr**: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="8bb39-1703">**name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1703">**name**: Pointer to destination for the pointer to the semaphore’s name.</span></span>
- <span data-ttu-id="8bb39-1704">**current_value**: wskaźnik do miejsca docelowego dla licznika bieżącego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1704">**current_value**: Pointer to destination for the current semaphore’s count.</span></span>
- <span data-ttu-id="8bb39-1705">**first_suspended**: wskaźnik do elementu docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1705">**first_suspended**: Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="8bb39-1706">**suspended_count**: wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tym semaforze.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1706">**suspended_count**: Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="8bb39-1707">**next_semaphore**: wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1707">**next_semaphore**: Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1708">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1708">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1709">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1709">Return Values</span></span>

- <span data-ttu-id="8bb39-1710">**TX_SUCCESS**: (0X00) pomyślne pobranie informacji semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1710">**TX_SUCCESS**: (0x00) Successful semaphore information retrieval.</span></span>
- <span data-ttu-id="8bb39-1711">TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1711">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1712">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1712">Allowed From</span></span>

<span data-ttu-id="8bb39-1713">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1713">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1714">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1714">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1715">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1715">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1716">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1716">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1717">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1717">See Also</span></span>

- <span data-ttu-id="8bb39-1718">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1718">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8bb39-1719">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1719">tx_semaphore_create</span></span>
- <span data-ttu-id="8bb39-1720">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1720">tx_semaphore_delete</span></span>
- <span data-ttu-id="8bb39-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="8bb39-1722">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1722">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1723">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1723">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1724">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1724">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8bb39-1725">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1725">tx_semaphore_put</span></span>
- <span data-ttu-id="8bb39-1726">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1726">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="8bb39-1727">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1727">tx_semaphore_performance_info_get</span></span> 

<span data-ttu-id="8bb39-1728">Pobierz informacje o wydajności semafora</span><span class="sxs-lookup"><span data-stu-id="8bb39-1728">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1729">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1729">Prototype</span></span>

```C
UINT  tx_semaphore_performance_info_get(TX_SEMAPHORE *semaphore_ptr,
        ULONG *puts, ULONG *gets,
        ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="8bb39-1730">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1730">Description</span></span>

<span data-ttu-id="8bb39-1731">Ta usługa pobiera informacje o wydajności dotyczące określonego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1731">This service retrieves performance information about the specified semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="8bb39-1732">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1732">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1733">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1733">Parameters</span></span>

- <span data-ttu-id="8bb39-1734">**semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1734">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="8bb39-1735">Put **: wskaźnik** do miejsca docelowego dla liczby żądań PUT wykonanych dla tego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1735">**puts**: Pointer to destination for the number of put requests performed on this semaphore.</span></span>
- <span data-ttu-id="8bb39-1736">**Pobiera**: wskaźnik do miejsca docelowego dla liczby żądań GET wykonanych dla tego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1736">**gets**: Pointer to destination for the number of get requests performed on this semaphore.</span></span>
- <span data-ttu-id="8bb39-1737">**zawieszenia**: wskaźnik do miejsca docelowego dla liczby zawieszeń wątku w tym semaforze.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1737">**suspensions**: Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
- <span data-ttu-id="8bb39-1738">**limity czasu**: wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia wątku dla tego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1738">**timeouts**: Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1739">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1739">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1740">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1740">Return Values</span></span>

- <span data-ttu-id="8bb39-1741">**TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1741">**TX_SUCCESS**: (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="8bb39-1742">**TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1742">**TX_PTR_ERROR**: (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="8bb39-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1743">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1744">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1744">Allowed From</span></span>

<span data-ttu-id="8bb39-1745">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1745">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1746">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1746">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1747">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1747">See Also</span></span>

- <span data-ttu-id="8bb39-1748">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1748">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8bb39-1749">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1749">tx_semaphore_create</span></span>
- <span data-ttu-id="8bb39-1750">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1750">tx_semaphore_delete</span></span>
- <span data-ttu-id="8bb39-1751">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1751">tx_semaphore_get</span></span>
- <span data-ttu-id="8bb39-1752">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1752">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8bb39-1753">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1753">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1754">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1754">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8bb39-1755">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1755">tx_semaphore_put</span></span>
- <span data-ttu-id="8bb39-1756">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1756">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="8bb39-1757">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1757">tx_semaphore_performance_system_info_get</span></span> 

<span data-ttu-id="8bb39-1758">Pobierz informacje o wydajności systemu semafora</span><span class="sxs-lookup"><span data-stu-id="8bb39-1758">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1759">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1759">Prototype</span></span>

```C
UINT tx_semaphore_performance_system_info_get(ULONG *puts,
       ULONG *gets, ULONG *suspensions, ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="8bb39-1760">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1760">Description</span></span>

<span data-ttu-id="8bb39-1761">Ta usługa pobiera informacje o wydajności dotyczące wszystkich semaforów w systemie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1761">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1762">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1762">The ThreadX SMP library and application must be built with **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1763">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1763">Parameters</span></span>

- <span data-ttu-id="8bb39-1764">Put **: wskaźnik** do miejsca docelowego dla łącznej liczby żądań PUT wykonanych na wszystkich semaforach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1764">**puts**: Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="8bb39-1765">**Pobiera**: wskaźnik do miejsca docelowego dla łącznej liczby żądań GET wykonanych na wszystkich semaforach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1765">**gets**: Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="8bb39-1766">**zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń wątku na wszystkich semaforach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1766">**suspensions**: Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="8bb39-1767">**limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia wątku dla wszystkich semaforów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1767">**timeouts**: Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1768">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1768">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1769">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1769">Return Values</span></span>

- <span data-ttu-id="8bb39-1770">TX_SUCCESS: (0x00) pomyślne pobieranie wydajności systemu semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1770">TX_SUCCESS: (0x00) Successful semaphore system performance get.</span></span>
- <span data-ttu-id="8bb39-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1771">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1772">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1772">Allowed From</span></span>

<span data-ttu-id="8bb39-1773">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1773">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1774">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1774">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1775">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1775">See Also</span></span>

- <span data-ttu-id="8bb39-1776">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1776">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8bb39-1777">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1777">tx_semaphore_create</span></span>
- <span data-ttu-id="8bb39-1778">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1778">tx_semaphore_delete</span></span>
- <span data-ttu-id="8bb39-1779">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1779">tx_semaphore_get</span></span>
- <span data-ttu-id="8bb39-1780">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1780">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8bb39-1781">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1781">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1782">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1782">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8bb39-1783">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1783">tx_semaphore_put</span></span>
- <span data-ttu-id="8bb39-1784">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1784">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="8bb39-1785">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1785">tx_semaphore_prioritize</span></span>

<span data-ttu-id="8bb39-1786">Ustawianie priorytetu listy zawieszania semafora</span><span class="sxs-lookup"><span data-stu-id="8bb39-1786">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1787">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1787">Prototype</span></span>

```C
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-1788">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1788">Description</span></span>

<span data-ttu-id="8bb39-1789">Ta usługa umieszcza wątek o najwyższym priorytecie w przypadku wystąpienia semafora na początku listy zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1789">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="8bb39-1790">Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1790">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1791">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1791">Parameters</span></span> 

- <span data-ttu-id="8bb39-1792">**semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1792">**semaphore_ptr**: Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1793">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1793">Return Values</span></span>

- <span data-ttu-id="8bb39-1794">**TX_SUCCESS**: (0x00) pomyślna priorytetyzacja semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1794">**TX_SUCCESS**: (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="8bb39-1795">TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik zliczania semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1795">TX_SEMAPHORE_ERROR: (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1796">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1796">Allowed From</span></span>

<span data-ttu-id="8bb39-1797">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1797">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1798">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1798">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1799">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1799">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1800">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1800">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1801">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1801">See Also</span></span>

- <span data-ttu-id="8bb39-1802">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1802">tx_semaphore_create</span></span>
- <span data-ttu-id="8bb39-1803">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1803">tx_semaphore_delete</span></span>
- <span data-ttu-id="8bb39-1804">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1804">tx_semaphore_get</span></span>
- <span data-ttu-id="8bb39-1805">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1805">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8bb39-1806">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1806">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="8bb39-1807">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1807">tx_semaphore_put</span></span>

<span data-ttu-id="8bb39-1808">Umieść wystąpienie w zliczaniu semafora</span><span class="sxs-lookup"><span data-stu-id="8bb39-1808">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1809">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1809">Prototype</span></span>

```C
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-1810">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1810">Description</span></span>

<span data-ttu-id="8bb39-1811">Ta usługa umieszcza wystąpienie w określonym semaforze zliczania, który w rzeczywistości zwiększa semafor zliczania o jeden.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1811">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1812">Jeśli ta usługa jest wywoływana, gdy semafor ma wszystkie (OxFFFFFFFF), Nowa operacja Put spowoduje, że semafor zostanie zresetowany do zera.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1812">If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1813">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1813">Parameters</span></span>

- <span data-ttu-id="8bb39-1814">**semaphore_ptr**: wskaźnik do wcześniej utworzonego bloku sterowania semaforem zliczania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1814">**semaphore_ptr**: Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1815">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1815">Return Values</span></span>

- <span data-ttu-id="8bb39-1816">**TX_SUCCESS**: (0X00) pomyślne umieszczenie semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1816">**TX_SUCCESS**: (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="8bb39-1817">TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik do zliczania semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1817">TX_SEMAPHORE_ERROR: (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1818">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1818">Allowed From</span></span>

<span data-ttu-id="8bb39-1819">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1819">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1820">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1820">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1821">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1821">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1822">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1822">Example</span></span>

```C
TX_SEMAPHORE     my_semaphore;
UINT             status;

/* Increment the counting semaphore "my_semaphore." */
status =  tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
   been incremented. Of course, if a thread was waiting,
   it was given the semaphore instance and resumed. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-1823">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1823">See Also</span></span>

- <span data-ttu-id="8bb39-1824">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1824">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8bb39-1825">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1825">tx_semaphore_create</span></span>
- <span data-ttu-id="8bb39-1826">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1826">tx_semaphore_delete</span></span>
- <span data-ttu-id="8bb39-1827">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1827">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8bb39-1828">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1828">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1829">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1829">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1830">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1830">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8bb39-1831">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1831">tx_semaphore_get</span></span>
- <span data-ttu-id="8bb39-1832">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1832">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="8bb39-1833">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1833">tx_semaphore_put_notify</span></span>

<span data-ttu-id="8bb39-1834">Powiadamiaj aplikację po umieszczeniu semafora</span><span class="sxs-lookup"><span data-stu-id="8bb39-1834">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1835">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1835">Prototype</span></span>

```C
UINT  tx_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr,
        VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```
### <a name="description"></a><span data-ttu-id="8bb39-1836">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1836">Description</span></span>

<span data-ttu-id="8bb39-1837">Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy określony semafor jest umieszczony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1837">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="8bb39-1838">Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1838">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="8bb39-1839">Wywołanie zwrotne powiadomienia semafora aplikacji nie może wywołać żadnego ThreadXego interfejsu API SMP z opcją zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1839">The application’s semaphore notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1840">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1840">Parameters</span></span> 

- <span data-ttu-id="8bb39-1841">**semaphore_ptr**: wskaźnik do wcześniej utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1841">**semaphore_ptr**: Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="8bb39-1842">**semaphore_put_notify**: wskaźnik do funkcji powiadamiania o wykorzystaniu semafora aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1842">**semaphore_put_notify**: Pointer to application’s semaphore put notification function.</span></span> <span data-ttu-id="8bb39-1843">Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1843">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1844">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1844">Return Values</span></span>

- <span data-ttu-id="8bb39-1845">**TX_SUCCESS**: (0x00) pomyślna Rejestracja powiadomienia o wprowadzeniu semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1845">**TX_SUCCESS**: (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="8bb39-1846">TX_SEMAPHORE_ERROR: (0x0C) Nieprawidłowy wskaźnik semafora.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1846">TX_SEMAPHORE_ERROR: (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="8bb39-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) system został skompilowany z wyłączonymi funkcjami powiadomień.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1847">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1848">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1848">Allowed From</span></span>

<span data-ttu-id="8bb39-1849">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1849">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1850">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1850">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1851">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1851">See Also</span></span>

- <span data-ttu-id="8bb39-1852">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1852">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="8bb39-1853">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1853">tx_semaphore_create</span></span>
- <span data-ttu-id="8bb39-1854">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1854">tx_semaphore_delete</span></span>
- <span data-ttu-id="8bb39-1855">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1855">tx_semaphore_get</span></span>
- <span data-ttu-id="8bb39-1856">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1856">tx_semaphore_info_get</span></span>
- <span data-ttu-id="8bb39-1857">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1857">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1858">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1858">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1859">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="8bb39-1859">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="8bb39-1860">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="8bb39-1860">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="8bb39-1861">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1861">tx_thread_create</span></span>

<span data-ttu-id="8bb39-1862">Utwórz wątek aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-1862">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1863">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1863">Prototype</span></span>

```C
UINT tx_thread_create(TX_THREAD *thread_ptr,
                          CHAR *name_ptr, VOID (*entry_function)(ULONG),
                          ULONG entry_input, VOID *stack_start,
                          ULONG stack_size, UINT priority,
                          UINT preempt_threshold, ULONG time_slice,
                          UINT auto_start);
```
### <a name="description"></a><span data-ttu-id="8bb39-1864">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1864">Description</span></span>

<span data-ttu-id="8bb39-1865">Ta usługa tworzy wątek aplikacji, który uruchamia wykonywanie w określonej funkcji wprowadzania zadań.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1865">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="8bb39-1866">Stos, priorytet, wartość progowa i wycinek czasu są wśród atrybutów określonych przez parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1866">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="8bb39-1867">Ponadto jest również określony początkowy stan wykonywania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1867">In addition, the initial execution state of the thread is also specified.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1868">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1868">Parameters</span></span>

- <span data-ttu-id="8bb39-1869">**thread_ptr**: wskaźnik do bloku sterującego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1869">**thread_ptr**: Pointer to a thread control block.</span></span>
- <span data-ttu-id="8bb39-1870">**name_ptr**: wskaźnik do nazwy wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1870">**name_ptr**: Pointer to the name of the thread.</span></span>
- <span data-ttu-id="8bb39-1871">**entry_function**: określa początkową funkcję C do wykonania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1871">**entry_function**: Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="8bb39-1872">Gdy wątek wraca z tej funkcji wejścia, jest on umieszczany w stanie ukończenia i zawieszony czasowo.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1872">When a thread returns from this entry function, it is placed in a completed state and suspended indefinitely.</span></span>
- <span data-ttu-id="8bb39-1873">**entry_input**: wartość 32-bitowa, która jest przesyłana do funkcji wejścia wątku podczas pierwszego wykonania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1873">**entry_input**: A 32-bit value that is passed to the thread’s entry function when it first executes.</span></span> <span data-ttu-id="8bb39-1874">Użycie tego danych wejściowych jest określane wyłącznie przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1874">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="8bb39-1875">**stack_start**: adres początkowy obszaru pamięci stosu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1875">**stack_start**: Starting address of the stack’s memory area.</span></span> 
- <span data-ttu-id="8bb39-1876">**stack_size**: liczba bajtów w obszarze pamięci stosu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1876">**stack_size**: Number bytes in the stack memory area.</span></span> <span data-ttu-id="8bb39-1877">Obszar stosu wątku musi być wystarczająco duży, aby obsługiwał jego najgorszą metodę użycia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1877">The thread’s stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="8bb39-1878">**priorytet**: liczbowy priorytet wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1878">**priority**: Numerical priority of thread.</span></span> <span data-ttu-id="8bb39-1879">Wartości prawne mieszczą się w zakresie od 0 do (TX_MAX_PRIORITES-1), gdzie wartość 0 reprezentuje najwyższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1879">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="8bb39-1880">**preempt_threshold**: najwyższy poziom priorytetu (od 0 do (TX_MAX_PRIORITIES-1)) wyłączono przechodzenie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1880">**preempt_threshold**: Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="8bb39-1881">Tylko priorytety wyższe niż ten poziom mogą przewagę tego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1881">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="8bb39-1882">Ta wartość nie może być większa niż określony priorytet.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1882">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="8bb39-1883">Wartość równa priorytetu wątku powoduje wyłączenie progu zastępujący.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1883">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="8bb39-1884">**time_slice**: liczba czasomierzy, przez jaką ten wątek może działać, zanim inne gotowe wątki o takim samym priorytecie mają szansę uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1884">**time_slice**: Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="8bb39-1885">Należy pamiętać, że użycie wartości progowej przekroczenia powoduje wyłączenie tworzenia wycinków czasu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1885">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="8bb39-1886">Dozwolone wartości wycinków czasu mieszczą się w zakresie od 1 do 0xFFFFFFFF (włącznie).</span><span class="sxs-lookup"><span data-stu-id="8bb39-1886">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="8bb39-1887">Wartość **TX_NO_TIME_SLICE** (wartość 0) powoduje wyłączenie wycinka czasu dla tego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1887">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="8bb39-1888">Korzystanie z wycinków czasu powoduje niewielkie obciążenie systemu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1888">Using time-slicing results in a slight amount of system overhead.</span></span> <span data-ttu-id="8bb39-1889">Ponieważ podział czasu jest przydatny tylko w przypadkach, gdy wiele wątków ma ten sam priorytet, wątki mające unikatowy priorytet nie powinny mieć przypisanego wycinka czasowego.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1889">Since time-slicing is only useful in cases where multiple threads share the same priority, threads having a unique priority should not be assigned a time-slice.</span></span>

- <span data-ttu-id="8bb39-1890">**auto_start**: określa, czy wątek zaczyna się od razu czy jest umieszczony w stanie wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1890">**auto_start**: Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="8bb39-1891">Opcje prawne są **TX_AUTO_START** (0x01) i **TX_DONT_START** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8bb39-1891">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="8bb39-1892">Jeśli TX_DONT_START jest określony, aplikacja musi później wywołać tx_thread_resume w celu uruchomienia wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1892">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1893">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1893">Return Values</span></span>

- <span data-ttu-id="8bb39-1894">**TX_SUCCESS**: (0X00) pomyślne utworzenie wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1894">**TX_SUCCESS**: (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="8bb39-1895">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik kontrolny wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1895">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="8bb39-1896">Wskaźnik ma wartość NULL lub wątek został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1896">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="8bb39-1897">TX_PTR_ERROR: (0x03) nieprawidłowy adres początkowy punktu wejścia lub obszar stosu jest nieprawidłowy, zazwyczaj ma wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1897">TX_PTR_ERROR: (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="8bb39-1898">TX_SIZE_ERROR: (0x05) rozmiar obszaru stosu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1898">TX_SIZE_ERROR: (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="8bb39-1899">Wątki muszą mieć co najmniej **TX_MINIMUM_STACK** bajtów do wykonania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1899">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="8bb39-1900">TX_PRIORITY_ERROR: (0x0F) nieprawidłowy priorytet wątku, który jest wartością spoza zakresu (od 0 do (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="8bb39-1900">TX_PRIORITY_ERROR: (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="8bb39-1901">TX_THRESH_ERROR: (0x18) określono nieprawidłowy preemptionthreshold.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1901">TX_THRESH_ERROR: (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="8bb39-1902">Ta wartość musi być prawidłowym priorytetem nie większym niż początkowy priorytet wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1902">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="8bb39-1903">TX_START_ERROR: (0x10) nieprawidłowy wybór autostartu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1903">TX_START_ERROR: (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="8bb39-1904">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1904">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1905">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1905">Allowed From</span></span>

<span data-ttu-id="8bb39-1906">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-1906">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1907">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1907">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1908">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-1908">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1909">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1909">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1910">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1910">See Also</span></span>

- <span data-ttu-id="8bb39-1911">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1911">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-1912">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1912">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-1913">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1913">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-1914">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1914">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-1915">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1915">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1916">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1916">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1917">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-1917">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-1918">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-1918">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-1919">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-1919">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-1920">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-1920">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-1921">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-1921">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-1922">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-1922">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-1923">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1923">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-1924">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-1924">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-1925">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-1925">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-1926">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-1926">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-1927">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-1927">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="8bb39-1928">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1928">tx_thread_delete</span></span>

<span data-ttu-id="8bb39-1929">Usuń wątek aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-1929">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1930">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1930">Prototype</span></span>

```C
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-1931">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1931">Description</span></span>

<span data-ttu-id="8bb39-1932">Ta usługa usuwa określony wątek aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1932">This service deletes the specified application thread.</span></span> <span data-ttu-id="8bb39-1933">Ponieważ określony wątek musi być w stanie zakończony lub zakończony, ta usługa nie może zostać wywołana z wątku próbującego usunąć sam siebie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1933">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-1934">Jest on odpowiedzialny za zarządzanie obszarem pamięci skojarzonym ze stosem wątku, który jest dostępny po zakończeniu tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1934">It is the application’s responsibility to manage the memory area associated with the thread’s stack, which is available after this service completes.</span></span> <span data-ttu-id="8bb39-1935">Ponadto aplikacja musi uniemożliwić korzystanie z usuniętego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1935">In addition, the application must prevent use of a deleted thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1936">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1936">Parameters</span></span>

- <span data-ttu-id="8bb39-1937">**thread_ptr**: wskaźnik do wcześniej utworzonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1937">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1938">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1938">Return Values</span></span>

- <span data-ttu-id="8bb39-1939">**TX_SUCCESS**: (0X00) pomyślne usunięcie wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1939">**TX_SUCCESS**: (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="8bb39-1940">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1940">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8bb39-1941">**TX_DELETE_ERROR**: (0X11) określony wątek nie jest w stanie przerwania lub zakończenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1941">**TX_DELETE_ERROR**: (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="8bb39-1942">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1942">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1943">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1943">Allowed From</span></span>

<span data-ttu-id="8bb39-1944">Wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-1944">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-1945">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1945">Preemption Possible</span></span>

<span data-ttu-id="8bb39-1946">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-1946">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1947">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1947">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-1948">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1948">See Also</span></span>

- <span data-ttu-id="8bb39-1949">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1949">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-1950">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1950">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-1951">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1951">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-1952">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1952">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-1953">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1953">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1954">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1954">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1955">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-1955">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-1956">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-1956">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-1957">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-1957">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-1958">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-1958">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-1959">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-1959">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-1960">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-1960">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-1961">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1961">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-1962">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-1962">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-1963">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-1963">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-1964">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-1964">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-1965">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-1965">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="8bb39-1966">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1966">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="8bb39-1967">Powiadamiaj aplikację przy wejściu i wyjściu wątku</span><span class="sxs-lookup"><span data-stu-id="8bb39-1967">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-1968">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-1968">Prototype</span></span>

```C
UINT  tx_thread_entry_exit_notify(TX_THREAD *thread_ptr,
        VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```
### <a name="description"></a><span data-ttu-id="8bb39-1969">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-1969">Description</span></span>

<span data-ttu-id="8bb39-1970">Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy określony wątek zostanie wprowadzony lub zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1970">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="8bb39-1971">Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1971">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="8bb39-1972">Wywołanie zwrotne powiadomienia o wejściu/wyjściu dla aplikacji nie może wywołać żadnego ThreadXego interfejsu API SMP z opcją zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1972">The application’s thread entry/exit notification callback is not allowed to call any ThreadX SMP API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-1973">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-1973">Parameters</span></span>

- <span data-ttu-id="8bb39-1974">**thread_ptr**: wskaźnik do wcześniej utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1974">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="8bb39-1975">**entry_exit_notify**: wskaźnik do funkcji powiadomienia o wejściu/wyjściu wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1975">**entry_exit_notify**: Pointer to application’s thread entry/exit notification function.</span></span> <span data-ttu-id="8bb39-1976">Drugi parametr funkcji powiadomień o wejściu/wyjściu określa, czy jest obecny wpis lub wyjście.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1976">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="8bb39-1977">Wartość TX_THREAD_ENTRY (0x00) wskazuje, że wątek został wprowadzony, podczas gdy wartość TX_THREAD_EXIT (0x01) wskazuje, że wątek został zakończony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1977">The value TX_THREAD_ENTRY (0x00) indicates the thread was entered, while the value TX_THREAD_EXIT (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="8bb39-1978">Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1978">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-1979">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-1979">Return Values</span></span>

- <span data-ttu-id="8bb39-1980">**TX_SUCCESS**: (0x00) pomyślna Rejestracja funkcji powiadomień o wejściu/wyjściu wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1980">**TX_SUCCESS**: (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="8bb39-1981">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1981">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="8bb39-1982">**TX_FEATURE_NOT_ENABLED (0xFF)** System został skompilowany z wyłączonymi funkcjami powiadomień.</span><span class="sxs-lookup"><span data-stu-id="8bb39-1982">**TX_FEATURE_NOT_ENABLED(0xFF)** The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-1983">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-1983">Allowed From</span></span>

<span data-ttu-id="8bb39-1984">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-1984">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-1985">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-1985">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="8bb39-1986">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-1986">See Also</span></span>

- <span data-ttu-id="8bb39-1987">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-1987">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-1988">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-1988">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-1989">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1989">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-1990">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-1990">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-1991">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1991">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-1992">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1992">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-1993">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-1993">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-1994">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-1994">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-1995">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-1995">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-1996">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-1996">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-1997">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-1997">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-1998">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-1998">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-1999">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-1999">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2000">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2000">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2001">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2001">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2002">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2002">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2003">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2003">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2004">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2004">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="8bb39-2005">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2005">tx_thread_identify</span></span>

<span data-ttu-id="8bb39-2006">Pobiera wskaźnik do aktualnie wykonywanego wątku</span><span class="sxs-lookup"><span data-stu-id="8bb39-2006">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2007">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2007">Prototype</span></span>

```C
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="8bb39-2008">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2008">Description</span></span>

<span data-ttu-id="8bb39-2009">Ta usługa zwraca wskaźnik do aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2009">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="8bb39-2010">Jeśli żaden wątek nie jest wykonywany, ta usługa zwraca wskaźnik o wartości null.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2010">If no thread is executing, this service returns a null pointer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2011">Jeśli ta usługa jest wywoływana przez funkcję ISR, wartość zwracana reprezentuje wątek uruchomiony przed wykonaniem procedury obsługi przerwań.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2011">If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2012">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2012">Parameters</span></span>

<span data-ttu-id="8bb39-2013">Brak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2013">None</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2014">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2014">Return Values</span></span>

- <span data-ttu-id="8bb39-2015">wskaźnik wątku: wskaźnik do aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2015">thread pointer: Pointer to the currently executing thread.</span></span> <span data-ttu-id="8bb39-2016">Jeśli żaden wątek nie jest wykonywany, wartość zwracana jest TX_NULL.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2016">If no thread is executing, the return value is TX_NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2017">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2017">Allowed From</span></span>

<span data-ttu-id="8bb39-2018">Wątki i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2018">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2019">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2019">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2020">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2020">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2021">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2021">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2022">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2022">See Also</span></span>

- <span data-ttu-id="8bb39-2023">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2023">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2024">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2024">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2025">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2025">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2026">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2026">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2027">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2027">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2028">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2028">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2029">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2029">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2030">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2030">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2031">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2031">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2032">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2032">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2033">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2033">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2034">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2034">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2035">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2035">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2036">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2036">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2037">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2037">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2038">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2038">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2039">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2039">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="8bb39-2040">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2040">tx_thread_info_get</span></span>

<span data-ttu-id="8bb39-2041">Pobierz informacje o wątku</span><span class="sxs-lookup"><span data-stu-id="8bb39-2041">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2042">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2042">Prototype</span></span>

```C
UINT tx_thread_info_get(TX_THREAD *thread_ptr, CHAR **name,
                          UINT *state, ULONG *run_count,
                          UINT *priority,
                          UINT *preemption_threshold,
                          ULONG *time_slice,
                          TX_THREAD **next_thread,
                          TX_THREAD **suspended_thread);
```
### <a name="description"></a><span data-ttu-id="8bb39-2043">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2043">Description</span></span>

<span data-ttu-id="8bb39-2044">Ta usługa pobiera informacje o określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2044">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2045">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2045">Parameters</span></span> 

- <span data-ttu-id="8bb39-2046">**thread_ptr**: wskaźnik do bloku sterowania wątkiem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2046">**thread_ptr**: Pointer to thread control block.</span></span>
- <span data-ttu-id="8bb39-2047">**name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2047">**name**: Pointer to destination for the pointer to the thread’s name.</span></span>
- <span data-ttu-id="8bb39-2048">**State**: wskaźnik do miejsca docelowego dla bieżącego stanu wykonywania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2048">**state**:  Pointer to destination for the thread’s current execution state.</span></span> <span data-ttu-id="8bb39-2049">Dopuszczalne są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="8bb39-2049">Possible values are as follows:</span></span>
    - <span data-ttu-id="8bb39-2050">**TX_READY**: (0x00)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2050">**TX_READY**: (0x00)</span></span>
    - <span data-ttu-id="8bb39-2051">**TX_COMPLETED**: (0x01)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2051">**TX_COMPLETED**: (0x01)</span></span>
    - <span data-ttu-id="8bb39-2052">**TX_TERMINATED**: (0x02)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2052">**TX_TERMINATED**: (0x02)</span></span>
    - <span data-ttu-id="8bb39-2053">**TX_SUSPENDED**: (0x03)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2053">**TX_SUSPENDED**: (0x03)</span></span>
    - <span data-ttu-id="8bb39-2054">**TX_SLEEP**: (0x04)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2054">**TX_SLEEP**: (0x04)</span></span>
    - <span data-ttu-id="8bb39-2055">**TX_QUEUE_SUSP**: (0x05)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2055">**TX_QUEUE_SUSP**: (0x05)</span></span>
    - <span data-ttu-id="8bb39-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2056">**TX_SEMAPHORE_SUSP**: (0x06)</span></span>
    - <span data-ttu-id="8bb39-2057">**TX_EVENT_FLAG**: (0x07)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2057">**TX_EVENT_FLAG**: (0x07)</span></span>
    - <span data-ttu-id="8bb39-2058">**TX_BLOCK_MEMORY**: (0x08)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2058">**TX_BLOCK_MEMORY**: (0x08)</span></span>
    - <span data-ttu-id="8bb39-2059">**TX_BYTE_MEMORY**: (0x09)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2059">**TX_BYTE_MEMORY**: (0x09)</span></span>
    - <span data-ttu-id="8bb39-2060">**TX_MUTEX_SUSP**: (0x0D)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2060">**TX_MUTEX_SUSP**: (0x0D)</span></span>

- <span data-ttu-id="8bb39-2061">**run_count**: wskaźnik do miejsca docelowego dla liczby uruchomień wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2061">**run_count**: Pointer to destination for the thread’s run count.</span></span> 
- <span data-ttu-id="8bb39-2062">**priorytet**: wskaźnik do miejsca docelowego dla priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2062">**priority**: Pointer to destination for the thread’s priority.</span></span>
- <span data-ttu-id="8bb39-2063">**preemption_threshold**: wskaźnik do miejsca docelowego dla progu zastępujący wątek.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2063">**preemption_threshold**: Pointer to destination for the thread’s preemption-threshold.</span></span>
- <span data-ttu-id="8bb39-2064">**time_slice**: wskaźnik do miejsca docelowego dla wycinka czasu wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2064">**time_slice**: Pointer to destination for the thread’s time-slice.</span></span> 
- <span data-ttu-id="8bb39-2065">**next_thread**: wskaźnik do miejsca docelowego dla następnego utworzonego wskaźnika wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2065">**next_thread**: Pointer to destination for next created thread pointer.</span></span>
- <span data-ttu-id="8bb39-2066">**suspended_thread**: wskaźnik do miejsca docelowego dla wskaźnika do następnego wątku na liście zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2066">**suspended_thread**: Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2067">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2067">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2068">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2068">Return Values</span></span>

- <span data-ttu-id="8bb39-2069">**TX_SUCCESS**: (0X00) pomyślne pobranie informacji wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2069">**TX_SUCCESS**: (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="8bb39-2070">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik kontrolny wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2070">TX_THREAD_ERROR: (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2071">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2071">Allowed From</span></span>

<span data-ttu-id="8bb39-2072">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2072">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2073">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2073">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2074">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2074">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2075">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2075">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2076">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2076">See Also</span></span>

- <span data-ttu-id="8bb39-2077">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2077">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2078">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2078">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2079">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2079">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2080">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2080">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2081">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2081">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2082">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2082">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2083">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2083">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2084">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2084">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2085">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2085">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2086">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2086">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2087">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2087">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2088">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2088">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2089">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2089">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2090">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2090">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2091">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2091">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2092">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2092">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2093">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2093">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="8bb39-2094">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2094">tx_thread_performance_info_get</span></span> 

<span data-ttu-id="8bb39-2095">Pobierz informacje o wydajności wątków</span><span class="sxs-lookup"><span data-stu-id="8bb39-2095">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2096">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2096">Prototype</span></span>

```C
UINT  tx_thread_performance_info_get(TX_THREAD *thread_ptr,
        ULONG *resumptions, ULONG *suspensions,
        ULONG *solicited_preemptions, ULONG *interrupt_preemptions,
        ULONG *priority_inversions, ULONG *time_slices,
        ULONG *relinquishes, ULONG *timeouts, ULONG *wait_aborts,
        TX_THREAD **last_preempted_by);
```
### <a name="description"></a><span data-ttu-id="8bb39-2097">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2097">Description</span></span>

<span data-ttu-id="8bb39-2098">Ta usługa pobiera informacje o wydajności dotyczące określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2098">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2099">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_THREAD_ENABLE_PERFORMANCE_INFO** zdefiniowanych w celu zwrócenia informacji o wydajności przez tę usługę.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2099">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2100">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2100">Parameters</span></span> 

- <span data-ttu-id="8bb39-2101">**thread_ptr**: wskaźnik do wcześniej utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2101">**thread_ptr**: Pointer to previously created thread.</span></span>
- <span data-ttu-id="8bb39-2102">**wznawiania**: wskaźnik do miejsca docelowego dla liczby wznowień tego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2102">**resumptions**: Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="8bb39-2103">**zawieszenia**: wskaźnik do miejsca docelowego dla liczby zawieszeń tego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2103">**suspensions**: Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="8bb39-2104">**solicited_preemptions**: wskaźnik do miejsca docelowego dla liczby przeniesień w wyniku wywołania usługi API ThreadX wykonanego przez ten wątek.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2104">**solicited_preemptions**: Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="8bb39-2105">**interrupt_preemptions**: wskaźnik do miejsca docelowego dla liczby przeniesień tego wątku w wyniku przetwarzania przerwań.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2105">**interrupt_preemptions**: Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="8bb39-2106">**priority_inversions**: wskaźnik do miejsca docelowego dla liczby niewersji priorytetu tego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2106">**priority_inversions**: Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="8bb39-2107">**time_slices**: wskaźnik do miejsca docelowego dla liczby timeslices tego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2107">**time_slices**: Pointer to destination for the number of timeslices of this thread.</span></span>
- <span data-ttu-id="8bb39-2108">**zwalnia**: wskaźnik do miejsca docelowego dla liczby operacji zwalniania wątku wykonywanych przez ten wątek.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2108">**relinquishes**: Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="8bb39-2109">**limity czasu**: wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia dla tego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2109">**timeouts**: Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="8bb39-2110">**wait_aborts**: wskaźnik do miejsca docelowego dla liczby przerwań oczekiwania wykonanych w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2110">**wait_aborts**: Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="8bb39-2111">**last_preempted_by**: wskaźnik do miejsca docelowego dla wskaźnika wątku, który ostatnio zastępują ten wątek.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2111">**last_preempted_by**: Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2112">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2112">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2113">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2113">Return Values</span></span>

- <span data-ttu-id="8bb39-2114">**TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2114">**TX_SUCCESS**: (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="8bb39-2115">**TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2115">**TX_PTR_ERROR**: (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="8bb39-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2116">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2117">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2117">Allowed From</span></span>

<span data-ttu-id="8bb39-2118">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2118">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2119">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2119">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2120">See Also</span></span>

- <span data-ttu-id="8bb39-2121">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2121">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2122">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2122">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2123">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2123">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2124">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2124">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2125">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2125">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2126">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2126">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2127">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2127">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2128">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2128">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2129">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2129">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2130">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2130">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2131">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2131">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2132">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2132">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2133">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2133">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2134">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2134">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2135">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2135">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2136">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2136">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2137">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2137">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="8bb39-2138">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2138">tx_thread_performance_system_info_get</span></span> 

<span data-ttu-id="8bb39-2139">Pobierz informacje o wydajności systemu wątków</span><span class="sxs-lookup"><span data-stu-id="8bb39-2139">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2140">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2140">Prototype</span></span>

```C
UINT tx_thread_performance_system_info_get(ULONG *resumptions,
       ULONG *suspensions, ULONG *solicited_preemptions,
       ULONG *interrupt_preemptions, ULONG *priority_inversions,
       ULONG *time_slices, ULONG *relinquishes, ULONG *timeouts,
       ULONG *wait_aborts, ULONG *non_idle_returns,
       ULONG *idle_returns);
```
### <a name="description"></a><span data-ttu-id="8bb39-2141">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2141">Description</span></span>

<span data-ttu-id="8bb39-2142">Ta usługa pobiera informacje o wydajności wszystkich wątków w systemie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2142">This service retrieves performance information about all the threads in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2143">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_THREAD_ENABLE_PERFORMANCE_INFO** zdefiniowanych w celu zwrócenia informacji o wydajności przez tę usługę.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2143">The ThreadX SMP library and application must be built with **TX_THREAD_ENABLE_PERFORMANCE_INFO** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2144">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2144">Parameters</span></span>

- <span data-ttu-id="8bb39-2145">**wznawiania**: wskaźnik do miejsca docelowego dla łącznej liczby wznowień wątków.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2145">**resumptions**: Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="8bb39-2146">**zawieszenia**: wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2146">**suspensions**: Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="8bb39-2147">**solicited_preemptions**: wskaźnik do miejsca docelowego dla łącznej liczby zastępujący wątków w wyniku wątku wywołującego usługę interfejsu API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2147">**solicited_preemptions**: Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="8bb39-2148">**interrupt_preemptions**: wskaźnik do miejsca docelowego dla łącznej liczby przeniesień wątków w wyniku przetwarzania przerwań.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2148">**interrupt_preemptions**: Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="8bb39-2149">**priority_inversions**: wskaźnik do miejsca docelowego dla łącznej liczby niewersji priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2149">**priority_inversions**: Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="8bb39-2150">**time_slices**: wskaźnik do miejsca docelowego dla łącznej liczby wycinków czasu wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2150">**time_slices**: Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="8bb39-2151">**zwalnia**: wskaźnik do miejsca docelowego dla łącznej liczby wyniesień wątków.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2151">**relinquishes**: Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="8bb39-2152">**limity czasu**: wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2152">**timeouts**: Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="8bb39-2153">**wait_aborts**: wskaźnik do miejsca docelowego dla łącznej liczby przerwań oczekiwania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2153">**wait_aborts**: Pointer to destination for the total number of thread wait aborts.</span></span> 
- <span data-ttu-id="8bb39-2154">**non_idle_returns**: wskaźnik do miejsca docelowego dla czasu, przez który wątek wraca do systemu, gdy inny wątek jest gotowy do wykonania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2154">**non_idle_returns**: Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span> 
- <span data-ttu-id="8bb39-2155">**idle_returns**: wskaźnik do miejsca docelowego dla czasu, przez który wątek wraca do systemu, gdy żaden inny wątek nie jest gotowy do wykonania (bezczynny system).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2155">**idle_returns**: Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2156">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2156">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2157">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2157">Return Values</span></span>

- <span data-ttu-id="8bb39-2158">**TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności systemu wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2158">**TX_SUCCESS**: (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="8bb39-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2159">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2160">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2160">Allowed From</span></span>

<span data-ttu-id="8bb39-2161">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2161">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2162">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2162">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2163">See Also</span></span>

- <span data-ttu-id="8bb39-2164">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2164">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2165">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2165">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2166">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2166">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2167">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2167">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2168">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2168">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2169">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2169">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2170">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2170">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2171">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2171">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2172">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2172">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2173">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2173">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2174">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2174">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2175">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2175">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2176">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2176">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2177">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2177">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2178">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2178">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2179">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2179">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2180">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2180">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="8bb39-2181">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2181">tx_thread_preemption_change</span></span>

<span data-ttu-id="8bb39-2182">Zmiana zastępujący — próg wątku aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2182">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2183">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2183">Prototype</span></span>

```C
UINT tx_thread_preemption_change(TX_THREAD *thread_ptr,
                          UINT new_threshold, UINT *old_threshold);
```
### <a name="description"></a><span data-ttu-id="8bb39-2184">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2184">Description</span></span>

<span data-ttu-id="8bb39-2185">Ta usługa zmienia próg przekroczenia określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2185">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="8bb39-2186">Próg zastępujący uniemożliwia przestawianie określonego wątku przez wątki równe lub mniejsze od wartości progowej przekroczenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2186">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2187">Użycie wartości progowej przekroczenia powoduje wyłączenie wycinka czasu dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2187">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2188">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2188">Parameters</span></span>

- <span data-ttu-id="8bb39-2189">**thread_ptr**: wskaźnik do wcześniej utworzonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2189">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="8bb39-2190">**new_threshold**: nowy przekroczenie — poziom priorytetu progu (od 0 do (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2190">**new_threshold**: New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="8bb39-2191">**old_threshold**: wskaźnik do lokalizacji, aby przywrócić poprzedni próg zastępujący.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2191">**old_threshold**: Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2192">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2192">Return Values</span></span>

- <span data-ttu-id="8bb39-2193">**TX_SUCCESS**: (0X00) pomyślne przekroczenie — zmiana progowa.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2193">**TX_SUCCESS**: (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="8bb39-2194">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2194">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8bb39-2195">**TX_THRESH_ERROR**: (0X18) określony nowy próg przechodzenia nie jest prawidłowym priorytetem wątku (wartość inna niż (od 0 do (TX_MAX_PRIORITIES-1)) lub jest większa niż (niższy priorytet) niż bieżący priorytet wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2195">**TX_THRESH_ERROR**: (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (TX_MAX_PRIORITIES-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="8bb39-2196">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do poprzedniej lokalizacji magazynu preemptionthreshold.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2196">TX_PTR_ERROR: (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="8bb39-2197">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2197">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2198">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2198">Allowed From</span></span>

<span data-ttu-id="8bb39-2199">Wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-2199">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2200">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2200">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2201">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2201">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2202">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2202">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2203">See Also</span></span>

- <span data-ttu-id="8bb39-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2204">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2205">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2207">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2210">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2210">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2211">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2211">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2212">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2212">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2213">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2213">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2214">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="8bb39-2221">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2221">tx_thread_priority_change</span></span>

<span data-ttu-id="8bb39-2222">Zmień priorytet wątku aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2222">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2223">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2223">Prototype</span></span>

```C
UINT tx_thread_priority_change(TX_THREAD *thread_ptr,
                          UINT new_priority, UINT *old_priority);
```
### <a name="description"></a><span data-ttu-id="8bb39-2224">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2224">Description</span></span>

<span data-ttu-id="8bb39-2225">Ta usługa zmienia priorytet określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2225">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="8bb39-2226">Prawidłowy zakres priorytetów należy do zakresu od 0 do (TX_MAX_PRIORITES-1), gdzie 0 oznacza najwyższy poziom priorytetu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2226">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2227">Próg przekroczenia określonego wątku jest automatycznie ustawiany na nowy priorytet.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2227">The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="8bb39-2228">W przypadku pożądanego nowego progu należy użyć usługi **tx_thread_preemption_change** po tym wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2228">If a new threshold is desired, the **tx_thread_preemption_change** service must be used after this call.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2229">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2229">Parameters</span></span>

- <span data-ttu-id="8bb39-2230">**thread_ptr**: wskaźnik do wcześniej utworzonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2230">**thread_ptr**: Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="8bb39-2231">**new_priority**: nowy poziom priorytetu wątku (od 0 do (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2231">**new_priority**: New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="8bb39-2232">**old_priority**: wskaźnik do lokalizacji, aby przywrócić poprzedni priorytet wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2232">**old_priority**: Pointer to a location to return the thread’s previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2233">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2233">Return Values</span></span>

- <span data-ttu-id="8bb39-2234">**TX_SUCCESS**: (0x00) pomyślna zmiana priorytetu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2234">**TX_SUCCESS**: (0x00) Successful priority change.</span></span>
- <span data-ttu-id="8bb39-2235">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2235">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8bb39-2236">TX_PRIORITY_ERROR: (0x0F) określony nowy priorytet jest nieprawidłowy (wartość inna niż (od 0 do (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2236">TX_PRIORITY_ERROR: (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="8bb39-2237">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do lokalizacji magazynu o poprzednim priorytecie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2237">TX_PTR_ERROR: (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="8bb39-2238">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2238">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2239">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2239">Allowed From</span></span>

<span data-ttu-id="8bb39-2240">Wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-2240">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2241">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2241">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2242">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2242">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2243">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2243">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2244">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2244">See Also</span></span>

- <span data-ttu-id="8bb39-2245">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2245">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2246">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2246">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2247">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2247">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2248">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2248">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2249">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2249">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2250">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2250">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2251">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2251">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2252">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2252">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2253">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2253">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2254">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2254">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2255">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2255">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2256">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2256">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2257">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2257">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2258">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2258">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2259">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2259">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2260">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2260">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2261">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2261">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="8bb39-2262">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2262">tx_thread_relinquish</span></span>

<span data-ttu-id="8bb39-2263">Zwalnianie kontroli do innych wątków aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2263">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2264">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2264">Prototype</span></span>

```C
VOID tx_thread_relinquish(VOID);
```
### <a name="description"></a><span data-ttu-id="8bb39-2265">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2265">Description</span></span>

<span data-ttu-id="8bb39-2266">Ta usługa zrzeka kontrolę procesora do innych gotowych do uruchomienia wątków o tym samym lub wyższym priorytecie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2266">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2267">Oprócz przepisywania kontroli do wątków o takim samym priorytecie, ta usługa również zwalnia z wykonywania kontroli nad wątkiem o najwyższym priorytecie z powodu ustawienia progu przekroczenia bieżącego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2267">In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2268">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2268">Parameters</span></span>

<span data-ttu-id="8bb39-2269">Brak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2269">None</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2270">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2270">Return Values</span></span>

<span data-ttu-id="8bb39-2271">Brak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2271">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2272">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2272">Allowed From</span></span>

<span data-ttu-id="8bb39-2273">Wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2274">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2274">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2275">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2276">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2276">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2277">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2277">See Also</span></span>

- <span data-ttu-id="8bb39-2278">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2278">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2279">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2279">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2280">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2280">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2281">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2281">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2282">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2282">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2283">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2283">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2284">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2284">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2285">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2285">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2286">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2286">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2287">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2288">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2289">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2289">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2290">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2290">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2291">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2291">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2292">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2292">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2293">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2293">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2294">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2294">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="8bb39-2295">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2295">tx_thread_reset</span></span>

<span data-ttu-id="8bb39-2296">Zresetuj wątek</span><span class="sxs-lookup"><span data-stu-id="8bb39-2296">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2297">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2297">Prototype</span></span>

```C
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-2298">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2298">Description</span></span>

<span data-ttu-id="8bb39-2299">Ta usługa resetuje określony wątek do wykonania w punkcie wejścia zdefiniowanym podczas tworzenia wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2299">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="8bb39-2300">Aby można było zresetować wątek, musi on być w stanie **TX_COMPLETED** lub **TX_TERMINATED**</span><span class="sxs-lookup"><span data-stu-id="8bb39-2300">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2301">Wątek należy wznowić, aby można było wykonać operację ponownie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2301">The thread must be resumed for it to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2302">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2302">Parameters</span></span> 

- <span data-ttu-id="8bb39-2303">**thread_ptr**: wskaźnik do wcześniej utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2303">**thread_ptr**: Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2304">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2304">Return Values</span></span>

- <span data-ttu-id="8bb39-2305">**TX_SUCCESS**: (0X00) pomyślne zresetowanie wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2305">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="8bb39-2306">**TX_NOT_DONE**: (0X20) określony wątek nie jest w stanie TX_COMPLETED lub TX_TERMINATED.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2306">**TX_NOT_DONE**: (0x20) Specified thread is not in a TX_COMPLETED or TX_TERMINATED state.</span></span>
- <span data-ttu-id="8bb39-2307">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2307">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="8bb39-2308">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2308">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2309">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2309">Allowed From</span></span>

<span data-ttu-id="8bb39-2310">Wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-2310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2311">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2311">Example</span></span>

```C
TX_THREAD     my_thread;

/* Reset the previously created thread "my_thread." */
status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2312">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2312">See Also</span></span>

- <span data-ttu-id="8bb39-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2313">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2314">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2316">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2319">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2319">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2323">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2323">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2324">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2324">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2325">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2325">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="8bb39-2330">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2330">tx_thread_resume</span></span>

<span data-ttu-id="8bb39-2331">Wznów zawieszony wątek aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2331">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2332">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2332">Prototype</span></span>

```C
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-2333">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2333">Description</span></span>

<span data-ttu-id="8bb39-2334">Ta usługa wznawia lub przygotowuje do wykonania wątek, który został wcześniej zawieszony przez wywołanie ***tx_thread_suspend*** .</span><span class="sxs-lookup"><span data-stu-id="8bb39-2334">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="8bb39-2335">Ponadto ta usługa wznawia wątki, które zostały utworzone bez automatycznego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2335">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2336">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2336">Parameters</span></span>

- <span data-ttu-id="8bb39-2337">**thread_ptr**: wskaźnik do zawieszonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2337">**thread_ptr**: Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2338">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2338">Return Values</span></span>

- <span data-ttu-id="8bb39-2339">**TX_SUCCESS**: (0X00) pomyślne wznowienie wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2339">**TX_SUCCESS**: (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="8bb39-2340">**TX_SUSPEND_LIFTED**: (0X19) poprzednio ustawione opóźnione zawieszenie zostało zniesione.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2340">**TX_SUSPEND_LIFTED**: (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="8bb39-2341">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2341">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8bb39-2342">**TX_RESUME_ERROR**: (0X12) określony wątek nie jest wstrzymany lub został wcześniej zawieszony przez usługę inną niż **_tx_thread_suspend_**.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2342">**TX_RESUME_ERROR**: (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2343">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2343">Allowed From</span></span>

<span data-ttu-id="8bb39-2344">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2344">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2345">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2345">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2346">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2346">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2347">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2347">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Resume the thread represented by "my_thread". */
status =  tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   now ready to execute. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2348">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2348">See Also</span></span>

- <span data-ttu-id="8bb39-2349">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2349">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2350">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2350">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2351">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2351">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2352">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2352">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2353">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2353">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2354">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2354">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2355">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2355">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2356">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2356">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2357">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2357">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2358">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2358">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2359">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2359">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2360">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2360">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2361">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2361">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2362">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2362">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2363">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2363">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2364">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2364">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2365">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2365">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="8bb39-2366">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2366">tx_thread_sleep</span></span>

<span data-ttu-id="8bb39-2367">Zawieś bieżący wątek przez określony czas</span><span class="sxs-lookup"><span data-stu-id="8bb39-2367">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2368">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2368">Prototype</span></span>

```C
UINT tx_thread_sleep(ULONG timer_ticks);
```
### <a name="description"></a><span data-ttu-id="8bb39-2369">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2369">Description</span></span>

<span data-ttu-id="8bb39-2370">Ta usługa powoduje zawieszenie wątku wywołującego dla określonej liczby taktów czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2370">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="8bb39-2371">Czas fizyczny skojarzony z cyklem czasomierza jest specyficzny dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2371">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="8bb39-2372">Ta usługa może być wywoływana tylko z wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2372">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2373">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2373">Parameters</span></span>

- <span data-ttu-id="8bb39-2374">**timer_ticks**: liczba cykli czasomierza wstrzymania wątku aplikacji wywołującej, od 0 do 0xffffffff.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2374">**timer_ticks**: The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="8bb39-2375">Jeśli określono wartość 0, usługa wraca natychmiast.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2375">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2376">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2376">Return Values</span></span>

- <span data-ttu-id="8bb39-2377">**TX_SUCCESS**: (0X00) powodzenie uśpienia wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2377">**TX_SUCCESS**: (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="8bb39-2378">**TX_WAIT_ABORTED**: (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2378">**TX_WAIT_ABORTED**: (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="8bb39-2379">**TX_CALLER_ERROR**: (0x13) wywołana z niewątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2379">**TX_CALLER_ERROR**: (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2380">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2380">Allowed From</span></span>

<span data-ttu-id="8bb39-2381">Wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-2381">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2382">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2382">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2383">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2383">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2384">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2384">Example</span></span>

```C
UINT status;

/* Make the calling thread sleep for 100
   timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
   application thread slept for the specified number of
   timer-ticks. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2385">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2385">See Also</span></span>

- <span data-ttu-id="8bb39-2386">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2386">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2387">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2387">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2388">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2388">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2389">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2389">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2390">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2390">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2391">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2391">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2392">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2392">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2393">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2393">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2394">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2394">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2395">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2395">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2396">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2396">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2397">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2397">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2398">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2398">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2399">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2399">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2400">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2400">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2401">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2401">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2402">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2402">tx_thread_wait_abort</span></span>

## <a name="tx_thread_smp_core_exclude"></a><span data-ttu-id="8bb39-2403">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="8bb39-2403">tx_thread_smp_core_exclude</span></span>

<span data-ttu-id="8bb39-2404">Wyklucz wykonywanie wątku na zestawie rdzeni</span><span class="sxs-lookup"><span data-stu-id="8bb39-2404">Exclude thread execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2405">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2405">Prototype</span></span>

```C
UINT  tx_thread_smp_core_exclude(TX_THREAD *thread_ptr,
                          ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="8bb39-2406">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2406">Description</span></span>

<span data-ttu-id="8bb39-2407">Ta funkcja wyklucza określony wątek z wykonywania na rdzeniach określonych w mapie bitowej o nazwie "*exclusion_map*".</span><span class="sxs-lookup"><span data-stu-id="8bb39-2407">This function excludes the specified thread from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="8bb39-2408">Każdy bit w "*exclusion_map*" reprezentuje rdzeń (bit 0 reprezentuje rdzeń 0 itd.).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2408">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="8bb39-2409">Jeśli bit jest ustawiony, odpowiadający rdzeń jest wykluczony z wykonywania określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2409">If the bit is set, the corresponding core is excluded from executing the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2410">Użycie wykluczenia procesora może spowodować dodatkowe przetwarzanie w wątku do podstawowej logiki mapowania, aby znaleźć optymalne dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2410">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="8bb39-2411">To przetwarzanie jest ograniczone przez liczbę gotowych wątków.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2411">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2412">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2412">Parameters</span></span> 

- <span data-ttu-id="8bb39-2413">**thread_ptr**: wskaźnik do wątku, aby zmienić wykluczenia rdzenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2413">**thread_ptr**: Pointer to thread to change the core exclusion.</span></span>
- <span data-ttu-id="8bb39-2414">**exclusion_map**: Mapa bitowa, gdzie bit Sit wskazuje, że rdzeń jest wykluczony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2414">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="8bb39-2415">Dostarczenie wartości 0 powoduje, że wątek będzie wykonywany na dowolnym rdzeń (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2415">Supplying a 0 value enables the thread to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2416">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2416">Return Values</span></span>

- <span data-ttu-id="8bb39-2417">TX_SUCCESS: (0x00) pomyślne wykluczenie rdzenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2417">TX_SUCCESS: (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="8bb39-2418">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2418">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2419">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2419">Allowed From</span></span>

<span data-ttu-id="8bb39-2420">Inicjalizacja, procedury ISR, wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-2420">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2421">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2421">Example</span></span>

```C
/* Exclude core 0 for "Thread 0". */
tx_thread_smp_core_exclude(&thread_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="8bb39-2422">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2422">See Also</span></span>

- <span data-ttu-id="8bb39-2423">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2423">tx_thread_smp_core_exclude_get</span></span>
- <span data-ttu-id="8bb39-2424">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2424">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_exclude_get"></a><span data-ttu-id="8bb39-2425">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2425">tx_thread_smp_core_exclude_get</span></span>

<span data-ttu-id="8bb39-2426">Pobiera wykluczenie rdzenia bieżącego wątku</span><span class="sxs-lookup"><span data-stu-id="8bb39-2426">Gets the thread's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2427">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2427">Prototype</span></span>

```C
UINT tx_thread_smp_core_exclude_get(TX_THREAD *thread_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-2428">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2428">Description</span></span>

<span data-ttu-id="8bb39-2429">Ta funkcja zwraca bieżącą listę wykluczeń rdzeni.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2429">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2430">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2430">Parameters</span></span>

- <span data-ttu-id="8bb39-2431">**thread_ptr**: wskaźnik do wątku, z którego ma zostać pobrany rdzeń wykluczenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2431">**thread_ptr**: Pointer to thread from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="8bb39-2432">**exclusion_map_ptr**: miejsce docelowe dla bieżącej mapy bitowej wykluczeń podstawowych.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2432">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2433">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2433">Return Values</span></span>

- <span data-ttu-id="8bb39-2434">TX_SUCCESS: (0x00) pomyślne pobranie wykluczenia rdzenia wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2434">TX_SUCCESS: (0x00) Successful retrieval of thread's core exclusion.</span></span>
- <span data-ttu-id="8bb39-2435">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2435">TX_THREAD_ERROR: (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="8bb39-2436">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik docelowy wykluczenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2436">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2437">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2437">Allowed From</span></span>

<span data-ttu-id="8bb39-2438">Inicjalizacja, procedury ISR, wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-2438">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2439">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2439">Example</span></span>

```C
ULONGexcluded_cores;
/* Retrieve the core exclusion for "Thread 0". */
tx_thread_smp_core_exclude_get(&thread_0, &excluded_cores);
```

### <a name="see-also"></a><span data-ttu-id="8bb39-2440">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2440">See Also</span></span>

- <span data-ttu-id="8bb39-2441">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="8bb39-2441">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="8bb39-2442">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2442">tx_thread_smp_core_get</span></span>

## <a name="tx_thread_smp_core_get"></a><span data-ttu-id="8bb39-2443">tx_thread_smp_core_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2443">tx_thread_smp_core_get</span></span>

<span data-ttu-id="8bb39-2444">Pobierz aktualnie wykonywane rdzeń obiektu wywołującego</span><span class="sxs-lookup"><span data-stu-id="8bb39-2444">Retrieve currently executing core of caller</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2445">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2445">Prototype</span></span>

```C
UINT  tx_thread_smp_core_get(void);
```
### <a name="description"></a><span data-ttu-id="8bb39-2446">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2446">Description</span></span>

<span data-ttu-id="8bb39-2447">Ta funkcja zwraca podstawowy identyfikator rdzenia wykonującego tę usługę.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2447">This function returns the core ID of the core executing this service.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2448">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2448">Parameters</span></span>

<span data-ttu-id="8bb39-2449">Brak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2449">None</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2450">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2450">Return Values</span></span>

- <span data-ttu-id="8bb39-2451">core_id: Identyfikator aktualnie wykonywanej klasy rdzeń (od 0 do TX_THREAD_SMP_MAX_CORES-1)</span><span class="sxs-lookup"><span data-stu-id="8bb39-2451">core_id: ID of currently executing core, (0 through TX_THREAD_SMP_MAX_CORES-1)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2452">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2452">Allowed From</span></span>

<span data-ttu-id="8bb39-2453">Inicjalizacja, procedury ISR, wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-2453">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2454">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2454">Example</span></span>

```C
UINTcore;
/* Pickup the currently executing core. */
core = tx_thread_smp_core_get();

/* At this point, “core” contains the executing core ID. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2455">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2455">See Also</span></span>

- <span data-ttu-id="8bb39-2456">tx_thread_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="8bb39-2456">tx_thread_smp_core_exclude</span></span>
- <span data-ttu-id="8bb39-2457">tx_thread_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2457">tx_thread_smp_core_exclude_get</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="8bb39-2458">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2458">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="8bb39-2459">Wywołanie zwrotne powiadomienia o błędzie stosu rejestracji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2459">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2460">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2460">Prototype</span></span>

```C
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```
### <a name="description"></a><span data-ttu-id="8bb39-2461">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2461">Description</span></span>

<span data-ttu-id="8bb39-2462">Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia do obsługi błędów stosu wątków.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2462">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="8bb39-2463">Gdy ThreadX SMP wykryje błąd stosu wątku podczas wykonywania, wywoła tę funkcję powiadamiania w celu przetworzenia błędu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2463">When ThreadX SMP detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="8bb39-2464">Przetwarzanie błędu jest całkowicie zdefiniowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2464">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="8bb39-2465">Wszystkie elementy od zawieszenia naruszenia wątku w celu zresetowania całego systemu mogą zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2465">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2466">Biblioteka SMP ThreadX musi być skompilowana przy użyciu **TX_ENABLE_STACK_CHECKING** zdefiniowanej w celu zwrócenia informacji o wydajności przez tę usługę.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2466">The ThreadX SMP library must be built with **TX_ENABLE_STACK_CHECKING** defined in order for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2467">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2467">Parameters</span></span>

- <span data-ttu-id="8bb39-2468">**error_handler**: wskaźnik do funkcji obsługi błędów stosu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2468">**error_handler**: Pointer to application’s stack error handling function.</span></span> <span data-ttu-id="8bb39-2469">Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2469">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2470">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2470">Return Values</span></span>

- <span data-ttu-id="8bb39-2471">**TX_SUCCESS**: (0X00) pomyślne zresetowanie wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2471">**TX_SUCCESS**: (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="8bb39-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2472">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2473">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2473">Allowed From</span></span>

<span data-ttu-id="8bb39-2474">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2474">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2475">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2475">Example</span></span>

```C
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX SMP
   so that thread stack errors can be handled by the application. */
status =  tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2476">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2476">See Also</span></span>

- <span data-ttu-id="8bb39-2477">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2477">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2478">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2478">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2479">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2479">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2480">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2480">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2481">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2481">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2482">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2482">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2483">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2483">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2484">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2484">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2485">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2485">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2486">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2486">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2487">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2487">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2488">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2488">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2489">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2489">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2490">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2490">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2491">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2491">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2492">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2492">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2493">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2493">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="8bb39-2494">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2494">tx_thread_suspend</span></span>

<span data-ttu-id="8bb39-2495">Wstrzymywanie wątku aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2495">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2496">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2496">Prototype</span></span>

```C
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-2497">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2497">Description</span></span>

<span data-ttu-id="8bb39-2498">Ta usługa wstrzymuje określony wątek aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2498">This service suspends the specified application thread.</span></span> <span data-ttu-id="8bb39-2499">Wątek może wywołać tę usługę, aby zawiesić się.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2499">A thread may call this service to suspend itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2500">Jeśli określony wątek został już zawieszony z innego powodu, to zawieszenie jest przechowywane wewnętrznie do momentu zniesienia wcześniejszego zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2500">If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted.</span></span> <span data-ttu-id="8bb39-2501">W takim przypadku wykonywane jest niewarunkowe zawieszenie określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2501">When that happens, this unconditional suspension of the specified thread is performed.</span></span> <span data-ttu-id="8bb39-2502">Dalsze niewarunkowe żądania zawieszenia nie mają żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2502">Further unconditional suspension requests have no effect.</span></span>

<span data-ttu-id="8bb39-2503">Po wstrzymaniu wątek musi zostać wznowiony przez ***tx_thread_resume*** , aby wykonać operację ponownie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2503">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

## <a name="parameters"></a><span data-ttu-id="8bb39-2504">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2504">Parameters</span></span>

- <span data-ttu-id="8bb39-2505">**thread_ptr**: wskaźnik do wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2505">**thread_ptr**: Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2506">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2506">Return Values</span></span>

- <span data-ttu-id="8bb39-2507">**TX_SUCCESS**: (0X00) pomyślne wstrzymanie wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2507">**TX_SUCCESS**: (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="8bb39-2508">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2508">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8bb39-2509">**TX_SUSPEND_ERROR**: (0X14) określony wątek jest w stanie przerwana lub ukończona.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2509">**TX_SUSPEND_ERROR**: (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="8bb39-2510">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2510">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2511">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2511">Allowed From</span></span>

<span data-ttu-id="8bb39-2512">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2512">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2513">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2513">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2514">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2514">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2515">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2515">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
   unconditionally suspended. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2516">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2516">See Also</span></span>

- <span data-ttu-id="8bb39-2517">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2517">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2518">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2518">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2519">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2519">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2520">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2520">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2521">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2521">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2522">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2522">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2523">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2523">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2524">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2524">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2525">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2525">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2526">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2526">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2527">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2527">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2528">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2528">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2529">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2529">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2530">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2530">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2531">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2531">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2532">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2532">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2533">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2533">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="8bb39-2534">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2534">tx_thread_terminate</span></span>

<span data-ttu-id="8bb39-2535">Przerywa wątek aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2535">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2536">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2536">Prototype</span></span>

```C
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-2537">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2537">Description</span></span>

<span data-ttu-id="8bb39-2538">Ta usługa przerywa określony wątek aplikacji niezależnie od tego, czy wątek jest wstrzymany, czy nie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2538">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="8bb39-2539">Wątek może wywoływać tę usługę, aby zakończyć działanie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2539">A thread may call this service to terminate itself.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2540">Po zakończeniu należy zresetować wątek, aby można było wykonać operację ponownie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2540">After being terminated, the thread must be reset for it to execute again.</span></span>

> [!WARNING]
> <span data-ttu-id="8bb39-2541">Jest on odpowiedzialny za zapewnienie, że wątek jest w stanie odpowiednim do zakończenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2541">It is the application's responsibility to ensure the thread is in a state suitable for termination.</span></span> <span data-ttu-id="8bb39-2542">Na przykład wątek nie powinien być zakończony podczas krytycznego przetwarzania aplikacji lub wewnątrz innych składników oprogramowania pośredniczącego, w którym może to spowodować, że przetwarzanie jest nieznane.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2542">For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2543">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2543">Parameters</span></span>

- <span data-ttu-id="8bb39-2544">**thread_ptr**: wskaźnik do wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2544">**thread_ptr**: Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2545">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2545">Return Values</span></span>

- <span data-ttu-id="8bb39-2546">**TX_SUCCESS**: (0X00) pomyślne zakończenie wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2546">**TX_SUCCESS**: (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="8bb39-2547">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2547">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8bb39-2548">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2548">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2549">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2549">Allowed From</span></span>

<span data-ttu-id="8bb39-2550">Wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-2550">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2551">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2551">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2552">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2552">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2553">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2553">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Terminate the thread represented by "my_thread". */
status =  tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
   and cannot execute again until it is reset. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2554">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2554">See Also</span></span>

- <span data-ttu-id="8bb39-2555">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2555">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2556">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2556">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2557">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2557">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2558">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2558">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2559">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2559">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2560">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2560">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2561">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2561">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2562">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2562">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2563">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2563">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2564">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2564">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2565">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2565">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2566">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2566">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2567">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2567">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2568">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2568">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2569">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2569">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2570">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2570">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="8bb39-2571">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2571">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="8bb39-2572">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2572">tx_thread_time_slice_change</span></span>

<span data-ttu-id="8bb39-2573">Zmienia czas wycinka wątku aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2573">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2574">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2574">Prototype</span></span>

```C
UINT tx_thread_time_slice_change(TX_THREAD *thread_ptr,
                          ULONG new_time_slice, ULONG *old_time_slice);
```
### <a name="description"></a><span data-ttu-id="8bb39-2575">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2575">Description</span></span>

<span data-ttu-id="8bb39-2576">Ta usługa zmienia wycinek czasu określonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2576">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="8bb39-2577">Wybranie wycinka czasu dla wątku polega na tym, że nie będzie działać więcej niż określona liczba taktów czasomierza, zanim inne wątki o tych samych lub wyższych priorytetach mają szansę na wykonanie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2577">Selecting a time-slice for a thread insures that it won’t execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2578">Użycie wartości progowej przekroczenia powoduje wyłączenie wycinka czasu dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2578">Using preemption-threshold disables time-slicing for the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2579">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2579">Parameters</span></span>

- <span data-ttu-id="8bb39-2580">**thread_ptr**: wskaźnik do wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2580">**thread_ptr**: Pointer to application thread.</span></span>
- <span data-ttu-id="8bb39-2581">**new_time_slice**: Nowa wartość wycinka czasu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2581">**new_time_slice**: New time slice value.</span></span> <span data-ttu-id="8bb39-2582">Wartości prawne obejmują TX_NO_TIME_SLICE i wartości liczbowe z przedziału od 1 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2582">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="8bb39-2583">**old_time_slice**: wskaźnik do lokalizacji przechowywania poprzedniej wartości timeslice określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2583">**old_time_slice**: Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2584">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2584">Return Values</span></span>

- <span data-ttu-id="8bb39-2585">**TX_SUCCESS**: (0x00) czas pomyślnego odtworzenia wycinka.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2585">**TX_SUCCESS**: (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="8bb39-2586">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2586">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8bb39-2587">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik do poprzedniej lokalizacji przechowywania wycinków czasu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2587">TX_PTR_ERROR: (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="8bb39-2588">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2588">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2589">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2589">Allowed From</span></span>

<span data-ttu-id="8bb39-2590">Wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-2590">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2591">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2591">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2592">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2592">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2593">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2593">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2594">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2594">See Also</span></span>

- <span data-ttu-id="8bb39-2595">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2595">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2596">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2596">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2597">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2597">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2598">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2598">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2599">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2599">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2600">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2600">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2601">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2601">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2602">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2602">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2603">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2603">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2604">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2604">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2605">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2605">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2606">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2606">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2607">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2607">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2608">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2608">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2609">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2609">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2610">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2610">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2611">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2611">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="8bb39-2612">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="8bb39-2612">tx_thread_wait_abort</span></span>

<span data-ttu-id="8bb39-2613">Przerwij zawieszenie określonego wątku</span><span class="sxs-lookup"><span data-stu-id="8bb39-2613">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2614">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2614">Prototype</span></span>

```C
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="8bb39-2615">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2615">Description</span></span>

<span data-ttu-id="8bb39-2616">Ta usługa przerywa pracę w stanie uśpienia lub dowolnego innego obiektu zawieszania określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2616">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="8bb39-2617">W przypadku przerwania oczekiwania zostanie zwrócona wartość TX_WAIT_ABORTED z usługi, w której wątek oczekiwał.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2617">If the wait is aborted, a TX_WAIT_ABORTED value is returned from the service that the thread was waiting on.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2618">Ta usługa nie zwalnia jawnego zawieszenia wykonywanego przez usługę tx_thread_suspend.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2618">This service does not release explicit suspension that is made by the tx_thread_suspend service.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2619">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2619">Parameters</span></span>

- <span data-ttu-id="8bb39-2620">**thread_ptr**: wskaźnik do wcześniej utworzonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2620">**thread_ptr**: Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2621">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2621">Return Values</span></span>

- <span data-ttu-id="8bb39-2622">**TX_SUCCESS**: (0X00) pomyślne przerwanie oczekiwania wątku.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2622">**TX_SUCCESS**: (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="8bb39-2623">TX_THREAD_ERROR: (0x0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2623">TX_THREAD_ERROR: (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="8bb39-2624">**TX_WAIT_ABORT_ERROR**: (0X1b) określony wątek nie jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2624">**TX_WAIT_ABORT_ERROR**: (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2625">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2625">Allowed From</span></span>

<span data-ttu-id="8bb39-2626">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2626">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2627">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2627">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2628">Tak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2628">Yes</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2629">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2629">Example</span></span>

```C
TX_THREAD     my_thread;
UINT          status;

/* Abort the suspension condition of "my_thread." */
status =  tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
   again, with a return value showing its suspension
   was aborted (TX_WAIT_ABORTED). */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2630">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2630">See Also</span></span>

- <span data-ttu-id="8bb39-2631">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2631">tx_thread_create</span></span>
- <span data-ttu-id="8bb39-2632">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2632">tx_thread_delete</span></span>
- <span data-ttu-id="8bb39-2633">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2633">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="8bb39-2634">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2634">tx_thread_identify</span></span>
- <span data-ttu-id="8bb39-2635">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2635">tx_thread_info_get</span></span>
- <span data-ttu-id="8bb39-2636">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2636">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2637">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2637">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="8bb39-2638">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2638">tx_thread_preemption_change</span></span>
- <span data-ttu-id="8bb39-2639">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2639">tx_thread_priority_change</span></span>
- <span data-ttu-id="8bb39-2640">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="8bb39-2640">tx_thread_relinquish</span></span>
- <span data-ttu-id="8bb39-2641">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="8bb39-2641">tx_thread_reset</span></span>
- <span data-ttu-id="8bb39-2642">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="8bb39-2642">tx_thread_resume</span></span>
- <span data-ttu-id="8bb39-2643">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="8bb39-2643">tx_thread_sleep</span></span>
- <span data-ttu-id="8bb39-2644">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="8bb39-2644">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="8bb39-2645">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="8bb39-2645">tx_thread_suspend</span></span>
- <span data-ttu-id="8bb39-2646">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2646">tx_thread_terminate</span></span>
- <span data-ttu-id="8bb39-2647">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2647">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="8bb39-2648">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2648">tx_time_get</span></span>

<span data-ttu-id="8bb39-2649">Pobiera bieżącą godzinę</span><span class="sxs-lookup"><span data-stu-id="8bb39-2649">Retrieves the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2650">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2650">Prototype</span></span>

```C
ULONG tx_time_get(VOID);
```
### <a name="description"></a><span data-ttu-id="8bb39-2651">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2651">Description</span></span>

<span data-ttu-id="8bb39-2652">Ta usługa zwraca zawartość wewnętrznego zegara systemowego.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2652">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="8bb39-2653">Każdy timertick zwiększa wewnętrzny zegar systemowy o jeden.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2653">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="8bb39-2654">Zegar systemowy jest ustawiany na zero podczas inicjowania i można go zmienić na określoną wartość przez ***tx_time_set*** usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2654">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2655">Rzeczywisty czas, jaki jest reprezentowany przez cykl czasomierza, jest specyficzny dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2655">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2656">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2656">Parameters</span></span>

<span data-ttu-id="8bb39-2657">Brak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2657">None</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2658">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2658">Return Values</span></span>

- <span data-ttu-id="8bb39-2659">Takty zegara systemowego: wartość wewnętrznego, wolnego, uruchomionego zegara systemowego.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2659">system clock ticks: Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2660">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2660">Allowed From</span></span>

<span data-ttu-id="8bb39-2661">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2661">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2662">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2662">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2663">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2663">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2664">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2664">Example</span></span>

```C
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time =  tx_time_get();

/* Current time now contains a copy of the internal system
   clock. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2665">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2665">See Also</span></span>

- <span data-ttu-id="8bb39-2666">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="8bb39-2666">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="8bb39-2667">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="8bb39-2667">tx_time_set</span></span>

<span data-ttu-id="8bb39-2668">Ustawia bieżącą godzinę</span><span class="sxs-lookup"><span data-stu-id="8bb39-2668">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2669">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2669">Prototype</span></span>

```C
VOID tx_time_set(ULONG new_time);
```
### <a name="description"></a><span data-ttu-id="8bb39-2670">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2670">Description</span></span>

<span data-ttu-id="8bb39-2671">Ta usługa ustawia wewnętrzny zegar systemowy do określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2671">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="8bb39-2672">Każdy czasomierz czasu wydłuża zegar systemu wewnętrznego o jeden.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2672">Each timer-tick increases the internal system clock by one.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2673">Rzeczywisty czas, jaki jest reprezentowany przez cykl czasomierza, jest specyficzny dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2673">The actual time each timer-tick represents is application specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2674">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2674">Parameters</span></span>

- <span data-ttu-id="8bb39-2675">**new_time**: nowy czas do umieszczenia w zegarze systemowym, wartości prawne mieszczą się w zakresie od 0 do 0xffffffff.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2675">**new_time**: New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2676">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2676">Return Values</span></span>

<span data-ttu-id="8bb39-2677">Brak</span><span class="sxs-lookup"><span data-stu-id="8bb39-2677">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2678">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2678">Allowed From</span></span>

<span data-ttu-id="8bb39-2679">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2679">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2680">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2680">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2681">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2681">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2682">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2682">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
   interrupt. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2683">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2683">See Also</span></span>

- <span data-ttu-id="8bb39-2684">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2684">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="8bb39-2685">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2685">tx_timer_activate</span></span>

<span data-ttu-id="8bb39-2686">Aktywuj czasomierz aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2686">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2687">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2687">Prototype</span></span>

```C
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-2688">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2688">Description</span></span>

<span data-ttu-id="8bb39-2689">Ta usługa aktywuje określony czasomierz aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2689">This service activates the specified application timer.</span></span> <span data-ttu-id="8bb39-2690">Procedury wygasania czasomierzy, które wygasają w tym samym czasie, są wykonywane w kolejności, w jakiej zostały aktywowane.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2690">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="8bb39-2691">Aby można było ponownie aktywować czasomierz, który wygasł, należy zresetować za pomocą **tx_timer_change** .</span><span class="sxs-lookup"><span data-stu-id="8bb39-2691">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2692">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2692">Parameters</span></span>

- <span data-ttu-id="8bb39-2693">**timer_ptr**: wskaźnik do wcześniej utworzonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2693">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2694">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2694">Return Values</span></span>

- <span data-ttu-id="8bb39-2695">**TX_SUCCESS**: (0x00) pomyślna aktywacja czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2695">**TX_SUCCESS**: (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="8bb39-2696">**TX_TIMER_ERROR**: (0X15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2696">**TX_TIMER_ERROR**: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="8bb39-2697">Czasomierz **TX_ACTIVATE_ERROR**: (0x17) był już aktywny lub jest już wygasłym czasomierzem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2697">**TX_ACTIVATE_ERROR**: (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2698">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2698">Allowed From</span></span>

<span data-ttu-id="8bb39-2699">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2699">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2700">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2700">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2701">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2701">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2702">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2702">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Activate an application timer. Assume that the
   application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now active. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2703">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2703">See Also</span></span>

- <span data-ttu-id="8bb39-2704">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2704">tx_timer_change</span></span>
- <span data-ttu-id="8bb39-2705">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2705">tx_timer_create</span></span>
- <span data-ttu-id="8bb39-2706">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2706">tx_timer_deactivate</span></span>
- <span data-ttu-id="8bb39-2707">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2707">tx_timer_delete</span></span>
- <span data-ttu-id="8bb39-2708">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2708">tx_timer_info_get</span></span>
- <span data-ttu-id="8bb39-2709">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2709">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2710">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2710">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="8bb39-2711">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2711">tx_timer_change</span></span>

<span data-ttu-id="8bb39-2712">Zmień czasomierz aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2712">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2713">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2713">Prototype</span></span>

```C
UINT tx_timer_change(TX_TIMER *timer_ptr,
                          ULONG initial_ticks, ULONG reschedule_ticks);
```
### <a name="description"></a><span data-ttu-id="8bb39-2714">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2714">Description</span></span>

<span data-ttu-id="8bb39-2715">Ta usługa zmienia charakterystykę wygaśnięcia określonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2715">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="8bb39-2716">Czasomierz należy dezaktywować przed wywołaniem tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2716">The timer must be deactivated prior to calling this service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2717">Przed ponownym uruchomieniem czasomierza wymagane jest wywołanie usługi **tx_timer_activate** .</span><span class="sxs-lookup"><span data-stu-id="8bb39-2717">A call to the **tx_timer_activate** service is required after this service in order to start the timer again.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2718">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2718">Parameters</span></span>

- <span data-ttu-id="8bb39-2719">**timer_ptr**: wskaźnik do bloku sterowania czasomierzem.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2719">**timer_ptr**: Pointer to a timer control block.</span></span>
- <span data-ttu-id="8bb39-2720">**initial_ticks**: określa początkową liczbę taktów dla wygaśnięcia czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2720">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="8bb39-2721">Wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2721">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="8bb39-2722">**reschedule_ticks**: określa liczbę taktów dla wszystkich wygasających czasomierzy po pierwszej.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2722">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="8bb39-2723">Wartość zerowa dla tego parametru powoduje, że czasomierz ma czasomierz jednorazowy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2723">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="8bb39-2724">W przeciwnym razie dla okresowych czasomierzy wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2724">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="8bb39-2725">Aby można było ponownie aktywować czasomierz, który wygasł, należy zresetować za pomocą **tx_timer_change** .</span><span class="sxs-lookup"><span data-stu-id="8bb39-2725">That an expired one-shot timer must be reset via **tx_timer_change** before it can be activated again.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2726">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2726">Return Values</span></span>

- <span data-ttu-id="8bb39-2727">**TX_SUCCESS**: (0X00) pomyślnie przeprowadzono zmianę czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2727">**TX_SUCCESS**: (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="8bb39-2728">TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2728">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="8bb39-2729">TX_TICK_ERROR: (0x16) Nieprawidłowa wartość (zero) dostarczona dla początkowych taktów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2729">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="8bb39-2730">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2730">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2731">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2731">Allowed From</span></span>

<span data-ttu-id="8bb39-2732">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2732">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2733">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2733">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2734">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2734">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2735">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2735">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2736">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2736">See Also</span></span>

- <span data-ttu-id="8bb39-2737">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2737">tx_timer_activate</span></span>
- <span data-ttu-id="8bb39-2738">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2738">tx_timer_create</span></span>
- <span data-ttu-id="8bb39-2739">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2739">tx_timer_deactivate</span></span>
- <span data-ttu-id="8bb39-2740">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2740">tx_timer_delete</span></span>
- <span data-ttu-id="8bb39-2741">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2741">tx_timer_info_get</span></span>
- <span data-ttu-id="8bb39-2742">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2742">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2743">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2743">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="8bb39-2744">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2744">tx_timer_create</span></span>

<span data-ttu-id="8bb39-2745">Utwórz czasomierz aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2745">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2746">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2746">Prototype</span></span>

```C
UINT tx_timer_create(TX_TIMER *timer_ptr, CHAR *name_ptr,
                          VOID (*expiration_function)(ULONG),
                          ULONG expiration_input, ULONG initial_ticks,
                          ULONG reschedule_ticks, UINT auto_activate)
```
### <a name="description"></a><span data-ttu-id="8bb39-2747">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2747">Description</span></span>

<span data-ttu-id="8bb39-2748">Ta usługa tworzy czasomierz aplikacji z określoną funkcją wygaśnięcia i okresowo.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2748">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2749">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2749">Parameters</span></span>

- <span data-ttu-id="8bb39-2750">**timer_ptr**: wskaźnik do bloku sterowania czasomierzem</span><span class="sxs-lookup"><span data-stu-id="8bb39-2750">**timer_ptr**: Pointer to a timer control block</span></span>
- <span data-ttu-id="8bb39-2751">**name_ptr**: wskaźnik do nazwy czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2751">**name_ptr**: Pointer to the name of the timer.</span></span>
- <span data-ttu-id="8bb39-2752">**expiration_function**: funkcja aplikacji do wywołania po wygaśnięciu czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2752">**expiration_function**: Application function to call when the timer expires.</span></span>
- <span data-ttu-id="8bb39-2753">**expiration_input**: dane wejściowe do przekazania do funkcji wygaśnięcia po wygaśnięciu czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2753">**expiration_input**: Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="8bb39-2754">**initial_ticks**: określa początkową liczbę taktów dla wygaśnięcia czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2754">**initial_ticks**: Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="8bb39-2755">Wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2755">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="8bb39-2756">**reschedule_ticks**: określa liczbę taktów dla wszystkich wygasających czasomierzy po pierwszej.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2756">**reschedule_ticks**: Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="8bb39-2757">Wartość zerowa dla tego parametru powoduje, że czasomierz ma czasomierz jednorazowy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2757">A zero for this parameter makes the timer a one-shot timer.</span></span> <span data-ttu-id="8bb39-2758">W przeciwnym razie dla okresowych czasomierzy wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2758">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

   > [!NOTE]
   > <span data-ttu-id="8bb39-2759">Po wygaśnięciu czasomierza z jednym zrzutem należy zresetować go za pomocą tx_timer_change, zanim będzie można go ponownie aktywować.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2759">After a one-shot timer expires, it must be reset via tx_timer_change before it can be activated again.</span></span>

- <span data-ttu-id="8bb39-2760">**Auto_Activate**: określa, czy czasomierz jest automatycznie uaktywniany podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2760">**auto_activate**: Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="8bb39-2761">Jeśli ta wartość jest **TX_AUTO_ACTIVATE** (0x01), czasomierz jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2761">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="8bb39-2762">W przeciwnym razie, jeśli wybrano wartość **TX_NO_ACTIVATE** (0x00), czasomierz zostanie utworzony w stanie nieaktywnym.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2762">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="8bb39-2763">W takim przypadku kolejne wywołanie usługi **_tx_timer_activate_** jest niezbędne do uruchomienia czasomierza w rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2763">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2764">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2764">Return Values</span></span>

- <span data-ttu-id="8bb39-2765">**TX_SUCCESS**: (0X00) pomyślne utworzenie czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2765">**TX_SUCCESS**: (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="8bb39-2766">TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2766">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="8bb39-2767">Wskaźnik ma wartość NULL lub czasomierz został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2767">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="8bb39-2768">TX_TICK_ERROR: (0x16) Nieprawidłowa wartość (zero) dostarczona dla początkowych taktów.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2768">TX_TICK_ERROR: (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="8bb39-2769">TX_ACTIVATE_ERROR: (0x17) wybrano nieprawidłową aktywację.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2769">TX_ACTIVATE_ERROR: (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="8bb39-2770">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2770">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2771">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2771">Allowed From</span></span>

<span data-ttu-id="8bb39-2772">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-2772">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2773">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2773">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2774">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2774">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2775">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2775">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2776">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2776">See Also</span></span>

- <span data-ttu-id="8bb39-2777">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2777">tx_timer_activate</span></span>
- <span data-ttu-id="8bb39-2778">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2778">tx_timer_change</span></span>
- <span data-ttu-id="8bb39-2779">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2779">tx_timer_deactivate</span></span>
- <span data-ttu-id="8bb39-2780">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2780">tx_timer_delete</span></span>
- <span data-ttu-id="8bb39-2781">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2781">tx_timer_info_get</span></span>
- <span data-ttu-id="8bb39-2782">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2782">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2783">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2783">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="8bb39-2784">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2784">tx_timer_deactivate</span></span>

<span data-ttu-id="8bb39-2785">Dezaktywuj czasomierz aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2785">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2786">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2786">Prototype</span></span>

```C
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="8bb39-2787">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2787">Description</span></span>

<span data-ttu-id="8bb39-2788">Ta usługa dezaktywuje określony czasomierz aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2788">This service deactivates the specified application timer.</span></span> <span data-ttu-id="8bb39-2789">Jeśli czasomierz został już zdezaktywowany, ta usługa nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2789">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2790">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2790">Parameters</span></span> 

- <span data-ttu-id="8bb39-2791">**timer_ptr**: wskaźnik do wcześniej utworzonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2791">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2792">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2792">Return Values</span></span>

- <span data-ttu-id="8bb39-2793">**TX_SUCCESS**: (0x00) pomyślna dezaktywacja czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2793">**TX_SUCCESS**: (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="8bb39-2794">TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2794">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2795">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2795">Allowed From</span></span>

<span data-ttu-id="8bb39-2796">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2796">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2797">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2797">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2798">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2798">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2799">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2799">Example</span></span>

```C
TX_TIMER     my_timer;
UINT         status;

/* Deactivate an application timer. Assume that the
   application timer has already been created. */
status =  tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   now deactivated. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2800">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2800">See Also</span></span>

- <span data-ttu-id="8bb39-2801">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2801">tx_timer_activate</span></span>
- <span data-ttu-id="8bb39-2802">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2802">tx_timer_change</span></span>
- <span data-ttu-id="8bb39-2803">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2803">tx_timer_create</span></span>
- <span data-ttu-id="8bb39-2804">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2804">tx_timer_delete</span></span>
- <span data-ttu-id="8bb39-2805">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2805">tx_timer_info_get</span></span>
- <span data-ttu-id="8bb39-2806">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2806">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2807">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2807">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="8bb39-2808">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2808">tx_timer_delete</span></span>

<span data-ttu-id="8bb39-2809">Usuń czasomierz aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2809">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2810">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2810">Prototype</span></span>

```C
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-2811">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2811">Description</span></span>

<span data-ttu-id="8bb39-2812">Ta usługa usuwa określony czasomierz aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2812">This service deletes the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2813">Jest to odpowiedzialność aplikacji, aby uniemożliwić korzystanie z usuniętego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2813">It is the application’s responsibility to prevent use of a deleted timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2814">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2814">Parameters</span></span> 

- <span data-ttu-id="8bb39-2815">**timer_ptr**: wskaźnik do wcześniej utworzonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2815">**timer_ptr**: Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2816">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2816">Return Values</span></span>

- <span data-ttu-id="8bb39-2817">**TX_SUCCESS**: (0X00) pomyślne usunięcie czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2817">**TX_SUCCESS**: (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="8bb39-2818">TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2818">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="8bb39-2819">TX_CALLER_ERROR: (0x13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2819">TX_CALLER_ERROR: (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2820">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2820">Allowed From</span></span>

<span data-ttu-id="8bb39-2821">Wątki</span><span class="sxs-lookup"><span data-stu-id="8bb39-2821">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2822">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2822">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2823">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2823">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2824">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2824">Example</span></span>

```c
TX_TIMER     my_timer;
UINT         status;

/* Delete application timer. Assume that the application
   timer has already been created. */
status =  tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
   deleted. */
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2825">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2825">See Also</span></span>

- <span data-ttu-id="8bb39-2826">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2826">tx_timer_activate</span></span>
- <span data-ttu-id="8bb39-2827">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2827">tx_timer_change</span></span>
- <span data-ttu-id="8bb39-2828">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2828">tx_timer_create</span></span>
- <span data-ttu-id="8bb39-2829">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2829">tx_timer_deactivate</span></span>
- <span data-ttu-id="8bb39-2830">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2830">tx_timer_info_get</span></span>
- <span data-ttu-id="8bb39-2831">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2831">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2832">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2832">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="8bb39-2833">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2833">tx_timer_info_get</span></span>

<span data-ttu-id="8bb39-2834">Pobierz informacje o czasomierzu aplikacji</span><span class="sxs-lookup"><span data-stu-id="8bb39-2834">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2835">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2835">Prototype</span></span>

```C
UINT tx_timer_info_get(TX_TIMER *timer_ptr, CHAR **name,
                          UINT *active, ULONG *remaining_ticks,
                          ULONG *reschedule_ticks,
                          TX_TIMER **next_timer)
```
### <a name="description"></a><span data-ttu-id="8bb39-2836">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2836">Description</span></span>

<span data-ttu-id="8bb39-2837">Ta usługa pobiera informacje o określonym czasomierzu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2837">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2838">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2838">Parameters</span></span>

- <span data-ttu-id="8bb39-2839">**timer_ptr**: wskaźnik do wcześniej utworzonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2839">**timer_ptr**: Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="8bb39-2840">**name**: wskaźnik do miejsca docelowego dla wskaźnika do nazwy czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2840">**name**: Pointer to destination for the pointer to the timer’s name.</span></span>
- <span data-ttu-id="8bb39-2841">**aktywny**: wskaźnik do miejsca docelowego dla aktywnego wskaźnika czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2841">**active**: Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="8bb39-2842">Jeśli czasomierz jest nieaktywny lub ta usługa jest wywoływana z samego czasomierza, zwracana jest wartość TX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2842">If the timer is inactive or this service is called from the timer itself, a TX_FALSE value is returned.</span></span> <span data-ttu-id="8bb39-2843">W przeciwnym razie, jeśli czasomierz jest aktywny, zwracana jest wartość TX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2843">Otherwise, if the timer is active, a TX_TRUE value is returned.</span></span>
- <span data-ttu-id="8bb39-2844">**remaining_ticks**: wskaźnik do miejsca docelowego dla liczby cykli czasomierza pozostawionych przed wygaśnięciem czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2844">**remaining_ticks**: Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="8bb39-2845">**reschedule_ticks**: wskaźnik do miejsca docelowego dla liczby taktów czasomierza, który zostanie użyty do automatycznego ponownego zaplanowania tego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2845">**reschedule_ticks**: Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="8bb39-2846">Jeśli wartość jest równa zero, czasomierz jest jednorazowy i nie zostanie ponownie zaplanowany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2846">If the value is zero, then the timer is a one-shot and won’t be rescheduled.</span></span>
- <span data-ttu-id="8bb39-2847">**next_timer**: wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2847">**next_timer**: Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="8bb39-2848">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2848">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2849">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2849">Return Values</span></span>

- <span data-ttu-id="8bb39-2850">**TX_SUCCESS**: (0X00) pomyślne pobranie informacji czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2850">**TX_SUCCESS**: (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="8bb39-2851">TX_TIMER_ERROR: (0x15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2851">TX_TIMER_ERROR: (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2852">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2852">Allowed From</span></span>

<span data-ttu-id="8bb39-2853">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2853">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="8bb39-2854">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2854">Preemption Possible</span></span>

<span data-ttu-id="8bb39-2855">Nie</span><span class="sxs-lookup"><span data-stu-id="8bb39-2855">No</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2856">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2856">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2857">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2857">See Also</span></span>

- <span data-ttu-id="8bb39-2858">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2858">tx_timer_activate</span></span>
- <span data-ttu-id="8bb39-2859">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2859">tx_timer_change</span></span>
- <span data-ttu-id="8bb39-2860">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2860">tx_timer_create</span></span>
- <span data-ttu-id="8bb39-2861">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2861">tx_timer_deactivate</span></span>
- <span data-ttu-id="8bb39-2862">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2862">tx_timer_delete</span></span>
- <span data-ttu-id="8bb39-2863">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2863">tx_timer_info_get</span></span>
- <span data-ttu-id="8bb39-2864">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2864">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="8bb39-2865">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2865">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="8bb39-2866">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2866">tx_timer_performance_info_get</span></span> 

<span data-ttu-id="8bb39-2867">Pobierz informacje o wydajności czasomierza</span><span class="sxs-lookup"><span data-stu-id="8bb39-2867">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2868">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2868">Prototype</span></span>

```C
UINT  tx_timer_performance_info_get(TX_TIMER *timer_ptr,
        ULONG *activates, ULONG *reactivates,
        ULONG *deactivates, ULONG *expirations,
        ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="8bb39-2869">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2869">Description</span></span>

<span data-ttu-id="8bb39-2870">Ta usługa pobiera informacje o wydajności dotyczące określonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2870">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2871">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_TIMER_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2871">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2872">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2872">Parameters</span></span> 

- <span data-ttu-id="8bb39-2873">**timer_ptr**: wskaźnik do wcześniej utworzonego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2873">**timer_ptr**: Pointer to previously created timer.</span></span>
- <span data-ttu-id="8bb39-2874">**aktywuje**: wskaźnik do miejsca docelowego dla liczby żądań aktywacji wykonanych dla tego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2874">**activates**: Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="8bb39-2875">**reactivates**: wskaźnik do miejsca docelowego dla liczby automatycznych ponownych aktywacji wykonanych na tym cyklicznym czasomierzu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2875">**reactivates**: Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="8bb39-2876">**dezaktywuje**: wskaźnik do miejsca docelowego dla liczby żądań dezaktywacji wykonanych dla tego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2876">**deactivates**: Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="8bb39-2877">**wygaśnięcia**: wskaźnik do miejsca docelowego dla liczby wygaśnięć tego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2877">**expirations**: Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="8bb39-2878">**expiration_adjusts**: wskaźnik do miejsca docelowego dla liczby wewnętrznych korekt wygaśnięcia wykonanych dla tego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2878">**expiration_adjusts**: Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="8bb39-2879">Te korekty są wykonywane w ramach przetwarzania przerwań czasomierza dla czasomierzy, które są większe niż domyślny rozmiar listy czasomierza (domyślnie czasomierze o wygasaniu większym niż 32 taktów).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2879">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2880">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2880">Supplying a TX_NULL for any parameter indicates the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2881">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2881">Return Values</span></span>

- <span data-ttu-id="8bb39-2882">**TX_SUCCESS**: (0X00) pomyślne pobieranie wydajności czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2882">**TX_SUCCESS**: (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="8bb39-2883">**TX_PTR_ERROR**: (0X03) Nieprawidłowy wskaźnik czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2883">**TX_PTR_ERROR**: (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="8bb39-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2884">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2885">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2885">Allowed From</span></span>

<span data-ttu-id="8bb39-2886">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2886">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2887">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2887">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2888">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2888">See Also</span></span>

- <span data-ttu-id="8bb39-2889">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2889">tx_timer_activate</span></span>
- <span data-ttu-id="8bb39-2890">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2890">tx_timer_change</span></span>
- <span data-ttu-id="8bb39-2891">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2891">tx_timer_create</span></span>
- <span data-ttu-id="8bb39-2892">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2892">tx_timer_deactivate</span></span>
- <span data-ttu-id="8bb39-2893">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2893">tx_timer_delete</span></span>
- <span data-ttu-id="8bb39-2894">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2894">tx_timer_info_get</span></span>
- <span data-ttu-id="8bb39-2895">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2895">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="8bb39-2896">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2896">tx_timer_performance_system_info_get</span></span> 

<span data-ttu-id="8bb39-2897">Pobierz informacje o wydajności systemu czasomierza</span><span class="sxs-lookup"><span data-stu-id="8bb39-2897">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2898">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2898">Prototype</span></span>

```C
UINT  tx_timer_performance_system_info_get(ULONG *activates,
        ULONG *reactivates, ULONG *deactivates,
        ULONG *expirations, ULONG *expiration_adjusts);
```
### <a name="description"></a><span data-ttu-id="8bb39-2899">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2899">Description</span></span>

<span data-ttu-id="8bb39-2900">Ta usługa pobiera informacje o wydajności wszystkich czasomierzy aplikacji w systemie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2900">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2901">Biblioteka i aplikacja SMP ThreadX muszą zostać skompilowane przy użyciu **TX_TIMER_ENABLE_PERFORMANCE_INFO** zdefiniowanych dla tej usługi w celu zwrócenia informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2901">The ThreadX SMP library and application must be built with **TX_TIMER_ENABLE_PERFORMANCE_INFO** defined for this service to return performance information.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2902">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2902">Parameters</span></span>

- <span data-ttu-id="8bb39-2903">**aktywuje**: wskaźnik do miejsca docelowego dla łącznej liczby żądań aktywacji wykonanych na wszystkich czasomierzach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2903">**activates**: Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="8bb39-2904">**reactivates**: wskaźnik do miejsca docelowego dla łącznej liczby automatycznych ponownych aktywacji wykonanych na wszystkich okresowych czasomierzach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2904">**reactivates**: Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="8bb39-2905">**dezaktywuje**: wskaźnik do miejsca docelowego dla łącznej liczby żądań dezaktywacji wykonanych na wszystkich czasomierzach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2905">**deactivates**: Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="8bb39-2906">**wygaśnięcia**: wskaźnik do miejsca docelowego dla łącznej liczby wygaśnięć dla wszystkich czasomierzy.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2906">**expirations**: Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="8bb39-2907">**expiration_adjusts**: wskaźnik do miejsca docelowego dla łącznej liczby wewnętrznych korekt wygaśnięcia wykonanych na wszystkich czasomierzach.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2907">**expiration_adjusts**: Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="8bb39-2908">Te korekty są wykonywane w ramach przetwarzania przerwań czasomierza dla czasomierzy, które są większe niż domyślny rozmiar listy czasomierza (domyślnie czasomierze o wygasaniu większym niż 32 taktów).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2908">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2909">Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2909">Supplying a TX_NULL for any parameter indicates that the parameter is not required.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2910">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2910">Return Values</span></span>

- <span data-ttu-id="8bb39-2911">**TX_SUCCESS**: (0X00) pomyślne uzyskanie czasomierza wydajności systemu.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2911">**TX_SUCCESS**: (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="8bb39-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2912">**TX_FEATURE_NOT_ENABLED**: (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2913">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2913">Allowed From</span></span>

<span data-ttu-id="8bb39-2914">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="8bb39-2914">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2915">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2915">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="8bb39-2916">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2916">See Also</span></span>

- <span data-ttu-id="8bb39-2917">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2917">tx_timer_activate</span></span>
- <span data-ttu-id="8bb39-2918">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="8bb39-2918">tx_timer_change</span></span>
- <span data-ttu-id="8bb39-2919">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="8bb39-2919">tx_timer_create</span></span>
- <span data-ttu-id="8bb39-2920">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="8bb39-2920">tx_timer_deactivate</span></span>
- <span data-ttu-id="8bb39-2921">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="8bb39-2921">tx_timer_delete</span></span>
- <span data-ttu-id="8bb39-2922">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2922">tx_timer_info_get</span></span>
- <span data-ttu-id="8bb39-2923">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2923">tx_timer_performance_info_get</span></span>

## <a name="tx_timer_smp_core_exclude"></a><span data-ttu-id="8bb39-2924">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="8bb39-2924">tx_timer_smp_core_exclude</span></span>

<span data-ttu-id="8bb39-2925">Wyklucz wykonywanie czasomierza na zestawie rdzeni</span><span class="sxs-lookup"><span data-stu-id="8bb39-2925">Exclude timer execution on a set of cores</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2926">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2926">Prototype</span></span>

```C
UINT  tx_timer_smp_core_exclude(TX_TIMER *timer_ptr, ULONG exclusion_map);
```
### <a name="description"></a><span data-ttu-id="8bb39-2927">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2927">Description</span></span>

<span data-ttu-id="8bb39-2928">Ta funkcja wyklucza określony czasomierz z wykonywania na rdzeniach określonych w mapie bitowej o nazwie "*exclusion_map*".</span><span class="sxs-lookup"><span data-stu-id="8bb39-2928">This function excludes the specified timer from executing on the core(s) specified in the bit map called "*exclusion_map*."</span></span> <span data-ttu-id="8bb39-2929">Każdy bit w "*exclusion_map*" reprezentuje rdzeń (bit 0 reprezentuje rdzeń 0 itd.).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2929">Each bit in "*exclusion_map*" represents a core (bit 0 represents core 0, etc.).</span></span> <span data-ttu-id="8bb39-2930">Jeśli bit jest ustawiony, odpowiadający rdzeń jest wykluczony z wykonywania określonego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2930">If the bit is set, the corresponding core is excluded from executing the specified timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8bb39-2931">Użycie wykluczenia procesora może spowodować dodatkowe przetwarzanie w wątku do podstawowej logiki mapowania, aby znaleźć optymalne dopasowanie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2931">Use of processor exclusion may cause additional processing in the thread to core mapping logic in order to find the optimal match.</span></span> <span data-ttu-id="8bb39-2932">To przetwarzanie jest ograniczone przez liczbę gotowych wątków.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2932">This processing is bounded by the number of ready threads.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2933">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2933">Parameters</span></span>

- <span data-ttu-id="8bb39-2934">**timer_ptr**: wskaźnik do czasomierza, aby zmienić wykluczenia rdzenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2934">**timer_ptr**: Pointer to timer to change the core exclusion.</span></span>
- <span data-ttu-id="8bb39-2935">**exclusion_map**: Mapa bitowa, gdzie bit Sit wskazuje, że rdzeń jest wykluczony.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2935">**exclusion_map**: Bit map where a sit bit indicates that that core is excluded.</span></span> <span data-ttu-id="8bb39-2936">Dostarczenie wartości 0 powoduje, że czasomierz będzie wykonywany na dowolnym rdzeniu (domyślnie).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2936">Supplying a 0 value enables the timer to execute on any core (default).</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2937">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2937">Return Values</span></span>

- <span data-ttu-id="8bb39-2938">Wykluczenie rdzenia **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="8bb39-2938">**TX_SUCCESS** (0x00) Successful core exclusion.</span></span>
- <span data-ttu-id="8bb39-2939">**TX_TIMER_ERROR** (0X0E) Nieprawidłowy wskaźnik czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2939">**TX_TIMER_ERROR** (0x0E) Invalid timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2940">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2940">Allowed From</span></span>

<span data-ttu-id="8bb39-2941">Inicjalizacja, procedury ISR, wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-2941">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2942">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2942">Example</span></span>

```C
/* Exclude core 0 for "Timer 0". */
tx_timer_smp_core_exclude(&timer_0, 0x01);
```

### <a name="see-also"></a><span data-ttu-id="8bb39-2943">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2943">See Also</span></span>

- <span data-ttu-id="8bb39-2944">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2944">tx_timer_smp_core_exclude_get</span></span>

## <a name="tx_timer_smp_core_exclude_get"></a><span data-ttu-id="8bb39-2945">tx_timer_smp_core_exclude_get</span><span class="sxs-lookup"><span data-stu-id="8bb39-2945">tx_timer_smp_core_exclude_get</span></span>

<span data-ttu-id="8bb39-2946">Pobiera bieżące wykluczenie rdzenia czasomierza</span><span class="sxs-lookup"><span data-stu-id="8bb39-2946">Gets the timer's current core exclusion</span></span>

### <a name="prototype"></a><span data-ttu-id="8bb39-2947">Prototype</span><span class="sxs-lookup"><span data-stu-id="8bb39-2947">Prototype</span></span>

```C
UINT tx_timer_smp_core_exclude_get(TX_TIMER *timer_ptr,
                         ULONG *exclusion_map_ptr);
```
### <a name="description"></a><span data-ttu-id="8bb39-2948">Opis</span><span class="sxs-lookup"><span data-stu-id="8bb39-2948">Description</span></span>

<span data-ttu-id="8bb39-2949">Ta funkcja zwraca bieżącą listę wykluczeń rdzeni.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2949">This function returns the current core exclusion list.</span></span>

### <a name="parameters"></a><span data-ttu-id="8bb39-2950">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bb39-2950">Parameters</span></span>

- <span data-ttu-id="8bb39-2951">**timer_ptr**: wskaźnik do czasomierza, z którego ma zostać pobrane podstawowe wykluczenie.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2951">**timer_ptr**: Pointer to timer from which to retrieve the core exclusion.</span></span>
- <span data-ttu-id="8bb39-2952">**exclusion_map_ptr**: miejsce docelowe dla bieżącej mapy bitowej wykluczeń podstawowych.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2952">**exclusion_map_ptr**: Destination for current core exclusion bit map.</span></span>

### <a name="return-values"></a><span data-ttu-id="8bb39-2953">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="8bb39-2953">Return Values</span></span>

- <span data-ttu-id="8bb39-2954">TX_SUCCESS: (0x00) pomyślne pobranie wykluczenia rdzenia czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2954">TX_SUCCESS: (0x00) Successful retrieval of timer's core exclusion.</span></span>
- <span data-ttu-id="8bb39-2955">TX_TIMER_ERROR: (0x0E) Nieprawidłowy wskaźnik czasomierza.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2955">TX_TIMER_ERROR: (0x0E) Invalid timer pointer.</span></span>
- <span data-ttu-id="8bb39-2956">TX_PTR_ERROR: (0x03) Nieprawidłowy wskaźnik docelowy wykluczenia.</span><span class="sxs-lookup"><span data-stu-id="8bb39-2956">TX_PTR_ERROR: (0x03) Invalid exclusion destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8bb39-2957">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="8bb39-2957">Allowed From</span></span>

<span data-ttu-id="8bb39-2958">Inicjalizacja, procedury ISR, wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="8bb39-2958">Initialization, ISRs, threads, and timers</span></span>

### <a name="example"></a><span data-ttu-id="8bb39-2959">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bb39-2959">Example</span></span>

```C
ULONGexcluded_cores;

/* Retrieve the core exclusion for "Timer 0". */
tx_timer_smp_core_exclude_get(&timer_0,&excluded_cores);
```
### <a name="see-also"></a><span data-ttu-id="8bb39-2960">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bb39-2960">See Also</span></span>

- <span data-ttu-id="8bb39-2961">tx_timer_smp_core_exclude</span><span class="sxs-lookup"><span data-stu-id="8bb39-2961">tx_timer_smp_core_exclude</span></span>