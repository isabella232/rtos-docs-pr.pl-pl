---
title: Rozdział 4 — Opis usług GUIX Services
description: Ten rozdział zawiera opis wszystkich usług GUIX (wymienionych poniżej) w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 7a17ab0d2500d021bb9397dbf673427362c45173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822356"
---
# <a name="chapter-4---description-of-guix-services"></a>Rozdział 4 — Opis usług GUIX Services

Ten rozdział zawiera opis wszystkich usług GUIX (wymienionych poniżej) w porządku alfabetycznym.  

W sekcji "wartości zwracane" w poniższych opisach interfejsów API nie ma wpływ na wartości **pogrubione** **GX_DISABLE_ERROR_CHECKING** definiują, która jest używana do wyłączania sprawdzania błędów interfejsu API, podczas gdy wartości Niepogrubione są całkowicie wyłączone. 

| **Usługa GUIX**                      | **Opis**                                                                             |
| -------------------------------------- | -------------------------------------------------------------------------------------------- |
| gx_accordion_menu_create            | Utwórz menu zgodnie z przepisami                                                                        |
| gx_accordion_menu_draw              | Menu Rysuj zgodnie z przepisami                                                                          |
| gx_accordion_menu_event_process    | Zdarzenie menu zgodnie z procesem                                                                 |
| gx_accordion_menu_position          | Pozycje menu pozycji                                                                          |
| gx_animation_canvas_define          | Dostarcz pamięć do kontrolera animacji dla kanwy, która ma być używana na potrzeby kolejnych animacji. |
| gx_animation_create                  | Tworzenie kontrolera animacji                                                               |
| gx_animation_delete                  | Usuwanie kontrolera animacji                                                               |
| gx_animation_drag_disable           | Wyłącz hak animacji przeciągnięcia ekranu                                                           |
| gx_animation_drag_enable            | Włącz hak animacji przeciągnięcia ekranu                                                            |
| gx_animation_landing_speed_set     | Ustaw szybkość wyładunku dla animacji przeciągania ekranu                                                  |
| gx_animation_start                   | Inicjowanie sekwencji animacji                                                               |
| gx_animation_stop                    | Wstrzymywanie sekwencji animacji                                                                |
| gx_binres_language_count_get      |  Pobierz liczbę języków z pliku zasobów binarnych                                          |
| gx_binres_language_info_load      |  Odczytywanie informacji o nazwie i rozmiarze języka z pliku zasobów binarnych.                           |
| gx_binres_language_table_load      | przestarzałe Załaduj tabelę języka z binarnego bufora danych zasobów                          |
| gx_binres_language_table_load_ext | Załaduj tabelę języka z binarnego bufora danych zasobów                                       |
| gx_binres_theme_load                | Ładowanie motywu z binarnego bufora danych zasobów                                                |
| gx_brush_default                     | Zainicjuj bieżący Pędzel do wartości domyślnych                                                         |
| gx_brush_define                      | Definiowanie pędzla                                                                                 |
| gx_button_background_draw           | Rysuj tło przycisku                                                                       |
| gx_button_create                     | Przycisk Utwórz                                                                                |
| gx_button_deselect                   | Przycisk Anuluj wybór                                                                              |
| gx_button_draw                       | Przycisk rysowania                                                                                  |
| gx_button_event_process            | Zdarzenie przycisku procesu                              |
| gx_button_select                    | Przycisk Wybierz                                     |
| gx_canvas_alpha_set                | Ustaw wartość alfa-Blend dla kanwy                  |
| gx_canvas_arc_draw                 | Łuk rysowania okręgu                                   |
| gx_canvas_block_move               | Przenieś blok                                        |
| gx_canvas_circle_draw              | Rysuj okrąg                                       |
| gx_canvas_create                    | Tworzenie kanwy                                   |
| gx_canvas_delete                    | Usuwanie kanwy                                   |
| gx_canvas_drawing_complete         | Ukończ rysowanie kanwy                           |
| gx_canvas_drawing_initiate         | Zainicjuj rysowanie na kanwie                        |
| gx_canvas_ellipse_draw             | Rysowanie elipsy                                   |
| gx_canvas_hardware_layer_bind     | Powiąż kanwę z warstwą grafiki                     |
| gx_canvas_hide                      | Ukrywanie kanwy                           |
| gx_canvas_line_draw                | Rysuj linię                                         |
| gx_canvas_memory_define            | Przypisywanie adresu pamięci kanwy                      |
| gx_canvas_offset_set               | Przypisanie kanwy x, przesunięcie ekranu y                  |
| gx_canvas_pie_draw                 | Rysowanie kształtu kołowego (klinowego)                          |
| gx_canvas_pixel_draw               | Rysowanie pojedynczego piksela                               |
| gx_canvas_pixelmap_blend           | Mieszanie Pixelmap z tłem                  |
| gx_canvas_pixelmap_get             | Pobierz Pixelmap wskazujący na dane kanwy            |
| gx_canvas_pixelmap_draw            | Rysuj Pixelmap                                     |
| gx_canvas_pixelmap_rotate          | Obróć Pixelmap                                   |
| gx_canvas_pixelmap_tile            | Pixelmap kafelka                                     |
| gx_canvas_polygon_draw             | Rysuj Wielokąt                                      |
| gx_canvas_rectangle_draw           | Rysuj prostokąt                                    |
| gx_canvas_rotated_text_draw       | przestarzałe Rysuj tekst obrócony o punkt środkowy |
| gx_canvas_rotated_text_draw_ext  | Rysuj tekst obrócony o punkt środkowy              |
| gx_canvas_shift                     | Przenieś kanwę o x, y                               |
| gx_canvas_show                      | Wyświetlanie kanwy jako widocznej                             |
| gx_canvas_text_draw                | przestarzałe Rysuj tekst                            |
| gx_canvas_text_draw_ext           | Rysuj tekst                                         |
| gx_checkbox_create                  | Utwórz pole wyboru                                 |
| gx_checkbox_draw                    | Rysowanie pola wyboru                                   |
| gx_checkbox_event_process          | Funkcja CheckBox zdarzenia                   |
| gx_checkbox_pixelmap_set           | Przypisz pole wyboru Pixelmap                          |
| gx_checkbox_select                  | Zaznacz pole wyboru                                   |
| gx_circular_gauge_angle_get       | Pobierz kąt wskazówki elementu widget wskaźnika                |
| gx_circular_gauge_angle_set       | Kąt przypisania elementu widgetu wskaźnika                  |
| gx_circular_gauge_animation_set   | Definiowanie animacji cyklicznego miernika                   |
| gx_circular_gauge_background_draw | Wyrysuj tło miernika cyklicznego                    |
| gx_circular_gauge_create           | Tworzenie widżetu miernik cykliczny                    |
| gx_circular_gauge_draw             | Rysowanie widgetu miernika okrągłego                      |
| gx_circular_gauge_event_process   | Zdarzenie cyklicznego miernika procesu                      |
| gx_context_brush_default            | Ustawianie pędzla bieżącego kontekstu                                      |
| gx_context_brush_define             | Definiowanie pędzla bieżącego kontekstu                                       |
| gx_context_brush_get                | Pobierz pędzel bieżącego kontekstu                                          |
| gx_context_brush_pattern_set       | Ustaw Wzorzec pędzla bieżącego kontekstu                           |
| gx_context_brush_set                | Ustaw pędzel bieżącego kontekstu                                          |
| gx_context_brush_style_set         | Ustaw styl pędzla bieżącego kontekstu                                    |
| gx_context_brush_width_set         | Ustaw szerokość pędzla bieżącego tekstu                                     |
| gx_context_color_get                | Rozpoznaj identyfikator koloru z wartością koloru                                     |
| gx_context_fill_color_set          | Ustaw kolor wypełnienia bieżącego kontekstu                                     |
| gx_context_font_get                 | Rozpoznawanie identyfikatora czcionki do wartości wskaźnika czcionki                               |
| gx_context_font_set                 | Ustaw czcionkę bieżącego kontekstu                                           |
| gx_context_line_color_set          | Ustaw kolor linii bieżącego kontekstu                                     |
| gx_context_pixelmap_get             | Rozpoznanie identyfikatora Pixelmap do Pixelmap wartości wskaźnika                       |
| gx_context_pixelmap_set             | Przypisywanie Pixelmap pędzla, używanego do wypełniania obszaru                            |
| gx_context_raw_brush_define        | Definiowanie surowego pędzla bieżącego kontekstu                                   |
| gx_context_raw_fill_color_set     | Ustaw nieprzetworzony kolor wypełnienia bieżącego kontekstu                                 |
| gx_context_raw_line_color_set     | Ustaw kolor nieprzetworzonego wiersza bieżącego kontekstu                                 |
| gx_context_string_get               | Pobierz ciąg skojarzony z bieżącym kontekstem rysowania (przestarzałe). |
| gx_context_string_get_ext          | Pobierz ciąg skojarzony z bieżącym kontekstem rysowania (przestarzałe). |
| gx_display_active_language_set     | Przypisywanie języka aktywnego                                                |
| gx_display_color_set                | Zastąp jedną wartość koloru w tabeli kolorów wyświetlania.                       |
| gx_display_color_table_set         | Przypisywanie tabeli kolorów używanej przez ekran                              |
| gx_display_create                    | Utwórz ekran                                                        |
| gx_display_delete                    | Usuń wyświetlanie                                                        |
| gx_display_font_table_set          | Przypisywanie tabeli czcionek używanej przez ekran                               |
| gx_display_language_table_get      | Pobierz tabelę języka skojarzoną z wyświetlaczem (przestarzałe)    |
| gx_display_language_table_get_ext | Pobierz tabelę języka skojarzoną z wyświetlaniem                 |
| gx_display_language_table_set      | Przypisz tabelę języka do wskazanego ekranu (przestarzałe)           |
| gx_display_language_table_set_ext | Przypisz tabelę języka do wskazanego ekranu.                       |
| gx_display_pixelmap_table_set      | Przypisywanie tabeli Pixelmap używanej przez ekran                           |
| gx_display_string_get               | Pobierz ciąg skojarzony z IDENTYFIKATORem ciągu (przestarzałe)                |
| gx_display_string_get_ext          | Pobierz ciąg skojarzony z IDENTYFIKATORem ciągu                             |
| gx_display_string_table_get             | Pobierz tabelę ciągów skojarzoną ze wskazanym ekranem (przestarzałe). |
| gx_display_string_table_get_ext        | Pobierz tabelę ciągów skojarzoną ze wskazanym wyświetlaniem               |
| gx_display_theme_install                 | Zainstaluj motywy na określonym ekranie                               |
| gx_drop_list_close                       | Zamknij listę rozwijaną                                                       |
| gx_drop_list_create                      | Utwórz listę rozwijaną                                                      |
| gx_drop_list_event_process               | Tworzenie listy rozwijanej zdarzeń                                            |
| gx_drop_list_open                        | Otwórz listę rozwijaną                                                        |
| gx_drop_list_pixelmap_set               | Ustaw Pixelmap na listę rozwijaną                                             |
| gx_drop_list_popup_set                  | Ustaw podręczny na listę rozwijaną                                                |
| gx_horizontal_list_children_position    | Umieść elementy widget elementów podrzędnych na liście poziomej                          |
| gx_horizontal_list_create                | Utwórz listę poziomą                                                |
| gx_horizontal_list_event_process        | Przetwarzanie zdarzenia na liście poziomej                                      |
| gx_horizontal_list_page_index_set      | Przypisz indeks strony listy poziomej                                     |
| gx_horizontal_list_selected_index_get  | Pobierz indeks wybranego elementu                                           |
| gx_horizontal_list_selected_widget_get | Pobierz widżet wybranego elementu                                          |
| gx_horizontal_list_selected_set         | Ustaw wybrany element                                                 |
| gx_horizontal_list_total_columns_set   | Zmień liczbę kolumn listy po utworzeniu                          |
| gx_horizontal_scrollbar_create           | Utwórz poziomy pasek przewijania                                           |
| gx_icon_button_create                    | Przycisk tworzenia ikony                                                    |
| gx_icon_button_draw                      | Rysowanie przycisku ikony                                                   |
| gx_icon_button_pixelmap_set             | Ustaw Pixelmap na przycisku ikony                                           |
| gx_icon_background_draw                  | Rysuj tło ikon                                                  |
| gx_icon_create                            | Ikona tworzenia                                                           |
| gx_icon_draw                              | Ikona rysowania                                                             |
| gx_icon_event_process                    | Funkcja przetwarzania zdarzeń ikon                                        |
| gx_icon_pixelmap_set                     | Ustaw Pixelmap dla ikony                                                 |
| gx_image_reader_create                   | Utwórz wystąpienie modułu czytnika obrazu                                   |
| gx_image_reader_palette_set             | Zdefiniuj paletę czytnika obrazu                                           |
| gx_image_reader_start                    | Rozpocznij proces dekompresowania i konwersji                           |
| gx_line_chart_axis_draw                 | Rysowanie wykresu liniowego x, oś y                                              |
| gx_line_chart_create                     | Utwórz wystąpienie GX_LINE_CHART                                       |
| gx_line_chart_data_draw                 | Rysowanie linii danych wykresu liniowego                                             |
| gx_line_chart_draw                       | Domyślny rysunek wykresu liniowego                                            |
| gx_line_chart_update                     | Wymuś aktualizację danych wykresu liniowego                                       |
| gx_line_chart_y_scale_calculate        | Oblicz skalę wartości danych na osi y na współrzędne pikseli.           |
| gx_menu_create                            | Utwórz menu                                                           |
| gx_menu_draw                              | Menu Rysuj                                                             |
| gx_menu_event_process                     | Zdarzenie menu procesu                                                    |
| gx_menu_insert                                | Wstaw nowy element                                                               |
| gx_menu_remove                                | Usuń element                                                                  |
| gx_menu_text_draw                            | Rysuj tekst menu                                                                  |
| gx_menu_text_offset_set                     | Ustaw przesunięcie rysowania tekstu menu                                                       |
| gx_multi_line_text_button_create           | Przycisk tworzenia wielowierszowego tekstu                                                   |
| gx_multi_line_text_button_draw             | Przycisk rysowania wielowierszowego tekstu                                                     |
| gx_multi_line_text_button_event_process   | Ustaw czcionkę dla przycisku tekstu wielowierszowego                                             |
| gx_multi_line_text_button_text_draw       | Fragment rysowania tekstu                                                 |
| gx_multi_line_text_button_text_id_set    | Ustaw przycisk ciągu systemowego na tekst                                                |
| gx_multi_line_text_button_text_set        | Przypisz ciąg zdefiniowany przez użytkownika do przycisku tekstowego (przestarzałe)                          |
| gx_multi_line_text_button_text_set_ext   | Przypisz ciąg zdefiniowany przez użytkownika do przycisku tekstowego                                       |
| gx_multi_line_text_input_backspace         | Usuń znak przed pozycją kursora wielowierszowego wprowadzania tekstu               |
| gx_multi_line_text_input_buffer_get       | Pobiera informacje o buforze widżetu wprowadzania tekstu                               |
| gx_multi_line_text_input_buffer_clear     | Usuwa wszystkie znaki z buforu wejściowego tekstu                               |
| gx_multi_line_text_input_char_insert      | Wstaw ciąg formatu UTF8 w pozycji kursora wielowierszowego wprowadzania tekstu (przestarzałe) |
| gx_multi_line_text_input_char_insert_ext | Wstaw ciąg formatu UTF8 w pozycji kursora wielowierszowego wprowadzania tekstu              |
| gx_multi_line_text_input_create            | Utwórz wielowierszowe wprowadzanie tekstu                                                    |
| gx_multi_line_text_input_cursor_pos_get  | Pobierz położenie kursora wielowierszowego tekstu wejściowego                                  |
| gx_multi_line_text_input_delete            | Usuń znak po rozłożeniu kursora tekstu wielowierszowego                 |
| gx_multi_line_text_input_down_arrow       | Przenieś kursor wielowierszowego wprowadzania tekstu do następnego wiersza                              |
| gx_multi_line_text_input_end               | Przesuń kursor wielowierszowego tekstu do końca bieżącego wiersza                |
| gx_multi_line_text_input_event_process    | Przetwarzaj tekst wielowierszowego tekstu wejściowego                                              |
| gx_multi_line_text_input_fill_color_set  | Ustawianie kolorów wypełnienia dla tekstu wielowierszowego                                       |
| gx_multi_line_text_input_home              | Przenieś kursor wielowierszowego wprowadzania tekstu do początku bieżącego wiersza              |
| gx_multi_line_text_input_left_arrow       | Przesuń kursor wielowierszowego wprowadzania tekstu w lewo o jeden znak                         |
| gx_multi_line_text_input_right_arrow      | Przesuń kursor wielowierszowego tekstu wejściowego o jeden znak w prawo                        |
| gx_multi_line_text_input_style_add        | Dodaj flagi wielowierszowego stylu tekstu                                                 |
| gx_multi_line_text_input_style_remove     | Usuń wielowierszowe flagi stylu tekstu                                              |
| gx_multi_line_text_input_style_set        | Przypisywanie flag stylu tekstu wielowierszowego                                              |
| gx_multi_line_text_input_text_color_set  | Przypisywanie kolorów tekstu wielowierszowego wprowadzania tekstu                                    |
| gx_multi_line_text_input_text_select      | Zaznacz tekst wielowierszowego tekstu wejściowego                                               |
| gx_multi_line_text_input_text_set         | Przypisywanie tekstu do wielowierszowego wprowadzania tekstu (przestarzałe)                               |
| gx_multi_line_text_input_text_set_ext          | Przypisywanie tekstu do wielowierszowego wprowadzania tekstu                         |
| gx_multi_line_text_input_up_arrow               | Przenieś kursor wielowierszowego tekstu wprowadzania do poprzedniego wiersza       |
| gx_multi_line_text_view_create                   | Tworzenie wielowierszowego widoku tekstu                                  |
| gx_multi_line_text_view_event_process           | Przetwarzanie zdarzenia wielowierszowego widoku tekstu                           |
| gx_multi_line_text_view_font_set                | Ustaw czcionkę używaną w widoku tekstu wielowierszowego                        |
| gx_multi_line_text_view_line_space_set         | Ustawianie wielowierszowego obramowania tekstu                          |
| gx_multi_line_text_view_scroll_info_get        | Pobierz informacje o przewijaniu wielowierszowego widoku tekstu                         |
| gx_multi_line_text_view_text_color_set         | Ustawianie koloru tekstu w widoku tekstu linii Mulit                       |
| gx_multi_line_text_view_text_id_set            | Ustawianie ciągu tekstowego systemu w widoku tekstu wielowierszowego               |
| gx_multi_line_text_view_text_set                | Ustaw ciąg zdefiniowany przez użytkownika na widok tekstu wielowierszowego (przestarzałe) |
| gx_multi_line_text_view_text_set_ext           | Ustaw ciąg zdefiniowany przez użytkownika na widok tekstu wielowierszowego              |
| gx_multi_line_text_view_whitespace_set          | Ustaw odstępy między widokiem tekstu wielowierszowego                          |
| gx_numeric_pixelmap_prompt_create                 | Tworzenie numerycznego monitu Pixelmap                               |
| gx_numeric_pixelmap_prompt_format_ function_set | Przesłoń funkcję formatu pixelmapego monitu          |
| gx_numeric_pixelmap_prompt_value_set             | Ustaw wartość monitu liczbowego                                     |
| gx_numeric_prompt_create                           | Utwórz monit liczbowy                                        |
| gx_numeric_prompt_format_function_set            | Przesłoń funkcję formatu monitu liczbowego                   |
| gx_numeric_prompt_value_set                       | Ustaw wartość monitu liczbowego                                     |
| gx_numeric_scroll_wheel_create                    | Utwórz widżet przewijania numerycznego                           |
| gx_numeric_scroll_wheel_range_set                | Przypisz zakres wartości kółka przewijania                              |
| gx_pixelmap_button_create                          | Utwórz przycisk Pixelmap                                       |
| gx_pixelmap_button_draw                            | Przycisk rysowania Pixelmap                                         |
| gx_pixelmap_button_event_process                  | Przetwarzanie zdarzenia Pixelmap Button                             |
| gx_pixelmap_button_pixelmap_set                   | Ustaw Pixelmap w Pixelmap przycisku                              |
| gx_pixelmap_prompt_create                          | Utwórz monit Pixelmap                                       |
| gx_pixelmap_prompt_draw                            | Rysowanie monitu Pixelmap                                         |
| gx_pixelmap_prompt_pixelmap_set                   | Ustaw Pixelmap w monicie Pixelmap                              |
| gx_pixelmap_slider_create                          | Utwórz suwak Pixelmap                                       |
| gx_pixelmap_slider_draw                            | Rysuj suwak Pixelmap                                         |
| gx_pixelmap_slider_event_process        | Przetwarzanie zdarzeń suwaka Pixelmap       |
| gx_pixelmap_slider_pixelmap_set         | Ustaw Pixelmap w suwaku Pixelmap        |
| gx_progress_bar_background_draw         | Rysuj tło paska postępu           |
| gx_progress_bar_create                   | Utwórz pasek postępu                  |
| gx_progress_bar_draw                     | Rysowanie paska postępu                    |
| gx_progress_bar_event_process           | Przetwarzanie zdarzenia paska postępu           |
| gx_progress_bar_font_set                | Ustaw czcionkę tekstu paska postępu          |
| gx_progress_bar_info_set                | Ustaw strukturę informacji paska postępu |
| gx_progress_bar_pixelmap_set            | Ustaw Pixelmap używany do rysowania paska postępu |
| gx_progress_bar_range_set               | Ustaw zakres wartości paska postępu        |
| gx_progress_bar_text_color_set         | Ustaw kolor tekstu paska postępu            |
| gx_progress_bar_text_draw               | Rysuj tekst paska postępu                 |
| gx_progress_bar_value_set               | Ustaw wartość paska postępu                 |
| gx_prompt_create                          | Utwórz monit                          |
| gx_prompt_draw                            | Rysuj monit                            |
| gx_prompt_event_process                   | Zdarzenie monitu procesu                   |
| gx_prompt_font_set                       | Ustawianie czcionki monitu                        |
| gx_prompt_text_color_set                | Ustaw kolor tekstu monitu                  |
| gx_prompt_text_draw                      | Fragment rysowania tekstu monitu    |
| gx_prompt_text_get                       | Pobierz tekst monitu (przestarzałe)           |
| gx_prompt_text_get_ext                  | Pobierz tekst monitu                        |
| gx_prompt_text_id_set                   | Ustawianie monitu z ciągiem tekstowym systemu     |
| gx_prompt_text_set                       | Ustaw tekst monitu (przestarzałe)           |
| gx_prompt_text_set_ext                  | Ustaw tekst monitu                        |
| gx_radial_progress_bar_anchor_set      | Ustaw kąt początkowy                     |
| gx_radial_progress_bar_background_draw | Rysuj tło paska postępu promieniowego    |
| gx_radial_progress_bar_create           | Utwórz pasek postępu promieniowego           |
| gx_radial_progress_bar_draw             | Rysowanie paska postępu promieniowego             |
| gx_radial_progress_bar_event_process   | Zdarzenie paska postępu promieniowego procesu      |
| gx_radial_progress_bar_font_set        | Ustaw czcionkę paska postępu promieniowego           |
| gx_radial_progress_bar_info_set        | Ustaw informacje o pasku postępu promieniowego    |
| gx_radial_progress_bar_text_color_set | Ustaw kolor tekstu paska postępu promieniowego     |
| gx_radial_progress_bar_text_draw       | Rysuj tekst paska postępu promieniowego          |
| gx_radial_progress_bar_value_set       | Ustaw wartość paska postępu promieniowego          |
| gx_radio_button_create                   | Utwórz przycisk radiowy                    |
| gx_radio_button_draw                     | Przycisk rysowania przycisku radiowego                      |
| gx_radio_button_pixelmap_set            | Ustaw Pixelmap w przycisku radiowym           |
| gx_radial_slider_anchor_angles_set     | Ustaw listę kątów zakotwiczenia suwaka promieniowego    |
| gx_radial_slider_angle_set              | Ustaw kąt suwaka promieniowego                |
| gx_radial_slider_animation_set          | Ustaw informacje o animacji suwaka promieniowego       |
| gx_radial_slider_animation_start               | Ustaw kąt suwaka promieniowego z animacją                      |
| gx_radial_slider_create                         | Tworzenie suwaka promieniowego                                      |
| gx_radial_slider_draw                           | Rysowanie suwaka promieniowego                                        |
| gx_radial_slider_event_process                 | Przetwórz zdarzenie suwaka promieniowego                               |
| gx_radial_slider_info_get                      | Pobierz wskaźnik informacji o suwaku promieniowym                  |
| gx_radial_slider_info_set                      | Ustaw informacje suwaka promieniowego                               |
| gx_radial_slider_pixelmap_set                  | Ustaw suwak promieniowy pixelmaps                                 |
| gx_rich_text_view_create                       | Tworzenie widoku tekstu sformatowanego                                     |
| gx_rich_text_view_draw                         | Rysuj widok tekstu sformatowanego                                         |
| gx_rich_text_view_set_fonts                    | Ustaw czcionki widoku tekstu sformatowanego                                    |
| gx_rich_text_view_text_draw                    | Rysuj tekst w postaci tekstu sformatowanego                                    |
| gx_screen_stack_create                          | Utwórz blok sterowania stosu ekranu GUIX i obszar pamięci. |
| gx_screen_stack_pop                             | Pokaż górny ekran z poziomu stosu ekranu.                   |
| gx_screen_stack_push                            | Wypchnij bieżący ekran do stosu ekranu.                |
| gx_screen_stack_reset                           | Zresetuj stos ekranu                                      |
| gx_scroll_wheel_create                          | Element widget tworzenia podstawowego kółka przewijania                             |
| gx_scroll_wheel_event_process                  | Przetwarzanie zdarzeń kółka przewijania                               |
| gx_scroll_wheel_gradient_alpha_set            | Modyfikuj gradient nakładki kółka przewijania                        |
| gx_scroll_wheel_row_height_set                | Przypisz wysokość wiersza kółka przewijania                              |
| gx_scroll_wheel_selected_background_set       | Przypisz obraz tła dla zaznaczonego wiersza                    |
| gx_scroll_wheel_selected_get                   | Pobierz indeks zaznaczonego wiersza                                 |
| gx_scroll_wheel_selected_set                   | Przypisz indeks zaznaczonego wiersza                                   |
| gx_scroll_wheel_speed_set                      | Przypisz szybkość przewijania                                      |
| gx_scroll_wheel_total_rows_set                | Przypisz łączną liczbę dostępnych wierszy                       |
| gx_scrollbar_draw                                | Rysuj pasek przewijania                                              |
| gx_scrollbar_event_process                      | Zdarzenie ScrollBar procesu                                     |
| gx_scrollbar_limit_check                        | Sprawdź limit ScrollBar                                       |
| gx_scrollbar_reset                               | Resetuj pasek przewijania                                             |
| gx_scrollbar_value_set                          | Przypisz wartość paska przewijania                                      |
| gx_single_line_text_input_backspace           | Obsługuj znak spacji                                  |
| gx_single_line_text_input_buffer_clear       | Wyczyść bufor znaków                                  |
| gx_single_line_text_input_buffer_get         | Pobierz wskaźnik buforu                                     |
| gx_single_line_text_input_character_delete   | Usuń znak                                            |
| gx_single_line_text_input_character_insert   | Wstaw znak                                            |
| gx_single_line_text_input_create              | Utwórz jednowierszowe wprowadzanie tekstu                               |
| gx_single_line_text_input_draw                | Rysuj widżet tekstu jednowierszowego                          |
| gx_single_line_text_input_draw_position_get | Pobierz pozycję początkową rysowania tekstu                           |
| gx_single_line_text_input_end                 | Przenieś kursor do końca                                          |
| gx_single_line_text_input_event_process      | Przetwarzanie zdarzeń wprowadzania tekstu                                 |
| gx_single_line_text_input_fill_color_set    | Ustawianie kolorów wypełnienia dla tekstu jednowierszowego                  |
| gx_single_line_text_input_home                | Przenieś kursor do strony głównej                                         |
| gx_single_line_text_input_left_arrow         | Obsługa klawisza Strzałka w lewo                                       |
| gx_single_line_text_input_position_get       | Pobierz położenie kursora                                         |
| gx_single_line_text_input_right_arrow        | Uchwyt klawisza Strzałka w prawo                                      |
| gx_single_line_text_input_style_add          | Dodaj flagi stylu                                             |
| gx_single_line_text_input_style_remove       | Usuń flagi stylu                                          |
| gx_single_line_text_input_style_set          | Przypisz flagi stylu                                          |
| gx_single_line_text_input_text_color_set  | Ustaw kolory tekstu dla tekstu jednowierszowego                      |
| gx_single_line_text_input_text_select     | Zaznacz tekst tekstu wejściowego z pojedynczym wierszem                              |
| gx_single_line_text_input_text_set        | Ustaw tekst tekstu wejściowego z pojedynczym wierszem (przestarzałe)                    |
| gx_single_line_text_input_text_set_ext    | Ustaw tekst tekstu wejściowego z pojedynczym wierszem                                 |
| gx_slider_create                          | Utwórz suwak                                                   |
| gx_slider_draw                            | Suwak rysowania                                                     |
| gx_slider_event_process                   | Zdarzenie suwaka procesu                                            |
| gx_slider_info_set                        | Ustaw blok informacji o suwaku                                    |
| gx_slider_needle_draw                     | Rysuj wskazówkę suwaka                                              |
| gx_slider_needle_position_get             | Pobierz położenie wskazówki dla suwaka                                      |
| gx_slider_tickmarks_draw                  | Rysuj suwak rysowania znaczniki                                           |
| gx_slider_travel_get                      | Pobierz drogę suwaka                                               |
| gx_slider_value_calculate                 | Oblicz wartość suwaka                                          |
| gx_slider_value_set                       | Ustaw wartość suwaka                                                |
| gx_sprite_create                          | Utwórz widżet GX_SPRITE                                         |
| gx_sprite_current_frame_set               | Przypisz bieżącą ramkę wyświetlaną dla widżetu Sprite                  |
| gx_sprite_frame_list_set                  | Przypisywanie lub modyfikowanie listy ramek Sprite                            |
| gx_sprite_start                           | Rozpocznij sekwencję ikon                                         |
| gx_sprite_stop                            | Zatrzymaj sekwencję ikon                                          |
| gx_string_scroll_wheel_create             | Utwórz `GX_STRING_SCROLL_WHEEL` widżet                          |
| gx_string_scroll_wheel_event_process      | Zdarzenie kółka przewijania ciągu procesu                               |
| gx_string_scroll_wheel_string_id_list_set | Przypisz tablicę identyfikatorów ciągów                                      |
| gx_string_scroll_wheel_string_list_set    | Modyfikuj wyświetlaną tablicę ciągów                                   |
| gx_string_scroll_wheel_text_get           | Pobierz tekst dla wiersza kółka przewijania                              |
| gx_studio_widget_create                   | Create widget zdefiniowany w programie Studio                             |
| gx_studio_named_widget_create             | Utwórz ekran zdefiniowany w programie Studio                             |
| gx_studio_display_configure               | Utwórz i zainicjuj `GX_DISPLAY` , `GX_CANVAS` i `GX_WINDOW_ROOT` |
| gx_system_active_language_set             | Przypisywanie identyfikatora języka aktywnego                                       |
| gx_system_canvas_refresh                  | Wymuś odświeżanie (rysowanie) zanieczyszczonych kanw                       |
| gx_system_dirty_mark                      | Oznacz obszar jako zanieczyszczony                                                 |
| gx_system_dirty_partial_add               | Oznacz obszar częściowy jako zanieczyszczony                                         |
| gx_system_draw_context_get                | Pobierz kontekst rysowania                                             |
| gx_system_event_fold                      | Foldevent                                                       |
| gx_system_event_send                      | Wyślij zdarzenie                                                      |
| gx_system_focus_claim                     | Fokus dotyczący roszczeń                                                     |
| gx_system_initialize                      | Zainicjuj GUIX                                                 |
| gx_system_language_table_get              | Pobierz tabelę języka                                         |
| gx_system_language_table_set              | Przypisz tabelę języka                                           |
| gx_system_memory_allocator_set            | Przypisywanie przydzielania pamięci/cofania alokatora                            |
| gx_system_pen_configure                  | Ustaw konfigurację pióra                                  |
| gx_system_screen_stack_create           | Utwórz kontrolkę stosu ekranu                            |
| gx_system_screen_stack_get              | Pobieranie wskaźników stosu ekranu                         |
| gx_system_screen_stack_pop              | Podręczny ekran z poziomu stosu ekranu                       |
| gx_system_screen_stack_push             | Wypchnij ekran do stosu ekranu              |
| gx_system_screen_stack_reset            | Zresetuj stos ekranu                                 |
| gx_system_scroll_appearance_get         | Uzyskaj wygląd przewijania                                  |
| gx_system_scroll_appearance_set         | Ustaw wygląd przewijania                                  |
| gx_system_start                           | Uruchom GUIX                                             |
| gx_system_string_get                     | Pobierz ciąg                                             |
| gx_system_string_table_get              | Pobierz tabelę ciągów                                       |
| gx_system_string_table_set              | Ustawianie tabeli ciągów                                       |
| gx_system_string_width_get              | Pobierz szerokość ciągu (przestarzałe)                          |
| gx_system_string_width_get_ext         | Pobierz szerokość ciągu                                       |
| gx_system_theme_install                  | Instalowanie czcionek Font/Color/Pixelmap                     |
| gx_system_timer_start                    | Uruchom czasomierz                                            |
| gx_system_timer_stop                     | Zatrzymaj czasomierz                                             |
| gx_system_version_string_get            | Pobierz ciąg wersji biblioteki GUIX (przestarzałe)      |
| gx_system_version_string_get_ext       | Pobierz ciąg wersji biblioteki GUIX                   |
| gx_system_widget_find                    | Znajdź widżet                                            |
| gx_text_button_create                    | Przycisk tworzenia tekstu                                     |
| gx_text_button_draw                      | Przycisk rysowania tekstu                                       |
| gx_text_button_event_process             | Zdarzenie przycisku tekstu procesu                              |
| gx_text_button_font_set                 | Ustaw czcionkę dla przycisku tekstu                               |
| gx_text_button_text_color_set          | Kolor przycisku ustawiania tekstu                                  |
| gx_text_button_text_draw                | Część rysowania tekstu na rysunku przycisku                 |
| gx_text_button_text_get                 | Pobierz tekst używany w przycisku tekstu (przestarzałe)              |
| gx_text_button_text_get_ext            | Pobierz tekst używany w przycisku tekstowym                           |
| gx_text_button_text_id_set             | Przycisk przypisywania ciągu systemowego do tekstu                    |
| gx_text_button_text_set                 | Przypisz ciąg zdefiniowany przez użytkownika do przycisku tekstowego (przestarzałe) |
| gx_text_button_text_set_ext            | Przypisz ciąg zdefiniowany przez użytkownika do przycisku tekstowego              |
| gx_text_scroll_wheel_callback_set      | Przypisanie wywołania zwrotnego pobierania ciągu (przestarzałe)          |
| gx_text_scroll_wheel_callback_set_ext | Przypisanie wywołania zwrotnego pobierania ciągu                       |
| gx_text_scroll_wheel_create             | Tworzenie pokrętła przewijania tekstu podstawowego                          |
| gx_text_scroll_wheel_draw               | Funkcja rysowania kółka przewijania tekstu                  |
| gx_text_scroll_wheel_event_process      | Zdarzenie kółka przewijania tekstu procesu                        |
| gx_text_scroll_wheel_font_set          | Przypisz czcionki kółka przewijania tekstu                         |
| gx_text_scroll_wheel_text_color_set   | Przypisz kolory tekstu kółka przewijania tekstu                   |
| gx_tree_view_create                    | Cretae widok drzewa                          |
| gx_tree_view_draw                      | Rysuj widok drzewa                              |
| gx_tree_view_event_process            | Zdarzenie widoku drzewa procesów                     |
| gx_tree — view_indentation_set           | Ustawianie wcięć widoku drzewa                   |
| gx_tree_view_position                  | Elementy widoku drzewa pozycji                    |
| gx_tree_view_root_line_color_set    | Ustaw kolor linii głównej widoku drzewa               |
| gx_tree_view_root_pixelmap_set       | Ustaw katalog główny widoku drzewa pixelmaps                |
| gx_tree_view_selected_get             | Pobierz wybrany element                      |
| gx_tree_view_selected_set             | Ustaw wybrany element                           |
| gx_utility_canvas_to_bmp              | Konwertuj pamięć kanwy na format mapy bitowej      |
| gx_utility_circle_point_get           | Punkt obliczania na okręgu               |
| gx_utility_gradient_create             | Tworzenie Pixelmap gradientu                  |
| gx_utility_gradient_delete              | Usuwanie gradientu Pixelmap                  |
| gx_utility_ltoa                         | Konwertuj liczbę całkowitą na ASCII               |
| gx_utility_math_acos                   | Arcus cosinus łuku                          |
| gx_utility_math_asin                   | Arcus sinus łuku                             |
| gx_utility_math_cos                    | Cosinus obliczeń                              |
| gx_utility_math_sin                    | Oblicz sinus                                |
| gx_utility_math_sqrt                   | Pierwiastek kwadratowy obliczeń                         |
| gx_utility_bidi_paragraph_reorder         | Zmień kolejność tekstu dwukierunkowego w kolejności wyświetlania|
| gx_utility_bidi_resolved_text_info_delete | Usuń tekst zmiany kolejności               |
| gx_utility_pixelmap_resize             | Zmień rozmiar Pixelmap                             |
| gx_utility_pixelmap_rotate             | Obróć Pixelmap według dowolnego kąta          |
| gx_utility_pixelmap_simple_rotate      | Obróć Pixelmap o 90, 180, 270 stopni     |
| gx_utility_rectangle_center            | Wyśrodkuj prostokąt wewnątrz innego prostokąta   |
| gx_utility_rectangle_center_find      | Znajdź środek prostokąta                    |
| gx_utility_rectangle_combine           | Połącz dwa prostokąty w pierwszej kolejności           |
| gx_utility_rectangle_compare           | Porównaj dwa prostokąty                      |
| gx_utility_rectangle_define            | Zdefiniuj prostokąt                            |
| gx_utility_rectangle_resize            | Zmień rozmiar prostokąta                            |
| gx_utility_rectangle_overlap_detect   | Wykrywanie nakładania się prostokątów                |
| gx_utility_rectangle_point_detect     | Wykryj, czy punkt znajduje się w prostokącie        |
| gx_utility_rectangle_shift             | Prostokąt przesunięcia                             |
| gx_utility_string_to_alphamap         | Renderowanie ciągu tekstowego do alphamap (przestarzałe) |
| gx_utility_string_to_alphamap_ext    | Renderowanie ciągu tekstowego do alphamap              |
| gx_vertical_list_children_position    | Umieść elementy podrzędne na liście pionowej          |
| gx_vertical_list_create                | Utwórz listę pionową                        |
| gx_vertical_list_event_process        | Zdarzenie przetwarzania listy pionowej                 |
| gx_vertical_list_selected_index_get  | Pobierz indeks wybranego elementu                     |
| gx_vertical_list_selected_widget_get | Pobierz wybrany element widget                         |
| gx_vertical_list_selected_set         | Ustaw wpis na liście pionowej                  |
| gx_vertical_list_total_rows_set      | Zmień liczbę wierszy listy po utworzeniu   |
| gx_vertical_scrollbar_create           | Utwórz pionowy pasek przewijania                   |
| gx_widget_allocate                      | Dynamicznie Przydziel widżet               |
| gx_widget_attach                        | Dołącz widżet do elementu nadrzędnego                     |
| gx_widget_background_draw              | Rysuj tło elementu widget                      |
| gx_widget_back_attach                  | Dołącz widżet do tyłu                       |
| gx_widget_back_move                    | Przenieś widżet do tyłu                         |
| gx_widget_block_move                   | Przenieś blok pikseli                        |
| gx_widget_border_draw                  | Obramowanie elementu widget rysowania                          |
| gx_widget_border_style_set            | Ustaw styl obramowania widżetu                     |
| gx_widget_border_width_get            | Ustaw szerokość obramowania elementu widget                     |
| gx_widget_canvas_get               | Pobierz kanwę widżetu                                                         |
| gx_widget_child_detect             | Wykryj element podrzędny widgetu                                                       |
| gx_widget_children_draw            | Elementy podrzędne elementu widget rysowania                                                      |
| gx_widget_client_get               | Pobierz obszar klienta widżetu                                                    |
| gx_widget_color_get                | Rozpoznaj identyfikator koloru z wartością koloru dla widocznego widżetu                      |
| gx_widget_create                    | Utwórz widżet                                                             |
| gx_widget_created_test             | Testuj, czy element widget został utworzony                                                    |
| gx_widget_delete                    | Usuń widżet                                                             |
| gx_widget_detach                    | Odłącz widżet z elementu nadrzędnego                                                 |
| gx_widget_draw                      | Element widget rysowania                                                               |
| gx_widget_draw_set                 | Ustaw funkcję rysowania elementu widget                                               |
| gx_widget_event_generate           | Generuj zdarzenie widgetu                                                     |
| gx_widget_event_process            | Zdarzenie widżetu procesu                                                      |
| gx_widget_event_process_set       | Ustaw funkcję przetwarzania zdarzeń elementu widget                                   |
| gx_widget_event_to_parent         | Wyślij zdarzenie do elementu nadrzędnego widżetu                                             |
| gx_widget_fill_color_set          | Przypisz kolor wypełnienia widżetu                                                  |
| gx_widget_find                      | Znajdź widżet                                                               |
| gx_widget_first_child_get         | Zwróć wskaźnik do pierwszego elementu podrzędnego                                             |
| gx_widget_focus_next               | Przenieś fokus wprowadzania do następnego widgetu                                           |
| gx_widget_focus_previous           | Przenieś fokus wprowadzania do poprzedniego widgetu                                       |
| gx_widget_font_get                 | Rozpoznawanie identyfikatora czcionki do wskaźnika dla widocznego widżetu                    |
| gx_widget_free                      | Wolna pamięć blokowa formantu widget                                          |
| gx_widget_front_move               | Przenieś widżet do przodu                                                      |
| gx_widget_height_get               | Pobierz wysokość widżetu                                                         |
| gx_widget_hide                      | Ukryj widżet                                                               |
| gx_widget_last_child_get          | Zwróć wskaźnik do ostatniego elementu podrzędnego                                              |
| gx_widget_next_sibling_get        | Zwróć wskaźnik do następnego elementu równorzędnego                                            |
| gx_widget_parent_get               | Zwróć wskaźnik do elementu nadrzędnego widget                                           |
| gx_widget_pixelmap_get             | Rozpoznanie identyfikatora Pixelmap na wskaźniku Pixelmap dla widocznego widżetu            |
| gx_widget_previous_sibling_get    | Zwróć wskaźnik do poprzedniego elementu równorzędnego                                        |
| gx_widget_resize                    | Zmień rozmiar widżetu                                                             |
| gx_widget_shift                     | Widżet przesunięcia                                                              |
| gx_widget_show                      | Pokaż widżet                                                               |
| gx_widget_status_add               | Dodaj stan widżetu                                                         |
| gx_widget_status_get               | Pobierz flagi stanu widżetu                                              |
| gx_widget_status_remove            | Usuń stan widżetu                                                      |
| gx_widget_string_get               | Pobierz ciąg skojarzony z IDENTYFIKATORem ciągu dla widocznego widżetu (przestarzałe) |
| gx_widget_string_get_ext          | Pobierz ciąg skojarzony z IDENTYFIKATORem ciągu dla widocznego elementu widget.             |
| gx_widget_status_test              | Stan elementu widget testu                                                        |
| gx_widget_style_add                | Dodaj styl widżetu                                                          |
| gx_widget_style_get                | Pobierz flagi stylu widżetu                                               |
| gx_widget_style_remove             | Usuń styl widgetu                                                       |
| gx_widget_style_set                | Ustaw styl widżetu                                                          |
| gx_widget_text_blend               | Renderowanie mieszania tekstu nad widżetem (przestarzałe)                              |
| gx_widget_text_blend_ext          | Renderowanie mieszania tekstu nad widżetem                                           |
| gx_widget_text_draw                | Renderowanie tekstu nad widżetem (przestarzałe)                                      |
| gx_widget_text_draw_ext           | Renderowanie tekstu nad widżetem                                            |
| gx_widget_text_id_draw            | Renderowanie tekstu identyfikowanego za pomocą identyfikatora ciągu powyżej elementu widget                           |
| gx_widget_top_visible_child_find | Zwróć wskaźnik do widocznego elementu podrzędnego, który jest rysowany w górnej części porządku osi Z   |
| gx_widget_type_find                | Znajdź Typ widgetu                                                          |
| gx_widget_width_get                | Pobierz szerokość widżetu                                                          |
| gx_window_canvas_set               | Ustawianie kanwy okna                                                         |
| gx_window_client_height_get       | Pobierz wysokość klienta okna                                                  |
| gx_window_client_scroll            | Przewinięcie okna klientów                                                     |
| gx_window_client_width_get        | Pobierz szerokość klienta okna                                                   |
| gx_window_close                     | Zakończ wykonywanie okna modalnego                                          |
| gx_window_create                    | Utwórz okno                                                             |
| gx_window_draw                      | Okno rysowania                                                               |
| gx_window_event_process            | Zdarzenie okna procesu                                                      |
| gx_window_execute                   | Wykonywanie okna modalnego                                                    |
| gx_window_root_create              | Utwórz okno główne                                                        |
| gx_window_root_delete              | Zniszcz okno główne                                                       |
| gx_window_root_event_process      | Przetwarzaj zdarzenie dla okna głównego                                             |
| gx_window_root_find                | Znajdź okno główne                                                          |
| gx_window_scroll_info_get         | Pobierz informacje przewijania okna                                                    |
| gx_window_scrollbar_find           | Znajdź pasek przewijania okna                                                     |
| gx_window_wallpaper_get            | Pobierz tapetę okna                                                      |
| gx_window_wallpaper_set            | Ustaw tapetę okna                                                      |

## <a name="gx_accordion_menu_create"></a>gx_accordion_menu_create

Tworzenie menu przyznanego

### <a name="prototype"></a>Prototype

```C
UINT gx_accordion_menu_create(
    GX_ACCORDION_MENU *accordion,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    ULONG style ,
    USHORT accordion_menu_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy menu harmonijka zgodnie z określonym i dołącza menu harmonijka do podanego widżetu nadrzędnego. Menu harmonijka to anexpanding/zwijanie menu wyświetlania. Akceptuje wszystkie typy widżetów jako elementy menu podrzędnego. Menu uzależnione mogą być zagnieżdżane, co oznacza, że można utworzyć kilka poziomów głębokości menu.

Aby wstawić element podrzędny do widżetu elementu menu, zaleca się GX_MENU touse typu widżet jako element menu nadrzędnego.

Porady dotyczące tworzenia menu z uwzględnieniem jednego poziomu:

1.  Utwórz menu zgodnie z przepisami.

2.  Dołącz widżety typu GX_MENU do menu wytycznymi.

3.  Dołącz podrzędne elementy widget do GX_MENU typu nadrzędnego. Typ elementu podrzędnego może być dowolnym typem widgetu GUIX.

Porady dotyczące tworzenia menu rozmieszczonych na wiele poziomów:

1.  Utwórz menu zgodnie z przepisami.

2.  Dołącz widżety typu GX_MENU do menu wytycznymi.

3.  Dołącz widżet typu GX_ACCORDION_MENU do elementu nadrzędnego typu GX_MENU.

4.  Dołącz elementy menu do elementu nadrzędnego typu GX_ACCORDION_MENU, zgodnie z opisem w temacie Tworzenie menu z uwzględnieniem jednego poziomu.

### <a name="parameters"></a>Parametry

- **zgodnie z przepisami** Blok kontrolny menu z przydziałem
- **Nazwa** Nazwa menu przyznanego
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **styl** Styl elementu widget. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **accordion_menu_id** Zdefiniowany przez aplikację identyfikator menu wystawcy
- **rozmiar** Rozmiar menu przyznanego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne utworzenie menu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_ACCORDION_MENU my_accordion;
GX_MENU menu_1;
GX_MENU item_1;
GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 100, 100, 300, 150);

status = gx_accordion_menu_create(&my_accordion, “my_accordion”,
                                  parent, GX_STYLE_ENABLED,
                                  MY_ACCORDION_ID, &size);

gx_menu_create(&menu_1, “menu_1”, &my_accordion,
               GX_STRING_ID_MENU_1, GX_ID_NONE,
               GX_STYLE_ENABLED | GX_TYLE_BORDER_THIN, 0, &size);

gx_menu_create(&item_1, “item_1”, &my_accordion,
               GX_STRING_ID_ITEM_1, GX_ID_NONE,
               GX_STYLE_ENABLED | GX_STYLE_BORDER_THIN, 0, &size);

gx_text_offset_set(&item_1, 30, 0);

gx_menu_insert(&menu_1, &item_1);

/* If status is GX_SUCCESS the accordion menu was successfully created. */

```

Aplikacja demonstracyjna demo_guix_widget_types, dostępna jako część instalacji programu GUIX Studio, zawiera kompletny przykład użycia widżetu menu harmonijka.

### <a name="see-also"></a>Zobacz też

- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_draw"></a>gx_accordion_menu_draw

Menu Rysuj zgodnie z przepisami

### <a name="prototype"></a>Prototype

```C
VOID gx_accordion_menu_draw(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>Opis

Ta usługa rysuje określone menu zgodnie z ustawieniami. Ta usługa jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest dostępna dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania dla widżetów menu.

### <a name="parameters"></a>Parametry

- **zgodnie z przepisami** Blok kontrolny menu z przydziałem

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Define a custom accordion menu draw function */

VOID my_accordion_menu_draw(GX_ACCORDION_MENU *accordion)
{
    /* Call default accordion menu draw. */
    gx_accordion_menu_draw(accordion);

    /* Add custom drawing here. */
}

```

### <a name="see-also"></a>Zobacz też

- gx_accordion_menu_create
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_event_process"></a>gx_accordion_menu_event_process

Zdarzenie menu zgodnie z procesem

### <a name="prototype"></a>Prototype

```C
UINT gx_accordion_menu_event_process(
    GX_ACCORDION_MENU *accordion, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego menu. Ta usługa powinna być wywoływana jako domyślna procedura obsługi zdarzeń przez wszelkie niestandardowe funkcje przetwarzania zdarzeń menu.

Ta usługa obsługuje zdarzenia GX_EVENT_PEN_DOWN i GX_EVENT_PEN_UP, aby rozwijać/zwijać element menu.

### <a name="parameters"></a>Parametry

- **zgodnie z przepisami** Blok kontrolny menu z przydziałem
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia menu w przypadku pomyślnego **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic accordion menu event processing as part of custom event processing function. */

UINT custom_accordion_event_process( 
    GX_ACCORDION_MENU *accordion,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default accordion menu
            event processing */
        status =
        gx_accordion_menu_event_process(accordion, event);
        break;
    }
    return status;
}

```

### <a name="see-also"></a>Zobacz też

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_accordion_menu_position"></a>gx_accordion_menu_position

Pozycje menu pozycji

### <a name="prototype"></a>Prototype

```C
UINT gx_accordion_menu_position(GX_ACCORDION_MENU *accordion);
```

### <a name="description"></a>Opis

Ta usługa umieszcza elementy menu w menu przyjmowane. Ta funkcja jest zwykle wywoływana wewnętrznie, gdy stają się widoczne menu. Jeśli chcesz wstawić/usunąć elementy do/z menu wystawcy lub zmienić style rozwinięte elementu podrzędnego, ta funkcja powinna być wywoływana w celu zmiany położenia elementów podrzędnych.

### <a name="parameters"></a>Parametry

- **zgodnie z przepisami** Blok kontrolny menu z przydziałem

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna pozycja menu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Position menu items in the accordion menu “my_accordion” */
status = gx_accordion_menu_position (&my_accordion);

/* If status is GX_SUCCESS the children in the accordion menu
“my_accordion” are positioned. */

```

### <a name="see-also"></a>Zobacz też

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_animation_canvas_define"></a>gx_animation_canvas_define

Udostępnianie pamięci kanwy kontrolerowi animacji

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_canvas_define(
    GX_ANIMATION *animation, 
    GX_CANVAS *canvas);
```

### <a name="description"></a>Opis

Ta usługa udostępnia kanwę pamięci do kontrolera animacji, który służy do implementowania sekwencji animacji. Ta udostępniona Kanwa powinna być wystarczająco duża, aby pomieścić widżet docelowy animacji.

Gdy Kanwa animacji jest zdefiniowana, widżet docelowy jest rysowany raz na tej kanwie animacji, a slajd ekranu lub efekt zaniku jest realizowany przez modyfikację przesunięcia kanwy i/lub wartości alfa kanwy. Gdy zapewniona jest obsługa sprzętu dla wielu warstw graficznych, Definiowanie kanwy animacji powiązanej z sprzętową warstwą nakładki grafiki może ***znacznie*** poprawić wydajność animacji slajdów i zanikania.

Menedżer animacji wymaga kanwy animacji, aby można było wykonywać zanikanie i Ściemnianie typów animacji w przypadku uruchamiania na głębokości koloru mniejszej niż 16 BPP.

### <a name="parameters"></a>Parametry

- **animacja** Wskaźnik do bloku sterowania animacją
- **Kanwa** Kanwa pamięci użyta do zaimplementowania animacji translacji.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie zdefiniowana Kanwa animacji
- **GX_INVALID_STATUS** (0X10) nieprawidłowy stan animacji
- **GX_INVALID_MEMORY_SIZE** (0x29) podany blok pamięci nie jest wystarczająco duży, aby można było utworzyć kanwę
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_ANIMATION animation;
GX_CANVAS animation_canvas;
GX_ROOT_WINDOW animation_root;
/* Create animation canvas. */
status = gx_canvas_create(
        &animation_canvas, /* Canvas control block. */
        “animation_canvas”, /* Name of canvas. */
        display, /* Display control block. */
        GX_ANIMATION_MANAGED, /* Type of canvas. */
        width, /* Width of canvas. */
        height, /* Height of canvas. */
        memory_area, /* Memory area of canvas. */
        memory_size /* Size of canvas memory. */
        );
if (status == GX_SUCCESS)
{
    /* Create the root window for the canvas. */
    status = gx_window_root_create(
        &animation_root, /* Root window control block. */
        “animation_root”, /* Name of root window. */
        &animation_canvas, /* Canvas of the root window. */ GX_STYLE_NONE, /* Style of the window. */
        GX_ID_NONE, /* Root window ID. */
        &root_size /* Window size. */
        );
}
if (status == GX_SUCCESS)
{
    /* Define canvas for the animation. */
    status = gx_animation_canvas_define(&animation,
                &animation_canvas);
}
/* If status is GX_SUCCESS the new canvas was successfully set to the animation manager. */

```

### <a name="see-also"></a>Zobacz też

- gx_animation_create,
- gx_animation_delete
- gx_animation_drag_disable,
- gx_animation_drag_enable
- gx_animation_landing_speed_set,
- gx_animation_start
- gx_animation_stop

## <a name="gx_animation_create"></a>gx_animation_create

Tworzenie kontrolera animacji

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_create(GX_ANIMATION *animation);
```

### <a name="description"></a>Opis

Ta usługa tworzy kontroler animacji. Kontroler jest zainicjowany do stanu bezczynności. Jeden nie może rozpocząć animacji, chyba że jest w stanie bezczynności. GX_ANIMATION wskaźnik bloku sterowania można uzyskać przy użyciu gx_system_animation_get () lub może być statycznie zdefiniowanym blokiem sterowania.

### <a name="parameters"></a>Parametry

- **animacja** Wskaźnik do bloku sterowania animacją


### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzył kontroler animacji
- Blok sterowania **GX_ALREADY_CREATED** (0x13) jest już zainicjowany
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_ANIMATION *animation;

/* Allocate an animaton control from system pool */
gx_system_animation_get(&animation);

/* Initialize the control block */

if (animation)
{
    status = gx_animation_create(&animation);
}

/* If status is GX_SUCCESS the new animation controller was successfully created and initialized. */

```

### <a name="see-also"></a>Zobacz też

- gx_animation_canvas_define,
- gx_animation_delete
- gx_animation_drag_disable,
- gx_animation_drag_enable
- gx_animation_start
- gx_animation_landing_speed_set,
- gx_animation_stop
- gx_system_animation_get
- gx_system_animation_free

## <a name="gx_animation_drag_disable"></a>gx_animation_drag_disable

Wyłącz hak animacji przeciągnięcia ekranu

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_drag_disable(
    GX_ANIMATION *animation, 
    GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa usuwa procedurę haka animacji przeciągnięcia ekranu z domyślnej funkcji procesu zdarzeń widżetu i przerywa sekwencję animacji. Procedura przeciągania animacji przeciągnięcia ekranu przechwytuje zdarzenia dla animacji przeciągnięcia ekranu.

### <a name="parameters"></a>Parametry

- **animacja** Wskaźnik do bloku sterowania animacją
- element **widget** Wskaźnik do bloku kontrolki elementu widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) powiodło się
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_ANIMATION animation;
GX_WIDGET *animation_parent;

/* Disable screen drag animation of “animation_parent”. */
status = gx_animation_drag_disable(&animation, animation_parent);

/* If status is GX_SUCCESS the screen drag hook has been removed
    from the event process of “animation_parent”. */

```

### <a name="see-also"></a>Zobacz też

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_enable
- gx_animation_landing_speed_set,
- gx__animation_start
- gx_animation_stop
- gx_system_animation_get,
- gx__system_animation_free

## <a name="gx_animation_drag_enable"></a>gx_animation_drag_enable

Włącz hak animacji przeciągnięcia ekranu

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_drag_enable(
    GX_ANIMATION *animation,
    GX_WIDGET *widget, 
    GX_ANIMATION_INFO *info);
```

### <a name="description"></a>Opis

Ta usługa ustawia wewnętrznie zdefiniowane przez funkcję przeciąganie animacji przeciągnięcia, funkcja jako procedurę punktu zaczepienia funkcji domyślnego procesu zdarzeń elementu widget. Funkcja przetwarzania zdarzeń animacji przeciągnięcia ekranu przechwytuje zdarzenia dla animacji przeciągnięcia ekranu.

Procedura przeciągania przeciągnięcia ekranu jest domyślną obsługą dla zdarzeń wejściowych pióra wysyłanych do docelowego elementu widget. Oryginalna funkcja przetwarzania zdarzeń widżetu jest wywoływana w sposób łańcuchowy po sprawdzeniu typów zdarzeń wejściowych przeciągania ekranu.

### <a name="parameters"></a>Parametry

- **animacja** Wskaźnik do bloku sterowania animacją
- element **widget** Wskaźnik do bloku kontrolki elementu widget
- **informacje** Informacje o animacji

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) powiodło się
- **GX_INVALID_STATUS** (0X26) nieprawidłowy stan animacji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa wartość
- Nie podano listy ekranu slajdu **GX_INVALID_WIDGET** (0x12)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_ANIMATION animation;
GX_ANIMATION_INFO info;
GX_WIDGET *animation_parent;
GX_WIDGET *screen_list[] = {
    screen_1,
    screen_2,
    screen_3,
    GX_NULL
}

memset(&info, 0, sizeof(GX_ANIMATION_INFO);
info.gx_animation_parent = animation_parent;

/* If GX_STYLE_ANIMATION_WRAP is set, the screen list will wrap itself. */
info.gx_animation_style = GX_ANIMATION_SCREEN_DRAG |
                          GX_ANIMATION_HORIZONTAL |
                          GX_STYLE_ANIMATION_WRAP;
info.gx_animation_frame_interval = 1;
info.gx_animation_slide_screen_list = screen_list;

status = gx_animation_drag_enable(&animation, animation_parent,
                                  info);

/* If status is GX_SUCCESS the screen slide animinatin event
    process function has been set as a hook procedure of
    “animation_parent”. */
```

### <a name="see-also"></a>Zobacz też

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_disable,
- gx__animation_landing_speed_set
- gx_animation_start,
- gx__animation_stop,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_animation_landing_speed_set"></a>gx_animation_landing_speed_set

Ustaw szybkość wyładunku dla animacji przeciągania ekranu

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_landing_speed_set(
    GX_ANIMATION *animation, 
    USHORT shift_per_step);
```

### <a name="description"></a>Opis

Ta usługa ustawia szybkość wyładowania dla animacji przeciągania ekranu.

### <a name="parameters"></a>Parametry

- **animacja** Wskaźnik do bloku sterowania animacją
- **shift_per_step** Odległość między kolejnymi krokami

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) powiodło się
- **GX_INVALID_VALUE** (0X22) nieprawidłowy parametr

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set landing speed of “my_animation” to 20. */
status = gx_animation_landing_peed_set(&my_animation, 20);

/* If status is GX_SUCCESS the landing speed is successfully set to 20. */
```

### <a name="see-also"></a>Zobacz też

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_slide_disable,
- gx__animation_slide_enable
- gx_animation_start,
- gx__animation_stop,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_animation_start"></a>gx_animation_start

Uruchom animację opartą na czasomierzu

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_start(
    GX_ANIMATION *animation, 
    GX_ANIMATION_INFO *params);
```

### <a name="description"></a>Opis

Ta usługa inicjuje sekwencję animacji przy użyciu wcześniej utworzonego wystąpienia animacji i nowego zestawu parametrów animacji. Ta funkcja tworzy lokalną kopię parametrów, co oznacza, że struktura parametrów nie musi być zdefiniowana statycznie.

Struktura formantów GX_ANIMATION może być zdefiniowana statycznie przez aplikację lub można ją uzyskać przy użyciu interfejsu API gx_system_animation_get ().

Struktura GX_ANIMATION_INFO definiuje parametry animacji, która ma zostać wykonana. Pełny opis tej struktury i znaczenie każdego pola można znaleźć w sekcji składnika animacji GUIX w rozdziale 3 tego podręcznika.

### <a name="parameters"></a>Parametry

- **animacja** Wskaźnik do bloku sterowania animacją
- **Parametry** Wskaźnik do struktury parametrów

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) powiodło się
- **GX_INVALID_VALUE** (0X22) nieprawidłowy parametr
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy element docelowy animacji
- **GX_INVALID_STATUS** (0X26) nieprawidłowy stan animacji
- **GX_INVALID_CANVAS** (0X20) Nieprawidłowa Kanwa animacji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_ANIMATION_INFO params;
GX_ANIMATION *animation;

/* obtain an animation control block pointer */
gx_system_animation_get(&animation);
if (animation)
{
    /* define a slide down and to the right */
    params.gx_animation_start_position.gx_point_x = 0;
    params.gx_animation_start_position.gx_point_y = 0;
    params.gx_animation_end_position.gx_point_x = 100;
    params.gx_animation_end_position.gx_point_y = 200;
    params.gx_animation_style= GX_ANIMATION_TRANSLATE;
    params.gx_animation_target = &my_window;
    params.gx_animation_parent = root_window;
    params.gx_animation_start_alpha = 255;
    params.gx_animation_end_alpha = 255;

    params.gx_animation_delay_before = 0;
    params.gx_animation_steps = 10;
    params.gx_animation_tick_rate = 2;

    status = gx_animation_start(&animation, &params);
}

/* If status is GX_SUCCESS the animation is initiated. */
```

### <a name="see-also"></a>Zobacz też

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_slide_disable,
- gx__animation_slide_enable
- gx_animation_landing_speed_set,
- gx__animation_stop
- gx_system_animation_get,
- gx__system_animation_free

## <a name="gx_animation_stop"></a>gx_animation_stop

Zatrzymaj aktywną animację opartą na czasomierzu

### <a name="prototype"></a>Prototype

```C
UINT gx_animation_stop(GX_ANIMATION *animation);
```

### <a name="description"></a>Opis

Zatrzymaj wcześniej uruchomioną animację. Jeśli wskaźnik bloku kontrolki animacji został przydzielony przy użyciu gx_system_animation_get, aplikacja może ponownie użyć bloku sterowania lub zwrócić go do puli systemu przy użyciu gx_system_animation_free ().

### <a name="parameters"></a>Parametry

- **animacja** Wskaźnik do bloku sterowania animacją

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) pomyślna GX_PTR_ERROR (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_STATUS** (0X26) nieprawidłowy stan kontrolera

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_ANIMATION animation;

status = gx_animation_stop(&animation);

/* If status is GX_SUCCESS the animation is stopped */

```

### <a name="see-also"></a>Zobacz też

- gx_animation_canvas_define,
- gx__animation_create
- gx_animation_drag_disable,
- gx__animation_drag_enable
- gx_animation_start,
- gx__system_animation_get
- gx_system_animation_free

## <a name="gx_binres_language_count_get"></a>gx_binres_language_count_get

Zwróć liczbę języków znajdujących się w danych zasobów binarnych

### <a name="prototype"></a>Prototype

```C
UINT gx_binres_language_count_get(
    GX_UBYTE *root_address, 
    GX_VALUE *returned_count);
```

### <a name="description"></a>Opis

Ta usługa analizuje binarny nagłówek danych zasobu, aby zwracał liczbę języków zawartych w danych binarnych. Jest to przydatne w przypadku aplikacji, które muszą wyświetlać listę wyboru dla użytkownika zezwalającą użytkownikowi na wybór z wybranych języków.

### <a name="parameters"></a>Parametry

- **root_address** Adres danych zasobów binarnych w pamięci
- **return_count** Lokalizacja do przechowywania zwróconej liczby języków

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) powiodło się
- **GX_INVALID_FORMAT** (0X24) nieprawidłowy zasób binarny
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_VALUE language_count = 0;

/* Specify address that binary resource data is located. */
GX_UBYTE    *root_address = 0x60000000;

status = gx_binres_language_count_get(root_address,
    &language_count);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Zobacz też

- gx_binres_language_info_load

## <a name="gx_binres_language_info_load"></a>gx_binres_language_info_load

Załaduj informacje o tabeli języka

### <a name="prototype"></a>Prototype

```C
UINT gx_binres_language_info_load(
    GX_UBYTE *root_address, 
    GX_LANGUAGE_HEDAER *put_info);
```

### <a name="description"></a>Opis

Ta usługa analizuje obiekt BLOB danych zasobów binarnych, aby wypełnić tablicę struktur GX_LANGUAGE_HEADER, informując o nazwach języka i rozmiarze tabeli ciągów każdego języka zawartego w danych binarnych. Aplikacja powinna najpierw wywołać gx_binres_language_count_get (), aby określić liczbę języków w danych binarnych i upewnić się, że wskaźnik put_info przeszedł do tej funkcji wskazuje tablicę struktur language_count GX_LANGUAGE_HEADER.

Ta usługa jest używana przez aplikację do określenia w czasie wykonywania zawartości binarnego fragmentu danych zasobu.

Struktura GX_LANGUAGE_HEADER jest definiowana jako:

```c
typedef struct GX_LANGUAGE_HEADER_STRUCT{
    USHORT gx_language_header_magic_number;
    USHORT gx_language_header_index;
    UCHAR gx_language_header_name[GX_LANGUAGE_HEADER_NAME_SIZE];
    ULONG  gx_language_header_data_size;
} GX_LANGUAGE_HEADER;
```

- Pole *magic_number* służy do wewnętrznej weryfikacji binarnego formatu danych zasobów.
- Pole *header_index* wskazuje kolejność, w jakiej języki są zdefiniowane w danych binarnych.
- Pole *header_name* zawiera nazwę języka.
- Pole *header_data_size* zawiera rozmiar danych tabeli ciągów języka.

### <a name="parameters"></a>Parametry

- **root_address** Adres danych zasobów binarnych w pamięci
- **put_info** Wskaźnik do tablicy struktur GX_LANGUAGE_HEADER

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) powiodło się
- **GX_INVALID_FORMAT** (0X24) nieprawidłowy zasób binarny
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_LANGUAGE_HEADER language_info[4];

/* Specify address that binary resource data is located. */
GX_UBYTE    *root_address = 0x60000000;

status = gx_binres_language_info_load(root_address,
    language_info);
/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Zobacz też

- gx_binres_language_count_get

## <a name="gx_binres_language_table_load"></a>gx_binres_language_table_load

Załaduj zasób tabeli języka (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_binres_language_table_load(
    GX_UBYTE *root_address, 
    GX_UBYTE **returned_language_table);
```

### <a name="description"></a>Opis

Ten przestarzały interfejs API umożliwia aplikacjom ładowanie danych tabeli ciągów ze starszych (starszych niż Release 5,6) plików danych zasobów binarnych.

Nowe aplikacje powinny używać gx_binres_language_table_load_ext ().

Ta usługa kompiluje strukturę tabeli języka zawierającą wskaźniki do zasobów tabeli, wygenerowana struktura danych wskazuje na dane zasobów "w miejscu", nie kopiuje danych zasobów. Dane zasobu muszą być umieszczone w ogólnej lokalizacji pamięci, a adres podstawowy tej lokalizacji pamięci jest przesyłany do tego interfejsu API.

Ta usługa wymaga wystarczającej ilości pamięci przydzielony przez środowisko uruchomieniowe, aby można było przechowywać strukturę tabeli języka, a w związku z tym gx_system_memory_allocator_set interfejs API musi zostać wywołany raz przed zażądaniem tej usługi.

Tabela zwracanych języków definiuje co najmniej jedną tabelę zawierającą ciąg (y), w której każda tabela ciągów zawiera wskaźniki do zasobów ciągów w pamięci danych zasobów.

### <a name="parameters"></a>Parametry

- **root_address** Adres danych zasobów binarnych w pamięci
- **zwrócono _language_table** Wskaźnik do załadowanej tabeli języka

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) powiodło się
- **GX_INVALID_FORMAT** (0X24) nieprawidłowy zasób binarny
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Nie zdefiniowano programu przydzielania pamięci **GX_SYSTEM_MEMPRY_ERROR** (0x30) lub funkcji bezpłatnej

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_UBYTE ***language_table = GX_NULL;

/* Specify address that binary resource data is located. */
GX_UBYTE *root_address = 0x60000000;

status = gx_binres_language_table_load(root_address,
                                        &language_table);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Zobacz też

- gx_binres_language_table_load_ext

## <a name="gx_binres_language_table_load_ext"></a>gx_binres_language_table_load_ext

Załaduj zasób tabeli języka

### <a name="prototype"></a>Prototype

```C
UINT gx_binres_language_table_load_ext(
    GX_UBYTE *root_address, 
    GX_STRING **returned_language_table);
```

### <a name="description"></a>Opis

Ta usługa kompiluje strukturę tabeli języka zawierającą wskaźniki do zasobów tabeli, wygenerowana struktura danych wskazuje na dane zasobów "w miejscu", nie kopiuje danych zasobów. Dane zasobu muszą być umieszczone w ogólnej lokalizacji pamięci, a adres podstawowy tej lokalizacji pamięci jest przesyłany do tego interfejsu API.

Ta usługa wymaga wystarczającej ilości pamięci przydzielony przez środowisko uruchomieniowe, aby można było przechowywać strukturę tabeli języka, a w związku z tym gx_system_memory_allocator_set interfejs API musi zostać wywołany raz przed zażądaniem tej usługi.

Tabela zwracanych języków definiuje co najmniej jedną tabelę zawierającą ciąg (y), w której każda tabela ciągów zawiera wskaźniki do zasobów ciągów w pamięci danych zasobów.

### <a name="parameters"></a>Parametry

- **root_address** Adres danych zasobów binarnych w pamięci
- **zwrócono _language_table** Wskaźnik do załadowanej tabeli języka

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) powiodło się
- **GX_INVALID_FORMAT** (0X24) nieprawidłowy zasób binarny
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Nie zdefiniowano programu przydzielania pamięci **GX_SYSTEM_MEMPRY_ERROR** (0x30) lub funkcji bezpłatnej

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING **language_table = GX_NULL;

/* Specify address that binary resource data is located. */
GX_UBYTE *root_address = 0x60000000;

status = gx_binres_language_table_load_ext(root_address,
                                            &language_table);

/* If status is GX_SUCCESS, the language table was successfully loaded. */

```

### <a name="see-also"></a>Zobacz też

- gx_binres_theme_load

## <a name="gx_binres_theme_load"></a>gx_binres_theme_load

Załaduj zasób motywu

### <a name="prototype"></a>Prototype

```C
UINT gx_binres_theme_load(
    GX_UBYTE *root_address, 
    INT theme_id, GX_THEME **returned_theme);
```

### <a name="description"></a>Opis

Ta usługa kompiluje strukturę GX_THEME zawierającą wskaźniki do tabel zasobów dla żądanego motywu. Wygenerowane struktury danych wskazują na dane zasobów "w miejscu", nie kopiuje danych zasobu. W związku z tym dane zasobów muszą być umieszczone w ogólnej lokalizacji pamięci, a adres podstawowy tej lokalizacji jest przesyłany do tego interfejsu API.

Ta usługa wymaga wystarczającej ilości pamięci przydzielonym przez środowisko uruchomieniowe, aby można było przechowywać strukturę tabeli kompozycji i dlatego gx_system_memory_allocator_set interfejs API musi zostać wywołany raz przed zażądaniem tej usługi.

### <a name="parameters"></a>Parametry

- **root_address** Adres danych zasobów binarnych w pamięci
- **theme_id** Identyfikator motywu
- **returned_theme** Wskaźnik do załadowanego motywu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) powiodło się
- **GX_INVALID_FORMAT** (0X24) nieprawidłowy zasób binarny
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE** (0X22) Nieprawidłowy identyfikator motywu
- Nie zdefiniowano programu przydzielania pamięci **GX_SYSTEM_MEMORY_ERROR** (0x30) lub funkcji bezpłatnej

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR *theme = GX_NULL;
GX_UBYTE *root_address = 0x60000000;
INT theme_id = 0;

status = gx_binres_theme_load(root_address, theme_id, &theme);

/* If status is GX_SUCCESS, the theme was successfully loaded. */
```

### <a name="see-also"></a>Zobacz też

- gx_binres_language_table_read

## <a name="gx_brush_default"></a>gx_brush_default
Ustawianie domyślnego pędzla

### <a name="prototype"></a>Prototype

```C
UINT gx_brush_default(GX_BRUSH *brush);
```

### <a name="description"></a>Opis

Ta usługa ustawia pędzle dla bieżącego kontekstu do wartości domyślnej systemu.

### <a name="parameters"></a>Parametry
- **pędzel** Wskaźnik do bloku kontrolki pędzla.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna definicja pędzla **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik pędzla

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/*Reset the brush to its default value. */
status = gx_brush_default(&my_brush);

/* If status is GX_SUCCESS the brush was successfully reset to its default value. */

```

### <a name="see-also"></a>Zobacz też

- gx_brush_define


## <a name="gx_brush_define"></a>gx_brush_define
Definiowanie pędzla

### <a name="prototype"></a>Prototype

```C
UINT gx_brush_define(
    GX_BRUSH *brush, 
    GX_COLOR line_color, 
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>Opis

Ta usługa definiuje pędzel z określonym kolorem linii, kolorem wypełnienia i stylem.

### <a name="parameters"></a>Parametry

- **pędzel** Wskaźnik do bloku kontrolki pędzla
- **line_color** Kolor linii pędzla. **Dodatek A** zawiera wstępnie zdefiniowane kolory. Należy pamiętać, że aplikacja może również dodać kolory niestandardowe.
- **fill_color** Kolor wypełnienia pędzla. **Dodatek A** zawiera wstępnie zdefiniowane kolory. Należy pamiętać, że aplikacja może również dodać kolory niestandardowe.
- **styl** Styl pędzla. **Dodatek D** zawiera opis obsługiwanych stylów pędzla. Style pędzla można łączyć w jedną zmienną przy użyciu funkcji bitowej lub operacji.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna definicja pędzla **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik pędzla

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Define a brush. */
status = gx_brush_define(&my_brush, GX_COLOR_BLACK, GX_COLOR_BLACK,
                         GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the brush was successfully created. */
```

### <a name="see-also"></a>Zobacz też

- gx_brush_default

## <a name="gx_button_background_draw"></a>gx_button_background_draw

 Rysuj tło przycisku

###<a name="prototype"></a>Prototype

```C
VOID gx_button_background_draw(GX_BUTTON *button);
```

### <a name="description"></a>Opis

Ta usługa rysuje tło przycisku. Ta funkcja jest zwykle wywoływana wewnętrznie przez funkcję gx_button_draw, ale jest dostępna dla aplikacji, aby pomóc w tworzeniu niestandardowych funkcji rysowania.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
VOID custom_button_draw(GX_BUTTON *button)
{
    /* Draw button background. */
    gx_button_background_draw(button);

    /* Add custom drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)button);
}
```

### <a name="see-also"></a>Zobacz też

- gx_button_create,
- gx__button_deselect,
- gx__button_draw
- gx_button_event_process,
- gx__button_select
- gx_icon_button_create,
- gx__pixelmap_button_create
- gx_pixelmap_button_draw,
- gx__radio_button_create
- gx_radio_button_draw,
- gx__text_button_create
- gx_text_button_color_set,
- gx__text_button_draw

## <a name="gx_button_create"></a>gx_button_create

Przycisk Utwórz

### <a name="prototype"></a>Prototype

```C
UINT gx_button_create(
    GX_BUTTON *button, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    ULONG style, 
    USHORT button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy określony przycisk i kojarzy przycisk z podanym widżetem nadrzędnym.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku
- **Nazwa** Logiczna nazwa przycisku
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget przycisku
- **styl** Styl przycisku. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **button_id** Zdefiniowany przez aplikację identyfikator przycisku
- **rozmiar** Rozmiar przycisku

### <a name="return-values"></a>Wartości zwrócone

- Tworzenie przycisku pomyślnego **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_BUTTON my_top_button;

/* Create a stop button. */
status = gx_button_create(&my_stop_button, "my stop button",
                            &my_parent_window,
                            GX_STYLE_BUTTON_TOGGLE,
                            MY_STOP_BUTTON_ID, &size);

/* If status is GX_SUCCESS the stop button was successfully created. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw,
- gx_button_deselect,
- gx_button_draw
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_deselect"></a>gx_button_deselect


Przycisk Anuluj wybór

### <a name="prototype"></a>Prototype

```C
UINT gx_button_deselect(
    GX_BUTTON *button, 
    GX_BOOL gen_event);
```

### <a name="description"></a>Opis

Ta usługa dewybiera określony przycisk i generuje zdarzenie sygnału w zależności od stylów przycisków.


| Styl przycisku              | Wysłać                     |
|---------------------------|----------------------------|
| Brak                      | GX_EVENT_CLICKED         |
| GX_STYLE_BUTTON_RADIO  | GX_EVENT_RADIO_DESELECT |
| GX_STYLE_BUTTON_TOGGLE | GX_EVENT_TOGGLE_OFF     |



### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku
- **gen_event** Jeśli GX_TRUE, przycisk spowoduje wygenerowanie zdarzenia GX_EVENT_CLICKED, GX_EVENT_DESELECT lub GX_EVENT_TOGGLE_OFFSET w zależności od stylu przycisku. Jeśli GX_FALSE, przycisk nie będzie generował żadnego zdarzenia wyższego poziomu nawet wtedy, gdy będzie to normalne.

### <a name="return-values"></a>Wartości zwrócone

- Usuń zaznaczenie przycisku pomyślnego **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Deselect button. */
status = gx_button_deselect(&my_stop_button, GX_TRUE);

/* If status is GX_SUCCESS the stop button was successfully deselected. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw,
- gx_button_create,
- gx_button_draw
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_button_draw"></a>gx_button_draw

Przycisk rysowania

### <a name="prototype"></a>Prototype

```C
VOID gx_button_draw(GX_BUTTON *button);
```

### <a name="description"></a>Opis

Ta usługa Rysuje określony przycisk. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest dostępna dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania dla widżetów przycisków niestandardowych.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom button draw function. */
VOID custom_button_draw(GX_BUTTON *button)
{
    /* Call default button draw. */
    gx_button_draw(button);

    /* Add custom drawing here. */
}

```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_event_process,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_event_process"></a>gx_button_event_process


Zdarzenie przycisku procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_button_event_process(
    GX_BUTTON *button, 
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego przycisku.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia pomyślnego przycisku **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic button event processing as part of custom event processing function. */

UINT custom_button_event_process(GX_BUTTON *button,
                                 GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default button
            event processing */
        status = gx_button_event_process(button, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_draw,
- gx_button_select
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set,
- gx_text_button_draw

## <a name="gx_button_select"></a>gx_button_select

Przycisk Wybierz

### <a name="prototype"></a>Prototype

```C
UINT gx_button_select(GX_BUTTON *button);
```

### <a name="description"></a>Opis

Ta usługa wybiera określony przycisk i generuje zdarzenie sygnału w zależności od stylów przycisków.

Dewybiera elementy równorzędne dla grupy przycisków radiowych.

| Styl przycisku                       | Wysłać                   |
|------------------------------------|--------------------------|
| GX_STYLE_BUTTON_RADIO           | GX_EVENT_RADIO_SELECT |
| GX_STYLE_BUTTON_EVENT_ON_PUSH | GX_EVENT_CLICKED       |
| GX_STYLE_BUTTON_TOGGLE          | GX_EVENT_TOGGLE_ON    |


### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku

### <a name="return-values"></a>Wartości zwrócone

- Przycisk pomyślnego wyboru **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Select button. */
status = gx_button_select(&my_stop_button);

/* If status is GX_SUCCESS the stop button was successfully selected. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw,
- gx_button_create
- gx_button_deselect,
- gx_button_draw,
- gx_button_event_process
- gx_radio_button_create,
- gx_radio_button_draw
- gx_icon_button_create,
- gx_pixelmap_button_create
- gx_pixelmap_button_draw,
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_canvas_alpha_set"></a>gx_canvas_alpha_set

Ustaw wartość alfa-Blend dla kanwy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_alpha_set(
    GX_CANVAS *canvas, 
    GX_UBYTE alpha);
```

### <a name="description"></a>Opis

Ta usługa ustawia wartość alfa-Blend dla określonej kanwy. Wartości alfa kanwy mogą mieć wartość z zakresu od 0 (transparent) do 255 (w pełni nieprzezroczysty).

Mieszanie kanw nakładki wymaga obsługi sprzętowej warstwy grafiki lub obsługi oprogramowania w ramach tworzenia kanwy złożonej.

Obsługa sprzętu dla mieszania kanwy jest włączana przez wywoływanie interfejsu API gx_canvas_hardware_layer_bind () przed ustawieniem wartości alfa kanwy. Gdy Kanwa jest powiązana z sprzętową warstwą grafiki, wywołanie interfejsu API gx_canvas_alpha_set () bezpośrednio wywołuje sprzętową warstwę grafiki mieszanie usług.

Aby korzystać z obsługi oprogramowania na potrzeby mieszania kanwy, aplikacja musi utworzyć kanwę ze stylem GX_CANVAS_COMPOSITE, w którym wszystkie inne zarządzane kanwy są złożone przed ostatecznym wyświetleniem. Obsługa oprogramowania dla mieszania kanwy jest dostępna tylko w przypadku uruchamiania z sterownikiem wyświetlania o wartości 16-BPP lub wyższej.

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy
- **Alpha** Alfa-Blend — wartość z zakresu od 0 (transparent) do 255 (nieprzezroczysty).

### <a name="return--values"></a>Wartości zwracane

- **GX_SUCCESS** (0X00) pomyślne przejście alfa-Blend
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_ERROR** (0X20) Nieprawidłowa Kanwa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the alpha-blend value of “my_canvas”. */
status = gx_canvas_alpha_set(&my_canvas, GX_ALPHA_VALUE_OPAQUE);

/* If status is GX_SUCCESS the alpha-blend value was successfully set. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_create,
- gx_canvas_drawing_complete
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift,
- gx_canvas_hardware_layer_bind,
- gx_canvas_show
- gx_canvas_hide

## <a name="gx_canvas_arc_draw"></a>gx_canvas_arc_draw

Rysuj łuk

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_arc_draw(
    INT xcenter, 
    INT ycenter, 
    UINT r,
    INT start_angle, 
    INT end_angle);
```

### <a name="description"></a>Opis

Ta usługa rysuje łuk okręgu na kanwie przy użyciu bieżącego pędzla. Łuk okręgu jest obcinany do nieprawidłowego regionu kanwy. Ta usługa wymaga zdefiniowania GX_ARC_DRAWING_SUPPORT.

### <a name="parameters"></a>Parametry

- **xcenter** x — pozycja środka łuku okręgu
- **YCenter** — pozycja y środka łuku okręgu
- promień łuku okręgu w języku **r**
- **start_angle** Kąt początkowy łuku okręgu
- **end_angle** Kąt końcowy łuku okręgu

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne narysowanie łuku **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa wartość
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Draw a circle arc from 0 degree to 90 degree in clockwise. */
status = gx_canvas_arc_draw(100, 100, 50, 0, 90);

/* If status is GX_SUCCESS the arc has been drawn on “my_canvas”. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_block_move,
- gx_canvas_circle_draw
- gx_display_create,
- gx_canvas_ellipse_draw
- gx_canvas_line_draw,
- gx_canvas_pie_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_block_move"></a>gx_canvas_block_move

Przenieś blok pikseli kanwy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_block_move(GX_RECTANGLE *block,
    GX_VALUE x_shift, GX_VALUE y_shift, GX_RECTANGLE *dirty);
```

### <a name="description"></a>Opis

Ta usługa przenosi blok danych pikseli kanwy w określonym kierunku. Ta usługa jest używana wewnętrznie przez GUIX do wykonywania szybkiego przewijania, ale może być również używana przez oprogramowanie aplikacji.

### <a name="parameters"></a>Parametry

- **Blokuj** Współrzędne obszaru do przeniesienia
- **x_shift** Liczba pikseli do przesunięcia na osi x
- **y_shift** Liczba pikseli do przesunięcia na osi y
- **zanieczyszczony** Jeśli blok został pomyślnie przeniesiony, ta funkcja zwraca część prostokąta źródłowego, która jest wciąż zanieczyszczona obiektowi wywołującemu w tym parametrze.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne przeniesienie bloku **GX_SUCCESS** (0x00)
- Nie można przenieść bloku **GX_FAILURE** (0x10)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
GX_RECTANGLE invalid;
GX_RECTANGLE move;

/* define 100 x 100 pixel rectangle */
gx_utility_rectangle_define(&move, 0, 0, 99, 99);

/* Move this rectangle 10 pixels to the right”. */
status = gx_canvas_block_move(&move, 10, 0, &invalid);

/* If status is GX_SUCCESS, then ‘invalid’ marks the area that needs to be redrawn after the block move. */

```

### <a name="see-also"></a>Zobacz też

- gx_canvas_arc_draw,
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_circle_draw"></a>gx_canvas_circle_draw

Rysuj okrąg

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_circle_draw(
    INT xcenter, 
    INT ycenter, 
    UINT r);
```

### <a name="description"></a>Opis

Ta usługa rysuje okrąg na kanwie przy użyciu bieżącego pędzla. Okrąg jest obcinany do nieprawidłowego regionu kanwy. Ta usługa wymaga zdefiniowania GX_ARC_DRAWING_SUPPORT.

### <a name="parameters"></a>Parametry

- **xcenter** x-coord środka okręgu
- **YCenter** y-coord środka Cirlce
- promień okręgu **r**

### <a name="return-values"></a>Wartości zwrócone

- Odświeżenie okręgu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa promień okręgu
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C

/* Draw a circle of radius 10 centered at (100, 100). */
status = gx_canvas_circle_draw(100, 100, 50);

/* If status is GX_SUCCESS the circle has been drawn on “my_canvas”. */

```

### <a name="see-also"></a>Zobacz też

- gx_canvas_arc_draw,
- gx_canvas_block_move,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_darw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw


## <a name="gx_canvas_create"></a>gx_canvas_create

Utwórz kanwę

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_create(
    GX_CANVAS *canvas, 
    GX_CONST GX_CHAR *name,
    GX_DISPLAY *display, 
    UINT type, 
    UINT width, 
    UINT height,
    GX_COLOR *memory_area, 
    ULONG memory_size);
```

### <a name="description"></a>Opis

Ta usługa tworzy kanwę o określonych właściwościach i skojarzonej pamięci.

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy
- **Nazwa** Nazwa logiczna kanwy
- **Wyświetl** Wskaźnik do wcześniej utworzonego ekranu
- **Typ** Typ typów kanwy canvasThe:
- **GX_CANVAS_SIMPLE:** Kanwa pamięci, która jest używana do rysowania poza ekranem.
- **GX_CANVAS_MANAGED:** Kanwa, która jest automatycznie opróżniana do aktywnego wyświetlania, w ramach procesu konstruowania złożonego lub jako część operacji przełączania buforu dla architektury jednej kanwy.
- **GX_CANVAS_VISIBLE:** Ta flaga może służyć do włączania i wyłączania kanwy bez utraty zawartości rysunku kanwy.
- **GX_CANVAS_MODIFIED:** Zarezerwowane do użytku w przyszłości.
- **GX_CANVAS_COMPOSITE:** Ta flaga jest używana przez aplikację podczas konfigurowania systemu wielokanwowego, który będzie złożonym wieloma zarządzanymi kanwami na kanwę kompozytową, a kompozyt jest kierowany do buforu ramki sprzętowej.
- **Szerokość** Szerokość w pikselach
- **wysokość** Wysokość w pikselach
- **memory_area** Obszar pamięci dla kanwy. Ta wartość może
- **GX_NULL** w momencie tworzenia kanwy
- **i** później zainicjowany przy użyciu gx_canvas_memory_define
- **memory_size** Rozmiar obszaru pamięci w bajtach lub 0, jeśli po utworzeniu kanwy zostanie zdefiniowana pamięć kanwy.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — tworzenie kanwy zakończonej powodzeniem
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_CANVAS_SIZE** (0X1C) Nieprawidłowy rozmiar bloku kontrolki kanwy
- **GX_INVALID_TYPE** (0X1b) Nieprawidłowy typ kanwy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Define global canvas memory area. */
GX_COLOR my_canvas_memory[272*480];

…

/* Create “my_canvas”. */
status = gx_canvas_create(&my_canvas, "my canvas", &my_display,
                    (GX_CANVAS_MANAGED | GX_CANVAS_VISIBLE),
                    272, 480,
                    my_canvas_memory,
                    sizeof(default_canvas_memory));

/* If status is GX_SUCCESS the 272 x 480 canvas was successfully created. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_delete,
- gx_canvas_hardware_layer_bind
- gx_canvas_memory_define

## <a name="gx_canvas_delete"></a>gx_canvas_delete

Usuń kanwę

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_delete(GX_CANVAS *canvas);
```

### <a name="description"></a>Opis

Ta usługa usuwa kanwę. Kanwa zostanie usunięta z wewnętrznej połączonej listy kanwy utrzymywanej przez GUIX.

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — tworzenie kanwy zakończonej powodzeniem
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CANVAS** (0X20) Nieprawidłowa Kanwa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Delete “my_canvas”. */
status = gx_canvas_delete (&my_canvas);

/* If status is GX_SUCCESS my_canvas was deleted. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_drawing_complete"></a>gx_canvas_drawing_complete

Ukończ rysowanie kanwy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_drawing_complete(
    GX_CANVAS *canvas, 
    GX_BOOL flush);
```

### <a name="description"></a>Opis

Ta usługa umożliwia GUIX na zakończenie rysowania aplikacji na określonej kanwie.

Aplikacja może korzystać z tej usługi, aby wymusić natychmiastowe rysowanie na kanwie. Spowoduje to opróżnienie kanwy do widocznego buforu ramek i/lub wyzwolenie operacji przełączania bugger, w zależności od architektury pamięci systemowej.

Ta usługa powinna być wywoływana tylko przez aplikację w celu zamknięcia sekwencji rysowania rozpoczętej z gx_canvas_drawing_initiate ().

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy
- **opróżnianie** Jeśli **_GX_TRUE_**, zmiany kanwy są opróżniane do wyświetlenia

### <a name="return-values"></a>Wartości zwrócone

- Zakończono pomyślne rysowanie **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Complete drawing on “my_canvas” and flush to display. */
status = gx_canvas_drawing_complete(&my_canvas, GX_TRUE);

/* If status is GX_SUCCESS the canvas drawing was successfully completed. */
```


### <a name="see-also"></a>Zobacz też

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift

## <a name="gx_canvas_drawing_initiate"></a>gx_canvas_drawing_initiate

Inicjuj rysowanie kanwy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_drawing_initiate(
    GX_CANVAS *canvas,
    GX_WIDGET *who, 
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>Opis

Ta usługa inicjuje rysowanie na określonej kanwie. Ta usługa jest wywoływana wewnętrznie w ramach operacji odroczonego rysowania wykonywanej automatycznie przez GUIX, gdy Kanwa wymaga aktualizacji. Jednak aplikacja może pominąć algorytm rysowania odroczonego GUIX i wykonać natychmiastowe i bezpośrednie rysowanie na kanwie, wywołując gx_canvas_drawing_inititate, a następnie wywołując odpowiednie funkcje rysowania, a następnie wywołując gx_canvas_drawing_complete ().

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy
- **kto** Wskaźnik do bloku kontrolki widget obiektu wywołującego. Ten parametr służy do inicjowania przycinania rysowania i wyświetlania parametrów dla kolejnych operacji rysowania.
- **dirty_area** Obszar do narysowania w obrębie. Ten parametr jest przesyłany przez obiekt wywołujący, aby wskazać obszar, do którego obiekt wywołujący chce, aby wszystkie operacje rysowania zostały obcięte. Zwykle jest to obszar, który został wcześniej oznaczony jako zanieczyszczony, ale obiekt wywołujący jest bezpłatny, aby rozwijać lub zwijać obszar przycinania.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne rozpoczęcie rysowania **GX_SUCCESS** (0x00)
- **GX_DRAW_NESTING_EXCEEDED** (0X05) przekracza maksymalną liczbę zagnieżdżenia
- **GX_NO_VIEW** (0X03) brak okienka ekranu dla obiektu wywołującego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CANVAS** (0X20) Nieprawidłowa Kanwa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Initiate drawing on “my_canvas”, my_widget.gx_widget_size
specify the area the application wants GUIX to redraw. */
status = gx_canvas_drawing_initiate(&my_canvas, &my_widget,
    &my_widget.gx_widget_size);

/* If status is GX_SUCCESS the canvas drawing was successfully initiated. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_offset_set
- gx_canvas_shift


## <a name="gx_canvas_ellipse_draw"></a>gx_canvas_ellipse_draw

Rysuj elipsę

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_ellipse_draw(
    INT xcenter, 
    INT ycenter, 
    INT a, 
    dINT b);
```

### <a name="description"></a>Opis

Ta usługa Rysuje elipsę na kanwie przy użyciu bieżącego pędzla. Elipsa jest obcinana do nieprawidłowego regionu kanwy. Ta usługa wymaga zdefiniowania GX_ARC_DRAWING_SUPPORT.

### <a name="parameters"></a>Parametry

- **xcenter** x-coord środka elipsy
- **YCenter** y-coord środka wielokropka
- **długość głównej** osi
- **b** Długość osi podrzędnej średnika

### <a name="return-values"></a>Wartości zwrócone

- Odświeżenie okręgu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa wartość
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Draw an ellipse of semi-major radius 100, semi-minor radius 50
    and centered at (200, 200). */
status = gx_canvas_ellipse_draw(200, 200, 100, 50);

/* If status is GX_SUCCESS the ellipse has been drawn on
    “my_canvas”. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create,
- gx_canvas_line_darw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw,
- gx_canvas_text_draw

## <a name="gx_canvas_hardware_layer_bind"></a>gx_canvas_hardware_layer_bind

Powiązywanie kanwy ze sprzętową warstwą grafiki

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_hardware_layer_bind(
    GX_CANVAS *canvas, 
    INT layer);
```

### <a name="description"></a>Opis

Ta usługa wiąże kanwę rysowania GUIX z sprzętową warstwą grafiki. Ta usługa jest wymagana tylko w przypadku urządzeń sprzętowych obsługujących wiele sprzętowych warstw graficznych.

Powiązanie kanwy ze sprzętową warstwą grafiki powoduje, że interfejsy API gx_canvas_show (), gx_canvas_hide (), gx_canvas_alpha_set () i gx_canvas_offset_set () są implementowane bezpośrednio przez sprzętowe usługi sterownika ekranu.

Jeśli sterownik ekranu sprzętowego nie obsługuje wielu warstw graficznych, ta usługa nie zwróci wartości GX_INVALID_DISPLAY.

### <a name="parameters"></a>Parametry

- **Kanwa** kanwy do wdrożenia na sprzęcie
- warstwa grafiki sprzętowej **warstwy**

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne powiązanie **GX_SUCCESS** (0x00)
- Nie zdefiniowano usługi warstwy wyświetlania **GX_INVALID_DISPLAY** (0x1D)
- Nieprawidłowe wskaźniki **GX_PTR_ERROR** (0x17)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_CANVAS** (0X20) Nieprawidłowa Kanwa
- **GX_NOT_SUPPORTED** (0X28) nie jest obsługiwana

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Binds the canvas to the hardware graphics layer 1. */
status = gx_canvas_hardware_layer_bind(&my_canvas, 1);

/* If status is GX_SUCCESS, the drawing canvas is bound to the
    hardware graphics. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_create,
- gx_canvas_memory_define

## <a name="gx_canvas_hide"></a>gx_canvas_hide

Ukrywanie kanwy, co sprawia, że jest niewidoczna

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>Opis

Ta usługa ukrywa kanwę GUIX. Jeśli Kanwa została powiązana z sprzętową warstwą grafiki przy użyciu gx_canvas_hardware_layer_bind (), ta usługa jest implementowana przy użyciu obsługi sprzętowej.

### <a name="parameters"></a>Parametry

- Kanwa **kanwy** do ukrycia

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna ukrycie **GX_SUCCESS** (0x00)
- **GX_INVALID_CANVAS** (0X20) Nieprawidłowa Kanwa
- Nieprawidłowe wskaźniki **GX_PTR_ERROR** (0x17)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Make my_canvas invisible. */
status = gx_canvas_hide(&my_canvas);

/* If status is GX_SUCCESS, the canvas has been hidden. */

```

### <a name="see-also"></a>Zobacz też

- gx_canvas_create,
- gx_canvas_drawing_complete
- gx_canvas_drawing_initiate,
- gx_canvas_offset_set
- gx_canvas_shift,
- gx_canvas_hardware_layer_bind,
- gx_canvas_show
- gx_canvas_hide

## <a name="gx_canvas_line_draw"></a>gx_canvas_line_draw

Rysuj linię

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_line_draw(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_VALUE x_end, 
    GX_VALUE y_end);
```

### <a name="description"></a>Opis

Ta usługa rysuje linię na kanwie przy użyciu bieżącego pędzla. Linia jest przycinana do nieprawidłowego regionu kanwy.

### <a name="parameters"></a>Parametry

- **x_start** Początkowe położenie linii x wiersza
- **y_end** Początkowe położenie osi y w wierszu
- **x_start** Końcowa pozycja x wiersza
- **y_end** Końcowa pozycja y linii.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne rysowanie wiersza **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania
- **GX_INVALID_WIDTH** (0X1E) Nieprawidłowa szerokość pędzla

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Draw line on canvas. */
status = gx_canvas_line_draw(0, 1, 320, 480);

/* If status is GX_SUCCESS, the line has been drawn to canvas. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_pie_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_memory_define"></a>gx_canvas_memory_define

Definiowanie pamięci kanwy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_memory_define(
    GX_CANVAS *canvas, 
    GX_COLOR *memory,
    ULONG memsize);
```

### <a name="description"></a>Opis

Ta usługa może być używana do przypisywania adresu pamięci kanwy po utworzeniu kanwy.

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do wcześniej utworzonej kanwy
- **pamięć** Adres pamięci kanwy
- **memsize** Rozmiar bloku pamięci kanwy w bajtach

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne przypisanie **GX_SUCCESS** (0x00)
- **GX_INVALID_CANVAS** (0X20) nieprawidłowy blok sterujący
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Assign canvas memory block. */
status = gx_canvas_memory_define(canvas,
    (GX_COLOR *) DRAM_MEMORY,
    (640 * 480 * 2));

/* If status is GX_SUCCESS, the canvas memory pointer has be
reassigned. */

```

### <a name="see-also"></a>Zobacz też

- gx_canvas_create,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_mouse_define"></a>gx_canvas_mouse_define

Definiowanie obrazu kursora myszy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_mouse_define(GX_CANVAS *canvas,
    GX_MOUSE_CURSOR_INFO *info);
```

### <a name="description"></a>Opis

Ta usługa definiuje informacje o myszy dla określonej kanwy. Ta usługa wymaga zdefiniowania GX_MOUSE_SUPPORT.

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy
- **informacje** Wskaźnik na informacje dotyczące kursora myszy. **Dodatek I** zawiera definicję do GX_MOUSE_CURSOR_INFO struktury.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — pomyślny zestaw informacji myszy
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set mouse cursor info. */
GX_MOUSE_CURSOR_INFO mouse_cursor;
mouse_cursor.gx_mouse_cursor_image_id = GX_PIXELMAP_ID_MOUSE;
mouse_cursor.gx_mouse_cursor_hotspot_x = 0;
mouse_cursor.gx_mouse_cursor_hotspot_y = 0;

status = gx_canvas_mouse_define(&my_canvas, &mouse_cursor);

/* If status is GX_SUCCESS the mouse info of “my_canvas” has been
set successfully. */

```

### <a name="see-also"></a>Zobacz też

- gx_canvas_mouse_show,
- gx_canvas_mouse_hide

## <a name="gx_canvas_mouse_hide"></a>gx_canvas_mouse_hide


Wyłączanie kursora myszy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_mouse_hide(GX_CANVAS *canvas);
```

### <a name="description"></a>Opis

Ta usługa sprawia, że kursor myszy jest ukryty na określonej kanwie. Ta usługa wymaga zdefiniowania GX_MOUSE_SUPPORT.

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) pomyślnego kursora myszy Ukryj
- **GX_FAILURE** (0X10) niepowodzenie ukrywania kursora myszy
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji


### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Hide the mouse cursor. */
status = gx_canvas_mouse_hide(&my_canvas);

/* If status is GX_SUCCESS the mouse cursor of “my_canvas” has been
hidden successfully. */

```

### <a name="see-also"></a>Zobacz też

- gx_canvas_mouse_show,
- gx_canvas_mouse_define

## <a name="gx_canvas_mouse_show"></a>gx_canvas_mouse_show


Włącz wskaźnik myszy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_mouse_show(GX_CANVAS *canvas);
```

### <a name="description"></a>Opis

Ta usługa sprawia, że kursor myszy jest widoczny dla określonej kanwy. Ta usługa wymaga zdefiniowania GX_MOUSE_SUPPORT. Interfejs API gx_canvas_mouse_define powinien zostać wywołany w celu zdefiniowania obrazu kursora myszy przed zażądaniem tej usługi.

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — pomyślny zestaw informacji myszy
- **GX_FAILURE** (0X10) nie powiodło się wyświetlenie kursora myszy
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Make mouse cursor hidden ”. */
status = gx_canvas_mouse_show(&my_canvas);

/* If status is GX_SUCCESS the mouse of “my_canvas” has been
hidden successfully. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_mouse_show,
- gx_canvas_mouse_define

## <a name="gx_canvas_offset_set"></a>gx_canvas_offset_set


Przypisanie kanwy x, przesunięcie ekranu y

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_offset_set(
    GX_CANVAS *canvas,
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>Opis

Ta usługa przypisuje przesunięcie wyświetlania x, y dla określonej kanwy. Steruje położeniem, w którym Kanwa jest złożona w buforze ramki widocznej, i jest często używana, gdy Kanwa jest mniejsza od ekranu fizycznego.

Jeśli Kanwa została powiązana z sprzętową warstwą grafiki przy użyciu interfejsu API gx_canvas_hardware_layer_bind (), usługa gx_canvas_offset_set jest implementowana bezpośrednio przy użyciu obsługi sprzętowej.

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy
- Współrzędna **x** x przesunięcia
- Współrzędna **y** y przesunięcia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — pomyślne przypisanie przesunięcia
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CANVAS** (0X20) Nieprawidłowa Kanwa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set display offset for “my_canvas”. */
status = gx_canvas_offset_set(&my_canvas, 20, 30);

/* If status is GX_SUCCESS the canvas drawing is now offset from
position 20,30. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_initiate,
- gx_canvas_shift
- gx_canvas_show,
- gx_canvas_hide,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_pie_draw"></a>gx_canvas_pie_draw


Rysuj wykres kołowy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pie_draw(
    INT xcenter, 
    INT ycenter,
    UINT r, 
    INT start_angle, 
    INT end_angle);
```

### <a name="description"></a>Opis

Ta usługa rysuje wykres kołowy do kanwy przy użyciu bieżącego pędzla kontekstu rysowania. Wykres kołowy jest przycinany do nieprawidłowego regionu kanwy. Ta usługa wymaga zdefiniowania GX_ARC_DRAWING_SUPPORT opcji konfiguracji.

### <a name="parameters"></a>Parametry

- **xcenter** x — pozycja środka kołowego
- **YCenter** osi y na środek koła
- **r** promień koła
- **start_angle** Kąt początkowy koła
- **end_angle** Kąt końcowy koła

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne narysowanie łuku **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa wartość
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Draw a pie from 0 degree to 90 degree in clockwise. */
status = gx_canvas_pie_draw(100, 100, 50, 0, 90);

/* If status is GX_SUCCESS the pie has been drawn to canvas. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pixelmap_draw,
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_pixel_draw"></a>gx_canvas_pixel_draw


Rysuj piksel

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixel_draw(GX_POINT position);
```

### <a name="description"></a>Opis

Ta usługa rysuje piksel na kanwie przy użyciu koloru linii bieżącego pędzla kontekstu rysowania. Jeśli opcja konfiguracji GX_BRUSH_ALPHA_SUPPORT jest zdefiniowana, mieszaj piksel w inny sposób, rysując piksel jako całkowicie nieprzezroczysty.

- **punkt** x, pozycja y pikseli do rysowania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne rysowanie Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_POINT point; /* the x,y position you want to draw to */
GX_RECTANGLE drawto; /* the rectangle bounding your drawing */
GX_CANVAS *mycanvas; /* the canvas you want to draw to */

/* calculate 1x1 pixel drawing area: */
gx_utility_rectangle_define(&drawto,
    point.gx_point_x, point.gx_point_y,
    point.gx_point_x, point.gx_point_y);

/* get my canvas: */
gx_widget_canvas_get(win, &mycanvas);

/* open my canvas for drawing: */
gx_canvas_drawing_initiate(mycanvas, win, &drawto);

/* setup my brush colors. Use any color ID in your resources: */
gx_context_line_color_set(GX_COLOR_ID_WINDOW_BORDER);

/* draw a pixel: */
status = gx_canvas_pixel_draw(point);

/* close the canvas: */
gx_canvas_drawing_complete(mycanvas, GX_TRUE);

/* If status is GX_SUCCESS, the pixel was successfully drawn to mycanvas. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_block_move,
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_blend"></a>gx_canvas_pixelmap_blend

Pixelmap Blend

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixelmap_blend(
    GX_VALUE x_position,
    GX_VALUE y_position, 
    GX_PIXELMAP *pixelmap, 
    GX_UBYTE alpha);
```

### <a name="description"></a>Opis

Ta usługa miesza Pixelmap z tłem kanwy. Współczynnik mieszania jest określany przez obiekt wywołujący. Wartość alfa może być z zakresu od 0 (w pełni przezroczyste) do 255 (w pełni nieprzezroczysty). Pixelmap może również zawierać wewnętrzny kanał alfa, który jest połączony z przychodzącą wartością mieszania. Ta usługa jest obsługiwana tylko przez sterowniki ekranu działające o głębi kolorów 16-BPP i wyższych.

### <a name="parameters"></a>Parametry

- **x_start** Początkowe położenie osi x Pixelmap
- **y_end** Początkowe położenie osi y Pixelmap
- **Pixelmap** Wskaźnik do Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne rysowanie Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_NOT_SUPPORTED** (0X28) nie jest obsługiwana
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Draw pixelmap on active canvas */

GX_PIXELMAP *map;
gx_system_pixelmap_get(ID_MY_PIXELMAP, &map);

status = gx_canvas_pixelmap_blend(10, 20, map, 128);

/* If status is GX_SUCCESS the pixelmap has been blended onto the current canvas. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_pixelmap_draw"></a>gx_canvas_pixelmap_draw

Rysuj Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixelmap_draw(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Opis

Ta usługa rysuje Pixelmap na kanwie.

### <a name="parameters"></a>Parametry

- **x_start** Początkowe położenie osi x Pixelmap
- **y_end** Początkowe położenie osi y Pixelmap
- **Pixelmap** Wskaźnik do Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne rysowanie Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Draw pixelmap on canvas. */
status = gx_canvas_pixelmap_draw(10, 20, &my_pixelmap);

/* If status is GX_SUCCESS the pixelmap “my_pixelmap” has been drawn. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_get"></a>gx_canvas_pixelmap_get

Pobierz Pixelmap kanwy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixelmap_get(GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Opis

Ta usługa zwraca strukturę GX_PIXELMAP wskazującą dane kanwy. Format Pixelmap jest ustawiany na bieżący format koloru wyświetlania.

### <a name="parameters"></a>Parametry

- **Pixelmap** Zwrócono Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne pobieranie Pixelmap
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Draw pixelmap on active canvas */

GX_PIXELMAP *map;

status = gx_canvas_pixelmap_get(map);

/* If status is GX_SUCCESS the pixelmap has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_pixelmap_blend,
- gx_canvas_pixelmap_tile
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_pixelmap_rotate"></a>gx_canvas_pixelmap_rotate


Rysuj obrócony Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixelmap_rotate(
    GX_VALUE x_position, 
    GX_VALUE y_position,
    GX_PIXELMAP *pixelmap, 
    INT angle,
    INT rot_cx, 
    INT rot_cy);
```

### <a name="description"></a>Opis

Ta usługa obraca Pixelmap w określonym kącie i renderuje Pixelmap do kanwy bezpośrednio w miarę wykonywania obrotu. Ta usługa różni się od gx_utility_pixelmap_rotate, ponieważ dane wyjściowe obrotu są bezpośrednio renderowane do pamięci kanwy, a obrócony Pixelmap nie jest zwracany do obiektu wywołującego.

Zaletą tej usługi w porównaniu gx_utility_pixelmap_rotate jest to, że nie jest wymagana dodatkowa pamięć do przechowywania obróconego Pixelmap. Wadą jest to, że kod obrotu musi być wykonywany za każdym razem, gdy Pixelmap jest rysowany.

Podczas renderowania obróconego Pixelmap są wymuszane walidacji wycinków i okienka ekranu.

### <a name="parameters"></a>Parametry

- **x_position** Początkowe położenie osi x Pixelmap
- **y_position** Początkowe położenie osi y Pixelmap
- **Pixelmap** Wskaźnik do Pixelmap
- **kąt** Kąt obrotu
- **rot_cx** X-coord środka obrotu. Jeśli ta wartość jest ustawiona na-1, środek obrazu jest używany jako środek obrotu.
- **rot_cy** T-coord środka obrotu. Jeśli ta wartość jest ustawiona na-1, środek obrazu jest używany jako środek obrotu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne rysowanie Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* rotate “src_pixelmap” by 30 degree in clockwise direction and draw in on canvas. */
status = gx_canvas_pixelmap_rotate(10, 20, &my_pixelmap, 30,
    -1, -1);

/* If status is GX_SUCCESS the rotated pixelmap “my_pixelmap” has been drawn. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_tile,
- gx_canvas_pixelmap_blend

## <a name="gx_canvas_pixelmap_tile"></a>gx_canvas_pixelmap_tile

Pixelmap kafelka

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_pixelmap_tile(
    GX_RECTANGLE *fill,
    GX_PIXELMAP *pixelmap);
```

### <a name="description"></a>Opis

Ta usługa wypełnia prostokąt na kanwie z żądanym Pixelmap.

### <a name="parameters"></a>Parametry

- **wypełnienie** Obszar do kafelka z Pixelmap
- **Pixelmap** Wskaźnik do Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- Kafelek Pixelmap (0x00) zakończony pomyślnie **GX_SUCCESS**
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania
- **GX_INVALID_VALUE** (0X22) Nieprawidłowy rozmiar wypełnienia

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Tile pixelmap on canvas */
status = gx_canvas_pixelmap_tile(&tile_area, &my_pixelmap);

/* If status is GX_SUCCESS the pixelmap “my_pixelmap” has been tiled on canvas */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_block_move,
- gx_canvas_pixelmap_get
- gx_canvas_pixelmap_blend,
- gx_canvas_pixelmap_draw

## <a name="gx_canvas_polygon_draw"></a>gx_canvas_polygon_draw


Rysuj Wielokąt

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_polygon_draw(
    GX_POINT *point_array,
    INT number_of_points);
```

### <a name="description"></a>Opis

Ta usługa rysuje wielokąt na kanwie przy użyciu bieżącego pędzla kontekstu rysowania.

### <a name="parameters"></a>Parametry

- **point_array** Tablica punktów wielokąta
- **number_of_points** Liczba punktów wielokąta

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne rysowanie wielokątów **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_POINT my_polygon[4] =
{
    { 208, 63 },
    { 274, 63 },
    { 274, 163 },
    { 208, 163 }
};

/* Draw polygon “my_polygon” on canvas. */
status = gx_canvas_polygon_draw(&my_polygon, 4);

/* If status is GX_SUCCESS the polygon “my_polygon” has been drawn. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_rectangle_draw
- gx_canvas_text_draw

## <a name="gx_canvas_rectangle_draw"></a>gx_canvas_rectangle_draw


Rysuj prostokąt

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_rectangle_draw(GX_RECTANGLE *rectangle);
```

### <a name="description"></a>Opis

Ta usługa rysuje prostokąt na kanwie.

### <a name="parameters"></a>Parametry

- **prostokąt** Prostokąt do rysowania

### <a name="return-values"></a>Wartości zwrócone

- Rysowanie pomyślnych prostokątów **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Draw rectangle “my_rectangle” on canvas. */
status = gx_canvas_rectangle_draw(&my_rectangle);

/* If status is GX_SUCCESS the rectangle “my_rectangle” has been drawn. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile,
- gx_canvas_polygon_draw
- gx_canvas_text_draw

## <a name="gx_canvas_rotated_text_draw"></a>gx_canvas_rotated_text_draw


Rysuj tekst obrócony o punkt środkowy (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_rotated_text_draw(
    const GX_CHAR *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>Opis

Ten interfejs API jest przestarzały na korzyść lub gx_canvas_rotated_text_draw_ext (). Mimo że w dalszym ciągu obsługiwane nowe aplikacje nie powinny używać tego interfejsu API i powinny używać gx_canvas_rotated_text_draw_ext ().

Ta usługa służy do rysowania tekstu na kanwie. Tekst jest rysowany jako obrócony o żądanym punkcie centrum. Bieżąca czcionka kontekstu rysowania i kolor linii kontekstu rysowania służy do renderowania tekstu.

Ta usługa używa gx_utility_string_to_alphamap funkcji do renderowania ciągu tekstowego do tymczasowego 8bpp Pixelmap zawierającego tylko wartość alfa. Następnie usługa obraca alphamap przy użyciu funkcji gx_utility_pixelmap_rotate. Gdy końcowa alphamap jest renderowana na kanwie, ta usługa zwolni tymczasowy alphamap i skojarzoną pamięć.

Ponieważ tymczasowy alphamap jest wymagany do renderowania obróconego tekstu, aplikacja musi skonfigurować gx_system_memory_allocator za pomocą interfejsu API wywoływania gx_system_memory_allocator_set () przed próbą narysowania obróconego tekstu.

Ta usługa powinna być używana tylko do renderowania obróconego tekstu "jednorazowo". Jeśli ten sam ciąg tekstowy zostanie narysowany wiele razy w różnych lokalizacjach lub w różnych kątach rotacji, bardziej wydajne jest użycie funkcji narzędzia gx_utility_string_to_alphamap (), aby utworzyć tekst alphamap raz, a następnie użyć gx_utility_pixelmap_rotate wiele razy, aby wielokrotnie obrócić powstające alphamap.

### <a name="parameters"></a>Parametry

- **tekst** Ciąg tekstowy do narysowania
- **xCenter** Wyśrodkuj położeniu wokół tego, który tekst zostanie obrócony.
- **yCenter** Wyśrodkuj położenie, wokół którego zostanie obrócony tekst.
- **kąt** Żądany kąt obrotu tekstu (w stopniach).

### <a name="return-values"></a>Wartości zwrócone

- Renderowanie tekstu w **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_SYSTEM_MEMORY_ERROR** (0X30) za mało dostępnej pamięci lub gx_system_memory_allocator nie została przypisana
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
void my_window_draw(GX_WINDOW *window)
{

    GX_VALUE xpos = 100;
    GX_VALUE ypos = 100;
    INT dynamic_count = 1234567;
    GX_CHAR dynamic_text[10];

    /* Call default window draw routine. */
    gx_window_draw(window);

    /* Set font. */
    gx_context_font_set(GX_FONT_ID_SMALL_BOLD);

    /* Convert int value to string. */
    gx_utility_ltoa(dynamic_count, dynamic_text, 20);

    /* Draw rotate text. */
    gx_canvas_rotated_text_draw(dynamic_text, xpos, ypos, 45);
}
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_rotated_text_draw_ext"></a>gx_canvas_rotated_text_draw_ext


Rysuj tekst obrócony o punkt środkowy

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_rotated_text_draw_ext(
    GX_CONST GX_STRING *text,
    GX_VALUE xCenter, 
    GX_VALUE yCenter, 
    INT angle);
```

### <a name="description"></a>Opis

Ta usługa służy do rysowania tekstu na kanwie. Tekst jest rysowany jako obrócony o żądanym punkcie centrum. Bieżąca czcionka kontekstu rysowania i kolor linii kontekstu rysowania służy do renderowania tekstu.

Ta usługa używa gx_utility_string_to_alphamap funkcji do renderowania ciągu tekstowego do tymczasowego 8bpp Pixelmap zawierającego tylko wartość alfa. Następnie usługa obraca alphamap przy użyciu funkcji gx_utility_pixelmap_rotate. Gdy końcowa alphamap jest renderowana na kanwie, ta usługa zwolni tymczasowy alphamap i skojarzoną pamięć.

Ponieważ tymczasowy alphamap jest wymagany do renderowania obróconego tekstu, aplikacja musi skonfigurować gx_system_memory_allocator przez wywołujący interfejs API ***gx_system_memory_allocator_set*** przed próbą narysowania obróconego tekstu.

Ta usługa powinna być używana tylko do renderowania obróconego tekstu "jednorazowo". Jeśli ten sam ciąg tekstowy zostanie narysowany wiele razy w różnych lokalizacjach lub w różnych kątach rotacji, bardziej wydajne jest użycie funkcji narzędzia gx_utility_string_to_alphamap (), aby utworzyć tekst alphamap raz, a następnie użyć gx_utility_pixelmap_rotate wiele razy, aby wielokrotnie obrócić powstające alphamap.

### <a name="parameters"></a>Parametry

- **tekst** Ciąg tekstowy do narysowania
- **xCenter** Wyśrodkuj położeniu wokół tego, który tekst zostanie obrócony.
- **yCenter** Wyśrodkuj położenie, wokół którego zostanie obrócony tekst.
- **kąt** Żądany kąt obrotu tekstu (w stopniach).

### <a name="return-values"></a>Wartości zwrócone

- Renderowanie tekstu w **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_CONTEXT** (0X06) Nieprawidłowy kontekst rysowania
- **GX_SYSTEM_MEMORY_ERROR** (0X30) za mało dostępnej pamięci lub gx_system_memory_allocator nie została przypisana.
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
void my_window_draw(GX_WINDOW *window)
{

    GX_VALUE xpos = 100;
    GX_VALUE ypos = 100;
    INT dynamic_count = 1234567;
    GX_CHAR dynamic_text[10];
    GX_STRING string;

    /* Call default window draw routine. */
    gx_window_draw(window);

    /* Set font. */
    gx_context_font_set(GX_FONT_ID_SMALL_BOLD);

    /* Convert int value to string. */
    gx_utility_ltoa(dynamic_count, dynamic_text, 20);

    string.gx_string_ptr = dynamic_text;
    string.gx_string_length = strlen(dynamic_text);

    /* Draw rotate text. */
    gx_canvas_rotated_text_draw_ext(&string, xpos, ypos, 45);
}
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_alpha_set,
- gx_canvas_drawing_complete
- gx_canvas_create,
- gx_canvas_drawing_initiate
- gx_canvas_offset_set,
- gx_canvas_shift

## <a name="gx_canvas_shift"></a>gx_canvas_shift


Przenieś kanwę o x, y

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_shift(
    GX_CANVAS *canvas, 
    GX_VALUE x, GX_VALUE y);
```

### <a name="description"></a>Opis

Ta usługa przenosi przesunięcie określonego obszaru roboczego o określoną liczbę. Ma to wpływ na położenie, w którym Kanwa jest renderowana w buforze ramki widocznej.

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy
- **x** pikseli do przesunięcia na osi x
- **y** pikseli do przesunięcia na osi y

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna zmiana kanwy **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CANVAS** (0X20) Nieprawidłowa Kanwa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Shift canvas “my_canvas”. */
status = gx_canvas_shift(&my_canvas, 10, 15);

/* If status is GX_SUCCESS the canvas has been shifted by 10 pixels
    on the X axis and 15 on the Y axis. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_drawing_complete,
- gx_canvas_initiate
- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_offset_set

## <a name="gx_canvas_show"></a>gx_canvas_show


Wyświetlanie kanwy jako widocznej

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_show(GX_CANVAS *canvas);
```

### <a name="description"></a>Opis

Ta usługa sprawia, że Kanwa jest widoczna. Jeśli Kanwa została wcześniej powiązana z sprzętową warstwą grafiki przy użyciu interfejsu API gx_canvas_hardware_layer_bind (), usługa gx_canvas_show () jest implementowana bezpośrednio przy użyciu obsługi sprzętowej.

### <a name="parameters"></a>Parametry

- **Kanwa** Wskaźnik do bloku kontrolki kanwy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — pomyślne przypisanie przesunięcia
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CANVAS** (0X20) Nieprawidłowa Kanwa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Make this canvas visible. */
status = gx_canvas_show(&my_canvas);

/* If status is GX_SUCCESS the canvas drawing is now visible */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_alpha_set,
- gx_canvas_create
- gx_canvas_drawing_complete,
- gx_canvas_initiate,
- gx_canvas_shift,
- gx_canvas_hide,
- gx_canvas_hardware_layer_bind

## <a name="gx_canvas_text_draw"></a>gx_canvas_text_draw

Rysuj tekst (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_text_draw(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_CONST GX_CHAR *string, 
    INT length);
```

### <a name="description"></a>Opis

Ta usługa rysuje tekst na kanwie. Ten interfejs API, chociaż nadal jest obsługiwany, jest przestarzały, a nowe aplikacje powinny zamiast tego używać gx_canvas_text_draw_ext ().

### <a name="parameters"></a>Parametry

- **x_start** Uruchamianie współrzędnych x dla tekstu
- **y_start** Początkowa Współrzędna y dla tekstu
- **ciąg** Wskaźnik do ciągu do rysowania
- **Długość** Jeśli długość >= 0, ogranicza liczbę znaków rysowanych do długości. Jeśli długość < 0, cały ciąg do momentu narysowania wartości NULL.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne rysowanie tekstu **GX_SUCCESS** (0x00)
- Niepowodzenie rysowania tekstu **GX_FAILURE** (0x1E)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Draw text “example” on current canvas”. */
status = gx_canvas_text_draw(10, 20, “example”, 7);

/* Draw all of a string of unknown length on the current canvas */
status = gx_canvas_text_draw(10, 40, string_ptr, -1);

/* If status is GX_SUCCESS the text “example” has been drawn. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw

## <a name="gx_canvas_text_draw_ext"></a>gx_canvas_text_draw_ext


Rysuj tekst

### <a name="prototype"></a>Prototype

```C
UINT gx_canvas_text_draw_ext(
    GX_VALUE x_start, 
    GX_VALUE y_start,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Opis

Ta usługa rysuje tekst na kanwie.

### <a name="parameters"></a>Parametry

- **x_start** Uruchamianie współrzędnych x dla tekstu
- **y_start** Początkowa Współrzędna y dla tekstu
- **ciąg** Wskaźnik do ciągu do rysowania

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne rysowanie tekstu **GX_SUCCESS** (0x00)
- Niepowodzenie rysowania tekstu **GX_FAILURE** (0x1E)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_CONTEXT** (0X06) brak otwartego kontekstu rysowania
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu
- **GX_INVALID_FONT** (0X16) Nieprawidłowa czcionka

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING string;
string.gx_string_ptr = “example”;
string.gx_string_length = 7;

/* Draw text “example” on current canvas”. */
status = gx_canvas_text_draw_ext(10, 20, &string);

/* If status is GX_SUCCESS the text “example” has been drawn. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_arc_draw,
- gx_canvas_block_move
- gx_canvas_circle_draw,
- gx_display_create
- gx_canvas_ellipse_draw,
- gx_canvas_line_draw
- gx_canvas_pie_draw,
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw,
- gx_canvas_rectangle_draw

## <a name="gx_checkbox_create"></a>gx_checkbox_create


Utwórz pole wyboru

### <a name="prototype"></a>Prototype

```C
UINT gx_checkbox_create(
    GX_CHECKBOX *checkbox, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT checkbox_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet CheckBox z określonymi właściwościami. GX_CHECKBOX pochodzi od GX_TEXT_BUTTON, a wszystkie usługi gx_text_button mogą być używane z GX_CHECKBOX widżetów.

### <a name="parameters"></a>Parametry

- **pole wyboru** Wskaźnik do pola wyboru bloku sterowania nazwa logiczna nazwa widżetu pola wyboru
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **text_id** Identyfikator zasobu tekstu pola wyboru
- **styl** Styl pola wyboru. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **checkbox_id** Zdefiniowany przez aplikację identyfikator pola wyboru
- **rozmiar** Wymiary pola wyboru

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne utworzenie pola wyboru
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- Nieprawidłowy rozmiar **GX_INVALID_SIZE** (0x19)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “my_checkbox”. */
status = gx_checkbox_create(&my_checkbox, “my_checkbox”,
    &my_parent,
    MY_CHECKBOX_TEXT_RESOURCE_ID, GX_STYLE_BORDER_RAISED,
    MY_CHECKBOX_ID,
    &size);

/* If status is GX_SUCCESS the checkbox “my_checkbox” has been created. */
```
### <a name="see-also"></a>Zobacz też

- gx_checkbox_draw,
- gx_checkbox_event_process,
- gx_checkbox_select

## <a name="gx_checkbox_draw"></a>gx_checkbox_draw

Pole wyboru rysowania

### <a name="prototype"></a>Prototype

```C
VOID gx_checkbox_draw(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>Opis

Ta usługa służy do rysowania określonego pola wyboru. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest uwidaczniana dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania niestandardowych widżetów pól wyboru.

### <a name="parameters"></a>Parametry

- **pole wyboru** Wskaźnik do bloku kontrolki CheckBox

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom checkbox draw function. */
VOID custom_checkbox_draw(GX_CHECKBOX *checkbox)
{
    /* Call default checkbox draw. */
    gx_checkbox_draw(checkbox);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_checkbox_create,
- gx_checkbox_event_process,
- gx_checkbox_select

## <a name="gx_checkbox_event_process"></a>gx_checkbox_event_process


Zdarzenie pola wyboru procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_checkbox_event_process(
    GX_CHECKBOX *checkbox, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego pola wyboru. Ta usługa powinna być wywoływana jako domyślna procedura obsługi zdarzeń przez wszelkie niestandardowe funkcje przetwarzania zdarzeń CheckBox.

### <a name="parameters"></a>Parametry

- **pole wyboru** Wskaźnik do bloku kontrolki CheckBox
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia CheckBox pomyślnego **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic checkbox event processing as part of custom event processing function. */

UINT custom_checkbox_event_process(GX_CHECKBOX *checkbox,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default checkbox
            event processing */
        status = gx_checkbox_event_process(checkbox, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_select

## <a name="gx_checkbox_pixelmap_set"></a>gx_checkbox_pixelmap_set


Ustaw Pixelmap dla pola wyboru

### <a name="prototype"></a>Prototype

```C
UINT gx_checkbox_pixelmap_set(
    GX_CHECKBOX *checkbox,
    GX_RESOURCE_ID unchecked_id, 
    GX_RESOURCE_ID checked_id,
    GX_RESOURCE_ID unchecked_disabled_id, 
    GX_RESOURCE_ID checked_disabled_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje pixelmaps do wyświetlania przez określone pole wyboru dla każdego stanu pola wyboru. Identyfikatory zasobów mogą być zduplikowane.

### <a name="parameters"></a>Parametry

- **pole wyboru** Wskaźnik do bloku kontrolki CheckBox
- **unchecked_id** Pixelmap używany dla stanu niesprawdzonego
- **checked_id** Pixelmap używany dla stanu zaznaczenia
- **unchecked_disabled_id** Pixelmap używany dla pola wyboru wyłączone i niezaznaczone
- **checked_disabled_id** Pixelmap używany dla wyłączonego i zaznaczonego pola wyboru

### <a name="return-values"></a>Wartości zwrócone

- Pole wyboru **GX_SUCCESS** (0x00) powiodło się
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Select “my_checkbox”. */
status = gx_checkbox_pixelmap_set(&my_checkbox,
    PIXELMAP_UNCHECKED_ID,
    PIXELMAP_CHECKED_ID, PIXELMAP_UNCHECKED_DISABLED_ID,
    PIXELMAP_CHECKED_SIABLED_ID));

/* If status is GX_SUCCESS the pixelmaps are assigned to the checkbox “my_checkbox” */
```

### <a name="see-also"></a>Zobacz też

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_event_process

## <a name="gx_checkbox_select"></a>gx_checkbox_select


Zaznacz pole wyboru

### <a name="prototype"></a>Prototype

```C
UINT gx_checkbox_select(GX_CHECKBOX *checkbox);
```

### <a name="description"></a>Opis

Ta usługa wymusza zaznaczenie pola wyboru w wybranym stanie.

### <a name="parameters"></a>Parametry

- **pole wyboru** Wskaźnik do bloku kontrolki CheckBox

### <a name="return-values"></a>Wartości zwrócone

- Pole wyboru **GX_SUCCESS** (0x00) powiodło się
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Select “my_checkbox”. */
status = gx_checkbox_select(&my_checkbox);

/* If status is GX_SUCCESS the checkbox “my_checkbox” has been toggled. */
```

### <a name="see-also"></a>Zobacz też

- gx_checkbox_create,
- gx_checkbox_draw,
- gx_checkbox_event_process

## <a name="gx_circular_gauge_angle_get"></a>gx_circular_gauge_angle_get


Pobierz kąt bieżący

### <a name="prototype"></a>Prototype

```C
UINT gx_circular_gauge_angle_get(
    GX_CIRCULAR_GAUGE *gauge, 
    INT *angle);
```

### <a name="description"></a>Opis

Ta usługa Pobiera bieżący kąt wskazówki dla widgetu miernika okrągłego.

### <a name="parameters"></a>Parametry

- **miernik** Wskaźnik do bloku kontrolki miernika okrągłego
- **kąt** Bieżący kąt wskazówki do pobrania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne odchylenia kątowe miernika
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
INT current_angle;

/* Retrieve the current needle angle of “my_gauge”. */
status = gx_circular_gauge_angle_get(&my_gauge, &current_angle);

/* If status is GX_SUCCESS the current needle angle of “my_gauge” has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_circular_gauge_angle_set,
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_angle_set"></a>gx_circular_gauge_angle_set


Ustaw kąt docelowy

### <a name="prototype"></a>Prototype

```C
UINT gx_circular_gauge_angle_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT angle);
```

### <a name="description"></a>Opis

Ta usługa ustawia kąt docelowy widżetu miernika okrągłego.

### <a name="parameters"></a>Parametry

- **miernik** Wskaźnik do bloku kontrolki miernika okrągłego
- **kąt** Kąt docelowej wskazówki

### <a name="return-values"></a>Wartości zwrócone

- Zestaw ostrych pomyślnych **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set target angle of “my_gauge” to 180. */
status = gx_circular_gauge_angle_set(&my_gauge, 180);

/* If status is GX_SUCCESS the circular gauge of “my_gauge” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_circular_gauge_angle_get,
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_animation_set"></a>gx_circular_gauge_animation_set


Ustaw parametry animacji

### <a name="prototype"></a>Prototype

```C
UINT gx_circular_gauge_animation_set(
    GX_CIRCULAR_GAUGE *gauge,
    INT steps, 
    INT delay);
```

### <a name="description"></a>Opis

Ta usługa ustawia kroki animacji i czas opóźnienia dla widżetu mierniki cyklicznej.

### <a name="parameters"></a>Parametry

- **miernik** Wskaźnik do bloku kontrolki miernika okrągłego
- **kroki** Łączna liczba kroków dla jednej rotacji
- **opóźnienie** Czas opóźnienia dla każdego kroku

### <a name="return-values"></a>Wartości zwrócone

- Pole wyboru **GX_SUCCESS** (0x00) powiodło się
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa wartość

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set animation steps and delay time of circular gauge “my_gauge”
    to 30 and 1, the needle of “my_gauge” will rotate from
    current angle to target angle by 30 steps with 1 tick delay between every step. */
status = gx_circular_gauge_animation_set(&my_gauge, 30, 1);

/* If status is GX_SUCCESS the steps and delay time of “my_gauge” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_background_draw"></a>gx_circular_gauge_background_draw


Wyrysuj tło miernika cyklicznego

### <a name="prototype"></a>Prototype

```C
VOID gx_circular_gauge_background_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>Opis

Ta usługa rysuje tło określonego miernika cyklicznego. Ta usługa jest zwykle wywoływana wewnętrznie przez funkcję gx_circular_gauge_draw, ale jest dostępna dla aplikacji, aby pomóc w tworzeniu niestandardowych funkcji rysowania.

### <a name="parameters"></a>Parametry

- **miernik** Wskaźnik do bloku kontrolki miernika okrągłego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Draw circular gauge background. */
gx_circular_gauge_background_draw(&my_circular_gauge);
```

### <a name="see-also"></a>Zobacz też

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set,
- gx_circular_gauge_create
- gx_circular_gauge_draw,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_create"></a>gx_circular_gauge_create


Utwórz miernik cykliczny

### <a name="prototype"></a>Prototype

```C
UINT gx_circular_gauge_create(
    GX_CIRCULAR_GAUGE *gauge,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_CIRCULAR_GAUGE_INFO *info,
    GX_RESOURCE_ID background_id,
    ULONG style,
    USHORT circular_gauge_id,
    GX_VALUE xpos,
    GX_VALUE ypos);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet miernika okrągły z określonymi właściwościami.

### <a name="parameters"></a>Parametry

- **miernik** Wskaźnik do bloku kontrolki miernika okrągłego
- **Nazwa** Logiczna nazwa widżetu miernika cyklicznego
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **informacje** Wskaźnik na strukturę informacji miernika. **Dodatek I** zawiera definicję do GX_CIRCULAR_GAUGE_INFO struktury
- **background_id** Identyfikator zasobu w tle miernika cyklicznego Pixelmap
- **styl** Styl miernika okrągłego. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **circular_gauge_id** Zdefiniowany przez aplikację identyfikator miernika cyklicznego
- **xpos** Wskaźnik współrzędnej x miernika
- **YPos** Pozycja współrzędnej y miernika

### <a name="return-values"></a>Wartości zwrócone

- Pole wyboru **GX_SUCCESS** (0x00) powiodło się
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontroli
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CIRCULAR_GAUGE gauge_info;

gauge_info.gx_circular_gauge_info_animation_steps = 30;
gauge_info.gx_circular_gauge_info_animation_delay = 1;
gauge_info.gx_circular_gauge_info_needle_xpos = 140;
gauge_info.gx_circular_gauge_info_needle_ypos = 140;
gauge_info.gx_circular_gauge_info_neelde_xcor = 20;
gauge_info.gx_circular_gauge_info_neelde_ycor = 88;
gauge_info.gx_circular_gauge_info_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Create “my_gauge”. */
status = gx_circular_gauge_create(&my_gauge, “my_gauge”,
            &my_parent,
            &gauge_info, MY_PIXELMAP_RESOURCE_ID, GX_NULL,
            MY_ICON_ID, 5, 30);

/* If status is GX_SUCCESS the circular gauge “my_gauge” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_draw
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_draw"></a>gx_circular_gauge_draw

Rysuj miernik cykliczny

### <a name="prototype"></a>Prototype

```C
VOID gx_circular_gauge_draw(GX_CIRCULAR_GAUGE *gauge);
```

### <a name="description"></a>Opis

Ta usługa Rysuje określony okrągły miernik. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest dostępna dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania dla widżetów niestandardowego miernika.

### <a name="parameters"></a>Parametry

- **miernik** Wskaźnik do bloku kontrolki miernika okrągłego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom circular gauge draw function. */
VOID custom_gauge_draw(GX_CIRCULAR_GAUGE *gauge)
{
    /* Call default circular gauge draw. */
    gx_circular_gauge_draw(gauge);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw
- gx_circular_gauge_create,
- gx_circular_gauge_event_process

## <a name="gx_circular_gauge_event_process"></a>gx_circular_gauge_event_process


Zdarzenie cyklicznego miernika procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_circular_gauge_event_process(
    GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego miernika cyklicznego.

### <a name="parameters"></a>Parametry

- **miernik** Wskaźnik do bloku sterowania miernikiem
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia pomyślnego miernika **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic circular gauge event processing as part of custom event processing function. */
UINT custom_gauge_event_process(GX_CIRCULAR_GAUGE *gauge,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default circular gauge
             event processing */
        status = gx_circular_gauge_event_process(gauge, event);
        break;
}
return status;
```

### <a name="see-also"></a>Zobacz też

- gx_circular_gauge_angle_get,
- gx_circular_gauge_angle_set
- gx_circular_gauge_animation_set
- gx_circular_gauge_background_draw,
- gx_circular_gauge_create
- gx_circular_gauge_draw

## <a name="gx_context_brush_default"></a>gx_context_brush_default


Ustaw pędzel bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_default(GX_DRAW_CONTEXT *context);
```

### <a name="description"></a>Opis

Ta usługa ustawia domyślny pędzel określonego kontekstu rysowania.

### <a name="parameters"></a>Parametry

- **kontekst** Wskaźnik do bloku kontroli kontekstu

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne utworzenie **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik kontekstu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the brush of “my_context” to default. */
status = gx_context_brush_default(&my_context);

/* If status is GX_SUCCESS the brush of “my_context” has been set to default. */

```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_define,
- gx_context_brush_get
- gx_context_brush_set,
- gx_context_brush_style_set
- gx_context_brush_pattern_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_define"></a>gx_context_brush_define


Definiowanie pędzla bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_define(
    GX_RESOURCE_ID line_color_id,
    GX_RESOURCE_ID fill_color_id, 
    UINT style);
```

### <a name="description"></a>Opis

Ta usługa definiuje pędzel bieżącego kontekstu rysowania.

### <a name="parameters"></a>Parametry

- **line_color_id** Identyfikator zasobu koloru linii. **Dodatek B** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **fill_color_id** Identyfikator zasobu koloru wypełnienia. **Dodatek B** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **styl** Styl pędzla. **Dodatek D** zawiera opis obsługiwanych stylów pędzla. Style pędzla można łączyć w jedną zmienną przy użyciu funkcji bitowej lub operacji.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — Definiowanie pędzla kontekstu pomyślnego
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_CONTEXT** (0X06) nie zdefiniowano aktywnego kontekstu rysowania
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Define the brush of the current context. */
status = gx_context_brush_define(GX_COLOR_BLACK_ID,
    GX_COLOR_BLACK_ID,
    GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the brush of the current context has been defined. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default,
- gx_context_brush_get
- gx_context_brush_set,
- gx_context_brush_pattern_set
- gx_context_brush_style_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_get"></a>gx_context_brush_get


Pobierz pędzel bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_get(GX_BRUSH **return_brush);
```

### <a name="description"></a>Opis

Ta usługa zwraca wskaźnik do aktywnego pędzla w bieżącym kontekście rysowania. Jeśli nie ma aktywnego kontekstu rysowania, usługa zakończy się niepowodzeniem i zwróci wskaźnik o wartości NULL.

### <a name="parameters"></a>Parametry

- **return_brush** Wskaźnik do miejsca docelowego dla pędzla.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrał pędzel kontekstu
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_BRUSH *my_brush;

/* Get the brush of the current context. */
status = gx_context_brush_get(&my_brush);

/* If status is GX_SUCCESS the brush of the current context has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_set,
- gx_context_brush_style_set
- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_pattern_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_pattern_set"></a>gx_context_brush_pattern_set


Ustaw Wzorzec pędzla bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_pattern_set(ULONG pattern);
```

### <a name="description"></a>Opis

Ta usługa ustawia Wzorzec pędzla bieżącego kontekstu rysowania.

Wzorzec pędzla jest używany do rysowania pionowych linii kreskowanych w poziomie i kreskowanych. Gdy gx_canvas_line_draw () jest wywoływana, a linia jest pozioma lub pionowa, a pole brush.gx_brush_line_pattern ma wartość różną od zera, zostanie narysowana linia wzorku.

Maska wzorca pędzla jest obecnie obsługiwana tylko dla linii poziomej i pionowej.

### <a name="parameters"></a>Parametry

- **wzorzec** Wzorzec, który ma być używany dla pędzla. Jest to prosty szesnastkowy wzorzec włączania/wyłączania, który będzie używany do rysowania linii wzorców.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) zestaw pędzli kontekstu pomyślnego
- **GX_INVALID_CONTEXT** (0X06) Nieprawidłowy kontekst rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the brush pattern for the current contex. */
status = gx_context_brush_pattern_set(0x80808080);

/* If status is GX_SUCCESS the brush pattern of the current context
has been set to the specified pattern. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_style_set
- gx_context_brush_width_set,
- gx_context_fill_color_set
- gx_context_font_set,
- gx_context_line_color_set
- gx_context_pixelmap_set,
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set,
- gx_context_raw_line_color_set

## <a name="gx_context_brush_set"></a>gx_context_brush_set


Ustaw pędzel bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_set(GX_BRUSH *brush);
```

### <a name="description"></a>Opis

Ta usługa ustawia pędzel bieżącego kontekstu rysowania.

### <a name="parameters"></a>Parametry

- **pędzel** Wskaźnik do pędzla, który ma być używany dla bieżącego kontekstu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) zestaw pędzli kontekstu pomyślnego
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_BRSUH my_brush;
GX_FONT *font;
GX_COLOR fill_color;
GX_COLOR line_color;

/* Retrieve the font that associated with the specified font ID. */
gx_context_font_get(MY_FONT_ID, &font);

/* Retrieve the color that associated with the specified color ID. */
gx_context_color_get(MY_FILL_COLOR_ID, &fill_color);
gx_context_color_get(MY_LINE_COLOR, &line_color);

my_brush.gx_brush_pixelmap = MY_PIXELMAP_ID;
my_brush.gx_brush_font = font;
my_brush.gx_brush_line_pattern = 0x80808080;
my_brush.gx_brush_pattern_mask = 0x80000000;
my_brush.gx_brush_fill_color = fill_color;
my_brush.gx_brush_line_color = line_color;
my_brush.gx_brush_style = GX_BRSUH_SOLID_FILL | GX_BRUSH_ALIAS |
                          GX_BRUSH_PIXELMAP_FILL | GX_BRUSH_ROUND
my_brush.gx_brush_width = 2;
my_brush.gx_brush_alpha = 255;

/* Set the brush of the current context. */
status = gx_context_brush_set(my_brush);

/* If status is GX_SUCCESS the brush of the current context has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_pattern_set
- gx_context_brush_style_set,
- gx_context_brush_width_set
- gx_context_fill_color_set,
- gx_context_font_set
- gx_context_line_color_set,
- gx_context_pixelmap_set
- gx_context_raw_brush_define,
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_brush_style_set"></a>gx_context_brush_style_set


Ustaw styl pędzla bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_style_set(UINT style);
```

### <a name="description"></a>Opis

Ta usługa ustawia styl pędzla bieżącego kontekstu rysowania.

### <a name="parameters"></a>Parametry

- **styl** Styl pędzla bieżącego kontekstu. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) ustawiony styl pędzla kontekstowego
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the brush style of the current context. */
status = gx_context_brush_style_set(GX_BRUSH_ALIAS);

/* If status is GX_SUCCESS the brush style of the current context has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default,
- gx_context_brush_define
- gx_context_brush_get,
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_width_set,
- gx_context_fill_color_set
- gx_context_font_set,
- gx_context_line_color_set
- gx_context_pixelmap_set,
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set,
- gx_context_raw_line_color_set

## <a name="gx_context_brush_width_set"></a>gx_context_brush_width_set


Ustaw szerokość pędzla bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_brush_width_set(UINT width);
```

### <a name="description"></a>Opis

Ta usługa ustawia szerokość aktywnego pędzla w bieżącym kontekście rysowania.

### <a name="parameters"></a>Parametry

**Szerokość** Szerokość pędzla w pikselach bieżącego kontekstu

### <a name="return-values"></a>Wartości zwrócone

**GX_SUCCESS** (0x00) ustawiono szerokość pędzla kontekstu

**GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the brush width of the current context to 10 pixels. */
status = gx_context_brush_width_set(10); /*

If status is GX_SUCCESS the brush width of the current context has been set to 10. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_color_get"></a>gx_context_color_get


Pobierz wartość koloru skojarzoną z IDENTYFIKATORem koloru w bieżącym kontekście rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_color_get(
    GX_RESOURCE_ID color_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>Opis

Ta usługa Pobiera wartość koloru skojarzoną ze wskazanym IDENTYFIKATORem koloru. Wartość koloru jest zwracana w formacie koloru aktywnego wyświetlania kontekstu. Ta usługa powinna być wywoływana tylko z poziomu aktywnej operacji rysowania.

### <a name="parameters"></a>Parametry

**color_id** Zażądano identyfikatora zasobu.

**return_color** Adres zmiennej do przechowania zwrócona wartość koloru.

### <a name="return-values"></a>Wartości zwrócone

Pobieranie pomyślnej wartości koloru **GX_SUCCESS** (0x00)

**GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu

**GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

**GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_COLOR color_value;

/* Get the color vaue. */
status = gx_context_color_get(MY_BLACK_COLOR_ID, &color_value);
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_fill_color_set"></a>gx_context_fill_color_set

Ustaw kolor wypełnienia bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_fill_color_set(GX_RESOURCE_ID fill_color_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia kolor wypełnienia aktywnego pędzla w bieżącym kontekście rysowania.

### <a name="parameters"></a>Parametry

- **fill_color_id** Identyfikator zasobu koloru wypełnienia bieżącego kontekstu. **Dodatek B** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) ustawiono kolor wypełnienia kontekstu
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the fill color of the current context to black. */
status = gx_context_fill_color_set(MY_BLACK_COLOR_ID);

/* If status is GX_SUCCESS the fill color of the current context has been set to black. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_font_get"></a>gx_context_font_get

Pobierz czcionkę skojarzoną z IDENTYFIKATORem czcionki w bieżącym kontekście rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_font_get(
    GX_RESOURCE_ID font_id,
    GX_FONT **return_font);
```

### <a name="description"></a>Opis

Ta usługa Pobiera wskaźnik czcionki skojarzony ze wskazanym IDENTYFIKATORem czcionki. Ta usługa powinna być wywoływana tylko z poziomu aktywnej operacji rysowania.

### <a name="parameters"></a>Parametry

- **font_id** Zażądano identyfikatora zasobu czcionki.
- **return_font** Adres zmiennej do przechowania zwrócony wskaźnik czcionki.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrała czcionkę
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_FONT *my_font;

/* Get the font pointer. */
status = gx_context_font_get(MY_MIDSIZE_FONT, &my_font);

/* If status is GX_SUCCESS, the font that indicated with MY_MIDSIZE_FONT has been successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_font_set"></a>gx_context_font_set

Ustaw czcionkę bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_font_set(GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia czcionkę w aktywnym pędzlu bieżącego kontekstu rysowania.

### <a name="parameters"></a>Parametry

- **font_id** Identyfikator zasobu czcionki bieżącego kontekstu

### <a name="return-values"></a>Wartości zwrócone

- Zestaw czcionek pomyślnego kontekstu **GX_SUCCESS** (0x00)
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the font of the current context to MY_FONT_ID. */
status = gx_context_font_set(MY_FONT_ID);

/* If status is GX_SUCCESS the font of the current context has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_line_color_set"></a>gx_context_line_color_set

Ustaw kolor linii bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_line_color_set(GX_RESOURCE_ID line_color_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia kolor linii aktywnego pędzla w bieżącym kontekście rysowania.

### <a name="parameters"></a>Parametry

- **line_color_id** Kolor linii bieżącego kontekstu. **Dodatek B** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) zestaw kolorów wiersza pomyślnego kontekstu
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the line color of the current context to black. */
status = gx_context_line_color_set(GX_COLOR_BLACK_ID);

/* If status is GX_SUCCESS the line color of the current context has been set to black. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_pixelmap_get"></a>gx_context_pixelmap_get

Pobierz Pixelmap skojarzone z IDENTYFIKATORem Pixelmap w bieżącym kontekście rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_pixelmap_get(
    GX_RESOURCE_ID pixelmap_id,
    GX_PIXELMAP **return_map);
```

### <a name="description"></a>Opis

Ta usługa Pobiera wskaźnik Pixelmap powiązany ze wskazanym IDENTYFIKATORem Pixelmap.

### <a name="parameters"></a>Parametry

- **pixelmap_id** Zażądano identyfikatora zasobu Pixelmap.
- **return_map** Adres zmiennej do przechowania zwrócony adres Pixelmap.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrał Pixelmap
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik Pixelmap

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_PIXELMAP *map;

/* Get the pixelmap pointer. */
status = gx_context_pixelmap_get(MY_PIXELMAP_ID, &map);

/* If status is GX_SUCCESS, the pixelmap was successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_pixelmap_set"></a>gx_context_pixelmap_set

Ustaw Pixelmap bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_pixelmap_set(GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje Pixelmap aktywnego pędzla w bieżącym kontekście rysowania.

### <a name="parameters"></a>Parametry

- **pixelmap_id** Identyfikator zasobu Pixelmap do użycia dla bieżącego kontekstu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne kontekst Pixelmap
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVLAID_CONTEXT** (0X06) Nieprawidłowy kontekst

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set pixelmap of the current context to MY_PIXELMAP_ID. */
status = gx_context_pixelmap_set(MY_PIXELMAP_ID);

/* If status is GX_SUCCESS the pixelmap of the current context has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_raw_brush_define"></a>gx_context_raw_brush_define

Zdefiniuj nieprzetworzony pędzel bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_raw_brush_define(
    GX_COLOR line_color,
    GX_COLOR fill_color, 
    UINT style);
```

### <a name="description"></a>Opis

Ta usługa definiuje surowy pędzel bieżącego kontekstu ekranu. Surowe definicje są używane, gdy 32-bitowe wartości kolorów ARGB są przesyłane do pędzla, a nie identyfikatorów kolorów. Surowe definicje kolorów są przydatne, gdy żądany kolor nie występuje w bieżącej tabeli kolorów systemu lub gdy wartość koloru RGB jest obliczana w czasie wykonywania.

### <a name="parameters"></a>Parametry

- **line_color** Kolor linii w 32-bitowym formacie koloru pierwotnego ARGB. **Dodatek A** zawiera wstępnie zdefiniowane kolory. Należy pamiętać, że aplikacja może również dodać kolory niestandardowe.
- **fill_color** Kolor wypełnienia w 32-bitowym formacie koloru pierwotnego ARGB. **Dodatek A** zawiera wstępnie zdefiniowane kolory. Należy pamiętać, że aplikacja może również dodać kolory niestandardowe.
- **styl** Styl pędzla. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — Definiowanie nieprawidłowego pędzla pierwotnego kontekstu
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Define the raw brush of the current context. */
status = gx_context_raw_brush_define(GX_COLOR_BLACK,
    GX_COLOR_BLACK, GX_STYLE_BORDER_NONE);

/* If status is GX_SUCCESS the raw brush of the current context has been defined. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_fill_color_set
- gx_context_raw_line_color_set

## <a name="gx_context_raw_fill_color_set"></a>gx_context_raw_fill_color_set

Ustaw nieprzetworzony kolor wypełnienia bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_raw_fill_color_set(GX_COLOR line_color);
```

### <a name="description"></a>Opis

Ta usługa ustawia pierwotny kolor wypełnienia bieżącego kontekstu ekranu. Parametr line_color jest 32 bitową wartością koloru w formacie ARGB, a nie wartością identyfikatora koloru. Surowe definicje kolorów są przydatne, gdy żądany kolor nie występuje w bieżącej tabeli kolorów systemu lub gdy wartość koloru RGB jest obliczana w czasie wykonywania.

### <a name="parameters"></a>Parametry

- **line_color** Kolor linii. **Dodatek A** zawiera wstępnie zdefiniowane kolory. Należy pamiętać, że aplikacja może również dodać kolory niestandardowe.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) ustawiony kolor pierwotnego wypełnienia kontekstu
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the raw fill color of the current context. */
status = gx_context_raw_fill_color_set(GX_COLOR_BLACK);

/* If status is GX_SUCCESS the raw fill color of the current context has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_line_color_set

## <a name="gx_context_raw_line_color_set"></a>gx_context_raw_line_color_set

Ustaw kolor nieprzetworzonej linii bieżącego kontekstu rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_context_raw_line_color_set(GX_COLOR line_color);
```

### <a name="description"></a>Opis

Ta usługa ustawia kolor linii aktywnego pędzla w bieżącym kontekście rysowania. Parametr line_color jest 32 bitową wartością koloru w formacie ARGB, a nie wartością identyfikatora koloru. Surowe definicje kolorów są przydatne, gdy żądany kolor nie występuje w bieżącej tabeli kolorów systemu lub gdy wartość koloru RGB jest obliczana w czasie wykonywania.

### <a name="parameters"></a>Parametry

- **line_color** Kolor wartości linii. **Dodatek A** zawiera wstępnie zdefiniowane kolory. Należy pamiętać, że aplikacja może również dodać kolory niestandardowe.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) ustawiony kolor niesformatowanego wiersza kontekstu
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

```C
/* Set the raw line color of the current context. */
status = gx_context_raw_line_color_set(GX_COLOR_BLACK);

/* If status is GX_SUCCESS the raw line color of the current context has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set

## <a name="gx_context_string_get"></a>gx_context_string_get

Pobierz ciąg skojarzony z IDENTYFIKATORem ciągu (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_context_string_get(GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **return_string);
```

### <a name="description"></a>Opis

Ten przestarzały interfejs API zwraca ciąg skojarzony z danym IDENTYFIKATORem ciągu. Nowe aplikacje powinny używać gx_context_string_get_ext ().

### <a name="parameters"></a>Parametry

- **string_id** Identyfikator ciągu wygenerowany przez aplikację GUIX Studio.
- **return_string** Adres zmiennej do zwrócenia wskaźnika ciągu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) ustawiony kolor niesformatowanego wiersza kontekstu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR *text;

status = gx_context_string_get(GX_ID_ERROR, &text);

/* If status is GX_SUCCESS the string pointer has been returned. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_string_get_ext

## <a name="gx_context_string_get_ext"></a>gx_context_string_get_ext

Pobierz ciąg skojarzony z danym IDENTYFIKATORem ciągu.

### <a name="prototype"></a>Prototype

```C
UINT gx_context_string_get_ext(
    GX_RESOURCE_ID string_id, 
    GX_STRING *return_string);
```

### <a name="description"></a>Opis

Ta usługa zwraca ciąg skojarzony z danym IDENTYFIKATORem ciągu. Ta usługa może być wywoływana tylko w przypadku aktywnego kontekstu rysowania, tj. z funkcji rysowania widżetu. Ta usługa identyfikuje aktywną kanwę i wyświetla i pobiera ciąg z zlokalizowanego wystąpienia ekranu.

### <a name="parameters"></a>Parametry

- **string_id** Identyfikator ciągu używany do identyfikowania ciągu, zgodnie z wygenerowanym przez GUIX Studio w pliku nagłówkowym zasobu aplikacji.
- **return_string** Adres zmiennej GX_STRING, w której zostanie zwrócony wskaźnik ciągu i długość ciągu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) ustawiony kolor niesformatowanego wiersza kontekstu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_CONTEXT** (0X06) nie ma aktywnego kontekstu rysowania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład


```C
GX_STRING string;

/* Set the raw line color of the current context. */
status = gx_context_string_get_ext(ID_ERROR, &string);

/* If status is GX_SUCCESS the string.gx_string_ptr and
string.gx_string_length values have been returned. */
```

### <a name="see-also"></a>Zobacz też

- gx_context_brush_default
- gx_context_brush_define
- gx_context_brush_get
- gx_context_brush_set
- gx_context_brush_pattern_set
- gx_context_brush_style_set
- gx_context_brush_width_set
- gx_context_fill_color_set
- gx_context_font_set
- gx_context_line_color_set
- gx_context_pixelmap_set
- gx_context_raw_brush_define
- gx_context_raw_fill_color_set

## <a name="gx_display_active_language_set"></a>gx_display_active_language_set

Przypisywanie aktywnego języka wyświetlania

### <a name="prototype"></a>Prototype

```C
UINT gx_display_active_language_set(
    GX_DISPLAY *display, 
    GX_UBYTE language);
```

### <a name="description"></a>Opis

Ta usługa przypisuje aktualnie aktywny język dla wskazanego ekranu. Indeks języka odpowiada językom zdefiniowanym w tabeli języka wyświetlania i nie jest identyfikatorem języka ANSI.

Różne ekrany w systemie wielu wyświetlaczy mogą uruchamiać różne języki aktywne. Tabelę języka wyświetlania należy przypisać przed użyciem tego interfejsu API. Gdy ekran zostanie zainicjowany przy użyciu gx_studio_display_configure, tabela języka zostanie automatycznie zainstalowana, a aplikacja zostanie przekazana w indeksie aktywnego języka.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **Język** Indeks aktywnego języka

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne przypisanie języka **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wyświetlania
- **GX_INVALID_VALUE** (0X22) Nieprawidłowy indeks języka

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Change value of color MY_COLOR_ID. */
status = gx_display_active_language_set(&my_display,
    LANGUAGE_ENGLISH);

/* If status is GX_SUCCESS the active language has been assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_language_table_set
- gx_studio_display_configure

## <a name="gx_display_color_set"></a>gx_display_color_set

Przypisz ponownie jedną wartość koloru

### <a name="prototype"></a>Prototype

```C
UINT gx_display_color_set(
    GX_DISPLAY *display,
    GX_RESOURCE_ID color_id, 
    GX_COLOR new_color);
```

### <a name="description"></a>Opis

Ta usługa ponownie przypisuje wartość koloru skojarzoną z określonym IDENTYFIKATORem koloru. Można go użyć do zmodyfikowania tabeli kolorów wyświetlanej bez podawania zupełnie nowej tabeli kolorów. Podana wartość koloru musi być w formacie natywnym obsługiwanym przez ekran.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **color_id** Identyfikator koloru do ponownego przypisania
- **new_color** Wartość koloru do przypisania do tego gniazda color_id

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne ponowne przypisanie koloru **GX_SUCCESS** (0x00)
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator koloru
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- Nieprawidłowe wyświetlanie **GX_INVALID_DISPLAY** (0x1D)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Change value of color MY_COLOR_ID. */
status = gx_display_color_set(&my_display, MY_COLOR_ID, 0x5454);

/* If status is GX_SUCCESS the color has been reassigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_color_table_set

## <a name="gx_display_color_table_set"></a>gx_display_color_table_set

Przypisz tabelę kolorów wyświetlania

### <a name="prototype"></a>Prototype

```C
UINT gx_display_color_table_set(
    GX_DISPLAY *display,
    GX_COLOR *color_table, 
    INT color_count);
```

### <a name="description"></a>Opis

Ta usługa ponownie przypisuje tabelę kolorów, która będzie używana przez ekran. Ta usługa jest zwykle wywoływana przez wygenerowaną funkcję konfiguracji wyświetlania GUIX Studio, ale może być również wywoływana przez oprogramowanie aplikacji.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **Color_Table** Tablica wartości kolorów w formacie natywnym.
- **color_count** Wskazuje liczbę wpisów w tabeli kolorów

### <a name="return-values"></a>Wartości zwrócone

- Zestaw tabeli kolorów pomyślnych **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- Nieprawidłowe wyświetlanie **GX_INVALID_DISPLAY** (0x1D)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_COLOR default_table[32] = { … };

/* Change the color table */
status = gx_display_color_table_set(&my_display, default_table, 32);

/* If status is GX_SUCCESS the color table has been reassigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_color_set

## <a name="gx_display_create"></a>gx_display_create

Utwórz ekran

### <a name="prototype"></a>Prototype

```C
UINT gx_display_create(
    GX_DISPLAY *display, 
    GX_CONST CHAR *name,
    UINT (*display_driver_setup)(GX_DISPLAY *),
    GX_VALUE width, 
    GX_VALUE height);
```

### <a name="description"></a>Opis

Ta usługa tworzy ekran i wywołuje funkcję instalacji sterownika wyświetlania. GUIX pobiera ten ekran i dodaje go do wewnętrznej listy wyświetlanych elementów.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **Nazwa** Nazwa wyświetlania
- **display_driver_setup** Wskaźnik wyświetlania funkcji instalacji sterownika
- **optional_driver_info** Wskaźnik do opcjonalnych informacji o sterowniku
- **color_format** Format koloru, zgodnie z definicją w **dodatku C**
- **Szerokość** Liczba pikseli na osi x
- **wysokość** Liczba pikseli na osi y

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne wyświetlenie ekranu
- **GX_SYSTEM_ERROR** (0XFE) nie można skonfigurować wyświetlania
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_SIZE** (0X23) Nieprawidłowy rozmiar bloku kontrolki wyświetlania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_DISPLAY my_display;

UINT my_driver_setup_callback(GX_DISPLAY *display)
{
    …
}

/* Create screen “my_display”. */
status = gx_display_create(&my_display, “my display”,
    my_driver_setup_callback, 320, 480);

/* If status is GX_SUCCESS, the screen “my_display” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_delete

## <a name="gx_display_delete"></a>gx_display_delete


Zniszcz ekran

### <a name="prototype"></a>Prototype

```C
UINT gx_display_delete(
    GX_DISPLAY *display,
    VOID (*display_driver_cleanup)(GX_DISPLAY *));
```

### <a name="description"></a>Opis

Ta usługa zamyka ekran i czyści przydzieloną zasoby.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **display_driver_cleanup** Wskaźnik wyświetlania funkcji oczyszczania sterownika

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne usunięcie wyświetlania **GX_SUCCESS** (0x00)
- **GX_FAILURE** (0X10) utworzona lista wyświetlania ma wartość null
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
VOID driver_cleanup_callback(GX_DISPLAY *display)
{
    …
}

/* Delete a display “my_display”. */
status = gx_display_delete(&my_display, driver_cleanup_callback);

/* If status is GX_SUCCESS the screen “my_display” has been destroyed. */
```

### <a name="see-also"></a>Zobacz też

- gx_canvas_block_move
- gx_canvas_line_draw
- gx_canvas_pixelmap_draw
- gx_canvas_pixelmap_tile
- gx_canvas_polygon_draw
- gx_canvas_rectangle_draw
- gx_canvas_text_draw
- gx_display_create

## <a name="gx_display_font_table_set"></a>gx_display_font_table_set

Przypisywanie tabeli czcionek wyświetlanych

### <a name="prototype"></a>Prototype

```C
UINT gx_display_font_table_set(
    GX_DISPLAY *display,
    GX_FONT **font_table, 
    INT table_size);
```

### <a name="description"></a>Opis

Ta usługa ponownie przypisuje tabelę czcionek, która będzie używana przez ekran. Ta usługa jest zwykle wywoływana przez wygenerowaną funkcję konfiguracji wyświetlania GUIX Studio, ale może być również wywoływana przez oprogramowanie aplikacji.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **font_table** Tablica wskaźników GX_FONT.
- **table_size** Liczba czcionek w tabeli

### <a name="return-values"></a>Wartości zwrócone

- Zestaw tabeli czcionek pomyślnych **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_FONT *font_table[32] = { … };

/* Assign font table */
status = gx_display_font_table_set(&my_display, font_table, 32);

/* If status is GX_SUCCESS, the font table has been reassigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_language_table_get"></a>gx_display_language_table_get

Pobierz tabelę języka wyświetlania (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_display_language_table_get(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE *language_count,
    UINT *string_table_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera tabelę języka z wskazanego ekranu. Ta usługa może być używana przez aplikację do modyfikowania tabeli języka wyświetlania w czasie wykonywania przy użyciu dynamicznie zdefiniowanych ciągów.

Ten interfejs API jest przestarzały i jest obsługiwany tylko w przypadku aplikacji korzystających z tabeli języka starego stylu (tj. plik zasobów wygenerowany przez program Studio jest generowany dla wersji biblioteki wcześniejszej niż wersja 5,6). Nowe aplikacje powinny używać gx_display_language_table_get_ext ().

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **tabela** Adres do otrzymania wskaźnika tabeli
- **language_count** Adres do otrzymania liczby języków
- **string_table_size** Adres odbierający rozmiar tabeli ciągów

### <a name="return-values"></a>Wartości zwrócone

- Zestaw tabeli czcionek pomyślnych **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR **language_table;
GX_UBYTE language_count;
UINT string_count;

/* Retrieve language table */
status = gx_display_language_table_get(&my_display,
        &language_table, &language_count, &string_count);

/* If status is GX_SUCCESS, the language table has been retrieved.
```

### <a name="see-also"></a>Zobacz też

- gx_display_language_table_set
- gx_display_active_langauge_set
- gx_display_string_get
- gx_display_language_table_get_ext

## <a name="gx_display_language_table_get_ext"></a>gx_display_language_table_get_ext

Pobierz tabelę języka wyświetlania

### <a name="prototype"></a>Prototype

```C
UINT gx_display_language_table_get_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE *language_count, 
    UINT *string_table_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera tabelę języka z wskazanego ekranu. Ta usługa może być używana przez aplikację do modyfikowania tabeli języka wyświetlania w czasie wykonywania przy użyciu dynamicznie zdefiniowanych ciągów.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **tabela** Adres do otrzymania wskaźnika tabeli
- **language_count** Adres do otrzymania liczby języków
- **string_table_size** Adres odbierający rozmiar tabeli ciągów

### <a name="return-values"></a>Wartości zwrócone

- Zestaw tabeli czcionek pomyślnych **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING **language_table;
GX_UBYTE language_count;
UINT string_count;

/* Retrieve language table */
status = gx_display_language_table_get_ext(&my_display,
    &language_table, &language_count, &string_count);

/* If status is GX_SUCCESS, the language table has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_language_table_set_ext
- gx_display_active_langauge_set
- gx_display_string_get_ext

## <a name="gx_display_language_table_set"></a>gx_display_language_table_set

Przypisywanie tabeli języka wyświetlania (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_display_language_table_set(
    GX_DISPLAY *display,
    GX_CHAR **table, 
    GX_UBYTE number_of_languages, 
    UINT number_of_strings);
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała, a nowe aplikacje powinny używać gx_display_language_table_set_ext (). Ta usługa jest obsługiwana tylko w przypadku zgodności z plikami zasobów wygenerowanymi przez program Studio, które są przeznaczone dla wersji biblioteki wcześniejszych niż wersja 5,6.

Ta usługa przypisuje tabelę języka, która będzie używana przez ekran. Ta usługa jest zwykle wywoływana przez funkcję wygenerowaną przez program GUIX Studio gx_studio_display_configure, ale może być również wywoływana przez oprogramowanie aplikacji.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **tabela** Tabela języka
- **number_of_languages** Liczba kolumn w podanej tabeli
- **number_of_strings** Liczba ciągów w każdej kolumnie tabeli

### <a name="return-values"></a>Wartości zwrócone

- Zestaw tabeli czcionek pomyślnych **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR ***language_table= my_app_language_table;

/* Assign language table */
status = gx_display_language_table_set(&my_display, language_table,
5, 232);

/* If status is GX_SUCCESS, the language table has been reassigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_active_language_set
- gx_display_string_get

## <a name="gx_display_language_table_set_ext"></a>gx_display_language_table_set_ext

Przypisywanie tabeli języka wyświetlania

### <a name="prototype"></a>Prototype

```C
UINT gx_display_language_table_set_ext(
    GX_DISPLAY *display,
    GX_STRING **table, 
    GX_UBYTE number_of_languages,
    UINT number_of_strings);
```

### <a name="description"></a>Opis

Ta usługa przypisuje tabelę języka, która będzie używana przez ekran. Ta usługa jest zwykle wywoływana przez funkcję wygenerowaną przez program GUIX Studio gx_studio_display_configure, ale może być również wywoływana przez oprogramowanie aplikacji.

Przypisanie tabeli języka środowiska uruchomieniowego jest zwykle wykonywane, gdy języki są ładowane z pliku zasobów binarnych przy użyciu gx_binres_language_table_load ().

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **tabela** Tabela języka
- **number_of_languages** Liczba kolumn w podanej tabeli
- **number_of_strings** Liczba ciągów w każdej kolumnie tabeli

### <a name="return-values"></a>Wartości zwrócone

- Zestaw tabeli czcionek pomyślnych **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING **language_table = my_app_language_table;

/* Assign the language table */
status = gx_display_language_table_set_ext(&my_display,
    language_table, 5, 132);

/* If status is GX_SUCCESS, the language table has been reassigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_active_language_set
- gx_display_string_get

## <a name="gx_display_pixelmap_table_set"></a>gx_display_pixelmap_table_set

Przypisywanie tabeli czcionek wyświetlanych

### <a name="prototype"></a>Prototype

```C
UINT gx_display_pixelmap_table_set(
    GX_DISPLAY *display,
    GX_PIXELMAP **pixelmap_table, 
    INT table_size);
```

### <a name="description"></a>Opis

Ta usługa ponownie przypisuje tabelę Pixelmap, która będzie używana przez ekran. Ta usługa jest zwykle wywoływana przez wygenerowaną przez program Studio funkcję konfiguracji wyświetlania, ale może być również wywoływana przez oprogramowanie aplikacji.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **pixelmap_table** Tablica wskaźników GX_PIXELMAP.
- **table_size** Liczba pixelmaps w tabeli

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawiono tabelę Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_PIXELMAP *pixelmap_table[32] = { … };

/* Assign pixelmap table */
status = gx_display_pixelmap_table_set(&my_display, pixelmap_table, 32);

/* If status is GX_SUCCESS the pixelmap table has been reassigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_color_set
- gx_display_color_table_set
- gx_display_font_table_set

## <a name="gx_display_string_get"></a>gx_display_string_get

Pobierz ciąg z aktywnej tabeli ciągów (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_display_string_get(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id, 
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_display_string_get_ext ().

Ta usługa Pobiera ciąg z aktywnej tabeli ciągów dla wskazanego wyświetlenia. Aktywny język służy do wybierania ciągu z tabeli języka przypisanej do ekranu.

Identyfikatory ciągów są generowane przez program GUIX Studio i znajdują się w pliku nagłówkowym zasobów aplikacji. h.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **string_id** Identyfikator ciągu wygenerowany przez GUIX Studio.
- **ciąg** Adres zmiennej wskaźnika ciągu

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne pobranie ciągu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator ciągu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wyświetlania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR *string;

/* Retrieve string value */
status = gx_display_string_get(&my_display,
    GX_STRING_ID_MONDAY, &string);

/* If status is GX_SUCCESS, the string has been retrieved. */
```


### <a name="see-also"></a>Zobacz też

- gx_display_active_language_set
- gx_display_language_table_set

## <a name="gx_display_string_get_ext"></a>gx_display_string_get_ext

Pobierz ciąg z aktywnej tabeli ciągów

### <a name="prototype"></a>Prototype

```C
UINT gx_display_string_get_ext(
    GX_DISPLAY *display,
    GX_RESOURCE_ID string_id,
    GX_STRING *string);
```

### <a name="description"></a>Opis

Ta usługa Pobiera ciąg z aktywnej tabeli ciągów dla wskazanego wyświetlenia. Aktywny język służy do wybierania ciągu z tabeli języka przypisanej do ekranu.

Identyfikatory ciągów są generowane przez program GUIX Studio i znajdują się w pliku nagłówkowym zasobów aplikacji. h.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **string_id** Identyfikator ciągu wygenerowany przez GUIX Studio.
- **ciąg** Adres zmiennej GX_STRING w
- **który** String.gx_string_ptr i
- zostanie zwrócona **String.gx_string_length** .

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne pobranie ciągu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator ciągu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik wyświetlania

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING string;

/* Retrieve string value */
status = gx_display_string_get_ext(&my_display,
    GX_STRING_ID_MONDAY, &string);

/* If status is GX_SUCCESS, the string has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_active_language_set
- gx_display_language_table_set


## <a name="gx_display_string_table_get"></a>gx_display_string_table_get


Pobierz aktywną tabelę ciągów (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_CHAR ***table,
    UINT *table_size);
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała i zastąpiona przez gx_display_string_table_get_ext ().

Ta usługa pobiera tabelę ciągów skojarzoną z aktywnym językiem. Ta usługa nie jest często używana, ale zapewnia kompletność dla tych aplikacji, które mogą wymagać dokonania modyfikacji w czasie wykonywania w tabeli ciągów.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **Język** Kolumna tabeli do pobrania.
- **tabela** Adres zmiennej do zwrócenia wskaźnika.
- **table_size** Adres zmiennej do zwrócenia rozmiaru tabeli

### <a name="return-values"></a>Wartości zwrócone

- Zestaw tabeli czcionek pomyślnych **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_NOT_FOUND** (0X09) Nieprawidłowy indeks języka
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR **string_table;
UINT table_size;

/* Retrieve string table */
status = gx_display_string_table_get(&my_display, LANGUAGE_ENGLISH,
    &string_table, &table_size);

/* If status is GX_SUCCESS, the string table has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_string_table_get_ext"></a>gx_display_string_table_get_ext


Pobieranie aktywnej tabeli ciągów

### <a name="prototype"></a>Prototype

```C
UINT gx_display_string_table_get(
    GX_DISPLAY *display,
    GX_UBYTE language, 
    GX_STRING **table, 
    UINT *table_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera tabelę ciągów skojarzoną z aktywnym językiem. Ta usługa nie jest często używana, ale zapewnia kompletność dla tych aplikacji, które mogą wymagać dokonania modyfikacji w czasie wykonywania w tabeli ciągów.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **Język** Kolumna tabeli do pobrania.
- **tabela** Adres zmiennej do zwrócenia wskaźnika.
- **table_size** Adres zmiennej do zwrócenia rozmiaru tabeli

### <a name="return-values"></a>Wartości zwrócone

- Zestaw tabeli czcionek pomyślnych **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_NOT_FOUND** (0X09) Nieprawidłowy indeks języka
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING *string_table;
UINT table_size;

/* Retrieve string table */
status = gx_display_string_table_get_ext(&my_display,
    LANGUAGE_ENGLISH, &string_table, &table_size);

/* If status is GX_SUCCESS, the string table has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_color_set
- gx_display_color_table_set
- gx_display_pixelmap_table_set

## <a name="gx_display_theme_install"></a>gx_display_theme_install


Zainstaluj motywy na określonym ekranie

### <a name="prototype"></a>Prototype

```C
UINT gx_display_theme_install(
    GX_DISPLAY *display, 
    GX_THEME *theme_table);
```

### <a name="description"></a>Opis

Ta usługa zainstaluje motywy na określonym ekranie. Ta usługa jest zwykle wywoływana przez wygenerowaną przez program Studio funkcję konfiguracji wyświetlania, ale może być również wywoływana przez oprogramowanie aplikacji.

### <a name="parameters"></a>Parametry

- **Wyświetl** Wskaźnik wyświetlania bloku sterowania
- **theme_table** Tabela motywów do zainstalowania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie zainstalował tabelę motywów
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik tabeli motywu
- Nieprawidłowe wyświetlanie **GX_INVALID_DISPLAY** (0x1D)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_THEME theme_1;

&theme_table[1] = {
    &theme_1,
    …
}

/* Define resource tables. */
GX_COLOR color_table[32] = {…};
GX_FONT *font_table[32] = {…};
GX_PIXELMAP *pixelmap_table[32] = { … };

/* Define scroll appearance. */
GX_SCROLLBAR_APPEARANCE scroll_appearance;

memset(&scroll_appearance, 0, sizeof(GX_SCROLLBAR_APPEARANCE));

scroll_appearance.gx_scroll_width = 20;
scroll_appearance.gx_scroll_thumb_width = 18;
scroll_appearance.gx_scroll_thumb_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_thumb_border_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_button_color =
    GX_COLOR_ID_SCROLL_BUTTON;
scroll_appearance.gx_scroll_thumb_travel_min = 20;
scroll_appearance.gx_scroll_thumb_travel_max = 20;
scroll appearance.gx_scroll_thumb_border_style =
    GX_STYLE_BORDER_THIN;

theme_1.theme_color_table = color_table;
theme_1.theme_font_table = font_table;
theme_1.theme_pixlemap_table = pixelmap_table;
theme_1.theme_palette = GX_NULL;
theme_1.theme_vertical_scrollbar_appearance = scroll_appearance;
theme_1.theme_horizontal_scrollbar_appearance = scroll_appearance;
theme_1.theme_vertical_scroll_style = GX_SCROLLBAR_RELATIVE_THUMB;
theme_1.theme_horizontal_scroll_style =
    GX_SCROLLBAR_RELATIVE_THUMB;
theme_1.theme_color_table_size = 32;
theme_1.theme_font_table_size = 32;
theme_1.theme_pixelmap_table_size = 32;
theme_1.theme_palette_size = 0;

/* Install theme table. */
status = gx_display_theme_install(&my_display, theme_table);

/* If status is GX_SUCCESS the theme table has been installed. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_color_set
- gx_display_color_table_set
- gx_display_font_table_set

## <a name="gx_drop_list_close"></a>gx_drop_list_close


Zamknij listę rozwijaną

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_close(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>Opis

Ta usługa zamyka listę rozwijaną z określoną listą docelową.

### <a name="parameters"></a>Parametry

- **drop_list** Wskaźnik do bloku kontrolki listy rozwijanej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie zamknięto listę rozwijaną
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Close a drop list. */
status = gx_drop_list_close(&drop_list);

/* If status is GX_SUCCESS, the drop list is closed. */
```

### <a name="see-also"></a>Zobacz też

- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_open

gx_drop_list_pixelmap_set, gx_drop_list_popup_get

## <a name="gx_drop_list_create"></a>gx_drop_list_create


Utwórz listę rozwijaną

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_create(
    GX_DROP_LIST *drop_list, 
    GX_CONST
    GX_CHAR *name, 
    GX_WIDGET *parent,
    INT total_rows, 
    INT open_height,
    VOID (*callback)(GX_VERTICAL_LIST *, 
    GX_WIDGET *, INT),
    ULONG style, 
    USHORT drop_list_id,
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Opis

Ta usługa tworzy listę rozwijaną. Lista rozwijana jest kombinacją widżetu listy rozwijanej i wyświetlaną pionową listą, która jest wyświetlana po otwarciu listy rozwijanej. Lista rozwijana w pionie jest tworzona automatycznie po utworzeniu widżetu list i wyświetlania lub ukrywania, gdy widżet listy rozwijanej jest otwarty lub zamknięty odpowiednio.

Widżet listy rozwijanej obsługuje dwa skojarzone pixelmaps. Pierwszy, opisany jako "tapeta listy" w widoku właściwości Studio, to opcjonalna tapeta Pixelmap, która jest wyświetlana jako tło listy pionowej, która jest wyświetlana po otwarciu widżetu listy rozwijanej. Druga Pixelmap, opisana jako "obraz tła" w widoku właściwości Studio, jest opcjonalnym obrazem wyświetlanym jako tło samego listy rozwijanej.

Widżet listy rozwijanej może mieć element widget podrzędny, który jest używany do otwierania i zamykania listy rozwijanej. Jest to zwyczajowa ikona lub widżet przycisku, ale nawet niestandardowy widżet może być używany jako przełącznik otwierania/zamykania dla nadrzędnej listy rozwijanej. Ustawienie klucza, które powoduje, że ten widżet podrzędny działa na liście rozwijanej, jest to, że ten widżet podrzędny musi mieć wstępnie zdefiniowany identyfikator widżetu ID_DROP_LIST_BUTTON.

Aby zdefiniować widżet podrzędny, który zostanie otwarty i zamknie listę rozwijaną, firstadd i podrzędny element widget na listę rozwijaną, i umieść ten element podrzędny na liście rozwijanej zgodnie z potrzebami:

![Zrzut ekranu przedstawiający listę rozwijaną.](./media/guix/image6.jpg)

Następnie za pomocą widoku właściwości programu Studio Przypisz ten element widget do wartości identyfikatora ID_DROP_LIST_BUTTON, czyli wewnętrznie zdefiniowanej przez siebie wartości identyfikatora rozpoznawanej przez nadrzędną listę rozwijaną:

![Zrzut ekranu przedstawiający widok Właściwości programu Studio.](./media/guix/image7.jpg)

### <a name="parameters"></a>Parametry
- **drop_list** Wskaźnik do bloku kontrolki listy rozwijanej
- **Nazwa** Nazwa listy rozwijanej
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **total_rows** Łączna liczba wierszy na liście rozwijanej
- **open_height** Wysokość listy pionowej wyświetlana po otwarciu listy rozwijanej.
- **wywołanie zwrotne** Funkcja wywoływana przez listę pionową, gdy lista jest przewijana. Aby uzyskać więcej informacji, zapoznaj się z dokumentacją GX_VERTICAL_LIST.
- **styl** Styl obramowania listy rozwijanej.
- **drop_list_id** Zdefiniowany przez aplikację Identyfikator listy rozwijanej
- **rozmiar** Wymiary listy rozwijanej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie Porzuć listę rozwijaną
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_DROP_LIST my_drop_list;
VOID list_row_create(GX_VERTICAL_LIST *list,
                     GX_WIDGET *row, INT index);
{
    …
}

GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 10, 10, 80, 40);

status = gx_drop_list_create(&my_drop_list,
    "my drop list", GX_NULL,
    10, 100, list_row_create,
    GX_STYLE_BORDER_RECESSED | GX_STYLE_ENABLED,
    ID_DROP_LIST, &size)

/* Is status is GX_SUCCESS, the drop list was successfully created. */
```

### <a name="see-also"></a>Zobacz również:

- gx_drop_list_close
- gx_drop_list_event_process
- gx_drop_list_open
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_event_process"></a>gx_drop_list_event_process


Zdarzenie usuwania listy rozwijanej

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_event_process(
    GX_DROP_LIST *list, 
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla listy rozwijanej.

### <a name="parameters"></a>Parametry

- **drop_list** Upuść listę rozwijaną kontrolkę widget
- **zdarzenie** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przetworzył zdarzenie usuwania listy
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic drop list event processing as part of custom event processing function. */

UINT custom_drop_list_event_process(GX_DROP_LIST *drop_list,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default drop list
            event processing */
        status = gx_drop_list_event_process(drop_list, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_open
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_open"></a>gx_drop_list_open


Otwórz listę rozwijaną

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_open(GX_DROP_LIST *drop_list);
```

### <a name="description"></a>Opis

Ta usługa otwiera wcześniej utworzoną listę rozwijaną.

### <a name="parameters"></a>Parametry

- **drop_list** Wskaźnik do bloku kontrolki listy rozwijanej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie Porzuć listę rozwijaną
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_DROP_LIST mylist;

/* Open the popup list of “mylist”. */
status = gx_drop_list_open(&mylist);

/* If status == GX_SUCCESS, the popup list of “mylist” has been displayed. */
```

### <a name="see-also"></a>Zobacz też

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_pixelmap_set
- gx_drop_list_popup_get

## <a name="gx_drop_list_pixelmap_set"></a>gx_drop_list_pixelmap_set


Przypisywanie obrazu tła do listy rozwijanej

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_pixelmap_set(
    GX_DROP_LIST *drop_list,
    GX_RESOURCE_ID id);
```

### <a name="description"></a>Opis

Przypisz obraz tła do listy rozwijanej. Ta Pixelmap jest używana jako tło dla widżetu listy rozwijanej, a nie dla wyskakującej listy pionowej, która jest wyświetlana, gdy lista jest otwarta. Aby przypisać Pixelmap do okienka podręcznego listy rozwijanej, należy najpierw wywołać gx_drop_list_popup_get, aby pobrać wskaźnik do listy podręcznej, a następnie użyć gx_window_wallpaper_set () do przypisania Pixelmap do tej listy podręcznej.

### <a name="parameters"></a>Parametry

- **drop_list** Wskaźnik do bloku kontrolki listy rozwijanej
- Identyfikator zasobu **identyfikatora** do pixlemap

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie Porzuć listę Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator pixlemap

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_DROP_LIST mylist;

/* create the drop list here */

/* Assign a pixelmap id, which will turn on the list button */
status = gx_drop_list_pixelmap_set(&mylist,
    GX_PIXELMAP_ID_DROP_LIST_BACKGROND);

/* If status is GX_SUCCESS, the pixelmap was successfully set. */
```

### <a name="see-also"></a>Zobacz również:

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_event_process
- gx_drop_list_open
- gx_drop_list_popup_get

## <a name="gx_drop_list_popup_get"></a>gx_drop_list_popup_get


Pobierz wskaźnik do listy okienka podręcznego

### <a name="prototype"></a>Prototype

```C
UINT gx_drop_list_popup_get(
    GX_DROP_LIST *drop_list,
    GX_VERTICAL_LIST **return_list);
```

### <a name="description"></a>Opis

Widżet listy rozwijanej składa się z widżetu listy rozwijanej i wyświetlaną pionową listę, która jest wyświetlana po otwarciu widżetu listy rozwijanej. Ta usługa Pobiera wskaźnik do składnika listy pionowej listy rozwijanej, umożliwiając aplikacji wywoływanie usług interfejsu API bezpośrednio na tej liście pionowej.

### <a name="parameters"></a>Parametry

- **drop_list** Wskaźnik do bloku kontrolki listy rozwijanej
- **return_list** Wskaźnik do listy pionowej przechowywanej na liście rozwijanej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrał podręczny list pionowy
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_DROP_LIST drop_list;
GX_VERTICAL_LIST *vertical_list;

/* Retrieve the popup list of “drop_list”. */
status = gx_drop_list_popup_get(&drop_list, &vertical_list)

/* If status is GX_SUCCESS, the popup list was successfully retrieved. */
```

### <a name="see-also"></a>Zobacz również:

- gx_drop_list_close
- gx_drop_list_create
- gx_drop_list_open
- gx_drop_list_pixelmap_set

## <a name="gx_horizontal_list_children_position"></a>gx_horizontal_list_children_position


Umieść elementy podrzędne dla listy poziomej

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_children_position(GX_HORIZONTAL_LIST *horizontal_list);
```

### <a name="description"></a>Opis

Ta funkcja umieszcza elementy podrzędne dla listy poziomej. Ta funkcja jest wywoływana automatycznie, gdy lista odbiera zdarzenie GX_EVENT_SHOW, ale powinna być wywoływana bezpośrednio, jeśli lista zostanie zmodyfikowana po jej udostępnieniu.

### <a name="parameters"></a>Parametry

- **horizontal_list** Wskaźnik do bloku kontrolki listy poziomej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pozycjonować elementy podrzędne dla listy poziomej
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Position children in the horizontal list */
status = gx_horizontal_list_children_position (&horizontal_list);

/* If status is GX_SUCCESS the children in the horizontal list are positioned. */
```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_create"></a>gx_horizontal_list_create


Utwórz listę poziomą

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_create(
    GX_HORIZONTAL_LIST *horizontal_list,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    INT total_columns,
    VOID (*callback)(GX_HORIZONTAL_LIST *, 
    GX_WIDGET *, INT),
    ULONG style, 
    USHORT horizontal_list_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy listę poziomą.

### <a name="parameters"></a>Parametry

- **horizontal_list** Blok kontrolny widżetu listy poziomej
- **Nazwa** Nazwa listy poziomej
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **total_columns** Łączna liczba comumns na liście poziomej
- **wywołanie zwrotne** Jest to wskaźnik do funkcji wywołania zwrotnego dostarczonej przez aplikację. Funkcja wywołania zwrotnego jest wywoływana, gdy pozioma lista jest przewijana, aby utworzyć nowo widoczne elementy listy. W ten sposób pozioma lista może wyświetlać dowolny typ widżetu zdefiniowany przez użytkownika jako elementy listy.
- **styl** Styl widżetu ScrollBar. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **horizontal_list_id** Zdefiniowany przez aplikację Identyfikator listy poziomej
- **rozmiar** Wymiary listy horitzonal

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzył listę poziomą
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Niepoprawna liczba kolumn **GX_INVALID_VALUE** (0x22)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create horizontal list “my_list” with 5 columns. */
status = gx_horizontal_list_create(&my_list, “my_list”, &my_parent,
    5, callback, GX_STYLE_WRAP, MY_LIST_ID, &size);

/* If status is GX_SUCCESS the horizontal list “my_list” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_list_children_position
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_event_process"></a>gx_horizontal_list_event_process


Zdarzenie przetworzenia listy poziomej

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla listy poziomej.

### <a name="parameters"></a>Parametry

- **Lista** Blok kontrolny widżetu listy poziomej
- **zdarzenie** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przetworzył zdarzenie listy poziomej
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Call generic horizontal list event processing as part of custom event processing function. */

UINT custom_list_event_process(
    GX_HORIZONTAL_LIST *list,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default horizontal
        list event processing */
        status =
        gx_horizontal_list_event_process(list, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_page_index_set"></a>gx_horizontal_list_page_index_set


Ustaw indeks strony początkowej

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_page_index_set(
    GX_HORIZONTAL_LIST *list,
    INT *index);
```

### <a name="description"></a>Opis

Ta usługa ustawia początkowy indeks dla listy poziomej.

### <a name="parameters"></a>Parametry

- **Lista** Blok kontrolny widżetu listy poziomej
- **indeks** Nowy indeks górny

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił indeks strony początkowej dla listy poziomej
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa wartość

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Sets the starting page index of horizontal list “my_list” as 1. */
status = gx_horizontal_list_page_index_set(&my_list, 1);

/* If status is GX_SUCCESS the starting page index of “my_list” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_index_get"></a>gx_horizontal_list_selected_index_get


Pobierz wybrany indeks wpisu z listy poziomej

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_selected_index_get(
    GX_horizobntal_LIST *horizontal_list,
    INT *return_index);
```

### <a name="description"></a>Opis

Ta usługa zwraca indeks pozycji listy poziomej.

### <a name="parameters"></a>Parametry

- **horizontal_list** Blok kontrolny widżetu listy poziomej
- **return_index** Miejsce docelowe dla indeksu listy zwracanych

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie uzyskano wpis listy poziomej
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
INT current_index_entry;

/* Get the list entry at the current index of horizontal list “my_list”. */
status = gx_horizontal_list_selected_index_get(&my_list,
    &current_index_entry);

/* If status is GX_SUCCESS, “current_index_entry” contains the current list selection index. */
```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_set"></a>gx_horizontal_list_selected_set


Przypisz wybrany wpis na liście poziomej

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_selected_set(
    GX_HORIZONATAL_LIST *horizontal_list,
    INT index);
```

### <a name="description"></a>Opis

Ta usługa przypisuje wybrany wpis na liście poziomej. W razie potrzeby pozioma lista zostanie prześwietlona, aby wyświetlić wybrany wpis.

### <a name="parameters"></a>Parametry

- **horizontal_list** Blok kontrolny widżetu listy poziomej
- **indeks** Położenie nowego wpisu listy na podstawie indeksu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił wpis listy poziomej
- Indeks **GX_FAILURE** (0x10) nie jest w nieprawidłowym zakresie
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the list entry of “my_list” to the child in line 12. */
status = gx_horizontal_list_selected_set(&my_list, 12);

/* If status is GX_SUCCESS, the list entry of “my_list” has been successfully set to 12. */
```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_selected_widget_get"></a>gx_horizontal_list_selected_widget_get


Pobierz wybrany wpis z listy poziomej

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_selected_widget_get(
    GX_horizobntal_LIST *horizontal_list,
    GX_WIDGET **return_list_entry);
```

### <a name="description"></a>Opis

Ta usługa zwraca zaznaczony wpis listy poziomej listy. Należy zauważyć, że jeśli lista pozioma zawiera więcej wierszy niż elementy podrzędne widget, a wybrany wpis został przewinięty z widoku, ten interfejs API zwróci GX_NULL, ponieważ elementy widget podrzędne są ponownie używane, ponieważ zawartość listy jest przewijana. Funkcja gx_horizontal_list_selected_index_get będzie niezawodnie zwracać indeks wybranego elementu, nawet jeśli ten element został przewinięty z widoku.

### <a name="parameters"></a>Parametry

- **horizontal_list** Blok kontrolny widżetu listy poziomej
- **return_list_entry** Miejsce docelowe dla widżetu wpisu listy zwrotnej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie uzyskano wpis listy poziomej
- **GX_FAILURE** (0X10) wybrany widżet został przewinięty z widoku na liście zawierającej więcej wierszy niż elementy podrzędne klienta.
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Get the list entry at the current index of horizontal list “my_list”. */
status = gx_horizontal_list_selected_widget_get(&my_list, &current_list_entry);

/* If status is GX_SUCCESS, “current_list_entry” contains a pointer to the currently selected widget. */

    
```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horizontal_list_selected_set
- gx_horizontal_list_total_columns_set

## <a name="gx_horizontal_list_total_columns_set"></a>gx_horizontal_list_total_columns_set


Przypisz łączną liczbę kolumn listy

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_list_total_columns_set(
    GX_HORIZONTAL_LIST *horizontal_list,
    INT count);
```

### <a name="description"></a>Opis

Ta usługa przypisuje łączną liczbę kolumn, które mają być wyświetlane na liście poziomej.

### <a name="parameters"></a>Parametry

- **horizontal_list** Blok kontrolny widżetu listy poziomej
- **Liczba** Liczba kolumn do wyświetlenia

### <a name="return-values"></a>Wartości zwrócone

- Liczba pomyślnych przydzielonych kolumn **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X10) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa wartość liczby

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Tell my list to display 20 total columns. */
status = gx_horizontal_list_total_columns_set(&my_list, 20);

/* If status is GX_SUCCESS, the total colums of “my_list” was successfully set to 20. */
```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_list_children_position
- gx_horizontal_list_create
- gx_horizontal_list_event_process
- gx_horizontal_list_page_index_set
- gx_horizontal_list_selected_index_get
- gx_horinzontal_list_selected_widget_get
- gx_horizontal_list_selected_set

## <a name="gx_horizontal_scrollbar_create"></a>gx_horizontal_scrollbar_create


Utwórz poziomy pasek przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_horizontal_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name,
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance ULONG style);
```

### <a name="description"></a>Opis

Ta usługa tworzy poziomy pasek przewijania. Identyfikator dla poziomego paska przewijania jest wstępnie zdefiniowany (ponieważ okno musi wiedzieć, jak przechwytywać zdarzenia z niego), a rozmiar jest automatyczny (ponieważ musi wypełnić szerokość klienta okna nadrzędnego). Jeśli zdecyduje się zezwolić na paski przewijania obszaru klienta, należy dodać kolejną funkcję Create z parametrami ID i size.

### <a name="parameters"></a>Parametry

- **pasek przewijania** Blok kontrolny widżetu ScrollBar
- **Nazwa** Nazwa paska przewijania
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **wygląd** Struktura wyglądu definiuje wygląd paska przewijania. Jeśli ta wartość jest GX_NULL, ScrollBar będzie używać domyślnego wyglądu ScrollBar zdefiniowanego przez gx_system_scroll_appearance_get. Zapoznaj się z **załącznikiem I** , aby zapoznać się z definicją struktury GX_SCROLLBAR_APPEARANCE.
- **Styl** Styl widżetu ScrollBar. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) powodzenie w poziomie — Tworzenie paska przewijania
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create horizontal scrollbar “my_scrollbar”. */
status = gx_horizontal_scrollbar_create(&my_scrollbar,
    “my_horizontal_scrollbar”, &my_parent, GX_NULL,
    GX_STYLE_SCROLLBAR_END_BUTTONS);

/* If status is GX_SUCCESS the horizontal scrollbar “my_scrollbar” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_icon_button_create"></a>gx_icon_button_create


Przycisk tworzenia ikony

### <a name="prototype"></a>Prototype

```C
UINT gx_icon_button_create(
    GX_ICON_BUTTON *button,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    GX_RESOURCE_ID icon_id,
    ULONG style,
    USHORT icon_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy określony widżet przycisku ikony.

GX_ICON_BUTTON pochodzi od GX_BUTTON i obsługuje wszystkie gx_button usługi interfejsu API.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku ikony
- **Nazwa** Nazwa logiczna widżetu przycisku ikony
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **icon_id** Identyfikator zasobu ikony
- **styl** Styl ikony. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **icon_button_id** Zdefiniowany przez aplikację przycisk ikony
- **rozmiar** Wymiary przycisku ikony

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — przycisk ikony został pomyślnie utworzony
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “my_icon_button”. */
status = gx_icon_button_create(&my_icon_button, “my_icon_button”,
    &my_parent,
    MY_ICON_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_ICON_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS the icon button “my_icon_button” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_button_draw"></a>gx_icon_button_draw


Rysowanie przycisku ikony

### <a name="prototype"></a>Prototype

```C
VOID gx_icon_button_draw(GX_ICON_BUTTON *button);
```

### <a name="description"></a>Opis

Ta usługa rysuje przycisk ikony. Ta funkcja jest zwykle wywoływana wewnętrznie przez GUIX w ramach operacji odświeżania kanwy, ale jest również dostępna dla aplikacji, która może chcieć udostępnić niestandardową funkcję rysowania i wywoływać domyślny rysunek przycisku ikony jako niestandardowa baza rysunku.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku ikony

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom icon draw function. */
void MyIconButtonDraw(GX_ICON_BUTTON *button)
{
    /* Do the normal drawing first */
    gx_icon_button_draw(button);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_button_pixelmap_set"></a>gx_icon_button_pixelmap_set


Ustaw Pixelmap do widżetu przycisku ikony

### <a name="prototype"></a>Prototype

```C
UINT gx_icon_button_pixelmap_set(
    GX_ICON_BUTTON *button,
    GX_RESOURCE_ID icon_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje nowy Pixelmap do widżetu przycisku ikony.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku ikony
- **icon_id** Identyfikator zasobu Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawili przycisk ikony Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set pixelmap for “my_icon_button”. */
status = gx_icon_button_pixelmap_set(&my_icon_button,
    GX_PIXELMAP_ID_ICON);

/* If status is GX_SUCCESS, the pixelmap of the icon button “my_icon_button” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_create
- gx_icon_draw
- gx_icon_pixelmap_set
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_radio_button_create
- gx_radio_button_draw gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_icon_background_draw"></a>gx_icon_background_draw


Rysuj tło ikon

### <a name="prototype"></a>Prototype

```C
VOID gx_icon_background_draw(GX_ICON *icon);
```

### <a name="description"></a>Opis

Ta usługa rysuje tło określonego widżetu ikon. Ta usługa jest zwykle wywoływana wewnętrznie przez funkcję gx_icon_button_draw, ale jest dostępna dla aplikacji, aby pomóc w tworzeniu niestandardowych funkcji rysowania.

### <a name="parameters"></a>Parametry

- **ikona** Wskaźnik do bloku kontrolki widżetu ikona

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom icon draw function. */
void MyIconButtonDraw(GX_ICON *icon)
{
    /* Call icon background draw. */
    gx_icon_background_draw(icon);

    /* Add custom drawing here */

    /* Draw child widgets. */
    gx_widget_children_draw(icon);
}
```

### <a name="see-also"></a>Zobacz też

- gx_icon_create
- gx_icon_draw
- gx_icon_event_process
- gx_icon_pixelmap_set

## <a name="gx_icon_create"></a>gx_icon_create


Ikona tworzenia

### <a name="prototype"></a>Prototype

```C
UINT gx_icon_create(
    GX_ICON *icon, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID pixelmap_id, 
    ULONG style,
    USHORT icon_id, 
    GX_VALUE x, 
    GX_VALUE y);
```

### <a name="description"></a>Opis

Ta usługa tworzy określony widżet ikony.

### <a name="parameters"></a>Parametry

- **ikona** Wskaźnik do bloku kontrolki ikona
- **Nazwa** Nazwa logiczna widżetu ikony
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **pixelmap_id** Identyfikator zasobu Pixelmap
- **styl** Styl ikony
- **icon_id** Zdefiniowany przez aplikację identyfikator ikony
- **x** początkowa pozycja współrzędnej x
- **y** , początkowa pozycja współrzędnej y

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne Tworzenie ikony **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “my_icon”. */
status = gx_icon_create(&my_icon, “my_icon”, &my_parent,
    MY_PIXELMAP_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_ICON_ID,
    5, 30);

/* If status is GX_SUCCESS the icon “my_icon” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_icon_button_create
- gx_icon_draw
- gx_icon_pixelmap_set

## <a name="gx_icon_draw"></a>gx_icon_draw


Ikona rysowania

### <a name="prototype"></a>Prototype

```C
VOID gx_icon_draw(GX_ICON *icon);
```

### <a name="description"></a>Opis

Ta usługa Rysuje określony widżet ikon. Ta usługa jest zwykle wywoływana wewnętrznie przez GUIX w ramach operacji odświeżania kanwy, ale jest również dostępna dla aplikacji, która może chcieć udostępnić funkcję rysowania niestandardowego i wywoływać domyślny rysunek ikony jako niestandardowa baza rysunku.

### <a name="parameters"></a>Parametry

- **ikona** Wskaźnik do bloku kontrolki widżetu ikona

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom icon drawing function. */

VOID my_icon_draw(GX_MENU *menu)
{
    /* Call default icon draw. */
    gx_icon_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_icon_button_create
- gx_icon_create
- gx_icon_pixelmap_set

## <a name="gx_icon_event_process"></a>gx_icon_event_process

Przetwarzanie zdarzenia widżetu ikony

### <a name="prototype"></a>Prototype

```C
UINT gx_icon_event_process(
    GX_ICON *icon, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa obsługuje zdarzenia wysyłane do widżetu GX_ICON.

### <a name="parameters"></a>Parametry

- **ikona** Wskaźnik do bloku kontrolki widżetu ikona
- **event_ptr** Wskaźnik do GX_EVENT struktury

### <a name="return-values"></a>Wartości zwrócone

- Zdarzenie ikony przetworzonej **GX_SUCCESS** (0X00) zostało zakończone pomyślnie
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
switch(event_ptr->gx_event_type)
{
case GX_EVENT_SHOW:
    /* Do default handling. */
    status = gx_icon_event_process(icon, event_ptr);

    /* add your own handling here */
    break;
}
```

### <a name="see-also"></a>Zobacz też

- gx_icon_button_create
- gx_icon_create
- gx_icon_pixelmap_set

## <a name="gx_icon_pixelmap_set"></a>gx_icon_pixelmap_set


Ustaw Pixelmap dla ikony

### <a name="prototype"></a>Prototype

```C
UINT gx_icon_pixelmap_set(
    GX_ICON *icon, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia Pixelmap dla określonego widżetu ikony.

### <a name="parameters"></a>Parametry

- **ikona** Wskaźnik do bloku kontrolki widżetu ikona
- **normal_id** Identyfikator zasobu stanu normalnego
- **selected_id** Identyfikator zasobu wybranego stanu

### <a name="return-values"></a>Wartości zwrócone

- Ikona pomyślnego Pixelmap (0x00) **GX_SUCCESS**
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set pixelmap for “my_icon”. */
status = gx_icon_pixelmap_set(&my_icon,
    MY_NOT_SELECTED_RESOURCE_ID,
    MY_SELECTED_ID);

/* If status is GX_SUCCESS, the icon “my_icon” has a pixelmap set. */
```

### <a name="see-also"></a>Zobacz też

- gx_icon_button_create
- gx_icon_create
- gx_icon_draw

## <a name="gx_image_reader_create"></a>gx_image_reader_create


Utwórz wystąpienie modułu czytnika obrazu

### <a name="prototype"></a>Prototype

```C
UINT gx_image_reader_create(
    GX_IMAGE_READER *image_reader,
    GX_CONST GX_UBYTE *data, 
    INT data_size,
    GX_UBYTE color_format, 
    GX_UBYTE mode);
```

### <a name="description"></a>Opis

Ta funkcja tworzy niesformatowany czytnik/dekoder obrazu środowiska uruchomieniowego. Obsługiwane są obecnie tylko typy obrazów RAW JPEG i PNG. Ta usługa wymaga zdefiniowania GX_SOFTWARE_DECODER_SUPPORT.

### <a name="parameters"></a>Parametry

- **image_reader** Blok sterowania czytnika obrazu
- **dane** Wskaźnik do nieprzetworzonych danych wejściowych.
- **data_size** Rozmiar nieprzetworzonych danych wejściowych.
- **color_format** Żądany format koloru wyjściowego.
- **tryb** Flagi kompresji, symulowania i trybów alfa.

### <a name="return-values"></a>Wartości zwrócone

- Zakończono Tworzenie czytnika obrazu **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE** (0X22) Nieprawidłowy rozmiar danych

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_IMAGE_READER my_image_reader;

“color format” could be set to:
    GX_COLOR_FORMAT_32ARGB
    GX_COLOR_FORMAT_24RGB
    GX_COLOR_FORMAT_565RGB
    GX_COLOR_FORMAT_8BIT_PALETTE

/* Create image reader “my_image_reader”. */
status = gx_image_reader_create(&my_image_reader, decoder_data,
    decoder_data_size,
    GX_COLOR_FORMAT_32ARGB,
    GX_IMAGE_READER_MODE_COMPRESS)

/* If status is GX_SUCCESS, “my_image_reader” has been successfully created. */
```

### <a name="see-also"></a>Zobacz też

- gx_image_reader_start
- gx_image_reader_palette_set

## <a name="gx_image_reader_palette_set"></a>gx_image_reader_palette_set


Zdefiniuj paletę czytnika obrazu

### <a name="prototype"></a>Prototype

```C
UINT gx_image_reader_palette_set(
    GX_IMAGE_READER *image_reader,
    GX_COLOR *pal,
    UINT palsize);
```

### <a name="description"></a>Opis

Ta usługa ustawia paletę dla bloku kontroli czytnika obrazu. Ta usługa wymaga zdefiniowania GX_SOFTWARE_DECODER_SUPPORT.

### <a name="parameters"></a>Parametry

- **image_reader** Blok sterowania czytnika obrazu
- **PAL** Wskaźnik do palety
- **palsize** Rozmiar palety

### <a name="return-values"></a>Wartości zwrócone

- Zestaw palet czytnika obrazów pomyślnych **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE** (0X22) Nieprawidłowy rozmiar palety

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set “my_palette” as the palette of “my_image_reader”. */
status = gx_image_reader_palette_set(&my_image_reader, my_palette,
    my_palette_size);

/* If status is GX_SUCCESS the palette of “my_image_reader” has been set to “my_palette”. */
```

### <a name="see-also"></a>Zobacz też

- gx_image_reader_create
- gx_image_reader_start

## <a name="gx_image_reader_start"></a>gx_image_reader_start

Rozpocznij proces dekompresowania i konwersji

### <a name="prototype"></a>Prototype

```C
UINT gx_image_reader_start(
    GX_IMAGE_READER *image_reader, 
    GX_PIXELMAP *outmap);
```

### <a name="description"></a>Opis

Ta usługa dekoduje obraz nieprzetworzony do określonego formatu koloru. Obsługiwane są obecnie tylko typy obrazów RAW JPEG i PNG. Wymaga to zdefiniowania GX_SOFTWARE_DECODER_SUPPORT.

### <a name="parameters"></a>Parametry

- **image_reader** Blok sterowania czytnika obrazu
- **Pixelmap** Pixelmap wyjściowy

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne odkodowanie obrazu **GX_SUCCESS** (0x00)
- Program przydzielania pamięci **GX_SYSTEM_MEMORY_ERROR** (0x30) nie został zdefiniowany lub alokacja pamięci nie powiodła się
- Typ obrazu wejściowego **GX_NOT_SUPPORTED** (0x28) lub format koloru wyjściowego nie jest obsługiwany
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_IMAGE_READER my_image_reader;
GX_PIXELMAP output_map;

/* Create my_image_reader here. */

/* Decoding a raw image according to the settings of “my_image_reader”. */
status = gx_image_reader_start(&my_image_reader, output_map)

/* If status is GX_SUCCESS “output_map” have been loaded with the requested pixelmap. */
```

### <a name="see-also"></a>Zobacz też

- gx_image_reader_create
- gx_image_reader_palette_set

## <a name="gx_line_chart_axis_draw"></a>gx_line_chart_axis_draw


Rysowanie wykresu liniowego x, oś y

### <a name="prototype"></a>Prototype

```C
VOID gx_line_chart_axis_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Opis

Ta usługa rysuje oś x, y wykresu liniowego. Kolory osi i parametry szerokości linii są pobierane z struktury informacji wykresu liniowego.

Ta usługa jest zwykle wywoływana wewnętrznie przez funkcję gx_line_chart_draw, ale jest dostępna dla aplikacji, aby pomóc w tworzeniu niestandardowych funkcji rysowania.

### <a name="parameters"></a>Parametry

- **Wykres** Blok sterowania wykresem liniowym.

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default window draw. */
    gx_window_draw((GX_WINDOW *)chart);

    /* Draw the line chart axis. */
    gx_line_chart_axis_draw(&chart->gx_line_chart_info);

    /* Draw the data line */
    gx_line_chart_data_draw(&chart->gx_line_chart_info);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_create"></a>gx_line_chart_create


Utwórz widżet GX_LINE_CHART

### <a name="prototype"></a>Prototype

```C
UINT gx_line_chart_create(
    GX_LINE_CHART *chart,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_LINE_CHART_INFO *info,
    ULONG style,
    USHORT chart_id, GX_RECTANGLE *size)
```

### <a name="description"></a>Opis

Ta usługa tworzy okno wykresu liniowego. Parametry i dane wykresu rysowania wykresu są przesyłane za pośrednictwem struktury GX_LINE_CHART_INFO.

GX_LINE_CHART jest oparta na GX_WINDOW i obsługuje wszystkie GX_WINDOW interfejsy API.

### <a name="parameters"></a>Parametry

- **Wykres** Wskaźnik do bloku sterowania GX_LINE_CHART.
- **Nazwa** Opcjonalna nazwa wykresu liniowego
- **element nadrzędny** Element widget elementu nadrzędnego lub GX_NULL
- **informacje** Struktura definiująca parametry rysowania wykresu liniowego. **Dodatek I** zawiera definicję do GX_LINE_CHART_INFO struktury.
- **styl** Flagi stylu widżetu
- **chart_id** Wartość identyfikatora logicznego wykresu
- **rozmiar** Prostokąt ograniczający okna wykresu

### <a name="return-values"></a>Wartości zwrócone

- Tworzenie wykresu liniowego w **GX_SUCCESS** (0x00) powiodło się
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create a line chart */
GX_LINE_CHART chart;
GX_RECTANGLE chart_size;
GX_LINE_CHART_INFO gx_chart_info;
GX_WINDOW_ROOT *root_window;

chart_size = root_window->gx_widget_size;

/* Initialize params for the GUIX base chart. */
gx_chart_info.gx_line_chart_min_val = DATA_MIN_VAL;
gx_chart_info.gx_line_chart_max_val = DATA_MAX_VAL;
gx_chart_info.gx_line_chart_max_data_count = MAX_DATA_COUNT;
gx_chart_info.gx_line_chart_active_data_count = 0;
gx_chart_info.gx_line_chart_axis_line_width = AXIS_LINE_WIDTH;
gx_chart_info.gx_line_chart_data_line_width = DATA_LINE_WIDTH;
gx_chart_info.gx_line_chart_data = chart_data;
gx_chart_info.gx_line_chart_line_color = GX_COLOR_ID_DATA_LINE;
gx_chart_info.gx_line_chart_axis_color = GX_COLOR_ID_AXIS_LINE;

/* Leave room for labels on bottom and right. */
gx_chart_info.gx_line_chart_left_margin = 0;
gx_chart_info.gx_line_chart_top_margin = 0;
gx_chart_info.gx_line_chart_right_margin = 80;
gx_chart_info.gx_line_chart_bottom_margin = 32;

status = gx_line_chart_create(&chart, “Line Chart”, root_window,
    &gx_chart_info, GX_STYLE_NONE, &chart_size);

/* If status is GX_SUCCESS, the “chart” has been successfully created. */
```

### <a name="see-also"></a>Zobacz też

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_data_draw"></a>gx_line_chart_data_draw


Rysowanie linii danych wykresu liniowego

### <a name="prototype"></a>Prototype

```C
VOID gx_line_chart_data_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Opis

Ta usługa rysuje wiersz danych wykresu liniowego. Kolory linii i parametry szerokości linii są pobierane z struktury informacji wykresu liniowego.

Ta usługa jest zwykle wywoływana wewnętrznie przez funkcję gx_line_chart_draw, ale jest dostępna dla aplikacji, aby pomóc w tworzeniu niestandardowych funkcji rysowania.

### <a name="parameters"></a>Parametry

- **Wykres** Blok sterowania wykresem liniowym

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default window draw. */
    gx_window_draw((GX_WINDOW *)chart);

    /* Draw the line chart axis. */
    gx_line_chart_axis_draw(chart);

    /* Draw the data line. */
    gx_line_chart_data_draw(chart);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_line_chart_create
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_draw"></a>gx_line_chart_draw


Rysowanie wykresu liniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_line_chart_draw(GX_LINE_CHART *chart);
```

### <a name="description"></a>Opis

Jest to domyślna funkcja rysowania wykresu liniowego, która rysuje oś wykresu i linię danych. Aplikacje zwykle zapewniają niestandardową funkcję rysowania, która zastąpi domyślny rysunek, aby dodać elementy, takie jak znaczniki, Scale lub inne informacje do osi wykresu i linii danych rysowanej przez widżet wykres liniowy linii bazowej.

### <a name="parameters"></a>Parametry

- **Wykres** Wskaźnik do bloku kontrolki wykres liniowy.

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom chart drawing function. */

VOID my_chart_draw(GX_LINE_CHART *chart)
{
    /* Call default line chart draw. */
    gx_line_chart_draw(chart);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_line_chart_create
- gx_line_chart_draw
- gx_line_chart_update
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_update"></a>gx_line_chart_update


Aktualizuj wiersz danych wykresu liniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_line_chart_update(
    GX_LINE_CHART *chart, 
    INT *data,
    INT data_count)
```

### <a name="description"></a>Opis

Ta usługa aktualizuje tablicę danych wykreśloną przez okno wykresu liniowego i Wymusza ponowne narysowanie okna.

### <a name="parameters"></a>Parametry

- **Wykres** Blok sterowania wykresem liniowym
- **dane** Tablica danych do wykreślenia
- **data_count** Rozmiar tablicy danych

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — pomyślne utworzenie przycisku tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
INT chart_data[100];
GX_LINE_CHART chart;

/* Update the data array associated with “chart”. */
status = gx_line_chart_update(&chart, chart_data, 100);

/* If status is GX_SUCCESS, the line chart data has been updated. */
```

### <a name="see-also"></a>Zobacz też

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_y_scale_calculate

## <a name="gx_line_chart_y_scale_calculate"></a>gx_line_chart_y_scale_calculate


Oblicz wartość skalowania osi y ze stałą punktem

### <a name="prototype"></a>Prototype

```C
UINT gx_line_chart_y_scale_calculate(
    GX_LINE_CHART *chart,
    INT *return_val);
```

### <a name="description"></a>Opis

Ta usługa oblicza wartość skalowania ustalonego służącą do wykreślania wartości danych na osi Y wykresu. Parametry chart_info i prostokąt ograniczający wykres są używane do obliczania wartości skalowania.

### <a name="parameters"></a>Parametry

- **Wykres** Blok sterowania wykresem liniowym
- **return_val** Adres wartości do przechowywania wartości zwracanej przez punkt trwały.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — Oblicz pomyślnie wartość skali y
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_LINE_CHART chart;
INT y_scale;

/* Caluclate y scale value of “chart”. */
status = gx_line_chart_y_scale_calculate(&chart, &y_scale);

/* If status is GX_SUCCESS, y scale value of “chart” has been calculated. */
```

### <a name="see-also"></a>Zobacz też

- gx_line_chart_create
- gx_line_chart_data_draw
- gx_line_chart_draw
- gx_line_chart_update

## <a name="gx_menu_create"></a>gx_menu_create


Tworzenie menu

### <a name="prototype"></a>Prototype

```C
UINT gx_menu_create(
    GX_MENU *menu,GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    GX_RESOURCE_ID fill_id, 
    ULONG style, 
    USHORT menu_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy menu jako wybrane i kojarzy menu z dostarczonym widżetem nadrzędnym. Akceptuje wszystkie typy widżetów jako element menu podrzędnego. Aby wstawić widżet jako element menu podrzędnego, wywołaj **gx_menu_insert**.

GX_MENU pochodzi od GX_PIXELMAP_PROMPT i obsługuje wszystkie gx_pixelmap_prompt usługi interfejsu API.

### <a name="parameters"></a>Parametry

- **menu** Wskaźnik do bloku kontrolki menu
- **Nazwa** Nazwa menu
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **text_id** Identyfikator zasobu tekstu
- **fill_id** Identyfikator zasobu wypełnienia
- **styl** Styl elementu widget. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **menu_id** Zdefiniowany przez aplikację identyfikator menu
- **rozmiar** Rozmiar menu

### <a name="return-values"></a>Wartości zwrócone

- Tworzenie menu **GX_SUCCESS** (0x00) powiodło się
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_MENU my_menu;

/* Create “my_menu”. */
status = gx_menu_create(&my_menu, “my_menu”, parent, MY_TEXT_ID,
    MY_FILL_ID, GX_STYLE_ENABLED, MY_MENU_ID,
    &size);

/* If status is GX_SUCCESS, the menu was successfully created. */
```

### <a name="see-also"></a>Zobacz też

- gx_accordion_meu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_draw"></a>gx_menu_draw


Menu Rysuj

### <a name="prototype"></a>Prototype

```C
VOID gx_menu_draw(GX_MENU *menu);
```

### <a name="description"></a>Opis

Ta usługa służy do rysowania określonego menu. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest uwidaczniana dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania niestandardowych widżetów menu.

### <a name="parameters"></a>Parametry

- **menu** Wskaźnik do bloku kontrolki menu

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom menu drawing function. */

VOID my_menu_draw(GX_MENU *menu)
{
    /* Call default menu draw. */
    gx_menu_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_event_process"></a>gx_menu_event_process

Zdarzenie menu procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_menu_event_process(GX_MENU *menu, GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego menu. Ta usługa powinna być wywoływana jako domyślna procedura obsługi zdarzeń za pomocą wszelkich funkcji niestandardowego przetwarzania zdarzeń menu.

### <a name="parameters"></a>Parametry

- **menu** Wskaźnik do bloku kontrolki menu
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia menu zakończono pomyślnie **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x23) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic menu event processing as part of custom event processing function. */

UINT custom_menu_event_process(GX_MENU *menu, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */

        /* Call default event process if this is a system event such as GX_EVENT_SHOW. */
        status = gx_menu_event_process(menu, event);
        break;

    default:
        /* Pass all other events to the default menu
           event processing */
        status = gx_menu_event_process(menu, event);
        break;
    }
    return status;
}

```

### <a name="see-also"></a>Zobacz też

- gx_menu_create
- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_insert"></a>gx_menu_insert


Wstaw nowy element

### <a name="prototype"></a>Prototype

```C
UINT gx_menu_insert(
    GX_MENU *menu, 
    GX_WIDGET *insert);
```

### <a name="description"></a>Opis

Ta usługa wstawia nowy element do menu.

### <a name="parameters"></a>Parametry

- **menu** Wskaźnik do bloku kontrolki menu
- element **widget** Wskaźnik do widżetu do wstawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie wstawiono nowy element do menu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Insert new item “my_widget” to the menu “my_menu”. */
status = gx_menu_insert(&my_menu, &my_widget);

/* If status is GX_SUCCESS the new item “my_widget” has been inserted to the menu “my_menu”. */
```

### <a name="see-also"></a>Zobacz też

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_remove"></a>gx_menu_remove


Usuń element

### <a name="prototype"></a>Prototype

```C
UINT gx_menu_remvoe(
    GX_MENU *menu, 
    GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa usuwa element z menu.

### <a name="parameters"></a>Parametry

- **menu** Wskaźnik do bloku kontrolki menu
- element **widget** Wskaźnik do elementu widget do usunięcia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie usunął element menu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Remove item “my_widget” from menu “my_menu” */
status = gx_menu_remove(&my_menu, &my_widget);

/* If status is GX_SUCCESS the item “my_widget” has been removed from menu “my_menu”. */
```

### <a name="see-also"></a>Zobacz też

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_text_draw
- gx_menu_text_offset_set

## <a name="gx_menu_text_draw"></a>gx_menu_text_draw


Rysuj tekst menu

### <a name="prototype"></a>Prototype

```C
VOID gx_menu_text_draw(GX_MENU *menu);
```

### <a name="description"></a>Opis

Ta usługa rysuje tekst menu. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest uwidaczniana dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania niestandardowych widżetów menu.

### <a name="parameters"></a>Parametry

- **menu** Wskaźnik do bloku kontrolki menu

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom menu drawing function. */

VOID my_menu_draw(GX_MENU *menu)
{
    /* Call default menu background draw. */
    gx_pixelmap_prompt_background_draw(
                            (GX_PIXELMAP_PROMPT *)menu);

    /* Draw menu text. */
    gx_menu_text_draw(menu);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_offset_set

## <a name="gx_menu_text_offset_set"></a>gx_menu_text_offset_set


Ustaw przesunięcie rysowania tekstu menu

### <a name="prototype"></a>Prototype

```C
UINT gx_menu_text_offset_set(
    GX_MENU *menu, 
    GX_VALUE x_offset,
    GX_VALUE y_offset);
```

### <a name="description"></a>Opis

Ta usługa ustawia przesunięcie x, y dla tekstu menu.

### <a name="parameters"></a>Parametry

- **menu** Wskaźnik do bloku kontrolki menu
- **x_offset** Współrzędna X przesunięcia
- **y_offset** Współrzędna Y przesunięcia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne Ustawianie przesunięcia tekstu menu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set text draw offset of menu “my_menu” to (20, 10). */
status = gx_menu_text_offset_set(&my_menu, 20, 10);

/* If status is GX_SUCCESS the text draw offset of menu “my_menu” has been set to (20, 10). */
```

### <a name="see-also"></a>Zobacz też

- gx_accordion_menu_create
- gx_accordion_menu_draw
- gx_accordion_menu_event_process
- gx_accordion_menu_position
- gx_menu_create
- gx_menu_draw
- gx_menu_event_process
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw

## <a name="gx_multi_line_text_button_create"></a>gx_multi_line_text_button_create


Przycisk tworzenia tekstu wielowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_button_create(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    ULONG style,
    USHORT text_button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet przycisku tekstu wielowierszowego. Przycisk tekstu wielowierszowego wyświetla tekst przycisku nad wierszami 1-n. Maksymalna liczba wierszy jest definiowana przez stałą GX_MULTI_LINE_TEXT_BUTTON_MAX_LINES, która domyślnie przyjmuje wartość 4. Podziały wierszy są ustawiane za pomocą powrotu karetki i/lub powrotu karetki + par wysuwu wiersza w ciągu tekstowym przypisanym do przycisku tekstu wielowierszowego.

GX_MULTI_LINE_TEXT_BUTTON pochodzi od GX_TEXT_BUTTON i obsługuje wszystkie gx_text_button usługi interfejsu API.

### <a name="parameters"></a>Parametry

- **text_button** Wskaźnik do bloku kontrolki przycisku tekstowego
- **Nazwa** Nazwa logiczna przycisku tekstu
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget przycisku
- **text_id** Identyfikator zasobu tekstu
- **styl** Styl przycisku tekstu. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **text_button_id** Zdefiniowany przez aplikację identyfikator przycisku tekstu
- **rozmiar** Rozmiar przycisku

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne utworzenie wielowierszowego przycisku tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create multi-line text button “my_text_button”. */
status = gx_multi_line_text_button_create(&my_text_button, "my text button",
    &my_parent_window, MY_TEXT_RESOURCE_ID,
    GX_STYLE_BUTTON_TOGGLE, MY_TEXT_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS, the multi-line text button “my_text_button” was created. */
```

### <a name="see-also"></a>Zobacz też

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_draw"></a>gx_multi_line_text_button_draw


Przycisk rysowania wielowierszowego tekstu

### <a name="prototype"></a>Prototype

```C
VOID gx_multi_line_text_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button);
```

### <a name="description"></a>Opis

Ta usługa rysuje przycisk tekstu wielowierszowego. Ta funkcja jest zwykle wywoływana wewnętrznie przez GUIX w ramach operacji odświeżania kanwy, ale jest również narażona na aplikację, która może chcieć udostępnić niestandardową funkcję rysowania i wywoływać domyślny rysunek wielowierszowego rysunku przycisku tekstu jako niestandardowa baza rysunku.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku tekstowego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Draw the text button “my_text_button”. */
void MyButtonDraw(GX_MULTI_LINE_TEXT_BUTTON *button)
{
    /* Do the normal drawing first */
    gx_multi_line_text_button_draw(&my_text_button);

    /* Add custom drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_event_process"></a>gx_multi_line_text_button_event_process


Domyślna obsługa zdarzeń dla wielowierszowego przycisku tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_button_event_process(
    GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa jest domyślną funkcją obsługi zdarzeń dla widżetu przycisk tekstu wielowierszowego. Ta funkcja jest dostępna dla aplikacji, które chcą zapewnić obsługę zdarzeń niestandardowych widżetu przycisk tekstu.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku tekstowego
- **event_ptr** Zdarzenie do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Zdarzenie **GX_SUCCESS** (0X00) zostało pomyślnie obsłużone
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT MyEventHandler(GX_MULTI_LINE_TEXT_BUTTON *button,
    GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case GX_EVENT_SHOW:
        gx_multi_line_text_button_event_process(button, event_ptr);
        /* add custom actions here */
        break;
    default:
        gx_multi_line_text_button_event_process(button, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>Zobacz też

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_draw"></a>gx_multi_line_text_button_text_draw


Funkcja obsługi rysowania

### <a name="prototype"></a>Prototype

```C
VOID gx_multi_line_text_button_text_draw(GX_MULTI_LINE_TEXT_BUTTON *text_button);
```

### <a name="description"></a>Opis

Ta funkcja obsługi służy do rysowania części tekstowej wielowierszowego przycisku tekstu. Ta funkcja jest wywoływana wewnętrznie przez gx_multi_line_text_button_draw () i jest udostępniana jako osobny interfejs API jako wygoda dla aplikacji, które definiują niestandardową funkcję rysowania wielowierszowego tekstu. Aplikacje, które chcą dostosować Rysowanie w tle przycisków, mogą zapewnić swoją niestandardową funkcję rysowania i wywoływać usługę multi_line_text_button_text_draw jako część niestandardowego rysunku, aby narysować tekst przycisku w tle.

### <a name="parameters"></a>Parametry

- **text_button** Wskaźnik do bloku kontrolki przycisku tekstowego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Define a custom drawing function */
VOID my_button_draw(GX_MULTI_LINE_TEXT_BUTTON *button)
{
    /* insert code here to draw button background */

    /* call support function to do text drawing */
    gx_multi_line_text_button_text_draw();

    /* draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) button);
}
```

### <a name="see-also"></a>Zobacz też

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set


## <a name="gx_multi_line_text_button_text_id_set"></a>gx_multi_line_text_button_text_id_set


Ustaw identyfikator zasobu tekstowego na przycisk tekst

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_button_text_id_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id)
```

### <a name="description"></a>Opis

Ta usługa Ustawia określony identyfikator zasobu ciągu na przycisk tekst. Ciąg może zawierać znaki nowego wiersza, które działają do wyświetlania tekstu w wielu wierszach w obszarze przycisku.

### <a name="parameters"></a>Parametry

- **text_button** Wskaźnik do bloku kontrolki przycisku tekstowego
- **string_id** Identyfikator zasobu ciągu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił identyfikator zasobu ciągu na przycisk tekstowy
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the string ID ”MY_STRING_ID” to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_id_set(
    &my_text_button, MY_STRING_ID);

/* If status is GX_SUCCESS, the string ID MY_STRING_ID was set to “my_text_button”. */
```

### <a name="see-also"></a>Zobacz też

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_set"></a>gx_multi_line_text_button_text_set


Przypisywanie tekstu do przycisku tekstu (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_mult_line_text_button_text_set(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_multi_line_text_button_text_set_ext ().

Ta usługa przypisuje określony ciąg do przycisku tekstu. Jeśli element widget text_button został utworzony przy użyciu GX_STYLE_TEXT_COPY stylu, widżet tworzy prywatną kopię ciągu tekstowego, a w związku z tym interfejs API gx_system_memmory_allocate_set musi zostać wywołany raz przed zażądaniem tej usługi. Jeśli GX_STYLE_TEXT_COPY nie jest aktywny, widżet nie tworzy prywatnej kopii ciągu przychodzącego, w związku z czym ciąg musi być statycznie lub globalnie przydzielony, tj. nie może to być automatyczna lub Tymczasowa zmienna.

### <a name="parameters"></a>Parametry

- **text_button** Wskaźnik do bloku kontrolki przycisku tekstowego
- wskaźnik **tekstowy** na ciąg zakończony ZNAKiem null

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił tekst na przycisk
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Nie zdefiniowano alokatora pamięci **GX_MEMORY_ERROR** (0x30)
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
static GX_CHAR text[] = “myrstring”;

/* Set text to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_set(&my_text_button, text);

/* If status is GX_SUCCESS, the text of “my_text_button” was set. */
```

### <a name="see-also"></a>Zobacz też

- gx_text_button_create
- gx_button_create
- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_button_text_set_ext"></a>gx_multi_line_text_button_text_set_ext


Przypisywanie tekstu do przycisku tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_mult_line_text_button_text_set_ext(
    GX_MULTI_LINE_TEXT_BUTTON *text_button,
    GX_STRING *string)
```

### <a name="description"></a>Opis

Ta usługa przypisuje określony ciąg do przycisku tekstu. Jeśli element widget text_button został utworzony przy użyciu GX_STYLE_TEXT_COPY stylu, widżet tworzy prywatną kopię ciągu tekstowego, a w związku z tym interfejs API gx_system_memmory_allocate_set musi zostać wywołany raz przed zażądaniem tej usługi. Jeśli GX_STYLE_TEXT_COPY nie jest aktywny, widżet nie tworzy prywatnej kopii ciągu przychodzącego, w związku z czym ciąg musi być statycznie lub globalnie przydzielony, tj. nie może to być automatyczna lub Tymczasowa zmienna.

### <a name="parameters"></a>Parametry

- **text_button** Wskaźnik do bloku kontrolki przycisku tekstowego
- wskaźnik **ciągu** do GX_STRING zmiennej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił tekst na przycisk
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Nie zdefiniowano alokatora pamięci **GX_MEMORY_ERROR** (0x30)
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
static GX_CHAR text[] = “myrstring”;
GX_STRING string;

string.gx_string_ptr = text;
string.gx_string_length = strlen(text);

/* Set text to the text button “my_text_button”. */
status = gx_multi_line_text_button_text_set_ext(&my_text_button, string);

/* If status is GX_SUCCESS, the text of “my_text_button” was set. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_button_draw
- gx_multi_line_text_button_event_process
- gx_multi_line_text_button_text_set
- gx_multi_line_text_button_text_id_set

## <a name="gx_multi_line_text_input_backspace"></a>gx_multi_line_text_input_backspace


Usuń znak przed pozycją kursora tekstu wielowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_backspace(
    GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa usuwa znak przed pozycją kursora wielowierszowego wprowadzania tekstu. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia klawisza Backspace w dół, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pomyślne wprowadzanie tekstu w wiele wierszy
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x23) jest nieprawidłowy
- **GX_FAILURE** (0X10) Nieprawidłowa czcionka

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Delete a character before the cursor of “my_text_input”. */
status = gx_multi_line_text_input_backspace(&my_text_input);

/* If status is GX_SUCCESS the character before the cursor has been deleted. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_buffer_clear"></a>gx_multi_line_text_input_buffer_clear


Usuwa wszystkie znaki z buforu wejściowego tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_buffer_clear(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa usuwa wszystkie znaki z bufora wejściowego tekstu.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne czyszczenie bufora danych wejściowych z wielowierszowym tekstem
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* clear input buffer of “my_text_input”. */
status = gx_multi_line_text_input_clear(&my_text_input);

/* If status is GX_SUCCESS the text input widget has emptied its input buffer. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_buffer_get"></a>gx_multi_line_text_input_buffer_get


Pobiera informacje o buforze widżetu wprowadzania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_buffer_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    GX_CHAR **buffer_address,
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje buforowe widżetu wprowadzanie tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego
- **buffer_address** Adres buforu wejściowego
- **content_size** Liczba bajtów danych wejściowych
- **buffer_size** Rozmiar buforu wejściowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne pobieranie tekstu wielowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR *buffer_address;
UINT context_size;
UINT buffer_size;

/* Retrieves buffer information of “my_text_input” widget. */
status = gx_multi_line_text_input_buffer_get(&my_text_input,
    &buffer_address, &string_size,
    &buffer_size);

/* If status is GX_SUCCESS the value of buffer_address, string_size and buffer_size has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_char_insert"></a>gx_multi_line_text_input_char_insert


Wstaw ciąg znaków w bieżącej pozycji kursora tekstu wielowierszowego (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_char_insert(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>Opis

Ten interfejs API jest przestarzały i zastąpiony przez gx_multi_line_text_input_char_insert_ext ().

Ta usługa wstawia ciąg znaków do buforu ciągów wejściowych tekstu wielowierszowego w bieżącym położeniu kursora. Ta usługa jest wywoływana wewnętrznie po odebraniu określonego zdarzenia związanego z kluczem, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego
- **insert_str** Ciąg znaków formatu UTF-8, który ma zostać wstawiony
- **insert_size** Liczba bajtów do wstawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie wstawiono ciąg znaków
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_INVALID_VALUE** (0X22) Nieprawidłowy rozmiar ciągu
- **GX_FAILURE** (0X10) Nieprawidłowa czcionka lub brak rozmiaru buforu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Insert characters at current cursor position. */
GX_CHAR insert_text[10] = “insert”;
status = gx_multi_line_text_input_char_insert(&my_text_input,
    insert_text,
    GX_STRLEN(insert_text));

/* If status is GX_SUCCESS the multi line text input widget has successfully insert the string. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_char_insert_ext

## <a name="gx_multi_line_text_input_char_insert_ext"></a>gx_multi_line_text_input_char_insert_ext


Wstaw ciąg znaków w bieżącej pozycji kursora tekstu wielowierszowego (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_char_insert_ext(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Opis

Ta usługa wstawia ciąg znaków do buforu ciągów wejściowych tekstu wielowierszowego w bieżącym położeniu kursora. Ta usługa jest wywoływana wewnętrznie w przypadku otrzymania określonych zdarzeń w dół, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego
- **ciąg** Ciąg znaków zakodowany w formacie UTF-8

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie wstawiono ciąg znaków
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_INVALID_VALUE** (0X22) Nieprawidłowy rozmiar ciągu
- **GX_FAILURE** (0X10) Nieprawidłowa czcionka lub brak rozmiaru buforu
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Insert characters at current cursor position. */
GX_CHAR insert_text[10] = “insert”;
GX_STRING string;

string.gx_string_ptr = insert_text;
string.gx_string_length = strlen(insert_text);

status = gx_multi_line_text_input_char_insert_ext(&my_text_input, &string);

/* If status is GX_SUCCESS the multi line text input widget has successfully inserted the string. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_create"></a>gx_multi_line_text_input_create


Utwórz wielowierszowe wprowadzanie tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_create(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WINDOW *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    ULONG style, USHORT text_input_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet tekstu wielowierszowego.

GX_MULTI_LINE_TEXT_INPUT pochodzi od GX_MULTI_LINE_TEXT_VIEW i obsługuje wszystkie gx_multi_line_text_view usługi.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego
- **Nazwa** Nazwa widżetu wprowadzania tekstu
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **input_buffer** Wskaźnik do buforu wejściowego tekstu
- **buffer_size** Rozmiar buforu wejściowego tekstu w bajtach
- **styl** Styl widżetu wprowadzania tekstu. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **text_input_id** Zdefiniowany przez aplikację identyfikator danych wejściowych tekstu
- **rozmiar** Wymiary widżetu wprowadzania tekstu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne tworzenie wielowierszowych danych wejściowych tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy.
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_MULTI_LINE_TEXT_INPUT my_text_input;
GX_CHAR my_buffer[100];
GX_RECTANGLE size;

/* Define widget size. */
gx_utility_rectangle_define(&size, 10, 10, 100, 200);

/* Create multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_create(&my_text_input,
    “my_text_input”, &my_parent,
    my_buffer, 100, GX_STYLE_BORDER_RAISED,
    MY_TEXT_INPUT_ID, &size);

/* If status is GX_SUCCESS, the text input “my_text_input” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_cursor_pos_get"></a>gx_multi_line_text_input_cursor_pos_get


Pobierz położenie kursora wielowierszowego tekstu wejściowego

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_cursor_pos_get(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_POINT cursor_pos);
```

### <a name="description"></a>Opis

Ta usługa Pobiera pozycję kursora iloczyn wprowadzanie tekstu.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego
- **cursor_pos** Pobrano pozycję kursora

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrała pozycję kursora
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Retrieve the cursor position of “my_text_input”. */
GX_POINT cursor_pos;
status = gx_multi_line_text_input_cursor_pos_get(&my_text_input,
    &cursor_pos);

/* If status is GX_SUCCESS the cursor position has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_delete"></a>gx_multi_line_text_input_delete


Usuń znak z położenia kursora wielowierszowego wprowadzania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_delete(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa usuwa znak po pozycji kursora tekstu wielowierszowego. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia usuwania klucza, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie usuwa znak po kursorze
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_FAILURE** (0X10) Nieprawidłowa czcionka

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Delete the character after the cursor of “my_text_input”. */
status = gx_multi_line_text_input_delete(&my_text_input);

/* If status is GX_SUCCESS the character after the cursor has been deleted. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_down_arrow"></a>gx_multi_line_text_input_down_arrow


Przenieś kursor wielowierszowego wprowadzania tekstu do następnego wiersza

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_down_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa umieszcza kursor widżetu wprowadzanie tekstu wielowierszowego w następnym wierszu. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia w dół klawisz Strzałka w dół, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeniesiono kursor wprowadzania tekstu do następnego wiersza
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_FAILURE** (0X10) Nieprawidłowa czcionka lub wysokość linii

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move input cursor to the next line. */
status = gx_multi_line_text_input_down_arrow(&my_text_input);

/* If status is GX_SUCCESS, text text input cursor has been moved to the next line. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_end"></a>gx_multi_line_text_input_end


Przesuń kursor wielowierszowego wprowadzania tekstu do końca bieżącego wiersza

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_end(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa umieszcza kursor widżetu wprowadzanie tekstu wielowierszowego do końca bieżącego wiersza ciągu. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia dotyczącego klucza zakończenia, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeniesiono kursor wprowadzania tekstu do końca bieżącego wiersza
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move input cursor to the end of current line. */
status = gx_multi_line_text_input_end(&my_text_input);

/* If status is GX_SUCCESS, the multi line text input cursor has been moved to the end of the current line. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_event_process"></a>gx_multi_line_text_input_event_process


Domyślna obsługa zdarzeń w przypadku wprowadzania tekstu wielowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_event_process(
    GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa jest domyślną funkcją obsługi zdarzeń dla widżetu wprowadzanie tekstu wielowierszowego. Ta funkcja jest dostępna dla aplikacji, które chcą zapewnić obsługę zdarzeń niestandardowych dla widżetu wprowadzanie tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontroli wprowadzania tekstu wielowierszowego
- **event_ptr** Zdarzenie do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Zdarzenie **GX_SUCCESS** (0X00) zostało pomyślnie obsłużone
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT MyEventHandler(GX_MULTI_LINE_TEXT_INPUT *input,
    GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;
    default:
        /* pass all other events to the generic multi line text
            input event processing */
        gx_multi_line_text_input_event_process(input, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_fill_color_set"></a>gx_multi_line_text_input_fill_color_set


Ustaw kolor tła tekstu wielowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_fill_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje kolory wypełnienia dla widżetu wprowadzanie tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego
- **normal_fill_color_id** Identyfikator zasobu normalnego koloru wypełnienia, który był używany w normalnym stanie.
- **selected_fill_color_id** Identyfikator zasobu wybranego koloru wypełnienia, który był używany, gdy element widget uzyska fokus
- **disabled_fill_color_id** Identyfikator zasobu wyłączonego koloru wypełnienia, który był używany, gdy GX_STYLE_ENABLED nie jest aktywny
- **readonly_fill_color_id** Identyfikator zasobu koloru wypełnienia tylko do odczytu, który jest używany, gdy oba GX_STYLE_ENABLED i GX_STYLE_INPUT_READONLY są aktywne.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił kolory dla wprowadzania tekstu wielowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set fill colors for the multi-line text input widget “my_text_input”. */

status = gx_multi_line_text_input_fill_color_set(&my_text_input,
    GX_COLOR_ID_NORMAL_FILL,
    GX_COLOR_ID_SELECTED_FILL,
    GX_COLOR_ID_DISABLED_FILL,
    GX_COLOR_ID_READONLY_FILL);

/* If status is GX_SUCCESS, the fill color of “my_text_input” has been successfully set. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_home"></a>gx_multi_line_text_input_home


Przesuń kursor wprowadzania tekstu do początku bieżącego wiersza

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_home(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa przenosi położenie kursora wprowadzania tekstu na początek bieżącego wiersza. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia dotyczącego klucza głównego, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeniesiono kursor do początku bieżącego wiersza
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move cursor to the start of the current line. */
status = gx_multi_line_text_input_home(&my_text_input);

/* If status is GX_SUCCESS the cursor has been moved to the start of the current line. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_left_arrow"></a>gx_multi_line_text_input_left_arrow


Przenieś kursor wielowierszowego tekstu wejściowego o jeden znak w lewo

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_left_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa przenosi kursor wielowierszowego tekstu wejściowego o jeden znak w lewo. Ta usługa jest wywoływana wewnętrznie w przypadku odebrania lewego klucza zdarzenia, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeniesiono kursor w lewo
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_FAILURE** (0X10) Nieprawidłowa czcionka

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move the cursor one character to the left. */
status = gx_multi_line_text_input_left_arrow(&my_text_input);

/* If status is GX_SUCCESS the multi line text input cursor has been moved one character to the left. */

```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_right_arrow"></a>gx_multi_line_text_input_right_arrow


Przesuń kursor tekstu linii iloczyn o jeden znak w prawo

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_right_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa przenosi kursor wielowierszowego tekstu wejściowego o jeden znak w prawo. Ta usługa jest wywoływana wewnętrznie, gdy zostanie odebrane odpowiednie zdarzenie w dół, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeniesiono kursor w prawo
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move cursor one character to the right. */
status = gx_multi_line_text_input_right_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the right. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_add"></a>gx_multi_line_text_input_style_add


Dodawanie wielowierszowych stylów wprowadzania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_style_add(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>Opis

Ta usługa dodaje style do widżetu wprowadzanie tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego
- **styl** Style do dodania. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne dodanie stylu wprowadzania tekstu wielowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Add style GX_STYTLE_CURSOR_ALWAYS to multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_add(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS the style GX_STYLE_CURSOR_ALWAYS has been successfully added. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_remove"></a>gx_multi_line_text_input_style_remove


Usuń style

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_remove(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    ULONG style);
```

### <a name="description"></a>Opis

Ta usługa usuwa określone style z widżetu wprowadzanie tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego
- **styl** Style do usunięcia. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne tworzenie wielowierszowych danych wejściowych tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Remove style GX_STYLE_CURSOR_ALWAYS from text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_remove(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS, the style GX_STYLE_CURSOR_ALWAYS has been successfully removed. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_style_set"></a>gx_multi_line_text_input_style_set

Ustaw style wprowadzania tekstu wielowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_style_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Opis

Ta usługa ustawia style dla widżetu wprowadzanie tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego
- **styl** Style do ustawienia. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) pomyślny zestaw stylów tekstu wielowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set style GX_STYLE_CURSOR_ALWAYS for text input widget “my_text_input”. */
status = gx_multi_line_text_input_style_set(&my_text_input,
    GX_STYLE_CURSOR_ALWAYS);

/* If status is GX_SUCCESS the text input style has been set */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_color_set"></a>gx_multi_line_text_input_text_color_set


Ustaw kolor tekstu wielowierszowego wprowadzania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_text_color_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje kolory tekstu dla widżetu wprowadzanie tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekstu wielowierszowego
- **normal_fill_color_id** Identyfikator zasobu standardowego koloru tekstu, który był używany w normalnym stanie.
- **selected_text_color_id** Identyfikator zasobu wybranego koloru tekstu, który był używany, gdy element widget uzyskuje fokus.
- **disabled_text_color_id** Identyfikator zasobu dla wyłączonego koloru tekstu, który był używany, gdy GX_STYLE_ENABLED nie jest aktywny
- **readonly_text_color_id** Identyfikator zasobu dla koloru tekstu tylko do odczytu, który jest używany, gdy oba GX_STYLE_ENABLED i GX_STYLE_TEXT_INPUT_READONLY są aktywne

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił kolory dla wprowadzania tekstu wielowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set text colors for the multi-line text input widget “my_text_input”. */
status = gx_multi_line_text_input_text_color_set(&my_text_input,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT,
    GX_COLOR_ID_READONLY_TEXT);

/* If status is GX_SUCCESS, the fill colors of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_select"></a>gx_multi_line_text_input_text_select


Zaznacz tekst

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_text_select(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>Opis

Ta usługa wybiera tekst tekstu wielowierszowego z określonym znacznikiem początkowym i indeksem znacznika końcowego oraz podświetla zaznaczony tekst z wybranymi kolorami wypełnienia i tekstu.

### <a name="parameters"></a>Parametry

- **text_input** Wskaźnik do bloku kontroli wprowadzania tekstu wielowierszowego
- **start_index** Indeks pierwszego zaznaczonego znaku
- **end_index** Indeks ostatniego zaznaczonego znaku

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne Zaznaczanie tekstu tekstu wielowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- Wartość indeksu **GX_INVALID_VALUE** (0x22) jest nieprawidłowa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Select text between index [0, 9]. */
status = gx_multi_line_text_input_text_select(&my_text_input,
    0,9);

/* If status is GX_SUCCESS, the text between 
    index [0, 9] “my_text_input” was selected. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_text_set"></a>gx_multi_line_text_input_text_set


Przypisywanie tekstu do tekstu wejściowego (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CHAR *text);
```

### <a name="description"></a>Opis

Ten interfejs API jest przestarzały i zastępuje go gx_multi_line_text_input_text_set_ext ().

Ta usługa przypisuje określony ciąg do wielowierszowego wejścia tekstu. Jeśli rozmiar buforu danych wejściowych widżetu multi_line_text_input jest mniejszy niż długość ciągu, ciąg zostanie obcięty.

### <a name="parameters"></a>Parametry

- **text_input** Wskaźnik do bloku kontroli wprowadzania tekstu wielowierszowego
- wskaźnik **tekstowy** na ciąg zakończony ZNAKiem null

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił tekst na wprowadzanie tekstu wielowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the string “my string” to the text button “my_text_input”. */
status = gx_multi_line_text_input_text_set(&my_text_input,
    “myrstring”);

/* If status is GX_SUCCESS, the content of “my_text_input” bas been reset. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_text_set_ext

## <a name="gx_multi_line_text_input_text_set_ext"></a>gx_multi_line_text_input_text_set_ext


Przypisywanie tekstu do tekstu wejściowego

### <a name="prototype"></a>Prototype

```C
UINT gx_mult_line_text_input_text_set(
    GX_MULTI_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Opis

Ta usługa przypisuje określony ciąg do wielowierszowego wejścia tekstu. Jeśli rozmiar buforu danych wejściowych widżetu multi_line_text_input jest mniejszy niż długość ciągu, ciąg zostanie obcięty.

### <a name="parameters"></a>Parametry

- **text_input** Wskaźnik do bloku kontroli wprowadzania tekstu wielowierszowego
- wskaźnik **ciągu** do GX_STRING do przypisania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił tekst na wprowadzanie tekstu wielowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the string “my string” to the text button “my_text_input”. */
GX_STRING string;
string.gx_string_ptr = “myrstring”;
string.gx_string_length = strlen(string.gx_string_ptr);

status = gx_multi_line_text_input_text_set_ext(&my_text_input,
    &string);

/* If status is GX_SUCCESS, the content of “my_text_input” bas been reset. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_input_up_arrow"></a>gx_multi_line_text_input_up_arrow


Przenieś kursor wielowierszowego tekstu wprowadzania do poprzedniego wiersza

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_input_up_arrow(GX_MULTI_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa przenosi kursor wielowierszowego tekstu wejściowego do poprzedniego wiersza tekstu. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia niskiego poziomu strzałki w dół, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeniesiono kursor do poprzedniego wiersza
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move the cursor to the previous line. */
status = gx_multi_line_text_input_up_arrow(&my_text_input);

/* If status is GX_SUCCESS the multi line text input cursor has been moved to the previous line. */

```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_create"></a>gx_multi_line_text_view_create


Tworzenie wielowierszowego widoku tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_create(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT text_view_id, 
    GX_CONST GX_RECTANGLE *size);

```

### <a name="description"></a>Opis

Ta usługa tworzy widżet GX_MULTI_LINE_TEXT_VIEW. Ten typ widżetu pochodzi od GX_WINDOW, w związku z czym wszystkie usługi interfejsu API gx_window mogą być również używane z tym typem widgetu.

### <a name="parameters"></a>Parametry

- **text_view** Blok kontrolny widżetu widok tekstu wielowierszowego
- **Nazwa** Nazwa widżetu widoku tekstu
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **text_id** Identyfikator zasobu ciągu tekstowego
- **styl** Styl widżetu widoku tekstu. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **text_view_id** Zdefiniowany przez aplikację Identyfikator widoku tekstu
- **rozmiar** Wymiary widżetu widok tekstu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzył widżet widoku tekstu wielowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_create(&my_text_view,
    “my_text_view”, &my_parent,
    TEXT_STRING_ID, GX_STYLE_BORDER_RAISED,
    MY_TEXT_VIEW_ID, &size);

/* If status is GX_SUCCESS the text view “my_text_view” has been successfully created. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_draw"></a>gx_multi_line_text_view_draw


Rysowanie elementu widget widoku tekstu wielowierszowego

### <a name="prototype"></a>Prototype

```C
VOID gx_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW * text_view);
```

### <a name="description"></a>Opis

Ta usługa rysuje widżet widoku tekstu wielowierszowego. Ta usługa jest zwykle wywoływana wewnętrznie podczas odświeżania kanwy, ale może być również wywoływana z niestandardowych funkcji rysowania wielowierszowego widoku tekstu.

### <a name="parameters"></a>Parametry

- **text_view** Blok kontrolny widżetu widok tekstu wielowierszowego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom multi line text view drawing function. */

VOID my_multi_line_text_view_draw(GX_MULTI_LINE_TEXT_VIEW *view)
{
    /* Call default multi line text view draw. */
    gx_multi_line_text_view_draw(view);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_event_process"></a>gx_multi_line_text_view_event_process


Przetwarzanie zdarzenia wielowierszowego widoku tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_event_process(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla widżetu widoku tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **text_view** Blok kontrolny widżetu widok tekstu wielowierszowego
- **zdarzenie** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne przetwarzanie zdarzeń w wielowierszowym widoku tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom event handler. */
UINT my_event_handler(GX_MULTI_LINE_TEXT_VIEW *view, GX_EVENT *event_ptr)
{
    switch(event->gx_event_type)
    {
    case GX_EVENT_SHOW:
        gx_multi_line_text_view_event_process(view, event_ptr);
        /* Add custom actions here. */
        break;
    default:
        gx_multi_line_text_view_event_process (view, event_ptr);
        break;
    }
    return GX_SUCCESS;
}
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_font_set"></a>gx_multi_line_text_view_font_set


Ustaw czcionkę używaną w wielowierszowym widoku tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia czcionkę widżetu widoku tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **text_view** Blok kontrolny widżetu widok tekstu wielowierszowego
- **font_id** Identyfikator zasobu dla czcionki

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił czcionkę dla wielowierszowego widoku tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set font ID FONT_ID to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_font_set(&my_text_view, FONT_ID);

/* If status is GX_SUCCESS, the text view “my_text_view” will use the specified font to display its text. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_line_space_set"></a>gx_multi_line_text_view_line_space_set


Ustawianie wielowierszowego obramowania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_line_space_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_BYTE line_space);
```

### <a name="description"></a>Opis

Ta usługa ustawia odstępy między wierszami tekstu dla widżetu widok tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **Widok** Blok kontrolny widżetu widok tekstu wielowierszowego
- **line_space** Wartość do ustawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił wartość przestrzeni wierszy dla wielowierszowego widoku tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

```C
/* Set line space of “my_text_view” to 2. */
status = gx_multi_line_text_view_line_space_set(&my_text_view, 2);

/* If status is GX_SUCCESS, the line space of “my_text_view” has been successfully set to 2. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_scroll_info_get"></a>gx_multi_line_text_view_scroll_info_get

Pobierz informacje o przewijaniu wielowierszowego widoku tekstu


### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_scroll_info_get(
    GX_MULTI_LINE_TEXT_VIEW *text_view, ULONG style,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o przewijaniu wielowierszowego widoku tekstu.

### <a name="parameters"></a>Parametry

- **text_view** Blok kontrolny widżetu widok tekstu wielowierszowego
- **Styl** GX_SCROLLBAR_HORIZONTAL lub GX_SCROLLBAR_VERTICAL
- **Informacje** Wskaźnik do miejsca docelowego dla informacji przewijania. **Dodatek I** zawiera definicję do GX_SCROLL_INFO struktury.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrała informacje przewijania widoku tekstu
- Element widget **GX_FAILURE** (0x10) nie jest widoczny lub nieprawidłowy identyfikator czcionki widoku tekstu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_SCROLL_INFO scroll_info;

/* Get scroll information for multi-line text view “my_text_view”. */
status = gx_multi_line_text_view_scroll_info_get(&my_text_view,
    &scroll_info);

/* If status is GX_SUCCESS the “scroll_info” contains the scroll information for multi-line text view “my_text_view”. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_color_set"></a>gx_multi_line_text_view_text_color_set


Ustaw kolor tekstu dla widoku tekstu wielowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_text_color_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCe_ID disabled_text_color_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje kolor tekstu do widżetu widoku tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **text_view** Blok kontrolny widżetu widok tekstu wielowierszowego
- **normal_text_color_id** Identyfikator zasobu standardowego koloru tekstu, który był używany w normalnym stanie.
- **selected_text_color_id** Identyfikator zasobu wybranego koloru tekstu, który był używany, gdy element widget uzyskuje fokus.
- **disabled_text_color_id** Identyfikator zasobu wyłączonego koloru tekstu, który był używany GX_STYLE_ENABLED nie jest aktywny

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił kolory dla wielowierszowego widoku tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set text colors for the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_color_set(&my_text_view,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_id_set"></a>gx_multi_line_text_view_text_id_set


Ustawianie ciągu tekstowego systemu w widoku tekstu wielowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_text_id_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_RESOURCE_ID text_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia identyfikator zasobu ciągu do wielowierszowego widżetu widoku tekstu.

### <a name="parameters"></a>Parametry

- **text_view** Blok kontrolny widżetu widok tekstu wielowierszowego
- **text_id** Identyfikator zasobu dla ciągu tekstowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił identyfikator ciągu dla wielowierszowego widoku tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set string ID STRING_ID to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_id_set(&my_text_view, STRING_ID);

/* If status is GX_SUCCESS the text id of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_text_set"></a>gx_multi_line_text_view_text_set


Ustawianie ciągu zdefiniowanego przez użytkownika w widoku tekstu wielowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_text_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>Opis

Ta usługa przypisuje ciąg tekstowy do widżetu widok tekstu wielowierszowego. Jeśli element widget text_view został utworzony przy użyciu GX_STYLE_TEXT_COPY stylu, widżet tworzy prywatną kopię ciągu tekstowego, a w związku z tym interfejs API gx_system_memory_allocate_set musi zostać wywołany raz przed zażądaniem tej usługi. Jeśli GX_STYLE_TEXT_COPY nie jest aktywny, widżet nie tworzy prywatnej kopii ciągu przychodzącego, w związku z czym przypisany ciąg musi być statycznie lub globalnie przydzielona, tj. nie może to być automatyczna lub Tymczasowa zmienna.

### <a name="parameters"></a>Parametry

- **text_view** Blok kontrolny widżetu widok tekstu wielowierszowego
- **tekst** Ciąg tekstowy zakończony zerem

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił ciąg dla wielowierszowego widoku tekstu
- Program przydzielania pamięci **GX_SYSTEM_MEMORY_ERROR** (0x30) nie został zdefiniowany lub alokacja pamięci nie powiodła się
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set string “my string” to the multi-line text view widget “my_text_view”. */
status = gx_multi_line_text_view_text_set(&my_text_view, “my string”);

/* If status is GX_SUCCESS the text of “my_text_view” has been successfully set. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_whitespace_set

## <a name="gx_multi_line_text_view_whitespace_set"></a>gx_multi_line_text_view_whitespace_set


Ustaw odstępy między widokiem tekstu wielowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_multi_line_text_view_whitespace_set(
    GX_MULTI_LINE_TEXT_VIEW *text_view, 
    GX_UBYTE whitespace);
```

### <a name="description"></a>Opis

Ta usługa ustawia odstępy między konturami widżetu i obszarem klienckim dla widżetu widok tekstu wielowierszowego.

### <a name="parameters"></a>Parametry

- **text_view** Blok kontrolny widżetu widok tekstu wielowierszowego
- **odstępy** Szerokość marginesu między widżetem text_view a wyświetlanym tekstem (w pikselach).

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił odstępy dla wielowierszowego widoku tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set whitespace of “my_text_view” to 2. */
status = gx_multi_line_text_view_whitespace_set(&my_text_view, 2);

/* If status is GX_SUCCESS the whitespace of “my_text_view” has been successfully set to 2. */
```

### <a name="see-also"></a>Zobacz też

- gx_multi_line_text_input_backspace
- gx_multi_line_text_input_buffer_clear
- gx_multi_line_text_input_buffer_get
- gx_multi_line_text_input_char_insert
- gx_multi_line_text_input_create
- gx_multi_line_text_input_cursor_pos_get
- gx_multi_line_text_input_delete
- gx_multi_line_text_input_down_arrow
- gx_multi_line_text_input_end
- gx_multi_line_text_input_event_process
- gx_multi_line_text_input_fill_color_set
- gx_multi_line_text_input_home
- gx_multi_line_text_input_left_arrow
- gx_multi_line_text_input_right_arrow
- gx_mutli_line_text_input_style_add
- gx_multi_line_text_input_style_remove
- gx_multi_line_text_input_style_set
- gx_multi_line_text_input_text_color_set
- gx_multi_line_text_input_text_select
- gx_multi_line_text_input_text_set
- gx_multi_line_text_input_up_arrow
- gx_multi_line_text_view_create
- gx_multi_line_text_view_draw
- gx_multi_line_text_view_event_process
- gx_multi_line_text_view_font_set
- gx_multi_line_text_view_line_space_set
- gx_multi_line_text_view_scroll_info_get
- gx_multi_line_text_view_text_color_set
- gx_multi_line_text_view_text_id_set
- gx_multi_line_text_view_text_set

## <a name="gx_numeric_pixelmap_prompt_create"></a>gx_numeric_pixelmap_prompt_create


Tworzenie numerycznego monitu Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_pixelmap_prompt_create(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, GX_RESOURCE_ID fill_id,
    ULONG style, USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy liczbowy widżet monitu Pixelmap. Numeric_pixelmap_prompt to tylko pixelmap_prompt, które utrzymują własny bufor i udostępniają interfejs API gx_numeric_pixelmap_prompt_value_set (INT), rozmiar buforu jest definiowany przez stałą GX_NUMERIC_PROMPT_BUFFER_SIZE, która domyślnie jest 16.

GX_NUMERIC_PIXELMAP_PROMPT pochodzi od GX_PIXELMAP_PROMPT i obsługuje wszystkie gx_pixelmap_prompt usługi interfejsu API.

### <a name="parameters"></a>Parametry

- **Monituj** Numeryczny blok kontroli monitu Pixelmap
- **Nazwa** Nazwa monitu
- **element nadrzędny** Blok nadrzędnego elementu widget
- **text_id** Identyfikator ciągu zasobu
- **fill_id** Identyfikator Pixelmap dla obszaru wypełnienia
- **styl** Styl pixelmapego monitu, **dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **pixelmap_prompt_id** Zdefiniowany przez aplikację identyfikator monitu
- **rozmiar** Wymiary numerycznego monitu Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzył numeryczny monit pixlemap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_create(&my_numeric_pix_prompt,
    “my_numeric_pix_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, MY_FEEL_RESOURCE_ID,
    GX_STYLE_BORDER_RAISED, MY_NUMERIC_PIXELMAP_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the numeric pixelmap prompt “my_numeric_pix_prompt” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_pixelmap_format_function_set
- gx_numeric_pixelmap_prompt_value_set

## <a name="gx_numeric_pixelmap_prompt_format_function_set"></a>gx_numeric_pixelmap_prompt_format_function_set


Przesłoń funkcję formatu pixelmapego monitu

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_pixelmap_format_function_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    OID (*format_func)(GX_NUMERIC_PIXELMAP_PROMPT *, INT));
```

### <a name="description"></a>Opis

Ta usługa zastępuje domyślną funkcję formatu widżetu pixlemap monitu. Funkcja formatowania domyślnego konwertuje wartość numeryczną monitu Pixelmap na ciąg i zapisuje ją w buforze prywatnym widżetu. Ta usługa umożliwia aplikacji Definiowanie własnej funkcji formatowania i przechowywanie wartości numerycznego monitu Pixelmap w buforze prywatnym widżetu.

### <a name="parameters"></a>Parametry

- **Monituj** Numeryczny blok kontroli monitu Pixelmap
- **format_func** Funkcja formatowania, która ma zostać ustawiona

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił numeryczną funkcję formatu monitu pixlemap
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Define my numeric pixelmap format function. */
VOID my_format_function(GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value)
{
    /* If the value is “1234”, the new format will be “12.34”. */

    INT length;
    gx_utility_ltoa(value / 100,
        prompt->gx_numeric_pixelmap_prompt_buffer,
        GX_NUMERIC_PROMPT_ BUFFER_SIZE);
    Length = GX_STRLEN(prompt->gx_numeric_pixelmap_prompt_buffer);
    prompt->gx_numeric_pixelmap_prompt_buffer[length++] = ‘.’;
    gx_utility_ltoa(value % 100,
        prompt->gx_numeric_pixelmap_prompt_buffer + length,
        GX_NUMERIC_PROMPT_BUFFER_SIZE - length);
}

/* Override default format function of “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_format_function_set(
    &my_numeric_pix_prompt,
    my_format_function);

/* If status is GX_SUCCESS the format function of “my_numeric_pix_prompt” has been override. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_pixelmap_prompt_create
- gx_numeric_pixelmap_prompt_value_set

## <a name="gx_numeric_pixelmap_prompt_value_set"></a>gx_numeric_pixelmap_prompt_value_set


Ustaw wartość numeryczną monitu pixlemap

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_pixelmap_prompt_value_set(
    GX_NUMERIC_PIXELMAP_PROMPT *prompt,
    INT value);
```

### <a name="description"></a>Opis

Ta usługa jest wartością całkowitą do numerycznego monitu Pixelmap.

### <a name="parameters"></a>Parametry

- **Monituj** Numeryczny blok kontroli monitu Pixelmap
- **wartość** Wartość całkowita do ustawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił wartość numeryczną monitu Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set a value to “my_numeric_pix_prompt”. */
status = gx_numeric_pixelmap_prompt_value_set(&my_numeric_pix_prompt, 1000);

/* If status is GX_SUCCESS the value of the numeric pixelmap prompt “my_numeric_pix_prompt” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_pixelmap_prompt_create
- gx_numeric_pixelmap_format_function_set

## <a name="gx_numeric_prompt_create"></a>gx_numeric_prompt_create


Utwórz monit liczbowy

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_prompt_create( 
    GX_NUMERIC_PROMPT *prompt,
    GX_CONST GX_CHAR name, GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    ULONG style, USHORT prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet z monitem numerycznym. Monit numeric_ jest tylko monitem, który utrzymuje własny bufor i udostępnia interfejs API gx_numeric_ prompt_value_set (INT), rozmiar buforu jest definiowany przez stałą GX_NUMERIC_PROMPT_BUFFER_SIZE, która domyślnie jest równa 16.

GX_NUMERIC_PROMPT pochodzi od GX_PROMPT i obsługuje wszystkie gx_prompt usługi interfejsu API.

### <a name="parameters"></a>Parametry

- **Monituj** Blok kontroli monitów numerycznych
- **Nazwa** Nazwa monitu
- **element nadrzędny** Blok nadrzędnego elementu widget
- **text_id** Identyfikator ciągu zasobu
- **styl** Styl monitu liczbowego, **dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **prompt_id** Zdefiniowany przez aplikację identyfikator monitu
- **rozmiar** Wymiary monitu liczbowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie Utwórz monit liczbowy
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “my_numeric _prompt”. */
status = gx_numeric_prompt_create(&my_numeric_prompt,
    “my_numeric_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, GX_STYLE_BORDER_RAISED, MY_NUMERIC_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the numeric prompt “my_numeric_prompt” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_format_function_set
- gx_numeric_prompt_value_set

## <a name="gx_numeric_prompt_format_function_set"></a>gx_numeric_prompt_format_function_set


Przesłoń funkcję formatu monitu liczbowego

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_format_function_set(
    GX_NUMERIC_PROMPT *prompt,
    VOID (*format_func)(GX_NUMERIC_PROMPT *, INT));
```

### <a name="description"></a>Opis

Ta usługa zastępuje domyślną funkcję formatu widżetu monitu liczbowego. Funkcja formatowania domyślnego konwertuje wartość numerycznego monitu na ciąg i zapisuje ją w buforze prywatnym widżetu. Ta usługa umożliwia aplikacji Definiowanie własnej funkcji formatowania i przechowywanie wartości numerycznego monitu w buforze prywatnym widżetu.

### <a name="parameters"></a>Parametry

- **Monituj** Blok kontroli monitów numerycznych
- **format_func** Funkcja formatowania, która ma zostać ustawiona

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił funkcję formatowania monitu liczbowego
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Define my numeric format function. */
VOID my_format_function(GX_NUMERIC_PROMPT *prompt, INT value)
{
    /* If the value is “1234”, the new format will be “12.34”. */

    INT length;
    gx_utility_ltoa(value / 100, prompt->gx_numeric_prompt_buffer,
        GX_NUMERIC_PROMPT_ BUFFER_SIZE);
    Length = GX_STRLEN(prompt->gx_numeric_prompt_buffer);
    prompt->gx_numeric_prompt_buffer[length++] = ‘.’;
    gx_utility_ltoa(value % 100,
        prompt->gx_numeric_prompt_buffer + length,
        GX_NUMERIC_PROMPT_BUFFER_SIZE - length);
}

/* Override the default format function of “my_numeric_prompt”. */
status = gx_numeric_prompt_format_function_set(&my_numeric_prompt,
    my_format_function);

/* If status is GX_SUCCESS, the format function of “my_numeric_prompt” has been override. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_prompt_create
- gx_numeric_prompt_value_set

## <a name="gx_numeric_prompt_value_set"></a>gx_numeric_prompt_value_set


Ustaw wartość monitu liczbowego

### <a name="prototype"></a>Prototype

```C
UINT gx_numeric_prompt_value_set(
    GX_NUMERIC_PROMPT *prompt, 
    INT value);
```

### <a name="description"></a>Opis

Ta usługa ustawia wartość całkowitą na monit liczbowy.

### <a name="parameters"></a>Parametry

- **Monituj** Blok kontroli monitów numerycznych
- **wartość** Wartość całkowita do ustawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił wartość numeryczną monitu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set a value to “my_numeric_prompt”. */
status = gx_numeric_prompt_value_set(&my_numeric_prompt, 1000);

/* If status is GX_SUCCESS the value of the numeric prompt “my_numeric_prompt” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_prompt_create
- gx_numeric_format_function_set

## <a name="gx_numeric_scroll_wheel_create"></a>gx_numeric_scroll_wheel_create


Tworzenie numerycznego kółka przewijania

### <a name="prototype"></a>Prototype


UINT gx_numeric_scroll_wheel_create (GX_NUMERIC_SCROLL_WHEEL * koło, GX_CONST GX_CHAR * nazwa, GX_WIDGET * Parent, INT start_val, INT end_val, style ULONG, USHORT wheel_id, GX_CONST GX_RECTANGLE * size);

### <a name="description"></a>Opis

Ta usługa tworzy liczbowy widżet kółka przewijania.

Numeryczne kółko przewijania jest typem widżetu kółka przewijania, który jest używany do wyświetlania zakresu liczb. Dostępne są również inne typy widżetów z kółkiem przewijania. Zapoznaj się z interfejsem API gx_scroll_wheel_create (), aby uzyskać więcej informacji na temat hierarchii widżetu, typy widżetów i wyprowadzania elementu widget.

GX_NUMERIC_SCROLL_WHEEL pochodzi od GX_TEXT_SCROLL_WHEEL i obsługuje wszystkie usługi gx_text_scroll_wheel i gx_scroll_wheel.

Wszystkie typy kółka przewijania generują zdarzenia GX_EVENT_LIST_SELECT do ich elementu nadrzędnego, gdy kółko przewijania jest przewijane.

Numeryczne kółko przewijania będzie domyślnie mieć wartość ABS (end_val – start_val) + 1 wierszy. Innymi słowy, kółko przewijania będzie wyświetlało każdą wartość między start_val i end_val, zwiększanie lub zmniejszanie o 1 z każdym wierszem. Należy pamiętać, że start_val może być większa lub mniejsza niż end_val, w zależności od tego, w jaki sposób aplikacja chce, aby zakres był widoczny.

Jeśli aplikacja chce zmienić przyrost wiersza, można to zrobić, wywołując gx_scroll_wheel_total_rows_set () po utworzeniu kółka przewijania numerycznego. Na przykład aplikacja chcąca utworzyć kółko przewijania, które wyświetla wartości lat 1980 do 2020, zwiększające się o 5, może to zrobić:

```C
gx_numeric_scroll_wheel_create(&wheel, GX_NULL, parent, 1980,
    2020, style, id, &size);

/* the years 1980 through 2020, inclusive, incrementing by 5 years,
yields 9 total rows */

gx_scroll_wheel_total_rows_set(&wheel, 9);
```

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do numerycznego bloku kontrolki pokrętła przewijania
- **Nazwa** Logiczna nazwa widżetu przycisku Pixelmap
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **start_val** Początkowa wartość liczbowa
- **end_val** Końcowa wartość liczbowa
- **styl** Styl pola wyboru. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **wheel_id** Zdefiniowany przez aplikację identyfikator kółka przewijania
- **rozmiar** Wymiary widgetu kółka przewijania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzył numeryczne kółko przewijania
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “year_wheel”. */
status = gx_numeric_scroll_wheel_create(&year_wheel,
    “year_selector””, &parent,
    1980, 2040,
    GX_STYLE_ENABLED | GX_STYLE_TEXT_CENTER |
    GX_STYLE_TRANSPARENT | GX_STYLE_WRAP |
    GX_STYLE_TEXT_SCROLL_WHEEL_ROUND,
    YEAR_WHEEL_ID,
    &size);

/* If status is GX_SUCCESS the scroll wheel “year_wheel” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_text_get

## <a name="gx_numeric_scroll_wheel_range_set"></a>gx_numeric_scroll_wheel_range_set


Przypisz zakres wartości numerycznego kółka przewijania

### <a name="prototype"></a>Prototype

```C
UINT
gx_numeric_scroll_wheel_range_set(
    GX_NUMERIC_SCROLL_WHEEL *wheel,
    INT start_val, INT end_val);
```

### <a name="description"></a>Opis

Ta usługa modyfikuje zakres wartości, które są dozwolone i wyświetlane przez liczbowy widżet kółka przewijania.

Numeryczne kółko przewijania jest typem widżetu kółka przewijania, który jest używany do wyświetlania zakresu liczb. Dostępne są również inne typy widżetów z kółkiem przewijania. Zapoznaj się z interfejsem API gx_scroll_wheel_create (), aby uzyskać więcej informacji na temat hierarchii widżetu, typy widżetów i wyprowadzania elementu widget.

Wywołanie tego interfejsu API spowoduje zresetowanie wierszy sumy kółka przewijania do wartości ABS (end_val – start_val) + 1, co oznacza, że kółko przewijania zostanie zwiększone o 1 dla każdego wiersza. Aby to zmienić, aplikacja może wywołać gx_scroll_wheel_total_rows_set (), aby zmienić łączną liczbę wierszy, efektywnie zmieniając wartość przyrostu między wierszami.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do numerycznego bloku kontrolki pokrętła przewijania
- **start_val** Początkowa wartość liczbowa 
- **end_val** Końcowa wartość liczbowa

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił numeryczny zakres kółka przewijania
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki 

### <a name="example"></a>Przykład

```C
/* Change range of “rate” scroll wheel. */

status = gx_numeric_scroll_wheel_range_set(&year_wheel, 0, 200);

/* If status is GX_SUCCESS the scroll wheel range has been modified. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_pixelmap_button_create"></a>gx_pixelmap_button_create


Utwórz przycisk Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_button_create(
    GX_PIXELMAP_BUTTON *button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id,
    GX_RESOURCE_ID disabled_id,
    ULONG style,
    USHORT pixelmap_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet przycisku Pixelmap.

GX_PIXELMAP_BUTTON pochodzi od GX_BUTTON i obsługuje wszystkie gx_button usługi.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku Pixelmap
- **Nazwa** Logiczna nazwa widżetu przycisku Pixelmap
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **normal_id** Identyfikator zasobu stanu normalnego
- **selected_id** Identyfikator zasobu wybranego stanu
- **disabled_id** Identyfikator zasobu wyłączonego stanu
- **styl** Styl pola wyboru. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **pixelmap_button_id** Zdefiniowany przez aplikację przycisk Pixelmap
- **rozmiar** Wymiary przycisku Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzył przycisk Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “my_pixelmap_button”. */
status = gx_pixelmap_button_create(&my_pixelmap_button,
    “my_pixelmap_button”, &my_parent,
    MY_NORMAL_RESOURCE_ID, MY_SELECTED_RESOURCE_ID,
    MY_DESELECTED_RESOURCE_ID, GX_STYLE_BORDER_RAISED,
    MY_PIXELMAP_BUTTON_ID,
    &size);

/* If status is GX_SUCCESS the pixelmap button “my_pixelmap_button” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_draw
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_draw"></a>gx_pixelmap_button_draw


Przycisk rysowania Pixelmap

### <a name="prototype"></a>Prototype

```C
VOID gx_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button);
```

### <a name="description"></a>Opis

Ta usługa rysuje widżet przycisku Pixelmap. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest uwidaczniana dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania dla widżetów przycisku niestandardowego Pixelmap.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom pixelmap button drawing function. */

VOID my_pixelmap_button_draw(GX_PIXELMAP_BUTTON *button)
{
    /* Call default pixelmap button draw. */
    gx_pixelmap_button_draw(button);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_event_process"></a>gx_pixelmap_button_event_process


Przetwarzanie zdarzenia Pixelmap Button

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_button_event_process(
    GX_PIXELMAP_BUTTON *button,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa udostępnia domyślną obsługę zdarzeń dla typu widżetu przycisk Pixelmap.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku Pixelmap
- **event_ptr** Wskaźnik do GX_EVENT struktury

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — pomyślne rysowanie przycisku Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
switch(event_ptr->gx_event_type)
{
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_pixelmap_button_event_process(icon, event_ptr);
    
        /* add my own handling here */
        break;
}
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_pxielmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_button_pixelmap_set"></a>gx_pixelmap_button_pixelmap_set


Przypisz pixelmaps do przycisku

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_button_pixelmap_set(
    GX_PIXELMAP_BUTTON *button, 
    GX_RESOURCE_ID normal_id,
    GX_RESOURCE_ID selected_id, 
    GX_RESOURCE_ID disabled_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia pixelmaps na przycisk Pixelmap.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku Pixelmap
- **normal_id** Identyfikator zasobu Pixelmap, który ma być używany jako stan Normalny
- **selected_id** Identyfikator zasobu Pixelmap, który ma być używany, gdy przycisk jest zaznaczony
- **disabled_id** Identyfikator zasobu Pixelmap, który ma być używany, gdy przycisk jest wyłączony

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawia Pixelmap na przycisk
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Draw “my_pixelmap_button”. */
status = gx_pixelmap_button_pixelmap_set (&my_pixelmap_button,
    NORMAL_ID, SELECTED_ID,
    DISABLED_ID);

/* If status is GX_SUCCESS the pixelmap button is properly configured with the specified pixelmaps. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_prompt_create"></a>gx_pixelmap_prompt_create


Utwórz monit Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_prompt_create(
    GX_PIXELMAP_PROMPT *prompt,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    GX_RESOURCE_ID fill_pixelmap_id,
    ULONG style,
    USHORT pixelmap_prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet monitu Pixelmap. Monit Pixelmap różni się od standardowego GX_PROMPT w tym, że maluje tło monitu przy użyciu pixelmaps. Funkcja Create akceptuje jeden identyfikator Pixelmap, normalny stan wypełnienia Pixelmap. Do poziomu wiersza polecenia Pixelmap można przypisać maksymalnie sześć pixelmaps.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do bloku sterowania monitem Pixelmap
- **Nazwa** Nazwa logiczna widżetu monitu Pixelmap
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **text_id** Identyfikator zasobu tekstu
- **fill_id** Identyfikator zasobu wypełnienia
- **styl** Styl pola wyboru. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **pixelmap_prompt_id** Zdefiniowany przez aplikację Identyfikator wiersza Pixelmap
- **rozmiar** Wymiary monitu Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — pomyślne utworzenie monitu Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “my_pixelmap_prompt”. */
status = gx_pixelmap_prompt_create(&my_pixelmap_prompt,
    “my_pixelmap_prompt”, &my_parent,
    MY_TEXT_RESOURCE_ID, MY_LEFT_RESOURCE_ID,
    MY_FILL_RESOURCE_ID, MY_RIGHT_RESOURCE_ID,
    GX_STYLE_BORDER_RAISED, MY_PIXELMAP_PROMPT_ID,
    &size);

/* If status is GX_SUCCESS the pixelmap prompt “my_pixelmap_prompt” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_pixelmap_prompt_draw"></a>gx_pixelmap_prompt_draw


Rysowanie monitu Pixelmap

### <a name="prototype"></a>Prototype

```C
VOID gx_pixelmap_prompt_draw(GX_PIXELMAP_PROMPT *prompt);
```

### <a name="description"></a>Opis

Ta usługa rysuje widżet Pixelmap. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest dostępna dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania dla widżetów monitów niestandardowych Pixelmap.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do bloku sterowania monitem Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom pixelmap prompt drawing function. */

VOID my_pixelmap_button_draw(GX_PIXELMAP_PROMPT *prompt)
{
    /* Call default pixelmap prompt draw. */
    gx_pixelmap_prompt_draw(prompt);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_pixelmap_prompt_pixelmap_set"></a>gx_pixelmap_prompt_pixelmap_set


Przypisz pixelmaps do monitu

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_prompt_pixelmap_set(
    GX_PIXELMAP_PROMPT *prompt,
    GX_RESOURCE_ID normal_left_pixelmap,
    GX_RESOURCE_ID normal_fill_pixelmap,
    GX_RESOURCE_ID normal_right_pixelmap,
    GX_RESOURCE_ID selected_left_pixelmap,
    GX_RESOURCE_ID selected_fill_pixelmap,
    GX_RESOURCE_ID selected_right_pixelmap);
```

### <a name="description"></a>Opis

Ta usługa przypisuje identyfikatory Pixelmap do monitu Pixelmap. Identyfikatory Pixelmap lewej, Fill i Right są używane do zezwalania aplikacji na użycie jednego zestawu pixelmaps do wyświetlania monitów o różne szerokości, ale o wspólnej wysokości, aby zaoszczędzić na wymaganiach dotyczących magazynu. Jeśli nie są używane lewe i prawe identyfikatory, powinny być ustawione na 0. Jeśli monit powinien wyglądać inaczej, gdy zyskuje fokus wprowadzania, wybrane identyfikatory Pixelmap są używane do tego celu. Jeśli wybrane identyfikatory nie są używane lub są takie same jak normalne identyfikatory, ustaw je na 0.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do bloku sterowania monitem Pixelmap
- **normal_left_id** Identyfikator zasobu Pixelmap, który ma być używany po lewej stronie w normalnym stanie
- **normal_fill_id** Identyfikator zasobu Pixelmap, który ma być używany jako uzupełniający wypełnianie w normalnym stanie
- **normal_right_id** Identyfikator zasobu Pixelmap, który ma być używany po prawej stronie w normalnym stanie
- **selected_left_id** Identyfikator zasobu Pixelmap, który ma być używany po lewej stronie w wybranym stanie
- **selected_fill_id** Identyfikator zasobu Pixelmap, który ma być używany jako wypełnienie z rozdzieleniem w wybranym stanie
- **selected_right_id** Identyfikator zasobu Pixelmap, który ma być używany po prawej stronie w wybranym stanie

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawia Pixelmap na monit
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Identyfikator zasobu **GX_INVALID_RESOURCE_ID** (0x33) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Assign pixelmap IDs to “my_prompt”. Only the normal state pixelmaps are used in this case */
status = gx_pixelmap_prompt_pixelmap_set (&my_prompt,
    normal_left_id, normal_fill_id,
    normal_right_id, 0, 0, 0);

/* If status is GX_SUCCESS the pixelmap prompt is properly configured with pixelmaps. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_pixelmap_slider_create"></a>gx_pixelmap_slider_create


Utwórz suwak Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_slider_create(
    GX_PIXELMAP_SLIDER *slider,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_SLIDER_INFO *info,
    GX_PIXELMAP_SLIDER_INFO *pixelmap_info, ULONG style,
    USHORT pixelmap_slider_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet suwaka Pixelmap.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka Pixelmap
- **Nazwa** Logiczna nazwa widgetu suwaka Pixelmap
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **informacje** Wskaźnik do struktury GX_SLIDER_INFO, która zawiera wartości definiujące minimalną wartość suwaka, wartość maksymalną, bieżącą wartość i limity wskazówki. **Dodatek I** zawiera definicję dla struktury GX_SLIDER_INFO.
- **pixelmap_info** Wskaźnik do struktury GX_PIXELMAP_SLIDER_INFO, która definiuje pixelmaps używany do rysowania tła suwaka i wskazówki. **Dodatek I** zawiera definicję dla struktury GX_PIXELMAP_SLIDER_INFO. Tło suwaka może używać jednego lub dwóch pixelmaps. Jeśli takie tło nie zmienia się po przeniesieniu wskazówki. Jeśli zdefiniowano dwa tła, tło przed wskazówką używa pierwszego pixelmapu w tle, a w tle po stronie wskazówki jest stosowane drugie Pixelmap w tle.
- **styl** Styl suwaka. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **pixelmap_slider_id** Zdefiniowany przez aplikację suwak Pixelmap
- **rozmiar** Wymiary monitu Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzył suwak Pixelmap
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_SLIDER_INFO info;
GX_PIXELMAP_SLIDER_INFO pixelmap_info;

/* Initiate slider information structure. */
info.gx_slider_info_min_val = 0;
info.gx_slider_info_max_val = 100;
info.gx_slider_info_current_val = 50;
info.gx_slider_info_min_travel = 10;
info.gx_slider_info_max_tralvel = 10;
info.gx_slider_info_needle_width = 5;
info.gx_slider_info_needle_height = 10;
info.gx_slider_info_needle_inset = 5;
info.gx_slider_info_needle_hotspot_offset;

/* Initiate pixelmap slider information structure. */
pixelmap_info.gx_pixelmap_slider_info_lower_background_pixelmap =
                                        GX_PIXELMAP_ID_ORANGE;
pixelmap_info.gx_pixelmap_slider_info_upper_background_pixelmap =
                                        GX_PIXELMAP_ID_EMPTY;
pixelmap_info.gx_pixelmap_slider_info_needle_pixelmap =
                                        GX_PIXELMAP_ID_NEEDLE;

/* Create “my_pixelmap_slider”. */
status = gx_pixelmap_slider_create(&my_pixelmap_slider,
                            “my_pixelmap_slider”, &my_parent,
                            &info, &pixelmap_info,
                            GX_STYLE_BORDER_RAISED,
                            MY_PIXELMAP_SLIDER_ID, &size);

/* If status is GX_SUCCESS the pixelmap slider “my_pixelmap_slider” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_draw"></a>gx_pixelmap_slider_draw


Rysuj suwak Pixelmap

### <a name="prototype"></a>Prototype

```C
VOID gx_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *slider);
```

### <a name="description"></a>Opis

Ta usługa rysuje widżet suwaka Pixelmap. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest dostępna dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania dla widżetów niestandardowego Pixelmap suwaka.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom pixelmap slider drawing function. */

VOID my_pixelmap_slider_draw(GX_PIXELMAP_SLIDER *pixelmap_slider)
{
    /* Call default pixelmap slider draw. */
    gx_pixelmap_slider_draw(pixelmap_slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_event_process"></a>gx_pixelmap_slider_event_process


Zdarzenie suwaka Pixelmap procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_slider_event_process(
    GX_PIXELMAP_SLIDER *slider,
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego widżetu suwaka Pixelmap.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do Pixelmap
- Kontrolka **suwaka** Blokuj wskaźnik zdarzenia do zdarzenia w celu przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia suwaka Pixelmap (0x00) zakończyła się pomyślnie **GX_SUCCESS**
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom event processing function. */
UINT my_event_hanlder(GX_PIXELMAP_SLIDER *pixelmap_slider, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_pixelmap_slider_event_process(pixelmap_slider,
                                                    event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_pixelmap_slider_event_process(pixelmap_slider,
                                                  event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_button_pixelmap_set
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_pixelmap_slider_pixelmap_set"></a>gx_pixelmap_slider_pixelmap_set


Przypisz pixelmaps do suwaka

### <a name="prototype"></a>Prototype

```C
UINT gx_pixelmap_slider_pixelmap_set(
    GX_PIXELMAP_SLIDER *slider,
    GX_PIXELMAP_SLIDER_INFO *pixinfo);
```

### <a name="description"></a>Opis

Ta usługa ustawia pixelmaps do suwaka Pixelmap.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka Pixelmap
- **pixinfo** Wskaźnik do struktury GX_PIXELMAP_SLIDER_INFO, która definiuje pixelmaps używany do rysowania tła suwaka i wskazówki. **Dodatek I** zawiera definicję dla struktury GX_PIXELMAP_SLIDER_INFO. Tło suwaka może używać jednego lub dwóch pixelmaps. Jeśli takie tło nie zmienia się po przeniesieniu wskazówki. Jeśli zdefiniowano dwa tła, tło przed wskazówką używa pierwszego pixelmapu w tle, a w tle po stronie wskazówki jest stosowane drugie Pixelmap w tle.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawia Pixelmap na suwak
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_PIXELMAP_SLIDER_INFO pixelmap_info;

/* Initiate pixelmap slider information structure. */
pixelmap_info.gx_pixelmap_slider_info_lower_background_pixelmap =
                                        GX_PIXELMAP_ID_ORANGE;
pixelmap_info.gx_pixelmap_slider_info_upper_background_pixelmap =
                                        GX_PIXELMAP_ID_EMPTY;
pixelmap_info.gx_pixelmap_slider_info_needle_pixelmap =
                                        GX_PIXELMAP_ID_NEEDLE;

/* Draw “my_pixelmap_button”. */
status = gx_pixelmap_slider _pixelmap_set (&my_pixelmap_slider,
                                &pixelmap_info);

/* If status is GX_SUCCESS the pixelmap slider is properly configured with “pixelmap_info”. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_radio_button_create
- gx_radio_button_draw
- gx_icon_button_create
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw

## <a name="gx_progress_bar_background_draw"></a>gx_progress_bar_background_draw


Rysuj tło paska postępu

### <a name="prototype"></a>Prototype

```C
VOID gx_progress_bar_background_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>Opis

Ta usługa rysuje tło określonego paska postępu. Ta funkcja jest wywoływana wewnętrznie jako część gx_progress_bar_draw (), ale jest dostępna dla aplikacji w celu obsługi tych przypadków, w których aplikacja definiuje niestandardową funkcję rysowania paska postępu.

### <a name="parameters"></a>Parametry

- **pasek postępu** Wskaźnik do bloku sterowania paskiem postępu

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar background draw. */
    gx_progress_bar_background_draw(progress_bar);

    /* Call default progress bar text draw. */
    gx_progress_bar_text_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_value_set

## <a name="gx_progress_bar_create"></a>gx_progress_bar_create


Utwórz pasek postępu

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_create(
    GX_PROGRESS_BAR *progress_bar,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_PROGRESS_BAR_INFO *progress_bar_info,
    ULONG style, 
    USHORT progress_bar_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet paska postępu.

### <a name="parameters"></a>Parametry

- **progress_bar** Blok sterowania paskiem postępu
- **Nazwa** Nazwa logiczna
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **progress_bar_info** Wskaźnik do struktury GX_PROGRESS_BAR_INFO. **Dodatek I** zawiera definicję dla struktury GX_PROGRESS_BAR_INFO.
- **styl** Styl paska postępu. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **progress_bar_id** Zdefiniowany przez aplikację pasek postępu
- **rozmiar** Wymiary paska postępu

### <a name="return-values"></a>Wartości zwrócone

- Tworzenie paska postępu o pomyślnym **zaGX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_PROGRESS_BAR_INFO info;
GX_RECTANGLE size;

info.gx_progress_bar_info_min_val = 0;
info.gx_progress_bar_info_max_val = 100;
info.gx_progress_bar_info_current_val = 0;
info.gx_progress_bar_font_id = GX_FONT_ID_SYSTEM_FONT;
info.gx_progress_bar_normal_text_color = GX_COLOR_ID_WHITE;
info.gx_progress_bar_selected_text_color = GX_COLOR_ID_BLUE;
info.gx_progress_bar_fill_pixelmap = 0;

size.gx_rectangle_left = 10;
size.gx_rectangle_top = 10;
size.gx_rectangle_right = 110;
size.gx_rectangle_bottom = 140;

/* Create a progress bar with the specified information. */
status = gx_progress_bar_create(&my_progress_bar, GX_NULL, GX_NULL,
                        &info, GX_STYLE_BORDER_THIN,
                        0, &size);

/* If status is GX_SUCSESS the progress bar “my_progress_bar” has been successfully created. */
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_draw"></a>gx_progress_bar_draw


Rysowanie paska postępu

### <a name="prototype"></a>Prototype

```C
VOID gx_progress_bar_draw(GX_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Opis

Ta usługa rysuje widżet paska postępu. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest dostępna dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania dla widżetów niestandardowego paska postępu.

### <a name="parameters"></a>Parametry

- **progress_bar** Blok sterowania paskiem postępu

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar draw. */
    gx_progress_bar_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_create
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_event_process"></a>gx_progress_bar_event_process


Postęp zdarzenia paska postępu

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_event_process(
    GX_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie paska postępu.

### <a name="parameters"></a>Parametry

- **progress_bar** Blok sterowania paskiem postępu
- **event_ptr** Wskaźnik do GX_EVENT struktury

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — pomyślne utworzenie monitu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_PROGRESS_BAR *progress_bar, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_progress_bar_event_process(progress_bar,
                                                event_ptr);
        /* add my own handling here */
        break;
    default:
        status = gx_progress_bar_event_process(progress_bar,
                                                event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_create
- gx_progress_bar_event_draw
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_font_set"></a>gx_progress_bar_font_set


Ustaw czcionkę tekstu paska postępu

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_font_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia czcionkę widżetu paska postępu.

### <a name="parameters"></a>Parametry

- **progress_bar** Blok sterowania paskiem postępu
- **font_id** Identyfikator zasobu czcionki

### <a name="return-values"></a>Wartości zwrócone

- Zestaw czcionek pomyślnego postępu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT status = gx_progress_bar_font_set(&progress_bar,
                                        GX_FONT_ID_MEDIUM);

/* if status is GX_SUCCESS, the font was successfully assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_info_set"></a>gx_progress_bar_info_set


Ustaw strukturę informacji paska postępu

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_info_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>Opis

Ta usługa resetuje strukturę informacji widżetu pasek postępu.

### <a name="parameters"></a>Parametry

- **progress_bar** Blok sterowania paskiem postępu
- **informacje** Wskaźnik do struktury GX_PROGRESS_BAR_INFO. **Dodatek I** zawiera definicję dla struktury GX_PROGRESS_BAR_INFO.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie zresetował informacje paska postępu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_PROGRESS_BAR_INFO info;

info.gx_progress_bar_info_min_val = 0;
info.gx_progress_bar_info_max_val = 100;
info.gx_progress_bar_info_current_val = 0;
info.gx_progress_bar_font_id = GX_FONT_ID_SYSTEM_FONT;
info.gx_progress_bar_normal_text_color = GX_COLOR_ID_WHITE;
info.gx_progress_bar_selected_text_color = GX_COLOR_ID_BLUE;
info.gx_progress_bar_fill_pixelmap = 0;

status = gx_progress_bar_info_set(&progress_bar, &info);

/* if status == GX_SUCCESS the progress bar info was re-assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_info_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_pixelmap_set"></a>gx_progress_bar_pixelmap_set


Ustaw Pixelmap używany do rysowania paska postępu

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_pixelmap_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID pixelmap_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia Pixelmap używany do wypełnienia tła paska postępu.

### <a name="parameters"></a>Parametry

- **progress_bar** Blok sterowania paskiem postępu
- **pixelmap_id** Identyfikator zasobu Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- Pixelmap (0x00) pasek postępu zakończony pomyślnie **GX_SUCCESS**
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT status = gx_progress_bar_pixelmap_set(&progress_bar,
                                GX_PIXELMAP_ID_PROGRESS_FILL);

/* if status is GX_SUCCESS, the pixelmap was successfully assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_pielmap_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_range_set"></a>gx_progress_bar_range_set


Ustaw zakres wartości paska postępu

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_range_set(
    GX_PROGRESS_BAR *progress_bar,
    INT min_value, 
    INT max_value);
```

### <a name="description"></a>Opis

Ta usługa ustawia zakres wartości paska postępu.

### <a name="parameters"></a>Parametry

- **progress_bar** Blok sterowania paskiem postępu
- **MIN_VALUE** Minimalna wartość paska postępu
- **MAX_VALUE** Maksymalna wartość paska postępu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) zestaw zakresów paska postępu zakończonych powodzeniem
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT status = gx_progress_bar_range_set(progress_bar, 0, 100);

/* if status is GX_SUCCESS, the progress bar range was successfully assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_range_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_text_color_set"></a>gx_progress_bar_text_color_set


Ustawianie koloru tekstu paska postępu

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_text_color_set(
    GX_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>Opis

Ta usługa ustawia kolor tekstu widżetu pasek postępu.

### <a name="parameters"></a>Parametry

- **progress_bar** Blok sterowania paskiem postępu
- **normal_text_color** Identyfikator zasobu standardowego koloru tekstu, który był używany w normalnym stanie.
- **selected_text_color** Identyfikator zasobu wybranego koloru tekstu, który był używany podczas uzyskiwania fokusu elementu widget.
- **disabled_text_color** Identyfikator zasobu wyłączonego koloru tekstu, który był używany, gdy GX_STYLE_ENABLED nie jest aktywny

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) ustawiony kolor tekstu paska postępu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set text colors for the progress bar “my_progress_bar”*/
UINT status = gx_progress_bar_text_color_set(&my_progress_bar,
                        GX_COLOR_ID_NORMAL_TEXT,
                        GX_COLOR_ID_SELECTED_TEXT,
                        GX_COLOR_ID_DISABLED_TEXT);

/* if status is GX_SUCCESS, the progress bar text colors were successfully assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_draw
- gx_progress_bar_value_set

## <a name="gx_progress_bar_text_draw"></a>gx_progress_bar_text_draw


Rysuj tekst paska postępu

### <a name="prototype"></a>Prototype

```C
VOID gx_progress_bar_text_draw(GX_PROGRESS_BAR *progress_bar)
```

### <a name="description"></a>Opis

Ta usługa rysuje tekst określonego paska postępu. Ta funkcja jest wywoływana wewnętrznie jako część gx_progress_bar_draw (), ale jest dostępna dla aplikacji w celu obsługi tych przypadków, w których aplikacja definiuje niestandardową funkcję rysowania paska postępu.

### <a name="parameters"></a>Parametry

- **pasek postępu** Wskaźnik do bloku sterowania paskiem postępu

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom progress bar drawing function. */

VOID my_progress_bar_draw(GX_PROGRESS_BAR *progress_bar)
{
    /* Call default progress bar background draw. */
    gx_progress_bar_background_draw(progress_bar);

    /* Call default progress bar text draw. */
    gx_progress_bar_text_draw(progress_bar);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_value_set

## <a name="gx_progress_bar_value_set"></a>gx_progress_bar_value_set


Ustaw bieżącą wartość paska postępu

### <a name="prototype"></a>Prototype

```C
UINT gx_progress_bar_value_set(
    GX_PROGRESS_BAR *progress_bar,
    INT value);
```

### <a name="description"></a>Opis

Ta usługa przypisuje bieżącą wartość paska postępu. Widżet paska postępu automatycznie unieważnia się i ponownie narysuje po zmianie wartości paska postępu.

### <a name="parameters"></a>Parametry

- **progress_bar** Blok sterowania paskiem postępu
- **wartość** Bieżąca wartość paska postępu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił wartość paska postępu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT status = gx_progress_bar_value_set(progress_bar, 50);

/* if status == GX_SUCCESS the progress bar value was successfully assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_progress_bar_value_create
- gx_progress_bar_draw
- gx_progress_bar_event_process
- gx_progress_bar_font_set
- gx_progress_bar_info_set
- gx_progress_bar_pielmap_set
- gx_progress_bar_range_set
- gx_progress_bar_text_color_set
- gx_progress_bar_text_draw

## <a name="gx_prompt_create"></a>gx_prompt_create


Utwórz monit

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_create(
    GX_PROMPT *prompt, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    GX_RESOURCE_ID text_id,
    ULONG style, 
    USHORT prompt_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet monitu.

GX_PROMPT pochodzi od GX_WIDGET i obsługuje wszystkie gx_widget usługi.

### <a name="parameters"></a>Parametry

- **Wskaźnik** do widżetu nadrzędnego
- **text_id** Identyfikator zasobu tekstu monitu
- **styl** Styl monitu. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **prompt_id** Zdefiniowany przez aplikację identyfikator monitu
- **rozmiar** Wymiary monitu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — pomyślne utworzenie monitu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “my_prompt”. */
status = gx_prompt_create(&my_prompt, “my_promPt”, &my_parent,
                    MY_PROMPT_TEXT_RESOURCE_ID,
                    GX_STYLE_BORDER_RAISED, MY_PROPMT_ID, &size);

/* If status is GX_SUCCESS the prompt “my_prompt” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_draw"></a>gx_prompt_draw


Rysuj monit

### <a name="prototype"></a>Prototype

```C
VOID gx_prompt_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>Opis

Ta usługa rysuje widżet monitu. Ta usługa jest wywoływana wewnętrznie przez GUIX podczas odświeżania kanwy, ale może być również wywoływana przez niestandardowe funkcje rysowania.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do monitu z blokiem kontrolki widżetu

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom prompt drawing function. */

VOID my_prompt_draw(GX_PROMPT *prompt)
{
    /* Call default prompt draw. */
    gx_prompt_draw(prompt);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_event_process"></a>gx_prompt_event_process


Zdarzenie monitu procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego monitu. Ta usługa powinna być wywoływana jako domyślna procedura obsługi zdarzeń przez wszelkie niestandardowe funkcje przetwarzania zdarzeń monitu.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do monitu o sterowanie
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia pomyślnego monitowania **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic prompt event processing as part of custom event processing function. */

UINT custom_prompt_event_process(GX_PROMPT *prompt, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default prompt event processing */
        status = gx_prompt_event_process(prompt, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_font_set"></a>gx_prompt_font_set


Ustawianie czcionki monitu

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_font_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia czcionkę widżetu monit.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do monitu z blokiem kontrolki widżetu
- **font_id** Identyfikator zasobu czcionki

### <a name="return-values"></a>Wartości zwrócone

- Zestaw czcionek pomyślnego monitu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the font of “my_prompt”. */
status = gx_prompt_font_set(&my_prompt, MY_PROMPT_FONT_ID);

/* If status is GX_SUCCESS the font for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_text_color_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_color_set"></a>gx_prompt_text_color_set


Ustaw kolor tekstu monitu

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_color_set(
    GX_PROMPT *prompt,
    GX_RESOURCE_ID normal_color,
    GX_RESOURCE_ID selected_color,
    GX_RESOURCE_ID disabled_color);
```

### <a name="description"></a>Opis

Ta usługa ustawia kolor tekstu widżetu monit.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do monitu z blokiem kontrolki widżetu
- **normal_color** Identyfikator zasobu koloru dla zwykłego tekstu. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **selected_color** Identyfikator zasobu koloru dla zaznaczonego tekstu używany, gdy element widget uzyskuje fokus. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **disabled_color** Identyfikator zasobu koloru dla wyłączonego tekstu używany, gdy GX_STYLE_ENABLED nie jest aktywny. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — zestaw kolorów tekstu monitu pomyślnego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET_SIZE** (0X14) Nieprawidłowy rozmiar widżetu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the text color of “my_prompt”. */
status = gx_prompt_text_color_set(&my_prompt,
                    GX_COLOR_ID_BLACK,
                    GX_COLOR_ID_LIGHTGRAY,
                    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_get
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_draw"></a>gx_prompt_text_draw


Funkcja obsługi rysowania

### <a name="prototype"></a>Prototype

```C
VOID gx_prompt_text_draw(GX_PROMPT *prompt);
```

### <a name="description"></a>Opis

Ta funkcja obsługi służy do rysowania części tekstowej monitu. Ta funkcja jest wywoływana wewnętrznie przez gx_prompt_draw () i jest udostępniana jako osobny interfejs API jako wygoda dla aplikacji, które definiują funkcję niestandardowego rysowania monitów. Aplikacje, które chcą dostosować Rysowanie w tle monitów, mogą zapewnić swoją niestandardową funkcję rysowania i wywoływać usługę gx_prompt_text_draw jako część niestandardowego rysunku, aby narysować tekst monitu w tle.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do bloku sterowania monitem

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Define a custom drawing function */
VOID my_prompt_draw(GX_PROMPT *prompt)
{
    /* insert code here to draw prompt background */

    /* call support function to do text drawing */
    gx_prompt_text_draw();

    /* draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) prompt);
}
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_get"></a>gx_prompt_text_get


Pobierz tekst monitu (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_CHAR **return_text);
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_prompt_text_get_ext ().

Ta usługa Pobiera tekst widżetu monit.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do monitu z blokiem kontrolki widżetu
- **return_text** Wskaźnik do miejsca docelowego dla tekstu

### <a name="return-values"></a>Wartości zwrócone

- Tekst monitu o pomyślne **zaGX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_PROMPT my_prompt;
GX_CHAR *my_prompt_text;

/* Get the text of “my_prompt”. */
status = gx_prompt_text_get(&my_prompt, &my_prompt_text);

/* If status is GX_SUCCESS the pointer “my_prompt_text” points to the text displayed by “my_prompt”. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_get_ext"></a>gx_prompt_text_get_ext


Pobierz tekst monitu

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_get(
    GX_PROMPT *prompt, 
    GX_STRING *return_string);
```

### <a name="description"></a>Opis

Ta usługa Pobiera ciąg widżetu monitu.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do monitu z blokiem kontrolki widżetu
- **return_string** Wskaźnik do miejsca docelowego dla ciągu

### <a name="return-values"></a>Wartości zwrócone

- Tekst monitu o pomyślne **zaGX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_PROMPT my_prompt;
GX_STRING my_prompt_string;

/* Get the text of “my_prompt”. */
status = gx_prompt_text_get_ext(&my_prompt, &my_prompt_string);

/* If status is GX_SUCCESS then my_prompt_string has been initialize to hold a copy of the prompt string. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_set

## <a name="gx_prompt_text_id_set"></a>gx_prompt_text_id_set


Ustaw identyfikator tekstu monitu

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_id_set(
    GX_PROMPT *prompt, 
    GX_RESOURCE_ID string_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia identyfikator ciągu dla widżetu monitu tekstu.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do monitu z blokiem kontrolki widżetu
- **string_id** Identyfikator zasobu ciągu

### <a name="return-values"></a>Wartości zwrócone

- Identyfikator SMS pomyślnego monitu o podanie wartości **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- Funkcja wolnych pamięci **GX_SYSTEM_MEMORY_ERROR** (0x30) nie jest zdefiniowana

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the string ID of “my_prompt”. */
status = gx_prompt_text_id_set(&my_prompt, MY_STRING_ID);

/* If status is GX_SUCCESS the text ID for prompt “my_prompt” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_get
- gx_prompt_text_set

## <a name="gx_prompt_text_set"></a>gx_prompt_text_set


Ustaw tekst monitu (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_set(
    GX_PROMPT *prompt, 
    GX_CHAR *text);
```

### <a name="description"></a>Opis

Ta usługa została wycofana na korzyść gx_prompt_text_set_ext ().

Ta usługa ustawia tekst widżetu monit. Jeśli widżet monit został utworzony z GX_STYLE_TEXT_COPY stylu, widżet tworzy prywatną kopię ciągu tekstowego przypisanego. Jeśli GX_STYLE_TEXT_COPY nie jest aktywny, widżet nie tworzy prywatnej kopii ciągu przychodzącego, w związku z czym ciąg musi być statycznie lub globalnie przydzielony, tj. nie może to być automatyczna lub Tymczasowa zmienna.

GX_PROMPT pochodzi od GX_WIDGET i w związku z tym wszystkie gx_widget usługi API mogą być używane z GX_PROMPT.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do monitu z blokiem kontrolki widżetu
- **tekst** Wskaźnik do tekstu

### <a name="return-values"></a>Wartości zwrócone

- Zestaw tekstu monitu o pomyślną **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Funkcja alokacji pamięci **GX_SYSTEM_MEMORY_ERROR** (0x30) nie jest zdefiniowana
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the text of “my_prompt” to “my_text”. */
status = gx_prompt_text_set(&my_prompt, “my_text”);

/* If status is GX_SUCCESS the text for “my_prompt” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_get

## <a name="gx_prompt_text_set_ext"></a>gx_prompt_text_set_ext

Ustaw tekst monitu

### <a name="prototype"></a>Prototype

```C
UINT gx_prompt_text_set_ext(
    GX_PROMPT *prompt,
    GX_STRING *string);
```

### <a name="description"></a>Opis

Ta usługa ustawia tekst widżetu monit. Jeśli widżet monit został utworzony z GX_STYLE_TEXT_COPY stylu, widżet tworzy prywatną kopię ciągu tekstowego przypisanego. Jeśli GX_STYLE_TEXT_COPY nie jest aktywny, widżet nie tworzy prywatnej kopii ciągu przychodzącego, w związku z czym ciąg musi być statycznie lub globalnie przydzielony, tj. nie może to być automatyczna lub Tymczasowa zmienna.

GX_PROMPT pochodzi od GX_WIDGET i w związku z tym wszystkie gx_widget usługi API mogą być używane z GX_PROMPT.

### <a name="parameters"></a>Parametry

- **Monituj** Wskaźnik do monitu z blokiem kontrolki widżetu
- **tekst** Wskaźnik do tekstu

### <a name="return-values"></a>Wartości zwrócone

- Zestaw tekstu monitu o pomyślną **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Funkcja alokacji pamięci **GX_SYSTEM_MEMORY_ERROR** (0x30) nie jest zdefiniowana
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING new_string;
new_string.gx_string_ptr = “my_text”;
new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Set the text of “my_prompt” to “new_string”. */
status = gx_prompt_text_set(&my_prompt, &new_string);

/* If status is GX_SUCCESS the text for “my_prompt” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_prompt_create
- gx_pixelmap_prompt_draw
- gx_pixelmap_prompt_pixelmap_set
- gx_prompt_create
- gx_prompt_draw
- gx_prompt_event_process
- gx_prompt_font_set
- gx_prompt_text_color_set
- gx_prompt_text_id_set
- gx_prompt_text_get

## <a name="gx_radial_progress_bar_anchor_set"></a>gx_radial_progress_bar_anchor_set


Ustaw kąt początkowy

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_anchor_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE angle);
```

### <a name="description"></a>Opis

Ta usługa ustawia kąt początkowy dla paska postępu promieniowego.

### <a name="parameters"></a>Parametry

- Wskaźnik paska **postępu** dla bloku sterowania paska postępu
- **kąt** Kąt początkowy łuku okręgu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) powodzenie promienia słupkowego na pasku postępu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_VALUE start_angle = 90;

/* Set the start angle of “my_progress_bar” to 90 degree. */
status = gx_radial_progress_bar_anchor_set(&my_progress_bar, start_angle);

/* If status is GX_SUCCESS the anchor value of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_background_draw"></a>gx_radial_progress_bar_background_draw


Rysuj tło

### <a name="prototype"></a>Prototype

```C
VOID gx_radial_progress_bar_background_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Opis

Ta usługa rysuje tło paska postępu promieniowego. Ta usługa jest wewnętrznie przywoływana przez funkcję gx_radial_progress_bar_draw, ale jest udostępniona do użycia przez aplikację w takich przypadkach, w której aplikacja definiuje niestandardową funkcję rysowania paska postępu

### <a name="parameters"></a>Parametry

- **pasek postępu** Wskaźnik do bloku kontrolki paska postępu promieniowego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom radial progress bar drawing function. */

VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Call default radial progress bar background draw. */
    gx_radial_progress_bar_background_draw(radial_progress);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```
### <a name="see-also"></a>Zobacz też

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_create"></a>gx_radial_progress_bar_create


Utwórz pasek postępu promieniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_create(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RADIAL_PROGRESS_BAR_INFO *info,
    ULONG style
    USHORT id);
```

### <a name="description"></a>Opis

Ta usługa tworzy Radialny pasek postępu.

Jeśli styl widżetu GX_STYLE_ENABLED zostanie zastosowany do paska postępu, pasek postępu przyjmie pen_down, pen_drag i pen_up dane wejściowe, aby zmodyfikować bieżącą wartość paska postępu.

GX_STYLE_PROGRESS_TEXT_DRAW stylu widżetu można użyć, aby włączyć rysowanie wartości paska postępu jako tekstu w obszarze paska postępu. Jeśli ten styl jest używany w połączeniu z GX_STYLE_PROGRESS_PERCENT stylu, wartość paska postępu jest wyświetlana jako wartość procentowa. W przeciwnym razie wartość paska postępu jest wyświetlana jako bieżąca wartość kątowa.

### <a name="parameters"></a>Parametry

- **pasek postępu** Wskaźnik do kontrolki paska postępu promieniowego
- Wskaźnik paska **postępu** dla bloku sterowania paska postępu
- **Nazwa** Nazwa paska postępu promieniowego
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **informacje** Wskaźnik do struktury GX_RADIAL_PROGRESS_BAR. **Dodatek I** zawiera definicję dla struktury GX_RADIAL_PROGRESS_BAR.
- **styl** Styl paska postępu promieniowego
- **Identyfikator** zdefiniowany przez aplikację pasek postępu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeprowadzono pasek postępu radialnego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy element widget elementu nadrzędnego

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RAIDAL_PROGRESS_BAR_INFO info;

info.gx_radial_progress_bar_info_xcenter = 200;
info.gx_radial_progress_bar_info_ycenter = 200;
info.gx_radial_progress_bar_info_radius = 100;
info.gx_radial_progress_bar_info_current_angle = 180;
info.gx_radial_progress_bar_info_anchor_val = -180;
info.gx_radial_progress_bar_info_font_id = GX_FONT_ID_SYSTEM;
info.gx_raidal_progress_bar_info_normal_text_color =
                                        GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_selected_text_color =
                                        GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_disabled_text_color =
                                        GX_COLOR_ID_DISABLED_TEXT;
info.gx_radial_progress_bar_info_normal_brush_width = 20;
info.gx_raidal_progress_bar_info_selected_brush_width = 16;
info.gx_radial_progress_bar_info_normal_brush_color =
                                        GX_COLOR_ID_WIDGET_FILL;
info.gx_radial_progress_bar_info_selected_brush_color =
                                        GX_COLOR_ID_SELECTED_FILL;

/* Create a radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_create(&my_progress_bar,
                    “my_progress_bar”, parent, &info,
                    GX_STYLE_ENABLED | GX_STYLE_TRANSPARENT |
                    GX_STYLE_PROGRESS_TEXT_DRAW,
                    ID_MY_RADIAL_PROGRESS);

/* If status is GX_SUCCESS the radial progress bar “my_progress_bar” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_draw"></a>gx_radial_progress_bar_draw


Rysowanie paska postępu promieniowego

### <a name="prototype"></a>Prototype

```C
VOID gx_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Opis

Ta usługa rysuje pasek postępu promieniowego. Ta usługa jest używana wewnętrznie do przywoływania przez funkcję gx_radial_progress_bar_create, ale jest udostępniona do użycia przez aplikację w takich przypadkach, w której aplikacja definiuje niestandardową funkcję rysowania paska postępu.

### <a name="parameters"></a>Parametry

- **pasek postępu** Wskaźnik do bloku kontrolki paska postępu promieniowego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom radial progress bar drawing function. */

VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Call default radial progress bar draw. */
    gx_radial_progress_bar_draw(radial_progress);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```

### <a name="see-also"></a>Zobacz też

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_size_calculate
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_event_process"></a>gx_radial_progress_bar_event_process


Zdarzenie paska postępu promieniowego procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_event_process(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie paska postępu promieniowego. Ta funkcja jest wewnętrznie przywoływana przez funkcję gx_radial_progress_bar_create, ale jest narażona na użycie przez aplikację w takich przypadkach, w których aplikacja definiuje niestandardową funkcję przetwarzania zdarzeń dotyczących postępu.

### <a name="parameters"></a>Parametry

- Wskaźnik paska **postępu** dla bloku sterowania paska postępu
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia dotyczącego paska postępu, **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_RADIAL_PROGRESS_BAR *radial_progress, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
        case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_radial_progress_bar_event_process(
                            radial_progress, event_ptr);
        /* add my own handling here */
        break;
    default:
        status = gx_radial_progress_bar_event_process(
                            radial_progress, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_font_set"></a>gx_radial_progress_bar_font_set


Ustaw czcionkę paska postępu promieniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_font_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia czcionkę widżetu pasek postępu promieniowego. Ten parametr nie działa, jeśli styl widżetu GX_STYLE_PROGRESS_TEXT_DRAW nie jest ustawiony.

### <a name="parameters"></a>Parametry

- Wskaźnik paska **postępu** dla bloku sterowania paska postępu
- **font_id** Identyfikator zasobu czcionki

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) powodzenie promienia paska postępu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set font for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_font_set(&my_progress_bar, font);

/* If status is GX_SUCCESS the font of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_info_set"></a>gx_radial_progress_bar_info_set


Ustaw informacje o pasku postępu promieniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_info_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RADIAL_PROGRESS_BAR_INFO *info);
```

### <a name="description"></a>Opis

Ta usługa resetuje parametry informacji przypisanych do paska postępu promieniowego.

### <a name="parameters"></a>Parametry

- Wskaźnik paska **postępu** dla bloku sterowania paska postępu
- **informacje** Wskaźnik do struktury informacji paska postępu promieniowego. **Dodatek I** zawiera definicję dla struktury GX_RADIAL_PROGRESS_BAR_INFO.

### <a name="return-values"></a>Wartości zwrócone

- Zestaw informacyjny paska postępu **GX_SUCCESS** (0X00) zakończony pomyślnie
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RAIDAL_PROGRESS_BAR_INFO info;

info.gx_radial_progress_bar_info_xcenter = 200;
info.gx_radial_progress_bar_info_ycenter = 200;
info.gx_radial_progress_bar_info_radius = 100;
info.gx_radial_progress_bar_info_current_angle = 180;
info.gx_radial_progress_bar_info_anchor_val = -180;
info.gx_radial_progress_bar_info_font_id = GX_FONT_ID_SYSTEM;
info.gx_raidal_progress_bar_info_normal_text_color =
                                GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_selected_text_color =
                                GX_COLOR_ID_TEXT;
info.gx_radial_progress_bar_info_disabled_text_color =
                                GX_COLOR_ID_DISABLED_TEXT;
info.gx_radial_progress_bar_info_normal_brush_width = 20;
info.gx_raidal_progress_bar_info_selected_brush_width = 16;
info.gx_radial_progress_bar_info_normal_brush_color =
                                GX_COLOR_ID_WIDGET_FILL;
info.gx_radial_progress_bar_info_selected_brush_color =
                                GX_COLOR_ID_SELECTED_FILL;

/* Set appearance information for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_info_set(&my_progress_bar, &info);

/* If status is GX_SUCCESS the appearance information of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_text_color_set"></a>gx_radial_progress_bar_text_color_set


Ustaw kolor tekstu paska postępu promieniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_text_color_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCE_ID disabled_text_color);
```

### <a name="description"></a>Opis

Ta usługa ustawia kolor tekstu paska postępu promieniowego. Ta wartość jest używana tylko wtedy, gdy styl GX_STYLE_PROGRESS_TEXT_DRAW jest ustawiony.

### <a name="parameters"></a>Parametry

- Wskaźnik paska **postępu** dla bloku sterowania paska postępu
- **normal_color** Identyfikator zasobu koloru tekstu w normalnym stanie. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **selected_color** Identyfikator zasobu koloru tekstu, gdy element widget uzyskuje fokus. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **disabled_color** Identyfikator zasobu tekstu, gdy styl GX_STYLE_ENABLED nie jest ustawiony. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawiony kolor słupka na pasku postępu dla tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) Nieprawidłowa kontrola widżetu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set text color for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_text_color_set(&my_progress_bar,
                            GX_COLOR_ID_NORMAL_TEXT,
                            GX_COLOR_ID_SELECTED_TEXT,
                            GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS the text color of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_draw
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_text_draw"></a>gx_radial_progress_bar_text_draw


Rysuj tekst paska postępu promieniowego

### <a name="prototype"></a>Prototype

```C
VOID gx_radial_progress_bar_text_draw(GX_RADIAL_PROGRESS_BAR *progress_bar);
```

### <a name="description"></a>Opis

Ta usługa rysuje tekst określonego paska postępu promieniowego. Ta funkcja jest wywoływana wewnętrznie jako część gx_radial_progress_bar_draw (), ale jest dostępna dla aplikacji w celu obsługi tych przypadków, w których aplikacja definiuje niestandardową funkcję rysowania paska postępu.

### <a name="parameters"></a>Parametry

- **pasek postępu** Wskaźnik do bloku kontrolki paska postępu promieniowego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Draw text for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_text_draw (&my_progress_bar);

/* If status is GX_SUCCESS the text of “my_progress_bar” has been drawn. */

/* Write a custom radial progress bar drawing function. */
VOID my_radial_progress_bar_draw(GX_RADIAL_PROGRESS_BAR *radial_progress)
{
    /* Add your own background draw here. */

    /* Call default radial progress bar text draw. */
    gx_radial_progress_bar_text_draw(radial_progress);

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radial_progress);
}
```

### <a name="see-also"></a>Zobacz też

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_value_set

## <a name="gx_radial_progress_bar_value_set"></a>gx_radial_progress_bar_value_set


Ustaw wartość paska postępu promieniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_progress_bar_value_set(
    GX_RADIAL_PROGRESS_BAR *progress_bar, 
    GX_VALUE value);
```

### <a name="description"></a>Opis

Ta usługa ustawia wartość paska postępu promieniowego. Przypisana wartość jest ograniczona do zakresu [-360, 360], definiując możliwy zakres wartości kątowych dla bieżącej lokalizacji paska postępu. Aplikacja musi skalować podaną rzeczywistą wartość, aby przypisać wartość kątową do widżetu pasek postępu.

Pasek postępu jest rysowany tak, aby bieżąca wartość wskazywała różnicę kątową między pozycją zakotwiczenia a punktem końcowym górnego łuku. Wartości ujemne powodują, że łuk ma być rysowany w kierunku w prawo, rozpoczynając od pozycji zakotwiczenia. Dodatnia wartość bieżąca powoduje, że łuk ma być rysowany w kierunku w prawo, rozpoczynając od pozycji zakotwiczenia.

Na przykład, aby narysować łuk zaczynający się na górze łuku (12 pozycji) i kończący się z prawej strony (trzy pozycje na końcu), przypisz wartość zakotwiczenia o 90 stopni i bieżącą wartość-90 stopni.

### <a name="parameters"></a>Parametry

- Wskaźnik paska **postępu** dla bloku sterowania paska postępu
- **wartość** Nowa wartość paska postępu

### <a name="return-values"></a>Wartości zwrócone

- Wartość ustawienia słupkowego postępu, **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- Nieprawidłowe wskaźniki **GX_PTR_ERROR** (0x07)
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_VALUE new_value = 180;

/* Set value for radial progress bar “my_progress_bar”. */
status = gx_radial_progress_bar_value_set(&my_progress_bar,
                                        new_value);

/* If status is GX_SUCCESS the value of “my_progress_bar” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_progress_bar_anchor_set
- gx_radial_progress_bar_background_draw
- gx_radial_progress_bar_create
- gx_radial_progress_bar_draw
- gx_radial_progress_bar_event_process
- gx_radial_progress_bar_font_set
- gx_radial_progress_bar_info_set
- gx_radial_progress_bar_text_color_set
- gx_radial_progress_bar_text_draw

## <a name="gx_radio_button_create"></a>gx_radio_button_create


Utwórz przycisk radiowy

### <a name="prototype"></a>Prototype

```C
UINT gx_radio_button_create(
    GX_RADIO_BUTTON *button,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, ULONG style,
    USHORT radio_button_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet przycisku radiowego. GX_RADIO_BUTTON pochodzi od GX_TEXT_BUTTON i w związku z tym wszystkie usługi gx_text_button są również obsługiwane przez ten typ widżetu.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki przycisku radiowego
- **Nazwa** Logiczna nazwa widżetu przycisku radiowego
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **text_id** Identyfikator zasobu przycisku radiowego
- **styl** Styl przycisku radiowego. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **radio_button_id** Zdefiniowany przez aplikację przycisk radiowy
- **rozmiar** Wymiary przycisku radiowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzono przycisk radiowy
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_** ROZMIAR (0x19) Nieprawidłowy rozmiar bloku kontrolki widgetu
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “my_radio_button”. */
status = gx_radio_button_create(&my_radio_button, “my_radio_button”, &my_parent,
                    MY_RADIO_BUTTON_TEXT_RESOURCE_ID,
                    GX_STYLE_BORDER_RAISED, MY_RADIO_BUTTON_ID, &size);

/* If status is GX_SUCCESS the radio button “my_radio_button” has been created. */
```
### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_draw

## <a name="gx_radio_button_draw"></a>gx_radio_button_draw


Przycisk rysowania przycisku radiowego

### <a name="prototype"></a>Prototype

```C
VOID gx_radio_button_draw(GX_RADIO_BUTTON *button);
```

### <a name="description"></a>Opis

Ta usługa rysuje widżet przycisku radiowego. Ta usługa jest wywoływana wewnętrznie przez odświeżanie kanwy GUIX, ale może być również wywoływana przez zastąpione funkcje rysowania.

### <a name="parameters"></a>Parametry

- **przycisk** Wskaźnik do bloku kontrolki widżetu przycisk radiowy

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom radio button drawing function. */

VOID my_radio_button_draw(GX_RADIO_BUTTON *radio_button)
{
    /* Call default radio button draw. */
    gx_radio_button_draw(radio_button);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *)radio_button);
}
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_create

## <a name="gx_radio_button_pixelmap_set"></a>gx_radio_button_pixelmap_set


Ustaw pixelmaps dla przycisku radiowego

### <a name="prototype"></a>Prototype

```C
UINT gx_radio_button_pixelmap_set(
    GX_RADIO_BUTTON *button,
    GX_RESOURCE_ID off_id,
    GX_RESOURCE_ID on_id,
    GX_RESOURCE_ID off_disabled_id,
    GX_RESOURCE_ID on_disabled_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje pixelmaps do wyświetlania przez określony przycisk radiowy dla każdego stanu przycisku. Identyfikatory zasobów mogą być zduplikowane.

### <a name="parameters"></a>Parametry

- **off_id** Pixelmap używany do stanu wyłączenia przycisku radiowego
- **on_id** Pixelmap używany dla przycisku radiowego w stanie
- **off_disabled_id** Pixelmap używany dla przycisku radiowego wyłączone i wyłączone
- **on_disabled_id** Pixelmap używany dla przycisku radiowego wyłączone i w stanie

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) przycisk radiowy pomyślnego pixelmaps zestawu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set pixelmap for “my_radio_button”. */
status = gx_radio_button_pixelmap_set(&my_radio_button,
                                MY_OFF_PIXELMAP,
                                MY_ON_PIXELMAP,
                                MY_OFF_DISABLED_PIXELMAP,
                                MY_ON_DISABLED_PIXELMAP);

/* If status is GX_SUCCESS the pixelmaps for radio button “my_radio_button” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_color_set
- gx_text_button_draw
- gx_radio_button_create

## <a name="gx_radial_slider_anchor_angles_set"></a>gx_radial_slider_anchor_angles_set


Ustaw listę zakotwiczenia suwaka promieniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_anchor_angles_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE *anchor_angles, 
    USHORT anchor_count);
```

### <a name="description"></a>Opis

Ta usługa Ustawia kąty zakotwiczenia dla suwaka promieniowego. Jeśli jest ustawiona lista kątów zakotwiczenia, kąt suwaka promieniowego będzie jednym ze zdefiniowanych kątów zakotwiczenia.

### <a name="parameters"></a>Parametry

- **suwak** Blok kontrolny suwaka promieniowego
- **anchor_angles** Lista kątów do ustawienia
- **anchor_count** Liczba kątów zakotwiczenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — Ustawianie kątów zakotwiczenia
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet
- **GX_INVALID_VALUE** (0X22) nieprawidłowa lista zakotwiczenia

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_VALUE anchor_angles[]={0, 30, 60, 90, 120, 150, 180};
USHORT anchor_count = 7;

/* Set anchor angles for radial slider. */
status = gx_radial_slider_anchor_angles_set(&my_radial_slider,
                                anchor_angles, anchor_count);

/* If status is GX_SUCCESS the anchor angles have been set for “my_radial_slider”. */

/* Set anchor angles for radial slider. */
status = gx_radial_slider_anchor_angles_set(&my_radial_slider,
                                GX_NULL, 0);

/* If status is GX_SUCCESS the anchor angles have been removed from “my_radial_slider”. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_angle_set"></a>gx_radial_slider_angle_set

Ustaw kąt suwaka promieniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_angle_set(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE new_angle);
```

### <a name="description"></a>Opis

Ta usługa ustawia nową wartość kąta dla suwaka promieniowego.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka promieniowego
- **new_angle** Nowa wartość kąta, która ma zostać ustawiona

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawiony kąt suwaka promieniowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set “my_radial_slider” angle to 0 degree(3 o’clock position). */
status = gx_radial_slider_angle_set(&my_radial_slider, 0);

/* If status is GX_SUCCESS the value of “my_radial_slider” has been set to 0 degree. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_animation_set"></a>gx_radial_slider_animation_set


Utwórz informacje o animacji suwaka promieniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_animation_set(
    GX_RADIAL_SLIDER *slider,
    USHORT steps, USHORT delay, 
    USHORT animation_style,
    VOID (*animation_update_callback)(GX_RADIAL_SLIDER *slider));
```

### <a name="description"></a>Opis

Ta usługa ustawia kroki animacji, czas opóźnienia i style animacji dla animacji promieniowej wskazówki suwaka.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka promieniowego
- **kroki** Łączna liczba kroków dla jednej animacji
- **opóźnienie** Czas opóźnienia dla każdego kroku animacji
- **animation_style** Typ funkcji krzywych napięcia, obejmuje:
  - GX_ANIMATION_BACK_EASE_IN
  - GX_ANIMATION_BACK_EASE_OUT
  - GX_ANIMATION_BACK_EASE_IN_OUT
  - GX_ANIMATION_BOUNCE_EASE_IN
  - GX_ANIMATION_BOUNCE_EASE_OUT
  - GX_ANIMATION_BOUNCE_EASE_IN_OUT
  - GX_ANIMATION_CIRC_EASE_IN
  - GX_ANIMATION_CIRC_EASE_OUT
  - GX_ANIMATION_CIRC_EASE_IN_OUT
  - GX_ANIMATION_CUBIC_EASE_IN
  - GX_ANIMATION_CUBIC_EASE_OUT
  - GX_ANIMATION_CUBIC_EASE_IN_OUT
  - GX_ANIMATION_ELASTIC_EASE_IN
  - GX_ANIMATION_ELASTIC_EASE_OUT
  - GX_ANIMATION_ELASTIC_EASE_IN_OUT
  - GX_ANIMATION_EXPO_EASE_IN
  - GX_ANIMATION_EXPO_EASE_OUT
  - GX_ANIMATION_EXPO_EASE_IN_OUT
  - GX_ANIMATION_QUAD_EASE_IN
  - GX_ANIMATION_QUAD_EASE_OUT
  - GX_ANIMATION_QUAD_EASE_IN_OUT
  - GX_ANIMATION_QUART_EASE_IN
  - GX_ANIMATION_QUART_EASE_OUT
  - GX_ANIMATION_QUART_EASE_IN_OUT
  - GX_ANIMATION_QUINT_EASE_IN
  - GX_ANIMATION_QUINT_EASE_OUT
  - GX_ANIMATION_QUINT_EASE_IN_OUT
  - GX_ANIMATION_SINE_EASE_IN
  - GX_ANIMATION_SINE_EASE_OUT
  - GX_ANIMATION_SINE_EASE_IN_OUT
- **animation_update_callback** Zdefiniowana przez użytkownika funkcja wywołania zwrotnego, która będzie wywoływana po każdym kroku animacji

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) ustawiono animację suwaka "powodzenie"
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
VOID animation_callback(GX_RADIAL_SLIDER *slider)
{
    /* This function will be called after each animation step,
    add custom code here. */
}

/* Set animation info for “my_radial_slider”. */
status = gx_radial_slider_animation_set(&my_radial_slider, 15, 2,
                                GX_ANIMATION_CIRC_EASE_IN_OUT,
                                animation_callback);

/* If status is GX_SUCCESS the radial slider needle will move with specified animation. */

/* Disable animation for “my_radial_slider”. */
status = gx_radial_slider_animation_set(&my_radial_slider, 0, 0,
                                        0, 0);

/* If status is GX_SUCCESS the radial slider needle will move without animation. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_animation_start"></a>gx_radial_slider_animation_start


Ustaw nową wartość suwaka promieniowego na animację

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_animation_start(
    GX_RADIAL_SLIDER *slider,
    GX_VALUE target_angle);
```

### <a name="description"></a>Opis

Ta usługa uruchamia animację, aby przenieść wskazówkę z suwaka z bieżącego położenia do określonej pozycji.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka promieniowego
- **target_angle** Wartość kąta docelowego

### <a name="return-values"></a>Wartości zwrócone

- Początek animacji dla suwaka promieniowego **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Start an animation to move radial slider needle from
current position to 90 degree position. */
status = gx_radial_slider_animation_start(&my_radial_slider, 90);

/* If status is GX_SUCCESS the radial slider needle animation has been started. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_create"></a>gx_radial_slider_create


Utwórz suwak promieniowy

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_create(
    GX_RADIAL_SLIDER *slider,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RADIAL_SLIDER_INFO *info,
    ULONG style,
    USHORT slider_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet suwak promieniowy.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka promieniowego
- **Nazwa** Logiczna nazwa widżetu suwaka promieniowego
- **element nadrzędny** Wskaźnik do widżetu nadrzędnego
- **informacje** Definicja wyglądu suwaka promieniowego, **dodatek I** zawiera definicję do GX_RADIAL_SLIDER_INFO.
- **styl** Styl przycisku radiowego. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **radio_button_id** Zdefiniowany przez aplikację suwak promieniowy
- **rozmiar** Wymiary suwaka promieniowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) udany suwak promieniowy
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_** ROZMIAR (0x19) Nieprawidłowy rozmiar bloku kontrolki widgetu
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy element widget elementu nadrzędnego

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RADIAL_SLIDER_INFO info;
GX_RECTANGLE size;

/* Distance from left side of widget to rotating center. */
info.gx_radial_slider_info_xcenter = 100;

/* Distance from top size of widget to rotating center. */
info.gx_radial_slider_info_ycenter = 100;

/* Radius of rotating circle. */
info.gx_radial_slider_info_radius = 100;

/* Widget of rotating track. */
info.gx_radial_slider_info_track_width = 40;

/* Current angle value. */
info.gx_radial_slider_info_current_angle = 0;

/* Minimum angle value. */
info.gx_radial_slider_min_anlge = -60;

/* Maximum angle value. */
info.gx_radial_slider_max_angle = 240;

/* Anchor value list. */
info.gx_radial_slider_angle_list = GX_NULL;

/* Anchor value count. */
info.gx_radial_slider_list_count = 0;

/* Resource ID of background pixelmap. */
info.gx_radial_slider_background_pixelmap = GX_PIXELMAP_ID_BKGRD;

/* Resource ID of needle pixelmap. */
info.gx_radial_slider_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Define widget size. */
gx_utility_rectangle_define(&size, 0, 0, 200, 200);

/* Create “my_radial_slider”. */
status = gx_radial_slider_create(&my_radial_slider,
                                “my_radial_slider”, &my_parent,
                                &info, GX_STYLE_ENABLED,
                                MY_RADIAL_SLIDER_ID, &size);

/* If status is GX_SUCCESS the radial slider “my_radial_slider” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_draw"></a>gx_radial_slider_draw


Suwak rysowania promieniowego

### <a name="prototype"></a>Prototype

```C
VOID gx_radial_slider_draw(GX_RADIAL_SLIDER *slider);
```

### <a name="description"></a>Opis

Ta usługa rysuje suwak promieniowy. Ta usługa jest wywoływana wewnętrznie przez odświeżanie kanwy GUIX, ale może być również wywoływana przez zastąpione funkcje rysowania.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka promieniowego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom radio button drawing function. */

VOID my_radial_slider_draw(GX_RADIAL_SLIDER *radial_slider)
{
    /* Call default radial slider draw. */
    gx_radio_slider_draw(radial_slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_event_process"></a>gx_radial_slider_event_process


Zdarzenie suwaka promieniowego procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_event_process(
    GX_RADIAL_SLIDER *slider,
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie suwaka promieniowego. Ta usługa powinna być wywoływana jako domyślna procedura obsługi zdarzeń przez wszelkie niestandardowe funkcje przetwarzania zdarzeń suwaka promieniowego.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka promieniowego
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia suwaka promieniowego " **GX_SUCCESS** (0x00)"
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom event processing function. */

UINT my_event_process(GX_RADIAL_SLIDER *slider,
                    GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_radial_slider_event_process(slider, event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_radial_slider_event_process(slider, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_info_get
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_info_get"></a>gx_radial_slider_info_get


Pobierz informacje o suwaku promieniowym

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_info_get(
    GX_RADIAL_SLIDER *slider,
    GX_RADIAL_SLIDER_INFO **info);
```

### <a name="description"></a>Opis

Ta usługa Pobiera wskaźnik informacji o suwaku promieniowym.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka promieniowego
- **informacje** Wskaźnik informacji o suwaku do pobrania

### <a name="return-values"></a>Wartości zwrócone

- Informacje dotyczące suwaka promieniowego **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RADIAL_SLIDER_INFO *info;

/* Retrive radial slider information structure. */
status = gx_radial_slider_info_get(&my_radial_slider,
                                    “my_radial_slider”, &info);

/* If status is GX_SUCCESS the radial slider information pointer of “my_radial_slider” has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_set
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_info_set"></a>gx_radial_slider_info_set


Ustaw informacje suwaka promieniowego

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_info_set(
    GX_RADIAL_SLIDER *slider,
    GX_RADIAL_SLIDER_INFO *info);
```

### <a name="description"></a>Opis

Ta usługa ustawia informacje o suwaku promieniowym.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka promieniowego
- **informacje** Informacje suwaka promieniowego do ustawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — zestaw informacyjny suwaka "powodzenie"
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RADIAL_SLIDER_INFO info;

/* Distance from left side of widget to rotating center. */
info.gx_radial_slider_info_xcenter = 100;

/* Distance from top size of widget to rotating center. */
info.gx_radial_slider_info_ycenter = 100;

/* Radius of rotating circle. */
info.gx_radial_slider_info_radius = 100;

/* Widget of rotating track. */
info.gx_radial_slider_info_track_width = 40;

/* Current angle value. */
info.gx_radial_slider_info_current_angle = 0;

/* Minimum angle value. */
info.gx_radial_slider_min_anlge = -60;

/* Maximum angle value. */
info.gx_radial_slider_max_angle = 240;

/* Anchor value list. */
info.gx_radial_slider_angle_list = GX_NULL;

/* Anchor value count. */
info.gx_radial_slider_list_count = 0;

/* Resource ID of background pixelmap. */
info.gx_radial_slider_background_pixelmap = GX_PIXELMAP_ID_BKGRD;

/* Resource ID of needle pixelmap. */
info.gx_radial_slider_needle_pixelmap = GX_PIXELMAP_ID_NEEDLE;

/* Reset radial slider info for “my_radial_slider”. */
status = gx_radial_slider_info_set(&my_radial_slider, &info);

/* If status is GX_SUCCESS the radial slider info of “my_radial_slider” has been reset. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_pixelmap_set

## <a name="gx_radial_slider_pixelmap_set"></a>gx_radial_slider_pixelmap_set


Ustaw suwak promieniowy pixelmaps

### <a name="prototype"></a>Prototype

```C
UINT gx_radial_slider_pixelmap_set(
    GX_RADIAL_SLIDER *slider,
    GX_RESOURCE_ID background_pixemap,
    GX_REOUSRCE_ID needle_pixelmap);
```

### <a name="description"></a>Opis

Ta usługa ustawia tło suwaka promieniowego i wskazówkę pixelmaps.

### <a name="parameters"></a>Parametry

- **suwak** Wskaźnik do bloku kontrolki suwaka promieniowego
- **background_pixelmap** Identyfikator zasobu w tle Pixelmap
- **needle_pixelmap** Identyfikator zasobu wskazówki Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- Pixelmap (0x00), pomyślne ustawienie suwaka promieniowego **GX_SUCCESS**
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create “my_radio_button”. */
status = gx_radial_slider_pixelmap_set(&my_radial_slider, GX_PIXELMAP_ID_BG, GX_PIXELMAP_ID_NEEDLE);

/* If status is GX_SUCCESS the background and needle pixelmap of “my_radial_slider” has been reset. */
```

### <a name="see-also"></a>Zobacz też

- gx_radial_slider_anchor_angles_set
- gx_radial_slider_angle_set
- gx_radial_slider_animation_set
- gx_radial_slider_animation_start
- gx_radial_slider_create
- gx_radial_slider_draw
- gx_radial_slider_event_process
- gx_radial_slider_info_get
- gx_radial_slider_info_set

## <a name="gx_rich_text_view_create"></a>gx_rich_text_view_create

Tworzenie widoku tekstu sformatowanego

### <a name="prototype"></a>Prototype

```C
UINT gx_rich_text_view_create(
    GX_RICH_TEXT_VIEW *text_view,
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id,
    GX_RICH_TEXT_FONTS *fonts,
    USHORT id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widok tekstu sformatowanego jako określony.


**Tagi formatowania są używane do wyświetlania typów specjalnych dla tekstu:**

- **\<b>\</b>** Ustaw czcionkę tekstową z określonym przez użytkownika identyfikatorem czcionki pogrubionej
- **\<i>\</i>** Ustaw czcionkę tekstową z określonym przez użytkownika kursywą identyfikatorem czcionki
- **\<u>\</u>** Włącz podkreślanie tekstu
- **\<f GX_FONT_ID>\</f>** Ustaw czcionkę tekstową o określonym identyfikatorze czcionki
- **\<c GX_COLOR_ID>\</c>** Ustaw czcionkę tekstu o określonym identyfikatorze koloru
- **\<hc GX_COLOR_ID>\</hc>** Ustaw kolor wyróżnienia tekstu określony identyfikator koloru
- **\<align left/right/center>\</align>** Ustawianie wyrównania tekstu

**Przykłady użycia tagów formatowania:**

- \<b>Jest to pogrubiony tekst< \b>
- \<i>Ten tekst jest pisany kursywą< \i>
- \<u>Jest to tekst z podkreśleniem< \u>
- \<f 0>Ten identyfikator czcionki tekstowej jest ustawiony na 0< \f>
- \<c 1>Ten identyfikator koloru tekstu jest ustawiony na 1< \c>
- \<hc 2>Ten identyfikator koloru wyróżnienia tekstu jest ustawiony na 2< \hc>
- \<align left> Ten tekst jest wyrównany do lewej< \align>

### <a name="parameters"></a>Parametry

- **text_view** Wskaźnik do bloku kontrolki widoku tekstu sformatowanego
- **Nazwa** Nazwa widoku tekstu sformatowanego
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **text_id** Identyfikator zasobu ciągu tekstowego
- **czcionki** Wskaźnik do informacji o czcionce widoku tekstu sformatowanego. **Dodatek I** zawiera definicję do GX_RICH_TEXT_FONTS struktury.
- **styl** Styl elementu widget. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **Identyfikator** zdefiniowany przez aplikację w widoku tekstu sformatowanego
- **rozmiar** Rozmiar widoku tekstu sformatowanego

### <a name="return-values"></a>Wartości zwrócone

- Zakończono Tworzenie widoku tekstu sformatowanego **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RICH_TEXT_VIEW rich_view;
GX_RCIH_TEXT_FONTS fonts;
GX_RECTANGLE size;

/* Defined widget size. */
gx_utility_rectangle_define(&size, 100, 100, 300, 150);

/* Define font information. */
fonts.gx_rich_text_fonts_normal_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_italic_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_italic_id = GX_FONT_ID_SYSTEM;

/* Create rich text view widget. */
status = gx_rich_text_view_create(&rich_view, “my_rich_view”,
                                  parent, GX_STRING_ID_TEST_STRING,
                                  &fonts,
                                  GX_STYLE_ENABLED,
                                  MY_RICH_VIEW_ID, &size);

/* If status is GX_SUCCESS the rich text view was successfully created. */

```

Aplikacja demonstracyjna demo_guix_widget_types, dostępna jako część instalacji programu GUIX Studio, zawiera kompletny przykład widżetu widok tekstu sformatowanego.

### <a name="see-also"></a>Zobacz też

- gx_rich_text_view_draw
- gx_rich_text_view_fonts_set
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_draw"></a>gx_rich_text_view_draw


Rysuj widok tekstu sformatowanego

### <a name="prototype"></a>Prototype

```C
VOID gx_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>Opis

Ta usługa Rysuje określony widżet widoku tekstu sformatowanego. Ta usługa jest zwykle wywoływana wewnętrznie przez GUIX w ramach operacji odświeżania kanwy, ale jest również dostępna dla aplikacji, która może chcieć udostępnić funkcję rysowania niestandardowego i wywoływać domyślny rysunek widoku tekstu sformatowanego jako niestandardowa baza rysunku.

### <a name="parameters"></a>Parametry

- **text_view** Wskaźnik do bloku kontrolki widżetu widok tekstu sformatowanego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom rich text view drawing function. */

VOID my_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view)
{
    /* Call default rich text view draw. */
    gx_rich_text_view_draw(text_view);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_rich_text_view_create
- gx_rich_text_view_fonts_set
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_fonts_set"></a>gx_rich_text_view_fonts_set

Ustaw czcionki widoku tekstu sformatowanego

### <a name="prototype"></a>Prototype

```C
UINT gx_rich_text_view_fonts_set(GX_RICH_TEXT_VIEW *text_view, GX_RICH_TEXT_FONTS *fonts);
```

### <a name="description"></a>Opis

Ta usługa ustawia czcionki widżetu widoku tekstu sformatowanego.

### <a name="parameters"></a>Parametry

- **text_view** Wskaźnik do bloku kontrolki widżetu widok tekstu sformatowanego
- **czcionki** Wskaźnik na informacje o czcionkach widoku tekstu sformatowanego. **Dodatek I** zawiera definicje do struktury GX_RICH_TEXT_FONTS.

### <a name="return-values"></a>Wartości zwrócone

- Zestaw czcionek (0x00) o pomyślnym zaawansowaniu widoku tekstu sformatowanego **GX_SUCCESS**
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RICH_TEXT_FONTS fonts;

/* Replace the font ids as needed. */
fonts.gx_rich_text_fonts_normal_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_italic_id = GX_FONT_ID_SYSTEM;
fonts.gx_rich_text_fonts_bold_italic_id = GX_FONT_ID_SYSTEM;

/* Set the font of “my_rich_view”. */
status = gx_rich_text_view_fonts_set(&my_rich_view, &fonts);

/* If status is GX_SUCCESS the font for rich text view “my_rich_view” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_rich_text_view_create
- gx_rich_text_view_draw
- gx_rich_text_view_text_draw

## <a name="gx_rich_text_view_text_draw"></a>gx_rich_text_view_text_draw


Rysuj tekst w postaci tekstu sformatowanego

### <a name="prototype"></a>Prototype

```C
VOID gx_rich_text_view_text_draw(GX_RICH_TEXT_VIEW *text_view);
```

### <a name="description"></a>Opis

Ta funkcja obsługi służy do rysowania części tekstowej w widoku tekstu sformatowanego. Ta funkcja jest wywoływana wewnętrznie przez gx_rich_text_view_draw () i jest udostępniana jako osobny interfejs API jako wygoda dla aplikacji, które definiują niestandardową funkcję rysowania widoku tekstu sformatowanego. Aplikacje, które chcą dostosować rysunek w tle widoku tekstu sformatowanego, mogą zapewnić swoją niestandardową funkcję rysowania i wywoływać usługę gx_rich_text_view_text_draw jako część niestandardowego rysunku, aby narysować tekst tekstu sformatowanego w tle.

### <a name="parameters"></a>Parametry

- **text_view** Wskaźnik do bloku kontrolki widżetu widok tekstu sformatowanego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom rich text view drawing function. */

VOID my_rich_text_view_draw(GX_RICH_TEXT_VIEW *text_view)
{
    /* Insert code here to draw rich text view background. */

    /* Call support function to do text drawing. */
    gx_rich_text_view_text_draw();

    /* Draw child widgets. */
    gx_widget_children_draw((GX_WIDGET *) rich_text_view);
}
```

### <a name="see-also"></a>Zobacz też

- gx_rich_text_view_create
- gx_rich_text_view_draw
- gx_rich_text_view_fonts_set

## <a name="gx_screen_stack_create"></a>gx_screen_stack_create


Inicjowanie stosu ekranu

### <a name="prototype"></a>Prototype

```C
UINT gx_screen_stack_create(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET **memory_buffer, 
    INT buffer_size);
```

### <a name="description"></a>Opis

Ta usługa inicjuje stos ekranu. Aplikacja musi zdefiniować blok pamięci i rozmiar buforu używany do implementowania funkcji stosu ekranu.

> [!NOTE]
> *Ten interfejs API jest przestarzały i został zastąpiony gx_system_screen_stack_create (). Ta wersja jest świadczona tylko w celu zapewnienia zgodności z poprzednimi wersjami z powyższymi wersjami biblioteki.*

### <a name="parameters"></a>Parametry

- **kontrolka** Blok sterowania stosu ekranu
- **memory_buffer** Wskaźnik do bufora pamięci, który został użyty jako stos ekranu
- **buffer_size** Rozmiar pamięci w bajtach

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne utworzenie stosu ekranu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE** (0X22) Nieprawidłowy rozmiar buforu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
#define SCREEN_STACK_SIZE 10

GX_SCREEN_STACK_CONTROL my_stack_control;
GX_WIDGET *screen_stack[SCREEN_STACK_SIZE];

/* Initialize “my_stack_control”. */
status = gx_screen_stack_create(&my_stack_control, screen_stack,
                        SCREEN_STACK_SIZE * sizeof(GX_WIDGET *));

/* If status is GX_SUCCESS the screen control block “my_stack control” has been initialized. */
```

### <a name="see-also"></a>Zobacz też

- gx_screen_stack_push
- gx_screen_stack_pop
- gx_screen_stack_reset

## <a name="gx_screen_stack_pop"></a>gx_screen_stack_pop


Usuń wpis znajdujący się najwyżej z stosu ekranu

### <a name="prototype"></a>Prototype

```C
UINT gx_screen_stack_pop(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>Opis

Ta usługa usuwa wpis z góry z stosu ekranu i dołącza ekran zdjęte do jego poprzedniego elementu nadrzędnego. Ten interfejs API odłącza również wszelkie istniejące elementy podrzędne z elementu nadrzędnego.

> [!NOTE]
> *Ten interfejs API jest przestarzały i został zastąpiony gx_system_screen_stack_pop (). Ta wersja jest świadczona tylko w celu zapewnienia zgodności z poprzednimi wersjami z powyższymi wersjami biblioteki.*

### <a name="parameters"></a>Parametry

- **kontrolka** Blok sterowania stosu ekranu

### <a name="return-values"></a>Wartości zwrócone

- Pomyślny stos ekranu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Remove the topmost entry from the screen stack. */
status = gx_screen_stack_pop(&my_stack_control);

/* If status is GX_SUCCESS the topmost entry has been removed from the screen stack, 
    and the popped screen has been attached to its parent. */
```

### <a name="see-also"></a>Zobacz też

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_reset

## <a name="gx_screen_stack_push"></a>gx_screen_stack_push


Wypychanie ekranu i jego elementów nadrzędnych do stosu

### <a name="prototype"></a>Prototype

```C
UINT gx_screen_stack_push(
    GX_SCREEN_STACK_CONTROL *control,
    GX_WIDGET *screen,
    GX_WIDGET *new_screen);
```

### <a name="description"></a>Opis

Ta usługa odłącza od jej elementu nadrzędnego, a następnie wypycha wskaźnik ekranu i wskaźnik nadrzędny na stosie ekranu. Nowy wskaźnik ekranu jest następnie dołączany do elementu nadrzędnego.


> [!NOTE]
> *Ten interfejs API jest przestarzały i został zastąpiony gx_system_screen_stack_pop (). Ta wersja jest świadczona tylko w celu zapewnienia zgodności z poprzednimi wersjami z powyższymi wersjami biblioteki.*

### <a name="parameters"></a>Parametry

- **kontrolka** Blok sterowania stosu ekranu
- **ekran** Wskaźnik ekranu do wypchnięcia
- **new_screen** Wskaźnik nowego ekranu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne wypychanie stosu ekranu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Push “screen” and its parent to screen stack, Dettach “screen” from its parent, and attach “new screen” to the parent. */
status = gx_screen_stack_push(&my_stack_control,
                                screen, new_screen);

/* If status is GX_SUCCESS the widget “screen” and its parent have been pushed to screen stack, “screen” has been detached from its parent, “new_screen” has been attached to the parent. */
```

### <a name="see-also"></a>Zobacz też

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_reset

## <a name="gx_screen_stack_reset"></a>gx_screen_stack_reset


Usuwa wszystkie wpisy z stosu ekranu

### <a name="prototype"></a>Prototype

```C
UINT gx_screen_stack_reset(GX_SCREEN_STACK_CONTROL *control);
```

### <a name="description"></a>Opis

Ta usługa usuwa wszystkie wpisy ze stosu ekranu.

> [!NOTE]
> *Ten interfejs API jest przestarzały i został zastąpiony gx_system_screen_stack_pop (). Ta wersja jest świadczona tylko w celu zapewnienia zgodności z poprzednimi wersjami z powyższymi wersjami biblioteki.*

### <a name="parameters"></a>Parametry

- **kontrolka** Blok sterowania stosu ekranu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne przewijanie — tworzenie
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Remove all enteries from the screen stack. */
status = gx_screen_stack_reset(&my_stack_control);

/* If status is GX_SUCCESS all entries of screen stack has been removed. */
```

### <a name="see-also"></a>Zobacz też

- gx_screen_stack_create
- gx_screen_stack_push
- gx_screen_stack_pop

## <a name="gx_scroll_thumb_create"></a>gx_scroll_thumb_create


Utwórz kciuk przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_thumb_create(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_SCROLLBAR *parent, ULONG style);
```

### <a name="description"></a>Opis

Ta usługa tworzy pokrętło przewijania. Ta usługa jest zwykle wywoływana wewnętrznie podczas tworzenia GX_SCROLLBAR, ale jest udostępniana publicznie w celu zezwalania na niestandardowe implementacje SCROLLBAR.

### <a name="parameters"></a>Parametry

- **scroll_thumb** Scroll — blok kontrolny widżetu
- **element nadrzędny** Wskaźnik na nadrzędny pasek przewijania
- **styl** Styl widżetu ScrollBar. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne przewijanie — tworzenie
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_SCROLL_THUMB my_scroll_thumb;

/* Create scroll thumb “my_scroll_thumb”. */
status = gx_scroll_thumb_create(&my_scroll_thumb, &my_scrollbar,
                                GX_STYLE_NONE);

/* If status is GX_SUCCESS the scroll thumb “my_scroll_thumb” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_scroll_thumb_draw
- gx_scroll_thumb_event_process

## <a name="gx_scroll_thumb_draw"></a>gx_scroll_thumb_draw


Rysuj kciuk przewijania

### <a name="prototype"></a>Prototype

```C
VOID gx_scroll_thumb_draw(GX_SCROLL_THUMB *scroll_thumb);
```

### <a name="description"></a>Opis

Ta usługa rysuje pokrętło przewijania. Ta usługa jest wywoływana wewnętrznie przez odświeżanie kanwy GUIX, ale może być również wywoływana przez zastąpione funkcje rysowania.

### <a name="parameters"></a>Parametry

- **scroll_thumb** Scroll — blok kontrolny widżetu

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom scroll thumb drawing function. */

VOID my_scroll_thumb_draw(GX_SCROLL_THUMB *thumb)
{
    /* Call default scroll thumb draw. */
    gx_scroll_thumb_draw(thumb);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_scroll_thumb_create
- gx_scroll_thumb_event_process

## <a name="gx_scroll_thumb_event_process"></a>gx_scroll_thumb_event_process


Zdarzenie przewijania przewijania procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_thumb_event_process(
    GX_SCROLL_THUMB *scroll_thumb,
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa obsługuje zdarzenia wysyłane do pokrętła ScrollBar. Ta usługa jest zwykle używana wewnętrznie przez GUIX, ale jest udostępniana publicznie, aby pomóc w zaimplementowaniu niestandardowych zachowań pasków przewijania.

### <a name="parameters"></a>Parametry

- **scroll_thumb** Scroll — blok kontrolny widżetu
- **zdarzenie** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia przewijania pomyślnego przewijania **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom event processing function. */

UINT my_event_process (GX_SCROLL_THUMB *thumb, GX_EVENT *event_ptr)
{
    switch(event_ptr->gx_event_type)
    {
    case GX_EVENT_SHOW:
        /* Do default handling. */
        status = gx_scroll_thumb_event_process(thumb, event_ptr);

        /* add my own handling here */
        break;
    default:
        status = gx_scroll_thumb_event_process(thumb, event_ptr);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_scroll_thumb_create
- gx_scroll_thumb_draw

## <a name="gx_scroll_wheel_create"></a>gx_scroll_wheel_create


Tworzenie podstawowego widgetu kółka przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_create( 
    GX_SCROLL_WHEEL *wheel, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    INT total_rows, 
    ULONG style,
    USHORT id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy generyczny widżet kółka przewijania.

Ogólne koło przewijania jest podstawowym elementem widget dla wszystkich typów widżetów przewijania kółka, w tym *gx_text_scroll_wheel** *, który jest podstawą dla *gx_numeric_scroll_wheel** * i gx_string_ elementów widget *scroll_wheel** *. Element widget podstawowego kółka przewijania zapewnia obsługę zdarzeń, animację przewijania i zaznaczone obliczenia wierszy dla wszystkich typów widżetu kółka przewijania.

Aplikacje nie zwykle tworzą wystąpienia widżetu ogólnego kółka przewijania, ponieważ ten typ widżetu nie udostępnia funkcji rysowania. Jednak dostęp do tego interfejsu API jest dostarczany, aby pomóc aplikacjom, które muszą utworzyć niestandardowy typ widżetu kółka przewijania.

GX_SCROLL_WHEEL bazują na GX_WINDOW i w związku z tym wszystkie GX_WINDOW interfejsy API mogą być używane z GX_SCROLL_WHEEL i widżetami uzyskanymi z GX_SCROLL_WHEEL.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do ogólnego bloku kontrolki pokrętła przewijania
- **Nazwa** Nazwa widżetu przypisanego do aplikacji
- **element nadrzędny** Element widget elementu nadrzędnego lub GX_NULL
- **total_rows** Łączna liczba dostępnych wierszy
- **styl** Flagi stylu widżetu
- **Identyfikator** widżetu przypisanego do aplikacji
- **rozmiar** Prostokąt definiujący początkowy rozmiar widżetu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzyła kółko przewijania
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontroli
- Utworzono element widget **GX_ALREADY_CREATED** (0x13)
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Call generic create function during custom widget createl. */

UINT custom_scroll_wheel_create(CUSTOM_SCROLL_WHEEL *wheel,
                    GX_CONST GX_CHAR *name,
                    GX_WIDGET *parent,
                    INT total_rows, ULONG style,
                    USHORT id,
                    GX_CONST GX_RECTANGLE *size)
{
    /* create base widget as part of custom create */
    status = gx_scroll_wheel_create(wheel, name, parent,
                            total_rows, style, id, size);

    /* If status is GX_SUCCESS the base scroll wheel has been created. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_event_process"></a>gx_scroll_wheel_event_process


Funkcja przetwarzania zdarzeń dla ogólnego widgetu kółka przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_event_process(
    GX_SCROLL_WHEEL *wheel,
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa udostępnia podstawową obsługę zdarzeń wejściowych dla wszystkich typów widżetów z kółkiem przewijania.

Ta funkcja jest udostępniona oprogramowaniu aplikacji, aby pomóc w aplikacjach, które wymagają utworzenia niestandardowego typu widgetu kółka przewijania. Aplikacje często zapewniają własną funkcję przetwarzania zdarzeń, ale wywołują ogólne przetwarzanie zdarzeń dla widżetów dla zdarzeń, które nie muszą być dostosowywane.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do ogólnego bloku kontrolki pokrętła przewijania
- **zdarzenie** GX_EVENT wskaźnik

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przewiń proces zdarzenia kółka
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Call generic scroll wheel event processing 
    as part of custom event processing function. */

UINT custom_scroll_wheel_event_process(CUSTOM_SCROLL_WHEEL *wheel,
                    GX_EVENT *event)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;

    default:
        /* pass all other events to the generic scroll wheel
            event processing */
        gx_scroll_wheel_event_process(wheel, event);
        break;
    }
}
```


### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_gradient_alpha_set"></a>gx_scroll_wheel_gradient_alpha_set


Przypisz gradient wartości alfa dla opcjonalnego gradientu nakładki

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_gradient_alpha_set(
    GX_SCROLL_WHEEL *wheel,
    GX_UBYTE start_alpha,
    GX_UBYTE end_alpha);
```

### <a name="description"></a>Opis

Ta usługa definiuje początkową i końcową wartość alfa dla opcjonalnej nakładki gradientu widżetu przewijania.

Wszystkie widżety z kółkiem przewijania obsługują efekt "zanikania" wierszy kółka przewijania jako wierszy w górnej i dolnej krawędzi widżetu przewijania. Ten efekt zaniku jest realizowany przez rysowanie Pixelmap gradientu nad wierszami kółka przewijania, co sprawia, że wiersze pojawiają się w taki sposób, że wiersze są rysowane blisko góry i u dołu widżetu przewijania.

Ta usługa interfejsu API pozwala aplikacji modyfikować intensywność efektu zanikania lub wyłączyć ten efekt całkowicie poprzez ustawienie wartości początkowych i końcowych alfa na 0.

Pixelmap gradientu jest tworzony w czasie wykonywania, gdy koło przewijania początkowo staną się widoczne. Wymaga to, aby usługa alokacji pamięci środowiska uruchomieniowego została zdefiniowana przy użyciu _gx_system_memory_allocator_set (). Jeśli funkcja alokatora pamięci nie została zdefiniowana, obraz gradientu nie zostanie utworzony i nie będzie dostępny żaden efekt zanikania.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do ogólnego bloku kontrolki pokrętła przewijania
- **start_alpha** Początkowa wartość alfa gradientu nakładki.
- **end_alpha** Wartość alfa końcowego gradientu nakładek.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił gradient dla kółka przewijania
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
status = gx_scroll_wheel_gradient_alpha_set(&wheel, 240, 0);
/* if status == GX_SUCCESS the wheel gradient alpha values were
Successfully assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_row_height_set"></a>gx_scroll_wheel_row_height_set


Przypisz wysokość wiersza dla każdego wiersza kółka

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_row_height_set(
    GX_SCROLL_WHEEL *wheel,
    GX_VALUE row_height);
```

### <a name="description"></a>Opis

Ta usługa przypisuje wysokość wiersza dla każdego wiersza kółka przewijania. Należy pamiętać, że jeśli kółko przewijania ma GX_STYLE_TEXT_SCROLL_WHEEL_ROUND stylu, Wysokość wiersza przechodzi przez transformację, która efektywnie zmniejsza wysokość wiersza jako wiersz blisko górnej lub dolnej krawędzi pokrętła.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do ogólnego bloku kontrolki pokrętła przewijania
- **row_height** Wartość wysokości wiersza w pikselach.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił wysokość kółka przewijania
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
status = gx_scroll_wheel_row_height_set(&wheel, 40);

/* if status == GX_SUCCESS the wheel row height has been set to 40
pixels. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_gradient_alpha_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_background_set"></a>gx_scroll_wheel_selected_background_set


Przypisz obraz tła dla zaznaczonego wiersza kółka

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_selected_background_set(
    GX_SCROLL_WHEEL*wheel, 
    GX_RESOURCE_ID image_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje opcjonalny identyfikator Pixelmap, który jest rysowany za zaznaczonym wierszem kółka przewijania. Można go użyć do wyróżnienia zaznaczonego wiersza, aby użytkownik mógł łatwo odróżnić wiersz kółka przewijania.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do ogólnego bloku kontrolki pokrętła przewijania
- **image_id** Identyfikator Pixelmap, który ma być używany jako obraz tła zaznaczonego wiersza.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił tło kółka przewijania
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
status = gx_scroll_wheel_selected_background_set(&wheel,
GX_PIXELMAP_ID_SELECTED_ROW);

/* if status == GX_SUCCESS the background image has been
assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_get"></a>gx_scroll_wheel_selected_get


Pobierz aktualnie wybrany wiersz koła

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_selected_get(
    GX_SCROLL_WHEEL *wheel,
    INT *row);
```

### <a name="description"></a>Opis

Ta usługa będzie wysyłać zapytania do pokrętła przewijania w celu pobrania aktualnie zaznaczonego wiersza. Obiekt wywołujący musi przekazać lokalizację, aby przywrócić wybrany indeks wiersza jako drugi parametr tej funkcji.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do ogólnego bloku kontrolki pokrętła przewijania
- **wiersz** Lokalizacja, w której zostanie zwrócona wartość wybranego wiersza.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrał wybrany wiersz kółka
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x19) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
INT row;
status = gx_scroll_wheel_selected_get(&wheel, &row);

/* if status == GX_SUCCESS the selected row has been returned in
the row variable. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_selected_set"></a>gx_scroll_wheel_selected_set


Przypisz wybrany wiersz kółka przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_selected_set(
    GX_SCROLL_WHEEL *wheel,
    INT row);
```

### <a name="description"></a>Opis

Ta usługa przypisuje aktualnie zaznaczony wiersz kółka przewijania.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do ogólnego bloku kontrolki pokrętła przewijania
- **wiersz** Wiersz pokrętła przewijania, który ma zostać wybrany.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił wybrany wiersz kółka
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
status = gx_scroll_wheel_selected_set(&wheel, 20);

/* if status == GX_SUCCESS the scroll wheel has been set to select
row 20 */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_speed_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_speed_set"></a>gx_scroll_wheel_speed_set


Przypisz szybkość przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_speed_set(
    GX_SCROLL_WHEEL *wheel,
    GX_FIXED_VAL start_speed_rate,
    GX_FIXED_VAL end_speed_rate,
    GX_VALUE max_steps,
    GX_VALUE delay);
```

### <a name="description"></a>Opis

Ta usługa przypisuje szybkość przewijania dla widgetu kółka przewijania.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do ogólnego bloku kontrolki pokrętła przewijania
- **start_speed_rate** Szybkość uruchamiania przewijania, aby szybko przełączać szybkość.
- **end_speed_rate** Szybkość kończenia przewijania do szybkości szybkiego przesuwania
- **max_steps** Maksymalna liczba kroków do przewijania.
- **opóźnienie** Czas opóźnienia każdego kroku.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił szybkość kółka
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa wartość

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
status = gx_scroll_wheel_speed_set(&wheel, GX_FIXED_VAL_MAKE(2),
                                GX_FIXED_VAL_MAKE(1) / 2, 10, 2);

/* if status == GX_SUCCESS the scroll wheel speed has been
successfully set. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scroll_wheel_total_rows_set"></a>gx_scroll_wheel_total_rows_set


Przypisz wszystkie dostępne wiersze kółka przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_scroll_wheel_total_rows_set(
    GX_SCROLL_WHEEL *wheel,
    INT total_rows);
```

### <a name="description"></a>Opis

Ta usługa przypisuje liczbę wierszy dostępnych we wskazanym kółku przewijania. Widżet z kółkiem przewijania zazwyczaj otrzymuje zawartość wiersza z aplikacji w postaci tablicy ciągów lub danych ciągu dostarczonych przez użytkownika. Ten interfejs API informuje kółko przewijania o łącznej liczbie wierszy, które powinny być prezentowane użytkownikowi.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do ogólnego bloku kontrolki pokrętła przewijania
- **total_rows** Całkowita liczba wierszy kółka, które mają być widoczne dla użytkownika.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił wiersz sumy kółka przewijania
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa wartość

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
status = gx_scroll_wheel_total_rows_set(&wheel, 100);

/* if status == GX_SUCCESS the scroll wheel has been changed to
display 100 total rows */
```
### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_speed_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_text_get

## <a name="gx_scrollbar_draw"></a>gx_scrollbar_draw


Rysuj pasek przewijania

### <a name="prototype"></a>Prototype

```C
VOID gx_scrollbar_draw(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>Opis

Ta usługa rysuje pasek przewijania. Wspólna funkcja rysowania jest używana zarówno jako pionowe, jak i poziome widżety ScrollBar. Ta usługa jest wywoływana wewnętrznie przez odświeżanie kanwy GUIX, ale może być również wywoływana przez zastąpione funkcje rysowania.

### <a name="parameters"></a>Parametry

- **pasek przewijania** Widżet ScrollBar do rysowania

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom scrollbar drawing function. */

VOID my_scrollbar_draw(GX_SCROLLBAR *scrollbar)
{
    /* Call default scrollbar draw. */
    gx_scrollbar_draw(thumb);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_ horizontal_scrollbar_create
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_event_process"></a>gx_scrollbar_event_process


Zdarzenie ScrollBar procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_scrollbar_event_process(
    GX_SCROLLBAR *scrollbar,
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie ScrollBar. Wspólna funkcja obsługi zdarzeń używana zarówno dla pionowych, jak i poziomych elementów widget ScrollBar.

### <a name="parameters"></a>Parametry

- **pasek przewijania** Blok kontrolny widżetu ScrollBar
- **zdarzenie** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Pomyślny proces zdarzenia ScrollBar **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
Call generic scrollbar event processing as part of custom event processing function. */

UINT custom_scrollbar_event_process(GX_SCROLLBAR *scrollbar,
                                    GX_EVENT *event)
{
    switch(event->gx_event_type)
    {
    case xyz:
        /* insert custom event handling here */
        break;
    default:
        /* pass all other events to the generic scrollbar
            event processing */
        gx_scrollbar_event_process(scrollbar, event);
        break;
    }
}
```

### <a name="see-also"></a>Zobacz też

- gx_ horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_limit_check"></a>gx_scrollbar_limit_check


Sprawdź limit ScrollBar

### <a name="prototype"></a>Prototype

```C
UINT gx_scrollbar_limit_check(GX_SCROLLBAR *scrollbar);
```

### <a name="description"></a>Opis

Ta usługa sprawdza limit ScrollBar i zapobiega występowaniu pokrętła ScrollBar poza wstępnie zdefiniowanymi limitami.

### <a name="parameters"></a>Parametry

- **pasek przewijania** Blok kontrolny widżetu ScrollBar

### <a name="return-values"></a>Wartości zwrócone

- Sprawdzanie limitu liczby pokazywanych pomyślnych **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Check scrollbar limit of “my_scrollbar”. */
status = gx_scrollbar_limit_check(&my_scrollbar);

/* If status is GX_SUCCESS the limit of scrollbar “my_scrollbar” has been checked. */
```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_reset"></a>gx_scrollbar_reset


Resetuj pasek przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_scrollbar_reset(
    GX_SCROLLBAR *scrollbar,
    GX_SCROLL_INFO *info);
```

### <a name="description"></a>Opis

Ta usługa resetuje pasek przewijania.

### <a name="parameters"></a>Parametry

- **pasek przewijania** Blok kontrolny widżetu ScrollBar
- **informacje** Wskaźnik do GX_SCROLL_INFO struktury, który definiuje limity ScrollBar, bieżącą wartość i krok lub przyrost. **Dodatek I** zawiera definicję do GX_SCROLL_INFO struktury.

### <a name="return-values"></a>Wartości zwrócone

- Resetowanie paska przewijania **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_INVALID_VALUE** (0x22) — informacje o przewijaniu są nieprawidłowe

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Reset scrollbar “my_scrollbar”. */

GX_SCROLL_INFO my_info;

my_info.gx_scroll_value = 0;
my_info.gx_scroll_minimum = 0;
my_info.gx_scroll_maximum = 100;
my_info.gx_scroll_visible = 10;
my_info.gx_scroll_increment = 1;

status = gx_scrollbar_reset(&my_scrollbar, &my_info);

/* If status is GX_SUCCESS the scrollbar “my_scrollbar” has been reset. */
```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_vertical_scrollbar_create

## <a name="gx_scrollbar_value_set"></a>gx_scrollbar_value_set


Przypisz wartość paska przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_scrollbar_value_set(
    GX_SCROLLBAR *scrollbar,
    INT value);
```

### <a name="description"></a>Opis

Ta usługa przypisuje bieżącą wartość paska przewijania. W oknie nadrzędnym zostanie wygenerowane zdarzenie GX_EVENT_VERTICAL_SCROLL lub GX_EVENT_HORIZONTAL_SCROLL.

### <a name="parameters"></a>Parametry

- **pasek przewijania** Blok kontrolny widżetu ScrollBar
- **wartość** Nowa wartość paska przewijania

### <a name="return-values"></a>Wartości zwrócone

- Pomyślny proces zdarzenia ScrollBar **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- Wartość przewijania **GX_INVALID_VALUE** (0x22) jest nieprawidłowa

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Assign new value for scrollbar “my_scrollbar”. */

status = gx_scrollbar_value_set(&my_scrollbar, 0);

/* If status is GX_SUCCESS the current position of scrollbar “my_scrollbar” has been set. */

```

### <a name="see-also"></a>Zobacz też

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_limit_check
- gx_scrollbar_reset
- gx_vertical_scrollbar_create

## <a name="gx_single_line_text_input_backspace"></a>gx_single_line_text_input_backspace


Przetwórz znak backspace w widżecie tekst wejściowy

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_backspace(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa usuwa znak przed pozycją kursora tekstu wejściowego. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia klawisza Backspace w dół, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne Tworzenie tekstu jednowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x23) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Delete a character before the cursor of “my_text_input”. */
status = gx_single_line_text_input_backspace(&my_text_input);

/* If status is GX_SUCCESS the character before the cursor has been deleted. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_buffer_clear"></a>gx_single_line_text_input_buffer_clear


Usuwa wszystkie znaki z buforu wejściowego tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_buffer_clear(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa usuwa wszystkie znaki z bufora wejściowego tekstu.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie wyczyszczono bufor wejścia jednowierszowego tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* clear input buffer of “my_text_input”. */
status = gx_single_line_text_input_clear(&my_text_input);

/* If status is GX_SUCCESS the text input widget has emptied its input buffer. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_buffer_backspace
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_buffer_get"></a>gx_single_line_text_input_buffer_get


Pobiera informacje o buforze widżetu wprowadzania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_buffer_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CHAR **buffer_address, 
    UINT *content_size, 
    UINT *buffer_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o buforze widżetu wprowadzania tekstu.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy
- **buffer_address** Adres buforu wejściowego
- **content_size** Liczba bajtów danych wejściowych
- **buffer_size** Rozmiar buforu wejściowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrały informacje buforu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR *buffer_address;
UINT buffer_size;
UINT content_size;

/* Retrieve buffer information of “my_text_input” widget. */
status = gx_single_line_text_input_buffer_get(&my_text_input,
                    &buffer_address, &string_size, &buffer_size);

/* If status is GX_SUCCESS the value of buffer_address, string_size and buffer_size has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_character_delete"></a>gx_single_line_text_input_character_delete


Usuń znak w bieżącym położeniu kursora

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_character_delete(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa usuwa znak po pozycji kursora tekstu wejściowego. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia usuwania klucza, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie usuwa znak po kursorze
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Delete the character after the cursor of “my_text_input”. */
status = gx_single_line_text_input_character_delete(&my_text_input);

/* If status is GX_SUCCESS the character after the cursor has been deleted. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_multi_line_text_input_create
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_character_insert"></a>gx_single_line_text_input_character_insert


Wstaw ciąg znaków w bieżącym położeniu kursora

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_character_insert(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_UBYTE *insert_str,
    UINT insert_size);
```

### <a name="description"></a>Opis

Ta usługa wstawia ciąg znaków do buforu ciągu wejściowego tekstu w bieżącym położeniu kursora.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy
- **insert_str** Ciąg znaków, który ma zostać wstawiony
- **insert_size** Liczba bajtów do wstawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie wstawiono znak
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Insert characters at current cursor position. */

GX_CHAR insert_text[10] = “insert”;
status = gx_single_line_text_input_character_insert(&my_text_input,
                                            insert_text,
                                            GX_STRLEN(insert_text));

/* If status is GX_SUCCESS the text input widget has successfully insert the string. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_create"></a>gx_single_line_text_input_create


Tworzenie widżetu wprowadzania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_create(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    GX_CHAR *input_buffer, UINT buffer_size,
    UINT style, USHORT text_input_id, GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet wprowadzania tekstu. Obiekt wywołujący musi dostarczyć magazyn dla ciągu wejściowego i wskazać maksymalną długość ciągu.

GX_SINGLE_LINE_TEXT_INPUT pochodzi od GX_PROMPT i w związku z tym wszystkie usługi gx_prompt mogą być używane z GX_SINGLE_LINE_TEXT_INPUT widżetów.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy
- **Nazwa** Opcjonalna nazwa logiczna widżetu
- **element nadrzędny** Opcjonalny widżet nadrzędny
- **input_buffer** Magazyn dla ciągu wejściowego
- **buffer_size** Rozmiar obszaru przechowywania ciągów wejściowych w bajtach.
- **styl** Flagi stylu wprowadzania tekstu
- **text_input_id** Opcjonalny identyfikator widżetu danych wejściowych
- **rozmiar** Prostokąt definiujący początkowy rozmiar widżetu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne Tworzenie tekstu jednowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_SINGLE_LINE_TEXT_INPUT my_text_input;
static GX_CHAR           text_input_buffer[100];
GX_RECTANGLE             size;

/* Define widget size. */
gx_utility_rectangle_define(&size, 10, 10, 110, 40);

/* Create single-line text input widget “my_text_input”. */
status = gx_single_line_text_input_create(&my_text_input,
                        “text_input”, GX_NULL, text_input_buffer, 100,
                        GX_STYLE_ENABLED, 0, &size);

/* If status is GX_SUCCESS, the text input widget has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_draw"></a>gx_single_line_text_input_draw


Rysowanie widżetu wprowadzania tekstu

### <a name="prototype"></a>Prototype

```C
VOID gx_single_line_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa rysuje widżet wprowadzania tekstu. Ta usługa jest zwykle wywoływana wewnętrznie podczas odświeżania kanwy, ale może być również wywoływana z funkcji niestandardowego rysowania tekstu wejściowego.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom single line text input draw function. */

VOID my_sl_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *input)
{
    /* Call default single line text input draw. */
    gx_single_line_text_input_draw(input);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_draw_position_get"></a>gx_single_line_text_input_draw_position_get


Pobierz pozycję początkową rysowania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_draw_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_VALUE *xpos, GX_VALUE *ypos);
```

### <a name="description"></a>Opis

Ta usługa Pobiera pozycję początku tekstu wejściowego tekstu.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy
- **xpos** Pobrano pozycję rysowania remisu we współrzędnym x
- **YPos** Pobrano pozycję rysowania remisu we współrzędnym y

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie Przenieś kursor wprowadzania tekstu do końca
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom single line text input draw function. */

VOID my_sl_text_input_draw(GX_SINGLE_LINE_TEXT_INPUT *input)
{
GX_VALUE xpos;
GX_VALUE ypos;

    /* Draw background. */
    gx_widget_border_draw(input, border_color, upper_fill_color,
                          lower_fill_color, GX_TRUE);

    /* Retrieve text draw start position. */
    gx_single_line_text_input_draw_position_get(input, xpos,
                                                ypos);

    /* Add your text drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_end"></a>gx_single_line_text_input_end


Przenieś kursor wprowadzania tekstu do końca ciągu

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_end(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa umieszcza kursor widżetu wprowadzanie tekstu na końcu ciągu wejściowego. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia dotyczącego klucza zakończenia, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie Przenieś kursor wprowadzania tekstu do końca
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move input cursor to end. */
status = gx_single_line_text_input_end(&my_text_input);

/* If status is GX_SUCCESS, text text input cursor has been moved to end. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_event_process"></a>gx_single_line_text_input_event_process


Funkcja przetwarzania zdarzeń widżetu wprowadzanie tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_event_process(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie wejściowe tekstu jednowierszowego. Ta funkcja jest wewnętrznie przywoływana przez funkcję gx_single_line_text_input_create, ale jest narażona na użycie przez aplikację w takich przypadkach, w których aplikacja definiuje niestandardową funkcję przetwarzania zdarzeń tekstu jednowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy
- **event_ptr** Wskaźnik do GX_EVENT struktury

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przetworzył zdarzenie wprowadzania tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Call generic single line text input event processing as part of custom event processing function. */

UINT custom_sl_text_input_event_process(
                                GX_SINGLE_LINE_TEXT_INPUT *input,
                                GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default single line
            text input event processing */
        status =
        gx_single_line_text_input_event_process(input, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_fill_color_set"></a>gx_single_line_text_input_fill_color_set


Ustaw kolor tła tekstu jednowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_fill_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_fill_color_id,
    GX_RESOURCE_ID selected_fill_color_id,
    GX_RESOURCE_ID disabled_fill_color_id,
    GX_RESOURCE_ID readonly_fill_color_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia kolor wypełnienia tekstu jednowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Wskaźnik do bloku kontroli wejścia tekstu jednowierszowego
- **normal_fill_color_id** Identyfikator zasobu koloru wypełnienia widżetu w normalnym stanie. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **selected_fill_color_id** Identyfikator zasobu koloru wypełnienia widżetu, gdy element widget uzyskuje fokus. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **disabled_fill_color_id** Identyfikator zasobu koloru wypełnienia widżetu, gdy styl GX_STYLE_ENABLED nie jest ustawiony. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **readonly_fill_color_id** Identyfikator zasobu koloru wypełnienia widżetu po ustawieniu obu stylów GX_STYLE_ENABLED i GX_STYLE_TEXT_INPUT_READYONLY. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawiono kolor wypełnienia tekstu jednowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set fill colors for single line text input “my_text_input”. */
status = gx_single_line_text_input_fill_color_set(&my_text_input,
                    GX_COLOR_ID_NORMAL_FILL,
                    GX_COLOR_ID_SELECTED_FILL,
                    GX_COLOR_ID_DISABLED_FILL,
                    GX_COLOR_ID_READONLY_FILL);

/* If status is GX_SUCCESS, the fill color of “my_text_input” was
set. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_home"></a>gx_single_line_text_input_home


Przenieś kursor wprowadzania tekstu do pozycji głównej

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_home(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa przenosi położenie kursora wprowadzania tekstu do początku ciągu wejściowego. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia dotyczącego klucza głównego, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeniesiono kursor do pozycji głównej
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move cursor to the start of the input text. */
status = gx_single_line_text_input_home(&my_text_input);

/* If status is GX_SUCCESS the cursor has been moved to the home position */
```

### <a name="see-also"></a>Zobacz też
- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_left_arrow"></a>gx_single_line_text_input_left_arrow


Przenieś kursor wejściowy o jeden znak w lewo

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_left_arrow(GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa przenosi kursor wprowadzania tekstu o jeden znak w lewo. Ta usługa jest wywoływana wewnętrznie w przypadku odebrania lewego klucza zdarzenia, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeniesiono kursor w lewo
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move the cursor one character to the left. */
status = gx_single_line_text_input_left_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the left. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_position_get"></a>gx_single_line_text_input_position_get

Przenieś kursor do położenia pikseli

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_position_get(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    INT pixel_position);
```

### <a name="description"></a>Opis

Ta usługa umieszcza kursor wprowadzania tekstu na podstawie żądanego położenia pikseli. Indeks kursora wprowadzania tekstu będzie obliczany na podstawie wartości x położenia pikseli. Ta usługa jest wywoływana wewnętrznie po odebraniu zdarzenia pióra, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy
- **pixel_position** Wartość X położenia pikseli

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił kursor na żądaną pozycję
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set cursor to requested position. */
status = gx_single_line_text_input_position_get(&my_text_input,
                                                100);

/* If status is GX_SUCCESS the text input widget cursor has been positioned */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_right_arrow"></a>gx_single_line_text_input_right_arrow


Przenieś kursor wejściowy o jeden znak w prawo

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_right_arrow(
    GX_SINGLE_LINE_TEXT_INPUT *text_input);
```

### <a name="description"></a>Opis

Ta usługa przenosi kursor wprowadzania tekstu o jeden znak w prawo. Ta usługa jest wywoływana wewnętrznie, gdy zostanie odebrane odpowiednie zdarzenie w dół, ale może być również wywoływana przez aplikację.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeniesiono kursor w prawo
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move cursor one character to the right. */
status = gx_single_line_text_input_right_arrow(&my_text_input);

/* If status is GX_SUCCESS the text input cursor has been moved one character to the right. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_add"></a>gx_single_line_text_input_style_add


Dodaj style

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_style_add(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Opis

Ta usługa dodaje określone style do widżetu wprowadzanie tekstu jednowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy
- **styl** Nowy styl do dodania. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie dodał styl do widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Add a new style to “my_text_input”. */
status = gx_single_line_text_input_style_add(&my_text_input,
GX_STYLE_CURSOR_AWAYS);

/* If status is GX_SUCCESS the GX_STYLE_CUSROSR_SHOR have been successfully added. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gax_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_remove"></a>gx_single_line_text_input_style_remove

Usuń style

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_style_remove(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Opis

Ta usługa usuwa określone style z jednowierszowego widżetu wprowadzania tekstu.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy
- **styl** Style do usunięcia. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie usunął style z widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Remove cursor blink style from “my_text_input”. */
status = gx_single_line_text_input_style_remove(&my_text_input,
GX_STYLE_CURSOR_BLINK);

/* If status is GX_SUCCESS the GX_STYLE_CURSOR_BLINK style has been successfully removed. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_style_set"></a>gx_single_line_text_input_style_set


Ustawianie stylów wprowadzania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_style_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input, 
    ULONG style);
```

### <a name="description"></a>Opis

Ta usługa ustawia określone style do widżetu wprowadzanie tekstu jednowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Blok kontrolny widżetu tekst jednowierszowy
- flagi stylu **stylu** do przypisania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił styl wprowadzania tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set style for “my_text_input”. */
status = gx_single_line_text_input_style_set(&my_text_input,
                    GX_STYLE_ENABLED | GX_STYLE_CURSOR_BLINK);

/* If status is GX_SUCCESS the text input style has been successfully set to the specified styles. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_signle_line_text_input_event_process
- gx_single_line_text_input_home
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_text_color_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_color_set"></a>gx_single_line_text_input_text_color_set


Ustaw kolor tekstu tekstu jednowierszowego

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id,
    GX_RESOURCE_ID readonly_text_color_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia kolor tekstu jednowierszowego tekstu wejściowego.

### <a name="parameters"></a>Parametry

- **text_input** Wskaźnik do bloku kontroli wejścia tekstu jednowierszowego
- **normal_text_color_id** Identyfikator zasobu koloru tekstu w normalnym stanie. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **selected_text_color_id** Identyfikator zasobu koloru tekstu, gdy element widget uzyskuje fokus. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **disabled_text_color_id** Identyfikator zasobu koloru tekstu, gdy GX_STYLE_ENABLED stylu nie jest ustawiony. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **readonly_text_color_id** Identyfikator zasobu tekstu, gdy ustawiono oba style GX_STYLE_ENABLED i GX_STYLE_TEXT_INPUT_READONLY. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawiono kolor tekstu jednowierszowego wejścia tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set text colors for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_color_set(&my_text_input,
                                        GX_COLOR_ID_NORMAL_TEXT,
                                        GX_COLOR_ID_SELECTED_TEXT,
                                        GX_COLOR_ID_DISABLED_TEXT,
                                        GX_COLOR_ID_READONLY_TEXT);

/* If status is GX_SUCCESS, the text color “my_text_input” was set. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_select
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_select"></a>gx_single_line_text_input_text_select

Zaznacz tekst

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_text_color_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    UINT start_index, UINT end_index);
```

### <a name="description"></a>Opis

Ta usługa zaznacza tekst z określonym znacznikiem początkowym i indeksem znacznika końcowego oraz podświetla zaznaczony tekst z wybranymi kolorami wypełnienia i tekstu.

### <a name="parameters"></a>Parametry

- **text_input** Wskaźnik do bloku kontroli wejścia tekstu jednowierszowego
- **start_index** Indeks pierwszego zaznaczonego znaku
- **end_index** Indeks ostatniego zaznaczonego znaku

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne Zaznaczanie tekstu tekstu jednowierszowego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- Wartość indeksu **GX_INVALID_VALUE** (0x22) jest nieprawidłowa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Select text between index [0, 9]. */
status = gx_single_line_text_input_text_select(&my_text_input,
                                                0,9);

/* If status is GX_SUCCESS, the text between index [0, 9] “my_text_input” was selected. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_set

## <a name="gx_single_line_text_input_text_set"></a>gx_single_line_text_input_text_set


Ustaw tekst tekstu wejściowego z pojedynczym wierszem (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_CHAR *text);
```

### <a name="description"></a>Opis

Ta usługa została uznana za przestarzałą na rzecz gx_single_line_text_input_text_set_ext ()

Ta usługa ustawia tekst tekstu jednowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Wskaźnik do bloku kontroli wejścia tekstu jednowierszowego
- **tekst** Ciąg tekstowy zakończony zerem

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawiono kolor tekstu jednowierszowego wejścia tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CONST GX_CHAR new_text = “Set Single Line Text Input Text”;

/* Set text for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_set(&my_text_input,
                                        new_text);

/* If status is GX_SUCCESS, the text of “my_text_input” was set. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_text_set_ext

## <a name="gx_single_line_text_input_text_set_ext"></a>gx_single_line_text_input_text_set_ext


Ustaw tekst tekstu wejściowego z pojedynczym wierszem

### <a name="prototype"></a>Prototype

```C
UINT gx_single_line_text_input_text_set(
    GX_SINGLE_LINE_TEXT_INPUT *text_input,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Opis

Ta usługa ustawia tekst tekstu jednowierszowego.

### <a name="parameters"></a>Parametry

- **text_input** Wskaźnik do bloku kontroli wejścia tekstu jednowierszowego
- **ciąg** Zmienna GX_STRING

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawiono kolor tekstu jednowierszowego wejścia tekstu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING new_string;
new_string.gx_string_ptr = “Set Single Line Text Input Text”;
new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Set text for single line text input “my_text_input”. */
status = gx_single_line_text_input_text_set_ext(&my_text_input,
                                        &new_string);

/* If status is GX_SUCCESS, the string has been assigned to my_text_input. */
```

### <a name="see-also"></a>Zobacz też

- gx_single_line_text_input_backspace
- gx_single_line_text_input_buffer_clear
- gx_single_line_text_input_buffer_get
- gx_single_line_text_input_character_delete
- gx_single_line_text_input_character_insert
- gx_single_line_text_input_create
- gx_single_line_text_input_draw
- gx_single_line_text_draw_position_get
- gx_single_line_text_input_end
- gx_single_line_text_input_event_process
- gx_single_line_text_input_fill_color_set
- gx_single_line_text_input_home
- gx_single_line_text_input_left_arrow
- gx_single_line_text_input_position_get
- gx_single_line_text_input_right_arrow
- gx_single_line_text_input_style_add
- gx_single_line_text_input_style_remove
- gx_single_line_text_input_style_set
- gx_single_line_text_input_text_set_ext


## <a name="gx_slider_create"></a>gx_slider_create

Utwórz suwak

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_create(
    GX_SLIDER *slider, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, INT tick_count,
    GX_SLIDER_INFO *slider_info,
    ULONG style, USHORT slider_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet suwaka.

GX_SLIDER pochodzi od GX_WIDGET i w związku z tym wszystkie gx_widget usługi API mogą być używane z GX_SLIDER widżetami typu.

### <a name="parameters"></a>Parametry

- **Slider**: blok kontrolny widżetu Slider
- **name**: Nazwa suwaka
- **element nadrzędny**: wskaźnik do elementu nadrzędnego widget
- **tick_count**: liczba znaczników suwaka
- **slider_info**: wskaźnik do informacji o suwaku, który jest strukturą używaną do przekazywania limitów wartości suwaka, rozmiaru i położenia wskazówki suwaka oraz innych parametrów suwaka. **Dodatek I** zawiera definicję do GX_SLIDER_INFO struktury.
- **styl**: styl suwaka. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **slider_id**: zdefiniowany przez aplikację identyfikator suwaka
- **rozmiar**: Wymiary suwaka

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) — Tworzenie suwaka pomyślne
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_ALREADY_CREATED**: (0x13) — element widget został już utworzony
- **GX_INVALID_SIZE**: (0X19) Nieprawidłowy rozmiar bloku kontrolki widgetu
- **GX_INVALID_WIDGET**: (0X12) element widget elementu nadrzędnego jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create slider “my_slider”. */

GX_SLIDER my_slider;
GX_SLIDER_INFO info;

info.gx_slider_info_min_val = 0;
info.gx_slider_info_max_val = 100;
info.gx_slider_info_current_val = 50;
info.gx_slider_info_increment = 1;
info.gx_slider_info_min_travel = 20;
info.gx_slider_info_max_travel = 20;
info.gx_slider_info_needle_width = 10;
info.gx_slider_info_needle_height = 10;
info.gx_slider_info_needle_inset = 5;
info.gx_slider_info_needle_hotspot_offset = 5;

status = gx_slider_create(&my_slider, “my_slider”,
    &my_parent, 10, info, GX_STYLE_ENABLED, ID_MY_SLIDER, &size);

/* If status is GX_SUCCESS the slider “my_slider” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_draw"></a>gx_slider_draw

Suwak rysowania

### <a name="prototype"></a>Prototype

```C
VOID gx_slider_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Opis

Ta usługa rysuje suwak. Ta usługa jest używana wewnętrznie przez funkcję gx_slider_create, ale jest również narażona na użycie przez aplikację w tych wystąpieniach, gdy zdefiniowana jest funkcja rysowania suwaków niestandardowych.

### <a name="parameters"></a>Parametry

- **Slider**: blok kontrolny widżetu Slider

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Call default slider draw. */
    gx_slider_draw(slider);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_event_process"></a>gx_slider_event_process

Zdarzenie suwaka procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_event_process(
    GX_SLIDER *slider, 
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie suwaka. Ta funkcja jest wewnętrznie przywoływana przez funkcję gx_slider_create, ale jest udostępniona do użycia przez aplikację w takich przypadkach, gdy aplikacja definiuje niestandardową funkcję przetwarzania zdarzeń suwaka.

### <a name="parameters"></a>Parametry

- **Slider**: blok kontrolny widżetu Slider
- **zdarzenie**: wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) proces zdarzenia suwaka zakończony pomyślnie
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic slider event processing as part of custom event processing function. */

UINT custom_slider_event_process(GX_SLIDER *slider,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;
    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default slider event processing */
            status = gx_slider_event_process(slider, event);
            break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_info_set"></a>gx_slider_info_set

Ustaw blok informacji o suwaku

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_info_set(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info);
```

### <a name="description"></a>Opis

Ta usługa przypisuje wybrane informacje o suwaku, takie jak minimum suwaka, maksimum suwaka i bieżąca wartość suwaka do wskazanego suwaka. Suwak zaktualizuje pozycję wskazówki i ponownie narysuje na podstawie nowych informacji o suwaku.

### <a name="parameters"></a>Parametry

- **Slider**: blok kontrolny widżetu Slider
- **info**: wskaźnik do struktury informacji o suwaku. **Dodatek I** zawiera definicję do GX_SLIDER_INFO struktury.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił informacje o suwaku
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_SLIDER_INFO my_slider_info;
my_slider_info.gx_slider_info_min_val = 0;
my_slider_info.gx_slider_info_max_val = 100;
my_slider_info.gx_slider_info_current_val = 50;
my_slider_info.gx_slider_info_increment = 1;
my_slider_info.gx_slider_info_min_travel = 20;
my_slider_info.gx_slider_info_max_travel = 20;
my_slider_info.gx_slider_info_needle_width = 10;
my_slider_info.gx_slider_info_needle_height = 10;
my_slider_info.gx_slider_info_needle_inset = 5;

my_slider_info.gx_slider_info_needle_hotspot_offset = 5;

/* Set slider information for slider “my_slider”. */
status = gx_slider_info_set (&my_slider, &my_slider_info);

/* If status is GX_SUCCESS the “my_slider” is configured with my_slider_info. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_needle_draw"></a>gx_slider_needle_draw

Rysuj wskazówkę suwaka

### <a name="prototype"></a>Prototype

```C
VOID gx_slider_needle_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Opis

Ta usługa rysuje wskazówkę suwaka. Ta usługa jest automatycznie wywoływana przez funkcję gx_slider_draw, ale może być również wywoływana przez aplikację jako część niestandardowej funkcji rysowania suwaka.

### <a name="parameters"></a>Parametry

- **Slider**: blok kontrolny widżetu Slider

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Add your own background draw here. */

    /* Call default tickmarks draw. */
    gx_slider_tickmarks_draw(slider);

    /* Call default slider needle draw. */
    gx_slider_needle_draw(slider);
}
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_needle_position_get"></a>gx_slider_needle_position_get

Pobierz położenie wskazówki dla suwaka

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_needle_position_get(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *slider_info,
    GX_RECTANGLE *return_position);
```

### <a name="description"></a>Opis

Ta usługa oblicza pozycję wskazówki suwaka na podstawie bieżącej wartości suwaka.

### <a name="parameters"></a>Parametry

- **Slider**: blok kontrolny widżetu Slider
- **slider_info**: wskaźnik do struktury informacji o suwaku definiujący limity suwaków, rozmiar wskazówki i przesunięcie oraz inne parametry suwaka. **Dodatek I** zawiera definicję do GX_SLIDER_INFO struktury.
- **return_position**: wskaźnik do miejsca docelowego dla pozycji wskazówki

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) udany wskaźnik wskazówki dla suwaka Get
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget
- **GX_INVALID_VALUE**: (0x22) nieprawidłowe informacje o suwaku

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RECTANGLE needle_position;

/* Get the needle position for slider “my_slider”. */
status = gx_slider_needle_posistion_get(&my_slider, &slider_info,
    &needle_position);

/* If status is GX_SUCCESS the needle position for slider “my_slider” has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_tickmarks_draw"></a>gx_slider_tickmarks_draw

Rysuj suwak rysowania znaczniki

### <a name="prototype"></a>Prototype

```C
VOID gx_slider_tickmarks_draw(GX_SLIDER *slider);
```

### <a name="description"></a>Opis

Ta usługa rysuje suwak znaczniki. Ta funkcja jest wywoływana wewnętrznie przez funkcję gx_slider_draw, ale jest udostępniona do użycia przez aplikacje, które mogą implementować funkcję rysowania suwaków niestandardowych.

### <a name="parameters"></a>Parametry

- **Slider**: blok kontrolny widżetu Slider

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom slider draw function. */
VOID my_slider_draw(GX_SLIDER *slider)
{
    /* Add your own background draw here. */

    /* Call default tickmarks draw. */
    gx_slider_tickmarks_draw(slider);

    /* Call default slider needle draw. */
    gx_slider_needle_draw(slider);
}
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_travel_get
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_travel_get"></a>gx_slider_travel_get

Pobierz drogę suwaka

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_travel_get(
    GX_SLIDER *widget,
    GX_SLIDER_INFO *info,
    INT *return_min_travel, 
    INT *return_max_travel);
```

### <a name="description"></a>Opis

Ta usługa Pobiera przesunięcie suwaka.

### <a name="parameters"></a>Parametry

- **Slider**: blok kontrolny widżetu Slider
- **info**: wskaźnik do struktury informacji o suwaku. **Dodatek I** zawiera definicję do GX_SLIDER_INFO struktury.
- **return_min_travel**: wskaźnik do miejsca docelowego dla minimalnej wartości skoku</td>
- **return_max_travell**: wskaźnik do miejsca docelowego dla maksymalnej wartości skoku</td>

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) Przesuwanie suwaka zakończone powodzeniem
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget
- **GX_INVALID_VALUE**: (0x22) nieprawidłowe informacje o suwaku

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Get travel information for for slider “my_slider”. */
status = gx_slider_travel_get(&my_slider, &info,
    &my_min_travel, &my_max_travel);

/* If status is GX_SUCCESS the travel max/min values for slider “my_slider” have been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_value_calculate
- gx_slider_value_set

## <a name="gx_slider_value_calculate"></a>gx_slider_value_calculate

Oblicz wartość suwaka

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_value_calculate(
    GX_SLIDER *slider, 
    GX_SLIDER_INFO *info,
    INT new_position);
```

### <a name="description"></a>Opis

Ta usługa oblicza wartość suwaka na podstawie pozycji wskazówki suwaka. Ta funkcja jest wywoływana wewnętrznie przez GUIX, gdy użytkownik przenosi wskazówkę suwaka, ale może być również wywoływana przez aplikację podczas implementowania niestandardowego widżetu suwaka.

### <a name="parameters"></a>Parametry

- **Slider**: blok kontrolny widżetu Slider
- **info**: wskaźnik do informacji o suwaku. **Dodatek I** zawiera definicję do GX_LISDER_INFO struktury.
- **new_position**: Nowa pozycja suwaka

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) Obliczanie wartości suwaka zakończone powodzeniem
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget
- **GX_INVALID_VALUE**: (0x22) nieprawidłowe informacje o suwaku

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Calculate new value for slider “my_slider”. */
status = gx_slider_value_calculate(&my_slider,
    &my_slider.gx_slider_info, new_slider_position);

/* If status is GX_SUCCESS the slider value of “my_slider” has been calculated. */

```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_set

## <a name="gx_slider_value_set"></a>gx_slider_value_set

Ustaw wartość suwaka

### <a name="prototype"></a>Prototype

```C
UINT gx_slider_value_set(
    GX_SLIDER *slider,
    GX_SLIDER_INFO *info, 
    INT new_value);
```

### <a name="description"></a>Opis

Ta usługa ustawia wartość suwaka. Ten interfejs API może być wywoływany przez aplikację w celu przeniesienia wskazówki suwaka w obszarze kontrola programu, pomijając potrzeby wprowadzania danych przez użytkownika w celu przeciągnięcia suwaka.

### <a name="parameters"></a>Parametry

- **Slider**: blok kontrolny widżetu Slider
- **info**: wskaźnik do struktury informacji o suwaku. **Dodatek I** zawiera definicję do GX_SLIDER_INFO struktury
- **new_value**: Nowa wartość suwaka

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) ustawiono wartość suwaka pomyślne
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set new value for slider “my_slider”. */
status = gx_slider_value_set(&my_slider,
    &my_slider.gx_slider_info, new_value);

/* If status is GX_SUCCESS the new value has been set for slider “my_slider”. */
```

### <a name="see-also"></a>Zobacz też

- gx_pixelmap_slider_create
- gx_pixelmap_slider_draw
- gx_pixelmap_slider_event_process
- gx_pixelmap_slider_pixelmap_set
- gx_slider_create
- gx_slider_draw
- gx_slider_event_process
- gx_slider_needle_draw
- gx_slider_needle_position_get
- gx_slider_needle_position_get
- gx_slider_tickmarks_draw
- gx_slider_travel_get
- gx_slider_value_calculate

##  <a name="gx_sprite_create"></a>gx_sprite_create

Tworzenie widżetu Sprite

### <a name="prototype"></a>Prototype

```C
UINT gx_sprite_create(
    GX_SPRITE *sprite, GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count,
    ULONG style, USHORT sprite_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet GX_SPRITE. Sprite jest używany do wyświetlania sekwencji pixelmaps jak w animacji lub może być używany jako element widget wyświetlania wielostanowego Pixelmap.

GX_SPRITE pochodzi od GX_WIDGET i obsługuje wszystkie gx_widget usługi interfejsu API.

Widżet GX_SPRITE wymaga tablicy struktur GX_SPRITE_FRAME do definiowania animacji Sprite. **Dodatek I** zawiera definicję do GX_PRITE_FRAME struktury.

### <a name="parameters"></a>Parametry

- **Sprite**: blok kontrolki widgetu Sprite
- **name**: opcjonalna nazwa Sprite
- **element nadrzędny**: wskaźnik do elementu nadrzędnego widget
- **frame_list**: tablica struktur GX_SPRITE_FRAME
- **frame_count**: określa liczbę wpisów w tablicy listy ramek
- **styl**: styl Sprite. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **sprite_id**: zdefiniowany przez aplikację identyfikator Sprite
- **rozmiar**: Wymiary Sprite

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) powodzenie tworzenia ikon
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_ALREADY_CREATED**: (0x13) — element widget został już utworzony
- **GX_INVALID_WIDGET**: (0X12) element widget elementu nadrzędnego jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create sprite “my_sprite”. */

status = gx_sprite_create(&my_sprite, “my_sprite”,
    &my_parent,
    sprite_frame_list, frame_count,
    GX_STYLE_SPRITE_AUTO|GX_STYLE_SPRITE_LOOP,
    ID_MY_SPRITE, &size);

/* If status is GX_SUCCESS the sprite “my_sprite” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_sprite_start
- gx_sprite_stop
- gx_sprite_current_frame_set
- gx_sprite_frame_list_set

## <a name="gx_sprite_current_frame_set"></a>gx_sprite_current_frame_set

Przypisz ramkę Sprite

### <a name="prototype"></a>Prototype

```C
UINT gx_sprite_current_frame_set(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>Opis

Ta usługa przypisuje bieżącą ramkę Sprite. Jeśli widżet GX_SPRITE nie jest automatycznie uruchomiony, może być używany jako Sygnalizator stanu kontrolowany przez program, wyświetlając Pixelmap Framed Command.

### <a name="parameters"></a>Parametry

- **Sprite**: blok kontrolki widgetu Sprite
- **ramka**: ramka Sprite do wyświetlenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) powiodło się
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Assign frame number 3 as the current sprite frame */
status = gx_sprite_current_frame_set(&my_sprite, 3);

/* If status is GX_SUCCESS the sprite “my_sprite” will display frame index 3. */
```

### <a name="see-also"></a>Zobacz też

- gx_sprite_start
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_sprite_frame_list_set"></a>gx_sprite_frame_list_set

Przypisywanie lub zmiana listy ramek Sprite

### <a name="prototype"></a>Prototype

```C
UINT gx_sprite_frame_list_set(
    GX_SPRITE *sprite,
    GX_SPRITE_FRAME *frame_list,
    USHORT frame_count);
```

### <a name="description"></a>Opis

Ta usługa może być używana do przypisywania lub ponownego przypisywania listy ramek używanej przez widżet Sprite po utworzeniu elementu widget Sprite. Aby uzyskać informacje o zawartości listy ramek Sprite, zapoznaj się z dokumentacją interfejsu API gx_sprite_create.

### <a name="parameters"></a>Parametry

- **Sprite**: blok kontrolki widgetu Sprite
- **frame_list**: tablica struktur GX_SPRITE_FRAME lub GX_NULL bez listy ramek.
- **frame_count**: liczba ramek w tablicy listy ramek

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) pomyślny zestaw list ramek Sprite
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Assign framelist_1, which has 10 frames, to my_sprite */
status = gx_sprite_frame_list_set(&my_sprite, framelist_1, 10);

/* If status is GX_SUCCESS the new frame list is now associated with this sprite */
```

### <a name="see-also"></a>Zobacz też

- gx_sprite_current_frame_set
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_create

## <a name="gx_sprite_start"></a>gx_sprite_start

Rozpocznij sekwencję przebiegu Sprite

### <a name="prototype"></a>Prototype

```C
UINT gx_sprite_start(
    GX_SPRITE *sprite, 
    USHORT frame);
```

### <a name="description"></a>Opis

Ta usługa uruchamia sekwencję autouruchamiania Sprite. Widżet Sprite przeprowadzi przechodzenie przez ramki Sprite do czasu osiągnięcia ostatniej ramki lub będzie działać w sposób ciągły, jeśli ustawiono styl GX_SPRITE_LOOP.

### <a name="parameters"></a>Parametry

- **Sprite**: blok kontrolki widgetu Sprite
- **Frame**: początkowa ramka Sprite do wyświetlenia, zazwyczaj ramka 0

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie rozpoczął uruchomienie Sprite
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Start the sprite “my_sprite” */
status = gx_sprite_start(&my_sprite, 0);

/* If status is GX_SUCCESS the sprite “my_sprite” will start running */
```

### <a name="see-also"></a>Zobacz też

- gx_sprite_current_frame_set
- gx_sprite_stop
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_sprite_stop"></a>gx_sprite_stop

Zatrzymaj sekwencję przebiegu Sprite

### <a name="prototype"></a>Prototype

```C
UINT gx_sprite_stop(GX_SPRITE *sprite);
```

### <a name="description"></a>Opis

Ta usługa wstrzymuje sekwencję autouruchamiania Sprite.

### <a name="parameters"></a>Parametry

- **Sprite**: blok kontrolki widgetu Sprite

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie zatrzymano przebieg Sprite
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Stop the sprite sequence */
status = gx_sprite_stop(&my_sprite);

/* If status is GX_SUCCESS the sprite “my_sprite” is stopped. */
```

### <a name="see-also"></a>Zobacz też

- gx_sprite_current_frame_set
- gx_sprite_start
- gx_sprite_create
- gx_sprite_frame_list_set

## <a name="gx_string_scroll_wheel_create"></a>gx_string_scroll_wheel_create

Tworzenie kółka przewijania typu String

### <a name="prototype"></a>Prototype

```C
UINT gx_string_scroll_wheel_create(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    GX_CONST GX_CHAR **string_list, 
    ULONG style,
    USHORT Id, 
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Opis

Ta usługa tworzy kółko przewijania typu String.

GX_STRING_SCROLL_WHEEL pochodzi od GX_TEXT_SCROLL_WHEEL i w związku z tym wszystkie funkcje interfejsu API gx_text_scroll_wheel może być używane z GX_STRING_SCROLL_WHEEL widżetami.

Aplikacja może przekazać prostą tablicę ciągów do funkcji Create, która definiuje ciągi, które będą wyświetlane przez kółko przewijania, lub aplikacja może przekazać GX_NULL jako parametr string_list i wywołać `gx_string_scroll_wheel_string_id_list_set()` interfejs API, aby dostarczyć tablicę identyfikatorów ciągów. Jeśli druga metoda jest używana, kółko przewijania ciągu będzie automatycznie przełączać wyświetlane ciągi w przypadku zmodyfikowania języka aktywnej aplikacji.

Alternatywnie, jeśli ciągi do wyświetlenia nie są zdefiniowane statycznie lub nie są znane w momencie utworzenia kółka przewijania, aplikacja może przekazać GX_NULL jako parametr listy ciągów i wywołać funkcję API gx_text_scroll_wheel_callback_set () w celu zdefiniowania funkcji wywołania zwrotnego, która będzie zawierać ciągi do wyświetlania w czasie rzeczywistym w miarę potrzeby.

### <a name="parameters"></a>Parametry

- **koło**: adres bloku formantu pokrętła przewijania ciągu
- **name**: Nazwa widżetu zdefiniowanego przez aplikację
- **element nadrzędny**: koło lub GX_NULL
- **total_rows**: łączną liczbę wierszy do prezentowania użytkownikowi
- **string_list**: statycznie zdefiniowana tablica ciągów lub GX_NULL
- **styl**: wymagane flagi stylu
- **ID**: flagi stylu koła zdefiniowanego przez aplikację
- **rozmiar**: początkowy rozmiar kółka przewijania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie utworzono koło przewijania ciągu
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR (0x07)**: nieprawidłowy wskaźnik
- **GX_ALREADY_CREATED**: (0x13) — element widget został już utworzony
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CONST GX_CHAR *days[] = {
    “Sunday”,
    “Monday”,
    “Tuesday”,
    “Wednesday”,
    “Thursday”,
    “Friday”,
    “Saturday”
};

GX_STRING_SCROLL_WHEEL wheel;

/* Create the string scroll wheel. */

status = gx_string_scroll_wheel_create(&wheel, “Day Wheel”,
    root, 7, days,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|GX_STYLE_TEXT_SCROLL_WHEEL_ROUND,
    ID_SCROLL_WHEEL_DAY, &size);

/* If status is GX_SUCCESS the string scroll wheel has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_event_process"></a>gx_string_scroll_wheel_event_process


Zdarzenie kółka przewijania ciągu procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, 
    INT id_count);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego kółka przewijania ciągu. Ta usługa powinna być wywoływana jako domyślna procedura obsługi zdarzeń przez wszelkie niestandardowe funkcje przetwarzania zdarzeń kółka przewijania ciągów.

### <a name="parameters"></a>Parametry

- **koło** Wskaźnik do bloku kontrolki pokrętła przewijania ciągu
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia kółka przewijania ciągu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic string scroll wheel event processing as part of custom event processing function. */

UINT custom_string_scroll_wheel_event_process(GX_STRING_SCROLL_WHEEL *wheel, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default string scroll wheel event processing */
        status = gx_string_scroll_wheel_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_string_id_list_set"></a>gx_string_scroll_wheel_string_id_list_set

Przypisz tablicę identyfikatorów ciągów

### <a name="prototype"></a>Prototype

```C
UINT gx_string_scroll_wheel_string_id_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_RESOURCE_ID *string_id_list, INT id_count);
```

### <a name="description"></a>Opis

Ta usługa przypisuje tablicę identyfikatorów ciągów do widgetu kółka przewijania ciągu. Ta metoda przypisywania ciągów do kółka przewijania ciągów jest zalecana, jeśli ciągi są zdefiniowane statycznie, a widżet musi działać w wielu językach. Jeśli ten interfejs API ma być używany, widżet przewijania kółka powinien zostać najpierw utworzony z listą ciągów GX_NULL.

### <a name="parameters"></a>Parametry

- **koło**: adres bloku formantu pokrętła przewijania ciągu
- **string_id_list**: tablica identyfikatorów ciągów
- **id_count**: rozmiar listy identyfikatorów.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił tablicę identyfikatorów ciągów
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget
- **GX_INVALID_VALUE**: 0X22) Nieprawidłowy rozmiar listy identyfikatorów

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CONST RESOURCE_ID wheel_ids[] = {
    GX_STRING_ID_SUNDAY,
    GX_STRING_ID_MONDAY,
    GX_STRING_ID_TUESDAY,
    GX_STRING_ID_WEDNESDAY,
    GX_STRING_ID_THURSDAY,
    GX_STRING_ID_FRIDAY,
    GX_STRING_ID_SATURDAY
};

GX_STRING_SCROLL_WHEEL wheel;

/* Stop the sprite sequence */

status = gx_string_scroll_wheel_string_id_list_set(&wheel, wheel_ids, 7);

/* If status is GX_SUCCESS the ID list has been assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_string_scroll_wheel_string_list_set"></a>gx_string_scroll_wheel_string_list_set

Przypisz tablicę ciągów

### <a name="prototype"></a>Prototype

```C
UINT gx_string_scroll_wheel_string_list_set(
    GX_STRING_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *string_list, 
    INT string_count);
```

### <a name="description"></a>Opis

Przypisuje tablicę ciągów do widgetu kółka przewijania ciągu. Ta wartość może służyć do modyfikowania ciągów wyświetlanych po początkowym utworzeniu elementu widget.

Należy zauważyć, że string_scroll_wheel nie obsługuje GX_STYLE_TEXT_COPY i dlatego tablica ciągów przenoszona do tej funkcji powinna być statycznie zdefiniowana przez aplikację.

### <a name="parameters"></a>Parametry

- **koło**: adres bloku formantu pokrętła przewijania ciągu
- **string_list**: tablica wskaźników ciągu
- **string_count**: rozmiar tablicy ciągów.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie zmieniły ciągi dla kółka przewijania
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget
- **GX_INVALID_VALUE**: (0X22) Nieprawidłowy rozmiar listy ciągów

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CONST GX_CHAR *days[] = {
    “Sunday”,
    “Monday”,
    “Tuesday”,
    “Wednesday”,
    “Thursday”,
    “Friday”,
    “Saturday”
};

GX_STRING_SCROLL_WHEEL wheel;

/* Set the array of strings to the scroll wheel. */

status = gx_string_scroll_wheel_string_list_set(&wheel, days, 7);

/* If status is GX_SUCCESS the string array has been assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_create
- gx_string_scroll_wheel_event_process
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_studio_widget_create"></a>gx_studio_widget_create

Tworzenie elementu widget zdefiniowanego w pliku specyfikacji wygenerowanej przez Studio

### <a name="prototype"></a>Prototype

```C
GX_WIDGET *gx_studio_widget_create(
    GX_BYTE *control,
    GX_CONST GX_STUDIO_WIDGET *definition, 
    GX_WIDGET *parent);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet i elementy podrzędne widżetu przy użyciu specyfikacji widget zdefiniowanej w pliku specyfikacji wygenerowanej przez program GUIX Studio. Ta funkcja pozwala uniknąć wyszukiwania "według nazwy" podobnej funkcji `gx_studio_named_widget_create()` .

Struktura GX_STUDIO_WIDGET jest zdefiniowana w pliku nagłówka specyfikacji aplikacji wygenerowanego przez program GUIX Studio.

Dla elementów widget przydzielony statycznie, blok kontrolki widżetu jest zdefiniowany w pliku z wygenerowanymi specyfikacjami. c, a podano nazwę widżetu zdefiniowaną w programie GUIX Studio. W przypadku elementów widget przypisywanych dynamicznie aplikacja powinna przekazać GX_NULL jako adres bloku kontrolki widżetu, a funkcja podejmie próbę dynamicznego przydzielenia bloku kontrolki widżetu za pomocą `gx_system_memory_allocate()` funkcji, która jest również definiowana przez i udostępniana przez aplikację.

Aby aplikacja mogła bezpośrednio odwoływać się do definicji widżetu GUIX Studio w wygenerowanym pliku specyfikacji, należy przestrzegać konwencji nazewnictwa wykorzystywanej przez generator kodu graficznego interfejsu użytkownika Studio. Struktura GX_STUDIO_WIDGET generowana w pliku Specification. c jest zawsze nazywana zgodnie z konwencją: <widget_name>_define, gdzie pole <widget_name> może powtarzać się wiele razy, jeśli widżet jest elementem podrzędnym widgetu podrzędnego.

### <a name="parameters"></a>Parametry

- **kontrolka** Wskaźnik do bloku kontrolki elementu widget lub GX_NULL, jeśli jest przydzielany dynamicznie.
- **Definicja** Struktura definicji widżetu wygenerowanego przez Studio
- wskaźnik **nadrzędny** do elementu nadrzędnego widżetu, jeśli istnieje

### <a name="return-values"></a>Wartości zwrócone

Wskaźnik do utworzonego bloku kontrolki widget lub GX_NULL, jeśli Tworzenie nie powiodło się.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create the widget “playlist_screen”, which is statically allocated. */

widget = gx_studio_widget_create(&playlist_screen,
    &playlist_screen_define,
    root_window);

/* If widget != GX_NULL the widget was created. */

/* create the widget “songs_screen”, which is dynamically allocated */

widget = gx_studio_widget_create(GX_NULL,
    &songs_screen_define, root_window);
```

### <a name="see-also"></a>Zobacz też

- gx_studio_named_widget_create

## <a name="gx_studio_named_widget_create"></a>gx_studio_named_widget_create

Tworzenie elementu widget zdefiniowanego w pliku specyfikacji wygenerowanej przez Studio

### <a name="prototype"></a>Prototype

```C
UINT *gx_studio_named_widget_create(
    char *name, 
    GX_WIDGET *parent,
    GX_WIDGET **new_widget);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet i elementy podrzędne widżetu przy użyciu specyfikacji widget zdefiniowanej w pliku specyfikacji wygenerowanej przez program GUIX Studio.

Ta funkcja API służy do tworzenia ekranów najwyższego poziomu przy użyciu nazwy ekranu określonej w aplikacji GUIX Studio jako identyfikatora definicji widżetu.

### <a name="parameters"></a>Parametry

- **Nazwa**: Nazwa ekranu, zgodnie z definicją w aplikacji GUIX Studio.
- **element nadrzędny**: wskaźnik do elementu nadrzędnego widżetu, jeśli istnieje
- **new_widget**: lokalizacja do zwrócenia wskaźnika utworzonego elementu widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) powiodło się
- **GX_FAILURE**: (0X11) nazwany element widget nie został znaleziony

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create the widget named “child_popup”,
   which is a child of the top-level screen “main_screen”. */

GX_WIDGET *menu_screen;

status = gx_studio_named_widget_create(“main_menu”,
    &root_window, &menu_screen);

/* If status == GX_SUCCESS the screen was created
   and linked to the root window. */
```

### <a name="see-also"></a>Zobacz też

- gx_studio_widget_create

## <a name="gx_studio_display_configure"></a>gx_studio_display_configure

Konfiguracja wyświetlania zdefiniowana w projekcie programu GUIX Studio

### <a name="prototype"></a>Prototype

```C
UINT *gx_studio_display_configure(
    USHORT display,
    UINT (*driver)(GX_DISPLAY *),
    USHORT language, 
    USHORT theme,
    GX_WINDOW_ROOT **return_root);
```

### <a name="description"></a>Opis

Ta usługa inicjuje GX_DISPLAY tak, aby była gotowa do użycia. Ta funkcja konsoliduje funkcje, aby zainicjować blok sterowania GX_DISPLAY, utworzyć kanwę w celu dopasowania do wyświetlania i utworzyć okno główne dla kanwy. Ta funkcja instaluje również motyw języka i zasobów żądany po zainicjowaniu ekranu.

Ta funkcja konsoliduje nakłady programistyczne najczęściej wymagane do przygotowania ekranu do użycia. Funkcja wywołuje gx_display_create (), gx_display_color_table_set, gx_display_font_table_set, gx_display_pixelmap_table_set, gx_system_language_table_set, gx_system_active_language_set, gx_system_scroll_appearance_set, gx_canvas_create i gx_window_root_create funkcji, wszystkie lub niektóre z nich byłyby wymagane przez program aplikacji.

### <a name="parameters"></a>Parametry

- **Wyświetl**: indeks w tabeli wyświetlania, która odnosi się do definicji wyświetlania w pliku projektu Studio.
- **Sterownik**: wskaźnik przedstawiający funkcję inicjowania sterownika. Ta funkcja jest wywoływana, aby zainicjować wskaźniki funkcji pośrednich bloku sterowania GX_DISPLAY, a także wykonać dowolną wymaganą konfigurację sprzętu.
- **Język**: indeks tabeli początkowej języka
- **Język**: początkowy indeks motywu
- **root**: wskaźnik do zmiennej, w której ma zostać zwrócony adres okna głównego lub GX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) powiodło się
- Nie można zainicjować wyświetlania **GX_FAILURE**: (0x11)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create the widget named “child_popup”, which is a child of the
   top-level screen “main_screen”. */

GX_WIDGET *menu_screen;

status = gx_studio_display_configure(MAIN_DISPLAY,
    my_driver_setup, LANGUAGE_ENGLISH, DEFAULT_THEME, GX_NULL);

/* If status == GX_SUCCESS the display was initialized, a canvas was
created for the display, a root window was created for the canvas, and
the requested language and theme have been installed.
*/
```

### <a name="see-also"></a>Zobacz też

- gx_display_create
- gx_display_color_table_set
- gx_display_font_table_set
- gx_display_pixelmap_table_set
- gx_system_language_table_set
- gx_system_active_language_set
- gx_system_scroll_appearance_set
- gx_canvas_create
- gx_window_root_create

## <a name="gx_system_active_language_set"></a>gx_system_active_language_set

Ustaw język aktywny

### <a name="prototype"></a>Prototype

```C
UINT gx_system_active_language_set(GX_UBYTE language);
```

### <a name="description"></a>Opis

Ta usługa ustawia bieżący język. Indeks języka musi być mniejszy niż liczba kolumn w tabeli ciągów aplikacji. Ta funkcja została uznana za przestarzałą na rzecz gx_display_active_language_set. Wszystkie nowe aplikacje powinny używać gx_display_active_langauge_set.

### <a name="parameters"></a>Parametry

- **Język**: indeks języka, zdefiniowany w pliku nagłówkowym zasobu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił aktywny język
- **GX_CALLER_ERROR**: * * (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: * * (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE**: * * (0X22) Nieprawidłowy indeks języka

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set active language and mark widget canvas as dirty. */
status = gx_system_active_language_set(ID_LANGUAGE_ENGLISH);

/* If status is GX_SUCCESS the active language has been assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_language_table_set
- gx_display_active_langauge_set
- gx_display_string_get

## <a name="gx_system_animation_get"></a>gx_system_animation_get

Uzyskaj blok sterowania animacją z puli systemowej

### <a name="prototype"></a>Prototype

```C
UINT gx_system_animation_get(GX_ANIMATION **animation);
```

### <a name="description"></a>Opis

Ta usługa może służyć do uzyskania bloku kontroli animacji z puli takich bloków sterujących obsługiwanych przez składnik gx_system. Pula bloków kontrolki animacji i powiązane usługi API są dostępne tylko wtedy, gdy stała GX_ANIMATION_POOL_SIZE jest zdefiniowana z wartością 0. Domyślnym ustawieniem tej wartości jest 6, co oznacza, że Pula bloków kontrolki animacji systemu zawiera rozmiar GX_ANIMATION bloku sterowania.

Blok kontrolny animacji przydzielony przy użyciu tego interfejsu API jest automatycznie zwracany do puli wolnych, jeśli animacja zostanie uruchomiona. Jeśli animacja jest zatrzymana przy użyciu gx_animation_stop lub nie można jej uruchomić z powodu błędnego błędu, blok sterowania animacji powinien zostać zwrócony do puli bezpłatna przez aplikację przy użyciu gx_system_animation_free.

### <a name="parameters"></a>Parametry

- **animacja**: adres wskaźnika do odbierania GX_ANIMATION wskaźnik.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie uzyskano blok kontrolny animacji
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik animacji
- **GX_OUT_OF_ANIMATIONS**: (0x31) wykorzystano pulę animacji systemowych

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_ANIMATION *animation;

UINT status = gx_system_animation_get(&animation);

if (status == GX_SUCCESS)
{
    gx_animation_start(animation, animation_info);
}
```

### <a name="see-also"></a>Zobacz też

- gx_animation_create
- gx_animation_start
- gx_animation_stop
- gx_system_animation_free

## <a name="gx_system_animation_free"></a>gx_system_animation_free

Zwróć blok sterowania animacją do puli systemu

### <a name="prototype"></a>Prototype

```C
UINT gx_system_animation_free(GX_ANIMATION *animation);
```

### <a name="description"></a>Opis

Ta usługa może być używana do zwrócenia bloku kontroli animacji do puli systemu. Pula bloków kontrolki animacji i powiązane usługi API są dostępne tylko wtedy, gdy stała GX_ANIMATION_POOL_SIZE jest zdefiniowana z wartością 0. Domyślnym ustawieniem tej wartości jest 6, co oznacza, że Pula bloków kontrolki animacji systemu zawiera rozmiar GX_ANIMATION bloku sterowania.

Blok sterowania animacją przydzieloną przy użyciu gx_system_animation_get () jest automatycznie zwracany do puli wolnych, jeśli animacja zostanie uruchomiona. Próba zwrócenia bloku sterowania animacją do puli bezpłatna, która została już zwrócona do bezpłatnej puli, nie ma żadnego wpływu.

Jeśli animacja jest zatrzymana przy użyciu gx_animation_stop lub nie można jej uruchomić z powodu błędu, blok sterowania animacji, który został uzyskany przy użyciu gx_system_animation_get (), powinien zostać zwrócony do puli wolnych przez aplikację przy użyciu gx_system_animation_free ().

Animacja musi być w stanie bezczynności, zanim będzie można zwrócić do puli bezpłatna. Animacja jest w stanie bezczynności, gdy nie została uruchomiona, gdy zostanie zatrzymana, lub gdy zostanie uruchomiona do ukończenia.

### <a name="parameters"></a>Parametry

- **animacja**: wskaźnik do bloku sterowania GX_ANIMATION.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) uccessfully — wydano blok animacji
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik animacji
- **GX_INVALID_ANIMATION**: (0x32) animacja nie jest bezczynna lub nie została przypisana z puli systemowej

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_ANIMATION *animation;

UINT status = gx_system_animation_get(&animation);

if (status == GX_SUCCESS)
{
    status = gx_animation_start(animation, animation_info);

    if (status != GX_SUCCESS)
    {
        /* animation did not start, return it to the free pool */
        gx_system_animation_free(animation);
    }
}
```

### <a name="see-also"></a>Zobacz też

- gx_animation_create
- gx_animation_start
- gx_animation_stop
- gx_system_animation_get

## <a name="gx_system_bidi_text_disable"></a>gx_system_bidi_text_disable

Wyłącz dynamiczną obsługę tekstu dwukierunkowego

### <a name="prototype"></a>Prototype

```C
UINT gx_system_bidi_text_disable(VOID);
```

### <a name="description"></a>Opis

Ta usługa wyłącza dynamiczną obsługę tekstu dwukierunkowego. Ta usługa wymaga zdefiniowania GX_DYNAMIC_BIDI_TEXT_SUPPORT podczas kompilowania biblioteki GUIX i jest wymagana tylko wtedy, gdy wymagana jest zmiana kolejności danych ciągu dwukierunkowego w czasie wykonywania. Większość aplikacji używa programu GUIX Studio do tworzenia poprawnie zmienianych kolejności ciągów tekstu dwukierunkowego.

### <a name="parameters"></a>Parametry

**Brak**

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie wyłączono obsługę tekstu dwukierunkowego

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* GX_DYNAMIC_BIDI_TEXT_SUPPORT is defined. */

/* Diable bidi text support. */
status = gx_system_bidi_text_disable();

/* If status is GX_SUCCESS, bidi text support was disabled. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_bidi_text_enable

## <a name="gx_system_bidi_text_enable"></a>gx_system_bidi_text_enable

Włącz dynamiczną obsługę tekstu dwukierunkowego

### <a name="prototype"></a>Prototype

```C
UINT gx_system_bidi_text_enable(VOID);
```

### <a name="description"></a>Opis

Ta usługa umożliwia dynamiczną obsługę tekstu dwukierunkowego. Ta usługa wymaga zdefiniowania GX_DYNAMIC_BIDI_TEXT_SUPPORT podczas kompilowania biblioteki GUIX i jest wymagana tylko wtedy, gdy wymagana jest zmiana kolejności danych ciągu dwukierunkowego w czasie wykonywania. Większość aplikacji używa programu GUIX Studio do tworzenia poprawnie zmienianych kolejności ciągów tekstu dwukierunkowego.

### <a name="parameters"></a>Parametry

**Brak**

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie włączono obsługę tekstu dwukierunkowego

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* GX_DYNAMIC_BIDI_TEXT_SUPPORT is defined. */

/* Enable bidi text support. */
status = gx_system_bidi_text_enable();

/* If status is GX_SUCCESS, bidi text support was enabled. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_bidi_text_disable

## <a name="gx_system_canvas_refresh"></a>gx_system_canvas_refresh

Odśwież wszystkie zanieczyszczone kanwy

### <a name="prototype"></a>Prototype

```C
UINT gx_system_canvas_refresh(VOID);
```

### <a name="description"></a>Opis

Ta usługa wymusza natychmiastowe Odrysowanie wszystkich zanieczyszczonych elementów widget i kanw. Ta usługa jest zwykle wywoływana wewnętrznie przez składnik systemu GUIX, ale może być wywoływana przez aplikację w celu wymuszenia natychmiastowej operacji odrysowania systemu.

### <a name="parameters"></a>Parametry

**Brak**

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie wydano blok animacji
- **GX_INVALID_CANVAS**: (0X20) nie utworzono kanwy
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Force immediate redraw operation. */
status = gx_system_canvas_refresh();

/* If status is GX_SUCCESS, canvas has been redraw. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_dirty_mark"></a>gx_system_dirty_mark

Oznacz obszar jako zanieczyszczony

### <a name="prototype"></a>Prototype

```C
UINT gx_system_dirty_mark(GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa oznacza obszar tego widżetu jako zanieczyszczony. To efektywnie ustawia widżet do przerysowania po zakończeniu przetwarzania zdarzeń systemowych.

### <a name="parameters"></a>Parametry

- **widget**: wskaźnik do bloku kontrolki elementu widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie oznaczył widżet jako zanieczyszczony
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Mark widget “my_widget” as dirty. */
status = gx_system_dirty_mark(&my_widget);

/* If status is GX_SUCCESS the area associated
   with “my_widget” has been marked as dirty. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_dirty_partial_add"></a>gx_system_dirty_partial_add

Oznacz obszar częściowy jako zanieczyszczony

### <a name="prototype"></a>Prototype

```C
UINT gx_system_dirty_partial_add(
    GX_WIDGET *widget,
    GX_RECTANGLE *dirty_area);
```

### <a name="description"></a>Opis

Ta usługa oznacza częściowy obszar tego widżetu jako zanieczyszczony. Powoduje to Zakolejkowanie widżetu do przerysowania przez operację odświeżania kanwy GUIX po zakończeniu przetwarzania zdarzeń systemowych.

### <a name="parameters"></a>Parametry

- **widget**: wskaźnik do bloku kontrolki elementu widget
- **dirty_area**: zanieczyszczony obszar elementu widget do oznaczania zanieczyszczony

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne częściowe zanieczyszczone pole
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget
- **GX_INVALID_SIZE**: (0X19) Nieprawidłowy rozmiar obszaru zanieczyszczonego

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Mark widget “my_widget” partial area as dirty. */

status = gx_system_dirty_partial_add(&my_widget,
    &partial_area);

/* If status is GX_SUCCESS the partial area “partial_area”
associated with “my_widget” has been marked as dirty. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_draw_context_get"></a>gx_system_draw_context_get

Pobierz kontekst rysowania

### <a name="prototype"></a>Prototype

```C
UINT gx_system_draw_context_get(GX_DRAW_CONTEXT **current_context);
```

### <a name="description"></a>Opis

Ta usługa zwraca wskaźnik do bieżącego kontekstu rysowania.

### <a name="parameters"></a>Parametry

- **current_context**: wskaźnik do miejsca docelowego dla bieżącego wskaźnika kontekstu rysowania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne uzyskanie bieżącego kontekstu
- **GX_PTR_ERROR**: 0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_DRAW_CONTEXT *current_context;

/* Get current drawing context. */

status = gx_system_draw_context_get(&current_context);

/* If status is GX_SUCCESS the current drawing context
   is contained in “current_context”. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_event_fold"></a>gx_system_event_fold

Wyślij zdarzenie

### <a name="prototype"></a>Prototype

```C
UINT gx_system_event_fold(GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przeszukuje kolejkę zdarzeń GUIX dla zdarzenia tego samego typu. Jeśli istnieje zdarzenie tego samego typu, ładunek zdarzenia zostanie zaktualizowany w celu dopasowania go do nowego zdarzenia. Jeśli nie zostanie znalezione pasujące zdarzenie, funkcja gx_system_event_send zostanie wywołana w celu dodania nowego zdarzenia do końca kolejki zdarzeń.

Ta funkcja jest często używana przez szybkie sterowniki wejścia Touch, aby zapobiec wypełnieniu kolejki zdarzeń z wieloma zdarzeniami PEN_DRAG. Ta funkcja może być również wywoływana przez aplikację, aby zapobiec dodawaniu wielu zdarzeń tego samego typu do kolejki zdarzeń GUIX.

### <a name="parameters"></a>Parametry

- **zdarzenie**: wskaźnik do zdarzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne wysłanie zdarzenia
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_EVENT my_event;

memset(&my_event, 0, sizeof(GX_EVENT));

my_event.gx_event_type = GX_EVENT_PEN_DOWN;

my_event.gx_event_payload.gx_event_pointdata.gx_point_x = 100;
my_event.gx_event_payload.gx_event_pointdata.gx_point_y = 200;

/* Send “my_event” for processing. */
status = gx_system_event_fold(&my_event);

/* If status is GX_SUCCESS the event has been sent for processing. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_event_send"></a>gx_system_event_send

Wyślij zdarzenie

### <a name="prototype"></a>Prototype

```C
UINT gx_system_event_send(GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa wysyła określone zdarzenie do kolejki zdarzeń systemu GUIX. Nowe zdarzenie jest umieszczane na końcu kolejki.

### <a name="parameters"></a>Parametry

- **zdarzenie**: wskaźnik do zdarzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne wysłanie zdarzenia
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Send “new_event” for processing. */

GX_EVENT new_event;

new_event.gx_event_target = widget ->gx_widget_parent;
new_event.gx_event_type = MY_EVENT_TYPE;

/* Set optional param. */
new_event.gx_event_payload.xxxx = yyyy
new_event.gx_event_sender = widget->gx_widget_id;

/* Push the event to event pool. */
status = gx_system_event_send(&new_event);

/* If status is GX_SUCCESS the event has been sent for processing. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_focus_claim"></a>gx_system_focus_claim

Fokus dotyczący roszczeń

### <a name="prototype"></a>Prototype

```C
UINT gx_system_focus_claim(GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa zastrzega fokus dla określonego widżetu. Jeśli widżet nie miał wcześniej fokusu, otrzyma zdarzenie GX_EVENT_FOCUS_GAINED.

### <a name="parameters"></a>Parametry

- **widget**: wskaźnik do bloku kontrolki elementu widget, aby przejąć fokus

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne zgłoszenie fokusu
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_NO_CHANGE**: element widget (0x08) już jest fokusem
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_WIDGET**: (nieprawidłowy element widget 0x12

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Claim focus for widget “my_widget”. */
status = gx_system_claim_focus(&my_widget);

/* If status is GX_SUCCESS the focus has been claimed for
   “my_widget”. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_initialize"></a>gx_system_initialize

Zainicjuj GUIX

### <a name="prototype"></a>Prototype

```C
UINT gx_system_initialize(VOID);
```

### <a name="description"></a>Opis

Ta usługa inicjuje GUIX. Ta usługa musi być wywoływana przed żadną inną usługą interfejsu API GUIX i powinna być wywoływana tylko raz podczas uruchamiania systemu.

### <a name="parameters"></a>Parametry

- **Brak**

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne zainicjowanie systemu
- **GX_SYSTEM_ERROR**: (0XFE) Nieprawidłowy rozmiar bloku kontroli GX_EVENT lub nie można utworzyć kolejki zdarzeń/obiektu mutex/wątku.
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Initialize GUIX. */
status = gx_system_initialize();

/* If status is GX_SUCCESS, GUIX has been initialized. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_language_table_get"></a>gx_system_language_table_get

Pobierz tabelę języka aktywnego

### <a name="prototype"></a>Prototype

```C
UINT gx_system_language_table_get( 
    GX_CHAR ****language_table,
    GX_UBYTE *languages_count, 
    UINT *string_count);
```

### <a name="description"></a>Opis

Ta usługa pobiera tabelę Active Language. Ta funkcja jest przestarzała na rzecz gx_display_language_table_get. Wszystkie nowe aplikacje powinny używać gx_display_language_table_get.

### <a name="parameters"></a>Parametry

- **language_table**: adres wskaźnika do tabeli języka powrotu.
- **languages_count**: adres zmiennej do zwrócenia kolumn tabeli.
- **string_count**: adres wskaźnika do zwracania wierszy tabeli.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie pobrałeś tabelę Active Language
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR ***language_table;

GX_UBYTE language_count;

UINT string_count;

/* Retrieve the language table */

status = gx_system_language_table_get(&language_table,
    &language_count, &string_count);
```

### <a name="see-also"></a>Zobacz też

- gx_display_language_table_get
- gx_display_language_table_set

## <a name="gx_system_language_table_set"></a>gx_system_language_table_set

Przypisz tabelę języka aktywnego

### <a name="prototype"></a>Prototype

```C
UINT gx_system_language_table_set(
    GX_CHAR ***language_table,
    GX_UBYTE languages_count, 
    UINT string_count);
```

### <a name="description"></a>Opis

Ta usługa instaluje tabelę aktywnych języków. Ta funkcja została uznana za przestarzałą na rzecz gx_display_language_table_set. Wszystkie nowe aplikacje powinny używać gx_display_language_table_set.

### <a name="parameters"></a>Parametry

- **language_table**: wskaźnik do tabeli językowej.
- **languages_count**: liczba języków w tabeli.
- **string_count**: liczba wierszy tabeli ciągów.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił tabelę języka
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Retrieve the language table */

status = gx_system_language_table_set(language_table,
    language_count, string_count);
```

### <a name="see-also"></a>Zobacz też

- gx_display_language_table_set
- gx_display_language_table_get
- gx_display_active_language_set

## <a name="gx_system_memory_allocator_set"></a>gx_system_memory_allocator_set

Przypisywanie funkcji alokacji pamięci, cofnięcia alokacji

### <a name="prototype"></a>Prototype

```C
UINT gx_system_memory_allocator_set(VOID *(allocate)(ULONG size),
    VOID(*release)(VOID *));
```

### <a name="description"></a>Opis

Ta usługa przypisuje funkcję wywołania zwrotnego dla aplikacji w celu przydzielenia pamięci dynamicznej i cofnięcia alokacji.

Jeśli aplikacja nie wymaga usługi GUIX, która używa dynamicznego przydzielania pamięci, ta usługa nie musi być wywoływana.

Jeśli jest używana, ta usługa powinna być wywoływana po gx_system_initialize (), która czyści wskaźniki usługi GUIX oraz przed jakąkolwiek usługą GUIX, która wymaga użycia dynamicznego przydzielania pamięci.

Usługi GUIX, które wymagają alokacji pamięci środowiska uruchomieniowego i usługi cofnięcia alokacji, obejmują:

- Ładowanie zasobów binarnych z magazynu zewnętrznego do środowiska uruchomieniowego GUIX.
- Dekoder obrazu JPEG środowiska uruchomieniowego oprogramowania.
- Dekoder obrazu PNG środowiska uruchomieniowego oprogramowania.
- Używanie widżetów tekstowych z GX_STYLE_TEXT_COPY.
- Funkcje narzędzia do zmiany rozmiaru i rotacji środowiska uruchomieniowego pixemap.
- Alokacja bloku ekranu i widżetu środowiska uruchomieniowego.

### <a name="parameters"></a>Parametry

- **Alokator**: funkcja alokatora pamięci
- **wydanie**: funkcja wolna pamięć

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie przypisać funkcję przydzielenia pamięci
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

W poniższym przykładzie użyto puli bajtów ThreadX do zaimplementowania usługi threadsafe pamięć dynamiczna i alokacja pamięci.

```C
TX_BYTE_POOL memory_pool;

#define SCRATCHPAD_SIZE (1024 * 4)

ULONG scratchpad[SCRATCHPAD_SIZE];

/* define memory allocation service */

VOID *memory_allocate(ULONG size)
{
    VOID *memptr;

    if (tx_byte_allocate(&memory_pool, &memptr, size, TX_NO_WAIT) == TX_SUCCESS)
    {
        return memptr;
    }
    return NULL;
}

/* define memory de-allocation service */
void memory_free(VOID *mem)
{
    tx_byte_release(mem);
}

/* create byte pool and install our dynamic memory services with GUIX
*/

VOID tx_application_define(void *first_unused_memory)
{
    /* create byte pool for GUIX to use */
    tx_byte_pool_create(&memory_pool, "scratchpad", scratchpad,
        SCRATCHPAD_SIZE * sizeof(ULONG));

    guix_setup();

    /* install our memory allocator and de-allocator */
    gx_system_memory_allocator_set(memory_allocate, memory_free);
}
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_pen_configure"></a>gx_system_pen_configure

Ustaw konfigurację pióra

### <a name="prototype"></a>Prototype

```C
UINT gx_system_pen_configure(GX_PEN_CONFIGURATION *pen_configuration);
```

### <a name="description"></a>Opis

Ta usługa ustawia konfigurację pióra, aby kontrolować szybkość pióra i parametry odległości używane do wyzwalania generacji typów zdarzeń GX_EVENT_FLICK.

Gx_pen_configuration_min_drag_dist element członkowski GX_PEN_CONFIGURATION jest stałym typem danych i należy używać GX_FIXED_VAL_MAKE (Value) do konwersji z INT do GX_FIXED_VAL. Na przykład jeśli chcesz ustawić minimalną odległość przeciągania na 0,5 pikseli na takt, musisz ustawić gx_pen_configuration_min_drag_dist na `GX_FIXED_VAL_MAKE(1) / 2` .

W GUIX releases 5.4.0 i starszym gx_pen_configuration_min_drag_dist członkiem GX_PEN_CONFIGURATION był typ (INT << 8), a nie typ GX_FIXED_VAL. Jeśli projekt z biblioteką 5.4.0 w wersji GUIX korzysta z tego interfejsu API, należy zmodyfikować parametr min_drag_dist lub GUIX_5_4_0_COMPATIBILITY #define podczas kompilowania biblioteki GUIX.

### <a name="parameters"></a>Parametry

- **pen_configuration** Wskaźnik do struktury konfiguracji pióra. **Dodatek I** zawiera definicję do GX_PEN_CONFIGURATION struktury

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił konfigurację pióra
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Define pen configuration, set minimum drag distance to 0.5 pixel
per tick, maximum pen speed to 10 ticks. That means GUIX will trigger
a vertical or horizontal flick event if the drag time is smaller than
10 ticks and the drag distance is bigger than 0.5 * drag_ticks. */

GX_PEN_CONFIGURATION pen_configuration;

#if defined(GUIX_5_4_0_COMPATIBILITY)
Pen_configuration.gx_pen_configuration_min_drag_dist = (1 << 8)/ 2;
#else
pen_configuration.gx_pen_configuration_min_drag_dist = GX_FIXED_VAL_MAKE(1) / 2;
#endif

pen_configuration.gx_pen_configuration_max_pen_speed_ticks = 10;

/* Set the pen configuration. */
status = gx_system_pen_configure(&pen_configuration);

/* If status is GX_SUCCESS the touch configure has been set. */
```

## <a name="gx_system_screen_stack_create"></a>gx_system_screen_stack_create

Tworzenie i Inicjowanie stosu ekranu systemu

### <a name="prototype"></a>Prototype

```C
UINT gx_system_screen_stack_create(
    GX_WIDGET **memory, 
    INT size);
```

### <a name="description"></a>Opis

Ta usługa definiuje pulę pamięci, która ma być używana na potrzeby stosu ekranu systemu. Stos ekranu systemu to opcjonalna funkcja, która może być używana przez aplikację do zarządzania wyglądem przepływu ekranu aplikacji.

Jeśli aplikacja zamierza korzystać z usług stosu ekranu, należy najpierw wywołać funkcję gx_system_screen_stack_create, aby skonfigurować region pamięci stosu ekranu.

### <a name="parameters"></a>Parametry

- **pamięć**: wskaźnik do bloku pamięci zarezerwowanej.
- **rozmiar**: rozmiar, w bajtach, zarezerwowany blok pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) — pomyślne utworzenie
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
#define SCREEN_STACK_DEPTH 8
GX_WIDGET *screen_stack[SCREEN_STACK_DEPTH * 2];

UINT status;

/* Get the scrollbar appearance. */

status = gx_system_screen_stack_create(screen_stack,
    sizeof(GX_WIDGET *) * SCREEN_STACK_DEPTH * 2);

/* If status is GX_SUCCESS the system screen stack is initialized
and ready for use. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_get"></a>gx_system_screen_stack_get

Pokaż górne wskaźniki stosu ekranu

### <a name="prototype"></a>Prototype

```C
UINT gx_system_screen_stack_get(
    GX_WIDGET **popped_parent,
    GX_WIDGET **popped_screen);
```

### <a name="description"></a>Opis

Ta funkcja powoduje wypunktowanie wskaźników stosu ekranu najwyższego poziomu i zwraca te wskaźniki do obiektu wywołującego. Ta funkcja różni się od gx_system_screen_stack_pop (), ponieważ ekran zdjęte nie jest automatycznie ponownie dołączany do poprzedniego elementu nadrzędnego. Zamiast tego wskaźniki są zdjęte ze stosu i zwracane do obiektu wywołującego, co umożliwia obiektowi wywołującemu dołączenie lub odrzucanie zwracanego ekranu zgodnie z potrzebami.

### <a name="parameters"></a>Parametry

- **popped_parent**: Lokalizacja przechowywania nadrzędnego wskaźnika widżetu.
- **popped_screen**: lokalizacja do przechowywania wskaźnika ekranu zdjęte.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie powiodło się pobranie wskaźników stosu ekranu
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_FAILURE**: (0X10) nieprawidłowy lub pusty stos ekranu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT status;

GX_WIDGET *parent_screen;

GX_WIDGET *popped_screen;

/* Pop a screen stack entry. */
status = gx_system_screen_stack_get(&parent_screen, &popped_screen);

/* If status is GX_SUCCESS, parent_screen and
popped_screen hold the topmost screen stack pointers. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_screen_stack_create
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_pop"></a>gx_system_screen_stack_pop

Podręczny wpis z poziomu stosu ekranu systemu

### <a name="prototype"></a>Prototype

```C
UINT gx_system_screen_stack_pop();
```

### <a name="description"></a>Opis

Ta funkcja powoduje przełączenie do górnego wpisu na stosie ekranu i automatyczne dołączanie ekranu zdjęte do widżetu nadrzędnego zdjęte.

### <a name="parameters"></a>Parametry

**brak**

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne pobranie wskaźników stosu ekranu
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_FAILURE**: (0X10) nieprawidłowy lub pusty stos ekranu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT status;

/* Pop a screen stack entry. */
status = gx_system_screen_stack_pop();

/* If status is GX_SUCCESS, the topmost screen stack entry has been
popped from the stack and re-attached to the previous parent. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_screen_stack_get
- gx_system_screen_stack_create
- gx_system_screen_stack_push
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_push"></a>gx_system_screen_stack_push

Wypychanie widżetu i wskaźnika nadrzędnego do stosu ekranu

### <a name="prototype"></a>Prototype

```C
UINT gx_system_screen_stack_push(GX_WIDGET *screen)
```

### <a name="description"></a>Opis

Ta usługa umieszcza wskaźnik do wskazanego widżetu, który jest zazwyczaj ekranem najwyższego poziomu na stosie ekranu. Jeśli widżet ma element nadrzędny, jest odłączony od elementu nadrzędnego. Wskaźnik widżetu nadrzędnego jest również wypychany do stosu ekranu. Widżet nadrzędny może mieć wartość NULL, co oznacza, że ekran, który nie jest widoczny lub dołączony do żadnego elementu nadrzędnego, może zostać wypchnięte do stosu ekranu. Jeśli widżet z elementem nadrzędnym jest wypychany do stosu ekranu, należy użyć interfejsu API screen_stack_get (), aby pobrać wskaźnik ekranu wypychanego, zamiast korzystać z interfejsu API screen_stack_pop (), który próbuje ponownie dołączyć widżet zdjęte do jego poprzedniego elementu nadrzędnego.

### <a name="parameters"></a>Parametry

- **ekran**: wskaźnik do widżetu do wypchnięcia do stosu ekranu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie uzyskuje wygląd paska przewijania
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Get the scrollbar appearance. */
status = gx_system_screen_stack_push(window);

/* If status is GX_SUCCESS, the widget pointed to by “window” has
been pushed to the screen stack, along with the widget’s parent
ponter. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_create
- gx_system_screen_stack_reset

## <a name="gx_system_screen_stack_reset"></a>gx_system_screen_stack_reset

Zresetuj stos ekranu systemu

### <a name="prototype"></a>Prototype

```C
UINT gx_system_screen_stack_reset();
```

### <a name="description"></a>Opis

Ta funkcja usuwa wszystkie wpisy ze stosu ekranu systemu. Jeśli ekrany zdjęte ze stosu mają dynamicznie przydzielane bloki kontroli przydzielone przez GUIX Studio, pamięć dla tych bloków kontroli jest zwalniana.

### <a name="parameters"></a>Parametry

**brak**

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie uzyskuje wygląd paska przewijania
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Get the scrollbar appearance. */
status = gx_system_screen_stack_reset();

/* If status is GX_SUCCESS the system screen stack has been cleared
of entries. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_screen_stack_get
- gx_system_screen_stack_pop
- gx_system_screen_stack_push
- gx_system_screen_stack_create

## <a name="gx_system_scroll_appearance_get"></a>gx_system_scroll_appearance_get

Uzyskaj wygląd przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_system_scroll_appearance_get(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *return_appearance);
```

### <a name="description"></a>Opis

Ta usługa pobiera wygląd paska przewijania.

### <a name="parameters"></a>Parametry

- **styl**: styl paska przewijania: `GX_SCROLLBAR_HORIZONTAL` lub `GX_SCROLLBAR_VERTICAL`
- **return_appearance**: wskaźnik do elementu docelowego dla wyglądu. **Dodatek I** zawiera definicję do GX_SCROLLBAR_APPERANCE

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie uzyskuje wygląd paska przewijania
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_SCROLLBAR_APPEARANCE my_appearance;

/* Get the scrollbar appearance. */

status = gx_system_scroll_appearance_get(style, &my_appearance);

/* If status is GX_SUCCESS “my_appearance” now contains the scroll
appearance. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_set
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_scroll_appearance_set"></a>gx_system_scroll_appearance_set

Ustaw wygląd przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_system_scroll_appearance_set(
    ULONG style,
    GX_SCROLLBAR_APPEARANCE *appearance);
```

### <a name="description"></a>Opis

Ta usługa ustawia domyślny wygląd przewijania. Po utworzeniu przewijania Ta struktura wyglądu jest używana, jeśli aplikacja nie udostępnia niestandardowej wersji.

### <a name="parameters"></a>Parametry

- **styl**: styl przewijania `GX_SCROLLBAR_HORIZONTAL` lub `GX_SCROLLBAR_VERTICAL`
- **wygląd**: zainicjowano wskaźnik do struktury wyglądu przy użyciu różnych atrybutów wyglądu ScrollBar. Zapoznaj się z **załącznikiem I** , aby zapoznać się z definicją struktury GX_SCROLLBAR_APPEARANCE.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił zestaw wyglądu przewijania
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_SCROLLBAR_APPEARANCE my_appearance;

memset(&my_appearance, 0, sizeof(GX_SCROLLBAR_APPEARANCE));

my_appearance.gx_scroll_width = 20;
my_appearance.gx_scroll_thumb_width = 18;

my_appearance.gx_scroll_thumb_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_thumb_border_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_button_color = GX_COLOR_ID_SCROLL_BUTTON;
my_appearance.gx_scroll_thumb_travel_min = 20;
my_appearance.gx_scroll_thumb_travel_max = 20;
my_appearance.gx_scroll_thumb_border_style = GX_STYLE_BORDER_THIN;

/* Set the scroll appearance. */

status = gx_system_scroll_appearance_set(GX_SCROLLBAR_VERTICAL, &my_appearance);

/* If status is GX_SUCCESS the scroll appearance has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_start"></a>gx_system_start

Uruchom GUIX

### <a name="prototype"></a>Prototype

```C
UINT gx_system_start(VOID);
```

### <a name="description"></a>Opis

Ta usługa uruchamia przetwarzanie GUIX. W normalnych warunkach ta funkcja nigdy nie zwraca, ale zamiast tego zaczyna przetwarzać kolejkę zdarzeń GUIX. Gdy kolejka zdarzeń GUIX jest pusta, ta usługa zawiesza wątek wywołujący do momentu nadejścia nowych zdarzeń w kolejce zdarzeń GUIX.

### <a name="parameters"></a>Parametry

- **Brak**

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne uruchomienie systemu
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Start GUIX. */
status = gx_system_start();

/* If status is GX_SUCCESS . GUIX has been started. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_string_get"></a>gx_system_string_get

Pobierz ciąg

### <a name="prototype"></a>Prototype

```C
UINT gx_system_string_get(
    GX_RESOURCE_ID string_id,
    GX_CHAR **return_string);
```

### <a name="description"></a>Opis

Ta usługa Pobiera ciąg dla określonego identyfikatora zasobu przy użyciu pierwszego zdefiniowanego ekranu i aktualnie aktywnego języka. Ta funkcja została uznana za przestarzałą na rzecz gx_display_string_get. Wszystkie nowe aplikacje powinny używać gx_display_string_get.

### <a name="parameters"></a>Parametry

- **string_id**: Identyfikator zasobu ciągu
- **return_string**: wskaźnik do wskaźnika elementu docelowego ciągu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) pomyślny ciąg Get
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR (0x07)**: nieprawidłowy wskaźnik
- **GX_INVALID_RESOURCE_ID**: (0X33) Nieprawidłowy identyfikator zasobu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Get the string associated with MY_STRING_ID. */

status = gx_system_string_get(MY_STRING_RESOURCE_ID, &my_string);

/* If status is GX_SUCCESS the string is contained in “my_string”.
*/
```

### <a name="see-also"></a>Zobacz też

- gx_display_string_get
- gx_display_string_table_get
- gx_display_language_table_set

## <a name="gx_system_string_table_get"></a>gx_system_string_table_get

Pobiera tabelę ciągów

### <a name="prototype"></a>Prototype

```C
UINT gx_system_string_table_get(
    GX_UBYTE language,
    GX_CHAR ***string_table,
    UINT *get_size);
```

### <a name="description"></a>Opis

Ta usługa pobiera tabelę ciągów dla żądanego języka z pierwszego ekranu. Ta funkcja została uznana za przestarzałą na rzecz gx_display_string_table_get. Wszystkie nowe aplikacje powinny używać gx_display_string_table_get.

### <a name="parameters"></a>Parametry

- **Język**: indeks języka
- **string_table**: wskaźnik do miejsca do magazynowania w wskaźniku tabeli ciągów lub wartości null, jeśli obiekt wywołujący nie musi uzyskać wskaźnika do tabeli ciągów.
- **get_size**: wskaźnik do magazynu dla liczby ciągów w tabeli ciągów lub wartości null, jeśli obiekt wywołujący nie musi uzyskać liczby ciągów w tabeli ciągów.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne pobieranie tabeli ciągów
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Get the string table. */

CHAR **my_string_table; UINT table_size;

status = gx_system_string_table_get(LANGUAGE_ID_ENGLISH,
    &my_string_table, &table_size);

/* If status is GX_SUCCESS . the pointer to the string table has
been obtained. */
```

### <a name="see-also"></a>Zobacz też

- gx_display_string_table_get
- gx_display_string_get
- gx_display_active_language_set
- gx_display_language_table_set

## <a name="gx_system_string_width_get"></a>gx_system_string_width_get

Pobierz szerokość ciągu (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_system_string_width_get(
    GX_FONT *font, GX_CHAR *string,
    INT string_length,
    GX_VALUE *return_width);
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_system_string_width_get_ext ().

Ta usługa oblicza szerokość wyświetlanego ciągu w pikselach przy użyciu określonej czcionki. Jeśli parametr string_length jest >= 0, obliczenia zawierają tylko liczbę żądań znaków. Jeśli string_length parametr ma wartość-1, cały ciąg do terminatora NULL jest używany w obliczeniach.

### <a name="parameters"></a>Parametry

- **Font**: wskaźnik do czcionki ciągu
- **String**: wskaźnik do ciągu
- **string_length**: długość ciągu
- **return_width**: miejsce docelowe dla szerokości ciągu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) pomyślna szerokość ciągu Get
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_FONT**: (0X16) Nieprawidłowa czcionka
- **GX_INVALID_STRING_LENGTH**: (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Get the string width of “my_string”. */

status = gx_system_string_width_get(&my_font, &my_string,
    strlen(my_string), &my_width);

/* If status is GX_SUCCESS . “my_width” contains the string width.
*/
```

### <a name="see-also"></a>Zobacz też

- gx_system_string_width_get_ext

## <a name="gx_system_string_width_get_ext"></a>gx_system_string_width_get_ext

Pobierz szerokość ciągu

### <a name="prototype"></a>Prototype

```C
UINT gx_system_string_width_get_ext(
    GX_FONT *font,
    GX_STRING *string,
    GX_VALUE *return_width);
```

### <a name="description"></a>Opis

Ta usługa oblicza szerokość wyświetlanego ciągu w pikselach przy użyciu określonej czcionki.

### <a name="parameters"></a>Parametry

- **Font**: wskaźnik do czcionki ciągu
- **String**: wskaźnik do ciągu
- **return_width**: miejsce docelowe dla szerokości ciągu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) pomyślna szerokość ciągu Get
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR**: 0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_FONT**: (0X16) Nieprawidłowa czcionka
- **GX_INVALID_STRING_LENGTH**: (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING my_string; my_string.gx_string_ptr = “Monday”;

my_string.gx_string_length = strlen(my_string.gx_string_ptr);

/* Get the string width of “my_string”. */

status = gx_system_string_width_get_ext(&my_font,
    &my_string, &my_width);

/* If status is GX_SUCCESS . “my_width” contains the string width.
*/
```

### <a name="see-also"></a>Zobacz też

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_timer_start"></a>gx_system_timer_start

Uruchom czasomierz

### <a name="prototype"></a>Prototype

```C
UINT gx_system_timer_start(
    GX_WIDGET *owner, 
    UINT timer_id,
    UINT initial_ticks,
    UINT reschedule_ticks);
```

### <a name="description"></a>Opis

Ta usługa uruchamia czasomierz dla określonego widżetu. GX_MAX_ACTIVE_TIMERS stała definiuje maksymalną obsługiwaną liczbę aktywnych czasomierzy. Domyślnym ustawieniem tej wartości jest 32.

### <a name="parameters"></a>Parametry

- **Owner**: wskaźnik do bloku kontrolki elementu widget
- **timer_id**: Identyfikator czasomierza
- **initial_ticks**: początkowe cykle wygasania
- **reschedule_ticks**: okresowe cykle wygasania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne uruchomienie czasomierza
- **GX_OUT_OF_TIMERS**: (0X04) nie więcej czasomierzy
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget
- Wartości czasomierza **GX_INVALID_VALUE**: (0x22) są nieprawidłowe

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Start a periodic timer for the widget “my_widget”. */
status = gx_system_timer_start(&my_widget, MY_TIMER_ID, 10, 20);

/* If status is GX_SUCCESS . the timer for “my_widget” has been
started. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_timer_stop"></a>gx_system_timer_stop

Zatrzymaj czasomierz

### <a name="prototype"></a>Prototype

```C
UINT gx_system_timer_stop(
    GW_WIDGET *owner, 
    UINT timer_id);
```

### <a name="description"></a>Opis

Ta usługa przerywa czasomierz z określoną timer_id skojarzoną z widżetem wywołującym. Aby zatrzymać wszystkie czasomierze połączone z określonym widżetem, aplikacja może przekazać wartość timer_id równą 0.

### <a name="parameters"></a>Parametry

- **Owner**: wskaźnik do bloku kontrolki elementu widget
- **timer_id**: Identyfikator czasomierza lub 0 dla wszystkich czasomierzy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne zatrzymanie czasomierza
- Nie znaleziono identyfikatora czasomierza **GX_NOT_FOUND**: (0x09)
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Stop the periodic timer for the widget “my_widget”. */
status = gx_system_timer_stop(&my_widget, MY_TIMER_ID);

/* If status is GX_SUCCESS . the timer for “my_widget” has been
stopped. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_event_fold
- gx_system_focus_claim
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_pen_configure
- gx_system_version_string_get
- gx_system_widget_find

## <a name="gx_system_version_string_get"></a>gx_system_version_string_get

Pobierz ciąg wersji biblioteki GUIX (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_system_version_string_get(GX_CHAR **version);
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_system_version_string_get_ext ().

Ta usługa Pobiera ciąg wersji biblioteki GUIX.

### <a name="parameters"></a>Parametry

- **Version**: wskaźnik zwraca wartość ciągu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie pobrał ciąg wersji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR *version;

/* get the library version string. */

status = gx_system_verrsion_string_get(&version);
```

### <a name="see-also"></a>Zobacz też

- gx_system_version_string_get_ext ()

## <a name="gx_system_version_string_get_ext"></a>gx_system_version_string_get_ext

Pobierz ciąg wersji biblioteki GUIX

### <a name="prototype"></a>Prototype

```C
UINT gx_system_version_string_get(GX_STRING *version);
```

### <a name="description"></a>Opis

Ta usługa Pobiera ciąg wersji biblioteki GUIX.

### <a name="parameters"></a>Parametry

- **Version**: wskaźnik zwraca wartość ciągu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie pobrał ciąg wersji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_STRING_LENGTH**: (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING version;

/* get the library version string. */

status = gx_system_version_string_get_ext(&version);
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_widget_find

## <a name="gx_system_widget_find"></a>gx_system_widget_find

Znajdź widżet

### <a name="prototype"></a>Prototype

```C
UINT gx_system_widget_find(
    USHORT widget_id,
    INT search_level, 
    GX_WIDGET **return_search_result);
```

### <a name="description"></a>Opis

Ta usługa wyszukuje określony identyfikator widżetu. W przeciwieństwie do gx_widget_find (), ta funkcja przeszukuje elementy podrzędne wszystkich okien głównych zdefiniowanych w systemie, co oznacza, że jest to wyczerpujące wyszukiwanie wszystkich widocznych elementów widget. Jeśli znasz element nadrzędny widżetu, którego szukasz, Użyj zamiast niego gx_widget_find ().

### <a name="parameters"></a>Parametry

- **widget_id**: Identyfikator elementu widget do wyszukania
- **search_level**: definiuje cykliczny poziom zagnieżdżenia, do którego są przeszukiwane podrzędne elementy widget. Jeśli ta wartość wynosi 0, przeszukiwane są tylko natychmiastowe elementy podrzędne każdego okna głównego. Jeśli ta wartość jest GX_SEARCH_DEPTH_INFINITE, funkcja zagnieżdża wszystkie elementy podrzędne wyszukiwania dla żądanego identyfikatora widżetu. Dla każdej innej wartości > 0 poziom wyszukiwania definiuje, jak głęboko zagnieżdżona ta funkcja będzie przeszukiwać żądany identyfikator widżetu.
- **return_search_result**: znaleziono wskaźnik do miejsca docelowego dla elementu widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne wyszukiwanie widżetu
- **GX_NOT_FOUND**: (0x09) nie znaleziono identyfikatora elementu widget
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Search recursively from the top level widget for the widget with
ID of MY_WIDGET_ID. */

status = gx_system_widget_find(MY_WIDGET_ID,
    GX_SEARCH_DEPTH_INFINITE,
    &my_widget);

/* If status is GX_SUCCESS . the search was successful and
“my_widget” contains the pointer to the widget. */
```

### <a name="see-also"></a>Zobacz też

- gx_system_active_language_set
- gx_system_canvas_refresh
- gx_system_dirty_mark
- gx_system_dirty_partial_add
- gx_system_draw_context_get
- gx_system_event_fold
- gx_system_event_send
- gx_system_focus_claim
- gx_system_initialize
- gx_system_initialize
- gx_system_language_table_get
- gx_system_language_table_set
- gx_system_memory_allocator_set
- gx_system_scroll_appearance_get
- gx_system_scroll_appearance_get
- gx_system_start
- gx_system_string_get
- gx_system_string_table_get
- gx_system_string_width_get
- gx_system_timer_start
- gx_system_timer_stop
- gx_system_pen_configure
- gx_system_version_string_get

## <a name="gx_text_button_create"></a>gx_text_button_create

Przycisk tworzenia tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_create(
    GX_TEXT_BUTTON *text_button,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    GX_RESOURCE_ID text_id, 
    ULONG style,
    USHORT text_button_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widżet przycisku tekstu.

GX_TEXT_BUTTON pochodzi od GX_BUTTON i obsługuje wszystkie gx_button usługi interfejsu API.

### <a name="parameters"></a>Parametry

- **text_button**: wskaźnik do bloku kontrolki przycisku tekstowego
- **name**: logiczna nazwa przycisku tekstowego
- **Parent**: wskaźnik do elementu nadrzędnego widget przycisku
- **text_id**: Identyfikator zasobu tekstu
- **styl**: styl przycisku tekstu. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **text_button_id**: zdefiniowany przez aplikację identyfikator przycisku tekstu
- **rozmiar**: rozmiar przycisku

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne utworzenie przycisku tekstu
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_ALREADY_CREATED**: (0x13) — element widget został już utworzony
- **GX_INVALID_SIZE**: (0X19) Nieprawidłowy rozmiar bloku kontrolki widgetu
- **GX_INVALID_WIDGET**: (0X12) element widget elementu nadrzędnego jest nieprawidłowy


### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_TEXT_BUTTON my_text_button;

GX_RECTANGLE size;

/* Define widget size. */

gx_utility_rectangle_define(&size, 0, 0, 100, 100);

/* Create text button “my_text_button”. */

status = gx_text_button_create(&my_text_button, "my text button",
    &my_parent_window, MY_TEXT_RESOURCE_ID,
    GX_STYLE_BUTTON_TOGGLE, MY_TEXT_BUTTON_ID, &size);

/* If status is GX_SUCCESS, the text button “my_text_button” was
created. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_color_set
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_draw"></a>gx_text_button_draw

Przycisk rysowania tekstu

### <a name="prototype"></a>Prototype

```C
VOID gx_text_button_draw(GX_TEXT_BUTTON *button);
```

### <a name="description"></a>Opis

Ta usługa rysuje przycisk tekst. Ta usługa jest zwykle wywoływana wewnętrznie podczas odświeżania kanwy, ale może być również wywoływana z funkcji niestandardowego rysowania przycisków tekstowych.

### <a name="parameters"></a>Parametry

- **Button**: wskaźnik do bloku kontrolki przycisku tekstowego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom text button draw function. */

VOID my_text_button_draw(GX_TEXT_BUTTON *text_button)
{
    /* Call default text button draw. */
    gx_text_button_draw(text_button);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_event_process
- gx_text_button_color_set
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_event_process"></a>gx_text_button_event_process


Zdarzenie przycisku tekstu procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego przycisku tekstu. Ta usługa powinna być wywoływana jako domyślna procedura obsługi zdarzeń za pomocą wszelkich funkcji niestandardowego przetwarzania zdarzeń tekstowych.

### <a name="parameters"></a>Parametry

- **text_button** Wskaźnik do bloku kontrolki przycisku tekstowego
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia dotyczącego prawidłowego przycisku tekstu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic text button event processing as part of custom event processing function. */

UINT custom_text_button_event_process(GX_TEXT_BUTTON *text_button, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default text button event processing */
        status = gx_text_button_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_color_set
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_font_set"></a>gx_text_button_font_set

Ustaw przycisk czcionki na tekst

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_font_set(
    GX_TEXT_BUTTON *button,
    GX_RESOURCE_ID font_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje czcionkę do określonego przycisku.

### <a name="parameters"></a>Parametry

- **Button**: wskaźnik do bloku kontrolki przycisku tekstowego
- **font_id**: Identyfikator zasobu czcionki

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił czcionkę
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the text button with the font ID MY_FONT. */
status = gx_text_button_font_set(&my_text_button, MY_FONT);

/* If status is GX_SUCCESS, the font of the text button
“my_text_button” was set to MY_FONT. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create
- gx_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_color_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_color_set"></a>gx_text_button_text_color_set

Kolor przycisku ustawiania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_color_set(
    GX_TEXT_BUTTON *text_button,
    GX_RESOURCE_ID normal_text_color_id,
    GX_RESOURCE_ID selected_text_color_id,
    GX_RESOURCE_ID disabled_text_color_id);
```

### <a name="description"></a>Opis

Ta usługa ustawia kolor przycisku tekstu.

### <a name="parameters"></a>Parametry

- **text_button**: wskaźnik do bloku kontrolki przycisku tekstowego
- **normal_text_color_id**: Identyfikator zasobu normalnego tekstu. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **selected_text_color_id**: Identyfikator zasobu zaznaczonego tekstu. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **disabled_text_color_id**: Identyfikator zasobu koloru dla wyłączonego tekstu. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) ustawiono kolor przycisku tekstu
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the color of the text button “my_text_button”. */
status = gx_text_button_text_color_set(&my_text_button,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS, the text color of “my_text_button” was
set. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_get
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_draw"></a>gx_text_button_text_draw

Funkcja obsługi do rysowania tekstu przycisku

### <a name="prototype"></a>Prototype

```C
VOID gx_text_button_text_draw(GX_TEXT_BUTTON *text_button);
```

### <a name="description"></a>Opis

Ta funkcja obsługi rysuje część tekstową przycisku tekstu. Ta funkcja jest wywoływana wewnętrznie przez gx_text_button_draw i jest udostępniana jako osobny interfejs API jako wygoda dla aplikacji, które definiują funkcję rysowania niestandardowego przycisku. Aplikacje, które chcą dostosować Rysowanie w tle przycisków, mogą zapewnić swoją niestandardową funkcję rysowania i wywoływać usługę gx_text_button_text_draw jako część niestandardowego rysunku, aby narysować tekst przycisku w tle.

### <a name="parameters"></a>Parametry

- **text_button**: wskaźnik do bloku kontrolki przycisku tekstowego

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Define a custom drawing function */

VOID my_button_draw(GX_TEXT_BUTTON *button)
{
    /* Insert code here to draw button background */

    /* Call support function to do text drawing */
    gx_text_button_text_draw(button);

    /* Draw child widgets */
    gx_widget_children_draw((GX_WIDGET *) button);
}
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_get"></a>gx_text_button_text_get

Pobierz tekst z przycisku tekstu (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_get(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR **return_text);
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_text_button_text_get_ext ().

Ta usługa Pobiera określony ciąg z przycisku tekstu.

### <a name="parameters"></a>Parametry

- **text_button**: wskaźnik do bloku kontrolki przycisku tekstowego
- **return_text**: wskaźnik do ciągu pobranego z przycisku tekstu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie Pobiera tekst z przycisku
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CHAR *string;

/* Get the string from the text button “my_text_button”. */
status = gx_text_button_text_get(&my_text_button, &string);

/* If status is GX_SUCCESS, the string pointer from
“my_text_button” is retrieved and stored in string. */
```

### <a name="see-also"></a>Zobacz też

- gx_text_button_text_get_ext

## <a name="gx_text_button_text_get_ext"></a>gx_text_button_text_get_ext

Pobierz tekst z przycisku tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_get_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *return_string);
```

### <a name="description"></a>Opis

Ta usługa Pobiera określony ciąg z przycisku tekstu.

### <a name="parameters"></a>Parametry

- **text_button**: wskaźnik do bloku kontrolki przycisku tekstowego
- **return_string**: wskaźnik do ciągu pobranego z przycisku tekstu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie Pobiera tekst z przycisku
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING string;

/* Get the string from the text button “my_text_button”. */
status = gx_text_button_text_get_ext(&my_text_button, &string);

/* If status is GX_SUCCESS, the string pointer and length from
“my_text_button” is retrieved and stored in string. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_set
- gx_text_button_text_id_set

## <a name="gx_text_button_text_id_set"></a>gx_text_button_text_id_set

Ustaw identyfikator zasobu tekstowego na przycisk tekst

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_id_set(
    GX_TEXT_BUTTON *text_button,
    RESOURCE_ID string_id);
```

### <a name="description"></a>Opis

Ta usługa Ustawia określony identyfikator zasobu ciągu na przycisk tekst.

### <a name="parameters"></a>Parametry

- **text_button**: wskaźnik do bloku kontrolki przycisku tekstowego
- **string_id**: Identyfikator zasobu ciągu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił identyfikator zasobu ciągu na przycisk tekstowy
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget
- **GX_INVALID_RESOURCE_ID**: (0x33) Nieprawidłowy identyfikator ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the string ID ”MY_STRING_ID” to the text button
“my_text_button”. */

status = gx_text_button_text_id_set(&my_text_button,
    MY_STRING_ID);

/* If status is GX_SUCCESS, the string ID MY_STRING_ID was set to
“my_text_button”. */
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get

## <a name="gx_text_button_text_set"></a>gx_text_button_text_set

Przypisywanie tekstu do przycisku tekstu (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_set(
    GX_TEXT_BUTTON *text_button,
    GX_CHAR *text);
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_text_button_text_set_ext ().

Ta usługa przypisuje określony ciąg do przycisku tekstu. Jeśli element widget text_button został utworzony z GX_STYLE_TEXT_COPY stylu, widżet tworzy prywatną kopię ciągu tekstowego przypisanego. Jeśli GX_STYLE_TEXT_COPY nie jest aktywny, widżet nie tworzy prywatnej kopii ciągu przychodzącego, w związku z czym ciąg musi być statycznie lub globalnie przydzielony, tj. nie może to być automatyczna lub Tymczasowa zmienna.

### <a name="parameters"></a>Parametry

- **text_button**: wskaźnik do bloku kontrolki przycisku tekstowego
- **Text**: wskaźnik do ciągu ZAKOŃCZONEGO wartością null

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił tekst na przycisk
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget
- **GX_SYSTEM_MEMORY_ERROR**: program przydzielania pamięci (0x30) nie został zdefiniowany lub alokacja pamięci nie powiodła się
- **GX_INVALID_STRING_LENGTH**: (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the string “my string” to the text button “my_text_button”.
*/

status = gx_text_button_text_set(&my_text_button, “my string”);

/* If status is GX_SUCCESS, the string “my_text_button” was set.
*/
```

### <a name="see-also"></a>Zobacz też

- gx_text_button_event_process
- gx_text_button_text_set_ext
- gx_text_button_text_id_set

## <a name="gx_text_button_text_set_ext"></a>gx_text_button_text_set_ext

Przypisywanie tekstu do przycisku tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_text_button_text_set_ext(
    GX_TEXT_BUTTON *text_button,
    GX_STRING *string);
```

### <a name="description"></a>Opis

Ta usługa przypisuje określony ciąg do przycisku tekstu. Jeśli element widget text_button został utworzony z GX_STYLE_TEXT_COPY stylu, widżet tworzy prywatną kopię ciągu tekstowego przypisanego. Jeśli GX_STYLE_TEXT_COPY nie jest aktywny, widżet nie tworzy prywatnej kopii ciągu przychodzącego, w związku z czym ciąg musi być statycznie lub globalnie przydzielony, tj. nie może to być automatyczna lub Tymczasowa zmienna.

### <a name="parameters"></a>Parametry

- **text_button**: wskaźnik do bloku kontrolki przycisku tekstowego
- **String**: wskaźnik do zmiennej GX_STRING

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił tekst na przycisk
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget
- **GX_SYSTEM_MEMORY_ERROR**: program przydzielania pamięci (0x30) nie został zdefiniowany lub alokacja pamięci nie powiodła się
- **GX_INVALID_STRING_LENGTH**: (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING new_string; new_string.gx_string_ptr = “Monday”;

new_string.gx_string_length = strlen(new_string.gx_string_ptr);

/* Assign the string “new_string” to the text button
“my_text_button”. */

status = gx_text_button_text_set_ext(&my_text_button, &new_string);

/* If status is GX_SUCCESS, the string “my_text_button” was set.
*/
```

### <a name="see-also"></a>Zobacz też

- gx_button_background_draw
- gx_button_create
- gx_button_deselect
- gx_button_draw
- gx_button_event_process
- gx_button_select
- gx_icon_button_create, x_pixelmap_button_create
- gx_pixelmap_button_draw
- gx_text_button_create
- gx_text_button_draw
- gx_text_button_event_process
- gx_text_button_font_set
- gx_text_button_text_color_set
- gx_text_button_text_get
- gx_text_button_text_id_set

## <a name="gx_text_input_cursor_blink_interval_set"></a>gx_text_input_cursor_blink_interval_set

Ustaw interwał migania kursora

### <a name="prototype"></a>Prototype

```C
UINT gx_text_input_cursor_blink_interval_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE blink_interval);
```

### <a name="description"></a>Opis

Ta usługa ustawia wartość interwału migania kursora.

### <a name="parameters"></a>Parametry

- **cursor_input** Blok kontrolny kursora
- **blink_interval** Wartość do ustawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił interwał migania kursora
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE**: (0x22) wartość interwału migania jest nieprawidłowa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set the blink interval value of “input_cursor” to 2. */
status = gx_text_input_cursor_blink_interval_set(input_cursor, 2);

/* If status is GX_SUCCESS, the blink interval value of
“input_cursor” has been successfully set to 2. */
```

### <a name="see-also"></a>Zobacz też

- gx_text_input_cursor_height_set
- gx_text_input_cursor_width_set

## <a name="gx_text_input_cursor_height_set"></a>gx_text_input_cursor_height_set

Ustaw wysokość kursora

### <a name="prototype"></a>Prototype

```C
UINT gx_text_input_cursor_height_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE height);
```

### <a name="description"></a>Opis

Ta usługa Ustawia wysokość kursora.

### <a name="parameters"></a>Parametry

- **cursor_input**: blok kontrolny kursora
- **wysokość** Wartość do ustawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawiono wysokość kursora
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- Wartość wysokości **GX_INVALID_VALUE**: (0x22) jest nieprawidłowa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set height value of “input_cursor”. */
status = gx_text_input_cursor_height_set(&input_cursor, 15);

/* If status is GX_SUCCESS, the height value of “input_curosr” has
been successfully set to 15. */
```

### <a name="see-also"></a>Zobacz też

- gx_text_input_cursor_blink_interval_set
- gx_text_input_cursor_width_set

## <a name="gx_text_input_cursor_width_set"></a>gx_text_input_cursor_width_set

Ustaw szerokość kursora

### <a name="prototype"></a>Prototype

```C
UINT gx_text_input_cursor_blink_width_set(
    GX_TEXT_INPUT_CURSOR *cursor_input,
    GX_UBYTE *width);
```

### <a name="description"></a>Opis

Ta usługa ustawia szerokość kursora.

### <a name="parameters"></a>Parametry

- **cursor_input**: blok kontrolny kursora
- **Width**: wartość do ustawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił szerokość kursora
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_VALUE**: (0x22) Nieprawidłowa wartość szerokości

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_TEXT_INPUT_CURSOR *input_cursor;

/* Pointer the input cursor to the cursor instance of single/multi
line text input widget. */

input_cursor = &sl_input.gx_single_line_text_input_cursor_instance;

/* Set width of “input_curosr” to 2. */

status = gx_text_input_cursor_blink_width_set(&input_cursor, 2);

/* If status is GX_SUCCESS, the width of “input_cursor” has been
successfully set to 2. */
```

### <a name="see-also"></a>Zobacz też

- gx_text_input_cursor_blink_interval_set
- gx_text_input_cursor_height_set

## <a name="gx_text_scroll_wheel_callback_set"></a>gx_text_scroll_wheel_callback_set

Przypisywanie funkcji wywołania zwrotnego typu Text kółka przewijania (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_wheel_callback_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *(*callback)(GX_TEXT_SCROLL_WHEEL *, int));
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_text_scroll_wheel_callback_set_ext ().

Ta usługa przypisuje funkcję wywołania zwrotnego, do którego zostanie wywołane kółko przewijania typu tekstowego, aby określić ciąg tekstowy, który ma być wyświetlany w każdym wierszu kółka przewijania.

W przypadku GX_NUMERIC_SCROLL_WHEEL i GX_STRING_SCROLL_WHEEL są udostępniane domyślne funkcje wywołania zwrotnego, a aplikacja nie musi wprowadzać żadnych zmian w celu korzystania z tych domyślnych implementacji.

Ten interfejs API jest dostępny, aby umożliwić aplikacji dostosowanie formatowania lub innych parametrów ciągu, który jest wyświetlany w każdym wierszu widżetu przewijania.

Funkcja wywołania zwrotnego będzie odbierać jako wskaźnik wejściowy do bloku sterowania kółkiem przewijania i wyświetlany numer wiersza. Funkcja powinna zwrócić wskaźnik do ciągu tekstowego.

### <a name="parameters"></a>Parametry

- **koło** Adres bloku formantu pokrętła przewijania ciągu
- **wywołanie zwrotne** Wskaźnik do funkcji wywołania zwrotnego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił wywołanie zwrotne
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_TEXT_SCROLL_WHEEL wheel;

GX_CHAR string_buffer[20];

GX_CHAR *my_wheel_callback(GX_TEXT_SCROLL_WHEEL *wheel, int row)
{
    /* Just for an example, return row number as string for rows
    >= 0, and return text “Invalid” otherwise */
    if (row >= 0)
    {
        gx_utility_ltoa(row, string_buffer, 20);
    }
    else
    {
        return(“Invalid”);
    }
}

gx_text_scroll_wheel_create(&wheel, “my wheel”, root, 10,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|ID_MY_WHEEL, &size);

status = gx_text_scroll_wheel_callback_set(&wheel,
    my_wheel_callback);

/* If status is GX_SUCCESS, the scroll whell callback function has
been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_callback_set_ext"></a>gx_text_scroll_wheel_callback_set_ext

Przypisywanie funkcji wywołania zwrotnego typu Text kółka przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_wheel_callback_set_ext(
    GX_TEXT_SCROLL_WHEEL *wheel,
    UINT *(*callback)(GX_TEXT_SCROLL_WHEEL *, int, GX_STRING *));
```

### <a name="description"></a>Opis

Ta usługa przypisuje funkcję wywołania zwrotnego, do którego zostanie wywołane kółko przewijania typu tekstowego, aby określić ciąg tekstowy, który ma być wyświetlany w każdym wierszu kółka przewijania.

W przypadku GX_NUMERIC_SCROLL_WHEEL i GX_STRING_SCROLL_WHEEL są udostępniane domyślne funkcje wywołania zwrotnego, a aplikacja nie musi wprowadzać żadnych zmian w celu korzystania z tych domyślnych implementacji.

Ten interfejs API jest dostępny, aby umożliwić aplikacji dostosowanie formatowania lub innych parametrów ciągu, który jest wyświetlany w każdym wierszu widżetu przewijania.

Funkcja wywołania zwrotnego będzie odbierać jako wskaźnik wejściowy do bloku sterowania kółkiem przewijania i wyświetlany numer wiersza. Funkcja powinna zwrócić wskaźnik do ciągu tekstowego.

### <a name="parameters"></a>Parametry

- **koło** Adres bloku formantu pokrętła przewijania ciągu
- **wywołanie zwrotne** Wskaźnik do funkcji wywołania zwrotnego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił wywołanie zwrotne
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_TEXT_SCROLL_WHEEL wheel;

GX_CHAR string_buffer[20];

UINT *my_wheel_callback(GX_TEXT_SCROLL_WHEEL *wheel, int row,
    GX_STRING *return_string)
{
    /* Just for an example, return row number as string for rows
    >= 0, and return text “Invalid” otherwise */
    if (row >= 0)
    {
        gx_utility_ltoa(row, string_buffer, 20);
        return_string->gx_string_ptr = string_buffer;
        return_string->gx_string_length = strlen(string_buffer);
    }
    else
    {
        return_string->gx_string_ptr = “Invalid”;
        return_string->gx_string_length = strlen(“Invalid”);
    }

    return GX_SUCCESS;
}

gx_text_scroll_wheel_create(&wheel, “my wheel”, root, 10,
    GX_STYLE_ENABLED|GX_STYLE_TEXT_CENTER|GX_STYLE_TRANSPARENT|
    GX_STYLE_WRAP|ID_MY_WHEEL, &size);

status = gx_text_scroll_wheel_callback_set_ext(&wheel,
    my_wheel_callback);

/* If status is GX_SUCCESS, the scroll whell callback function has
been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_create"></a>gx_text_scroll_wheel_create

Tworzenie kółka przewijania tekstu

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_wheel_create(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    ULONG style, 
    USHORT Id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy kółko przewijania tekstu. Kółko przewijania tekstu jest podstawowym elementem widget dla elementów widget GX_STRING_SCROLL_WHEEL i GX_NUMERIC_SCROLL_WHEEL. Ta funkcja jest wywoływana wewnętrznie przez gx_string_scroll_wheel_create i gx_numeric_scroll_wheel_create i jest udostępniana jako osobny interfejs API jako wygoda dla aplikacji, które definiują niestandardowy widżet kółka przewijania.

### <a name="parameters"></a>Parametry

- **koło**: adres bloku formantu pokrętła przewijania tekstu
- **name**: Nazwa widżetu zdefiniowanego przez aplikację
- **element nadrzędny**: koło lub GX_NULL
- **total_rows**: łączną liczbę wierszy do prezentowania użytkownikowi
- **styl**: wymagane flagi stylu
- **ID**: flagi stylu koła zdefiniowanego przez aplikację
- **rozmiar**: początkowy rozmiar kółka przewijania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie utworzono koło przewijania tekstu
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_ALREADY_CREATED**: (0x13) — element widget został już utworzony
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget


### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Define a custom scroll wheel widget. */
typedef MY_SCROLL_WHEEL_STRUCT
{
    GX_TEXT_SCROLL_WHEEL text_scroll_wheel;

    /* Add custom members here. */

} MY_SCROLL_WHEEL;

MY_SCROLL_WHEEL my_scroll_wheel;

UINT my_scroll_wheel_create(MY_SCROLL_WHEEL *wheel,
    GX_CONST GX_CHAR *name, GX_WIDGET *parent,
    INT total_rows, ULONG style, USHORT Id,
    GX_CONST GX_RECTANGLE *size)
{
    /* Call base creation. */
    status = gx_text_scroll_wheel_create(
        &wheel.text_scroll_wheel,
        ”my_text_scroll_wheel”, GX_NULL, 7,
        GX_STYLE_ENABLED, ID_MY_SCROLL_WHEEL, &size);

    if (status == GX_SUCCESS)
    {
        /* Add custom initialization here. */
        if(parent)
        {
            gx_widget_link(parent, (GX_WIDGET *)wheel);
        }
    }
}
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_string_scroll_wheel_string_id_list_set
- gx_string_scroll_wheel_string_list_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_draw"></a>gx_text_scroll_wheel_draw

Rysowanie kółka przewijania tekstu

### <a name="prototype"></a>Prototype

```C
VOID gx_text_scroll_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel);
```

### <a name="description"></a>Opis

Jest to domyślna funkcja rysowania dla wszystkich typów kół na podstawie GX_TEXT_SCROLL_WHEEL. Ta funkcja może zostać przesłonięta przez aplikacje, które wymagają dostosowania wyglądu kółka przewijania tekstu.

GX_STRING_SCROLL_WHEEL i GX_NUMERIC_SCROLL_WHEEL są oparte na lub pochodzące od GX_TEXT_SCROLL_WHEEL.

### <a name="parameters"></a>Parametry

- **koło**: adres bloku formantu pokrętła przewijania ciągu

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom wheel draw function. */
UINT my_wheel_draw(GX_TEXT_SCROLL_WHEEL *wheel)
{
    /* Perform default drawing */
    gx_text_scroll_wheel_draw(wheel);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_event_process"></a>gx_text_scroll_wheel_event_process


Zdarzenie kółka przewijania tekstu procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego kółka przewijania tekstu. Ta usługa powinna być wywoływana jako domyślna procedura obsługi zdarzeń przez dowolne funkcje przetwarzania zdarzeń niestandardowego kółka przewijania tekstu.

### <a name="parameters"></a>Parametry

- **koło** Blok sterowania przesuwaniem wskaźnika do tekstu
- **event_ptr** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Proces zdarzenia kółka przewijania tekstu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic text scroll wheel event processing as part of custom event processing function. */

UINT custom_text_scroll_wheel_event_process(GX_TEXT_SCROLL_WHEEL *wheel, GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;

    default:
        /* Pass all other events to the default text scroll wheel event processing */
        status = gx_text_scroll_wheel_event_process(wheel, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_font_set
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_font_set"></a>gx_text_scroll_wheel_font_set

Przypisz czcionki używane do rysowania wierszy przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_font_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_font, 
    GX_RESOURCE_ID selected_font);
```

### <a name="description"></a>Opis

Przypisz czcionki Użyj, aby narysować tekst widżetu tekstowego kółka przewijania tekstu.

### <a name="parameters"></a>Parametry

- **koło**: adres bloku formantu pokrętła przewijania ciągu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie przypisać czcionkę kółka
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_NUMERIC_SCROLL_WHEEL wheel;

status = gx_text_scroll_wheel_font_set(&wheel,
    GX_FONT_ID_WHEEL_NORMAL,
    GX_FONT_ID_WHEEL_SELECTED);

/* If status is GX_SUCCESS, the scroll wheel fonts have been assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_text_color_set

## <a name="gx_text_scroll_wheel_text_color_set"></a>gx_text_scroll_wheel_text_color_set

Przypisywanie kolorów używanych do rysowania wierszy przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_text_scroll_wheel_text_color_set(
    GX_TEXT_SCROLL_WHEEL *wheel,
    GX_RESOURCE_ID normal_text_color,
    GX_RESOURCE_ID selected_text_color,
    GX_RESOURCe_ID disabled_text_color);
```

### <a name="description"></a>Opis

Ta funkcja przypisuje kolory tekstu używane do rysowania wierszy przewijania tekstu.

### <a name="parameters"></a>Parametry

- **koło**: adres bloku formantu pokrętła przewijania ciągu
- **normal_text_color**: kolor używany do rysowania niezaznaczonych wierszy
- **selected_text_color**: kolor używany do rysowania zaznaczonego wiersza.
- **disabled_text_color**: kolor używany do rysowania tekstu dla wyłączonego widżetu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie przypisano kolor tekstu kółka przewijania
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING_SCROLL_WHEEL wheel;

UINT status = gx_text_scroll_wheel_text_color_set(&wheel,
    GX_COLOR_ID_NORMAL_TEXT,
    GX_COLOR_ID_SELECTED_TEXT,
    GX_COLOR_ID_DISABLED_TEXT);

/* If status is GX_SUCCESS, the colors used to draw the wheel text have been assigned. */
```

### <a name="see-also"></a>Zobacz też

- gx_numeric_scroll_wheel_create
- gx_numeric_scroll_wheel_range_set
- gx_scroll_wheel_create
- gx_scroll_wheel_event_process
- gx_scroll_wheel_gradient_alpha_set
- gx_scroll_wheel_row_height_set
- gx_scroll_wheel_selected_background_set
- gx_scroll_wheel_selected_get
- gx_scroll_wheel_selected_set
- gx_scroll_wheel_total_rows_set
- gx_text_scroll_wheel_callback_set
- gx_text_scroll_wheel_create
- gx_text_scroll_wheel_draw
- gx_text_scroll_wheel_event_process
- gx_text_scroll_wheel_font_set

## <a name="gx_tree_view_create"></a>gx_tree_view_create

Tworzenie widoku drzewa

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_create(
    GX_TREE_VIEW *tree,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent,
    ULONG style, 
    USHORT tree_view_id,
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy widok drzewa jako określony i kojarzy widok drzewa z podanym widżetem nadrzędnym. Akceptuje wszystkie typy widżetów jako element menu podrzędnego. Zaleca się używanie widżetu typu GX_MENU jako elementu podrzędnego menu.

GX_TREE_VIEW pochodzi od GX_WINDOW i obsługuje wszystkie gx_window usługi interfejsu API.

### <a name="parameters"></a>Parametry

- **drzewo**: wskaźnik do bloku kontrolki widoku drzewa
- **Nazwa**: Nazwa widoku drzewa
- **element nadrzędny**: wskaźnik do elementu nadrzędnego widget
- **styl**: styl elementu widget. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **menu_id**: zdefiniowany przez aplikację Identyfikator widoku drzewa
- **rozmiar**: rozmiar widoku drzewa

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne utworzenie widoku drzewa
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_ALREADY_CREATED**: (0x13) — element widget został już utworzony
- **GX_INVALID_SIZE**: (0X19) Nieprawidłowy rozmiar bloku kontrolki widgetu
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
status = gx_tree_view_create(&my_tree_view,
    “my_tree_view”, parent,
    GX_STYLE_ENABLED, MY_TREE_VIEW_ID,
    &size);

/* If status is GX_SUCCESS the tree view was successfully created. */
```

### <a name="see-also"></a>Zobacz też

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_draw"></a>gx_tree_view_draw

Rysuj widok drzewa

### <a name="prototype"></a>Prototype

```C
VOID gx_tree_view_draw(GX_TREE_VIEW *tree);
```

### <a name="description"></a>Opis

Ta usługa Rysuje określony widok drzewa. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest dostępna dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania dla widżetów niestandardowego widoku drzewa.

### <a name="parameters"></a>Parametry

- **drzewo** Wskaźnik do bloku kontrolki widoku drzewa

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom tree view draw function. */
UINT my_tree_view_draw(GX_TREE_VIEW *tree_view)
{
    /* Perform default drawing */
    gx_tree_view_draw(tree_view);

    /* Add custom drawing here */
}
```

### <a name="see-also"></a>Zobacz też

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_event_process"></a>gx_tree_view_event_process

Zdarzenie widoku drzewa procesów

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_event_process(
    GX_TREE_VIEW *tree, 
    GX_EVENT event_ptr);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla określonego widoku drzewa. Ta usługa powinna być wywoływana jako domyślna procedura obsługi zdarzeń przez wszystkie niestandardowe funkcje przetwarzania zdarzeń w widoku drzewa.

### <a name="parameters"></a>Parametry

- **drzewo**: wskaźnik do bloku kontrolki widoku drzewa
- **event_ptr**: wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) zdarzenie widoku drzewa procesu zakończone powodzeniem
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic tree view event processing as part of custom event
    processing function. */

UINT custom_tree_view_event_process(GX_TREE_VIEW *tree_view,
    GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default tree view
                event processing */
            status = gx_tree_view_event_process(tree_view, event);
            break;
    }
}
return status;
```

### <a name="see-also"></a>Zobacz też

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_indentation_set"></a>gx_tree_view_indentation_set

Ustawianie wcięć widoku drzewa

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_indentation_set(
    GX_TREE_VIEW *tree,
    GX_VALUE indentation);
```

### <a name="description"></a>Opis

Ta usługa Ustawia wcięcia widoku drzewa.

### <a name="parameters"></a>Parametry

- **drzewo**: wskaźnik do bloku kontrolki widoku drzewa
- **wcięcia**: wcięcie do ustawienia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił wcięcia widoku drzewa
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set tree view “my_tree” indentation to 10. */
status = gx_tree_view_indentation_set(&my_tree, 10);

/* If status is GX_SUCCESS the indentation of tree view “my_tree”
has been set to 10. */
```

### <a name="see-also"></a>Zobacz też

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixemlap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_position"></a>gx_tree_view_position

Elementy widoku drzewa pozycji

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_position(GX_TREE_VIEW *tree);
```

### <a name="description"></a>Opis

Elementy widoku drzewa pozycji usługi.

### <a name="parameters"></a>Parametry

- **drzewo**: wskaźnik do bloku kontrolki widoku drzewa

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie pozycjonowane elementy widoku drzewa
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Position tree view “my_tree” items. */
status = gx_tree_view_position(&my_tree);

/* If status is GX_SUCCESS the items of tree view “my_tree” has
been positioned. */
```

### <a name="see-also"></a>Zobacz też

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_root_line_color_set"></a>gx_tree_view_root_line_color_set

Ustaw kolor linii głównej widoku drzewa

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_root_line_color_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID color_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje kolor linii głównej widoku drzewa.

### <a name="parameters"></a>Parametry

- **drzewo**: wskaźnik do bloku kontrolki widoku drzewa
- **color_id**: Identyfikator zasobu koloru linii głównej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne Ustawianie koloru linii głównej
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set root line color for tree view “my_tree”. */

status = gx_tree_view_root_line_color_set(&my_tree,
    MY_ROOT LINE_COLOR_ID);

/* If status is GX_SUCCESS the root line color of the tree view
“my_tree” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_root_pixelmap_set"></a>gx_tree_view_root_pixelmap_set

Ustaw katalog główny widoku drzewa Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_root_pixelmap_set(
    GX_TREE_VIEW *tree,
    GX_RESOURCE_ID expand_map_id,
    GX_RESOURCE_ID collapse_map_id);
```

### <a name="description"></a>Opis

Ta usługa przypisuje rozszerzanie i zwijanie Pixelmap widoku drzewa.

### <a name="parameters"></a>Parametry

- **drzewo**: wskaźnik do bloku kontrolki widoku drzewa
- **expand_map_id**: Identyfikator zasobu dla rozwiń Pixelmap
- **collapse_map_id**: Identyfikator zasobu zwijania Pixelmap

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie ustawił katalog główny Pixelmap
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set root pixelmaps for tree view “my_tree”. */

status = gx_tree_view_root_pixelmap_set(&my_tree,
    MY_EXPAND_MAP_ID,
    MY_COLLAPSE_MAP_ID);

/* If status is GX_SUCCESS the root pixelmaps of tree view
“my_tree” has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_selected_get
- gx_tree_view_selected_set

## <a name="gx_tree_view_selected_get"></a>gx_tree_view_selected_get

Pobierz wybrany element

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_selected_get(
    GX_TREE_VIEW *tree,
    GX_WIDGET **selected);
```

### <a name="description"></a>Opis

Ta usługa Pobiera bieżący wybrany element widoku drzewa.

### <a name="parameters"></a>Parametry

- **drzewo**: wskaźnik do bloku kontrolki widoku drzewa
- **zaznaczone**: wskaźnik do wybranego wskaźnika widżetu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie pobrał wybrany element
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Retrieve selected item of tree view “my_tree”. */

GX_WIDGET *selected;

status = gx_tree_view_selected_get(&my_tree, &selected);

/* If status is GX_SUCCESS the selected item of tree view “my_tree”
has been retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_set

## <a name="gx_tree_view_selected_set"></a>gx_tree_view_selected_set

Ustaw wybrany element

### <a name="prototype"></a>Prototype

```C
UINT gx_tree_view_selected_set(
    GX_TREE_VIEW *tree,
    GX_WIDGET *selected);
```

### <a name="description"></a>Opis

Ta usługa ustawia wybrany element dla widoku drzewa.

### <a name="parameters"></a>Parametry

- **drzewo**: wskaźnik do bloku kontrolki widoku drzewa
- **zaznaczone**: wskaźnik do nowego wybranego elementu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) menu rysowania pomyślne
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET**: (0x12) nieprawidłowy element widget

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set selected item of tree view “my_tree” to “tree_view_item’. */
status = gx_tree_view_selected_set(&my_tree, &tree_view_item);

/* If status is GX_SUCCESS selected item of tree view “my_menu” has
been set to “tree_view_item”. */
```

### <a name="see-also"></a>Zobacz też

- gx_menu_draw
- gx_menu_insert
- gx_menu_remove
- gx_menu_text_draw
- gx_menu_text_offset_set
- gx_tree_view_create
- gx_tree_view_draw
- gx_tree_view_event_process
- gx_tree_view_indentation_set
- gx_tree_view_position
- gx_tree_view_root_line_color_set
- gx_tree_view_root_pixelmap_set
- gx_tree_view_selected_get

## <a name="gx_utility_canvas_to_bmp"></a>gx_utility_canvas_to_bmp

Konwertuj memort kanwy na mapę bitową

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_canvas_to_bmp(
    GX_CANVAS *canvas, 
    GX_RECTANGLE *rect,
    UINT (*write_data)(GX_UBYTE *byte_data, UINT data_count));
```

### <a name="description"></a>Opis

Ta usługa konwertuje pamięć kanwy na plik mapy bitowej.

### <a name="parameters"></a>Parametry

- **Kanwa**: wskaźnik bloku kontrolki kanwy
- **Rect**: prostokąt do przekonwertowania
- **WRITE_DATA**: wskaźnik funkcji wywołania zwrotnego do zapisywania danych

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie przekonwertowano wartość całkowitą na ciąg
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik buforu powrotu
- **GX_INVALID_SIZE**: (0X19) Nieprawidłowy rozmiar buforu powrotu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
FILE *fp = GX_NULL;

/* define call back function of how to write the data read from
canvas memory. */

UINT write_data_callback(GX_UBYTE *byte_data, UINT data_count)
{
    if (fp)
    {
        fwrite(byte_data, 1, data_count, fp);
    }
    return GX_SUCCESS;
}

VOID scroll_wheel_screen_draw(GX_WINDOW *window)
{
    UINT status;

    GX_RECTANGLE size = {31,31,610,450};
    gx_window_draw(window);
    if (screenshot)
    {
        fp = fopen("../screenshot.bmp", "wb");
        /* Convert canvas memory to bitmap format.
           Status GX_SUCCESS means operation succeed. */
        status = gx_utility_canvas_to_bmp(root->gx_window_root_canvas,
            &size, write_data_callback);

        fclose(fp);
    }
}
```

### <a name="see-also"></a>Zobacz też

- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_circle_point_get"></a>gx_utility_circle_point_get

Oblicz punkt na okręgu

### <a name="prototype"></a>Prototype

```C
INT gx_utility_circle_point_get(
    INT xCenter, 
    INT yCenter,
    UINT radius, 
    INT angle, 
    GX_POINT *point);
```

### <a name="description"></a>Opis

Ta usługa oblicza punkt na okręgu, w którym znajduje się okrąg, promień i kąt.

### <a name="parameters"></a>Parametry

- **xCenter**: Współrzędna x środka okręgu
- **yCenter**: Współrzędna y środka okręgu
- **promień**: promień okręgu
- **kąt**: kąt, w którym ma zostać obliczony punkt obwodu koła (w stopniach).
- **Point**: Address zmiennej GX_POINT, w której ma być przechowywana obliczona Współrzędna x, y
- **end_alpha**: końcowa wartość alfa

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) gradient został utworzony
- **GX_PTR_ERROR**: (0X07) nieprawidłowy adres punktu powrotu
- **GX_INVALID_VALUE**: (0X22) nieprawidłowy parametr RADIUS

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_POINT point;
    UINT status;

        status = gx_utility_circle_point_get(100, 100,
20, 45,
&point);

/* If status is GX_SUCCESS the value of point is the x,y coordinate of a point on the circle perimeter at an angle of 45 degrees, where the circle is centered at (100, 100), has a radius of 20 pixels */

```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_gradient_create"></a>gx_utility_gradient_create

Tworzenie Pixelmap gradientu

### <a name="prototype"></a>Prototype

```C
INT gx_utility_gradient_create(
    GX_GRADIENT *gradient,
    GX_VALUE width, 
    GX_VALUE height,
    UCHAR type, 
    GX_UBYTE start_alpha, 
    GX_UBYTE end_alpha);
```

### <a name="description"></a>Opis

Ta usługa tworzy Pixelmap gradientu w czasie wykonywania. Obraz gradientu może służyć do osiągnięcia efektów zaniku i innych interesujących zmian wizualnych.

Szerokość i wysokość żądanego gradientu nie może być krótsza niż 2x2 pikseli.

GUIX wewnętrznie utrzymuje listę utworzonych gradientów, a ta funkcja najpierw przeszuka listę gradientów, aby znaleźć pasujący Pixelmap gradientu przed utworzeniem nowego Pixelmap. Innymi słowy, ten sam Pixelmap gradientu jest potrzebny wiele razy, tylko jeden Pixelmap jest w rzeczywistości tworzony, a każdy gradient, który wymaga tego Pixelmap, udostępnia utworzony Pixelmap.

Ten interfejs API wymaga zdefiniowania funkcji gx_system_memory_allocator, aby zezwalać na alokację pamięci środowiska uruchomieniowego.

Flagi typu gradientu obejmują GX_GRADIENT_TYPE_ALPHA i GX_GRADIENT_TYPE_MIRROR. Obecnie są obsługiwane tylko gradienty typu GX_GRADIENT_TYPE_ALPHA (tj. Ta flaga typu musi być ustawiona). Flaga GX_GRADIENT_TYPE_MORROR jest opcjonalna, a po ustawieniu powoduje, że logika tworzenia gradientu tworzy gradient, który zmienia się z start_alpha na end_alpha i z powrotem do start_alpha. W przeciwnym razie jest tworzony gradient liniowy.

### <a name="parameters"></a>Parametry

- **gradient**: wskaźnik do struktury bloku sterowania gradientem
- **Width**: żądana szerokość Pixelmap
- **wysokość**: żądana wysokość Pixelmap
- **Typ**: żądany typ gradientu
- **start_alpha**: Rozpoczynanie wartości alfa
- **end_alpha**: końcowa wartość alfa

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) gradient został utworzony
- **GX_INVALID_SIZE**: (0X19) gradient nie ma co najmniej 2x2 pikseli
- **GX_NOT_SUPPORTED**: (0X28) gradient nie jest typu GX_GRADIENT_TYPE_ALPHA
- **GX_FAILURE**: program przydzielania pamięci (0x10) nie został zdefiniowany lub alokacja pamięci nie powiodła się
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0x07) Nieprawidłowy wskaźnik gradientu<
- Wartość parametru **GX_INVALID_VALUE**: (0x22) nie jest prawidłowa
- Typ gradientu **GX_INVALID_TYPE**: (0x1B) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_GRADIENT gradient;

UINT status;

status = gx_utiity_gradient_create(&gradient, 3, 40,
    GX_GRADIENT_TYPE_ALPHA, 240, 0);

/* If status == GX_SUCCESS the gradient pixelmap has been created */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_gradient_delete"></a>gx_utility_gradient_delete

Usuwanie wcześniej utworzonego gradientu

### <a name="prototype"></a>Prototype

```C
INT gx_utility_gradient_delete(GX_GRADIENT *gradient);
```

### <a name="description"></a>Opis

Ta usługa usuwa wcześniej utworzony gradient. Jeśli Pixelmap skojarzony z tym gradientem nie jest używany przez żadne inne gradienty, dane Pixelmap również zostaną usunięte.

### <a name="parameters"></a>Parametry

- **gradient**: wskaźnik do bloku sterowania gradientem

### <a name="return-values"></a>Wartości zwrócone

- Gradient **GX_SUCCESS**: (0x00) został usunięty
- **GX_CALLER_ERROR**: (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR**: (0x07) wskaźnik gradientu jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_GRADIENT gradient;

UINT status;

/* Delete previously created gradient. */
status = gx_utility_gradient_delete(&gradient);

/* If status == GX_SUCCESS, the gradient has been deleted. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_ltoa"></a>gx_utility_ltoa

Konwertuj liczbę całkowitą na ASCII

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_itoa(
    LONG value, 
    GX_CHAR *return_buffer,
    UINT seturn_buffer_size);
```

### <a name="description"></a>Opis

Ta usługa konwertuje wartość Long Integer na ciąg ASCII.

### <a name="parameters"></a>Parametry

- **Value**: wartość Long Integer do przekonwertowania
- **return_buffer**: bufor docelowy dla ciągu ASCII
- **return_buffer_size**: rozmiar buforu docelowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie przekonwertowano wartość całkowitą na ciąg
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik buforu powrotu
- **GX_INVALID_SIZE**: (0X19) Nieprawidłowy rozmiar buforu powrotu

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
INT my_value = 200;

GX_CHAR string_buffer[10];

UINT status;

/* Convert “my_value” into an ASCII string. */
status = gx_utility_ltoa(my_value, string_buffer, 10);

/* If status is GX_SUCCESS, “string_buffer” contains the ASCII
representation of “my_value”. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_acos"></a>gx_utility_math_acos

Arcus cosinus łuku

### <a name="prototype"></a>Prototype

```C
INT gx_utility_math_acos(GX_FIXED_VAL x);
```

### <a name="description"></a>Opis

Ta usługa oblicza wartość kąta łuku x.

Wartość wejściowa jest stałym typem danych, wywołanie GX_FIXED_VAL_MAKE do konwersji z typu INT na typ GX_FIXED_VAL. Na przykład jeśli chcesz obliczyć cosinus łuku 0,5, wprowadź dane wejściowe jako GX_FIXED_VAL_MAKE (1)/2.

W 5.4.0 lub w mniejszej wersji GUIX typ wartości wejściowej tej funkcji to INT, a wartość jest ograniczona do zakresu [-256, 256]. Aplikacja musi skalować wartość z zakresu [-1, 1] do zakresu [-256, 256] przed wywołaniem tej usługi. Jeśli projekt z GUIX w wersji równej lub mniejszej niż 5.4.0 ma odwołanie do tego interfejsu API i chcesz uaktualnić projekt przy użyciu najnowszej biblioteki GUIX. Dostępne są dwie opcje.

1. Popraw wartość wejściową tego wywołania interfejsu API, aby użyć wartości typu danych GX_FIXED_VAL.
1. Zdefiniuj GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametry

- **x**: wartość, której cosinus łuku jest obliczany

### <a name="return-values"></a>Wartości zwrócone

- **kąt**: wartość kąta łuku cosinus x

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
/* Compute the angle value of arc cosine of “0.5”. */

#if defined(GUIX_5_4_0_COMPATIBILITY)
    x = 256 / 2;
#else
    x = GX_FIXED_VAL_MAKE(1) / 2;
#endif

angle = gx_utility_math_acos(x);

/* “angle” contains the angle value of arc cosine “x”. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_asin
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_asin"></a>gx_utility_math_asin

Arcus sinus łuku

### <a name="prototype"></a>Prototype

```C
INT gx_utility_math_asin(GX_FIXED_VAL x);
```

### <a name="description"></a>Opis

Ta usługa oblicza wartość kąta łuku x.

Wartość wejściowa jest stałym typem danych, wywołanie GX_FIXED_VAL_MAKE do konwersji z typu INT na typ GX_FIXED_VAL. Na przykład jeśli chcesz obliczyć sinus łuku 0,5, wprowadź dane wejściowe jako GX_FIXED_VAL_MAKE (1)/2.

W 5.4.0 lub w mniejszej wersji GUIX typ wartości wejściowej tej funkcji to INT, a wartość jest ograniczona do zakresu [-256, 256]. Aplikacja musi skalować wartość z zakresu [-1, 1] do zakresu [-256, 256] przed wywołaniem tej usługi. Jeśli projekt ma wersję GUIX równą lub mniejszą niż 5.4.0, i chcesz uaktualnić projekt przy użyciu najnowszej biblioteki GUIX. Dostępne są dwie opcje.

1. Popraw wartość wejściową tego wywołania interfejsu API, aby użyć wartości typu danych GX_FIXED_VAL.
1. Zdefiniuj GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametry

- **x**: wartość, której sinus łuku jest obliczany

### <a name="return-values"></a>Wartości zwrócone

- **kąt**: wartość kąta łuku sinus x

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
/* Compute the angle value of arc sine of “x”. */

#if defined GUIX_5_4_0_COMPATIBILITY
    x = 256 / 2;
#else
    X = GX_FIXED_VAL_MAKE(1) / 2;
#endif

angle = gx_utility_math_asin(x);

/* “angle” contains the angle value of arc sine “x”. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_cos"></a>gx_utility_math_cos

Cosinus obliczeń

### <a name="prototype"></a>Prototype

```C
GX_FIXED_VAL gx_utility_math_cos(GX_FIXED_VAL angle);
```

### <a name="description"></a>Opis

Ta usługa oblicza cosinus podanego kąta.

Wartość wejściowa jest stałym typem danych, wywołanie GX_FIXED_VAL_MAKE do konwersji z INT na GX_FIXED_VAL. Na przykład jeśli chcesz obliczyć cosinus o 90 stopni, wprowadź dane wejściowe jako GX_FIXED_VAL_MAKE (90).

Wartość zwracana jest stałym typem danych, wywołanie GX_FIXED_VAL_TO_INT do konwersji z GX_FIXED_VAL na INT.

W wersji GUIX 5.4.0 lub o mniejszej wersji wartość wejściowa i typ wartości zwracanej tej usługi to INT, wartość wejściowa i wartość zwracana są powiększone o 256. W związku z tym aplikacja musi skalować wartość kąta o 256 przed wywołaniem tej usługi. Jeśli projekt ma wersję GUIX równą lub mniejszą niż 5.4.0 i chcesz uaktualnić projekt przy użyciu najnowszej biblioteki GUIX, dostępne są dwie opcje.

1. Popraw wartość wejściową i obsługę do wartości zwracanej tego wywołania interfejsu API, aby użyć wartości typu daty GX_FIXED_VAL.
1. Zdefiniuj GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametry

- **kąt**: kąt oblicza cosinus

### <a name="return-values"></a>Wartości zwrócone

- **cosinus**: cosinus podanego kąta

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
/* Compute cosine of 90 degree. */

INT angle = 90;

#if defined (GUIX_5_4_0_COMPATIBILITY)
    INT scaled_angle = angle << 8;
#else
    GX_FIXED_VAL scaled_angle = GX_FIXED_VAL_MAKE(angle);
#endif

my_angle_cosine = gx_utility_math_cos(scaled_angle);

/* “my_angle_cosine” contains the cosine of “my_angle”. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_math_asin
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_sin"></a>gx_utility_math_sin

Oblicz sinus

### <a name="prototype"></a>Prototype

```C
GX_FIXED_VAL gx_utility_math_sin(GX_FIXED_VAL angle);
```

### <a name="description"></a>Opis

Ta usługa oblicza sinus podanego kąta.

Wartość wejściowa jest stałym typem danych, wywołanie GX_FIXED_VAL_MAKE do konwersji z INT na GX_FIXED_VAL. Na przykład jeśli chcesz obliczyć sinus o 90 stopni, wprowadź dane wejściowe jako GX_FIXED_VAL_MAKE (90). 

Wartość zwracana jest stałym typem danych, wywołanie GX_FIXED_VAL_TO_INT do konwersji z GX_FIXED_VAL na INT.

W 5.4.0 lub mniejszej wersji GUIX, wartość wejściowa i typ zwracanej wartości to INT, wartość wejściowa i wartość zwracana są powiększone o 256. W związku z tym aplikacja musi skalować wartość kąta o 256 przed wywołaniem tej usługi. Jeśli projekt ma wersję GUIX równą lub mniejszą niż 5.4.0 i chcesz uaktualnić projekt przy użyciu najnowszej biblioteki GUIX, dostępne są dwie opcje.

1. Popraw wartość wejściową i przekazanie do zwracanej wartości tego wywołania interfejsu API, aby użyć wartości typu danych GX_FIXED_VAL.
1. Zdefiniuj GUIX_5_4_0_COMPATIBILITY.

### <a name="parameters"></a>Parametry

- **kąt**: kąt do obliczenia sinusa

### <a name="return-values"></a>Wartości zwrócone

- **sinus**: sinus podanego kąta

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
INT my_angle = 80;

/* Compute sine of “my_angle”. */

#if defined(GUIX_5_4_0_COMPATIBILITY)
    INT scaled_angle = my_angle << 8;
#else
    GX_FIXED_VAL = GX_FIXED_VAL_MAKE(my_angle);
#endif

my_angle_sine = gx_utility_math_sin(scaled_angle);

/* “my_angle_sine” contains the sine of “my_angle”. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_acos
- gx_utility_asin
- gx_utility_math_cos
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_math_sqrt"></a>gx_utility_math_sqrt

Pierwiastek kwadratowy obliczeń

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_math_sqrt(UINT value);
```

### <a name="description"></a>Opis

Ta usługa Oblicza pierwiastek kwadratowy z podanej wartości.

### <a name="parameters"></a>Parametry

- **wartość**: wartość do wyliczenia pierwiastek kwadratowy

### <a name="return-values"></a>Wartości zwrócone

- **pierwiastek kwadratowy**: pierwiastek kwadratowy podanej wartości

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
/* Compute square root of “my_value”. */
my_square_root = gx_utility_math_sqrt(my_value);

/* “my_square_root” contains the square root of “my_value”. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_bidi_paragraph_reorder"></a>gx_utility_bidi_paragraph_reorder

Zmień kolejność tekstu dwukierunkowego w kolejności wyświetlania

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_bidi_paragraph_reorder(GX_BIDI_TEXT_INFO *input_info, 
                                       GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>Opis

Ta usługa zmienia kolejność tekstu dwukierunkowego w kolejności wyświetlania. Jeśli podano czcionkę rysowania tekstu i szerokość wyświetlania, najpierw zostanie zastosowany podział wiersza, a proces zmiany kolejności zostanie zastosowany na podstawie poszczególnych wierszy. Jeśli podany tekst zawiera więcej niż jeden akapit, usługa spowoduje przerwanie tekstu w akapitach, podział wiersza i zmiana kolejności każdego akapitu zostaną połączone jako lista.

### <a name="parameters"></a>Parametry

- **input_info**: wskaźnik do informacji o dzieleniu wierszy i zmianach kolejności tekstu
- **resolved_info_head**: wskaźnik do połączonej listy, który zawiera podział wierszy i zmianę kolejności wyników każdego akapitu podanego tekstu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0x00) pomyślna zmiana kolejności tekstu dwukierunkowego
- **GX_PTR_ERROR**: (0X07) nieprawidłowe wskaźniki wejściowe
- **GX_SYSTEM_MEMORY_ERROR**: program przydzielania pamięci (0x30) nie został zdefiniowany lub alokacja pamięci nie powiodła się

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład
#### <a name="draw-single-line-bidi-text-to-canvas"></a>Rysuj jednowierszowy tekst dwukierunkowy do kanwy
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Single Line String";
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = GX_NULL;
    input_info.gx_bidi_text_info_display_width = -1;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        /* Draw reordered bidi text to canvas. */
        gx_canvas_text_draw_ext(widget->gx_widget_size.gx_rectangle_left,
                                widget->gx_widget_size.gx_rectangle_top,
                                resolved_info.gx_bidi_resolved_text_info_text);

        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```
#### <a name="draw-multi-line-bidi-text-to-canvas"></a>Rysuj wieloliniowy tekst dwukierunkowy do kanwy
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Multi Line BiDi Text Display Example";
    GX_FONT *font;
    GX_RECTANGLE client;
    GX_VALUE display_width;
    INT index;
    GX_VALUE xpos;
    GX_VALUE ypos;
    
    /* Pickup the font. */
    gx_context_font_get(font_id, &font);
    gx_widget_client_get(widget, 2, &client);
    
    display_width = (GX_VALUE)(client.gx_rectangle_right - client.gx_rectangle_left + 1);
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = font;
    input_info.gx_bidi_text_info_display_width = display_width;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        xpos = client.gx_rectangle_left;
        ypos = client.gx_rectangle_top;
        
        /* Draw reordered bidi text to canvas. */
        for(index = 0; index < resolved_info.gx_bidi_resolved_text_info_total_lines; index++)
        {
            gx_canvas_text_draw_ext(xpos, ypos, &resolved_info.gx_bidi_resolved_text_info_text[index]);
        
            ypos += font->gx_font_line_height;
        }
        
        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

#### <a name="draw-multi-paragraph-bidi-text-to-canvas"></a>Rysuj dwuakapitowy tekst dwukierunkowy do kanwy
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_BIDI_RESOLVED_TEXT_INFO *next;
    GX_CHAR bidi_text[] = "Multi Paragraph\r BiDi Text Display Example";
    GX_FONT *font;
    GX_RECTANGLE client;
    GX_VALUE display_width;
    INT index;
    GX_VALUE xpos;
    GX_VALUE ypos;
    
    /* Pickup the font. */
    gx_context_font_get(font_id, &font);
    gx_widget_client_get(widget, 2, &client);
    
    display_width = (GX_VALUE)(client.gx_rectangle_right - client.gx_rectangle_left + 1);
    
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = font;
    input_info.gx_bidi_text_info_display_width = display_width;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        xpos = client.gx_rectangle_left;
        ypos = client.gx_rectangle_top;
        
        next = resolved_info;
        
        /* Draw reordered bidi text to canvas. */
        while(next)
        {
            for(index = 0; index < next.gx_bidi_resolved_text_info_total_lines; index++)
            {
                gx_canvas_text_draw_ext(xpos, ypos, &next.gx_bidi_resolved_text_info_text[index]);
            
                ypos += font->gx_font_line_height;
            }
            
            next = next->gx_bidi_resolved_text_info_next;
        }
        
        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

### <a name="see-also"></a>Zobacz też

- gx_utility_bidi_resolved_text_info_delete

## <a name="gx_utility_bidi_resolved_text_info_delete"></a>gx_utility_bidi_resolved_text_info_delete

Usuń rozpoznaną listę informacji o tekście dwukierunkowym

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_bidi_resolved_text_info_delete(GX_BIDI_RESOLVED_TEXT_INFO **resolved_info_head)
```

### <a name="description"></a>Opis

Ta usługa usuwa listę rozwiązanych informacji, która zwróciła gx_utility_bidi_paragraph_reorder.

### <a name="parameters"></a>Parametry

- **resolved_info_head**: wskaźnik do rozwiązanej listy informacji o tekście dwukierunkowym

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne rozwiązany usuwanie tekstu
- **GX_PTR_ERROR**: (0X07) nieprawidłowe wskaźniki wejściowe
- **GX_SYSTEM_MEMORY_ERROR**: program przydzielania pamięci (0x30) nie został zdefiniowany lub alokacja pamięci nie powiodła się

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład
```C
VOID custom_widget_draw(GX_WIDGET *widget)
{
    GX_BIDI_TEXT_INFO input_info;
    GX_BIDI_RESOLVED_TEXT_INFO *resolved_info;
    GX_CHAR bidi_text[] = "Single Line String";
    
    input_info.gx_bidi_text_info_text.gx_string_ptr = bidi_text;
    input_info.gx_bidi_text_info_text.gx_string_length = sizeof(bidi_text) - 1;
    input_info.gx_bidi_text_info_font = GX_NULL;
    input_info.gx_bidi_text_info_display_width = -1;
    
    /* Reordering BiDi text. */
    status = gx_utility_bidi_paragraph_reorder(&input_info, &resolved_info);
    
    if(status == GX_SUCCESS)
    {
        /* Draw reordered bidi text to canvas. */
        gx_canvas_text_draw_ext(widget->gx_widget_size.gx_rectangle_left,
                                widget->gx_widget_size.gx_rectangle_top,
                                resolved_info.gx_bidi_resolved_text_info_text);

        /* Delete resolved information list. */
        gx_utility_bidi_resolved_text_info_delete(&resolved_info);
    }
}
```

### <a name="see-also"></a>Zobacz też

- gx_utility_bidi_paragraph_reorder

## <a name="gx_utility_pixelmap_resize"></a>gx_utility_pixelmap_resize

Zmień rozmiar Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_pixelmap_resize(
    GX_PIXELMAP *src,
    GX_PIXELMAP *destination, 
    INT width, 
    INT height);
```

### <a name="description"></a>Opis

Ta usługa zmienia rozmiar Pixelmap i zwraca wskaźnik do nowego Pixelmap, który jest wynikiem zmiany rozmiaru Pixelmap.

Ta usługa wymaga wcześniejszego użycia gx_system_memory_allocator_set, aby umożliwić alokację pamięci do przechowywania danych Pixelmap o zmienionym rozmiarze.

### <a name="parameters"></a>Parametry

- **src**: wskaźnik do Pixelmap do zmiany rozmiaru
- **miejsce docelowe**: bufor docelowy dla wyników Pixelmap
- **Width**: szerokość wyników Pixelmap (w pikselach)
- **Height**: Hieght wyników Pixelmap w pikselach

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne zmiana rozmiaru Pixelmap
- **GX_PTR_ERROR**: (0X07) Nieprawidłowa źródłowa lub docelowa wskaźnik Pixelmap
- Wartość szerokości lub wysokości **GX_INVALID_VALUE**: (0x22) jest nieprawidłowa
- **GX_NOT_SUPPORTED**: (0X28) Źródło Pixelmap jest skompresowanym formatem
- **GX_SYSTEM_MEMORY_ERROR**: program przydzielania pamięci (0x30) nie został zdefiniowany lub alokacja pamięci nie powiodła się

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
GX_PIXLEMAP *des_pixelmap;

/* Resize “src_pixelmap” with specifiy width and height. */
status = gx_utility_pixelmap_resize(src_pixelmap,
    &des_pixelmap, 100, 200);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of resize. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift
- gx_canvas_pixelmap_rotate

## <a name="gx_utility_pixelmap_rotate"></a>gx_utility_pixelmap_rotate

Obróć Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_pixelmap_rotate(
    GX_PIXELMAP *src, INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx, 
    UINT *rot_cy);
```

### <a name="description"></a>Opis

Ta usługa obraca Pixelmap i zwraca wskaźnik do nowego Pixelmap, który jest wynikiem obrotu Pixelmap. Aby obrócić Pixelmap bezpośrednio do kanwy, użyj gx_canvas_pixelmap_rotate ().

Ta usługa wymaga wcześniejszego użycia gx_system_memory_allocator_set, aby umożliwić alokacji pamięci przechowywanie obróconych danych Pixelmap.

### <a name="parameters"></a>Parametry

- **src**: Pixelmap do obrócenia
- **kąt**: kąt obrotu w stopniach
- **miejsce docelowe**: bufor docelowy dla wyników Pixelmap
- **rot_cx**: pobrana Współrzędna x środka rotacji w odniesieniu do elementu docelowego Pixelmap. Powinna zostać zainicjowana przy użyciu współrzędnych x środka rotacji w odniesieniu do źródła Pixelmap. Jeśli rot_cx jest GX_NULL, wartość nie zostanie pobrana.
- **rot_cy**: pobrana Współrzędna y środka rotacji w odniesieniu do elementu docelowego Pixelmap. Powinna zostać zainicjowana przy użyciu Współrzędna y środka rotacji w odniesieniu do źródła Pixelmap. Jeśli rot_cy jest GX_NULL, wartość nie zostanie pobrana.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne obracanie Pixelmap
- **GX_PTR_ERROR**: (0X07) Nieprawidłowa źródłowa lub docelowa wskaźnik Pixelmap
- **GX_INVALID_VALUE**: (0x22) wartość kąta wynosi 0
- **GX_INVALID_FORMAT**: (0X28) Źródło Pixelmap jest skompresowanym formatem, co nie jest obsługiwane.
- **GX_SYSTEM_MEMORY_ERROR**: program przydzielania pamięci (0x30) nie został zdefiniowany lub alokacja pamięci nie powiodła się

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
rot_cx = source_rotate_center_x;
rot_cy = source_rotate_center_y;

/* rotate “src_pixelmap” by 30 degree in clockwise direction. */
status = gx_utility_pixelmap_rotate(src_pixelmap, 30,
    &des_pixelmap, &rot_cx, &rot_cy);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of rotation. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift
- gx_canvas_pixelmap_rotate

## <a name="gx_utility_pixelmap_simple_rotate"></a>gx_utility_pixelmap_simple_rotate

Obróć Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_pixelmap_simple_rotate(
    GX_PIXELMAP *src,
    INT angle,
    GX_PIXELMAP *destination,
    UINT *rot_cx,
    UINT *rot_cy);
```

### <a name="description"></a>Opis

Ta usługa obraca Pixelmap o 90 stopni, 180 stopnia lub 270 stopień.

### <a name="parameters"></a>Parametry

- **src**: Pixelmap do obrócenia
- **kąt**: kąt obrotu w stopniach
- **miejsce docelowe**: bufor docelowy dla wyników Pixelmap
- **rot_cx**: pobrana Współrzędna x środka rotacji w odniesieniu do elementu docelowego Pixelmap. Powinna zostać zainicjowana przy użyciu współrzędnych x środka rotacji w odniesieniu do źródła Pixelmap. Jeśli rot_cx jest GX_NULL, wartość nie zostanie pobrana.
**rot_cy**: pobrana Współrzędna y środka rotacji w odniesieniu do elementu docelowego Pixelmap. Powinna zostać zainicjowana przy użyciu Współrzędna y środka rotacji w odniesieniu do źródła Pixelmap. Jeśli rot_cy jest GX_NULL, wartość nie zostanie pobrana.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślne obracanie Pixelmap
- **GX_PTR_ERROR**: (0X07) Nieprawidłowa źródłowa lub docelowa wskaźnik Pixelmap
- Wartość kąta **GX_INVALID_VALUE**: (0x22) to 0 lub nie jest to prosty kąt, taki jak 90, 180, 270
- **GX_INVALID_FORMAT**: (0X28) Źródło Pixelmap jest skompresowanym formatem, co nie jest obsługiwane.
- **GX_SYSTEM_MEMORY_ERROR**: program przydzielania pamięci (0x30) nie został zdefiniowany lub alokacja pamięci nie powiodła się

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
rot_cx = source_rotate_center_x;
rot_cy = source_rotate_center_y;

/* rotate “src_pixelmap” by 90 degree in clockwise direction. */
status = gx_utility_pixelmap_simple_rotate(src_pixelmap, 90,
    &des_pixelmap,
    &rot_cx, &rot_cy);

/* If status is GX_SUCCESS. “des_pixelmap” successfully load the
resulting pixelmap of rotation. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_center"></a>gx_utility_rectangle_center

Wyśrodkuj prostokąt w innym prostokącie

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_center(
    GX_RECTANGLE *rectangle,
    GX_RECTANGLE *within_rectangle);
```

### <a name="description"></a>Opis

Ta usługa centrum usług umieszcza prostokąt w innym prostokącie.

### <a name="parameters"></a>Parametry

- **prostokąt**: prostokąt do środka
- **within_rectangle**: prostokąt do wyśrodkowania w obrębie

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie wyśrodkować prostokąt
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik prostokąta wejściowego
- **GX_INVALID_SIZE**: (0X19) Nieprawidłowy rozmiar prostokąta

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
UINT status;

/* Center “my_inner_rectangle” inside of “my_outer_rectangle”.*/
status = gx_utility_rectangle_center(&my_inner_rectangle,
    &my_outer_rectangle);

/* Is status is GX_SUCCESS, “my_inner_rectangle” is centered
within “my_other_rectangle”. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_center_find"></a>gx_utility_rectangle_center_find

Znajdź środek prostokąta

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_center_find(
    GX_RECTANGLE *rectangle,
    GX_POINT *return_center);
```

### <a name="description"></a>Opis

Ta usługa znajduje środek prostokąta.

### <a name="parameters"></a>Parametry

- **prostokąt**: prostokąt
- **return_center**: wskaźnik do punktu środkowego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie odnalazło środek prostokąta
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik wejściowy
- **GX_INVALID_SIZE**: (0X19) Nieprawidłowy rozmiar prostokąta

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT status;

GX_RECTANGLE my_rectangle;

GX_POINT my_center_point;

gx_utility_define(&my_rectangle, 0, 0, 100, 100);

/* Find center of “my_rectangle””. */

status = gx_utility_rectangle_center_find(&my_rectangle,
    &my_center_point);

/* If status is GX_SUCCESS, “my_center_point” is the center point
of “my_rectangle” (50, 50). */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_combine"></a>gx_utility_rectangle_combine

Połącz dwa prostokąty w pierwszej kolejności

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_combine(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>Opis

Ta usługa łączy pierwszy i drugi prostokąt do pierwszego prostokąta. Pierwszy prostokąt jest rozwinięty w celu uwzględnienia drugiego.

### <a name="parameters"></a>Parametry

- **first_rectangle**: pierwszy prostokąt i połączony prostokąt
- **second_rectangle**: drugi prostokąt

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie połączone dwa prostokąty
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik wejściowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT status;

GX_RECTANGLE rect_a;

GX_RECTANGLE rect_b;

gx_utility_rectangle_define(&rect_a, 0, 0, 100, 100);
gx_utility_rectangle_define(&rect_b, 50, 50, 200, 200);

/* Combine “my_rectangle_a” to “my_rectangle_b”. */
status = gx_utility_rectangle_combine(&rect_a, &rect_b);

/* If status is GX_SUCCESS, “rect_a” is (0, 0, 200, 200) the merger
of the original “rect_a” and “rect_b”. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_compare"></a>gx_utility_rectangle_compare

Porównaj dwa prostokąty

### <a name="prototype"></a>Prototype

```C
GX_BOOL gx_utility_rectangle_compare( 
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle);
```

### <a name="description"></a>Opis

Ta usługa porównuje pierwszy i drugi prostokąt. Jeśli są równe, zwracana jest wartość GX_TRUE.

### <a name="parameters"></a>Parametry

- **first_rectangle**: pierwszy prostokąt
- **second_rectangle**: drugi prostokąt

### <a name="return-values"></a>Wartości zwrócone

- **wynik**: GX_TRUE, jeśli prostokąty są równe. w przeciwnym razie GX_FALSE jest zwracany.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Compare “my_rectangle_a” to “my_rectangle_b”. */
result = gx_utility_rectangle_compare(&my_rectangle_a,
    &my_rectangle_b);

/* If result is GX_TRUE, the two rectangles are equal. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_define"></a>gx_utility_rectangle_define

Definiowanie prostokąta

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_define(
    GX_RECTANGLE *rectangle,
    GX_VALUE left,
    GX_VALUE top, 
    GX_VALUE right, 
    GX_VALUE bottom);
```

### <a name="description"></a>Opis

Ta usługa definiuje prostokąt jako określony.

### <a name="parameters"></a>Parametry

- **prostokąt**: blok sterowania prostokątem
- z **lewej**: z lewej strony
- **Góra**: najwyższe współrzędne
- **prawy**: najbardziej koordynuje
- **dół**: najbardziej koordynuj

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie zdefiniowano prostokąt
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik prostokąta

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
UINT status;

GX_RECTANGLE my_rect;

/* Define “my_rect”. */

status = gx_utility_rectangle_define(&my_rect, 10, 5, 200, 100);

/* If status is GX_SUCCESS, “my_rect” is defined. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_overlap_detect"></a>gx_utility_rectangle_overlap_detect

Wykrywanie nakładania się prostokątów

### <a name="prototype"></a>Prototype

```C
GX_BOOL gx_utility_rectangle_overlap_detect(
    GX_RECTANGLE *first_rectangle,
    GX_RECTANGLE *second_rectangle,
    GX_RECTANGLE *return_overlap_area);
```

### <a name="description"></a>Opis

Ta usługa wykrywa dowolne nakładanie się w dostarczone prostokąty. Jeśli zostanie znalezione nakładanie się, usługa zwraca GX_TRUE i nakładający się prostokąt.

### <a name="parameters"></a>Parametry

- **first_rectangle**: pierwszy prostokąt
- **second_rectangle**: drugi prostokąt
- **return_overlap_area**: nakładający się obszar prostokąta

### <a name="return-values"></a>Wartości zwrócone

- **wynik**: GX_TRUE, jeśli prostokąty nakładają się, w przeciwnym razie GX_FALSE.

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
/* Detect overlap of “my_rectangle_a” and “my_rectangle_b”. */
result = gx_utility_rectangle_overlap_detect(&my_rectangle_a,
    &my_rectangle_b,
    &my_overlap_area);

/* If result is GX_TRUE, “my_overlap_area” specifies the area the
rectangles overlap. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_point_detect"></a>gx_utility_rectangle_point_detect

Wykryj, czy punkt znajduje się w prostokącie

### <a name="prototype"></a>Prototype

```C
GX_BOOL gx_utility_rectangle_point_detect(
    GX_RECTANGLE *rectangle,
    GX_POINT point);
```

### <a name="description"></a>Opis

Ta usługa wykrywa, czy określony punkt znajduje się w prostokącie. Jeśli punkt znajduje się w prostokącie, usługa zwraca GX_TRUE.

### <a name="parameters"></a>Parametry

- **prostokąt**: prostokąt
- **punkt**: punkt

### <a name="return-values"></a>Wartości zwrócone

- **wynik**: GX_TRUE, jeśli punkt znajduje się w prostokącie, w przeciwnym razie GX_FALSE

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```c
GX_RECTANGLE my_rectangle;

GX_POINT my_point;

gx_utility_rectangle_define(&my_rectangle, 0, 0, 100, 100);

my_point.gx_point_x = 20; my_point.gx_point_y = 20;

/* Detect if point “my_point” is within “my_rectangle””. */
result = gx_utility_rectangle_point_detect(&my_rectangle,
    &my_point);

/* If result is GX_TRUE, “my_point” resides in the rectangle. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_resize"></a>gx_utility_rectangle_resize

Prostokąt wzrostu

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_resize(
    GX_RECTANGLE *rectangle,
    GX_VALUE adjust);
```

### <a name="description"></a>Opis

Ta usługa zwiększa rozmiar prostokąta w określony sposób.

### <a name="parameters"></a>Parametry

- **prostokąt**: wskaźnik do prostokąta
- **Dostosuj**: wartość, aby dopasować prostokąt

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie Zmieniono rozmiar prostokąta
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik prostokąta wejściowego

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
UINT status;

/* Adjust “my_rectangle” by increasing 20 pixels on four sides */
status = gx_utility_rectangle_resize(&my_rectangle, 20);

/* If status is GX_SUCCESS, “my_rectangle” is 20 pixels larger. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect
- gx_utility_rectangle_shift

## <a name="gx_utility_rectangle_shift"></a>gx_utility_rectangle_shift

Prostokąt przesunięcia

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_rectangle_shift(
    GX_RECTANGLE *rectangle,
    GX_VALUE x_shift,
    GX_VALUE y_shift);
```

### <a name="description"></a>Opis

Ta usługa przenosi prostokąt według określonych wartości.

### <a name="parameters"></a>Parametry

- **prostokąt**: prostokąt do przesunięcia
- **x_shif**: liczba pikseli do przesunięcia na osi x
- **y_shift**: liczba pikseli do przesunięcia na osi y

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie przesunie prostokąt
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik prostokąta wejściowego

### <a name="allowed-from"></a>Dozwolone z

Wszystko

### <a name="example"></a>Przykład

```C
UINT status;

/* Shift “my_rectangle”. */

status = gx_utility_rectangle_shift(&my_rectangle, 10, 20);

/* If status is GX_SUCCESS, “my_rectangle” has been shifted. */
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect

## <a name="gx_utility_string_to_alphamap"></a>gx_utility_string_to_alphamap

Renderowanie ciągu do typu 8bpp alphamap Pixelmap (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_string_to_alphamap(
    const GX_CHAR *text, const
    GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>Opis

Ta usługa została wycofana na korzyść gx_utility_string_to_alphamap_ext ().

Ta usługa renderuje ciąg tekstowy do alphamap, który jest specjalną formą 8bpp Pixelmap zawierającą tylko wartości alfanumeryczne. Ta usługa jest zwykle używana wraz z gx_utility_pixelmap_rotate i gx_canvas_pixelmap_draw do rysowania obróconego tekstu na kanwie.

Ta usługa oblicza rozmiar pamięci wymaganej przez alphamap i wywołuje funkcję gx_system_memory_allocator () zdefiniowaną przez aplikację w celu dynamicznego przydzielenia pamięci. Aplikacja musi wywołać gx_system_memory_allocator_set () w pewnym momencie, zazwyczaj podczas uruchamiania programu, przed użyciem tej usługi.

Jeśli ciąg tekstowy ma zostać obrócony i narysowany do kanwy tylko raz, usługa gx_canvas_rotated_text_draw () jest świadczona jako alternatywna. gx_canvas_rotated_text_draw () wywoła gx_utility_string_to_alphamap (), gx_utility_pixelmap_rotate () i gx_canvas_pixelmap_draw (), aby renderować obrócony tekst w jednej operacji. Jeśli jednak ten sam tekst zostanie narysowany wiele razy obrócony o różne kąty, bardziej wydajne jest utworzenie alphamap raz przy użyciu interfejsu API gx_utility_string_to_alphmap, a następnie obrócenie alphamap w razie potrzeby wiele razy.

### <a name="parameters"></a>Parametry

- **Text**: ciąg tekstowy do renderowania do alphamap
- **czcionka**: Czcionka, która ma być renderowana w tekście
- **return_map**: wskaźnik do GX_PIXELMAP do zwrócenia do obiektu wywołującego.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie renderuje ciąg tekstowy do alphamap
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik wejściowy
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) alokacja pamięci/bezpłatna funkcja nie jest zdefiniowana
- **GX_INVALID_STRING_LENGTH**: (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_PIXELMAP alphamap;

GX_PIXELMAP rotated_text;

INT xpos;

INT ypos;

gx_widget_font_get(widget, GX_FONT_ID_SCREEN_LABEL, &font);

/* render string to alphamap once */

gx_utility_string_to_alphamap("Hello World", font, &alphamap);

/* rotate and render the alphmap at multiple angles */

gx_utility_pixelmap_rotate(&alphamap, 45, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(10, 10, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 135, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(100, 100, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 300, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(200, 200, &rotated_text);
```

### <a name="see-also"></a>Zobacz też

- gx_utility_string_to_alphamap_ext

## <a name="gx_utility_string_to_alphamap_ext"></a>gx_utility_string_to_alphamap_ext

Renderowanie ciągu do typu 8bpp alphamap Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_utility_string_to_alphamap_ext(
    GX_CONST GX_STRING *string,
    GX_CONST GX_FONT *font, 
    GX_PIXELMAP *return_map);
```

### <a name="description"></a>Opis

Ta usługa renderuje ciąg tekstowy do alphamap, który jest specjalną formą 8bpp Pixelmap zawierającą tylko wartości alfanumeryczne. Ta usługa jest zwykle używana wraz z gx_utility_pixelmap_rotate i gx_canvas_pixelmap_draw do rysowania obróconego tekstu na kanwie.

Ta usługa oblicza rozmiar pamięci wymaganej przez alphamap i wywołuje funkcję gx_system_memory_allocator () zdefiniowaną przez aplikację w celu dynamicznego przydzielenia pamięci. Aplikacja musi wywołać gx_system_memory_allocator_set () w pewnym momencie, zazwyczaj podczas uruchamiania programu, przed użyciem tej usługi.

Jeśli ciąg tekstowy ma zostać obrócony i narysowany do kanwy tylko raz, usługa gx_canvas_rotated_text_draw () jest świadczona jako alternatywna. gx_canvas_rotated_text_draw () wywoła gx_utility_string_to_alphamap (), gx_utility_pixelmap_rotate () i gx_canvas_pixelmap_draw (), aby renderować obrócony tekst w jednej operacji. Jeśli jednak ten sam tekst zostanie narysowany wiele razy obrócony o różne kąty, bardziej wydajne jest utworzenie alphamap raz przy użyciu interfejsu API gx_utility_string_to_alphmap, a następnie obrócenie alphamap w razie potrzeby wiele razy.

### <a name="parameters"></a>Parametry

- **ciąg**: ciąg tekstowy do renderowania do alphamap
- **czcionka**: Czcionka, która ma być renderowana w tekście
- **return_map**: wskaźnik do GX_PIXELMAP do zwrócenia do obiektu wywołującego.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS**: (0X00) pomyślnie renderuje ciąg tekstowy do alphamap
- **GX_PTR_ERROR**: (0X07) Nieprawidłowy wskaźnik wejściowy
- **GX_SYSTEM_MEMORY_ERROR**: (0x30) alokacja pamięci/bezpłatna funkcja nie jest zdefiniowana
- **GX_INVALID_STRING_LENGTH**: (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING string;

GX_PIXELMAP alphamap;

GX_PIXELMAP rotated_text;

INT xpos;

INT ypos;

gx_widget_font_get(widget, GX_FONT_ID_SCREEN_LABEL, &font);

string.gx_string_ptr = “Hello World”;

string.gx_string_length = strlen(string.gx_string_ptr);

/* render string to alphamap once */
gx_utility_string_to_alphamap_ext(&string, font, &alphamap);

/* rotate and render the alphmap at multiple angles */
gx_utility_pixelmap_rotate(&alphamap, 45, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(10, 10, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 135, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(100, 100, &rotated_text);

gx_utility_pixelmap_rotate(&alphamap, 300, &rotated_text,
    &xpos, &ypos);

gx_canvas_pixelmap_draw(200, 200, &rotated_text);
```

### <a name="see-also"></a>Zobacz też

- gx_utility_ltoa
- gx_utility_math_cos
- gx_utility_math_sin
- gx_utility_math_sqrt
- gx_utility_pixelmap_rotate
- gx_utility_pixelmap_simple_rotate
- gx_utility_rectangle_center
- gx_utility_rectangle_center_find
- gx_utility_rectangle_combine
- gx_utility_rectangle_compare
- gx_utility_rectangle_define
- gx_utility_rectangle_grow
- gx_utility_rectangle_overlap_detect
- gx_utility_rectangle_point_detect

## <a name="gx_vertical_list_children_position"></a>gx_vertical_list_children_position
### <a name="position-children-for-the-vertical-list"></a>Umieść elementy podrzędne dla listy pionowej

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_children_position(
    GX_VERTICAL_LIST *vertical_list)
```

### <a name="description"></a>Opis

Ta funkcja umieszcza elementy podrzędne dla listy pionowej.

### <a name="parameters"></a>Parametry

- **vertical_list** Wskaźnik do bloku kontrolki listy pionowej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie umieściła elementy podrzędne listy pionowej
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Position children in the vertical list */
status = gx_vertical_list_children_position (&vertical_list);

/* If status is GX_SUCCESS the children in the vertical list are positioned.. */
```

### <a name="see-also"></a>Zobacz też

- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selecgted_widget_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_create"></a>gx_vertical_list_create
### <a name="create-vertical-list"></a>Utwórz listę pionową

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_create(
    GX_VERTICAL_LIST *vertical_list,
    GX_CONST GX_CHAR *name, 
    GX_WIDGET *parent, 
    INT total_rows,
    VOID (*callback)(GX_VERTICAL_LIST *, GX_WIDGET *, INT),
    ULONG style, USHORT vertical_list_id,
    GX_CONST GX_RECTANGLE *size);
```
### <a name="description"></a>Opis

Ta usługa tworzy listę pionową.

GX_VERTICAL_LIST pochodzi od GX_WINDOW i obsługuje wszystkie gx_window usługi interfejsu API.

### <a name="parameters"></a>Parametry

- **vertical_list** Blok kontrolny widżetu listy pionowej
- **Nazwa** Nazwa listy pionowej
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **total_rows** Łączna liczba wierszy na liście pionowej
- **wywołanie zwrotne** Funkcja, która będzie wywoływana przez listę pionową, gdy lista zostanie przewinięty. Obiekt wywołujący powinien początkowo utworzyć wystarczającą liczbę elementów podrzędnych opartych na GX_WIDGET, aby wypełnić widoczne wiersze listy. Gdy lista jest przewijana, ta funkcja jest wywoływana, aby ponownie utworzyć elementy podrzędne listy odpowiadające podanemu indeksowi listy
- **styl** Styl widżetu ScrollBar. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **vertical_list_id** Zdefiniowany przez aplikację Identyfikator listy pionowej
- **rozmiar** Wymiary listy pionowej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzył listę pionową
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Niepoprawna liczba wierszy w **GX_INVALID_VALUE** (0x22)
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create vertical list “my_list” with 20 rows. */
status = gx_vertical_list_create(&my_list, “my_list”, &my_parent,
                    20, callback, GX_STYLE_WRAP, MY_LIST_ID,
                    &size);

/* If status is GX_SUCCESS the vertical list “my_list” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_vertical_list_children_position
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_event_process"></a>gx_vertical_list_event_process
### <a name="process-vertical-list-event"></a>Zdarzenie przetwarzania listy pionowej

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_event_process(GX_VERTICAL_LIST *list,
                                                      GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla listy pionowej.

### <a name="parameters"></a>Parametry

- **Lista** Blok kontrolny widżetu listy pionowej
- **zdarzenie** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przetworzył zdarzenie listy pionowej
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Process “my_event” for vertical list “my_list”. */
status = gx_vertical_list_event_process(&my_list, &my_event);

/* If status is GX_SUCCESS the event for vertical list “my_list” has been processed. */
```

### <a name="see-also"></a>Zobacz też

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_selected_set

## <a name="gx_vertical_list_page_index_set"></a>gx_vertical_list_page_index_set
### <a name="set-starting-page-index"></a>Ustaw indeks strony początkowej

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_page_index_set(
    GX_VERTICAL_LIST *list,
    INT index);
```
### <a name="description"></a>Opis

Ta usługa ustawia początkowy indeks listy pionowej.

### <a name="parameters"></a>Parametry

- **Lista** Blok kontrolny widżetu listy pionowej
- **indeks** Nowy indeks górny

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił indeks strony początkowej dla listy pionowej
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik widżetu
- **GX_INVALID_VALUE** (0X22) Nieprawidłowa wartość indeksu
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the starting page index of vertical list “my_list” to 4. */
status = gx_vertical_list_page_index_set(&my_list, 4);

/* If status is GX_SUCCESS the starting page index of “my_list” has
been set to 4. */
```
### <a name="see-also"></a>Zobacz też

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_index_get"></a>gx_vertical_list_selected_index_get
### <a name="get-selected-index-from-vertical-list"></a>Pobierz wybrany indeks z listy pionowej

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_selected_index_get(
    GX_VERTICAL_LIST *vertical_list,
    INT *return_index);
```
### <a name="description"></a>Opis

Ta usługa zwraca wybrany indeks listy pionowej

### <a name="parameters"></a>Parametry

- **vertical_list** Blok kontrolny widżetu listy pionowej
- **return_index** Miejsce docelowe powrotu wybranego indeksu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobiera wpis listy pionowej
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
INT current_selected_index;

/* Get the list entry at the current index of vertical list “my_list”. */
status = gx_vertical_list_selected_index_get(&my_list, &current_selected_index);

/* If status is GX_SUCCESS, “current_list_index” contains the index of the selected list item. */
```
### <a name="see-also"></a>Zobacz też

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_set"></a>gx_vertical_list_selected_set
### <a name="assign-the-selected-entry-in-a-vertical-list"></a>Przypisz wybrany wpis na liście pionowej

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_selected_set(
    GX_VERTICAL_LIST *vertical_list,
    INT index);
```

### <a name="description"></a>Opis

Ta usługa przypisuje wybrany wpis na liście pionowej. W razie potrzeby Pionowa lista zostanie prześwietlona, aby wyświetlić wybrany wpis.

### <a name="parameters"></a>Parametry

- **vertical_list** Blok kontrolny widżetu listy pionowej
- **indeks** Położenie nowego wpisu listy na podstawie indeksu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił wpis listy pionowej
- Nie znaleziono indeksu wejściowego **GX_FAILURE** (0x10) na liście
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_WIDGET** (0X12) Pionowa lista lub element widget wpisów listy jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the list entry of “my_list” to the child in line 12. */
status = gx_vertical_list_selected_set(&my_list, 12);

/* If status is GX_SUCCESS, the list entry of “my_list” has been successfully set to 12. */
```
### <a name="see-also"></a>Zobacz też

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_get
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_selected_widget_get"></a>gx_vertical_list_selected_widget_get
### <a name="get-selected-widget-from-vertical-list"></a>Pobierz wybrany element widget z listy pionowej

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_selected_widget_get(
    GX_VERTICAL_LIST *vertical_list,
    GX_WIDGET **return_list_entry);
```
### <a name="description"></a>Opis

Ta usługa zwraca wybrany element widget listy pionowej. Należy pamiętać, że jeśli lista zawiera więcej wierszy niż podrzędne elementy widget, a wybrany widżet podrzędny został przewinięty z widoku, ta funkcja zwróci GX_NULL jako wskaźnik GX_WIDGET, ponieważ widżet został ponownie użyty do wyświetlenia nowego wpisu listy.

### <a name="parameters"></a>Parametry

- **vertical_list** Blok kontrolny widżetu listy pionowej
- **return_list_entry** Miejsce docelowe dla widżetu wpisu listy zwrotnej

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobiera wpis listy pionowej
- **GX_FAILURE** (0x10) wybrany element widget został przewinięty z widoku.
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_WIDGET *current_selected_widget;

/* Get the list entry at the current index of vertical list “my_list”. */
status = gx_vertical_list_selected_widget_get(&my_list, &current_selected_widget);

/* If status is GX_SUCCESS, “current_list_entry” contains a pointer to the currently selected widget. */
```

### <a name="see-also"></a>Zobacz też

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_set
- gx_vertical_list_total_rows_set

## <a name="gx_vertical_list_total_rows_set"></a>gx_vertical_list_total_rows_set
### <a name="set-total-number-of-vertical-list-rows"></a>Ustaw łączną liczbę wierszy listy pionowej

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_list_total_rows_set(
    GX_VERTICAL_LIST *vertical_list,
    INT count);
```
### <a name="description"></a>Opis

Ta usługa przypisuje lub zmienia łączną liczbę wierszy listy.

### <a name="parameters"></a>Parametry

- **vertical_list** Blok kontrolny widżetu listy pionowej
- **Liczba** Liczba nowych wierszy listy

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił liczbę pionowych wierszy listy
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- Wartość liczby wierszy w **GX_INVALID_VALUE** (0x22) jest nieprawidłowa

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set the list row count to 20 items. */
status = gx_vertical_list_total_rows_set(&my_list, 20);

/* If status is GX_SUCCESS, the total rows of “my_list” has been set to 20. */
```
### <a name="see-also"></a>Zobacz też

- gx_vertical_list_children_position
- gx_vertical_list_create
- gx_vertical_list_event_process
- gx_vertical_list_page_index_set
- gx_vertical_list_selected_index_get
- gx_vertical_list_selected_widget_get
- gx_vertical_list_selected_set

## <a name="gx_vertical_scrollbar_create"></a>gx_vertical_scrollbar_create
### <a name="create-vertical-scrollbar"></a>Utwórz pionowy pasek przewijania

### <a name="prototype"></a>Prototype

```C
UINT gx_vertical_scrollbar_create(
    GX_SCROLLBAR *scrollbar,
    GX_CONST GX_CHAR *name, 
    GX_WINDOW *parent,
    GX_SCROLLBAR_APPEARANCE *appearance,
    ULONG style);
```
### <a name="description"></a>Opis

Ta usługa tworzy pionowy pasek przewijania.

### <a name="parameters"></a>Parametry

- **pasek przewijania** Blok kontrolny widżetu ScrollBar
- **Nazwa** Nazwa paska przewijania
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **wygląd** Wygląd pionowego widżetu paska przewijania.
- **styl** Styl paska przewijania.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przeprowadzono pionowy pasek przewijania
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Create vertical scrollbar “my_scrollbar”. */
status = gx_vertical_scrollbar_create(&my_scrollbar,
                          “my_vertical_scrollbar”,
                          &my_parent, &scrollbar_appearance,
                          GX_STYLE_ENABLED);

/* If status is GX_SUCCESS the vertical scrollbar “my_scrollbar” has been created. */
```
### <a name="see-also"></a>Zobacz też

- gx_horizontal_scrollbar_create
- gx_scrollbar_draw
- gx_scrollbar_event_process
- gx_scrollbar_limit_check
- gx_scrollbar_reset

## <a name="gx_widget_allocate"></a>gx_widget_allocate
### <a name="allocate-a-widget-control-block"></a>Przydzielanie bloku kontrolki widgetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_allocate(
    GX_WIDGET **control_block,
    ULONG memsize);
```
### <a name="description"></a>Opis

Ta usługa dynamicznie przydziela blok kontrolki widżetu przez wywołanie funkcji alokacji pamięci zdefiniowanej przez aplikację. Ta usługa jest używana głównie przez funkcje wygenerowane przez GUIX Studio do dynamicznego przydzielania bloku sterowania, gdy właściwość "dynamiczna alokacja" została wybrana w widoku właściwości programu GUIX Studio.

### <a name="parameters"></a>Parametry

- **control_block** Wskaźnik do zwróconego wskaźnika bloku sterowania
- **memsize** Rozmiar bloku kontroli (w bajtach)

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) — przydzielenie widżetu pomyślne
- Program przydzielania pamięci **GX_SYSTEM_MEMORY_ERROR** (0x30) nie został zdefiniowany lub alokacja pamięci nie powiodła się
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Nieprawidłowy rozmiar pamięci **GX_INVALID_MEMORY_SIZE** (0x29)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_TEXT_BUTTON *button;

/* Attach “my_widget” to “my_parent”. */
status = gx_widget_allocate(&button, sizeof(GX_TEXT_BUTTON));

/* If status is GX_SUCCESS the button widget control block is allocated. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_attach"></a>gx_widget_attach
### <a name="attach-widget-to-its-parent"></a>Dołącz widżet do jego elementu nadrzędnego

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>Opis

Ta usługa dołącza widżet do określonego elementu nadrzędnego. Jeśli widżet jest już dołączony do innego elementu nadrzędnego, najpierw jest odłączony. Jeśli widżet jest już dołączony do tego samego elementu nadrzędnego, funkcja nic nie robi.

Widżet zostanie przesunięty w przód od elementu nadrzędnego względem porządku osi z. Jeśli elementy widget elementu równorzędnego nakładają się, ten element widget jest rysowany na elementach równorzędnych. Aby umieścić nowy widżet z tyłu porządku osi z, użyj gx_widget_back_attach lub gx_widget_back_move.

### <a name="parameters"></a>Parametry

- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- element **widget** Wskaźnik do elementu widget podrzędny

### <a name="return-values"></a>Wartości zwrócone

- Dołączanie widżetu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element nadrzędny or **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Attach “my_widget” to “my_parent”. */
status = gx_widget_attach(&my_parent, &my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is attached to “my_parent”. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_background_draw"></a>gx_widget_background_draw
### <a name="draw-a-widget-background"></a>Rysowanie tła widżetu

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_background_draw(GX_WIDGET *widget);
```
### <a name="description"></a>Opis

Ta usługa wykonuje pełny kolor wypełnienia tła widżetu. Ta usługa jest automatycznie wywoływana przez funkcję gx_widget_draw, ale może być również wywoływana przez aplikację jako część niestandardowej funkcji rysowania widżetu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do elementu widget do rysowania

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
    /* Call default widget background draw. */
    gx_widget_background_draw(widget);

    /* Add your own drawing here. */

    /* Draw child widgets. */
    gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_back_attach"></a>gx_widget_back_attach
### <a name="attach-widget-to-its-parent"></a>Dołącz widżet do jego elementu nadrzędnego

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_back_attach(
    GX_WIDGET *parent, 
    GX_WIDGET *widget);
```
### <a name="description"></a>Opis

Ta usługa dołącza widżet do określonego elementu nadrzędnego. Jeśli widżet jest już dołączony do innego elementu nadrzędnego, najpierw jest odłączony. Jeśli widżet jest już dołączony do tego samego elementu nadrzędnego, funkcja nic nie robi.

Widżet zmieni się z tyłu elementu podrzędnego w stosunku do porządku osi z. Jeśli elementy widget elementu równorzędnego nakładają się, ten element widget jest rysowany za tymi elementami równorzędnymi. Aby umieścić nowy widżet z góry porządku osi z, użyj gx_widget_attach lub gx_widget_front_move.

### <a name="parameters"></a>Parametry

- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- element **widget** Wskaźnik do elementu widget podrzędny

### <a name="return-values"></a>Wartości zwrócone

- Dołączanie widżetu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element nadrzędny or **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Attach “my_widget” to “my_parent”. */
status = gx_widget_back_attach(&my_parent, &my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is attached to “my_parent”. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_back_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_back_move"></a>gx_widget_back_move
### <a name="move-widget-to-back"></a>Przenieś widżet do tyłu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_back_move(
    GX_WIDGET *widget,
    GX_BOOL *return_widget_moved);
```
### <a name="description"></a>Opis

Ta usługa przenosi widżet do tyłu w porządku osi Z elementów podrzędnych elementu nadrzędnego.

### <a name="parameters"></a>Parametry

- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **return_widget_moved** Wskaźnik do elementu docelowego dla flagi wskazującej, że element widget został przeniesiony

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne przejście widżetu do tyłu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_NO_CHANGE** (0X08) nie są stosowane żadne zmiany
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move “my_widget” to the back. */
status = gx_widget_back_move(&my_widget, &moved_flag);

/* If status is GX_SUCCESS and “moved_flag” is GX_TRUE, the widget “my_widget” was moved to the back. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_block_move"></a>gx_widget_block_move
### <a name="move-a-rectangular-block-of-pixels"></a>Przenoszenie prostokątnego bloku pikseli

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_block_move(
    GX_WIDGET *widget,
    GX_RECTANGLE *block,
    INT xshift, INT yshift);
```

### <a name="description"></a>Opis

Ta usługa przenosi prostokątny blok pikseli. Ta usługa jest najczęściej używana do implementowania szybkiego przewijania.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do elementu widget żądający przeniesienia bloku
- **Blokuj** Blok ograniczający prostokąt do przeniesienia
- **xshift** Kwota przesunięcia x w pikselach.
- **yshift** Wartość przesunięcia y w pikselach.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne przejście widżetu do tyłu
- Nie znaleziono kanwy widżetu **GX_INVALID_CANVAS** (0x20)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move a block of pixels 20 pixels to the right. */
status = gx_widget_block_move(&my_widget, &size, 20, 0);

/* If status is GX_SUCCESS the block of pixels was moved. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_draw"></a>gx_widget_border_draw
### <a name="draw-widget-border"></a>Obramowanie elementu widget rysowania

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_border_draw(
    GX_WIDGET *widget,
    GX_COLOR border_color,
    GX_COLOR upper_fill, 
    GX_COLOR lower_fill, 
    GX_BOOL fill);
```

### <a name="description"></a>Opis

Ta usługa rysuje obramowanie widżetu. Ta usługa jest zwykle wywoływana jako część funkcji rysowania widżetu. Ta usługa interpretuje flagi stylu obramowania widżetu do rysowania bez obramowania, cienkiego obramowania, wypukłego obramowania, obramowania wgłębienia ani grubego obramowania.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **border_color** Kolor obramowania. **Dodatek A** zawiera wstępnie zdefiniowane kolory. Należy pamiętać, że aplikacja może również dodać kolory niestandardowe.
- **upper_fill** Kolor górnego wypełnienia. **Dodatek A** zawiera wstępnie zdefiniowane kolory. Należy pamiętać, że aplikacja może również dodać kolory niestandardowe.
- **lower_fill** Kolor dolnego wypełnienia. **Dodatek A** zawiera wstępnie zdefiniowane kolory. Należy pamiętać, że aplikacja może również dodać kolory niestandardowe.
- **wypełnienie** Ta flaga logiczna wskazuje, czy obszar widżetu ma być wypełniony podanymi kolorami wypełnienia. Jeśli ta wartość jest GX_FALSE, rysowany jest tylko obramowanie elementu widget.

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
      /* Call widget border draw. */
      gx_widget_border_draw(widget, GX_COLOR_BLACK,
                            GX_COLOR_GREEN, GX_COLOR_BLUE,
                            GX_TRUE);

      /* Add your own drawing here. */

      /* Draw child widgets. */
      Gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_style_set"></a>gx_widget_border_style_set
### <a name="set-widget-border-style"></a>Ustaw styl obramowania widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_border_style_set(
    GX_WIDGET *widget, 
    ULONG style);
```

### <a name="description"></a>Opis

Ta usługa ustawia styl obramowania widżetu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **styl** Styl obramowania. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.

### <a name="return-values"></a>Wartości zwrócone

- Zestaw stylu obramowania **GX_SUCCESS** (0X00) zakończony powodzeniem
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set border style of “my_widget”. */
status = gx_widget_border_style_set(&my_widget,
                                    GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS the widget “my_widget” border style has been set. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_border_width_get"></a>gx_widget_border_width_get
### <a name="get-widget-border-width"></a>Pobierz szerokość obramowania elementu widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_border_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width);
```

### <a name="description"></a>Opis

Ta usługa Pobiera szerokość obramowania widżetu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **return_width** Wskaźnik do miejsca docelowego dla szerokości obramowania elementu widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrała szerokość obramowania
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_VALUE my_width;

/* Get border width of “my_widget”. */
status = gx_widget_border_width_get(&my_widget, &my_width);

/* If status is GX_SUCCESS, “my_width” contains the border width of the widget “my_widget”. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_canvas_get"></a>gx_widget_canvas_get
### <a name="get-widget-canvas"></a>Pobierz kanwę widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_canvas_get(
    GX_WIDGET *widget,
    GX_CANVAS **return_canvas)
```
### <a name="description"></a>Opis

Ta usługa zwraca wskaźnik do kanwy, na której jest renderowany ten element widget.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **return_canvas** Wskaźnik do miejsca docelowego dla kanwy elementu widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne pobieranie kanwy widżetu
- Nie znaleziono kanwy widżetu **GX_FAILURE** (0x10)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Get canvas associated with “my_widget”. */
status = gx_widget_canvas_get(&my_widget, &my_canvas);

/* If status is GX_SUCCESS, “my_canvas” contains the canvas of the widget “my_widget”. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_child_detect"></a>gx_widget_child_detect
### <a name="detect-widget-child"></a>Wykryj element podrzędny widgetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_child_detect(
    GX_WIDGET *parent, 
    GX_WIDGET *child,
    GX_BOOL *return_detect);
```

### <a name="description"></a>Opis

Ta usługa wykrywa, czy widżet jest elementem podrzędnym widżetu nadrzędnego. Ta usługa jest zagnieżdżona w celu przeszukiwania elementów podrzędnych i zwraca wartość TRUE, jeśli widżet nadrzędny znajduje się na dowolnym poziomie jako element nadrzędny widżetu podrzędnego.

### <a name="parameters"></a>Parametry

- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **element podrzędny** Wskaźnik do elementu widget podrzędny
- **return_detect** Wskaźnik do miejsca docelowego na potrzeby wykrywania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne wykrywanie elementu podrzędnego widżetu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element nadrzędny lub podrzędny elementu **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_BOOL detected;

/* Determine if “my_child” is a child of “my_widget”. */
status = gx_widget_child_detect(&my_widget, &my_child, &detected);

/* If status is GX_SUCCESS and “detected” is GX_TRUE, “my_child” is a child of widget “my_widget”. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_children_draw"></a>gx_widget_children_draw
### <a name="draw-widget-children"></a>Elementy podrzędne elementu widget rysowania

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_children_draw(GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa rysuje wszystkie elementy podrzędne widżetu nadrzędnego. Ta usługa jest zwykle wywoływana przez wszystkie funkcje rysowania standardowego widżetu do rysowania wszelkich istniejących elementów widget i powinny być wywoływane przez dowolne niestandardowe funkcje rysowania, aby umożliwić dołączenie podrzędnych elementów widget do niestandardowego typu widżetu nadrzędnego.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom widget draw function. */

VOID my_widget_draw(GX_WIDGET * widget)
{
        /* Call default widget background draw. */
        gx_widget_background_draw(widget);

        /* Add your own drawing here. */

        /* Draw child widgets. */
        gx_widget_children_draw(widget);
}
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_client_get"></a>gx_widget_client_get
### <a name="get-widget-client-area"></a>Pobierz obszar klienta widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_client_get(
    GX_WIDGET *widget,
    GX_VALUE border_width,
    GX_RECTANGLE *return_client_area);
```
### <a name="description"></a>Opis

Ta usługa oblicza obszar klienta widżetu, odejmując szerokość obramowania widżetu od ogólnego rozmiaru widżetu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **border_width** Szerokość obramowania widgetu
- **return_client_area** Miejsce docelowe dla zwracanego obszaru klienta

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne odbieranie obszaru klienta widżetu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- Obramowanie widgetu **GX_INVALID_VALUE** (0x22) jest nieprawidłowe

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RECTANGLE client_area
/* Get client area of widget “my_widget”. */
status = gx_widget_client_get(&my_widget, my_widget_width,
                              &client_area);

/* If status is GX_SUCCESS, the “client_area” is the client area of “my_widget”. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_color_get"></a>gx_widget_color_get
### <a name="get-color"></a>Pobierz kolor

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_color_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_COLOR *return_color);
```

### <a name="description"></a>Opis

Ta usługa Pobiera kolor skojarzony z podanym IDENTYFIKATORem zasobu. Ta usługa powinna być wywoływana tylko przez widoczne widżety.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do bloku kontrolki elementu widget
- **resource_id** Identyfikator zasobu koloru. **Dodatek B** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **return_color** Wskaźnik do miejsca docelowego dla koloru. **Dodatek A** zawiera wstępnie zdefiniowane kolory. Należy pamiętać, że aplikacja może również dodać kolory niestandardowe.

### <a name="return-values"></a>Wartości zwrócone

- Pobieranie pomyślnego koloru **GX_SUCCESS** (0x00)
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_CANVAS** (0x20) Kanwa widżetu jest nieprawidłowa lub element widget jest niewidoczny
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_COLOR actual_color;

/* Get color for resource ID MY_FIRST_COLOR_ID. */
status = gx_widget_color_get(my_widget, MY_FIRST_COLOR_RESOURCE_ID,
                            &actual_color);

/* If status is GX_SUCCESS the actual color is contained in “actual_color”. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_font_get
- gx_widget_pixelmap_get

## <a name="gx_widget_create"></a>gx_widget_create
### <a name="create-widget"></a>Utwórz widżet

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_create(
    GX_WIDGET *widget, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent,
    ULONG style, 
    USHORT widget_id,
    GX_CONST GX_RECTANGLE *size);
```
### <a name="description"></a>Opis

Ta usługa tworzy widżet.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **Nazwa** Logiczna nazwa widżetu
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **styl** Stylów. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **widget_id** Zdefiniowany przez aplikację identyfikator widżetu
- **rozmiar** Rozmiar widżetu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) pomyślnego utworzenia widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_WIDGET my_widget;
GX_RECTANGLE size;

gx_utility_rectangle_define(&size, 0, 0, 100, 100);

/* Get client area of widget “my_widget”. */
status = gx_widget_create(&my_widget, "my widget",
                          &my_parent_window, GX_STYLE_BORDER_RAISED, MY_WIDGET_ID, &size);

/* If status is GX_SUCCESS, the widget “my_widget” has been created. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_created_test"></a>gx_widget_created_test
### <a name="test-if-widget-created"></a>Testuj, czy element widget został utworzony

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_created_test(
    GX_WIDGET *widget,
    GX_BOOL *return_test);
```
### <a name="description"></a>Opis

Ta usługa sprawdza, czy element widget został wcześniej utworzony. Jeśli nie zostaną napotkane żadne błędy, ta funkcja zwróci GX_SUCCESS, bez względu na to, czy element widget został jeszcze utworzony. Wynik testu znajduje się na return_test wskaźniku.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **return_test** Miejsce docelowe dla wyniku testu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne zakończenie testu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_BOOL was_created;

/* Test to see if widget “my_widget” is created. */
status = gx_widget_created_test(&my_widget, &was_created);

/* If status is GX_SUCCESS, no error occurred. If “was_created” is
GX_TRUE, the widget “my_widget” has been created. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_delete"></a>gx_widget_delete
### <a name="delete-widget"></a>Usuń widżet

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_delete(GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa usuwa widżet. Jeśli blok kontrolki widżetu jest przydzielany dynamicznie, usługa gx_system_memory_free jest wywoływana w celu zwolnienia dynamicznie przydzielonych magazynów.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) pomyślnego usunięcia GX_CALLER_ERROR widżetu (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- Funkcja wolnych pamięci **GX_SYSTEM_MEMORY_ERROR** (0x30) nie jest zdefiniowana

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Delete widget “my_widget”. */
status = gx_widget_delete(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been deleted. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_detach"></a>gx_widget_detach
### <a name="detach-widget-from-parent"></a>Odłącz widżet z elementu nadrzędnego

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_detach(GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa odłącza widżet od swojego elementu nadrzędnego.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) pomyślnego odłączenia widżetu, GX_CALLER_ERROR (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Detach widget “my_widget” from its parent. */
status = gx_widget_detach(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been detached. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_draw"></a>gx_widget_draw
### <a name="draw-widget"></a>Element widget rysowania

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_draw(GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa rysuje element widget. Ta funkcja jest zwykle wywoływana wewnętrznie przez mechanizm odświeżania kanwy GUIX, ale jest dostępna dla aplikacji, aby pomóc w zaimplementowaniu niestandardowych funkcji rysowania.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
      /* Call default widget draw. */
      gx_widget_draw(widget);

      /* Add your own drawing here. */
}
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_draw_set"></a>gx_widget_draw_set
### <a name="assign-the-widget-drawing-function"></a>Przypisywanie funkcji rysowania widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_draw_set(
    GX_WIDGET *widget,
    VOID (*drawing_function) (GX_WIDGET *));
```

### <a name="description"></a>Opis

Ta usługa zastępuje domyślną funkcję rysowania widżetu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **drawing_function** Wskaźnik do funkcji rysowania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne przesłonięcie funkcji rysowania widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Define a custom drawing function. */
VOID my_drawing_function(GX_WIDGET *widget)
{
      /* Add your own drawing here. */
}

/* Set the drawing function of widget “my_widget” to “my_drawing_function”. */
status = gx_widget_draw_set(&my_widget, my_drawing_function);

/* If status is GX_SUCCESS the widget “my_widget” has the drawning function “my_drawing_function”. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_generate"></a>gx_widget_event_generate
### <a name="generate-widget-event"></a>Generuj zdarzenie widgetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_event_generate(
    GX_WIDGET *widget, 
    USHORT event_type, LONG value);
```

### <a name="description"></a>Opis

Ta usługa generuje GX_SIGNAL typ zdarzenia, który jest określonym typem lub klasą GX_EVENT. gx_widget_event_generate () Koduje identyfikator widżetu 16-bitowego wraz z przekazywaniem w event_type, do jednej wartości 32 bit GX_EVENT. gx_event_type. Parametr value jest zakodowany w wygenerowanym gx_event. gx_event_payload pole gx_event_payload.gx_event_longdata.

Pole wygenerowana event.gx_event_target jest zawsze ładowane z elementem nadrzędnym widżetu wywołującego, co oznacza, że wygenerowane zdarzenie jest zawsze wysyłane najpierw do elementu nadrzędnego widżetu generującego.

Należy pamiętać, że gx_widget_event_generate należy używać tylko do wysyłania typów zdarzeń GX_SIGNAL zakres. Dla wszystkich innych typów zdarzeń, w tym typów zdarzeń zdefiniowanych przez użytkownika, należy użyć interfejsu API gx_system_event_send (), który przyznaje pełną kontrolę nad każdym polem zdarzenia wypchnięte w kolejce zdarzeń GUIX.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **event_type** Typ zdarzenia. **Dodatek E** zawiera wstępnie zdefiniowane zdarzenia GUIX. Aplikacja może dodawać dodatkowe zdarzenia.
- **wartość** Dodatkowe informacje o zdarzeniu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne generowanie zdarzeń widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Generate a redraw event for widget “my_widget”. */
status = gx_widget_event_generate(&my_widget, GX_EVENT_REDRAW, 0);

/* If status is GX_SUCCESS the redraw event for widget “my_widget” has been generated. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get
- gx_system_event_send

## <a name="gx_widget_event_process"></a>gx_widget_event_process
### <a name="process-widget-event"></a>Zdarzenie widżetu procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_event_process(
    GX_WIDGET *widget, 
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Jest to domyślna funkcja przetwarzania zdarzeń dla wszystkich elementów widget. Gdy jest zapisywana funkcja niestandardowego przetwarzania zdarzeń, domyślną akcją dla każdego typu zdarzenia powinna być zawsze przekazanie zdarzenia do typu widżetu, na którym jest oparty element widget. Widżety, które są oparte na najbardziej podstawowym typie GX_WIDGET, używają gx_widget_event_process jako domyślnej funkcji przetwarzania zdarzeń.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **zdarzenie** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne przetwarzanie zdarzeń widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Process event “my_event” for widget “my_widget”. */
status = gx_widget_event_process(&my_widget, &my_event);

/* If status is GX_SUCCESS the event “my_event” for widget “my_widget” has been processed. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_process_set"></a>gx_widget_event_process_set
### <a name="set-event-processing-function-of-widget"></a>Ustaw funkcję przetwarzania zdarzeń elementu widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_event_process_set(
    GX_WIDGET *widget,
    UINT (*event_processing) (GX_WIDGET *, GX_EVENT *));
```

### <a name="description"></a>Opis

Ta usługa zastępuje funkcję przetwarzania zdarzeń elementu widget.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **Event_Processing** Wskaźnik do nowej funkcji przetwarzania zdarzeń

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) zakończono pomyślne przesłonięcie przetwarzania zdarzeń widżetu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
UINT my_event_process(GX_TREE_VIEW *tree_view,
                      GX_EVENT *event)
{
      UINT status = GX_SUCCESS;

      switch(event->gx_event_type)
      {
      case xyz:
            /* Insert custom event handling here */
            break;

      default:
            /* Pass all other events to the default tree view
               event processing */
            status = gx_tree_view_event_process(tree_view, event);
            break;
      }
      return status;
}

/* Use “my_event_process” to process events for widget “my_tree_view”. */
status = gx_widget_event_process_set((GX_WIDGET *)&my_tree_view,
                    (VOID (*)(GX_WIDGET *))my_event_process);

/* If status is GX_SUCCESS all event processing for widget “my_tree_view” is handled by “my_event_process”. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_event_to_parent"></a>gx_widget_event_to_parent
### <a name="send-event-to-widgets-parent"></a>Wyślij zdarzenie do elementu nadrzędnego widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_event_to_parent(
    GX_WIDGET *widget,
    GX_EVENT *event);
```
### <a name="description"></a>Opis

Ta usługa wysyła zdarzenie do elementu nadrzędnego widżetu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **zdarzenie** Wskaźnik do zdarzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie wysłał zdarzenie do elementu nadrzędnego widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Send my_event to the widget’s parent */
status = gx_widget_event_to_parent(&my_widget, my_event);

/* If status is GX_SUCCESS the event has been delivered to the parent of my_widget. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_fill_color_set"></a>gx_widget_fill_color_set
### <a name="set-widget-background-color"></a>Ustaw kolor tła widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_fill_color_set(
    GX_WIDGET *widget,
    GX_RESOURCE_ID normal_color_id,
    GX_RESOURCE_ID selected_color_id,
    GX_RESOURCE_ID disabled_color_id);
```
### <a name="description"></a>Opis

Ta usługa ustawia kolory tła widżetu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **normal_color_id** Identyfikator zasobu koloru wypełnienia w normalnym stanie. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **selected_color_id** Identyfikator zasobu koloru wypełnienia, gdy element widget uzyskuje fokus. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.
- **disabled_color_id** Identyfikator zasobu koloru wypełnienia, gdy styl GX_STYLE_ENABLED nie jest ustawiony. **Dodatek A** zawiera wstępnie zdefiniowane identyfikatory zasobów koloru. Należy pamiętać, że aplikacja może również dodać identyfikatory zasobów koloru niestandardowego.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie ustawił kolor wypełnienia widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set background of “my_widget”. */
status = gx_widget_fill_color_set(&my_widget,
                    GX_COLOR_ID_NORMAL_FILL,
                    GX_COLOR_ID_SELECTED_FILL,
                    GX_COLOR_ID_DISABLED_FILL);

/* If status is GX_SUCCESS the widget “my_widget” background has been set. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_create
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_find"></a>gx_widget_find
### <a name="find-child-widget-of-parent-widget"></a>Znajdź element widget elementu nadrzędnego widgetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    INT search_depth, 
    GX_WIDGET **return_widget);
```
### <a name="description"></a>Opis

Ta usługa przeszukuje elementy podrzędne określonego elementu nadrzędnego szukające widżetu z żądanym wartością identyfikatora.

### <a name="parameters"></a>Parametry

- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget, z którego jest uruchamiane wyszukiwanie
- **widget_id** Identyfikator elementu widget do wyszukania
- **search_depth** Definiuje cykliczny poziom zagnieżdżenia, do którego funkcja będzie przeszukiwać elementy podrzędne. Jeśli ta wartość jest <= 0, przeszukiwane są tylko natychmiastowe elementy podrzędne widżetu nadrzędnego. Jeśli ta wartość jest GX_SEARCH_DEPTH_INFINITE, wszystkie elementy podrzędne wszystkich elementów widget podrzędnych są wyczerpująco przeszukiwane. Dla każdej innej wartości > 0 ta wartość ogranicza, jak głęboko zagnieżdżona ta funkcja będzie przeszukiwać za pomocą elementów widget dla żądanego identyfikatora widżetu.
- **return_widget** Wskaźnik do miejsca docelowego dla znalezionego widżetu

### <a name="return-values"></a>Wartości zwrócone

- Odnalezienie elementu widget pomyślnego **GX_SUCCESS** (0x00)
- Element widget **GX_NOT_FOUND** (0x09) nie Fount
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_WIDGET *widget_found;

/* Find widget “my_widget”. */
status = gx_widget_find(&my_widget, GX_SEARCH_DEPTH_INFINITE
                        MY_WIDGET_ID, &widget_found);

/* If status is GX_SUCCESS, the pointer “widget_found” contains the pointer to the widget found. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_first_child_get"></a>gx_widget_first_child_get
### <a name="return-pointer-to-first-child-widget"></a>Zwróć wskaźnik do pierwszego widżetu podrzędnego

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_first_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Opis

GUIX utrzymuje strukturalną listę widżetów nadrzędnych i podrzędnych. Ta usługa zwraca wskaźnik do pierwszego widgetu podrzędnego elementu nadrzędnego.

### <a name="parameters"></a>Parametry

- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **widget_return** Wskaźnik do zwrócenia wskaźnika widżetu

### <a name="return-values"></a>Wartości zwrócone

- Zwrócony wskaźnik **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik widżetu
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve child widget pointer. */

GX_WIDGET *get_child_widget(GX_WIDGET *parent)
{
      GX_WIDGET *child;
      UINT status;

      status = gx_widget_first_child_get(parent, &child);
      if (status == GX_SUCCESS)
      {
            return child;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Zobacz też

- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_focus_next"></a>gx_widget_focus_next
### <a name="move-focus-to-next-widget-in-navigation-order"></a>Przenieś fokus do następnego widżetu w kolejności nawigacji

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_focus_next(GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa przenosi fokus do następnego elementu widget równorzędnego na połączonej liście widżetów, które akceptują fokus.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do bloku kontrolki elementu widget

### <a name="return-values"></a>Wartości zwrócone

- Zmieniono fokus **GX_SUCCESS** (0x00)
- Fokus **GX_FAILURE** (0x00) nie został przeniesiony
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move focus to next widget in navigation order. */ status =
gx_widget_focus_next(&my_widget);

/* If status is GX_SUCCESS the focus has been moved to the next
widget in the navigation order */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_focus_previous

## <a name="gx_widget_focus_previous"></a>gx_widget_focus_previous
### <a name="move-focus-to-previous-widget-in-navigation-order"></a>Przenieś fokus do poprzedniego widżetu w kolejności nawigacji

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_focus_previous(GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa przenosi fokus do poprzedniego widżetu w kolejności nawigacji.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu, który ma bieżący fokus wprowadzania.

### <a name="return-values"></a>Wartości zwrócone

- Zmieniono fokus **GX_SUCCESS** (0x00)
- Fokus **GX_FAILURE** (0x00) nie został przeniesiony

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Move focus to previuos widget in navigation order. */ status =
gx_widget_focus_previous(&my_widget);

/* If status is GX_SUCCESS the input focus has been moved to the
previous widget. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_focus_next

## <a name="gx_widget_font_get"></a>gx_widget_font_get
### <a name="get-font-for-specified-resource-id"></a>Pobierz czcionkę dla określonego identyfikatora zasobu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_font_get(
    GX_WIDGETG *widget,
    GX_RESOURCE_ID resource_id,
    GX_FONT **return_font);
```
### <a name="description"></a>Opis

Ta usługa pobiera czcionkę skojarzoną z określonym IDENTYFIKATORem zasobu z tabeli Fonts wyświetlanej, na której jest widoczny ten element widget. Ta funkcja powinna być wywoływana tylko przez widoczny element widget.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do bloku kontrolki elementu widget
- **resource_id** Identyfikator zasobu czcionki
- **return_font** Wskaźnik do miejsca docelowego dla wskaźnika czcionki

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrała czcionkę
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_CANVAS** (0x20) Kanwa widżetu jest nieprawidłowa lub element widget jest niewidoczny
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik widżetu
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_FONT *my_font;
/* Get font for MY_FONT_ID. */
status = gx_widget_font_get(widget, MY_FONT_RESOURCE_ID, &my_font);
/* If status is GX_SUCCESS the font pointer has been retrieved in “my_font”. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_color_get
- gx_widget_pixelmap_get

## <a name="gx_widget_free"></a>gx_widget_free
### <a name="release-memory-associated-with-a-widget"></a>Zwolnij pamięć skojarzoną z widżetem

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_free(GX_WIDGETG *widget);
```

### <a name="description"></a>Opis

Ta usługa zwalnia pamięć skojarzoną z blokiem kontrolki widget.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do bloku kontrolki elementu widget
- **resource_id** Identyfikator zasobu czcionki
- **return_font** Wskaźnik do miejsca docelowego dla wskaźnika czcionki

### <a name="return-values"></a>Wartości zwrócone

- Element widget **GX_SUCCESS** (0X00) został pomyślnie zwolniony
- Funkcja wolnych pamięci **GX_SYSTEM_MEMPRY_ERROR** (0x30) nie jest zdefiniowana
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik widżetu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_WIDGET widget;
UINT status;

status = gx_widget_allocate(&widget, sizeof(GX_WIDGET))

/* Free a runtime allocated widget. */
if (status == GX_SUCCESS)
{
      status = gx_widget_free(widget);
}

/* If status is GX_SUCCESS the memory that allocated to the widget has been released. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_front_move"></a>gx_widget_front_move
### <a name="move-widget-to-front"></a>Przenieś widżet do przodu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_front_move(
    GX_WIDGET *widget, 
    GX_BOOL *return_moved);
```

### <a name="description"></a>Opis

Ta usługa przenosi widżet do przodu na liście nadrzędnych elementów widget.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do elementu widget do przeniesienia
- **return_moved** Wskaźnik do miejsca docelowego dla elementu widget wskazujący został przeniesiony

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne przejście widżetu do przodu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_NO_CHANGE** (0x08) jest już na wierzchu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_BOOL widget_moved;

/* Move widget “my_widget” to the front. */
status = gx_widget_front_move(&my_widget, &widget_moved);

/* If status is GX_SUCCESS and “widget_moved” is GX_TRUE, the
widget “my_widget” was moved to the front . */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_height_get"></a>gx_widget_height_get
### <a name="get-widget-height"></a>Pobierz wysokość widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_height_get(
    GX_WIDGET *widget,
    UINT *return_height);
```

### <a name="description"></a>Opis

Ta usługa pobiera wysokość elementu widget.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **return_height** Wskaźnik do miejsca docelowego dla wysokości widżetu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne pobieranie wysokości widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_VALUE widget_height;

/* Get height for widget “my_widget”. */
status = gx_widget_height_get(&my_widget, &widget_height);

/* If status is GX_SUCCESS the height of the widget is contained in
“widget_height” . */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_hide"></a>gx_widget_hide
### <a name="hide-widget"></a>Ukryj widżet

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_hide(GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa ukrywa widżet. Ten widżet jest nadal dołączony do elementu nadrzędnego, ale nie może być rysowany na kanwie.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu

### <a name="return-values"></a>Wartości zwrócone

- Niepowodzenie ukrywania **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
/* Hide widget “my_widget”. */
status = gx_widget_hide(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” is hidden. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_style_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_last_child_get"></a>gx_widget_last_child_get
### <a name="return-pointer-to-last-child-widget"></a>Zwróć wskaźnik do ostatniego widżetu podrzędnego

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_last_child_get(
    GX_WIDGET *parent,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Opis

GUIX utrzymuje strukturalną listę widżetów nadrzędnych i podrzędnych. Ta usługa zwraca wskaźnik do ostatniego widżetu podrzędnego elementu nadrzędnego.

### <a name="parameters"></a>Parametry

- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **widget_return** Wskaźnik do zwrócenia wskaźnika widżetu

### <a name="return-values"></a>Wartości zwrócone

- Zwrócony wskaźnik **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik widżetu
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve child widget pointer. */

GX_WIDGET *get_last_child_widget(GX_WIDGET *parent)
{

      GX_WIDGET *child;
      UINT status;

      status = gx_widget_last_child_get(parent, &child);
      if (status == GX_SUCCESS)
      {
              return child;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Zobacz też

- gx_widget_first_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_next_sibling_get"></a>gx_widget_next_sibling_get
### <a name="return-pointer-to-next-sibling-of-current-widget"></a>Zwróć wskaźnik do następnego elementu równorzędnego bieżącego widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_next_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Opis

GUIX utrzymuje strukturalną listę widżetów nadrzędnych i podrzędnych. Ta usługa zwraca wskaźnik do następnego elementu równorzędnego bieżącego widżetu.

### <a name="parameters"></a>Parametry

- **bieżące** Wskaźnik do bieżącego widżetu
- **widget_return** Wskaźnik do zwrócenia wskaźnika widżetu

### <a name="return-values"></a>Wartości zwrócone

- Zwrócony wskaźnik **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik widżetu
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve next sibling widget pointer. */

GX_WIDGET *get_next(GX_WIDGET *current)
{
      GX_WIDGET *sibling;
      UINT status;

      status = gx_widget_next_sibling_get(current, &sibling);
      if (status == GX_SUCCESS)
      {
            return sibling;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Zobacz też

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_parent_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_parent_get"></a>gx_widget_parent_get
### <a name="return-pointer-to-parent-of-current-widget"></a>Zwróć wskaźnik do elementu nadrzędnego bieżącego widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_parent_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```
### <a name="description"></a>Opis

GUIX utrzymuje strukturalną listę widżetów nadrzędnych i podrzędnych. Ta usługa zwraca wskaźnik do elementu nadrzędnego bieżącego widżetu.

### <a name="parameters"></a>Parametry

- **bieżące** Wskaźnik do bieżącego widżetu
- **widget_return** Wskaźnik do zwrócenia wskaźnika widżetu

### <a name="return-values"></a>Wartości zwrócone

- Zwrócony wskaźnik **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik widżetu
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve parent widget */

GX_WIDGET *get_parent(GX_WIDGET *current)
{
      GX_WIDGET *parent;
      UINT status;

      status = gx_widget_parent_get(current, &parent);
      if (status == GX_SUCCESS)
      {
            return parent;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Zobacz też

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_previous_sibling_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_pixelmap_get"></a>gx_widget_pixelmap_get
### <a name="get-pixelmap"></a>Pobierz Pixelmap

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_pixelmap_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID resource_id,
    GX_PIXELMAP **return_pixelmap);
```

### <a name="description"></a>Opis

Ta usługa pobiera Pixelmap skojarzone z podanym IDENTYFIKATORem zasobu. Ta usługa powinna być wywoływana tylko dla widocznych elementów widget.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do bloku kontrolki elementu widget
- **pixelmap_id** Identyfikator zasobu Pixelmap
- **return_pixelmap** Wskaźnik do Pixelmap docelowego wskaźnika

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne pobieranie Pixelmap
- **GX_INVALID_RESOURCE_ID** (0X33) Nieprawidłowy identyfikator zasobu
- **GX_INVALID_CANVAS** (0x20) Kanwa widżetu jest nieprawidłowa lub element widget jest niewidoczny
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```c
GX_PIXELMAP *my_pixelmap;

/* Get the pixelmap associated with MY_PIXELMAP_ID. */
status = gx_widget_pixelmap_get(widget, MY_PIXELMAP_RESOURCE_ID,
                                &my_pixelmap);

/* If status is GX_SUCCESS, “my_pixelmap” contains the pixemap pointer. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_color_get
- gx_widget_font_get

## <a name="gx_widget_previous_sibling_get"></a>gx_widget_previous_sibling_get
### <a name="return-pointer-to-previous-sibling-of-the-current-widget"></a>Zwróć wskaźnik do poprzedniego elementu równorzędnego bieżącego widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_previous_sibling_get(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>Opis

GUIX utrzymuje strukturalną listę widżetów nadrzędnych i podrzędnych. Ta usługa zwraca wskaźnik do poprzedniego elementu równorzędnego bieżącego widżetu.

### <a name="parameters"></a>Parametry

- **bieżące** Wskaźnik do bieżącego widżetu
- **widget_return** Wskaźnik do zwrócenia wskaźnika widżetu

### <a name="return-values"></a>Wartości zwrócone

- Zwrócony wskaźnik **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik widżetu
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve previous sibling widget */

GX_WIDGET *get_previous(GX_WIDGET *current)
{
      GX_WIDGET *sibling;
      UINT status;

      status = gx_widget_previous_sibling_get(current, &sibling);
      if (status == GX_SUCCESS)
      {
          return sibling;
      }
      return GX_NULL;
}
```
### <a name="see-also"></a>Zobacz też

- gx_widget_first_child_get
- gx_widget_last_child_get
- gx_widget_next_sibling_get
- gx_widget_parent_get
- gx_widget_top_visible_child_find

## <a name="gx_widget_resize"></a>gx_widget_resize
### <a name="resize-widget"></a>Zmień rozmiar widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_resize(
    GX_WIDGET *widget, 
    GX_RECTANGLE *new_size);
```
### <a name="description"></a>Opis

Ta usługa zmienia rozmiar widżetu. Jeśli widżet jest widoczny, zostanie automatycznie unieważniony i umieszczony w kolejce do przerysowania.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **new_size** Nowy rozmiar widżetu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne zmiana rozmiaru widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RECTANGLE new_size;

gx_utility_rectangle_define(&new_size, 0, 0, 100, 100);

/* Resize widget “my_widget”. */
status = gx_widget_resize(&my_widget, &new_size);

/* If status is GX_SUCCESS the widget “my_widget” has been resized. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_shift"></a>gx_widget_shift
### <a name="shift-widget"></a>Widżet przesunięcia

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_shift(
    GX_WIDGET *widget, 
    GX_VALUE x_shift,
    GX_VALUE y_shift, 
    GX_BOOL mark_dirty);
```

### <a name="description"></a>Opis

Ta usługa przenosi widżet i opcjonalnie oznacza go jako zanieczyszczony.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **x_shift** Liczba pikseli do przesunięcia na osi x
- **y_shift** Liczba pikseli do przesunięcia na osi y
- **mark_dirty** GX_TRUE wskazujące na zanieczyszczone, w przeciwnym razie GX_FALSE

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) pomyślnego przesunięcia widżetu GX_CALLER_ERROR (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Shift widget “my_widget”. */
status = gx_widget_shift(&my_widget, 10, 20, GX_FALSE);

/* If status is GX_SUCCESS the widget “my_widget” has been shifted. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_show"></a>gx_widget_show
### <a name="show-widget"></a>Pokaż widżet

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_show(GX_WIDGET *widget);
```

### <a name="description"></a>Opis

Ta usługa pokazuje widżet. Widżet stanie się widoczny tylko wtedy, gdy jest dołączony do elementu nadrzędnego, a widżet nadrzędny jest również widoczny.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) pomyślnego wyświetlenia widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Show widget “my_widget”. */
status = gx_widget_show(&my_widget);

/* If status is GX_SUCCESS the widget “my_widget” has been shown. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_add"></a>gx_widget_status_add
### <a name="add-widget-status"></a>Dodaj stan widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_status_add(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>Opis

Ta usługa dodaje dowolną kombinację stanu flags do określonego widżetu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **stan** Stan do dodania

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne dodanie stanu widżetu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Add status to widget “my_widget”. */
status = gx_widget_status_add(&my_widget, status_to_add);

/* If status is GX_SUCCESS the widget “my_widget” status was. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_get"></a>gx_widget_status_get
### <a name="get-widget-status"></a>Pobierz stan widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_status_get(
    GX_WIDGET *widget,
    ULONG *return_status)
```

### <a name="description"></a>Opis

Ta usługa pobiera flagi stanu z elementu widget.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **return_status** Wskaźnik do zwracanego stanu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne pobieranie stanu widżetu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
ULONT get_status;

/* Retrieve status flag from widget “my_widget”. */ status =
gx_widget_status_get(&my_widget, &get_status);

/* If status is GX_SUCCESS the status from widget “my_widget” is
saved to “get_status”. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_remove"></a>gx_widget_status_remove
### <a name="remove-widget-status"></a>Usuń stan widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_status_remove(
    GX_WIDGET *widget, 
    ULONG status)
```

### <a name="description"></a>Opis

Ta usługa usuwa określone flagi stanu z wewnętrznej zmiennej stanu widżetów.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **stan** Stan do usunięcia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) usunięcie stanu widżetu zakończonego powodzeniem
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Remove status of widget “my_widget”. */
status = gx_widget_status_remove(&my_widget, status_to_remove);

/* If status is GX_SUCCESS, the status flags are removed from the
widget “my_widget”. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_status_test"></a>gx_widget_status_test
### <a name="test-widget-status"></a>Stan elementu widget testu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_status_test(
    GX_WIDGET *widget, 
    ULONG status,
    GX_BOOL *return_test);
```
### <a name="description"></a>Opis

Ta usługa sprawdza flagi stanu określonego widżetu i zapisuje wynik w pamięci wskazanej przez "return_test".

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **stan** Stan do przetestowania
- **return_status** Wskaźnik do miejsca docelowego dla wyniku testu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) Test stanu widżetu pomyślne
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_BOOL test_result;

/* Test status of widget “my_widget”. */
status = gx_widget_status_test(&my_widget, status_to_test,
                              &test_result);

/* If status is GX_SUCCESS the widget “my_widget” status was tested
and the result in “test_result”. */
```
### <a name="see-also"></a>Zobacz też

- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_widget_string_get"></a>gx_widget_string_get
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id-deprecated"></a>Pobierz ciąg skojarzony z widocznym widżetem i IDENTYFIKATORem ciągu (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_CHAR **string);
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_widget_string_get_ext ().

Ta usługa zwraca wpis tabeli ciągów dla danej wartości identyfikatora ciągu. Ta usługa jest podobna do gx_display_string_get, z tą różnicą, że aktywne wyświetlanie jest określane automatycznie, a nie przez wywołującego. Ta usługa może być używana tylko dla elementów widget, które są widoczne, tj. wyświetlania skojarzonych z tym widżetem.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **string_id** Wartość identyfikatora ciągu z nagłówka zasobów
- **ciąg** Adres zmiennej do zwrócenia ciągu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) Test stanu widżetu pomyślne
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_CONST GX_CHAR *string;

/* Test status of widget “my_widget”. */
status = gx_widget_string_get(&my_widget, GX_STRING_ID_SHUTDOWN,
      &string);

/* If status is GX_SUCCESS the string has been retrieved */
```
### <a name="see-also"></a>Zobacz też

- gx_display_string_get
- gx_display_active_langauge_set

## <a name="gx_widget_string_get_ext"></a>gx_widget_string_get_ext
### <a name="retrieve-string-associated-with-a-visible-widget-and-string-id"></a>Pobierz ciąg skojarzony z widocznym widżetem i IDENTYFIKATORem ciągu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_string_get(
    GX_WIDGET *widget,
    GX_RESOURCE_ID string_id,
    GX_CONST GX_STRING *string);
```

### <a name="description"></a>Opis

Ta usługa zwraca wpis tabeli ciągów dla danej wartości identyfikatora ciągu. Ta usługa jest podobna do gx_display_string_get, z tą różnicą, że aktywne wyświetlanie jest określane automatycznie, a nie przez wywołującego. Ta usługa może być używana tylko dla elementów widget, które są widoczne, tj. wyświetlania skojarzonych z tym widżetem.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **string_id** Wartość identyfikatora ciągu z nagłówka zasobów
- **ciąg** Adres zmiennej do zwrócenia ciągu

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) Test stanu widżetu pomyślne
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_STRING string;

/* Test status of widget “my_widget”. */

status = gx_widget_string_get_ext(&my_widget,
                          GX_STRING_ID_SHUTDOWN, &string);

/* If status is GX_SUCCESS the string has been retrieved */
```

### <a name="see-also"></a>Zobacz też

- gx_display_string_get
- gx_display_active_langauge_set

## <a name="gx_widget_style_add"></a>gx_widget_style_add
### <a name="add-widget-style"></a>Dodaj styl widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_style_add(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Opis

Ta usługa dodaje styl do widżetu. Ponadto są podejmowane następujące działania.

Jeśli dodany styl jest GX_STYLE_TRANSPARENT, GX_STATUS_TRANSPARENT zostanie dodany stan.

Jeśli dodany styl jest GX_STYLE_ENABLED, GX_STATUS_SELECTABLE zostanie dodany stan.

Jeśli widżet jest widoczny, zostanie automatycznie unieważniony i umieszczony w kolejce do przerysowania.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **styl** Nowy styl do dodania. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) pomyślnego dodania stylu widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Add style to widget “my_widget”. */
status = gx_widget_style_add(&my_widget, GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS, the style was successfully applied to the widget “my_widget”. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_get"></a>gx_widget_style_get
### <a name="get-widget-style"></a>Pobierz styl widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_style_get(
    GX_WIDGET *widget, 
    ULONG *return_style)
```

### <a name="description"></a>Opis

Ta usługa Pobiera flagę stylu z elementu widget.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **return_style** Wskaźnik do zwracanego stylu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie pobrał styl widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki


### <a name="example"></a>Przykład

```C
/* Retrieve style from widget into “style”. */
status = gx_widget_style_get(&my_widget, &style);

/* If status is GX_SUCCESS the style flag from widget is saved in “style”. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_remove
- gx_widget_style_add
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_remove"></a>gx_widget_style_remove
### <a name="remove-widget-style"></a>Usuń styl widgetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_style_remove(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Opis

Ta usługa usuwa styl z elementu widget. Ponadto są podejmowane następujące działania.

Jeśli usunięty styl jest GX_STYLE_TRANSPARENT, stan GX_STATUS_TRANSPARENT zostanie usunięty.

Jeśli usunięty styl jest GX_STYLE_ENABLED, stan GX_STATUS_SELECTABLE zostanie usunięty.

Jeśli widżet jest widoczny, zostanie automatycznie unieważniony i umieszczony w kolejce do przerysowania.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **styl** Styl do usunięcia. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne usunięcie stylu widżetu **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Remove style from widget “my_widget”. */
status = gx_widget_style_remove(&my_widget,
                                GX_STYLE_BORDER_RAISED);

/* If status is GX_SUCCESS the GX_STYLE_BORDER_RAISED style was removed from the widget “my_widget”.*/
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_style_set"></a>gx_widget_style_set
### <a name="set-widget-style"></a>Ustaw styl widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_style_set(
    GX_WIDGET *widget, 
    ULONG style)
```

### <a name="description"></a>Opis

Ta usługa ustawia styl do widżetu.

Jeśli zestaw stylów zawiera GX_STYLE_TRANSPARENT, zostanie dodany stan GX_STATUS_TRANSPARENT, w przeciwnym razie stan zostanie usunięty.

Jeśli zestaw stylów zawiera GX_STYLE_ENABLED, zostanie dodany stan GX_STATUS_SELECTABLE, w przeciwnym razie stan zostanie usunięty.

Jeśli widżet jest widoczny, zostanie automatycznie unieważniony i umieszczony w kolejce do przerysowania.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **styl** Styl do ustawienia. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0x00) ustawiony styl widżetu pomyślnego
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set style GX_STYLE_TRANSPARENT to the widget “my_widget”. */
status = gx_widget_style_set(&my_widget, GX_STYLE_TRANSPARENT);

/* If status is GX_SUCCESS the widget “my_widget” style is set to GX_STYLE_TRANSPARENT. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_set
- gx_widget_width_get

## <a name="gx_widget_text_blend"></a>gx_widget_text_blend
### <a name="blend-text-assigned-to-widget-deprecated"></a>Tekst mieszany przypisany do elementu widget (przestarzałe)

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_text_blend(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CHAR *string,
    INT x_offset, 
    INT y_offset, 
    UCHAR alpha)
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_widget_text_blend_ext ().

Ta usługa miesza określony tekst nad widżetem przy użyciu bieżącego pędzla i wyrównania tekstu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **tColor** Kolor tekstu
- **font_id** Identyfikator czcionki
- **ciąg** Ciąg rysowania
- **x_offset** Dopasowanie położenia rysunku
- **y_offset** Dopasowanie położenia rysunku
- **Alpha** Mieszanie wartości 0-255

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne uzyskanie szerokości widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Blend “my_string” over “my_widget” given alpha value 120. */
status = gx_widget_text_blend(&my_widget, my_text_color, my_font_id,
                              &my_string, xoffset, yoffset, 120);

/* If status is GX_SUCCESS “my_string” has been blend to “my_widget”. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_text_blend_ext

## <a name="gx_widget_text_blend_ext"></a>gx_widget_text_blend_ext
### <a name="blend-text-assigned-to-widget"></a>Tekst mieszany przypisany do elementu widget

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_text_blend(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CONST GX_STRING *string,
    INT x_offset, 
    INT y_offset, 
    UCHAR alpha)
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_widget_text_blend_ext ().

Ta usługa renderuje ciąg w określonym widżecie przy użyciu bieżącego pędzla i wyrównania tekstu oraz określonego koloru, czcionki i przesunięcia x, y.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **tColor** Kolor tekstu
- **font_id** Identyfikator czcionki
- **ciąg** Ciąg rysowania
- **x_offset** Dopasowanie położenia rysunku
- **y_offset** Dopasowanie położenia rysunku
- **Alpha** Mieszanie wartości 0-255

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne uzyskanie szerokości widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- **GX_INVALID_STRING_LENGTH** (0X34) Nieprawidłowa długość ciągu

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
gx_string render_string;
render_string.gx_string_ptr = “Hello”;
render_string.gx_string_length =
    strlen(render_string.gx_string_ptr);

/* Blend “my_string” over “my_widget” given alpha value 120. */
status = gx_widget_text_blend_ext(&my_widget,
        my_text_color,
        my_font_id,
        &render_string, xoffset, yoffset, 120);

/* If status is GX_SUCCESS “my_string” has been blend to “my_widget”. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_text_draw_ext

## <a name="gx_widget_text_draw"></a>gx_widget_text_draw
### <a name="draw-text-assigned-to-widget-deprecated"></a>Rysuj tekst przypisany do elementu widget (przestarzałe)

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_text_draw(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    GX_CHAR *string,
    INT x_offset, 
    INT y_offset)
```

### <a name="description"></a>Opis

Ta usługa jest przestarzała na rzecz gx_widget_text_draw_ext ().

Ta usługa Rysuje określony tekst nad widżetem przy użyciu bieżącego pędzla i wyrównania tekstu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **tColor** Kolor tekstu
- **font_id** Identyfikator czcionki
- **ciąg** Ciąg rysowania
- **x_offset** Dopasowanie położenia rysunku
- **y_offset** Dopasowanie położenia rysunku

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background raw here. */

    /* Call widget text draw. */
    gx_widget_text_draw(widget, my_text_color, my_font_id
                        &my_string, xoffset, yoffset);
}
```

### <a name="see-also"></a>Zobacz też

- gx_widget_text_blend
- gx_widget_text_id_draw

## <a name="gx_widget_text_draw_ext"></a>gx_widget_text_draw_ext
### <a name="draw-text-assigned-to-widget"></a>Rysuj tekst przypisany do widgetu

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_text_draw(
    GX_WIDGET *widget,
    UINT *tColor,
    UINT font_id, 
    GX_CONST GX_STRING *string,
    INT x_offset,
    INT y_offset)
```

### <a name="description"></a>Opis

Ta usługa Rysuje określony tekst nad widżetem przy użyciu bieżącego pędzla i wyrównania tekstu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **tColor** Kolor tekstu
- **font_id** Identyfikator czcionki
- **text_id** Identyfikator tekstu
- **x_offset** Dopasowanie położenia rysunku
- **y_offset** Dopasowanie położenia rysunku

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
gx_string render_string;
render_string.gx_string_ptr = “Hello”;
render_string.gx_string_length =
    strlen(render_string.gx_string_ptr);

/* Write a custom widget draw function. */
VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background draw here. */

    /* Call widget text draw. */
    gx_widget_text_draw_ext(widget, my_text_color, my_font_id
                        &render_string, xoffset, yoffset);
}
```

### <a name="see-also"></a>Zobacz też

- gx_widget_text_blend
- gx_widget_text_id_draw

## <a name="gx_widget_text_id_draw"></a>gx_widget_text_id_draw
### <a name="draw-text-assigned-to-widget"></a>Rysuj tekst przypisany do widgetu

### <a name="prototype"></a>Prototype

```C
VOID gx_widget_text_id_draw(
    GX_WIDGET *widget, 
    UINT *tColor,
    UINT font_id, 
    UINT text_id,
    INT x_offset, 
    INT y_offse)
```

### <a name="description"></a>Opis

Ta usługa rysuje tekst w widżecie przy użyciu identyfikatora tekstu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **tColor** Kolor tekstu
- **font_id** Identyfikator czcionki
- **text_id** Identyfikator tekstu
- **x_offset** Dopasowanie położenia rysunku
- **y_offset** Dopasowanie położenia rysunku

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Write a custom widget draw function. */

VOID my_custom_widget_draw(GX_WIDGET *widget)
{
    /* Add your own background raw here. */

    /* Call widget text id draw. */
    gx_widget_text_id_draw(widget, my_text_color, my_font_id
                            &my_string_id, xoffset, yoffset);
}
```

### <a name="see-also"></a>Zobacz też

- gx_widget_text_blend
- gx_widget_text_draw

## <a name="gx_widget_top_visible_child_find"></a>gx_widget_top_visible_child_find
### <a name="return-pointer-to-visible-child-that-is-top-of-z-order"></a>Zwróć wskaźnik do widocznego elementu podrzędnego, który jest góra z kolejności Z

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_top_visible_child_find(
    GX_WIDGET *current,
    GX_WIDGET **widget_return);
```

### <a name="description"></a>Opis

GUIX utrzymuje strukturalną listę widżetów nadrzędnych i podrzędnych.
Ta usługa zwraca wskaźnik do najwyższego widocznego elementu podrzędnego bieżącego widżetu.

### <a name="parameters"></a>Parametry

- **bieżące** Wskaźnik do bieżącego widżetu
- **widget_return** Wskaźnik do zwrócenia wskaźnika widżetu

### <a name="return-values"></a>Wartości zwrócone

- Zwrócony wskaźnik **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik widżetu
- **GX_INVALID_WIDGET** (0X12) nieprawidłowy widżet

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Retrieve topmost visible widget on the display */

GX_WIDGET *get_top_window(GX_WINDOW_ROOT *root)
{
    GX_WIDGET *top_window;
    UINT status;

    status = gx_widget_top_visible_child_find(root, &top_window);
    if (status == GX_SUCCESS)
    {
        return top_window;
    }
    return GX_NULL;
}
```

### <a name="see-also"></a>Zobacz też

- gx_widget_first_child_get,
- gx_widget_last_child_get,
- gx_widget_next_sibling_get,
- gx_widget_parent_get,
- gx_widget_previous_sibling_get

## <a name="gx_widget_type_find"></a>gx_widget_type_find
### <a name="search-for-a-widget-of-the-requested-type"></a>Wyszukaj widżet o żądanym typie

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_type_find(
    GX_WIDGET *parent, 
    USHORT widget_id,
    GX_WIDGET **return_widget)
```

### <a name="description"></a>Opis

Ta usługa szuka widżetu żądanego typu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **return_width** Wskaźnik do miejsca docelowego dla szerokości elementu widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne uzyskanie szerokości widżetu
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_WIDGET *retrieved_widget;

/* Find horizontal scrollbar under “parent_widget”. */
status = gx_widget_type_find(&parent_widget,
                GX_TYPE_HORIZONTAL_SCROLL_BAR, &retrieved_widget);

/* If status is GX_SUCCESS, the horizontal scrollbar widget is retrieved. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_widget_width_get"></a>gx_widget_width_get
### <a name="get-widget-width"></a>Pobierz szerokość widżetu

### <a name="prototype"></a>Prototype

```C
UINT gx_widget_width_get(
    GX_WIDGET *widget,
    GX_VALUE *return_width)
```

### <a name="description"></a>Opis

Ta usługa Pobiera szerokość widżetu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do widżetu
- **return_width** Wskaźnik do miejsca docelowego dla szerokości elementu widget

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne uzyskanie szerokości widżetu
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_VALUE my_widget_width;

/* Get width of widget “my_widget”. */
status = gx_widget_width_get(&my_widget, &my_widget_width);

/* If status is GX_SUCCESS the width of widget “my_widget” is in “my_widget_width”. */
```

### <a name="see-also"></a>Zobacz też

- gx_widget_attach
- gx_widget_back_move
- gx_widget_background_set
- gx_widget_border_draw
- gx_widget_border_style_set
- gx_widget_border_width_get
- gx_widget_canvas_get
- gx_widget_child_detect
- gx_widget_children_draw
- gx_widget_client_get
- gx_widget_created
- gx_widget_created_test
- gx_widget_delete
- gx_widget_detach
- gx_widget_draw
- gx_widget_draw_set
- gx_widget_event_generate
- gx_widget_event_process
- gx_widget_event_process_set
- gx_widget_event_to_parent
- gx_widget_find
- gx_widget_front_move
- gx_widget_height_get
- gx_widget_hide
- gx_widget_resize
- gx_widget_shift
- gx_widget_show
- gx_widget_status_add
- gx_widget_status_get
- gx_widget_status_remove
- gx_widget_status_test
- gx_widget_style_add
- gx_widget_style_get
- gx_widget_style_remove
- gx_widget_style_set

## <a name="gx_window_client_height_get"></a>gx_window_client_height_get
### <a name="get-window-client-height"></a>Pobierz wysokość klienta okna

### <a name="prototype"></a>Prototype

```C
UINT gx_window_client_height_get(
    GX_WINDOW *window,
    GX_VALUE *return_height);
```

### <a name="description"></a>Opis

Ta usługa pobiera wysokość klienta okna.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do okna
- **return_height** Wskaźnik do miejsca docelowego dla wysokości klienta

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne pobieranie wysokości przez klienta okna
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RECTANGLE my_client_height;

/* Get client height of “my_window”. */
status = gx_window_client_height_get(&my_window,
                                     &my_client_height);

/* If status is GX_SUCCESS the window “my_window” client height is contained in “my_client_height”. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- x_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_client_scroll"></a>gx_window_client_scroll
### <a name="scroll-window-clients"></a>Przewinięcie okna klientów

### <a name="prototype"></a>Prototype

```C
UINT gx_window_client_scroll(
    GX_WINDOW *window, 
    GX_VALUE x_scroll,
    GX_VALUE y_scroll);
```

### <a name="description"></a>Opis

Ta usługa przewija klientów systemu Windows o określoną liczbę.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do okna
- **x_scroll** Kwota do przewijania na osi x
- **y_scroll** Kwota do przewijania na osi y

### <a name="return-values"></a>Wartości zwrócone

- Przewinięcie okna klienta powiodło się **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- Wartości przewijania **GX_INVALID_VALUE** (0x22) są nieprawidłowe

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Scroll clients of “my_window”. */
status = gx_window_client_scroll(&my_window, 10, 0);

/* If status is GX_SUCCESS the clients of window “my_window” have been scrolled. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_client_width_get"></a>gx_window_client_width_get
### <a name="get-window-client-width"></a>Pobierz szerokość klienta okna

### <a name="prototype"></a>Prototype

```C
UINT gx_window_client_width_get(
    GX_WINDOW *window,
    GX_VALUE *return_width);
```

### <a name="description"></a>Opis

Ta usługa Pobiera szerokość klienta określonego okna.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do okna
- **return_height** Wskaźnik do miejsca docelowego dla szerokości klienta

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne pobieranie szerokości klienta okna **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_VALUE my_client_widthl

/* Get client width of “my_window”. */
status = gx_window_client_width_get(&my_window, &my_client_width);

/* If status is GX_SUCCESS “my_client_width” contains the client width of window “my_window”. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_close"></a>gx_window_close
### <a name="close-modal-window"></a>Zamknij okno modalne

### <a name="prototype"></a>Prototype

```C
UINT gx_window_close(GX_WINDOW *window);
```

### <a name="description"></a>Opis

Ta usługa wymusza odłączenie okna modalnego od jego elementu nadrzędnego i powrót ze pętli wykonywania modalnego.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do bloku sterowania oknem

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie zamknięto okno
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Close window “my_window”. */
status = gx_window_close(&my_window);

/* If status is GX_SUCCESS window “my_window” has been closed. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_create"></a>gx_window_create
### <a name="create-window"></a>Utwórz okno

### <a name="prototype"></a>Prototype

```C
UINT gx_window_create(
    GX_WINDOW *window, 
    GX_CONST GX_CHAR *name,
    GX_WIDGET *parent, 
    ULONG style,
    USHORT window_id, 
    GX_CONST GX_RECTANGLE *size);
```

### <a name="description"></a>Opis

Ta usługa tworzy okno.

GX_WINDOW pochodzi od GX_WIDGET i obsługuje wszystkie gx_widget usługi interfejsu API.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do bloku sterowania oknem
- **Nazwa** Nazwa logiczna okna
- **element nadrzędny** Wskaźnik do elementu nadrzędnego widget
- **styl** Styl okna. **Dodatek D** zawiera wstępnie zdefiniowane style ogólne dla wszystkich elementów widget, a także style charakterystyczne dla widżetu.
- **window_id** Zdefiniowany przez aplikację identyfikator okna
- **rozmiar** Rozmiar okna

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne utworzenie okna **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_WINDOW my_window;

/* Create window “my_window”. */
status = gx_window_create(&my_window, "my window",
                          &my_parent_window, GX_STYLE_BORDER_RAISED,
                          MY_WINDOW_ID, &size);

/* If status is GX_SUCCESS window “my_window” has been created. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_draw"></a>gx_window_draw
### <a name="draw-window"></a>Okno rysowania

### <a name="prototype"></a>Prototype

```C
VOID gx_window_draw(GX_WINDOW *window);
```

### <a name="description"></a>Opis

Ta usługa rysuje okno. Ta usługa jest zwykle wywoływana wewnętrznie podczas odświeżania kanwy, ale może być również wywoływana z funkcji niestandardowego rysowania okna.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do bloku sterowania oknem

### <a name="return-values"></a>Wartości zwrócone

- **Brak**

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Write a custom window draw function. */

VOID my_custom_window_draw(GX_WINDOW *window)
{
    /* Call default window draw. */
    gx_window_draw(window);

    /* Add your own drawing here. */
}
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_event_process"></a>gx_window_event_process
### <a name="process-window-event"></a>Zdarzenie okna procesu

### <a name="prototype"></a>Prototype

```C
UINT gx_window_event_process(
    GX_WINDOW *window, 
    GX_EVENT *event);
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenie dla tego okna.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do bloku sterowania oknem
- **zdarzenie** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- Zakończono przetwarzanie zdarzenia okna **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic window event processing as part of custom event processing function. */

UINT custom_window_event_process(GX_WINDOW *window,
                                 GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
        case xyz:
            /* Insert custom event handling here */
            break;
        default:
            /* Pass all other events to the default window
            event processing */
            status = gx_window_event_process(window, event);
            break;
        }
        return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_execute"></a>gx_window_execute
### <a name="modally-execute-a-window"></a>Modalne wykonywanie okna

### <a name="prototype"></a>Prototype

```C
UINT gx_window_execute(
    GX_WINDOW *window,
    ULONG *return_ptr)
```

### <a name="description"></a>Opis

Ta usługa modalnie wykonuje okno. Wszystkie dane wejściowe użytkownika (zdarzenia pióra itp.) poza obszarem klienta okna zostaną zignorowane. Należy zauważyć, że ta funkcja wprowadza ciągłą pętlę wykonywania i nie wraca do obiektu wywołującego do momentu zakończenia wykonywania modelu.

Wykonywanie modalne kończy się, gdy przetwarzanie zdarzeń dla każdego odebranego zdarzenia zwróci wartość stanu różną od zera lub gdy zostanie wywołana funkcja interfejsu API gx_window_close. Kod powrotu niezerowego przetwarzania zdarzeń jest zwracany do obiektu wywołującego za pomocą return_ptr przekazana do tego interfejsu API

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do bloku sterowania oknem
- **return_ptr** Lokalizacja do zapisania stanu zakończenia wykonywania operacji modalnych. Może być GX_NULL.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne wykonanie **GX_SUCCESS** (0x00)
- **GX_SYSTEM_EVENT_RECEIVE_ERROR (0x05)** Odbiór zdarzenia z kolejki zdarzeń nie powiodło się
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Execute a modal window. */
status = gx_window_execute(&my_window, &return_code);

/* If status is GX_SUCCESS the window was executed, and return_code holds the execution return code. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_create"></a>gx_window_root_create
### <a name="create-a-root-window"></a>Utwórz okno główne

### <a name="prototype"></a>Prototype

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_CONST GX_CHAR *name,
    GX_CANVAS *canvas, 
    ULONG style,
    USHORT id,
    GX_CONST GX_RECTANGLE *size)
```

### <a name="description"></a>Opis

Ta usługa tworzy okno główne.

### <a name="parameters"></a>Parametry

- **root_window** Wskaźnik do bloku sterowania oknem głównym

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie utworzyła okno główne
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- **GX_INVALID_SIZE** (0X19) Nieprawidłowy rozmiar bloku kontrolki widget
- Element widget **GX_ALREADY_CREATED** (0x13) został już utworzony

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_ROOT_WINDOW root_window;
GX_CANVAS canvas;

/* Create canvas here. */

/* Create a root window */
status = gx_window_root_create(&root_window, “root”, &canvas,
GX_STYLE_BORDER_NONE, GX_NULL, &size);

/* If status is GX_SUCCESS, the “root_window” is successfully created. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find

## <a name="gx_window_root_delete"></a>gx_window_root_delete
### <a name="destroy-a-root-window"></a>Niszczenie okna głównego

### <a name="prototype"></a>Prototype

```C
UINT gx_window_root_delete(GX_WINDOW_ROOT *root_window)
```

### <a name="description"></a>Opis

Ta usługa usuwa okno główne.

### <a name="parameters"></a>Parametry

- **root_window** Wskaźnik do bloku sterowania oknem głównym

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie usunął okno główne
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- Funkcja wolnych pamięci **GX_SYSTEM_MEMORY_ERROR** (0x30) nie jest zdefiniowana

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Delete a root window */
status = gx_window_root_delete(&root_window);

/* If status is GX_SUCCESS the “root_window” is destroyed. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_event_process"></a>gx_window_root_event_process
### <a name="process-event-for-the-root-window"></a>Przetwarzaj zdarzenie dla okna głównego

### <a name="prototype"></a>Prototype

```C
UINT gx_window_root_create(
    GX_WINDOW_ROOT *root_window,
    GX_EVENT *event)
```

### <a name="description"></a>Opis

Ta usługa przetwarza zdarzenia dla określonego okna głównego.

### <a name="parameters"></a>Parametry

- **root_window** Wskaźnik do bloku sterowania oknem głównym
- **zdarzenie** Wskaźnik do zdarzenia do przetworzenia

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślnie przetworzył zdarzenie głównego okna
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```C
/* Call generic root window event processing as part of custom event processing function. */

UINT custom_root_window_event_process(GX_ROOT_WINDOW *root,
                                      GX_EVENT *event)
{
    UINT status = GX_SUCCESS;

    switch(event->gx_event_type)
    {
    case xyz:
        /* Insert custom event handling here */
        break;
    default:
        /* Pass all other events to the default root window
            event processing */
        status = gx_window_root_event_process(root, event);
        break;
    }
    return status;
}
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_root_find"></a>gx_window_root_find
### <a name="find-root-window"></a>Znajdź okno główne

### <a name="prototype"></a>Prototype

```C
UINT gx_window_root_find(
    GX_WIDGET *widget,
    GX_WINDOW_ROOT **return_root_window);
```

### <a name="description"></a>Opis

Ta usługa umożliwia znalezienie okna głównego określonego widżetu.

### <a name="parameters"></a>Parametry

- element **widget** Wskaźnik do bloku kontrolki elementu widget
- **return_root_window** Wskaźnik do miejsca docelowego dla znalezionego okna głównego

### <a name="return-values"></a>Wartości zwrócone

- **GX_SUCCESS** (0X00) pomyślne znalezienie okna głównego
- Okno główne **GX_FAILURE** (0x00) nie istnieje
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Find root window associated with window “my_window”. */
status = gx_window_root_find(&my_window, &root_window);

/* If status is GX_SUCCESS the “root_window” contains the root window for window “my_window”. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_scroll_info_get"></a>gx_window_scroll_info_get
### <a name="get-window-scroll-info"></a>Pobierz informacje przewijania okna

### <a name="prototype"></a>Prototype

```C
UINT gx_window_scroll_info_get(
    GX_WINDOW *window, 
    ULONG style,
    GX_SCROLL_INFO *return_scroll_info);
```

### <a name="description"></a>Opis

Ta usługa pobiera informacje o przewinięciu okna.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do okna
- **styl** GX_SCROLLBAR_HORIZONTAL lub GX_SCROLLBAR_VERTICAL
- **return_scroll_info** Wskaźnik do miejsca docelowego dla informacji przewijania. Okno nadrzędne inicjuje tę strukturę, aby poinformować pasek przewijania o łącznym rozmiarze okna nadrzędnego, widocznym obszarze i przyrostie przewijania. Domyślna implementacja używa obszaru klienckiego systemu Windows jako obszaru możliwego do wyświetlania i przewijania według pikseli, ale dostosowana implementacja okna może korzystać z parametrów przewijania. **Dodatek I** zawiera definicję struktury GX_SCROLL_INFO

### <a name="return-values"></a>Wartości zwrócone

- Pobieranie informacji o pomyślnym przewinięciu okna **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- Nieprawidłowy typ **GX_INVALID_TYPE** (0x1B)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_SCROLL_INFO scroll_info;

/* Get scroll information for window “my_window”. */
status = gx_window_scroll_info_get(&my_window,
                    GX_SCROLLBAR_HORIZONTAL, &scroll_info);

/* If status is GX_SUCCESS the “scroll_info” contains the scroll information for window “my_window”. */
```
### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scrollbar_find
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_scrollbar_find"></a>gx_window_scrollbar_find
### <a name="find-window-scrollbar"></a>Znajdź pasek przewijania okna

### <a name="prototype"></a>Prototype

```C
UINT gx_window_scrollbar_find(
    GX_WINDOW *window, 
    USHORT type,
    GX_SCROLLBAR **return_scrollbar);
```

### <a name="description"></a>Opis

Ta usługa znajduje pasek przewijania dla określonego okna.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do okna
- **Typ** GX_TYPE_VERTICAL_SCROLL lub GX_TYPE_HORIZONTAL_SCROLL
- **return_scrollbar** Wskaźnik do miejsca docelowego dla paska przewijania

### <a name="return-values"></a>Wartości zwrócone

- Odnalezienie pomyślnego paska przewijania okna **GX_SUCCESS** (0x00)
- Nie znaleziono paska przewijania **GX_NOT_FOUND** (0x09)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy
- Nieprawidłowy typ **GX_INVALID_TYPE** (0x1B)

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Find horizontal scrollbar for window “my_window”. */
status = gx_window_scrollbar_find(&my_window,
                 GX_SCROLLBAR_HORIZONTAL, &my_scrollbar);

/* If status is GX_SUCCESS the “my_scrollbar” contains the horizontal scrollbar for window “my_window”. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_wallpaper_get
- gx_window_wallpaper_set

## <a name="gx_window_wallpaper_get"></a>gx_window_wallpaper_get
### <a name="get-window-wallpaper"></a>Pobierz tapetę okna

### <a name="prototype"></a>Prototype

```C
UINT gx_window_wallpaper_get(
    GX_WINDOW *window,
    GX_RESOURCE_ID *return_wallpaper_id);
```

### <a name="description"></a>Opis

Ta usługa pobiera tapetę dla określonego okna.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do okna
- **return_wallpaper_id** Wskaźnik do miejsca docelowego dla identyfikatora zasobu Tapety

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne pobieranie Tapety okna **GX_SUCCESS** (0x00)
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
GX_RESOURCE_ID my_window_wallpaper;

/* Get wallpaper for window “my_window”. */
status = gx_window_wallpaper_get(&my_window, &my_window_wallpaper);

/* If status is GX_SUCCESS the “my_window_wallpaper” contains the wallpaper resource ID for window “my_window”. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
- gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_set

## <a name="gx_window_wallpaper_set"></a>gx_window_wallpaper_set
### <a name="set-window-wallpaper"></a>Ustaw tapetę okna

### <a name="prototype"></a>Prototype

```C
UINT gx_window_wallpaper_set(
    GX_WINDOW *window,
    GX_RESOURCE_ID wallpaper_id,
    GX_BOOL tile);
```

### <a name="description"></a>Opis

Ta usługa ustawia tapetę dla określonego okna.

### <a name="parameters"></a>Parametry

- **okno** Wskaźnik do okna
- **wallpaper_id** Identyfikator zasobu tapety do użycia
- **kafelek** Tapeta jest rozmieszczana w przypadku GX_TRUE, w przeciwnym razie tapeta nie jest rozrozmieszczana

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne ustawienie tapety okna **GX_SUCCESS** (0x00)
- **GX_CALLER_ERROR** (0X11) Nieprawidłowy obiekt wywołujący tej funkcji
- **GX_PTR_ERROR** (0X07) Nieprawidłowy wskaźnik
- Element widget **GX_INVALID_WIDGET** (0x12) jest nieprawidłowy

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacje i wątki

### <a name="example"></a>Przykład

```C
/* Set wallpaper for window “my_window”. */
status = gx_window_wallpaper_set(&my_window,
                                 MY_WALLPAPER_RESOURCE_ID,
                                 GX_TRUE);

/* If status is GX_SUCCESS the wallpaper for window “my_window” is set. */
```

### <a name="see-also"></a>Zobacz też

- gx_window_canvas_set
- gx_window_client_height_get
- gx_window_client_scroll
- gx_window_client_width_get
- gx_window_create
- gx_window_draw
- gx_window_event_process
- gx_window_root_create
- gx_window_root_delete
- gx_window_root_event_process
- gx_window_root_find
-  gx_window_scroll_info_get
- gx_window_scrollbar_find
- gx_window_wallpaper_get
