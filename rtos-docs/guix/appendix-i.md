---
title: Dodatek I-GUIX struktury informacji
description: Dowiedz się więcej o strukturach informacji GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dc7775cdde8f1aa89ca650561713f54ac6c069eb
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550222"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="e435b-103">Dodatek I-GUIX struktury informacji</span><span class="sxs-lookup"><span data-stu-id="e435b-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="e435b-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="e435b-105">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```
| <span data-ttu-id="e435b-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-106">Members</span></span> | <span data-ttu-id="e435b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-107">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="e435b-108">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="e435b-108">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="e435b-109">Tekst do zmiany kolejności</span><span class="sxs-lookup"><span data-stu-id="e435b-109">Text for reordering</span></span> |
| <span data-ttu-id="e435b-110">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="e435b-110">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="e435b-111">Czcionka używana do wyświetlania tekstu, ustawiana na GX_NULL, jeśli podział wiersza nie jest wymagany</span><span class="sxs-lookup"><span data-stu-id="e435b-111">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="e435b-112">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="e435b-112">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="e435b-113">Dostępna szerokość wyświetlania, ustaw ją na wartość-1, jeśli podział wiersza nie jest wymagany</span><span class="sxs-lookup"><span data-stu-id="e435b-113">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="e435b-114">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-114">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="e435b-115">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-115">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

| <span data-ttu-id="e435b-116">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-116">Members</span></span> | <span data-ttu-id="e435b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-117">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="e435b-118">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="e435b-118">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="e435b-119">Wskaźnik do tablicy zmiany kolejności tekstu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="e435b-119">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="e435b-120">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="e435b-120">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="e435b-121">Łączna liczba wierszy rozwiązanego tekstu dwukierunkowego w jednym akapicie</span><span class="sxs-lookup"><span data-stu-id="e435b-121">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="e435b-122">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="e435b-122">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="e435b-123">Rozpoznano informacje o tekście dwukierunkowym dla następnego akapitu</span><span class="sxs-lookup"><span data-stu-id="e435b-123">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="e435b-124">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-124">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="e435b-125">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-125">Definition</span></span>

```c
typedef struct GX_CIRCULAR_GAUGE_INFO_STRUCT
{
    INT             gx_circular_gauge_info_animation_steps;
    INT             gx_circular_gauge_info_animation_delay;
    GX_VALUE        gx_circular_gauge_info_needle_xpos;
    GX_VALUE        gx_circular_gauge_info_needle_ypos;
    GX_VALUE        gx_circular_gauge_info_needle_xcor;
    GX_VALUE        gx_circular_gauge_info_needle_ycor;
    GX_RESOURCE_ID  gx_circular_gauge_info_needle_pixelmap;
} GX_CIRCULAR_GAUGE_INFO;
```

| <span data-ttu-id="e435b-126">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-126">Members</span></span> | <span data-ttu-id="e435b-127">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-127">Description</span></span> |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="e435b-128">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="e435b-128">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="e435b-129">Łączna liczba kroków przenoszonych przez wskazówkę podczas przesuwania z bieżącego kąta wskazówki do nowo przypisanego kąta wskazówki</span><span class="sxs-lookup"><span data-stu-id="e435b-129">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="e435b-130">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="e435b-130">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="e435b-131">Liczba taktów zegara GUIX na opóźnienie między krokami animacji</span><span class="sxs-lookup"><span data-stu-id="e435b-131">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="e435b-132">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="e435b-132">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="e435b-133">Odległość od lewej krawędzi widgetu miernika do środka obrotu wskazówki</span><span class="sxs-lookup"><span data-stu-id="e435b-133">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="e435b-134">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="e435b-134">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="e435b-135">Odległość od góry widżetu miernika do środka obrotu wskazówki dotyczącej miernika</span><span class="sxs-lookup"><span data-stu-id="e435b-135">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="e435b-136">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="e435b-136">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="e435b-137">Odległość od lewej krawędzi obrazu wskazówki do środka obrotu wskazówki dotyczącego miernika</span><span class="sxs-lookup"><span data-stu-id="e435b-137">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="e435b-138">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="e435b-138">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="e435b-139">Odległość od góry obrazu wskazówki do środka obrotu wskazówki dotyczącej miernika</span><span class="sxs-lookup"><span data-stu-id="e435b-139">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="e435b-140">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-140">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="e435b-141">Identyfikator zasobu Pixelmap, który będzie używany do rysowania wskazówki miernika.</span><span class="sxs-lookup"><span data-stu-id="e435b-141">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="e435b-142">Ten obraz zostanie obrócony zgodnie z wymaganiami widżetu miernik, aby wyświetlić wskazówkę miernika w dowolnym położeniu</span><span class="sxs-lookup"><span data-stu-id="e435b-142">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="e435b-143">Na poniższym diagramie przedstawiono współrzędne xpos, YPos i XCOR, ycor:</span><span class="sxs-lookup"><span data-stu-id="e435b-143">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![Diagram współrzędnych Y i X wskazówki](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="e435b-145">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-145">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="e435b-146">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-146">Definition</span></span>

```c
typedef struct GX_LINE_CHART_INFO_STRUCT
{
    INT            gx_line_chart_min_val;
    INT            gx_line_chart_max_val;
    INT           *gx_line_chart_data;
    GX_VALUE       gx_line_left_margin;
    GX_VALUE       gx_line_top_margin;
    GX_VALUE       gx_line_right_margin;
    GX_VALUE       gx_line_bottom_margin;
    GX_VALUE       gx_line_chart_max_data_count;
    GX_VALUE       gx_line_chart_active_data_count;
    GX_VALUE       gx_line_chart_axis_line_width;
    GX_VALUE       gx_line_chart_data_line_width;
    GX_RESOURCE_ID gx_line_chart_axis_color;
    GX_RESOURCE_ID gx_line_chart_line_color;
} GX_LINE_CHART_INFO;
```

| <span data-ttu-id="e435b-147">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-147">Members</span></span> | <span data-ttu-id="e435b-148">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-148">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="e435b-149">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="e435b-149">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="e435b-150">Minimalna wartość danych, która jest używana do obliczania skalowania</span><span class="sxs-lookup"><span data-stu-id="e435b-150">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="e435b-151">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="e435b-151">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="e435b-152">Maksymalna wartość danych, która jest używana do obliczania skalowania</span><span class="sxs-lookup"><span data-stu-id="e435b-152">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="e435b-153">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="e435b-153">**gx_line_chart_data**</span></span>             | <span data-ttu-id="e435b-154">Wskaźnik na tablicę wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e435b-154">Pointer to an array of integer values.</span></span> <span data-ttu-id="e435b-155">Są to wartości całkowite kreślone przez widżet wykres liniowy</span><span class="sxs-lookup"><span data-stu-id="e435b-155">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="e435b-156">**gx_line_ <side> _margin**</span><span class="sxs-lookup"><span data-stu-id="e435b-156">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="e435b-157">Przesunięcie z okna wykresu jest powiązane z zewnętrznym obszarem renderowania wykresu.</span><span class="sxs-lookup"><span data-stu-id="e435b-157">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="e435b-158">Oś wykresu i linia danych są zawsze kreślone w obrębie tej wewnętrznej granicy, co umożliwia aplikacji rysowanie etykiet i innych informacji wewnątrz okna wykresu, ale poza obszarem grafu znaków</span><span class="sxs-lookup"><span data-stu-id="e435b-158">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="e435b-159">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="e435b-159">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="e435b-160">Liczba wartości danych, które mogą być obecne.</span><span class="sxs-lookup"><span data-stu-id="e435b-160">The number of data values which may be present.</span></span> <span data-ttu-id="e435b-161">Ten parametr służy do obliczania skali x lub interwału wykreślania punktów danych.</span><span class="sxs-lookup"><span data-stu-id="e435b-161">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="e435b-162">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="e435b-162">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="e435b-163">Liczba wartości danych, które faktycznie znajdują się w tablicy danych.</span><span class="sxs-lookup"><span data-stu-id="e435b-163">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="e435b-164">Wykres liniowy może być skalowany w celu narysowania maksymalnie 100 wartości (na przykład), ale w każdej konkretnej aktualizacji może być rzeczywiście obecne.</span><span class="sxs-lookup"><span data-stu-id="e435b-164">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="e435b-165">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="e435b-165">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="e435b-166">Szerokość linii używana do rysowania osi poziomej i pionowej</span><span class="sxs-lookup"><span data-stu-id="e435b-166">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="e435b-167">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="e435b-167">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="e435b-168">Szerokość wykreślonego wiersza danych</span><span class="sxs-lookup"><span data-stu-id="e435b-168">Width of the plotted data line</span></span> |
| <span data-ttu-id="e435b-169">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-169">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="e435b-170">Identyfikator zasobu używany do rysowania linii osi</span><span class="sxs-lookup"><span data-stu-id="e435b-170">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="e435b-171">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-171">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="e435b-172">Identyfikator zasobu używany do rysowania linii danych wykresu</span><span class="sxs-lookup"><span data-stu-id="e435b-172">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="e435b-173">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-173">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="e435b-174">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-174">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

| <span data-ttu-id="e435b-175">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-175">Members</span></span> | <span data-ttu-id="e435b-176">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-176">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="e435b-177">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="e435b-177">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="e435b-178">Identyfikator zasobu obrazu myszy</span><span class="sxs-lookup"><span data-stu-id="e435b-178">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="e435b-179">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="e435b-179">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="e435b-180">Przesunięcie od lewej krawędzi obrazu myszy do hotspotu obrazu myszy.</span><span class="sxs-lookup"><span data-stu-id="e435b-180">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="e435b-181">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="e435b-181">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="e435b-182">Przesunięcie od góry obrazu myszy do hotspotu obrazu myszy.</span><span class="sxs-lookup"><span data-stu-id="e435b-182">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="e435b-183">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="e435b-183">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="e435b-184">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-184">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

| <span data-ttu-id="e435b-185">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-185">Members</span></span> | <span data-ttu-id="e435b-186">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-186">Description</span></span> |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="e435b-187">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="e435b-187">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="e435b-188">Minimalną odległość przeciągania na cykl czasomierza GUIX, aby wyzwolić zdarzenie szybkiego ruchu.</span><span class="sxs-lookup"><span data-stu-id="e435b-188">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="e435b-189">Wywołaj GX_FIXED_VAL_MAKE, aby utworzyć stałą wartość typu danych</span><span class="sxs-lookup"><span data-stu-id="e435b-189">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="e435b-190">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="e435b-190">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="e435b-191">Maksymalna szybkość przeciągania w taktach czasomierza GUIX w celu wyzwalania zdarzenia szybkiego ruchu</span><span class="sxs-lookup"><span data-stu-id="e435b-191">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="e435b-192">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-192">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="e435b-193">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-193">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

| <span data-ttu-id="e435b-194">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-194">Members</span></span> | <span data-ttu-id="e435b-195">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-195">Description</span></span> |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="e435b-196">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-196">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="e435b-197">Identyfikator zasobu Pixelmap do wypełniania tła przed wskazówką.</span><span class="sxs-lookup"><span data-stu-id="e435b-197">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="e435b-198">Jeśli nie ustawiono górnego Pixelmap w tle, jest on używany do wypełniania tła przed i po wskazówkę</span><span class="sxs-lookup"><span data-stu-id="e435b-198">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="e435b-199">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-199">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="e435b-200">Identyfikator zasobu Pixelmap do wypełnienia tła po wskazówki</span><span class="sxs-lookup"><span data-stu-id="e435b-200">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="e435b-201">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-201">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="e435b-202">Identyfikator zasobu wskazówki Pixelmap</span><span class="sxs-lookup"><span data-stu-id="e435b-202">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="e435b-203">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-203">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="e435b-204">**Definicja**</span><span class="sxs-lookup"><span data-stu-id="e435b-204">**Definition**</span></span>

```c
typedef struct GX_PROGRESS_BAR_INFO_STRUCT
{
    INT gx_progress_bar_info_min_val;
    INT gx_progress_bar_info_max_val;
    INT gx_progress_bar_info_current_val;
    GX_RESOURCE_ID gx_progress_bar_font_id;
    GX_RESOURCE_ID gx_progress_bar_normal_text_color;
    GX_RESOURCE_ID gx_progress_bar_selected_text_color;
    GX_RESOURCE_ID gx_progress_bar_disabled_text_color;
    GX_RESOURCE_ID gx_progress_bar_fill_pixelmap;
} GX_PROGRESS_BAR_INFO;
```

| <span data-ttu-id="e435b-205">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-205">Members</span></span> | <span data-ttu-id="e435b-206">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-206">Description</span></span> |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="e435b-207">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="e435b-207">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="e435b-208">Minimalna raportowana wartość</span><span class="sxs-lookup"><span data-stu-id="e435b-208">Minimum reported value</span></span> |
| <span data-ttu-id="e435b-209">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="e435b-209">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="e435b-210">Maksymalna raportowana wartość</span><span class="sxs-lookup"><span data-stu-id="e435b-210">Maximum reported value</span></span> |
| <span data-ttu-id="e435b-211">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="e435b-211">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="e435b-212">Bieżąca wartość</span><span class="sxs-lookup"><span data-stu-id="e435b-212">Current value</span></span> |
| <span data-ttu-id="e435b-213">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="e435b-213">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="e435b-214">Identyfikator zasobu czcionki używany do rysowania opcjonalnej wartości tekstowej w widżecie pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="e435b-214">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="e435b-215">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-215">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="e435b-216">Identyfikator zasobu koloru tekstu w normalnym stanie używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="e435b-216">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="e435b-217">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-217">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="e435b-218">Identyfikator zasobu koloru tekstu, gdy element widget uzyskuje fokus, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="e435b-218">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="e435b-219">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-219">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="e435b-220">Identyfikator zasobu koloru tekstu, gdy GX_STYLE_ENABLED nie jest aktywny, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="e435b-220">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="e435b-221">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-221">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="e435b-222">Identyfikator zasobu Pixelmap do wypełnienia tła</span><span class="sxs-lookup"><span data-stu-id="e435b-222">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="e435b-223">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-223">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="e435b-224">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-224">Definition</span></span>

```c
typedef struct GX_RADIAL_PROGRESS_BAR_INFO_STRUCT
{
    GX_VALUE       gx_radial_progress_bar_info_xcenter;
    GX_VALUE       gx_radial_progress_bar_info_ycenter;
    GX_VALUE       gx_radial_progress_bar_info_radius;
    GX_VALUE       gx_radial_progress_bar_info_current_val;
    GX_VALUE       gx_radial_progress_bar_info_anchor_val;
    GX_RESOURCE_ID gx_radial_progress_bar_info_font_id;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_text_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_disabled_text_color;
    GX_VALUE       gx_radial_progress_bar_info_normal_brush_width;
    GX_VALUE       gx_radial_progress_bar_info_selected_brush_width;
    GX_RESOURCE_ID gx_radial_progress_bar_info_normal_brush_color;
    GX_RESOURCE_ID gx_radial_progress_bar_info_selected_brush_color;
} GX_RADIAL_PROGRESS_BAR_INFO;
```

| <span data-ttu-id="e435b-225">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-225">Members</span></span> | <span data-ttu-id="e435b-226">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-226">Description</span></span> |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="e435b-227">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="e435b-227">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="e435b-228">Położenie elementu widget w współrzędnej x</span><span class="sxs-lookup"><span data-stu-id="e435b-228">Widget position in x coordinate</span></span> |
| <span data-ttu-id="e435b-229">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="e435b-229">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="e435b-230">Położenie elementu widget w współrzędnym y</span><span class="sxs-lookup"><span data-stu-id="e435b-230">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="e435b-231">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="e435b-231">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="e435b-232">Promień okręgu postępu</span><span class="sxs-lookup"><span data-stu-id="e435b-232">Radius of the progress circle</span></span> |
| <span data-ttu-id="e435b-233">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="e435b-233">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="e435b-234">Bieżąca wartość, ograniczona do zakresu [-360, 360], wskazuje różnicę kątową między pozycją zakotwiczenia a punktem końcowym górnego łuku. Wartość ujemna powoduje, że łuk ma być rysowany w kierunku w prawo, rozpoczynając od pozycji zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="e435b-234">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="e435b-235">Wartość dodatnia powoduje, że łuk ma być rysowany w kierunku przychodzącym w prawo, rozpoczynając od pozycji zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="e435b-235">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="e435b-236">Aplikacja musi skalować wskazane wartości rzeczywiste, aby przypisać wartość kątową do widżetu paska postępu.</span><span class="sxs-lookup"><span data-stu-id="e435b-236">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="e435b-237">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="e435b-237">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="e435b-238">Kąt początkowy łuku górnego postępu. Wartość jest definiowana w zakresie liczby całkowitej z 0 stopni wskazujących prawy i 90 stopień wskazujący na pozycję prostą.</span><span class="sxs-lookup"><span data-stu-id="e435b-238">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="e435b-239">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="e435b-239">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="e435b-240">Identyfikator zasobu czcionki używany do rysowania opcjonalnej wartości tekstowej w widżecie pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="e435b-240">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="e435b-241">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-241">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="e435b-242">Identyfikator zasobu koloru tekstu w normalnym stanie używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="e435b-242">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="e435b-243">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-243">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="e435b-244">Identyfikator zasobu koloru tekstu, gdy element widget uzyskuje fokus, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="e435b-244">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="e435b-245">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-245">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="e435b-246">Identyfikator zasobu koloru tekstu, gdy GX_STYLE_ENABLED nie jest aktywny, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="e435b-246">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="e435b-247">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="e435b-247">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="e435b-248">Szerokość dolnego okręgu postępu</span><span class="sxs-lookup"><span data-stu-id="e435b-248">Width of the lower progress circle</span></span> |
| <span data-ttu-id="e435b-249">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="e435b-249">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="e435b-250">Szerokość górnego łuku postępu, górny łuk może być węższy, taki sam jak lub większy niż dolny okrąg</span><span class="sxs-lookup"><span data-stu-id="e435b-250">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="e435b-251">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-251">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="e435b-252">Identyfikator zasobu koloru do wypełnienia dolnego okręgu postępu</span><span class="sxs-lookup"><span data-stu-id="e435b-252">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="e435b-253">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-253">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="e435b-254">Identyfikator zasobu koloru do wypełnienia łuku górnego postępu</span><span class="sxs-lookup"><span data-stu-id="e435b-254">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="e435b-255">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-255">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="e435b-256">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-256">Definition</span></span>

```c
typedef struct GX_RADIAL_SLIDER_INFO_STRUCT
{
    GX_VALUE       gx_radial_slider_info_xcenter;
    GX_VALUE       gx_radial_slider_info_ycenter;
    USHORT         gx_radial_slider_info_radius;
    USHORT         gx_radial_slider_info_track_width;
    GX_VALUE       gx_radial_slider_info_current_angle;
    GX_VALUE       gx_radial_slider_info_min_angle;
    GX_VALUE       gx_radial_slider_info_max_angle;
    GX_VALUE      *gx_radial_slider_info_angle_list;
    USHORT         gx_radial_slider_info_list_cont;
    GX_RESOURCE_ID gx_radial_slider_info_background_pixelmap;
    GX_RESOURCE_ID gx_radial_slider_info_needle_pixelmap;
} GX_RADIAL_SLIDER_INFO;
```

| <span data-ttu-id="e435b-257">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-257">Members</span></span> | <span data-ttu-id="e435b-258">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-258">Description</span></span> |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="e435b-259">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="e435b-259">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="e435b-260">Odległość od lewej krawędzi elementu widget suwaka do środka obrotu wskazówki kontrolki suwaka</span><span class="sxs-lookup"><span data-stu-id="e435b-260">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="e435b-261">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="e435b-261">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="e435b-262">Odległość od góry elementu widget suwaka do środka obrotu wskazówki kontrolki suwaka</span><span class="sxs-lookup"><span data-stu-id="e435b-262">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="e435b-263">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="e435b-263">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="e435b-264">Promień okręgu suwaka promieniowego</span><span class="sxs-lookup"><span data-stu-id="e435b-264">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="e435b-265">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="e435b-265">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="e435b-266">Szerokość kontrolki suwaka promieniowego</span><span class="sxs-lookup"><span data-stu-id="e435b-266">Width of radial slider track</span></span> |
| <span data-ttu-id="e435b-267">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="e435b-267">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="e435b-268">Bieżący kąt suwaka</span><span class="sxs-lookup"><span data-stu-id="e435b-268">Current slider angle</span></span> |
| <span data-ttu-id="e435b-269">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="e435b-269">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="e435b-270">Minimalny kąt suwaka</span><span class="sxs-lookup"><span data-stu-id="e435b-270">Minimum slider angle</span></span> |
| <span data-ttu-id="e435b-271">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="e435b-271">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="e435b-272">Maksymalny kąt suwaka</span><span class="sxs-lookup"><span data-stu-id="e435b-272">Maximum slider angle</span></span> |
| <span data-ttu-id="e435b-273">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="e435b-273">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="e435b-274">Lista wartości kątowych, definiuje kąty kotwicowe, jeśli jest ustawiona, kąt suwaka może być tylko jednym ze zdefiniowanych kątów zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="e435b-274">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="e435b-275">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="e435b-275">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="e435b-276">Liczba kątów zakotwiczenia</span><span class="sxs-lookup"><span data-stu-id="e435b-276">Number of anchor angles</span></span> |
| <span data-ttu-id="e435b-277">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-277">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="e435b-278">Identyfikator zasobu w tle Pixelmap</span><span class="sxs-lookup"><span data-stu-id="e435b-278">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="e435b-279">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-279">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="e435b-280">Identyfikator zasobu wskazówki Pixelmap</span><span class="sxs-lookup"><span data-stu-id="e435b-280">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="e435b-281">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="e435b-281">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="e435b-282">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-282">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

| <span data-ttu-id="e435b-283">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-283">Members</span></span> | <span data-ttu-id="e435b-284">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-284">Description</span></span> |
| -------------------------------- | ------------------------|
| <span data-ttu-id="e435b-285">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="e435b-285">**gx_rectangle_left**</span></span>            | <span data-ttu-id="e435b-286">Po lewej stronie prostokąta</span><span class="sxs-lookup"><span data-stu-id="e435b-286">Left of the rectangle</span></span>   |  
| <span data-ttu-id="e435b-287">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="e435b-287">**gx_rectangle_top**</span></span>             | <span data-ttu-id="e435b-288">Góra prostokąta</span><span class="sxs-lookup"><span data-stu-id="e435b-288">Top of the rectangle</span></span>    | 
| <span data-ttu-id="e435b-289">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="e435b-289">**gx_rectangle_right**</span></span>           | <span data-ttu-id="e435b-290">Z prawej strony prostokąta</span><span class="sxs-lookup"><span data-stu-id="e435b-290">Right of the rectangle</span></span>  |
| <span data-ttu-id="e435b-291">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="e435b-291">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="e435b-292">Dolna część prostokąta</span><span class="sxs-lookup"><span data-stu-id="e435b-292">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="e435b-293">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="e435b-293">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="e435b-294">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-294">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

| <span data-ttu-id="e435b-295">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-295">Members</span></span> | <span data-ttu-id="e435b-296">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-296">Description</span></span> |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="e435b-297">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="e435b-297">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="e435b-298">Identyfikator zasobu zwykłej czcionki tekstu</span><span class="sxs-lookup"><span data-stu-id="e435b-298">Resource ID of normal text font</span></span> |
| <span data-ttu-id="e435b-299">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="e435b-299">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="e435b-300">Identyfikator zasobu czcionki pogrubionej tekstu</span><span class="sxs-lookup"><span data-stu-id="e435b-300">Resource ID of bold text font</span></span> |
| <span data-ttu-id="e435b-301">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="e435b-301">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="e435b-302">Identyfikator zasobu czcionki tekstu kursywy</span><span class="sxs-lookup"><span data-stu-id="e435b-302">Resource ID of italic text font</span></span> |
| <span data-ttu-id="e435b-303">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="e435b-303">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="e435b-304">Identyfikator zasobu czcionki pogrubionej kursywy</span><span class="sxs-lookup"><span data-stu-id="e435b-304">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="e435b-305">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-305">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="e435b-306">**Definicja**</span><span class="sxs-lookup"><span data-stu-id="e435b-306">**Definition**</span></span>

```c
typedef struct GX_SCROLL_INFO_STRUCT
{
    INT      gx_scroll_value;
    INT      gx_scroll_minimum;
    INT      gx_scroll_maximum;
    GX_VALUE gx_scroll_visible;
    GX_VALUE gx_scroll_increment;
} GX_SCROLL_INFO;
```

| <span data-ttu-id="e435b-307">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-307">Members</span></span> | <span data-ttu-id="e435b-308">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-308">Description</span></span> |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="e435b-309">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="e435b-309">**gx_scroll_value**</span></span>     | <span data-ttu-id="e435b-310">Bieżąca pozycja przewijania</span><span class="sxs-lookup"><span data-stu-id="e435b-310">Current scroll position</span></span>       |
| <span data-ttu-id="e435b-311">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="e435b-311">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="e435b-312">Minimalna zgłoszona pozycja</span><span class="sxs-lookup"><span data-stu-id="e435b-312">Minimum reported position</span></span>     |
| <span data-ttu-id="e435b-313">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="e435b-313">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="e435b-314">Maksymalna zgłoszona pozycja</span><span class="sxs-lookup"><span data-stu-id="e435b-314">Maximum reported position</span></span>     |
| <span data-ttu-id="e435b-315">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="e435b-315">**gx_scroll_visible**</span></span>   | <span data-ttu-id="e435b-316">Widoczny zakres okna nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="e435b-316">Parent window visible range</span></span>   |
| <span data-ttu-id="e435b-317">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="e435b-317">**gx_scroll_increment**</span></span> | <span data-ttu-id="e435b-318">Minimalna wartość różnicowa ScrollBar</span><span class="sxs-lookup"><span data-stu-id="e435b-318">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="e435b-319">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="e435b-319">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="e435b-320">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-320">Definition</span></span>

```c
typedef struct GX_SCROLLBAR_APPEARANCE_STRUCT
{
    GX_VALUE       gx_scroll_width;
    GX_VALUE       gx_scroll_thumb_width;
    GX_VALUE       gx_scroll_thumb_travel_min;
    GX_VALUE       gx_scroll_thumb_travel_max;
    GX_UBYTE       gx_scroll_thumb_border_style;
    GX_RESOURCE_ID gx_scroll_fill_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_pixelmap;
    GX_RESOURCE_ID gx_scroll_up_pixelmap;
    GX_RESOURCE_ID gx_scroll_down_pixelmap;
    GX_RESOURCE_ID gx_scroll_thumb_color;
    GX_RESOURCE_ID gx_scroll_thumb_border_color;
    GX_RESOURCE_ID gx_scroll_button_color;
} GX_SCROLLBAR_APPEARANCE;
```

| <span data-ttu-id="e435b-321">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-321">Members</span></span> | <span data-ttu-id="e435b-322">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-322">Description</span></span> |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="e435b-323">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="e435b-323">**gx_scroll_width**</span></span>                      | <span data-ttu-id="e435b-324">Szerokość widżetu ScrollBar w pikselach</span><span class="sxs-lookup"><span data-stu-id="e435b-324">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="e435b-325">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="e435b-325">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="e435b-326">Szerokość przycisku przewijania, które slajdy na pasku przewijania (w pikselach).</span><span class="sxs-lookup"><span data-stu-id="e435b-326">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="e435b-327">Ta wartość jest zwykle pewną liczbą pikseli mniejszą niż całkowita szerokość paska przewijania.</span><span class="sxs-lookup"><span data-stu-id="e435b-327">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="e435b-328">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="e435b-328">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="e435b-329">Przesunięcie od końca paska przewijania do minimalnego punktu podróży przycisku przewijania.</span><span class="sxs-lookup"><span data-stu-id="e435b-329">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="e435b-330">Tego limitu można użyć, aby zapobiec przeniesieniu przycisku przewijania na koniec paska przewijania.</span><span class="sxs-lookup"><span data-stu-id="e435b-330">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="e435b-331">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="e435b-331">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="e435b-332">Przesunięcie od końca paska przewijania do maksymalnego punktu podróży przycisku przewijania.</span><span class="sxs-lookup"><span data-stu-id="e435b-332">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="e435b-333">Tego limitu można użyć, aby zapobiec przeniesieniu przycisku przewijania na koniec paska przewijania.</span><span class="sxs-lookup"><span data-stu-id="e435b-333">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="e435b-334">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="e435b-334">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="e435b-335">Style obramowania przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="e435b-335">Border styles of thumb button</span></span> |
| <span data-ttu-id="e435b-336">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-336">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="e435b-337">Opcjonalny identyfikator Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="e435b-337">Optional pixelmap ID.</span></span> <span data-ttu-id="e435b-338">Jeśli ten identyfikator Pixelmap nie jest zerem, pasek przewijania używa tego Pixelmap do rysowania tła paska przewijania</span><span class="sxs-lookup"><span data-stu-id="e435b-338">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="e435b-339">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-339">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="e435b-340">Opcjonalny identyfikator Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="e435b-340">Optional pixelmap ID.</span></span> <span data-ttu-id="e435b-341">Jeśli ten identyfikator Pixelmap ma wartość różną od zera, przycisk przewijania ScrollBar używa tego Pixelmap do rysowania</span><span class="sxs-lookup"><span data-stu-id="e435b-341">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="e435b-342">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-342">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="e435b-343">Opcjonalny identyfikator Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="e435b-343">Optional pixelmap ID.</span></span> <span data-ttu-id="e435b-344">Jeśli ten identyfikator Pixelmap ma wartość różną od zera, pasek przewijania używa tego identyfikatora Pixelmap do rysowania przycisku przewijania w lewo/w górę</span><span class="sxs-lookup"><span data-stu-id="e435b-344">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="e435b-345">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-345">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="e435b-346">Opcjonalny identyfikator Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="e435b-346">Optional pixelmap ID.</span></span> <span data-ttu-id="e435b-347">Jeśli ten identyfikator Pixelmap ma wartość różną od zera, pasek przewijania używa tego identyfikatora Pixelmap do rysowania przycisku końca w prawym/dół paska przewijania</span><span class="sxs-lookup"><span data-stu-id="e435b-347">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="e435b-348">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-348">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="e435b-349">Identyfikator zasobu koloru używany do wypełnienia przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="e435b-349">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="e435b-350">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-350">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="e435b-351">Identyfikator zasobu koloru używany do rysowania obramowania przycisku kciuka</span><span class="sxs-lookup"><span data-stu-id="e435b-351">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="e435b-352">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="e435b-352">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="e435b-353">Identyfikator zasobu koloru używany do wypełniania przycisków końca paska przewijania</span><span class="sxs-lookup"><span data-stu-id="e435b-353">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="e435b-354">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="e435b-354">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="e435b-355">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-355">Definition</span></span>

```c
typedef struct GX_SLIDER_INFO_STRUCT
{
    INT      gx_slider_info_min_val;
    INT      gx_slider_info_max_val;
    INT      gx_slider_info_current_val;
    INT      gx_slider_info_increment;
    GX_VALUE gx_slider_info_min_travel;
    GX_VALUE gx_slider_info_max_travel;
    GX_VALUE gx_slider_info_needle_width;
    GX_VALUE gx_slider_info_needle_height;
    GX_VALUE gx_slider_info_needle_inset;
    GX_VALUE gx_slider_info_needle_hotspot_offset;
} GX_SLIDER_INFO;
```

| <span data-ttu-id="e435b-356">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-356">Members</span></span> | <span data-ttu-id="e435b-357">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-357">Description</span></span> |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="e435b-358">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="e435b-358">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="e435b-359">Minimalna raportowana wartość</span><span class="sxs-lookup"><span data-stu-id="e435b-359">Minimum reported value</span></span> |
| <span data-ttu-id="e435b-360">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="e435b-360">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="e435b-361">Maksymalna raportowana wartość</span><span class="sxs-lookup"><span data-stu-id="e435b-361">Maximum reported value</span></span> |
| <span data-ttu-id="e435b-362">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="e435b-362">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="e435b-363">Bieżąca wartość</span><span class="sxs-lookup"><span data-stu-id="e435b-363">Current value</span></span> |
| <span data-ttu-id="e435b-364">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="e435b-364">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="e435b-365">Limit podróży wskazówki</span><span class="sxs-lookup"><span data-stu-id="e435b-365">Needle travel limit</span></span> |
| <span data-ttu-id="e435b-366">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="e435b-366">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="e435b-367">Limit podróży wskazówki</span><span class="sxs-lookup"><span data-stu-id="e435b-367">Needle travel limit</span></span> |
| <span data-ttu-id="e435b-368">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="e435b-368">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="e435b-369">Szerokość wskazówki w pikselach</span><span class="sxs-lookup"><span data-stu-id="e435b-369">Needle width in pixel</span></span> |
| <span data-ttu-id="e435b-370">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="e435b-370">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="e435b-371">Wysokość wskazówki (w pikselach)</span><span class="sxs-lookup"><span data-stu-id="e435b-371">Needle height in pixel</span></span> |
|<span data-ttu-id="e435b-372">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="e435b-372">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="e435b-373">Pozycja rysowania wskazówki.</span><span class="sxs-lookup"><span data-stu-id="e435b-373">Needle draw position.</span></span> <span data-ttu-id="e435b-374">Jeśli ustawiono GX_STYLE_SLIDER_VERTICAL, służy do określania przesunięcia od pozycji początku rysowania wskazówki do lewego suwaka.</span><span class="sxs-lookup"><span data-stu-id="e435b-374">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="e435b-375">Else, używany do określania przesunięcia od pozycji początkowej rysowania wskazówki do górnej krawędzi suwaka.</span><span class="sxs-lookup"><span data-stu-id="e435b-375">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="e435b-376">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="e435b-376">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="e435b-377">Wskazówki hotpot_offset, używane do określania przesunięcia od pozycji początkowej rysowania wskazówki do punktu aktywnego suwaka.</span><span class="sxs-lookup"><span data-stu-id="e435b-377">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="e435b-378">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="e435b-378">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="e435b-379">Definicja</span><span class="sxs-lookup"><span data-stu-id="e435b-379">Definition</span></span>

```c
typedef struct GX_SPRITE_FRAME_STRUCT
{
    GX_RESOURCE_ID gx_sprite_frame_pixelmap;
    GX_VALUE gx_sprite_frame_x_offset;
    GX_VALUE gx_sprite_frame_y_offset;
    UINT gx_sprite_frame_delay;
    UINT gx_sprite_frame_background_operation;
    UCHAR gx_sprite_frame_alpha;
} GX_SPRITE_FRAME;
```

| <span data-ttu-id="e435b-380">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e435b-380">Members</span></span> | <span data-ttu-id="e435b-381">Opis</span><span class="sxs-lookup"><span data-stu-id="e435b-381">Description</span></span> |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="e435b-382">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="e435b-382">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="e435b-383">Identyfikator zasobu Pixelmap, który ma być wyświetlany dla tej ramki.</span><span class="sxs-lookup"><span data-stu-id="e435b-383">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="e435b-384">Identyfikator może być równy 0.</span><span class="sxs-lookup"><span data-stu-id="e435b-384">The ID can be 0.</span></span> |
| <span data-ttu-id="e435b-385">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="e435b-385">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="e435b-386">Przesunięcie od widgetu Sprite po lewej stronie, aby wyświetlić Pixelmap</span><span class="sxs-lookup"><span data-stu-id="e435b-386">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="e435b-387">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="e435b-387">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="e435b-388">Przesunięcie od elementu widget Sprite góry, aby wyświetlić Pixelmap</span><span class="sxs-lookup"><span data-stu-id="e435b-388">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="e435b-389">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="e435b-389">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="e435b-390">Wartość opóźnienia w taktach czasomierza GUIX, po wyświetleniu tej ramki przed przejściem do następnej ramki Sprite</span><span class="sxs-lookup"><span data-stu-id="e435b-390">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="e435b-391">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="e435b-391">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="e435b-392">Zdefiniuj sposób wymazywania tła.</span><span class="sxs-lookup"><span data-stu-id="e435b-392">Define how the background should be erased.</span></span> <span data-ttu-id="e435b-393">Możliwe wartości dla tego pola to:</span><span class="sxs-lookup"><span data-stu-id="e435b-393">Possible values for this field are:</span></span><br /><span data-ttu-id="e435b-394">GX_SPRITE_BACKGROUND_NO_ACTION: brak wypełniania między ramkami</span><span class="sxs-lookup"><span data-stu-id="e435b-394">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="e435b-395">GX_SPRITE_BACKGROUND_SOLID_FILL: ponowne rysowanie tła Sprite</span><span class="sxs-lookup"><span data-stu-id="e435b-395">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="e435b-396">GX_SPRITE_BACKGROUND_RESTORE: Przywróć poprzedni Pixelmap</span><span class="sxs-lookup"><span data-stu-id="e435b-396">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="e435b-397">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="e435b-397">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="e435b-398">Wartość alfa, która ma zostać dodana do wyświetlanego Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="e435b-398">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="e435b-399">Wartość 255 określa, że nie należy nałożyć dodatkowej wartości alfa.</span><span class="sxs-lookup"><span data-stu-id="e435b-399">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="e435b-400">Jeśli Pixelmap zawiera kanał alfa, ten kanał alfa zostanie dodany do ramki alfa wartości.</span><span class="sxs-lookup"><span data-stu-id="e435b-400">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
