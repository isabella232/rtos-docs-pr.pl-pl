---
title: Dodatek C — Style widżetu GUIX
description: Dowiedz się więcej o stylach widżetu GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9519d68af64b777e34deb1bf11e6962e78a96b86bdbfd90f5b379c5b56c92268
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784652"
---
# <a name="appendix-c---guix-widget-styles"></a>Dodatek C — Style widżetu GUIX

__***Style ogólne (używane z większość typów widżetów):***__

**GX_STYLE_BORDER_NONE**
  - Wartość: 0x00000000
  - Opis: użyj tego stylu, aby narysować widżet bez obramowania.

**GX_STYLE_BORDER_RAISED**
  - Wartość: 0x00000001
  - Opis: Rysowanie widżetu z podniesionym obramowaniem.

**GX_STYLE_BORDER_RECESSED**
  - Wartość: 0x00000002
  - Opis: Rysowanie widżetu z reced obramowaniem.

**GX_STYLE_BORDER_THIN**
  - Wartość: 0x00000004
  - Opis: Rysowanie obramowania o szerokości jednego piksela.

**GX_STYLE_BORDER_THICK** 
  - Wartość: 0x00000008
  - Opis: Rysowanie widżetu o grubym obramowaniu.

**GX_STYLE_BORDER_MASK**
  - Wartość: 0x0000000f
  - Opis: Wartość maski używana do testowania tylko pól stylu elementu członkowskiego stylu widżetu.

**GX_STYLE_TRANSPARENT**
  - Wartość: 0x10000000
  - Opis: Utwórz widżet, który jest co najmniej częściowo przezroczysty. Tego stylu należy używać, gdy widżet nie jest w pełni nieprzezroczysty, w tym widżety, które narysują półprzezroczystą mapę pikseli jako tło widżetu. Ta flaga stylu informuje interfejs GUIX, że element nadrzędny widżetu musi być rysowany, aby odświeżyć obszar tła widżetu.

**GX_STYLE_DRAW_SELECTED**
  - Wartość: 0x20000000
  - Opis: określ, że widżet powinien być rysowany przy użyciu kolorów i czcionek wybranego stanu. Różne typy widżetów używają DRAW_SELECTED na różne sposoby, aby wskazać, że widżet jest aktualnie wybrany.

**GX_STYLE_ENABLED**
  - Wartość: 0x40000000
  - Opis: Oznacz widżet jako włączony, co umożliwia widżetowi akceptowanie zdarzeń wejściowych użytkownika i generowanie sygnałów wyjściowych.
  
**GX_STYLE_DYNAMICALLY_ALLOCATED**
  - Wartość: 0x80000000
  - Opis: wskazuje, że pamięć bloku kontrolki widżetu jest przydzielana dynamicznie przy użyciu usługi gx_system_memory_allocator podczas tworzenia widżetu, a pamięć bloku sterowania jest wolnej w przypadku zniszczenia widżetu.

**GX_STYLE_USE_LOCAL_ALPHA**
  - Wartość: 0x01000000
  - Opis: instruuje funkcje rysowania GUIX, aby podczas rysowania widżetu używać lokalnej wartości alfa widżetu. Ta flaga jest zwykle używana przez wewnętrzną logikę GUIX do implementowania animacji zanikania widżetu.


__***Style wyrównania tekstu (style stosowane do wszystkich widżetów, które rysować tekst):***__

**GX_STYLE_TEXT_LEFT**
  - Wartość: 0x00001000
  - Opis: Tekst jest rysowany do lewej w obszarze klienta widżetu.

**GX_STYLE_TEXT_RIGHT** 
  - Wartość: 0x00002000
  - Opis: Tekst jest rysowany do prawej strony w obszarze klienta widżetu.

**GX_STYLE_TEXT_CENTER**
  - Wartość: 0x00004000
  - Opis: Tekst jest rysowany do środka w obszarze klienta widżetu.

**GX_STYLE_TEXT_COPY**
  - Wartość: 0x00008000
  - Opis: domyślnie widżety, które rysują tekst, przechowują tylko wskaźnik do tekstu przekazanego przez aplikację. W przypadku statycznie zdefiniowanego tekstu zdefiniowanego w tabeli ciągów nie ma powodu, aby widżet porządkował prywatną kopię przypisanego tekstu. Jeśli jednak tekst przypisany do widżetu jest tworzony dynamicznie przy użyciu funkcji takich jak sprint() lub gx_utility_ltoa, często wygodnie jest poinformować widżet, aby zachować własną prywatną kopię dowolnego przypisanego tekstu. Dzięki temu aplikacja może używać zmiennych automatycznych lub tymczasowych podczas definiowania ciągu tekstowego, gdy w przeciwnym razie aplikacja będzie wymagać zdefiniowania statycznie zdefiniowanych tablic znaków dla każdego widżetu tekstu używającego tekstu zdefiniowanego dynamicznie. Gdy ta flaga stylu jest ustawiona, widżet użyje funkcji gx_system_memory_allocator do dynamicznego przydzielania bloku pamięci potrzebnego do przechowywania prywatnej kopii przypisanego ciągu. W związku z tym użycie tej flagi stylu jest predykatem aplikacji definiującej memory_allocator i memory_deallocator funkcji. GX_STYLE_TEXT_COPY nie powinny zostać wyczyszone po jego skonfigurowaniu, co spowoduje nieprzewidywalne wyniki.

__***Style przycisku (mają zastosowanie tylko do typów widżetów przycisków GUIX):***__

**GX_STYLE_BUTTON_PUSHED**
  - Wartość 0x00000010
  - Opis: wskazuje, że przycisk jest w stanie wypchniętą lub wybraną.

**GX_STYLE_BUTTON_TOGGLE**
  - Wartość 0x00000020
  - Opis: przycisk przełącza stan między wypchniętą i rozsyłaną przy każdym zdarzeniu kliknięcia. Ten styl jest często używany z przyciskami stylu "pole wyboru".

**GX_STYLE_BUTTON_RADIO**
  - Wartość 0x00000040
  - Opis: Ten styl wskazuje, że przycisk będzie wyłączny, i usuń zaznaczenie wszystkich elementów równorzędnych przycisku po wybraniu. Ten styl jest często używany z przyciskami stylu "przycisku radiowego".

**GX_STYLE_BUTTON_EVENT_ON_PUSH**
  - Wartość: 0x00000080
  - Opis: wskazuje, że przycisk generuje zdarzenie kliknięcia po początkowym wypchnięciu. Domyślną operacją jest wygenerowanie zdarzenia kliknięcia po zwolnieniu przycisku.

**GX_STYLE_BUTTON_REPEAT**
  - Wartość 0x00000100
  - Opis: wskazuje, że przycisk powinien wysyłać zdarzenia powtórzeń kliknięcia do elementu nadrzędnego przycisku, gdy przycisk jest w stanie wypchnięć.

__***Style listy (mają zastosowanie tylko do typów widżetów listy GUIX):***__

**GX_STYLE_CENTER_SELECTED** 
  - Wartość: 0x00000010
  - Opis: Zarezerwowane

**GX_STYLE_WRAP**
  - Wartość 0x00000020
  - Opis: Dzieci listy są zawijane od początku do końca, gdy lista jest przeciągowana lub przewijana przez początkowy lub końcowy indeks listy.

**GX_STYLE_FLICKABLE**
  - Wartość: 0x00000040
  - Opis: Zarezerwowane

__***Style przycisku Mapa pikseli i przycisku ikony:***__

**GX_STYLE_HALIGN_CENTER**
  - Wartość: 0x00010000
  - Opis: Mapa pikseli przycisku powinna być wyrównana do środka w obrębie granicy przycisku na osi poziomej.

**GX_STYLE_HALIGN_LEFT**
  - Wartość: 0x00020000
  - Opis: Mapa pikseli przycisku powinna być wyrównana do lewej wewnątrz granicy przycisku na osi poziomej.

**GX_STYLE_HALIGN_RIGHT**
  - Wartość 0x00040000
  - Opis: Mapa pikseli przycisku powinna być wyrównana do prawej wewnątrz granicy przycisku na osi poziomej.

**GX_STYLE_VALIGN_CENTER**
  - Wartość 0x00080000
  - Opis: Mapa pikseli przycisku powinna być wyśrodkowana w obrębie granicy przycisku na osi pionowej.

**GX_STYLE_VALIGN_TOP**
  - Wartość: 0x00100000
  - Opis: Mapa pikseli przycisku powinna być wyrównana do góry w obrębie granicy przycisku na osi pionowej.

**GX_STYLE_VALIGN_BOTTOM**
  - Wartość: 0x00200000
  - Opis: Mapa pikseli przycisku powinna być wyrównana do dołu w obrębie granicy przycisku na pionowej osi poziomej.

__***Style suwaka (appy tylko do GX_SLIDER i pochodne typy widżetów):***__

**GX_STYLE_SHOW_NEEDLE**
  - Wartość: 0x00000200
  - Opis: Ten styl musi być dołączony, aby suwak narysowył wskaźnik igły. Ten styl można wyłączyć, jeśli aplikacja chce wyłączyć igłę suwaka lub narysować niestandardowy wskaźnik wskaźników.

**GX_STYLE_SHOW_TICKMARKS**
  - Wartość: 0x00000400
  - Opis: widżet suwaka będzie rysować oprogramowanie linii znacznika znacznika kreskowego, gdy ten styl jest włączony.

**GX_STYLE_SLIDER_VERTICAL**
  - Wartość 0x00000800
  - Opis: ustaw tę flagę stylu, aby utworzyć suwak pionowy, i wyczyść tę flagę stylu, aby utworzyć suwak poziomy.

__***Style sprite (dotyczy tylko GX_SPRITE typów widżetów):***__

**GX_STYLE_SPRITE_AUTO**
  - Wartość: 0x00000010
  - Opis: wskazuje, że animacja sprite będzie uruchamiana automatycznie, gdy widżet sprite odebrał GX_EVENT_SHOW zdarzenia.

**GX_STYLE_SPRITE_LOOP**
  - Wartość: 0x00000020
  - Opis: W tym stylu widżet sprite będzie stale przechodzić w pętli przez ramki animacji sprite do momentu zatrzymania sprite przez aplikację.

__***Style suwaka mapy pikseli:***__

**GX_STYLE_TILE_BACKGROUND**
  - Wartość 0x00001000
  - Opis: obraz tła suwaka jest kafelkowany w celu wypełnienia prostokąta granicznego sprite'a. Dzięki temu mały pionowy lub poziomy obraz paska może służyć do wypełnienia tła suwaka.

__***Dodatkowe style paska postępu:***__

**GX_STYLE_PROGRESS_PERCENT**
  - Wartość: 0x00000010
  - Opis: gdy ten styl zostanie ustawiony, pasek postępu będzie rysować wartość słupka jako wartość procentową, a nie nieprzetworzioną. Tekst jest wyśrodkowany na prostokątze ograniczającym pasek postępu.

**GX_STYLE_PROGRESS_TEXT_DRAW**
  - Wartość: 0x00000020
  - Opis: Narysuj bieżącą wartość paska postępu jako tekst dziesiętny wyśrodkowany na pasku postępu.

**GX_STYLE_PROGRESS_VERTICAL**
  - Wartość: 0x0000040
  - Opis: wskazuje, że postęp jest zorientowany w pionie. Wartość domyślna to orientacja pozioma.

**GX_STYLE_PROGRESS_SEGMENT_FILL:**
  - **Wartość**: 0x00000100
  - Opis: Wartość paska postępu jest wskazywana za pomocą segmentowanych wypełnionych prostokątów, a nie z pełnym wypełnieniem.

__***Dodatkowe style paska postępu promieniowego:***__

**GX_STYLE_RADIAL_PROGRESS_ALIAS**
  - Wartość: 0x00000200
  - Opis: Narysuj pasek postępu promieniowego przy użyciu stylów pędzla o aliasach. Wymaga to większej przepustowości procesora, ale również zapewnia bardziej ładną wydajność. W przypadku celów procesora CPU o niższej wydajności wyczyszczenie tej flagi stylu spowoduje szybszą szybkość rysowania.

**GX_STYLE_RADIAL_PROGRESS_ROUND**
  - Wartość: 0x00000400
  - Opis: Użyj stylu pędzla z zaokrąglaną linią końcową podczas rysowania promieniowego słupka postępu. Wartość domyślna to koniec linii kwadratowej.

__***Dodatkowe style wprowadzania tekstu:***__

**GX_STYLE_ CURSOR_BLINK**
  - Wartość: 0x00000040
  - Opis: Kursor widżetu wprowadzania tekstu będzie się migał i wyłączał, a nie stałą.

**GX_STYLE_ CURSOR_ALWAYS**
  - Wartość: 0x00000080
  - Opis Kursor widżetu wprowadzania tekstu jest zwykle wyświetlany tylko wtedy, gdy element widget jest właścicielem fokusu wejściowego. Ta flaga stylu sprawi, że kursor będzie zawsze widoczny niezależnie od fokusu wejściowego.

**GX_STYLE_TEXT_INPUT_NOTIFY_ALL**
  - Wartość: 0x00000100
  - Opis: za pomocą tej flagi stylu ustaw GX_EVENT_TEXT_EDITED zdarzenia za każdym razem, gdy zdarzenie klawisza down zostanie odebrane przez widżet wprowadzania tekstu.

__***Dodatkowe style okna:***__

**GX_STYLE_TILE_WALLPAPER**
  - Wartość: 0x00040000
  - Opis: w oknie zostanie kafelkowany dowolny przypisany obraz tapety w celu wypełnienia prostokąta klienta okna.

**GX_STYLE_AUTO_HSCROLL**
  - Wartość: 0x00100000
  - Opis: Zarezerwowane do użytku w przyszłości.

**GX_STYLE_AUTO_VSCROLL**
  - Wartość: 0x00200000
  - Opis: Zarezerwowane do użytku w przyszłości.

__***Dodatkowe style menu:***__

**GX_STYLE_MENU_EXPANDED**
  - Wartość: 0x00000010
  - Opis: widżet menu Accordion jest początkowo w stanie rozwiniętym.

__***Dodatkowe style widoku drzewa:***__

**GX_STYLE_TREE_VIEW_SHOW_ROOT_LINES**
  - Wartość: 0x00000010
  - Opis: Widżet widoku drzewa powinien rysować linie z ikony węzła do głównego węzła drzewa.

__***Dodatkowe style paska przewijania:***__

**GX_SCROLLBAR_BACKGROUND_TILE**
  - Wartość: 0x00010000
  - Opis: Zarezerwowane do użytku w przyszłości.

**GX_SCROLLBAR_RELATIVE_THUMB**
  - Wartość: 0x00020000
  - Opis: Szerokość kciuka paska przewijania (w przypadku poziomego paska przewijania) lub wysokość (w przypadku pionowego paska przewijania) jest obliczana na podstawie proporcji widocznego obszaru okna nadrzędnego do minimalnego i maksymalnego zakresu paska przewijania.

**GX_SCROLLBAR_END_BUTTONS**
  - Wartość: 0x00040000
  - Opis: pasek przewijania automatycznie tworzy i dołącza przyciski na każdym końcu obszaru paska przewijania.

**GX_SCROLLBAR_VERTICAL** 
  - Wartość: 0x01000000
  - Opis: Pasek przewijania jest w orientacji pionowej.

**GX_SCROLLBAR_HORIZONTAL**
  - Wartość: 0x02000000
  - Opis: Pasek przewijania jest w orientacji poziomej.

__***Style kółka przewijania tekstu:***__

**GX_STYLE_TEXT_SCROLL_WHEEL_ROUND**
  - Wartość: 0x00000200
  - Opis: Koło przewijania używa algorytmu sinusoidalnego, aby koło przewijania było wyświetlane jako zaokrąglone. Ta flaga stylu może znacząco poprawić wydajność widżetu kółka przewijania, ale może również nadać kółka realistyczny wygląd 3D.