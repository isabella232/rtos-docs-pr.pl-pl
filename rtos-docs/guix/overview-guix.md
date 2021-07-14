---
title: Opis Azure RTOS GUIX i Azure RTOS GUIX Studio
description: Azure RTOS GUIX to profesjonalny pakiet, który spełnia potrzeby deweloperów systemów osadzonych.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a6ac2c7a76893d516b9beae9b893c9764de60ba
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754934"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="248da-103">Omówienie graficznego Azure RTOS GUIX i Azure RTOS GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="248da-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="248da-104">Osadzony interfejs GUIX platformy Azure to zaawansowane rozwiązanie z graficznym interfejsem użytkownika klasy przemysłowej firmy Microsoft zaprojektowane specjalnie z myślą o aplikacjach z głębokiego osadzoną platformą, w czasie rzeczywistym i aplikacjach IoT.</span><span class="sxs-lookup"><span data-stu-id="248da-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="248da-105">Firma Microsoft udostępnia również w pełni funkcjonalne narzędzie do projektowania aplikacji klasycznych WYSIWYG o nazwie Azure RTOS GUIX Studio, które umożliwia deweloperom projektowanie graficznego interfejsu użytkownika na pulpicie i generowanie osadzonego kodu graficznego graficznego interfejsu użytkownika AZURE RTOS GUIX, który można następnie wyeksportować do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="248da-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="248da-106">Azure RTOS GUIX jest w pełni zintegrowany z systemem Azure RTOS ThreadX RTOS i jest dostępny dla wielu tych samych procesorów obsługiwanych przez Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="248da-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="248da-107">Wszystko to w połączeniu z bardzo małym zużyciem pamięci, szybkim wykonywaniem i doskonałą łatwością użycia sprawia, że narzędzie Azure RTOS GUIX jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT wymagających interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="248da-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="248da-108">Azure RTOS GUIX API</span><span class="sxs-lookup"><span data-stu-id="248da-108">Azure RTOS GUIX API</span></span>

### <a name="powerful-apis"></a><span data-ttu-id="248da-109">Zaawansowane interfejsy API</span><span class="sxs-lookup"><span data-stu-id="248da-109">Powerful APIs</span></span>

* <span data-ttu-id="248da-110">Pełna obsługa bezpośredniego rysowania kanwy w razie potrzeby</span><span class="sxs-lookup"><span data-stu-id="248da-110">Full support for direct canvas drawing when needed</span></span>
* <span data-ttu-id="248da-111">Prosta w interakcji Azure RTOS wygenerowanym kodem GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="248da-111">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>
* <span data-ttu-id="248da-112">Interfejsy API dla linii, prostokąta, wielokąta itp.</span><span class="sxs-lookup"><span data-stu-id="248da-112">APIs for line, rectangle, polygon, etc.</span></span>
* <span data-ttu-id="248da-113">Interfejsy API dla okręgu, łuku, koła, rąbka, wielokropka itp.</span><span class="sxs-lookup"><span data-stu-id="248da-113">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>
* <span data-ttu-id="248da-114">Interfejsy API do rysowania i pozycjonowania tekstu</span><span class="sxs-lookup"><span data-stu-id="248da-114">APIs for text drawing and positioning</span></span>
* <span data-ttu-id="248da-115">Anty aliasy, wypełnienia tekstury i wypełnienia pełne</span><span class="sxs-lookup"><span data-stu-id="248da-115">Anti-aliasing, texture fills, and solid fills</span></span>
* <span data-ttu-id="248da-116">Interfejsy API do tworzenia i modyfikacji ekranów i widżetów</span><span class="sxs-lookup"><span data-stu-id="248da-116">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="248da-117">Azure RTOS plików generowanych przez program GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="248da-117">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="248da-118">Automatycznie generowane pliki źródłowe ANSI C</span><span class="sxs-lookup"><span data-stu-id="248da-118">Automatically generated ANSI C source files</span></span>
* <span data-ttu-id="248da-119">Odizoluje oprogramowanie aplikacji od szczegółów układu</span><span class="sxs-lookup"><span data-stu-id="248da-119">Insulates application software from layout details</span></span>
* <span data-ttu-id="248da-120">Zawiera czcionki i obrazy wymagane przez projekt interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="248da-120">Includes fonts and images required by UI design</span></span>
* <span data-ttu-id="248da-121">Wygenerowane pliki skompilowane przy użyciu kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="248da-121">Generated files compiled with application code</span></span>
* <span data-ttu-id="248da-122">Układ ekranu można aktualizować bez wpływu na logikę aplikacji</span><span class="sxs-lookup"><span data-stu-id="248da-122">Screen layout can be updated without affecting application logic</span></span>
* <span data-ttu-id="248da-123">Identyfikatory zasobów tworzą niezależność języka i motywu</span><span class="sxs-lookup"><span data-stu-id="248da-123">Resource IDs create language and theme independence</span></span>
* <span data-ttu-id="248da-124">Niestandardowe funkcje rysowania i przetwarzania zdarzeń dostarczone przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="248da-124">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="248da-125">Biblioteka widżetów</span><span class="sxs-lookup"><span data-stu-id="248da-125">Widget library</span></span>

* <span data-ttu-id="248da-126">Wstępnie zdefiniowany, ale dostosowywalny zestaw wspólnych elementów interfejsu</span><span class="sxs-lookup"><span data-stu-id="248da-126">Pre-defined but customizable set of common interface elements</span></span>
* <span data-ttu-id="248da-127">Bardzo mała, kompaktowa i wydajna</span><span class="sxs-lookup"><span data-stu-id="248da-127">Extremely small, compact, and efficient</span></span>
* <span data-ttu-id="248da-128">Biblioteka zawiera przycisk, miernik, listę, okno, przewijanie, suwak, pasek postępu, monit i wiele innych</span><span class="sxs-lookup"><span data-stu-id="248da-128">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>
* <span data-ttu-id="248da-129">W pełni dostosowywalny rysunek i wygląd</span><span class="sxs-lookup"><span data-stu-id="248da-129">Fully customizable drawing and appearance</span></span>
* <span data-ttu-id="248da-130">W pełni dostosowywalne działanie i obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="248da-130">Fully customizable operation and event handling</span></span>
* <span data-ttu-id="248da-131">Tylko używane widżety są połączone z oprogramowaniem aplikacji</span><span class="sxs-lookup"><span data-stu-id="248da-131">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="248da-132">Obliczenia matematyczne i narzędzia</span><span class="sxs-lookup"><span data-stu-id="248da-132">Math and utilities</span></span>

* <span data-ttu-id="248da-133">Funkcje dla sin, cos, arcsin, arccos, tangens, square root</span><span class="sxs-lookup"><span data-stu-id="248da-133">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>
* <span data-ttu-id="248da-134">Funkcje do manipulowania regionami ekranu</span><span class="sxs-lookup"><span data-stu-id="248da-134">Functions for manipulating screen regions</span></span>
* <span data-ttu-id="248da-135">Konfiguracja i uruchamianie systemu</span><span class="sxs-lookup"><span data-stu-id="248da-135">System configuration and startup</span></span>
* <span data-ttu-id="248da-136">Definicja puli pamięci (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="248da-136">Memory pool definition (optional)</span></span>
* <span data-ttu-id="248da-137">Zarządzanie czasomierzem</span><span class="sxs-lookup"><span data-stu-id="248da-137">Timer Management</span></span>
* <span data-ttu-id="248da-138">Zarządzanie animacjami</span><span class="sxs-lookup"><span data-stu-id="248da-138">Animation Management</span></span>
* <span data-ttu-id="248da-139">Konserwacja zanieczyszczonej listy</span><span class="sxs-lookup"><span data-stu-id="248da-139">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="248da-140">Przetwarzanie obrazów</span><span class="sxs-lookup"><span data-stu-id="248da-140">Image processing</span></span>

* <span data-ttu-id="248da-141">Funkcje dekodowania obrazów JPEG i PNG w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="248da-141">Functions for runtime decode of jpeg and png images</span></span>
* <span data-ttu-id="248da-142">Stosowanie ditheringu i konwersji przestrzeni kolorów</span><span class="sxs-lookup"><span data-stu-id="248da-142">Apply dithering and color space conversion</span></span>
* <span data-ttu-id="248da-143">Obracanie obrazów</span><span class="sxs-lookup"><span data-stu-id="248da-143">Image rotation</span></span>
* <span data-ttu-id="248da-144">Skalowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="248da-144">Image scaling</span></span>
* <span data-ttu-id="248da-145">Łączenie obrazów</span><span class="sxs-lookup"><span data-stu-id="248da-145">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="248da-146">Przetwarzanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="248da-146">Event processing</span></span>

* <span data-ttu-id="248da-147">Automatycznie wstrzymuje Azure RTOS GUIX, gdy jest w stanie bezczynności</span><span class="sxs-lookup"><span data-stu-id="248da-147">Automatically suspends Azure RTOS GUIX thread when idle</span></span>
* <span data-ttu-id="248da-148">Model programowania sterowanego zdarzeniami popularny w projektowaniu interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="248da-148">Event-driven programming model popular in UI design</span></span>
* <span data-ttu-id="248da-149">Odwłaszcza sterowniki wejściowe Azure RTOS wątku rysowania GUIX</span><span class="sxs-lookup"><span data-stu-id="248da-149">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>
* <span data-ttu-id="248da-150">Funkcje do wysyłania i odbierania zdarzeń</span><span class="sxs-lookup"><span data-stu-id="248da-150">Functions for sending and receiving events</span></span>
* <span data-ttu-id="248da-151">Wstępnie zdefiniowane typy zdarzeń dla wszystkich typów Azure RTOS guix</span><span class="sxs-lookup"><span data-stu-id="248da-151">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>
* <span data-ttu-id="248da-152">Obsługiwane zdarzenia niestandardowe zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="248da-152">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="248da-153">Przetwarzanie kanwy</span><span class="sxs-lookup"><span data-stu-id="248da-153">Canvas processing</span></span>

* <span data-ttu-id="248da-154">Przycinanie i konserwacja w kolejności Z</span><span class="sxs-lookup"><span data-stu-id="248da-154">Clipping and Z-Order maintenance</span></span>
* <span data-ttu-id="248da-155">Odizoluje bibliotekę widżetów od szczegółów sprzętu</span><span class="sxs-lookup"><span data-stu-id="248da-155">Insulates widget library from hardware details</span></span>
* <span data-ttu-id="248da-156">Odizoluje aplikację od szczegółów sprzętu</span><span class="sxs-lookup"><span data-stu-id="248da-156">Insulates application from hardware details</span></span>
* <span data-ttu-id="248da-157">Automatyczne odświeżanie w tle obszarów zanieczyszczonych</span><span class="sxs-lookup"><span data-stu-id="248da-157">Automatic background refresh of dirty areas</span></span>
* <span data-ttu-id="248da-158">Obsługiwane jest wiele kanwy z warstwami i mieszaniem</span><span class="sxs-lookup"><span data-stu-id="248da-158">Multiple canvases with layering and blending supported</span></span>
* <span data-ttu-id="248da-159">Może być wywoływana bezpośrednio przez oprogramowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="248da-159">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="248da-160">Wejściowe sterowników urządzeń</span><span class="sxs-lookup"><span data-stu-id="248da-160">Input device driver(s)</span></span>

* <span data-ttu-id="248da-161">Obsługa specyficzna dla sprzętu, Azure RTOS GRAFICZNEGO interfejsu użytkownika i aplikacji odizolowane od szczegółów sprzętu</span><span class="sxs-lookup"><span data-stu-id="248da-161">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>
* <span data-ttu-id="248da-162">Obsługiwana jest odporność na dotyk, cap Touch i klawiaturę</span><span class="sxs-lookup"><span data-stu-id="248da-162">Resistive Touch, Cap Touch, and keypad supported</span></span>
* <span data-ttu-id="248da-163">Zdarzenia wejściowe przekazywane do Azure RTOS zdarzeń GUIX</span><span class="sxs-lookup"><span data-stu-id="248da-163">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="248da-164">Wyświetlanie sterowników</span><span class="sxs-lookup"><span data-stu-id="248da-164">Display drivers</span></span>

* <span data-ttu-id="248da-165">Obsługa specyficzna dla sprzętu</span><span class="sxs-lookup"><span data-stu-id="248da-165">Hardware-specific support</span></span>
* <span data-ttu-id="248da-166">Sterowniki ogólne dostępne dla wszystkich formatów i głębokości kolorów</span><span class="sxs-lookup"><span data-stu-id="248da-166">Generic drivers provided for all color depth and formats</span></span>
* <span data-ttu-id="248da-167">Dostosowane do korzystania z dostępnych akceleratorów graficznych</span><span class="sxs-lookup"><span data-stu-id="248da-167">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="248da-168">Sprzęt docelowy</span><span class="sxs-lookup"><span data-stu-id="248da-168">Target hardware</span></span>

* <span data-ttu-id="248da-169">Niemal każdy sprzęt z możliwością graficznego wyjścia jest zgodny z graficznym interfejsem użytkownika GUIX</span><span class="sxs-lookup"><span data-stu-id="248da-169">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>
* <span data-ttu-id="248da-170">Obsługiwane są różne ekrany fizyczne</span><span class="sxs-lookup"><span data-stu-id="248da-170">Multiple physical displays supported</span></span>
* <span data-ttu-id="248da-171">Minimalne wymagania dotyczące pamięci RAM i pamięci Flash</span><span class="sxs-lookup"><span data-stu-id="248da-171">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="248da-172">Tworzenie eleganckich interfejsów użytkownika</span><span class="sxs-lookup"><span data-stu-id="248da-172">Create Elegant User Interfaces</span></span>

<span data-ttu-id="248da-173">Azure RTOS GUIX i Azure RTOS GUIX Studio zapewniają wszystkie funkcje niezbędne do tworzenia wyjątkowo eleganckich interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="248da-173">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="248da-174">Standardowy pakiet Azure RTOS GUIX zawiera różne przykładowe interfejsy użytkownika, w tym dokumentację urządzeń medycznych, dokumentację inteligentnych zegarków, dokumentację automatyzacji domu, dokumentację sterowania przemysłowego, informacje o przemyśle samochodowym oraz różne przykłady sprite i animacji.</span><span class="sxs-lookup"><span data-stu-id="248da-174">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="248da-175">Kliknij przykłady referencyjne pokazane poniżej.</span><span class="sxs-lookup"><span data-stu-id="248da-175">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="248da-176">Home Automation</span><span class="sxs-lookup"><span data-stu-id="248da-176">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="248da-177">Medycznych</span><span class="sxs-lookup"><span data-stu-id="248da-177">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="248da-178">Produkty konsumenckie</span><span class="sxs-lookup"><span data-stu-id="248da-178">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="248da-179">Towary białe</span><span class="sxs-lookup"><span data-stu-id="248da-179">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="248da-180">Motoryzacja</span><span class="sxs-lookup"><span data-stu-id="248da-180">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="248da-181">Przemysłowe</span><span class="sxs-lookup"><span data-stu-id="248da-181">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="248da-182">Każda Azure RTOS GUIX ma odpowiadający Azure RTOS GUIX Studio, który definiuje wszystkie elementy graficzne projektu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="248da-182">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="248da-183">Zmiana projektu odwołania jest łatwa.</span><span class="sxs-lookup"><span data-stu-id="248da-183">Changing a reference design is easy.</span></span> <span data-ttu-id="248da-184">Wystarczy otworzyć odpowiedni projekt AZURE RTOS GUIX, wprowadzić odpowiednie zmiany, zapisać projekt, a następnie wybrać pozycję *Project*.</span><span class="sxs-lookup"><span data-stu-id="248da-184">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="248da-185">Wygeneruj wszystkie pliki wyjściowe, aby wygenerować kod C dla Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="248da-185">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="248da-186">Następnie po prostu ponownie skompilować aplikację docelową i uruchomić ją, aby zaobserwować zmodyfikowany projekt odwołania.</span><span class="sxs-lookup"><span data-stu-id="248da-186">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="guix-memory-footprint"></a><span data-ttu-id="248da-187">GuiX Memory footprint (Zużycie pamięci w graficznym interfejsie użytkownika)</span><span class="sxs-lookup"><span data-stu-id="248da-187">GUIX Memory footprint</span></span>

<span data-ttu-id="248da-188">Azure RTOS GUIX ma znacząco niewielką ilość pamięci RAM 13,2 KB i 4 KB pamięci RAM na potrzeby podstawowej obsługi, bez uwzględnienia pamięci wymaganej dla kanwy.</span><span class="sxs-lookup"><span data-stu-id="248da-188">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="248da-189">W przypadku ekranu z wewnętrzną technologią GRAM i technologią samodzielnego odświeżania nie jest wymagana żadna pamięć kanwy.</span><span class="sxs-lookup"><span data-stu-id="248da-189">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="248da-190">Jednak w celu poprawienia wydajności rysowania lub w przypadku konfiguracji wyświetlania, która nie korzysta z lokalnego programu GRAM na ekranie, aplikacja definiuje obszar pamięci kanwy.</span><span class="sxs-lookup"><span data-stu-id="248da-190">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="248da-191">Wymagania dotyczące pamięci kanwy są funkcją rozmiaru kanwy oraz głębokości koloru i są definiowane przez formułę:</span><span class="sxs-lookup"><span data-stu-id="248da-191">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="248da-192"><i>Pamięć RAM kanwy (w bajtach) = (x \* y \* (bpp/8))</i></span><span class="sxs-lookup"><span data-stu-id="248da-192"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="248da-193">Gdzie "x" i "y" to wymiary kanwy (ekranu).</span><span class="sxs-lookup"><span data-stu-id="248da-193">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="248da-194">Większość aplikacji korzysta również z zasobów graficznych, które nie są uwzględnione w podstawowych wymaganiach Azure RTOS magazynu biblioteki GUIX.</span><span class="sxs-lookup"><span data-stu-id="248da-194">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="248da-195">Te zasoby obejmują czcionki, ikony graficzne (mapy pikseli) i ciągi statyczne.</span><span class="sxs-lookup"><span data-stu-id="248da-195">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="248da-196">Te dane mogą być przechowywane w sekcji pamięci const (tj. flash).</span><span class="sxs-lookup"><span data-stu-id="248da-196">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="248da-197">Rozmiar tego obszaru pamięci zależy od wielu czynników, takich jak liczba i rozmiar użytych unikatowych czcionek, liczba i rozmiar używanych ikon graficznych, format koloru danych wyjściowych oraz to, czy każdy zasób używa skompresowanych danych, ponieważ interfejs GUIX programu Azure RTOS obsługuje kompresję RLE danych czcionek i map pikseli.</span><span class="sxs-lookup"><span data-stu-id="248da-197">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="248da-198">Wymagania dotyczące magazynu dla każdego zasobu są wyświetlane w aplikacji Azure RTOS GUIX Studio, dzięki czemu użytkownik może śledzić i monitorować ilość pamięci flash, która będzie zużywana przez zasoby aplikacji.</span><span class="sxs-lookup"><span data-stu-id="248da-198">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="248da-199">Podobnie Azure RTOS ThreadX, rozmiar Azure RTOS GUIX jest automatycznie skalowany na podstawie usług faktycznie używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="248da-199">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="248da-200">W ten sposób praktycznie nie ma potrzeby skomplikowanej konfiguracji i parametrów kompilacji, co ułatwia deweloperom pracę.</span><span class="sxs-lookup"><span data-stu-id="248da-200">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="248da-201">Proste, łatwe w użyciu</span><span class="sxs-lookup"><span data-stu-id="248da-201">Simple, easy-to-use</span></span>

<span data-ttu-id="248da-202">Azure RTOS GUIX jest bardzo prosty w użyciu, Azure RTOS program GUIX Studio jeszcze bardziej ułatwia deweloperom wizualne projektowanie na pulpicie i generowanie kodu C, który działa w rzeczywistym celu.</span><span class="sxs-lookup"><span data-stu-id="248da-202">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="248da-203">Aplikacje mogą następnie dodawać własne niestandardowe funkcje obsługi zdarzeń i rysowania, aby ukończyć graficzny interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="248da-203">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="248da-204">Korzystanie z interfejsu AZURE RTOS GUIX jest proste.</span><span class="sxs-lookup"><span data-stu-id="248da-204">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="248da-205">Interfejs AZURE RTOS GUIX jest intuicyjny i wysoce funkcjonalny.</span><span class="sxs-lookup"><span data-stu-id="248da-205">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="248da-206">Nazwy interfejsu API składa się z rzeczywistych słów, a nie "alfabetu" i/lub wysoce skróconych nazw, które są tak popularne w innych produktach systemu plików.</span><span class="sxs-lookup"><span data-stu-id="248da-206">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="248da-207">Wszystkie Azure RTOS GUIX mają wiodący *gx_* i są zgodne z konwencją nazewnictwa rzeczowników.</span><span class="sxs-lookup"><span data-stu-id="248da-207">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="248da-208">Ponadto w interfejsie API istnieje spójność funkcjonalna.</span><span class="sxs-lookup"><span data-stu-id="248da-208">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="248da-209">Na przykład wszystkie interfejsy API, które inicjują blok sterowania widżetu, mają nazwy widget_type _create, a parametry funkcji tworzenia dla każdego typu widżetu są zawsze zdefiniowane w tej &lt; &gt; samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="248da-209">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="248da-210">Kompleksowy zestaw wbudowanych widżetów</span><span class="sxs-lookup"><span data-stu-id="248da-210">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="248da-211">Azure RTOS GUIX udostępnia bogaty zestaw wbudowanych widżetów, w tym:</span><span class="sxs-lookup"><span data-stu-id="248da-211">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>
* <span data-ttu-id="248da-212">Accordion Menu</span><span class="sxs-lookup"><span data-stu-id="248da-212">Accordion Menu</span></span>
* <span data-ttu-id="248da-213">Przycisk</span><span class="sxs-lookup"><span data-stu-id="248da-213">Button</span></span>
* <span data-ttu-id="248da-214">Pole wyboru</span><span class="sxs-lookup"><span data-stu-id="248da-214">Checkbox</span></span>
* <span data-ttu-id="248da-215">Okrągły miernik</span><span class="sxs-lookup"><span data-stu-id="248da-215">Circular Gauge</span></span>
* <span data-ttu-id="248da-216">Lista rozwijana</span><span class="sxs-lookup"><span data-stu-id="248da-216">Drop Down List</span></span>
* <span data-ttu-id="248da-217">Lista pozioma</span><span class="sxs-lookup"><span data-stu-id="248da-217">Horizontal List</span></span>
* <span data-ttu-id="248da-218">Poziome okno paska przewijania</span><span class="sxs-lookup"><span data-stu-id="248da-218">Horizontal Scrollbar Window</span></span>
* <span data-ttu-id="248da-219">Ikona</span><span class="sxs-lookup"><span data-stu-id="248da-219">Icon</span></span>
* <span data-ttu-id="248da-220">Przycisk ikony</span><span class="sxs-lookup"><span data-stu-id="248da-220">Icon Button</span></span>
* <span data-ttu-id="248da-221">Wykres liniowy</span><span class="sxs-lookup"><span data-stu-id="248da-221">Line Chart</span></span>
* <span data-ttu-id="248da-222">Menu</span><span class="sxs-lookup"><span data-stu-id="248da-222">Menu</span></span>
* <span data-ttu-id="248da-223">Przycisk tekstowy z wieloma wierszami</span><span class="sxs-lookup"><span data-stu-id="248da-223">Multi Line Text Button</span></span>
* <span data-ttu-id="248da-224">Wprowadzanie tekstu w wielu wierszach</span><span class="sxs-lookup"><span data-stu-id="248da-224">Multi Line Text Input</span></span>
* <span data-ttu-id="248da-225">Widok tekstu wielo wierszowego</span><span class="sxs-lookup"><span data-stu-id="248da-225">Multi Line Text View</span></span>
* <span data-ttu-id="248da-226">Numeric Pixelmap Prompt</span><span class="sxs-lookup"><span data-stu-id="248da-226">Numeric Pixelmap Prompt</span></span>
* <span data-ttu-id="248da-227">Monit liczbowy</span><span class="sxs-lookup"><span data-stu-id="248da-227">Numeric Prompt</span></span>
* <span data-ttu-id="248da-228">Numeryczne kółka przewijania</span><span class="sxs-lookup"><span data-stu-id="248da-228">Numeric Scroll Wheel</span></span>
* <span data-ttu-id="248da-229">Przycisk Pixelmap</span><span class="sxs-lookup"><span data-stu-id="248da-229">Pixelmap Button</span></span>
* <span data-ttu-id="248da-230">Monit o mapowanie pikseli</span><span class="sxs-lookup"><span data-stu-id="248da-230">Pixelmap Prompt</span></span>
* <span data-ttu-id="248da-231">Suwak mapy pikseli</span><span class="sxs-lookup"><span data-stu-id="248da-231">Pixelmap Slider</span></span>
* <span data-ttu-id="248da-232">Sprite mapy pikseli</span><span class="sxs-lookup"><span data-stu-id="248da-232">Pixelmap Sprite</span></span>
* <span data-ttu-id="248da-233">pasek postępu</span><span class="sxs-lookup"><span data-stu-id="248da-233">Progress Bar</span></span>
* <span data-ttu-id="248da-234">Monit</span><span class="sxs-lookup"><span data-stu-id="248da-234">Prompt</span></span>
* <span data-ttu-id="248da-235">Pasek postępu promieniowego</span><span class="sxs-lookup"><span data-stu-id="248da-235">Radial Progress Bar</span></span>
* <span data-ttu-id="248da-236">przycisk radiowy</span><span class="sxs-lookup"><span data-stu-id="248da-236">Radio Button</span></span>
* <span data-ttu-id="248da-237">Kółko</span><span class="sxs-lookup"><span data-stu-id="248da-237">Scroll Wheel</span></span>
* <span data-ttu-id="248da-238">Wprowadzanie tekstu w jednym wierszu</span><span class="sxs-lookup"><span data-stu-id="248da-238">Single Line Text Input</span></span>
* <span data-ttu-id="248da-239">Suwak</span><span class="sxs-lookup"><span data-stu-id="248da-239">Slider</span></span>
* <span data-ttu-id="248da-240">Kółka przewijania ciągów</span><span class="sxs-lookup"><span data-stu-id="248da-240">String Scroll Wheel</span></span>
* <span data-ttu-id="248da-241">Przycisk tekstowy</span><span class="sxs-lookup"><span data-stu-id="248da-241">Text Button</span></span>
* <span data-ttu-id="248da-242">Widok drzewa</span><span class="sxs-lookup"><span data-stu-id="248da-242">Tree View</span></span>
* <span data-ttu-id="248da-243">Lista pionowa</span><span class="sxs-lookup"><span data-stu-id="248da-243">Vertical List</span></span>
* <span data-ttu-id="248da-244">Pionowy pasek przewijania</span><span class="sxs-lookup"><span data-stu-id="248da-244">Vertical Scrollbar</span></span>

<span data-ttu-id="248da-245">Aplikacja może łatwo tworzyć własne widżety klienta.</span><span class="sxs-lookup"><span data-stu-id="248da-245">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="248da-246">Kompletny interfejs API rysowania niskiego poziomu</span><span class="sxs-lookup"><span data-stu-id="248da-246">Complete low-level drawing API</span></span>

<span data-ttu-id="248da-247">Azure RTOS GUIX zapewnia niezawodny interfejs API rysowania kanwy, który umożliwia aplikacji renderowanie złożonych kształtów graficznych.</span><span class="sxs-lookup"><span data-stu-id="248da-247">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="248da-248">Wszystkie funkcje obsługują anty aliasy dla obiektów docelowych o dużej głębokości kolorów, a wszystkie kształty mogą być wypełnione naszym konturem, w tym wypełnieniem wzorca pełnej mapy i mapy pikseli.</span><span class="sxs-lookup"><span data-stu-id="248da-248">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="248da-249">Wszystkie typy pierwotne rysowania obsługują pędzla alpha w przypadku uruchamiania z 16 bpp i większą głębokością koloru.</span><span class="sxs-lookup"><span data-stu-id="248da-249">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="248da-250">Funkcje rysowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="248da-250">Drawing functions include:</span></span>

* <span data-ttu-id="248da-251">Arc Draw</span><span class="sxs-lookup"><span data-stu-id="248da-251">Arc Draw</span></span>
* <span data-ttu-id="248da-252">Rysowanie w okręgu</span><span class="sxs-lookup"><span data-stu-id="248da-252">Circle Draw</span></span>
* <span data-ttu-id="248da-253">Rysowanie liniowe</span><span class="sxs-lookup"><span data-stu-id="248da-253">Line Draw</span></span>
* <span data-ttu-id="248da-254">Rysowanie kołowe</span><span class="sxs-lookup"><span data-stu-id="248da-254">Pie Draw</span></span>
* <span data-ttu-id="248da-255">Pixelmap Blend</span><span class="sxs-lookup"><span data-stu-id="248da-255">Pixelmap Blend</span></span>
* <span data-ttu-id="248da-256">Kafelek pixelmap</span><span class="sxs-lookup"><span data-stu-id="248da-256">Pixelmap Tile</span></span>
* <span data-ttu-id="248da-257">Rysowanie wielokąta</span><span class="sxs-lookup"><span data-stu-id="248da-257">Polygon Draw</span></span>
* <span data-ttu-id="248da-258">Rysowanie tekstu</span><span class="sxs-lookup"><span data-stu-id="248da-258">Text Draw</span></span>
* <span data-ttu-id="248da-259">Chord Draw</span><span class="sxs-lookup"><span data-stu-id="248da-259">Chord Draw</span></span>
* <span data-ttu-id="248da-260">Rysowanie wielokropka</span><span class="sxs-lookup"><span data-stu-id="248da-260">Ellipse Draw</span></span>
* <span data-ttu-id="248da-261">Rysowanie pikseli</span><span class="sxs-lookup"><span data-stu-id="248da-261">Pixel Draw</span></span>
* <span data-ttu-id="248da-262">Rysowanie mapy pikseli</span><span class="sxs-lookup"><span data-stu-id="248da-262">Pixelmap Draw</span></span>
* <span data-ttu-id="248da-263">Obracanie mapy pikseli</span><span class="sxs-lookup"><span data-stu-id="248da-263">Pixelmap Rotate</span></span>
* <span data-ttu-id="248da-264">Rysowanie prostokąta</span><span class="sxs-lookup"><span data-stu-id="248da-264">Rectangle Draw</span></span>
* <span data-ttu-id="248da-265">Text Blend</span><span class="sxs-lookup"><span data-stu-id="248da-265">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="248da-266">Domyślne bezpłatne czcionki i łatwe dodawanie kolejnych</span><span class="sxs-lookup"><span data-stu-id="248da-266">Default free fonts and easy to add more</span></span>

<span data-ttu-id="248da-267">Azure RTOS GUIX udostępnia bezpłatny zestaw czcionek TrueType.</span><span class="sxs-lookup"><span data-stu-id="248da-267">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="248da-268">Deweloperzy mogą dodawać dodatkowe czcionki TrueType zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="248da-268">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="248da-269">Format Azure RTOS GUIX obsługuje anty aliasy 8bpp, anty aliasy 4bpp i czcionki monochromatyczne 1bpp.</span><span class="sxs-lookup"><span data-stu-id="248da-269">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="248da-270">W przypadku aplikacji z ograniczeniami zasobów Azure RTOS GUIX wstępnie renderuje czcionki TrueType do skompresowanego formatu mapy bitowej przy użyciu naszego narzędzia klasycznego GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="248da-270">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="248da-271">Niestandardowa implementacja dekodera JPG i PNG</span><span class="sxs-lookup"><span data-stu-id="248da-271">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="248da-272">Implementacja niestandardowego dekodera JPG i PNG w implementacji dekodera plików JPG i PNG.</span><span class="sxs-lookup"><span data-stu-id="248da-272">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="248da-273">Ta implementacja obsługuje konwersję przestrzeni kolorów, dithering i tworzenie środowiska uruchomieniowego Azure RTOS obrazów w formacie pikseli zgodnych z guix.</span><span class="sxs-lookup"><span data-stu-id="248da-273">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="248da-274">Rozbudowana obsługa ekranu i ekranu dotykowego</span><span class="sxs-lookup"><span data-stu-id="248da-274">Extensive display and touchscreen support</span></span>

<span data-ttu-id="248da-275">Azure RTOS GUIX udostępnia ogólne sterowniki wyświetlania dla niemal wszystkich formatów kolorów, w tym monochromatycznych 1bpp, palety 8 bpp, formatu 8 bpp 3:3:2,</span><span class="sxs-lookup"><span data-stu-id="248da-275">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="248da-276">16 bpp 565 rgb, format 16 bpp 4:4:4:4, 32 format bpp x:r:g:b i 32 bpp a:r:g:b.</span><span class="sxs-lookup"><span data-stu-id="248da-276">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="248da-277">Ponadto Azure RTOS GUIX jest zintegrowany z wieloma najpopularniejszymi kontrolerami i akceleratorami sprzętowym (ST ChromeArt, Renesas Aby itp.).</span><span class="sxs-lookup"><span data-stu-id="248da-277">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="248da-278">Azure RTOS GUIX w pełni obsługuje ekran dotykowy (w tym obsługę gestów), pióra i wirtualnych urządzeń wejściowych klawiatury.</span><span class="sxs-lookup"><span data-stu-id="248da-278">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="248da-279">Azure RTOS GUIX Studio desktop WYSIWYG tool</span><span class="sxs-lookup"><span data-stu-id="248da-279">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="248da-280">Azure RTOS GUIX Studio udostępnia kompletne środowisko projektowe ekranu WYSIWYG, które umożliwia użytkownikowi przeciąganie i upuszczanie elementów graficznych używanych do tworzenia ekranów graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="248da-280">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="248da-281">Azure RTOS GUIX Studio automatycznie generuje kod C zgodny z biblioteką Azure RTOS GUIX, gotowy do skompilowania i uruchomienia na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="248da-281">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="248da-282">Deweloperzy mogą tworzyć wstępnie wyrenderowane czcionki do użycia w aplikacji przy użyciu zintegrowanego Azure RTOS generowania czcionek w programie GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="248da-282">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="248da-283">Czcionki mogą być generowane w formatach monochromatycznych lub anty aliasów i są zoptymalizowane pod kątem oszczędzania miejsca w miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="248da-283">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="248da-284">Czcionki mogą zawierać dowolny zestaw znaków, w tym znaki Unicode dla aplikacji wielojęzycznych.</span><span class="sxs-lookup"><span data-stu-id="248da-284">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="248da-285">Azure RTOS GUIX Studio ułatwia importowanie grafiki z plików PNG lub JPG z konwersją na skompresowane Azure RTOS GUIX Pixelmaps do użycia w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="248da-285">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="248da-286">Wiele typów widżetów Azure RTOS GUIX zaprojektowano w celu uwzględnienia grafiki użytkownika w celu niestandardowego wyglądu i wyglądu.</span><span class="sxs-lookup"><span data-stu-id="248da-286">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="248da-287">Ponadto program Azure RTOS GUIX Studio umożliwia dostosowywanie domyślnych kolorów i stylów rysowania używanych przez widżety GUIX programu Azure RTOS, dzięki czemu deweloperzy mogą bardzo łatwo dostroić wygląd Azure RTOS GUIX.</span><span class="sxs-lookup"><span data-stu-id="248da-287">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="248da-288">Generowanie i konserwacja ciągów aplikacji to kolejna wbudowana Azure RTOS GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="248da-288">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="248da-289">Dzięki temu deweloperzy mogą projektować aplikacje przy użyciu jednego języka do programowania oraz szybko i łatwo dodawać obsługę dodatkowych języków po premierze produktu.</span><span class="sxs-lookup"><span data-stu-id="248da-289">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="248da-290">Kompletną aplikację AZURE RTOS GUIX można wykonać na komputerze stacjonarnym w środowisku programu Azure RTOS GUIX Studio, co umożliwia szybkie i łatwe generowanie oraz demonstrację koncepcji graficznego interfejsu użytkownika, testowanie przepływów ekranu oraz obserwowanie przejść ekranu i animacji.</span><span class="sxs-lookup"><span data-stu-id="248da-290">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="248da-291">Po zakończeniu projekt można wyeksportować jako struktury danych gotowe do użycia w języku C, gotowe do skompilowania i powiązać za pomocą graficznego interfejsu Azure RTOS GUIX i Azure RTOS ThreadX.</span><span class="sxs-lookup"><span data-stu-id="248da-291">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="248da-292">Azure RTOS GUIX i Azure RTOS GUIX Studio obsługują wiele motywów zasobów, dzięki czemu aplikację można łatwo zmienić w czasie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="248da-292">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="248da-293">Czcionki, kolory i mapy pikseli można zmieniać w czasie uruchamiania za pomocą jednego prostego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="248da-293">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="248da-294">Dowiedz się więcej o programie GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="248da-294">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="248da-295">Ukończ symulację win32</span><span class="sxs-lookup"><span data-stu-id="248da-295">Complete Win32 simulation</span></span>

<span data-ttu-id="248da-296">Azure RTOS GUIX działa na komputerze Windows, używając dokładnie tej samej biblioteki rysowania, która jest uruchamiana na tablicy docelowej.</span><span class="sxs-lookup"><span data-stu-id="248da-296">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="248da-297">Za Azure RTOS GUIX można skompilować i uruchomić aplikację z graficznym interfejsem użytkownika na komputerze i użyć tego samego kodu aplikacji w celu debugowania, szybkiego prototypowania, pokazu i docelowej operacji WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="248da-297">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="248da-298">Zaawansowana technologia</span><span class="sxs-lookup"><span data-stu-id="248da-298">Advanced technology</span></span>

* <span data-ttu-id="248da-299">Azure RTOS technologii GUIX obejmują:</span><span class="sxs-lookup"><span data-stu-id="248da-299">Azure RTOS GUIX's advanced technology incorporates:</span></span>
* <span data-ttu-id="248da-300">Łączenie alfa</span><span class="sxs-lookup"><span data-stu-id="248da-300">Alpha blending</span></span>
* <span data-ttu-id="248da-301">Anty aliasy</span><span class="sxs-lookup"><span data-stu-id="248da-301">Anti-Aliasing</span></span>
* <span data-ttu-id="248da-302">Automatyczne skalowanie</span><span class="sxs-lookup"><span data-stu-id="248da-302">Automatic scaling</span></span>
* <span data-ttu-id="248da-303">Kompresja mapy bitowej</span><span class="sxs-lookup"><span data-stu-id="248da-303">Bitmap compression</span></span>
* <span data-ttu-id="248da-304">Łączenie kanwy</span><span class="sxs-lookup"><span data-stu-id="248da-304">Canvas blending</span></span>
* <span data-ttu-id="248da-305">Obsługa widżetów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="248da-305">Custom widget support</span></span>
* <span data-ttu-id="248da-306">Obsługa odroczonego rysowania</span><span class="sxs-lookup"><span data-stu-id="248da-306">Deferred drawing support</span></span>
* <span data-ttu-id="248da-307">Obsługa ditheringu</span><span class="sxs-lookup"><span data-stu-id="248da-307">Dithering support</span></span>
* <span data-ttu-id="248da-308">Programowanie neutralne dla endian</span><span class="sxs-lookup"><span data-stu-id="248da-308">Endian neutral programming</span></span>
* <span data-ttu-id="248da-309">Obsługa akceleratora sprzętowego</span><span class="sxs-lookup"><span data-stu-id="248da-309">Hardware accelerator support</span></span>
* <span data-ttu-id="248da-310">Obsługa wielu języków i kodowanie UTF-8</span><span class="sxs-lookup"><span data-stu-id="248da-310">Multilingual support and UTF-8 encoding</span></span>
* <span data-ttu-id="248da-311">Obsługa wielu ekranów i kanwy</span><span class="sxs-lookup"><span data-stu-id="248da-311">Multiple display and canvas support</span></span>
* <span data-ttu-id="248da-312">Zoptymalizowane przycinanie, rysowanie i obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="248da-312">Optimized clipping, drawing, and event handling</span></span>
* <span data-ttu-id="248da-313">Dekoder PLIKÓW JPEG i PNG środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="248da-313">Runtime JPEG and PNG decoder</span></span>
* <span data-ttu-id="248da-314">Osłanianie i motywy</span><span class="sxs-lookup"><span data-stu-id="248da-314">Skinning and Themes</span></span>
* <span data-ttu-id="248da-315">Obsługuje monochromatyczne za pośrednictwem 32-bitowej wartości true-color w formatach alfagraficznych</span><span class="sxs-lookup"><span data-stu-id="248da-315">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>
* <span data-ttu-id="248da-316">Obsługa przejść, sprite'ów i animacji</span><span class="sxs-lookup"><span data-stu-id="248da-316">Transitions, Sprites, and Animation support</span></span>
* <span data-ttu-id="248da-317">Symulacja Win32</span><span class="sxs-lookup"><span data-stu-id="248da-317">Win32 simulation</span></span>
* <span data-ttu-id="248da-318">Zarządzanie oknami, w tym okienka widoków i konserwacja w kolejności Z</span><span class="sxs-lookup"><span data-stu-id="248da-318">Window management including Viewports and Z-order maintenance</span></span>
