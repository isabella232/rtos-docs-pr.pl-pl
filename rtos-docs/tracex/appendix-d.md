---
title: Dodatek D — zrzucanie i bufor śledzenia
description: Zatopienie buforu śledzenia utworzonego przez usługę Azure RTO ThreadX do pliku na komputerze hosta odbywa się za pośrednictwem poleceń i/lub narzędzi dostarczonych przez określone narzędzie deweloperskie.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 30f6b5e329feeb2dca37dda391fd738aba587c9a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823628"
---
# <a name="appendix-d---dumping-and-trace-buffer"></a><span data-ttu-id="667ee-103">Dodatek D — zrzucanie i bufor śledzenia</span><span class="sxs-lookup"><span data-stu-id="667ee-103">Appendix D - Dumping and trace buffer</span></span>

<span data-ttu-id="667ee-104">Zatopienie buforu śledzenia utworzonego przez usługę Azure RTO ThreadX do pliku na komputerze hosta odbywa się za pośrednictwem poleceń i/lub narzędzi dostarczonych przez określone narzędzie deweloperskie.</span><span class="sxs-lookup"><span data-stu-id="667ee-104">Dumping the trace buffer created by Azure RTOS ThreadX to a file on the host computer is done via commands and/or utilities provided by the specific development tool being used.</span></span> <span data-ttu-id="667ee-105">Ten dodatek zawiera przykłady zatopienia buforu śledzenia do pliku hosta w niektórych najpopularniejszych narzędziach programistycznych używanych z programem ThreadX.</span><span class="sxs-lookup"><span data-stu-id="667ee-105">This appendix contains examples of dumping a trace buffer to a host file in some of the more popular development tools used with ThreadX.</span></span> 

## <a name="benchx-tools"></a><span data-ttu-id="667ee-106">Narzędzia BenchX</span><span class="sxs-lookup"><span data-stu-id="667ee-106">BenchX Tools</span></span>

<span data-ttu-id="667ee-107">Bufor śledzenia może być w łatwy sposób zrzucany do pliku hosta za pomocą narzędzi BenchX, wybierając przycisk ***przechowuj pamięć do pliku** _ w _widokach pamięci_* \*, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="667ee-107">The trace buffer can be dumped to a host file easily with the BenchX tools by selecting the ***Store Memory To File** _ button within the _*_Memory View_\*\*, as shown below:</span></span>

![Zrzut ekranu przedstawiający widok pamięci w narzędziach BenchX.](./media/user-guide/image642.jpg)

<span data-ttu-id="667ee-109">W tym momencie Określ adres bufora śledzenia, rozmiar, nazwę pliku docelowego (w tym ścieżkę), a następnie wybierz przycisk ***Zapisz*** , jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="667ee-109">At this point, specify the trace buffer address, size, destination file name (including path), and select the ***Save*** button as shown below.</span></span> <span data-ttu-id="667ee-110">Spowoduje to utworzenie binarnego pliku śledzenia do wyświetlania w TraceX.</span><span class="sxs-lookup"><span data-stu-id="667ee-110">This will create the binary trace file for viewing within TraceX.</span></span>

![Zrzut ekranu przedstawiający okno dialogowe BenchX narzędzi do zapisywania.](./media/user-guide/image643.jpg)

## <a name="realview-tools"></a><span data-ttu-id="667ee-112">Narzędzia RealView</span><span class="sxs-lookup"><span data-stu-id="667ee-112">RealView Tools</span></span>

<span data-ttu-id="667ee-113">Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi ARM RealView, wprowadzając następujące polecenie w wierszu polecenia w RealView:</span><span class="sxs-lookup"><span data-stu-id="667ee-113">The trace buffer can be dumped to a host file easily with the ARM RealView tools by entering the following command at the command-line prompt in RealView:</span></span>

```c 
> WRITEFILE,raw trace_file.trx=0x6860..0xE560
```

<span data-ttu-id="667ee-114">Po zakończeniu plik ***trace_file. TRX*** będzie zawierać bufor śledzenia, który znajduje się na początku adresu 0x6860 i trafia do 0xE560.</span><span class="sxs-lookup"><span data-stu-id="667ee-114">Upon completion, the file ***trace_file.trx*** will contain the trace buffer that is located starting at the address 0x6860 and goes up to address 0xE560.</span></span> <span data-ttu-id="667ee-115">Ten plik jest gotowy do wyświetlania przez TraceX.</span><span class="sxs-lookup"><span data-stu-id="667ee-115">This file is ready for viewing by TraceX.</span></span>

## <a name="iar-tools"></a><span data-ttu-id="667ee-116">Narzędzia IAR</span><span class="sxs-lookup"><span data-stu-id="667ee-116">IAR Tools</span></span>

<span data-ttu-id="667ee-117">Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi IAR, klikając prawym przyciskiem myszy w widoku pamięć i wybierając pozycję ***Zapisz pamięć...***</span><span class="sxs-lookup"><span data-stu-id="667ee-117">The trace buffer can be dumped to a host file easily with the IAR tools by simply right-clicking in the memory view and selecting the ***Memory Save…***</span></span> <span data-ttu-id="667ee-118">, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="667ee-118">option, as shown below.</span></span>

![Zrzut ekranu opcji zapisywania pamięci w narzędziach IAR.](./media/user-guide/image0_311.jpg)

<span data-ttu-id="667ee-120">Spowoduje to wyświetlenie okna dialogowego \***Zapisz pamięć** _.</span><span class="sxs-lookup"><span data-stu-id="667ee-120">This results in the \***Memory Save** _ dialog to be displayed.</span></span> <span data-ttu-id="667ee-121">Wprowadź adres początkowy i końcowy oraz nazwę pliku śledzenia, a następnie wybierz przycisk _*_Zapisz_*_ .</span><span class="sxs-lookup"><span data-stu-id="667ee-121">Enter the starting and ending address and the trace file name, then select the _*_Save_*_ button.</span></span> <span data-ttu-id="667ee-122">W przykładzie pokazanym poniżej narzędzia IAR zapisują określony bufor śledzenia w rekordach SZESNASTKOWych Intel w pliku _ *_trace_file. hex_* \*.</span><span class="sxs-lookup"><span data-stu-id="667ee-122">In the example shown below, the IAR tools save the specified trace buffer into Intel HEX records in the file _\*_trace_file.hex_\*\*.</span></span>

![Zrzut ekranu przedstawiający okno dialogowe zapisywania pamięci narzędzi IAR.](./media/user-guide/image648.jpg)

<span data-ttu-id="667ee-124">W tym momencie mamy bufor śledzenia zapisany w pliku ***trace_file. hex*** na hoście i jest gotowy do wyświetlania z TraceX.</span><span class="sxs-lookup"><span data-stu-id="667ee-124">At this point, we have the trace buffer saved in the ***trace_file.hex*** file on the host and is ready for viewing with TraceX.</span></span>

## <a name="codewarrior-tools"></a><span data-ttu-id="667ee-125">Narzędzia CodeWarrior</span><span class="sxs-lookup"><span data-stu-id="667ee-125">CodeWarrior Tools</span></span>

<span data-ttu-id="667ee-126">Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi CodeWarrior, wprowadzając polecenie \***Save** _ w oknie poleceń.</span><span class="sxs-lookup"><span data-stu-id="667ee-126">The trace buffer can be dumped to a host file easily with the CodeWarrior tools by entering the \***save** _ command in the Command Window.</span></span> <span data-ttu-id="667ee-127">Poniższy przykład: _ *_Save_*\* polecenie zakłada, że bufor śledzenia zaczyna się od 0x102200 i kończą się o 0x109F00:</span><span class="sxs-lookup"><span data-stu-id="667ee-127">The following example _ *_save_*\* command assumes the trace buffer starts at 0x102200 and ends at 0x109F00:</span></span>

```c
> save –b p:0x102200..0x109F00 trace_file.trx -a 32bit
```

<span data-ttu-id="667ee-128">Powoduje to, że bufor śledzenia jest zapisywany w pliku ***trace_file. TRX*** na hoście.</span><span class="sxs-lookup"><span data-stu-id="667ee-128">This results in the trace buffer being saved in the file ***trace_file.trx*** on the host.</span></span>

## <a name="mplab-tools"></a><span data-ttu-id="667ee-129">Narzędzia MPLAB</span><span class="sxs-lookup"><span data-stu-id="667ee-129">MPLAB Tools</span></span>

<span data-ttu-id="667ee-130">MPLAB może utworzyć plik śledzenia zgodny z TraceX za pomocą narzędzia do eksportowania tabeli, co umożliwia eksportowanie dowolnego zakresu pamięci do pliku hosta.</span><span class="sxs-lookup"><span data-stu-id="667ee-130">MPLAB can create a TraceX-compatible trace file through its Export Table utility, which allows the export of any range of memory to a host file.</span></span> <span data-ttu-id="667ee-131">Aby użyć tego narzędzia do tworzenia pliku śledzenia dla TraceX, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="667ee-131">To use this utility to create a trace file for TraceX, proceed as follows:</span></span>

<span data-ttu-id="667ee-132">**Krok 1** Otwórz okno pamięci, wybierając polecenie Wyświetl > pamięć.</span><span class="sxs-lookup"><span data-stu-id="667ee-132">**Step 1** Open a memory window by selecting View -> Memory.</span></span>

![Zrzut ekranu przedstawiający pamięć wybraną w menu Widok.](./media/user-guide/image0_316.jpg)

<span data-ttu-id="667ee-134">**Krok 2** Kliknij prawym przyciskiem myszy w **widoku pamięci** , aby wyświetlić listę opcji.</span><span class="sxs-lookup"><span data-stu-id="667ee-134">**Step 2** Right-click within the **Memory View** to display a list of options.</span></span> <span data-ttu-id="667ee-135">Określ **Format wyświetlania — 1 bajt** , aby wybrać wyświetlanie bajtów.</span><span class="sxs-lookup"><span data-stu-id="667ee-135">Specify **Display Format -1 Byte** to select byte display..</span></span>

![Zrzut ekranu przedstawiający widok pamięci z wybraną opcją format wyświetlania.](./media/user-guide/image650.png)

![Zrzut ekranu przedstawiający okno dialogowe Przejdź do.](./media/user-guide/image651.jpg)

<span data-ttu-id="667ee-138">**Krok 3** Kliknij ponownie prawym przyciskiem myszy w oknie **Widok pamięci** i wybierz pozycję **Przejdź do**, co spowoduje otwarcie okna dialogowego, w którym można określić adres buforu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="667ee-138">**Step 3** Right-click again within the **Memory View** Window and select **Go To**, which opens a dialog box that enables you to specify the address of the event buffer.</span></span> <span data-ttu-id="667ee-139">Ten przykład pokazuje **_event_buffer_** wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="667ee-139">This example shows **_event_buffer_** being displayed.</span></span>

![Zrzut ekranu przedstawiający widok pamięci z wybraną opcją przejdź do.](./media/user-guide/image0_312.jpg)

![Zrzut ekranu przedstawiający przykład pokazujący wyświetlaną event_buffer.](./media/user-guide/image653.png)

<span data-ttu-id="667ee-142">**Krok 4** Podświetla zawartość pierwszej lokalizacji buforu śledzenia, która jest zawsze ciągiem BTXT....</span><span class="sxs-lookup"><span data-stu-id="667ee-142">**Step 4** This highlights the contents of the first location of the trace buffer, which is always the string BTXT….</span></span>

![Zrzut ekranu przedstawiający pierwszą lokalizację buforu śledzenia.](./media/user-guide/image0_313.jpg)

<span data-ttu-id="667ee-144">**Krok 5** Teraz ponownie kliknij prawym przyciskiem myszy, aby wyświetlić menu Opcje, a następnie wybierz pozycję **Eksportuj tabelę**.</span><span class="sxs-lookup"><span data-stu-id="667ee-144">**Step 5** Now, right-click again to bring up the options menu, and select **Export Table**.</span></span>

![Zrzut ekranu przedstawiający widok pamięci z wybraną opcją Eksportuj tabelę.](./media/user-guide/image0_314.jpg)

<span data-ttu-id="667ee-146">**Krok 6** Spowoduje to wyświetlenie okna dialogowego **Eksportowanie tabeli** , jak pokazano.</span><span class="sxs-lookup"><span data-stu-id="667ee-146">**Step 6** This brings up the **Export Table** dialog, as shown.</span></span> <span data-ttu-id="667ee-147">Określ zakres adresów do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="667ee-147">Specify the range of addresses to export.</span></span> <span data-ttu-id="667ee-148">W przypadku bufora śledzenia 8K, podobnie jak w tym przykładzie, określ zakres 0xA00006AC do 0xA00026AC, a następnie wprowadź nazwę pliku hosta, który ma zostać utworzony (demo_threadx. TRX w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="667ee-148">For an 8K trace buffer, as is the case in this example, specify the range 0xA00006AC to 0xA00026AC, and enter a name for the host file to be created (demo_threadx.trx in this example).</span></span>

<span data-ttu-id="667ee-149">! [[Zrzut ekranu przedstawiający okno dialogowe Eksport jako.](./media/user-guide/image656.jpg)</span><span class="sxs-lookup"><span data-stu-id="667ee-149">![[Screenshot of the Export As dialog.](./media/user-guide/image656.jpg)</span></span>

<span data-ttu-id="667ee-150">**Krok 7** Na hoście zostanie utworzony plik o nazwie **demo_threadx. TRX** , a ten plik może być otwarty przez TraceX.</span><span class="sxs-lookup"><span data-stu-id="667ee-150">**Step 7** A file named **demo_threadx.trx** will be created on the host, and this file can be opened by TraceX.</span></span>

## <a name="ghs-tools"></a><span data-ttu-id="667ee-151">Narzędzia GHS</span><span class="sxs-lookup"><span data-stu-id="667ee-151">GHS Tools</span></span>

<span data-ttu-id="667ee-152">Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi GHS, wprowadzając następujące polecenie w wierszu polecenia w oknie polecenia debugowania:</span><span class="sxs-lookup"><span data-stu-id="667ee-152">The trace buffer can be dumped to a host file easily with the GHS tools by entering the following command at the command-line prompt in the debug command window:</span></span>

```c
memdump raw c:releasethreadxdemo_threadx.trx event_buffer 32768
```

<span data-ttu-id="667ee-153">Po zakończeniu plik **demo_threadx. TRX** będzie zawierać bufor śledzenia, który znajduje się w event_buffer o rozmiarze 32 768 bajtów i będzie gotowy do wyświetlania przez TraceX.</span><span class="sxs-lookup"><span data-stu-id="667ee-153">Upon completion, the file **demo_threadx.trx** will contain the trace buffer that is located in the event_buffer with a size of 32,768 bytes and is ready for viewing by TraceX.</span></span>

## <a name="renesas-hew"></a><span data-ttu-id="667ee-154">Renesas HEW</span><span class="sxs-lookup"><span data-stu-id="667ee-154">Renesas HEW</span></span>

<span data-ttu-id="667ee-155">Bufor śledzenia można łatwo zrzucić do pliku hosta za pomocą narzędzi Renasas HEW, wykonując następujące trzy kroki (i podkroki) poniżej:</span><span class="sxs-lookup"><span data-stu-id="667ee-155">The trace buffer can be dumped to a host file easily with the Renasas HEW tools by following the three steps (and substeps) below:</span></span>

<span data-ttu-id="667ee-156">**Krok 1** Otwórz okno pamięci.</span><span class="sxs-lookup"><span data-stu-id="667ee-156">**Step 1** Open Memory Window.</span></span>

<span data-ttu-id="667ee-157">! [[Zrzut ekranu przedstawiający okno pamięci.](./media/user-guide/image657.jpg)</span><span class="sxs-lookup"><span data-stu-id="667ee-157">![[Screenshot of the Memory Window.](./media/user-guide/image657.jpg)</span></span>

<span data-ttu-id="667ee-158">**Krok 2** Umieść kursor w oknie pamięci i kliknij prawym przyciskiem myszy.</span><span class="sxs-lookup"><span data-stu-id="667ee-158">**Step 2** Place cursor within memory window and right click.</span></span>

![Zrzut ekranu okna pamięci z wybraną opcją Zapisz.](./media/user-guide/image0_315.jpg)

<span data-ttu-id="667ee-160">**Krok 3** Wybierz pozycję Zapisz, a następnie w oknie Zapisz pamięć jako wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="667ee-160">**Step 3** Select Save, then in the Save Memory As window do the following:</span></span>

- <span data-ttu-id="667ee-161">Wybierz format pliku: dane binarne.</span><span class="sxs-lookup"><span data-stu-id="667ee-161">Select File format: Binary.</span></span>
- <span data-ttu-id="667ee-162">Określ nazwę pliku: zgodnie z potrzebami</span><span class="sxs-lookup"><span data-stu-id="667ee-162">Specify Filename: As Desired</span></span>
- <span data-ttu-id="667ee-163">Określ adres początkowy: trace_buffer</span><span class="sxs-lookup"><span data-stu-id="667ee-163">Specify Start address: trace_buffer</span></span>
- <span data-ttu-id="667ee-164">Określ adres końcowy: (trace_buffer + rozmiar)</span><span class="sxs-lookup"><span data-stu-id="667ee-164">Specify End address: (trace_buffer+size)</span></span>
- <span data-ttu-id="667ee-165">Określ rozmiar dostępu: 1</span><span class="sxs-lookup"><span data-stu-id="667ee-165">Specify Access size: 1</span></span>
- <span data-ttu-id="667ee-166">Klikanie pozycji Zapisz.</span><span class="sxs-lookup"><span data-stu-id="667ee-166">Click Save</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Zapisywanie pamięci jako.](./media/user-guide/image659.jpg)