---
title: Instalowanie i korzystanie z programu GUIX Studio
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem narzędzia projektowania systemu interfejsu użytkownika GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d7b5f94c26842b408ea1b00aeeb78e111bea3623
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823071"
---
# <a name="chapter-2-installation-and-use-of-guix-studio"></a><span data-ttu-id="f5073-103">Rozdział 2. Instalowanie i korzystanie z programu GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="f5073-103">Chapter 2: Installation and Use of GUIX Studio</span></span>

<span data-ttu-id="f5073-104">Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem narzędzia projektowania systemu interfejsu użytkownika GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="f5073-104">This chapter contains a description of various issues related to installation, setup, and usage of the GUIX Studio UI system design tool.</span></span> 

## <a name="product-distribution"></a><span data-ttu-id="f5073-105">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="f5073-105">Product Distribution</span></span>

<span data-ttu-id="f5073-106">Aplikację GUIX Studio można uzyskać ze [sklepu Microsoft App Store](https://microsoft.com/store/apps) , wyszukując GUIX Studio lub przechodząc bezpośrednio do [strony programu GUIX Studio](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span><span class="sxs-lookup"><span data-stu-id="f5073-106">You can obtain the GUIX Studio app from the [Microsoft App Store](https://microsoft.com/store/apps) by searching for GUIX Studio, or by going directly to [the GUIX Studio page](https://www.microsoft.com/p/azure-rtos-guix-studio/9pbm1k1r7q0f?activetab=pivot:overviewtab).</span></span> <span data-ttu-id="f5073-107">Następnie wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="f5073-107">Then do the following.</span></span>

1. <span data-ttu-id="f5073-108">Na stronie GUIX Studio w sklepie App Store kliknij przycisk **Pobierz** lub **Zainstaluj** , aby pobrać program GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="f5073-108">From the GUIX Studio page in the App Store, click the **Get** or **Install** button to download GUIX Studio.</span></span>

1. <span data-ttu-id="f5073-109">W przeglądarce może zostać wyświetlony komunikat z pytaniem, czy chcesz otworzyć Microsoft Store, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="f5073-109">Your browser may display a message asking if you want to open the Microsoft Store, as shown in the figure below.</span></span> <span data-ttu-id="f5073-110">Jeśli tak, wybierz przycisk **Otwórz** .</span><span class="sxs-lookup"><span data-stu-id="f5073-110">If it does, choose the **Open** button.</span></span>
<span data-ttu-id="f5073-111">![Wybierz pozycję Otwórz, aby zainstalować program GUIX Studio.](./media/guix-studio/open-ms-store.png)</span><span class="sxs-lookup"><span data-stu-id="f5073-111">![Choose Open to install GUIX Studio.](./media/guix-studio/open-ms-store.png)</span></span>

1. <span data-ttu-id="f5073-112">Po zakończeniu instalacji wybierz przycisk **Uruchom** .</span><span class="sxs-lookup"><span data-stu-id="f5073-112">When the install finishes, choose the **Launch** button.</span></span>

1. <span data-ttu-id="f5073-113">Przy pierwszym uruchomieniu programu GUIX Studio zostanie wyświetlone okno dialogowe z pytaniem, czy chcesz sklonować repozytorium GUIX na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f5073-113">The first time that GUIX Studio launches, it displays a dialog box asking if you want to clone the GUIX repo to your local computer.</span></span> <span data-ttu-id="f5073-114">Można wybrać klonowanie repozytorium, wskazać miejsce, w którym zostało już Sklonowane repozytorium, lub zrezygnować z klonowania repozytorium. w takim przypadku na komputerze jest zainstalowany jeden przykładowy projekt.</span><span class="sxs-lookup"><span data-stu-id="f5073-114">You can either choose to clone the repository, point to where you have already cloned the repo, or choose not to clone the repo at all (in which case, one example project is installed on your computer).</span></span>
<span data-ttu-id="f5073-115">![Wybierz klonowanie repozytorium, wskaż już Sklonowane repozytorium lub Pomiń.](./media/guix-studio/clone-repo.png)</span><span class="sxs-lookup"><span data-stu-id="f5073-115">![Choose to clone the repo, point to an already-cloned repo, or skip.](./media/guix-studio/clone-repo.png)</span></span>

> <span data-ttu-id="f5073-116">!</span><span class="sxs-lookup"><span data-stu-id="f5073-116">!</span></span>[!NOTE]
> <span data-ttu-id="f5073-117">Możesz powrócić do tego okna dialogowego w dowolnym momencie, wybierając pozycję **Konfiguruj** z menu głównego GUIX stuido, a następnie **repozytorium GUIX**.</span><span class="sxs-lookup"><span data-stu-id="f5073-117">You can return to this dialog box at any time by choosing **Configure** from the main menu of GUIX Stuido, followed by **GUIX Repository**.</span></span>

<span data-ttu-id="f5073-118">Po zakończeniu procesu uruchamiania będzie można korzystać z programu GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="f5073-118">After the startup process is finished, you will be ready to use GUIX Studio.</span></span>

## <a name="using-guix-studio"></a><span data-ttu-id="f5073-119">Korzystanie z programu GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="f5073-119">Using GUIX Studio</span></span>

<span data-ttu-id="f5073-120">Korzystanie z programu GUIX Studio jest proste — wystarczy uruchomić program GUIX Studio za pomocą przycisku "***Start***".</span><span class="sxs-lookup"><span data-stu-id="f5073-120">Using GUIX Studio is easy - simply run GUIX Studio via the "***Start***" button.</span></span> <span data-ttu-id="f5073-121">W tym momencie zobaczysz interfejs użytkownika programu GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="f5073-121">At this point you will observe the GUIX Studio UI.</span></span> <span data-ttu-id="f5073-122">Teraz można przystąpić do tworzenia graficznego interfejsu użytkownika przy użyciu programu GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="f5073-122">You are now ready to use GUIX Studio to graphically create your embedded UI.</span></span> <span data-ttu-id="f5073-123">W tym miejscu utworzysz nowy projekt lub Otwórz istniejący projekt, w tym przykładowe projekty GUIX.</span><span class="sxs-lookup"><span data-stu-id="f5073-123">From here you create a new project or open an existing project, including the GUIX example projects.</span></span>

> [!NOTE]
> <span data-ttu-id="f5073-124">Możesz również kliknąć dwukrotnie dowolny plik projektu GUIX Studio o rozszerzeniu "**GXP",** co spowoduje automatyczne uruchomienie GUIX Studio i otwarcie przywoływanego projektu.</span><span class="sxs-lookup"><span data-stu-id="f5073-124">You can also double-click on any GUIX Studio project file with an extension of "**gxp,**" which will automatically launch GUIX Studio and open the referenced project.</span></span>

## <a name="guix-studio-project-samples"></a><span data-ttu-id="f5073-125">Przykłady projektu GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="f5073-125">GUIX Studio Project Samples</span></span>

<span data-ttu-id="f5073-126">Seria przykładowych plików projektu GUIX Studio o rozszerzeniu "\***GXP**_" znajduje się w_ \* podkatalogu "_Samples_\* \*" instalacji.</span><span class="sxs-lookup"><span data-stu-id="f5073-126">A series of example GUIX Studio project files with the extension "\***gxp**_" are found in the "_\*_Samples_\*\*" sub-directory of your installation.</span></span> <span data-ttu-id="f5073-127">Te wstępnie skompilowane projekty pomogą Ci uzyskać komfort korzystania z programu GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="f5073-127">These pre-built example projects will help you get comfortable with using GUIX Studio.</span></span>

<span data-ttu-id="f5073-128">Jeden przykładowy plik projektu, który jest zawsze obecny to plik \***Samples/demo_guix_simple/guix_simple. GXP** _.</span><span class="sxs-lookup"><span data-stu-id="f5073-128">One example project file that is always present is the file \***samples/demo_guix_simple/guix_simple.gxp** _.</span></span> <span data-ttu-id="f5073-129">Ten przykładowy plik projektu pokazuje definicję prostego interfejsu użytkownika GUIX, zgodnie z opisem w *_rozdziale 7_*\* tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f5073-129">This example project file shows the definition of a simple GUIX UI, as described in _ *_Chapter 7_*\* of this document.</span></span>

![Zrzut ekranu przedstawiający interfejs użytkownika programu GUIX Studio.](./media/guix-studio/image_10.png)

<span data-ttu-id="f5073-131">**Rysunek 1**</span><span class="sxs-lookup"><span data-stu-id="f5073-131">**Figure 1**</span></span>

## <a name="keyboard-shortcuts"></a><span data-ttu-id="f5073-132">Skróty klawiaturowe</span><span class="sxs-lookup"><span data-stu-id="f5073-132">Keyboard Shortcuts</span></span>

- <span data-ttu-id="f5073-133">**Ctrl + N:** Nowy projekt</span><span class="sxs-lookup"><span data-stu-id="f5073-133">**Ctrl + N:** New Project</span></span>
- <span data-ttu-id="f5073-134">**Ctrl + O:** Otwórz projekt</span><span class="sxs-lookup"><span data-stu-id="f5073-134">**Ctrl + O:** Open Project</span></span>
- <span data-ttu-id="f5073-135">**Ctrl + S:** Zapisz projekt</span><span class="sxs-lookup"><span data-stu-id="f5073-135">**Ctrl + S:** Save Project</span></span>
- <span data-ttu-id="f5073-136">**Ctrl + Shift + S:** Zapisz projekt jako</span><span class="sxs-lookup"><span data-stu-id="f5073-136">**Ctrl + Shift + S:** Save Project As</span></span>
- <span data-ttu-id="f5073-137">**Alt + F4:** Opuść</span><span class="sxs-lookup"><span data-stu-id="f5073-137">**Alt + F4:** Exit</span></span>
