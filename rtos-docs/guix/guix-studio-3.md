---
title: Opis programu GUIX Studio
description: Ten rozdział zawiera opis narzędzia do analizy systemu GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 89bbcd51c22dddef6e420750e8c8805a66344335
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822273"
---
# <a name="chapter-3-description-of-guix-studio"></a><span data-ttu-id="602e2-103">Rozdział 3: Opis programu GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="602e2-103">Chapter 3: Description of GUIX Studio</span></span>

<span data-ttu-id="602e2-104">Ten rozdział zawiera opis narzędzia do analizy systemu GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="602e2-104">This chapter contains a description of the GUIX Studio system analysis tool.</span></span> <span data-ttu-id="602e2-105">W tym rozdziale znajduje się opis ogólnych funkcji interfejsu GUI.</span><span class="sxs-lookup"><span data-stu-id="602e2-105">A description of the overall functionality of the GUI is found in this chapter.</span></span> 

## <a name="guix-studio-views"></a><span data-ttu-id="602e2-106">Widoki GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="602e2-106">GUIX Studio Views</span></span>

<span data-ttu-id="602e2-107">Istnieje pięć głównych obszarów interfejsu użytkownika programu GUIX Studio, a mianowicie **pasek narzędzi**\* _, widok _*_projektu_*_, _*_Widok właściwości_*_, _*_Widok docelowy_*_ i _*_Widok zasobów_*_.</span><span class="sxs-lookup"><span data-stu-id="602e2-107">There are five principal areas of the GUIX Studio UI, namely the ***Toolbar** _, _*_Project View_*_, _*_Properties View_*_, _*_Target View_*_, and _*_Resource View_\*_.</span></span> <span data-ttu-id="602e2-108">*_Ilustracja 2_*\* przedstawia podstawowy interfejs użytkownika programu GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="602e2-108">_ *_Figure 2_*\* shows the basic GUIX Studio UI.</span></span> <span data-ttu-id="602e2-109">Każdy z tych widoków został szczegółowo omówiony w poniższych podsekcjach.</span><span class="sxs-lookup"><span data-stu-id="602e2-109">Each of the views is further discussed in the following sub-sections.</span></span>

![Zrzut ekranu przedstawiający podstawowy interfejs użytkownika programu GUIX Studio.](./media/guix-studio/image_10.png)

<span data-ttu-id="602e2-111">**Rysunek 2**</span><span class="sxs-lookup"><span data-stu-id="602e2-111">**Figure 2**</span></span>

### <a name="title"></a><span data-ttu-id="602e2-112">Tytuł</span><span class="sxs-lookup"><span data-stu-id="602e2-112">Title</span></span>

- <span data-ttu-id="602e2-113">GUIX Studio 18: ***title** _ wyświetla wersję programu GUIX Studio, a także aktualnie otwarty projekt, jak pokazano na początku _ *_rysunku 2_** poprzednio.</span><span class="sxs-lookup"><span data-stu-id="602e2-113">GUIX Studio 18: The ***Title** _ displays the GUIX Studio version as well as the currently open project, as shown at the top of _ *_Figure 2_** previously.</span></span>

### <a name="toolbar"></a><span data-ttu-id="602e2-114">Pasek narzędzi</span><span class="sxs-lookup"><span data-stu-id="602e2-114">Toolbar</span></span>

<span data-ttu-id="602e2-115">**Pasek narzędzi**\* _ pokazuje przyciski dostępne dla dewelopera programu GUIX Studio, jak pokazano na _rysunku 3_\* \* \*.</span><span class="sxs-lookup"><span data-stu-id="602e2-115">The ***Toolbar** _ shows the buttons available to the GUIX Studio developer, as shown in _*_Figure 3_\*\*.</span></span>

![Zrzut ekranu przedstawiający pasek narzędzi GUIX Studio.](./media/guix-studio/image11.jpg)

<span data-ttu-id="602e2-117">**Rysunek 3**</span><span class="sxs-lookup"><span data-stu-id="602e2-117">**Figure 3**</span></span>

<span data-ttu-id="602e2-118">Przyciski paska narzędzi są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="602e2-118">The toolbar buttons are defined as follows:</span></span>

![Przycisk Nowy](./media/guix-studio/new-button.png) <span data-ttu-id="602e2-120">Tworzy nowy projekt programu GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="602e2-120">Creates a new GUIX Studio project</span></span>

![Przycisk Otwórz](./media/guix-studio/open-button.png) <span data-ttu-id="602e2-122">Otwiera istniejący projekt programu GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="602e2-122">Opens an existing GUIX Studio project</span></span>

![Przycisk Zapisz](./media/guix-studio/save-button.png) <span data-ttu-id="602e2-124">Zapisuje projekt</span><span class="sxs-lookup"><span data-stu-id="602e2-124">Saves the project</span></span>

![Przycisk Wytnij](./media/guix-studio/cut-button.png) <span data-ttu-id="602e2-126">Zaznaczono element widget wycinania, w tym elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="602e2-126">Cut widget selected, including children</span></span>

![Kopiuj](./media/guix-studio/copy-button.png) <span data-ttu-id="602e2-128">Kopiuj wybrany widżet, w tym elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="602e2-128">Copy selected widget, including children</span></span>

![Przycisk Wklej](./media/guix-studio/paste-button.png) <span data-ttu-id="602e2-130">Wklej widżet i elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="602e2-130">Paste widget and children</span></span>

![Przycisk Wyrównaj do lewej](./media/guix-studio/left-align-button.png) <span data-ttu-id="602e2-132">Wyrównanie wybranych elementów widget do lewej</span><span class="sxs-lookup"><span data-stu-id="602e2-132">Left-align selected widgets</span></span>

![Przycisk Wyrównaj do prawej](./media/guix-studio/right-align-button.png) <span data-ttu-id="602e2-134">Wyrównanie wybranych elementów widget do prawej</span><span class="sxs-lookup"><span data-stu-id="602e2-134">Right-align selected widgets</span></span>

![Przycisk Wyrównaj do góry](./media/guix-studio/top-align-button.png) <span data-ttu-id="602e2-136">Wyrównaj do góry wybrane widżety</span><span class="sxs-lookup"><span data-stu-id="602e2-136">Top-align selected widgets</span></span>

![Przycisk Wyrównaj do dołu](./media/guix-studio/bottom-align-button.png) <span data-ttu-id="602e2-138">Wyrównaj do dołu wybrane widżety</span><span class="sxs-lookup"><span data-stu-id="602e2-138">Bottom-align selected widgets</span></span>

![Przycisk spacji w pionie](./media/guix-studio/space-vertically-button.png) <span data-ttu-id="602e2-140">Równe miejsce wybrane widżety w pionie</span><span class="sxs-lookup"><span data-stu-id="602e2-140">Equally space selected widgets vertically</span></span>

![Przycisk odstępu w poziomie](./media/guix-studio/space-horizontally-button.png) <span data-ttu-id="602e2-142">Równe miejsce wybrane widżety w poziomie</span><span class="sxs-lookup"><span data-stu-id="602e2-142">Equally space selected widgets horizontally</span></span>

![Przycisk o równej szerokości](./media/guix-studio/equal-width-button.png) <span data-ttu-id="602e2-144">Ustaw wybraną szerokość równą wartości widget</span><span class="sxs-lookup"><span data-stu-id="602e2-144">Make selected widgets equal width</span></span>

![Przycisk równej wysokości](./media/guix-studio/equal-height-button.png) <span data-ttu-id="602e2-146">Zmień wysokość wybranych elementów widget</span><span class="sxs-lookup"><span data-stu-id="602e2-146">Make selected widgets equal height</span></span>

![Przycisk Przenieś przód](./media/guix-studio/move-front-button.png) <span data-ttu-id="602e2-148">Przenieś wybrane elementy widget na wierzch</span><span class="sxs-lookup"><span data-stu-id="602e2-148">Move selected widgets to front</span></span>

![Przycisk przenoszenia wstecz](./media/guix-studio/move-back-button.png) <span data-ttu-id="602e2-150">Przenieś wybrane elementy widget na spód</span><span class="sxs-lookup"><span data-stu-id="602e2-150">Move selected widgets to back</span></span>

![Przycisk rozmiar](./media/guix-studio/size-button.png) <span data-ttu-id="602e2-152">Rozmiar wybranego elementu widget do zawartości na ekranie celu</span><span class="sxs-lookup"><span data-stu-id="602e2-152">Size selected widget to content Zoom out target screen</span></span>

![Przycisk Powiększ](./media/guix-studio/zoom-out-button.png) <span data-ttu-id="602e2-154">Ekran pomniejszej wartości docelowej</span><span class="sxs-lookup"><span data-stu-id="602e2-154">Zoom out target screen</span></span>

![Przycisk Powiększ](./media/guix-studio/zoom-in-button.png) <span data-ttu-id="602e2-156">Powiększ na ekranie docelowym</span><span class="sxs-lookup"><span data-stu-id="602e2-156">Zoom in target screen</span></span>

![Przycisk nagrywania](./media/guix-studio/record-button.png) <span data-ttu-id="602e2-158">Rejestruj makro</span><span class="sxs-lookup"><span data-stu-id="602e2-158">Record Macro</span></span>

![Przycisk odtwarzania](./media/guix-studio/playback-button.png) <span data-ttu-id="602e2-160">Makro odtwarzania</span><span class="sxs-lookup"><span data-stu-id="602e2-160">Playback Macro</span></span>

![Przycisk Uruchom](./media/guix-studio/run-button.png) <span data-ttu-id="602e2-162">Uruchom aplikację</span><span class="sxs-lookup"><span data-stu-id="602e2-162">Run Application</span></span>

![Przycisk about — informacje](./media/guix-studio/about-button.png) <span data-ttu-id="602e2-164">Informacje o programie GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="602e2-164">About GUIX Studio</span></span>

### <a name="project-view"></a><span data-ttu-id="602e2-165">Widok projektu</span><span class="sxs-lookup"><span data-stu-id="602e2-165">Project View</span></span>

<span data-ttu-id="602e2-166">\***Widok projektu** _ pokazuje hierarchiczną listę obiektów GUIX, które składają się na OSADZONY interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="602e2-166">The \***Project View** _ shows the hierarchical list GUIX objects that comprise the embedded UI.</span></span> <span data-ttu-id="602e2-167">Nowe obiekty GUIX można dodać, klikając obiekt nadrzędny, a następnie wybierając obiekt z menu _*_Wstaw_*_ (lub klikając prawym przyciskiem myszy obiekt i wybierając je z menu rozwijanego po prawej stronie).</span><span class="sxs-lookup"><span data-stu-id="602e2-167">New GUIX objects can be added by clicking on the parent object and then selecting an object from the _*_Insert_*_ menu (or by right-clicking on the object and selecting from the right-click menu).</span></span> <span data-ttu-id="602e2-168">Na _*_rysunku 4_*_ poniżej przedstawiono _Widok projektu_ GUIX Studio _ \* \* \*.</span><span class="sxs-lookup"><span data-stu-id="602e2-168">_*_Figure 4_*_ below shows the GUIX Studio _\*_Project View_\*\*.</span></span>

![Zrzut ekranu przedstawiający widok projektu GUIX Studio.](./media/guix-studio/image_35.png)

<span data-ttu-id="602e2-170">**Rysunek 4**</span><span class="sxs-lookup"><span data-stu-id="602e2-170">**Figure 4**</span></span>

### <a name="properties-view"></a><span data-ttu-id="602e2-171">Widok właściwości</span><span class="sxs-lookup"><span data-stu-id="602e2-171">Properties View</span></span>

<span data-ttu-id="602e2-172">**Widok właściwości**\* _ pokazuje szczegółowe informacje o właściwości aktualnie wybranego obiektu GUIX, który można wybrać za pośrednictwem _*_widoku projektu_*_ lub klikając bezpośrednio na obiekcie w _*_widoku elementu docelowego_*_.</span><span class="sxs-lookup"><span data-stu-id="602e2-172">The ***Properties View** _ shows detailed property information of the currently selected GUIX object, which can be selected via the _*_Project View_*_ or by clicking directly on the object in the _*_Target View_\*_.</span></span> <span data-ttu-id="602e2-173">Na _*_rysunku 5_*_ poniżej przedstawiono _Widok właściwości_ GUIX Studio _ \* \* \*.</span><span class="sxs-lookup"><span data-stu-id="602e2-173">_*_Figure 5_*_ below shows the GUIX Studio _\*_Properties View_\*\*.</span></span>

![Zrzut ekranu przedstawiający widok Właściwości programu GUIX Studio.](./media/guix-studio/image36.jpg)

<span data-ttu-id="602e2-175">**Rysunek 5**</span><span class="sxs-lookup"><span data-stu-id="602e2-175">**Figure 5**</span></span>

### <a name="target-view"></a><span data-ttu-id="602e2-176">Widok docelowy</span><span class="sxs-lookup"><span data-stu-id="602e2-176">Target View</span></span>

<span data-ttu-id="602e2-177">**Widok docelowy**\* _ jest obszarem projektowania i układu ekranu WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="602e2-177">The \***Target View** _ is the WYSIWYG screen design and layout area.</span></span> <span data-ttu-id="602e2-178">Ten widok jest przeznaczony do reprezentowania fizycznego ekranu lub wyświetlaczy dostępnego na sprzęcie docelowym.</span><span class="sxs-lookup"><span data-stu-id="602e2-178">This view is meant to represent the physical display or displays available on your target hardware.</span></span> <span data-ttu-id="602e2-179">Obiekty można zaznaczać, przenosić, zmieniać ich rozmiar itp. za pomocą prostych operacji myszy.</span><span class="sxs-lookup"><span data-stu-id="602e2-179">Objects can be selected, moved, resized, etc. via simple mouse operations.</span></span> <span data-ttu-id="602e2-180">Ponadto w wybranych obiektach w widoku docelowym są dostępne operacje wyrównania i kolejności przycisków.</span><span class="sxs-lookup"><span data-stu-id="602e2-180">In addition, alignment and Z-order button operations are available on selected objects in the Target View.</span></span> <span data-ttu-id="602e2-181">Wybranie obiektu w _*_widoku docelowym_*_ spowoduje również wyświetlenie właściwości tego obiektu w _*_widoku właściwości_*_.</span><span class="sxs-lookup"><span data-stu-id="602e2-181">Selecting an object in the _*_Target View_*_ will also result in the properties for that object to be displayed in the _*_Properties View_*_.</span></span> <span data-ttu-id="602e2-182">Na _*_rysunku 6_*_ poniżej przedstawiono _Widok docelowy_ GUIX Studio _ \* \* \*.</span><span class="sxs-lookup"><span data-stu-id="602e2-182">_*_Figure 6_*_ below shows the GUIX Studio _\*_Target View_\*\*.</span></span>

![Zrzut ekranu przedstawiający widok docelowy programu GUIX Studio.](./media/guix-studio/image_37.png)

<span data-ttu-id="602e2-184">**Rysunek 6.**</span><span class="sxs-lookup"><span data-stu-id="602e2-184">**Figure 6**</span></span>

### <a name="resource-view"></a><span data-ttu-id="602e2-185">Widok zasobów</span><span class="sxs-lookup"><span data-stu-id="602e2-185">Resource View</span></span>

<span data-ttu-id="602e2-186">\***Widok zasobów** _ służy do zarządzania zasobami (kolorami, czcionkami, pixelmaps i ciągami) dostępnymi dla ekranów aplikacji zdefiniowanych dla każdego ekranu.</span><span class="sxs-lookup"><span data-stu-id="602e2-186">The \***Resource View** _ is used to manage the resources (colors, fonts, pixelmaps, and strings) available to applications screens defined for each display.</span></span> <span data-ttu-id="602e2-187">Możesz kliknąć nagłówki grupy widok zasobów, aby rozwinąć każdą grupę i sprawdzić zawartość grupy.</span><span class="sxs-lookup"><span data-stu-id="602e2-187">You can click on the resource view group headers to expand each group and examine the group contents.</span></span> <span data-ttu-id="602e2-188">_*_Rysunek 7_*_ poniżej przedstawia GUIX Studio _ *_Widok zasobów_* \*.</span><span class="sxs-lookup"><span data-stu-id="602e2-188">_*_Figure 7_*_ below shows the GUIX Studio _\*_Resource View_\*\*.</span></span>

![Zrzut ekranu GUIX Studio Widok zasobów.](./media/guix-studio/image38.jpg)

<span data-ttu-id="602e2-190">**Rysunek 7**</span><span class="sxs-lookup"><span data-stu-id="602e2-190">**Figure 7**</span></span>

<span data-ttu-id="602e2-191">Tytuł grup zasobów wskazuje bieżącą nazwę motywu.</span><span class="sxs-lookup"><span data-stu-id="602e2-191">The title of the resource groups indicates current theme name.</span></span> <span data-ttu-id="602e2-192">Jeśli dostępnych jest wiele motywów, można przełączać się między motywami, klikając strzałkę w górę i w dół.</span><span class="sxs-lookup"><span data-stu-id="602e2-192">If multi themes available, you are able to switch between themes by clicking on the up and down arrow.</span></span>

<span data-ttu-id="602e2-193">Wszystkie grupy zasobów w widoku powyżej mogą być rozwinięte lub zwinięte przez kliknięcie nagłówka grupy.</span><span class="sxs-lookup"><span data-stu-id="602e2-193">Each resource group in the view above can be expanded or collapsed by clicking on the group header.</span></span> <span data-ttu-id="602e2-194">Bardziej szczegółowy opis poszczególnych grup zasobów znajduje się w następnym rozdziale.</span><span class="sxs-lookup"><span data-stu-id="602e2-194">A more detailed description of each resource groups follows in the next chapter.</span></span>

## <a name="the-guix-studio-project"></a><span data-ttu-id="602e2-195">Projekt GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="602e2-195">The GUIX Studio Project</span></span>

<span data-ttu-id="602e2-196">Projekt programu GUIX Studio przechowuje informacje o projekcie ekranu interfejsu użytkownika i zasobach interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="602e2-196">A GUIX Studio project maintains information about your UI screen design and UI resources.</span></span> <span data-ttu-id="602e2-197">Dane projektu są zapisywane w pliku formatu XML z rozszerzeniem ". ***GXP***".</span><span class="sxs-lookup"><span data-stu-id="602e2-197">The project data is saved to an XML format file with the extension ".***gxp***".</span></span> <span data-ttu-id="602e2-198">Ponieważ plik projektu jest plikiem schematu XML, może być kontrolowany pod kontrolą wersji i udostępniony w innym pliku źródłowym.</span><span class="sxs-lookup"><span data-stu-id="602e2-198">Since the project file is an XML schema file, it can be versioned controlled and shared similar to any other source file.</span></span>

<span data-ttu-id="602e2-199">Przy pierwszym uruchomieniu przy użyciu programu GUIX Studio należy otworzyć jeden z przykładowych projektów dostarczonych z dystrybucją lub utworzyć nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="602e2-199">When you first start using GUIX Studio, you will need to either open one of the example projects provided with the distribution or create a new project.</span></span> <span data-ttu-id="602e2-200">Cała Twoja służbowa jest zapisywana w pliku danych projektu.</span><span class="sxs-lookup"><span data-stu-id="602e2-200">All of your work is saved to the project data file.</span></span>

<span data-ttu-id="602e2-201">GUIX Studio tworzy również pliki źródłowe ANSI C.</span><span class="sxs-lookup"><span data-stu-id="602e2-201">GUIX Studio also produces ANSI C source files.</span></span> <span data-ttu-id="602e2-202">Te pliki źródłowe zawierają zasoby aplikacji lub struktury danych opisujące zaprojektowane ekrany.</span><span class="sxs-lookup"><span data-stu-id="602e2-202">These source files contain either your application resources or data structures describing your designed screens.</span></span> <span data-ttu-id="602e2-203">GUIX Studio zapisuje również w tych generowanych funkcjach interfejsu API plików źródłowych, które wiedzą, jak używać wygenerowanych struktur danych do dynamicznego tworzenia ekranów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="602e2-203">GUIX Studio also writes to these generated source files API functions that know to utilize the generated data structures to dynamically create your application screens.</span></span> <span data-ttu-id="602e2-204">Oprogramowanie aplikacji po prostu wywoła dostarczone funkcje interfejsu API w celu utworzenia ekranów zaprojektowanych w ramach programu GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="602e2-204">Your application software will simply invoke the provided API functions to create the screens you have designed within GUIX Studio.</span></span>

<span data-ttu-id="602e2-205">Podczas projektowania interfejsu użytkownika należy okresowo używać programu GUIX Studio do generowania plików wyjściowych zgodnych z GUIX, które umożliwią Kompilowanie i uruchamianie zaprojektowanego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="602e2-205">As you progress in designing your user interface, you will periodically want to use GUIX Studio to generate the GUIX compatible output files that will allow you to build and run the interface you have designed.</span></span> <span data-ttu-id="602e2-206">Można kompilować i uruchamiać wygenerowane pliki źródłowe dla sprzętu docelowego lub na pulpicie systemu Windows, które symulują ThreadX i GUIX.</span><span class="sxs-lookup"><span data-stu-id="602e2-206">You can compile and run the generated source files for either your target hardware or on your Windows desktop that simulates ThreadX and GUIX.</span></span>

## <a name="guix-studio-project-organization"></a><span data-ttu-id="602e2-207">Organizacja projektu programu GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="602e2-207">GUIX Studio Project Organization</span></span>

<span data-ttu-id="602e2-208">Warto mieć pewną wiedzę na temat podstawowej organizacji projektu GUIX Studio, aby zrozumieć, jak używać GUIX Studio efektywnie i zrozumieć informacje przedstawione w widoku projektu środowiska IDE GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="602e2-208">It is helpful to have some knowledge of the basic organization of a GUIX Studio project to understand how to use GUIX Studio effectively and to understand the information presented in the Project View of the GUIX Studio IDE.</span></span> <span data-ttu-id="602e2-209">Widok projektu jest podsumowującą wizualną reprezentacją wszystkich informacji zawartych w projekcie.</span><span class="sxs-lookup"><span data-stu-id="602e2-209">The Project View is a summary visual representation of all of the information contained in your project.</span></span>

<span data-ttu-id="602e2-210">Przed rozpoczęciem opisywania projektu konieczne jest zdefiniowanie kilku warunków.</span><span class="sxs-lookup"><span data-stu-id="602e2-210">Before describing the project, it is necessary to define few terms.</span></span> <span data-ttu-id="602e2-211">Najpierw użyjemy **wyświetlania** terminu do oznaczania fizycznego urządzenia wyświetlającego.</span><span class="sxs-lookup"><span data-stu-id="602e2-211">First, we use the term **Display** to mean a physical display device.</span></span> <span data-ttu-id="602e2-212">Jest to najczęściej wyświetlane urządzenie wyświetlacza LCD, ale może ono korzystać z innej technologii.</span><span class="sxs-lookup"><span data-stu-id="602e2-212">This is most often an LCD display device but it could be using other technology.</span></span> <span data-ttu-id="602e2-213">Następnym terminem jest **ekran**, który oznacza obiekt GUIX najwyższego poziomu, zazwyczaj okno GUIX i wszystkie skojarzone z nim elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="602e2-213">The next term is **Screen**, which mean a top-level GUIX object, usually a GUIX Window, and all of its associated child elements.</span></span> <span data-ttu-id="602e2-214">Ekran to konstrukcja programowa, która może być zdefiniowana i modyfikowana w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="602e2-214">A Screen is a software construct that can be defined and modified at runtime.</span></span> <span data-ttu-id="602e2-215">Na koniec **motyw** jest kolekcją zasobów.</span><span class="sxs-lookup"><span data-stu-id="602e2-215">Finally, a **Theme** is a collection of resources.</span></span> <span data-ttu-id="602e2-216">Motyw zawiera tabelę definicji koloru, definicje czcionek i definicje Pixelmap, które zostały zaprojektowane tak, aby dobrze współpracować i przedstawić użytkownikowi końcowemu spójny wygląd i działanie.</span><span class="sxs-lookup"><span data-stu-id="602e2-216">A theme includes a table of color definitions, font definitions, and pixelmap definitions that are designed to work well together and present your end user with a consistent look and feel.</span></span>

<span data-ttu-id="602e2-217">Projekt najpierw zawiera zestaw informacji globalnych, takich jak nazwa projektu, liczba obsługiwanych wyświetlaczy, rozdzielczość i format koloru każdego ekranu, liczba obsługiwanych języków, Nazwa każdego obsługiwanego języka.</span><span class="sxs-lookup"><span data-stu-id="602e2-217">The project first includes a set of global information such as the project name, number of displays supported, the resolution and color format of each display, the number of languages supported, the name of each supported language.</span></span> <span data-ttu-id="602e2-218">Nazwa projektu to pierwszy węzeł wyświetlany w widoku projektu.</span><span class="sxs-lookup"><span data-stu-id="602e2-218">The project name is the first node displayed in the Project View.</span></span>

<span data-ttu-id="602e2-219">Projekt dalej organizuje wszystkie informacje wymagane do 4 fizycznych wyświetlania, a ekrany i zasoby dostępne dla każdego ekranu.</span><span class="sxs-lookup"><span data-stu-id="602e2-219">The project next organizes all of the information required for up to 4 physical displays and the screens and resources available to each display.</span></span> <span data-ttu-id="602e2-220">Nazwy wyświetlane są węzłami następnego poziomu w drzewie widoku projektu.</span><span class="sxs-lookup"><span data-stu-id="602e2-220">The display names are the next level nodes in the Project View tree.</span></span>

<span data-ttu-id="602e2-221">Unikatowa funkcja aplikacji GUIX Studio to wbudowana obsługa wielu ekranów fizycznych, z których każda ma własne rozdzielczości x, y, format koloru, ekrany i zasoby.</span><span class="sxs-lookup"><span data-stu-id="602e2-221">A unique feature of the GUIX Studio application is built-in support for multiple physical displays, each with its own x,y resolution, color format, screens, and resources.</span></span> <span data-ttu-id="602e2-222">Chociaż większość aplikacji GUIX korzysta tylko z jednego fizycznego ekranu, ta funkcja jest ważna w przypadku, gdy produkt musi obsługiwać wiele równoczesnych ekranów fizycznych.</span><span class="sxs-lookup"><span data-stu-id="602e2-222">While the vast majority of GUIX applications utilize only one physical display, this capability is important for those making a product that must support multiple simultaneous physical displays.</span></span>

<span data-ttu-id="602e2-223">Poniżej każdej definicji ekranu znajdują się okna lub ekrany najwyższego poziomu zdefiniowane dla tego ekranu.</span><span class="sxs-lookup"><span data-stu-id="602e2-223">Beneath each display definition are the top-level windows or screens defined for that display.</span></span> <span data-ttu-id="602e2-224">Definicje ekranu mogą być zagnieżdżane na dowolnym poziomie w zależności od liczby i zagnieżdżenia elementów widget podrzędnych na każdym ekranie.</span><span class="sxs-lookup"><span data-stu-id="602e2-224">The screen definitions can be nested to any level depending on the number and nesting of child widgets on each screen.</span></span>

<span data-ttu-id="602e2-225">Ten ekran i podrzędna organizacja widżetu są wyświetlane w sposób graficzny w widoku projektu.</span><span class="sxs-lookup"><span data-stu-id="602e2-225">This screen and child widget organization is displayed in a graphical manner in the Project View.</span></span>

<span data-ttu-id="602e2-226">Skojarzone z poszczególnymi ekranami są kompozycje obsługiwane przez ekran i zawartość zasobów tworzących każdy motyw.</span><span class="sxs-lookup"><span data-stu-id="602e2-226">Also associated with each display are the Themes supported by the display and the resource content composing each Theme.</span></span> <span data-ttu-id="602e2-227">Jeśli projekt zawiera wiele ekranów, Zauważ, że Widok zasobów zmienia jego zawartość po wybraniu jednego ekranu, a następnie innej.</span><span class="sxs-lookup"><span data-stu-id="602e2-227">If your project includes multiple displays, you will notice that the Resource View changes its content when you select one display and then another.</span></span> <span data-ttu-id="602e2-228">Wynika to z faktu, że zawartość zasobu jest połączona z każdym wyświetlaniem.</span><span class="sxs-lookup"><span data-stu-id="602e2-228">This is because the resource content is linked to each display.</span></span> <span data-ttu-id="602e2-229">Nie tylko format koloru może być inny, ale pixelmaps, kolory i czcionki, których wybierasz, mogą się różnić od jednego wyświetlania fizycznego na inny.</span><span class="sxs-lookup"><span data-stu-id="602e2-229">Not only the color format may be different, but the pixelmaps, colors, and fonts you choose to use may vary from one physical display to another.</span></span>

<span data-ttu-id="602e2-230">Końcowy składnik obsługiwany przez projekt to dane tabeli ciągów skojarzone z poszczególnymi ekranami.</span><span class="sxs-lookup"><span data-stu-id="602e2-230">The final component maintained by the project is the string table data associated with each display.</span></span> <span data-ttu-id="602e2-231">Ponieważ wyświetlacze mogą być bardzo różnymi rozdzielczościami x, y, dane ciągu są obsługiwane niezależnie dla każdego ekranu zdefiniowanego w projekcie.</span><span class="sxs-lookup"><span data-stu-id="602e2-231">Since displays can be of very different x,y resolutions, the string data is maintained independently for each display defined in the project.</span></span>
