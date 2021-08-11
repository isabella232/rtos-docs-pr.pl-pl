---
title: Zasoby programu GUIX Studio
description: Program GUIX Studio umożliwia zarządzanie wszystkimi zasobami interfejsu użytkownika, których aplikacja będzie używać w przypadku kolorów, czcionek, map pikseli i ciągów. W kolejnych sekcjach opisano sposób dodawania, modyfikowania i usuwania zasobów w projekcie ekranu interfejsu użytkownika.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dd694cb7d34df7ecae206c3dcaf7d75a20bd4bd4e26471bb94da4129897ef727
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116786148"
---
# <a name="chapter-4-guix-studio-resources"></a>Rozdział 4. Zasoby programu GUIX Studio

Program GUIX Studio umożliwia zarządzanie wszystkimi zasobami interfejsu użytkownika, których aplikacja będzie używać w przypadku kolorów, czcionek, map pikseli i ciągów. W kolejnych sekcjach opisano sposób dodawania, modyfikowania i usuwania zasobów w projekcie ekranu interfejsu użytkownika. 

Całe zarządzanie zasobami odbywa się w ramach ***Widok zasobów** _ interfejsu użytkownika programu GUIX Studio, jak pokazano poniżej na rysunku _*_8_**.

![Zrzut ekranu przedstawiający interfejs GUIX Studio Widok zasobów.](./media/guix-studio/image38.jpg)

**Rysunek 8**

## <a name="color-resources"></a>Kolorowanie zasobów

Sekcja ***Kolory** _ Widok zasobów _*_umożliwia_*_ zarządzanie zasobami kolorów. Możesz rozwinąć ten widok, klikając pole _ * w nagłówku widoku, co spowoduje wyświetlenie widoku pokazanego *+* poniżej na **_rysunku 9:_**

![Zrzut ekranu przedstawiający sekcję Kolory Widok zasobów](./media/guix-studio/image_39.png)

**Rysunek 9**

Zasoby kolorów składają się z co najmniej jednego koloru, z których każdy ma unikatową nazwę logiczną. Na przykład na rysunku **9** nazwa logiczna **CANVAS,** która jest identyfikatorem koloru systemu dla koloru wypełnienia tła ekranu, jest skojarzona z kolorem fizycznym czarny. Ten zasób koloru jest używany za każdym razem, **gdy aplikacja GX_COLOR_ID_CANVAS** jako kolor we właściwościach obiektu.

Po lewej stronie jest wyświetlany kolor "swatch" wskazujący wartość RGB koloru, a po nim nazwa identyfikatora koloru. Wartość RGB skojarzoną z dowolną nazwą identyfikatora można zmienić w dowolnym momencie. Nie można zmienić wstępnie zdefiniowanych nazw identyfikatorów kolorów systemu, ponieważ są one używane wewnętrznie przez bibliotekę GUIX. Można jednak zmienić dowolne wartości kolorów. Zmiana wartości koloru systemu to **zmiana globalna**. Oznacza to, że każdy widżet, który nie ma określonego przypisania koloru, będzie przyjmować nową wartość koloru systemu.

Możesz zmienić zarówno nazwę koloru, jak i wartość koloru dla kolorów niestandardowych dodanych do motywu.

Aby zmodyfikować zasób koloru, kliknij dwukrotnie (lub kliknij prawym przyciskiem myszy i wybierz menu) w zasobie kolorów. Ta akcja prowadzi do okna dialogowego definicji kolorów. W tym oknie dialogowym zasób koloru można zmodyfikować w celu dopasowania go do potrzeb interfejsu użytkownika aplikacji. ***Rysunek 10** _ przedstawia okno dialogowe modyfikacji, gdy kliknij dwukrotnie pozycję _ *CANVAS**. Wygląd tego okna dialogowego zmieni się w zależności od ustawień formatu kolorów ekranu docelowego.

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie koloru.](./media/guix-studio/edit_color.png)

**Rysunek 10**

Wygląd okna dialogowego Edytowanie koloru zmieni się w zależności od konfiguracji głębokości koloru i formatu koloru bieżącego ekranu.

Aby dodać nowy zasób koloru, w sekcji ***Kolory** _ Widok zasobów *_*_* wybierz następujący przycisk:

![Przycisk Dodaj nowy kolor](./media/guix-studio/image41.jpg)

Użyj wyświetlonego okna dialogowego koloru, aby dodać nowy zasób koloru, jak pokazano poniżej na rysunku ***Rysunek 11**:*

![Zrzut ekranu przedstawiający nowy kolor w oknie dialogowym Edytowanie koloru.](./media/guix-studio/new_color.png)

**Rysunek 11**

Po wykonaniu tych kroków wybranie opcji Zapisz **nowy** zasób koloru o **nazwie NEW_COLOR** z kolorem fizycznym zielonym będzie dostępne dla aplikacji.

**Specjalne zagadnienia dotyczące zmieniania ustawień formatu kolorów wyświetlania:**

Podczas tworzenia nowego projektu zostanie automatycznie wyświetlony monit o skonfigurowanie wyświetlania projektu i formatu kolorów poszczególnych ekranów. Najczęściej należy dokonać tych wyborów jeden raz i nie trzeba modyfikować tych ustawień konfiguracji.

Może się okazać, że konieczna będzie zmiana ustawień formatu kolorów wyświetlania w późniejszym czasie. W takim przypadku program GUIX Studio dokona najlepszej konwersji bieżącego systemu i wartości RGB koloru użytkownika ze starego formatu kolorów na nowy format kolorów. Ta konwersja jest zgodna z kilkoma regułami logicznymi.

W przypadku kolorów zdefiniowanych przez użytkownika program GUIX Studio zawsze próbuje przekonwertować poprzedni kolor na najbliższy pasujący kolor w nowym formacie kolorów. W przypadku konwersji z dużej głębokości kolorów, takiej jak format koloru 16 bpp 5:6:5 na format skali szarości lub koloru monochromatyczne, ta zmiana może spowodować niepożądane konwersje kolorów. W przypadku dokonywania dużych zmian w ustawieniach głębokości kolorów wyświetlania mogą być wymagane ręczne aktualizacje nowej tabeli kolorów zdefiniowanej przez użytkownika.

W przypadku wstępnie zdefiniowanych kolorów systemowych program GUIX Studio wewnętrznie definiuje trzy unikatowe domyślne tabele kolorów. Jedna domyślna tabela kolorów jest używana dla wszystkich głębokości kolorów większych niż 4 bpp skali szarości, druga domyślna tabela kolorów jest używana do formatów kolorów szarych (1 bpp < display_color_format <= 4bpp), a na koniec trzecia domyślna tabela kolorów systemowych jest używana do formatu kolorów monochromatycznych.

Po przełączeniu formatu kolorów wyświetlania przy użyciu Project konfiguracji są stosowane następujące reguły:

1) Jeśli stare i nowe formaty kolorów wyświetlania używają różnych domyślnych tabel kolorów systemowych zdefiniowanych powyżej, kolory systemowe są resetowane do wstępnie zdefiniowanych kolorów domyślnych. Innymi słowy, jeśli przełączysz się ze skali koloru na szary lub ze skali szarości do monochromatycznej głębokości koloru, kolory systemowe zostaną zresetowane do wewnętrznie zdefiniowanych wartości domyślnych dla nowej głębokości koloru. Chociaż może to spowodować utratę pewnych niestandardowych informacji o kolorach, to rozwiązanie stanowi rozsądny punkt początkowy w przypadku zmiany ustawień formatu kolorów wyświetlania.

2) Jeśli stare i nowe formaty kolorów używają tej samej domyślnej tabeli kolorów, co oznacza, że zmieniasz mniej radykalny format kolorów, program GUIX Studio przetestuje każdy kolor systemu, aby określić, czy wartość RGB koloru systemu została zmodyfikowana na podstawie wartości domyślnej. Jeśli wartość RGB koloru systemu została zmodyfikowana, program GUIX Studio wykonaje konwersję najlepiej dopasowaną ze starego formatu kolorów na nowy format kolorów. Jeśli kolor systemu nie został zmodyfikowany, zostanie zresetowany do domyślnego koloru dla nowego formatu kolorów.

**Specjalne zagadnienia dotyczące działania trybu palety:**

W przypadku skonfigurowania formatu kolorów dla 256 trybów palety kolorów w projekcie użytkownik może skonfigurować sposób instalowania i korzystania z palety. Możesz uzyskać dostęp do definicji palety i edytować ją za pomocą przycisku Konfiguruj| Okno dialogowe motywów. Jeśli projekt został ustawiony na 8 bpp, powinien zostać wyświetlony przycisk "Edytuj paletę". Kliknij ten przycisk, aby wyprowadzić okno dialogowe Edytowanie palety:

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie palety.](./media/guix-studio/edit_palette.png)

Program GUIX Studio dzieli paletę na dwie sekcje: sekcję "zdefiniowana przez użytkownika" i sekcję "wygenerowana automatycznie". Program GUIX Studio uruchamia zaawansowany algorytm generowania optymalnej palety, aby utworzyć najlepszą paletę do wyświetlania obrazów zawartych w poszczególnych motywach. Możesz wytłać dowolną liczbę pozycji palety, które należy zdefiniować, wpisując liczbę w polu "Wstępnie zdefiniowane wpisy palety" i wprowadzić dowolną wartość RGB dla dowolnego z tych miejsc. Pozostałe miejsca zostaną przydzielone do programu Studio w celu utworzenia optymalnej palety kolorów do wyświetlania obrazów.

Jeśli w tym trybie chcesz edytować kolor zdefiniowany w widoku zasobów, edytor kolorów umożliwia wybranie tylko wstępnie zdefiniowanych wpisów palety. Wynika to z tego, że pozostałe wpisy palety są generowane automatycznie przez program GUIX Studio i zmieniają się w przypadku modyfikacji obrazów dodanych do projektu.

Jeśli podczas uruchamiania w trybie palety 8bpp jest wymagane wyświetlanie czcionek z aliasami, należy zdefiniować tablicę wpisów palety, które tworzą gradient dla każdego koloru pierwszego planu/tła używanego do wyświetlania tekstu z aliasami. Można użyć 8 pozycji palety dla gradientu dla każdej kombinacji kolorów lub 16 pozycji palety, aby uzyskać bardziej płynny gradient. Ta liczba użytych wpisów palety jest określana przez pole wyboru "Number of Palette Mode Anti-Aliased Text Colors" (Liczba kolorów tekstu w trybie palety z anty aliasami) w oknie dialogowym Project Konfiguracji. Możesz użyć gradientu z tylko 8 wpisami, aby zminimalizować wpisy palety używane dla każdej kombinacji kolorów, lub użyć 16 gradientów wejściowych, aby zapewnić najbardziej płynny wygląd tekstu o aliasach.

Aby uprościć definiowanie gradientu kolorów w celu wyświetlania tekstu o aliasach lub generowania gradientu kolorów do własnego użycia, w oknie dialogowym Edytowanie palety znajduje się przycisk Generuj gradient. Aby użyć tej funkcji, należy najpierw przypisać wartości r:g:b kolorów gradientu początkowego i końcowego.

Jeśli na przykład chcesz wyświetlić anty aliasowany czerwony tekst na średnim szarym tle przy użyciu ośmiu wpisów palety rozpoczynających się od indeksu 50, przypisz wartość r:g:b 255:0:0 do indeksu palety 50, a wartość r:g:b 128:128:128 do indeksu palety 57. Wprowadź te wartości indeksu palety w polach start-index i end-index w tym oknie dialogowym, a następnie kliknij przycisk Generuj gradient. Wpisy palety od 51 do 56 zostaną zainicjowane w celu zdefiniowania płynnego przejścia gradientu między kolorami granicznym.

## <a name="font-resources"></a>Zasoby czcionek

Aby zarządzać zasobami czcionek, należy _**_ najpierw rozwinąć sekcję ***Czcionki** _ Widok zasobów, klikając pole _ *, co spowoduje, że w oknie dialogowym pokazanym poniżej na rysunku *+* **_12:_**

![Zrzut ekranu przedstawiający sekcję Czcionki w Widok zasobów.](./media/guix-studio/image44.jpg)

**Rysunek 12**

Zasoby czcionek składają się z co najmniej jednej czcionki, z których każda ma unikatową nazwę logiczną. Na przykład na rysunku **12** nazwa logiczna SYSTEM jest skojarzona z określoną czcionką.  Ten zasób czcionki jest używany za każdym razem, gdy aplikacja określi **wartość SYSTEM** jako czcionkę we właściwościach obiektu. Grupa czcionek wyświetla podgląd WYSIWYG dla symbolu czcionki po lewej stronie, wysokości czcionki w pikselach, nazwy identyfikatora czcionki i rozmiaru czcionki (w kb).

W powyższym widoku pierwsze cztery czcionki są wstępnie zdefiniowanymi domyślnymi czcionkami, które są wymagane przez bibliotekę GUIX. Można zmienić dane czcionek skojarzone z tymi czcionkami, ale nie można zmienić tych nazw identyfikatorów czcionek.

Ostatnia czcionka pokazana powyżej o nazwie "Kursywa" jest czcionką niestandardową, która została dodana do projektu przez użytkownika.

Aby zmodyfikować zasób czcionki, kliknij dwukrotnie (lub kliknij prawym przyciskiem myszy i wybierz menu) w zasobie czcionki. W tym oknie dialogowym zasób czcionki można zmodyfikować w celu dopasowania go do potrzeb interfejsu użytkownika aplikacji. ***Rysunek 13** _ przedstawia okno dialogowe modyfikacji po dwukrotnym kliknięciu przycisku _ *SYSTEM**.

! [[Zrzut ekranu przedstawiający okno dialogowe modyfikacji po dwukrotnym kliknięciu przycisku SYSTEM.](./media/guix-studio/edit_system_font.png)

**Rysunek 13**

Aby dodać nowy zasób czcionki, w sekcji ***Czcionki** _ Widok zasobów *_*_* wybierz następujący przycisk:

![Przycisk Dodaj nową czcionkę](./media/guix-studio/image46.jpg)

Spowoduje to wywołanie `Font Edit` okna dialogowego w celu dodania nowego zasobu czcionki, jak pokazano poniżej na ***rysunku 14:***

![Zrzut ekranu przedstawiający okno dialogowe modyfikacji w celu dodania nowego zasobu czcionki.](./media/guix-studio/add_new_font.png)

**Rysunek 14**

Nowe czcionki GUIX są tworzone przez program GUIX Studio, który renderuje wybraną czcionkę TrueType o określonym rozmiarze. W związku z tym powyższe okno dialogowe najpierw wymaga ścieżki czcionki TrueType. Możesz użyć przycisku przeglądania, aby przejść do katalogu zawierającego pliki czcionek w systemie dewelopera. Kilka czcionek TrueType znajduje się również w podfoldecie GUIX/fonts wszędzie tam, gdzie zainstalowano program GUIX Studio.

Jeśli to możliwe, lokalizacja pliku czcionki TrueType jest przechowywana wewnętrznie przy użyciu ścieżki względnej projektu. Z tego powodu ważne jest, aby zachować wszystkie pliki czcionek we wspólnej lokalizacji i użyć wspólnej struktury drzewa katalogów dla projektów i plików czcionek, aby umożliwić przenoszenie projektów GUIX Studio z jednej stacji deweloperskie do innej.

Pole Nazwa czcionki umożliwia określenie nazwy identyfikatora zasobu czcionki. Jest to identyfikator zasobu, który będzie używany w kodzie wygenerowanym przez program GUIX Studio, a także używany przez aplikację podczas odwoływania się do czcionki. Ta nazwa musi spełniać wymagania dotyczące składni nazw zmiennych języka C.

Po wprowadzeniu pliku czcionki TrueType wprowadź nazwę logiczną czcionki.

Pole wyboru "**Generate Kerning Info"**(Generowanie informacji o kerningu) powoduje, że program GUIX Studio dołącza informacje dotyczące kerningu do wygenerowanej czcionki, która służy do dopasowywania względnych pozycji kolejnych glifów w ciągu. Jeśli chcesz zastosować kerning z ciągami, musisz użyć czcionki zawierającej informacje dotyczące kerningu i włączyć to pole wyboru. Należy również zdefiniować opcję kompilacji biblioteki GUIX "GX_FONT_KERNING_SUPPORT" do obsługi renderowania tekstu z informacjami kerningu.

Pole wyboru **"Include character set defined by String Table"**(Uwzględnij zestaw znaków zdefiniowany przez tabelę ciągów) powoduje, że program GUIX Studio dołącza te symboly, do których odwołuje się tabela ciągów statycznych, w wygenerowanej czcionce. Możesz dołączyć dodatkowe glify, wybierając i edytując zakresy znaków wymienione poniżej, ale tę opcję można wybrać, aby szybko wygenerować minimalny zestaw znaków potrzebny do wyświetlenia ciągów zdefiniowanych w tabeli ciągów. Oczywiście jeśli tabela ciągów używa glifów, które nie są obecne w czcionce źródłowej TrueType, te znaki nie będą dostępne w czcionce GUIX i nie będą wyświetlane w systemie docelowym.

Aby wygenerować bardziej kompletną czcionkę lub czcionkę, która zawiera znaki, które mogą nie być używane w tabeli statycznie zdefiniowanych ciągów, możesz również wybrać zakresy znaków z poniższej listy. Pamiętaj, że możesz wybrać dowolną liczbę zakresów znaków i edytować rzeczywisty początkowy i końcowy kod znaku, który ma zostać uwzględniony w każdym wybranym zakresie.

Wstępnie zdefiniowane zakresy znaków i nazwy stron to tylko sugestie, które pozwalają łatwo wybrać zestaw znaków wymagany dla aktywnych języków używanych obecnie. Nazwy języków na liście nie mają żadnego wpływu na wygenerowaną czcionkę GUIX i możesz wpisać dowolny zakres znaków hex, który chcesz dla dowolnego włączonego lub wybranego zakresu znaków.

Jeśli na przykład chcesz wygenerować czcionkę zawierającą tylko znaki numeryczne, możesz wybrać stronę kodową "Ascii", ale wprowadzić wartość początkową 0030 i wartość końcową 0039, aby wygenerować czcionkę zawierającą tylko znaki liczbowe. Należy pamiętać, że wartości zakresu znaków zakodowane w formacie szesnastkowym, który jest normalną notacją dla tabel znaków Unicode.

Domyślnie program GUIX Studio i biblioteka GUIX obsługują kody znaków 0x0000 pośrednictwem 0xffff, które obejmują wszystkie aktywne języki, formularze matematyczne i inne symbole w użyciu już dziś. Jeśli wymagane jest użycie kodów znaków powyżej wartości 0xffff, w tym niektórych prywatnych obszarów użycia, należy włączyć pole wyboru "Obsługa rozszerzonego zakresu znaków". Gdy to pole wyboru jest zaznaczone, program GUIX Studio umożliwia użytkownikowi określenie zakresów znaków od 0x0000 do 0x10ffff, w tym zakresów znaków unicode użytku prywatnego. Jeśli ten rozszerzony zakres znaków jest wymagany, należy również zdefiniować opcję kompilacji biblioteki GUIX "GX_EXTENDED_UNICODE_SUPPORT", aby biblioteka GUIX obsługiła wewnętrznie 32-bitowe kody znaków, a nie domyślną konfigurację, która obsługuje 16-bitowe kody znaków.

Jeśli zaznaczysz zarówno pole wyboru "Uwzględnij zestaw znaków zdefiniowany przez tabelę ciągów", jak i co najmniej jeden z zakresów znaków na poniższej liście, program GUIX Studio połączy te wybory w najedyńczność zarówno wybranych zakresów, jak i tych znaków używanych w tabeli ciągów. Oczywiście wybrana czcionka źródłowa TrueType musi również zawierać wymagane znaki, aby program GUIX Studio tworzyć znaczące symboly dla każdej żądanej wartości znaku.

Po określeniu zakresu znaków określ wysokość czcionki w pikselach i format czcionki. Obsługiwane są zarówno czcionki anty aliasowe, jak i binarne. Czcionki binarne wymagają mniej statycznego obszaru przechowywania danych, jednak czcionki anty aliasów dają najlepszy wygląd na celach działających w skali szarości 4 BPP lub wyższych głębokościach kolorów.

>[!NOTE]  
> *"Wysokość czcionki" odnosi się do kwadratu EM czcionki. W tradycyjnych typach metalowych kwadrat EM był równy wysokości linii ciała metalowego, z którego wynosi się każda litera, a każda metalowa treść miała taki sam rozmiar. W przypadku typu metal rozmiar fizyczny litery zwykle nie może przekraczać kwadratu EM. W typie cyfrowym EM jest siatką dowolnej rozdzielczości, która jest używana jako przestrzeń projektowa czcionki cyfrowej. W przypadku tych czcionek cyfrowych często niektóre cechy glifów, takie jak akcenty i spadki, mogą wykraczać poza granice kwadratu EM. Wynik końcowy jest taki, że wysokość widżetu potrzebna do pełnego wyświetlenia określonej czcionki często musi być nieco większa niż żądana wysokość pikseli czcionki.*

Po zakończeniu wszystkich pól konfiguracji czcionki kliknij przycisk OK, aby utworzyć nowy zasób czcionki. Program GUIX Studio wygeneruje czcionkę zgodną z guix z wybranymi właściwościami, doda ją do zasobów projektu i udostępni czcionkę do użycia przez aplikację.

## <a name="pixel-map-resources"></a>Zasoby z mapą pikseli

Aby zarządzać zasobami mapy pikseli, należy najpierw rozwinąć sekcję ***** Mapy pikseli _ witryny _*_Widok zasobów,_*_ klikając pole _ *, co spowoduje, że zostanie wyświetlone okno dialogowe pokazane poniżej na rysunku *+* **_15:_**

Po `Pixelmap` rozwinięciu grupy powinna zostać wyświetlony podgląd podobny do tego:

![Zrzut ekranu przedstawiający sekcję Mapy pikseli w Widok zasobów.](./media/guix-studio/pixelmap_view.png)

**Rysunek 15**

Zasoby mapy pikseli składają się z co najmniej jednej mapy pikseli, z których każda zawiera podgląd obrazu mapy pikseli po lewej stronie, wymiary mapy pikseli w pikselach, unikatową nazwę logiczną i rozmiar magazynu mapy pikseli w wyjściowym pliku zasobów (w KB).

Pierwsza grupa map pikseli obejmuje wstępnie zdefiniowane systemowe mapy pikseli wymagane przez widżety GUIX, takie jak przyciski radiowe i pola wyboru. Dane mapy pikseli skojarzone z systemową mapą pikseli można zmienić, ale nie można zmienić nazw identyfikatorów map pikseli. Powyżej przedstawiono również kilka niestandardowych map pikseli o nazwach takich jak "BACKGROUND" i "BUTTON_ACTIVE". Są to przykłady map pikseli dodanych przez użytkownika do projektu, które mogą służyć do renderowania GX_PIXELMAP_BUTTON widget.

Ponieważ wiele projektów zawiera dużą liczbę map pikseli, widok mapy pikseli umożliwia zdefiniowanie dowolnej liczby folderów mapy pikseli w celu zorganizowania obrazów mapy pikseli. 

Dodawanie nowego folderu mapy pikseli odbywa się przez kliknięcie prawym przyciskiem myszy nagłówka sekcji Widok zasobów `Pixelmaps` wybranie pozycji "Dodaj folder". 

Aby zmodyfikować zasób mapy pikseli, kliknij dwukrotnie (lub kliknij prawym przyciskiem myszy i wybierz menu) w zasobie mapy pikseli. W tym oknie dialogowym zasób mapy pikseli można zmodyfikować w celu dopasowania go do potrzeb interfejsu użytkownika aplikacji. ***Rysunek 16** _ przedstawia okno dialogowe modyfikacji po *dwukrotnym kliknięciu RADIO_ON* _ * .

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie map pikseli.](./media/guix-studio/image49.jpg)

**Rysunek 16**

Okno dialogowe umożliwia zdefiniowanie nowej mapy pikseli lub `Edit Pixelmap` zmodyfikowanie zawartości istniejącej mapy pikseli. W tle program GUIX Studio odczytuje obraz wejściowy i konwertuje obraz na format, który może być `GUIX GX_PIXELMAP` używany przez bibliotekę GUIX. Program GUIX Studio konwertuje również przestrzeń kolorów obrazu przychodzącego na przestrzeń kolorów ekranu, na której będzie używana mapa pikseli.

Pierwsze pole tego okna dialogowego to ścieżka do obrazu źródłowego. Program GUIX Studio obsługuje dane wejściowe plików obrazów w formacie PNG (.png) lub JPEG (.jpg). Możesz użyć przycisku "przeglądaj", aby znaleźć żądany plik wejściowy w lokalnym systemie plików.

Jeśli to możliwe, lokalizacja pliku obrazu wejściowego jest przechowywana wewnętrznie przy użyciu ścieżki względnej projektu. Z tego powodu ważne jest, aby zachować wszystkie pliki obrazów we wspólnej lokalizacji i użyć wspólnej struktury drzewa katalogów dla projektów i plików obrazów, aby umożliwić przenoszenie projektów GUIX Studio z jednej stacji dewelopera do innej i nie utracić śledzenia danych wejściowych obrazu.

Pola `Pixelmap ID` umożliwiają określenie nazwy logicznej zasobu mapy pikseli. Ta nazwa wpisana w tym miejscu musi być unikatowa i musi być przestrzegana reguł składni nazw zmiennych języka C.

Pole wyboru Określ plik wyjściowy umożliwia określenie unikatowego pliku wyjściowego dla każdego mapowania pikseli. Jeśli to pole wyboru nie jest zaznaczone, dane mapy pikseli są zapisywane w domyślnym pliku zasobów dla tego wyświetlania. Jeśli pole wyboru jest zaznaczone, możesz wpisać określoną nazwę pliku, w którym będą zapisywane dane dla tej mapy pikseli. Celem tej opcji jest umożliwienie dzielenia danych mapy pikseli, które mogą być bardzo dużymi tablicami C, na wiele plików wyjściowych. Niektóre kompilatory mają trudności z obsługą plików języka C, które są setkami tysięcy wierszy źródłowych.

Pole wyboru "Kompresuj dane wyjściowe" umożliwia określenie, czy dane wyjściowe mapy pikseli są używane przez zastrzeżony algorytm kompresji GUIX. Skompresowane pliki wyjściowe są zwykle mniejsze, ale wymagają również czasu procesora do renderowania w miejsce docelowe. Najczęściej wybiera się kompresję dużych map pikseli i format nieskompresowany w przypadku mniejszych map pikseli.

Pole wyboru określa, w jaki sposób program GUIX Studio korzysta z informacji o kanale alfa, które czasami .png `Include Alpha Channel` w plikach wejściowych formatu. Jeśli to pole wyboru jest zaznaczone, a ekran jest uruchomiony z głębokością koloru 16 bpp lub wyższą, program GUIX Studio zachowa pełne przychodzące dane alfa w pliku wyjściowym. Jeśli to pole wyboru nie zostanie zaznaczone, GUIX wyprodukuje nieco mniejszy plik wyjściowy. Ten plik wyjściowy może zawierać przezroczystość, ale nie będzie zawierać pełnych informacji mieszania alfa.

Pole wyboru nakazuje programowi GUIX Studio zastosowanie zaawansowanego algorytmu ditheringu podczas konwertowania obrazu wejściowego do użycia z niższym `Dither` poziomem głębokości kolorów. Funkcja ditheringu jest zwykle włączona, ale może powodować większe pliki wyjściowe w przypadku kompresji, ponieważ będzie mniej powtarzających się pikseli.

Po odpowiednim skonfigurowaniu wszystkich opcji kliknij przycisk OK, aby utworzyć nowy zasób mapy pikseli. Program GUIX Studio odczyta plik obrazu wejściowego, zdekompresuje go, wykona konwersję i dithering przestrzeni kolorów, opcjonalnie ponownie skompresuje dane i zapisze dane w formacie zgodnym z `GX_PIXELMAP` GUIX. Nowa mapa pikseli jest dodawana do zasobów projektu i dostępna do użycia przez aplikację.

Aby dodać nowy zasób mapy pikseli, w sekcji witryny `Pixelmaps` ***Widok zasobów*** wybierz następujący przycisk:

![Dodaj przycisk New Pixel-map (Nowy mapa pikseli).](./media/guix-studio/image50.jpg)

**Edycja wsadowego mapowania pikseli**

Aby zmodyfikować właściwości wielu map pikseli, kliknij prawym przyciskiem myszy grupę lub folder pixelmap  i wybierz **polecenie** Edytuj mapy pikseli, aby wywołać okno dialogowe Edytowanie map pikseli.

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie map z wieloma pikselami.](./media/guix-studio/batch_pixelmap_edit.jpg)

Opis stanu pola wyboru:

![Zaznaczonego przycisku.](./media/guix-studio/checkbox_checked.jpg)
Ten stan oznacza, że wszystkie mapy pikseli mają zaznaczoną właściwość . Możesz usunąć zaznaczenie przycisku, aby zmienić właściwość dla wszystkich map pikseli.

![Przycisk niezaznaczone.](./media/guix-studio/checkbox_unchecked.jpg)
Ten stan oznacza, że wszystkie mapy pikseli mają właściwość niezaznaczone. Możesz sprawdzić przycisk, aby zmienić właściwość dla wszystkich map pikseli.

![Niezdefiniowany przycisk.](./media/guix-studio/checkbox_undetermined.jpg)
Ten stan oznacza, że mapy pikseli mają inny stan dla właściwości, można sprawdzić lub usunąć zaznaczenie przycisku, aby zmienić właściwość dla wszystkich map pikseli. W przeciwnym razie właściwość pozostaje niezmieniona.


## <a name="string-resources"></a>Zasoby ciągów

Po rozwinięciu grupy Ciągi powinna zostać wyświetlony podgląd tabeli ciągów projektu, jak pokazano poniżej:

![Zrzut ekranu przedstawiający rozwiniętą grupę Ciągi.](./media/guix-studio/string_res_view.png)

**Rysunek 17**

Zasoby ciągów składają się z co najmniej jednego ciągu, z których każdy ma unikatową nazwę logiczną. Na przykład na rysunku **17** nazwa logiczna "PATIENT_LIST" jest skojarzona z ciągiem "Lista pacjentów" wyświetlanym po prawej stronie. Ten zasób ciągu jest używany zawsze, gdy aplikacja PATIENT_LIST jako ciąg we właściwościach obiektu.

Zawsze pamiętaj, że nazwy identyfikatorów dla wszystkich typów zasobów muszą być nazwami zmiennych zgodnymi ze składnią języka C. Te nazwy będą szeroko używane, gdy pliki zasobów projektu i pliki specyfikacji są produkowane przez program Studio.

Aby zmodyfikować zasób ciągu, kliknij dwukrotnie (lub kliknij prawym przyciskiem myszy i wybierz menu) w zasobie ciągu, aby wywołać okno dialogowe ***Edytor tabeli ciągów** _. W _*_oknie dialogowym Edytor_*_ tabel ciągów można zmodyfikować zasób ciągu, aby dopasować go do potrzeb interfejsu użytkownika aplikacji. _*_Rysunek 18_*_ przedstawia okno dialogowe modyfikacji po *dwukrotnym kliknięciu STRING_13* _ STRING_13 *.

W tym przypadku nazwa identyfikatora ciągu jest wyświetlana po lewej stronie, a zawartość ciągu dla pierwszego języka lub języka referencyjnego jest wyświetlana po prawej stronie. Oczywiście dokładna zawartość ciągu jest bardzo specyficzna dla Twojej aplikacji, jednak układ podglądu grupy Ciąg jest spójny.

Program GUIX Studio obsługuje tekst statyczny i aplikację wielojęzykową, definiując i utrzymując tabelę ciągów. Tabela ciągów definiuje jeden identyfikator ciągu dla każdego rekordu i jedną stałą ciągu dla każdego rekordu dla każdego obsługiwanego języka.

Języki, które mają być obsługiwane przez aplikację, są definiowane przy użyciu okna dialogowego Konfiguracji języka, które podano poniżej:

![Zrzut ekranu przedstawiający okno dialogowe Konfiguracja języka.](./media/guix-studio/config_languages.png)

**Rysunek 18**

Okno dialogowe konfiguracji języka jest wywoływane przy użyciu ustawienia | Polecenie Languages w menu aplikacji. To okno dialogowe umożliwia zdefiniowanie liczby języków, które mają być obsługiwane przez aplikację, oraz nazwy lub identyfikatora języka, które mają być skojarzone z każdym językiem. Obsługiwane języki można modyfikować po utworzeniu projektu, ale jeśli język zostanie usunięty, należy pamiętać, że dane ciągu skojarzone z tym językiem również zostały usunięte i nie można ich pobrać.

Pole wyboru **"Zdefiniowane statycznie"** wskazuje, że wybrany język zostanie statycznie zdefiniowany w formacie kodu źródłowego w wygenerowanym pliku zasobów. Jeśli żadne języki nie są zdefiniowane statycznie, wskaźnik tabeli języka zostanie ustawiony na wartość NULL w wygenerowanej tabeli wyświetlania, a język musi zostać załadowany i zainstalowany przez aplikację przy użyciu interfejsów API modułu ładującego zasobów binarnych dostarczonych przez bibliotekę GUIX.

Pole wyboru **"Obsługa tekstu Bidi"** powoduje, że program GUIX Studio włączy obsługę dwukierunkowego renderowania tekstu. To pole wyboru należy włączyć, jeśli ciągi, które będą wprowadzane dla tego języka, wymagają dwukierunkowego renderowania tekstu.

Pole wyboru **"Generate Bidi Text in Display Order"**(Generowanie tekstu Bidi w kolejności wyświetlania) powoduje, że program GUIX Studio generuje tekst dwukierunkowy do pliku wyjściowego w kolejności wyświetlania. Jeśli ta opcja jest zaznaczona, przetwarzanie środowiska uruchomieniowego w bibliotece GUIX nie jest wymagane do poprawnego renderowania tekstu dwukierunkowego. Po wybraniu tej opcji renderowanie tekstu dwukierunkowego NIE powinno być włączone w bibliotece GUIX. Ta konfiguracja daje najlepszą wydajność środowiska uruchomieniowego, ale nie obsługuje renderowania dynamicznie zdefiniowanych dwukierunkowych ciągów tekstowych.

Pierwszy język lub "Indeks 1" jest określany jako "język referencyjny". Jest to język, który będzie używany przez program GUIX Studio podczas definiowania i edytowania projektu interfejsu użytkownika. Wszystkie inne języki w tabeli ciągów są nazywane językami tłumaczenia. Program GUIX Studio obsługuje eksportowanie i importowanie danych tabeli ciągów w plikach danych formatu XLIFF lub CSV standardowych w branży, wygodnych do wymiany informacji o ciągach z tłumaczami, którzy mogą pomóc deweloperowi aplikacji w dodawaniu tłumaczeń dla języków obsługiwanych poza językiem referencyjnym. Podczas eksportowania tabeli ciągów GUIX do pliku XLIFF lub CSV język referencyjny wraz z jednym językiem tłumaczenia są uwzględniane w pliku wymiany danych w postaci ciągu XLIFF lub CSV. Podobnie podczas importowania pliku XLIFF lub CSV zaimportowane dane są używane do wypełnienia jednego języka tłumaczenia w tabeli ciągów GUIX.

![Zrzut ekranu edytora tabeli ciągów.](./media/guix-studio/image53.jpg)

**Rysunek 19**

Okno dialogowe Edytor tabel ciągów najpierw wyświetla listę identyfikatorów ciągów po lewej stronie, a następnie dane ciągu języka referencyjnego. Jeśli zdefiniowano więcej niż jeden język, trzecia kolumna zawiera jeden z obsługiwanych języków tłumaczenia. Trzecią kolumnę można otworzyć i zamknąć, klikając małą strzałkę w prawym górnym rogu kolumny języka referencyjnego.

Gdy kolumna języka tłumaczenia jest widoczna, możesz przechodzić między językami tłumaczenia zawartymi w projekcie, klikając małe strzałki w prawym górnym rogu kolumny języka tłumaczenia na liście ciągów.

Rekord ciągu można edytować, klikając rekord w tabeli, aby go wybrać. Po wybraniu rekordu identyfikator ciągu rekordu i zawartość ciągu są wyświetlane w polach poniżej widoku tabeli. Możesz wpisać nowe wartości w tych polach, aby zmodyfikować identyfikator ciągu i zawartość ciągu.

Pole po prawej stronie widoku tabeli zawiera podglądy widżetów odwołujące się do wybranego ciągu. Jest to przydatne, aby sprawdzić, czy edytowany ciąg przekroczy określony obszar widżetu.

Pola po prawej stronie zawartości ciągu obejmują:

- "Liczba odwołań": to pole wskazuje, jak często w projekcie GUIX Studio jest używany konkretny identyfikator ciągu. Jeśli liczba od referencyjnych jest 0, ten ciąg może być przestarzały i opcjonalnie może zostać usunięty przez użytkownika.
- Szerokość ciągu (w pikselach) wskazuje szerokość wyświetlania ciągu przy użyciu wskazanej czcionki.
- Pole "Uwagi" jest opcjonalnym polem komentarza, które umożliwia dodawanie informacji o celu lub użyciu każdego ciągu. Te uwagi są zawarte w wszelkich wyeksportowanych plikach danych ciągów XLIFF, aby pomóc tłumaczom w dokładnych i znaczących tłumaczeniach ciągów.

Za każdym razem, gdy zostanie ***otwarte okno*** dialogowe Edytor tabel ciągów, możesz dodać do projektu dodatkowe ciągi, klikając przycisk Dodaj ciąg w górnej części okna dialogowego. Przestarzałe lub nieużywane ciągi można usunąć z projektu, wybierając najpierw ciąg, a następnie klikając przycisk Usuń ciąg w górnej części okna dialogowego.

Oprócz ręcznego dodawania nowych ciągów do projektu przy użyciu okna dialogowego Edytor tabel ciągów, można również pośrednio dodać nowe ciągi, po prostu wpisując zawartość ciągu w polu "Tekst" widoku właściwości dowolnego widżetu obsługującego tekst. Innymi słowy, podczas dodawania nowych widżetów w widoku docelowym lub wpisywania informacji tekstowych w widoku właściwości te akcje automatycznie tworzą nowe wpisy w tabeli ciągów projektu.

## <a name="adding-language-translations"></a>Dodawanie tłumaczeń języka

Edytor tabel ciągów GUIX Studio obsługuje przepływ pracy definicji języka, który umożliwia deweloperowi utworzenie aplikacji przy użyciu jego języka podstawowego, a następnie wyeksportowanie danych ciągu do standardowego pliku XML lub CSV schematu do wysłania do eksperta ds. tłumaczenia języka. Plik tłumaczenia jest następnie zwracany do dewelopera, który może zaimportować tłumaczenia języka z powrotem do swojego projektu studio, dodając w ten sposób obsługę nowego języka do swojej aplikacji.

Ta funkcja jest wywoływana przy użyciu przycisków Eksportuj (aby zapisać dane ciągu w pliku) i Importuj (aby odczytać przetłumaczone ciągi) w górnej części Edytora tabel ciągów. Przycisk Eksportuj służy do tworzenia pliku XML lub CSV schematu XLIFF, który zawiera ciągi języka referencyjnego. Ten plik może być używany przez tłumacza przy użyciu narzędzi i edytorów, które obsługują standardowy format pliku XLIFF lub CSV.

Gdy ekspert ds. tłumaczenia zwróci Ci plik XLIFF z nowymi tłumaczeniami ciągów, możesz użyć przycisku Importuj, aby odczytać dane z tego pliku XLIFF lub CSV. Jeśli plik XLIFF lub CSV zawiera nowy język, nowy język zostanie dodany do projektu. Jeśli plik XLIFF zawiera nowe dane ciągu dla istniejącego języka, te nowe dane są importowane do projektu. Ciągi języka referencyjnego nie są modyfikowane przez operację importu.

Po kliknięciu przycisku Eksportuj zostanie wyświetlone okno dialogowe Kontrolka eksportu XLIFF/CSV, które jest wyświetlane poniżej:

![Zrzut ekranu przedstawiający okno dialogowe Kontrolka eksportu XLIFF/CSV.](./media/guix-studio/image54.jpg)

**Rysunek 20**

Pola Source Language (Język źródłowy) i Target Language (Język docelowy) określają, które kolumny tabeli ciągów zostaną zapisane w pliku XLIFF lub CSV jako język referencyjny i język tłumaczenia. Język źródłowy to ciągi referencyjne, a Język docelowy to język, dla którego tłumacz dostarcza przetłumaczone dane ciągu.

Pole Wersja XLIFF określa jedną z dwóch głównych wersji formatu pliku XLIFF: 1.2 lub 2.0 (lub nowszą). Te standardy formatu plików XLIFF są niezgodne i przed użyciem poleceń eksportu/importu XLIFF musisz wiedzieć, z jakiej wersji korzystają narzędzia. Więcej informacji na temat schematu XLIFF i standardów XLIFF można znaleźć tutaj:

- wersja 1.2: [https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html](https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html)
- wersja 2.0: [https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0os.pdf](https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0-os.pdf)

Pola nazwy pliku wyjściowego i ścieżki wyjściowej umożliwiają określenie nazwy pliku i lokalizacji, w której zostanie zapisany plik wyjściowy. Nazwa pliku zależy całkowicie od użytkownika, jednak zalecamy użycie nazw, które wskazują języki źródłowe i docelowe zawarte w wyeksportowanych plikach.
