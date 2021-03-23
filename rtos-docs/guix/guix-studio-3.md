---
title: Opis programu GUIX Studio
description: Ten rozdział zawiera opis narzędzia do analizy systemu GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 89bbcd51c22dddef6e420750e8c8805a66344335
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822273"
---
# <a name="chapter-3-description-of-guix-studio"></a>Rozdział 3: Opis programu GUIX Studio

Ten rozdział zawiera opis narzędzia do analizy systemu GUIX Studio. W tym rozdziale znajduje się opis ogólnych funkcji interfejsu GUI. 

## <a name="guix-studio-views"></a>Widoki GUIX Studio

Istnieje pięć głównych obszarów interfejsu użytkownika programu GUIX Studio, a mianowicie **pasek narzędzi*** _, widok _*_projektu_*_, _*_Widok właściwości_*_, _*_Widok docelowy_*_ i _*_Widok zasobów_*_. *_Ilustracja 2_** przedstawia podstawowy interfejs użytkownika programu GUIX Studio. Każdy z tych widoków został szczegółowo omówiony w poniższych podsekcjach.

![Zrzut ekranu przedstawiający podstawowy interfejs użytkownika programu GUIX Studio.](./media/guix-studio/image_10.png)

**Rysunek 2**

### <a name="title"></a>Tytuł

- GUIX Studio 18: ***title** _ wyświetla wersję programu GUIX Studio, a także aktualnie otwarty projekt, jak pokazano na początku _ *_rysunku 2_** poprzednio.

### <a name="toolbar"></a>Pasek narzędzi

**Pasek narzędzi*** _ pokazuje przyciski dostępne dla dewelopera programu GUIX Studio, jak pokazano na _rysunku 3_* * *.

![Zrzut ekranu przedstawiający pasek narzędzi GUIX Studio.](./media/guix-studio/image11.jpg)

**Rysunek 3**

Przyciski paska narzędzi są zdefiniowane w następujący sposób:

![Przycisk Nowy](./media/guix-studio/new-button.png) Tworzy nowy projekt programu GUIX Studio

![Przycisk Otwórz](./media/guix-studio/open-button.png) Otwiera istniejący projekt programu GUIX Studio

![Przycisk Zapisz](./media/guix-studio/save-button.png) Zapisuje projekt

![Przycisk Wytnij](./media/guix-studio/cut-button.png) Zaznaczono element widget wycinania, w tym elementy podrzędne

![Kopiuj](./media/guix-studio/copy-button.png) Kopiuj wybrany widżet, w tym elementy podrzędne

![Przycisk Wklej](./media/guix-studio/paste-button.png) Wklej widżet i elementy podrzędne

![Przycisk Wyrównaj do lewej](./media/guix-studio/left-align-button.png) Wyrównanie wybranych elementów widget do lewej

![Przycisk Wyrównaj do prawej](./media/guix-studio/right-align-button.png) Wyrównanie wybranych elementów widget do prawej

![Przycisk Wyrównaj do góry](./media/guix-studio/top-align-button.png) Wyrównaj do góry wybrane widżety

![Przycisk Wyrównaj do dołu](./media/guix-studio/bottom-align-button.png) Wyrównaj do dołu wybrane widżety

![Przycisk spacji w pionie](./media/guix-studio/space-vertically-button.png) Równe miejsce wybrane widżety w pionie

![Przycisk odstępu w poziomie](./media/guix-studio/space-horizontally-button.png) Równe miejsce wybrane widżety w poziomie

![Przycisk o równej szerokości](./media/guix-studio/equal-width-button.png) Ustaw wybraną szerokość równą wartości widget

![Przycisk równej wysokości](./media/guix-studio/equal-height-button.png) Zmień wysokość wybranych elementów widget

![Przycisk Przenieś przód](./media/guix-studio/move-front-button.png) Przenieś wybrane elementy widget na wierzch

![Przycisk przenoszenia wstecz](./media/guix-studio/move-back-button.png) Przenieś wybrane elementy widget na spód

![Przycisk rozmiar](./media/guix-studio/size-button.png) Rozmiar wybranego elementu widget do zawartości na ekranie celu

![Przycisk Powiększ](./media/guix-studio/zoom-out-button.png) Ekran pomniejszej wartości docelowej

![Przycisk Powiększ](./media/guix-studio/zoom-in-button.png) Powiększ na ekranie docelowym

![Przycisk nagrywania](./media/guix-studio/record-button.png) Rejestruj makro

![Przycisk odtwarzania](./media/guix-studio/playback-button.png) Makro odtwarzania

![Przycisk Uruchom](./media/guix-studio/run-button.png) Uruchom aplikację

![Przycisk about — informacje](./media/guix-studio/about-button.png) Informacje o programie GUIX Studio

### <a name="project-view"></a>Widok projektu

***Widok projektu** _ pokazuje hierarchiczną listę obiektów GUIX, które składają się na OSADZONY interfejs użytkownika. Nowe obiekty GUIX można dodać, klikając obiekt nadrzędny, a następnie wybierając obiekt z menu _*_Wstaw_*_ (lub klikając prawym przyciskiem myszy obiekt i wybierając je z menu rozwijanego po prawej stronie). Na _*_rysunku 4_*_ poniżej przedstawiono _Widok projektu_ GUIX Studio _ * * *.

![Zrzut ekranu przedstawiający widok projektu GUIX Studio.](./media/guix-studio/image_35.png)

**Rysunek 4**

### <a name="properties-view"></a>Widok właściwości

**Widok właściwości*** _ pokazuje szczegółowe informacje o właściwości aktualnie wybranego obiektu GUIX, który można wybrać za pośrednictwem _*_widoku projektu_*_ lub klikając bezpośrednio na obiekcie w _*_widoku elementu docelowego_*_. Na _*_rysunku 5_*_ poniżej przedstawiono _Widok właściwości_ GUIX Studio _ * * *.

![Zrzut ekranu przedstawiający widok Właściwości programu GUIX Studio.](./media/guix-studio/image36.jpg)

**Rysunek 5**

### <a name="target-view"></a>Widok docelowy

**Widok docelowy*** _ jest obszarem projektowania i układu ekranu WYSIWYG. Ten widok jest przeznaczony do reprezentowania fizycznego ekranu lub wyświetlaczy dostępnego na sprzęcie docelowym. Obiekty można zaznaczać, przenosić, zmieniać ich rozmiar itp. za pomocą prostych operacji myszy. Ponadto w wybranych obiektach w widoku docelowym są dostępne operacje wyrównania i kolejności przycisków. Wybranie obiektu w _*_widoku docelowym_*_ spowoduje również wyświetlenie właściwości tego obiektu w _*_widoku właściwości_*_. Na _*_rysunku 6_*_ poniżej przedstawiono _Widok docelowy_ GUIX Studio _ * * *.

![Zrzut ekranu przedstawiający widok docelowy programu GUIX Studio.](./media/guix-studio/image_37.png)

**Rysunek 6.**

### <a name="resource-view"></a>Widok zasobów

***Widok zasobów** _ służy do zarządzania zasobami (kolorami, czcionkami, pixelmaps i ciągami) dostępnymi dla ekranów aplikacji zdefiniowanych dla każdego ekranu. Możesz kliknąć nagłówki grupy widok zasobów, aby rozwinąć każdą grupę i sprawdzić zawartość grupy. _*_Rysunek 7_*_ poniżej przedstawia GUIX Studio _ *_Widok zasobów_* *.

![Zrzut ekranu GUIX Studio Widok zasobów.](./media/guix-studio/image38.jpg)

**Rysunek 7**

Tytuł grup zasobów wskazuje bieżącą nazwę motywu. Jeśli dostępnych jest wiele motywów, można przełączać się między motywami, klikając strzałkę w górę i w dół.

Wszystkie grupy zasobów w widoku powyżej mogą być rozwinięte lub zwinięte przez kliknięcie nagłówka grupy. Bardziej szczegółowy opis poszczególnych grup zasobów znajduje się w następnym rozdziale.

## <a name="the-guix-studio-project"></a>Projekt GUIX Studio

Projekt programu GUIX Studio przechowuje informacje o projekcie ekranu interfejsu użytkownika i zasobach interfejsu użytkownika. Dane projektu są zapisywane w pliku formatu XML z rozszerzeniem ". ***GXP***". Ponieważ plik projektu jest plikiem schematu XML, może być kontrolowany pod kontrolą wersji i udostępniony w innym pliku źródłowym.

Przy pierwszym uruchomieniu przy użyciu programu GUIX Studio należy otworzyć jeden z przykładowych projektów dostarczonych z dystrybucją lub utworzyć nowy projekt. Cała Twoja służbowa jest zapisywana w pliku danych projektu.

GUIX Studio tworzy również pliki źródłowe ANSI C. Te pliki źródłowe zawierają zasoby aplikacji lub struktury danych opisujące zaprojektowane ekrany. GUIX Studio zapisuje również w tych generowanych funkcjach interfejsu API plików źródłowych, które wiedzą, jak używać wygenerowanych struktur danych do dynamicznego tworzenia ekranów aplikacji. Oprogramowanie aplikacji po prostu wywoła dostarczone funkcje interfejsu API w celu utworzenia ekranów zaprojektowanych w ramach programu GUIX Studio.

Podczas projektowania interfejsu użytkownika należy okresowo używać programu GUIX Studio do generowania plików wyjściowych zgodnych z GUIX, które umożliwią Kompilowanie i uruchamianie zaprojektowanego interfejsu. Można kompilować i uruchamiać wygenerowane pliki źródłowe dla sprzętu docelowego lub na pulpicie systemu Windows, które symulują ThreadX i GUIX.

## <a name="guix-studio-project-organization"></a>Organizacja projektu programu GUIX Studio

Warto mieć pewną wiedzę na temat podstawowej organizacji projektu GUIX Studio, aby zrozumieć, jak używać GUIX Studio efektywnie i zrozumieć informacje przedstawione w widoku projektu środowiska IDE GUIX Studio. Widok projektu jest podsumowującą wizualną reprezentacją wszystkich informacji zawartych w projekcie.

Przed rozpoczęciem opisywania projektu konieczne jest zdefiniowanie kilku warunków. Najpierw użyjemy **wyświetlania** terminu do oznaczania fizycznego urządzenia wyświetlającego. Jest to najczęściej wyświetlane urządzenie wyświetlacza LCD, ale może ono korzystać z innej technologii. Następnym terminem jest **ekran**, który oznacza obiekt GUIX najwyższego poziomu, zazwyczaj okno GUIX i wszystkie skojarzone z nim elementy podrzędne. Ekran to konstrukcja programowa, która może być zdefiniowana i modyfikowana w czasie wykonywania. Na koniec **motyw** jest kolekcją zasobów. Motyw zawiera tabelę definicji koloru, definicje czcionek i definicje Pixelmap, które zostały zaprojektowane tak, aby dobrze współpracować i przedstawić użytkownikowi końcowemu spójny wygląd i działanie.

Projekt najpierw zawiera zestaw informacji globalnych, takich jak nazwa projektu, liczba obsługiwanych wyświetlaczy, rozdzielczość i format koloru każdego ekranu, liczba obsługiwanych języków, Nazwa każdego obsługiwanego języka. Nazwa projektu to pierwszy węzeł wyświetlany w widoku projektu.

Projekt dalej organizuje wszystkie informacje wymagane do 4 fizycznych wyświetlania, a ekrany i zasoby dostępne dla każdego ekranu. Nazwy wyświetlane są węzłami następnego poziomu w drzewie widoku projektu.

Unikatowa funkcja aplikacji GUIX Studio to wbudowana obsługa wielu ekranów fizycznych, z których każda ma własne rozdzielczości x, y, format koloru, ekrany i zasoby. Chociaż większość aplikacji GUIX korzysta tylko z jednego fizycznego ekranu, ta funkcja jest ważna w przypadku, gdy produkt musi obsługiwać wiele równoczesnych ekranów fizycznych.

Poniżej każdej definicji ekranu znajdują się okna lub ekrany najwyższego poziomu zdefiniowane dla tego ekranu. Definicje ekranu mogą być zagnieżdżane na dowolnym poziomie w zależności od liczby i zagnieżdżenia elementów widget podrzędnych na każdym ekranie.

Ten ekran i podrzędna organizacja widżetu są wyświetlane w sposób graficzny w widoku projektu.

Skojarzone z poszczególnymi ekranami są kompozycje obsługiwane przez ekran i zawartość zasobów tworzących każdy motyw. Jeśli projekt zawiera wiele ekranów, Zauważ, że Widok zasobów zmienia jego zawartość po wybraniu jednego ekranu, a następnie innej. Wynika to z faktu, że zawartość zasobu jest połączona z każdym wyświetlaniem. Nie tylko format koloru może być inny, ale pixelmaps, kolory i czcionki, których wybierasz, mogą się różnić od jednego wyświetlania fizycznego na inny.

Końcowy składnik obsługiwany przez projekt to dane tabeli ciągów skojarzone z poszczególnymi ekranami. Ponieważ wyświetlacze mogą być bardzo różnymi rozdzielczościami x, y, dane ciągu są obsługiwane niezależnie dla każdego ekranu zdefiniowanego w projekcie.
