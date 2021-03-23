---
title: Rozdział 4 — Analiza wydajności usługi Azure RTO TraceX
description: W tym rozdziale opisano narzędzie analiza wydajności usługi Azure RTO TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 6cf1b5bd5349efd97c3afc8a9e7f57f477f06f8f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823442"
---
# <a name="chapter-4---azure-rtos-tracex-performance-analysis"></a><span data-ttu-id="4258b-103">Rozdział 4 — Analiza wydajności usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="4258b-103">Chapter 4 - Azure RTOS TraceX performance analysis</span></span>

<span data-ttu-id="4258b-104">W tym rozdziale opisano narzędzie analiza wydajności usługi Azure RTO TraceX:</span><span class="sxs-lookup"><span data-stu-id="4258b-104">This chapter describes the Azure RTOS TraceX performance analysis tool:</span></span>

## <a name="performance-analysis"></a><span data-ttu-id="4258b-105">Analiza wydajności</span><span class="sxs-lookup"><span data-stu-id="4258b-105">Performance Analysis</span></span>

<span data-ttu-id="4258b-106">TraceX zapewnia wbudowaną analizę wydajności plików śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4258b-106">TraceX provides built-in performance analysis of trace files.</span></span> <span data-ttu-id="4258b-107">Informacje takie jak *profil wykonywania*, *popularne usługi*, *użycie stosu wątków* i różne *statystyki wydajności, w* tym statystyki FileX i NetX *,* są łatwo dostępne.</span><span class="sxs-lookup"><span data-stu-id="4258b-107">Information such as the *execution profile*, *popular services*, *thread stack usage*, and various *performance statistics,* including FileX and NetX statistics *,* are readily available.</span></span> <span data-ttu-id="4258b-108">Te informacje są dostępne za pośrednictwem elementu menu ***Widok*** .</span><span class="sxs-lookup"><span data-stu-id="4258b-108">This information is available via the ***View*** menu item.</span></span> 


## <a name="execution-profile"></a><span data-ttu-id="4258b-109">Profil wykonywania</span><span class="sxs-lookup"><span data-stu-id="4258b-109">Execution Profile</span></span>

<span data-ttu-id="4258b-110">Wybranie przycisku ***Generuj profil wykonywania** _ lub _*_profilu wykonywania widoku_\*_ przedstawia profil wykonywania TraceX dla aktualnie załadowanego pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4258b-110">Selecting the ***Generate Execution Profile** _ button or _*_View -Execution Profile_\*_ presents the TraceX execution profile for the currently loaded trace file.</span></span> <span data-ttu-id="4258b-111">Profil wykonywania skojarzony z przykładowym śladem demonstracyjnym ThreadX jest wyświetlany w _ \* rysunek 19 \* \*.</span><span class="sxs-lookup"><span data-stu-id="4258b-111">The execution profile associated with the sample ThreadX demonstration trace is shown in _\*Figure 19\*\*.</span></span>

![Zrzut ekranu przedstawiający profil wykonywania skojarzony z przykładowym śladem demonstracyjnym ThreadX.](./media/user-guide/execution_profile.png)

<span data-ttu-id="4258b-113">**RYSUNEK 19.**</span><span class="sxs-lookup"><span data-stu-id="4258b-113">**FIGURE 19**</span></span>

<span data-ttu-id="4258b-114">Przykład przedstawiony na **rysunku 19** wskazuje, że niemal 45% czasu przetwarzania należy do **_wątku 2_*_, a niemal 51% czasu przetwarzania jest wewnątrz wątku _*_1_** jest to wartość logiczna od momentu, gdy dane śledzenia przedstawiają te wątki wysyłające i otrzymujące komunikaty.</span><span class="sxs-lookup"><span data-stu-id="4258b-114">The example shown in **Figure 19** indicates that nearly 45% of the processing time is inside of **_thread 2_*_ and nearly 51% of the processing time is inside of _*_thread 1_** This is logical since the bulk of the trace shows these threads sending and receiving messages.</span></span> <span data-ttu-id="4258b-115">W tym przykładzie w pozostałym kontekście wykonania znajduje się tylko niewielki czas wykonania.</span><span class="sxs-lookup"><span data-stu-id="4258b-115">The remaining execution contexts have only a small amount of execution time in this example.</span></span>

## <a name="popular-services"></a><span data-ttu-id="4258b-116">Popularne usługi</span><span class="sxs-lookup"><span data-stu-id="4258b-116">Popular Services</span></span>

<span data-ttu-id="4258b-117">Wybranie pozycji \***wyświetl >popularne usługi** _ prezentuje popularne usługi w aktualnie załadowanym pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4258b-117">Selecting \***View ->Popular Services** _ presents the popular services in the currently loaded trace file.</span></span> <span data-ttu-id="4258b-118">Domyślnie te informacje są wyświetlane dla całego systemu.</span><span class="sxs-lookup"><span data-stu-id="4258b-118">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="4258b-119">Jednak dostępne są również popularne usługi dla określonych wątków.</span><span class="sxs-lookup"><span data-stu-id="4258b-119">However, the popular services for specific threads are also available.</span></span> <span data-ttu-id="4258b-120">Popularne usługi w przykładowym śladzie demonstracyjnej ThreadX są wyświetlane w _ \* rysunek 20 \* \*.</span><span class="sxs-lookup"><span data-stu-id="4258b-120">The popular services in the sample ThreadX demonstration trace are shown in _\*Figure 20\*\*.</span></span>

![Zrzut ekranu przedstawiający popularne usługi w przykładowym śladzie demonstracyjnej ThreadX.](./media/user-guide/popular_services.png)

<span data-ttu-id="4258b-122">**RYSUNEK 20**</span><span class="sxs-lookup"><span data-stu-id="4258b-122">**FIGURE 20**</span></span>

<span data-ttu-id="4258b-123">Przykład przedstawiony na **rysunku 20** wskazuje, że **_tx_queue_send_*_ i _*_tx_queue_receive_** są dwiema najpopularniejszymi usługami w tym śledzeniu.</span><span class="sxs-lookup"><span data-stu-id="4258b-123">The example shown in **Figure 20** indicates that **_tx_queue_send_*_ and _*_tx_queue_receive_** are the two most popular services in this trace.</span></span> <span data-ttu-id="4258b-124">Jest to zgodne z zachowaniem standardowej demonstracji ThreadX, z którego przechwycono ten ślad.</span><span class="sxs-lookup"><span data-stu-id="4258b-124">This is consistent with the behavior of the standard ThreadX demonstration from which this trace was captured.</span></span>

<span data-ttu-id="4258b-125">Dla tej analizy można wybrać określone wątki przy użyciu listy rozwijanej wyboru znajdującej się u góry tego okna.</span><span class="sxs-lookup"><span data-stu-id="4258b-125">Specific threads can be selected for this analysis by using the drop down selection list at the top of this window.</span></span> <span data-ttu-id="4258b-126">**Rysunek 21** przedstawia tę analizę **_wątku 3_**.</span><span class="sxs-lookup"><span data-stu-id="4258b-126">**Figure 21** shows this analysis for **_thread 3_**.</span></span>

![Zrzut ekranu przedstawiający analizę TraceX popularnych usług.](./media/user-guide/popular_services_thread3.png)

<span data-ttu-id="4258b-128">**RYSUNEK 21**</span><span class="sxs-lookup"><span data-stu-id="4258b-128">**FIGURE 21**</span></span>

## <a name="thread-stack-usage-analysis-for-thread-3"></a><span data-ttu-id="4258b-129">Użycie stosu wątków</span><span class="sxs-lookup"><span data-stu-id="4258b-129">Thread Stack Usage</span></span> ![Analiza wątku 3.](./media/user-guide/screen_shot_17.png)

<span data-ttu-id="4258b-131">Wybranie przycisku ***Generuj stos wątków** lub przycisk _*_Wyświetl-> użycie stosu wątku_\*_ przedstawia użycie stosu dla każdego wątku w pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4258b-131">Selecting the ***Generate Thread Stack Usage** _ button or _*_View -> Thread Stack Usage_\*_ presents the stack usage for each thread in the trace file.</span></span> <span data-ttu-id="4258b-132">Jest to realizowane przez ThreadX z uwzględnieniem bieżącego wskaźnika stosu wątków w wielu wpisach śledzenia w pliku.</span><span class="sxs-lookup"><span data-stu-id="4258b-132">This is accomplished by ThreadX including the current thread stack pointer in many of the trace entries in the file.</span></span> <span data-ttu-id="4258b-133">Użycie stosu 100% wskazuje, że stos został przepełniony i musi zostać poprawiony w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4258b-133">A stack usage of 100% indicates the stack has overflowed and must be corrected in the application.</span></span> <span data-ttu-id="4258b-134">Jeśli w tym pliku śledzenia nie ma wykonania wątku, użycie stosu dla tego wątku jest wyświetlane w 0%.</span><span class="sxs-lookup"><span data-stu-id="4258b-134">If there is no thread execution within this trace file, the stack usage for that thread is shown at 0%.</span></span> <span data-ttu-id="4258b-135">Użycie stosu wątku w przykładowym śladzie demonstracyjnej ThreadX jest pokazane w _ \* rysunek 22 \* \*.</span><span class="sxs-lookup"><span data-stu-id="4258b-135">The thread stack usage in the sample ThreadX demonstration trace is shown in _\*Figure 22\*\*.</span></span>

![Zrzut ekranu przedstawiający użycie stosu wątku TraceX.](./media/user-guide/thread_stack_usage.png)

<span data-ttu-id="4258b-137">**RYSUNEK 22**</span><span class="sxs-lookup"><span data-stu-id="4258b-137">**FIGURE 22**</span></span>

<span data-ttu-id="4258b-138">Przykład przedstawiony na **rysunku 22** wskazuje, że większość wątków w tym śladzie ma od 9% do 12% użycia stosu.</span><span class="sxs-lookup"><span data-stu-id="4258b-138">The example shown in **Figure 22** indicates that most threads in this trace have between 9% and 12% stack usage.</span></span>

## <a name="performance-statistics"></a><span data-ttu-id="4258b-139">Statystyka wydajności</span><span class="sxs-lookup"><span data-stu-id="4258b-139">Performance Statistics</span></span>

<span data-ttu-id="4258b-140">Wybranie przycisku ***Generuj statystykę wydajności** _ przycisk lub _ *_Widok-> statystyki wydajności_** przedstawia dane statystyczne wydajności aktualnie załadowanego pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4258b-140">Selecting the ***Generate Performance Statistics** _ button or _ *_View -> Performance Statistics_** presents the performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="4258b-141">Domyślnie te informacje są wyświetlane dla całego systemu.</span><span class="sxs-lookup"><span data-stu-id="4258b-141">By default, this information is displayed for the entire system.</span></span> <span data-ttu-id="4258b-142">Jednak statystyki wydajności są również dostępne dla każdego określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="4258b-142">However, the performance statistics are also available for each specific thread.</span></span>

<span data-ttu-id="4258b-143">Statystyka wydajności przykładowego śledzenia demonstracji ThreadX przedstawiono na **rysunku 23**.</span><span class="sxs-lookup"><span data-stu-id="4258b-143">The performance statistics of the sample ThreadX demonstration trace are shown in **Figure 23**.</span></span>

![Zrzut ekranu przedstawiający statystyki wydajności TraceX.](./media/user-guide/performance_statistics.png)

<span data-ttu-id="4258b-145">**RYSUNEK 23**</span><span class="sxs-lookup"><span data-stu-id="4258b-145">**FIGURE 23**</span></span>

<span data-ttu-id="4258b-146">Przykład pokazany na **rysunku 23** wskazuje, że wystąpiły 18 przełączników kontekstu w tym pliku śledzenia, a także pięć zawieszeń wątku, zawieszenia 16 wątków, 19 wznowień wątków i trzech przerwań.</span><span class="sxs-lookup"><span data-stu-id="4258b-146">The example shown in **Figure 23** indicates that there were 18 context switches in this trace file, as well as five thread preemptions, 16 thread suspensions, 19 thread resumptions, and three interrupts.</span></span> <span data-ttu-id="4258b-147">W tym pliku śledzenia nie znaleziono żadnych wersji priorytetu.</span><span class="sxs-lookup"><span data-stu-id="4258b-147">There were no priority inversions found in this trace file.</span></span> <span data-ttu-id="4258b-148">Należy zauważyć, że istnieją dwie kategorie niewersji priorytetu, czyli *deterministyczne* i *niedeterministyczne*.</span><span class="sxs-lookup"><span data-stu-id="4258b-148">Notice there are two categories of priority inversions, namely, *deterministic* and *nondeterministic*.</span></span> <span data-ttu-id="4258b-149">Deterministyczne priorytety są niewersjami priorytetowymi, w których wątek jest blokowany w elemencie mutex należącym do wątku o niższym priorytecie.</span><span class="sxs-lookup"><span data-stu-id="4258b-149">Deterministic priority inversions are priority inversion in which a thread is blocked on a mutex owned by a lower priority thread.</span></span> <span data-ttu-id="4258b-150">Niedeterministyczna wersja priorytetu polega na tym, że inny wątek o niższym priorytecie jest uruchamiany podczas nieużywanej wersji priorytetu.</span><span class="sxs-lookup"><span data-stu-id="4258b-150">An nondeterministic priority inversion is where a different lower priority thread runs during a deterministic priority inversion.</span></span> <span data-ttu-id="4258b-151">Później może to spowodować nieprzewidziane zachowanie chronometrażu w aplikacji i należy uważnie przeanalizować.</span><span class="sxs-lookup"><span data-stu-id="4258b-151">The later can cause unforeseen timing behavior in the application and should be studied carefully.</span></span>

## <a name="filex-statistics"></a><span data-ttu-id="4258b-152">Statystyka FileX</span><span class="sxs-lookup"><span data-stu-id="4258b-152">FileX Statistics</span></span>

<span data-ttu-id="4258b-153">Wybranie opcji \***View-> FileX Statistics** _ przedstawia statystykę wydajności FileX aktualnie załadowanego pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4258b-153">Selecting \***View -> FileX Statistics** _ presents the FileX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="4258b-154">Te informacje są wyświetlane dla całego systemu, na wszystkich otwartych.. obiekty/Media.</span><span class="sxs-lookup"><span data-stu-id="4258b-154">This information is displayed for the entire system, on all opened ../media objects.</span></span> <span data-ttu-id="4258b-155">Statystyka wydajności przykładowego śladu demonstracyjnego FileX jest wyświetlana w _ \* rysunek 24 \* \*.</span><span class="sxs-lookup"><span data-stu-id="4258b-155">The performance statistics of the sample FileX demonstration trace are shown in _\*Figure 24\*\*.</span></span>

![Zrzut ekranu przedstawiający statystyki FileX.](./media/user-guide/filex_statistics.png)

<span data-ttu-id="4258b-157">**RYSUNEK 24**</span><span class="sxs-lookup"><span data-stu-id="4258b-157">**FIGURE 24**</span></span>

<span data-ttu-id="4258b-158">Przykład przedstawiony na **rysunku 27** wskazuje, że wystąpiły 19. /Media otwiera, 19.. /Media zamyka, 19.. /Media opróżnia, 18 odczyty katalogów, 19 zapisów w katalogu i 18 pamięci podręcznej katalogów.</span><span class="sxs-lookup"><span data-stu-id="4258b-158">The example shown in **Figure 27** indicates there were 19 ../media opens, 19 ../media closes, 19 ../media flushes, 18 directory reads, 19 directory writes, and 18 directory cache misses.</span></span> <span data-ttu-id="4258b-159">Dodatkowe informacje można wyświetlić, przewijając w dół okna Statystyka.</span><span class="sxs-lookup"><span data-stu-id="4258b-159">Additonal information can be viewed by scrolling down in the statistics window.</span></span>

## <a name="netx-statistics"></a><span data-ttu-id="4258b-160">Statystyka NetX</span><span class="sxs-lookup"><span data-stu-id="4258b-160">NetX Statistics</span></span>

<span data-ttu-id="4258b-161">Wybór \***View-NetX Statistics** _ przedstawia statystykę wydajności NetX aktualnie załadowanego pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4258b-161">Selecting \***View -NetX Statistics** _ presents the NetX performance statistics of the currently loaded trace file.</span></span> <span data-ttu-id="4258b-162">Te informacje są wyświetlane dla całego systemu.</span><span class="sxs-lookup"><span data-stu-id="4258b-162">This information is displayed for the entire system.</span></span> <span data-ttu-id="4258b-163">Statystyka wydajności przykładowego śladu demonstracyjnego NetX jest wyświetlana w _ \* Rysunek 25 \* \*.</span><span class="sxs-lookup"><span data-stu-id="4258b-163">The performance statistics of the sample NetX demonstration trace are shown in _\*Figure 25\*\*.</span></span>

![Zrzut ekranu przedstawiający statystyki NetX.](./media/user-guide/netx_statistics.png)

<span data-ttu-id="4258b-165">**RYSUNEK 25**</span><span class="sxs-lookup"><span data-stu-id="4258b-165">**FIGURE 25**</span></span>

<span data-ttu-id="4258b-166">Przykład przedstawiony na **rysunku nr 25** wskazuje, że nie było zdarzeń ARP, ping lub UDP, ale wystąpiły 30 pakietów IP, wysłano 1 368 bajtów IP, odebrano 30 pakietów IP i odebrano 1 360 bajtów IP.</span><span class="sxs-lookup"><span data-stu-id="4258b-166">The example shown in **Figure 25** indicates there were no ARP, Ping, or UDP events, but there were 30 IP packets sent, 1,368 IP bytes sent, 30 IP packets received, and 1,360 IP bytes received.</span></span>

## <a name="trace-file-information"></a><span data-ttu-id="4258b-167">Informacje o pliku śledzenia</span><span class="sxs-lookup"><span data-stu-id="4258b-167">Trace File Information</span></span>

<span data-ttu-id="4258b-168">Wybranie opcji \***Wyświetl-> informacje o pliku śledzenia** _ przedstawia pewne podstawowe informacje o otwartym pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4258b-168">Selecting \***View -> Trace File Information** _ presents some basic information about the opened trace file.</span></span> <span data-ttu-id="4258b-169">Te informacje obejmują kolejność bajtów pliku, rozmiar źródła czasu, maksymalną liczbę bajtów dla każdej nazwy obiektu i adres podstawowy wszystkich wskaźników plików śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4258b-169">This information includes the byte order of the file, size of the time source, maximum number of bytes for each object name, and the base address of all trace file pointers.</span></span> <span data-ttu-id="4258b-170">_ *Ilustracja 26*\* przedstawia informacje o pliku śledzenia dla standardowego pliku śledzenia **_demo_threadx. TRX_** .</span><span class="sxs-lookup"><span data-stu-id="4258b-170">_ *Figure 26*\* shows the trace file information for the standard **_demo_threadx.trx_** trace file.</span></span>

![Zrzut ekranu przedstawiający informacje o pliku TraceX.](./media/user-guide/trace_file_info.png)

<span data-ttu-id="4258b-172">**RYSUNEK 26**</span><span class="sxs-lookup"><span data-stu-id="4258b-172">**FIGURE 26**</span></span>

## <a name="raw-trace-dump"></a><span data-ttu-id="4258b-173">Nieprzetworzony zrzut śledzenia</span><span class="sxs-lookup"><span data-stu-id="4258b-173">Raw Trace Dump</span></span>

<span data-ttu-id="4258b-174">Wybranie opcji \***wyświetl > nieprzetworzony zrzut śledzenia** _ przedstawia okno dialogowe z nazwą pliku zawierającego nieprzetworzony zrzut śledzenia.</span><span class="sxs-lookup"><span data-stu-id="4258b-174">Selecting \***View -> Raw Trace Dump** _ presents a dialog to name the file containing the raw trace dump.</span></span> <span data-ttu-id="4258b-175">Po wprowadzeniu nazwy pliku i ścieżki TraceX kompiluje Nieprzetworzony plik śledzenia w formacie tekstowym i uruchomi _*_notepad.exe_*_ , aby go wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="4258b-175">After the file name and path are entered, TraceX builds the raw trace file in text format and launches _*_notepad.exe_*_ to display it.</span></span> <span data-ttu-id="4258b-176">_ *Ilustracja 27*\* przedstawia nieprzetworzony zrzut pliku śledzenia dla standardowego pliku śledzenia **_demo_threadx. TRX_** .</span><span class="sxs-lookup"><span data-stu-id="4258b-176">_ *Figure 27*\* shows the raw trace file dump for the standard **_demo_threadx.trx_** trace file.</span></span>

![Zrzut ekranu przedstawiający nieprzetworzony zrzut śledzenia.](./media/user-guide/raw_trace_dump.png)

<span data-ttu-id="4258b-178">**RYSUNEK 27**</span><span class="sxs-lookup"><span data-stu-id="4258b-178">**FIGURE 27**</span></span>
