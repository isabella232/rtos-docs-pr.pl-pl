---
title: Opis programu GUIX Studio
description: Ten rozdział zawiera opis narzędzia do analizy systemu GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 843106aa67d2a978c7f271954e028b32ba4dd007fe35a36b7c17ba0f5f80e4a9
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116787034"
---
# <a name="chapter-3-description-of-guix-studio"></a>Rozdział 3. Opis programu GUIX Studio

Ten rozdział zawiera opis narzędzia do analizy systemu GUIX Studio. Opis ogólnej funkcjonalności graficznego interfejsu użytkownika znajduje się w tym rozdziale. 

## <a name="guix-studio-views"></a>Widoki GUIX Studio

Istnieje pięć głównych obszarów interfejsu użytkownika programu GUIX Studio, a mianowicie ***** Pasek narzędzi _, _*_widok_*_ _*_Project,_*_ widok właściwości, widok _*_docelowy_*_ _*_i Widok zasobów_*_. _ *_Rysunek 2_** przedstawia podstawowy interfejs użytkownika programu GUIX Studio. Każdy z widoków został bardziej omówiony w poniższych podsekcjach.

![Zrzut ekranu przedstawiający podstawowy interfejs użytkownika programu GUIX Studio.](./media/guix-studio/image_10.png)

**Rysunek 2**

### <a name="title"></a>Tytuł

- GUIX Studio 18: ***Tytuł** _ wyświetla wersję programu GUIX Studio, a także aktualnie otwarty projekt, jak pokazano w górnej części _ *_Rysunek 2_** wcześniej.

### <a name="toolbar"></a>Pasek narzędzi

***Pasek narzędzi** _ pokazuje przyciski dostępne dla dewelopera programu GUIX Studio, jak pokazano na rysunku _*_3_**.

![Zrzut ekranu przedstawiający pasek narzędzi GUIX Studio.](./media/guix-studio/image11.jpg)

**Rysunek 3**

Przyciski paska narzędzi są zdefiniowane w następujący sposób:

![Przycisk Nowy](./media/guix-studio/new-button.png) Tworzy nowy projekt GUIX Studio

![Przycisk Otwórz](./media/guix-studio/open-button.png) Otwiera istniejący projekt GUIX Studio

![Przycisk Zapisz](./media/guix-studio/save-button.png) Zapisuje projekt

![Przycisk Wytnij](./media/guix-studio/cut-button.png) Wybrany widżet wycinania, w tym elementy children

![Kopiuj](./media/guix-studio/copy-button.png) Kopiowanie wybranego widżetu, w tym elementów children

![Przycisk Wklej](./media/guix-studio/paste-button.png) Wklejanie widżetu i elementów children

![Przycisk wyrównania do lewej](./media/guix-studio/left-align-button.png) Wybrane widżety wyrównane do lewej

![Przycisk wyrównania do prawej](./media/guix-studio/right-align-button.png) Wyrównywanie zaznaczonych widżetów do prawej

![Przycisk wyrównania do góry](./media/guix-studio/top-align-button.png) Wyrównaj do góry wybrane widżety

![Przycisk wyrównania do dołu](./media/guix-studio/bottom-align-button.png) Wyrównywanie wybranych widżetów do dołu

![Przycisk spacji w pionie](./media/guix-studio/space-vertically-button.png) Równomierne odstępy między wybranymi widżetami w pionie

![Przycisk Spacja w poziomie](./media/guix-studio/space-horizontally-button.png) Równomierne odstępy między wybranymi widżetami w poziomie

![Przycisk o równej szerokości](./media/guix-studio/equal-width-button.png) Przyrównanie wybranych widżetów do równej szerokości

![Przycisk o równej wysokości](./media/guix-studio/equal-height-button.png) Równe wysokości wybranych widżetów

![Przenoszenie przycisku przed](./media/guix-studio/move-front-button.png) Przenoszenie wybranych widżetów na przód

![Przycisk Cofnięcie](./media/guix-studio/move-back-button.png) Przenoszenie wybranych widżetów do tyłu

![Przycisk Rozmiar](./media/guix-studio/size-button.png) Rozmiar wybranego widżetu dla zawartości Pomniejszanie ekranu docelowego

![Przycisk Pomniejszanie](./media/guix-studio/zoom-out-button.png) Pomniejszanie ekranu docelowego

![Przycisk Powiększanie](./media/guix-studio/zoom-in-button.png) Powiększanie ekranu docelowego

![Przycisk Rekord](./media/guix-studio/record-button.png) Makro rekordu

![Przycisk odtwarzania](./media/guix-studio/playback-button.png) Makro odtwarzania

![Przycisk Uruchom](./media/guix-studio/run-button.png) Uruchamianie aplikacji

![Przycisk Informacje](./media/guix-studio/about-button.png) Informacje o programie GUIX Studio

### <a name="project-view"></a>Project Widok

Widok ***Project** _ przedstawia hierarchiczną listę obiektów GUIX, które składają się na osadzony interfejs użytkownika. Nowe obiekty GUIX można dodać, klikając obiekt nadrzędny, a następnie wybierając obiekt z _*_menu_*_ Wstaw (lub klikając obiekt prawym przyciskiem myszy i wybierając go z menu dostępnego po kliknięciu prawym przyciskiem myszy). _*_Rysunek 4_*_ poniżej przedstawia widok Project GUIX Studio __*._

![Zrzut ekranu przedstawiający widok Project GUIX Studio.](./media/guix-studio/image_35.png)

**Rysunek 4**

### <a name="properties-view"></a>Widok właściwości

***Widok właściwości** _ zawiera szczegółowe informacje o właściwości aktualnie wybranego obiektu GUIX, które można wybrać za pośrednictwem widoku _*_Project lub_*_ klikając bezpośrednio obiekt w widoku _*_docelowym_*_. _*_Rysunek 5_*_ poniżej przedstawia widok właściwości programu GUIX Studio __*_**.

![Zrzut ekranu przedstawiający widok właściwości programu GUIX Studio.](./media/guix-studio/image36.jpg)

**Rysunek 5**

### <a name="target-view"></a>Widok docelowy

***Widok docelowy** _ to obszar projektowania i układu ekranu WYSIWYG. Ten widok jest przeznaczony do reprezentowania fizycznego wyświetlania lub wyświetlania dostępnego na sprzęcie docelowym. Obiekty można wybierać, przenosić, zmieniać ich rozmiar itp. za pomocą prostych operacji myszy. Ponadto operacje wyrównania i przycisku porządek osi Z są dostępne dla wybranych obiektów w widoku docelowym. Wybranie obiektu w widoku _*_obiektu_*_ docelowego spowoduje również wyświetlenie właściwości tego obiektu w widoku _*_właściwości_*_. _*_Rysunek 6_*_ poniżej przedstawia widok docelowy GUIX Studio __*_**.

![Zrzut ekranu przedstawiający widok docelowy programu GUIX Studio.](./media/guix-studio/image_37.png)

**Rysunek 6**

### <a name="resource-view"></a>Widok zasobów

***Widok zasobów** _ służy do zarządzania zasobami (kolorami, czcionkami, mapami pikseli i ciągami) dostępnymi dla ekranów aplikacji zdefiniowanych dla każdego ekranu. Możesz kliknąć nagłówki grupy widoku zasobów, aby rozwinąć każdą grupę i zbadać jej zawartość. _*_Rysunek 7_*_ poniżej przedstawia program GUIX Studio _*_Widok zasobów_**.

![Zrzut ekranu przedstawiający interfejs GUIX Studio Widok zasobów.](./media/guix-studio/image38.jpg)

**Rysunek 7**

Tytuł grup zasobów wskazuje bieżącą nazwę motywu. Jeśli dostępnych jest wiele motywów, możesz przełączać się między motywami, klikając strzałkę w górę i w dół.

Każdą grupę zasobów w widoku powyżej można rozwinąć lub zwinąć, klikając nagłówek grupy. Bardziej szczegółowy opis poszczególnych grup zasobów jest następujący w następnym rozdziale.

## <a name="the-guix-studio-project"></a>Interfejs GUIX Studio Project

Projekt GUIX Studio przechowuje informacje o projekcie ekranu interfejsu użytkownika i zasobach interfejsu użytkownika. Dane projektu są zapisywane w pliku w formacie XML z rozszerzeniem ". ***gxp***". Ponieważ plik projektu jest plikiem schematu XML, można go kontrolować i udostępniać w wersji, podobnie jak każdy inny plik źródłowy.

Po pierwszym rozpoczęciu korzystania z programu GUIX Studio należy otworzyć jeden z przykładowych projektów dostarczanych z dystrybucją lub utworzyć nowy projekt. Cała praca jest zapisywana w pliku danych projektu.

GuiX Studio tworzy również pliki źródłowe ANSI C. Te pliki źródłowe zawierają zasoby aplikacji lub struktury danych opisujące zaprojektowane ekrany. Program GUIX Studio zapisuje również w tych funkcjach interfejsu API wygenerowanych plików źródłowych, które wiedzą, że wykorzystują wygenerowane struktury danych do dynamicznego tworzenia ekranów aplikacji. Oprogramowanie aplikacji po prostu wywoła dostarczone funkcje interfejsu API, aby utworzyć ekrany zaprojektowane w programie GUIX Studio.

W trakcie projektowania interfejsu użytkownika okresowo będziesz używać programu GUIX Studio do generowania plików wyjściowych zgodnych z guix, które umożliwią skompilowanie i uruchomienie zaprojektowanego interfejsu. Możesz skompilować i uruchomić wygenerowane pliki źródłowe dla sprzętu docelowego lub na komputerze Windows, który symuluje narzędzia ThreadX i GUIX.

## <a name="guix-studio-project-organization"></a>GuiX Studio Project Organization

Warto mieć wiedzę na temat podstawowej organizacji projektu GUIX Studio, aby zrozumieć sposób efektywnego korzystania z programu GUIX Studio i zrozumieć informacje przedstawione w widoku Project ide programu GUIX Studio. Widok Project to wizualna reprezentacja podsumowująca wszystkich informacji zawartych w projekcie.

Przed opisaniem projektu należy zdefiniować kilka terminów. Najpierw używamy terminu Wyświetlanie **jako** fizycznego urządzenia wyświetlającego. Najczęściej jest to urządzenie wyświetlające ZACM, ale może ono korzystać z innej technologii. Następny termin to **Screen**, który oznacza obiekt najwyższego poziomu GUIX, zazwyczaj okno GUIX i wszystkie skojarzone z nim elementy podrzędne. Ekran to konstrukcja oprogramowania, która może być definiowana i modyfikowana w czasie wykonywania. Na koniec **temat** jest kolekcją zasobów. Motyw zawiera tabelę definicji kolorów, definicji czcionek i definicji mapy pikseli, które zostały zaprojektowane tak, aby dobrze ze sobą współpracować i zapewnić użytkownikowi końcowego spójny wygląd i sposób działania.

Projekt najpierw zawiera zestaw informacji globalnych, takich jak nazwa projektu, liczba obsługiwanych ekranów, rozdzielczość i format kolorów poszczególnych ekranów, liczba obsługiwanych języków oraz nazwa każdego obsługiwanego języka. Nazwa projektu jest pierwszym węzłem wyświetlanym w Project widoku.

Następnie projekt organizuje wszystkie informacje wymagane dla maksymalnie 4 fizycznych ekranów oraz ekrany i zasoby dostępne dla każdego z nich. Nazwy wyświetlane są węzłami następnego poziomu w drzewie widoków Project widoku.

Unikatową funkcją aplikacji GUIX Studio jest wbudowana obsługa wielu ekranów fizycznych, z których każdy ma własną rozdzielczość x,y, format kolorów, ekrany i zasoby. Mimo że większość aplikacji GUIX korzysta tylko z jednego fizycznego ekranu, ta funkcja jest ważna dla osób, które robią produkt, który musi obsługiwać wiele jednoczesnych ekranów fizycznych.

Poniżej każdej definicji wyświetlania znajdują się okna lub ekrany najwyższego poziomu zdefiniowane dla tego ekranu. Definicje ekranu można zagnieżdżać na dowolnym poziomie w zależności od liczby i zagnieżdżania widżetów podrzędnych na każdym ekranie.

Organizacja tego ekranu i podrzędnego widżetu jest wyświetlana w sposób graficzny w Project widoku.

Z każdym ekranem są również skojarzone motywy obsługiwane przez wyświetlanie oraz zawartość zasobów poszczególnych motywów. Jeśli projekt zawiera wiele ekranów, zauważysz, że Widok zasobów jego zawartość po wybraniu jednego ekranu, a następnie innego. Jest to spowodowane tym, że zawartość zasobu jest połączona z każdym ekranem. Nie tylko format kolorów może się różnić, ale mapy pikseli, kolory i czcionki, które mają być używane, mogą się różnić w zależności od ekranu fizycznego.

Końcowym składnikiem utrzymywanym przez projekt jest ciąg danych tabeli skojarzonych z każdym ekranem. Ponieważ ekrany mogą mieć bardzo różne rozdzielczości x,y, dane ciągu są zachowywane niezależnie dla każdego ekranu zdefiniowanego w projekcie.
