---
title: Informacje o platformie Azure RTO GUIX i platformie Azure RTO GUIX Studio
description: Usługa Azure RTO GUIX to pakiet z jakością profesjonalną, utworzony w celu spełnienia wymagań deweloperów systemów osadzonych.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0d0ff37784673f851ab918e20b255d19ddf98b0f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822998"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a><span data-ttu-id="11d26-103">Omówienie usług Azure RTO GUIX i Azure RTO GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="11d26-103">Overview of Azure RTOS GUIX and Azure RTOS GUIX Studio</span></span>

<span data-ttu-id="11d26-104">Interfejs GUI platformy Azure GUIX Embedded to zaawansowane rozwiązanie klasy korporacyjnej GUI firmy Microsoft zaprojektowane specjalnie pod kątem głęboko osadzonych, w czasie rzeczywistym i IoT.</span><span class="sxs-lookup"><span data-stu-id="11d26-104">Azure GUIX embedded GUI is Microsoft’s advanced, industrial grade GUI solution designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="11d26-105">Firma Microsoft udostępnia również w pełni funkcjonalne narzędzie do projektowania w systemie WYSIWYG o nazwie Azure RTO GUIX Studio, które umożliwia deweloperom projektowanie graficznego interfejsu użytkownika na pulpicie i generowanie kodu graficznego interfejsu GUI platformy Azure RTO GUIX, który można następnie wyeksportować do obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="11d26-105">Microsoft also provides a full-featured WYSIWYG desktop design tool named Azure RTOS GUIX Studio, which allows developers to design their GUI on the desktop and generate Azure RTOS GUIX embedded GUI code that can then be exported to the target.</span></span> <span data-ttu-id="11d26-106">Usługa Azure RTO GUIX jest w pełni zintegrowana z platformą Azure RTO ThreadX RTO i jest dostępna dla wielu procesorów obsługiwanych przez platformę Azure RTO ThreadX.</span><span class="sxs-lookup"><span data-stu-id="11d26-106">Azure RTOS GUIX is fully integrated with Azure RTOS ThreadX RTOS and is available for many of the same processors supported by Azure RTOS ThreadX.</span></span> <span data-ttu-id="11d26-107">Wszystko to w połączeniu z bardzo małym zasięgiem, szybkim wykonaniem i najbardziej łatwym w użyciu, dzięki czemu usługa Azure RTO GUIX idealny wybór dla najbardziej wymagających aplikacji IoT, które wymagają interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11d26-107">All of this combined with an extremely small footprint, fast execution, and superior ease-of-use, make Azure RTOS GUIX the ideal choice for the most demanding embedded IoT applications requiring a user interface.</span></span> 

## <a name="azure-rtos-guix-api"></a><span data-ttu-id="11d26-108">Interfejs API usługi Azure RTO GUIX</span><span class="sxs-lookup"><span data-stu-id="11d26-108">Azure RTOS GUIX API</span></span>

### <a name="intuitive-and-consistent-api"></a><span data-ttu-id="11d26-109">Intuicyjny i spójny interfejs API</span><span class="sxs-lookup"><span data-stu-id="11d26-109">Intuitive and consistent API</span></span>

* <span data-ttu-id="11d26-110">W konwencji nazewnictwa czasowników</span><span class="sxs-lookup"><span data-stu-id="11d26-110">Noun-verb naming convention</span></span>

* <span data-ttu-id="11d26-111">Wszystkie interfejsy API mają wiodące *gx_* do łatwej identyfikacji jako Azure RTO GUIX</span><span class="sxs-lookup"><span data-stu-id="11d26-111">All APIs have leading *gx_* to easily identify as Azure RTOS GUIX</span></span>

* <span data-ttu-id="11d26-112">Model programowania oparty na zdarzeniach (API)</span><span class="sxs-lookup"><span data-stu-id="11d26-112">Event-driven programming model (API)</span></span>

* <span data-ttu-id="11d26-113">Pełna obsługa bezpośredniego rysowania kanwy w razie potrzeby</span><span class="sxs-lookup"><span data-stu-id="11d26-113">Full support for direct canvas drawing when needed</span></span>

* <span data-ttu-id="11d26-114">Prosta do współpracy z wygenerowanym kodem usługi Azure RTO GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="11d26-114">Simple to interact with Azure RTOS GUIX Studio generated code</span></span>

* <span data-ttu-id="11d26-115">Interfejsy API dla linii, prostokątów, wielokątów itp.</span><span class="sxs-lookup"><span data-stu-id="11d26-115">APIs for line, rectangle, polygon, etc.</span></span>

* <span data-ttu-id="11d26-116">Interfejsy API dla okręgu, łuku, koła, skrót, elipsy itp.</span><span class="sxs-lookup"><span data-stu-id="11d26-116">APIs for circle, arc, pie, chord, ellipse, etc.</span></span>

* <span data-ttu-id="11d26-117">Interfejsy API do rysowania i pozycjonowania tekstu</span><span class="sxs-lookup"><span data-stu-id="11d26-117">APIs for text drawing and positioning</span></span>

* <span data-ttu-id="11d26-118">Wygładzanie, wypełnienia tekstury i wypełnienia kryjące</span><span class="sxs-lookup"><span data-stu-id="11d26-118">Anti-aliasing, texture fills, and solid fills</span></span>

* <span data-ttu-id="11d26-119">Interfejsy API do tworzenia i modifing ekranów i widżetów</span><span class="sxs-lookup"><span data-stu-id="11d26-119">APIs for creating and modifing screens and widgets</span></span>

### <a name="azure-rtos-guix-studio-generated-files"></a><span data-ttu-id="11d26-120">Pliki wygenerowane przez usługę Azure RTO GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="11d26-120">Azure RTOS GUIX Studio Generated Files</span></span>

* <span data-ttu-id="11d26-121">Automatycznie wygenerowane pliki źródłowe ANSI C</span><span class="sxs-lookup"><span data-stu-id="11d26-121">Automatically generated ANSI C source files</span></span>

* <span data-ttu-id="11d26-122">Izolowanie oprogramowania aplikacji od szczegółów układu</span><span class="sxs-lookup"><span data-stu-id="11d26-122">Insulates application software from layout details</span></span>

* <span data-ttu-id="11d26-123">Zawiera czcionki i obrazy wymagane przez Projektowanie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="11d26-123">Includes fonts and images required by UI design</span></span>

* <span data-ttu-id="11d26-124">Wygenerowane pliki skompilowane przy użyciu kodu aplikacji</span><span class="sxs-lookup"><span data-stu-id="11d26-124">Generated files compiled with application code</span></span>

* <span data-ttu-id="11d26-125">Układ ekranu można zaktualizować bez wpływu na logikę aplikacji</span><span class="sxs-lookup"><span data-stu-id="11d26-125">Screen layout can be updated without affecting application logic</span></span>

* <span data-ttu-id="11d26-126">Identyfikatory zasobów Utwórz niezależność języka i motywu</span><span class="sxs-lookup"><span data-stu-id="11d26-126">Resource IDs create language and theme independence</span></span>

* <span data-ttu-id="11d26-127">Funkcje niestandardowego rysowania i przetwarzania zdarzeń dostarczone przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="11d26-127">User-supplied custom drawing and event processing functions</span></span>

### <a name="widget-library"></a><span data-ttu-id="11d26-128">Biblioteka widżetów</span><span class="sxs-lookup"><span data-stu-id="11d26-128">Widget library</span></span>

* <span data-ttu-id="11d26-129">Wstępnie zdefiniowany, ale dostosowywalny zestaw wspólnych elementów interfejsu</span><span class="sxs-lookup"><span data-stu-id="11d26-129">Pre-defined but customizable set of common interface elements</span></span>

* <span data-ttu-id="11d26-130">Niezwykle małe, kompaktowe i wydajne</span><span class="sxs-lookup"><span data-stu-id="11d26-130">Extremely small, compact, and efficient</span></span>

* <span data-ttu-id="11d26-131">Biblioteka zawiera przycisk, miernik, listę, okno, przewijanie, suwak, pasek postępu, monit i wiele innych</span><span class="sxs-lookup"><span data-stu-id="11d26-131">Library includes button, gauge, list, window, scroll, slider, progress bar, prompt and many more</span></span>

* <span data-ttu-id="11d26-132">W pełni dostosowywalny rysunek i wygląd</span><span class="sxs-lookup"><span data-stu-id="11d26-132">Fully customizable drawing and appearance</span></span>

* <span data-ttu-id="11d26-133">W pełni dostosowywalna obsługa operacji i zdarzeń</span><span class="sxs-lookup"><span data-stu-id="11d26-133">Fully customizable operation and event handling</span></span>

* <span data-ttu-id="11d26-134">Tylko użyte elementy widget są połączone z oprogramowaniem aplikacji</span><span class="sxs-lookup"><span data-stu-id="11d26-134">Only the widgets used are linked with application software</span></span>

### <a name="math-and-utilities"></a><span data-ttu-id="11d26-135">Math i narzędzia</span><span class="sxs-lookup"><span data-stu-id="11d26-135">Math and utilities</span></span>

* <span data-ttu-id="11d26-136">Funkcje dla Sin, cos, łuków, ARccOS, tangens, pierwiastek kwadratowy</span><span class="sxs-lookup"><span data-stu-id="11d26-136">Functions for sin, cos, arcsin, arccos, tangent, square root</span></span>

* <span data-ttu-id="11d26-137">Funkcje manipulowania regionami ekranu</span><span class="sxs-lookup"><span data-stu-id="11d26-137">Functions for manipulating screen regions</span></span>

* <span data-ttu-id="11d26-138">Konfiguracja systemu i uruchamianie</span><span class="sxs-lookup"><span data-stu-id="11d26-138">System configuration and startup</span></span>

* <span data-ttu-id="11d26-139">Definicja puli pamięci (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="11d26-139">Memory pool definition (optional)</span></span>

* <span data-ttu-id="11d26-140">Zarządzanie czasomierzem</span><span class="sxs-lookup"><span data-stu-id="11d26-140">Timer Management</span></span>

* <span data-ttu-id="11d26-141">Zarządzanie animacją</span><span class="sxs-lookup"><span data-stu-id="11d26-141">Animation Management</span></span>

* <span data-ttu-id="11d26-142">Konserwacja listy zanieczyszczonej</span><span class="sxs-lookup"><span data-stu-id="11d26-142">Dirty list maintenance</span></span>

### <a name="image-processing"></a><span data-ttu-id="11d26-143">Przetwarzanie obrazów</span><span class="sxs-lookup"><span data-stu-id="11d26-143">Image processing</span></span>

* <span data-ttu-id="11d26-144">Funkcje dekodowania środowiska uruchomieniowego obrazów JPEG i PNG</span><span class="sxs-lookup"><span data-stu-id="11d26-144">Functions for runtime decode of jpeg and png images</span></span>

* <span data-ttu-id="11d26-145">Stosowanie symulowania i konwersji przestrzeni kolorów</span><span class="sxs-lookup"><span data-stu-id="11d26-145">Apply dithering and color space conversion</span></span>

* <span data-ttu-id="11d26-146">Obrót obrazu</span><span class="sxs-lookup"><span data-stu-id="11d26-146">Image rotation</span></span>

* <span data-ttu-id="11d26-147">Skalowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="11d26-147">Image scaling</span></span>

* <span data-ttu-id="11d26-148">Mieszanie obrazów</span><span class="sxs-lookup"><span data-stu-id="11d26-148">Image blending</span></span>

### <a name="event-processing"></a><span data-ttu-id="11d26-149">Przetwarzanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="11d26-149">Event processing</span></span>

* <span data-ttu-id="11d26-150">Automatycznie wstrzymuje wątek usługi Azure RTO GUIX, gdy jest on bezczynny</span><span class="sxs-lookup"><span data-stu-id="11d26-150">Automatically suspends Azure RTOS GUIX thread when idle</span></span>

* <span data-ttu-id="11d26-151">Model programowania oparty na zdarzeniach popularne w projekcie interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="11d26-151">Event-driven programming model popular in UI design</span></span>

* <span data-ttu-id="11d26-152">Izolowanie sterowników wejściowych z wątku rysowania usługi Azure RTO GUIX</span><span class="sxs-lookup"><span data-stu-id="11d26-152">Insulates input drivers from Azure RTOS GUIX drawing thread</span></span>

* <span data-ttu-id="11d26-153">Funkcje wysyłania i otrzymywania zdarzeń</span><span class="sxs-lookup"><span data-stu-id="11d26-153">Functions for sending and receiving events</span></span>

* <span data-ttu-id="11d26-154">Wstępnie zdefiniowane typy zdarzeń dla wszystkich typów widżetów GUIX usługi Azure RTO</span><span class="sxs-lookup"><span data-stu-id="11d26-154">Pre-defined event types for all Azure RTOS GUIX widget types</span></span>

* <span data-ttu-id="11d26-155">Obsługiwane zdarzenia niestandardowe zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="11d26-155">User-defined custom events supported</span></span>

### <a name="canvas-processing"></a><span data-ttu-id="11d26-156">Przetwarzanie kanwy</span><span class="sxs-lookup"><span data-stu-id="11d26-156">Canvas processing</span></span>

* <span data-ttu-id="11d26-157">Przycinanie i obsługa porządku osi Z</span><span class="sxs-lookup"><span data-stu-id="11d26-157">Clipping and Z-Order maintenance</span></span>

* <span data-ttu-id="11d26-158">Izolowanie biblioteki widget ze szczegółowych informacji o sprzęcie</span><span class="sxs-lookup"><span data-stu-id="11d26-158">Insulates widget library from hardware details</span></span>

* <span data-ttu-id="11d26-159">Izolowanie aplikacji od szczegółów sprzętu</span><span class="sxs-lookup"><span data-stu-id="11d26-159">Insulates application from hardware details</span></span>

* <span data-ttu-id="11d26-160">Automatyczne odświeżanie w tle obszarów zanieczyszczonych</span><span class="sxs-lookup"><span data-stu-id="11d26-160">Automatic background refresh of dirty areas</span></span>

* <span data-ttu-id="11d26-161">Obsługa wielu kanw z obsługą warstw i mieszania</span><span class="sxs-lookup"><span data-stu-id="11d26-161">Multiple canvases with layering and blending supported</span></span>

* <span data-ttu-id="11d26-162">Może być wywoływana bezpośrednio przez oprogramowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="11d26-162">Can be invoked directly by the application software</span></span>

### <a name="input-device-drivers"></a><span data-ttu-id="11d26-163">Sterowniki urządzeń wejściowych</span><span class="sxs-lookup"><span data-stu-id="11d26-163">Input device driver(s)</span></span>

* <span data-ttu-id="11d26-164">Obsługa specyficzna dla sprzętu, usługa Azure RTO GUIX i aplikacja izolowana ze szczegółowych informacji o sprzęcie</span><span class="sxs-lookup"><span data-stu-id="11d26-164">Hardware-specific support, Azure RTOS GUIX and application insulated from hardware details</span></span>

* <span data-ttu-id="11d26-165">Obsługiwane są odporne na dotknięcia, dotknięcie i klawiatura</span><span class="sxs-lookup"><span data-stu-id="11d26-165">Resistive Touch, Cap Touch, and keypad supported</span></span>

* <span data-ttu-id="11d26-166">Zdarzenia wejściowe przesłane do kolejki zdarzeń usługi Azure RTO GUIX</span><span class="sxs-lookup"><span data-stu-id="11d26-166">Input events passed to Azure RTOS GUIX event queue</span></span>

### <a name="display-drivers"></a><span data-ttu-id="11d26-167">Sterowniki ekranu</span><span class="sxs-lookup"><span data-stu-id="11d26-167">Display drivers</span></span>

* <span data-ttu-id="11d26-168">Obsługa sprzętowa</span><span class="sxs-lookup"><span data-stu-id="11d26-168">Hardware-specific support</span></span>

* <span data-ttu-id="11d26-169">Ogólne sterowniki dostarczone dla całej głębi kolorów i formatów</span><span class="sxs-lookup"><span data-stu-id="11d26-169">Generic drivers provided for all color depth and formats</span></span>

* <span data-ttu-id="11d26-170">Dostosowany do korzystania z dostępnych akceleratorów grafiki</span><span class="sxs-lookup"><span data-stu-id="11d26-170">Customized to utilize available graphics accelerators</span></span>

### <a name="target-hardware"></a><span data-ttu-id="11d26-171">Sprzęt docelowy</span><span class="sxs-lookup"><span data-stu-id="11d26-171">Target hardware</span></span>

* <span data-ttu-id="11d26-172">Niemal każdy sprzęt z możliwością grafiki wyjściowej jest zgodny z GUIX</span><span class="sxs-lookup"><span data-stu-id="11d26-172">Nearly any hardware capable of graphical output Is compatible with GUIX</span></span>

* <span data-ttu-id="11d26-173">Obsługiwane są wiele fizycznych wyświetlaczy</span><span class="sxs-lookup"><span data-stu-id="11d26-173">Multiple physical displays supported</span></span>

* <span data-ttu-id="11d26-174">Minimalna ilość pamięci RAM i wymagania dotyczące programu Flash</span><span class="sxs-lookup"><span data-stu-id="11d26-174">Minimal RAM and Flash requirements</span></span>

## <a name="create-elegant-user-interfaces"></a><span data-ttu-id="11d26-175">Tworzenie eleganckich interfejsów użytkownika</span><span class="sxs-lookup"><span data-stu-id="11d26-175">Create Elegant User Interfaces</span></span>

<span data-ttu-id="11d26-176">Usługi Azure RTO GUIX i Azure RTO GUIX Studio oferują wszystkie funkcje niezbędne do tworzenia unikatowych interfejsów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11d26-176">Azure RTOS GUIX and Azure RTOS GUIX Studio provide all the features necessary to create uniquely elegant user interfaces.</span></span> <span data-ttu-id="11d26-177">Standardowy pakiet platformy Azure RTO GUIX obejmuje różne przykładowe interfejsy użytkownika, w tym informacje dotyczące urządzeń medycznych, odwołanie do inteligentnej czujki, odwołanie do automatyzacji domu, odwołanie do kontroli przemysłowej, odwołanie do sieci samochodowej i różne przykłady ikon i animacji.</span><span class="sxs-lookup"><span data-stu-id="11d26-177">The standard Azure RTOS GUIX package includes various sample user interfaces, including a medical device reference, a smart watch reference, a home automation reference, an industrial control reference, an automotive reference, and various sprite and animation examples.</span></span> <span data-ttu-id="11d26-178">Kliknij przykłady referencyjne poniżej.</span><span class="sxs-lookup"><span data-stu-id="11d26-178">Please click on the reference examples shown below.</span></span>

### <a name="home-automation"></a><span data-ttu-id="11d26-179">Automatyzacja domu</span><span class="sxs-lookup"><span data-stu-id="11d26-179">Home Automation</span></span>

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a><span data-ttu-id="11d26-180">Leczniczych</span><span class="sxs-lookup"><span data-stu-id="11d26-180">Medical</span></span>

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a><span data-ttu-id="11d26-181">Produkty konsumenckie</span><span class="sxs-lookup"><span data-stu-id="11d26-181">Consumer</span></span>

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a><span data-ttu-id="11d26-182">Białe towary</span><span class="sxs-lookup"><span data-stu-id="11d26-182">White Goods</span></span>

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a><span data-ttu-id="11d26-183">Motoryzacja</span><span class="sxs-lookup"><span data-stu-id="11d26-183">Automotive</span></span>

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a><span data-ttu-id="11d26-184">Branżowe</span><span class="sxs-lookup"><span data-stu-id="11d26-184">Industrial</span></span>

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

<span data-ttu-id="11d26-185">Każda dokumentacja usługi Azure RTO GUIX ma odpowiedni projekt platformy Azure RTO GUIX Studio, który definiuje wszystkie elementy graficzne w projekcie referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="11d26-185">Each Azure RTOS GUIX reference has a corresponding Azure RTOS GUIX Studio project that defines all the graphical elements of the reference design.</span></span> <span data-ttu-id="11d26-186">Zmiana projektu referencyjnego jest prosta.</span><span class="sxs-lookup"><span data-stu-id="11d26-186">Changing a reference design is easy.</span></span> <span data-ttu-id="11d26-187">Po prostu otwórz odpowiedni projekt usługi Azure RTO GUIX, wprowadź żądane zmiany, Zapisz projekt, a następnie wybierz pozycję *projekt*.</span><span class="sxs-lookup"><span data-stu-id="11d26-187">Simply open the corresponding Azure RTOS GUIX project, make the desired changes, save the project, and then select *Project*.</span></span>

<span data-ttu-id="11d26-188">Generuj wszystkie pliki wyjściowe, aby wygenerować kod języka C dla usługi Azure RTO GUIX.</span><span class="sxs-lookup"><span data-stu-id="11d26-188">Generate All Output Files to generate the C code for Azure RTOS GUIX.</span></span> <span data-ttu-id="11d26-189">Następnie po prostu Skompiluj ponownie aplikację docelową i uruchom polecenie, aby obserwować zmodyfikowany projekt odwołań.</span><span class="sxs-lookup"><span data-stu-id="11d26-189">Then simply rebuild the target application and run to observe the modified reference design.</span></span>

### <a name="small-footprint"></a><span data-ttu-id="11d26-190">Niewielkie rozmiary</span><span class="sxs-lookup"><span data-stu-id="11d26-190">Small-footprint</span></span>

<span data-ttu-id="11d26-191">Usługa Azure RTO GUIX ma niewielką minimalną wartość 13.2 KB i 4 KB pamięci RAM na potrzeby podstawowej pomocy technicznej, bez uwzględnienia pamięci wymaganej dla kanwy.</span><span class="sxs-lookup"><span data-stu-id="11d26-191">Azure RTOS GUIX has a remarkably small minimal footprint of 13.2KB of FLASH and 4KB RAM for basic support, not including the memory required for a canvas.</span></span>

<span data-ttu-id="11d26-192">Do wyświetlania z wewnętrzną technologią uczenia i samodzielnego odświeżania nie jest wymagana żadna pamięć kanwy.</span><span class="sxs-lookup"><span data-stu-id="11d26-192">For a display with internal GRAM and self-refresh technology, no canvas memory is required.</span></span> <span data-ttu-id="11d26-193">Jednak aby zwiększyć wydajność rysowania lub dla konfiguracji wyświetlania, która nie korzysta z lokalnego do wyświetlania, obszar pamięci kanwy jest definiowany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="11d26-193">However, to improve drawing performance, or for a display configuration that does not utilize GRAM local to the display, a canvas memory area is defined by the application.</span></span>

<span data-ttu-id="11d26-194">Wymagania dotyczące pamięci kanwy są funkcją rozmiaru kanwy oraz głębią kolorów i są zdefiniowane przez formułę:</span><span class="sxs-lookup"><span data-stu-id="11d26-194">Canvas memory requirements are a function of the canvas size as well as the color depth, and are defined by the formula:</span></span>

<span data-ttu-id="11d26-195"><i>Pamięć RAM kanwy (w bajtach) = (x \* y \* (BPP/8))</i></span><span class="sxs-lookup"><span data-stu-id="11d26-195"><i>Canvas RAM (bytes) = (x \* y \* (bpp/8))</i></span></span>

<span data-ttu-id="11d26-196">Gdzie "x" i "y" są wymiarami kanwy (Display).</span><span class="sxs-lookup"><span data-stu-id="11d26-196">Where “x” and “y” are the dimensions of the canvas (display).</span></span>

<span data-ttu-id="11d26-197">Większość aplikacji korzysta również z zasobów graficznych, które nie są uwzględnione w podstawowych wymaganiach dotyczących magazynu biblioteki usługi Azure RTO GUIX.</span><span class="sxs-lookup"><span data-stu-id="11d26-197">Most applications also utilize graphical resources, which are not included in the core Azure RTOS GUIX library storage requirements.</span></span> <span data-ttu-id="11d26-198">Te zasoby obejmują czcionki, graficzne ikony (pixelmaps) i ciągi statyczne.</span><span class="sxs-lookup"><span data-stu-id="11d26-198">These resources include fonts, graphical icons (pixelmaps), and static strings.</span></span> <span data-ttu-id="11d26-199">Te dane mogą być przechowywane w sekcji Pamięć stała (tj. FLASH).</span><span class="sxs-lookup"><span data-stu-id="11d26-199">This data can be stored in the const memory section (i.e. FLASH).</span></span>

<span data-ttu-id="11d26-200">Rozmiar tego obszaru pamięci zależy od wielu czynników, w tym liczby i rozmiaru używanych czcionek, liczby i rozmiaru używanych ikon graficznych, formatu koloru wyjściowego oraz tego, czy każdy zasób korzysta z skompresowanych danych, ponieważ usługa Azure RTO GUIX obsługuje kompresję RLE zarówno czcionki, jak i Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="11d26-200">The size of this memory area is dependent on a number of factors, including the number and size of unique fonts used, the number and size of the graphical icons used, the output color format, and whether or not each resource is using compressed data, since Azure RTOS GUIX supports RLE compression of both font and pixelmap data.</span></span> <span data-ttu-id="11d26-201">Wymagania dotyczące magazynu dla każdego zasobu są wyświetlane w aplikacji Azure RTO GUIX Studio, co umożliwia użytkownikowi śledzenie i monitorowanie ilości pamięci flash, która będzie używana przez zasoby aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11d26-201">The storage requirements for each resource are displayed within the Azure RTOS GUIX Studio application, allowing the user to track and monitor the amount of flash memory that will be consumed by the application resources.</span></span>

<span data-ttu-id="11d26-202">Podobnie jak w przypadku usługi Azure RTO ThreadX, rozmiar usługi Azure RTO GUIX jest automatycznie skalowany w oparciu o usługi faktycznie używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="11d26-202">Like Azure RTOS ThreadX, the size of Azure RTOS GUIX automatically scales based on the services actually used by the application.</span></span> <span data-ttu-id="11d26-203">To praktycznie eliminuje konieczność tworzenia skomplikowanych parametrów konfiguracji i kompilacji, co ułatwia deweloperom.</span><span class="sxs-lookup"><span data-stu-id="11d26-203">This virtually eliminates the need for complicated configuration and build parameters, making things easier for the developer.</span></span>

### <a name="fast-execution"></a><span data-ttu-id="11d26-204">Szybkie wykonywanie</span><span class="sxs-lookup"><span data-stu-id="11d26-204">Fast execution</span></span>

<span data-ttu-id="11d26-205">Usługa Azure RTO GUIX jest zapisywana wyłącznie w języku C i została zaprojektowana z myślą o szybkości.</span><span class="sxs-lookup"><span data-stu-id="11d26-205">Azure RTOS GUIX is written exclusively in C and is designed for speed.</span></span> <span data-ttu-id="11d26-206">Usługa Azure RTO GUIX wymaga minimalnej warstwy wywołań wewnętrznych funkcji.</span><span class="sxs-lookup"><span data-stu-id="11d26-206">Azure RTOS GUIX has minimal internal function call layering.</span></span>

<span data-ttu-id="11d26-207">Ponadto usługa Azure RTO GUIX zapewnia zoptymalizowane obcinanie, rysowanie i obsługę zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="11d26-207">In addition, Azure RTOS GUIX provides optimized clipping, drawing, and event handling.</span></span> <span data-ttu-id="11d26-208">Wszystkie te i ogólne zasady projektowania zorientowane na wydajność ułatwiają platformie Azure RTO GUIX osiąganie najszybszej możliwej wydajności.</span><span class="sxs-lookup"><span data-stu-id="11d26-208">All of this and a general performance-oriented design philosophy help Azure RTOS GUIX achieve the fastest possible performance.</span></span>

### <a name="pre-certified--by-tuv-to-many-safety-standards"></a><span data-ttu-id="11d26-209">Certyfikowane przed certyfikatami przez TUV z wieloma standardami bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="11d26-209">Pre-certified  by TUV to many safety standards</span></span>

<span data-ttu-id="11d26-210">Usługa Azure RTO GUIX została certyfikowana przez moimi-TUV Saar do użytku w systemach krytycznych dla bezpieczeństwa, zgodnie z IEC-61508 SIL 4, IEC-62304, Klasa bezpieczeństwa SW, ISO 26262 ASIL D i EN 50128.</span><span class="sxs-lookup"><span data-stu-id="11d26-210">Azure RTOS GUIX has been certified by SGS-TUV  Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="11d26-211">Certyfikat potwierdza, że usługa Azure RTO GUIX może być używana w rozwoju oprogramowania związanego z bezpieczeństwem w celu uzyskania najwyższych poziomów integralności zabezpieczeń IEC-61508, IEC-62304, ISO 26262 i EN 50128 na potrzeby "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemów związanych z bezpieczeństwem".</span><span class="sxs-lookup"><span data-stu-id="11d26-211">The certification confirms that Azure RTOS GUIX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="11d26-212">MOIMI-TUV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGS-Group i TUV Saarland, stał się wiodącą, niezależną firmą do testowania, przeprowadzania inspekcji, sprawdzania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie.</span><span class="sxs-lookup"><span data-stu-id="11d26-212">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="11d26-213">Standard bezpieczeństwa przemysłowego IEC 61508, a także wszystkie standardy, które są od niego pochodzące, w tym IEC-62304, ISO 26262 i EN 50128, są używane do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego sprzętu medycznego, systemów kontroli procesów, maszyn przemysłowych, samochodów i systemów kontroli szynowej.</span><span class="sxs-lookup"><span data-stu-id="11d26-213">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles and railway control systems.</span></span>

<img alt="SGS-TUV Saar" class="img-responsive" src="https://rtos.com/wp-content/uploads/2017/10/partener-logo-sgs-tuv-saar-2.png"/>

#### <a name="simple-easy-to-use"></a><span data-ttu-id="11d26-214">Proste i łatwe w użyciu</span><span class="sxs-lookup"><span data-stu-id="11d26-214">Simple, easy-to-use</span></span>

<span data-ttu-id="11d26-215">Korzystanie z usługi Azure RTO GUIX jest bardzo proste, a usługa Azure RTO GUIX Studio ułatwia deweloperom wizualne projektowanie na pulpicie i generowanie kodu języka C, który jest uruchamiany w rzeczywistym miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="11d26-215">Azure RTOS GUIX is very simple to use and Azure RTOS GUIX Studio makes it even easier by allowing developers to visually design on the desktop and generate C code that runs on the actual target.</span></span> <span data-ttu-id="11d26-216">Aplikacje mogą następnie dodać własne niestandardowe funkcje obsługi zdarzeń i rysowania, aby zakończyć ich graficzny interfejs użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11d26-216">Applications can then add their own custom event handling and drawing functions to complete their GUI.</span></span>

<span data-ttu-id="11d26-217">Korzystanie z interfejsu API usługi Azure RTO GUIX jest proste.</span><span class="sxs-lookup"><span data-stu-id="11d26-217">Using the Azure RTOS GUIX API is straightforward.</span></span> <span data-ttu-id="11d26-218">Interfejs API usługi Azure RTO GUIX jest intuicyjny i wysoce funkcjonalny.</span><span class="sxs-lookup"><span data-stu-id="11d26-218">The Azure RTOS GUIX API is both intuitive and highly functional.</span></span> <span data-ttu-id="11d26-219">Nazwy interfejsów API są prawdziwe mówiące i nie są "alfabetem" i/lub bardzo skróconymi nazwami, które są powszechnie używane w innych produktach systemu plików.</span><span class="sxs-lookup"><span data-stu-id="11d26-219">The API names are made of real words and not the “alphabet soup” and/or the highly abbreviated names that are so common in other file system products.</span></span> <span data-ttu-id="11d26-220">Wszystkie interfejsy API usługi Azure RTO GUIX mają wiodące *gx_* i są zgodne z konwencją nazewnictwa czasowników.</span><span class="sxs-lookup"><span data-stu-id="11d26-220">All Azure RTOS GUIX APIs have a leading *gx_* and follow a noun-verb naming convention.</span></span> <span data-ttu-id="11d26-221">Ponadto istnieje spójność funkcjonalna w całym interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="11d26-221">Furthermore, there is a functional consistency throughout the API.</span></span> <span data-ttu-id="11d26-222">Na przykład wszystkie interfejsy API, które inicjują blok kontrolki widżetu, mają nazwę &lt; widget_type &gt; _create, a parametry funkcji tworzenia dla każdego typu widżetu są zawsze zdefiniowane w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="11d26-222">For example, all APIs that initialize a widget control block are named &lt; widget_type&gt;_create, and the create function parameters for each widget type are always defined in the same order.</span></span>

### <a name="comprehensive-set-of-built-in-widgets"></a><span data-ttu-id="11d26-223">Kompleksowy zestaw wbudowanych elementów widget</span><span class="sxs-lookup"><span data-stu-id="11d26-223">Comprehensive set of built-in widgets</span></span>

* <span data-ttu-id="11d26-224">Usługa Azure RTO GUIX oferuje bogaty zestaw wbudowanych elementów widget, takich jak:</span><span class="sxs-lookup"><span data-stu-id="11d26-224">Azure RTOS GUIX provides a rich set of built-in widgets, including:</span></span>

* <span data-ttu-id="11d26-225">Menu przyznane</span><span class="sxs-lookup"><span data-stu-id="11d26-225">Accordion Menu</span></span>

* <span data-ttu-id="11d26-226">Przycisk</span><span class="sxs-lookup"><span data-stu-id="11d26-226">Button</span></span>

* <span data-ttu-id="11d26-227">Pole wyboru</span><span class="sxs-lookup"><span data-stu-id="11d26-227">Checkbox</span></span>

* <span data-ttu-id="11d26-228">Miernik kołowy</span><span class="sxs-lookup"><span data-stu-id="11d26-228">Circular Gauge</span></span>

* <span data-ttu-id="11d26-229">Lista rozwijana</span><span class="sxs-lookup"><span data-stu-id="11d26-229">Drop Down List</span></span>

* <span data-ttu-id="11d26-230">Lista pozioma</span><span class="sxs-lookup"><span data-stu-id="11d26-230">Horizontal List</span></span>

* <span data-ttu-id="11d26-231">Poziome okno przewijania</span><span class="sxs-lookup"><span data-stu-id="11d26-231">Horizontal Scrollbar Window</span></span>

* <span data-ttu-id="11d26-232">Ikona</span><span class="sxs-lookup"><span data-stu-id="11d26-232">Icon</span></span>

* <span data-ttu-id="11d26-233">Przycisk ikony</span><span class="sxs-lookup"><span data-stu-id="11d26-233">Icon Button</span></span>

* <span data-ttu-id="11d26-234">Wykres liniowy</span><span class="sxs-lookup"><span data-stu-id="11d26-234">Line Chart</span></span>

* <span data-ttu-id="11d26-235">Menu</span><span class="sxs-lookup"><span data-stu-id="11d26-235">Menu</span></span>

* <span data-ttu-id="11d26-236">Przycisk tekstu wielowierszowego</span><span class="sxs-lookup"><span data-stu-id="11d26-236">Multi Line Text Button</span></span>

* <span data-ttu-id="11d26-237">Wprowadzanie tekstu wielowierszowego</span><span class="sxs-lookup"><span data-stu-id="11d26-237">Multi Line Text Input</span></span>

* <span data-ttu-id="11d26-238">Widok tekstu wielowierszowego</span><span class="sxs-lookup"><span data-stu-id="11d26-238">Multi Line Text View</span></span>

* <span data-ttu-id="11d26-239">Numeryczny monit Pixelmap</span><span class="sxs-lookup"><span data-stu-id="11d26-239">Numeric Pixelmap Prompt</span></span>

* <span data-ttu-id="11d26-240">Monit liczbowy</span><span class="sxs-lookup"><span data-stu-id="11d26-240">Numeric Prompt</span></span>

* <span data-ttu-id="11d26-241">Pokrętło przewijania liczbowego</span><span class="sxs-lookup"><span data-stu-id="11d26-241">Numeric Scroll Wheel</span></span>

* <span data-ttu-id="11d26-242">Przycisk Pixelmap</span><span class="sxs-lookup"><span data-stu-id="11d26-242">Pixelmap Button</span></span>

* <span data-ttu-id="11d26-243">Pixelmap monit</span><span class="sxs-lookup"><span data-stu-id="11d26-243">Pixelmap Prompt</span></span>

* <span data-ttu-id="11d26-244">Suwak Pixelmap</span><span class="sxs-lookup"><span data-stu-id="11d26-244">Pixelmap Slider</span></span>

* <span data-ttu-id="11d26-245">Pixelmap Sprite</span><span class="sxs-lookup"><span data-stu-id="11d26-245">Pixelmap Sprite</span></span>

* <span data-ttu-id="11d26-246">pasek postępu</span><span class="sxs-lookup"><span data-stu-id="11d26-246">Progress Bar</span></span>

* <span data-ttu-id="11d26-247">Monit</span><span class="sxs-lookup"><span data-stu-id="11d26-247">Prompt</span></span>

* <span data-ttu-id="11d26-248">Pasek postępu promieniowego</span><span class="sxs-lookup"><span data-stu-id="11d26-248">Radial Progress Bar</span></span>

* <span data-ttu-id="11d26-249">przycisk radiowy</span><span class="sxs-lookup"><span data-stu-id="11d26-249">Radio Button</span></span>

* <span data-ttu-id="11d26-250">Kółko przewijania</span><span class="sxs-lookup"><span data-stu-id="11d26-250">Scroll Wheel</span></span>

* <span data-ttu-id="11d26-251">Wejście tekstu jednowierszowego</span><span class="sxs-lookup"><span data-stu-id="11d26-251">Single Line Text Input</span></span>

* <span data-ttu-id="11d26-252">Suwak</span><span class="sxs-lookup"><span data-stu-id="11d26-252">Slider</span></span>

* <span data-ttu-id="11d26-253">Kółko przewijania ciągów</span><span class="sxs-lookup"><span data-stu-id="11d26-253">String Scroll Wheel</span></span>

* <span data-ttu-id="11d26-254">Przycisk tekstu</span><span class="sxs-lookup"><span data-stu-id="11d26-254">Text Button</span></span>

* <span data-ttu-id="11d26-255">Widok drzewa</span><span class="sxs-lookup"><span data-stu-id="11d26-255">Tree View</span></span>

* <span data-ttu-id="11d26-256">Lista pionowa</span><span class="sxs-lookup"><span data-stu-id="11d26-256">Vertical List</span></span>

* <span data-ttu-id="11d26-257">Pionowy pasek przewijania</span><span class="sxs-lookup"><span data-stu-id="11d26-257">Vertical Scrollbar</span></span>

<span data-ttu-id="11d26-258">Aplikacja może również łatwo tworzyć własne widżety klienta.</span><span class="sxs-lookup"><span data-stu-id="11d26-258">It’s easy for the application to create its own customer widgets as well.</span></span>

### <a name="complete-low-level-drawing-api"></a><span data-ttu-id="11d26-259">Kompletny interfejs API rysowania niskiego poziomu</span><span class="sxs-lookup"><span data-stu-id="11d26-259">Complete low-level drawing API</span></span>

<span data-ttu-id="11d26-260">Usługa Azure RTO GUIX zapewnia niezawodny interfejs API rysowania kanwy, co pozwala aplikacji na renderowanie złożonych kształtów graficznych.</span><span class="sxs-lookup"><span data-stu-id="11d26-260">Azure RTOS GUIX provides a robust canvas drawing API, allowing the application to render complex graphical shapes.</span></span>

<span data-ttu-id="11d26-261">Wszystkie funkcje obsługują wygładzanie w przypadku obiektów docelowych o dużej głębi kolorów, a wszystkie kształty mogą być wypełniane, w tym wypełnieniami pełnymi i Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="11d26-261">All functions support anti-aliasing on high color depth targets, and all shapes can be filled our outlined, including solid and pixelmap pattern fills.</span></span> <span data-ttu-id="11d26-262">Wszystkie elementy pierwotne rysowania obsługują alfa pędzla, gdy działa o 16 BPP i większej głębi kolorów.</span><span class="sxs-lookup"><span data-stu-id="11d26-262">All drawing primitives support brush alpha when running at 16 bpp and higher color depth.</span></span> <span data-ttu-id="11d26-263">Funkcje rysowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="11d26-263">Drawing functions include:</span></span>

* <span data-ttu-id="11d26-264">Rysuj łuk</span><span class="sxs-lookup"><span data-stu-id="11d26-264">Arc Draw</span></span>

* <span data-ttu-id="11d26-265">Okrąg rysowania</span><span class="sxs-lookup"><span data-stu-id="11d26-265">Circle Draw</span></span>

* <span data-ttu-id="11d26-266">Rysowanie linii</span><span class="sxs-lookup"><span data-stu-id="11d26-266">Line Draw</span></span>

* <span data-ttu-id="11d26-267">Rysowanie wykresu kołowego</span><span class="sxs-lookup"><span data-stu-id="11d26-267">Pie Draw</span></span>

* <span data-ttu-id="11d26-268">Pixelmap Blend</span><span class="sxs-lookup"><span data-stu-id="11d26-268">Pixelmap Blend</span></span>

* <span data-ttu-id="11d26-269">Kafelek Pixelmap</span><span class="sxs-lookup"><span data-stu-id="11d26-269">Pixelmap Tile</span></span>

* <span data-ttu-id="11d26-270">Rysowanie wielokątów</span><span class="sxs-lookup"><span data-stu-id="11d26-270">Polygon Draw</span></span>

* <span data-ttu-id="11d26-271">Rysowanie tekstu</span><span class="sxs-lookup"><span data-stu-id="11d26-271">Text Draw</span></span>

* <span data-ttu-id="11d26-272">Skrót remis</span><span class="sxs-lookup"><span data-stu-id="11d26-272">Chord Draw</span></span>

* <span data-ttu-id="11d26-273">Rysowanie elips</span><span class="sxs-lookup"><span data-stu-id="11d26-273">Ellipse Draw</span></span>

* <span data-ttu-id="11d26-274">Rysowanie pikseli</span><span class="sxs-lookup"><span data-stu-id="11d26-274">Pixel Draw</span></span>

* <span data-ttu-id="11d26-275">Pixelmap remis</span><span class="sxs-lookup"><span data-stu-id="11d26-275">Pixelmap Draw</span></span>

* <span data-ttu-id="11d26-276">Pixelmap</span><span class="sxs-lookup"><span data-stu-id="11d26-276">Pixelmap Rotate</span></span>

* <span data-ttu-id="11d26-277">Rysowanie prostokąta</span><span class="sxs-lookup"><span data-stu-id="11d26-277">Rectangle Draw</span></span>

* <span data-ttu-id="11d26-278">Mieszanie tekstu</span><span class="sxs-lookup"><span data-stu-id="11d26-278">Text Blend</span></span>

### <a name="default-free-fonts-and-easy-to-add-more"></a><span data-ttu-id="11d26-279">Domyślne czcionki bezpłatne i łatwe dodawanie</span><span class="sxs-lookup"><span data-stu-id="11d26-279">Default free fonts and easy to add more</span></span>

<span data-ttu-id="11d26-280">Usługa Azure RTO GUIX oferuje bezpłatny zestaw czcionek TrueType.</span><span class="sxs-lookup"><span data-stu-id="11d26-280">Azure RTOS GUIX provides a free set of TrueType fonts.</span></span> <span data-ttu-id="11d26-281">Deweloperzy mogą dodawać dodatkowe czcionki TrueType zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="11d26-281">Developers can add additional TrueType fonts as desired.</span></span>

<span data-ttu-id="11d26-282">Format czcionki GUIX usługi Azure RTO obsługuje 8bpp Anti-aliasing, 4bpp Anti-aliasing i 1bpp monochromatyczne czcionki.</span><span class="sxs-lookup"><span data-stu-id="11d26-282">The Azure RTOS GUIX font format supports 8bpp anti-aliasing, 4bpp anti-aliasing, and 1bpp monochrome fonts.</span></span> <span data-ttu-id="11d26-283">W przypadku większości aplikacji z ograniczeniami zasobów usługa Azure RTO GUIX wstępnie renderuje czcionki TrueType do formatu skompresowanej mapy bitowej przy użyciu narzędzia klasycznego GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="11d26-283">For the most resource-constrained applications, Azure RTOS GUIX pre-renders the TrueType fonts to a compressed bitmap format using our GUIX Studio desktop tool.</span></span>

### <a name="custom-jpg-and-png-decoder-implementation"></a><span data-ttu-id="11d26-284">Implementacja niestandardowego dekodera JPG i PNG</span><span class="sxs-lookup"><span data-stu-id="11d26-284">Custom JPG and PNG decoder implementation</span></span>

<span data-ttu-id="11d26-285">Implementacja niestandardowego dekodera JPG i PNG, implementacja dekodera pliku JPG i PNG.</span><span class="sxs-lookup"><span data-stu-id="11d26-285">Custom JPG and PNG decoder implementation JPG and PNG file decoder implementation.</span></span> <span data-ttu-id="11d26-286">Ta implementacja obsługuje konwersję przestrzeni kolorów, symulowanie i tworzenie obrazów formatu Pixelmap zgodnych z usługą Azure RTO GUIX.</span><span class="sxs-lookup"><span data-stu-id="11d26-286">This implementation supports color space conversion, dithering, and runtime creation of Azure RTOS GUIX-compatible pixelmap format images.</span></span>

### <a name="extensive-display-and-touchscreen-support"></a><span data-ttu-id="11d26-287">Rozbudowana obsługa wyświetlania i ekranu dotykowego</span><span class="sxs-lookup"><span data-stu-id="11d26-287">Extensive display and touchscreen support</span></span>

<span data-ttu-id="11d26-288">Usługa Azure RTO GUIX udostępnia ogólne sterowniki wyświetlania dla niemal wszystkich formatów kolorów, w tym 1bpp monochromatyczny, 8 palety BPP, 8 BPP 3:3:2,</span><span class="sxs-lookup"><span data-stu-id="11d26-288">Azure RTOS GUIX provides generic display drivers for nearly all color formats, including 1bpp monochrome, 8 bpp palette, 8 bpp 3:3:2 format,</span></span>

<span data-ttu-id="11d26-289">16 BPP 565 RGB, format 16 BPP 4:4:4:4, 32 BPP x:r: g:b format i 32 BPP a:r: g:b format.</span><span class="sxs-lookup"><span data-stu-id="11d26-289">16 bpp 565 rgb format, 16 bpp 4:4:4:4 format, 32 bpp x:r:g:b format, and 32 bpp a:r:g:b format.</span></span> <span data-ttu-id="11d26-290">Ponadto usługa Azure RTO GUIX jest zintegrowana z wieloma najpopularniejszymi kontrolerami LCD i akceleratorami sprzętowymi (ST ChromeArt, Renesas synergia itp.).</span><span class="sxs-lookup"><span data-stu-id="11d26-290">In addition, Azure RTOS GUIX is integrated with many of the most popular LCD controllers and hardware accelerators (ST ChromeArt, Renesas Synergy, etc.).</span></span>

<span data-ttu-id="11d26-291">Usługa Azure RTO GUIX w pełni obsługuje ekran dotykowy (w tym obsługę gestów), pióro i wirtualne urządzenia wejściowe z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="11d26-291">Azure RTOS GUIX fully supports touchscreen (including gesture support), pen, and virtual keyboard input devices.</span></span>

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a><span data-ttu-id="11d26-292">Narzędzie Azure RTO GUIX Studio w trybie WYSIWYG</span><span class="sxs-lookup"><span data-stu-id="11d26-292">Azure RTOS GUIX Studio desktop WYSIWYG tool</span></span>

<span data-ttu-id="11d26-293">Usługa Azure RTO GUIX Studio oferuje kompletne środowisko projektowania ekranu, które pozwala użytkownikowi na przeciąganie i upuszczanie elementów graficznych używanych do tworzenia ekranów graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11d26-293">Azure RTOS GUIX Studio provides a complete WYSIWYG screen design environment which allows the user to drag-and-drop graphical elements used to build the GUI screens.</span></span> <span data-ttu-id="11d26-294">Usługa Azure RTO GUIX Studio automatycznie generuje kod C zgodny z biblioteką GUIX RTO platformy Azure, gotowy do skompilowania i uruchomienia w miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="11d26-294">Azure RTOS GUIX Studio automatically generates C code compatible with the Azure RTOS GUIX library, ready to be compiled and run on the target.</span></span> <span data-ttu-id="11d26-295">Deweloperzy mogą tworzyć wstępnie renderowane czcionki do użycia w aplikacji przy użyciu zintegrowanego narzędzia do generowania czcionek usługi Azure RTO GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="11d26-295">Developers can produce pre-rendered fonts for use within an application using the integrated Azure RTOS GUIX Studio font generation tool.</span></span> <span data-ttu-id="11d26-296">Czcionki można generować w formatach monochromatycznych lub z wygładzaniem i są zoptymalizowane pod kątem oszczędzania miejsca na miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="11d26-296">Fonts can be generated in monochrome or anti-aliased formats, and are optimized to save space on the target.</span></span> <span data-ttu-id="11d26-297">Czcionki mogą zawierać dowolny zestaw znaków, w tym znaki Unicode dla aplikacji wielojęzycznych.</span><span class="sxs-lookup"><span data-stu-id="11d26-297">Fonts can include any set of characters, including Unicode characters for multi-lingual applications.</span></span>

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

<span data-ttu-id="11d26-298">Usługa Azure RTO GUIX Studio ułatwia importowanie grafiki z plików PNG lub JPG z konwersją na skompresowany system Azure RTO GUIX Pixelmaps do użycia w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="11d26-298">Azure RTOS GUIX Studio facilitates the import of graphics from PNG or JPG files with conversion to compressed Azure RTOS GUIX Pixelmaps for use on the target system.</span></span> <span data-ttu-id="11d26-299">Wiele typów widżetów GUIX usługi Azure RTO została zaprojektowana w celu uwzględnienia grafiki użytkownika w celu uzyskania niestandardowego wyglądu i działania.</span><span class="sxs-lookup"><span data-stu-id="11d26-299">Many of the Azure RTOS GUIX widget types are designed to incorporate user graphics for a custom look and feel.</span></span> <span data-ttu-id="11d26-300">Ponadto usługa Azure RTO GUIX Studio umożliwia dostosowanie domyślnych kolorów i stylów rysowania używanych przez widżety GUIX platformy Azure RTO, dzięki czemu deweloperzy mogą łatwo dostosowywać wygląd rozwiązań Azure RTO GUIX.</span><span class="sxs-lookup"><span data-stu-id="11d26-300">In addition, Azure RTOS GUIX Studio allows customization of the default colors and drawing styles used by the Azure RTOS GUIX widgets, allowing developers to tune the appearance of Azure RTOS GUIX very easily.</span></span> <span data-ttu-id="11d26-301">Generowanie i obsługa ciągów aplikacji jest kolejną wbudowaną funkcją platformy Azure RTO GUIX Studio.</span><span class="sxs-lookup"><span data-stu-id="11d26-301">Generation and maintenance of application strings is another built-in facility of Azure RTOS GUIX Studio.</span></span> <span data-ttu-id="11d26-302">Pozwala to deweloperom na projektowanie aplikacji przy użyciu jednego języka do opracowania i szybkie i łatwe dodawanie obsługi dodatkowych języków po wydaniu produktu.</span><span class="sxs-lookup"><span data-stu-id="11d26-302">This enables developers to design an application using one language for developing, and quickly and easily add support for additional languages after the product is released.</span></span> <span data-ttu-id="11d26-303">Kompletna aplikacja usługi Azure RTO GUIX może być wykonywana na komputerze stacjonarnym w środowisku usługi Azure RTO GUIX Studio, co pozwala na szybkie i łatwe generowanie i demonstrację pojęć GUI, testowanie przepływów ekranu oraz obserwacje przejść ekranu i animacji.</span><span class="sxs-lookup"><span data-stu-id="11d26-303">A complete Azure RTOS GUIX application can be executed on a PC desktop within the Azure RTOS GUIX Studio environment, allowing a quick and easy generation and demonstration of GUI concepts, testing of screen flows, and observation of screen transitions and animations.</span></span> <span data-ttu-id="11d26-304">Po zakończeniu projektowania można eksportować jako docelowe struktury danych języka C gotowe do skompilowania i połączoną z bibliotekami Azure RTO GUIX i Azure RTO ThreadX.</span><span class="sxs-lookup"><span data-stu-id="11d26-304">When completed, a design can be exported as target-ready C data structures, ready to be compiled and linked with the Azure RTOS GUIX and Azure RTOS ThreadX libraries.</span></span>

<span data-ttu-id="11d26-305">Usługa Azure RTO GUIX i usługa Azure RTO GUIX Studio obsługują wiele kompozycji zasobów, dzięki czemu aplikacja może być łatwo w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="11d26-305">Azure RTOS GUIX and Azure RTOS GUIX Studio support multiple resource themes, allowing an application to be easily reskinned at run-time.</span></span> <span data-ttu-id="11d26-306">Czcionki, kolory i pixelmaps można zmieniać w czasie wykonywania za pomocą jednego prostego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="11d26-306">Fonts, colors, and pixelmaps can be changed at run-time with one simple API.</span></span>

<span data-ttu-id="11d26-307">Dowiedz się więcej o programie GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="11d26-307">Learn more about GUIX Studio</span></span>

### <a name="complete-win32-simulation"></a><span data-ttu-id="11d26-308">Ukończ symulację Win32</span><span class="sxs-lookup"><span data-stu-id="11d26-308">Complete Win32 simulation</span></span>

<span data-ttu-id="11d26-309">Usługa Azure RTO GUIX działa na komputerze z systemem Windows, używając dokładnie tej samej biblioteki rysowania, która jest uruchamiana na tablicy docelowej.</span><span class="sxs-lookup"><span data-stu-id="11d26-309">Azure RTOS GUIX runs on a Windows PC, using exactly the same drawing library that runs on the target board.</span></span> <span data-ttu-id="11d26-310">Za pomocą usługi Azure RTO GUIX można kompilować i uruchamiać aplikację graficznego interfejsu użytkownika na komputerze oraz korzystać z tego samego kodu aplikacji w celu debugowania, szybkiego tworzenia prototypów, demonstracyjnej i docelowej operacji WYSIWYG.</span><span class="sxs-lookup"><span data-stu-id="11d26-310">With Azure RTOS GUIX, you can build and run a GUI application on the PC, and use the same application code on your target for debugging, rapid prototyping, demonstration, and WYSIWYG target operation.</span></span>

### <a name="advanced-technology"></a><span data-ttu-id="11d26-311">Technologia zaawansowana</span><span class="sxs-lookup"><span data-stu-id="11d26-311">Advanced technology</span></span>

* <span data-ttu-id="11d26-312">Zaawansowana technologia Azure RTO GUIX:</span><span class="sxs-lookup"><span data-stu-id="11d26-312">Azure RTOS GUIX's advanced technology incorporates:</span></span>

* <span data-ttu-id="11d26-313">Mieszanie alfa</span><span class="sxs-lookup"><span data-stu-id="11d26-313">Alpha blending</span></span>

* <span data-ttu-id="11d26-314">Wygładzanie</span><span class="sxs-lookup"><span data-stu-id="11d26-314">Anti-Aliasing</span></span>

* <span data-ttu-id="11d26-315">Automatyczne skalowanie</span><span class="sxs-lookup"><span data-stu-id="11d26-315">Automatic scaling</span></span>

* <span data-ttu-id="11d26-316">Kompresja mapy bitowej</span><span class="sxs-lookup"><span data-stu-id="11d26-316">Bitmap compression</span></span>

* <span data-ttu-id="11d26-317">Mieszanie kanwy</span><span class="sxs-lookup"><span data-stu-id="11d26-317">Canvas blending</span></span>

* <span data-ttu-id="11d26-318">Obsługa niestandardowego widżetu</span><span class="sxs-lookup"><span data-stu-id="11d26-318">Custom widget support</span></span>

* <span data-ttu-id="11d26-319">Obsługa rysowania odroczonego</span><span class="sxs-lookup"><span data-stu-id="11d26-319">Deferred drawing support</span></span>

* <span data-ttu-id="11d26-320">Obsługa symulowania</span><span class="sxs-lookup"><span data-stu-id="11d26-320">Dithering support</span></span>

* <span data-ttu-id="11d26-321">Programowanie neutralne endian</span><span class="sxs-lookup"><span data-stu-id="11d26-321">Endian neutral programming</span></span>

* <span data-ttu-id="11d26-322">Obsługa akceleratora sprzętowego</span><span class="sxs-lookup"><span data-stu-id="11d26-322">Hardware accelerator support</span></span>

* <span data-ttu-id="11d26-323">Obsługa wielojęzyczna i kodowanie UTF-8</span><span class="sxs-lookup"><span data-stu-id="11d26-323">Multilingual support and UTF-8 encoding</span></span>

* <span data-ttu-id="11d26-324">Obsługa wielu wyświetlaczy i kanwy</span><span class="sxs-lookup"><span data-stu-id="11d26-324">Multiple display and canvas support</span></span>

* <span data-ttu-id="11d26-325">Zoptymalizowane obcinanie, rysowanie i obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="11d26-325">Optimized clipping, drawing, and event handling</span></span>

* <span data-ttu-id="11d26-326">Dekoder plików JPEG i PNG</span><span class="sxs-lookup"><span data-stu-id="11d26-326">Runtime JPEG and PNG decoder</span></span>

* <span data-ttu-id="11d26-327">Karnacje i motywy</span><span class="sxs-lookup"><span data-stu-id="11d26-327">Skinning and Themes</span></span>

* <span data-ttu-id="11d26-328">Obsługuje monochromatyczny do 32-bitowego True-Color z formatami grafiki alfa</span><span class="sxs-lookup"><span data-stu-id="11d26-328">Supports monochrome through 32-bit true-color with alpha graphics formats</span></span>

* <span data-ttu-id="11d26-329">Przejścia, sprites i obsługa animacji</span><span class="sxs-lookup"><span data-stu-id="11d26-329">Transitions, Sprites, and Animation support</span></span>

* <span data-ttu-id="11d26-330">Symulacja Win32</span><span class="sxs-lookup"><span data-stu-id="11d26-330">Win32 simulation</span></span>

* <span data-ttu-id="11d26-331">Zarządzanie oknami, w tym okienka ekranu i konserwacja Z kolejnością Z</span><span class="sxs-lookup"><span data-stu-id="11d26-331">Window management including Viewports and Z-order maintenance</span></span>

### <a name="fastest-time-to-market"></a><span data-ttu-id="11d26-332">Najszybszy czas wprowadzenia na rynek</span><span class="sxs-lookup"><span data-stu-id="11d26-332">Fastest time-to-market</span></span>

<span data-ttu-id="11d26-333">Usługa Azure RTO GUIX jest łatwa do zainstalowania, uczenia się, używania, debugowania, weryfikowania, certyfikowania i konserwowania.</span><span class="sxs-lookup"><span data-stu-id="11d26-333">Azure RTOS GUIX is easy to install, learn, use, debug, verify, certify and maintain.</span></span> <span data-ttu-id="11d26-334">Usługa Azure RTO GUIX Studio pomaga również uprościć projektowanie i implementację osadzonego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="11d26-334">Azure RTOS GUIX Studio also helps making embedded GUI design and implementation easier.</span></span> <span data-ttu-id="11d26-335">W związku z tym usługa Azure RTO GUIX jest jednym z najpopularniejszych rozwiązań interfejsu GUI dla osadzonych urządzeń IoT.</span><span class="sxs-lookup"><span data-stu-id="11d26-335">As a result, Azure RTOS GUIX is one of the most popular GUI solutions for embedded IoT devices.</span></span> <span data-ttu-id="11d26-336">Nasza spójna przedział czasu na rynek jest oparta na:</span><span class="sxs-lookup"><span data-stu-id="11d26-336">Our consistent time-to-market advantage is built on:</span></span>

* <span data-ttu-id="11d26-337">Dokumentacja dotycząca jakości — zapoznaj się z naszym [podręcznikiem użytkownika usługi Azure RTO GUIX](about-guix.md) i zapoznaj się z Tobą.</span><span class="sxs-lookup"><span data-stu-id="11d26-337">Quality Documentation – please review our [Azure RTOS GUIX User Guide](about-guix.md) and see for yourself!</span></span>

* <span data-ttu-id="11d26-338">Ukończ dostępność kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="11d26-338">Complete Source Code Availability</span></span>

* <span data-ttu-id="11d26-339">Łatwy w użyciu interfejs API</span><span class="sxs-lookup"><span data-stu-id="11d26-339">Easy-to-use API</span></span>

* <span data-ttu-id="11d26-340">Kompleksowy i zaawansowany zestaw funkcji</span><span class="sxs-lookup"><span data-stu-id="11d26-340">Comprehensive and Advanced Feature Set</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="11d26-341">Jedna prosta licencja</span><span class="sxs-lookup"><span data-stu-id="11d26-341">One Simple License</span></span>

<span data-ttu-id="11d26-342">Nie ma kosztu użycia i przetestowania kodu źródłowego bez ponoszenia kosztów dla licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. wszystkie inne urządzenia wymagają prostej licencji rocznej.</span><span class="sxs-lookup"><span data-stu-id="11d26-342">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="11d26-343">Pełny kod źródłowy o najwyższej jakości</span><span class="sxs-lookup"><span data-stu-id="11d26-343">Full, highest-quality source code</span></span>

<span data-ttu-id="11d26-344">W ciągu lat kod źródłowy usługi Azure RTO NetX ustawił na pasku jakość i łatwość interpretacji.</span><span class="sxs-lookup"><span data-stu-id="11d26-344">Throughout the years, Azure RTOS NetX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="11d26-345">Ponadto Konwencja o jednej funkcji na plik umożliwia łatwe nawigowanie po źródle.</span><span class="sxs-lookup"><span data-stu-id="11d26-345">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="11d26-346">Obsługuje najpopularniejsze architektury</span><span class="sxs-lookup"><span data-stu-id="11d26-346">Supports most popular architectures</span></span>

<span data-ttu-id="11d26-347">Usługa Azure RTO GUIX działa na najpopularniejszych mikroprocesorach 32-bitowych, w pełni przetestowanych i w pełni obsługiwanych, w tym:</span><span class="sxs-lookup"><span data-stu-id="11d26-347">Azure RTOS GUIX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="11d26-348">Architektury zaawansowane:</span><span class="sxs-lookup"><span data-stu-id="11d26-348">Advanced Architectures:</span></span>

<span data-ttu-id="11d26-349">**Urządzenia analogowe**: SHARC, Blackfin, CM4xx</span><span class="sxs-lookup"><span data-stu-id="11d26-349">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="11d26-350">**Andes rdzeń**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="11d26-350">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="11d26-351">**Ambiqmicro**: Apollo MCUs</span><span class="sxs-lookup"><span data-stu-id="11d26-351">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="11d26-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/wy/A8/A9/A5x 64-BI/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="11d26-352">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="11d26-353">**Erze**: Xtensa, romb</span><span class="sxs-lookup"><span data-stu-id="11d26-353">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="11d26-354">**Ceva**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, wiced Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="11d26-354">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="11d26-355">**Cypress**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="11d26-355">**Cypress**: RISC-V</span></span>

<span data-ttu-id="11d26-356">**EnSilica**: ESI-RISC</span><span class="sxs-lookup"><span data-stu-id="11d26-356">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="11d26-357">**Infineon**: XMC1000, XMC4000, TriCore</span><span class="sxs-lookup"><span data-stu-id="11d26-357">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="11d26-358">**Intel; Intel FPGA**: x36/Pentium, XScale, Nios II, Cyclone, Arria 10</span><span class="sxs-lookup"><span data-stu-id="11d26-358">**Intel; Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="11d26-359">**Chip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/g/L/SV, PIC24/PIC32</span><span class="sxs-lookup"><span data-stu-id="11d26-359">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="11d26-360">**Mikrośrednik**: RISC-V</span><span class="sxs-lookup"><span data-stu-id="11d26-360">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="11d26-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, I.MX, ColdFire, Kinetis Cortex-M3/M4</span><span class="sxs-lookup"><span data-stu-id="11d26-361">**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="11d26-362">**Renesas**: sh, HS, V850, RX, rz, synergia</span><span class="sxs-lookup"><span data-stu-id="11d26-362">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="11d26-363">**Krzem Labs**: EFM32</span><span class="sxs-lookup"><span data-stu-id="11d26-363">**Silicon Labs**: EFM32</span></span>

<span data-ttu-id="11d26-364">**SynopSYS**: Arc 600, 700, łuk em, łuk HS</span><span class="sxs-lookup"><span data-stu-id="11d26-364">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="11d26-365">**St**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span><span class="sxs-lookup"><span data-stu-id="11d26-365">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="11d26-366">**: C5xxx**, C6xxx, Stellaris, Sitara, Tiva-C</span><span class="sxs-lookup"><span data-stu-id="11d26-366">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="11d26-367">**Przetwarzanie Wave**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, Klasa M</span><span class="sxs-lookup"><span data-stu-id="11d26-367">**Wave Computing**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="11d26-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span><span class="sxs-lookup"><span data-stu-id="11d26-368">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>
