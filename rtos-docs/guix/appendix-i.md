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
# <a name="appendix-i---guix-information-structures"></a>Dodatek I-GUIX struktury informacji 

## <a name="gx_bidi_text_info"></a>GX_BIDI_TEXT_INFO 

### <a name="definition"></a>Definicja

```c
typedef struct GX_BIDI_TEXT_INFO_STRUCT
{
    GX_STRING gx_bidi_text_info_text;
    GX_FONT  *gx_bidi_text_info_font;
    GX_VALUE  gx_bidi_text_info_display_width;
} GX_BIDI_TEXT_INFO;
```
| Elementy członkowskie | Opis |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_text_info_text**               | Tekst do zmiany kolejności |
| **gx_bidi_text_info_font**               | Czcionka używana do wyświetlania tekstu, ustawiana na GX_NULL, jeśli podział wiersza nie jest wymagany |
| **gx_bidi_text_info_display_width**      | Dostępna szerokość wyświetlania, ustaw ją na wartość-1, jeśli podział wiersza nie jest wymagany |

## <a name="gx_bidi_resolved_text_info"></a>GX_BIDI_RESOLVED_TEXT_INFO 

### <a name="definition"></a>Definicja

```c
typedef struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT
{
    GX_STRING                                *gx_bidi_resolved_text_info_text;
    UINT                                      gx_bidi_resolved_text_info_total_lines;
    struct GX_BIDI_RESOLVED_TEXT_INFO_STRUCT *gx_bidi_resolved_text_info_next;
} GX_BIDI_RESOLVED_TEXT_INFO;
```

| Elementy członkowskie | Opis |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_bidi_resolved_text_info_text**             | Wskaźnik do tablicy zmiany kolejności tekstu dwukierunkowego |
| **gx_bidi_resolved_text_info_total_lines**      | Łączna liczba wierszy rozwiązanego tekstu dwukierunkowego w jednym akapicie |
| **gx_bidi_resolved_text_info_next**             | Rozpoznano informacje o tekście dwukierunkowym dla następnego akapitu |

## <a name="gx_circular_gauge_info"></a>GX_CIRCULAR_GAUGE_INFO

### <a name="definition"></a>Definicja

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

| Elementy członkowskie | Opis |
| ------------------------------------------------ | -------------------------------------------- |
| **gx_circular_gauge_info_animation_steps**       | Łączna liczba kroków przenoszonych przez wskazówkę podczas przesuwania z bieżącego kąta wskazówki do nowo przypisanego kąta wskazówki |
| **gx_circular_gauge_info_animation_delay**       | Liczba taktów zegara GUIX na opóźnienie między krokami animacji |
| **gx_circular_gauge_info_needle_xpos**           | Odległość od lewej krawędzi widgetu miernika do środka obrotu wskazówki |
| **gx_circular_gauge_info_needle_ypos**           | Odległość od góry widżetu miernika do środka obrotu wskazówki dotyczącej miernika |
| **gx_circular_gauge_info_needle_xcor**           | Odległość od lewej krawędzi obrazu wskazówki do środka obrotu wskazówki dotyczącego miernika |
| **gx_circular_gauge_info_needle_ycor**           | Odległość od góry obrazu wskazówki do środka obrotu wskazówki dotyczącej miernika |
| **gx_circular_gauge_info_needle_pixelmap**       | Identyfikator zasobu Pixelmap, który będzie używany do rysowania wskazówki miernika. Ten obraz zostanie obrócony zgodnie z wymaganiami widżetu miernik, aby wyświetlić wskazówkę miernika w dowolnym położeniu |

Na poniższym diagramie przedstawiono współrzędne xpos, YPos i XCOR, ycor:

![Diagram współrzędnych Y i X wskazówki](./media/guix/image8.png)

## <a name="gx_line_chart_info"></a>GX_LINE_CHART_INFO

### <a name="definition"></a>Definicja

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

| Elementy członkowskie | Opis |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_line_chart_min_val**          | Minimalna wartość danych, która jest używana do obliczania skalowania
| **gx_line_chart_max_val**          | Maksymalna wartość danych, która jest używana do obliczania skalowania |
| **gx_line_chart_data**             | Wskaźnik na tablicę wartości całkowitych. Są to wartości całkowite kreślone przez widżet wykres liniowy |
| **gx_line_ <side> _margin**          | Przesunięcie z okna wykresu jest powiązane z zewnętrznym obszarem renderowania wykresu. Oś wykresu i linia danych są zawsze kreślone w obrębie tej wewnętrznej granicy, co umożliwia aplikacji rysowanie etykiet i innych informacji wewnątrz okna wykresu, ale poza obszarem grafu znaków |
| **gx_line_chart_max_data_count**   | Liczba wartości danych, które mogą być obecne. Ten parametr służy do obliczania skali x lub interwału wykreślania punktów danych. |
| **gx_line_active_data_count**      | Liczba wartości danych, które faktycznie znajdują się w tablicy danych. Wykres liniowy może być skalowany w celu narysowania maksymalnie 100 wartości (na przykład), ale w każdej konkretnej aktualizacji może być rzeczywiście obecne. |
| **gx_line_axis_line_width**        | Szerokość linii używana do rysowania osi poziomej i pionowej |
| **gx_line_data_line_width**        | Szerokość wykreślonego wiersza danych |
| **gx_line_chart_axis_color**       | Identyfikator zasobu używany do rysowania linii osi |
| **gx_line_chart_line_color**       | Identyfikator zasobu używany do rysowania linii danych wykresu |

## <a name="gx_mouse_cursor_info"></a>GX_MOUSE_CURSOR_INFO 

### <a name="definition"></a>Definicja

```c
typedef struct GX_MOUSE_CURSOR_INFO_STRUCT
{
    GX_RESOURCE_ID             gx_mouse_cursor_image_id;
    GX_VALUE                   gx_mouse_cursor_hotspot_x;
    GX_VALUE                   gx_mouse_cursor_hotspot_y;
} GX_MOUSE_CURSOR_INFO;
```

| Elementy członkowskie | Opis |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_mouse_cursor_image_id**       | Identyfikator zasobu obrazu myszy |
| **gx_mouse_cursor_hotspot_x**      | Przesunięcie od lewej krawędzi obrazu myszy do hotspotu obrazu myszy. |
| **gx_mouse_cursor_hotspot_y**      | Przesunięcie od góry obrazu myszy do hotspotu obrazu myszy. |

## <a name="gx_pen_configuration"></a>GX_PEN_CONFIGURATION 

### <a name="definition"></a>Definicja

```c
typedef struct GX_PEN_CONFIGURATION_STRUCT
{
    GX_FIXED_VAL     gx_pen_configuration_min_drag_dist;
    UINT             gx_pen_configuration_max_pen_speed_ticks;
}GX_PEN_CONFIGURATION;
```

| Elementy członkowskie | Opis |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_pen_configuration_min_drag_dist**       | Minimalną odległość przeciągania na cykl czasomierza GUIX, aby wyzwolić zdarzenie szybkiego ruchu. Wywołaj GX_FIXED_VAL_MAKE, aby utworzyć stałą wartość typu danych |
| **gx_pen_configuration_max_pen_speed_ticks** | Maksymalna szybkość przeciągania w taktach czasomierza GUIX w celu wyzwalania zdarzenia szybkiego ruchu | 

## <a name="gx_pixelmap_slider_info"></a>GX_PIXELMAP_SLIDER_INFO 

### <a name="definition"></a>Definicja

```c
typedef struct GX_PIXELMAP_SLIDER_INFO_STRUCT
{
    GX_RESOURCE_ID gx_pixelmap_slider_info_lower_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_upper_background_pixelmap;
    GX_RESOURCE_ID gx_pixelmap_slider_info_needle_pixelmap;
} GX_PIXELMAP_SLIDER_INFO;
```

| Elementy członkowskie | Opis |
| ----------------------------------------------------- | ---------------------------------------- |
| **gx_pixelmap_slider_info_lower_background_pixelmap** | Identyfikator zasobu Pixelmap do wypełniania tła przed wskazówką. Jeśli nie ustawiono górnego Pixelmap w tle, jest on używany do wypełniania tła przed i po wskazówkę |
| **gx_pixelmap_slider_info_upper_background_pixelmap** | Identyfikator zasobu Pixelmap do wypełnienia tła po wskazówki |
| **gx_pixelmap_slider_info_needle_pixelmap**           | Identyfikator zasobu wskazówki Pixelmap |

## <a name="gx_progress_bar_info"></a>GX_PROGRESS_BAR_INFO 

### <a name="definition"></a>**Definicja**

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

| Elementy członkowskie | Opis |
| -------------------------------------------- | ------------------------------------------------ |
| **gx_progress_bar_info_min_val**             | Minimalna raportowana wartość |
| **gx_progress_bar_info_max_val**             | Maksymalna raportowana wartość |
| **gx_progress_bar_info_current_val**         | Bieżąca wartość |
| **gx_progress_bar_info_font_id**             | Identyfikator zasobu czcionki używany do rysowania opcjonalnej wartości tekstowej w widżecie pasek postępu.      |
| **gx_progress_bar_normal_text_color**        | Identyfikator zasobu koloru tekstu w normalnym stanie używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu |
| **gx_progress_bar_selected_text_color**      | Identyfikator zasobu koloru tekstu, gdy element widget uzyskuje fokus, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu |
| **gx_progress_bar_disabled_text_color**      | Identyfikator zasobu koloru tekstu, gdy GX_STYLE_ENABLED nie jest aktywny, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu |
| **gx_progress_bar_fill_pixelmap**            | Identyfikator zasobu Pixelmap do wypełnienia tła|

## <a name="gx_radial_progress_bar_info"></a>GX_RADIAL_PROGRESS_BAR_INFO

### <a name="definition"></a>Definicja

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

| Elementy członkowskie | Opis |
| ------------------------------------------------- | -------------------------------------------- |
| **gx_radial_progress_bar_info_xcenter**           | Położenie elementu widget w współrzędnej x |
| **gx_radial_progress_bar_info_ycenter**           | Położenie elementu widget w współrzędnym y  |
| **gx_radial_progress_bar_info_radius**            | Promień okręgu postępu |
| **gx_radial_progress_bar_info_current_val**       | Bieżąca wartość, ograniczona do zakresu [-360, 360], wskazuje różnicę kątową między pozycją zakotwiczenia a punktem końcowym górnego łuku. Wartość ujemna powoduje, że łuk ma być rysowany w kierunku w prawo, rozpoczynając od pozycji zakotwiczenia. Wartość dodatnia powoduje, że łuk ma być rysowany w kierunku przychodzącym w prawo, rozpoczynając od pozycji zakotwiczenia. Aplikacja musi skalować wskazane wartości rzeczywiste, aby przypisać wartość kątową do widżetu paska postępu. |
| **gx_radial_progress_bar_anchor_val**             | Kąt początkowy łuku górnego postępu. Wartość jest definiowana w zakresie liczby całkowitej z 0 stopni wskazujących prawy i 90 stopień wskazujący na pozycję prostą. |
| **gx_radial_progress_bar_font_id**                | Identyfikator zasobu czcionki używany do rysowania opcjonalnej wartości tekstowej w widżecie pasek postępu. |
| **gx_radial_progress_bar_normal_text_color**      | Identyfikator zasobu koloru tekstu w normalnym stanie używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu |
| **gx_radial_progress_bar_selected_text_color**    |Identyfikator zasobu koloru tekstu, gdy element widget uzyskuje fokus, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu |
| **gx_radial_progress_bar_disabled_text_color**    | Identyfikator zasobu koloru tekstu, gdy GX_STYLE_ENABLED nie jest aktywny, używany do definiowania opcjonalnego rysowania tekstu w widżecie pasek postępu |
| **gx_radial_progress_bar_normal_brush_width**     | Szerokość dolnego okręgu postępu |
| **gx_radial_progress_bar_selected_brush_width**   | Szerokość górnego łuku postępu, górny łuk może być węższy, taki sam jak lub większy niż dolny okrąg |
| **gx_radial_progress_bar_normal_brush_color**     | Identyfikator zasobu koloru do wypełnienia dolnego okręgu postępu |
| **gx_radial_progress_bar_selected_brush_color**   | Identyfikator zasobu koloru do wypełnienia łuku górnego postępu |

## <a name="gx_radial_slider_info"></a>GX_RADIAL_SLIDER_INFO 

### <a name="definition"></a>Definicja

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

| Elementy członkowskie | Opis |
| --------------------------------------------- | ------------------------------------------------ |
**gx_radial_slider_info_xcenter**               | Odległość od lewej krawędzi elementu widget suwaka do środka obrotu wskazówki kontrolki suwaka |
| **gx_radial_slider_info_ycenter**             | Odległość od góry elementu widget suwaka do środka obrotu wskazówki kontrolki suwaka |
| **gx_radial_slider_info_radius**              | Promień okręgu suwaka promieniowego |
| **gx_radial_slider_info_track_width**         | Szerokość kontrolki suwaka promieniowego |
| **gx_radial_slider_info_current_angle**       | Bieżący kąt suwaka |
| **gx_radial_slider_info_min_angle**           | Minimalny kąt suwaka |
| **gx_radial_slider_info_max_angle**           | Maksymalny kąt suwaka |
| **gx_radial_slider_info_angle_list**          | Lista wartości kątowych, definiuje kąty kotwicowe, jeśli jest ustawiona, kąt suwaka może być tylko jednym ze zdefiniowanych kątów zakotwiczenia. |
| **gx_radial_slider_info_list_count**          | Liczba kątów zakotwiczenia |
| **gx_radial_slider_info_background_pixelmap** | Identyfikator zasobu w tle Pixelmap |
| **gx_radial_slider_info_needle_pixelmap**     | Identyfikator zasobu wskazówki Pixelmap |

## <a name="gx_rectangle"></a>GX_RECTANGLE

### <a name="definition"></a>Definicja

```c
typedef struct GX_RECTANGLE_STRUCT
{
    GX_VALUE gx_rectangle_left;
    GX_VALUE gx_rectangle_top;
    GX_VALUE gx_rectangle_right;
    GX_VALUE gx_rectangle_bottom;
} GX_RECTANGLE;
```

| Elementy członkowskie | Opis |
| -------------------------------- | ------------------------|
| **gx_rectangle_left**            | Po lewej stronie prostokąta   |  
| **gx_rectangle_top**             | Góra prostokąta    | 
| **gx_rectangle_right**           | Z prawej strony prostokąta  |
| **gx_rectangle_bottom**          | Dolna część prostokąta |

## <a name="gx_rich_text_fonts"></a>GX_RICH_TEXT_FONTS 

### <a name="definition"></a>Definicja

```c
typedef struct GX_RICH_TEXT_FONTS_STRUCT
{
    GX_RESOURCE_ID             gx_rich_text_fonts_normal_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_italic_id;
    GX_RESOURCE_ID             gx_rich_text_fonts_bold_italic_id;
} GX_RICH_TEXT_FONTS;
```

| Elementy członkowskie | Opis |
| ---------------------------------- | ---------------------------------------------------------- |
| **gx_rich_text_fonts_normal_id**   | Identyfikator zasobu zwykłej czcionki tekstu |
| **gx_rich_text_fonts_bold_id**     | Identyfikator zasobu czcionki pogrubionej tekstu |
| **gx_rich_text_fonts_italic_id**   | Identyfikator zasobu czcionki tekstu kursywy |
| **gx_rich_text_fonts_bold_italic_id** | Identyfikator zasobu czcionki pogrubionej kursywy |

## <a name="gx_scroll_info"></a>GX_SCROLL_INFO 
### <a name="definition"></a>**Definicja**

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

| Elementy członkowskie | Opis |
| ----------------------- | ----------------------------- |
| **gx_scroll_value**     | Bieżąca pozycja przewijania       |
| **gx_scroll_minimum**   | Minimalna zgłoszona pozycja     |
| **gx_scroll_maximum**   | Maksymalna zgłoszona pozycja     |
| **gx_scroll_visible**   | Widoczny zakres okna nadrzędnego   |
| **gx_scroll_increment** | Minimalna wartość różnicowa ScrollBar |

## <a name="gx_scrollbar_appearance"></a>GX_SCROLLBAR_APPEARANCE 

### <a name="definition"></a>Definicja

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

| Elementy członkowskie | Opis |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_scroll_width**                      | Szerokość widżetu ScrollBar w pikselach |
| **gx_scroll_thumb_width**                | Szerokość przycisku przewijania, które slajdy na pasku przewijania (w pikselach). Ta wartość jest zwykle pewną liczbą pikseli mniejszą niż całkowita szerokość paska przewijania. |
| **gx_scroll_thumb_travel_min**           | Przesunięcie od końca paska przewijania do minimalnego punktu podróży przycisku przewijania. Tego limitu można użyć, aby zapobiec przeniesieniu przycisku przewijania na koniec paska przewijania. |
| **gx_scroll_thumb_travel_max**           | Przesunięcie od końca paska przewijania do maksymalnego punktu podróży przycisku przewijania. Tego limitu można użyć, aby zapobiec przeniesieniu przycisku przewijania na koniec paska przewijania. |
| **gx_scroll_thumb_border_style**         | Style obramowania przycisku przewijania |
| **gx_scroll_fill_pixelmap**              | Opcjonalny identyfikator Pixelmap. Jeśli ten identyfikator Pixelmap nie jest zerem, pasek przewijania używa tego Pixelmap do rysowania tła paska przewijania |
| **gx_scroll_thumb_pixelmap**             | Opcjonalny identyfikator Pixelmap. Jeśli ten identyfikator Pixelmap ma wartość różną od zera, przycisk przewijania ScrollBar używa tego Pixelmap do rysowania |
| **gx_scroll_up_pixelmap**                | Opcjonalny identyfikator Pixelmap. Jeśli ten identyfikator Pixelmap ma wartość różną od zera, pasek przewijania używa tego identyfikatora Pixelmap do rysowania przycisku przewijania w lewo/w górę |
| **gx_scroll_down_pixelmap**              | Opcjonalny identyfikator Pixelmap. Jeśli ten identyfikator Pixelmap ma wartość różną od zera, pasek przewijania używa tego identyfikatora Pixelmap do rysowania przycisku końca w prawym/dół paska przewijania |
| **gx_scroll_thumb_color**                | Identyfikator zasobu koloru używany do wypełnienia przycisku przewijania |
| **gx_scroll_thumb_border_color**         | Identyfikator zasobu koloru używany do rysowania obramowania przycisku kciuka | 
| **gx_scroll_button_color**               | Identyfikator zasobu koloru używany do wypełniania przycisków końca paska przewijania |

## <a name="gx_slider_info"></a>GX_SLIDER_INFO

### <a name="definition"></a>Definicja

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

| Elementy członkowskie | Opis |
| --------------------------------------- | ------------------------------------------------------ |
| **gx_slider_info_min_val**              | Minimalna raportowana wartość |
| **gx_slider_info_max_val**              | Maksymalna raportowana wartość |
| **gx_slider_info_current_value**        | Bieżąca wartość |
| **gx_slider_info_min_travel**           | Limit podróży wskazówki |
| **gx_slider_info_max_travel**           | Limit podróży wskazówki |
| **gx_slider_info_needle_width**         | Szerokość wskazówki w pikselach |
| **gx_slider_info_needle_height**        | Wysokość wskazówki (w pikselach) |
|**gx_slider_info_needle_inset**          | Pozycja rysowania wskazówki. Jeśli ustawiono GX_STYLE_SLIDER_VERTICAL, służy do określania przesunięcia od pozycji początku rysowania wskazówki do lewego suwaka. Else, używany do określania przesunięcia od pozycji początkowej rysowania wskazówki do górnej krawędzi suwaka. |
| **gx_slider_info_needle_hotspot_offset** | Wskazówki hotpot_offset, używane do określania przesunięcia od pozycji początkowej rysowania wskazówki do punktu aktywnego suwaka. |

## <a name="gx_sprite_frame"></a>GX_SPRITE_FRAME

### <a name="definition"></a>Definicja

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

| Elementy członkowskie | Opis |
| ---------------------------------------- | ----------------------------------------------------- |
| **gx_sprite_frame_pixelmap**             | Identyfikator zasobu Pixelmap, który ma być wyświetlany dla tej ramki. Identyfikator może być równy 0. |
| **gx_sprite_frame_x_offset**             | Przesunięcie od widgetu Sprite po lewej stronie, aby wyświetlić Pixelmap |
| **gx_sprite_frame_y_offset**             | Przesunięcie od elementu widget Sprite góry, aby wyświetlić Pixelmap |
| **gx_sprite_frame_delay**                | Wartość opóźnienia w taktach czasomierza GUIX, po wyświetleniu tej ramki przed przejściem do następnej ramki Sprite |
| **gx_sprite_frame_background_operation** | Zdefiniuj sposób wymazywania tła. Możliwe wartości dla tego pola to:<br />GX_SPRITE_BACKGROUND_NO_ACTION: brak wypełniania między ramkami<br />GX_SPRITE_BACKGROUND_SOLID_FILL: ponowne rysowanie tła Sprite<br />GX_SPRITE_BACKGROUND_RESTORE: Przywróć poprzedni Pixelmap |
| **gx_sprite_frame_alpha**                | Wartość alfa, która ma zostać dodana do wyświetlanego Pixelmap. Wartość 255 określa, że nie należy nałożyć dodatkowej wartości alfa. Jeśli Pixelmap zawiera kanał alfa, ten kanał alfa zostanie dodany do ramki alfa wartości. |
