---
title: Prosty przykładowy projekt
description: W tym rozdziale opisano sposób tworzenia przykładowego projektu w programie GUIX Studio i wykonywania przykładu na GUIX.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3661396f097e0ed7bd872fae01a7bec9212001b9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822332"
---
# <a name="chapter-10-example-project"></a><span data-ttu-id="e9ae7-103">Rozdział 10: przykładowy projekt</span><span class="sxs-lookup"><span data-stu-id="e9ae7-103">Chapter 10: Example Project</span></span>

<span data-ttu-id="e9ae7-104">W tym rozdziale opisano sposób tworzenia przykładowego projektu w programie GUIX Studio i wykonywania przykładu na GUIX.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-104">This chapter describes how to create an example project in GUIX Studio and execute the example on GUIX.</span></span>

## <a name="create-new-project"></a><span data-ttu-id="e9ae7-105">Tworzenie nowego projektu</span><span class="sxs-lookup"><span data-stu-id="e9ae7-105">Create New Project</span></span>

<span data-ttu-id="e9ae7-106">Pierwszym krokiem jest utworzenie nowego projektu i skonfigurowanie ekranów i języków, które będą obsługiwane przez projekt.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-106">The first step is creating a new project and configuring the displays and languages that the project will support.</span></span> <span data-ttu-id="e9ae7-107">Po pierwszym uruchomieniu GUIX Studio zobaczysz ekran ***ostatnie projekty*** :</span><span class="sxs-lookup"><span data-stu-id="e9ae7-107">When you first start GUIX Studio, you will see the ***Recent Projects*** screen:</span></span>

![Zrzut ekranu przedstawiający okno dialogowe GUIX Studio ostatnich projektów.](./media/guix-studio/recent_projects.png)

<span data-ttu-id="e9ae7-109">**Rysunek 10,1**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-109">**Figure 10.1**</span></span>

<span data-ttu-id="e9ae7-110">Kliknij pozycję \***Utwórz nowy projekt** _...</span><span class="sxs-lookup"><span data-stu-id="e9ae7-110">Click on the \***Create New Project** _…</span></span> <span data-ttu-id="e9ae7-111">, aby rozpocząć nowy projekt.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-111">button to begin a new project.</span></span> <span data-ttu-id="e9ae7-112">Zostanie wyświetlone okno dialogowe _ \*_New GUIX Project_\*\*, pokazane tutaj:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-112">You will be presented with the _ *_New GUIX Project_*\* dialog, shown here:</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Tworzenie nowego projektu w programie GUIX Studio.](./media/guix-studio/create_new_project.png)

<span data-ttu-id="e9ae7-114">**Rysunek 10,2**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-114">**Figure 10.2**</span></span>

<span data-ttu-id="e9ae7-115">Wpisz nazwę "***new_example***" jako nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-115">Type the name "***new_example***" as the project name.</span></span> <span data-ttu-id="e9ae7-116">Nazwy projektów powinny zawierać standardowe reguły nazewnictwa języka C, czyli nie znaki specjalne ani zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-116">Project names should use standard C variable naming rules, that is, no special or reserved characters.</span></span> <span data-ttu-id="e9ae7-117">Wpisz ścieżkę do lokalizacji, w której ma być zapisany projekt.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-117">Type the path to the location where the project should be saved.</span></span> <span data-ttu-id="e9ae7-118">Ścieżka musi być prawidłowym katalogiem systemu plików, czyli GUIX Studio nie utworzy katalogu, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-118">The path must be a valid file system directory, that is, GUIX Studio will not create the directory if it does not exist.</span></span> <span data-ttu-id="e9ae7-119">Kliknij przycisk OK, aby utworzyć projekt.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-119">Click "OK" to create the project.</span></span>

<span data-ttu-id="e9ae7-120">Następnym wyświetlonym ekranem jest ekran Konfiguracja projektu, przedstawiony tutaj:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-120">The next screen shown is the Project Configuration screen, shown here:</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Konfigurowanie projektu programu GUIX Studio.](./media/guix-studio/config_new_project.png)

<span data-ttu-id="e9ae7-122">**Rysunek 10,3**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-122">**Figure 10.3**</span></span>

<span data-ttu-id="e9ae7-123">To okno dialogowe pozwala określić, ile wyświetla projekt będzie obsługiwał, i nadaj nazwę każdemu wyświetlaczowi.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-123">This dialog allows you to specify how many displays your project will support, and give a name to each display.</span></span> <span data-ttu-id="e9ae7-124">Należy określić format koloru obsługiwany przez każdy ekran i opcjonalnie wpisać nazwę ścieżki dla plików wyjściowych generowanych przez Studio dla każdego ekranu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-124">You must specify the color format supported by each display, and optionally type a pathname for the output files generated by Studio for each display.</span></span> <span data-ttu-id="e9ae7-125">Domyślnym katalogiem plików wyjściowych jest "***. \\***", co oznacza, że pliki wyjściowe C są zapisywane w tym samym katalogu co projekt.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-125">The default directory for the output files is "***.\\***", meaning the C output files are written to the same directory as the project itself.</span></span>

<span data-ttu-id="e9ae7-126">Na potrzeby tego przykładu pozostaw ***liczba wyświetleń** _ o wartości "1", wpisz nazwę "_*_main_display_*_" w polu Nazwa wyświetlana i zaznacz opcję "_*_Przydziel pamięć kanwy_\*_".</span><span class="sxs-lookup"><span data-stu-id="e9ae7-126">For this example, leave the ***Number of Displays** _ set to "1", type the name "_*_main_display_*_" in the display name field, and check "_*_allocate canvas memory_\*_".</span></span> <span data-ttu-id="e9ae7-127">Pozostaw wartości domyślne w polach rozdzielczość, format koloru i katalog, a następnie kliknij _ *_OK_* \*.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-127">Leave the resolution, color format, and directory fields at their default values, and click _\*_OK_\*\*.</span></span>

<span data-ttu-id="e9ae7-128">Zobaczysz teraz projekt otwarty za pomocą środowiska IDE programu Studio, jak pokazano na rysunku 10,4:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-128">You should now see your project open with the Studio IDE, as shown in figure 10.4:</span></span>

![Zrzut ekranu projektu otwarty za pomocą programu Studio IDE.](./media/guix-studio/initial_screen.png)

<span data-ttu-id="e9ae7-130">**Rysunek 10,4**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-130">**Figure 10.4**</span></span>

<span data-ttu-id="e9ae7-131">Podczas tworzenia nowego projektu GUIX Studio automatycznie tworzy domyślne okno jako punkt początkowy dla projektu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-131">When you create a new project, GUIX Studio automatically creates a default window as the starting point for your project.</span></span> <span data-ttu-id="e9ae7-132">To szare pole jest domyślnym oknem utworzonym dla Ciebie, wyśrodkowanym w *widoku docelowym*.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-132">This gray box is the default window created for you, centered within the *Target View*.</span></span>

<span data-ttu-id="e9ae7-133">Jeśli to okno nie jest zaznaczone, kliknij okno, aby narysować kreskowane pole zaznaczenia wokół okna.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-133">If this window is not selected, click on the window so that the dashed selection box is drawn around the window.</span></span> <span data-ttu-id="e9ae7-134">Teraz w widoku ***Właściwości** _ Zmień _*_nazwę widżetu_*_, _*_identyfikator widżetu_*_, _*_lewy_*_, _*_górny_*_, _*_Szerokość_*_, _*_wysokość_\*_ i _ \*_obramowanie_\*\*, aby dopasować te ustawienia poniżej.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-134">Now in the ***Properties View** _, change the _*_Widget Name_*_, _*_Widget Id_*_, _*_Left_*_, _*_Top_*_, _*_Width_*_, _*_Height_*_, and _ *_Border_** to match those settings shown below.</span></span> <span data-ttu-id="e9ae7-135">Po wprowadzeniu tych zmian w widoku docelowym powinny zostać wyświetlone zmiany od razu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-135">As you make these changes, you should see your changes immediately taking effect within the Target View.</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Widok właściwości.](./media/guix-studio/initial_window_properties.png)

<span data-ttu-id="e9ae7-137">**Rysunek 10,5**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-137">**Figure 10.5**</span></span>

<span data-ttu-id="e9ae7-138">Następnie dodamy zasób Pixelmap, który będzie używany w elemencie widget \***GX_ICON** _.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-138">Next we will add a pixelmap resource to be used within a \***GX_ICON** _ widget.</span></span> <span data-ttu-id="e9ae7-139">Dla tego przykładu udostępniono kilka ikon z dystrybucją programu GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-139">Several icons are provided with your GUIX Studio distribution that will work fine for this example.</span></span> <span data-ttu-id="e9ae7-140">Rozwiń _*_Pixelmaps_*_ widok zasobów i kliknij przycisk _ \*_Dodaj nowy Pixelmap_\*\*:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-140">Expand your _*_Pixelmaps_*_ Resource View and click the _ *_Add New Pixelmap_*\* button:</span></span>

![Zrzut ekranu przedstawiający przycisk Dodaj nowy Pixelmap.](./media/guix-studio/image74.jpg)

<span data-ttu-id="e9ae7-142">Przejdź do folderu instalacji programu GUIX Studio i w folderze ***./Graphics/Icons** _ wybierz plik o nazwie _*_i_history_lg.png_\*_.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-142">Browse to your GUIX Studio installation folder, and within the ***./graphics/icons** _ folder select the file named _*_i_history_lg.png_\*_.</span></span> <span data-ttu-id="e9ae7-143">Kliknij przycisk _*_Otwórz_*_ , aby dodać ten zasób do projektu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-143">Click _*_Open_*_ to add this resource to your project.</span></span> <span data-ttu-id="e9ae7-144">Element _ *_Pixelmaps_*\* widok zasobów powinien teraz zawierać Podgląd nowo dodanego obrazu ikony:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-144">Your _ *_Pixelmaps_*\* Resource View should now show a preview of the newly added icon image:</span></span>

![Zrzut ekranu przedstawiający Widok zasobów Pixelmaps.](./media/guix-studio/example_add_pixelmap.png)

<span data-ttu-id="e9ae7-146">**Rysunek 10,6**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-146">**Figure 10.6**</span></span>

<span data-ttu-id="e9ae7-147">Nowy zasób obrazu zostanie użyty później w ramach naszego projektu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-147">We will use this new image resource later as part of our UI design.</span></span>

<span data-ttu-id="e9ae7-148">Podobnie jak w przypadku dodawania zasobów Pixelmap, dodamy nowy zasób czcionki do naszego przybornika, aby można było użyć tej czcionki w dalszej części tego projektu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-148">Similar to adding a pixelmap resource, we will add a new font resource to our toolbox so that we can use this font later in our design.</span></span> <span data-ttu-id="e9ae7-149">Rozwiń pozycję ***Fonts** _ widok zasobów i kliknij przycisk _*_Dodaj nową czcionkę_\*_ .</span><span class="sxs-lookup"><span data-stu-id="e9ae7-149">Expand the ***Fonts** _ Resource View and click on the _*_Add New Font_\*_ button.</span></span> <span data-ttu-id="e9ae7-150">Ta akcja spowoduje wywołanie okna dialogowego _*_Dodawanie/edytowanie_*_ czcionki.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-150">This action will invoke the _*_Add/Edit_*_ font dialog.</span></span> <span data-ttu-id="e9ae7-151">Następnie przejdź do dostarczonych czcionek GUIX w folderze instalacyjnym programu GUIX Studio _\*_ . \\ czcionki \\ verasans_ *_ i wybierz plik czcionek TrueType o nazwie _*_VeraIt. ttf_*_. Wpisz Font nazwa czcionki "_*_MEDIUM_ITALIC_*_" w polu Nazwa czcionki i wpisz "_*_30_\* \*" w polu height.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-151">Next, browse to the supplied GUIX fonts in the GUIX Studio installation folder, _\*_.\\fonts\\verasans_ *_, and select the TrueType font file named _*_VeraIt.ttf_*_. Type font the font name "_*_MEDIUM_ITALIC_*_" in the font name field, and type "_*_30_\*\*" in the height field.</span></span> <span data-ttu-id="e9ae7-152">Okno dialogowe powinno teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-152">Your dialog should now look like this:</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Edycja czcionki.](./media/guix-studio/example_add_font.png)

<span data-ttu-id="e9ae7-154">**Rysunek 10,7**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-154">**Figure 10.7**</span></span>

<span data-ttu-id="e9ae7-155">Kliknij przycisk ***OK*** , aby dodać tę czcionkę do projektu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-155">Click ***OK*** to add this font to your project.</span></span> <span data-ttu-id="e9ae7-156">Teraz powinna zostać wyświetlona Czcionka w Widok zasobów:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-156">You should now see the font in your Resource View:</span></span>

![Zrzut ekranu przedstawiający czcionki w Widok zasobów.](./media/guix-studio/example_font_added.png)

<span data-ttu-id="e9ae7-158">**Rysunek 10,8**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-158">**Figure 10.8**</span></span>

<span data-ttu-id="e9ae7-159">Będziemy używać nowej czcionki później w naszym projekcie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-159">We will use this new font later in our UI design.</span></span>

<span data-ttu-id="e9ae7-160">Teraz, gdy dostępne są nowe zasoby, musimy dodać do naszego ekranu elementy widgetowe, które mogą korzystać z tych zasobów.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-160">Now that we have some new resources available, we need to add some child widgets to our screen that can utilize these resources.</span></span> <span data-ttu-id="e9ae7-161">Wybierz wcześniej utworzone okno o nazwie "\***hello_world** _", klikając prawym przyciskiem myszy okno w widoku docelowym.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-161">Select the previously created window named "\***hello_world** _" by right-clicking on the window in the Target View.</span></span> <span data-ttu-id="e9ae7-162">W wyświetlonym menu podręcznym wybierz polecenie menu _*_Wstaw, tekst, Monituj,_*_ aby wstawić nowy _ *_GX_PROMPT_*\* widżet i dołączyć widżet do okna tła.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-162">In the pop-up menu that is now displayed, select the menu command _*_Insert, Text, Prompt_*_ to insert a new _ *_GX_PROMPT_*\* widget and attach the widget to the background window.</span></span> <span data-ttu-id="e9ae7-163">Okno powinno teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-163">Your window should now look like this:</span></span>

![Zrzut ekranu przedstawiający menu podręczne z wybranym monitem](./media/guix-studio/image78.jpg)

<span data-ttu-id="e9ae7-165">**Rysunek 10,9**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-165">**Figure 10.9**</span></span>

<span data-ttu-id="e9ae7-166">Kliknij czcionkę o nazwie "***MEDIUM_ITALIC** _" w polu _ *_fonts_** widok zasobów i przeciągnij czcionkę i upuść ją w widżecie monit.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-166">Click on the font named "***MEDIUM_ITALIC** _" in the _ *_Fonts_** Resource View, and drag and drop the font on the prompt widget.</span></span> <span data-ttu-id="e9ae7-167">Następnie Edytuj właściwości monitu, jak pokazano na rysunku 10,10 Aby zmienić rozmiar monitu, ustaw przezroczystość monitu i Zmień tekst i styl monitu:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-167">Next, edit the prompt properties as shown in figure 10.10 to resize the prompt, set the prompt transparency, and change the prompt text and style:</span></span>

![Zrzut ekranu przedstawiający widok właściwości dla monitu.](./media/guix-studio/image79.jpg)

<span data-ttu-id="e9ae7-169">**Rysunek 10,10**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-169">**Figure 10.10**</span></span>

<span data-ttu-id="e9ae7-170">Może być konieczne przewinięcie w pionie w widoku właściwości, aby zobaczyć wszystkie te ustawienia w zależności od rozdzielczości ekranu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-170">You may need to scroll vertically in the Properties View to see each of these settings depending on your screen resolution.</span></span> <span data-ttu-id="e9ae7-171">Po wprowadzeniu tych zmian widok docelowy powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-171">After making these changes, your Target View should now look like this:</span></span>

![Zrzut ekranu przedstawiający menu podręczne z zaznaczonym Hello world.](./media/guix-studio/image80.jpg)

<span data-ttu-id="e9ae7-173">**Rysunek 10,11**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-173">**Figure 10.11**</span></span>

<span data-ttu-id="e9ae7-174">Następnie umieścimy widżet styl przycisku ikony na ekranie.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-174">Next we will place an Icon Button style widget on the screen.</span></span> <span data-ttu-id="e9ae7-175">Zaznacz okno tła, klikając je, a następnie użyj menu najwyższego poziomu lub menu podręcznego kliknij prawym przyciskiem myszy, aby wybrać pozycję ***Wstaw, przycisk, przycisk ikony** _, aby dodać nową _*_GX_ICON_BUTTON_\*_ do okna.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-175">Select the background window by clicking on it, and use either the top-level menu or the right-click pop-up menu to select ***Insert, Button, Icon Button** _ to add a new _*_GX_ICON_BUTTON_\*_ to the window.</span></span> <span data-ttu-id="e9ae7-176">Kliknij ikonę o nazwie _ \*_I_HISTORY_LG_\*\*, która została dodana wcześniej i przeciągnij ją na przycisk ikony.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-176">Click on the Icon named _ *_I_HISTORY_LG_*\* that we added earlier and drag it to the icon button.</span></span> <span data-ttu-id="e9ae7-177">Korzystając z widoku właściwości, Dostosuj położenie i rozmiar ikony, tak jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-177">Using the properties view, adjust the icon position and size as show below:</span></span>

![Zrzut ekranu przedstawiający widok Właściwości widżet stylu przycisku ikony.](./media/guix-studio/image81.jpg)

<span data-ttu-id="e9ae7-179">**Rysunek 10,12**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-179">**Figure 10.12**</span></span>

<span data-ttu-id="e9ae7-180">Ekran powinien teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-180">Your screen should now look like this:</span></span>

![Zrzut ekranu przedstawiający menu podręczne z ikoną Hello world i Schowka.](./media/guix-studio/image82.jpg)

<span data-ttu-id="e9ae7-182">**Rysunek 10,13**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-182">**Figure 10.13**</span></span>

<span data-ttu-id="e9ae7-183">Zostanie to wykonane dla prostego przykładowego projektu ekranu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-183">We will call this complete for the simple example screen design.</span></span> <span data-ttu-id="e9ae7-184">Rzeczywiste ekrany aplikacji prawdopodobnie będą znacznie bardziej zaawansowane, ale wystarczy, aby zobaczyć, jak używać programu GUIX Studio do tworzenia własnych ekranów aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-184">Your actual application screens will likely be much more sophisticated, but this is enough to show you how to use GUIX Studio to create your own application screens.</span></span>

## <a name="generate-resource-and-application-code"></a><span data-ttu-id="e9ae7-185">Generowanie kodu zasobu i aplikacji</span><span class="sxs-lookup"><span data-stu-id="e9ae7-185">Generate Resource and Application Code</span></span>

<span data-ttu-id="e9ae7-186">Następnym krokiem jest utworzenie pliku zasobów i pliku specyfikacji, który definiuje osadzony interfejs użytkownika czasu wykonywania GUIX.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-186">The next step is to generate the resource file and specification file that define the embedded GUIX run-time UI.</span></span> <span data-ttu-id="e9ae7-187">Aby wygenerować pliki wyjściowe, należy kliknąć prawym przyciskiem myszy węzeł \***main_display** _ w widoku projektu i wybrać polecenie _ \*_Generuj pliki zasobów_\*\*.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-187">To generate your output files you will need right-click on the ***main_display** _ node in the Project View, and select the _ *_Generate Resource Files_** command.</span></span> <span data-ttu-id="e9ae7-188">Zobaczysz okno informacji wskazujące pliki zasobów, które zostały wygenerowane, jak pokazano na rysunku 10,14:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-188">You will observe an information window that indicates your resource files have been generated, as shown in figure 10.14:</span></span>

![Zrzut ekranu okna dialogowego powiadomienia.](./media/guix-studio/image83.jpg)

<span data-ttu-id="e9ae7-190">**Rysunek 10,14**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-190">**Figure 10.14**</span></span>

<span data-ttu-id="e9ae7-191">Kliknij przycisk \***OK**, aby odrzucić to powiadomienie, i Użyj tej samej procedury, aby kliknąć prawym przyciskiem myszy węzeł _*_main_display_*_ i wybierz polecenie _ \*_Generuj pliki specyfikacji_\*\*.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-191">Click ***OK** _ to dismiss this notification, and use the same procedure to right-click on the _*_main_display_*_ node and select the _ *_Generate Specification Files_** command.</span></span> <span data-ttu-id="e9ae7-192">Należy obserwować podobne okno powiadomień.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-192">You should observe a similar notification window.</span></span> <span data-ttu-id="e9ae7-193">Pliki prostej aplikacji interfejsu użytkownika zostały już wygenerowane.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-193">You have now generated your simple UI application files.</span></span>

## <a name="create-user-supplied-code"></a><span data-ttu-id="e9ae7-194">Utwórz kod dostarczony przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="e9ae7-194">Create User Supplied Code</span></span>

<span data-ttu-id="e9ae7-195">Następnym krokiem jest utworzenie własnego pliku aplikacji, który wywoła projekt ekranu wygenerowany przez program GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-195">The next step is to create your own application file that will invoke the GUIX Studio-generated screen design.</span></span> <span data-ttu-id="e9ae7-196">Korzystając z preferowanego edytora, Utwórz plik źródłowy o nazwie ***new_example. c*** i wprowadź następujący kod źródłowy do tego pliku:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-196">Using your preferred editor, create a source file named ***new_example.c***, and enter the following source code into this file:</span></span>

```C

/* This is an example of the GUIX graphics framework in Win32. */
/* Include system files. */

#include <stdio.h>
#include "tx_api.h"
#include "gx_api.h"

/* Include GUIX resource and specification files for example. */

#include "new_example_resources.h"
#include "new_example_specifications.h"

/* Define the new example thread control block and stack. */

TX_THREAD new_example_thread;
UCHAR new_example_thread_stack[4096];

/* Define the root window pointer. */

GX_WINDOW_ROOT *root_window;

/* Define function prototypes. */

VOID new_example_thread_entry(ULONG thread_input);
UINT win32_graphics_driver_setup_24bpp(GX_DISPLAY *display);

int main()
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter();
    return(0);
}

VOID tx_application_define(void *first_unused_memory)
{
    /* Create the new example thread. */
    tx_thread_create(&new_example_thread, "GUIX New Example Thread", 
                      new_example_thread_entry, 0, 
                      new_example_thread_stack, sizeof(new_example_thread_stack),
                      1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);
}

VOID new_example_thread_entry(ULONG thread_input)
{

    /* Initialize the GUIX library */
    gx_system_initialize();

    /* Configure the main display. */
    gx_studio_display_configure(MAIN_DISPLAY,                      /* Display to configure*/
                                win32_graphics_driver_setup_24bpp, /* Driver to use */
                                LANGUAGE_ENGLISH,                  /* Language to install */
                                MAIN_DISPLAY_DEFAULT_THEME,        /* Theme to install */
                                &root_window);                     /* Root window pointer */

    /* Create the screen - attached to root window. */

    gx_studio_named_widget_create("hello_world", (GX_WIDGET *) root_window, GX_NULL);

    /* Show the root window to make it visible. */
    gx_widget_show(root_window);

    /* Let GUIX run. */
    gx_system_start();

}
```

<span data-ttu-id="e9ae7-197">Powyższy kod źródłowy tworzy typowy wątek ThreadX o nazwie `GUIX New Example Thread` o rozmiarze 4 KB.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-197">The source code above creates a typical ThreadX thread named `GUIX New Example Thread` with a stack size of 4K bytes.</span></span> <span data-ttu-id="e9ae7-198">Interesujące zadania zaczynają się w funkcji o nazwie ***new_example_thread_entry***.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-198">The interesting work begins in the function named ***new_example_thread_entry***.</span></span> <span data-ttu-id="e9ae7-199">Ta funkcja to miejsce, w którym rozpoczyna się GUIX określony wątek.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-199">This function is where the GUIX specific thread begins to run.</span></span>

<span data-ttu-id="e9ae7-200">Pierwsze wywołanie jest funkcją o nazwie ***gx_system_initialize***.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-200">The first call is to the function named ***gx_system_initialize***.</span></span> <span data-ttu-id="e9ae7-201">To wywołanie jest zawsze wymagane, zanim inne interfejsy API GUIX są wywoływane w celu przygotowania biblioteki GUIX do pierwszego użycia.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-201">This call is always required before any other GUIX APIs are invoked to prepare the GUIX library for first use.</span></span>

<span data-ttu-id="e9ae7-202">Następnie przykład wywołuje funkcję ***gx_studio_display_configure***.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-202">Next, the example calls the function ***gx_studio_display_configure***.</span></span> <span data-ttu-id="e9ae7-203">Ta funkcja tworzy wystąpienie wyświetlania GUIX, instaluje żądany język tabeli ciągów aplikacji, instaluje żądany motyw z zasobów wyświetlanych i zwraca wskaźnik do głównego okna, które zostało utworzone dla tego ekranu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-203">This function creates the GUIX display instance, installs the requested language of the application string table, installs the requested theme from the display resources, and returns a pointer to the root window that has been created for this display.</span></span> <span data-ttu-id="e9ae7-204">Główne okno służy jako element nadrzędny wszystkich ekranów najwyższego poziomu, które będą wyświetlane w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-204">The root window is used as the parent of all top-level screens that our application will display.</span></span>

<span data-ttu-id="e9ae7-205">Kolejne przykładowe wywołania \***gx_studio_named_widget_create** _ w celu utworzenia wystąpienia naszego ekranu _ \*_hello_world_\*\*.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-205">Next the example calls ***gx_studio_named_widget_create** _ to create an instance of our _ *_hello_world_** screen.</span></span> <span data-ttu-id="e9ae7-206">Ta funkcja korzysta ze struktur danych i zasobów wytwarzanych przez program GUIX Studio, aby utworzyć wystąpienie ekranu, zgodnie z definicją.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-206">This function uses the data structures and resource produces by GUIX Studio to create an instance of the screen as we have defined it.</span></span> <span data-ttu-id="e9ae7-207">Przekazujemy wskaźnik głównego okna jako drugi parametr do tego wywołania funkcji, co oznacza, że ekran ma być natychmiast dołączony do okna głównego.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-207">We pass the root window pointer as the second parameter to this function call, meaning we want the screen to be immediately attached to the root window.</span></span> <span data-ttu-id="e9ae7-208">Ostatni parametr jest opcjonalnym wskaźnikiem powrotu, którego można użyć, jeśli chcemy zachować wskaźnik do tworzonego ekranu.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-208">The last parameter is an optional return pointer that can be used if we want to keep a pointer to the created screen.</span></span>

<span data-ttu-id="e9ae7-209">Następny \***gx_widget_show** _ jest wywoływany, co sprawia, że główne okno i wszystkie jego elementy podrzędne, w tym ekran _ \*_hello_world_\*\*, widoczne.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-209">Next ***gx_widget_show** _ is called, which makes the root window and all of its children, including the _ *_hello_world_** screen, visible.</span></span>

<span data-ttu-id="e9ae7-210">Na koniec przykład wywołuje ***gx_system_start***.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-210">Finally, the example calls ***gx_system_start***.</span></span> <span data-ttu-id="e9ae7-211">Ta funkcja rozpoczyna wykonywanie pętli przetwarzania zdarzeń systemu GUIX.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-211">This function begins executing the GUIX system event processing loop.</span></span>

## <a name="build-and-run-the-example"></a><span data-ttu-id="e9ae7-212">Kompiluj i uruchamiaj przykład</span><span class="sxs-lookup"><span data-stu-id="e9ae7-212">Build and Run the Example</span></span>

<span data-ttu-id="e9ae7-213">Kompilowanie i uruchamianie przykładu jest specyficzne dla narzędzi i środowiska kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-213">Building and running the example is specific to your build tools and environment.</span></span> <span data-ttu-id="e9ae7-214">Można jednak zdefiniować ogólny proces:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-214">However we can define the general process:</span></span>

1. <span data-ttu-id="e9ae7-215">Tworzenie nowego katalogu i projektu aplikacji</span><span class="sxs-lookup"><span data-stu-id="e9ae7-215">Create a new directory and application project</span></span>
1. <span data-ttu-id="e9ae7-216">Dodaj te pliki do projektu:</span><span class="sxs-lookup"><span data-stu-id="e9ae7-216">Add these files to the project:</span></span>

    <span data-ttu-id="e9ae7-217">**new_example_resources. c**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-217">**new_example_resources.c**</span></span>

    <span data-ttu-id="e9ae7-218">**new_example_specification. c**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-218">**new_example_specification.c**</span></span>

    <span data-ttu-id="e9ae7-219">**new_example. c**</span><span class="sxs-lookup"><span data-stu-id="e9ae7-219">**new_example.c**</span></span>

1. <span data-ttu-id="e9ae7-220">Dodaj pliki obsługi środowiska uruchomieniowego Win32 ze ścieżki instalacji programu GUIX Studio ***./win32_runtime***.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-220">Add the Win32 run-time support files from the GUIX Studio installation path ***./win32_runtime***.</span></span> <span data-ttu-id="e9ae7-221">Obejmuje to nagłówek Win32 i pliki bibliotek uruchomieniowych ThreadX i GUIX.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-221">This includes the ThreadX and GUIX Win32 header and run-time library files.</span></span>
1. <span data-ttu-id="e9ae7-222">Dodawanie biblioteki Win32 GUIX (***GX. lib***) do projektu</span><span class="sxs-lookup"><span data-stu-id="e9ae7-222">Add the GUIX Win32 library (***gx.lib***) to the project</span></span>
1. <span data-ttu-id="e9ae7-223">Dodawanie biblioteki Win32 ThreadX (***TX. lib***) do projektu</span><span class="sxs-lookup"><span data-stu-id="e9ae7-223">Add the ThreadX Win32 library (***tx.lib***) to the project</span></span>
1. <span data-ttu-id="e9ae7-224">Kompiluj, łącz i uruchamiaj aplikację.</span><span class="sxs-lookup"><span data-stu-id="e9ae7-224">Compile, Link, and Run the application!</span></span>
