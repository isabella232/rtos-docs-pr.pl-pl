---
title: Rozdział 5 — sterowniki wyświetlania GUIX
description: Sterowniki wyświetlania GUIX definiują interfejs oprogramowania między abstrakcyjną kanwą rysowania a fizycznym sprzętem do wyświetlania.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 804187ce8562e274205e97448da77d29f99016072c137cb3c4f1f42dac58c432
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788545"
---
# <a name="chapter-5---guix-display-drivers"></a>Rozdział 5 — sterowniki wyświetlania GUIX

Sterowniki wyświetlania GUIX definiują interfejs oprogramowania między abstrakcyjną kanwą rysowania a fizycznym sprzętem do wyświetlania. Sterownik wyświetlania GUIX implementuje funkcje rysowania najniższego poziomu, które faktycznie zmieniają informacje o kolorze pikseli w pamięci kanwy i przesyłują pamięć kanwy do fizycznego bufora ramek wyświetlania w systemach z podwójnym buforem.

Sterowniki wyświetlania GUIX są definiowane przez strukturę zawierającą parametry wyświetlania fizycznego oraz zestaw wskaźników funkcji do funkcji sterowników niskiego poziomu. Dzięki tym wskaźnikom funkcji pośrednich abstrakcyjne funkcje kanwy i rysowania widżetów są całkowicie niezależne od szczegółów sprzętu.

GuiX zapewnia kompletny, w pełni funkcjonalny, domyślny zestaw funkcji rysowania dla każdego obsługiwanego formatu kolorów i głębokości kolorów. Podczas implementowania sterownika wyświetlania bez możliwości przyspieszenia sprzętowego lub innych kwestii specyficznych dla sprzętu te domyślne funkcje rysowania są zwykle wystarczające dla ostatecznej implementacji sterownika. W przypadku tych najprostszych sterowników jedyną funkcją, która zwykle musi być zaimplementowana w oprogramowaniu sterowników, jest funkcja konfigurowania urządzenia sprzętowego. Często wiąże się to z inicjowaniem różnych rejestrów sprzętu w celu zdefiniowania zegara wyświetlania , wymiarów wyświetlania itp. W przypadku wszystkich innych funkcji implementacja sterownika po prostu inicjuje wskaźniki GX_DISPLAY do domyślnych implementacji funkcji dla żądanej głębokości i formatu koloru.

Podczas implementowania niestandardowego sterownika wyświetlania najlepszym rozwiązaniem jest najpierw zainicjowanie wskaźników funkcji rysowania sterowników wyświetlania z domyślną implementacją oprogramowania dla głębokości kolorów, którą chcesz obsługiwać, a następnie zastąp te wskaźniki funkcji tam, gdzie jest to wymagane, aby wywołać implementacje funkcji niestandardowych (jeśli istnieje). W tym celu dostępna jest domyślna funkcja konfiguracji dla każdego obsługiwanego formatu i głębokości kolorów. Jeśli na przykład piszesz 16-bitowy sterownik wyświetlania RGB w formacie 5:6:5, pierwszą rzeczą, jaką zwykle robi sterownik niestandardowy, jest wywołanie ogólnej procedury konfiguracji dla tej głębokości kolorów:

UINT my_custom_565_display_driver(GX_DISPLAY *display)

```c
{
      
      // perform standard function pointer setup
      
      _gx_display_driver_565rgb_setup(display, GX_NULL,
      
             my_buffertoggle);

}
```

Parametr my_buffer_toggle powyżej jest wskaźnikiem do funkcji przełączania buforu sterownika wyświetlania (która może być GX_NULL, jeśli sterownik jest buforowany pojedynczo i rysowany bezpośrednio do buforu ramek sprzętowych).

Jeśli piszesz niestandardowy sterownik wyświetlania, musisz dołączyć plik nagłówka gx_display.h do niestandardowego źródła sterownika, który jest plikiem nagłówka użytku wewnętrznego niedostępnym dla oprogramowania na poziomie aplikacji.

Funkcje rysowania na poziomie wyświetlania GUIX odbierają jako dane wejściowe wskaźnik **GX_DRAW_CONTEXT** struktury. Struktura **GX_DRAW_CONTEXT** definiuje współrzędne przycinania dla bieżącej operacji rysowania wraz z używanym pędzlem i kolorami. Każda funkcja rysowania otrzymuje jako dane wejściowe dodatkowe parametry specyficzne dla wymagań funkcji.

Podpis punktu **wejścia GX_DISPLAY** sterowników jest zdefiniowany jako

```c
UINT <device>_graphics_driver_<format>(GX_DISPLAY *diplay)
```

Chociaż nazwa tej funkcji jest całkowicie do implementatora, konwencją sterowników dostarczanych z graficznym interfejsem użytkownika jest użycie nazwy urządzenia specyficznej dla sprzętu w polu i formacie kolorów dla pola <device> <format> powyżej.

Ta funkcja musi zainicjować strukturę **GX_DISPLAY** danych wejściowych i wykonać wymaganą konfigurację sprzętu. Struktura **GX_DISPLAY** zawiera następujące pola.

| &nbsp; |
| --- | --- |
| ULONG gx_display_id <br/> Jest to pole do użycia przez aplikację w przypadkach, gdy tworzone jest więcej niż jedno wystąpienie określonego sterownika. |
| CHAR *gx_display_name <br/> Opcjonalna nazwa używana do identyfikowania sterownika. |
| GX_DISPLAY *gx_display_created_next <br/> To pole jest inicjowane przez graficzny interfejs użytkownika i służy do tworzenia i obsługi listy wszystkich wystąpień GX_DISPLAY. |
| GX_DISPLAY *gx_display_created_previous <br/> To pole jest inicjowane przez graficzny interfejs użytkownika i służy do tworzenia i obsługi listy wszystkich wystąpień GX_DISPLAY. |
| GX_VALUE gx_display_color_format <br/> To pole powinno odzwierciedlać format danych graficznych obsługiwany przez ten sterownik. Typy formatów kolorów są definiowane w gx_api.h. |
| GX_VALUE gx_display_width <br/> To pole powinno zostać zainicjowane w celu przechowywania fizycznej szerokości ekranu w pikselach. |
| GX_VALUE gx_display_height <br/> To pole powinno zostać zainicjowane w celu przechowywania fizycznej wysokości ekranu w pikselach. |
| GX_COLOR *gx_display_color_table <br/> Jest to wskaźnik do tabeli używanej do konwertowania wartości identyfikatorów kolorów na wartości specyficzne dla formatu kolorów. |
| GX_PIXELMAP *gx_display_pixelmap_table <br/> Jest to wskaźnik do tabeli aktywnej mapy pikseli dla tego ekranu. |
| GX_FONT *gx_display_font_table <br/> Jest to wskaźnik do aktywnej tabeli czcionek dla tego wyświetlania. |
| GX_COLOR *gx_display_palette <br/> W przypadku sterowników trybu palety jest to wskaźnik do aktywnej palety kolorów. W przypadku sterowników, które nie korzystają z palety kolorów, ten wskaźnik jest GX_NULL. |
| UINT gx_display_pixelmap_table_size <br/> Liczba wpisów w tabeli aktywnej mapy pikseli. |
| UINT gx_display_font_table_size <br/> Liczba wpisów w aktywnej tabeli czcionek. |
| UINT gx_display_palette_size <br/> Liczba wpisów w palecie kolorów (jeśli są dostępne). |
| ULONG gx_display_handle <br/> Unikatowy identyfikator lub *dojście*, które określa wyświetlanie.
| UINT gx_display_driver_ready <br/> To pole jest służące do sygnalizowania graficznego interfejsu użytkownika, gdy sterownik jest gotowy do działania. W niektórych przypadkach sterownik może wymagać kilku poziomów inicjowania i konfiguracji, w którym guix nie może próbować korzystać ze sterownika. Ta flaga powinna być ustawiona na 1, gdy sterownik jest gotowy do obsługi żądań rysowania. |
| VOID *gx_display_driver_data <br/> To pole jest do użycia przez implementację sterownika. Jeśli sterownik musi utworzyć dodatkowe informacje, które nie są dostępne w strukturze GX_DISPLAY, powinien przydzielić miejsce i wskazać te dodatkowe dane przy użyciu tego pola struktury. Przykładem dodatkowych danych specyficznych dla sterownika może być kanał DMA używany przez sterownik lub kanał SPI, z którym jest połączony bufor ramki wyświetlania. |
| VOID (*gx_display_driver_drawing_initiate)(GX_DISPLAY_STRUCT *display, struct GX_CANVAS_STRUCT *canvas) <br/> Jest to wskaźnik funkcji, który, jeśli nie ma wartości NULL, jest wywoływany przez gx_canvas_drawing_initiate funkcji. W przypadku sterowników wyświetlania, które korzystają z akceleratora grafiki lub listy ekranów sprzętowych, ta funkcja może służyć do rozpoczęcia nowej listy ekranów. Ten wskaźnik funkcji może mieć wartość NULL. |
| VOID (*gx_display_driver_palette_set)(GX_DISPLAY_STRUCT *display, GX_COLOR *palette, INT count) <br/> Jest to wskaźnik do funkcji w celu zainstalowania palety kolorów. Ta funkcja ma wartość NULL, chyba że sterownik działa w trybie palety (nazywanym również tabelą wyszukiwania kolorów lub trybem CLUT). |
| VOID (*gx_display_driver_simple_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> Jest to wskaźnik do funkcji implementowania ogólnego rysowania linii, bez anty aliasów. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_simple_wide_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> Jest to wskaźnik do funkcji implementowania ogólnego rysowania szerokiej linii, bez anty aliasów. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_anti_aliased_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> Jest to wskaźnik do funkcji w celu zaimplementowania ogólnego rysowania linii o anty aliasach. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_anti_aliased_wide_line_draw)(GX_DRAW_CONTECT *context, INT x1, INTy1, INT x2, INT y2) <br/> Jest to wskaźnik do funkcji w celu zaimplementowania ogólnego rysowania szerokiej linii z anty aliasami. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_horizonal_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y) <br/> Jest to wskaźnik do funkcji w celu zaimplementowania specjalnego przypadku rysowania linii poziomej. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_horizonal_pixelmap_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y, GX_PIXELMAP *map) <br/> Jest to wskaźnik do funkcji w celu zaimplementowania rysowania pojedynczego wiersza mapy pikseli. Ta funkcja jest używana wewnętrznie do wypełniania kształtów za pomocą wzorca. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_vertical_line_draw)(GX_DRAW_CONTECT *context, INT y1, INT y2, INT x) <br/> Jest to wskaźnik do funkcji w celu zaimplementowania specjalnego przypadku rysowania linii poziomej. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_horizonal_pattern_line_draw)(GX_DRAW_CONTECT *context, INT x1, INT x2, INT y) <br/> Jest to wskaźnik do funkcji w celu zaimplementowania poziomego rysowania linii wzorca. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_vertical_pattern_line_draw)(GX_DRAW_CONTECT *context, INT y1, INT y2, INT x) <br/> Jest to wskaźnik do funkcji implementowania pionowego rysowania linii wzorca. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_canvas_copy)(struktura GX_CANVAS_STRUCT *source, struct GX_CANVAS_STRUCT *dest) <br/> Jest to wskaźnik do funkcji do kopiowania danych kanwy z jednej kanwy do innej. Nieprawidłowy prostokąt kanwy źródłowej służy do definiowania obszaru kopiowania. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_canvas_blend)(struct GX_CANVAS_STRUCT *source, struct GX_CANVAS_STRUCT *dest) <br/> Jest to wskaźnik do funkcji do danych kanwy alfa-blend z kanwy źródłowej z istniejącymi danymi na kanwie docelowej. Nieprawidłowy prostokąt kanwy źródłowej służy do definiowania obszaru mieszania. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_pixelmap_blend)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp, GX_UBYTE alpha) <br/> Jest to wskaźnik do funkcji w celu zmieszania mapy pikseli na kanwie tła zdefiniowanej przez kontekst rysowania. Dostarczona wartość alfa może być dodatkiem do kanału alfa zawartego w danych mapy pikseli. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_pixelmap_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> Jest to wskaźnik do funkcji w celu narysowania mapy pikseli na kanwie zdefiniowanej przez kontekst rysowania. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_jpeg_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> Jest to wskaźnik do funkcji, która dekoduje obraz jpg i renderuje go bezpośrednio na kanwie. Ta funkcja jest dostępna tylko wtedy, GX_SOFTWARE_DECODER_SUPPORT jest zdefiniowana. Ten wskaźnik funkcji ma wartość NULL. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_png_draw)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp) <br/> Jest to wskaźnik do funkcji, która dekoduje obraz PNG i renderuje go bezpośrednio na kanwie. Ta funkcja jest dostępna tylko wtedy, GX_SOFTWARE_DECODER_SUPPORT jest zdefiniowana. Ten wskaźnik funkcji ma wartość NULL. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_pixelmap_rotate)(GX_DRAW_CONTEXT *context, INT xpos, INT ypos, GX_PIXELMAP *pmp INT angle, INT rot_cx, INT rot_cy) <br/> Jest to wskaźnik do funkcji w celu obracania mapy pixelemap i renderowania wyniku bezpośrednio na kanwie. Ta funkcja jest wywoływana przez interfejs API gx_canvas_pixelmap_rotate implementacje tej funkcji są udostępniane dla każdego obsługiwanego formatu kolorów i głębokości kolorów. |
| VOID *gx_display_driver_pixel_write)(GX_DRAW_CONTEXT *context, INT x, INT y, GX_COLOR color) <br/> Jest to wskaźnik do funkcji, która zapisuje jeden piksel w pamięci kanwy. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. <br/>
| VOID *gx_display_driver_block_move)(GX_DRAW_CONTEXT *context,GX_RECTANGLE *block, INT xshift, INT yshift) <br/> Jest to wskaźnik do funkcji służącej do przenoszenia lub przesuwania bloku pikseli na kanwie. Ta funkcja jest używana głównie do szybkiego przewijania zawartości okna. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_pixel_blend)(GX_DRAW_CONTEXT *context, INT x, INT y, GX_COLOR color, GX_UBYTE alpha) <br/> Ta funkcja służy do mieszania wartości koloru przychodzących pikseli z istniejącą wartością koloru w pamięci kanwy na pozycji x,y. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| GX_COLOR (*gx_display_driver_native_color_get)(GX_COLOR rawcolor) <br/> Ta funkcja konwertuje kolor z 32-bitowego formatu kolorów A:R:G:B używanego wewnętrznie przez guix na natywny format kolorów kanwy i wyświetlania. W przypadku sterowników wyświetlania działających na niższych głębokościach kolorów oczekiwana jest utrata informacji o kolorze. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| USHORT (*gx_display_driver_row_pitch_get)(szerokość USHORT) <br/> Zwraca liczbę bajtów lub krok jednego wiersza danych graficznych przy żądanej szerokości kanwy. Ta funkcja służy do obliczania rozmiaru obszaru pamięci potrzebnego do utworzenia kanwy. Wysokość i szerokość wiersza nie zawsze są takie same ze względu na ograniczenia wyrównania linii skanowania sprzętu. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_buffer_toggle)(struktura GX_CANVAS_STRUCT *canvas, GX_RECTANGLE *dirty_area) <br/> Jest to wskaźnik do funkcji do przełączania się między buforami ramek roboczych i widocznych dla systemów pamięci z podwójnym buforem. Ta funkcja musi najpierw poinstruować sprzęt, aby rozpocząć korzystanie z nowego buforu ramek, a następnie skopiować zmodyfikowaną część nowego widocznego buforu do buforu towarzyszącego, aby zapewnić, że dwa bufory pozostają w pamięci. | 
| VOID (*gx_display_driver_polygon_draw)(GX_DRAW_CONTEXT *context, INT num_points, GX_POINT *vertices <br/> Wskaźnik do funkcji w celu narysowania wielokąta. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_polygon_fill)(GX_DRAW_CONTEXT *context, INT num_points, GX_POINT *vertices <br/> Wskaźnik do funkcji w celu narysowania wypełnionego wielokąta. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_circle_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> Wskaźnik do funkcji w celu narysowania okręgu. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_anti_aliased_circle_draw) (GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> Wskaźnik do funkcji, aby narysować anty aliasowany okrąg. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_wide_circle_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> Wskaźnik do funkcji w celu narysowania okręgu z szerokim konturem. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_wide_anti_aliased_circle_draw) (GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> Wskaźnik do funkcji, aby narysować anty aliasowany okrąg z szerokim konturem. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_circle_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r) <br/> Wskaźnik do funkcji w celu narysowania wypełnionego okręgu. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Wskaźnik do funkcji w celu narysowania łuku. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_anti_aliased_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INTend_angle) <br/> Wskaźnik do funkcji w celu narysowania łuku o anty aliasach. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_wide_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Wskaźnik do funkcji w celu narysowania łuku z szerokim konturem. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_anti_aliased_wide_arc_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INTend_angle) <br/> Wskaźnik do funkcji w celu narysowania łuku o anty aliasach. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_arc_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Wskaźnik do funkcji w celu narysowania wypełnionego łuku. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_pie_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, UINT r, INT start_angle, INT end_angle) <br/> Wskaźnik do funkcji w celu narysowania wypełnionego koła. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> Wskaźnik do funkcji w celu narysowania wielokropka. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_anti_aliased_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> Wskaźnik do funkcji w celu narysowania wielokropka. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_wide_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> Wskaźnik do funkcji w celu narysowania wielokropka z szerokim konturem. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_anti_aliased_wide_ellipse_draw)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> Wskaźnik do funkcji w celu narysowania wielokropka z szerokim konturem. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_ellipse_fill)(GX_DRAW_CONTEXT *context, INT xcenter, INT ycenter, INT a, INT b) <br/> Wskaźnik do funkcji, aby narysować wypełnioną wielokropek. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_8bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, constGX_GLYPH *glyph) <br/> Wskaźnik funkcji do narysowania 8-bitowego aliasu tekstowego na kanwie przy użyciu pędzla bieżącego kontekstu rysowania. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_4bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, const GX_GLYPH *glyph) <br/> Wskaźnik funkcji do narysowania 4-bitowego aliasu tekstowego na kanwie przy użyciu pędzla bieżącego kontekstu rysowania. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |
| VOID (*gx_display_driver_1bit_glyph_draw)(GX_DRAW_CONTEXT *context, GX_RECTANGLE *draw_area, GX_POINT *map_offset, const GX_GLYPH *glyph) <br/> Wskaźnik do funkcji, aby narysować jeden 1-bitowy monochromatyczny tekst na kanwie przy użyciu pędzla bieżącego kontekstu rysowania. Domyślne implementacje tej funkcji są dostępne dla każdego obsługiwanego formatu koloru i głębokości koloru. |


