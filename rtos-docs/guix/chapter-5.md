---
title: Rozdział 5 — sterowniki wyświetlania GUIX
description: Sterowniki wyświetlania GUIX definiują interfejs oprogramowania między abstrakcyjną kanwą rysowania a fizycznym sprzętem wyświetlania.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7c8f509aee1892693c22f8cfba3207158de4a1e9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823077"
---
# <a name="chapter-5---guix-display-drivers"></a>Rozdział 5 — sterowniki wyświetlania GUIX

Sterowniki wyświetlania GUIX definiują interfejs oprogramowania między abstrakcyjną kanwą rysowania a fizycznym sprzętem wyświetlania. Sterownik wyświetlania GUIX implementuje funkcje rysowania najniższego poziomu, które faktycznie zmieniają informacje o kolorach pikseli w pamięci kanwy i transferuje pamięć kanwy do fizycznego buforu ramek wyświetlania w systemach z podwójnym buforem.

Sterowniki wyświetlania GUIX są definiowane przez strukturę zawierającą fizyczne parametry wyświetlania oraz zestaw wskaźników funkcji do funkcji sterownika niskiego poziomu. Za pomocą tych bezpośrednich wskaźników funkcji, ogólna Kanwa i funkcje rysowania widżetu są całkowicie niezależne od szczegółów sprzętowych.

GUIX zapewnia kompletny, w pełni funkcjonalny, domyślny zestaw funkcji rysowania dla każdej obsługiwanej głębi kolorów i formatu koloru. Podczas implementowania sterownika wyświetlania bez konkretnej możliwości przyspieszania sprzętowego lub innych zagadnień specyficznych dla sprzętu te domyślne funkcje rysowania są zwykle wystarczające dla ostatecznej implementacji sterownika. W przypadku tych najprostszej liczby sterowników jedyną funkcją, która zwykle musi być implementowana w oprogramowaniu sterownika, jest funkcja służąca do konfigurowania urządzenia sprzętowego. Często wiąże się to z zainicjowaniem różnych rejestrów sprzętu w celu zdefiniowania zegara wyświetlacza LCD, wyświetlania wymiarów itp. W przypadku wszystkich innych funkcji implementacja sterownika po prostu inicjuje wskaźniki funkcji GX_DISPLAY do domyślnych implementacji funkcji dla żądanej głębi kolorów i formatu.

W przypadku implementowania niestandardowego sterownika wyświetlania najlepszym rozwiązaniem jest najpierw zainicjowanie wskaźników funkcji rysowania sterowników ekranu z domyślną implementacją oprogramowania dla głębi kolorów, która ma być obsługiwana, a następnie zastąp te wskaźniki funkcji, jeśli jest to wymagane, aby wywołać implementacje funkcji niestandardowych (jeśli istnieją). Aby to ułatwić, dostępna jest domyślna funkcja konfiguracji dla każdej obsługiwanej głębi kolorów i formatu. Na przykład, jeśli piszesz sterownik ekranu o 16-bitowym 5:6:5 formacie RGB, pierwszy element, który zwykle jest używany przez niestandardowy sterownik, jest wywoływanie ogólnej procedury konfiguracji dla tej głębi kolorów:

UINT my_custom_565_display_driver (GX_DISPLAY * Display)

```c
{
      
      // perform standard function pointer setup
      
      _gx_display_driver_565rgb_setup(display, GX_NULL,
      
             my_buffertoggle);

}
```

Parametr my_buffer_toggle powyżej jest wskaźnikiem do funkcji przełączania buforu sterownika wyświetlania (która może być GX_NULL, jeśli sterownik jest jednobuforowany i jest bezpośrednio rysowany do buforu ramki sprzętowej).

W przypadku pisania niestandardowego sterownika wyświetlania należy uwzględnić plik nagłówkowy gx_display. h w niestandardowym źródle sterowników, czyli plik nagłówka wewnętrznego use nie jest dostępny dla oprogramowania na poziomie aplikacji.

Funkcje rysowania poziomu wyświetlania GUIX są odbierane jako dane wejściowe wskaźnika do struktury **GX_DRAW_CONTEXT** . Struktura **GX_DRAW_CONTEXT** definiuje współrzędne przycinania dla bieżącej operacji rysowania wraz z używanym pędzlem i kolorami. Każda funkcja rysowania otrzymuje jako dane wejściowe dodatkowe parametry charakterystyczne dla wymagań funkcji.

Sygnatura punktu wejścia sterownika **GX_DISPLAY** jest definiowana jako

```c
UINT <device>_graphics_driver_<format>(GX_DISPLAY *diplay)
```

Chociaż nazwa tej funkcji jest kompletna do realizatora, Konwencja dla sterowników dostarczanych z GUIX polega na użyciu specyficznej dla sprzętu nazwy urządzenia w <device> formacie pola i koloru dla <format> powyższego pola.

Ta funkcja musi inicjować strukturę **GX_DISPLAY** podaną jako dane wejściowe i wykonywać wymagane konfiguracje sprzętu. Struktura **GX_DISPLAY** zawiera następujące pola.

| &nbsp; |
| --- | --- |
| ULONG gx_display_id <br/> Jest to pole używane przez aplikację w przypadku utworzenia więcej niż jednego wystąpienia określonego sterownika. |
| CHAR * gx_display_name <br/> Opcjonalna nazwa używana do identyfikowania sterownika. |
| GX_DISPLAY * gx_display_created_next <br/> To pole jest inicjowane przez GUIX i służy do tworzenia i konserwowania listy wszystkich wystąpień GX_DISPLAY. |
| GX_DISPLAY * gx_display_created_previous <br/> To pole jest inicjowane przez GUIX i służy do tworzenia i konserwowania listy wszystkich wystąpień GX_DISPLAY. |
| GX_VALUE gx_display_color_format <br/> To pole powinno uwzględniać format danych graficznych obsługiwany przez ten sterownik. Typy formatów kolorów są zdefiniowane w pliku nagłówkowym gx_api. h. |
| GX_VALUE gx_display_width <br/> To pole powinno być zainicjowane, aby pomieścić fizyczną szerokość ekranu w pikselach. |
| GX_VALUE gx_display_height <br/> To pole powinno być inicjowane w celu przechowywania fizycznej wysokości wyświetlania w pikselach. |
| GX_COLOR * gx_display_color_table <br/> Jest to wskaźnik do tabeli używanej do konwertowania wartości identyfikatora koloru na wartości koloru określonego koloru. |
| GX_PIXELMAP * gx_display_pixelmap_table <br/> Jest to wskaźnik do aktywnej tabeli Pixelmap dla tego ekranu. |
| GX_FONT * gx_display_font_table <br/> Jest to wskaźnik do aktywnej tabeli czcionek dla tego ekranu. |
| GX_COLOR * gx_display_palette <br/> W przypadku sterowników trybu palety jest to wskaźnik do aktywnej palety kolorów. W przypadku sterowników, które nie używają palety kolorów, ten wskaźnik jest GX_NULL. |
| Gx_display_pixelmap_table_size UINT <br/> Liczba wpisów w aktywnej tabeli Pixelmap. |
| Gx_display_font_table_size UINT <br/> Liczba wpisów w aktywnej tabeli czcionek. |
| Gx_display_palette_size UINT <br/> Liczba wpisów w palecie kolorów (jeśli istnieje). |
| ULONG gx_display_handle <br/> Unikatowy identyfikator lub *uchwyt*, który określa wyświetlanie.
| Gx_display_driver_ready UINT <br/> To pole jest używane do sygnalizowania GUIX, gdy sterownik jest gotowy do działania. W niektórych przypadkach sterownik może wymagać kilku poziomów inicjalizacji i konfiguracji, podczas gdy GUIX czasu nie mogą próbować korzystać z sterownika. Ta flaga powinna mieć ustawioną wartość 1, gdy sterownik jest gotowy do obsługi żądań rysowania. |
| VOID * gx_display_driver_data <br/> To pole jest używane przez implementację sterownika. Jeśli sterownik musi utworzyć i odwołać się do dodatkowych informacji niedostępnych w strukturze GX_DISPLAY, Sterownik powinien przydzielić miejsce dla i wskazać te dodatkowe dane przy użyciu tego pola struktury. Przykładem dodatkowych danych specyficznych dla sterownika może być kanał DMA używany przez sterownik lub kanał SPI, do którego jest podłączony bufor ramki wyświetlania. |
| VOID (* gx_display_driver_drawing_initiate) (struktura GX_DISPLAY_STRUCT * Display, struct GX_CANVAS_STRUCT * Kanwa) <br/> Jest to wskaźnik funkcji, który, jeśli nie ma wartości NULL, jest wywoływany przez funkcję gx_canvas_drawing_initiate. W przypadku sterowników wyświetlania wykorzystujących listę wyświetlania akceleratora grafiki lub grafiki sprzętowej ta funkcja może być używana do rozpoczęcia nowej listy wyświetlania. Ten wskaźnik funkcji może mieć wartość NULL. |
| VOID (* gx_display_driver_palette_set) (struktura GX_DISPLAY_STRUCT * Display, GX_COLOR * paleta, liczba INT) <br/> Jest to wskaźnik do funkcji służącej do instalowania palety kolorów. Ta funkcja ma wartość NULL, chyba że sterownik działa w palecie (nazywany również trybem Table Lookup lub CLUT). |
| VOID (* gx_display_driver_simple_line_draw) (GX_DRAW_CONTECT * Context, INT x1, INTy1, INT X2, INT Y2) <br/> Jest to wskaźnik do funkcji implementującej ogólny rysunek liniowy bez wygładzania. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_simple_wide_line_draw) (GX_DRAW_CONTECT * Context, INT x1, INTy1, INT X2, INT Y2) <br/> Jest to wskaźnik do funkcji służącej do implementowania ogólnego rysowania liniowego, bez wygładzania. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_anti_aliased_line_draw) (GX_DRAW_CONTECT * Context, INT x1, INTy1, INT X2, INT Y2) <br/> Jest to wskaźnik do funkcji implementującej ogólny rysunek z wygładzoną linią. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_anti_aliased_wide_line_draw) (GX_DRAW_CONTECT * Context, INT x1, INTy1, INT X2, INT Y2) <br/> Jest to wskaźnik do funkcji służącej do implementowania ogólnego rysowania wygładzonych linii. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_horizonal_line_draw) (GX_DRAW_CONTECT * Context, INT x1, INT X2, INT y) <br/> Jest to wskaźnik do funkcji, aby zaimplementować specjalny przypadek rysowania linii poziomej. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_horizonal_pixelmap_line_draw) (GX_DRAW_CONTECT * kontekst, INT x1, INT X2, INT y, GX_PIXELMAP map) <br/> Jest to wskaźnik do funkcji, aby zaimplementować rysowanie pojedynczego wiersza Pixelmap. Ta funkcja jest używana wewnętrznie dla kształtów wypełnienia wzorca. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_vertical_line_draw) (GX_DRAW_CONTECT * Context, INT Y1, INT Y2, INT x) <br/> Jest to wskaźnik do funkcji, aby zaimplementować specjalny przypadek rysowania linii poziomej. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_horizonal_pattern_line_draw) (GX_DRAW_CONTECT * Context, INT x1, INT X2, INT y) <br/> Jest to wskaźnik do funkcji służącej do implementowania rysowania liniowego linii wzorka. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_vertical_pattern_line_draw) (GX_DRAW_CONTECT * Context, INT Y1, INT Y2, INT x) <br/> Jest to wskaźnik do funkcji, aby zaimplementować rysowanie pionowego obramowania linii. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_canvas_copy) (struktura GX_CANVAS_STRUCT * source, struktura GX_CANVAS_STRUCT * docelowy) <br/> Jest to wskaźnik do funkcji, aby skopiować dane kanwy z jednej kanwy do innej. Do zdefiniowania obszaru kopiowania jest używany nieprawidłowy prostokąt kanwy źródłowej. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_canvas_blend) (struktura GX_CANVAS_STRUCT * source, struktura GX_CANVAS_STRUCT * docelowy) <br/> Jest to wskaźnik do funkcji, która umożliwia alfa-Blend danych kanwy z kanwy źródłowej z istniejącymi danymi na kanwie docelowej. Kanwa źródłowa nieprawidłowy prostokąt jest używany do definiowania obszaru mieszania. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_pixelmap_blend) (GX_DRAW_CONTEXT * Context, INT xpos, INT YPos, GX_PIXELMAP * PMP, GX_UBYTE Alpha) <br/> Jest to wskaźnik do funkcji służącej do mieszania Pixelmap na kanwie tła zdefiniowanej przez kontekst rysowania. Podana wartość alfa może być uzupełnieniem kanału alfa zawartego w danych Pixelmap. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_pixelmap_draw) (GX_DRAW_CONTEXT * Context, INT xpos, INT YPos, GX_PIXELMAP * PMP) <br/> Jest to wskaźnik do funkcji, aby narysować Pixelmap do kanwy zdefiniowanej przez kontekst rysowania. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_jpeg_draw) (GX_DRAW_CONTEXT * Context, INT xpos, INT YPos, GX_PIXELMAP * PMP) <br/> Jest to wskaźnik do funkcji, aby zdekodować obraz jpg i renderować go bezpośrednio na kanwie. Ta funkcja jest dostępna tylko wtedy, gdy GX_SOFTWARE_DECODER_SUPPORT jest zdefiniowana. Ten wskaźnik funkcji ma wartość NULL. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_png_draw) (GX_DRAW_CONTEXT * Context, INT xpos, INT YPos, GX_PIXELMAP * PMP) <br/> Jest to wskaźnik do funkcji, aby zdekodować obraz PNG i renderować go bezpośrednio na kanwie. Ta funkcja jest dostępna tylko wtedy, gdy GX_SOFTWARE_DECODER_SUPPORT jest zdefiniowana. Ten wskaźnik funkcji ma wartość NULL. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_pixelmap_rotate) (GX_DRAW_CONTEXT * Context, INT xpos, INT YPos, GX_PIXELMAP * PMP INT, INT rot_cx, INT rot_cy) <br/> Jest to wskaźnik do funkcji, aby obrócić pixemap i renderować wynik bezpośrednio do kanwy. Ta funkcja jest wywoływana przez gx_canvas_pixelmap_rotate implementacje APIDefault tej funkcji są dostępne dla każdej obsługiwanej głębi kolorów i formatu koloru. |
| VOID * gx_display_driver_pixel_write) (GX_DRAW_CONTEXT * kontekst, INT x, INT y, GX_COLOR Color) <br/> Jest to wskaźnik do funkcji, aby napisać jeden piksel w pamięci kanwy. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. <br/>
| VOID * gx_display_driver_block_move) (GX_DRAW_CONTEXT * kontekst, GX_RECTANGLE * blok, INT xshift, INT yshift) <br/> Jest to wskaźnik do funkcji służącej do przenoszenia lub przesuwania bloku pikseli w obrębie kanwy. Ta funkcja jest używana głównie do szybkiego przewijania zawartości okna. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_pixel_blend) (GX_DRAW_CONTEXT * kontekst, INT x, INT y, GX_COLOR Color, GX_UBYTE Alpha) <br/> Ta funkcja jest używana do alfa-Blend wartości koloru przychodzącego pikseli z istniejącą wartością koloru w pamięci kanwy na pozycji x, y. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| GX_COLOR (* gx_display_driver_native_color_get) (GX_COLOR rawcolor) <br/> Ta funkcja konwertuje kolor z 32-bitowego A:R: G:B format koloru używany wewnętrznie przez GUIX do natywnego formatu koloru kanwy i wyświetlania. Oczekiwana jest pewna utrata informacji o kolorach dla sterowników wyświetlanych z niższym głębią kolorów. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| USHORT (* gx_display_driver_row_pitch_get) (szerokość USHORT) <br/> Zwraca liczbę bajtów lub krok jednego wiersza danych graficznych, która ma żądaną szerokość kanwy. Ta funkcja służy do obliczania rozmiaru obszaru pamięci wymaganego do utworzenia kanwy. Wysokość i szerokość wiersza nie zawsze są takie same ze względu na ograniczenia wyrównania linii skanowania sprzętowego. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_buffer_toggle) (struktura GX_CANVAS_STRUCT * Kanwa, GX_RECTANGLE * dirty_area) <br/> Jest to wskaźnik do funkcji służącej do przełączania między działającymi i widocznymi buforami ramek dla podwójnych buforowanych systemów pamięci. Ta funkcja musi najpierw nakazać sprzętowi rozpoczęcie korzystania z nowego buforu ramek, a następnie skopiować zmodyfikowaną część nowego widocznego bufora do bufora pomocnika, aby upewnić się, że dwa bufory pozostają zsynchronizowane. | 
| VOID (* gx_display_driver_polygon_draw) (GX_DRAW_CONTEXT * kontekst, INT num_points, GX_POINT * wierzchołków <br/> Wskaźnik do funkcji, aby narysować wielokąt. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_polygon_fill) (GX_DRAW_CONTEXT * kontekst, INT num_points, GX_POINT * wierzchołków <br/> Wskaźnik do funkcji, aby narysować wypełniony wielokąt. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_circle_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r) <br/> Wskaźnik do funkcji, aby narysować okrąg. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_anti_aliased_circle_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r) <br/> Wskaźnik do funkcji, aby narysować okrąg antyaliasowy. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_wide_circle_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r) <br/> Wskaźnik do funkcji, aby narysować okrąg z szeroką konturem. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_wide_anti_aliased_circle_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r) <br/> Wskaźnik do funkcji, aby narysować wygładzony okrąg z szerokim konturem. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_circle_fill) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r) <br/> Wskaźnik do funkcji, aby narysować wypełniony okrąg. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_arc_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r, INT start_angle, INT end_angle) <br/> Wskaźnik do funkcji, aby narysować łuk. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_anti_aliased_arc_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r, INT start_angle, INTend_angle) <br/> Wskaźnik do funkcji, aby narysować łuk wygładzony. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_wide_arc_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r, INT start_angle, INT end_angle) <br/> Wskaźnik do funkcji, aby narysować łuk z szerokim konturem. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_anti_aliased_wide_arc_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r, INT start_angle, INTend_angle) <br/> Wskaźnik do funkcji, aby narysować łuk wygładzony. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_arc_fill) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r, INT start_angle, INT end_angle) <br/> Wskaźnik do funkcji, aby narysować wypełniony łuk. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_pie_fill) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, UINT r, INT start_angle, INT end_angle) <br/> Wskaźnik do funkcji, aby narysować wypełniony wykres kołowy. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_ellipse_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, INT a, INT b) <br/> Wskaźnik do funkcji, aby narysować elipsę. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_anti_aliased_ellipse_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, INT a, INT b) <br/> Wskaźnik do funkcji, aby narysować elipsę. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_wide_ellipse_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, INT a, INT b) <br/> Wskaźnik do funkcji, aby narysować wielokropek z szerokim konturem. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_anti_aliased_wide_ellipse_draw) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, INT a, INT b) <br/> Wskaźnik do funkcji, aby narysować wielokropek z szerokim konturem. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_ellipse_fill) (GX_DRAW_CONTEXT * Context, INT xcenter, INT YCenter, INT a, INT b) <br/> Wskaźnik do funkcji, aby narysować wypełnioną elipsę. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_8bit_glyph_draw) (GX_DRAW_CONTEXT * kontekst, GX_RECTANGLE * draw_area, GX_POINT * map_offset, constGX_GLYPH * symbol) <br/> Wskaźnik do funkcji, aby narysować symbol tekstu z aliasem 1 8-bitowy na kanwie przy użyciu pędzla bieżącego kontekstu rysowania. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_4bit_glyph_draw) (GX_DRAW_CONTEXT * kontekst, GX_RECTANGLE * draw_area, GX_POINT * map_offset, const GX_GLYPH * symbol) <br/> Wskaźnik do funkcji, aby narysować symbol tekstu z aliasem 1 4-bitowy na kanwie przy użyciu pędzla bieżącego kontekstu rysowania. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |
| VOID (* gx_display_driver_1bit_glyph_draw) (GX_DRAW_CONTEXT * kontekst, GX_RECTANGLE * draw_area, GX_POINT * map_offset, const GX_GLYPH * symbol) <br/> Wskaźnik do funkcji, aby narysować 1 1-bitowy symbol tekstu monochromatycznego na kanwie przy użyciu pędzla bieżącego kontekstu rysowania. Dla każdej obsługiwanej głębi kolorów i formatu koloru są dostępne domyślne implementacje tej funkcji. |


