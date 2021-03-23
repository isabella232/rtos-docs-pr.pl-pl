---
title: Rozdział 1 — wprowadzenie do GUIX
description: GUIX to implementacja (GUI) o wysokiej wydajności w czasie rzeczywistym zaprojektowana wyłącznie dla osadzonych aplikacji opartych na platformie Azure RTO ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b90da988a03d59b1bca3f5584164d641bef96454
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823107"
---
# <a name="chapter-1---introduction-to-azure-rtos-guix"></a><span data-ttu-id="e7754-103">Rozdział 1 — wprowadzenie do usługi Azure RTO GUIX</span><span class="sxs-lookup"><span data-stu-id="e7754-103">Chapter 1 - Introduction to Azure RTOS GUIX</span></span>

<span data-ttu-id="e7754-104">Usługa Azure RTO GUIX (GUIX) to implementacja interfejsu graficznego o wysokiej wydajności w czasie rzeczywistym zaprojektowana wyłącznie dla osadzonych aplikacji opartych na ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e7754-104">Azure RTOS GUIX (GUIX) is a high-performance real-time implementation of a graphical interface framework designed exclusively for embedded ThreadX-based applications.</span></span> <span data-ttu-id="e7754-105">Ten rozdział zawiera wprowadzenie do GUIX oraz opis jego aplikacji i korzyści.</span><span class="sxs-lookup"><span data-stu-id="e7754-105">This chapter contains an introduction to GUIX and a description of its applications and benefits.</span></span>

## <a name="guix-feature-overview"></a><span data-ttu-id="e7754-106">Omówienie funkcji GUIX</span><span class="sxs-lookup"><span data-stu-id="e7754-106">GUIX Feature Overview</span></span>

<span data-ttu-id="e7754-107">W przeciwieństwie do wielu innych implementacji graficznego interfejsu użytkownika, GUIX został zaprojektowany jako uniwersalny — można łatwo skalować od małych aplikacji opartych na kontrolerze przy użyciu zaawansowanych procesorów RISC i DSP.</span><span class="sxs-lookup"><span data-stu-id="e7754-107">Unlike many other GUI implementations, GUIX is designed to be versatile—easily scaling from small micro-controller-based applications to those that use powerful RISC and DSP processors.</span></span> <span data-ttu-id="e7754-108">Jest to bardzo zróżnicowane dla domeny publicznej lub innych implementacji komercyjnych pierwotnie przeznaczonych dla środowisk stacji roboczych, ale a następnie zostały podzielone na osadzone projekty.</span><span class="sxs-lookup"><span data-stu-id="e7754-108">This is in sharp contrast to public domain or other commercial implementations originally intended for workstation environments but then squeezed into embedded designs.</span></span> <span data-ttu-id="e7754-109">Omówienie funkcji GUIX:</span><span class="sxs-lookup"><span data-stu-id="e7754-109">An overview of GUIX features follows:</span></span>

- <span data-ttu-id="e7754-110">Łatwe korzystanie z narzędzia projektowania opartego na hoście GUIX Studio</span><span class="sxs-lookup"><span data-stu-id="e7754-110">Easy to use with host-based design tool GUIX Studio</span></span>

- <span data-ttu-id="e7754-111">Środowisko uruchomieniowe Win32 GUIX dla pełnego prototypu hostowanego</span><span class="sxs-lookup"><span data-stu-id="e7754-111">Win32 GUIX run-time environment for complete hosted prototyping</span></span>

- <span data-ttu-id="e7754-112">Obsługuje większość procesorów obsługiwanych przez ThreadX</span><span class="sxs-lookup"><span data-stu-id="e7754-112">Supports most processors supported by ThreadX</span></span>

- <span data-ttu-id="e7754-113">Zapisywane wyłącznie w ANSI C</span><span class="sxs-lookup"><span data-stu-id="e7754-113">Written exclusively in ANSI C</span></span>

- <span data-ttu-id="e7754-114">Neutralne</span><span class="sxs-lookup"><span data-stu-id="e7754-114">Endian neutral</span></span>

- <span data-ttu-id="e7754-115">Najmniejszy, Fast graficzny interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="e7754-115">Smallest, Fasted Embedded GUI</span></span>

- <span data-ttu-id="e7754-116">Konfigurowalny czas wykonywania, liczba obiektów, rozmiar ekranu itp.</span><span class="sxs-lookup"><span data-stu-id="e7754-116">Run-time configurable, number of objects, screen size, etc.</span></span>

- <span data-ttu-id="e7754-117">Łatwy do zapisu interfejs sterownika wyświetlania</span><span class="sxs-lookup"><span data-stu-id="e7754-117">Easy to write display driver interface</span></span>

- <span data-ttu-id="e7754-118">Kolor (do 32 BPP głębi kolorów), obsługa monochromatyczna i Skala szarości</span><span class="sxs-lookup"><span data-stu-id="e7754-118">Color (up to 32-bpp color depth), monochrome, and grayscale support</span></span>

- <span data-ttu-id="e7754-119">Obsługa wielu języków za pomocą kodowania ciągów UTF8 i zasobów ciągów</span><span class="sxs-lookup"><span data-stu-id="e7754-119">Multilingual support via UTF8 string encoding and string resources</span></span>

- <span data-ttu-id="e7754-120">Domyślne czcionki bezpłatne i łatwe dodawanie nowych czcionek</span><span class="sxs-lookup"><span data-stu-id="e7754-120">Default free fonts and easy to add new fonts</span></span>

- <span data-ttu-id="e7754-121">Obsługiwane są różne kanwy rysowania o różnych rozmiarach</span><span class="sxs-lookup"><span data-stu-id="e7754-121">Multiple drawing Canvases supported, of various sizes</span></span>

- <span data-ttu-id="e7754-122">Obsługiwane są wiele ekranów o różnych rozmiarach i głębiach kolorów</span><span class="sxs-lookup"><span data-stu-id="e7754-122">Multiple displays of different sizes and color depths supported</span></span>

- <span data-ttu-id="e7754-123">Obsługa przejścia ekranu (zanikanie, ściemnianie, przesuwanie itp.)</span><span class="sxs-lookup"><span data-stu-id="e7754-123">Screen Transition support (fade in, fade out, swipe, etc.)</span></span>

- <span data-ttu-id="e7754-124">Obsługa ekranu dotykowego, gestu i klawiatury wirtualnej</span><span class="sxs-lookup"><span data-stu-id="e7754-124">Touch Screen, Gesture, and Virtual Keyboard Support</span></span>

- <span data-ttu-id="e7754-125">Kompresja mapy bitowej</span><span class="sxs-lookup"><span data-stu-id="e7754-125">Bitmap compression</span></span>

- <span data-ttu-id="e7754-126">Obsługa mieszania alfa</span><span class="sxs-lookup"><span data-stu-id="e7754-126">Alpha Blending Support</span></span>

- <span data-ttu-id="e7754-127">Obsługa symulacji</span><span class="sxs-lookup"><span data-stu-id="e7754-127">Dither Support</span></span>

- <span data-ttu-id="e7754-128">Obsługa antyaliasów</span><span class="sxs-lookup"><span data-stu-id="e7754-128">Anti-Aliasing Support</span></span>

- <span data-ttu-id="e7754-129">Karnacje i motywy</span><span class="sxs-lookup"><span data-stu-id="e7754-129">Skinning and Themes</span></span>

- <span data-ttu-id="e7754-130">Mieszanie kanwy</span><span class="sxs-lookup"><span data-stu-id="e7754-130">Canvas Blending</span></span>

- <span data-ttu-id="e7754-131">Zakończenie zarządzania oknem</span><span class="sxs-lookup"><span data-stu-id="e7754-131">Complete Window Management</span></span>

  - <span data-ttu-id="e7754-132">Relacja nadrzędny/podrzędny</span><span class="sxs-lookup"><span data-stu-id="e7754-132">Parent/Child Relationship</span></span>

  - <span data-ttu-id="e7754-133">Dynamiczne tworzenie, usuwanie, zmiana rozmiarów, przechodzenie</span><span class="sxs-lookup"><span data-stu-id="e7754-133">Dynamic creation, deletion, resizing, moving</span></span>
  - <span data-ttu-id="e7754-134">Oddzielanie obsługi i rysowania zdarzeń</span><span class="sxs-lookup"><span data-stu-id="e7754-134">Separate event handling and drawing</span></span> 
  - <span data-ttu-id="e7754-135">Porządek osi Z</span><span class="sxs-lookup"><span data-stu-id="e7754-135">Z-order</span></span>
  - <span data-ttu-id="e7754-136">Przycinanie i widoki</span><span class="sxs-lookup"><span data-stu-id="e7754-136">Clipping and views</span></span>

- <span data-ttu-id="e7754-137">Obszerny zestaw elementów widget</span><span class="sxs-lookup"><span data-stu-id="e7754-137">Extensive Set of Widgets</span></span>

  - <span data-ttu-id="e7754-138">Różne typy przycisków, suwaki i numery telefonów</span><span class="sxs-lookup"><span data-stu-id="e7754-138">Various button types, sliders, and dials</span></span>

  - <span data-ttu-id="e7754-139">Lista rozwijana</span><span class="sxs-lookup"><span data-stu-id="e7754-139">Drop Down List</span></span>
  
  - <span data-ttu-id="e7754-140">Monit</span><span class="sxs-lookup"><span data-stu-id="e7754-140">Prompt</span></span>

  - <span data-ttu-id="e7754-141">Widok tekstu wielowierszowego</span><span class="sxs-lookup"><span data-stu-id="e7754-141">Multi-Line text view</span></span>
  
  - <span data-ttu-id="e7754-142">Pojedyncze i wielowierszowe wprowadzanie tekstu</span><span class="sxs-lookup"><span data-stu-id="e7754-142">Single and Multi-Line text input</span></span>
  
  - <span data-ttu-id="e7754-143">Pokrętła przewijania liczbowego i tekstowego</span><span class="sxs-lookup"><span data-stu-id="e7754-143">Numeric and Textual Scroll Wheels</span></span>
  
  - <span data-ttu-id="e7754-144">Okna i paski przewijania</span><span class="sxs-lookup"><span data-stu-id="e7754-144">Windows and Scroll Bars</span></span>
  
  - <span data-ttu-id="e7754-145">Pasek postępu promieniowego</span><span class="sxs-lookup"><span data-stu-id="e7754-145">Radial Progress Bar</span></span>
  
  - <span data-ttu-id="e7754-146">Klasy</span><span class="sxs-lookup"><span data-stu-id="e7754-146">Sprite</span></span>

### <a name="ansi-c-source-code"></a><span data-ttu-id="e7754-147">Kod źródłowy ANSI C</span><span class="sxs-lookup"><span data-stu-id="e7754-147">ANSI C Source Code</span></span>

<span data-ttu-id="e7754-148">GUIX jest zapisywana całkowicie w standardzie ANSI C i jest natychmiast przenośny do praktycznie dowolnej architektury procesora, która ma kompilator ANSI C i obsługę ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e7754-148">GUIX is written completely in ANSI C and is portable immediately to virtually any processor architecture that has an ANSI C compiler and ThreadX support.</span></span> <span data-ttu-id="e7754-149">Mimo że Zapisano w standardzie ANSI C, GUIX korzysta z modelu zorientowanego obiektowo i dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="e7754-149">Although written in ANSI C, GUIX uses an object oriented model and inheritance.</span></span>

### <a name="not-a-black-box"></a><span data-ttu-id="e7754-150">To nie jest czarne pole</span><span class="sxs-lookup"><span data-stu-id="e7754-150">Not A Black Box</span></span>

<span data-ttu-id="e7754-151">Większość dystrybucji GUIX obejmuje pełny kod źródłowy języka C.</span><span class="sxs-lookup"><span data-stu-id="e7754-151">Most distributions of GUIX include the complete C source code.</span></span> <span data-ttu-id="e7754-152">Eliminuje to problemy "z czarnym pudełkem" występujące w wielu komercyjnych implementacjach graficznego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e7754-152">This eliminates the “black-box” problems that occur with many commercial GUI implementations.</span></span> <span data-ttu-id="e7754-153">Korzystając z GUIX, deweloperzy aplikacji mogą zobaczyć dokładnie, co robi graficzny interfejs użytkownika — nie ma Mysteries!</span><span class="sxs-lookup"><span data-stu-id="e7754-153">By using GUIX, applications developers can see exactly what the GUI is doing—there are no mysteries!</span></span>

<span data-ttu-id="e7754-154">Kod źródłowy umożliwia również modyfikacje specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7754-154">Having the source code also allows for application specific modifications.</span></span> <span data-ttu-id="e7754-155">Chociaż nie jest to zalecane, korzystne jest, aby mieć możliwość modyfikacji graficznego interfejsu użytkownika, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="e7754-155">Although not recommended, it is certainly beneficial to have the ability to modify the GUI if it is required.</span></span> <span data-ttu-id="e7754-156">Te funkcje są szczególnie wygodne dla deweloperów przyzwyczajonych do pracy z produktami wewnętrznymi lub publicznymi.</span><span class="sxs-lookup"><span data-stu-id="e7754-156">These features are especially comforting to developers accustomed to working with in-house or public domain products.</span></span> <span data-ttu-id="e7754-157">Powinny one mieć kod źródłowy i możliwość jego modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e7754-157">They expect to have source code and the ability to modify it.</span></span> <span data-ttu-id="e7754-158">GUIX to Ultimate oprogramowanie graficznego interfejsu użytkownika dla takich deweloperów.</span><span class="sxs-lookup"><span data-stu-id="e7754-158">GUIX is the ultimate GUI software for such developers.</span></span>

## <a name="embedded-gui-applications"></a><span data-ttu-id="e7754-159">Osadzone aplikacje graficznego interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e7754-159">Embedded GUI Applications</span></span>

<span data-ttu-id="e7754-160">Osadzone aplikacje GUI są aplikacjami, które mają wymagania dotyczące interfejsu użytkownika i są wykonywane w mikroprocesorach ukrytych w produktach, takich jak telefony komórkowe, sprzęt komunikacyjny, silniki motoryzacyjne, drukarki laserowe, urządzenia medyczne itd.</span><span class="sxs-lookup"><span data-stu-id="e7754-160">Embedded GUI applications are applications that have a user interface requirement and execute on microprocessors hidden inside products such as cellular phones, communication equipment, automotive engines, laser printers, medical devices, and so forth.</span></span> <span data-ttu-id="e7754-161">Takie aplikacje prawie zawsze mają pewne ograniczenia dotyczące pamięci i wydajności.</span><span class="sxs-lookup"><span data-stu-id="e7754-161">Such applications almost always have some memory and performance constraints.</span></span> <span data-ttu-id="e7754-162">Innym rozróżnieniem osadzonego interfejsu użytkownika jest to, że oprogramowanie i sprzęt mają dedykowany cel.</span><span class="sxs-lookup"><span data-stu-id="e7754-162">Another distinction of embedded GUI is that their software and hardware have a dedicated purpose.</span></span>

### <a name="real-time-gui-software"></a><span data-ttu-id="e7754-163">Oprogramowanie graficznego interfejsu użytkownika w czasie rzeczywistym</span><span class="sxs-lookup"><span data-stu-id="e7754-163">Real-time GUI Software</span></span>

<span data-ttu-id="e7754-164">W istocie oprogramowanie graficznego interfejsu użytkownika, które musi wykonać przetwarzanie w określonym czasie, jest nazywane oprogramowaniem *graficznego interfejsu użytkownika w czasie rzeczywistym* , a w przypadku wystąpienia ograniczeń czasowych w aplikacjach graficznego interfejsu użytkownika są one klasyfikowane jako aplikacje w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="e7754-164">Basically, GUI software that must perform its processing within an exact period of time is called *real-time GUI* software, and when time constraints are imposed on GUI applications, they are classified as realtime applications.</span></span> <span data-ttu-id="e7754-165">Wbudowane aplikacje graficznego interfejsu użytkownika są prawie zawsze w czasie rzeczywistym ze względu na ich nieodłączną współpracę z zewnętrznym światem.</span><span class="sxs-lookup"><span data-stu-id="e7754-165">Embedded GUI applications are almost always real-time because of their inherent interaction with the external world.</span></span>

## <a name="guix-benefits"></a><span data-ttu-id="e7754-166">Korzyści z GUIX</span><span class="sxs-lookup"><span data-stu-id="e7754-166">GUIX Benefits</span></span>

<span data-ttu-id="e7754-167">Podstawową zaletą korzystania z GUIX dla aplikacji osadzonych są wysoka wydajność, bogate funkcje i bardzo małe wymagania dotyczące pamięci.</span><span class="sxs-lookup"><span data-stu-id="e7754-167">The primary benefits of using GUIX for embedded applications are high-performance, feature rich, and very small memory requirements.</span></span> <span data-ttu-id="e7754-168">GUIX jest również całkowicie zintegrowany z wysoką wydajnością i wielostronicowym systemem operacyjnym Azure RTO ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e7754-168">GUIX is also completely integrated with the high-performance, multitasking Azure RTOS ThreadX real-time operating system.</span></span>

### <a name="improved-responsiveness"></a><span data-ttu-id="e7754-169">Zwiększona czas odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="e7754-169">Improved Responsiveness</span></span>

<span data-ttu-id="e7754-170">Produkt GUIX o wysokiej wydajności umożliwia aplikacjom reagowanie szybciej niż kiedykolwiek wcześniej.</span><span class="sxs-lookup"><span data-stu-id="e7754-170">The high-performance GUIX product enables applications to respond faster than ever before.</span></span> <span data-ttu-id="e7754-171">Jest to szczególnie ważne w przypadku aplikacji osadzonych, które mają znaczną ilość informacji wizualnych lub rygorystyczne wymagania dotyczące chronometrażu na potrzeby wyświetlania takich informacji.</span><span class="sxs-lookup"><span data-stu-id="e7754-171">This is especially important for embedded applications that either have a significant volume of visual information or strict timing requirements on displaying such information.</span></span>

### <a name="software-maintenance"></a><span data-ttu-id="e7754-172">Konserwacja oprogramowania</span><span class="sxs-lookup"><span data-stu-id="e7754-172">Software Maintenance</span></span>

<span data-ttu-id="e7754-173">Korzystanie z programu GUIX umożliwia deweloperom łatwe partycjonowanie aspektów graficznego interfejsu użytkownika aplikacji osadzonej.</span><span class="sxs-lookup"><span data-stu-id="e7754-173">Using GUIX allows developers to easily partition the GUI aspects of their embedded application.</span></span> <span data-ttu-id="e7754-174">Takie partycjonowanie sprawia, że cały proces tworzenia oprogramowania jest łatwy i znacząco ulepsza konserwację w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="e7754-174">This partitioning makes the entire development process easy and significantly enhances future software maintenance.</span></span>

### <a name="increased-throughput"></a><span data-ttu-id="e7754-175">Zwiększona przepływność</span><span class="sxs-lookup"><span data-stu-id="e7754-175">Increased Throughput</span></span>

<span data-ttu-id="e7754-176">Program GUIX zapewnia dostęp do najwyższej jakości graficznego interfejsu użytkownika, który jest bezpośrednio przesyłany do osadzonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7754-176">GUIX provides the highest-performance GUI available, which directly transfers to the embedded application.</span></span> <span data-ttu-id="e7754-177">Aplikacje GUIX mogą przetwarzać informacje o interfejsie użytkownika szybciej niż aplikacje, które nie są GUIX.</span><span class="sxs-lookup"><span data-stu-id="e7754-177">GUIX applications are able to process user interface information faster than non-GUIX applications!</span></span>

### <a name="processor-isolation"></a><span data-ttu-id="e7754-178">Izolacja procesora</span><span class="sxs-lookup"><span data-stu-id="e7754-178">Processor Isolation</span></span>

<span data-ttu-id="e7754-179">GUIX zapewnia niezawodny, niezależny od procesora interfejs między aplikacją a podstawowym procesorem i wyświetlaczem sprzętowym.</span><span class="sxs-lookup"><span data-stu-id="e7754-179">GUIX provides a robust, processor-independent interface between the application and the underlying processor and display hardware.</span></span> <span data-ttu-id="e7754-180">Pozwala to deweloperom skoncentrować się na aspektach wysokiego poziomu interfejsu użytkownika, a nie poświęca dodatkowych czasu na rozwiązywanie problemów ze sprzętem.</span><span class="sxs-lookup"><span data-stu-id="e7754-180">This allows developers to concentrate on the high-level aspects of the user interface rather than spending extra time dealing with display hardware issues.</span></span>

### <a name="ease-of-use"></a><span data-ttu-id="e7754-181">Łatwość użycia</span><span class="sxs-lookup"><span data-stu-id="e7754-181">Ease of Use</span></span>

<span data-ttu-id="e7754-182">GUIX jest zaprojektowana z myślą o deweloperu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7754-182">GUIX is designed with the application developer in mind.</span></span> <span data-ttu-id="e7754-183">Interfejs GUIX i architektura wywołania usługi są łatwe do zrozumienia.</span><span class="sxs-lookup"><span data-stu-id="e7754-183">The GUIX architecture and service call interface are easy to understand.</span></span> <span data-ttu-id="e7754-184">W związku z tym GUIX deweloperzy mogą szybko korzystać z zaawansowanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="e7754-184">As a result, GUIX developers can quickly use its advanced features.</span></span>

### <a name="improve-time-to-market"></a><span data-ttu-id="e7754-185">Popraw czas wprowadzenia na rynek</span><span class="sxs-lookup"><span data-stu-id="e7754-185">Improve Time to Market</span></span>

<span data-ttu-id="e7754-186">Zaawansowane funkcje GUIX przyspieszają proces tworzenia oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="e7754-186">The powerful features of GUIX accelerate the software development process.</span></span> <span data-ttu-id="e7754-187">GUIX abstrakcje większości procesorów i wyświetlania problemów sprzętowych, usuwając te problemy z większości implementacji interfejsu użytkownika aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e7754-187">GUIX abstracts most processor and display hardware issues, thereby removing these concerns from a majority of application user interface implementation.</span></span> <span data-ttu-id="e7754-188">Ta funkcja, która jest powiązana z łatwym w użyciu i zaawansowanym zestawem funkcji, skutkuje szybszym czasem wprowadzenia na rynek.</span><span class="sxs-lookup"><span data-stu-id="e7754-188">This feature, coupled with the ease-of-use and advanced feature set, results in a faster time to market!</span></span>

### <a name="protecting-the-software-investment"></a><span data-ttu-id="e7754-189">Ochrona inwestycji w oprogramowanie</span><span class="sxs-lookup"><span data-stu-id="e7754-189">Protecting the Software Investment</span></span>

<span data-ttu-id="e7754-190">GUIX jest zapisywana wyłącznie w standardzie ANSI C i jest w pełni zintegrowana z systemem operacyjnym Azure RTO ThreadX w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="e7754-190">GUIX is written exclusively in ANSI C and is fully integrated with the Azure RTOS ThreadX real-time operating system.</span></span> <span data-ttu-id="e7754-191">Oznacza to, że aplikacje GUIX są natychmiast przenośne do wszystkich obsługiwanych procesorów ThreadX.</span><span class="sxs-lookup"><span data-stu-id="e7754-191">This means GUIX applications are instantly portable to all ThreadX supported processors.</span></span> <span data-ttu-id="e7754-192">Jeszcze lepiej można obsługiwać całkowicie nową architekturę procesora z ThreadX w ciągu kilku tygodni.</span><span class="sxs-lookup"><span data-stu-id="e7754-192">Better yet, a completely new processor architecture can be supported with ThreadX in a matter of weeks.</span></span> <span data-ttu-id="e7754-193">W związku z tym użycie GUIX gwarantuje, że ścieżka migracji aplikacji i chroni pierwotne inwestycje rozwojowe.</span><span class="sxs-lookup"><span data-stu-id="e7754-193">As a result, using GUIX ensures the application’s migration path and protects the original development investment.</span></span>
