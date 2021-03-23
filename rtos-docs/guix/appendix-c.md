---
title: Dodatek C — style widżetu GUIX
description: Dowiedz się więcej na temat stylów widżetu GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 83d5c5167739e91b7af8fce6b04213f610984fc6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823184"
---
# <a name="appendix-c---guix-widget-styles"></a><span data-ttu-id="6fb72-103">Dodatek C — style widżetu GUIX</span><span class="sxs-lookup"><span data-stu-id="6fb72-103">Appendix C - GUIX Widget Styles</span></span>

<span data-ttu-id="6fb72-104">__***Ogólne Style (używane z większością typów widżetów):***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-104">__***General Styles (Used with most widget types):***__</span></span>

<span data-ttu-id="6fb72-105">**GX_STYLE_BORDER_NONE**</span><span class="sxs-lookup"><span data-stu-id="6fb72-105">**GX_STYLE_BORDER_NONE**</span></span>
  - <span data-ttu-id="6fb72-106">Wartość: 0x00000000</span><span class="sxs-lookup"><span data-stu-id="6fb72-106">Value: 0x00000000</span></span>
  - <span data-ttu-id="6fb72-107">Opis: ten styl służy do rysowania widżetu bez obramowania.</span><span class="sxs-lookup"><span data-stu-id="6fb72-107">Description: Use this style to draw a widget with no border.</span></span>

<span data-ttu-id="6fb72-108">**GX_STYLE_BORDER_RAISED**</span><span class="sxs-lookup"><span data-stu-id="6fb72-108">**GX_STYLE_BORDER_RAISED**</span></span>
  - <span data-ttu-id="6fb72-109">Wartość: 0x00000001</span><span class="sxs-lookup"><span data-stu-id="6fb72-109">Value: 0x00000001</span></span>
  - <span data-ttu-id="6fb72-110">Opis: element widget rysowania z podniesionym obramowaniem.</span><span class="sxs-lookup"><span data-stu-id="6fb72-110">Description: Draw widget with a raised border.</span></span>

<span data-ttu-id="6fb72-111">**GX_STYLE_BORDER_RECESSED**</span><span class="sxs-lookup"><span data-stu-id="6fb72-111">**GX_STYLE_BORDER_RECESSED**</span></span>
  - <span data-ttu-id="6fb72-112">Wartość: 0x00000002</span><span class="sxs-lookup"><span data-stu-id="6fb72-112">Value: 0x00000002</span></span>
  - <span data-ttu-id="6fb72-113">Opis: element widget rysowania z wgłębieniem.</span><span class="sxs-lookup"><span data-stu-id="6fb72-113">Description: Draw widget with a recessed border.</span></span>

<span data-ttu-id="6fb72-114">**GX_STYLE_BORDER_THIN**</span><span class="sxs-lookup"><span data-stu-id="6fb72-114">**GX_STYLE_BORDER_THIN**</span></span>
  - <span data-ttu-id="6fb72-115">Wartość: 0x00000004</span><span class="sxs-lookup"><span data-stu-id="6fb72-115">Value: 0x00000004</span></span>
  - <span data-ttu-id="6fb72-116">Opis: Rysuj obramowanie o szerokości jednopikselowej.</span><span class="sxs-lookup"><span data-stu-id="6fb72-116">Description: Draw a one-pixel width border.</span></span>

<span data-ttu-id="6fb72-117">**GX_STYLE_BORDER_THICK**</span><span class="sxs-lookup"><span data-stu-id="6fb72-117">**GX_STYLE_BORDER_THICK**</span></span> 
  - <span data-ttu-id="6fb72-118">Wartość: 0x00000008</span><span class="sxs-lookup"><span data-stu-id="6fb72-118">Value: 0x00000008</span></span>
  - <span data-ttu-id="6fb72-119">Opis: element widget rysowania o grubej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="6fb72-119">Description: Draw widget with a thick border.</span></span>

<span data-ttu-id="6fb72-120">**GX_STYLE_BORDER_MASK**</span><span class="sxs-lookup"><span data-stu-id="6fb72-120">**GX_STYLE_BORDER_MASK**</span></span>
  - <span data-ttu-id="6fb72-121">Wartość: 0x0000000f</span><span class="sxs-lookup"><span data-stu-id="6fb72-121">Value: 0x0000000f</span></span>
  - <span data-ttu-id="6fb72-122">Opis: wartość maski używana do testowania tylko pól stylu elementu członkowskiego stylu widżetu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-122">Description: Mask value used to test only the style fields of the widget style member.</span></span>

<span data-ttu-id="6fb72-123">**GX_STYLE_TRANSPARENT**</span><span class="sxs-lookup"><span data-stu-id="6fb72-123">**GX_STYLE_TRANSPARENT**</span></span>
  - <span data-ttu-id="6fb72-124">Wartość: 0x10000000</span><span class="sxs-lookup"><span data-stu-id="6fb72-124">Value: 0x10000000</span></span>
  - <span data-ttu-id="6fb72-125">Opis: Utwórz widżet, który jest co najmniej częściowo przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="6fb72-125">Description: Create a widget that is at least partially transparent.</span></span> <span data-ttu-id="6fb72-126">Ten styl powinien być używany, gdy widżet nie rysuje w pełni nieprzezroczysty, w tym widżetów, które rysują półprzezroczysty Pixelmap jako tło widżetu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-126">This style should be used when a widget does not draw itself fully opaque, including widgets that draw a semi-transparent pixelmap as the widget background.</span></span> <span data-ttu-id="6fb72-127">Ta flaga stylu informuje GUIX, że element nadrzędny widget musi być rysowany w celu odświeżenia obszaru tła widżetu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-127">This style flag informs GUIX that the widget parent must be drawn to refresh the widget background area.</span></span>

<span data-ttu-id="6fb72-128">**GX_STYLE_DRAW_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="6fb72-128">**GX_STYLE_DRAW_SELECTED**</span></span>
  - <span data-ttu-id="6fb72-129">Wartość: 0x20000000</span><span class="sxs-lookup"><span data-stu-id="6fb72-129">Value: 0x20000000</span></span>
  - <span data-ttu-id="6fb72-130">Opis: Określ, czy element widget ma być rysowany przy użyciu wybranych kolorów i czcionek stanu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-130">Description: Specify that the widget should be drawn using selected state colors and fonts.</span></span> <span data-ttu-id="6fb72-131">Różne typy widżetów używają stylu DRAW_SELECTED na różne sposoby wskazywania widżetu jest aktualnie zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="6fb72-131">Different widget types use the DRAW_SELECTED style in different ways to indicate the widget is currently selected.</span></span>

<span data-ttu-id="6fb72-132">**GX_STYLE_ENABLED**</span><span class="sxs-lookup"><span data-stu-id="6fb72-132">**GX_STYLE_ENABLED**</span></span>
  - <span data-ttu-id="6fb72-133">Wartość: 0x40000000</span><span class="sxs-lookup"><span data-stu-id="6fb72-133">Value: 0x40000000</span></span>
  - <span data-ttu-id="6fb72-134">Opis: Oznacz widżet jako włączony, co pozwala widżetowi akceptować zdarzenia wejściowe użytkownika i generować sygnały wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="6fb72-134">Description: Mark the widget as enabled, which allows the widget to accept user input events and generate output signals.</span></span>
  
<span data-ttu-id="6fb72-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span><span class="sxs-lookup"><span data-stu-id="6fb72-135">**GX_STYLE_DYNAMICALLY_ALLOCATED**</span></span>
  - <span data-ttu-id="6fb72-136">Wartość: 0x80000000</span><span class="sxs-lookup"><span data-stu-id="6fb72-136">Value: 0x80000000</span></span>
  - <span data-ttu-id="6fb72-137">Opis: wskazuje, że pamięć blokowa kontrolki widżetu jest przydzielana dynamicznie przy użyciu usługi gx_system_memory_allocator podczas tworzenia elementu widget, a pamięć bloku sterowania jest zwalniana, jeśli widżet zostanie zniszczony.</span><span class="sxs-lookup"><span data-stu-id="6fb72-137">Description: Indicates the widget control block memory is dynamically allocated using the gx_system_memory_allocator service when the widget is created, and the control block memory is freed if the widget is destroyed.</span></span>

<span data-ttu-id="6fb72-138">**GX_STYLE_USE_LOCAL_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="6fb72-138">**GX_STYLE_USE_LOCAL_ALPHA**</span></span>
  - <span data-ttu-id="6fb72-139">Wartość: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="6fb72-139">Value: 0x01000000</span></span>
  - <span data-ttu-id="6fb72-140">Opis: instruuje funkcje rysowania GUIX do użycia lokalnej wartości alfa widżetu podczas rysowania widżetu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-140">Description: Instructs GUIX drawing functions to use the local widget alpha value when drawing the widget.</span></span> <span data-ttu-id="6fb72-141">Ta flaga jest zwykle używana przez wewnętrzną logikę GUIX do implementowania animacji zanikania elementu widget.</span><span class="sxs-lookup"><span data-stu-id="6fb72-141">This flag is normally used by the internal GUIX logic to implement widget fading animations.</span></span>


<span data-ttu-id="6fb72-142">__***Style wyrównania tekstu (style zastosowane do wszystkich elementów widget, które rysują tekst):***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-142">__***Text Alignment Styles (styles applied to all widgets that draw text):***__</span></span>

<span data-ttu-id="6fb72-143">**GX_STYLE_TEXT_LEFT**</span><span class="sxs-lookup"><span data-stu-id="6fb72-143">**GX_STYLE_TEXT_LEFT**</span></span>
  - <span data-ttu-id="6fb72-144">Wartość: 0x00001000</span><span class="sxs-lookup"><span data-stu-id="6fb72-144">Value: 0x00001000</span></span>
  - <span data-ttu-id="6fb72-145">Opis: tekst jest rysowany wyrównany do lewej w obszarze klienta widżetu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-145">Description: Text is drawn left-aligned within the widget client area.</span></span>

<span data-ttu-id="6fb72-146">**GX_STYLE_TEXT_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="6fb72-146">**GX_STYLE_TEXT_RIGHT**</span></span> 
  - <span data-ttu-id="6fb72-147">Wartość: 0x00002000</span><span class="sxs-lookup"><span data-stu-id="6fb72-147">Value: 0x00002000</span></span>
  - <span data-ttu-id="6fb72-148">Opis: tekst jest rysowany do prawej strony w obszarze klienta widżetu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-148">Description: Text is drawn right-aligned within the widget client area.</span></span>

<span data-ttu-id="6fb72-149">**GX_STYLE_TEXT_CENTER**</span><span class="sxs-lookup"><span data-stu-id="6fb72-149">**GX_STYLE_TEXT_CENTER**</span></span>
  - <span data-ttu-id="6fb72-150">Wartość: 0x00004000</span><span class="sxs-lookup"><span data-stu-id="6fb72-150">Value: 0x00004000</span></span>
  - <span data-ttu-id="6fb72-151">Opis: tekst jest rysowany jako wyrównany do środka w obszarze klienta widżetu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-151">Description: Text is drawn center-aligned within the widget client area.</span></span>

<span data-ttu-id="6fb72-152">**GX_STYLE_TEXT_COPY**</span><span class="sxs-lookup"><span data-stu-id="6fb72-152">**GX_STYLE_TEXT_COPY**</span></span>
  - <span data-ttu-id="6fb72-153">Wartość: 0x00008000</span><span class="sxs-lookup"><span data-stu-id="6fb72-153">Value: 0x00008000</span></span>
  - <span data-ttu-id="6fb72-154">Opis: Domyślnie elementy widget, które rysują tekst, zachowują tylko wskaźnik do tekstu, który jest przesyłany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="6fb72-154">Description: By default, widgets that draw text keep only a pointer to the text which is passed in by the application.</span></span> <span data-ttu-id="6fb72-155">Dla statycznie zdefiniowanego tekstu, który jest zdefiniowany w tabeli ciągów, nie istnieje powód, aby element widget miał prywatną kopię przypisanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-155">For statically defined text that is defined within the string table, there is no reason for the widget to make a private copy of the text assigned.</span></span> <span data-ttu-id="6fb72-156">Jeśli jednak tekst przypisany do widżetu jest tworzony dynamicznie przy użyciu funkcji, takich jak przebieg () lub gx_utility_ltoa, to często wygodniejsze jest poinformowanie widżetu, aby zachować jego prywatną kopię dowolnego przypisanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-156">However, if the text assigned to a widget is created dynamically using functions like sprint() or gx_utility_ltoa, then it is often convenient to tell the widget to keep it’s own private copy of any text assigned.</span></span> <span data-ttu-id="6fb72-157">Dzięki temu aplikacja może używać zmiennych automatycznych lub tymczasowych podczas definiowania ciągu tekstowego, gdy w przeciwnym razie aplikacja będzie wymagała zdefiniowania statycznie zdefiniowanych tablic znaków dla każdego widżetu tekstu, który używa dynamicznie zdefiniowanego tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-157">This allows the application to use automatic or temporary variables when defining the text string, when the application would otherwise be required to define statically defined character arrays for each text widget that is using dynamically defined text.</span></span> <span data-ttu-id="6fb72-158">Gdy ta flaga stylu zostanie ustawiona, widżet użyje funkcji gx_system_memory_allocator do dynamicznego przydzielenia bloku pamięci wymaganego do przechowywania prywatnej kopii przypisanego ciągu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-158">When this style flag is set, the widget will use the gx_system_memory_allocator function to dynamically allocate the memory block needed to hold a private copy of the assigned string.</span></span> <span data-ttu-id="6fb72-159">W związku z tym użycie tej flagi stylu jest oznaczane przez aplikację definiującą memory_allocator i memory_deallocator funkcje.</span><span class="sxs-lookup"><span data-stu-id="6fb72-159">Therefore using this style flag is predicated on the application defining memory_allocator and memory_deallocator functions.</span></span> <span data-ttu-id="6fb72-160">GX_STYLE_TEXT_COPY nie powinno być czyszczone po ustawieniu i dlatego spowoduje to nieprzewidywalne wyniki.</span><span class="sxs-lookup"><span data-stu-id="6fb72-160">GX_STYLE_TEXT_COPY should not be cleared after it has been set, and doing so will cause unpredictable results.</span></span>

<span data-ttu-id="6fb72-161">__***Style przycisków (Zastosuj tylko do typów widżetów GUIX Button):***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-161">__***Button Styles (apply only to GUIX button widget types):***__</span></span>

<span data-ttu-id="6fb72-162">**GX_STYLE_BUTTON_PUSHED**</span><span class="sxs-lookup"><span data-stu-id="6fb72-162">**GX_STYLE_BUTTON_PUSHED**</span></span>
  - <span data-ttu-id="6fb72-163">0x00000010 wartości</span><span class="sxs-lookup"><span data-stu-id="6fb72-163">Value 0x00000010</span></span>
  - <span data-ttu-id="6fb72-164">Opis: wskazuje, że przycisk jest w stanie wypchnięcie lub zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="6fb72-164">Description: Indicates the button is in the pushed or selected state.</span></span>

<span data-ttu-id="6fb72-165">**GX_STYLE_BUTTON_TOGGLE**</span><span class="sxs-lookup"><span data-stu-id="6fb72-165">**GX_STYLE_BUTTON_TOGGLE**</span></span>
  - <span data-ttu-id="6fb72-166">0x00000020 wartości</span><span class="sxs-lookup"><span data-stu-id="6fb72-166">Value 0x00000020</span></span>
  - <span data-ttu-id="6fb72-167">Opis: przycisk powoduje przełączenie stanu między wypychaniem i wypchnięciem po każdym kliknięciu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="6fb72-167">Description: Button will switch status between pushed and unpushed on every click event.</span></span> <span data-ttu-id="6fb72-168">Ten styl jest często używany z przyciskami stylu "CheckBox".</span><span class="sxs-lookup"><span data-stu-id="6fb72-168">This style is commonly used with “checkbox” style buttons.</span></span>

<span data-ttu-id="6fb72-169">**GX_STYLE_BUTTON_RADIO**</span><span class="sxs-lookup"><span data-stu-id="6fb72-169">**GX_STYLE_BUTTON_RADIO**</span></span>
  - <span data-ttu-id="6fb72-170">0x00000040 wartości</span><span class="sxs-lookup"><span data-stu-id="6fb72-170">Value 0x00000040</span></span>
  - <span data-ttu-id="6fb72-171">Opis: ten styl wskazuje, że przycisk będzie wyłączny, i usuń zaznaczenie dowolnego elementu równorzędnego przycisku po zaznaczeniu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-171">Description: This style indicates the button will be exclusive, and deselect any button siblings when selected.</span></span> <span data-ttu-id="6fb72-172">Ten styl jest często używany z przycisków opcji stylu "przycisk radiowy".</span><span class="sxs-lookup"><span data-stu-id="6fb72-172">This style is commonly used with “radio button” style buttons.</span></span>

<span data-ttu-id="6fb72-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span><span class="sxs-lookup"><span data-stu-id="6fb72-173">**GX_STYLE_BUTTON_EVENT_ON_PUSH**</span></span>
  - <span data-ttu-id="6fb72-174">Wartość: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="6fb72-174">Value: 0x00000080</span></span>
  - <span data-ttu-id="6fb72-175">Opis: wskazuje, że przycisk generuje zdarzenie kliknięcia po pierwszym wypchnięciu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-175">Description: Indicates the button generates a click event when initially pushed.</span></span> <span data-ttu-id="6fb72-176">Domyślną operacją jest wygenerowanie zdarzenia kliknięcia po wydaniu przycisku.</span><span class="sxs-lookup"><span data-stu-id="6fb72-176">The default operation is to generate a click event when the button is released.</span></span>

<span data-ttu-id="6fb72-177">**GX_STYLE_BUTTON_REPEAT**</span><span class="sxs-lookup"><span data-stu-id="6fb72-177">**GX_STYLE_BUTTON_REPEAT**</span></span>
  - <span data-ttu-id="6fb72-178">0x00000100 wartości</span><span class="sxs-lookup"><span data-stu-id="6fb72-178">Value 0x00000100</span></span>
  - <span data-ttu-id="6fb72-179">Opis: wskazuje, że przycisk powinien wysyłać powtarzające się zdarzenia kliknięcia do elementu nadrzędnego przycisku, gdy przycisk jest przechowywany w stanie pushd.</span><span class="sxs-lookup"><span data-stu-id="6fb72-179">Description: Indicates the button should send repeated click events to the button parent when the button is held in the pushed state.</span></span>

<span data-ttu-id="6fb72-180">__***Style list (dotyczy tylko typów widżetów listy GUIX):***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-180">__***List Styles (apply only to GUIX list widget types):***__</span></span>

<span data-ttu-id="6fb72-181">**GX_STYLE_CENTER_SELECTED**</span><span class="sxs-lookup"><span data-stu-id="6fb72-181">**GX_STYLE_CENTER_SELECTED**</span></span> 
  - <span data-ttu-id="6fb72-182">Wartość: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="6fb72-182">Value: 0x00000010</span></span>
  - <span data-ttu-id="6fb72-183">Opis: zastrzeżony</span><span class="sxs-lookup"><span data-stu-id="6fb72-183">Description: Reserved</span></span>

<span data-ttu-id="6fb72-184">**GX_STYLE_WRAP**</span><span class="sxs-lookup"><span data-stu-id="6fb72-184">**GX_STYLE_WRAP**</span></span>
  - <span data-ttu-id="6fb72-185">0x00000020 wartości</span><span class="sxs-lookup"><span data-stu-id="6fb72-185">Value 0x00000020</span></span>
  - <span data-ttu-id="6fb72-186">Opis: elementy podrzędne listy są zawijane od początku do końca, gdy lista jest przeciągana lub przewijana poza indeks listy początkowej lub końcowej.</span><span class="sxs-lookup"><span data-stu-id="6fb72-186">Description: The list children wrap from start to end when the list is dragged or scrolled past the starting or ending list index.</span></span>

<span data-ttu-id="6fb72-187">**GX_STYLE_FLICKABLE**</span><span class="sxs-lookup"><span data-stu-id="6fb72-187">**GX_STYLE_FLICKABLE**</span></span>
  - <span data-ttu-id="6fb72-188">Wartość: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="6fb72-188">Value: 0x00000040</span></span>
  - <span data-ttu-id="6fb72-189">Opis: zastrzeżony</span><span class="sxs-lookup"><span data-stu-id="6fb72-189">Description: Reserved</span></span>

<span data-ttu-id="6fb72-190">__***Przycisk Pixelmap i style przycisków ikon:***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-190">__***Pixelmap Button and Icon Button Styles:***__</span></span>

<span data-ttu-id="6fb72-191">**GX_STYLE_HALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="6fb72-191">**GX_STYLE_HALIGN_CENTER**</span></span>
  - <span data-ttu-id="6fb72-192">Wartość: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="6fb72-192">Value: 0x00010000</span></span>
  - <span data-ttu-id="6fb72-193">Opis: przycisk Pixelmap powinien być wyrównany do środka w granicy przycisku na osi poziomej.</span><span class="sxs-lookup"><span data-stu-id="6fb72-193">Description: The button pixelmap should be center aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="6fb72-194">**GX_STYLE_HALIGN_LEFT**</span><span class="sxs-lookup"><span data-stu-id="6fb72-194">**GX_STYLE_HALIGN_LEFT**</span></span>
  - <span data-ttu-id="6fb72-195">Wartość: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="6fb72-195">Value: 0x00020000</span></span>
  - <span data-ttu-id="6fb72-196">Opis: przycisk Pixelmap powinien być wyrównany do lewej w obrębie granicy przycisku na osi poziomej.</span><span class="sxs-lookup"><span data-stu-id="6fb72-196">Description: The button pixelmap should be left aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="6fb72-197">**GX_STYLE_HALIGN_RIGHT**</span><span class="sxs-lookup"><span data-stu-id="6fb72-197">**GX_STYLE_HALIGN_RIGHT**</span></span>
  - <span data-ttu-id="6fb72-198">0x00040000 wartości</span><span class="sxs-lookup"><span data-stu-id="6fb72-198">Value 0x00040000</span></span>
  - <span data-ttu-id="6fb72-199">Opis: przycisk Pixelmap powinien być wyrównany do prawej w granicach przycisku na osi poziomej.</span><span class="sxs-lookup"><span data-stu-id="6fb72-199">Description: The button pixelmap should be right aligned within the button boundary on the horizontal axis.</span></span>

<span data-ttu-id="6fb72-200">**GX_STYLE_VALIGN_CENTER**</span><span class="sxs-lookup"><span data-stu-id="6fb72-200">**GX_STYLE_VALIGN_CENTER**</span></span>
  - <span data-ttu-id="6fb72-201">0x00080000 wartości</span><span class="sxs-lookup"><span data-stu-id="6fb72-201">Value 0x00080000</span></span>
  - <span data-ttu-id="6fb72-202">Opis: przycisk Pixelmap powinien być wyrównany do środka w granicy przycisku na osi pionowej.</span><span class="sxs-lookup"><span data-stu-id="6fb72-202">Description: The button pixelmap should be center aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="6fb72-203">**GX_STYLE_VALIGN_TOP**</span><span class="sxs-lookup"><span data-stu-id="6fb72-203">**GX_STYLE_VALIGN_TOP**</span></span>
  - <span data-ttu-id="6fb72-204">Wartość: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="6fb72-204">Value: 0x00100000</span></span>
  - <span data-ttu-id="6fb72-205">Opis: przycisk Pixelmap powinien być wyrównany do góry w obrębie granicy przycisku na osi pionowej.</span><span class="sxs-lookup"><span data-stu-id="6fb72-205">Description: The button pixelmap should be top aligned within the button boundary on the vertical axis.</span></span>

<span data-ttu-id="6fb72-206">**GX_STYLE_VALIGN_BOTTOM**</span><span class="sxs-lookup"><span data-stu-id="6fb72-206">**GX_STYLE_VALIGN_BOTTOM**</span></span>
  - <span data-ttu-id="6fb72-207">Wartość: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="6fb72-207">Value: 0x00200000</span></span>
  - <span data-ttu-id="6fb72-208">Opis: przycisk Pixelmap powinien być wyrównany do dołu w ramach granicy przycisku na pionowej osi poziomej.</span><span class="sxs-lookup"><span data-stu-id="6fb72-208">Description: The button pixelmap should be bottom aligned within the button boundary on the vertical horizontal axis.</span></span>

<span data-ttu-id="6fb72-209">__***Style suwaka (Appy tylko do GX_SLIDER i pochodnych typów widżetów):***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-209">__***Slider Styles (Appy only to GX_SLIDER and derived widget types):***__</span></span>

<span data-ttu-id="6fb72-210">**GX_STYLE_SHOW_NEEDLE**</span><span class="sxs-lookup"><span data-stu-id="6fb72-210">**GX_STYLE_SHOW_NEEDLE**</span></span>
  - <span data-ttu-id="6fb72-211">Wartość: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="6fb72-211">Value: 0x00000200</span></span>
  - <span data-ttu-id="6fb72-212">Opis: ten styl musi być dołączony do suwaka, aby narysować wskaźnik wskazówki.</span><span class="sxs-lookup"><span data-stu-id="6fb72-212">Description: This style must be included for the slider to draw the needle indicator.</span></span> <span data-ttu-id="6fb72-213">Ten styl można wyłączyć, jeśli aplikacja chce wyłączyć wskazówki suwaka lub narysować niestandardowy wskaźnik wskazówki.</span><span class="sxs-lookup"><span data-stu-id="6fb72-213">This style can be disabled if the application wants to disable the slider needle or draw a custom needle indicator.</span></span>

<span data-ttu-id="6fb72-214">**GX_STYLE_SHOW_TICKMARKS**</span><span class="sxs-lookup"><span data-stu-id="6fb72-214">**GX_STYLE_SHOW_TICKMARKS**</span></span>
  - <span data-ttu-id="6fb72-215">Wartość: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="6fb72-215">Value: 0x00000400</span></span>
  - <span data-ttu-id="6fb72-216">Opis: widżet Slider wykona rysowanie oprogramowania linii znaczników kreskowanych, gdy ten styl jest włączony.</span><span class="sxs-lookup"><span data-stu-id="6fb72-216">Description: The slider widget will do software drawing of dashed tickmark lines when this style is enabled.</span></span>

<span data-ttu-id="6fb72-217">**GX_STYLE_SLIDER_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="6fb72-217">**GX_STYLE_SLIDER_VERTICAL**</span></span>
  - <span data-ttu-id="6fb72-218">0x00000800 wartości</span><span class="sxs-lookup"><span data-stu-id="6fb72-218">Value 0x00000800</span></span>
  - <span data-ttu-id="6fb72-219">Opis: Ustaw tę flagę stylu, aby utworzyć pionowy suwak, i wyczyść flagę tego stylu, aby utworzyć suwak poziomy.</span><span class="sxs-lookup"><span data-stu-id="6fb72-219">Description: Set this style flag to create a vertical slider, and clear this style flag to create a horizontal slider.</span></span>

<span data-ttu-id="6fb72-220">__***Style ikon (dotyczy tylko typów widżetów GX_SPRITE):***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-220">__***Sprite Styles (Applies only to GX_SPRITE widget types):***__</span></span>

<span data-ttu-id="6fb72-221">**GX_STYLE_SPRITE_AUTO**</span><span class="sxs-lookup"><span data-stu-id="6fb72-221">**GX_STYLE_SPRITE_AUTO**</span></span>
  - <span data-ttu-id="6fb72-222">Wartość: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="6fb72-222">Value: 0x00000010</span></span>
  - <span data-ttu-id="6fb72-223">Opis: wskazuje, że animacja Sprite zostanie uruchomiona automatycznie, gdy widżet Sprite otrzyma zdarzenie GX_EVENT_SHOW.</span><span class="sxs-lookup"><span data-stu-id="6fb72-223">Description: Indicates the sprite animation will run automatically when the sprite widget received the GX_EVENT_SHOW event.</span></span>

<span data-ttu-id="6fb72-224">**GX_STYLE_SPRITE_LOOP**</span><span class="sxs-lookup"><span data-stu-id="6fb72-224">**GX_STYLE_SPRITE_LOOP**</span></span>
  - <span data-ttu-id="6fb72-225">Wartość: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="6fb72-225">Value: 0x00000020</span></span>
  - <span data-ttu-id="6fb72-226">Opis: w tym stylu widżet Sprite będzie ciągle przechodził do pętli przez klatki animacji Sprite, dopóki Sprite nie zostanie zatrzymany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="6fb72-226">Description: With this style, the sprite widget will continuously loop through sprite animation frames until the sprite is stopped by the application.</span></span>

<span data-ttu-id="6fb72-227">__***Style suwaka Pixelmap:***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-227">__***Pixelmap Slider Styles:***__</span></span>

<span data-ttu-id="6fb72-228">**GX_STYLE_TILE_BACKGROUND**</span><span class="sxs-lookup"><span data-stu-id="6fb72-228">**GX_STYLE_TILE_BACKGROUND**</span></span>
  - <span data-ttu-id="6fb72-229">0x00001000 wartości</span><span class="sxs-lookup"><span data-stu-id="6fb72-229">Value 0x00001000</span></span>
  - <span data-ttu-id="6fb72-230">Opis: obraz tła suwaka jest rozsunięty, aby wypełnić prostokąt powiązany z ikoną.</span><span class="sxs-lookup"><span data-stu-id="6fb72-230">Description: The slider background image is tiled to fill the sprite bounding rectangle.</span></span> <span data-ttu-id="6fb72-231">Dzięki temu mały pionowy lub poziomy obraz rozłożony będzie używany do wypełnienia tła suwaka.</span><span class="sxs-lookup"><span data-stu-id="6fb72-231">This allows a small vertical or horizontal stripe image to be used to fill the slider background.</span></span>

<span data-ttu-id="6fb72-232">__***Dodatkowe style paska postępu:***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-232">__***Additional Progress Bar Styles:***__</span></span>

<span data-ttu-id="6fb72-233">**GX_STYLE_PROGRESS_PERCENT**</span><span class="sxs-lookup"><span data-stu-id="6fb72-233">**GX_STYLE_PROGRESS_PERCENT**</span></span>
  - <span data-ttu-id="6fb72-234">Wartość: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="6fb72-234">Value: 0x00000010</span></span>
  - <span data-ttu-id="6fb72-235">Opis: po ustawieniu tego stylu pasek postępu będzie miał wartość procentową, a nie wartość pierwotną.</span><span class="sxs-lookup"><span data-stu-id="6fb72-235">Description: When this style is set, the progress bar will draw  bar value as a percentage rather than a raw value.</span></span> <span data-ttu-id="6fb72-236">Tekst jest wyśrodkowany w prostokącie związanym z paskiem postępu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-236">The text is centered in the progress bar bounding rectangle.</span></span>

<span data-ttu-id="6fb72-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span><span class="sxs-lookup"><span data-stu-id="6fb72-237">**GX_STYLE_PROGRESS_TEXT_DRAW**</span></span>
  - <span data-ttu-id="6fb72-238">Wartość: 0x00000020</span><span class="sxs-lookup"><span data-stu-id="6fb72-238">Value: 0x00000020</span></span>
  - <span data-ttu-id="6fb72-239">Opis: Narysuj bieżącą wartość paska postępu jako tekst dziesiętny wyśrodkowany na pasku postępu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-239">Description: Draw the current progress bar value as decimal text centered within the progress bar.</span></span>

<span data-ttu-id="6fb72-240">**GX_STYLE_PROGRESS_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="6fb72-240">**GX_STYLE_PROGRESS_VERTICAL**</span></span>
  - <span data-ttu-id="6fb72-241">Wartość: 0x0000040</span><span class="sxs-lookup"><span data-stu-id="6fb72-241">Value: 0x0000040</span></span>
  - <span data-ttu-id="6fb72-242">Opis: wskazuje, że postęp ma orientację w pionie.</span><span class="sxs-lookup"><span data-stu-id="6fb72-242">Description: Indicate the progress is vertically oriented.</span></span> <span data-ttu-id="6fb72-243">Wartość domyślna to orientacja pozioma.</span><span class="sxs-lookup"><span data-stu-id="6fb72-243">The default is horizontal orientation.</span></span>

<span data-ttu-id="6fb72-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span><span class="sxs-lookup"><span data-stu-id="6fb72-244">**GX_STYLE_PROGRESS_SEGMENT_FILL**:</span></span>
  - <span data-ttu-id="6fb72-245">**Wartość**: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="6fb72-245">**Value**: 0x00000100</span></span>
  - <span data-ttu-id="6fb72-246">Opis: wartość paska postępu jest wskazywana przy użyciu wypełnionych prostokątów, a nie wypełnienia pełnego.</span><span class="sxs-lookup"><span data-stu-id="6fb72-246">Description: The progress bar value is indicated with segmented filled rectangles, rather than a solid fill.</span></span>

<span data-ttu-id="6fb72-247">__***Dodatkowe style paska postępu promieniowego:***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-247">__***Additional Radial Progress Bar Styles:***__</span></span>

<span data-ttu-id="6fb72-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="6fb72-248">**GX_STYLE_RADIAL_PROGRESS_ALIAS**</span></span>
  - <span data-ttu-id="6fb72-249">Wartość: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="6fb72-249">Value: 0x00000200</span></span>
  - <span data-ttu-id="6fb72-250">Opis: Narysuj Radialny pasek postępu przy użyciu stylów pędzla z wygładzaniem.</span><span class="sxs-lookup"><span data-stu-id="6fb72-250">Description: Draw the radial progress bar using anti-aliased brush styles.</span></span> <span data-ttu-id="6fb72-251">Wymaga to większej przepustowości procesora, ale również zapewnia wrażenie wz.</span><span class="sxs-lookup"><span data-stu-id="6fb72-251">This requires more CPU bandwidth but also produces a nicer appearance.</span></span> <span data-ttu-id="6fb72-252">W przypadku docelowych wydajności procesora CPU, czyszczenie tej flagi stylu spowoduje szybsze Rysowanie.</span><span class="sxs-lookup"><span data-stu-id="6fb72-252">For lower performance CPU targets, clearing this style flag will result in faster drawing speed.</span></span>

<span data-ttu-id="6fb72-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span><span class="sxs-lookup"><span data-stu-id="6fb72-253">**GX_STYLE_RADIAL_PROGRESS_ROUND**</span></span>
  - <span data-ttu-id="6fb72-254">Wartość: 0x00000400</span><span class="sxs-lookup"><span data-stu-id="6fb72-254">Value: 0x00000400</span></span>
  - <span data-ttu-id="6fb72-255">Opis: podczas rysowania łuku słupkowego postępu należy używać stylu pędzla okrągłego. Wartość domyślna to kwadratowy koniec linii.</span><span class="sxs-lookup"><span data-stu-id="6fb72-255">Description: Use a round line end brush style when drawing the radial progress bar arc. The default is a square line end.</span></span>

<span data-ttu-id="6fb72-256">__***Dodatkowe style wprowadzania tekstu:***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-256">__***Additional Text Input Styles:***__</span></span>

<span data-ttu-id="6fb72-257">**GX_STYLE_ CURSOR_BLINK**</span><span class="sxs-lookup"><span data-stu-id="6fb72-257">**GX_STYLE_ CURSOR_BLINK**</span></span>
  - <span data-ttu-id="6fb72-258">Wartość: 0x00000040</span><span class="sxs-lookup"><span data-stu-id="6fb72-258">Value: 0x00000040</span></span>
  - <span data-ttu-id="6fb72-259">Opis: kursor widżetu wprowadzanie tekstu zostanie włączony i wyłączony, a nie jest stały.</span><span class="sxs-lookup"><span data-stu-id="6fb72-259">Description: The text input widget cursor will flash on and off rather than being steady.</span></span>

<span data-ttu-id="6fb72-260">**GX_STYLE_ CURSOR_ALWAYS**</span><span class="sxs-lookup"><span data-stu-id="6fb72-260">**GX_STYLE_ CURSOR_ALWAYS**</span></span>
  - <span data-ttu-id="6fb72-261">Wartość: 0x00000080</span><span class="sxs-lookup"><span data-stu-id="6fb72-261">Value: 0x00000080</span></span>
  - <span data-ttu-id="6fb72-262">Opis</span><span class="sxs-lookup"><span data-stu-id="6fb72-262">Description.</span></span> <span data-ttu-id="6fb72-263">Kursor widżetu wprowadzanie tekstu jest zwykle wyświetlany tylko wtedy, gdy widżet jest właścicielem fokusu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-263">The text input widget cursor is normally only displayed when the widget owns input focus.</span></span> <span data-ttu-id="6fb72-264">Ta flaga stylu sprawia, że kursor będzie zawsze widoczny niezależnie od fokusu danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6fb72-264">This style flag will make the cursor always visible regardless of input focus.</span></span>

<span data-ttu-id="6fb72-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span><span class="sxs-lookup"><span data-stu-id="6fb72-265">**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**</span></span>
  - <span data-ttu-id="6fb72-266">Wartość: 0x00000100</span><span class="sxs-lookup"><span data-stu-id="6fb72-266">Value: 0x00000100</span></span>
  - <span data-ttu-id="6fb72-267">Opis: w przypadku tej flagi stylu Ustaw zdarzenie GX_EVENT_TEXT_EDITED za każdym razem, gdy zdarzenie w dół jest odbierane przez widżet wprowadzania tekstu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-267">Description: With this style flag set the GX_EVENT_TEXT_EDITED event every time key down event is received by the text input widget.</span></span>

<span data-ttu-id="6fb72-268">__***Dodatkowe style okna:***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-268">__***Additional Window Styles:***__</span></span>

<span data-ttu-id="6fb72-269">**GX_STYLE_TILE_WALLPAPER**</span><span class="sxs-lookup"><span data-stu-id="6fb72-269">**GX_STYLE_TILE_WALLPAPER**</span></span>
  - <span data-ttu-id="6fb72-270">Wartość: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="6fb72-270">Value: 0x00040000</span></span>
  - <span data-ttu-id="6fb72-271">Opis: w oknie zostanie umieszczony kafelek każdy przypisany obraz Tapety, aby wypełnić prostokąt klienta okna.</span><span class="sxs-lookup"><span data-stu-id="6fb72-271">Description: The window will tile any assigned wallpaper image to fill the window client rectangle.</span></span>

<span data-ttu-id="6fb72-272">**GX_STYLE_AUTO_HSCROLL**</span><span class="sxs-lookup"><span data-stu-id="6fb72-272">**GX_STYLE_AUTO_HSCROLL**</span></span>
  - <span data-ttu-id="6fb72-273">Wartość: 0x00100000</span><span class="sxs-lookup"><span data-stu-id="6fb72-273">Value: 0x00100000</span></span>
  - <span data-ttu-id="6fb72-274">Opis: zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="6fb72-274">Description: Reserved for future use.</span></span>

<span data-ttu-id="6fb72-275">**GX_STYLE_AUTO_VSCROLL**</span><span class="sxs-lookup"><span data-stu-id="6fb72-275">**GX_STYLE_AUTO_VSCROLL**</span></span>
  - <span data-ttu-id="6fb72-276">Wartość: 0x00200000</span><span class="sxs-lookup"><span data-stu-id="6fb72-276">Value: 0x00200000</span></span>
  - <span data-ttu-id="6fb72-277">Opis: zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="6fb72-277">Description: Reserved for future use.</span></span>

<span data-ttu-id="6fb72-278">__***Dodatkowe style menu:***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-278">__***Additional Menu Styles:***__</span></span>

<span data-ttu-id="6fb72-279">**GX_STYLE_MENU_EXPANDED**</span><span class="sxs-lookup"><span data-stu-id="6fb72-279">**GX_STYLE_MENU_EXPANDED**</span></span>
  - <span data-ttu-id="6fb72-280">Wartość: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="6fb72-280">Value: 0x00000010</span></span>
  - <span data-ttu-id="6fb72-281">Opis: widżet menu harmonijka jest początkowo w stanie rozwiniętym.</span><span class="sxs-lookup"><span data-stu-id="6fb72-281">Description: Accordion menu widget is initially in expanded state.</span></span>

<span data-ttu-id="6fb72-282">__***Dodatkowe style widoku drzewa:***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-282">__***Additional Tree View Styles:***__</span></span>

<span data-ttu-id="6fb72-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span><span class="sxs-lookup"><span data-stu-id="6fb72-283">**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**</span></span>
  - <span data-ttu-id="6fb72-284">Wartość: 0x00000010</span><span class="sxs-lookup"><span data-stu-id="6fb72-284">Value: 0x00000010</span></span>
  - <span data-ttu-id="6fb72-285">Opis: widżet widoku drzewa powinien rysować linie z ikony węzła do węzła drzewa głównego.</span><span class="sxs-lookup"><span data-stu-id="6fb72-285">Description: Tree view widget should draw lines from node icon to root tree node.</span></span>

<span data-ttu-id="6fb72-286">__***Dodatkowe style paska przewijania:***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-286">__***Additional Scrollbar Styles:***__</span></span>

<span data-ttu-id="6fb72-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span><span class="sxs-lookup"><span data-stu-id="6fb72-287">**GX_SCROLLBAR_BACKGROUND_TILE**</span></span>
  - <span data-ttu-id="6fb72-288">Wartość: 0x00010000</span><span class="sxs-lookup"><span data-stu-id="6fb72-288">Value: 0x00010000</span></span>
  - <span data-ttu-id="6fb72-289">Opis: zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="6fb72-289">Description: Reserved for future use.</span></span>

<span data-ttu-id="6fb72-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span><span class="sxs-lookup"><span data-stu-id="6fb72-290">**GX_SCROLLBAR_RELATIVE_THUMB**</span></span>
  - <span data-ttu-id="6fb72-291">Wartość: 0x00020000</span><span class="sxs-lookup"><span data-stu-id="6fb72-291">Value: 0x00020000</span></span>
  - <span data-ttu-id="6fb72-292">Opis: szerokość przycisku przewijania ekranu (dla poziomego paska przewijania) lub wysokość (dla pionowego paska przewijania) jest obliczana na podstawie współczynnika widocznego obszaru okna nadrzędnego do minimalnej i maksymalnej wartości paska przewijania.</span><span class="sxs-lookup"><span data-stu-id="6fb72-292">Description: The scrollbar thumb width (for a horizontal scroll bar) or height (for a vertical scroll bar) are calculated based on the ratio of the visible area of the parent window to the min and max scrollbar range.</span></span>

<span data-ttu-id="6fb72-293">**GX_SCROLLBAR_END_BUTTONS**</span><span class="sxs-lookup"><span data-stu-id="6fb72-293">**GX_SCROLLBAR_END_BUTTONS**</span></span>
  - <span data-ttu-id="6fb72-294">Wartość: 0x00040000</span><span class="sxs-lookup"><span data-stu-id="6fb72-294">Value: 0x00040000</span></span>
  - <span data-ttu-id="6fb72-295">Opis: pasek przewijania automatycznie tworzy i dołącza przyciski na każdym końcu regionu ScrollBar.</span><span class="sxs-lookup"><span data-stu-id="6fb72-295">Description: The scrollbar automatically creates and attaches buttons at each end of the scrollbar region.</span></span>

<span data-ttu-id="6fb72-296">**GX_SCROLLBAR_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="6fb72-296">**GX_SCROLLBAR_VERTICAL**</span></span> 
  - <span data-ttu-id="6fb72-297">Wartość: 0x01000000</span><span class="sxs-lookup"><span data-stu-id="6fb72-297">Value: 0x01000000</span></span>
  - <span data-ttu-id="6fb72-298">Opis: pasek przewijania ma orientację w pionie.</span><span class="sxs-lookup"><span data-stu-id="6fb72-298">Description: The scrollbar is vertically oriented.</span></span>

<span data-ttu-id="6fb72-299">**GX_SCROLLBAR_HORIZONTAL**</span><span class="sxs-lookup"><span data-stu-id="6fb72-299">**GX_SCROLLBAR_HORIZONTAL**</span></span>
  - <span data-ttu-id="6fb72-300">Wartość: 0x02000000</span><span class="sxs-lookup"><span data-stu-id="6fb72-300">Value: 0x02000000</span></span>
  - <span data-ttu-id="6fb72-301">Opis: pasek przewijania ma orientację poziomą.</span><span class="sxs-lookup"><span data-stu-id="6fb72-301">Description: The scrollbar is horizontally oriented.</span></span>

<span data-ttu-id="6fb72-302">__***Style kółka przewijania tekstu:***__</span><span class="sxs-lookup"><span data-stu-id="6fb72-302">__***Text Scroll Wheel Styles:***__</span></span>

<span data-ttu-id="6fb72-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span><span class="sxs-lookup"><span data-stu-id="6fb72-303">**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**</span></span>
  - <span data-ttu-id="6fb72-304">Wartość: 0x00000200</span><span class="sxs-lookup"><span data-stu-id="6fb72-304">Value: 0x00000200</span></span>
  - <span data-ttu-id="6fb72-305">Opis: kółko przewijania używa algorytmu sinusoidalną, aby kółko przewijania pojawiało się w postaci zaokrąglonego kształtu.</span><span class="sxs-lookup"><span data-stu-id="6fb72-305">Description: The scroll wheel uses a Sinusoidal algorithm to make the scroll wheel appear to have a rounded shape.</span></span> <span data-ttu-id="6fb72-306">Ta flaga stylu może zwiększyć znaczący koszt do wydajności widgetu kółka przewijania, ale może również dać kółko realistyczny wygląd 3W.</span><span class="sxs-lookup"><span data-stu-id="6fb72-306">This style flag can add significant overhead to the performance of the scroll wheel widget, but can also give the wheel a 3D realistic appearance.</span></span>