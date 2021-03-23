---
title: Rozdział 6 — zdarzenia śledzenia usługi Azure RTO ThreadX
description: W tym rozdziale opisano zdarzenia usługi Azure RTO ThreadX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8f0ff03d112597371059d925f64b7511454e123c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823460"
---
# <a name="chapter-6---azure-rtos-threadx-trace-events"></a><span data-ttu-id="af64b-103">Rozdział 6 — zdarzenia śledzenia usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="af64b-103">Chapter 6 - Azure RTOS ThreadX trace events</span></span>

<span data-ttu-id="af64b-104">W tym rozdziale opisano zdarzenia usługi Azure RTO ThreadX.</span><span class="sxs-lookup"><span data-stu-id="af64b-104">This chapter describes the Azure RTOS ThreadX events.</span></span> 

## <a name="list-of-events-and-icons"></a><span data-ttu-id="af64b-105">Lista zdarzeń i ikon</span><span class="sxs-lookup"><span data-stu-id="af64b-105">List of Events and Icons</span></span>

<span data-ttu-id="af64b-106">Poniżej znajduje się lista zdarzeń ThreadX wyświetlanych przez TraceX:</span><span class="sxs-lookup"><span data-stu-id="af64b-106">The following is a list of ThreadX events displayed by TraceX:</span></span>

| <span data-ttu-id="af64b-107">**Ikona**</span><span class="sxs-lookup"><span data-stu-id="af64b-107">**Icon**</span></span>                         | <span data-ttu-id="af64b-108">**Znaczenie**</span><span class="sxs-lookup"><span data-stu-id="af64b-108">**Meaning**</span></span> |
| -------------------------------- | ------------------------------------- |
| ![Ikona wznowienia wątku wewnętrznego](./media/user-guide/tx-events/image1.png)    | <span data-ttu-id="af64b-110">Wewnętrzny wznowienie wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-110">Internal thread resume</span></span>  |
| ![Ikona wstrzymania wątku wewnętrznego](./media/user-guide/tx-events/image2.png)    | <span data-ttu-id="af64b-112">Zawieszenie wątku wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="af64b-112">Internal thread suspend</span></span> |
| ![Ikona przejścia do procedury usługi przerwania](./media/user-guide/tx-events/image3.png)    | <span data-ttu-id="af64b-114">Wejście procedury usługi przerwania (ISR)</span><span class="sxs-lookup"><span data-stu-id="af64b-114">Interrupt Service Routine (ISR) Enter</span></span> |
| ![Ikona zakończenia procedury usługi przerwania](./media/user-guide/tx-events/image4.png)    | <span data-ttu-id="af64b-116">Zakończenie procedury usługi przerwania (ISR)</span><span class="sxs-lookup"><span data-stu-id="af64b-116">Interrupt Service Routine (ISR) Exit</span></span>  |
| ![Ikona wewnętrznego wycinka czasu](./media/user-guide/tx-events/image5.png)    | <span data-ttu-id="af64b-118">Wewnętrzny czas wycinka</span><span class="sxs-lookup"><span data-stu-id="af64b-118">Internal time-slice</span></span> |
| ![Ikona uruchamiania](./media/user-guide/tx-events/image6.png)    | <span data-ttu-id="af64b-120">Uruchomienie</span><span class="sxs-lookup"><span data-stu-id="af64b-120">Running</span></span> |
| ![Ikona blokowania alokacji puli](./media/user-guide/tx-events/image7.png)    | <span data-ttu-id="af64b-122">**Przydziel pulę bloków** (*tx_block_allocate*)</span><span class="sxs-lookup"><span data-stu-id="af64b-122">**Block pool allocate** (*tx_block_allocate*)</span></span>  |
| ![Ikona tworzenia puli blokowej](./media/user-guide/tx-events/image8.png)    | <span data-ttu-id="af64b-124">**Blokuj Tworzenie puli** (*tx_block_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="af64b-124">**Block pool create** (*tx_block_pool_create*)</span></span> |
| ![Ikona usuwania puli blokowej](./media/user-guide/tx-events/image9.png)    | <span data-ttu-id="af64b-126">**Blokuj Usuwanie puli** (*tx_block_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="af64b-126">**Block pool delete** (*tx_block_pool_delete*)</span></span> |
| ![Ikona uzyskiwania informacji o puli bloku](./media/user-guide/tx-events/image10.png)    | <span data-ttu-id="af64b-128">**Pobierz informacje o puli bloków** (*tx_block_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-128">**Block pool information get** (*tx_block_pool_info_get*)</span></span> |
| ![Informacje o wydajności puli bloku](./media/user-guide/tx-events/image11.png)    | <span data-ttu-id="af64b-130">**Uzyskaj informacje o wydajności puli bloku** (*tx_block_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-130">**Block pool performance information get** (*tx_block_pool_performance_info_get*)</span></span> |
| ![Ikona blokowania informacji o wydajności systemu puli](./media/user-guide/tx-events/image12.png)    | <span data-ttu-id="af64b-132">**Odczytaj informacje o wydajności systemu puli** (*tx_block_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-132">**Block pool system performance information get** (*tx_block_pool_performance_system_info_get*)</span></span> |
| ![Ikona zablokowania priorytetów puli](./media/user-guide/tx-events/image13.png)    | <span data-ttu-id="af64b-134">**Zablokuj priorytety puli** (*tx_block_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="af64b-134">**Block pool prioritize** (*tx_block_pool_prioritize*)</span></span> |
| ![Ikona blokowania wersji do puli](./media/user-guide/tx-events/image14.png)    | <span data-ttu-id="af64b-136">**Blokuj wydanie do puli** (*tx_block_release*)</span><span class="sxs-lookup"><span data-stu-id="af64b-136">**Block release to pool** (*tx_block_release*)</span></span> |
| ![Ikona pamięci przydziału puli bajtów](./media/user-guide/tx-events/image15.png)    | <span data-ttu-id="af64b-138">**Alokacja pamięci w puli bajtów** (*tx_byte_allocate*)</span><span class="sxs-lookup"><span data-stu-id="af64b-138">**Byte pool allocate memory** (*tx_byte_allocate*)</span></span> |
| ![Ikona tworzenia puli bajtów](./media/user-guide/tx-events/image16.png)    | <span data-ttu-id="af64b-140">**Tworzenie puli bajtów** (*tx_byte_pool_create*)</span><span class="sxs-lookup"><span data-stu-id="af64b-140">**Byte pool create** (*tx_byte_pool_create*)</span></span> |
| ![Ikona usuwania puli bajtów](./media/user-guide/tx-events/image17.png)    | <span data-ttu-id="af64b-142">**Usuwanie puli bajtów** (*tx_byte_pool_delete*)</span><span class="sxs-lookup"><span data-stu-id="af64b-142">**Byte pool delete** (*tx_byte_pool_delete*)</span></span> |
| ![Ikona pobierania informacji o puli bajtów](./media/user-guide/tx-events/image18.png)    | <span data-ttu-id="af64b-144">**Pobieranie informacji o puli bajtów** (*tx_byte_pool_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-144">**Byte pool information get** (*tx_byte_pool_info_get*)</span></span> |
| ![Ikona uzyskiwania informacji o wydajności puli bajtów](./media/user-guide/tx-events/image19.png)    | <span data-ttu-id="af64b-146">**Pobieranie informacji o wydajności puli bajtów** (*tx_byte_pool_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-146">**Byte pool performance information get** (*tx_byte_pool_performance_info_get*)</span></span> |
| ![Ikona uzyskiwania informacji o wydajności systemu puli bajtów](./media/user-guide/tx-events/image20.png)    | <span data-ttu-id="af64b-148">**Pobieranie informacji o wydajności systemu w puli bajtów** (*tx_byte_pool_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-148">**Byte pool system performance information get** (*tx_byte_pool_performance_system_info_get*)</span></span> |
| ![Ikona priorytet puli bajtów](./media/user-guide/tx-events/image21.png)    | <span data-ttu-id="af64b-150">**Priorytetyzacja puli bajtów** (*tx_byte_pool_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="af64b-150">**Byte pool prioritize** (*tx_byte_pool_prioritize*)</span></span> |
| ![Ikona zwalniania pamięci do puli](./media/user-guide/tx-events/image22.png)    | <span data-ttu-id="af64b-152">**Zwolnij pamięć w puli** (*tx_byte_release*)</span><span class="sxs-lookup"><span data-stu-id="af64b-152">**Byte memory release to pool** (*tx_byte_release*)</span></span> |
| ![Ikona tworzenia flag zdarzeń](./media/user-guide/tx-events/image23.png)    | <span data-ttu-id="af64b-154">**Flagi zdarzeń Create** (*tx_event_flags_create*)</span><span class="sxs-lookup"><span data-stu-id="af64b-154">**Event flags create** (*tx_event_flags_create*)</span></span> |
| ![Ikona usuwania flag zdarzeń](./media/user-guide/tx-events/image24.png)    | <span data-ttu-id="af64b-156">**Flagi zdarzenia Delete** (*tx_event_flags_delete*)</span><span class="sxs-lookup"><span data-stu-id="af64b-156">**Event flags delete** (*tx_event_flags_delete*)</span></span> |
| ![Ikona pobierania flag zdarzeń](./media/user-guide/tx-events/image25.png)    | <span data-ttu-id="af64b-158">**Flagi zdarzenia Get** (*tx_event_flags_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-158">**Event flags get** (*tx_event_flags_get*)</span></span> |
| ![Ikona uzyskiwania informacji o flagach zdarzeń](./media/user-guide/tx-events/image26.png)    | <span data-ttu-id="af64b-160">**Informacje o flagach zdarzenia Get** (*tx_event_flags_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-160">**Event flags information get** (*tx_event_flags_info_get*)</span></span> |
| ![Ikona uzyskiwania informacji o wydajności flag zdarzeń](./media/user-guide/tx-events/image27.png)    | <span data-ttu-id="af64b-162">**Informacje o wydajności flag zdarzeń Get** (*tx_event_flags_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-162">**Event flags performance information get** (*tx_event_flags_performance_info_get*)</span></span> |
| ![Ikona zdarzenia informacje o wydajności systemu](./media/user-guide/tx-events/image28.png)    | <span data-ttu-id="af64b-164">**Flagi zdarzeń pobieranie informacji o wydajności systemu** (*tx_event_flags_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-164">**Event flags system performance information get** (*tx_event_flags_performance_system_info_get*)</span></span> |
| ![Ikona zestawu flag zdarzeń](./media/user-guide/tx-events/image29.png)    | <span data-ttu-id="af64b-166">**Ustawione flagi zdarzeń** (*tx_event_flags_set*)</span><span class="sxs-lookup"><span data-stu-id="af64b-166">**Event flags set** (*tx_event_flags_set*)</span></span> |
| ![Ikona powiadomienia ustawiona flaga zdarzenia](./media/user-guide/tx-events/image30.png)    | <span data-ttu-id="af64b-168">**Ustawianie flag zdarzeń powiadamiania** (*tx_event_flags_set_notify*)</span><span class="sxs-lookup"><span data-stu-id="af64b-168">**Event flags set notify** (*tx_event_flags_set_notify*)</span></span> |
| ![Ikona włączania/wyłączania przerwań](./media/user-guide/tx-events/image31.png)    | <span data-ttu-id="af64b-170">**Włącz/Wyłącz przerwania** (*tx_interrupt_control*)</span><span class="sxs-lookup"><span data-stu-id="af64b-170">**Interrupt enable/disable** (*tx_interrupt_control*)</span></span> |
| ![Ikona tworzenia obiektu mutex](./media/user-guide/tx-events/image32.png)    | <span data-ttu-id="af64b-172">**Tworzenie obiektu mutex** (*tx_mutex_create*)</span><span class="sxs-lookup"><span data-stu-id="af64b-172">**Mutex create** (*tx_mutex_create*)</span></span> |
| ![Ikona usuwania muteksu](./media/user-guide/tx-events/image33.png)    | <span data-ttu-id="af64b-174">**Usuwanie obiektu mutex** (*tx_mutex_delete*)</span><span class="sxs-lookup"><span data-stu-id="af64b-174">**Mutex delete** (*tx_mutex_delete*)</span></span> |
| ![Ikona pobierania muteksu](./media/user-guide/tx-events/image34.png)    | <span data-ttu-id="af64b-176">**Pobieranie obiektu mutex** (*tx_mutex_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-176">**Mutex get** (*tx_mutex_get*)</span></span> |
| ![Ikona pobierania informacji o muteksie](./media/user-guide/tx-events/image35.png)    | <span data-ttu-id="af64b-178">**Pobieranie informacji o muteksie** (*tx_mutex_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-178">**Mutex information get** (*tx_mutex_info_get*)</span></span> |
| ![Ikona pobierania informacji o wydajności muteksu](./media/user-guide/tx-events/image36.png)    | <span data-ttu-id="af64b-180">**Pobieranie informacji o wydajności muteksu** (*tx_mutex_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-180">**Mutex performance information get** (*tx_mutex_performance_info_get*)</span></span> |
| ![Ikona uzyskiwania informacji o wydajności systemu muteksu](./media/user-guide/tx-events/image37.png)    | <span data-ttu-id="af64b-182">**Pobieranie informacji o wydajności systemu muteksu** (*tx_mutex_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-182">**Mutex system performance information get** (*tx_mutex_performance_system_info_get*)</span></span> |
| ![Ikona priorytetyzacji obiektu mutex](./media/user-guide/tx-events/image38.png)    | <span data-ttu-id="af64b-184">**Priorytetyzacja obiektu mutex** (*tx_mutex_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="af64b-184">**Mutex prioritize** (*tx_mutex_prioritize*)</span></span> |
| ![Ikona Put obiektu mutex](./media/user-guide/tx-events/image39.png)    | <span data-ttu-id="af64b-186">**Put muteksu** (*tx_mutex_put*)</span><span class="sxs-lookup"><span data-stu-id="af64b-186">**Mutex put** (*tx_mutex_put*)</span></span> |
| ![Ikona tworzenia kolejki](./media/user-guide/tx-events/image40.png)    | <span data-ttu-id="af64b-188">**Tworzenie kolejki** (*tx_queue_create*)</span><span class="sxs-lookup"><span data-stu-id="af64b-188">**Queue create** (*tx_queue_create*)</span></span> |
| ![Ikona usuwania kolejki](./media/user-guide/tx-events/image41.png)    | <span data-ttu-id="af64b-190">**Usuwanie kolejki** (*tx_queue_delete*)</span><span class="sxs-lookup"><span data-stu-id="af64b-190">**Queue delete** (*tx_queue_delete*)</span></span> |
| ![Ikona opróżniania kolejki](./media/user-guide/tx-events/image42.png)    | <span data-ttu-id="af64b-192">**Opróżnianie kolejki** (*tx_queue_flush*)</span><span class="sxs-lookup"><span data-stu-id="af64b-192">**Queue flush** (*tx_queue_flush*)</span></span> |
| ![Ikona wysyłania z kolejki](./media/user-guide/tx-events/image43.png)    | <span data-ttu-id="af64b-194">**Wyślij fronton kolejki** (*tx_queue_front_send*)</span><span class="sxs-lookup"><span data-stu-id="af64b-194">**Queue front send** (*tx_queue_front_send*)</span></span> |
| ![Ikona pobierania informacji o kolejce](./media/user-guide/tx-events/image44.png)    | <span data-ttu-id="af64b-196">**Pobieranie informacji o kolejce** (*tx_queue_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-196">**Queue information get** (*tx_queue_info_get*)</span></span> |
| ![Ikona pobierania informacji o wydajności kolejki](./media/user-guide/tx-events/image45.png)    | <span data-ttu-id="af64b-198">**Pobierz informacje o wydajności kolejki** (*tx_queue_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-198">**Queue performance information get** (*tx_queue_performance_info_get*)</span></span> |
| ![Ikona uzyskiwania informacji o wydajności systemu kolejkowania](./media/user-guide/tx-events/image46.png)    | <span data-ttu-id="af64b-200">**Pobierz informacje o wydajności systemu** (*tx_queue_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-200">**Queue system performance information get** (*tx_queue_performance_system_info_get*)</span></span> |
| ![Ikona priorytetyzacji kolejki](./media/user-guide/tx-events/image47.png)    | <span data-ttu-id="af64b-202">**Priorytetyzacja kolejki** (*tx_queue_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="af64b-202">**Queue prioritize** (*tx_queue_prioritize*)</span></span> |
| ![Ikona komunikatu odbierania kolejki](./media/user-guide/tx-events/image48.png)    | <span data-ttu-id="af64b-204">**Komunikat odbioru kolejki** (*tx_queue_receive*)</span><span class="sxs-lookup"><span data-stu-id="af64b-204">**Queue receive message** (*tx_queue_receive*)</span></span> |
| ![Ikona wysyłania komunikatu w kolejce](./media/user-guide/tx-events/image49.png)    | <span data-ttu-id="af64b-206">**Wyślij wiadomość do kolejki** (*tx_queue_send*)</span><span class="sxs-lookup"><span data-stu-id="af64b-206">**Queue send message** (*tx_queue_send*)</span></span> |
| ![Ikona powiadomienia o wysłaniu kolejki](./media/user-guide/tx-events/image50.png)    | <span data-ttu-id="af64b-208">**Powiadomienie o wysłaniu kolejki** (*tx_queue_send_notify*)</span><span class="sxs-lookup"><span data-stu-id="af64b-208">**Queue send notify** (*tx_queue_send_notify*)</span></span> |
| ![Ikona umieszczenia sufitu semafora](./media/user-guide/tx-events/image51.png)    | <span data-ttu-id="af64b-210">**Umieszczenie sufitu semafora** (*tx_semaphore_ceiling_put*)</span><span class="sxs-lookup"><span data-stu-id="af64b-210">**Semaphore ceiling put** (*tx_semaphore_ceiling_put*)</span></span> |
| ![Ikona tworzenia semafora](./media/user-guide/tx-events/image52.png)    | <span data-ttu-id="af64b-212">**Tworzenie semafora** (*tx_semaphore_create*)</span><span class="sxs-lookup"><span data-stu-id="af64b-212">**Semaphore create** (*tx_semaphore_create*)</span></span> |
| ![Ikona usuwania semafora](./media/user-guide/tx-events/image53.png)    | <span data-ttu-id="af64b-214">**Usuwanie semafora** (*tx_semaphore_delete*)</span><span class="sxs-lookup"><span data-stu-id="af64b-214">**Semaphore delete** (*tx_semaphore_delete*)</span></span> |
| ![Ikona pobierania semafora](./media/user-guide/tx-events/image54.png)    | <span data-ttu-id="af64b-216">**Pobieranie semafora** (*tx_semaphore_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-216">**Semaphore get** (*tx_semaphore_get*)</span></span> |
| ![Ikona pobierania informacji o semaforach](./media/user-guide/tx-events/image55.png)    | <span data-ttu-id="af64b-218">**Pobieranie informacji o semaforze** (*tx_semaphore_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-218">**Semaphore information get** (*tx_semaphore_info_get*)</span></span> |
| ![Ikona pobierania informacji o wydajności semafora](./media/user-guide/tx-events/image56.png)    | <span data-ttu-id="af64b-220">**Pobieranie informacji o wydajności semaforów** (*tx_semaphroe_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-220">**Semaphore performance information get** (*tx_semaphroe_performance_info_get*)</span></span> |
| ![Ikona uzyskiwania informacji o wydajności systemu semafora](./media/user-guide/tx-events/image57.png)    | <span data-ttu-id="af64b-222">**Pobieranie informacji o wydajności systemu semaforów** (*tx_semaphore_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-222">**Semaphore system performance information get** (*tx_semaphore_performance_system_info_get*)</span></span> |
| ![Ikona priorytetyzacji semaforów](./media/user-guide/tx-events/image58.png)    | <span data-ttu-id="af64b-224">**Priorytetyzacja semaforów** (*tx_semaphore_prioritize*)</span><span class="sxs-lookup"><span data-stu-id="af64b-224">**Semaphore prioritize** (*tx_semaphore_prioritize*)</span></span> |
| ![Ikona umieszczenia semafora](./media/user-guide/tx-events/image59.png)    | <span data-ttu-id="af64b-226">**Umieszczenie semafora** (*tx_semaphore_put*)</span><span class="sxs-lookup"><span data-stu-id="af64b-226">**Semaphore put** (*tx_semaphore_put*)</span></span> |
| ![Ikona powiadomienia dotyczącego umieszczenia semafora](./media/user-guide/tx-events/image60.png)    | <span data-ttu-id="af64b-228">**Powiadomienie o wprowadzeniu semafora** (*tx_semaphore_put_notify*)</span><span class="sxs-lookup"><span data-stu-id="af64b-228">**Semaphore put notify** (*tx_semaphore_put_notify*)</span></span> |
| ![Ikona tworzenia wątku](./media/user-guide/tx-events/image61.png)    | <span data-ttu-id="af64b-230">**Tworzenie wątku** (*tx_thread_create*)</span><span class="sxs-lookup"><span data-stu-id="af64b-230">**Thread create** (*tx_thread_create*)</span></span> |
| ![Ikona usuwania wątku](./media/user-guide/tx-events/image62.png)    | <span data-ttu-id="af64b-232">**Usuwanie wątku** (*tx_thread_delete*)</span><span class="sxs-lookup"><span data-stu-id="af64b-232">**Thread delete** (*tx_thread_delete*)</span></span> |
| ![Ikona powiadomienia o wyjściu/wprowadzeniu wątku](./media/user-guide/tx-events/image63.png)    | <span data-ttu-id="af64b-234">**Powiadomienie o wyjściu/wprowadzeniu wątku** (*tx_thread_entry_exit_notify*)</span><span class="sxs-lookup"><span data-stu-id="af64b-234">**Thread exit/entry notify** (*tx_thread_entry_exit_notify*)</span></span> |
| ![Ikona identyfikacji wątku](./media/user-guide/tx-events/image64.png)    | <span data-ttu-id="af64b-236">**Identyfikator wątku** (*tx_thread_identify*)</span><span class="sxs-lookup"><span data-stu-id="af64b-236">**Thread identify** (*tx_thread_identify*)</span></span> |
| ![Ikona pobierania informacji o wątkach](./media/user-guide/tx-events/image65.png)    | <span data-ttu-id="af64b-238">**Pobieranie informacji o wątku** (*tx_thread_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-238">**Thread information get** (*tx_thread_info_get*)</span></span> |
| ![Ikona uzyskiwania informacji o wydajności wątków](./media/user-guide/tx-events/image66.png)    | <span data-ttu-id="af64b-240">**Informacje o wydajności wątku Get** (*tx_thread_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-240">**Thread performance information get** (*tx_thread_performance_info_get*)</span></span> |
| ![Ikona uzyskiwania informacji o systemie wydajności wątków](./media/user-guide/tx-events/image67.png)    | <span data-ttu-id="af64b-242">**Informacje o systemie wydajności wątku Get** (*tx_thread_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-242">**Thread performance system information get** (*tx_thread_performance_system_info_get*)</span></span> |
| ![Ikona zmiany zastępujący wątek](./media/user-guide/tx-events/image68.png)    | <span data-ttu-id="af64b-244">**Zmiana zastępujący wątek** (*tx_thread_preemption_change*)</span><span class="sxs-lookup"><span data-stu-id="af64b-244">**Thread preemption change** (*tx_thread_preemption_change*)</span></span> |
| ![Ikona zmiany priorytetu wątku](./media/user-guide/tx-events/image69.png)    | <span data-ttu-id="af64b-246">**Zmiana priorytetu wątku** (*tx_thread_priority_change*)</span><span class="sxs-lookup"><span data-stu-id="af64b-246">**Thread priority change** (*tx_thread_priority_change*)</span></span> |
| ![Ikona zrzeczenia wątku](./media/user-guide/tx-events/image70.png)    | <span data-ttu-id="af64b-248">**Zrzeka się wątku** (*tx_thread_relinquish*)</span><span class="sxs-lookup"><span data-stu-id="af64b-248">**Thread relinquish** (*tx_thread_relinquish*)</span></span> |
| ![Ikona resetowania wątku](./media/user-guide/tx-events/image71.png)    | <span data-ttu-id="af64b-250">**Resetowanie wątku** (*tx_thread_reset*)</span><span class="sxs-lookup"><span data-stu-id="af64b-250">**Thread reset** (*tx_thread_reset*)</span></span> |
| ![\* Ikona wznowienia wątku](./media/user-guide/tx-events/image72.png)    | <span data-ttu-id="af64b-252">**Wznowienie wątku** (\**tx_thread_resume*)</span><span class="sxs-lookup"><span data-stu-id="af64b-252">**Thread resume** (\**tx_thread_resume*)</span></span> |
| ![Ikona uśpienia wątku](./media/user-guide/tx-events/image73.png)    | <span data-ttu-id="af64b-254">**Wątek uśpienia** (*tx_thread_sleep*) \*</span><span class="sxs-lookup"><span data-stu-id="af64b-254">**Thread Sleep** (*tx_thread_sleep*)\*</span></span> |
| ![Ikona powiadomienia o błędzie stosu wątku](./media/user-guide/tx-events/image74.png)    | <span data-ttu-id="af64b-256">**Powiadomienie o błędzie stosu wątku** (*tx_thread_stack_error_notify*)</span><span class="sxs-lookup"><span data-stu-id="af64b-256">**Thread stack error notify** (*tx_thread_stack_error_notify*)</span></span> |
| ![Ikona wstrzymania wątku](./media/user-guide/tx-events/image75.png)    | <span data-ttu-id="af64b-258">**Wstrzymywanie wątku** (*tx_thread_suspend*)</span><span class="sxs-lookup"><span data-stu-id="af64b-258">**Thread suspend** (*tx_thread_suspend*)</span></span> |
| ![Ikona zakończenia wątku](./media/user-guide/tx-events/image76.png)    | <span data-ttu-id="af64b-260">**Zakończenie wątku** (*tx_thread_terminate*)</span><span class="sxs-lookup"><span data-stu-id="af64b-260">**Thread terminate** (*tx_thread_terminate*)</span></span> |
| ![Ikona zmiany czasu wątku](./media/user-guide/tx-events/image77.png)    | <span data-ttu-id="af64b-262">**Zmiana wycinka czasu wątku** (*tx_thread_time_slice_change*)</span><span class="sxs-lookup"><span data-stu-id="af64b-262">**Thread time-slice change** (*tx_thread_time_slice_change*)</span></span> |
| ![Ikona przerwania oczekiwania wątku](./media/user-guide/tx-events/image78.png)    | <span data-ttu-id="af64b-264">**Przerwanie oczekiwania wątku** (*tx_thread_wait_abort*)</span><span class="sxs-lookup"><span data-stu-id="af64b-264">**Thread wait abort** (*tx_thread_wait_abort*)</span></span> |
| ![Ikona uzyskiwania czasu](./media/user-guide/tx-events/image79.png)    | <span data-ttu-id="af64b-266">**Czas Get** (*tx_time_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-266">**Time get** (*tx_time_get*)</span></span> |
| ![Ikona zestawu czasu](./media/user-guide/tx-events/image80.png)    | <span data-ttu-id="af64b-268">**Zestaw czasu** (*tx_time_set*)</span><span class="sxs-lookup"><span data-stu-id="af64b-268">**Time set** (*tx_time_set*)</span></span> |
| ![\* Ikona aktywowania czasomierza](./media/user-guide/tx-events/image81.png)    | <span data-ttu-id="af64b-270">**Aktywowanie czasomierza** (*tx_timer_activate*)</span><span class="sxs-lookup"><span data-stu-id="af64b-270">**Timer activate** (*tx_timer_activate*)</span></span> |
| ![Ikona zmiany czasomierza](./media/user-guide/tx-events/image82.png)    | <span data-ttu-id="af64b-272">**Zmiana czasomierza** (*tx_timer_change*)</span><span class="sxs-lookup"><span data-stu-id="af64b-272">**Timer change** (*tx_timer_change*)</span></span> |
| ![Ikona tworzenia czasomierza](./media/user-guide/tx-events/image83.png)    | <span data-ttu-id="af64b-274">**Tworzenie czasomierza** (*tx_timer_create*)</span><span class="sxs-lookup"><span data-stu-id="af64b-274">**Timer create** (*tx_timer_create*)</span></span> |
| ![Ikona dezaktywacji czasomierza](./media/user-guide/tx-events/image84.png)    | <span data-ttu-id="af64b-276">**Dezaktywacja czasomierza** (*tx_timer_deactivate*)</span><span class="sxs-lookup"><span data-stu-id="af64b-276">**Timer deactivate** (*tx_timer_deactivate*)</span></span> |
| ![Ikona usuwania czasomierza](./media/user-guide/tx-events/image85.png)    | <span data-ttu-id="af64b-278">**Usuwanie czasomierza** (*tx_timer_delete*)</span><span class="sxs-lookup"><span data-stu-id="af64b-278">**Timer delete** (*tx_timer_delete*)</span></span> |
| ![Ikona pobierania informacji o czasomierzu](./media/user-guide/tx-events/image86.png)    | <span data-ttu-id="af64b-280">**Pobieranie informacji o czasomierzu** (*tx_timer_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-280">**Timer information get** (*tx_timer_info_get*)</span></span> |
| ![Ikona pobierania informacji o wydajności czasomierza](./media/user-guide/tx-events/image87.png)    | <span data-ttu-id="af64b-282">**Informacje o wydajności czasomierza Pobierz** (*tx_timer_performance_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-282">**Timer performance information get** (*tx_timer_performance_info_get*)</span></span> |
| ![\* Ikona pobierania informacji o systemie wydajności czasomierza](./media/user-guide/tx-events/image88.png)    | <span data-ttu-id="af64b-284">**Informacje o systemie wydajności czasomierza Get** (*tx_timer_performance_system_info_get*)</span><span class="sxs-lookup"><span data-stu-id="af64b-284">**Timer performance system information get** (*tx_timer_performance_system_info_get*)</span></span> |
| ![User-Defined Eventicon](./media/user-guide/tx-events/image0.png)    | <span data-ttu-id="af64b-286">**Zdarzenie zdefiniowane przez użytkownika** (zobacz rozdział 10)</span><span class="sxs-lookup"><span data-stu-id="af64b-286">**User-Defined Event** (See Chapter 10)</span></span>    |

## <a name="event-descriptions"></a><span data-ttu-id="af64b-287">Opisy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af64b-287">Event Descriptions</span></span>

### <a name="internal-thread-resume"></a><span data-ttu-id="af64b-288">Wewnętrzny wznowienie wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-288">Internal thread resume</span></span>

#### <a name="internal-thread-resume"></a><span data-ttu-id="af64b-289">Wewnętrzny wznowienie wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-289">Internal thread resume</span></span>

<span data-ttu-id="af64b-290">**Ikona** ![ Ikona wznowienia wątku wewnętrznego](./media/user-guide/tx-events/image1.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-290">**Icon** ![Internal thread resume icon](./media/user-guide/tx-events/image1.png)</span></span>

<span data-ttu-id="af64b-291">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-291">**Description**</span></span>

<span data-ttu-id="af64b-292">To zdarzenie reprezentuje wewnętrzne przetwarzanie w ThreadX, które wznawia wątek do wykonania.</span><span class="sxs-lookup"><span data-stu-id="af64b-292">This event represents the internal processing in ThreadX that resumes a thread for execution.</span></span> <span data-ttu-id="af64b-293">Jeśli określony wątek jest najwyższym priorytetem i przekroczenie — próg nie blokuje jego wykonywania, System rozpocznie wykonywanie tego nowo przygotowanego wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-293">If the specified thread is the highest priority and preemption-threshold does not block its execution, the system will start executing this newly ready thread.</span></span>

<span data-ttu-id="af64b-294">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-294">**Information Fields**</span></span>

- <span data-ttu-id="af64b-295">Pole informacji 1: wskaźnik wznawiania wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-295">Info Field 1: Pointer to the thread being resumed.</span></span>
- <span data-ttu-id="af64b-296">Pole informacji 2: poprzedni stan wznawianego wątku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="af64b-296">Info Field 2: Previous state of the thread being resumed, as follows:</span></span>

  |  <span data-ttu-id="af64b-297">Stan wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-297">Thread state</span></span>                     | <span data-ttu-id="af64b-298">Wartość</span><span class="sxs-lookup"><span data-stu-id="af64b-298">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="af64b-299">TX_READY</span><span class="sxs-lookup"><span data-stu-id="af64b-299">TX_READY</span></span>                         | <span data-ttu-id="af64b-300">0</span><span class="sxs-lookup"><span data-stu-id="af64b-300">0</span></span>       |
  |  <span data-ttu-id="af64b-301">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="af64b-301">TX_COMPLETED</span></span>                     | <span data-ttu-id="af64b-302">1</span><span class="sxs-lookup"><span data-stu-id="af64b-302">1</span></span>       |
  |  <span data-ttu-id="af64b-303">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="af64b-303">TX_TERMINATED</span></span>                    | <span data-ttu-id="af64b-304">2</span><span class="sxs-lookup"><span data-stu-id="af64b-304">2</span></span>       |
  |  <span data-ttu-id="af64b-305">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="af64b-305">TX_SUSPENDED</span></span>                     | <span data-ttu-id="af64b-306">3</span><span class="sxs-lookup"><span data-stu-id="af64b-306">3</span></span>       |
  |  <span data-ttu-id="af64b-307">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="af64b-307">TX_SLEEP</span></span>                         | <span data-ttu-id="af64b-308">4</span><span class="sxs-lookup"><span data-stu-id="af64b-308">4</span></span>       |
  |  <span data-ttu-id="af64b-309">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="af64b-309">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="af64b-310">5</span><span class="sxs-lookup"><span data-stu-id="af64b-310">5</span></span>       |
  |  <span data-ttu-id="af64b-311">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="af64b-311">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="af64b-312">6</span><span class="sxs-lookup"><span data-stu-id="af64b-312">6</span></span>       |
  |  <span data-ttu-id="af64b-313">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="af64b-313">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="af64b-314">7</span><span class="sxs-lookup"><span data-stu-id="af64b-314">7</span></span>       |
  |  <span data-ttu-id="af64b-315">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="af64b-315">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="af64b-316">8</span><span class="sxs-lookup"><span data-stu-id="af64b-316">8</span></span>       |
  |  <span data-ttu-id="af64b-317">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="af64b-317">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="af64b-318">9</span><span class="sxs-lookup"><span data-stu-id="af64b-318">9</span></span>       |
  |  <span data-ttu-id="af64b-319">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="af64b-319">TX_TCP_IP</span></span>                        | <span data-ttu-id="af64b-320">12</span><span class="sxs-lookup"><span data-stu-id="af64b-320">12</span></span>      |
  |  <span data-ttu-id="af64b-321">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="af64b-321">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="af64b-322">13</span><span class="sxs-lookup"><span data-stu-id="af64b-322">13</span></span>      |

- <span data-ttu-id="af64b-323">Pole informacji 3: wartość wskaźnika stosu podczas wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-323">Info Field 3: Stack pointer value during the call.</span></span> 
- <span data-ttu-id="af64b-324">Pole informacji 4: wskaźnik do następnego priorytetu wątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="af64b-324">Info Field 4: Pointer to next highest priority thread to execute.</span></span>

### <a name="internal-thread-suspend"></a><span data-ttu-id="af64b-325">Zawieszenie wątku wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="af64b-325">Internal thread suspend</span></span>

#### <a name="internal-thread-suspend"></a><span data-ttu-id="af64b-326">Zawieszenie wątku wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="af64b-326">Internal thread suspend</span></span>

<span data-ttu-id="af64b-327">**Ikona** ![ Ikona wstrzymania wątku wewnętrznego](./media/user-guide/tx-events/image2.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-327">**Icon** ![Internal thread suspend icon](./media/user-guide/tx-events/image2.png)</span></span>

<span data-ttu-id="af64b-328">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-328">**Description**</span></span>

<span data-ttu-id="af64b-329">To zdarzenie reprezentuje wewnętrzne przetwarzanie w ThreadX, które wstrzymuje wykonywanie wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-329">This event represents the internal processing in ThreadX that suspends a thread's execution.</span></span> <span data-ttu-id="af64b-330">Kolejny wątek o najwyższym priorytecie gotowy do wykonania jest umieszczany w czwartym polu informacji.</span><span class="sxs-lookup"><span data-stu-id="af64b-330">The next highest priority thread ready for execution is placed in the fourth information field.</span></span> <span data-ttu-id="af64b-331">Jeśli ta wartość jest RÓWNa NULL, nie istnieje żaden inny wątek gotowy do wykonania i system jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="af64b-331">If this value is NULL, there is no other thread ready for execution and the system is idle.</span></span>

<span data-ttu-id="af64b-332">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-332">**Information Fields**</span></span>

- <span data-ttu-id="af64b-333">Pole informacji 1: wskaźnik do wstrzymanego wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-333">Info Field 1: Pointer to the thread being suspended.</span></span>
- <span data-ttu-id="af64b-334">Pole informacji 2: nowy stan zawieszenia wątku w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="af64b-334">Info Field 2: New state of the thread being suspended, as follows:</span></span>

  |  <span data-ttu-id="af64b-335">Stan wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-335">Thread state</span></span>                     | <span data-ttu-id="af64b-336">Wartość</span><span class="sxs-lookup"><span data-stu-id="af64b-336">Value</span></span>        |
  |---------------------------------- | --------|
  |  <span data-ttu-id="af64b-337">TX_COMPLETED</span><span class="sxs-lookup"><span data-stu-id="af64b-337">TX_COMPLETED</span></span>                     | <span data-ttu-id="af64b-338">1</span><span class="sxs-lookup"><span data-stu-id="af64b-338">1</span></span>       |
  |  <span data-ttu-id="af64b-339">TX_TERMINATED</span><span class="sxs-lookup"><span data-stu-id="af64b-339">TX_TERMINATED</span></span>                    | <span data-ttu-id="af64b-340">2</span><span class="sxs-lookup"><span data-stu-id="af64b-340">2</span></span>       |
  |  <span data-ttu-id="af64b-341">TX_SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="af64b-341">TX_SUSPENDED</span></span>                     | <span data-ttu-id="af64b-342">3</span><span class="sxs-lookup"><span data-stu-id="af64b-342">3</span></span>       |
  |  <span data-ttu-id="af64b-343">TX_SLEEP</span><span class="sxs-lookup"><span data-stu-id="af64b-343">TX_SLEEP</span></span>                         | <span data-ttu-id="af64b-344">4</span><span class="sxs-lookup"><span data-stu-id="af64b-344">4</span></span>       |
  |  <span data-ttu-id="af64b-345">TX_QUEUE_SUSP</span><span class="sxs-lookup"><span data-stu-id="af64b-345">TX_QUEUE_SUSP</span></span>                    | <span data-ttu-id="af64b-346">5</span><span class="sxs-lookup"><span data-stu-id="af64b-346">5</span></span>       |
  |  <span data-ttu-id="af64b-347">TX_SEMAPHORE_SUSP</span><span class="sxs-lookup"><span data-stu-id="af64b-347">TX_SEMAPHORE_SUSP</span></span>                | <span data-ttu-id="af64b-348">6</span><span class="sxs-lookup"><span data-stu-id="af64b-348">6</span></span>       |
  |  <span data-ttu-id="af64b-349">TX_EVENT_FLAG</span><span class="sxs-lookup"><span data-stu-id="af64b-349">TX_EVENT_FLAG</span></span>                    | <span data-ttu-id="af64b-350">7</span><span class="sxs-lookup"><span data-stu-id="af64b-350">7</span></span>       |
  |  <span data-ttu-id="af64b-351">TX_BLOCK_MEMORY</span><span class="sxs-lookup"><span data-stu-id="af64b-351">TX_BLOCK_MEMORY</span></span>                  | <span data-ttu-id="af64b-352">8</span><span class="sxs-lookup"><span data-stu-id="af64b-352">8</span></span>       |
  |  <span data-ttu-id="af64b-353">TX_BYTE_MEMORY</span><span class="sxs-lookup"><span data-stu-id="af64b-353">TX_BYTE_MEMORY</span></span>                   | <span data-ttu-id="af64b-354">9</span><span class="sxs-lookup"><span data-stu-id="af64b-354">9</span></span>       |
  |  <span data-ttu-id="af64b-355">TX_TCP_IP</span><span class="sxs-lookup"><span data-stu-id="af64b-355">TX_TCP_IP</span></span>                        | <span data-ttu-id="af64b-356">12</span><span class="sxs-lookup"><span data-stu-id="af64b-356">12</span></span>      |
  |  <span data-ttu-id="af64b-357">TX_MUTEX_SUSP</span><span class="sxs-lookup"><span data-stu-id="af64b-357">TX_MUTEX_SUSP</span></span>                    | <span data-ttu-id="af64b-358">13</span><span class="sxs-lookup"><span data-stu-id="af64b-358">13</span></span>      |

- <span data-ttu-id="af64b-359">Pole informacji 3: wartość wskaźnika stosu podczas wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-359">Info Field 3: Stack pointer value during the call.</span></span> <span data-ttu-id="af64b-360">Pole informacji 4: wskaźnik do następnego priorytetu wątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="af64b-360">Info Field 4: Pointer to next highest priority thread to execute.</span></span> <span data-ttu-id="af64b-361">Jeśli wartość jest równa NULL, system jest bezczynny.</span><span class="sxs-lookup"><span data-stu-id="af64b-361">If NULL, the system is idle.</span></span>

### <a name="interrupt-service-routine-isr-enter"></a><span data-ttu-id="af64b-362">Wejście procedury usługi przerwania (ISR)</span><span class="sxs-lookup"><span data-stu-id="af64b-362">Interrupt Service Routine (ISR) enter</span></span> 

#### <a name="enter-isr"></a><span data-ttu-id="af64b-363">Wprowadź ISR</span><span class="sxs-lookup"><span data-stu-id="af64b-363">Enter ISR</span></span> 

<span data-ttu-id="af64b-364">**Ikona** ![ Ikona wprowadzania I S](./media/user-guide/tx-events/image3.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-364">**Icon** ![Enter I S R icon](./media/user-guide/tx-events/image3.png)</span></span>

<span data-ttu-id="af64b-365">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-365">**Description**</span></span>

<span data-ttu-id="af64b-366">To zdarzenie przedstawia wprowadzenie procedury usługi przerwania (ISR) w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="af64b-366">This event represents entering an Interrupt Service Routine (ISR) in the application.</span></span> <span data-ttu-id="af64b-367">Wykonanie procedury usługi przerwania jest kontynuowane do momentu zakończenia zdarzenia ISR.</span><span class="sxs-lookup"><span data-stu-id="af64b-367">The interrupt service routine execution continues until the ISR exit event takes place.</span></span>

<span data-ttu-id="af64b-368">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-368">**Information Fields**</span></span>

- <span data-ttu-id="af64b-369">Pole informacji 1: wartość wskaźnika stosu podczas wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-369">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="af64b-370">Pole informacji 2: zdefiniowany przez aplikację numer ISR (opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="af64b-370">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="af64b-371">Pole informacji 3: zagnieżdżona liczba przerwań.</span><span class="sxs-lookup"><span data-stu-id="af64b-371">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="af64b-372">Pole informacji 4: Flaga wyłączenia wewnętrznej zastępujące.</span><span class="sxs-lookup"><span data-stu-id="af64b-372">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="interrupt-service-routine-isr-exit"></a><span data-ttu-id="af64b-373">Zakończenie procedury usługi przerwania (ISR)</span><span class="sxs-lookup"><span data-stu-id="af64b-373">Interrupt Service Routine (ISR) exit</span></span> 

#### <a name="exit-isr"></a><span data-ttu-id="af64b-374">Wyjdź z procedury ISR</span><span class="sxs-lookup"><span data-stu-id="af64b-374">Exit ISR</span></span>

<span data-ttu-id="af64b-375">**Ikona** ![ Ikona zamykania I języka R](./media/user-guide/tx-events/image4.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-375">**Icon** ![Exit I S R icon](./media/user-guide/tx-events/image4.png)</span></span>

<span data-ttu-id="af64b-376">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-376">**Description**</span></span>

<span data-ttu-id="af64b-377">To zdarzenie reprezentuje zakończenie procedury usługi przerwania (ISR) w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="af64b-377">This event represents exiting an Interrupt Service Routine (ISR) in the application.</span></span>

<span data-ttu-id="af64b-378">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-378">**Information Fields**</span></span>

- <span data-ttu-id="af64b-379">Pole informacji 1: wartość wskaźnika stosu podczas wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-379">Info Field 1: Stack pointer value during the call.</span></span>
- <span data-ttu-id="af64b-380">Pole informacji 2: zdefiniowany przez aplikację numer ISR (opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="af64b-380">Info Field 2: Application-defined ISR number (optional).</span></span>
- <span data-ttu-id="af64b-381">Pole informacji 3: zagnieżdżona liczba przerwań.</span><span class="sxs-lookup"><span data-stu-id="af64b-381">Info Field 3: Nested interrupt count.</span></span>
- <span data-ttu-id="af64b-382">Pole informacji 4: Flaga wyłączenia wewnętrznej zastępujące.</span><span class="sxs-lookup"><span data-stu-id="af64b-382">Info Field 4: Internal preemption disable flag.</span></span>

### <a name="internal-time-slice"></a><span data-ttu-id="af64b-383">Wewnętrzny czas wycinka</span><span class="sxs-lookup"><span data-stu-id="af64b-383">Internal time-slice</span></span>

#### <a name="internal-time-slice"></a><span data-ttu-id="af64b-384">Wewnętrzny czas wycinka</span><span class="sxs-lookup"><span data-stu-id="af64b-384">Internal time-slice</span></span>

<span data-ttu-id="af64b-385">**Ikona** ![ Ikona wewnętrznego wycinka czasu](./media/user-guide/tx-events/image5.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-385">**Icon** ![Internal time-slice icon](./media/user-guide/tx-events/image5.png)</span></span>

<span data-ttu-id="af64b-386">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-386">**Description**</span></span>

<span data-ttu-id="af64b-387">To zdarzenie reprezentuje wewnętrzne przetwarzanie w ThreadX, które wykonuje operację wycinka czasu.</span><span class="sxs-lookup"><span data-stu-id="af64b-387">This event represents the internal processing in ThreadX that performs the time-slice operation.</span></span> <span data-ttu-id="af64b-388">Następny wątek o takim samym priorytecie jest umieszczany w pierwszym polu informacji.</span><span class="sxs-lookup"><span data-stu-id="af64b-388">The next thread of the same priority is placed in the first information field.</span></span> <span data-ttu-id="af64b-389">Jeśli ta wartość jest taka sama jak bieżący wątek, nie wykonano wycinka czasu.</span><span class="sxs-lookup"><span data-stu-id="af64b-389">If this value is the same as the current thread, no time-slice was performed.</span></span>

- <span data-ttu-id="af64b-390">Pole informacji 1: wskaźnik do następnego wątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="af64b-390">Info Field 1: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="af64b-391">Pole informacji 2: zagnieżdżona liczba przerwań.</span><span class="sxs-lookup"><span data-stu-id="af64b-391">Info Field 2: Nested interrupt count.</span></span>
- <span data-ttu-id="af64b-392">Pole informacji 3: Flaga wyłączenia wewnętrznej zastępujące.</span><span class="sxs-lookup"><span data-stu-id="af64b-392">Info Field 3: Internal preemption disable flag.</span></span>
- <span data-ttu-id="af64b-393">Pole informacji 4: wartość wskaźnika stosu podczas wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-393">Info Field 4: Stack pointer value during the call.</span></span>

### <a name="running"></a><span data-ttu-id="af64b-394">Uruchomienie</span><span class="sxs-lookup"><span data-stu-id="af64b-394">Running</span></span>

#### <a name="running-in-context"></a><span data-ttu-id="af64b-395">Uruchamianie w kontekście</span><span class="sxs-lookup"><span data-stu-id="af64b-395">Running in context</span></span>

<span data-ttu-id="af64b-396">**Ikona** ![ Ikona uruchamiania](./media/user-guide/tx-events/image6.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-396">**Icon** ![Running icon](./media/user-guide/tx-events/image6.png)</span></span>

<span data-ttu-id="af64b-397">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-397">**Description**</span></span>

<span data-ttu-id="af64b-398">To zdarzenie reprezentuje działające w kontekście wątku lub bezczynnym systemie.</span><span class="sxs-lookup"><span data-stu-id="af64b-398">This event represents running within a thread context or idle system.</span></span> <span data-ttu-id="af64b-399">Służy do zilustrowania kolejnych zmian w kontekście w wyniku przerwania.</span><span class="sxs-lookup"><span data-stu-id="af64b-399">It is used to illustrate subsequent changes in context as a result of an interrupt.</span></span>

<span data-ttu-id="af64b-400">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-400">**Information Fields**</span></span>
- <span data-ttu-id="af64b-401">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-401">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-402">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-402">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-403">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-403">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-404">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-404">Info Field 4: Not used.</span></span>

### <a name="block-allocate"></a><span data-ttu-id="af64b-405">Zablokuj alokację</span><span class="sxs-lookup"><span data-stu-id="af64b-405">Block Allocate</span></span> 

#### <a name="tx_block_allocate"></a><span data-ttu-id="af64b-406">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="af64b-406">tx_block_allocate</span></span>

<span data-ttu-id="af64b-407">**Ikona** ![ Ikona blokowania alokacji](./media/user-guide/tx-events/image7.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-407">**Icon** ![Block allocate icon](./media/user-guide/tx-events/image7.png)</span></span>

<span data-ttu-id="af64b-408">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-408">**Description**</span></span>

<span data-ttu-id="af64b-409">To zdarzenie reprezentuje przypisanie bloku pamięci za pośrednictwem tx_block_allocate.</span><span class="sxs-lookup"><span data-stu-id="af64b-409">This event represents allocating a memory block via tx_block_allocate.</span></span> <span data-ttu-id="af64b-410">Jeśli to się powiedzie, adres przydzielony blok jest zwracany w drugim polu informacji.</span><span class="sxs-lookup"><span data-stu-id="af64b-410">If successful, the address of the block allocated is returned in the second information field.</span></span>

<span data-ttu-id="af64b-411">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-411">**Information Fields**</span></span>
- <span data-ttu-id="af64b-412">Pole informacji 1: wskaźnik do odpowiedniej puli bloków.</span><span class="sxs-lookup"><span data-stu-id="af64b-412">Info Field 1: Pointer to the corresponding block pool.</span></span>
- <span data-ttu-id="af64b-413">Pole informacji 2: wskaźnik do zwróconego bloku pamięci (Jeśli powodzenie).</span><span class="sxs-lookup"><span data-stu-id="af64b-413">Info Field 2: Pointer to the memory block returned (if successful).</span></span>
- <span data-ttu-id="af64b-414">Pole informacji 3: opcja oczekiwania dostarczona do wywołania tx_block_allocate.</span><span class="sxs-lookup"><span data-stu-id="af64b-414">Info Field 3: The wait option supplied to the tx_block_allocate call.</span></span>
- <span data-ttu-id="af64b-415">Pole informacji 4: pozostałe dostępne bloki w puli po tej alokacji.</span><span class="sxs-lookup"><span data-stu-id="af64b-415">Info Field 4: Remaining available blocks in the pool after this allocation.</span></span>

### <a name="block-pool-create"></a><span data-ttu-id="af64b-416">Tworzenie puli blokowej</span><span class="sxs-lookup"><span data-stu-id="af64b-416">Block Pool Create</span></span>

#### <a name="tx_block_pool_create"></a><span data-ttu-id="af64b-417">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="af64b-417">tx_block_pool_create</span></span>

<span data-ttu-id="af64b-418">**Ikona** ![ Ikona tworzenia puli blokowej](./media/user-guide/tx-events/image8.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-418">**Icon** ![Block pool create icon](./media/user-guide/tx-events/image8.png)</span></span>

<span data-ttu-id="af64b-419">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-419">**Description**</span></span>

<span data-ttu-id="af64b-420">To zdarzenie reprezentuje Tworzenie puli bloków pamięci za pośrednictwem tx_block_pool_create.</span><span class="sxs-lookup"><span data-stu-id="af64b-420">This event represents creating a memory block pool via tx_block_pool_create.</span></span>

<span data-ttu-id="af64b-421">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-421">**Information Fields**</span></span>

- <span data-ttu-id="af64b-422">Pole informacji 1: wskaźnik do odpowiadającego bloku sterowania puli bloku.</span><span class="sxs-lookup"><span data-stu-id="af64b-422">Info Field 1: Pointer to the corresponding block pool control block.</span></span>
- <span data-ttu-id="af64b-423">Pole informacji 2: wskaźnik do obszaru pamięci początkowej puli.</span><span class="sxs-lookup"><span data-stu-id="af64b-423">Info Field 2: Pointer to the starting memory area of the pool.</span></span>
- <span data-ttu-id="af64b-424">Pole informacji 3: liczba bloków w puli.</span><span class="sxs-lookup"><span data-stu-id="af64b-424">Info Field 3: The number of blocks in the pool.</span></span> <span data-ttu-id="af64b-425">Pole informacji 4: rozmiar każdego bloku w puli w bajtach.</span><span class="sxs-lookup"><span data-stu-id="af64b-425">Info Field 4: The size of each block in the pool in bytes.</span></span>

### <a name="block-pool-delete"></a><span data-ttu-id="af64b-426">Blokuj Usuwanie puli</span><span class="sxs-lookup"><span data-stu-id="af64b-426">Block Pool Delete</span></span>

#### <a name="tx_block_pool_delete"></a><span data-ttu-id="af64b-427">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="af64b-427">tx_block_pool_delete</span></span>

<span data-ttu-id="af64b-428">**Ikona** ![ Ikona usuwania puli blokowej](./media/user-guide/tx-events/image9.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-428">**Icon** ![Block pool delete icon](./media/user-guide/tx-events/image9.png)</span></span>

<span data-ttu-id="af64b-429">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-429">**Description**</span></span>

<span data-ttu-id="af64b-430">To zdarzenie reprezentuje usunięcie puli bloków pamięci za pośrednictwem tx_block_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="af64b-430">This event represents deleting a memory block pool via tx_block_pool_delete.</span></span>

<span data-ttu-id="af64b-431">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-431">**Information Fields**</span></span>

- <span data-ttu-id="af64b-432">Pole informacji 1: wskaźnik do bloku kontroli puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="af64b-432">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="af64b-433">Pole informacji 2: wartość wskaźnika stosu podczas wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-433">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="af64b-434">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-434">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-435">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-435">Info Field 4: Not used.</span></span>

### <a name="block-pool-information-get"></a><span data-ttu-id="af64b-436">Uzyskaj informacje o puli bloku</span><span class="sxs-lookup"><span data-stu-id="af64b-436">Block Pool Information Get</span></span> 

#### <a name="tx_block_pool_info_get"></a><span data-ttu-id="af64b-437">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-437">tx_block_pool_info_get</span></span>

<span data-ttu-id="af64b-438">**Ikona** ![ Ikona uzyskiwania informacji o puli bloku](./media/user-guide/tx-events/image10.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-438">**Icon** ![Block pool information get icon](./media/user-guide/tx-events/image10.png)</span></span>

<span data-ttu-id="af64b-439">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-439">**Description**</span></span>

<span data-ttu-id="af64b-440">To zdarzenie reprezentuje pobieranie informacji o puli bloków pamięci za pośrednictwem tx_block_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-440">This event represents getting information about a memory block pool via tx_block_pool_info_get.</span></span>

<span data-ttu-id="af64b-441">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-441">**Information Fields**</span></span>

- <span data-ttu-id="af64b-442">Pole informacji 1: wskaźnik do bloku kontroli puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="af64b-442">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="af64b-443">Pole informacji 2: wartość wskaźnika stosu podczas wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-443">Info Field 2: Stack pointer value during the call.</span></span>
- <span data-ttu-id="af64b-444">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-444">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-445">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-445">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-information-get"></a><span data-ttu-id="af64b-446">Uzyskaj informacje o wydajności puli bloku</span><span class="sxs-lookup"><span data-stu-id="af64b-446">Block Pool Performance Information Get</span></span>

#### <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="af64b-447">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-447">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="af64b-448">**Ikona** ![ Ikona uzyskiwania informacji o wydajności puli blokowych](./media/user-guide/tx-events/image11.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-448">**Icon** ![Block pool performance information get icon](./media/user-guide/tx-events/image11.png)</span></span>

<span data-ttu-id="af64b-449">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-449">**Description**</span></span>

<span data-ttu-id="af64b-450">To zdarzenie reprezentuje informacje o wydajności puli bloków pamięci za pośrednictwem tx_block_pool_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-450">This event represents getting performance information about a memory block pool via tx_block_pool_performance_info_get.</span></span>

<span data-ttu-id="af64b-451">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-451">**Information Fields**</span></span>

- <span data-ttu-id="af64b-452">Pole informacji 1: wskaźnik do bloku kontroli puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="af64b-452">Info Field 1: Pointer to the block pool control block.</span></span>
- <span data-ttu-id="af64b-453">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-453">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-454">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-454">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-455">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-455">Info Field 4: Not used.</span></span>

### <a name="block-pool-performance-system-information-get"></a><span data-ttu-id="af64b-456">Uzyskaj informacje o wydajności systemu dla puli</span><span class="sxs-lookup"><span data-stu-id="af64b-456">Block Pool Performance System Information Get</span></span>

#### <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="af64b-457">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-457">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="af64b-458">**Ikona** ![ Ikona uzyskiwania informacji o systemie wydajności puli blokowej](./media/user-guide/tx-events/image12.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-458">**Icon** ![Block pool performance system information get icon](./media/user-guide/tx-events/image12.png)</span></span>

<span data-ttu-id="af64b-459">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-459">**Description**</span></span>

<span data-ttu-id="af64b-460">To zdarzenie reprezentuje informacje o wydajności wszystkich pul bloków pamięci za pośrednictwem tx_block_pool_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-460">This event represents getting performance information about all memory block pools via tx_block_pool_performance_system_info_get.</span></span>

<span data-ttu-id="af64b-461">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-461">**Information Fields**</span></span>
- <span data-ttu-id="af64b-462">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-462">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-463">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-463">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-464">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-464">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-465">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-465">Info Field 4: Not used.</span></span>

### <a name="block-pool-prioritize"></a><span data-ttu-id="af64b-466">Priorytet puli bloków</span><span class="sxs-lookup"><span data-stu-id="af64b-466">Block Pool Prioritize</span></span>

#### <a name="tx_block_pool_prioritize"></a><span data-ttu-id="af64b-467">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="af64b-467">tx_block_pool_prioritize</span></span>

<span data-ttu-id="af64b-468">**Ikona** ![ Ikona zablokowania priorytetów puli](./media/user-guide/tx-events/image13.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-468">**Icon** ![Block pool prioritize icon](./media/user-guide/tx-events/image13.png)</span></span>

<span data-ttu-id="af64b-469">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-469">**Description**</span></span>

<span data-ttu-id="af64b-470">To zdarzenie przedstawia umieszczenie wątku zawieszenia HighestPriority na początku listy zawieszania puli bloku.</span><span class="sxs-lookup"><span data-stu-id="af64b-470">This event represents placing the highestpriority suspended thread at the front of the block pool suspension list.</span></span> <span data-ttu-id="af64b-471">Jeśli jest to wykonywane przed wywołaniem tx_block_release, wątek o najwyższym priorytecie zostanie odebrany.</span><span class="sxs-lookup"><span data-stu-id="af64b-471">If this is done prior to calling tx_block_release, the highest priority suspended thread will receive the released block.</span></span>

<span data-ttu-id="af64b-472">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-472">**Information Fields**</span></span>
- <span data-ttu-id="af64b-473">Pole informacji 1: wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="af64b-473">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="af64b-474">Pole informacji 2: liczba wątków zawieszonych w tej puli bloku.</span><span class="sxs-lookup"><span data-stu-id="af64b-474">Info Field 2: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="af64b-475">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-475">Info Field 3: Stack pointer at the time of the call.</span></span>
- <span data-ttu-id="af64b-476">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-476">Info Field 4: Not used.</span></span>

### <a name="block-release"></a><span data-ttu-id="af64b-477">Blokuj wydanie</span><span class="sxs-lookup"><span data-stu-id="af64b-477">Block Release</span></span> 

#### <a name="tx_block_release"></a><span data-ttu-id="af64b-478">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="af64b-478">tx_block_release</span></span>

<span data-ttu-id="af64b-479">**Ikona** ![ Ikona bloku wersji](./media/user-guide/tx-events/image14.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-479">**Icon** ![Block release icon](./media/user-guide/tx-events/image14.png)</span></span>

<span data-ttu-id="af64b-480">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-480">**Description**</span></span>

<span data-ttu-id="af64b-481">To zdarzenie reprezentuje wydawanie wcześniej przydzielonych bloków z powrotem do puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="af64b-481">This event represents releasing a previously allocated block back to the block pool.</span></span>

<span data-ttu-id="af64b-482">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-482">**Information Fields**</span></span>

- <span data-ttu-id="af64b-483">Pole informacji 1: wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="af64b-483">Info Field 1: Memory block pool pointer.</span></span>
- <span data-ttu-id="af64b-484">Pole informacji 2: wskaźnik do zablokowania do wydania.</span><span class="sxs-lookup"><span data-stu-id="af64b-484">Info Field 2: Pointer to block to release.</span></span>
- <span data-ttu-id="af64b-485">Pole informacji 3: liczba wątków zawieszonych w tej puli bloku.</span><span class="sxs-lookup"><span data-stu-id="af64b-485">Info Field 3: Number of threads suspended on this block pool.</span></span>
- <span data-ttu-id="af64b-486">Pole informacji 4: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-486">Info Field 4: Stack pointer at the time of the call.</span></span>

### <a name="byte-allocate"></a><span data-ttu-id="af64b-487">Przydział bajtów</span><span class="sxs-lookup"><span data-stu-id="af64b-487">Byte Allocate</span></span> 

#### <a name="tx_byte_allocate"></a><span data-ttu-id="af64b-488">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="af64b-488">tx_byte_allocate</span></span>

<span data-ttu-id="af64b-489">**Ikona** ![ Ikona przydziału bajtów](./media/user-guide/tx-events/image15.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-489">**Icon** ![Byte allocate icon](./media/user-guide/tx-events/image15.png)</span></span>

<span data-ttu-id="af64b-490">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-490">**Description**</span></span>

<span data-ttu-id="af64b-491">To zdarzenie reprezentuje przydzielenie pamięci za pośrednictwem tx_byte_allocate.</span><span class="sxs-lookup"><span data-stu-id="af64b-491">This event represents allocating memory via tx_byte_allocate.</span></span> <span data-ttu-id="af64b-492">Jeśli to się powiedzie, adres przydzielenia pamięci jest zwracany w drugim polu informacji.</span><span class="sxs-lookup"><span data-stu-id="af64b-492">If successful, the address of the memory allocated is returned in the second information field.</span></span>

<span data-ttu-id="af64b-493">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-493">**Information Fields**</span></span>
- <span data-ttu-id="af64b-494">Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-494">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="af64b-495">Pole informacji 2: wskaźnik do zwróconej pamięci (Jeśli powodzenie).</span><span class="sxs-lookup"><span data-stu-id="af64b-495">Info Field 2: Pointer to the memory returned (if successful).</span></span>
- <span data-ttu-id="af64b-496">Pole informacji 3: Liczba żądanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-496">Info Field 3: Number of bytes requested.</span></span> <span data-ttu-id="af64b-497">Pole informacji 4: opcja oczekiwania dostarczona do wywołania tx_byte_allocate.</span><span class="sxs-lookup"><span data-stu-id="af64b-497">Info Field 4: The wait option supplied to the tx_byte_allocate call.</span></span>

### <a name="byte-pool-create"></a><span data-ttu-id="af64b-498">Tworzenie puli bajtów</span><span class="sxs-lookup"><span data-stu-id="af64b-498">Byte Pool Create</span></span>

#### <a name="tx_byte_pool_create"></a><span data-ttu-id="af64b-499">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="af64b-499">tx_byte_pool_create</span></span>

<span data-ttu-id="af64b-500">**Ikona** ![ Ikona tworzenia puli bajtów](./media/user-guide/tx-events/image16.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-500">**Icon** ![Byte pool create icon](./media/user-guide/tx-events/image16.png)</span></span>

<span data-ttu-id="af64b-501">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-501">**Description**</span></span>

<span data-ttu-id="af64b-502">To zdarzenie reprezentuje Tworzenie puli bajtów za pośrednictwem tx_byte_pool_create.</span><span class="sxs-lookup"><span data-stu-id="af64b-502">This event represents creating a byte pool via tx_byte_pool_create.</span></span>

<span data-ttu-id="af64b-503">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-503">**Information Fields**</span></span>

- <span data-ttu-id="af64b-504">Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-504">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="af64b-505">Pole informacji 2: wskaźnik do początku obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="af64b-505">Info Field 2: Pointer to the start of the memory area.</span></span> <span data-ttu-id="af64b-506">Pole informacji 3: liczba bajtów w puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-506">Info Field 3: Number of bytes in the byte pool.</span></span>
- <span data-ttu-id="af64b-507">Pole informacji 4: Wskaźnik stosu w momencie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-507">Info Field 4: The stack pointer at the time of the call.</span></span>

### <a name="byte-pool-delete"></a><span data-ttu-id="af64b-508">Usuwanie puli bajtów</span><span class="sxs-lookup"><span data-stu-id="af64b-508">Byte Pool Delete</span></span> 

#### <a name="tx_byte_pool_delete"></a><span data-ttu-id="af64b-509">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="af64b-509">tx_byte_pool_delete</span></span>

<span data-ttu-id="af64b-510">**Ikona** ![ Ikona usuwania puli bajtów](./media/user-guide/tx-events/image17.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-510">**Icon** ![Byte pool delete icon](./media/user-guide/tx-events/image17.png)</span></span>

<span data-ttu-id="af64b-511">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-511">**Description**</span></span>

<span data-ttu-id="af64b-512">To zdarzenie reprezentuje Usuwanie puli bajtów za pośrednictwem tx_byte_pool_delete.</span><span class="sxs-lookup"><span data-stu-id="af64b-512">This event represents deleting a byte pool via tx_byte_pool_delete.</span></span>

<span data-ttu-id="af64b-513">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-513">**Information Fields**</span></span>

- <span data-ttu-id="af64b-514">Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-514">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="af64b-515">Pole informacji 2: Wskaźnik stosu w momencie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-515">Info Field 2: The stack pointer at the time of the call.</span></span>
- <span data-ttu-id="af64b-516">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-516">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-517">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-517">Info Field 4: Not used.</span></span>

### <a name="byte-pool-information-get"></a><span data-ttu-id="af64b-518">Pobieranie informacji o puli bajtów</span><span class="sxs-lookup"><span data-stu-id="af64b-518">Byte Pool Information Get</span></span>

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="af64b-519">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-519">tx_byte_pool_info_get</span></span>

<span data-ttu-id="af64b-520">**Ikona** ![ Ikona pobierania informacji o puli bajtów](./media/user-guide/tx-events/image18.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-520">**Icon** ![Byte pool information get icon](./media/user-guide/tx-events/image18.png)</span></span>

<span data-ttu-id="af64b-521">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-521">**Description**</span></span>

<span data-ttu-id="af64b-522">To zdarzenie reprezentuje informacje o puli bajtów za pośrednictwem tx_byte_pool_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-522">This event represents getting byte pool information via tx_byte_pool_info_get.</span></span>

<span data-ttu-id="af64b-523">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-523">**Information Fields**</span></span>

- <span data-ttu-id="af64b-524">Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-524">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="af64b-525">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-525">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-526">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-526">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-527">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-527">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-info-get"></a><span data-ttu-id="af64b-528">Pobieranie informacji o wydajności puli bajtów</span><span class="sxs-lookup"><span data-stu-id="af64b-528">Byte Pool Performance Info Get</span></span> 

#### <a name="tx_byte_pool_info_get"></a><span data-ttu-id="af64b-529">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-529">tx_byte_pool_info_get</span></span>

<span data-ttu-id="af64b-530">**Ikona** ![ Ikona uzyskiwania informacji o wydajności puli bajtów](./media/user-guide/tx-events/image19.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-530">**Icon** ![Byte pool performance info get icon](./media/user-guide/tx-events/image19.png)</span></span>

<span data-ttu-id="af64b-531">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-531">**Description**</span></span>

<span data-ttu-id="af64b-532">To zdarzenie reprezentuje informacje o wydajności puli bajtów za pośrednictwem tx_byte_pool_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-532">This event represents getting byte pool performance information via tx_byte_pool_performance_info_get.</span></span>

<span data-ttu-id="af64b-533">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-533">**Information Fields**</span></span>

- <span data-ttu-id="af64b-534">Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-534">Info Field 1: Pointer to the corresponding byte pool.</span></span>
- <span data-ttu-id="af64b-535">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-535">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-536">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-536">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-537">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-537">Info Field 4: Not used.</span></span>

### <a name="byte-pool-performance-system-info-get"></a><span data-ttu-id="af64b-538">Pobieranie informacji o systemie wydajności puli bajtów</span><span class="sxs-lookup"><span data-stu-id="af64b-538">Byte Pool Performance System Info Get</span></span> 

#### <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="af64b-539">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-539">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="af64b-540">**Ikona** ![ Ikona pobierania informacji o systemie wydajności puli bajtów](./media/user-guide/tx-events/image20.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-540">**Icon** ![Byte pool performance system info get icon](./media/user-guide/tx-events/image20.png)</span></span>

<span data-ttu-id="af64b-541">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-541">**Description**</span></span>

<span data-ttu-id="af64b-542">To zdarzenie reprezentuje informacje o systemie wydajności puli bajtów za pośrednictwem tx_byte_pool_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-542">This event represents getting byte pool performance system information via tx_byte_pool_performance_system_info_get.</span></span>

<span data-ttu-id="af64b-543">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-543">**Information Fields**</span></span>

- <span data-ttu-id="af64b-544">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-544">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-545">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-545">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-546">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-546">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-547">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-547">Info Field 4: Not used.</span></span>

### <a name="byte-pool-prioritize"></a><span data-ttu-id="af64b-548">Priorytetyzacja puli bajtów</span><span class="sxs-lookup"><span data-stu-id="af64b-548">Byte Pool Prioritize</span></span>

#### <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="af64b-549">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="af64b-549">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="af64b-550">**Ikona** ![ Ikona priorytetyzacji puli bajtów](./media/user-guide/tx-events/image21.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-550">**Icon** ![Byte pool prioritize icon](./media/user-guide/tx-events/image21.png)</span></span>

<span data-ttu-id="af64b-551">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-551">**Description**</span></span>

<span data-ttu-id="af64b-552">To zdarzenie reprezentuje priorytet listy zawieszania puli bajtów za pośrednictwem tx_byte_pool_prioritize.</span><span class="sxs-lookup"><span data-stu-id="af64b-552">This event represents prioritizing the byte pool's suspension list via tx_byte_pool_prioritize.</span></span>

<span data-ttu-id="af64b-553">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-553">**Information Fields**</span></span>

- <span data-ttu-id="af64b-554">Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-554">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="af64b-555">Pole informacji 2: liczba wątków zawieszonych obecnie w puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-555">Info Field 2: Number of threads currently suspended on byte pool.</span></span>
- <span data-ttu-id="af64b-556">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-556">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-557">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-557">Info Field 4: Not used.</span></span>

### <a name="byte-release"></a><span data-ttu-id="af64b-558">Wydanie bajtów</span><span class="sxs-lookup"><span data-stu-id="af64b-558">Byte Release</span></span>

#### <a name="tx_byte_release"></a><span data-ttu-id="af64b-559">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="af64b-559">tx_byte_release</span></span>

<span data-ttu-id="af64b-560">**Ikona** ![ Ikona zwolnienia bajtów](./media/user-guide/tx-events/image22.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-560">**Icon** ![Byte release icon](./media/user-guide/tx-events/image22.png)</span></span>

<span data-ttu-id="af64b-561">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-561">**Description**</span></span>

<span data-ttu-id="af64b-562">To zdarzenie reprezentuje blok pamięci przydzielony z puli bajtów za pośrednictwem tx_byte_release.</span><span class="sxs-lookup"><span data-stu-id="af64b-562">This event represents releasing a block of memory allocated from a byte pool via tx_byte_release.</span></span>

<span data-ttu-id="af64b-563">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-563">**Information Fields**</span></span>

- <span data-ttu-id="af64b-564">Pole informacji 1: wskaźnik do odpowiedniej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-564">Info Field 1: Pointer to corresponding byte pool.</span></span>
- <span data-ttu-id="af64b-565">Pole informacji 2: wskaźnik do wcześniej przydzieloną pamięć puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-565">Info Field 2: Pointer to previously allocated byte pool memory.</span></span>
- <span data-ttu-id="af64b-566">Pole informacji 3: liczba wątków zawieszonych w tej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="af64b-566">Info Field 3: Number of threads suspended on this byte pool.</span></span>
- <span data-ttu-id="af64b-567">Pole informacji 4: liczba dostępnych bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="af64b-567">Info Field 4: Number of available bytes of memory.</span></span>

### <a name="event-flags-create"></a><span data-ttu-id="af64b-568">Tworzenie flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af64b-568">Event Flags Create</span></span> 

#### <a name="tx_event_flags_create"></a><span data-ttu-id="af64b-569">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="af64b-569">tx_event_flags_create</span></span>

<span data-ttu-id="af64b-570">**Ikona** ![ Ikona tworzenia flag zdarzeń](./media/user-guide/tx-events/image23.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-570">**Icon** ![Event flags create icon](./media/user-guide/tx-events/image23.png)</span></span>

<span data-ttu-id="af64b-571">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-571">**Description**</span></span>

<span data-ttu-id="af64b-572">To zdarzenie reprezentuje Tworzenie nowej grupy flag zdarzeń za pośrednictwem tx_event_flags_create.</span><span class="sxs-lookup"><span data-stu-id="af64b-572">This event represents creating a new event flags group via tx_event_flags_create.</span></span>

<span data-ttu-id="af64b-573">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-573">**Information Fields**</span></span> 
- <span data-ttu-id="af64b-574">Pole informacji 1: wskaźnik do flagi zdarzenia w bloku sterowania grupą.</span><span class="sxs-lookup"><span data-stu-id="af64b-574">Info Field 1: Pointer to event flags group control block.</span></span>
- <span data-ttu-id="af64b-575">Pole informacji 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-575">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-576">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-576">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-577">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-577">Info Field 4: Not used.</span></span>

### <a name="event-flags-delete"></a><span data-ttu-id="af64b-578">Usuwanie flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af64b-578">Event Flags Delete</span></span> 

#### <a name="tx_event_flags_delete"></a><span data-ttu-id="af64b-579">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="af64b-579">tx_event_flags_delete</span></span>

<span data-ttu-id="af64b-580">**Ikona** ![ Ikona usuwania flag zdarzeń](./media/user-guide/tx-events/image24.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-580">**Icon** ![Event flags delete icon](./media/user-guide/tx-events/image24.png)</span></span>

<span data-ttu-id="af64b-581">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-581">**Description**</span></span>

<span data-ttu-id="af64b-582">To zdarzenie reprezentuje usunięcie grupy flag zdarzeń za pośrednictwem tx_event_flags_delete.</span><span class="sxs-lookup"><span data-stu-id="af64b-582">This event represents deleting an event flags group via tx_event_flags_delete.</span></span>

<span data-ttu-id="af64b-583">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-583">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-584">Pole informacji 1: wskaźnik do grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af64b-584">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="af64b-585">Pole informacji 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-585">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-586">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-586">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-587">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-587">Info Field 4: Not used.</span></span>

### <a name="event-flags-get"></a><span data-ttu-id="af64b-588">Pobieranie flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af64b-588">Event Flags Get</span></span> 

#### <a name="tx_event_flags_get"></a><span data-ttu-id="af64b-589">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="af64b-589">tx_event_flags_get</span></span>

<span data-ttu-id="af64b-590">**Ikona** ![ Ikona zdarzenia gt](./media/user-guide/tx-events/image25.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-590">**Icon** ![Event flags gt icon](./media/user-guide/tx-events/image25.png)</span></span>

<span data-ttu-id="af64b-591">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-591">**Description**</span></span>

<span data-ttu-id="af64b-592">To zdarzenie przedstawia pobieranie flag zdarzeń z istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-592">This event represents retrieving event flags from an existing event flags group via tx_event_flags_get.</span></span>

<span data-ttu-id="af64b-593">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-593">**Information Fields**</span></span>

- <span data-ttu-id="af64b-594">Pole informacji 1: wskaźnik do grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af64b-594">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="af64b-595">Pole informacji 2: zażądano flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af64b-595">Info Field 2: Event flags requested.</span></span>
- <span data-ttu-id="af64b-596">Pole informacji 3: flagi zdarzeń obecnie ustawione w grupie.</span><span class="sxs-lookup"><span data-stu-id="af64b-596">Info Field 3: Event flags currently set in the group.</span></span>
- <span data-ttu-id="af64b-597">Pole informacji 4: zażądano opcji dla flag zdarzeń get.</span><span class="sxs-lookup"><span data-stu-id="af64b-597">Info Field 4: Option requested on the event flags get.</span></span>

### <a name="event-flags-information-get"></a><span data-ttu-id="af64b-598">Informacje o flagach zdarzenia</span><span class="sxs-lookup"><span data-stu-id="af64b-598">Event Flags Information Get</span></span>

#### <a name="tx_event_flags_info_get"></a><span data-ttu-id="af64b-599">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-599">tx_event_flags_info_get</span></span>

<span data-ttu-id="af64b-600">**Ikona** ![ Ikona uzyskiwania informacji o flagach zdarzeń](./media/user-guide/tx-events/image26.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-600">**Icon** ![Event flags information get icon](./media/user-guide/tx-events/image26.png)</span></span>

<span data-ttu-id="af64b-601">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-601">**Description**</span></span>

<span data-ttu-id="af64b-602">To zdarzenie reprezentuje pobieranie informacji dotyczących istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-602">This event represents retrieving information regarding an existing event flags group via tx_event_flags_info_get.</span></span>

<span data-ttu-id="af64b-603">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-603">**Information Fields**</span></span>

- <span data-ttu-id="af64b-604">Pole informacji 1: wskaźnik do grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af64b-604">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="af64b-605">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-605">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-606">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-606">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-607">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-607">Info Field 4: Not used.</span></span>

### <a name="event-flags-performance-information-get"></a><span data-ttu-id="af64b-608">Informacje o wydajności flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af64b-608">Event Flags Performance Information Get</span></span> 

#### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="af64b-609">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-609">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="af64b-610">**Ikona** ![ Ikona uzyskiwania informacji o wydajności flag zdarzeń](./media/user-guide/tx-events/image27.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-610">**Icon** ![Event flags performance information get icon](./media/user-guide/tx-events/image27.png)</span></span>

<span data-ttu-id="af64b-611">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-611">**Description**</span></span>

<span data-ttu-id="af64b-612">To zdarzenie reprezentuje pobieranie informacji o wydajności dotyczących istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-612">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_info_get.</span></span>

<span data-ttu-id="af64b-613">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-613">**Information Fields**</span></span> 
- <span data-ttu-id="af64b-614">Pole informacji 1: wskaźnik do grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af64b-614">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="af64b-615">Pole informacji 2: nieużywane</span><span class="sxs-lookup"><span data-stu-id="af64b-615">Info Field 2: Not used</span></span>
- <span data-ttu-id="af64b-616">Pole informacji 3: nieużywane</span><span class="sxs-lookup"><span data-stu-id="af64b-616">Info Field 3: Not used</span></span>
- <span data-ttu-id="af64b-617">Pole informacji 4: nieużywane</span><span class="sxs-lookup"><span data-stu-id="af64b-617">Info Field 4: Not Used</span></span>

### <a name="event-flags-performance-system-info-get"></a><span data-ttu-id="af64b-618">Flagi zdarzeń informacje o systemie wydajności pobieranie</span><span class="sxs-lookup"><span data-stu-id="af64b-618">Event Flags Performance System Info Get</span></span>

#### <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="af64b-619">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-619">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="af64b-620">**Ikona** ![ Flagi zdarzeń informacje o systemie wydajności pobieranie](./media/user-guide/tx-events/image28.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-620">**Icon** ![Event flags performance system info get icon](./media/user-guide/tx-events/image28.png)</span></span>

<span data-ttu-id="af64b-621">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-621">**Description**</span></span>

<span data-ttu-id="af64b-622">To zdarzenie reprezentuje pobieranie informacji o wydajności dotyczących istniejącej grupy flag zdarzeń za pośrednictwem tx_event_flags_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-622">This event represents retrieving performance information regarding an existing event flags group via tx_event_flags_performance_system_info_get.</span></span>

<span data-ttu-id="af64b-623">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-623">**Information Fields**</span></span>
- <span data-ttu-id="af64b-624">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-624">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-625">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-625">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-626">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-626">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-627">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-627">Info Field 4: Not used.</span></span>

### <a name="event-flags-set"></a><span data-ttu-id="af64b-628">Ustawione flagi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af64b-628">Event Flags Set</span></span> 

#### <a name="tx_event_flags_set"></a><span data-ttu-id="af64b-629">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="af64b-629">tx_event_flags_set</span></span>

<span data-ttu-id="af64b-630">**Ikona** ![ Ikona zestawu flag zdarzeń](./media/user-guide/tx-events/image29.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-630">**Icon** ![Event flags set icon](./media/user-guide/tx-events/image29.png)</span></span>

<span data-ttu-id="af64b-631">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-631">**Description**</span></span>

<span data-ttu-id="af64b-632">To zdarzenie reprezentuje flagę zdarzenia ustawienia (lub wyczyszczenia) w istniejącej grupie flag zdarzeń za pośrednictwem tx_event_flags_set.</span><span class="sxs-lookup"><span data-stu-id="af64b-632">This event represents setting (or clearing) event flags in an existing event flags group via tx_event_flags_set.</span></span>

<span data-ttu-id="af64b-633">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-633">**Information Fields**</span></span>

- <span data-ttu-id="af64b-634">Pole informacji 1: wskaźnik do grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af64b-634">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="af64b-635">Pole informacji 2: flagi zdarzeń do ustawienia (lub wyczyść).</span><span class="sxs-lookup"><span data-stu-id="af64b-635">Info Field 2: Event flags to set (or clear).</span></span>
- <span data-ttu-id="af64b-636">Pole informacji 3: i lub opcja flagi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="af64b-636">Info Field 3: AND or OR event flag option.</span></span>
- <span data-ttu-id="af64b-637">Pole informacji 4: liczba wątków zawieszonych w grupie flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af64b-637">Info Field 4: Number of threads suspended on event flag group.</span></span>

### <a name="event-flags-set-notify"></a><span data-ttu-id="af64b-638">Ustawione powiadomienia flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af64b-638">Event Flags Set Notify</span></span>

#### <a name="tx_event_flags_set_notify"></a><span data-ttu-id="af64b-639">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="af64b-639">tx_event_flags_set_notify</span></span>

<span data-ttu-id="af64b-640">**Ikona** ![ Ikona powiadomienia ustawiona flaga zdarzenia](./media/user-guide/tx-events/image30.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-640">**Icon** ![Event flags set notify icon](./media/user-guide/tx-events/image30.png)</span></span>

<span data-ttu-id="af64b-641">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-641">**Description**</span></span>

<span data-ttu-id="af64b-642">To zdarzenie reprezentuje zarejestrowanie wywołania zwrotnego powiadomienia dla każdej operacji zestawu flag zdarzeń w istniejącej grupie flag zdarzeń za pośrednictwem tx_event_flags_set_notify.</span><span class="sxs-lookup"><span data-stu-id="af64b-642">This event represents registering a notification callback for any event flag set operation on an existing event flags group via tx_event_flags_set_notify.</span></span>

<span data-ttu-id="af64b-643">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-643">**Information Fields**</span></span>

- <span data-ttu-id="af64b-644">Pole informacji 1: wskaźnik do grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af64b-644">Info Field 1: Pointer to event flags group.</span></span>
- <span data-ttu-id="af64b-645">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-645">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-646">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-646">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-647">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-647">Info Field 4: Not used.</span></span>

### <a name="interrupt-control"></a><span data-ttu-id="af64b-648">Kontrola przerwania</span><span class="sxs-lookup"><span data-stu-id="af64b-648">Interrupt Control</span></span> 

#### <a name="tx_interrupt_control"></a><span data-ttu-id="af64b-649">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="af64b-649">tx_interrupt_control</span></span>

<span data-ttu-id="af64b-650">**Ikona** ![ Ikona kontrolki przerwania](./media/user-guide/tx-events/image31.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-650">**Icon** ![Interrupt control icon](./media/user-guide/tx-events/image31.png)</span></span>

<span data-ttu-id="af64b-651">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-651">**Description**</span></span>

<span data-ttu-id="af64b-652">To zdarzenie reprezentuje zmianę stan blokady przerwania procesora za pośrednictwem tx_interrupt_control.</span><span class="sxs-lookup"><span data-stu-id="af64b-652">This event represents changing the interrupt lockout posture of the processor via tx_interrupt_control.</span></span>

<span data-ttu-id="af64b-653">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-653">**Information Fields**</span></span>

- <span data-ttu-id="af64b-654">Pole informacji 1: nowe przerwanie stan.</span><span class="sxs-lookup"><span data-stu-id="af64b-654">Info Field 1: New interrupt posture.</span></span>
- <span data-ttu-id="af64b-655">Pole informacji 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-655">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-656">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-656">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-657">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-657">Info Field 4: Not used.</span></span>

### <a name="mutex-create"></a><span data-ttu-id="af64b-658">Tworzenie obiektu mutex</span><span class="sxs-lookup"><span data-stu-id="af64b-658">Mutex Create</span></span> 

#### <a name="tx_mutex_create"></a><span data-ttu-id="af64b-659">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="af64b-659">tx_mutex_create</span></span>

<span data-ttu-id="af64b-660">**Ikona** ![ Ikona tworzenia obiektu mutex](./media/user-guide/tx-events/image32.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-660">**Icon** ![Mutex create icon](./media/user-guide/tx-events/image32.png)</span></span>

<span data-ttu-id="af64b-661">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-661">**Description**</span></span>

<span data-ttu-id="af64b-662">To zdarzenie reprezentuje Tworzenie elementu mutex za pośrednictwem tx_mutex_create.</span><span class="sxs-lookup"><span data-stu-id="af64b-662">This event represents creating a mutex via tx_mutex_create.</span></span>

<span data-ttu-id="af64b-663">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-663">**Information Fields**</span></span>

- <span data-ttu-id="af64b-664">Pole informacji 1: wskaźnik do bloku sterowania muteksem.</span><span class="sxs-lookup"><span data-stu-id="af64b-664">Info Field 1: Pointer to mutex control block.</span></span>
- <span data-ttu-id="af64b-665">Pole informacji 2: priorytet — opcja dziedziczenia</span><span class="sxs-lookup"><span data-stu-id="af64b-665">Info Field 2: Priority inheritance option</span></span>
- <span data-ttu-id="af64b-666">(TX_INHERIT lub TX_NO_INHERIT).</span><span class="sxs-lookup"><span data-stu-id="af64b-666">(TX_INHERIT or TX_NO_INHERIT).</span></span>
- <span data-ttu-id="af64b-667">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-667">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-668">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-668">Info Field 4: Not used.</span></span>

### <a name="mutex-delete"></a><span data-ttu-id="af64b-669">Usuwanie obiektu mutex</span><span class="sxs-lookup"><span data-stu-id="af64b-669">Mutex Delete</span></span> 

#### <a name="tx_mutex_delete"></a><span data-ttu-id="af64b-670">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="af64b-670">tx_mutex_delete</span></span>

<span data-ttu-id="af64b-671">**Ikona** ![ Ikona usuwania muteksu](./media/user-guide/tx-events/image33.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-671">**Icon** ![Mutex delete icon](./media/user-guide/tx-events/image33.png)</span></span>

<span data-ttu-id="af64b-672">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-672">**Description**</span></span>

<span data-ttu-id="af64b-673">To zdarzenie reprezentuje usunięcie elementu mutex za pośrednictwem tx_mutex_delete.</span><span class="sxs-lookup"><span data-stu-id="af64b-673">This event represents deleting a mutex via tx_mutex_delete.</span></span>

<span data-ttu-id="af64b-674">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-674">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-675">Pole informacji 1: wskaźnik do elementu mutex.</span><span class="sxs-lookup"><span data-stu-id="af64b-675">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="af64b-676">Pole informacji 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-676">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-677">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-677">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-678">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-678">Info Field 4: Not used.</span></span>

### <a name="mutex-get"></a><span data-ttu-id="af64b-679">Pobieranie obiektu mutex</span><span class="sxs-lookup"><span data-stu-id="af64b-679">Mutex Get</span></span> 

#### <a name="tx_mutex_get"></a><span data-ttu-id="af64b-680">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="af64b-680">tx_mutex_get</span></span>

<span data-ttu-id="af64b-681">**Ikona** ![ Ikona pobierania muteksu](./media/user-guide/tx-events/image34.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-681">**Icon** ![Mutex get icon](./media/user-guide/tx-events/image34.png)</span></span>

<span data-ttu-id="af64b-682">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-682">**Description**</span></span>

<span data-ttu-id="af64b-683">To zdarzenie reprezentuje uzyskanie elementu mutex za pośrednictwem tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-683">This event represents obtaining a mutex via tx_mutex_get.</span></span>

<span data-ttu-id="af64b-684">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-684">**Information Fields**</span></span>

- <span data-ttu-id="af64b-685">Pole informacji 1: wskaźnik do elementu mutex.</span><span class="sxs-lookup"><span data-stu-id="af64b-685">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="af64b-686">Pole informacji 2: opcja oczekiwania dostarczona do wywołania tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-686">Info Field 2: The wait option supplied to the tx_mutex_get call.</span></span>
- <span data-ttu-id="af64b-687">Pole informacji 3: wskaźnik do wątku, do którego należy element mutex (wartość NULL oznacza, że mutex nie jest własnością).</span><span class="sxs-lookup"><span data-stu-id="af64b-687">Info Field 3: Pointer to thread that owns the mutex (NULL implies the mutex is not owned).</span></span>
- <span data-ttu-id="af64b-688">Pole informacji 4: liczba wystąpień wątku będącego właścicielem, tx_mutex_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-688">Info Field 4: Number of times the owning thread has called tx_mutex_get.</span></span>

### <a name="mutex-information-get"></a><span data-ttu-id="af64b-689">Pobieranie informacji o muteksie</span><span class="sxs-lookup"><span data-stu-id="af64b-689">Mutex Information Get</span></span>

#### <a name="tx_mutex_info_get"></a><span data-ttu-id="af64b-690">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-690">tx_mutex_info_get</span></span>

<span data-ttu-id="af64b-691">**Ikona** ![ Ikona pobierania informacji o muteksie](./media/user-guide/tx-events/image35.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-691">**Icon** ![Mutex information get icon](./media/user-guide/tx-events/image35.png)</span></span>

<span data-ttu-id="af64b-692">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-692">**Description**</span></span>

<span data-ttu-id="af64b-693">To zdarzenie reprezentuje pobieranie informacji o muteksie za pośrednictwem tx_mutex_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-693">This event represents retrieving mutex information via tx_mutex_info_get.</span></span>

<span data-ttu-id="af64b-694">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-694">**Information Fields**</span></span>

- <span data-ttu-id="af64b-695">Pole informacji 1: wskaźnik do elementu mutex.</span><span class="sxs-lookup"><span data-stu-id="af64b-695">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="af64b-696">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-696">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-697">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-697">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-698">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-698">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-information-get"></a><span data-ttu-id="af64b-699">Pobieranie informacji o wydajności muteksu</span><span class="sxs-lookup"><span data-stu-id="af64b-699">Mutex Performance Information Get</span></span> 

#### <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="af64b-700">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-700">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="af64b-701">**Ikona** ![ Ikona pobierania informacji o wydajności muteksu](./media/user-guide/tx-events/image36.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-701">**Icon** ![Mutex performance information get icon](./media/user-guide/tx-events/image36.png)</span></span>

<span data-ttu-id="af64b-702">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-702">**Description**</span></span>

<span data-ttu-id="af64b-703">To zdarzenie reprezentuje pobieranie informacji o wydajności obiektu mutex za pośrednictwem tx_mutex_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-703">This event represents retrieving mutex performance information via tx_mutex_performance_info_get.</span></span>

<span data-ttu-id="af64b-704">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-704">**Information Fields**</span></span>

- <span data-ttu-id="af64b-705">Pole informacji 1: wskaźnik do elementu mutex.</span><span class="sxs-lookup"><span data-stu-id="af64b-705">Info Field 1: Pointer to mutex.</span></span>
- <span data-ttu-id="af64b-706">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-706">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-707">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-707">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-708">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-708">Info Field 4: Not used.</span></span>

### <a name="mutex-performance-system-info-get"></a><span data-ttu-id="af64b-709">Pobieranie informacji o systemie wydajności muteksu</span><span class="sxs-lookup"><span data-stu-id="af64b-709">Mutex Performance System Info Get</span></span>

#### <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="af64b-710">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-710">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="af64b-711">**Ikona** ![ Ikona uzyskiwania informacji o systemie wydajności muteksu](./media/user-guide/tx-events/image37.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-711">**Icon** ![Mutex performance system info get icon](./media/user-guide/tx-events/image37.png)</span></span>

<span data-ttu-id="af64b-712">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-712">**Description**</span></span>

<span data-ttu-id="af64b-713">To zdarzenie reprezentuje pobieranie informacji o wydajności systemu muteksów za pośrednictwem tx_mutex_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-713">This event represents retrieving mutex system performance information via tx_mutex_performance_system_info_get.</span></span>

<span data-ttu-id="af64b-714">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-714">**Information Fields**</span></span>

- <span data-ttu-id="af64b-715">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-715">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-716">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-716">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-717">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-717">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-718">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-718">Info Field 4: Not used.</span></span>

### <a name="mutex-prioritize"></a><span data-ttu-id="af64b-719">Priorytet obiektu mutex</span><span class="sxs-lookup"><span data-stu-id="af64b-719">Mutex Prioritize</span></span> 

#### <a name="tx_mutex_prioritize"></a><span data-ttu-id="af64b-720">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="af64b-720">tx_mutex_prioritize</span></span>

<span data-ttu-id="af64b-721">**Ikona** ![ Ikona priorytetyzacji obiektu mutex](./media/user-guide/tx-events/image38.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-721">**Icon** ![Mutex prioritize icon](./media/user-guide/tx-events/image38.png)</span></span>

<span data-ttu-id="af64b-722">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-722">**Description**</span></span>

<span data-ttu-id="af64b-723">To zdarzenie reprezentuje określanie priorytetów listy zawieszeń obiektu mutex za pośrednictwem tx_mutex_prioritize.</span><span class="sxs-lookup"><span data-stu-id="af64b-723">This event represents prioritizing the mutex's suspension list via tx_mutex_prioritize.</span></span>

<span data-ttu-id="af64b-724">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-724">**Information Fields**</span></span>

- <span data-ttu-id="af64b-725">Pole informacji 1: wskaźnik do odpowiadającego mu obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="af64b-725">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="af64b-726">Pole informacji 2: liczba wątków zawieszonych obecnie w elemencie mutex.</span><span class="sxs-lookup"><span data-stu-id="af64b-726">Info Field 2: Number of threads currently suspended on the mutex.</span></span>
- <span data-ttu-id="af64b-727">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-727">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-728">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-728">Info Field 4: Not used.</span></span>

### <a name="mutex-put"></a><span data-ttu-id="af64b-729">Put mutex</span><span class="sxs-lookup"><span data-stu-id="af64b-729">Mutex Put</span></span> 

#### <a name="tx_mutex_put"></a><span data-ttu-id="af64b-730">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="af64b-730">tx_mutex_put</span></span>

<span data-ttu-id="af64b-731">**Ikona** ![ Ikona Put obiektu mutex](./media/user-guide/tx-events/image39.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-731">**Icon** ![Mutex put icon](./media/user-guide/tx-events/image39.png)</span></span>

<span data-ttu-id="af64b-732">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-732">**Description**</span></span>

<span data-ttu-id="af64b-733">To zdarzenie reprezentuje wydawanie poprzednio posiadanego obiektu mutex za pośrednictwem tx_mutex_put.</span><span class="sxs-lookup"><span data-stu-id="af64b-733">This event represents releasing a previously owned mutex via tx_mutex_put.</span></span>

<span data-ttu-id="af64b-734">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-734">**Information Fields**</span></span>

- <span data-ttu-id="af64b-735">Pole informacji 1: wskaźnik do odpowiadającego mu obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="af64b-735">Info Field 1: Pointer to corresponding mutex.</span></span>
- <span data-ttu-id="af64b-736">Pole informacji 2: wskaźnik wątku będącego właścicielem obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="af64b-736">Info Field 2: Pointer of thread owning the mutex.</span></span>
- <span data-ttu-id="af64b-737">Pole informacji 3: Liczba oczekujących żądań pobrania obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="af64b-737">Info Field 3: Number of outstanding mutex get requests.</span></span>
- <span data-ttu-id="af64b-738">Pole informacji 4: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-738">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="queue-create"></a><span data-ttu-id="af64b-739">Tworzenie kolejki</span><span class="sxs-lookup"><span data-stu-id="af64b-739">Queue Create</span></span> 

#### <a name="tx_queue_create"></a><span data-ttu-id="af64b-740">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="af64b-740">tx_queue_create</span></span>

<span data-ttu-id="af64b-741">**Ikona** ![ Ikona tworzenia kolejki](./media/user-guide/tx-events/image40.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-741">**Icon** ![Queue create icon](./media/user-guide/tx-events/image40.png)</span></span>

<span data-ttu-id="af64b-742">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-742">**Description**</span></span>

<span data-ttu-id="af64b-743">To zdarzenie reprezentuje Tworzenie kolejki komunikatów za pośrednictwem tx_queue_create.</span><span class="sxs-lookup"><span data-stu-id="af64b-743">This event represents creating a message queue via tx_queue_create.</span></span>

<span data-ttu-id="af64b-744">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-744">**Information Fields**</span></span>

- <span data-ttu-id="af64b-745">Pole informacji 1: wskaźnik do bloku sterowania kolejką.</span><span class="sxs-lookup"><span data-stu-id="af64b-745">Info Field 1: Pointer to queue control block.</span></span>
- <span data-ttu-id="af64b-746">Pole informacji 2: rozmiar komunikatu — w odniesieniu do 32-bitowych wyrazów.</span><span class="sxs-lookup"><span data-stu-id="af64b-746">Info Field 2: Size of message – in terms of 32-bit words.</span></span>
- <span data-ttu-id="af64b-747">Pole informacji 3: Wskaźnik początku obszaru pamięci kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-747">Info Field 3: Pointer to start of queue memory area.</span></span>
- <span data-ttu-id="af64b-748">Pole informacji 4: liczba bajtów w obszarze pamięci kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-748">Info Field 4: Number of bytes in the queue memory area.</span></span>

### <a name="queue-delete"></a><span data-ttu-id="af64b-749">Usuwanie kolejki</span><span class="sxs-lookup"><span data-stu-id="af64b-749">Queue Delete</span></span> 

#### <a name="tx_queue_delete"></a><span data-ttu-id="af64b-750">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="af64b-750">tx_queue_delete</span></span>

<span data-ttu-id="af64b-751">**Ikona** ![ Ikona usuwania kolejki](./media/user-guide/tx-events/image41.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-751">**Icon** ![Queue delete icon](./media/user-guide/tx-events/image41.png)</span></span>

<span data-ttu-id="af64b-752">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-752">**Description**</span></span>

<span data-ttu-id="af64b-753">To zdarzenie reprezentuje usunięcie kolejki za pośrednictwem tx_queue_delete.</span><span class="sxs-lookup"><span data-stu-id="af64b-753">This event represents deleting a queue via tx_queue_delete.</span></span>

<span data-ttu-id="af64b-754">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-754">**Information Fields**</span></span>

- <span data-ttu-id="af64b-755">Pole informacji 1: wskaźnik do kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-755">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="af64b-756">Pole informacji 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-756">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-757">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-757">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-758">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-758">Info Field 4: Not used.</span></span>

### <a name="queue-flush"></a><span data-ttu-id="af64b-759">Opróżnianie kolejki</span><span class="sxs-lookup"><span data-stu-id="af64b-759">Queue Flush</span></span> 

#### <a name="tx_queue_flush"></a><span data-ttu-id="af64b-760">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="af64b-760">tx_queue_flush</span></span>

<span data-ttu-id="af64b-761">**Ikona** ![ Ikona opróżniania kolejki](./media/user-guide/tx-events/image42.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-761">**Icon** ![Queue flush icon](./media/user-guide/tx-events/image42.png)</span></span>

<span data-ttu-id="af64b-762">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-762">**Description**</span></span>

<span data-ttu-id="af64b-763">To zdarzenie reprezentuje opróżnianie (czyszczenie całej zawartości kolejki) kolejki za pośrednictwem tx_queue_flush.</span><span class="sxs-lookup"><span data-stu-id="af64b-763">This event represents flushing (clearing all queue contents) of a queue via tx_queue_flush.</span></span>

<span data-ttu-id="af64b-764">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-764">**Information Fields**</span></span>

- <span data-ttu-id="af64b-765">Pole informacji 1: wskaźnik do kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-765">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="af64b-766">Pole informacji 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-766">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-767">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-767">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-768">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-768">Info Field 4: Not used.</span></span>

### <a name="queue-front-send"></a><span data-ttu-id="af64b-769">Wysyłanie frontonu kolejki</span><span class="sxs-lookup"><span data-stu-id="af64b-769">Queue Front Send</span></span> 

#### <a name="tx_queue_front_send"></a><span data-ttu-id="af64b-770">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="af64b-770">tx_queue_front_send</span></span>

<span data-ttu-id="af64b-771">**Ikona** ![ Ikona wysyłania z kolejki](./media/user-guide/tx-events/image43.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-771">**Icon** ![Queue front send icon](./media/user-guide/tx-events/image43.png)</span></span>

<span data-ttu-id="af64b-772">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-772">**Description**</span></span>

<span data-ttu-id="af64b-773">To zdarzenie reprezentuje Wysyłanie komunikatu z przodu kolejki za pośrednictwem tx_queue_front_send.</span><span class="sxs-lookup"><span data-stu-id="af64b-773">This event represents sending a message to the front of a queue via tx_queue_front_send.</span></span>

<span data-ttu-id="af64b-774">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-774">**Information Fields**</span></span>

- <span data-ttu-id="af64b-775">Pole informacji 1: wskaźnik do kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-775">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="af64b-776">Pole informacji 2: wskaźnik do początku komunikatu.</span><span class="sxs-lookup"><span data-stu-id="af64b-776">Info Field 2: Pointer to start of message.</span></span>
- <span data-ttu-id="af64b-777">Pole informacji 3: Poczekaj na polecenie</span><span class="sxs-lookup"><span data-stu-id="af64b-777">Info Field 3: Wait option supplied to the</span></span>
- <span data-ttu-id="af64b-778">tx_queue_front_send wywołanie.</span><span class="sxs-lookup"><span data-stu-id="af64b-778">tx_queue_front_send call.</span></span>
- <span data-ttu-id="af64b-779">Pole informacji 4: liczba komunikatów, które zostały już w kolejce.</span><span class="sxs-lookup"><span data-stu-id="af64b-779">Info Field 4: Number of messages already enqueued.</span></span>

### <a name="queue-information-get"></a><span data-ttu-id="af64b-780">Pobieranie informacji o kolejce</span><span class="sxs-lookup"><span data-stu-id="af64b-780">Queue Information Get</span></span> 

#### <a name="tx_queue_info_get"></a><span data-ttu-id="af64b-781">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-781">tx_queue_info_get</span></span>

<span data-ttu-id="af64b-782">**Ikona** ![ Ikona pobierania informacji o kolejce](./media/user-guide/tx-events/image44.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-782">**Icon** ![Queue information get icon](./media/user-guide/tx-events/image44.png)</span></span>

<span data-ttu-id="af64b-783">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-783">**Description**</span></span>

<span data-ttu-id="af64b-784">To zdarzenie reprezentuje pobieranie informacji o kolejce za pośrednictwem tx_queue_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-784">This event represents getting information about a queue via tx_queue_info_get.</span></span>

<span data-ttu-id="af64b-785">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-785">**Information Fields**</span></span> 
- <span data-ttu-id="af64b-786">Pole informacji 1: wskaźnik do kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-786">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="af64b-787">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-787">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-788">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-788">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-789">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-789">Info Field 4: Not used.</span></span>

### <a name="queue-performance-info-get"></a><span data-ttu-id="af64b-790">Pobieranie informacji o wydajności kolejki</span><span class="sxs-lookup"><span data-stu-id="af64b-790">Queue Performance Info Get</span></span> 

#### <a name="tx_queue_performance_info_get"></a><span data-ttu-id="af64b-791">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-791">tx_queue_performance_info_get</span></span>

<span data-ttu-id="af64b-792">**Ikona** ![ Ikona pobierania informacji o wydajności kolejki](./media/user-guide/tx-events/image45.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-792">**Icon** ![Queue performance info get icon](./media/user-guide/tx-events/image45.png)</span></span>

<span data-ttu-id="af64b-793">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-793">**Description**</span></span>

<span data-ttu-id="af64b-794">To zdarzenie reprezentuje informacje o wydajności kolejki za pośrednictwem tx_queue_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-794">This event represents getting performance information about a queue via tx_queue_performance_info_get.</span></span>

<span data-ttu-id="af64b-795">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-795">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-796">Pole informacji 1: wskaźnik do kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-796">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="af64b-797">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-797">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-798">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-798">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-799">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-799">Info Field 4: Not used.</span></span>

### <a name="queue-performance-system-info-get"></a><span data-ttu-id="af64b-800">Informacje o systemie wydajności kolejki pobieranie</span><span class="sxs-lookup"><span data-stu-id="af64b-800">Queue Performance System Info Get</span></span> 

#### <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="af64b-801">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-801">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="af64b-802">**Ikona** ![ Ikona pobierania informacji o systemie wydajności kolejki](./media/user-guide/tx-events/image46.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-802">**Icon** ![Queue performance system info get icon](./media/user-guide/tx-events/image46.png)</span></span>

<span data-ttu-id="af64b-803">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-803">**Description**</span></span>

<span data-ttu-id="af64b-804">To zdarzenie reprezentuje pobieranie informacji o wydajności systemu na wszystkich kolejkach w systemie.</span><span class="sxs-lookup"><span data-stu-id="af64b-804">This event represents getting system performance information about all the queues in the system.</span></span>

<span data-ttu-id="af64b-805">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-805">**Information Fields**</span></span>

- <span data-ttu-id="af64b-806">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-806">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-807">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-807">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-808">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-808">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-809">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-809">Info Field 4: Not used.</span></span>

### <a name="queue-prioritize"></a><span data-ttu-id="af64b-810">Priorytety kolejki</span><span class="sxs-lookup"><span data-stu-id="af64b-810">Queue Prioritize</span></span> 

#### <a name="tx_queue_prioritize"></a><span data-ttu-id="af64b-811">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="af64b-811">tx_queue_prioritize</span></span>

<span data-ttu-id="af64b-812">**Ikona** ![ Ikona priorytetyzacji kolejki](./media/user-guide/tx-events/image47.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-812">**Icon** ![Queue prioritize icon](./media/user-guide/tx-events/image47.png)</span></span>

<span data-ttu-id="af64b-813">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-813">**Description**</span></span>

<span data-ttu-id="af64b-814">To zdarzenie reprezentuje wyznaczanie priorytetów listy zawieszania kolejki za pośrednictwem tx_queue_prioritize.</span><span class="sxs-lookup"><span data-stu-id="af64b-814">This event represents prioritizing the queue's suspension list via tx_queue_prioritize.</span></span>

<span data-ttu-id="af64b-815">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-815">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-816">Pole informacji 1: wskaźnik do odpowiedniej kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-816">Info Field 1: Pointer to corresponding queue.</span></span>
- <span data-ttu-id="af64b-817">Pole informacji 2: liczba wątków zawieszonych obecnie w kolejce.</span><span class="sxs-lookup"><span data-stu-id="af64b-817">Info Field 2: Number of threads currently suspended on the queue.</span></span>
- <span data-ttu-id="af64b-818">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-818">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-819">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-819">Info Field 4: Not used.</span></span>

#### <a name="queue-receive"></a><span data-ttu-id="af64b-820">Odbieranie kolejki</span><span class="sxs-lookup"><span data-stu-id="af64b-820">Queue Receive</span></span> 

##### <a name="tx_queue_receive"></a><span data-ttu-id="af64b-821">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="af64b-821">tx_queue_receive</span></span>

<span data-ttu-id="af64b-822">**Ikona** ![ Ikona odbierania kolejki](./media/user-guide/tx-events/image48.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-822">**Icon** ![Queue receive icon](./media/user-guide/tx-events/image48.png)</span></span>

<span data-ttu-id="af64b-823">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-823">**Description**</span></span>

<span data-ttu-id="af64b-824">To zdarzenie reprezentuje odebranie komunikatu z kolejki za pośrednictwem tx_queue_receive.</span><span class="sxs-lookup"><span data-stu-id="af64b-824">This event represents receiving a message from a queue via tx_queue_receive.</span></span>

<span data-ttu-id="af64b-825">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-825">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-826">Pole informacji 1: wskaźnik do kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-826">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="af64b-827">Pole informacji 2: wskaźnik do elementu docelowego dla komunikatu.</span><span class="sxs-lookup"><span data-stu-id="af64b-827">Info Field 2: Pointer to destination for message.</span></span> <span data-ttu-id="af64b-828">Pole informacji 3: Poczekaj na wywołanie.</span><span class="sxs-lookup"><span data-stu-id="af64b-828">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="af64b-829">Pole informacji 4: liczba komunikatów, które są obecnie w kolejce.</span><span class="sxs-lookup"><span data-stu-id="af64b-829">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send"></a><span data-ttu-id="af64b-830">Wysyłanie kolejki</span><span class="sxs-lookup"><span data-stu-id="af64b-830">Queue Send</span></span> 

#### <a name="tx_queue_send"></a><span data-ttu-id="af64b-831">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="af64b-831">tx_queue_send</span></span>

<span data-ttu-id="af64b-832">**Ikona** ![ Ikona wysyłania kolejki](./media/user-guide/tx-events/image49.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-832">**Icon** ![Queue send icon](./media/user-guide/tx-events/image49.png)</span></span>

<span data-ttu-id="af64b-833">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-833">**Description**</span></span>

<span data-ttu-id="af64b-834">To zdarzenie reprezentuje Wysyłanie komunikatu do kolejki za pośrednictwem tx_queue_send.</span><span class="sxs-lookup"><span data-stu-id="af64b-834">This event represents sending a message to a queue via tx_queue_send.</span></span>

<span data-ttu-id="af64b-835">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-835">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-836">Pole informacji 1: wskaźnik do kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-836">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="af64b-837">Pole informacji 2: wskaźnik do komunikatu.</span><span class="sxs-lookup"><span data-stu-id="af64b-837">Info Field 2: Pointer to message.</span></span>
- <span data-ttu-id="af64b-838">Pole informacji 3: Poczekaj na wywołanie.</span><span class="sxs-lookup"><span data-stu-id="af64b-838">Info Field 3: Wait option supplied to the call.</span></span>
- <span data-ttu-id="af64b-839">Pole informacji 4: liczba komunikatów, które są obecnie w kolejce.</span><span class="sxs-lookup"><span data-stu-id="af64b-839">Info Field 4: Number of messages currently queued.</span></span>

### <a name="queue-send-notify"></a><span data-ttu-id="af64b-840">Powiadomienie o wysłaniu kolejki</span><span class="sxs-lookup"><span data-stu-id="af64b-840">Queue Send Notify</span></span> 

#### <a name="tx_queue_send_notify"></a><span data-ttu-id="af64b-841">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="af64b-841">tx_queue_send_notify</span></span>

<span data-ttu-id="af64b-842">**Ikona** ![ Ikona powiadomienia o wysłaniu kolejki](./media/user-guide/tx-events/image50.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-842">**Icon** ![Queue send notify icon](./media/user-guide/tx-events/image50.png)</span></span>

<span data-ttu-id="af64b-843">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-843">**Description**</span></span>

<p><span data-ttu-id="af64b-844">To zdarzenie reprezentuje zarejestrowanie wywołania zwrotnego za pomocą tx_queue_send_notify, który jest wywoływany za każdym razem, gdy komunikat jest wysyłany do kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-844">This event represents registering a callback via tx_queue_send_notify which is called whenever a message is sent to a queue.</span></span>

<span data-ttu-id="af64b-845">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-845">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-846">Pole informacji 1: wskaźnik do kolejki.</span><span class="sxs-lookup"><span data-stu-id="af64b-846">Info Field 1: Pointer to queue.</span></span>
- <span data-ttu-id="af64b-847">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-847">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-848">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-848">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-849">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-849">Info Field 4: Not used.</span></span>

### <a name="semaphore-ceiling-put"></a><span data-ttu-id="af64b-850">Nakładanie limitu semafora</span><span class="sxs-lookup"><span data-stu-id="af64b-850">Semaphore Ceiling Put</span></span> 

#### <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="af64b-851">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="af64b-851">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="af64b-852">**Ikona** ![ Ikona umieszczenia sufitu semafora](./media/user-guide/tx-events/image51.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-852">**Icon** ![Semaphore ceiling put icon](./media/user-guide/tx-events/image51.png)</span></span>

<span data-ttu-id="af64b-853">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-853">**Description**</span></span>

<span data-ttu-id="af64b-854">To zdarzenie reprezentuje umieszczenie w semaforze za pośrednictwem tx_semaphore_ceiling_put.</span><span class="sxs-lookup"><span data-stu-id="af64b-854">This event represents putting to a semaphore via tx_semaphore_ceiling_put.</span></span> <span data-ttu-id="af64b-855">Różni się to od tx_semaphore_put, że maksymalna wartość semafora jest sprawdzana w taki sposób, że operacja Put nie może przekroczyć maksymalnej wartości lub limitu.</span><span class="sxs-lookup"><span data-stu-id="af64b-855">This differs from tx_semaphore_put in that the maximum value of the semaphore is examined such that the put operation is not allowed to exceed the maximum value or ceiling.</span></span>

<span data-ttu-id="af64b-856">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-856">**Information Fields**</span></span>

- <span data-ttu-id="af64b-857">Pole informacji 1: wskaźnik do semafora.</span><span class="sxs-lookup"><span data-stu-id="af64b-857">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="af64b-858">Pole informacji 2: Bieżąca liczba semaforów.</span><span class="sxs-lookup"><span data-stu-id="af64b-858">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="af64b-859">Pole informacji 3: liczba wątków zawieszonych w semaforze.</span><span class="sxs-lookup"><span data-stu-id="af64b-859">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="af64b-860">Pole informacji 4: limit sufitu podany w wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="af64b-860">Info Field 4: Ceiling limit supplied to the call.</span></span>

#### <a name="semaphore-create"></a><span data-ttu-id="af64b-861">Tworzenie semafora</span><span class="sxs-lookup"><span data-stu-id="af64b-861">Semaphore Create</span></span> 

##### <a name="tx_semaphore_create"></a><span data-ttu-id="af64b-862">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="af64b-862">tx_semaphore_create</span></span>

<span data-ttu-id="af64b-863">**Ikona** ![ Ikona tworzenia semafora](./media/user-guide/tx-events/image52.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-863">**Icon** ![Semaphore create icon](./media/user-guide/tx-events/image52.png)</span></span>

<span data-ttu-id="af64b-864">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-864">**Description**</span></span>

<span data-ttu-id="af64b-865">To zdarzenie reprezentuje tworzenie semafora za pośrednictwem tx_semaphore_create.</span><span class="sxs-lookup"><span data-stu-id="af64b-865">This event represents creating a semaphore via tx_semaphore_create.</span></span>

<span data-ttu-id="af64b-866">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-866">**Information Fields**</span></span>

- <span data-ttu-id="af64b-867">Pole informacji 1: wskaźnik do bloku sterowania semaforem.</span><span class="sxs-lookup"><span data-stu-id="af64b-867">Info Field 1: Pointer to semaphore control block.</span></span>
- <span data-ttu-id="af64b-868">Pole informacji 2: początkowa liczba semaforów.</span><span class="sxs-lookup"><span data-stu-id="af64b-868">Info Field 2: Initial semaphore count.</span></span>
- <span data-ttu-id="af64b-869">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-869">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-870">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-870">Info Field 4: Not used.</span></span>

### <a name="semaphore-delete"></a><span data-ttu-id="af64b-871">Usuwanie semafora</span><span class="sxs-lookup"><span data-stu-id="af64b-871">Semaphore Delete</span></span> 

#### <a name="tx_semaphore_delete"></a><span data-ttu-id="af64b-872">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="af64b-872">tx_semaphore_delete</span></span>

<span data-ttu-id="af64b-873">**Ikona** ![ Ikona usuwania semafora](./media/user-guide/tx-events/image53.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-873">**Icon** ![Semaphore delete icon](./media/user-guide/tx-events/image53.png)</span></span>

<span data-ttu-id="af64b-874">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-874">**Description**</span></span>

<span data-ttu-id="af64b-875">To zdarzenie reprezentuje usuwanie semafora za pośrednictwem tx_semaphore_delete.</span><span class="sxs-lookup"><span data-stu-id="af64b-875">This event represents deleting a semaphore via tx_semaphore_delete.</span></span>

<span data-ttu-id="af64b-876">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-876">**Information Fields**</span></span>

- <span data-ttu-id="af64b-877">Pole informacji 1: wskaźnik do semafora.</span><span class="sxs-lookup"><span data-stu-id="af64b-877">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="af64b-878">NFO pole 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-878">nfo Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-879">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-879">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-880">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-880">Info Field 4: Not used.</span></span>

### <a name="semaphore-get"></a><span data-ttu-id="af64b-881">Pobieranie semafora</span><span class="sxs-lookup"><span data-stu-id="af64b-881">Semaphore Get</span></span> 

#### <a name="tx_semaphore_get"></a><span data-ttu-id="af64b-882">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="af64b-882">tx_semaphore_get</span></span>

<span data-ttu-id="af64b-883">**Ikona** ![ Ikona pobierania semafora](./media/user-guide/tx-events/image54.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-883">**Icon** ![Semaphore get icon](./media/user-guide/tx-events/image54.png)</span></span>

<span data-ttu-id="af64b-884">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-884">**Description**</span></span>

<span data-ttu-id="af64b-885">To zdarzenie reprezentuje uzyskanie semafora za pośrednictwem tx_semaphore_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-885">This event represents obtaining a semaphore via tx_semaphore_get.</span></span>

<span data-ttu-id="af64b-886">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-886">**Information Fields**</span></span>

- <span data-ttu-id="af64b-887">Pole informacji 1: wskaźnik do semafora.</span><span class="sxs-lookup"><span data-stu-id="af64b-887">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="af64b-888">Pole informacji 2: Poczekaj na wywołanie.</span><span class="sxs-lookup"><span data-stu-id="af64b-888">Info Field 2: Wait option supplied to the call.</span></span>
- <span data-ttu-id="af64b-889">Pole informacji 3: Bieżąca liczba semaforów.</span><span class="sxs-lookup"><span data-stu-id="af64b-889">Info Field 3: Current semaphore count.</span></span>
- <span data-ttu-id="af64b-890">Pole informacji 4: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-890">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-information-get"></a><span data-ttu-id="af64b-891">Pobieranie informacji o semaforze</span><span class="sxs-lookup"><span data-stu-id="af64b-891">Semaphore Information Get</span></span> 

#### <a name="tx_semaphore_info_get"></a><span data-ttu-id="af64b-892">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-892">tx_semaphore_info_get</span></span>

<span data-ttu-id="af64b-893">**Ikona** ![ Ikona pobierania informacji o semaforach](./media/user-guide/tx-events/image55.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-893">**Icon** ![Semaphore information get icon](./media/user-guide/tx-events/image55.png)</span></span>

<span data-ttu-id="af64b-894">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-894">**Description**</span></span>

<span data-ttu-id="af64b-895">To zdarzenie reprezentuje uzyskanie informacji o semaforze za pośrednictwem tx_semaphore_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-895">This event represents obtaining information about a semaphore via tx_semaphore_info_get.</span></span>

<span data-ttu-id="af64b-896">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-896">**Information Fields**</span></span>

- <span data-ttu-id="af64b-897">Pole informacji 1: wskaźnik do semafora.</span><span class="sxs-lookup"><span data-stu-id="af64b-897">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="af64b-898">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-898">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-899">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-899">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-900">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-900">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-info-get"></a><span data-ttu-id="af64b-901">Pobieranie informacji o wydajności semafora</span><span class="sxs-lookup"><span data-stu-id="af64b-901">Semaphore Performance Info Get</span></span> 

#### <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="af64b-902">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-902">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="af64b-903">**Ikona** ![ Ikona pobierania informacji o wydajności semafora](./media/user-guide/tx-events/image56.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-903">**Icon** ![Semaphore performance info get icon](./media/user-guide/tx-events/image56.png)</span></span>

<span data-ttu-id="af64b-904">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-904">**Description**</span></span>

<span data-ttu-id="af64b-905">To zdarzenie reprezentuje uzyskanie informacji o wydajności semafora za pośrednictwem tx_semaphore_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-905">This event represents obtaining performance information about a semaphore via tx_semaphore_performance_info_get.</span></span>

<span data-ttu-id="af64b-906">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-906">**Information Fields**</span></span>

- <span data-ttu-id="af64b-907">Pole informacji 1: wskaźnik do semafora.</span><span class="sxs-lookup"><span data-stu-id="af64b-907">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="af64b-908">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-908">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-909">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-909">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-910">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-910">Info Field 4: Not used.</span></span>

### <a name="semaphore-performance-system-info"></a><span data-ttu-id="af64b-911">Informacje o systemie wydajności semafora</span><span class="sxs-lookup"><span data-stu-id="af64b-911">Semaphore Performance System Info</span></span> 

#### <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="af64b-912">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-912">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="af64b-913">**Ikona** ![ Ikona informacji o systemie wydajności semafora](./media/user-guide/tx-events/image57.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-913">**Icon** ![Semaphore performance system info icon](./media/user-guide/tx-events/image57.png)</span></span>

<span data-ttu-id="af64b-914">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-914">**Description**</span></span>

<span data-ttu-id="af64b-915">To zdarzenie reprezentuje uzyskanie informacji o wydajności wszystkich semaforów w systemie za pośrednictwem tx_semaphore_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-915">This event represents obtaining performance information about all semaphores in the system via tx_semaphore_performance_system_info_get.</span></span>

<span data-ttu-id="af64b-916">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-916">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-917">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-917">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-918">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-918">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-919">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-919">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-920">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-920">Info Field 4: Not used.</span></span>

### <a name="semaphore-prioritize"></a><span data-ttu-id="af64b-921">Priorytetyzacja semaforów</span><span class="sxs-lookup"><span data-stu-id="af64b-921">Semaphore Prioritize</span></span> 

#### <a name="tx_semaphore_prioritize"></a><span data-ttu-id="af64b-922">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="af64b-922">tx_semaphore_prioritize</span></span>

<span data-ttu-id="af64b-923">**Ikona** ![ Ikona priorytetyzacji semaforów](./media/user-guide/tx-events/image58.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-923">**Icon** ![Semaphore prioritize icon](./media/user-guide/tx-events/image58.png)</span></span>

<span data-ttu-id="af64b-924">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-924">**Description**</span></span>

<span data-ttu-id="af64b-925">To zdarzenie reprezentuje określanie priorytetów listy zawieszania semafora za pośrednictwem tx_semaphore_prioritize.</span><span class="sxs-lookup"><span data-stu-id="af64b-925">This event represents prioritizing the semaphore's suspension list via tx_semaphore_prioritize.</span></span>

<span data-ttu-id="af64b-926">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-926">**Information Fields**</span></span>

- <span data-ttu-id="af64b-927">Pole informacji 1: wskaźnik do odpowiedniego semafora.</span><span class="sxs-lookup"><span data-stu-id="af64b-927">Info Field 1: Pointer to corresponding semaphore.</span></span>
- <span data-ttu-id="af64b-928">Pole informacji 2: liczba wątków zawieszonych obecnie w semaforze.</span><span class="sxs-lookup"><span data-stu-id="af64b-928">Info Field 2: Number of threads currently suspended on the semaphore.</span></span>
- <span data-ttu-id="af64b-929">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-929">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-930">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-930">Info Field 4: Not used.</span></span>

### <a name="semaphore-put"></a><span data-ttu-id="af64b-931">Umieszczenie semafora</span><span class="sxs-lookup"><span data-stu-id="af64b-931">Semaphore Put</span></span> 

#### <a name="tx_semaphore_put"></a><span data-ttu-id="af64b-932">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="af64b-932">tx_semaphore_put</span></span>

<span data-ttu-id="af64b-933">**Ikona** ![ Ikona umieszczenia semafora](./media/user-guide/tx-events/image59.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-933">**Icon** ![Semaphore put icon](./media/user-guide/tx-events/image59.png)</span></span>

<span data-ttu-id="af64b-934">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-934">**Description**</span></span>

<span data-ttu-id="af64b-935">To zdarzenie reprezentuje zwolnienie wystąpienia semafora za pośrednictwem tx_semaphore_put.</span><span class="sxs-lookup"><span data-stu-id="af64b-935">This event represents releasing a semaphore instance via tx_semaphore_put.</span></span>

<span data-ttu-id="af64b-936">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-936">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-937">Pole informacji 1: wskaźnik do odpowiedniego semafora.</span><span class="sxs-lookup"><span data-stu-id="af64b-937">Info Field 1: Pointer to corresponding semaphore.</span></span> <span data-ttu-id="af64b-938">Pole informacji 2: Bieżąca liczba semaforów.</span><span class="sxs-lookup"><span data-stu-id="af64b-938">Info Field 2: Current semaphore count.</span></span>
- <span data-ttu-id="af64b-939">Pole informacji 3: liczba wątków zawieszonych w semaforze.</span><span class="sxs-lookup"><span data-stu-id="af64b-939">Info Field 3: Number of threads suspended on the semaphore.</span></span>
- <span data-ttu-id="af64b-940">Pole informacji 4: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-940">Info Field 4: Stack pointer at time of call.</span></span>

### <a name="semaphore-put-notify"></a><span data-ttu-id="af64b-941">Powiadomienie o przeniesieniu semafora</span><span class="sxs-lookup"><span data-stu-id="af64b-941">Semaphore Put Notify</span></span> 

#### <a name="tx_semaphore_put_notify"></a><span data-ttu-id="af64b-942">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="af64b-942">tx_semaphore_put_notify</span></span>

<span data-ttu-id="af64b-943">**Ikona** ![ Ikona powiadomienia dotyczącego umieszczenia semafora](./media/user-guide/tx-events/image60.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-943">**Icon** ![Semaphore put notify icon](./media/user-guide/tx-events/image60.png)</span></span>

<span data-ttu-id="af64b-944">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-944">**Description**</span></span>

<span data-ttu-id="af64b-945">To zdarzenie reprezentuje zarejestrowanie wywołania zwrotnego za pomocą tx_semaphore_put_notify, który jest wywoływany za każdym razem, gdy wystąpienie semafora jest umieszczane.</span><span class="sxs-lookup"><span data-stu-id="af64b-945">This event represents registering a callback via tx_semaphore_put_notify that is called whenever a semaphore instance is put.</span></span>

<span data-ttu-id="af64b-946">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-946">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-947">Pole informacji 1: wskaźnik do semafora.</span><span class="sxs-lookup"><span data-stu-id="af64b-947">Info Field 1: Pointer to semaphore.</span></span>
- <span data-ttu-id="af64b-948">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-948">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-949">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-949">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-950">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-950">Info Field 4: Not used.</span></span>

### <a name="thread-create"></a><span data-ttu-id="af64b-951">Tworzenie wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-951">Thread Create</span></span> 

#### <a name="tx_thread_create"></a><span data-ttu-id="af64b-952">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="af64b-952">tx_thread_create</span></span>

<span data-ttu-id="af64b-953">**Ikona** ![ Ikona tworzenia wątku](./media/user-guide/tx-events/image61.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-953">**Icon** ![Thread create icon](./media/user-guide/tx-events/image61.png)</span></span>

<span data-ttu-id="af64b-954">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-954">**Description**</span></span>

<span data-ttu-id="af64b-955">To zdarzenie reprezentuje tworzenie wątku za pośrednictwem tx_thread_create.</span><span class="sxs-lookup"><span data-stu-id="af64b-955">This event represents creating a thread via tx_thread_create.</span></span>

<span data-ttu-id="af64b-956">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-956">**Information Fields**</span></span>

- <span data-ttu-id="af64b-957">Pole informacji 1: wskaźnik do bloku sterowania wątkiem.</span><span class="sxs-lookup"><span data-stu-id="af64b-957">Info Field 1: Pointer to thread control block.</span></span>
- <span data-ttu-id="af64b-958">Pole informacji 2: priorytet wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-958">Info Field 2: Priority of thread.</span></span>
- <span data-ttu-id="af64b-959">Pole informacji 3: Wskaźnik stosu dla wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-959">Info Field 3: Stack pointer for thread.</span></span>
- <span data-ttu-id="af64b-960">NFO pole 4: rozmiar stosu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="af64b-960">nfo Field 4: Size of stack in bytes.</span></span>

### <a name="thread-delete"></a><span data-ttu-id="af64b-961">Usuwanie wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-961">Thread Delete</span></span> 

#### <a name="tx_thread_delete"></a><span data-ttu-id="af64b-962">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="af64b-962">tx_thread_delete</span></span>

<span data-ttu-id="af64b-963">**Ikona** ![ Ikona usuwania wątku](./media/user-guide/tx-events/image62.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-963">**Icon** ![Thread delete icon](./media/user-guide/tx-events/image62.png)</span></span>

<span data-ttu-id="af64b-964">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-964">**Description**</span></span>

<span data-ttu-id="af64b-965">To zdarzenie reprezentuje usuwanie wątku za pośrednictwem tx_thread_delete.</span><span class="sxs-lookup"><span data-stu-id="af64b-965">This event represents deleting a thread via tx_thread_delete.</span></span>

<span data-ttu-id="af64b-966">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-966">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-967">Pole informacji 1: wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-967">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="af64b-968">Pole informacji 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-968">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-969">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-969">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-970">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-970">Info Field 4: Not used.</span></span>

### <a name="thread-entryexit-notify"></a><span data-ttu-id="af64b-971">Powiadomienie o wejściu/wyjściu wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-971">Thread Entry/Exit Notify</span></span> 

#### <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="af64b-972">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="af64b-972">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="af64b-973">**Ikona** ![ Ikona powiadomienia o wejściu/wyjściu wątku](./media/user-guide/tx-events/image63.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-973">**Icon** ![Thread entry/exit notify icon](./media/user-guide/tx-events/image63.png)</span></span>

<span data-ttu-id="af64b-974">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-974">**Description**</span></span>

<span data-ttu-id="af64b-975">To zdarzenie reprezentuje rejestrację wywołania zwrotnego za pomocą tx_thread_entry_exit_notify, która jest wywoływana za każdym razem, gdy wątek zostanie wprowadzony lub zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="af64b-975">This event represents registering a callback via tx_thread_entry_exit_notify that is called whenever a thread is entered or exits.</span></span>

<span data-ttu-id="af64b-976">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-976">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-977">Pole informacji 1: wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-977">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="af64b-978">Pole informacji 2: stan wątku w czasie rejestracji.</span><span class="sxs-lookup"><span data-stu-id="af64b-978">Info Field 2: Thread state at time of the registration.</span></span>
- <span data-ttu-id="af64b-979">Pole informacji 3: wskaźnik do stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-979">Info Field 3: Pointer to stack at time of call.</span></span>
- <span data-ttu-id="af64b-980">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-980">Info Field 4: Not used.</span></span>

#### <a name="thread-identify"></a><span data-ttu-id="af64b-981">Identyfikator wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-981">Thread Identify</span></span> 

##### <a name="tx_thread_identify"></a><span data-ttu-id="af64b-982">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="af64b-982">tx_thread_identify</span></span>

<span data-ttu-id="af64b-983">**Ikona** ![ Ikona identyfikacji wątku](./media/user-guide/tx-events/image64.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-983">**Icon** ![Thread identify icon](./media/user-guide/tx-events/image64.png)</span></span>

<span data-ttu-id="af64b-984">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-984">**Description**</span></span>

<span data-ttu-id="af64b-985">To zdarzenie reprezentuje wskaźnik bieżącego wątku za pośrednictwem tx_thread_identify.</span><span class="sxs-lookup"><span data-stu-id="af64b-985">This event represents getting the current thread pointer via tx_thread_identify.</span></span>

<span data-ttu-id="af64b-986">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-986">**Information Fields**</span></span>

- <span data-ttu-id="af64b-987">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-987">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-988">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-988">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-989">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-989">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-990">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-990">Info Field 4: Not used.</span></span>

### <a name="thread-information-get"></a><span data-ttu-id="af64b-991">Pobieranie informacji o wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-991">Thread Information Get</span></span> 

#### <a name="tx_thread_info_get"></a><span data-ttu-id="af64b-992">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-992">tx_thread_info_get</span></span>

<span data-ttu-id="af64b-993">**Ikona** ![ Ikona pobierania informacji o wątkach](./media/user-guide/tx-events/image65.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-993">**Icon** ![Thread information get icon](./media/user-guide/tx-events/image65.png)</span></span>

<span data-ttu-id="af64b-994">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-994">**Description**</span></span>

<span data-ttu-id="af64b-995">To zdarzenie reprezentuje pobieranie informacji o określonym wątku za pośrednictwem tx_thread_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-995">This event represents getting information about the specified thread via tx_thread_info_get.</span></span>

<span data-ttu-id="af64b-996">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-996">**Information Fields**</span></span>

- <span data-ttu-id="af64b-997">Pole informacji 1: wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-997">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="af64b-998">Pole informacji 2: stan wątku w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-998">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="af64b-999">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-999">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1000">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1000">Info Field 4: Not used.</span></span>

#### <a name="thread-performance-information-get"></a><span data-ttu-id="af64b-1001">Pobieranie informacji o wydajności wątków</span><span class="sxs-lookup"><span data-stu-id="af64b-1001">Thread Performance Information Get</span></span> 

##### <a name="tx_thread_performance_info_get"></a><span data-ttu-id="af64b-1002">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-1002">tx_thread_performance_info_get</span></span>

<span data-ttu-id="af64b-1003">**Ikona** ![ Ikona uzyskiwania informacji o wydajności wątków](./media/user-guide/tx-events/image66.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1003">**Icon** ![Thread performance information get icon](./media/user-guide/tx-events/image66.png)</span></span>

<span data-ttu-id="af64b-1004">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1004">**Description**</span></span>

<span data-ttu-id="af64b-1005">To zdarzenie reprezentuje informacje o wydajności określonego wątku za pośrednictwem tx_thread_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-1005">This event represents getting performance information about the specified thread via tx_thread_performance_info_get.</span></span>

<span data-ttu-id="af64b-1006">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1006">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1007">Pole informacji 1: wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-1007">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="af64b-1008">Pole informacji 2: stan wątku w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1008">Info Field 2: State of thread at time of call.</span></span>
- <span data-ttu-id="af64b-1009">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1009">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1010">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1010">Info Field 4: Not used.</span></span>

### <a name="thread-performance-system-info-get"></a><span data-ttu-id="af64b-1011">Pobieranie informacji o systemie wydajności wątków</span><span class="sxs-lookup"><span data-stu-id="af64b-1011">Thread Performance System Info Get</span></span> 

#### <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="af64b-1012">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-1012">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="af64b-1013">**Ikona** ![ Ikona pobierania informacji o systemie wydajności wątków](./media/user-guide/tx-events/image67.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1013">**Icon** ![Thread performance system info get icon](./media/user-guide/tx-events/image67.png)</span></span>

<span data-ttu-id="af64b-1014">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1014">**Description**</span></span>

<span data-ttu-id="af64b-1015">To zdarzenie reprezentuje informacje o wydajności wszystkich wątków za pośrednictwem tx_thread_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-1015">This event represents getting performance information about all threads via tx_thread_performance_system_info_get.</span></span>

<span data-ttu-id="af64b-1016">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1016">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-1017">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1017">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-1018">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1018">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-1019">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1019">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1020">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1020">Info Field 4: Not used.</span></span>

### <a name="thread-preemption-change"></a><span data-ttu-id="af64b-1021">Zmiana zastępujący wątek</span><span class="sxs-lookup"><span data-stu-id="af64b-1021">Thread Preemption Change</span></span> 

#### <a name="tx_thread_preemption_change"></a><span data-ttu-id="af64b-1022">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="af64b-1022">tx_thread_preemption_change</span></span>

<span data-ttu-id="af64b-1023">**Ikona** ![ Ikona zmiany zastępujący wątek](./media/user-guide/tx-events/image68.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1023">**Icon** ![Thread preemption change icon](./media/user-guide/tx-events/image68.png)</span></span>

<span data-ttu-id="af64b-1024">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1024">**Description**</span></span>

<span data-ttu-id="af64b-1025">To zdarzenie reprezentuje próg zastępujący wątku za pośrednictwem tx_thread_preemption_change.</span><span class="sxs-lookup"><span data-stu-id="af64b-1025">This event represents changing a thread's preemption-threshold via tx_thread_preemption_change.</span></span>

<span data-ttu-id="af64b-1026">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1026">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-1027">Pole informacji 1: wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-1027">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="af64b-1028">Pole informacji 2: nowy przekroczenie — próg.</span><span class="sxs-lookup"><span data-stu-id="af64b-1028">Info Field 2: New preemption-threshold.</span></span>
- <span data-ttu-id="af64b-1029">Pole informacji 3: poprzednie przekroczenie — próg.</span><span class="sxs-lookup"><span data-stu-id="af64b-1029">Info Field 3: Previous preemption-threshold.</span></span>
- <span data-ttu-id="af64b-1030">Pole informacji 4: stan wątku w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1030">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-priority-change"></a><span data-ttu-id="af64b-1031">Zmiana priorytetu wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-1031">Thread Priority Change</span></span> 

#### <a name="tx_thread_priority_change"></a><span data-ttu-id="af64b-1032">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="af64b-1032">tx_thread_priority_change</span></span>

<span data-ttu-id="af64b-1033">**Ikona** ![ Ikona zmiany priorytetu wątku](./media/user-guide/tx-events/image69.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1033">**Icon** ![Thread priority change icon](./media/user-guide/tx-events/image69.png)</span></span>

<span data-ttu-id="af64b-1034">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1034">**Description**</span></span>

<span data-ttu-id="af64b-1035">To zdarzenie reprezentuje zmianę priorytetu wątku za pośrednictwem tx_thread_priority_change.</span><span class="sxs-lookup"><span data-stu-id="af64b-1035">This event represents changing a thread's priority via tx_thread_priority_change.</span></span>

- <span data-ttu-id="af64b-1036">Pola informacji</span><span class="sxs-lookup"><span data-stu-id="af64b-1036">Information Fields</span></span> 
- <span data-ttu-id="af64b-1037">Pole informacji 1: wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-1037">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="af64b-1038">Pole informacji 2: nowy priorytet.</span><span class="sxs-lookup"><span data-stu-id="af64b-1038">Info Field 2: New priority.</span></span>
- <span data-ttu-id="af64b-1039">Pole informacji 3: poprzedni priorytet.</span><span class="sxs-lookup"><span data-stu-id="af64b-1039">Info Field 3: Previous priority.</span></span>
- <span data-ttu-id="af64b-1040">Pole informacji 4: stan wątku w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1040">Info Field 4: Thread's state at time of call.</span></span>

### <a name="thread-relinquish"></a><span data-ttu-id="af64b-1041">Zrzeka się wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-1041">Thread Relinquish</span></span> 

#### <a name="tx_thread_relinquish"></a><span data-ttu-id="af64b-1042">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="af64b-1042">tx_thread_relinquish</span></span>

<span data-ttu-id="af64b-1043">**Ikona** ![ Ikona zrzeczenia wątku](./media/user-guide/tx-events/image70.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1043">**Icon** ![Thread relinquish icon](./media/user-guide/tx-events/image70.png)</span></span>

<span data-ttu-id="af64b-1044">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1044">**Description**</span></span>

<span data-ttu-id="af64b-1045">To zdarzenie reprezentuje procesor z wątku za pośrednictwem tx_thread_relinquish.</span><span class="sxs-lookup"><span data-stu-id="af64b-1045">This event represents relinquishing the processor from a thread via tx_thread_relinquish.</span></span>

<span data-ttu-id="af64b-1046">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1046">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1047">Pole informacji 1: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1047">Info Field 1: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-1048">Pole informacji 2: wskaźnik do następnego wątku do wykonania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1048">Info Field 2: Pointer to the next thread to execute.</span></span>
- <span data-ttu-id="af64b-1049">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1049">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1050">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1050">Info Field 4: Not used.</span></span>

### <a name="thread-reset"></a><span data-ttu-id="af64b-1051">Resetowanie wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-1051">Thread Reset</span></span> 

#### <a name="tx_thread_reset"></a><span data-ttu-id="af64b-1052">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="af64b-1052">tx_thread_reset</span></span>

<span data-ttu-id="af64b-1053">**Ikona** ![ Ikona resetowania wątku](./media/user-guide/tx-events/image71.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1053">**Icon** ![Thread reset icon](./media/user-guide/tx-events/image71.png)</span></span>

<span data-ttu-id="af64b-1054">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1054">**Description**</span></span>

<span data-ttu-id="af64b-1055">To zdarzenie reprezentuje zresetowanie ukończonego lub zakończonego wątku za pośrednictwem tx_thread_reset.</span><span class="sxs-lookup"><span data-stu-id="af64b-1055">This event represents resetting a completed or terminated thread via tx_thread_reset.</span></span>

<span data-ttu-id="af64b-1056">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1056">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1057">Pole informacji 1: wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-1057">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="af64b-1058">Pole informacji 2: stan wątku w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1058">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="af64b-1059">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1059">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1060">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1060">Info Field 4: Not used.</span></span>

#### <a name="thread-resume"></a><span data-ttu-id="af64b-1061">Wznowienie wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-1061">Thread Resume</span></span> 

##### <a name="tx_thread_resume"></a><span data-ttu-id="af64b-1062">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="af64b-1062">tx_thread_resume</span></span>

<span data-ttu-id="af64b-1063">**Ikona** ![ Ikona wznowienia wątku](./media/user-guide/tx-events/image72.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1063">**Icon** ![Thread resume icon](./media/user-guide/tx-events/image72.png)</span></span>

<span data-ttu-id="af64b-1064">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1064">**Description**</span></span>

<span data-ttu-id="af64b-1065">To zdarzenie reprezentuje wznawianie zawieszonego wątku za pośrednictwem tx_thread_resume.</span><span class="sxs-lookup"><span data-stu-id="af64b-1065">This event represents resuming a suspended thread via tx_thread_resume.</span></span>

<span data-ttu-id="af64b-1066">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1066">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1067">Pole informacji 1: wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-1067">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="af64b-1068">Pole informacji 2: stan wątku w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1068">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="af64b-1069">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1069">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-1070">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1070">Info Field 4: Not used.</span></span>

### <a name="thread-sleep"></a><span data-ttu-id="af64b-1071">Wątek uśpienia</span><span class="sxs-lookup"><span data-stu-id="af64b-1071">Thread Sleep</span></span> 

#### <a name="tx_thread_sleep"></a><span data-ttu-id="af64b-1072">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="af64b-1072">tx_thread_sleep</span></span>

<span data-ttu-id="af64b-1073">**Ikona** ![ Ikona uśpienia wątku](./media/user-guide/tx-events/image73.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1073">**Icon** ![Thread sleep icon](./media/user-guide/tx-events/image73.png)</span></span>

<span data-ttu-id="af64b-1074">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1074">**Description**</span></span>

<span data-ttu-id="af64b-1075">To zdarzenie reprezentuje wstrzymanie bieżącego wątku dla określonej liczby taktów czasomierza za pośrednictwem tx_thread_sleep.</span><span class="sxs-lookup"><span data-stu-id="af64b-1075">This event represents suspending the current thread for a specified number of timer ticks via tx_thread_sleep.</span></span>

<span data-ttu-id="af64b-1076">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1076">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1077">Pole informacji 1: liczba taktów do zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="af64b-1077">Info Field 1: Number of ticks to suspend for.</span></span>
- <span data-ttu-id="af64b-1078">Pole informacji 2: stan wątku w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1078">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="af64b-1079">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1079">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-1080">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1080">Info Field 4: Not used.</span></span>

### <a name="thread-stack-error-notify"></a><span data-ttu-id="af64b-1081">Powiadomienie o błędzie stosu wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-1081">Thread Stack Error Notify</span></span> 

#### <a name="tx_thread_stack_error_notify_event"></a><span data-ttu-id="af64b-1082">tx_thread_stack_error_notify_event</span><span class="sxs-lookup"><span data-stu-id="af64b-1082">tx_thread_stack_error_notify_event</span></span>

<span data-ttu-id="af64b-1083">**Ikona** ![ Ikona powiadomienia o błędzie stosu wątku](./media/user-guide/tx-events/image74.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1083">**Icon** ![Thread stack error notify icon](./media/user-guide/tx-events/image74.png)</span></span>

<span data-ttu-id="af64b-1084">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1084">**Description**</span></span>

<span data-ttu-id="af64b-1085">To zdarzenie reprezentuje procedurę rejestrowania błędu stosu wątku za pośrednictwem tx_thread_stack_error_notify_event.</span><span class="sxs-lookup"><span data-stu-id="af64b-1085">This event represents registering a thread stack error notification routine via tx_thread_stack_error_notify_event.</span></span>

<span data-ttu-id="af64b-1086">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1086">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-1087">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1087">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-1088">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1088">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-1089">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1089">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1090">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1090">Info Field 4: Not used.</span></span>

### <a name="thread-suspend"></a><span data-ttu-id="af64b-1091">Wstrzymywanie wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-1091">Thread Suspend</span></span> 

#### <a name="tx_thread_suspend"></a><span data-ttu-id="af64b-1092">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="af64b-1092">tx_thread_suspend</span></span>

<span data-ttu-id="af64b-1093">**Ikona** ![ Ikona wstrzymania wątku](./media/user-guide/tx-events/image75.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1093">**Icon** ![Thread suspend icon](./media/user-guide/tx-events/image75.png)</span></span>

<span data-ttu-id="af64b-1094">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1094">**Description**</span></span>

<span data-ttu-id="af64b-1095">To zdarzenie reprezentuje zawieszenie wątku za pośrednictwem tx_thread_suspend.</span><span class="sxs-lookup"><span data-stu-id="af64b-1095">This event represents suspending a thread via tx_thread_suspend.</span></span>

<span data-ttu-id="af64b-1096">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1096">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-1097">Pole informacji 1: wskaźnik do wątku, który ma zostać wstrzymany.</span><span class="sxs-lookup"><span data-stu-id="af64b-1097">Info Field 1: Pointer to thread to suspend.</span></span>
- <span data-ttu-id="af64b-1098">Pole informacji 2: stan wątku w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1098">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="af64b-1099">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1099">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-1100">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1100">Info Field 4: Not used.</span></span>

### <a name="thread-terminate"></a><span data-ttu-id="af64b-1101">Zakończenie wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-1101">Thread Terminate</span></span> 

#### <a name="tx_thread_terminate"></a><span data-ttu-id="af64b-1102">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="af64b-1102">tx_thread_terminate</span></span>

<span data-ttu-id="af64b-1103">**Ikona** ![ Ikona zakończenia wątku](./media/user-guide/tx-events/image76.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1103">**Icon** ![Thread terminate icon](./media/user-guide/tx-events/image76.png)</span></span>

<span data-ttu-id="af64b-1104">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1104">**Description**</span></span>

<span data-ttu-id="af64b-1105">To zdarzenie reprezentuje zakończenie wątku za pośrednictwem tx_thread_terminate.</span><span class="sxs-lookup"><span data-stu-id="af64b-1105">This event represents terminating a thread via tx_thread_terminate.</span></span>

<span data-ttu-id="af64b-1106">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1106">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-1107">Pole informacji 1: wskaźnik do wątku do przerwania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1107">Info Field 1: Pointer to thread to terminate.</span></span>
- <span data-ttu-id="af64b-1108">Pole informacji 2: stan wątku w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1108">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="af64b-1109">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1109">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-1110">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1110">Info Field 4: Not used.</span></span>

### <a name="thread-time-slice-change"></a><span data-ttu-id="af64b-1111">Time-Slice zmiany wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-1111">Thread Time-Slice Change</span></span> 

#### <a name="tx_thread_time_slice_change"></a><span data-ttu-id="af64b-1112">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="af64b-1112">tx_thread_time_slice_change</span></span>

<span data-ttu-id="af64b-1113">**Ikona** ![ Ikona zmiany czasu wątku](./media/user-guide/tx-events/image77.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1113">**Icon** ![Thread time-slice change icon](./media/user-guide/tx-events/image77.png)</span></span>

<span data-ttu-id="af64b-1114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1114">**Description**</span></span>

<span data-ttu-id="af64b-1115">To zdarzenie reprezentuje zmianę wycinka czasu wątku za pośrednictwem tx_thread_time_slice_change.</span><span class="sxs-lookup"><span data-stu-id="af64b-1115">This event represents changing a thread's time-slice via tx_thread_time_slice_change.</span></span>

<span data-ttu-id="af64b-1116">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1116">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1117">Pole informacji 1: wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-1117">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="af64b-1118">Pole informacji 2: nowy plasterek czasu.</span><span class="sxs-lookup"><span data-stu-id="af64b-1118">Info Field 2: New time-slice.</span></span>
- <span data-ttu-id="af64b-1119">Pole informacji 3: poprzedni czas wycinka.</span><span class="sxs-lookup"><span data-stu-id="af64b-1119">Info Field 3: Previous time-slice.</span></span>
- <span data-ttu-id="af64b-1120">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1120">Info Field 4: Not used.</span></span>

### <a name="thread-wait-abort"></a><span data-ttu-id="af64b-1121">Przerwanie oczekiwania wątku</span><span class="sxs-lookup"><span data-stu-id="af64b-1121">Thread Wait Abort</span></span> 

#### <a name="tx_thread_wait_abort"></a><span data-ttu-id="af64b-1122">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="af64b-1122">tx_thread_wait_abort</span></span>

<span data-ttu-id="af64b-1123">**Ikona** ![ Ikona przerwania oczekiwania wątku](./media/user-guide/tx-events/image78.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1123">**Icon** ![Thread wait abort icon](./media/user-guide/tx-events/image78.png)</span></span>

<span data-ttu-id="af64b-1124">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1124">**Description**</span></span>

<span data-ttu-id="af64b-1125">To zdarzenie reprezentuje przerwanie zawieszenia wątku za pośrednictwem tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="af64b-1125">This event represents aborting a thread's suspension via tx_thread_wait_abort.</span></span>

<span data-ttu-id="af64b-1126">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1126">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1127">Pole informacji 1: wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="af64b-1127">Info Field 1: Pointer to thread.</span></span>
- <span data-ttu-id="af64b-1128">Pole informacji 2: stan wątku w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1128">Info Field 2: Thread's state at time of call.</span></span>
- <span data-ttu-id="af64b-1129">Pole informacji 3: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1129">Info Field 3: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-1130">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1130">Info Field 4: Not used.</span></span>

### <a name="time-get"></a><span data-ttu-id="af64b-1131">Czas Get</span><span class="sxs-lookup"><span data-stu-id="af64b-1131">Time Get</span></span> 

#### <a name="tx_time_get"></a><span data-ttu-id="af64b-1132">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="af64b-1132">tx_time_get</span></span>

<span data-ttu-id="af64b-1133">**Ikona** ![ Ikona uzyskiwania czasu](./media/user-guide/tx-events/image79.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1133">**Icon** ![Time get icon](./media/user-guide/tx-events/image79.png)</span></span>

<span data-ttu-id="af64b-1134">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1134">**Description**</span></span>

<span data-ttu-id="af64b-1135">To zdarzenie reprezentuje bieżącą liczbę cykli czasomierza za pośrednictwem tx_time_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-1135">This event represents getting the current number of timer ticks via tx_time_get.</span></span>

<span data-ttu-id="af64b-1136">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1136">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1137">Pole informacji 1: Bieżąca liczba taktów czasomierza.</span><span class="sxs-lookup"><span data-stu-id="af64b-1137">Info Field 1: Current number of timer ticks.</span></span>
- <span data-ttu-id="af64b-1138">Pole informacji 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1138">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-1139">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1139">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1140">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1140">Info Field 4: Not used.</span></span>

### <a name="time-set"></a><span data-ttu-id="af64b-1141">Zestaw czasu</span><span class="sxs-lookup"><span data-stu-id="af64b-1141">Time Set</span></span> 

#### <a name="tx_time_set"></a><span data-ttu-id="af64b-1142">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="af64b-1142">tx_time_set</span></span>

<span data-ttu-id="af64b-1143">**Ikona** ![ Ikona zestawu czasu](./media/user-guide/tx-events/image80.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1143">**Icon** ![Time set icon](./media/user-guide/tx-events/image80.png)</span></span>

<span data-ttu-id="af64b-1144">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1144">**Description**</span></span>

<span data-ttu-id="af64b-1145">To zdarzenie reprezentuje ustawienie bieżącej liczby taktów czasomierza za pośrednictwem tx_time_set.</span><span class="sxs-lookup"><span data-stu-id="af64b-1145">This event represents setting the current number of timer ticks via tx_time_set.</span></span>

<span data-ttu-id="af64b-1146">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1146">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1147">Pole informacji 1: Nowa liczba taktów czasomierza.</span><span class="sxs-lookup"><span data-stu-id="af64b-1147">Info Field 1: New number of timer ticks.</span></span>
- <span data-ttu-id="af64b-1148">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1148">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-1149">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1149">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1150">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1150">Info Field 4: Not used.</span></span>

### <a name="timer-activate"></a><span data-ttu-id="af64b-1151">Aktywuj czasomierz</span><span class="sxs-lookup"><span data-stu-id="af64b-1151">Timer Activate</span></span> 

#### <a name="tx_timer_activate"></a><span data-ttu-id="af64b-1152">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="af64b-1152">tx_timer_activate</span></span>

<span data-ttu-id="af64b-1153">**Ikona** ![ Ikona aktywacji czasomierza](./media/user-guide/tx-events/image81.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1153">**Icon** ![Timer activate icon](./media/user-guide/tx-events/image81.png)</span></span>

<span data-ttu-id="af64b-1154">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1154">**Description**</span></span>

<span data-ttu-id="af64b-1155">To zdarzenie reprezentuje aktywację określonego czasomierza za pośrednictwem tx_timer_activate.</span><span class="sxs-lookup"><span data-stu-id="af64b-1155">This event represents activating the specified timer via tx_timer_activate.</span></span>

<span data-ttu-id="af64b-1156">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1156">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1157">Pole informacji 1: wskaźnik do czasomierza.</span><span class="sxs-lookup"><span data-stu-id="af64b-1157">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="af64b-1158">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1158">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-1159">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1159">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1160">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1160">Info Field 4: Not used.</span></span>

### <a name="timer-change"></a><span data-ttu-id="af64b-1161">Zmiana czasomierza</span><span class="sxs-lookup"><span data-stu-id="af64b-1161">Timer Change</span></span> 

#### <a name="tx_timer_change"></a><span data-ttu-id="af64b-1162">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="af64b-1162">tx_timer_change</span></span>

<span data-ttu-id="af64b-1163">**Ikona** ![ Ikona zmiany czasomierza](./media/user-guide/tx-events/image82.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1163">**Icon** ![Timer change icon](./media/user-guide/tx-events/image82.png)</span></span>

<span data-ttu-id="af64b-1164">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1164">**Description**</span></span>

<span data-ttu-id="af64b-1165">To zdarzenie reprezentuje zmianę określonego czasomierza za pośrednictwem tx_timer_change.</span><span class="sxs-lookup"><span data-stu-id="af64b-1165">This event represents changing the specified timer via tx_timer_change.</span></span>

<span data-ttu-id="af64b-1166">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1166">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1167">Pole informacji 1: wskaźnik do czasomierza.</span><span class="sxs-lookup"><span data-stu-id="af64b-1167">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="af64b-1168">Pole informacji 2: początkowe cykle wygasania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1168">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="af64b-1169">Pole informacji 3: ponowne planowanie taktów wygasania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1169">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="af64b-1170">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1170">Info Field 4: Not used.</span></span>

### <a name="timer-create"></a><span data-ttu-id="af64b-1171">Tworzenie czasomierza</span><span class="sxs-lookup"><span data-stu-id="af64b-1171">Timer Create</span></span> 

#### <a name="tx_timer_create"></a><span data-ttu-id="af64b-1172">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="af64b-1172">tx_timer_create</span></span>

<span data-ttu-id="af64b-1173">**Ikona** ![ Ikona tworzenia czasomierza](./media/user-guide/tx-events/image83.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1173">**Icon** ![Timer create icon](./media/user-guide/tx-events/image83.png)</span></span>

<span data-ttu-id="af64b-1174">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1174">**Description**</span></span>

<span data-ttu-id="af64b-1175">To zdarzenie reprezentuje tworzenie czasomierza za pośrednictwem tx_timer_create.</span><span class="sxs-lookup"><span data-stu-id="af64b-1175">This event represents creating a timer via tx_timer_create.</span></span>

<span data-ttu-id="af64b-1176">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1176">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1177">Pole informacji 1: wskaźnik do bloku sterowania czasomierzem.</span><span class="sxs-lookup"><span data-stu-id="af64b-1177">Info Field 1: Pointer to timer control block.</span></span>
- <span data-ttu-id="af64b-1178">Pole informacji 2: początkowe cykle wygasania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1178">Info Field 2: Initial expiration ticks.</span></span>
- <span data-ttu-id="af64b-1179">Pole informacji 3: ponowne planowanie taktów wygasania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1179">Info Field 3: Reschedule expiration ticks.</span></span>
- <span data-ttu-id="af64b-1180">Pole informacji 4: Automatyczne włączanie wartości — albo TX_AUTO_ACTIVATE (1), albo TX_NO_ACTIVATE (0).</span><span class="sxs-lookup"><span data-stu-id="af64b-1180">Info Field 4: Automatic enable value—either TX_AUTO_ACTIVATE (1) or TX_NO_ACTIVATE (0).</span></span>

### <a name="timer-deactivate"></a><span data-ttu-id="af64b-1181">Dezaktywacja czasomierza</span><span class="sxs-lookup"><span data-stu-id="af64b-1181">Timer Deactivate</span></span> 

#### <a name="tx_timer_deactivate"></a><span data-ttu-id="af64b-1182">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="af64b-1182">tx_timer_deactivate</span></span>

<span data-ttu-id="af64b-1183">**Ikona** ![ Ikona dezaktywacji czasomierza](./media/user-guide/tx-events/image84.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1183">**Icon** ![Timer deactivate icon](./media/user-guide/tx-events/image84.png)</span></span>

<span data-ttu-id="af64b-1184">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1184">**Description**</span></span>

<span data-ttu-id="af64b-1185">To zdarzenie reprezentuje dezaktywowanie czasomierza za pośrednictwem tx_timer_deactivate.</span><span class="sxs-lookup"><span data-stu-id="af64b-1185">This event represents deactivating a timer via tx_timer_deactivate.</span></span>

<span data-ttu-id="af64b-1186">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1186">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1187">Pole informacji 1: wskaźnik do czasomierza.</span><span class="sxs-lookup"><span data-stu-id="af64b-1187">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="af64b-1188">Pole informacji 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1188">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-1189">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1189">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1190">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1190">Info Field 4: Not used.</span></span>

### <a name="timer-delete"></a><span data-ttu-id="af64b-1191">Usuwanie czasomierza</span><span class="sxs-lookup"><span data-stu-id="af64b-1191">Timer Delete</span></span> 

#### <a name="tx_timer_delete"></a><span data-ttu-id="af64b-1192">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="af64b-1192">tx_timer_delete</span></span>

<span data-ttu-id="af64b-1193">**Ikona** ![ Ikona usuwania czasomierza](./media/user-guide/tx-events/image85.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1193">**Icon** ![Timer delete icon](./media/user-guide/tx-events/image85.png)</span></span>

<span data-ttu-id="af64b-1194">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1194">**Description**</span></span>

<span data-ttu-id="af64b-1195">To zdarzenie reprezentuje usunięcie czasomierza za pośrednictwem tx_timer_delete.</span><span class="sxs-lookup"><span data-stu-id="af64b-1195">This event represents deleting a timer via tx_timer_delete.</span></span>

<span data-ttu-id="af64b-1196">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1196">**Information Fields**</span></span> 

- <span data-ttu-id="af64b-1197">Pole informacji 1: wskaźnik do czasomierza.</span><span class="sxs-lookup"><span data-stu-id="af64b-1197">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="af64b-1198">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1198">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-1199">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1199">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1200">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1200">Info Field 4: Not used.</span></span>

### <a name="timer-information-get"></a><span data-ttu-id="af64b-1201">Pobieranie informacji o czasomierzu</span><span class="sxs-lookup"><span data-stu-id="af64b-1201">Timer Information Get</span></span> 

#### <a name="tx_timer_info_get"></a><span data-ttu-id="af64b-1202">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-1202">tx_timer_info_get</span></span>

<span data-ttu-id="af64b-1203">**Ikona** ![ Ikona uzyskiwania informacji o czasomierzu](./media/user-guide/tx-events/image86.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1203">**Icon** ![Timer get information icon](./media/user-guide/tx-events/image86.png)</span></span>

<span data-ttu-id="af64b-1204">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1204">**Description**</span></span>

<span data-ttu-id="af64b-1205">To zdarzenie reprezentuje informacje o czasomierzu za pośrednictwem tx_timer_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-1205">This event represents getting timer information via tx_timer_info_get.</span></span>

<span data-ttu-id="af64b-1206">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1206">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1207">Pole informacji 1: wskaźnik do czasomierza.</span><span class="sxs-lookup"><span data-stu-id="af64b-1207">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="af64b-1208">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1208">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-1209">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1209">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1210">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1210">Info Field 4: Not used.</span></span>

### <a name="timer-performance-information-get"></a><span data-ttu-id="af64b-1211">Pobieranie informacji o wydajności czasomierza</span><span class="sxs-lookup"><span data-stu-id="af64b-1211">Timer Performance Information Get</span></span> 

#### <a name="tx_timer_performance_info_get"></a><span data-ttu-id="af64b-1212">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-1212">tx_timer_performance_info_get</span></span>

<span data-ttu-id="af64b-1213">**Ikona** ![ Ikona pobierania informacji o wydajności czasomierza](./media/user-guide/tx-events/image87.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1213">**Icon** ![Timer performance information get icon](./media/user-guide/tx-events/image87.png)</span></span>

<span data-ttu-id="af64b-1214">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1214">**Description**</span></span> 

<span data-ttu-id="af64b-1215">To zdarzenie reprezentuje informacje o wydajności czasomierza za pośrednictwem tx_timer_performance_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-1215">This event represents getting timer performance information via tx_timer_performance_info_get.</span></span>

<span data-ttu-id="af64b-1216">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1216">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1217">Pole informacji 1: wskaźnik do czasomierza.</span><span class="sxs-lookup"><span data-stu-id="af64b-1217">Info Field 1: Pointer to timer.</span></span>
- <span data-ttu-id="af64b-1218">Pole informacji 2: Wskaźnik stosu w czasie wywołania.</span><span class="sxs-lookup"><span data-stu-id="af64b-1218">Info Field 2: Stack pointer at time of call.</span></span>
- <span data-ttu-id="af64b-1219">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1219">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1220">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1220">Info Field 4: Not used.</span></span>

### <a name="timer-system-performance-info-get"></a><span data-ttu-id="af64b-1221">Czasomierz informacji o wydajności systemu</span><span class="sxs-lookup"><span data-stu-id="af64b-1221">Timer System Performance Info Get</span></span> 

#### <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="af64b-1222">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="af64b-1222">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="af64b-1223">**Ikona** ![ Ikona uzyskiwania informacji o wydajności systemu czasomierza](./media/user-guide/tx-events/image88.png)</span><span class="sxs-lookup"><span data-stu-id="af64b-1223">**Icon** ![Timer system performance info get icon](./media/user-guide/tx-events/image88.png)</span></span>


<span data-ttu-id="af64b-1224">**Opis**</span><span class="sxs-lookup"><span data-stu-id="af64b-1224">**Description**</span></span> 

<span data-ttu-id="af64b-1225">To zdarzenie reprezentuje pobieranie wszystkich informacji o wydajności czasomierza za pośrednictwem tx_timer_performance_system_info_get.</span><span class="sxs-lookup"><span data-stu-id="af64b-1225">This event represents getting all timer performance information via tx_timer_performance_system_info_get.</span></span>

<span data-ttu-id="af64b-1226">**Pola informacji**</span><span class="sxs-lookup"><span data-stu-id="af64b-1226">**Information Fields**</span></span>

- <span data-ttu-id="af64b-1227">Pole informacji 1: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1227">Info Field 1: Not used.</span></span>
- <span data-ttu-id="af64b-1228">Pole informacji 2: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1228">Info Field 2: Not used.</span></span>
- <span data-ttu-id="af64b-1229">Pole informacji 3: nie zostało użyte.</span><span class="sxs-lookup"><span data-stu-id="af64b-1229">Info Field 3: Not used.</span></span>
- <span data-ttu-id="af64b-1230">Pole informacji 4: nieużywane.</span><span class="sxs-lookup"><span data-stu-id="af64b-1230">Info Field 4: Not used.</span></span>