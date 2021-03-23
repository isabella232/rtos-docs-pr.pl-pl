---
title: Rozdział 6 — system demonstracyjny dla usługi Azure RTO ThreadX
description: Ten rozdział zawiera opis systemu demonstracyjnego, który jest dostarczany ze wszystkimi pakietami obsługi procesora usługi Azure RTO ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: be85ba77e5c27366f61899c0939be7cad1845bbe
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821355"
---
# <a name="chapter-6---demonstration-system-for-azure-rtos-threadx"></a><span data-ttu-id="b0be7-103">Rozdział 6 — system demonstracyjny dla usługi Azure RTO ThreadX</span><span class="sxs-lookup"><span data-stu-id="b0be7-103">Chapter 6 - Demonstration System for Azure RTOS ThreadX</span></span>

<span data-ttu-id="b0be7-104">Ten rozdział zawiera opis systemu demonstracyjnego, który jest dostarczany ze wszystkimi pakietami obsługi procesora usługi Azure RTO ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b0be7-104">This chapter contains a description of the demonstration system that is delivered with all Azure RTOS ThreadX processor support packages.</span></span>

## <a name="overview"></a><span data-ttu-id="b0be7-105">Omówienie</span><span class="sxs-lookup"><span data-stu-id="b0be7-105">Overview</span></span>

<span data-ttu-id="b0be7-106">Każda dystrybucja produktu ThreadX zawiera system demonstracyjny, który działa na wszystkich obsługiwanych mikroprocesorach.</span><span class="sxs-lookup"><span data-stu-id="b0be7-106">Each ThreadX product distribution contains a demonstration system that runs on all supported microprocessors.</span></span>

<span data-ttu-id="b0be7-107">Ten przykładowy system jest zdefiniowany w pliku dystrybucji ***demo_threadx. c*** i został zaprojektowany, aby zilustrować, w jaki sposób ThreadX jest używany w osadzonym środowisku wielowątkowej.</span><span class="sxs-lookup"><span data-stu-id="b0be7-107">This example system is defined in the distribution file ***demo_threadx.c*** and is designed to illustrate how ThreadX is used in an embedded multithread environment.</span></span> <span data-ttu-id="b0be7-108">Demonstracja składa się z inicjowania, ośmiu wątków, jednej puli bajtów, jednej puli blokowej, jednej kolejki, jednego semafora, jednego obiektu mutex i jednej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0be7-108">The demonstration consists of initialization, eight threads, one byte pool, one block pool, one queue, one semaphore, one mutex, and one event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="b0be7-109">*Z wyjątkiem rozmiaru stosu wątku aplikacja demonstracyjna jest taka sama we wszystkich obsługiwanych procesorach ThreadX.*</span><span class="sxs-lookup"><span data-stu-id="b0be7-109">*Except for the thread's stack size, the demonstration application is identical on all ThreadX supported processors.*</span></span>

<span data-ttu-id="b0be7-110">Pełna lista ***demo_threadx. c***, w tym numery wierszy, do których odwołuje się w pozostałej części tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="b0be7-110">The complete listing of ***demo_threadx.c***, including the line numbers referenced throughout the remainder of this chapter.</span></span>

## <a name="application-define"></a><span data-ttu-id="b0be7-111">Definiowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="b0be7-111">Application Define</span></span>

<span data-ttu-id="b0be7-112">Funkcja ***tx_application_define*** jest wykonywana po zakończeniu podstawowej inicjalizacji ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b0be7-112">The ***tx_application_define*** function executes after the basic ThreadX initialization is complete.</span></span> <span data-ttu-id="b0be7-113">Jest on odpowiedzialny za skonfigurowanie wszystkich początkowych zasobów systemowych, w tym wątków, kolejek, semaforów, muteksów, flag zdarzeń i pul pamięci.</span><span class="sxs-lookup"><span data-stu-id="b0be7-113">It is responsible for setting up all of the initial system resources, including threads, queues, semaphores, mutexes, event flags, and memory pools.</span></span>

<span data-ttu-id="b0be7-114">System demonstracyjny \***tx_application_define** _ (_line liczby 60-164 \*) tworzy obiekty demonstracyjne w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="b0be7-114">The demonstration system's ***tx_application_define** _ (_line numbers 60-164*) creates the demonstration objects in the following order:</span></span>

- <span data-ttu-id="b0be7-115">byte_pool_0</span><span class="sxs-lookup"><span data-stu-id="b0be7-115">byte_pool_0</span></span>
- <span data-ttu-id="b0be7-116">thread_0</span><span class="sxs-lookup"><span data-stu-id="b0be7-116">thread_0</span></span>
- <span data-ttu-id="b0be7-117">thread_1</span><span class="sxs-lookup"><span data-stu-id="b0be7-117">thread_1</span></span>
- <span data-ttu-id="b0be7-118">thread_2</span><span class="sxs-lookup"><span data-stu-id="b0be7-118">thread_2</span></span>
- <span data-ttu-id="b0be7-119">thread_3</span><span class="sxs-lookup"><span data-stu-id="b0be7-119">thread_3</span></span>
- <span data-ttu-id="b0be7-120">thread_4</span><span class="sxs-lookup"><span data-stu-id="b0be7-120">thread_4</span></span>
- <span data-ttu-id="b0be7-121">thread_5</span><span class="sxs-lookup"><span data-stu-id="b0be7-121">thread_5</span></span>
- <span data-ttu-id="b0be7-122">thread_6</span><span class="sxs-lookup"><span data-stu-id="b0be7-122">thread_6</span></span>
- <span data-ttu-id="b0be7-123">thread_7</span><span class="sxs-lookup"><span data-stu-id="b0be7-123">thread_7</span></span>
- <span data-ttu-id="b0be7-124">queue_0</span><span class="sxs-lookup"><span data-stu-id="b0be7-124">queue_0</span></span>
- <span data-ttu-id="b0be7-125">semaphore_0</span><span class="sxs-lookup"><span data-stu-id="b0be7-125">semaphore_0</span></span>
- <span data-ttu-id="b0be7-126">event_flags_0</span><span class="sxs-lookup"><span data-stu-id="b0be7-126">event_flags_0</span></span>
- <span data-ttu-id="b0be7-127">mutex_0</span><span class="sxs-lookup"><span data-stu-id="b0be7-127">mutex_0</span></span>
- <span data-ttu-id="b0be7-128">block_pool_0</span><span class="sxs-lookup"><span data-stu-id="b0be7-128">block_pool_0</span></span>

<span data-ttu-id="b0be7-129">System demonstracyjny nie tworzy żadnych innych dodatkowych obiektów ThreadX.</span><span class="sxs-lookup"><span data-stu-id="b0be7-129">The demonstration system does not create any other additional ThreadX objects.</span></span> <span data-ttu-id="b0be7-130">Jednak rzeczywista aplikacja może tworzyć obiekty systemowe podczas wykonywania wewnątrz wątków.</span><span class="sxs-lookup"><span data-stu-id="b0be7-130">However, an actual application may create system objects during runtime inside of executing threads.</span></span>

### <a name="initial-execution"></a><span data-ttu-id="b0be7-131">Początkowe wykonanie</span><span class="sxs-lookup"><span data-stu-id="b0be7-131">Initial Execution</span></span>

<span data-ttu-id="b0be7-132">Wszystkie wątki są tworzone z opcją **TX_AUTO_START** .</span><span class="sxs-lookup"><span data-stu-id="b0be7-132">All threads are created with the **TX_AUTO_START** option.</span></span> <span data-ttu-id="b0be7-133">Dzięki temu są one początkowo gotowe do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b0be7-133">This makes them initially ready for execution.</span></span> <span data-ttu-id="b0be7-134">Po zakończeniu ***tx_application_define*** sterowanie jest przekazywane do harmonogramu wątków i z każdego wątku.</span><span class="sxs-lookup"><span data-stu-id="b0be7-134">After ***tx_application_define*** completes, control is transferred to the thread scheduler and from there to each individual thread.</span></span>

<span data-ttu-id="b0be7-135">Kolejność wykonywania wątków zależy od ich priorytetu i kolejności, w której zostały utworzone.</span><span class="sxs-lookup"><span data-stu-id="b0be7-135">The order in which the threads execute is determined by their priority and the order that they were created.</span></span> <span data-ttu-id="b0be7-136">W systemie demonstracyjnym ***thread_0*** wykonywane jako pierwsze, ponieważ ma najwyższy priorytet (*został utworzony z priorytetem 1*).</span><span class="sxs-lookup"><span data-stu-id="b0be7-136">In the demonstration system, ***thread_0*** executes first because it has the highest priority (*it was created with a priority of 1*).</span></span> <span data-ttu-id="b0be7-137">Po ***thread_0*** zawieszania ***thread_5*** jest wykonywane, a następnie wykonywanie ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _* _thread_7_\* \*, \***thread_1**_ i finally _ *_thread_2_* \*.</span><span class="sxs-lookup"><span data-stu-id="b0be7-137">After ***thread_0*** suspends, ***thread_5*** is executed, followed by the execution of ***thread_3** _, _*_thread_4_*_, _*_thread_6_*_, _*_thread_7_\*\*, \***thread_1**_, and finally _\*_thread_2_\*\*.</span></span>

> [!NOTE]
> <span data-ttu-id="b0be7-138">*Mimo że **thread_3** i **thread_4** mają ten sam priorytet (utworzone z priorytetem 8), **thread_3** wykonywane jako pierwsze. Dzieje się tak, ponieważ **thread_3** została utworzona i stała się gotowa przed **thread_4**. Wątki o równym priorytecie są wykonywane w sposób "FIFO".*</span><span class="sxs-lookup"><span data-stu-id="b0be7-138">*Even though **thread_3** and **thread_4** have the same priority (both created with a priority of 8), **thread_3** executes first. This is because **thread_3** was created and became ready before **thread_4**. Threads of equal priority execute in a FIFO fashion.*</span></span>

## <a name="thread-0"></a><span data-ttu-id="b0be7-139">Wątek 0</span><span class="sxs-lookup"><span data-stu-id="b0be7-139">Thread 0</span></span>

<span data-ttu-id="b0be7-140">Funkcja ***thread_0_entry*** oznacza punkt wejścia wątku *(wiersze 167-190*).</span><span class="sxs-lookup"><span data-stu-id="b0be7-140">The function ***thread_0_entry*** marks the entry point of the thread *(lines 167-190*).</span></span> <span data-ttu-id="b0be7-141">***Thread_0*** to pierwszy wątek w systemie demonstracyjnym do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b0be7-141">***Thread_0*** is the first thread in the demonstration system to execute.</span></span> <span data-ttu-id="b0be7-142">Przetwarzanie jest proste: zwiększa jego licznik, uśpienia dla 10 cykli czasomierza, ustawia flagę zdarzenia w celu wznowienia ***thread_5***, a następnie powtarza sekwencję.</span><span class="sxs-lookup"><span data-stu-id="b0be7-142">Its processing is simple: it increments its counter, sleeps for 10 timer ticks, sets an event flag to wake up ***thread_5***, then repeats the sequence.</span></span>

<span data-ttu-id="b0be7-143">***Thread_0*** to wątek o najwyższym priorytecie w systemie.</span><span class="sxs-lookup"><span data-stu-id="b0be7-143">***Thread_0*** is the highest priority thread in the system.</span></span> <span data-ttu-id="b0be7-144">Gdy zażądana uśpienie wygaśnie, przejdzie wszystkie inne wykonywane wątki w demonstracji.</span><span class="sxs-lookup"><span data-stu-id="b0be7-144">When its requested sleep expires, it will preempt any other executing thread in the demonstration.</span></span>

## <a name="thread-1"></a><span data-ttu-id="b0be7-145">Wątek 1</span><span class="sxs-lookup"><span data-stu-id="b0be7-145">Thread 1</span></span>

<span data-ttu-id="b0be7-146">Funkcja \***thread_1_entry** _ oznacza punkt wejścia wątku _(wiersze 193-216 *). ***Thread_1*** to drugi wątek w systemie demonstracyjnym do wykonania. Jego przetwarzanie polega na zwiększeniu jego licznika, wysłaniu komunikatu do ***thread_2*** (* przez \* ***queue_0***) i powtórzeniu sekwencji. Należy zauważyć, że \***thread_1**_ zawiesza się za każdym razem, gdy _*_queue_0_*_ zostaje zapełniony (_line 207 \*).</span><span class="sxs-lookup"><span data-stu-id="b0be7-146">The function ***thread_1_entry** _ marks the entry point of the thread _(lines 193-216 *). ***Thread_1*** is the second-to-last thread in the demonstration system to execute. Its processing consists of incrementing its counter, sending a message to ***thread_2*** (* through* ***queue_0***), and repeating the sequence. Notice that \***thread_1**_ suspends whenever _*_queue_0_*_ becomes full (_line 207\*).</span></span>

## <a name="thread-2"></a><span data-ttu-id="b0be7-147">Wątek 2</span><span class="sxs-lookup"><span data-stu-id="b0be7-147">Thread 2</span></span>

<span data-ttu-id="b0be7-148">Funkcja ***thread_2_entry*** oznacza punkt wejścia wątku *(wiersze 219-243*).</span><span class="sxs-lookup"><span data-stu-id="b0be7-148">The function ***thread_2_entry*** marks the entry point of the thread *(lines 219-243*).</span></span> <span data-ttu-id="b0be7-149">***Thread_2*** to ostatni wątek w systemie demonstracyjnym do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b0be7-149">***Thread_2*** is the last thread in the demonstration system to execute.</span></span> <span data-ttu-id="b0be7-150">Jego przetwarzanie polega na zwiększeniu licznika, otrzymaniu komunikatu z ***thread_1*** (za pośrednictwem ***queue_0***) i powtarzaniu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="b0be7-150">Its processing consists of incrementing its counter, getting a message from ***thread_1*** (through ***queue_0***), and repeating the sequence.</span></span> <span data-ttu-id="b0be7-151">Należy zauważyć, że ***thread_2** _ zawiesza się za każdym razem, gdy _*_queue_0_\*_ jest puste (_line 233 \*).</span><span class="sxs-lookup"><span data-stu-id="b0be7-151">Notice that ***thread_2** _ suspends whenever _*_queue_0_*_ becomes empty (_line 233*).</span></span>

<span data-ttu-id="b0be7-152">Chociaż ***thread_1** _ i _ *_thread_2_** mają najniższy priorytet w systemie demonstracyjnym (\* priorytet 16 \*), te *wątki 3 i 4*</span><span class="sxs-lookup"><span data-stu-id="b0be7-152">Although ***thread_1** _ and _ *_thread_2_** share the lowest priority in the demonstration system (\* priority 16\*), they *Threads 3 and 4*</span></span>

<span data-ttu-id="b0be7-153">są również jedyne wątki, które są gotowe do wykonania przez większość czasu.</span><span class="sxs-lookup"><span data-stu-id="b0be7-153">are also the only threads that are ready for execution most of the time.</span></span> <span data-ttu-id="b0be7-154">Są to również jedyne wątki utworzone przy użyciu dzielenia czasu (*wiersze 87 i 93*).</span><span class="sxs-lookup"><span data-stu-id="b0be7-154">They are also the only threads created with time-slicing (*lines 87 and 93*).</span></span> <span data-ttu-id="b0be7-155">Dla każdego wątku można wykonać maksymalnie 4 Takty czasomierza przed wykonaniem innego wątku.</span><span class="sxs-lookup"><span data-stu-id="b0be7-155">Each thread is allowed to execute for a maximum of 4 timer ticks before the other thread is executed.</span></span>

## <a name="threads-3-and-4"></a><span data-ttu-id="b0be7-156">Wątki 3 i 4</span><span class="sxs-lookup"><span data-stu-id="b0be7-156">Threads 3 and 4</span></span>

<span data-ttu-id="b0be7-157">Funkcja ***thread_3_and_4_entry*** oznacza punkt wejścia obu ***thread_3** _ i _ *_thread_4_** (linie 246-280).</span><span class="sxs-lookup"><span data-stu-id="b0be7-157">The function ***thread_3_and_4_entry*** marks the entry point of both ***thread_3** _ and _ *_thread_4_** (lines 246-280).</span></span> <span data-ttu-id="b0be7-158">Oba wątki mają priorytet 8, co sprawia, że te trzecie i czwarte wątki w systemie demonstracyjnym do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b0be7-158">Both threads have a priority of 8, which makes them the third and fourth threads in the demonstration system to execute.</span></span> <span data-ttu-id="b0be7-159">Przetwarzanie dla każdego wątku jest takie samo: zwiększanie jego licznika, uzyskiwanie ***semaphore_0***, uśpionych przez 2 Takty czasomierza, zwalnianie ***semaphore_0*** i Powtarzanie sekwencji.</span><span class="sxs-lookup"><span data-stu-id="b0be7-159">The processing for each thread is the same: incrementing its counter, getting ***semaphore_0***, sleeping for 2 timer ticks, releasing ***semaphore_0***, and repeating the sequence.</span></span> <span data-ttu-id="b0be7-160">Należy zauważyć, że każdy wątek zawiesza się za każdym razem, gdy ***semaphore_0*** jest niedostępny (wiersz 264).</span><span class="sxs-lookup"><span data-stu-id="b0be7-160">Notice that each thread suspends whenever ***semaphore_0*** is unavailable (line 264).</span></span>

<span data-ttu-id="b0be7-161">Ponadto oba wątki używają tej samej funkcji do ich głównego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="b0be7-161">Also both threads use the same function for their main processing.</span></span>
<span data-ttu-id="b0be7-162">Nie ma to żadnych problemów, ponieważ oba mają własny unikatowy stos, a C jest naturalnie.</span><span class="sxs-lookup"><span data-stu-id="b0be7-162">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span> <span data-ttu-id="b0be7-163">Każdy wątek określa, który z nich sprawdza parametr wejściowy wątku (wiersz 258), który jest instalatorem podczas ich tworzenia (wiersze 102 i 109).</span><span class="sxs-lookup"><span data-stu-id="b0be7-163">Each thread determines which one it is by examination of the thread input parameter (line 258), which is setup when they are created (lines 102 and 109).</span></span>

> [!NOTE]
> <span data-ttu-id="b0be7-164">*Należy również uzyskać bieżący punkt wątku podczas wykonywania wątku i porównać go z adresem bloku sterowania, aby określić tożsamość wątku.*</span><span class="sxs-lookup"><span data-stu-id="b0be7-164">*It is also reasonable to obtain the current thread point during thread execution and compare it with the control block's address to determine thread identity.*</span></span>

## <a name="thread-5"></a><span data-ttu-id="b0be7-165">Wątek 5</span><span class="sxs-lookup"><span data-stu-id="b0be7-165">Thread 5</span></span>

<span data-ttu-id="b0be7-166">Funkcja ***thread_5_entry*** oznacza punkt wejścia wątku (wiersze 283-305).</span><span class="sxs-lookup"><span data-stu-id="b0be7-166">The function ***thread_5_entry*** marks the entry point of the thread (lines 283-305).</span></span> <span data-ttu-id="b0be7-167">***Thread_5*** to drugi wątek w systemie demonstracyjnym do wykonania.</span><span class="sxs-lookup"><span data-stu-id="b0be7-167">***Thread_5*** is the second thread in the demonstration system to execute.</span></span> <span data-ttu-id="b0be7-168">Jego przetwarzanie polega na zwiększeniu jego licznika, otrzymaniu flagi zdarzenia z ***thread_0*** (za pośrednictwem ***event_flags_0***) i powtórzeniu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="b0be7-168">Its processing consists of incrementing its counter, getting an event flag from ***thread_0*** (through ***event_flags_0***), and repeating the sequence.</span></span> <span data-ttu-id="b0be7-169">Należy zauważyć, że ***thread_5*** zawiesza się za każdym razem, gdy flaga zdarzenia w ***event_flags_0*** jest niedostępna (wiersz 298).</span><span class="sxs-lookup"><span data-stu-id="b0be7-169">Notice that ***thread_5*** suspends whenever the event flag in ***event_flags_0*** is not available (line 298).</span></span>

## <a name="threads-6-and-7"></a><span data-ttu-id="b0be7-170">Wątki 6 i 7</span><span class="sxs-lookup"><span data-stu-id="b0be7-170">Threads 6 and 7</span></span>

<span data-ttu-id="b0be7-171">Funkcja ***thread_6_and_7_entry*** oznacza punkt wejścia obu ***thread_6** _ i _ *_thread_7_** (linie 307-358).</span><span class="sxs-lookup"><span data-stu-id="b0be7-171">The function ***thread_6_and_7_entry*** marks the entry point of both ***thread_6** _ and _ *_thread_7_** (lines 307-358).</span></span> <span data-ttu-id="b0be7-172">Oba wątki mają priorytet 8, co sprawia, że w systemie demonstracyjnym są wykonywane piąte i szóste wątki.</span><span class="sxs-lookup"><span data-stu-id="b0be7-172">Both threads have a priority of 8, which makes them the fifth and sixth threads in the demonstration system to execute.</span></span> <span data-ttu-id="b0be7-173">Przetwarzanie dla każdego wątku jest takie samo: zwiększanie jego licznika, ***mutex_0*** dwa razy, uśpione przez 2 Takty czasomierza, zwalniać ***mutex_0*** dwa razy i powtarzać sekwencję.</span><span class="sxs-lookup"><span data-stu-id="b0be7-173">The processing for each thread is the same: incrementing its counter, getting ***mutex_0*** twice, sleeping for 2 timer ticks, releasing ***mutex_0*** twice, and repeating the sequence.</span></span> <span data-ttu-id="b0be7-174">Należy zauważyć, że każdy wątek zawiesza się za każdym razem, gdy ***mutex_0*** jest niedostępny (wiersz 325).</span><span class="sxs-lookup"><span data-stu-id="b0be7-174">Notice that each thread suspends whenever ***mutex_0*** is unavailable (line 325).</span></span>

<span data-ttu-id="b0be7-175">Ponadto oba wątki używają tej samej funkcji do ich głównego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="b0be7-175">Also both threads use the same function for their main processing.</span></span> <span data-ttu-id="b0be7-176">Nie ma to żadnych problemów, ponieważ oba mają własny unikatowy stos, a C jest naturalnie.</span><span class="sxs-lookup"><span data-stu-id="b0be7-176">This presents no problems because they both have their own unique stack, and C is naturally reentrant.</span></span>
<span data-ttu-id="b0be7-177">Każdy wątek określa, który z nich sprawdza parametr wejściowy wątku (wiersz 319), który jest instalatorem podczas ich tworzenia (wiersze 126 i 133).</span><span class="sxs-lookup"><span data-stu-id="b0be7-177">Each thread determines which one it is by examination of the thread input parameter (line 319), which is setup when they are created (lines 126 and 133).</span></span>

## <a name="observing-the-demonstration"></a><span data-ttu-id="b0be7-178">Obserwowanie demonstracji</span><span class="sxs-lookup"><span data-stu-id="b0be7-178">Observing the Demonstration</span></span>

<span data-ttu-id="b0be7-179">Każdy z wątków demonstracyjnych zwiększa swój własny unikatowy licznik.</span><span class="sxs-lookup"><span data-stu-id="b0be7-179">Each of the demonstration threads increments its own unique counter.</span></span>
<span data-ttu-id="b0be7-180">Następujące liczniki mogą zostać zbadane w celu sprawdzenia działania demonstracyjnego:</span><span class="sxs-lookup"><span data-stu-id="b0be7-180">The following counters may be examined to check on the demo's operation:</span></span>

- <span data-ttu-id="b0be7-181">thread_0_counter</span><span class="sxs-lookup"><span data-stu-id="b0be7-181">thread_0_counter</span></span>
- <span data-ttu-id="b0be7-182">thread_1_counter</span><span class="sxs-lookup"><span data-stu-id="b0be7-182">thread_1_counter</span></span>
- <span data-ttu-id="b0be7-183">thread_2_counter</span><span class="sxs-lookup"><span data-stu-id="b0be7-183">thread_2_counter</span></span>
- <span data-ttu-id="b0be7-184">thread_3_counter</span><span class="sxs-lookup"><span data-stu-id="b0be7-184">thread_3_counter</span></span>
- <span data-ttu-id="b0be7-185">thread_4_counter</span><span class="sxs-lookup"><span data-stu-id="b0be7-185">thread_4_counter</span></span>
- <span data-ttu-id="b0be7-186">thread_5_counter</span><span class="sxs-lookup"><span data-stu-id="b0be7-186">thread_5_counter</span></span>
- <span data-ttu-id="b0be7-187">thread_6_counter</span><span class="sxs-lookup"><span data-stu-id="b0be7-187">thread_6_counter</span></span>
- <span data-ttu-id="b0be7-188">thread_7_counter</span><span class="sxs-lookup"><span data-stu-id="b0be7-188">thread_7_counter</span></span>

<span data-ttu-id="b0be7-189">Każdy z tych liczników powinien nadal wzrosnąć w miarę wykonywania demonstracji, przy czym wartości ***thread_1_counter** _ i _ *_thread_2_counter_** zwiększają się z największą częstotliwością.</span><span class="sxs-lookup"><span data-stu-id="b0be7-189">Each of these counters should continue to increase as the demonstration executes, with ***thread_1_counter** _ and _ *_thread_2_counter_** increasing at the fastest rate.</span></span>

## <a name="distribution-file-demo_threadxc"></a><span data-ttu-id="b0be7-190">Plik dystrybucji: demo_threadx. c</span><span class="sxs-lookup"><span data-stu-id="b0be7-190">Distribution file: demo_threadx.c</span></span>

<span data-ttu-id="b0be7-191">W tej sekcji jest wyświetlana kompletna lista ***demo_threadx. c***, w tym numery wierszy, do których odwołuje się w tym rozdziale.</span><span class="sxs-lookup"><span data-stu-id="b0be7-191">This section displays the complete listing of ***demo_threadx.c***, including the line numbers referenced throughout this chapter.</span></span>

```c
/* This is a small demo of the high-performance ThreadX kernel. It includes examples of eight
threads of different priorities, using a message queue, semaphore, mutex, event flags group,
byte pool, and block pool. */

#include "tx_api.h"

#define DEMO_STACK_SIZE 1024
#define DEMO_BYTE_POOL_SIZE 9120
#define DEMO_BLOCK_POOL_SIZE 100
#define DEMO_QUEUE_SIZE 100

/* Define the ThreadX object control blocks... */

TX_THREAD thread_0;
TX_THREAD thread_1;
TX_THREAD thread_2;
TX_THREAD thread_3;
TX_THREAD thread_4;
TX_THREAD thread_5;
TX_THREAD thread_6;
TX_THREAD thread_7;
TX_QUEUE queue_0;
TX_SEMAPHORE semaphore_0;
TX_MUTEX mutex_0;
TX_EVENT_FLAGS_GROUP event_flags_0;
TX_BYTE_POOL byte_pool_0;
TX_BLOCK_POOL block_pool_0;

/* Define the counters used in the demo application... */

ULONG thread_0_counter;
ULONG thread_1_counter;
ULONG thread_1_messages_sent;
ULONG thread_2_counter;
ULONG thread_2_messages_received;
ULONG thread_3_counter;
ULONG thread_4_counter;
ULONG thread_5_counter;
ULONG thread_6_counter;
ULONG thread_7_counter;

/* Define thread prototypes. */

void thread_0_entry(ULONG thread_input);
void thread_1_entry(ULONG thread_input);
void thread_2_entry(ULONG thread_input);
void thread_3_and_4_entry(ULONG thread_input);
void thread_5_entry(ULONG thread_input);
void thread_6_and_7_entry(ULONG thread_input);


/* Define main entry point. */

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
}

/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{

    CHAR *pointer;

    /* Create a byte memory pool from which to allocate the thread stacks. */
    tx_byte_pool_create(&byte_pool_0, "byte pool 0", first_unused_memory,
        DEMO_BYTE_POOL_SIZE);

    /* Put system definition stuff in here, e.g., thread creates and other assorted
        create information. */

    /* Allocate the stack for thread 0. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create the main thread. */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 1. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 1 and 2. These threads pass information through a ThreadX
        message queue. It is also interesting to note that these threads have a time
        slice. */
    tx_thread_create(&thread_1, "thread 1", thread_1_entry, 1,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 2. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);
        tx_thread_create(&thread_2, "thread 2", thread_2_entry, 2,
        pointer, DEMO_STACK_SIZE,
        16, 16, 4, TX_AUTO_START);

    /* Allocate the stack for thread 3. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 3 and 4. These threads compete for a ThreadX counting semaphore.
        An interesting thing here is that both threads share the same instruction area. */
    tx_thread_create(&thread_3, "thread 3", thread_3_and_4_entry, 3,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 4. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_4, "thread 4", thread_3_and_4_entry, 4,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 5. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create thread 5. This thread simply pends on an event flag, which will be set
        by thread_0. */
    tx_thread_create(&thread_5, "thread 5", thread_5_entry, 5,
        pointer, DEMO_STACK_SIZE,
        4, 4, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 6. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    /* Create threads 6 and 7. These threads compete for a ThreadX mutex. */
    tx_thread_create(&thread_6, "thread 6", thread_6_and_7_entry, 6,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the stack for thread 7. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_STACK_SIZE, TX_NO_WAIT);

    tx_thread_create(&thread_7, "thread 7", thread_6_and_7_entry, 7,
        pointer, DEMO_STACK_SIZE,
        8, 8, TX_NO_TIME_SLICE, TX_AUTO_START);

    /* Allocate the message queue. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_QUEUE_SIZE*sizeof(ULONG), TX_NO_WAIT);

    /* Create the message queue shared by threads 1 and 2. */
    tx_queue_create(&queue_0, "queue 0", TX_1_ULONG, pointer, DEMO_QUEUE_SIZE*sizeof(ULONG));

    /* Create the semaphore used by threads 3 and 4. */
    tx_semaphore_create(&semaphore_0, "semaphore 0", 1);

    /* Create the event flags group used by threads 1 and 5. */
    tx_event_flags_create(&event_flags_0, "event flags 0");

    /* Create the mutex used by thread 6 and 7 without priority inheritance. */
    tx_mutex_create(&mutex_0, "mutex 0", TX_NO_INHERIT);

    /* Allocate the memory for a small block pool. */
    tx_byte_allocate(&byte_pool_0, &pointer, DEMO_BLOCK_POOL_SIZE, TX_NO_WAIT);

    /* Create a block memory pool to allocate a message buffer from. */
    tx_block_pool_create(&block_pool_0, "block pool 0", sizeof(ULONG), pointer,
        DEMO_BLOCK_POOL_SIZE);

    /* Allocate a block and release the block memory. */
    tx_block_allocate(&block_pool_0, &pointer, TX_NO_WAIT);

    /* Release the block back to the pool. */
    tx_block_release(pointer);
}

/* Define the test threads. */
void thread_0_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sits in while-forever-sleep loop. */
    while(1)
    {

        /* Increment the thread counter. */
        thread_0_counter++;

        /* Sleep for 10 ticks. */
        tx_thread_sleep(10);

        /* Set event flag 0 to wakeup thread 5. */
        status = tx_event_flags_set(&event_flags_0, 0x1, TX_OR);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_1_entry(ULONG thread_input)
{
    UINT status;


    /* This thread simply sends messages to a queue shared by thread 2. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_1_counter++;

        /* Send message to queue 0. */
        status = tx_queue_send(&queue_0, &thread_1_messages_sent, TX_WAIT_FOREVER);

        /* Check completion status. */
        if (status != TX_SUCCESS)
            break;

        /* Increment the message sent. */
        thread_1_messages_sent++;
    }
}


void thread_2_entry(ULONG thread_input)
{
    ULONG received_message;
    UINT status;

    /* This thread retrieves messages placed on the queue by thread 1. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_2_counter++;

        /* Retrieve a message from the queue. */
        status = tx_queue_receive(&queue_0, &received_message, TX_WAIT_FOREVER);

        /* Check completion status and make sure the message is what we
        expected. */
        if ((status != TX_SUCCESS) || (received_message != thread_2_messages_received))
            break;

        /* Otherwise, all is okay. Increment the received message count. */
        thread_2_messages_received++;
    }
}


void thread_3_and_4_entry(ULONG thread_input)
{
    UINT status;


    /* This function is executed from thread 3 and thread 4. As the loop
    below shows, these function compete for ownership of semaphore_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 3)
            thread_3_counter++;
        else
            thread_4_counter++;

        /* Get the semaphore with suspension. */
        status = tx_semaphore_get(&semaphore_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the semaphore. */
        tx_thread_sleep(2);

        /* Release the semaphore. */
        status = tx_semaphore_put(&semaphore_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}


void thread_5_entry(ULONG thread_input)
{
    UINT status;
    ULONG actual_flags;


    /* This thread simply waits for an event in a forever loop. */
    while(1)
    {
        /* Increment the thread counter. */
        thread_5_counter++;

        /* Wait for event flag 0. */
        status = tx_event_flags_get(&event_flags_0, 0x1, TX_OR_CLEAR,
            &actual_flags, TX_WAIT_FOREVER);

        /* Check status. */
        if ((status != TX_SUCCESS) || (actual_flags != 0x1))
            break;
    }
}

void thread_6_and_7_entry(ULONG thread_input)
{
    UINT status;

    /* This function is executed from thread 6 and thread 7. As the loop
        below shows, these function compete for ownership of mutex_0. */
    while(1)
    {
        /* Increment the thread counter. */
        if (thread_input == 6)
            thread_6_counter++;
        else
            thread_7_counter++;

        /* Get the mutex with suspension. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Get the mutex again with suspension. This shows
            that an owning thread may retrieve the mutex it
            owns multiple times. */
        status = tx_mutex_get(&mutex_0, TX_WAIT_FOREVER);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Sleep for 2 ticks to hold the mutex. */
        tx_thread_sleep(2);

        /* Release the mutex. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;

        /* Release the mutex again. This will actually
            release ownership since it was obtained twice. */
        status = tx_mutex_put(&mutex_0);

        /* Check status. */
        if (status != TX_SUCCESS)
            break;
    }
}
```
