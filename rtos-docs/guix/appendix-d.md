---
title: Dodatek D-GUIX pędzla, kanwy i atrybuty gradientu
description: Dowiedz się więcej na temat GUIX pędzla, kanwy i atrybutów gradientu.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 19c0687a54be244ae395124664b4b6da0f4e90b6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823179"
---
# <a name="appendix-d---guix-brush-canvas-and-gradient-attributes"></a><span data-ttu-id="7c44f-103">Dodatek D-GUIX pędzla, kanwy i atrybuty gradientu</span><span class="sxs-lookup"><span data-stu-id="7c44f-103">Appendix D - GUIX Brush, Canvas and Gradient Attributes</span></span>

<span data-ttu-id="7c44f-104">__**Style pędzla:**__</span><span class="sxs-lookup"><span data-stu-id="7c44f-104">__**Brush Styles:**__</span></span>

<span data-ttu-id="7c44f-105">**GX_BRUSH_OUTLINE**</span><span class="sxs-lookup"><span data-stu-id="7c44f-105">**GX_BRUSH_OUTLINE**</span></span>
- <span data-ttu-id="7c44f-106">Wartość: 0x0000</span><span class="sxs-lookup"><span data-stu-id="7c44f-106">Value: 0x0000</span></span>
- <span data-ttu-id="7c44f-107">Opis: ten styl pędzla dotyczy funkcji rysowania kształtów, takich jak gx_canvas_rectangle_draw lub gx_canvas_polygon_draw.</span><span class="sxs-lookup"><span data-stu-id="7c44f-107">Description: This brush style applies to shape drawing functions such as gx_canvas_rectangle_draw or gx_canvas_polygon_draw.</span></span> <span data-ttu-id="7c44f-108">Ten styl wskazuje, że kształt powinien być wyróżniony, oprócz opcjonalnego wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="7c44f-108">This style indicateds the shape should be outlined, in addition to optionally being fill.</span></span> <span data-ttu-id="7c44f-109">Jeśli styl GX_BRUSH_OUTLINE jest ustawiony i GX_BRSUH_SOLID_FILL jest wyczyszczone, kształt jest tylko obramowany.</span><span class="sxs-lookup"><span data-stu-id="7c44f-109">If the GX_BRUSH_OUTLINE style is set and the GX_BRSUH_SOLID_FILL is cleared, the shape is only outlined.</span></span>

<span data-ttu-id="7c44f-110">**GX_BRUSH_SOLID_FILL**</span><span class="sxs-lookup"><span data-stu-id="7c44f-110">**GX_BRUSH_SOLID_FILL**</span></span>
- <span data-ttu-id="7c44f-111">Wartość: 0x0001</span><span class="sxs-lookup"><span data-stu-id="7c44f-111">Value: 0x0001</span></span>
- <span data-ttu-id="7c44f-112">Opis: ten styl pędzla ma zastosowanie do funkcji rysowania kształtów i wskazuje, że żądany kształt powinien być wypełniony pełnym kolorem przy użyciu bieżącego koloru wypełnienia pędzla.</span><span class="sxs-lookup"><span data-stu-id="7c44f-112">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be filled with a solid color using the current brush fill color.</span></span>

<span data-ttu-id="7c44f-113">**GX_BRUSH_PIXELMAP_FILL**</span><span class="sxs-lookup"><span data-stu-id="7c44f-113">**GX_BRUSH_PIXELMAP_FILL**</span></span>
- <span data-ttu-id="7c44f-114">Wartość: 0x0002</span><span class="sxs-lookup"><span data-stu-id="7c44f-114">Value: 0x0002</span></span>
- <span data-ttu-id="7c44f-115">Opis: ten styl pędzla ma zastosowanie do funkcji rysowania kształtów i wskazuje, że żądany kształt powinien być wypełniony deseniem z bieżącym Pixelmap pędzla.</span><span class="sxs-lookup"><span data-stu-id="7c44f-115">Description: This brush style applies to shape drawing functions, and indicates that the requested shape should be pattern filled with the current brush pixelmap.</span></span>

<span data-ttu-id="7c44f-116">**GX_BRUSH_ALIAS**</span><span class="sxs-lookup"><span data-stu-id="7c44f-116">**GX_BRUSH_ALIAS**</span></span>
- <span data-ttu-id="7c44f-117">Wartość: 0x0004</span><span class="sxs-lookup"><span data-stu-id="7c44f-117">Value: 0x0004</span></span>
- <span data-ttu-id="7c44f-118">Opis: ten styl pędzla dotyczy wszystkich rysowania linii i konturów kształtów.</span><span class="sxs-lookup"><span data-stu-id="7c44f-118">Description: This brush style applies to all line drawing and shape outlines.</span></span> <span data-ttu-id="7c44f-119">Jeśli ta flaga jest ustawiona, linie i konspekty są rysowane z dokładniejszą, ale również bardziej czasochłonne algorytmy rysowania z aliasami.</span><span class="sxs-lookup"><span data-stu-id="7c44f-119">If this flag is set, lines and outlines are drawing with the more accurate but also more time consuming anti-aliased drawing algorithms.</span></span> <span data-ttu-id="7c44f-120">Ta flaga stylu jest używana tylko dla głębi kolorów 16-BPP i wyższych.</span><span class="sxs-lookup"><span data-stu-id="7c44f-120">This style flag is only used for 16-bpp color depths and higher.</span></span>

<span data-ttu-id="7c44f-121">**GX_BRUSH_UNDERLINE**</span><span class="sxs-lookup"><span data-stu-id="7c44f-121">**GX_BRUSH_UNDERLINE**</span></span>
- <span data-ttu-id="7c44f-122">Wartość: 0x0008</span><span class="sxs-lookup"><span data-stu-id="7c44f-122">Value: 0x0008</span></span>
- <span data-ttu-id="7c44f-123">Opis: Ta flaga ma zastosowanie do rysowania tekstu i wskazuje, że kolejny tekst rysowany powinien być podkreślony.</span><span class="sxs-lookup"><span data-stu-id="7c44f-123">Description: This flag applies to text drawing, and indicates that subsequent text drawn should be underlined.</span></span>

<span data-ttu-id="7c44f-124">**GX_BRUSH_ROUND**</span><span class="sxs-lookup"><span data-stu-id="7c44f-124">**GX_BRUSH_ROUND**</span></span>
- <span data-ttu-id="7c44f-125">Wartość: 0x0010</span><span class="sxs-lookup"><span data-stu-id="7c44f-125">Value: 0x0010</span></span>
- <span data-ttu-id="7c44f-126">Opis: Ta flaga ma zastosowanie do rysowania linii i wskazuje, że końcówki linii są rysowane przy użyciu okrągłego lub okrągłego kształtu, a nie domyślnego kształtu kwadratowego.</span><span class="sxs-lookup"><span data-stu-id="7c44f-126">Description: This flag applies to line drawing, and indicates that line ends are drawn with a round or circular shape, rather than the default square shape.</span></span>

<span data-ttu-id="7c44f-127">__**Flagi kanwy:**__</span><span class="sxs-lookup"><span data-stu-id="7c44f-127">__**Canvas Flags:**__</span></span>

<span data-ttu-id="7c44f-128">**GX_CANVAS_SIMPLE**</span><span class="sxs-lookup"><span data-stu-id="7c44f-128">**GX_CANVAS_SIMPLE**</span></span>
- <span data-ttu-id="7c44f-129">Wartość: 0x01</span><span class="sxs-lookup"><span data-stu-id="7c44f-129">Value: 0x01</span></span>
- <span data-ttu-id="7c44f-130">Opis: Kanwa pamięci, która jest używana do rysowania poza ekranem.</span><span class="sxs-lookup"><span data-stu-id="7c44f-130">Description: A memory canvas which is used to off-screen drawing.</span></span>

<span data-ttu-id="7c44f-131">**GX_CANVAS_MANAGED**</span><span class="sxs-lookup"><span data-stu-id="7c44f-131">**GX_CANVAS_MANAGED**</span></span>
- <span data-ttu-id="7c44f-132">Wartość: 0x02</span><span class="sxs-lookup"><span data-stu-id="7c44f-132">Value: 0x02</span></span>
- <span data-ttu-id="7c44f-133">Opis: Kanwa, która jest automatycznie opróżniana do aktywnego wyświetlania, w ramach procesu konstruowania złożonego lub jako część operacji przełączania buforu dla architektury jednej kanwy.</span><span class="sxs-lookup"><span data-stu-id="7c44f-133">Description: A canvas which automatically flushed to the active display, either as part of the composite building process or as part of the buffer toggle operation for single-canvas architectures.</span></span>

<span data-ttu-id="7c44f-134">**GX_CANVAS_VISIBLE**</span><span class="sxs-lookup"><span data-stu-id="7c44f-134">**GX_CANVAS_VISIBLE**</span></span>
- <span data-ttu-id="7c44f-135">Wartość: 0x04</span><span class="sxs-lookup"><span data-stu-id="7c44f-135">Value: 0x04</span></span>
- <span data-ttu-id="7c44f-136">Opis: Ta flaga może służyć do włączania i wyłączania kanwy bez utraty zawartości rysunku kanwy.</span><span class="sxs-lookup"><span data-stu-id="7c44f-136">Description: This flag can be used to turn on and off a canvas, without losing the canvas drawing contents.</span></span>

<span data-ttu-id="7c44f-137">**GX_CANVAS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="7c44f-137">**GX_CANVAS_MODIFIED**</span></span>
- <span data-ttu-id="7c44f-138">Wartość: 0x08</span><span class="sxs-lookup"><span data-stu-id="7c44f-138">Value: 0x08</span></span>
- <span data-ttu-id="7c44f-139">Opis: zarezerwowane do użytku w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="7c44f-139">Description: Reserved for future use.</span></span>

<span data-ttu-id="7c44f-140">**GX_CANVAS_COMPOSITE**</span><span class="sxs-lookup"><span data-stu-id="7c44f-140">**GX_CANVAS_COMPOSITE**</span></span>
- <span data-ttu-id="7c44f-141">Wartość: 0x20</span><span class="sxs-lookup"><span data-stu-id="7c44f-141">Value: 0x20</span></span>
- <span data-ttu-id="7c44f-142">Opis: Ta flaga jest używana przez aplikację podczas konfigurowania systemu wielokanwowego, który będzie złożonym wieloma zarządzanymi kanwami na kanwę kompozytową, a kompozyt jest kierowany do buforu ramki sprzętowej.</span><span class="sxs-lookup"><span data-stu-id="7c44f-142">Description: This flag is used by the application when configuring a multiple-canvas system which will composite multiple managed canvases into the composite canvas, and the composite is the driven to the hardware frame buffer.</span></span>

<span data-ttu-id="7c44f-143">__**Typy gradientów:**__</span><span class="sxs-lookup"><span data-stu-id="7c44f-143">__**Gradient Types:**__</span></span>

<span data-ttu-id="7c44f-144">**GX_GRADIENT_TYPE_VERTICAL**</span><span class="sxs-lookup"><span data-stu-id="7c44f-144">**GX_GRADIENT_TYPE_VERTICAL**</span></span>
- <span data-ttu-id="7c44f-145">Wartość: 0x01</span><span class="sxs-lookup"><span data-stu-id="7c44f-145">Value: 0x01</span></span>
- <span data-ttu-id="7c44f-146">Opis: Tworzy gradient alphamap w pionie.</span><span class="sxs-lookup"><span data-stu-id="7c44f-146">Description: Creates a vertical alphamap gradient.</span></span>

<span data-ttu-id="7c44f-147">**GX_GRADIENT_TYPE_ALPHA**</span><span class="sxs-lookup"><span data-stu-id="7c44f-147">**GX_GRADIENT_TYPE_ALPHA**</span></span>
- <span data-ttu-id="7c44f-148">Wartość: 0x02</span><span class="sxs-lookup"><span data-stu-id="7c44f-148">Value: 0x02</span></span>
- <span data-ttu-id="7c44f-149">Opis: umożliwia tworzenie gradientu stylu mapy alfa.</span><span class="sxs-lookup"><span data-stu-id="7c44f-149">Description: Creats an alpha-map style gradient.</span></span> <span data-ttu-id="7c44f-150">Jest to obecnie jedyny obsługiwany styl gradientu.</span><span class="sxs-lookup"><span data-stu-id="7c44f-150">This is currently the only gradient style supported.</span></span>

<span data-ttu-id="7c44f-151">**GX_GRADIENT_TYPE_MIRROR**</span><span class="sxs-lookup"><span data-stu-id="7c44f-151">**GX_GRADIENT_TYPE_MIRROR**</span></span>
- <span data-ttu-id="7c44f-152">Wartość: 0x04</span><span class="sxs-lookup"><span data-stu-id="7c44f-152">Value: 0x04</span></span>
- <span data-ttu-id="7c44f-153">Opis: Ta flaga wskazuje, że gradient ma być ustawiony na wartość szczytową w środku zakresu szerokość/wysokość, i wrócić do wartości początkowej, ponieważ osiągnie ona prawą/dolną krawędź.</span><span class="sxs-lookup"><span data-stu-id="7c44f-153">Description: This flag indicates that the gradient should peak at the center of the width/height range, and return to the starting value as it reaches the right/bottom edge.</span></span> <span data-ttu-id="7c44f-154">Bez tej flagi stylu gradient będzie gradientem liniowym od góry do dołu lub od lewej do prawej, w zależności od flagi GX_GRADIENT_TYPE_VERTICAL.</span><span class="sxs-lookup"><span data-stu-id="7c44f-154">Without this style flag, the gradient will be a linear gradient from top-to-bottom or left-to-right, depending on the GX_GRADIENT_TYPE_VERTICAL flag.</span></span>