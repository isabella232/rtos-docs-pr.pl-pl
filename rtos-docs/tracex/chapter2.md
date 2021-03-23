---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO TraceX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem narzędzia do analizy systemu Azure RTO TraceX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 05d7fe3df38c7e8a3480c8ea0d4922a109de9ede
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823478"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-tracex"></a><span data-ttu-id="b6805-103">Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO TraceX</span><span class="sxs-lookup"><span data-stu-id="b6805-103">Chapter 2 - Installation and use of Azure RTOS TraceX</span></span>

<span data-ttu-id="b6805-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem narzędzia do analizy systemu Azure RTO TraceX.</span><span class="sxs-lookup"><span data-stu-id="b6805-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS TraceX system analysis tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="b6805-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="b6805-105">Product Distribution</span></span>

<span data-ttu-id="b6805-106">Aplikację TraceX można uzyskać ze [sklepu Microsoft App Store](https://microsoft.com/store/apps) , wyszukując TraceX lub przechodząc bezpośrednio do [strony TraceX](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span><span class="sxs-lookup"><span data-stu-id="b6805-106">You can obtain the TraceX app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for TraceX, or by going directly to [the TraceX page](https://www.microsoft.com/p/azure-rtos-tracex/9nf1lfd5xxg3?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="b6805-107">Następnie wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="b6805-107">Then do the following.</span></span>

1. <span data-ttu-id="b6805-108">Na stronie TraceX w sklepie App Store kliknij przycisk **Pobierz** lub **Zainstaluj** , aby zainstalować TraceX.</span><span class="sxs-lookup"><span data-stu-id="b6805-108">From the TraceX page in the App Store, click the **Get** or **Install** button to install TraceX.</span></span>

1. <span data-ttu-id="b6805-109">W przeglądarce może zostać wyświetlony komunikat z pytaniem, czy chcesz otworzyć Microsoft Store, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="b6805-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="b6805-110">Jeśli tak, wybierz przycisk **Otwórz** .</span><span class="sxs-lookup"><span data-stu-id="b6805-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="b6805-111">![Wybierz pozycję Otwórz, aby zainstalować TraceX.](../guix/media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="b6805-111">![Choose Open to install TraceX.](../guix/media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="b6805-112">Po zakończeniu instalacji wybierz przycisk **Uruchom** .</span><span class="sxs-lookup"><span data-stu-id="b6805-112">When the install finishes, choose the **Launch** button.</span></span> 

## <a name="using-tracex"></a><span data-ttu-id="b6805-113">Korzystanie z TraceX</span><span class="sxs-lookup"><span data-stu-id="b6805-113">Using TraceX</span></span>

<span data-ttu-id="b6805-114">Korzystanie z TraceX jest tak proste, jak otwieranie pliku śledzenia w TraceX!</span><span class="sxs-lookup"><span data-stu-id="b6805-114">Using TraceX is as easy as opening a trace file inside TraceX!</span></span> <span data-ttu-id="b6805-115">Uruchom TraceX za pomocą przycisku \***Start** _.</span><span class="sxs-lookup"><span data-stu-id="b6805-115">Run TraceX via the \***Start** _ button.</span></span> <span data-ttu-id="b6805-116">W tym momencie zostanie zaobserwuj graficzny interfejs użytkownika (GUI) TraceX.</span><span class="sxs-lookup"><span data-stu-id="b6805-116">At this point you will observe the TraceX graphic user interface (GUI).</span></span> <span data-ttu-id="b6805-117">Teraz można przystąpić do korzystania z TraceX, aby wyświetlić graficznie istniejący docelowy bufor śledzenia.</span><span class="sxs-lookup"><span data-stu-id="b6805-117">You are now ready to use TraceX to graphically view an existing target trace buffer.</span></span> <span data-ttu-id="b6805-118">Można to łatwo zrobić, klikając pozycję _ *_plik-> Otwórz,_* a następnie wprowadzając plik śledzenia binarnego.</span><span class="sxs-lookup"><span data-stu-id="b6805-118">This is easily done by clicking _ *_File -> Open,_*\* then entering the binary trace file.</span></span>

>[!IMPORTANT]
><span data-ttu-id="b6805-119">*Możesz również kliknąć dwukrotnie dowolny plik śledzenia z rozszerzeniem **TRX,** co spowoduje automatyczne uruchomienie TraceX.*</span><span class="sxs-lookup"><span data-stu-id="b6805-119">*You can also double-click on any trace file with an extension of **trx,** which will automatically launch TraceX.*</span></span>

![Zrzut ekranu przedstawiający graficzny interfejs użytkownika TraceX.](./media/user-guide/screen_shot_8.png)

<span data-ttu-id="b6805-121">**RYSUNEK 1**</span><span class="sxs-lookup"><span data-stu-id="b6805-121">**FIGURE 1**</span></span>

>[!IMPORTANT]
><span data-ttu-id="b6805-122">*Zapoznaj się z **rozdziałem 5** , aby uzyskać instrukcje dotyczące sposobu generowania buforów śledzenia w miejscu docelowym przy użyciu ThreadX.*</span><span class="sxs-lookup"><span data-stu-id="b6805-122">*Refer to **Chapter 5** for instructions on how to generate trace buffers on the target using ThreadX.*</span></span>

## <a name="tracex-examples"></a><span data-ttu-id="b6805-123">Przykłady TraceX</span><span class="sxs-lookup"><span data-stu-id="b6805-123">TraceX Examples</span></span>

<span data-ttu-id="b6805-124">Przy pierwszym uruchomieniu aplikacji TraceX lub zaktualizowaniu aplikacji TraceX zostanie wyświetlony monit o zainstalowanie przykładowych plików śledzenia TraceX i pliku custom_events. trxc do katalogu zdefiniowanego przez użytkownika na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="b6805-124">The first time you run the TraceX application, or when the TraceX application is updated, you will be prompted to install the TraceX example trace files and the custom_events.trxc file to a user-defined directory on your local machine.</span></span>

<span data-ttu-id="b6805-125">Po zakończeniu tego kroku instalacji, przykładowe pliki śledzenia z rozszerzeniem **TRX** są dostępne w podkatalogu **TraceFiles** folderu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b6805-125">After this installation step in completed, the example trace files with the extension **trx** are found in the **TraceFiles** subdirectory of your installation folder.</span></span> <span data-ttu-id="b6805-126">Te wstępnie skompilowane przykłady ułatwią uzyskanie komfortu korzystania z TraceX w buforach śledzenia generowanych przez ThreadX z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="b6805-126">These pre-built examples will help you get comfortable with using TraceX on the trace buffers generated by ThreadX running with your application.</span></span>

<span data-ttu-id="b6805-127">Jeden przykład zawsze obecny plik śledzenia to plik \***demo_threadx. TRX** _.</span><span class="sxs-lookup"><span data-stu-id="b6805-127">One example trace file always present is the file \***demo_threadx.trx** _.</span></span> <span data-ttu-id="b6805-128">Ten przykładowy plik śledzenia przedstawia wykonywanie standardowego demona ThreadX, zgodnie z opisem w rozdziale 6 podręcznika użytkownika _ThreadX \*.</span><span class="sxs-lookup"><span data-stu-id="b6805-128">This example trace file shows the execution of the standard ThreadX demo, as described in Chapter 6 of the _ThreadX User Guide\*.</span></span>

![Zrzut ekranu okna dialogowego Otwieranie w programie TraceX.](./media/user-guide/screen_shot_9.png)

<span data-ttu-id="b6805-130">**RYSUNEK 2**</span><span class="sxs-lookup"><span data-stu-id="b6805-130">**FIGURE 2**</span></span>
