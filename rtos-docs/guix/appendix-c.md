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
# <a name="appendix-c---guix-widget-styles"></a>Dodatek C — style widżetu GUIX

__***Ogólne Style (używane z większością typów widżetów):***__

**GX_STYLE_BORDER_NONE**
  - Wartość: 0x00000000
  - Opis: ten styl służy do rysowania widżetu bez obramowania.

**GX_STYLE_BORDER_RAISED**
  - Wartość: 0x00000001
  - Opis: element widget rysowania z podniesionym obramowaniem.

**GX_STYLE_BORDER_RECESSED**
  - Wartość: 0x00000002
  - Opis: element widget rysowania z wgłębieniem.

**GX_STYLE_BORDER_THIN**
  - Wartość: 0x00000004
  - Opis: Rysuj obramowanie o szerokości jednopikselowej.

**GX_STYLE_BORDER_THICK** 
  - Wartość: 0x00000008
  - Opis: element widget rysowania o grubej krawędzi.

**GX_STYLE_BORDER_MASK**
  - Wartość: 0x0000000f
  - Opis: wartość maski używana do testowania tylko pól stylu elementu członkowskiego stylu widżetu.

**GX_STYLE_TRANSPARENT**
  - Wartość: 0x10000000
  - Opis: Utwórz widżet, który jest co najmniej częściowo przezroczysty. Ten styl powinien być używany, gdy widżet nie rysuje w pełni nieprzezroczysty, w tym widżetów, które rysują półprzezroczysty Pixelmap jako tło widżetu. Ta flaga stylu informuje GUIX, że element nadrzędny widget musi być rysowany w celu odświeżenia obszaru tła widżetu.

**GX_STYLE_DRAW_SELECTED**
  - Wartość: 0x20000000
  - Opis: Określ, czy element widget ma być rysowany przy użyciu wybranych kolorów i czcionek stanu. Różne typy widżetów używają stylu DRAW_SELECTED na różne sposoby wskazywania widżetu jest aktualnie zaznaczone.

**GX_STYLE_ENABLED**
  - Wartość: 0x40000000
  - Opis: Oznacz widżet jako włączony, co pozwala widżetowi akceptować zdarzenia wejściowe użytkownika i generować sygnały wyjściowe.
  
**GX_STYLE_DYNAMICALLY_ALLOCATED**
  - Wartość: 0x80000000
  - Opis: wskazuje, że pamięć blokowa kontrolki widżetu jest przydzielana dynamicznie przy użyciu usługi gx_system_memory_allocator podczas tworzenia elementu widget, a pamięć bloku sterowania jest zwalniana, jeśli widżet zostanie zniszczony.

**GX_STYLE_USE_LOCAL_ALPHA**
  - Wartość: 0x01000000
  - Opis: instruuje funkcje rysowania GUIX do użycia lokalnej wartości alfa widżetu podczas rysowania widżetu. Ta flaga jest zwykle używana przez wewnętrzną logikę GUIX do implementowania animacji zanikania elementu widget.


__***Style wyrównania tekstu (style zastosowane do wszystkich elementów widget, które rysują tekst):***__

**GX_STYLE_TEXT_LEFT**
  - Wartość: 0x00001000
  - Opis: tekst jest rysowany wyrównany do lewej w obszarze klienta widżetu.

**GX_STYLE_TEXT_RIGHT** 
  - Wartość: 0x00002000
  - Opis: tekst jest rysowany do prawej strony w obszarze klienta widżetu.

**GX_STYLE_TEXT_CENTER**
  - Wartość: 0x00004000
  - Opis: tekst jest rysowany jako wyrównany do środka w obszarze klienta widżetu.

**GX_STYLE_TEXT_COPY**
  - Wartość: 0x00008000
  - Opis: Domyślnie elementy widget, które rysują tekst, zachowują tylko wskaźnik do tekstu, który jest przesyłany przez aplikację. Dla statycznie zdefiniowanego tekstu, który jest zdefiniowany w tabeli ciągów, nie istnieje powód, aby element widget miał prywatną kopię przypisanego tekstu. Jeśli jednak tekst przypisany do widżetu jest tworzony dynamicznie przy użyciu funkcji, takich jak przebieg () lub gx_utility_ltoa, to często wygodniejsze jest poinformowanie widżetu, aby zachować jego prywatną kopię dowolnego przypisanego tekstu. Dzięki temu aplikacja może używać zmiennych automatycznych lub tymczasowych podczas definiowania ciągu tekstowego, gdy w przeciwnym razie aplikacja będzie wymagała zdefiniowania statycznie zdefiniowanych tablic znaków dla każdego widżetu tekstu, który używa dynamicznie zdefiniowanego tekstu. Gdy ta flaga stylu zostanie ustawiona, widżet użyje funkcji gx_system_memory_allocator do dynamicznego przydzielenia bloku pamięci wymaganego do przechowywania prywatnej kopii przypisanego ciągu. W związku z tym użycie tej flagi stylu jest oznaczane przez aplikację definiującą memory_allocator i memory_deallocator funkcje. GX_STYLE_TEXT_COPY nie powinno być czyszczone po ustawieniu i dlatego spowoduje to nieprzewidywalne wyniki.

__***Style przycisków (Zastosuj tylko do typów widżetów GUIX Button):***__

**GX_STYLE_BUTTON_PUSHED**
  - 0x00000010 wartości
  - Opis: wskazuje, że przycisk jest w stanie wypchnięcie lub zaznaczone.

**GX_STYLE_BUTTON_TOGGLE**
  - 0x00000020 wartości
  - Opis: przycisk powoduje przełączenie stanu między wypychaniem i wypchnięciem po każdym kliknięciu zdarzenia. Ten styl jest często używany z przyciskami stylu "CheckBox".

**GX_STYLE_BUTTON_RADIO**
  - 0x00000040 wartości
  - Opis: ten styl wskazuje, że przycisk będzie wyłączny, i usuń zaznaczenie dowolnego elementu równorzędnego przycisku po zaznaczeniu. Ten styl jest często używany z przycisków opcji stylu "przycisk radiowy".

**GX_STYLE_BUTTON_EVENT_ON_PUSH**
  - Wartość: 0x00000080
  - Opis: wskazuje, że przycisk generuje zdarzenie kliknięcia po pierwszym wypchnięciu. Domyślną operacją jest wygenerowanie zdarzenia kliknięcia po wydaniu przycisku.

**GX_STYLE_BUTTON_REPEAT**
  - 0x00000100 wartości
  - Opis: wskazuje, że przycisk powinien wysyłać powtarzające się zdarzenia kliknięcia do elementu nadrzędnego przycisku, gdy przycisk jest przechowywany w stanie pushd.

__***Style list (dotyczy tylko typów widżetów listy GUIX):***__

**GX_STYLE_CENTER_SELECTED** 
  - Wartość: 0x00000010
  - Opis: zastrzeżony

**GX_STYLE_WRAP**
  - 0x00000020 wartości
  - Opis: elementy podrzędne listy są zawijane od początku do końca, gdy lista jest przeciągana lub przewijana poza indeks listy początkowej lub końcowej.

**GX_STYLE_FLICKABLE**
  - Wartość: 0x00000040
  - Opis: zastrzeżony

__***Przycisk Pixelmap i style przycisków ikon:***__

**GX_STYLE_HALIGN_CENTER**
  - Wartość: 0x00010000
  - Opis: przycisk Pixelmap powinien być wyrównany do środka w granicy przycisku na osi poziomej.

**GX_STYLE_HALIGN_LEFT**
  - Wartość: 0x00020000
  - Opis: przycisk Pixelmap powinien być wyrównany do lewej w obrębie granicy przycisku na osi poziomej.

**GX_STYLE_HALIGN_RIGHT**
  - 0x00040000 wartości
  - Opis: przycisk Pixelmap powinien być wyrównany do prawej w granicach przycisku na osi poziomej.

**GX_STYLE_VALIGN_CENTER**
  - 0x00080000 wartości
  - Opis: przycisk Pixelmap powinien być wyrównany do środka w granicy przycisku na osi pionowej.

**GX_STYLE_VALIGN_TOP**
  - Wartość: 0x00100000
  - Opis: przycisk Pixelmap powinien być wyrównany do góry w obrębie granicy przycisku na osi pionowej.

**GX_STYLE_VALIGN_BOTTOM**
  - Wartość: 0x00200000
  - Opis: przycisk Pixelmap powinien być wyrównany do dołu w ramach granicy przycisku na pionowej osi poziomej.

__***Style suwaka (Appy tylko do GX_SLIDER i pochodnych typów widżetów):***__

**GX_STYLE_SHOW_NEEDLE**
  - Wartość: 0x00000200
  - Opis: ten styl musi być dołączony do suwaka, aby narysować wskaźnik wskazówki. Ten styl można wyłączyć, jeśli aplikacja chce wyłączyć wskazówki suwaka lub narysować niestandardowy wskaźnik wskazówki.

**GX_STYLE_SHOW_TICKMARKS**
  - Wartość: 0x00000400
  - Opis: widżet Slider wykona rysowanie oprogramowania linii znaczników kreskowanych, gdy ten styl jest włączony.

**GX_STYLE_SLIDER_VERTICAL**
  - 0x00000800 wartości
  - Opis: Ustaw tę flagę stylu, aby utworzyć pionowy suwak, i wyczyść flagę tego stylu, aby utworzyć suwak poziomy.

__***Style ikon (dotyczy tylko typów widżetów GX_SPRITE):***__

**GX_STYLE_SPRITE_AUTO**
  - Wartość: 0x00000010
  - Opis: wskazuje, że animacja Sprite zostanie uruchomiona automatycznie, gdy widżet Sprite otrzyma zdarzenie GX_EVENT_SHOW.

**GX_STYLE_SPRITE_LOOP**
  - Wartość: 0x00000020
  - Opis: w tym stylu widżet Sprite będzie ciągle przechodził do pętli przez klatki animacji Sprite, dopóki Sprite nie zostanie zatrzymany przez aplikację.

__***Style suwaka Pixelmap:***__

**GX_STYLE_TILE_BACKGROUND**
  - 0x00001000 wartości
  - Opis: obraz tła suwaka jest rozsunięty, aby wypełnić prostokąt powiązany z ikoną. Dzięki temu mały pionowy lub poziomy obraz rozłożony będzie używany do wypełnienia tła suwaka.

__***Dodatkowe style paska postępu:***__

**GX_STYLE_PROGRESS_PERCENT**
  - Wartość: 0x00000010
  - Opis: po ustawieniu tego stylu pasek postępu będzie miał wartość procentową, a nie wartość pierwotną. Tekst jest wyśrodkowany w prostokącie związanym z paskiem postępu.

**GX_STYLE_PROGRESS_TEXT_DRAW**
  - Wartość: 0x00000020
  - Opis: Narysuj bieżącą wartość paska postępu jako tekst dziesiętny wyśrodkowany na pasku postępu.

**GX_STYLE_PROGRESS_VERTICAL**
  - Wartość: 0x0000040
  - Opis: wskazuje, że postęp ma orientację w pionie. Wartość domyślna to orientacja pozioma.

**GX_STYLE_PROGRESS_SEGMENT_FILL**:
  - **Wartość**: 0x00000100
  - Opis: wartość paska postępu jest wskazywana przy użyciu wypełnionych prostokątów, a nie wypełnienia pełnego.

__***Dodatkowe style paska postępu promieniowego:***__

**GX_STYLE_RADIAL_PROGRESS_ALIAS**
  - Wartość: 0x00000200
  - Opis: Narysuj Radialny pasek postępu przy użyciu stylów pędzla z wygładzaniem. Wymaga to większej przepustowości procesora, ale również zapewnia wrażenie wz. W przypadku docelowych wydajności procesora CPU, czyszczenie tej flagi stylu spowoduje szybsze Rysowanie.

**GX_STYLE_RADIAL_PROGRESS_ROUND**
  - Wartość: 0x00000400
  - Opis: podczas rysowania łuku słupkowego postępu należy używać stylu pędzla okrągłego. Wartość domyślna to kwadratowy koniec linii.

__***Dodatkowe style wprowadzania tekstu:***__

**GX_STYLE_ CURSOR_BLINK**
  - Wartość: 0x00000040
  - Opis: kursor widżetu wprowadzanie tekstu zostanie włączony i wyłączony, a nie jest stały.

**GX_STYLE_ CURSOR_ALWAYS**
  - Wartość: 0x00000080
  - Opis Kursor widżetu wprowadzanie tekstu jest zwykle wyświetlany tylko wtedy, gdy widżet jest właścicielem fokusu. Ta flaga stylu sprawia, że kursor będzie zawsze widoczny niezależnie od fokusu danych wejściowych.

**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**
  - Wartość: 0x00000100
  - Opis: w przypadku tej flagi stylu Ustaw zdarzenie GX_EVENT_TEXT_EDITED za każdym razem, gdy zdarzenie w dół jest odbierane przez widżet wprowadzania tekstu.

__***Dodatkowe style okna:***__

**GX_STYLE_TILE_WALLPAPER**
  - Wartość: 0x00040000
  - Opis: w oknie zostanie umieszczony kafelek każdy przypisany obraz Tapety, aby wypełnić prostokąt klienta okna.

**GX_STYLE_AUTO_HSCROLL**
  - Wartość: 0x00100000
  - Opis: zarezerwowane do użytku w przyszłości.

**GX_STYLE_AUTO_VSCROLL**
  - Wartość: 0x00200000
  - Opis: zarezerwowane do użytku w przyszłości.

__***Dodatkowe style menu:***__

**GX_STYLE_MENU_EXPANDED**
  - Wartość: 0x00000010
  - Opis: widżet menu harmonijka jest początkowo w stanie rozwiniętym.

__***Dodatkowe style widoku drzewa:***__

**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**
  - Wartość: 0x00000010
  - Opis: widżet widoku drzewa powinien rysować linie z ikony węzła do węzła drzewa głównego.

__***Dodatkowe style paska przewijania:***__

**GX_SCROLLBAR_BACKGROUND_TILE**
  - Wartość: 0x00010000
  - Opis: zarezerwowane do użytku w przyszłości.

**GX_SCROLLBAR_RELATIVE_THUMB**
  - Wartość: 0x00020000
  - Opis: szerokość przycisku przewijania ekranu (dla poziomego paska przewijania) lub wysokość (dla pionowego paska przewijania) jest obliczana na podstawie współczynnika widocznego obszaru okna nadrzędnego do minimalnej i maksymalnej wartości paska przewijania.

**GX_SCROLLBAR_END_BUTTONS**
  - Wartość: 0x00040000
  - Opis: pasek przewijania automatycznie tworzy i dołącza przyciski na każdym końcu regionu ScrollBar.

**GX_SCROLLBAR_VERTICAL** 
  - Wartość: 0x01000000
  - Opis: pasek przewijania ma orientację w pionie.

**GX_SCROLLBAR_HORIZONTAL**
  - Wartość: 0x02000000
  - Opis: pasek przewijania ma orientację poziomą.

__***Style kółka przewijania tekstu:***__

**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**
  - Wartość: 0x00000200
  - Opis: kółko przewijania używa algorytmu sinusoidalną, aby kółko przewijania pojawiało się w postaci zaokrąglonego kształtu. Ta flaga stylu może zwiększyć znaczący koszt do wydajności widgetu kółka przewijania, ale może również dać kółko realistyczny wygląd 3W.