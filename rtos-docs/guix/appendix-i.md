---
title: Dodatek I-GUIX struktury informacji
description: Dowiedz się więcej o strukturach informacji GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 03a10aeb65017befaf5e7b440046dbff9f9252ef
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823113"
---
# <a name="appendix-i---guix-information-structures"></a><span data-ttu-id="b7113-103">Dodatek I-GUIX struktury informacji</span><span class="sxs-lookup"><span data-stu-id="b7113-103">Appendix I - GUIX Information Structures</span></span> 

## <a name="gx_bidi_text_info"></a><span data-ttu-id="b7113-104">GX_BIDI_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-104">GX_BIDI_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7113-105">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-105">Definition</span></span>

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="b7113-106">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-106">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b7113-107">**gx_bidi_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="b7113-107">**gx_bidi_text_info_text**</span></span>               | <span data-ttu-id="b7113-108">Tekst do zmiany kolejności</span><span class="sxs-lookup"><span data-stu-id="b7113-108">Text for reordering</span></span> |
| <span data-ttu-id="b7113-109">**gx_bidi_text_info_font**</span><span class="sxs-lookup"><span data-stu-id="b7113-109">**gx_bidi_text_info_font**</span></span>               | <span data-ttu-id="b7113-110">Czcionka używana do wyświetlania tekstu, ustawiana na GX_NULL, jeśli podział wiersza nie jest wymagany</span><span class="sxs-lookup"><span data-stu-id="b7113-110">Font used to display text, set it to GX_NULL if line breaking is not needed</span></span> |
| <span data-ttu-id="b7113-111">**gx_bidi_text_info_display_width**</span><span class="sxs-lookup"><span data-stu-id="b7113-111">**gx_bidi_text_info_display_width**</span></span>      | <span data-ttu-id="b7113-112">Dostępna szerokość wyświetlania, ustaw ją na wartość-1, jeśli podział wiersza nie jest wymagany</span><span class="sxs-lookup"><span data-stu-id="b7113-112">Available width for displaying, set it to -1 if line breaking is not needed</span></span> |

## <a name="gx_bidi_resolved_text_info"></a><span data-ttu-id="b7113-113">GX_BIDI_RESOLVED_TEXT_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-113">GX_BIDI_RESOLVED_TEXT_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7113-114">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-114">Definition</span></span>

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

### <a name="members"></a><span data-ttu-id="b7113-115">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-115">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b7113-116">**gx_bidi_resolved_text_info_text**</span><span class="sxs-lookup"><span data-stu-id="b7113-116">**gx_bidi_resolved_text_info_text**</span></span>             | <span data-ttu-id="b7113-117">Wskaźnik do tablicy zmiany kolejności tekstu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="b7113-117">Pointer to the array of reordered bidi text</span></span> |
| <span data-ttu-id="b7113-118">**gx_bidi_resolved_text_info_total_lines**</span><span class="sxs-lookup"><span data-stu-id="b7113-118">**gx_bidi_resolved_text_info_total_lines**</span></span>      | <span data-ttu-id="b7113-119">Łączna liczba wierszy rozwiązanego tekstu dwukierunkowego w jednym akapicie</span><span class="sxs-lookup"><span data-stu-id="b7113-119">Total lines of resolved bidi text for one paragraph</span></span> |
| <span data-ttu-id="b7113-120">**gx_bidi_resolved_text_info_next**</span><span class="sxs-lookup"><span data-stu-id="b7113-120">**gx_bidi_resolved_text_info_next**</span></span>             | <span data-ttu-id="b7113-121">Rozpoznano informacje o tekście dwukierunkowym dla następnego akapitu</span><span class="sxs-lookup"><span data-stu-id="b7113-121">Resolved bidi text information for the next paragraph</span></span> |

## <a name="gx_circular_gauge_info"></a><span data-ttu-id="b7113-122">GX_CIRCULAR_GAUGE_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-122">GX_CIRCULAR_GAUGE_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b7113-123">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-123">Definition</span></span>

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
### <a name="members"></a><span data-ttu-id="b7113-124">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-124">Members</span></span>

|                                                  |                                              |
| ------------------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="b7113-125">**gx_circular_gauge_info_animation_steps**</span><span class="sxs-lookup"><span data-stu-id="b7113-125">**gx_circular_gauge_info_animation_steps**</span></span>       | <span data-ttu-id="b7113-126">Łączna liczba kroków przenoszonych przez wskazówkę podczas przesuwania z bieżącego kąta wskazówki do nowo przypisanego kąta wskazówki</span><span class="sxs-lookup"><span data-stu-id="b7113-126">Total steps the needle will travel through when moving from the current needle angle to a newly assigned needle angle</span></span> |
| <span data-ttu-id="b7113-127">**gx_circular_gauge_info_animation_delay**</span><span class="sxs-lookup"><span data-stu-id="b7113-127">**gx_circular_gauge_info_animation_delay**</span></span>       | <span data-ttu-id="b7113-128">Liczba taktów zegara GUIX na opóźnienie między krokami animacji</span><span class="sxs-lookup"><span data-stu-id="b7113-128">The number of GUIX clock ticks to delay between animation steps</span></span> |
| <span data-ttu-id="b7113-129">**gx_circular_gauge_info_needle_xpos**</span><span class="sxs-lookup"><span data-stu-id="b7113-129">**gx_circular_gauge_info_needle_xpos**</span></span>           | <span data-ttu-id="b7113-130">Odległość od lewej krawędzi widgetu miernika do środka obrotu wskazówki</span><span class="sxs-lookup"><span data-stu-id="b7113-130">The distance from the left of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b7113-131">**gx_circular_gauge_info_needle_ypos**</span><span class="sxs-lookup"><span data-stu-id="b7113-131">**gx_circular_gauge_info_needle_ypos**</span></span>           | <span data-ttu-id="b7113-132">Odległość od góry widżetu miernika do środka obrotu wskazówki dotyczącej miernika</span><span class="sxs-lookup"><span data-stu-id="b7113-132">The distance from the top of the gauge widget to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b7113-133">**gx_circular_gauge_info_needle_xcor**</span><span class="sxs-lookup"><span data-stu-id="b7113-133">**gx_circular_gauge_info_needle_xcor**</span></span>           | <span data-ttu-id="b7113-134">Odległość od lewej krawędzi obrazu wskazówki do środka obrotu wskazówki dotyczącego miernika</span><span class="sxs-lookup"><span data-stu-id="b7113-134">The distance from the left of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b7113-135">**gx_circular_gauge_info_needle_ycor**</span><span class="sxs-lookup"><span data-stu-id="b7113-135">**gx_circular_gauge_info_needle_ycor**</span></span>           | <span data-ttu-id="b7113-136">Odległość od góry obrazu wskazówki do środka obrotu wskazówki dotyczącej miernika</span><span class="sxs-lookup"><span data-stu-id="b7113-136">The distance from the top of the needle image to the center-of-rotation of the gauge needle</span></span> |
| <span data-ttu-id="b7113-137">**gx_circular_gauge_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-137">**gx_circular_gauge_info_needle_pixelmap**</span></span>       | <span data-ttu-id="b7113-138">Identyfikator zasobu Pixelmap, który będzie używany do rysowania wskazówki miernika.</span><span class="sxs-lookup"><span data-stu-id="b7113-138">Resource ID of the pixelmap which will be used to draw the gauge needle.</span></span> <span data-ttu-id="b7113-139">Ten obraz zostanie obrócony zgodnie z wymaganiami widżetu miernik, aby wyświetlić wskazówkę miernika w dowolnym położeniu</span><span class="sxs-lookup"><span data-stu-id="b7113-139">This image will be rotated as needed by the gauge widget to display the gauge needle in any position</span></span> |

<span data-ttu-id="b7113-140">Na poniższym diagramie przedstawiono współrzędne xpos, YPos i XCOR, ycor:</span><span class="sxs-lookup"><span data-stu-id="b7113-140">The diagram below illustrates the xpos, ypos, and xcor, ycor coordinates:</span></span>

![Diagram współrzędnych Y i X wskazówki](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a><span data-ttu-id="b7113-142">GX_LINE_CHART_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-142">GX_LINE_CHART_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b7113-143">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-143">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7113-144">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-144">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b7113-145">**gx_line_chart_min_val**</span><span class="sxs-lookup"><span data-stu-id="b7113-145">**gx_line_chart_min_val**</span></span>          | <span data-ttu-id="b7113-146">Minimalna wartość danych, która jest używana do obliczania skalowania</span><span class="sxs-lookup"><span data-stu-id="b7113-146">The minimum data value, which is used to calculate scaling</span></span>
| <span data-ttu-id="b7113-147">**gx_line_chart_max_val**</span><span class="sxs-lookup"><span data-stu-id="b7113-147">**gx_line_chart_max_val**</span></span>          | <span data-ttu-id="b7113-148">Maksymalna wartość danych, która jest używana do obliczania skalowania</span><span class="sxs-lookup"><span data-stu-id="b7113-148">The maximum data value, which is used to calculate scaling</span></span> |
| <span data-ttu-id="b7113-149">**gx_line_chart_data**</span><span class="sxs-lookup"><span data-stu-id="b7113-149">**gx_line_chart_data**</span></span>             | <span data-ttu-id="b7113-150">Wskaźnik na tablicę wartości całkowitych.</span><span class="sxs-lookup"><span data-stu-id="b7113-150">Pointer to an array of integer values.</span></span> <span data-ttu-id="b7113-151">Są to wartości całkowite kreślone przez widżet wykres liniowy</span><span class="sxs-lookup"><span data-stu-id="b7113-151">These are the integer values plotted by the line chart widget</span></span> |
| <span data-ttu-id="b7113-152">**gx_line_ <side> _margin**</span><span class="sxs-lookup"><span data-stu-id="b7113-152">**gx_line_<side>_margin**</span></span>          | <span data-ttu-id="b7113-153">Przesunięcie z okna wykresu jest powiązane z zewnętrznym obszarem renderowania wykresu.</span><span class="sxs-lookup"><span data-stu-id="b7113-153">The offset from the chart window outer bound to the actual chart rendering area.</span></span> <span data-ttu-id="b7113-154">Oś wykresu i linia danych są zawsze kreślone w obrębie tej wewnętrznej granicy, co umożliwia aplikacji rysowanie etykiet i innych informacji wewnątrz okna wykresu, ale poza obszarem grafu znaków</span><span class="sxs-lookup"><span data-stu-id="b7113-154">The chart axis and data line are always plotted within this inner boundary, which allows the application to draw labels and other information inside the chart window but outside the char graphing area</span></span> |
| <span data-ttu-id="b7113-155">**gx_line_chart_max_data_count**</span><span class="sxs-lookup"><span data-stu-id="b7113-155">**gx_line_chart_max_data_count**</span></span>   | <span data-ttu-id="b7113-156">Liczba wartości danych, które mogą być obecne.</span><span class="sxs-lookup"><span data-stu-id="b7113-156">The number of data values which may be present.</span></span> <span data-ttu-id="b7113-157">Ten parametr służy do obliczania skali x lub interwału wykreślania punktów danych.</span><span class="sxs-lookup"><span data-stu-id="b7113-157">This parameter is used for calculating the x-axis scaling or interval for plotting data points.</span></span> |
| <span data-ttu-id="b7113-158">**gx_line_active_data_count**</span><span class="sxs-lookup"><span data-stu-id="b7113-158">**gx_line_active_data_count**</span></span>      | <span data-ttu-id="b7113-159">Liczba wartości danych, które faktycznie znajdują się w tablicy danych.</span><span class="sxs-lookup"><span data-stu-id="b7113-159">The number of data values that actually present in the data array.</span></span> <span data-ttu-id="b7113-160">Wykres liniowy może być skalowany w celu narysowania maksymalnie 100 wartości (na przykład), ale w każdej konkretnej aktualizacji może być rzeczywiście obecne.</span><span class="sxs-lookup"><span data-stu-id="b7113-160">A line chart may be scaled to draw a maximum of 100 values (for example), but on any particular update a smaller number of data values may actually be present.</span></span> |
| <span data-ttu-id="b7113-161">**gx_line_axis_line_width**</span><span class="sxs-lookup"><span data-stu-id="b7113-161">**gx_line_axis_line_width**</span></span>        | <span data-ttu-id="b7113-162">Szerokość linii używana do rysowania osi poziomej i pionowej</span><span class="sxs-lookup"><span data-stu-id="b7113-162">Width of the line used to draw the horizontal and vertical axis</span></span> |
| <span data-ttu-id="b7113-163">**gx_line_data_line_width**</span><span class="sxs-lookup"><span data-stu-id="b7113-163">**gx_line_data_line_width**</span></span>        | <span data-ttu-id="b7113-164">Szerokość wykreślonego wiersza danych</span><span class="sxs-lookup"><span data-stu-id="b7113-164">Width of the plotted data line</span></span> |
| <span data-ttu-id="b7113-165">**gx_line_chart_axis_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-165">**gx_line_chart_axis_color**</span></span>       | <span data-ttu-id="b7113-166">Identyfikator zasobu używany do rysowania linii osi</span><span class="sxs-lookup"><span data-stu-id="b7113-166">Resource ID of the color used to draw the axis lines</span></span> |
| <span data-ttu-id="b7113-167">**gx_line_chart_line_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-167">**gx_line_chart_line_color**</span></span>       | <span data-ttu-id="b7113-168">Identyfikator zasobu używany do rysowania linii danych wykresu</span><span class="sxs-lookup"><span data-stu-id="b7113-168">Resource ID of the color used to draw the chart data line</span></span> |

## <a name="gx_mouse_cursor_info"></a><span data-ttu-id="b7113-169">GX_MOUSE_CURSOR_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-169">GX_MOUSE_CURSOR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7113-170">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-170">Definition</span></span>

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

### <a name="members"></a><span data-ttu-id="b7113-171">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-171">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b7113-172">**gx_mouse_cursor_image_id**</span><span class="sxs-lookup"><span data-stu-id="b7113-172">**gx_mouse_cursor_image_id**</span></span>       | <span data-ttu-id="b7113-173">Identyfikator zasobu obrazu myszy</span><span class="sxs-lookup"><span data-stu-id="b7113-173">Resource ID of the mouse image</span></span> |
| <span data-ttu-id="b7113-174">**gx_mouse_cursor_hotspot_x**</span><span class="sxs-lookup"><span data-stu-id="b7113-174">**gx_mouse_cursor_hotspot_x**</span></span>      | <span data-ttu-id="b7113-175">Przesunięcie od lewej krawędzi obrazu myszy do hotspotu obrazu myszy.</span><span class="sxs-lookup"><span data-stu-id="b7113-175">The offset from the left of the mouse image to the mouse image hotspot</span></span> |
| <span data-ttu-id="b7113-176">**gx_mouse_cursor_hotspot_y**</span><span class="sxs-lookup"><span data-stu-id="b7113-176">**gx_mouse_cursor_hotspot_y**</span></span>      | <span data-ttu-id="b7113-177">Przesunięcie od góry obrazu myszy do hotspotu obrazu myszy.</span><span class="sxs-lookup"><span data-stu-id="b7113-177">The offset from the top of the mouse image to the mouse image hotspot</span></span> |

## <a name="gx_pen_configuration"></a><span data-ttu-id="b7113-178">GX_PEN_CONFIGURATION</span><span class="sxs-lookup"><span data-stu-id="b7113-178">GX_PEN_CONFIGURATION</span></span> 

### <a name="definition"></a><span data-ttu-id="b7113-179">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-179">Definition</span></span>

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

### <a name="members"></a><span data-ttu-id="b7113-180">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-180">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="b7113-181">**gx_pen_configuration_min_drag_dist**</span><span class="sxs-lookup"><span data-stu-id="b7113-181">**gx_pen_configuration_min_drag_dist**</span></span>       | <span data-ttu-id="b7113-182">Minimalną odległość przeciągania na cykl czasomierza GUIX, aby wyzwolić zdarzenie szybkiego ruchu.</span><span class="sxs-lookup"><span data-stu-id="b7113-182">The minimum drag distance per GUIX timer tick to trigger an FLICK event.</span></span> <span data-ttu-id="b7113-183">Wywołaj GX_FIXED_VAL_MAKE, aby utworzyć stałą wartość typu danych</span><span class="sxs-lookup"><span data-stu-id="b7113-183">Call GX_FIXED_VAL_MAKE to make a fixed point data type value</span></span> |
| <span data-ttu-id="b7113-184">**gx_pen_configuration_max_pen_speed_ticks**</span><span class="sxs-lookup"><span data-stu-id="b7113-184">**gx_pen_configuration_max_pen_speed_ticks**</span></span> | <span data-ttu-id="b7113-185">Maksymalna szybkość przeciągania w taktach czasomierza GUIX w celu wyzwalania zdarzenia szybkiego ruchu</span><span class="sxs-lookup"><span data-stu-id="b7113-185">The maximum drag speed in GUIX timer ticks to trigger an FLICK event</span></span> | 

## <a name="gx_pixelmap_slider_info"></a><span data-ttu-id="b7113-186">GX_PIXELMAP_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-186">GX_PIXELMAP_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7113-187">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-187">Definition</span></span>

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

### <a name="members"></a><span data-ttu-id="b7113-188">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-188">Members</span></span>

|                                                       |                                          |
| ----------------------------------------------------- | ---------------------------------------- |
| <span data-ttu-id="b7113-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-189">**gx_pixelmap_slider_info_lower_background_pixelmap**</span></span> | <span data-ttu-id="b7113-190">Identyfikator zasobu Pixelmap do wypełniania tła przed wskazówką.</span><span class="sxs-lookup"><span data-stu-id="b7113-190">Resource ID of the pixelmap for filling the background before the needle.</span></span> <span data-ttu-id="b7113-191">Jeśli nie ustawiono górnego Pixelmap w tle, jest on używany do wypełniania tła przed i po wskazówkę</span><span class="sxs-lookup"><span data-stu-id="b7113-191">If upper background pixelmap is not set, it’s used for filling background both before and after the needle</span></span> |
| <span data-ttu-id="b7113-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-192">**gx_pixelmap_slider_info_upper_background_pixelmap**</span></span> | <span data-ttu-id="b7113-193">Identyfikator zasobu Pixelmap do wypełnienia tła po wskazówki</span><span class="sxs-lookup"><span data-stu-id="b7113-193">Resource ID of the pixelmap for filling background after the needle</span></span> |
| <span data-ttu-id="b7113-194">**gx_pixelmap_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-194">**gx_pixelmap_slider_info_needle_pixelmap**</span></span>           | <span data-ttu-id="b7113-195">Identyfikator zasobu wskazówki Pixelmap</span><span class="sxs-lookup"><span data-stu-id="b7113-195">Resource ID of the needle pixelmap</span></span> |

## <a name="gx_progress_bar_info"></a><span data-ttu-id="b7113-196">GX_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-196">GX_PROGRESS_BAR_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7113-197">**Definicja**</span><span class="sxs-lookup"><span data-stu-id="b7113-197">**Definition**</span></span>

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

### <a name="members"></a><span data-ttu-id="b7113-198">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-198">Members</span></span>

|                                              |                                                  |
| -------------------------------------------- | ------------------------------------------------ |
| <span data-ttu-id="b7113-199">**gx_progress_bar_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="b7113-199">**gx_progress_bar_info_min_val**</span></span>             | <span data-ttu-id="b7113-200">Minimalna raportowana wartość</span><span class="sxs-lookup"><span data-stu-id="b7113-200">Minimum reported value</span></span> |
| <span data-ttu-id="b7113-201">**gx_progress_bar_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="b7113-201">**gx_progress_bar_info_max_val**</span></span>             | <span data-ttu-id="b7113-202">Maksymalna raportowana wartość</span><span class="sxs-lookup"><span data-stu-id="b7113-202">Maximum reported value</span></span> |
| <span data-ttu-id="b7113-203">**gx_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="b7113-203">**gx_progress_bar_info_current_val**</span></span>         | <span data-ttu-id="b7113-204">Bieżąca wartość</span><span class="sxs-lookup"><span data-stu-id="b7113-204">Current value</span></span> |
| <span data-ttu-id="b7113-205">**gx_progress_bar_info_font_id**</span><span class="sxs-lookup"><span data-stu-id="b7113-205">**gx_progress_bar_info_font_id**</span></span>             | <span data-ttu-id="b7113-206">Identyfikator zasobu czcionki używany do rysowania opcjonalnej wartości tekstowej w widżecie pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="b7113-206">Resource ID of the font, used to draw the optional text value within the progress bar widget</span></span>      |
| <span data-ttu-id="b7113-207">**gx_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-207">**gx_progress_bar_normal_text_color**</span></span>        | <span data-ttu-id="b7113-208">Identyfikator zasobu koloru tekstu w normalnym stanie używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="b7113-208">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7113-209">**gx_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-209">**gx_progress_bar_selected_text_color**</span></span>      | <span data-ttu-id="b7113-210">Identyfikator zasobu koloru tekstu, gdy element widget uzyskuje fokus, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="b7113-210">Resource ID of the text color when the widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7113-211">**gx_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-211">**gx_progress_bar_disabled_text_color**</span></span>      | <span data-ttu-id="b7113-212">Identyfikator zasobu koloru tekstu, gdy GX_STYLE_ENABLED nie jest aktywny, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="b7113-212">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7113-213">**gx_progress_bar_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-213">**gx_progress_bar_fill_pixelmap**</span></span>            | <span data-ttu-id="b7113-214">Identyfikator zasobu Pixelmap do wypełnienia tła</span><span class="sxs-lookup"><span data-stu-id="b7113-214">Resource ID of the pixelmap for background filling</span></span>|

## <a name="gx_radial_progress_bar_info"></a><span data-ttu-id="b7113-215">GX_RADIAL_PROGRESS_BAR_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-215">GX_RADIAL_PROGRESS_BAR_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b7113-216">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-216">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7113-217">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-217">Members</span></span>

|                                                   |                                              |
| ------------------------------------------------- | -------------------------------------------- |
| <span data-ttu-id="b7113-218">**gx_radial_progress_bar_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="b7113-218">**gx_radial_progress_bar_info_xcenter**</span></span>           | <span data-ttu-id="b7113-219">Położenie elementu widget w współrzędnej x</span><span class="sxs-lookup"><span data-stu-id="b7113-219">Widget position in x coordinate</span></span> |
| <span data-ttu-id="b7113-220">**gx_radial_progress_bar_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="b7113-220">**gx_radial_progress_bar_info_ycenter**</span></span>           | <span data-ttu-id="b7113-221">Położenie elementu widget w współrzędnym y</span><span class="sxs-lookup"><span data-stu-id="b7113-221">Widget position in y coordinate</span></span>  |
| <span data-ttu-id="b7113-222">**gx_radial_progress_bar_info_radius**</span><span class="sxs-lookup"><span data-stu-id="b7113-222">**gx_radial_progress_bar_info_radius**</span></span>            | <span data-ttu-id="b7113-223">Promień okręgu postępu</span><span class="sxs-lookup"><span data-stu-id="b7113-223">Radius of the progress circle</span></span> |
| <span data-ttu-id="b7113-224">**gx_radial_progress_bar_info_current_val**</span><span class="sxs-lookup"><span data-stu-id="b7113-224">**gx_radial_progress_bar_info_current_val**</span></span>       | <span data-ttu-id="b7113-225">Bieżąca wartość, ograniczona do zakresu [-360, 360], wskazuje różnicę kątową między pozycją zakotwiczenia a punktem końcowym górnego łuku. Wartość ujemna powoduje, że łuk ma być rysowany w kierunku w prawo, rozpoczynając od pozycji zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="b7113-225">Current value, limited to the range [-360, 360], indicates the angular delta between the anchor position and the end point of the upper arc. Negative value causes the arc to be drawn in a clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="b7113-226">Wartość dodatnia powoduje, że łuk ma być rysowany w kierunku przychodzącym w prawo, rozpoczynając od pozycji zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="b7113-226">Positive value causes the arc to be drawn in a counter-clockwise direction starting at the anchor position.</span></span> <span data-ttu-id="b7113-227">Aplikacja musi skalować wskazane wartości rzeczywiste, aby przypisać wartość kątową do widżetu paska postępu.</span><span class="sxs-lookup"><span data-stu-id="b7113-227">The application must scale the real-word value being indicated to assign an angular value to the progress bar widget</span></span> |
| <span data-ttu-id="b7113-228">**gx_radial_progress_bar_anchor_val**</span><span class="sxs-lookup"><span data-stu-id="b7113-228">**gx_radial_progress_bar_anchor_val**</span></span>             | <span data-ttu-id="b7113-229">Kąt początkowy łuku górnego postępu. Wartość jest definiowana w zakresie liczby całkowitej z 0 stopni wskazujących prawy i 90 stopień wskazujący na pozycję prostą.</span><span class="sxs-lookup"><span data-stu-id="b7113-229">Starting angle of the upper progress arc. The value is defined in terms of integer degree with 0 degree pointing to the right and 90 degree indicating straight up position.</span></span> |
| <span data-ttu-id="b7113-230">**gx_radial_progress_bar_font_id**</span><span class="sxs-lookup"><span data-stu-id="b7113-230">**gx_radial_progress_bar_font_id**</span></span>                | <span data-ttu-id="b7113-231">Identyfikator zasobu czcionki używany do rysowania opcjonalnej wartości tekstowej w widżecie pasek postępu.</span><span class="sxs-lookup"><span data-stu-id="b7113-231">Resource ID of the font used to draw the optional text value within the progress bar widget</span></span> |
| <span data-ttu-id="b7113-232">**gx_radial_progress_bar_normal_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-232">**gx_radial_progress_bar_normal_text_color**</span></span>      | <span data-ttu-id="b7113-233">Identyfikator zasobu koloru tekstu w normalnym stanie używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="b7113-233">Resource ID of the text color in normal state, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7113-234">**gx_radial_progress_bar_selected_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-234">**gx_radial_progress_bar_selected_text_color**</span></span>    |<span data-ttu-id="b7113-235">Identyfikator zasobu koloru tekstu, gdy element widget uzyskuje fokus, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="b7113-235">Resource ID of the text color when widget gain focus, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7113-236">**gx_radial_progress_bar_disabled_text_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-236">**gx_radial_progress_bar_disabled_text_color**</span></span>    | <span data-ttu-id="b7113-237">Identyfikator zasobu koloru tekstu, gdy GX_STYLE_ENABLED nie jest aktywny, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu</span><span class="sxs-lookup"><span data-stu-id="b7113-237">Resource ID of the text color when GX_STYLE_ENABLED is not active, used to define the optional text drawing within the progress bar widget</span></span> |
| <span data-ttu-id="b7113-238">**gx_radial_progress_bar_normal_brush_width**</span><span class="sxs-lookup"><span data-stu-id="b7113-238">**gx_radial_progress_bar_normal_brush_width**</span></span>     | <span data-ttu-id="b7113-239">Szerokość dolnego okręgu postępu</span><span class="sxs-lookup"><span data-stu-id="b7113-239">Width of the lower progress circle</span></span> |
| <span data-ttu-id="b7113-240">**gx_radial_progress_bar_selected_brush_width**</span><span class="sxs-lookup"><span data-stu-id="b7113-240">**gx_radial_progress_bar_selected_brush_width**</span></span>   | <span data-ttu-id="b7113-241">Szerokość górnego łuku postępu, górny łuk może być węższy, taki sam jak lub większy niż dolny okrąg</span><span class="sxs-lookup"><span data-stu-id="b7113-241">Width of the upper progress arc, the upper arc may be narrower, the same as, or wider than the lower circle</span></span> |
| <span data-ttu-id="b7113-242">**gx_radial_progress_bar_normal_brush_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-242">**gx_radial_progress_bar_normal_brush_color**</span></span>     | <span data-ttu-id="b7113-243">Identyfikator zasobu koloru do wypełnienia dolnego okręgu postępu</span><span class="sxs-lookup"><span data-stu-id="b7113-243">Resource ID of the color to fill lower progress circle</span></span> |
| <span data-ttu-id="b7113-244">**gx_radial_progress_bar_selected_brush_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-244">**gx_radial_progress_bar_selected_brush_color**</span></span>   | <span data-ttu-id="b7113-245">Identyfikator zasobu koloru do wypełnienia łuku górnego postępu</span><span class="sxs-lookup"><span data-stu-id="b7113-245">Resource ID of the color to fill upper progress arc</span></span> |

## <a name="gx_radial_slider_info"></a><span data-ttu-id="b7113-246">GX_RADIAL_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-246">GX_RADIAL_SLIDER_INFO</span></span> 

### <a name="definition"></a><span data-ttu-id="b7113-247">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-247">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7113-248">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-248">Members</span></span>

|                                               |                                                  |
| --------------------------------------------- | ------------------------------------------------ |
<span data-ttu-id="b7113-249">**gx_radial_slider_info_xcenter**</span><span class="sxs-lookup"><span data-stu-id="b7113-249">**gx_radial_slider_info_xcenter**</span></span>               | <span data-ttu-id="b7113-250">Odległość od lewej krawędzi elementu widget suwaka do środka obrotu wskazówki kontrolki suwaka</span><span class="sxs-lookup"><span data-stu-id="b7113-250">Distance from the left of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="b7113-251">**gx_radial_slider_info_ycenter**</span><span class="sxs-lookup"><span data-stu-id="b7113-251">**gx_radial_slider_info_ycenter**</span></span>             | <span data-ttu-id="b7113-252">Odległość od góry elementu widget suwaka do środka obrotu wskazówki kontrolki suwaka</span><span class="sxs-lookup"><span data-stu-id="b7113-252">Distance from the top of the slider widget to the center-of-rotation of the slider needle</span></span> |
| <span data-ttu-id="b7113-253">**gx_radial_slider_info_radius**</span><span class="sxs-lookup"><span data-stu-id="b7113-253">**gx_radial_slider_info_radius**</span></span>              | <span data-ttu-id="b7113-254">Promień okręgu suwaka promieniowego</span><span class="sxs-lookup"><span data-stu-id="b7113-254">Radius of the radial slider circle</span></span> |
| <span data-ttu-id="b7113-255">**gx_radial_slider_info_track_width**</span><span class="sxs-lookup"><span data-stu-id="b7113-255">**gx_radial_slider_info_track_width**</span></span>         | <span data-ttu-id="b7113-256">Szerokość kontrolki suwaka promieniowego</span><span class="sxs-lookup"><span data-stu-id="b7113-256">Width of radial slider track</span></span> |
| <span data-ttu-id="b7113-257">**gx_radial_slider_info_current_angle**</span><span class="sxs-lookup"><span data-stu-id="b7113-257">**gx_radial_slider_info_current_angle**</span></span>       | <span data-ttu-id="b7113-258">Bieżący kąt suwaka</span><span class="sxs-lookup"><span data-stu-id="b7113-258">Current slider angle</span></span> |
| <span data-ttu-id="b7113-259">**gx_radial_slider_info_min_angle**</span><span class="sxs-lookup"><span data-stu-id="b7113-259">**gx_radial_slider_info_min_angle**</span></span>           | <span data-ttu-id="b7113-260">Minimalny kąt suwaka</span><span class="sxs-lookup"><span data-stu-id="b7113-260">Minimum slider angle</span></span> |
| <span data-ttu-id="b7113-261">**gx_radial_slider_info_max_angle**</span><span class="sxs-lookup"><span data-stu-id="b7113-261">**gx_radial_slider_info_max_angle**</span></span>           | <span data-ttu-id="b7113-262">Maksymalny kąt suwaka</span><span class="sxs-lookup"><span data-stu-id="b7113-262">Maximum slider angle</span></span> |
| <span data-ttu-id="b7113-263">**gx_radial_slider_info_angle_list**</span><span class="sxs-lookup"><span data-stu-id="b7113-263">**gx_radial_slider_info_angle_list**</span></span>          | <span data-ttu-id="b7113-264">Lista wartości kątowych, definiuje kąty kotwicowe, jeśli jest ustawiona, kąt suwaka może być tylko jednym ze zdefiniowanych kątów zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="b7113-264">Angle value list, defines anchor angles, if set, slider angle can only be one of the defined anchor angles</span></span> |
| <span data-ttu-id="b7113-265">**gx_radial_slider_info_list_count**</span><span class="sxs-lookup"><span data-stu-id="b7113-265">**gx_radial_slider_info_list_count**</span></span>          | <span data-ttu-id="b7113-266">Liczba kątów zakotwiczenia</span><span class="sxs-lookup"><span data-stu-id="b7113-266">Number of anchor angles</span></span> |
| <span data-ttu-id="b7113-267">**gx_radial_slider_info_background_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-267">**gx_radial_slider_info_background_pixelmap**</span></span> | <span data-ttu-id="b7113-268">Identyfikator zasobu w tle Pixelmap</span><span class="sxs-lookup"><span data-stu-id="b7113-268">Resource ID of background pixelmap</span></span> |
| <span data-ttu-id="b7113-269">**gx_radial_slider_info_needle_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-269">**gx_radial_slider_info_needle_pixelmap**</span></span>     | <span data-ttu-id="b7113-270">Identyfikator zasobu wskazówki Pixelmap</span><span class="sxs-lookup"><span data-stu-id="b7113-270">Resource ID of needle pixelmap</span></span> |

## <a name="gx_rectangle"></a><span data-ttu-id="b7113-271">GX_RECTANGLE</span><span class="sxs-lookup"><span data-stu-id="b7113-271">GX_RECTANGLE</span></span>

### <a name="definition"></a><span data-ttu-id="b7113-272">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-272">Definition</span></span>

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

### <a name="members"></a><span data-ttu-id="b7113-273">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-273">Members</span></span>

|                                  |                         |
| -------------------------------- | ------------------------|
| <span data-ttu-id="b7113-274">**gx_rectangle_left**</span><span class="sxs-lookup"><span data-stu-id="b7113-274">**gx_rectangle_left**</span></span>            | <span data-ttu-id="b7113-275">Po lewej stronie prostokąta</span><span class="sxs-lookup"><span data-stu-id="b7113-275">Left of the rectangle</span></span>   |  
| <span data-ttu-id="b7113-276">**gx_rectangle_top**</span><span class="sxs-lookup"><span data-stu-id="b7113-276">**gx_rectangle_top**</span></span>             | <span data-ttu-id="b7113-277">Góra prostokąta</span><span class="sxs-lookup"><span data-stu-id="b7113-277">Top of the rectangle</span></span>    | 
| <span data-ttu-id="b7113-278">**gx_rectangle_right**</span><span class="sxs-lookup"><span data-stu-id="b7113-278">**gx_rectangle_right**</span></span>           | <span data-ttu-id="b7113-279">Z prawej strony prostokąta</span><span class="sxs-lookup"><span data-stu-id="b7113-279">Right of the rectangle</span></span>  |
| <span data-ttu-id="b7113-280">**gx_rectangle_bottom**</span><span class="sxs-lookup"><span data-stu-id="b7113-280">**gx_rectangle_bottom**</span></span>          | <span data-ttu-id="b7113-281">Dolna część prostokąta</span><span class="sxs-lookup"><span data-stu-id="b7113-281">Bottom of the rectangle</span></span> |

## <a name="gx_rich_text_fonts"></a><span data-ttu-id="b7113-282">GX_RICH_TEXT_FONTS</span><span class="sxs-lookup"><span data-stu-id="b7113-282">GX_RICH_TEXT_FONTS</span></span> 

### <a name="definition"></a><span data-ttu-id="b7113-283">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-283">Definition</span></span>

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

### <a name="members"></a><span data-ttu-id="b7113-284">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-284">Members</span></span>

|                                    |                                                            |
| ---------------------------------- | ---------------------------------------------------------- |
| <span data-ttu-id="b7113-285">**gx_rich_text_fonts_normal_id**</span><span class="sxs-lookup"><span data-stu-id="b7113-285">**gx_rich_text_fonts_normal_id**</span></span>   | <span data-ttu-id="b7113-286">Identyfikator zasobu zwykłej czcionki tekstu</span><span class="sxs-lookup"><span data-stu-id="b7113-286">Resource ID of normal text font</span></span> |
| <span data-ttu-id="b7113-287">**gx_rich_text_fonts_bold_id**</span><span class="sxs-lookup"><span data-stu-id="b7113-287">**gx_rich_text_fonts_bold_id**</span></span>     | <span data-ttu-id="b7113-288">Identyfikator zasobu czcionki pogrubionej tekstu</span><span class="sxs-lookup"><span data-stu-id="b7113-288">Resource ID of bold text font</span></span> |
| <span data-ttu-id="b7113-289">**gx_rich_text_fonts_italic_id**</span><span class="sxs-lookup"><span data-stu-id="b7113-289">**gx_rich_text_fonts_italic_id**</span></span>   | <span data-ttu-id="b7113-290">Identyfikator zasobu czcionki tekstu kursywy</span><span class="sxs-lookup"><span data-stu-id="b7113-290">Resource ID of italic text font</span></span> |
| <span data-ttu-id="b7113-291">**gx_rich_text_fonts_bold_italic_id**</span><span class="sxs-lookup"><span data-stu-id="b7113-291">**gx_rich_text_fonts_bold_italic_id**</span></span> | <span data-ttu-id="b7113-292">Identyfikator zasobu czcionki pogrubionej kursywy</span><span class="sxs-lookup"><span data-stu-id="b7113-292">Resource ID of bold italic text font</span></span> |

## <a name="gx_scroll_info"></a><span data-ttu-id="b7113-293">GX_SCROLL_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-293">GX_SCROLL_INFO</span></span> 
### <a name="definition"></a><span data-ttu-id="b7113-294">**Definicja**</span><span class="sxs-lookup"><span data-stu-id="b7113-294">**Definition**</span></span>

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

### <a name="members"></a><span data-ttu-id="b7113-295">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-295">Members</span></span>

|                         |                               |
| ----------------------- | ----------------------------- |
| <span data-ttu-id="b7113-296">**gx_scroll_value**</span><span class="sxs-lookup"><span data-stu-id="b7113-296">**gx_scroll_value**</span></span>     | <span data-ttu-id="b7113-297">Bieżąca pozycja przewijania</span><span class="sxs-lookup"><span data-stu-id="b7113-297">Current scroll position</span></span>       |
| <span data-ttu-id="b7113-298">**gx_scroll_minimum**</span><span class="sxs-lookup"><span data-stu-id="b7113-298">**gx_scroll_minimum**</span></span>   | <span data-ttu-id="b7113-299">Minimalna zgłoszona pozycja</span><span class="sxs-lookup"><span data-stu-id="b7113-299">Minimum reported position</span></span>     |
| <span data-ttu-id="b7113-300">**gx_scroll_maximum**</span><span class="sxs-lookup"><span data-stu-id="b7113-300">**gx_scroll_maximum**</span></span>   | <span data-ttu-id="b7113-301">Maksymalna zgłoszona pozycja</span><span class="sxs-lookup"><span data-stu-id="b7113-301">Maximum reported position</span></span>     |
| <span data-ttu-id="b7113-302">**gx_scroll_visible**</span><span class="sxs-lookup"><span data-stu-id="b7113-302">**gx_scroll_visible**</span></span>   | <span data-ttu-id="b7113-303">Widoczny zakres okna nadrzędnego</span><span class="sxs-lookup"><span data-stu-id="b7113-303">Parent window visible range</span></span>   |
| <span data-ttu-id="b7113-304">**gx_scroll_increment**</span><span class="sxs-lookup"><span data-stu-id="b7113-304">**gx_scroll_increment**</span></span> | <span data-ttu-id="b7113-305">Minimalna wartość różnicowa ScrollBar</span><span class="sxs-lookup"><span data-stu-id="b7113-305">Scrollbar minimum delta value</span></span> |

## <a name="gx_scrollbar_appearance"></a><span data-ttu-id="b7113-306">GX_SCROLLBAR_APPEARANCE</span><span class="sxs-lookup"><span data-stu-id="b7113-306">GX_SCROLLBAR_APPEARANCE</span></span> 

### <a name="definition"></a><span data-ttu-id="b7113-307">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-307">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7113-308">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-308">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="b7113-309">**gx_scroll_width**</span><span class="sxs-lookup"><span data-stu-id="b7113-309">**gx_scroll_width**</span></span>                      | <span data-ttu-id="b7113-310">Szerokość widżetu ScrollBar w pikselach</span><span class="sxs-lookup"><span data-stu-id="b7113-310">Width of the scrollbar widget, in pixels</span></span> |
| <span data-ttu-id="b7113-311">**gx_scroll_thumb_width**</span><span class="sxs-lookup"><span data-stu-id="b7113-311">**gx_scroll_thumb_width**</span></span>                | <span data-ttu-id="b7113-312">Szerokość przycisku przewijania, które slajdy na pasku przewijania (w pikselach).</span><span class="sxs-lookup"><span data-stu-id="b7113-312">Width of the thumb button which slides on the scrollbar, in pixels.</span></span> <span data-ttu-id="b7113-313">Ta wartość jest zwykle pewną liczbą pikseli mniejszą niż całkowita szerokość paska przewijania.</span><span class="sxs-lookup"><span data-stu-id="b7113-313">This value is usually some number of pixels less than the total scrollbar width</span></span> |
| <span data-ttu-id="b7113-314">**gx_scroll_thumb_travel_min**</span><span class="sxs-lookup"><span data-stu-id="b7113-314">**gx_scroll_thumb_travel_min**</span></span>           | <span data-ttu-id="b7113-315">Przesunięcie od końca paska przewijania do minimalnego punktu podróży przycisku przewijania.</span><span class="sxs-lookup"><span data-stu-id="b7113-315">Offset from the end of scrollbar to minimum thumb button travel point.</span></span> <span data-ttu-id="b7113-316">Tego limitu można użyć, aby zapobiec przeniesieniu przycisku przewijania na koniec paska przewijania.</span><span class="sxs-lookup"><span data-stu-id="b7113-316">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="b7113-317">**gx_scroll_thumb_travel_max**</span><span class="sxs-lookup"><span data-stu-id="b7113-317">**gx_scroll_thumb_travel_max**</span></span>           | <span data-ttu-id="b7113-318">Przesunięcie od końca paska przewijania do maksymalnego punktu podróży przycisku przewijania.</span><span class="sxs-lookup"><span data-stu-id="b7113-318">Offset from the end of scrollbar to maximum thumb button travel point.</span></span> <span data-ttu-id="b7113-319">Tego limitu można użyć, aby zapobiec przeniesieniu przycisku przewijania na koniec paska przewijania.</span><span class="sxs-lookup"><span data-stu-id="b7113-319">This limit can be used to prevent the thumb button from traveling to the very end of the scrollbar</span></span> |
| <span data-ttu-id="b7113-320">**gx_scroll_thumb_border_style**</span><span class="sxs-lookup"><span data-stu-id="b7113-320">**gx_scroll_thumb_border_style**</span></span>         | <span data-ttu-id="b7113-321">Style obramowania przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="b7113-321">Border styles of thumb button</span></span> |
| <span data-ttu-id="b7113-322">**gx_scroll_fill_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-322">**gx_scroll_fill_pixelmap**</span></span>              | <span data-ttu-id="b7113-323">Opcjonalny identyfikator Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="b7113-323">Optional pixelmap ID.</span></span> <span data-ttu-id="b7113-324">Jeśli ten identyfikator Pixelmap nie jest zerem, pasek przewijania używa tego Pixelmap do rysowania tła paska przewijania</span><span class="sxs-lookup"><span data-stu-id="b7113-324">If this pixelmap ID is not zero, the scrollbar uses this pixelmap to draw the scrollbar background</span></span> |
| <span data-ttu-id="b7113-325">**gx_scroll_thumb_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-325">**gx_scroll_thumb_pixelmap**</span></span>             | <span data-ttu-id="b7113-326">Opcjonalny identyfikator Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="b7113-326">Optional pixelmap ID.</span></span> <span data-ttu-id="b7113-327">Jeśli ten identyfikator Pixelmap ma wartość różną od zera, przycisk przewijania ScrollBar używa tego Pixelmap do rysowania</span><span class="sxs-lookup"><span data-stu-id="b7113-327">If this pixelmap ID is not zero, the scrollbar thumb button uses this pixelmap to draw itself</span></span> |
| <span data-ttu-id="b7113-328">**gx_scroll_up_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-328">**gx_scroll_up_pixelmap**</span></span>                | <span data-ttu-id="b7113-329">Opcjonalny identyfikator Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="b7113-329">Optional pixelmap ID.</span></span> <span data-ttu-id="b7113-330">Jeśli ten identyfikator Pixelmap ma wartość różną od zera, pasek przewijania używa tego identyfikatora Pixelmap do rysowania przycisku przewijania w lewo/w górę</span><span class="sxs-lookup"><span data-stu-id="b7113-330">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar left/up end button</span></span> |
| <span data-ttu-id="b7113-331">**gx_scroll_down_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-331">**gx_scroll_down_pixelmap**</span></span>              | <span data-ttu-id="b7113-332">Opcjonalny identyfikator Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="b7113-332">Optional pixelmap ID.</span></span> <span data-ttu-id="b7113-333">Jeśli ten identyfikator Pixelmap ma wartość różną od zera, pasek przewijania używa tego identyfikatora Pixelmap do rysowania przycisku końca w prawym/dół paska przewijania</span><span class="sxs-lookup"><span data-stu-id="b7113-333">If this pixelmap ID is not zero, the scrollbar uses this pixelmap ID to draw the scrollbar right/down end button</span></span> |
| <span data-ttu-id="b7113-334">**gx_scroll_thumb_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-334">**gx_scroll_thumb_color**</span></span>                | <span data-ttu-id="b7113-335">Identyfikator zasobu koloru używany do wypełnienia przycisku przewijania</span><span class="sxs-lookup"><span data-stu-id="b7113-335">Resource ID of color used to fill thumb button</span></span> |
| <span data-ttu-id="b7113-336">**gx_scroll_thumb_border_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-336">**gx_scroll_thumb_border_color**</span></span>         | <span data-ttu-id="b7113-337">Identyfikator zasobu koloru używany do rysowania obramowania przycisku kciuka</span><span class="sxs-lookup"><span data-stu-id="b7113-337">Resource ID of color used to draw the border of thumb button</span></span> | 
| <span data-ttu-id="b7113-338">**gx_scroll_button_color**</span><span class="sxs-lookup"><span data-stu-id="b7113-338">**gx_scroll_button_color**</span></span>               | <span data-ttu-id="b7113-339">Identyfikator zasobu koloru używany do wypełniania przycisków końca paska przewijania</span><span class="sxs-lookup"><span data-stu-id="b7113-339">Resource ID of color used to fill scrollbar end buttons</span></span> |

## <a name="gx_slider_info"></a><span data-ttu-id="b7113-340">GX_SLIDER_INFO</span><span class="sxs-lookup"><span data-stu-id="b7113-340">GX_SLIDER_INFO</span></span>

### <a name="definition"></a><span data-ttu-id="b7113-341">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-341">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7113-342">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-342">Members</span></span>

|                                         |                                                        |
| --------------------------------------- | ------------------------------------------------------ |
| <span data-ttu-id="b7113-343">**gx_slider_info_min_val**</span><span class="sxs-lookup"><span data-stu-id="b7113-343">**gx_slider_info_min_val**</span></span>              | <span data-ttu-id="b7113-344">Minimalna raportowana wartość</span><span class="sxs-lookup"><span data-stu-id="b7113-344">Minimum reported value</span></span> |
| <span data-ttu-id="b7113-345">**gx_slider_info_max_val**</span><span class="sxs-lookup"><span data-stu-id="b7113-345">**gx_slider_info_max_val**</span></span>              | <span data-ttu-id="b7113-346">Maksymalna raportowana wartość</span><span class="sxs-lookup"><span data-stu-id="b7113-346">Maximum reported value</span></span> |
| <span data-ttu-id="b7113-347">**gx_slider_info_current_value**</span><span class="sxs-lookup"><span data-stu-id="b7113-347">**gx_slider_info_current_value**</span></span>        | <span data-ttu-id="b7113-348">Bieżąca wartość</span><span class="sxs-lookup"><span data-stu-id="b7113-348">Current value</span></span> |
| <span data-ttu-id="b7113-349">**gx_slider_info_min_travel**</span><span class="sxs-lookup"><span data-stu-id="b7113-349">**gx_slider_info_min_travel**</span></span>           | <span data-ttu-id="b7113-350">Limit podróży wskazówki</span><span class="sxs-lookup"><span data-stu-id="b7113-350">Needle travel limit</span></span> |
| <span data-ttu-id="b7113-351">**gx_slider_info_max_travel**</span><span class="sxs-lookup"><span data-stu-id="b7113-351">**gx_slider_info_max_travel**</span></span>           | <span data-ttu-id="b7113-352">Limit podróży wskazówki</span><span class="sxs-lookup"><span data-stu-id="b7113-352">Needle travel limit</span></span> |
| <span data-ttu-id="b7113-353">**gx_slider_info_needle_width**</span><span class="sxs-lookup"><span data-stu-id="b7113-353">**gx_slider_info_needle_width**</span></span>         | <span data-ttu-id="b7113-354">Szerokość wskazówki w pikselach</span><span class="sxs-lookup"><span data-stu-id="b7113-354">Needle width in pixel</span></span> |
| <span data-ttu-id="b7113-355">**gx_slider_info_needle_height**</span><span class="sxs-lookup"><span data-stu-id="b7113-355">**gx_slider_info_needle_height**</span></span>        | <span data-ttu-id="b7113-356">Wysokość wskazówki (w pikselach)</span><span class="sxs-lookup"><span data-stu-id="b7113-356">Needle height in pixel</span></span> |
|<span data-ttu-id="b7113-357">**gx_slider_info_needle_inset**</span><span class="sxs-lookup"><span data-stu-id="b7113-357">**gx_slider_info_needle_inset**</span></span>          | <span data-ttu-id="b7113-358">Pozycja rysowania wskazówki.</span><span class="sxs-lookup"><span data-stu-id="b7113-358">Needle draw position.</span></span> <span data-ttu-id="b7113-359">Jeśli ustawiono GX_STYLE_SLIDER_VERTICAL, służy do określania przesunięcia od pozycji początku rysowania wskazówki do lewego suwaka.</span><span class="sxs-lookup"><span data-stu-id="b7113-359">If GX_STYLE_SLIDER_VERTICAL is set, used to specify the offset from the needle draw start position to the slider left.</span></span> <span data-ttu-id="b7113-360">Else, używany do określania przesunięcia od pozycji początkowej rysowania wskazówki do górnej krawędzi suwaka.</span><span class="sxs-lookup"><span data-stu-id="b7113-360">Else, used to specify the offset from the needle draw start position to the slider top.</span></span> |
| <span data-ttu-id="b7113-361">**gx_slider_info_needle_hotspot_offset**</span><span class="sxs-lookup"><span data-stu-id="b7113-361">**gx_slider_info_needle_hotspot_offset**</span></span> | <span data-ttu-id="b7113-362">Wskazówki hotpot_offset, używane do określania przesunięcia od pozycji początkowej rysowania wskazówki do punktu aktywnego suwaka.</span><span class="sxs-lookup"><span data-stu-id="b7113-362">Needle hotpot_offset, used to specify the offset from the needle draw start position to the slider hotspot.</span></span> |

## <a name="gx_sprite_frame"></a><span data-ttu-id="b7113-363">GX_SPRITE_FRAME</span><span class="sxs-lookup"><span data-stu-id="b7113-363">GX_SPRITE_FRAME</span></span>

### <a name="definition"></a><span data-ttu-id="b7113-364">Definicja</span><span class="sxs-lookup"><span data-stu-id="b7113-364">Definition</span></span>

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

### <a name="members"></a><span data-ttu-id="b7113-365">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b7113-365">Members</span></span>

|                                          |                                                       |
| ---------------------------------------- | ----------------------------------------------------- |
| <span data-ttu-id="b7113-366">**gx_sprite_frame_pixelmap**</span><span class="sxs-lookup"><span data-stu-id="b7113-366">**gx_sprite_frame_pixelmap**</span></span>             | <span data-ttu-id="b7113-367">Identyfikator zasobu Pixelmap, który ma być wyświetlany dla tej ramki.</span><span class="sxs-lookup"><span data-stu-id="b7113-367">Resource ID of the pixelmap to be displayed for this frame.</span></span> <span data-ttu-id="b7113-368">Identyfikator może być równy 0.</span><span class="sxs-lookup"><span data-stu-id="b7113-368">The ID can be 0.</span></span> |
| <span data-ttu-id="b7113-369">**gx_sprite_frame_x_offset**</span><span class="sxs-lookup"><span data-stu-id="b7113-369">**gx_sprite_frame_x_offset**</span></span>             | <span data-ttu-id="b7113-370">Przesunięcie od widgetu Sprite po lewej stronie, aby wyświetlić Pixelmap</span><span class="sxs-lookup"><span data-stu-id="b7113-370">Offset from the sprite widget left to display the pixelmap</span></span> |
| <span data-ttu-id="b7113-371">**gx_sprite_frame_y_offset**</span><span class="sxs-lookup"><span data-stu-id="b7113-371">**gx_sprite_frame_y_offset**</span></span>             | <span data-ttu-id="b7113-372">Przesunięcie od elementu widget Sprite góry, aby wyświetlić Pixelmap</span><span class="sxs-lookup"><span data-stu-id="b7113-372">Offset from the sprite widget top to display the pixelmap</span></span> |
| <span data-ttu-id="b7113-373">**gx_sprite_frame_delay**</span><span class="sxs-lookup"><span data-stu-id="b7113-373">**gx_sprite_frame_delay**</span></span>                | <span data-ttu-id="b7113-374">Wartość opóźnienia w taktach czasomierza GUIX, po wyświetleniu tej ramki przed przejściem do następnej ramki Sprite</span><span class="sxs-lookup"><span data-stu-id="b7113-374">Delay value, in GUIX timer ticks, after displaying this frame before advancing to the next sprite frame</span></span> |
| <span data-ttu-id="b7113-375">**gx_sprite_frame_background_operation**</span><span class="sxs-lookup"><span data-stu-id="b7113-375">**gx_sprite_frame_background_operation**</span></span> | <span data-ttu-id="b7113-376">Zdefiniuj sposób wymazywania tła.</span><span class="sxs-lookup"><span data-stu-id="b7113-376">Define how the background should be erased.</span></span> <span data-ttu-id="b7113-377">Możliwe wartości dla tego pola to:</span><span class="sxs-lookup"><span data-stu-id="b7113-377">Possible values for this field are:</span></span><br /><span data-ttu-id="b7113-378">GX_SPRITE_BACKGROUND_NO_ACTION: brak wypełniania między ramkami</span><span class="sxs-lookup"><span data-stu-id="b7113-378">GX_SPRITE_BACKGROUND_NO_ACTION: No fill between frames</span></span><br /><span data-ttu-id="b7113-379">GX_SPRITE_BACKGROUND_SOLID_FILL: ponowne rysowanie tła Sprite</span><span class="sxs-lookup"><span data-stu-id="b7113-379">GX_SPRITE_BACKGROUND_SOLID_FILL: Redraw sprite background</span></span><br /><span data-ttu-id="b7113-380">GX_SPRITE_BACKGROUND_RESTORE: Przywróć poprzedni Pixelmap</span><span class="sxs-lookup"><span data-stu-id="b7113-380">GX_SPRITE_BACKGROUND_RESTORE: Restore previous pixelmap</span></span> |
| <span data-ttu-id="b7113-381">**gx_sprite_frame_alpha**</span><span class="sxs-lookup"><span data-stu-id="b7113-381">**gx_sprite_frame_alpha**</span></span>                | <span data-ttu-id="b7113-382">Wartość alfa, która ma zostać dodana do wyświetlanego Pixelmap.</span><span class="sxs-lookup"><span data-stu-id="b7113-382">Alpha value to be added to the displayed pixelmap.</span></span> <span data-ttu-id="b7113-383">Wartość 255 określa, że nie należy nałożyć dodatkowej wartości alfa.</span><span class="sxs-lookup"><span data-stu-id="b7113-383">The value 255 specifies that no extra alpha value should be imposed.</span></span> <span data-ttu-id="b7113-384">Jeśli Pixelmap zawiera kanał alfa, ten kanał alfa zostanie dodany do ramki alfa wartości.</span><span class="sxs-lookup"><span data-stu-id="b7113-384">If the pixelmap includes an alpha channel, this alpha channel will be added to the frame alpha value.</span></span> |
