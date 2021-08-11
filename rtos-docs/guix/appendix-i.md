---
title: Dodatek I — struktury informacyjne GUIX
description: Dowiedz się więcej o strukturach informacyjnych GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8730dbfc49ed51716f32c118a25ebffc907b19a54d98d83ede4155f87fbecb7b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784170"
---
# <a name="appendix-i---guix-information-structures"></a>Dodatek I — struktury informacyjne GUIX 

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
| **gx_bidi_text_info_font**               | Czcionka używana do wyświetlania tekstu, ustaw ją na wartość GX_NULL jeśli podział wiersza nie jest wymagany |
| **gx_bidi_text_info_display_width**      | Dostępna szerokość do wyświetlania, ustaw ją na -1, jeśli podział wiersza nie jest wymagany |

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
| **gx_bidi_resolved_text_info_text**             | Wskaźnik do tablicy tekstu z ponowną kolejnością ofert |
| **gx_bidi_resolved_text_info_total_lines**      | Łączna liczba wierszy rozpoznanego tekstu oferty dla jednego akapitu |
| **gx_bidi_resolved_text_info_next**             | Rozwiązano problem z informacjami tekstowym dla następnego akapitu |

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
| **gx_circular_gauge_info_animation_steps**       | Łączna liczba kroków, przez które przechodzi igła podczas przechodzenia z bieżącego kąta igłą do nowo przypisanego kąta igły |
| **gx_circular_gauge_info_animation_delay**       | Liczba takt zegara GUIX w celu opóźnienia między krokami animacji |
| **gx_circular_gauge_info_needle_xpos**           | Odległość od lewej strony widżetu miernika do środka obrotu wskaźnika |
| **gx_circular_gauge_info_needle_ypos**           | Odległość od góry widżetu miernika do środka obrotu wskaźnika |
| **gx_circular_gauge_info_needle_xcor**           | Odległość od lewej strony obrazu z iniekcją do środka obrotu wskaźnika |
| **gx_circular_gauge_info_needle_ycor**           | Odległość od góry obrazu z iniekcją do środka obrotu wskaźnika |
| **gx_circular_gauge_info_needle_pixelmap**       | Identyfikator zasobu mapy pikseli, która zostanie użyta do narysowania wskaźnika. Ten obraz zostanie obrócony zgodnie z potrzebami przez widżet miernika, aby wyświetlić wskaźnik miernika w dowolnej pozycji |

Na poniższym diagramie przedstawiono współrzędne xpos, ypos i xcor, ycor:

![Diagram współrzędnych Y i X](./media/guix/image8.png)

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
| **gx_line_chart_max_val**          | Maksymalna wartość danych używana do obliczania skalowania |
| **gx_line_chart_data**             | Wskaźnik do tablicy wartości całkowitych. Są to wartości całkowite wykreślone przez widżet wykresu liniowego |
| **gx_line_ <side> _margin**          | Przesunięcie od zewnętrznego okna wykresu powiązane z rzeczywistym obszarem renderowania wykresu. Oś wykresu i linia danych są zawsze wykreślone w obrębie tej wewnętrznej granicy, co umożliwia aplikacji rysowanie etykiet i innych informacji wewnątrz okna wykresu, ale poza obszarem wykresu char |
| **gx_line_chart_max_data_count**   | Liczba wartości danych, które mogą być obecne. Ten parametr służy do obliczania skalowania osi x lub interwału wykreślania punktów danych. |
| **gx_line_active_data_count**      | Liczba wartości danych, które faktycznie są obecne w tablicy danych. Wykres liniowy można skalować w celu narysowania maksymalnie 100 wartości (na przykład), ale w przypadku każdej konkretnej aktualizacji mniejsza liczba wartości danych może być faktycznie obecna. |
| **gx_line_axis_line_width**        | Szerokość linii używanej do rysowania osi poziomej i pionowej |
| **gx_line_data_line_width**        | Szerokość wykreślanych linii danych |
| **gx_line_chart_axis_color**       | Identyfikator zasobu koloru używanego do rysowania linii osi |
| **gx_line_chart_line_color**       | Identyfikator zasobu koloru używanego do rysowania linii danych wykresu |

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
| **gx_mouse_cursor_hotspot_x**      | Przesunięcie od lewej strony obrazu myszy do hotspotu obrazu myszy |
| **gx_mouse_cursor_hotspot_y**      | Przesunięcie od góry obrazu myszy do hotspotu obrazu myszy |

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
| **gx_pen_configuration_min_drag_dist**       | Minimalna odległość przeciągania na znacznik czasomierza GUIX w celu wyzwolenia zdarzenia MIGOTANIA. Wywołaj GX_FIXED_VAL_MAKE, aby wprowadzić stałą wartość typu danych punktu |
| **gx_pen_configuration_max_pen_speed_ticks** | Maksymalna szybkość przeciągania w taktach czasomierza GUIX w celu wyzwolenia zdarzenia MIGOTANIA | 

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
| **gx_pixelmap_slider_info_lower_background_pixelmap** | Identyfikator zasobu mapy pikseli do wypełnienia tła przed igłą. Jeśli górna mapa pikseli tła nie jest ustawiona, służy do wypełniania tła przed i po igieł |
| **gx_pixelmap_slider_info_upper_background_pixelmap** | Identyfikator zasobu mapy pikseli do wypełnienia tła po igłę |
| **gx_pixelmap_slider_info_needle_pixelmap**           | Identyfikator zasobu mapy pikseli nagieł |

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
| **gx_progress_bar_info_min_val**             | Minimalna zgłoszona wartość |
| **gx_progress_bar_info_max_val**             | Maksymalna zgłoszona wartość |
| **gx_progress_bar_info_current_val**         | Bieżąca wartość |
| **gx_progress_bar_info_font_id**             | Identyfikator zasobu czcionki używany do rysowania opcjonalnej wartości tekstowej w widżecie paska postępu      |
| **gx_progress_bar_normal_text_color**        | Identyfikator zasobu koloru tekstu w stanie normalnym używany do definiowania opcjonalnego rysowania tekstu w widżecie paska postępu |
| **gx_progress_bar_selected_text_color**      | Identyfikator zasobu koloru tekstu w przypadku uzyskania fokusu widżetu, używany do definiowania opcjonalnego rysowania tekstu w widżecie paska postępu |
| **gx_progress_bar_disabled_text_color**      | Identyfikator zasobu koloru tekstu, gdy GX_STYLE_ENABLED nie jest aktywny, używany do definiowania opcjonalnego rysowania tekstu w widżecie paska postępu |
| **gx_progress_bar_fill_pixelmap**            | Identyfikator zasobu mapy pikseli do wypełnienia w tle|

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
| **gx_radial_progress_bar_info_xcenter**           | Pozycja widżetu na współrzędnych x |
| **gx_radial_progress_bar_info_ycenter**           | Pozycja widżetu we współrzędnej y  |
| **gx_radial_progress_bar_info_radius**            | Promień okręgu postępu |
| **gx_radial_progress_bar_info_current_val**       | Bieżąca wartość ograniczona do zakresu [-360, 360] wskazuje różnicę kątową między położeniem kotwicy a punktem końcowy górnego łuku. Wartość ujemna powoduje rysowanie łuku w kierunku zgodnym z ruchem wskazówek zegara, zaczynając od pozycji kotwicy. Wartość dodatnia powoduje rysowanie łuku w kierunku przeciwnym do wskazówek zegara, zaczynając od pozycji kotwicy. Aplikacja musi skalować wskazywaną wartość rzeczywistego wyrazu, aby przypisać wartość angular do widżetu paska postępu |
| **gx_radial_progress_bar_anchor_val**             | Kąt początkowy górnego łuku postępu. Wartość jest definiowana jako stopień liczby całkowitej z 0 stopniem wskazującym na prawo i o 90 stopni wskazującym prostą pozycję w górę. |
| **gx_radial_progress_bar_font_id**                | Identyfikator zasobu czcionki używanej do rysowania opcjonalnej wartości tekstowej w widżecie paska postępu |
| **gx_radial_progress_bar_normal_text_color**      | Identyfikator zasobu koloru tekstu w stanie normalnym używany do definiowania opcjonalnego rysowania tekstu w widżecie paska postępu |
| **gx_radial_progress_bar_selected_text_color**    |Identyfikator zasobu koloru tekstu w przypadku uzyskania fokusu widżetu, używany do definiowania opcjonalnego rysowania tekstu w widżecie paska postępu |
| **gx_radial_progress_bar_disabled_text_color**    | Identyfikator zasobu koloru tekstu, gdy GX_STYLE_ENABLED nie jest aktywny, używany do definiowania opcjonalnego rysowania tekstu w widżecie paska postępu |
| **gx_radial_progress_bar_normal_brush_width**     | Szerokość dolnego okręgu postępu |
| **gx_radial_progress_bar_selected_brush_width**   | Szerokość górnego łuku postępu, górny arc może być węższy, taki sam jak lub szerszy niż dolny okrąg |
| **gx_radial_progress_bar_normal_brush_color**     | Identyfikator zasobu koloru do wypełnienia niższego okręgu postępu |
| **gx_radial_progress_bar_selected_brush_color**   | Identyfikator zasobu koloru do wypełnienia górnego łuku postępu |

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
**gx_radial_slider_info_xcenter**               | Odległość od lewej strony widżetu suwaka do środka obrotu suwaka |
| **gx_radial_slider_info_ycenter**             | Odległość od góry widżetu suwaka do środka obrotu suwaka |
| **gx_radial_slider_info_radius**              | Promień okręgu suwaka promieniowego |
| **gx_radial_slider_info_track_width**         | Szerokość ścieżki suwaka promieniowego |
| **gx_radial_slider_info_current_angle**       | Bieżący kąt suwaka |
| **gx_radial_slider_info_min_angle**           | Minimalny kąt suwaka |
| **gx_radial_slider_info_max_angle**           | Maksymalny kąt suwaka |
| **gx_radial_slider_info_angle_list**          | Lista wartości kąta, definiuje kąty zakotwiczenia, jeśli jest ustawiona, kąt suwaka może być tylko jednym ze zdefiniowanych kątów zakotwiczenia |
| **gx_radial_slider_info_list_count**          | Liczba kątów zakotwiczenia |
| **gx_radial_slider_info_background_pixelmap** | Identyfikator zasobu mapy pikseli tła |
| **gx_radial_slider_info_needle_pixelmap**     | Identyfikator zasobu mapy pikseli napiwki |

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
| **gx_rectangle_top**             | Górna część prostokąta    | 
| **gx_rectangle_right**           | Prawą część prostokąta  |
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
| **gx_rich_text_fonts_normal_id**   | Identyfikator zasobu zwykłej czcionki tekstowej |
| **gx_rich_text_fonts_bold_id**     | Identyfikator zasobu z pogrubioną czcionką tekstową |
| **gx_rich_text_fonts_italic_id**   | Identyfikator zasobu czcionki tekstu kursywą |
| **gx_rich_text_fonts_bold_italic_id** | Identyfikator zasobu z pogrubioną czcionką tekstową kursywą |

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
| **gx_scroll_visible**   | Zakres widocznych okien nadrzędnych   |
| **gx_scroll_increment** | Minimalna wartość różnicowa paska przewijania |

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
| **gx_scroll_width**                      | Szerokość widżetu paska przewijania w pikselach |
| **gx_scroll_thumb_width**                | Szerokość przycisku miniatury wysuwa się na pasku przewijania w pikselach. Ta wartość jest zwykle o kilka pikseli mniejsza niż całkowita szerokość paska przewijania |
| **gx_scroll_thumb_travel_min**           | Przesunięcie od końca paska przewijania do minimalnego punktu podróży przycisku miniatury. Tego limitu można użyć, aby uniemożliwić przesuwanie przycisku kciuka do samego końca paska przewijania |
| **gx_scroll_thumb_travel_max**           | Przesunięcie od końca paska przewijania do maksymalnego punktu podróży przycisku miniatury. Tego limitu można użyć, aby uniemożliwić przesuwanie przycisku kciuka do samego końca paska przewijania |
| **gx_scroll_thumb_border_style**         | Style obramowania przycisku kciuka |
| **gx_scroll_fill_pixelmap**              | Opcjonalny identyfikator mapy pikseli. Jeśli ten identyfikator mapy pikseli nie jest zerowy, pasek przewijania używa tej mapy pikseli do narysowania tła paska przewijania |
| **gx_scroll_thumb_pixelmap**             | Opcjonalny identyfikator mapy pikseli. Jeśli ten identyfikator mapy pikseli nie ma wartości zero, przycisk przewijania na pasku przewijania używa tej mapy pikseli do narysowania samego siebie |
| **gx_scroll_up_pixelmap**                | Opcjonalny identyfikator mapy pikseli. Jeśli ten identyfikator mapy pikseli nie jest zerowy, pasek przewijania używa tego identyfikatora mapy pikseli do narysowania przycisku paska przewijania w lewo/w górę |
| **gx_scroll_down_pixelmap**              | Opcjonalny identyfikator mapy pikseli. Jeśli ten identyfikator mapy pikseli nie jest zerowy, pasek przewijania używa tego identyfikatora mapy pikseli do narysowania przycisku paska przewijania w prawo/w dół |
| **gx_scroll_thumb_color**                | Identyfikator zasobu koloru używany do wypełniania przycisku kciuka |
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
| **gx_slider_info_min_val**              | Minimalna zgłoszona wartość |
| **gx_slider_info_max_val**              | Maksymalna zgłoszona wartość |
| **gx_slider_info_current_value**        | Bieżąca wartość |
| **gx_slider_info_min_travel**           | Limit podróży za pomocą szprych |
| **gx_slider_info_max_travel**           | Limit podróży za pomocą szprych |
| **gx_slider_info_needle_width**         | Szerokość szprych w pikselach |
| **gx_slider_info_needle_height**        | Wysokość napiwka w pikselach |
|**gx_slider_info_needle_inset**          | Położenie rysowania za pomocą szprych. Jeśli GX_STYLE_SLIDER_VERTICAL ustawiono wartość , służy do określania przesunięcia od pozycji rozpoczęcia rysowania naiwną do suwaka w lewo. W innym przypadku służy do określania przesunięcia od pozycji startowej rysowania naiwnie do góry suwaka. |
| **gx_slider_info_needle_hotspot_offset** | Czas hotpot_offset, używany do określania przesunięcia od pozycji rozpoczęcia rysowania igłą do hotspotu suwaka. |

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
| **gx_sprite_frame_pixelmap**             | Identyfikator zasobu mapy pikseli, która ma być wyświetlana dla tej ramki. Identyfikator może mieć 0. |
| **gx_sprite_frame_x_offset**             | Przesunięcie od widżetu sprite w lewo w celu wyświetlenia mapy pikseli |
| **gx_sprite_frame_y_offset**             | Przesunięcie od góry widżetu sprite w celu wyświetlenia mapy pikseli |
| **gx_sprite_frame_delay**                | Wartość opóźnienia w taktach czasomierza GUIX po wyświetleniu tej ramki przed przejściem do następnej ramki sprite |
| **gx_sprite_frame_background_operation** | Zdefiniuj sposób wymazywania tła. Możliwe wartości dla tego pola to:<br />GX_SPRITE_BACKGROUND_NO_ACTION: Brak wypełnienia między ramkami<br />GX_SPRITE_BACKGROUND_SOLID_FILL: Ponowne rysowanie tła sprite<br />GX_SPRITE_BACKGROUND_RESTORE: Przywracanie poprzedniej mapy pikseli |
| **gx_sprite_frame_alpha**                | Wartość alfa, która ma zostać dodana do wyświetlanej mapy pikseli. Wartość 255 określa, że nie należy nakładać żadnej dodatkowej wartości alfa. Jeśli mapa pikseli zawiera kanał alfa, ten kanał alfa zostanie dodany do wartości alfa ramki. |
