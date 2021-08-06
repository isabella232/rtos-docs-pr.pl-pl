---
title: Uwagi dotyczące edytowania określonych typów widżetów
description: Szczegółowe komentarze opisujące metody edycji dla niektórych złożonych typów widżetów.
author: jdeere5220
ms.author: kemaxwel
ms.date: 9/30/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 374471df85c4cd0fffae5b5cc7ad31d2237877f2
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178286"
---
# <a name="chapter-8-notes-on-editing-specific-widget-types"></a>Rozdział 8. Uwagi dotyczące edytowania określonych typów widżetów

Program GUIX Studio umożliwia użytkownikowi łatwe tworzenie i modyfikowanie widżetów GUIX, które będą tworzyć ekrany interfejsu użytkownika aplikacji. Większość tych metod edycji jest intuicyjna i oczywista. Aby na przykład zmienić rozmiar widżetu, możesz wybrać widżet za pomocą myszy i przeciągnąć obramowanie widżetu. Możesz również bezpośrednio wpisać w polach właściwości left/top/width/height wybranego widżetu.

Niektóre typy widżetów wymagają bardziej zaawansowanego procesu edytowania, ponieważ same widżety są nieco bardziej zaawansowane w zakresie obsługi funkcji.

Ten rozdział zawiera uwagi dotyczące bardziej zaawansowanych funkcji edycji dla tych bardziej złożonych typów widżetów. Te uwagi będą rozszerzane wraz z rozwijaniem funkcji programu GUIX Studio wraz z typami widżetów dostarczanymi w bibliotece GUIX.

## <a name="rich-text-view"></a>Widok tekstu sformatowanego

Ten widżet służy do wyświetlania tekstu sformatowanego, który obsługuje wbudowane kody formatowania tekstu. Te kody formatowania obejmują pogrubienie, kursywę i kilka innych. Aby rozpocząć, kliknij prawym przyciskiem myszy wybrany element  nadrzędny w widoku Project *lub* widoku docelowym i wybierz menu **Wstaw/Tekst/Widok** sformatowany, aby wstawić widżet widoku tekstu sformatowanego.

Oprócz standardowego zestawu właściwości obsługiwanych przez wszystkie typy widżetów typ widżetu Widok sformatowany obsługuje dodatkowe właściwości.

### <a name="additional-properties"></a>Dodatkowe właściwości

| Właściwość | Znaczenie |
|----------|---------|
| Wyrównywanie tekstu | Domyślne wyrównanie tekstu |
| Normalna czcionka| Domyślna czcionka tekstowa |
| Czcionka pogrubiona  | Czcionka tekstu dla tekstu oznaczonego jako pogrubiona |
| Czcionka kursywa| Czcionka tekstu dla tekstu oznaczonego kursywą|
| Czcionka kursywa pogrubiona| Czcionka tekstu oznaczona jako pogrubiona i kursywa |
| Kopiowanie tekstu prywatnego | Należy sprawdzić, czy widżet ma zachować własną prywatną kopię dowolnego przypisanego tekstu |
| Białe znaki | Szerokość marginesu między widżetem i wyświetlanym tekstem w pikselach. |
| Przestrzeń wiersza | Odstęp między dwoma liniami tekstu w pikselach. |
|||

### <a name="the-rich-text-formatting-codes"></a>Kody formatowania tekstu sformatowanego

Następujące kody formatu są obsługiwane w przypadku formatowania tekstu.

|Tag|Znaczenie|
|---|---|
|\<b>\</b> | Renderuj czcionkę tekstową z określonym przez użytkownika pogrubionym identyfikatorem czcionki|
|\<i>\</i> | Renderuj czcionkę tekstową z określonym przez użytkownika identyfikatorem czcionki kursywą|
|\<u>\</u> | Renderowanie podkreślonego tekstu|
|\<f GX_FONT_ID>\</f> | Renderuj tekst przy użyciu określonego identyfikatora czcionki. |
|\<c GX_COLOR_ID>\</c> | Renderowanie tekstu przy użyciu określonego identyfikatora koloru|
|\<hc GX_COLOR_ID>\</hc> | Renderowanie tekstu przy użyciu określonego identyfikatora koloru tła|
|\<align left/right/center>\</align> | Przypisywanie wyrównania tekstu|
|||

Istnieją dwa sposoby edytowania ciągu tekstu sformatowanego z poziomu programu GUIX Studio:

- Użyj okna dialogowego Edytowanie tekstu sformatowanego, które jest zalecaną i najprostszą metodą edycji.
- Użyj okna dialogowego Edytor tabel ciągów, które umożliwia ręczne wstawianie tagów formatowania pokazanych w powyższej tabeli.

Po wybraniu widżetu Widok tekstu sformatowanego  w widoku docelowym  wybierz przycisk Edytuj tekst sformatowany w widoku *właściwości,* aby wywołać okno dialogowe edycji tekstu sformatowanego pokazane na rysunku 8.1.

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie tekstu sformatowanego w programie GUIX Studio.](./media/guix-studio/edit_rich_text_dialog.png)

**Rysunek 8.1**

Okienko po lewej stronie to pole edycji tekstu sformatowanego. Możesz użyć ikon paska narzędzi, aby ułatwić wstawianie wymaganych tagów. Zaznacz dowolny blok tekstu w polu edycji, a następnie wybierz przyciski paska narzędzi, aby zastosować wymagane style i kolory do wybranego bloku tekstu. Okno dialogowe Edytowanie tekstu sformatowanego to prosty sposób wstawiania kodów formatowania do ciągu testowego. Możesz również ręcznie wstawić te tagi lub w razie potrzeby wygenerować je w czasie wykonywania.

Prawe okienko to podgląd widżetu, który pokazuje sposób renderowania tekstu w widoku docelowym. Kolor tła podglądu widżetu jest stały, co może nie być zgodne z przypisanym kolorem tła widżetu w widoku docelowym.

Nazwy identyfikatorów zasobów są używane w tekście sformatowanych w celu odwołania się do określonych zasobów czcionek lub kolorów. Jeśli nazwa zasobu czcionki lub koloru zostanie zmieniona po przywołyniu jej przez ciąg tekstu sformatowanego, program GUIX Studio automatycznie zaktualizuje ciąg tekstu sformatowanego, aby odzwierciedlić zmiany nazwy zasobu. Z drugiej strony, jeśli usuniesz zasób czcionki lub koloru, do którego odwołuje się widżet tekstu sformatowanego, musisz ręcznie edytować tekst sformatowany, aby usunąć lub zmienić nazwy identyfikatorów zasobów, które zostały usunięte.

Po wybraniu przycisku Zapisz w tym oknie dialogowym zdefiniowany ciąg tekstu sformatowanego zostanie dodany do tabeli ciągów projektu.

## <a name="string-scroll-wheel"></a>Kółka przewijania ciągów

Widżet koła przewijania ciągów obsługuje wyświetlanie tablicy ciągów. Te ciągi mogą być przypisywane dynamicznie lub, jeśli aplikacja obsługuje wiele języków, przypisane ciągi można ściągnąć z aktywnej tabeli ciągów.

Widżet koła przewijania ciągów obsługuje tablicę ciągów. Okno dialogowe Edytowanie koła przewijania ciągów, pokazane na rysunku 8.2, umożliwia użytkownikowi przypisanie tej tablicy ciągów.

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie koła przewijania ciągów w programie GUIX Studio.](./media/guix-studio/string_scroll_wheel_edit.png)

**Rysunek 8.2**

Aby wywołać to okno dialogowe, wybierz widżet koła przewijania ciągów w widoku *docelowym* lub widoku *Project widoku*. Po wybraniu tego typu widżetu widok *właściwości będzie* zawierać przycisk **Edytuj ciągi.** Wybierz ten przycisk, aby wywołać okno dialogowe Edytowanie koła przewijania ciągów.

Aby przypisać ciąg do każdego indeksu tekstowego, możesz wybrać identyfikator ciągu z listy rozwijanej lub wpisać nową wartość ciągu w polu Tekst po prawej stronie. Gdy zmiany zostaną wprowadzone, wszystkie nowe lub zmodyfikowane ciągi zostaną zapisane w aktywnej tabeli ciągów.

## <a name="sprite"></a>Sprite

Widżet sprite służy do wyświetlania sekwencji obrazów w celu zapewnienia efektu animacji. Widżet sprite wymaga listy ramek, która jest tablicą identyfikatorów obrazów i unikatowych parametrów stosowanych do każdego obrazu w ramce. Aby utworzyć tę listę ramek dla widżetu sprite,dostępne jest okno dialogowe Edytowanie ramek sprite'u, pokazane na rysunku 8.3:

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie ramek sprite w programie GUIX Studio.](./media/guix-studio/edit_sprite_frames.png)

**Rysunek 8.3**

Aby wywołać to okno dialogowe, wybierz widżet sprite w widoku *docelowym* lub Project *widoku*. Po wybraniu tego typu widżetu widok *właściwości będzie* zawierać przycisk Edytuj **listę ramek.** Wybierz ten przycisk, aby wywołać okno dialogowe Edytowanie koła przewijania ciągów.

Pole *Łączna liczba ramek sprite* jest polem wejściowym, które umożliwia wprowadzenie całkowitej całkowitej liczby ramek do wyświetlania przez widżet sprite. Obrazy mogą być ponownie używane na liście ramek, co oznacza, że nie każdy obraz musi być unikatowy.

Pole Sprite Frame ID (Identyfikator ramki sprite'a) jest wartością wyboru indeksu ramek z zakresu od 1 do łączną liczbę ramek. Zwiększa i zmniejsza tę wartość, aby przejść z jednej ramki sprite do następnej.

Każda ramka sprite ma kilka parametrów. Pierwsza to operacja w tle. To pole naśladuje możliwości popularnego formatu animacji GIF. Dostępne są następujące opcje:

- Brak operacji, co oznacza, że bieżący obraz ramki jest rysowany na poprzednim obrazie ramki.
- Przywróć mapę pierwszego piksela, co oznacza, że mapa indeksu 1 pikseli jest rysowana przed bieżącą mapą pikseli i
- Pełne wypełnienie kolorem, co oznacza, że tło sprite jest wypełniane kolorem tła sprite'u przed rysowaniem bieżącej ramki.

Pole Identyfikator mapy pikseli umożliwia wybranie dowolnej mapy pikseli dodanej wcześniej do zasobów projektu. Ten sam identyfikator mapy pikseli może być używany dla wielu ramek. Na przykład animacja sprite'a może wykorzystywać ruch obrazu (przy użyciu pól przesunięcia x i y) zamiast lub oprócz używania różnych obrazów sprite.

Pole Wartość alfa jest stosowane do całego rysunku z mapą pikseli. To pole ma wpływ tylko w przypadku uruchamiania z głębokością koloru 8 bpp lub wyższą. Wartość alfa 0 jest w pełni przezroczysta, a wartość alfa 255 jest nieprzezroczysta.

Można określić przesunięcie w obrębie ramki sprite, w której będzie rysowana bieżąca mapa pikseli, przy użyciu pól Przesunięcie ramki x i Przesunięcie ramki y. Innymi słowy, każdy narysowany obraz nie musi być pełnym rozmiarem widżetu sprite.

Okres opóźnienia określa czas opóźnienia przed przejściem do następnej ramki sprite. Ta wartość jest w taktach, które dla domyślnej konfiguracji czasomierza GUIX/ThreadX każdy znacznik reprezentuje 50 ms.

Po zapisaniu zmian w oknie dialogowym Edytowanie ramek sprite program GUIX Studio może wygenerować pełną tablicę list ramek w ramach generowania pliku specyfikacji danych wyjściowych.

### <a name="assign-a-sprite-widget-with-gif-resource"></a>Przypisywanie widżetu sprite za pomocą zasobu GIF
Możesz dodać zasób GIF do grupy zasobów **Pixelmap** i bezpośrednio przypisać zasób GIF do widżetu sprite. Po skonfigurowaniu zasobu GIF lista ramek zostanie wygenerowana automatycznie. Każdą ramkę listy ramek można edytować za pomocą okna dialogowego edycji sprite:

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie ramek sprite programu GUIX Studio dla zasobu GIF.](./media/guix-studio/edit_sprite_gif_frames.jpg)

**Rysunek 8.4**