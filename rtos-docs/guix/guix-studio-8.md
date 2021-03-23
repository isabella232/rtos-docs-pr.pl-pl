---
title: Uwagi dotyczące edytowania określonych typów widżetu
description: Szczegółowe komentarze opisujące metody edycji dla niektórych złożonych typów elementów widget.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3194a1b8c8965bf821631a8c34ac5e9961f8c8ff
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823029"
---
# <a name="chapter-8-notes-on-editing-specific-widget-types"></a>Rozdział 8: uwagi dotyczące edytowania określonych typów widżetu

Program GUIX Studio umożliwia użytkownikowi łatwe tworzenie i modyfikowanie widżetów GUIX, które tworzą ekrany interfejsu użytkownika aplikacji. Większość z tych metod edycji jest intuicyjna i oczywista. Na przykład aby zmienić rozmiar widżetu, można wybrać widżet z myszą i przeciągnąć obramowania widżetu. Możesz również bezpośrednio wpisać pola właściwości left/top/width/Height wybranego widżetu.

Niektóre typy elementów widget wymagają bardziej zaawansowanego procesu edycji, ponieważ te widżety stanowią nieco bardziej zaawansowaną obsługę funkcji.

Ten rozdział zawiera informacje na temat bardziej zaawansowanych funkcji edycji dla tych bardziej złożonych typów widżetów. Te informacje zostaną rozmieszczone jako funkcje programu GUIX Studio z wyprzedzeniem i typami widżetów znajdującymi się w bibliotece GUIX.

## <a name="rich-text-view"></a>Widok tekstu sformatowanego

Ten widżet służy do wyświetlania tekstu sformatowanego, który obsługuje kody formatowania tekstu wbudowanego. Te kody formatowania obejmują pogrubienie, kursywę i kilka innych. Aby rozpocząć, kliknij prawym przyciskiem myszy wybrany element nadrzędny w *widoku projektu* lub *Widok docelowy* , a następnie wybierz polecenie menu **Wstaw/tekst/Rich Text** , aby wstawić widżet widoku tekstu sformatowanego.

Oprócz standardowego zestawu właściwości obsługiwanych przez wszystkie typy elementów widget typ widżetu widok tekstu sformatowanego obsługuje dodatkowe właściwości.

### <a name="additional-properties"></a>Dodatkowe właściwości

| Właściwość | Znaczenie |
|----------|---------|
| Wyrównanie tekstu | Domyślne wyrównanie tekstu |
| Czcionka normalna| Domyślna czcionka tekstu |
| Czcionka pogrubiona  | Czcionka tekstu oznaczona jako pogrubiona |
| Kursywa — czcionka| Czcionka tekstowa dla tekstu oznaczonego kursywą|
| Czcionka pogrubiona kursywą| Czcionka tekstowa dla tekstu oznaczonego pogrubioną i kursywą |
| Prywatna kopia do tekstu | Należy sprawdzić, czy widżet ma zachować własną prywatną kopię dowolnego tekstu przypisanego |
| Białe znaki | Szerokość marginesu między widżetem a wyświetlanym tekstem (w pikselach). |
| Miejsce w wierszu | Odstęp między dwoma wierszami tekstu (w pikselach). |
|||

### <a name="the-rich-text-formatting-codes"></a>Kody formatowania tekstu sformatowanego

W przypadku formatowania tekstu obsługiwane są następujące kody formatu.

|Tag|Znaczenie|
|---|---|
|\<b>\</b> | Renderuj czcionkę tekstu przy użyciu pogrubienia czcionki o określonym przez użytkownika|
|\<i>\</i> | Renderuj czcionkę tekstu za pomocą podanego przez użytkownika identyfikatora czcionki kursywy|
|\<u>\</u> | Renderowanie tekstu podkreślonego|
|\<f GX_FONT_ID>\</f> | Renderowanie tekstu przy użyciu podanego identyfikatora czcionki. |
|\<c GX_COLOR_ID>\</c> | Renderowanie tekstu przy użyciu określonego identyfikatora koloru|
|\<hc GX_COLOR_ID>\</hc> | Renderowanie tekstu przy użyciu określonego identyfikatora koloru tła|
|\<align left/right/center>\</align> | Przypisywanie wyrównania tekstu|
|||

Istnieją dwa sposoby edytowania ciągu tekstu sformatowanego z poziomu programu GUIX Studio:

- Użyj okna dialogowego Edytowanie tekstu sformatowanego, który jest zalecaną i najprostszą metodą edycji.
- Użyj okna dialogowego edytora tabeli ciągów, które pozwala na ręczne Wstawianie tagów formatowania pokazanych w powyższej tabeli.

Po wybraniu widżetu widok tekstu sformatowanego w *widoku cel* wybierz przycisk **Edytuj tekst sformatowany** w *widoku właściwości* , aby wywoływać okno dialogowe edycji tekstu sformatowanego, pokazane na rysunku 8,1.

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie tekstu sformatowanego w programie GUIX Studio.](./media/guix-studio/edit_rich_text_dialog.png)

**Rysunek 8,1**

Okienko po lewej stronie to pole edycji tekstu sformatowanego. Możesz użyć ikon paska narzędzi, aby ułatwić Wstawianie wymaganych tagów. Zaznacz dowolny blok tekstu w polu edycji, a następnie wybierz przyciski paska narzędzi, aby zastosować wymagane style i kolory do zaznaczonego bloku tekstu. Okno dialogowe Edytowanie tekstu sformatowanego jest łatwym sposobem wstawiania kodów formatowania do ciągu testowego. Możesz również wstawić te Tagi ręcznie lub nawet generować je w czasie wykonywania, jeśli jest to konieczne.

Prawe okienko jest podglądem widżetu, aby pokazać, jak tekst jest renderowany w widoku docelowym. Kolor tła podglądu widżetu został naprawiony, co może być niezgodne z przypisaną kolorem tła widżetu w widoku docelowym.

Nazwy identyfikatorów zasobów są używane w tekście sformatowanym do odwoływania się do określonych zasobów czcionek i kolorów. Jeśli nazwa zasobu czcionki lub koloru zostanie zmieniona po odwołaniu się do niego przez ciąg tekstu sformatowanego, program GUIX Studio automatycznie zaktualizuje ciąg tekstu sformatowanego, aby odzwierciedlić zmiany nazwy zasobu. Z drugiej strony, jeśli usuniesz czcionkę lub kolor koloru, do którego odwołuje się widżet tekstu sformatowanego, musisz ręcznie zmodyfikować zmieniony tekst sformatowany, aby usunąć lub zmienić nazwy identyfikatorów zasobów, które zostały usunięte.

Po wybraniu przycisku Zapisz w tym oknie dialogowym zdefiniowany ciąg tekstu sformatowanego zostanie dodany do tabeli ciągów projektu.

## <a name="string-scroll-wheel"></a>Kółko przewijania ciągów

Widżet do przewijania ciągu obsługuje wyświetlanie tablicy ciągów. Te ciągi mogą być dynamicznie przypisywane lub, w przypadku, gdy aplikacja obsługuje wiele języków, przypisane ciągi można ściągnąć z aktywnej tabeli ciągów.

Widżet przewijania tekstu obsługuje tablicę ciągów. Zostanie wyświetlone okno dialogowe edycji kółka przewijania ciągów, pokazane na rysunku 8,2.

![Zrzut ekranu przedstawiający okno dialogowe Edytuj kółko GUIX Studio.](./media/guix-studio/string_scroll_wheel_edit.png)

**Rysunek 8,2**

Aby wywołać to okno dialogowe, Wybierz widżet przewijania ciągu w *widoku docelowym* lub *widoku projektu*. Po wybraniu tego typu elementu widget w *widoku właściwości* zostanie umieszczony przycisk **Edytuj ciągi** . Wybierz ten przycisk, aby wywołać okno dialogowe edycji kółka przewijania ciągu.

Aby przypisać ciąg dla każdego indeksu tekstu, można wybrać identyfikator ciągu z listy rozwijanej lub wpisać nową wartość ciągu w polu tekstowym po prawej stronie. Po dokonaniu zmian wszystkie nowe lub zmodyfikowane ciągi są zapisywane w aktywnej tabeli ciągów.

## <a name="sprite"></a>Klasy

Widżet Sprite służy do wyświetlania sekwencji obrazów w celu zapewnienia efektu animacji. Widżet Sprite wymaga listy ramek, która jest tablicą identyfikatorów obrazów i unikatowych parametrów zastosowanych do każdego obrazu w ramce. Aby zbudować tę listę ramek dla widżetu Sprite, można wyświetlić okno dialogowe Edytowanie ramek Sprite, pokazane na rysunku 8,3:

![Zrzut ekranu przedstawiający okno dialogowe GUIX Studio Edit Sprite frames.](./media/guix-studio/edit_sprite_frames.png)

**Rysunek 8,3**

Aby wywołać to okno dialogowe, Wybierz widżet Sprite w *widoku docelowym* lub *widoku projektu*. Po wybraniu tego typu elementu widget w *widoku właściwości* będzie dostępny przycisk **Edytuj frameList** . Wybierz ten przycisk, aby wywołać okno dialogowe edycji kółka przewijania ciągu.

*Łączna liczba pól ramek Sprite* jest polem wejściowym umożliwiającym wprowadzanie całkowitej liczby ramek, które mają być wyświetlane przez widżet Sprite. Obrazy mogą być ponownie używane na liście ramek, co oznacza, że nie każdy obraz musi być unikatowy.

Pole Identyfikator ramki Sprite jest wartością wyboru indeksu ramki, która jest z zakresu od 1 do całkowitej liczby ramek. Zwiększ i zmniejsz tę wartość, aby przejść z jednej klatki Sprite do następnej.

Każda ramka Sprite ma kilka parametrów. Pierwszy jest operacją w tle. To pole służy do naśladowania możliwości popularnego formatu animacji GIF. Dostępne są następujące opcje:

- Brak operacji, co oznacza, że bieżący obraz ramki jest rysowany na poprzedniej ilustracji.
- Przywróć pierwszą mapę pikseli, co oznacza, że mapa pikseli indeksu 1 jest rysowana przed bieżącą mapą pikseli i
- Wypełnienie pełnego koloru, co oznacza, że tło Sprite jest wypełnione kolorem tła Sprite przed rysowaniem bieżącej ramki.

Pole ID mapy pikseli umożliwia wybranie dowolnej mapy pikseli, która została wcześniej dodana do zasobów projektu. Ten sam identyfikator mapy pikseli może być używany w przypadku wielu ramek. Na przykład animacja Sprite może wykorzystać Przenoszenie obrazu (przy użyciu pól przesunięcia x i y) zamiast lub oprócz innych obrazów Sprite.

Pole wartość alfa jest stosowane do całego rysunku mapy pikseli. To pole ma efekt tylko wtedy, gdy działa na 8 BPP głębi kolorów i wyższych. Wartość alfa 0 jest w pełni przezroczysta, a wartość alfa 255 jest nieprzezroczysta.

Możesz określić przesunięcie w ramce Sprite, w której bieżące mapy pikseli będą rysowane przy użyciu pól przesunięcia ramki x i przesunięcia ramki y. Innymi słowy, każdy rysowany obraz nie musi być pełnym rozmiarem widżetu Sprite.

Okres opóźnienia określa czas oczekiwania przed przejściem do następnej ramki Sprite. Ta wartość jest w taktach, co oznacza domyślną konfigurację czasomierza GUIX/ThreadX każdy takt reprezentuje 50 ms.

Po zapisaniu zmian w oknie dialogowym Edytowanie ramek Sprite GUIX Studio jest w stanie wygenerować tablicę kompletnej listy ramek jako część generowania pliku specyfikacji danych wyjściowych.
