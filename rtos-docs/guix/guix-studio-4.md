---
title: Zasoby programu GUIX Studio
description: Program GUIX Studio umożliwia zarządzanie wszystkimi zasobami interfejsu użytkownika, które będą używane przez aplikację na potrzeby kolorów, czcionek, map pikseli i ciągów. W poniższych sekcjach opisano sposób dodawania, modyfikowania i usuwania zasobów w ramach projektu ekranu interfejsu użytkownika.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 3c3769c3ddf0eef73546627f1f50fa3d11b16948
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823059"
---
# <a name="chapter-4-guix-studio-resources"></a>Rozdział 4: zasoby programu GUIX Studio

Program GUIX Studio umożliwia zarządzanie wszystkimi zasobami interfejsu użytkownika, które będą używane przez aplikację na potrzeby kolorów, czcionek, map pikseli i ciągów. W poniższych sekcjach opisano sposób dodawania, modyfikowania i usuwania zasobów w ramach projektu ekranu interfejsu użytkownika. 

Wszystkie zarządzanie zasobami odbywa się w ramach programu ***Widok zasobów** _ interfejsu użytkownika GUIX Studio, jak pokazano poniżej w _ *_rysunek 8_* *.

![Zrzut ekranu GUIX Studio Widok zasobów.](./media/guix-studio/image38.jpg)

**Rysunek 8.**

## <a name="color-resources"></a>Zasoby koloru

Sekcja ***Colors** _ _*_Widok zasobów_*_ umożliwia zarządzanie zasobami kolorów. Ten widok można rozwinąć *+* , klikając pole _ * w nagłówku widoku, co spowoduje wyświetlenie widoku pokazanego poniżej na **_rysunku 9_**:

![Zrzut ekranu przedstawiający sekcję kolory Widok zasobów](./media/guix-studio/image_39.png)

**Rysunek 9.**

Zasoby koloru składają się z co najmniej jednego koloru, z których każdy ma unikatową nazwę logiczną. Na przykład na **rysunku 9** Kanwa nazwy logicznej **,** czyli Identyfikator koloru systemu dla koloru wypełnienia tła ekranu, jest skojarzony z kolorem fizycznym czarny. Ten zasób koloru jest używany za każdym razem, gdy aplikacja określi **GX_COLOR_ID_CANVAS** jako kolor we właściwościach obiektu.

Kolor "próbnik" wskazujący, że kolor RGB jest pokazywany po lewej stronie, a następnie nazwę identyfikatora koloru. W dowolnym momencie można zmienić wartość RGB skojarzoną z dowolną nazwą identyfikatora. Nie można zmienić wstępnie zdefiniowanych nazw identyfikatorów kolorów systemu, ponieważ są one używane wewnętrznie przez bibliotekę GUIX. Można jednak zmienić dowolną wartość koloru. Zmiana wartości koloru systemu jest **zmianą globalną**. Oznacza to, że każdy widżet, który nie ma określonego przypisania koloru, zajmie się nową wartością koloru systemu.

Można zmienić nazwę koloru i wartość koloru dla kolorów niestandardowych, które zostały dodane do motywu.

Aby zmodyfikować zasób koloru, kliknij dwukrotnie (lub kliknij prawym przyciskiem myszy i wybierz pozycję menu) w zasobie koloru. Ta akcja powoduje wyświetlenie okna dialogowego definicji koloru. W tym oknie dialogowym można zmodyfikować zasób koloru, aby odpowiadał wymaganiom interfejsu użytkownika aplikacji. ***Rysunek 10** _ pokazuje okno dialogowe modyfikacji, gdy zostanie kliknięta podwójna *Kanwa**. Wygląd tego okna dialogowego zmieni się w zależności od ustawień formatu koloru wyświetlanego na ekranie docelowym.

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie koloru.](./media/guix-studio/edit_color.png)

**Rysunek 10**

Wygląd okna dialogowego Edytuj kolor zostanie zmieniony w zależności od koloru i konfiguracji formatu koloru bieżącego ekranu.

Aby dodać nowy zasób koloru, w sekcji ***Colors** _ w *_Widok zasobów_** wybierz następujący przycisk:

![Przycisk Dodaj nowy kolor](./media/guix-studio/image41.jpg)

Korzystając z okna dialogowego wynikowego koloru, można dodać nowy zasób koloru, jak pokazano poniżej w ***rysunek 11**:*

![Zrzut ekranu przedstawiający nowy kolor w oknie dialogowym Edytowanie koloru.](./media/guix-studio/new_color.png)

**Rysunek 11**

Po wykonaniu tych kroków wybierz pozycję **Zapisz** nowy zasób koloru o nazwie **NEW_COLOR** przy użyciu koloru fizycznego zielony będzie dostępny dla aplikacji.

**Specjalne zagadnienia dotyczące zmiany ustawień wyświetlania kolorów:**

Podczas tworzenia nowego projektu zostanie automatycznie wyświetlony monit o skonfigurowanie wyświetlania projektu oraz formatu koloru poszczególnych ekranów. W większości przypadków należy wprowadzić te opcje jeden raz i nie trzeba modyfikować tych ustawień konfiguracji.

Możesz określić, że w późniejszym czasie trzeba zmienić ustawienia formatowania koloru wyświetlania. W takim przypadku GUIX Studio będzie najlepiej pasować do konwersji bieżącego systemu i koloru RGB z starego formatu koloru na nowy format koloru. Ta konwersja jest zgodna z kilkoma regułami logicznymi.

W przypadku kolorów zdefiniowanych przez użytkownika program GUIX Studio zawsze próbuje skonwertować poprzedni kolor na najbliższy pasujący kolor w nowym formacie koloru. W przypadku konwersji z dużej głębi kolorów, takiej jak format koloru 16 BPP 5:6:5 na szary lub monochromatyczny format koloru, ta zmiana może spowodować nieodpowiednie konwersje kolorów. Podczas wprowadzania dużej zmiany w ustawieniach głębi kolorów wyświetlania niektóre ręczne aktualizacje dla nowej tabeli kolorów zdefiniowanej przez użytkownika mogą być wymagane.

W przypadku wstępnie zdefiniowanych kolorów systemu GUIX Studio wewnętrznie definiuje trzy unikatowe domyślne tabele kolorów. Jedna domyślna tabela kolorów jest używana dla wszystkich głębi kolorów o wartości większej niż 4-BPP szarej skali. druga domyślna tabela kolorów jest używana dla formatów koloru szarego skalowania (1 BPP < display_color_format <= 4bpp), a Wreszcie trzecia domyślna tabela kolorów systemu jest używana dla formatu koloru monochromatyczny.

Po przełączeniu formatu wyświetlanego koloru przy użyciu okna dialogowego konfiguracji projektu są stosowane następujące reguły:

1) Jeśli w starym i nowym formacie koloru wyświetlania są używane różne domyślne tabele kolorów systemowych zdefiniowane powyżej, kolory systemu są resetowane do wstępnie zdefiniowanych kolorów domyślnych. Innymi słowy, jeśli zmienisz kolor na szary lub Skala szarości z szarym skalowaniem na czarną głębię kolorów, kolory systemu zostaną zresetowane do wewnętrznie zdefiniowanych wartości domyślnych dla nowej głębi kolorów. Chociaż może to spowodować utratę niektórych dostosowanych informacji o kolorach, rozwiązanie to zapewnia rozsądny punkt początkowy, gdy wprowadzisz znaczną zmianę ustawień formatu koloru wyświetlania.

2) Jeśli stare i nowe formaty kolorów używają tej samej domyślnej tabeli kolorów, co oznacza, że wprowadzasz mniej znaczące zmiany formatu koloru, program GUIX Studio przetestuje każdy kolor systemu, aby ustalić, czy zmodyfikowano wartość koloru systemu RGB z wartości domyślnej. Jeśli wartość RGB koloru systemu została zmodyfikowana, GUIX Studio wykona konwersję najlepiej dopasowanej ze starego formatu koloru do nowego formatu koloru. Jeśli kolor systemu nie został zmodyfikowany, zostanie zresetowany do domyślnego koloru dla nowego formatu koloru.

**Specjalne zagadnienia dotyczące operacji w trybie palety:**

Jeśli projekt jest skonfigurowany pod kątem formatu koloru w trybie 256 palety kolorów, użytkownik może skonfigurować sposób definiowania i używania palety. Możesz uzyskać dostęp do definicji palety i edytować ją za pomocą opcji Konfiguruj | Okno dialogowe motywy i jeśli projekt jest ustawiony na 8 BPP, powinien zostać wyświetlony przycisk "Edytuj paletę". Kliknij ten przycisk, aby wyświetlić okno dialogowe Edytowanie palety:

![Zrzut ekranu przedstawiający okno dialogowe Edytowanie palety.](./media/guix-studio/edit_palette.png)

GUIX Studio dzieli paletę na dwie sekcje: sekcję "zdefiniowane przez użytkownika" i sekcję "wygenerowany automatycznie". GUIX Studio uruchamia zaawansowany, optymalny algorytm generowania palety, aby utworzyć najlepszą paletę do wyświetlania obrazów dołączonych do każdego motywu. Można wydzielenie dowolną liczbę wpisów palety, które należy zdefiniować, wpisując liczbę w polu "wstępnie zdefiniowane wpisy palety" i wprowadzając dowolną wartość RGB dla dowolnego z tych miejsc. Pozostałe miejsca zostaną przydzieleni do programu Studio, aby utworzyć optymalną paletę kolorów do wyświetlania obrazów.

W przypadku działania w tym trybie, jeśli chcesz edytować kolor zdefiniowany w widoku zasobów, Edytor kolorów umożliwi wybranie tylko z zdefiniowanych wstępnie zdefiniowanych wpisów palety. Wynika to z faktu, że pozostałe wpisy w palecie są generowane automatycznie przez program GUIX Studio i zmienią się, ponieważ obrazy dodawane do projektu są modyfikowane.

Jeśli jest wymagane Wyświetlanie czcionek antyaliasowych podczas działania w trybie palety 8bpp, należy zdefiniować tablicę wpisów palety, która tworzy gradient dla każdego pierwszego planu/koloru tła, aby wyświetlić tekst antyaliasowy. Możesz użyć 8 wpisów palety dla gradientu dla każdej kombinacji kolorów lub 16 wpisów palety dla gładkiego gradientu. Ta liczba użytych wpisów palety jest określana na podstawie pola wyboru "Liczba kolorów tekstu przeciwaliasowego w trybie palety" w oknie dialogowym konfiguracji projektu. Możesz użyć gradientu zawierającego tylko osiem wpisów, aby zminimalizować liczbę elementów palety używanych dla każdej kombinacji kolorów, lub użyć 16 gradientów wejścia, aby zapewnić gładki wygląd tekstu.

Aby uprościć Definiowanie gradientu koloru do wyświetlania tekstu antyaliasowego lub wygenerować gradient koloru dla własnego użycia, okno dialogowe Edytowanie palety zawiera przycisk Generuj gradient. Aby użyć tej funkcji, należy najpierw przypisać wartości r:g: b koloru początkowego i końcowego gradientu.

Jeśli na przykład chcesz wyświetlić czerwony tekst na średnim, szarym tle przy użyciu ośmiu wpisów z palety, zaczynając od indeksu 50, należy przypisać r:g: b 255:0:0 do indeksu palety 50, a r:g: b wartość 128:128:128 do indeksu palety 57. Wprowadź te wartości indeksów palety do pól indeksów początkowych i indeksów końcowych w tym oknie dialogowym, a następnie kliknij przycisk Generuj gradient. Wpisy palety od 51 do 56 zostaną zainicjowane w celu zdefiniowania płynnej przejścia gradientu między kolorami powiązanymi.

## <a name="font-resources"></a>Zasoby czcionek

Aby zarządzać zasobami czcionek, należy najpierw rozwinąć sekcję ***Fonts** _ _*_Widok zasobów_*_ *+* , klikając pole _ *, co spowoduje wyświetlenie okna dialogowego przedstawionego poniżej na **_rysunku 12_**:

![Zrzut ekranu przedstawiający sekcję czcionki w Widok zasobów.](./media/guix-studio/image44.jpg)

**Rysunek 12**

Zasoby czcionek składają się z jednej lub kilku czcionek, z których każda ma unikatową nazwę logiczną. Na przykład na **rysunku 12** **system** nazw logicznych jest skojarzony z określoną czcionką. Ten zasób czcionki jest używany za każdym razem, gdy aplikacja określa **system** jako czcionkę we właściwościach obiektu. Grupa czcionek pokazuje, że w lewej części symboli czcionki są wyświetlane w widoku WYSIWYG, Wysokość czcionki w pikselach, nazwę identyfikatora czcionki i rozmiar czcionki (w KB).

W widoku powyżej pierwsze cztery czcionki to wstępnie zdefiniowane czcionki domyślne, które są wymagane przez bibliotekę GUIX. Można zmienić dane czcionki skojarzone z tymi czcionkami, ale nie można zmienić tych nazw.

Ostatnia czcionka pokazana powyżej o nazwie "kursywa" jest czcionką niestandardową, która została dodana do projektu przez użytkownika.

Aby zmodyfikować zasób czcionki, kliknij dwukrotnie (lub kliknij prawym przyciskiem myszy i wybierz pozycję menu) dla zasobu czcionki. Z tego okna dialogowego można zmodyfikować zasób czcionki w taki sposób, aby odpowiadał wymaganiom interfejsu użytkownika aplikacji. ***Rysunek 13** _ pokazuje okno dialogowe modyfikacji po dwukrotnym kliknięciu _ *system**.

! [[Zrzut ekranu okna dialogowego modyfikacji, gdy system jest dwukrotnie kliknięty.](./media/guix-studio/edit_system_font.png)

**Rysunek 13**

Aby dodać nowy zasób czcionki, w sekcji ***Fonts** _ *_Widok zasobów_** wybierz następujący przycisk:

![Przycisk Dodaj nową czcionkę](./media/guix-studio/image46.jpg)

Spowoduje to wywołanie `Font Edit` okna dialogowego umożliwiającego dodanie nowego zasobu czcionki, jak pokazano poniżej na ***rysunku 14***:

![Zrzut ekranu przedstawiający okno dialogowe modyfikacji, w którym można dodać nowy zasób czcionki.](./media/guix-studio/add_new_font.png)

**Rysunek 14**

Nowe czcionki GUIX są tworzone przez GUIX Studio, które renderuje wybraną czcionkę TrueType w określonym rozmiarze. W związku z tym powyższe okno dialogowe wymaga ścieżki czcionki TrueType. Możesz użyć przycisku Przeglądaj, aby przejść do katalogu zawierającego pliki czcionek w systemie deweloperskim. Kilka czcionek TrueType znajduje się również w podfolderze GUIX/Fonts, wszędzie tam, gdzie zainstalowano program GUIX Studio.

Jeśli jest to możliwe, lokalizacja pliku czcionki TrueType jest przechowywana wewnętrznie przy użyciu ścieżki względnej dla projektu. Z tego powodu ważne jest, aby zachować wszystkie pliki czcionek we wspólnej lokalizacji i używać wspólnej struktury drzewa katalogów dla projektów i plików czcionek, aby umożliwić przenoszenie projektów GUIX Studio z jednej stacji deweloperskiej do innej.

Pole Nazwa czcionki pozwala określić nazwę identyfikatora zasobu czcionki. Jest to identyfikator zasobu, który będzie używany w kodzie wygenerowanym przez program GUIX Studio, a także używany przez aplikację podczas odwoływania się do czcionki. Ta nazwa musi być zgodna ze składnią nazw zmiennych języka C.

Po wybraniu pliku czcionki TrueType, który ma być używany jako dane wejściowe, wprowadź nazwę logiczną czcionki.

Pole wyboru "**Generuj informacje o kerningu**" instruuje program GUIX Studio o uwzględnienie informacji o kerningu w wygenerowanej czcionce, która jest używana do dostosowywania względnych położenia symboli w ciągu. Jeśli chcesz zastosować kerning z użyciem ciągów, musisz użyć czcionki zawierającej informacje o kerningu i włączyć to pole wyboru. Należy również zdefiniować opcję kompilacji biblioteki GUIX "GX_FONT_KERNING_SUPPORT", aby umożliwić renderowanie tekstu z informacjami o kerningu.

Pole wyboru "**Uwzględnij zestaw znaków zdefiniowany przez tabelę ciągów**" instruuje program GUIX Studio, aby dołączył te glify, do których odwołuje się tabela ciągów statycznych w wygenerowanej czcionce. Można dołączać dodatkowe symbole, wybierając i edytując wymienione poniżej zakresy znaków, ale tę opcję można wybrać, aby szybko wygenerować minimalny zestaw znaków, który jest wymagany do wyświetlania ciągów zdefiniowanych w tabeli ciągów. Oczywiście, jeśli tabela ciągów używa symboli, które nie występują w czcionce źródłowej TrueType, te znaki nie będą dostępne w czcionce GUIX i nie będą wyświetlane w systemie docelowym.

Aby wygenerować bardziej kompletną czcionkę lub czcionkę zawierającą znaki, które nie mogą być używane w statycznie zdefiniowanej tabeli ciągów, można również wybrać zakresy znaków z poniższej listy. Należy zauważyć, że można wybrać dowolną liczbę zakresów znaków i można edytować faktyczny, początkowy i końcowy kod znaku do uwzględnienia w każdym z wybranych zakresów.

Wstępnie zdefiniowane zakresy znaków i nazwy stron to tylko sugestie pozwalające łatwo wybrać zestaw znaków wymagany dla aktywnych języków używanych dzisiaj. Wymienione nazwy języka nie mają wpływu na wygenerowaną czcionkę GUIX i można wpisywać dowolne zakresy znaków szesnastkowych, które mają być stosowane dla dowolnego włączonego lub zaznaczonego zakresu znaków.

Na przykład jeśli chcesz wygenerować czcionkę zawierającą tylko znaki numeryczne, możesz wybrać stronę kodową "ASCII", ale wprowadzić wartość początkową 0030 i wartość końcową 0039, aby wygenerować czcionkę zawierającą tylko znaki numeryczne. Należy zauważyć, że wartości zakresu znaków kodowane w formacie szesnastkowym, czyli notacją normalną dla tabel znaków Unicode.

Domyślnie GUIX Studio i Biblioteka GUIX obsługują kody znaków 0x0000 za pomocą 0xFFFF, które obejmują wszystkie aktywne Języki, formy matematyczne i inne symbole używane dzisiaj. Jeśli wymagane jest użycie kodów znaków powyżej wartości 0xFFFF, w tym niektórych obszarów użytku prywatnego, należy włączyć pole wyboru "Obsługuj zakres znaków rozszerzonych". Gdy to pole wyboru jest zaznaczone, GUIX Studio zezwala użytkownikowi na Określanie zakresów znaków z 0x0000 przez 0x10FFFF, które obejmują zakresy znaków prywatnych Unicode. Jeśli jest wymagany ten rozszerzony zakres znaków, należy również zdefiniować opcję kompilacji biblioteki GUIX "GX_EXTENDED_UNICODE_SUPPORT", tak aby Biblioteka GUIX obsługiwała wewnętrznie kody znaków 32-bitowe zamiast domyślnej konfiguracji, która obsługuje 16 kodów znaków.

Jeśli zaznaczysz pole wyboru "Uwzględnij zestaw znaków zdefiniowany przez tabelę ciągów" i co najmniej jeden z zakresów znaków na poniższej liście, program GUIX Studio połączy te wybory w nadzbiór wybranych zakresów i tych znaków, które są używane w tabeli ciągów. Oczywiście wybrana czcionka źródłowa TrueType musi zawierać również wymagane znaki, aby GUIX Studio generowała znaczące symbole dla każdej wymaganej wartości znaku.

Po ustaleniu zakresu znaków Określ wysokość czcionki w pikselach i format czcionki. Obsługiwane są zarówno czcionki wygładzone, jak i binarne. Czcionki binarne wymagają mniej statycznego obszaru magazynowania danych, jednak czcionki z aliasami dają najlepszy wygląd w przypadku obiektów docelowych, które działają w skali szarości o wartości 4 BPP lub wyższej.

>[!NOTE]  
> *"Wysokość czcionki" odnosi się do znaku PAUZy czcionki. W przypadku tradycyjnego typu metalu, kwadracik jest równy wysokości linii ciała metalu, z której rośnie każda litera, a każda z nich jest w tym samym rozmiarze. W przypadku typu metalu rozmiar fizyczny litery nie może zwykle przekroczyć kwadratu EM. W polu Typ cyfrowy EM to siatka dowolnej rozdzielczości, która jest używana jako przestrzeń projektowa czcionki cyfrowej. W przypadku tych czcionek cyfrowych często niektóre funkcje glifów, takie jak akcenty i znaki, mogą wykraczać poza limity w kwadracie. Wynik końcowy polega na tym, że wysokość widżetu potrzebna do pełnej wyświetlania konkretnej czcionki często będzie musiała być nieco większa, a następnie żądana wysokość pikseli czcionki.*

Po zakończeniu wszystkich pól konfiguracji czcionek kliknij przycisk OK, aby utworzyć nowy zasób czcionki. Program GUIX Studio wygeneruje czcionkę zgodną z GUIX z wybranymi właściwościami, doda tę czcionkę do zasobów projektu i udostępnienie czcionki do użycia przez aplikację.

## <a name="pixel-map-resources"></a>Zasoby mapy pikseli

Aby zarządzać zasobami mapy pikseli, należy najpierw rozwinąć sekcję ***Pixel-Maps** _ w _*_Widok zasobów_*_ , klikając *+* pole _ *, co spowoduje wyświetlenie okna dialogowego przedstawionego poniżej na **_rysunku 15_**:

Gdy `Pixelmap` Grupa zostanie rozwinięta, powinna zostać wyświetlona wersja zapoznawcza podobna do tej:

![Zrzut ekranu przedstawiający sekcję mapy pikseli w Widok zasobów.](./media/guix-studio/pixelmap_view.png)

**Rysunek 15**

Zasoby mapy pikseli składają się z co najmniej jednej mapy pikseli, z których każdy zawiera podgląd obrazu mapy pikseli po lewej stronie, wymiary mapy pikseli w pikselach, unikatową nazwę logiczną i rozmiar magazynu pikseli mapy w pliku zasobów wyjściowych (w KB).

Pierwsza grupa map pikseli obejmuje wstępnie zdefiniowane mapy pikseli systemu wymagane przez widżety GUIX, takie jak przyciski radiowe i pola wyboru. Można zmienić dane mapy pikseli skojarzone z mapami pikseli systemu, ale nie można zmienić tych nazw identyfikatorów pikseli. Podano również kilka niestandardowych map pikseli z nazwami takimi jak "BACKGROUND" i "BUTTON_ACTIVE". Są to przykładowe mapy pikseli, które użytkownik dodał do projektu, który może służyć do renderowania widżetu GX_PIXELMAP_BUTTON.

Ponieważ wiele projektów zawiera dużą liczbę map pikseli, widok mapy pikseli pozwala zdefiniować dowolną liczbę folderów map pikseli do organizowania obrazów mapy pikseli. 

Dodawanie nowego folderu mapy pikseli odbywa się przez kliknięcie prawym przyciskiem myszy `Pixelmaps` nagłówka sekcji ***Widok zasobów*** wybranie pozycji "Dodaj folder".

Aby zmodyfikować zasób mapy pikseli, kliknij dwukrotnie (lub kliknij prawym przyciskiem myszy i wybierz pozycję menu) w zasobie mapy pikseli. Z tego okna dialogowego zasób mapy pikseli można zmodyfikować w taki sposób, aby odpowiadał wymaganiom interfejsu użytkownika aplikacji. ***Rysunek 16** _ pokazuje okno dialogowe modyfikacji, gdy element _ *RADIO_ON** jest dwukrotnie kliknięty.

![Zrzut ekranu okna dialogowego Edytowanie map pikseli.](./media/guix-studio/image49.jpg)

**Rysunek 16**

`Edit Pixelmap`Okno dialogowe umożliwia zdefiniowanie nowej mapy pikseli lub zmodyfikowanie zawartości istniejącej mapy pikseli. W tle program GUIX Studio odczytuje obraz wejściowy i konwertuje obraz do `GUIX GX_PIXELMAP` formatu, który może być używany przez bibliotekę GUIX. Program GUIX Studio konwertuje również przestrzeń kolorów przychodzącego obrazu na przestrzeń kolorów ekranu, na którym zostanie użyta Mapa pikseli.

Pierwsze pole tego okna dialogowego jest ścieżką do obrazu źródłowego. Program GUIX Studio obsługuje wprowadzanie plików obrazów w formacie PNG (PNG) lub JPEG (jpg). Możesz użyć przycisku Przeglądaj, aby znaleźć żądany plik wejściowy w lokalnym systemie plików.

Jeśli jest to możliwe, lokalizacja wejściowego pliku obrazu jest przechowywana wewnętrznie przy użyciu ścieżki względnej dla projektu. Z tego powodu ważne jest, aby zachować wszystkie pliki obrazów we wspólnej lokalizacji i korzystać ze wspólnej struktury drzewa katalogów dla projektów i plików obrazów w celu umożliwienia przenoszenia projektów GUIX Studio z jednej stacji deweloperskiej do innej i nie utraty śledzenia danych wejściowych obrazu.

`Pixelmap ID`Pola umożliwiają określenie logicznej nazwy zasobu mapy pikseli. Wpisana tutaj nazwa musi być unikatowa i musi być zgodna z regułami składni nazw zmiennych języka C.

Pole wyboru Określ plik wyjściowy umożliwia określenie unikatowego pliku wyjściowego dla każdej mapy pikseli. Jeśli to pole wyboru nie jest zaznaczone, dane mapy pikseli są zapisywane w domyślnym pliku zasobów dla tego ekranu. Jeśli pole wyboru jest zaznaczone, można wpisać określoną nazwę pliku, w której będą zapisywane dane dla mapy pikseli. Celem tej opcji jest umożliwienie podzielenia danych mapy pikseli, które mogą być bardzo dużymi tablicami C w wielu plikach wyjściowych. Niektóre kompilatory wynoszą problemy z obsługą plików C, które są setkami tysięcy wierszy źródłowych.

Pole wyboru "Kompresuj dane wyjściowe" pozwala określić, czy dane wyjściowe mapy pikseli używają własnościowego algorytmu kompresji GUIX. Skompresowane pliki wyjściowe są zwykle mniejsze, ale wymagają one również czasu procesora do renderowania na miejscu docelowym. Najczęściej będziesz wybierać kompresję dla dużych map pikseli i użyć nieskompresowanego formatu dla mniejszych map pikseli.

`Include Alpha Channel`Pole wyboru określa, w jaki sposób GUIX Studio wykorzystuje informacje o kanale alfa, czasami obecne w plikach wejściowych formatu PNG. Jeśli to pole wyboru jest zaznaczone, a wyświetlacz jest uruchomiony o 16-BPP głębi kolorów lub wyższej, program GUIX Studio zachowa pełne przychodzące dane alfa w pliku wyjściowym. Jeśli to pole wyboru nie jest zaznaczone, GUIX wygeneruje nieco mniejszy plik wyjściowy. Ten plik wyjściowy może zawierać przezroczystość, ale nie będzie zawierać pełnych informacji alfa-Blend.

To `Dither` pole wyboru instruuje program GUIX Studio o zastosowanie zaawansowanego algorytmu symulowania kolorów podczas konwertowania obrazu wejściowego do użycia z niższym kolorem głębokości wyświetlania. Symulacja jest zwykle włączona, ale może spowodować większe pliki wyjściowe, jeśli jest używana kompresja, ponieważ będzie mniej powtarzanych pikseli.

Po wybraniu wszystkich opcji kliknij przycisk OK, aby utworzyć nowy zasób mapy pikseli. Program GUIX Studio odczyta plik obrazu wejściowego, dekompresuje go, przeprowadzi konwersję przestrzeni kolorów i Roztrząsanie, opcjonalnie ponownie kompresuje dane i zapisuje dane w formacie zgodnym z GUIX `GX_PIXELMAP` . Nowa mapa pikseli zostanie dodana do zasobów projektu i udostępniona do użycia przez aplikację.

Aby dodać nowy zasób mapy pikseli, w `Pixelmaps` sekcji ***Widok zasobów*** wybierz następujący przycisk:

![Przycisk Dodaj nowy piksel-mapa.](./media/guix-studio/image50.jpg)

## <a name="string-resources"></a>Zasoby ciągów

Po rozwinięciu grupy ciągów powinna zostać wyświetlona wersja zapoznawcza tabeli ciągów projektu, jak pokazano poniżej:

![Zrzut ekranu grupy rozwinięte ciągi.](./media/guix-studio/string_res_view.png)

**Rysunek 17**

Zasoby ciągu składają się z co najmniej jednego ciągu, z których każdy ma unikatową nazwę logiczną. Na przykład na **rysunku 17** nazwa logiczna "PATIENT_LIST" jest skojarzona z ciągiem "Lista pacjentów" pokazywanym po prawej stronie. Ten zasób ciągu jest używany za każdym razem, gdy aplikacja określa PATIENT_LIST jako ciąg we właściwościach obiektu.

Należy zawsze pamiętać, że nazwy identyfikatorów dla wszystkich typów zasobów muszą być nazwami zmiennych zgodnymi ze składnią języka C. Te nazwy będą używane w szerokim czasie, gdy pliki zasobów projektu i pliki specyfikacji są tworzone przez Studio.

Aby zmodyfikować zasób ciągu, kliknij dwukrotnie (lub kliknij prawym przyciskiem myszy i wybierz pozycję menu) w polu zasób ciągu, aby wywołać okno dialogowe **Edytor tabel ciągów*** _. W oknie dialogowym _*_Edytor tabeli ciągów_*_ można zmodyfikować zasób ciągu w taki sposób, aby odpowiadał wymaganiom interfejsu użytkownika aplikacji. _*_Ilustracja 18_*_ przedstawia okno dialogowe modyfikacji po dwukrotnym kliknięciu _ *STRING_13**.

W takim przypadku nazwa identyfikatora ciągu jest pokazywana po lewej stronie, który jest wyświetlany w prawej części ciągu pierwszego lub referencyjnego języka. Oczywiście dokładna zawartość ciągu jest bardzo specyficzna dla aplikacji, ale układ w wersji zapoznawczej grupy ciągów jest spójny.

Program GUIX Studio obsługuje statyczny tekst i wielojęzykową aplikację, definiując i utrzymując tabelę ciągów. Tabela ciągów definiuje jeden identyfikator ciągu dla każdego rekordu, a jedna stała ciąg dla każdego rekordu dla każdego z obsługiwanych języków.

Języki, które mają być obsługiwane przez aplikację, są definiowane przy użyciu okna dialogowego konfiguracji języka, pokazanego tutaj:

![Zrzut ekranu przedstawiający okno dialogowe konfiguracji języka.](./media/guix-studio/config_languages.png)

**Rysunek 18**

Okno dialogowe konfiguracji języka jest wywoływane przy użyciu konfiguracji | Polecenie Języki w menu aplikacji. To okno dialogowe pozwala określić liczbę języków, które mają być obsługiwane przez aplikację, oraz nazwę lub identyfikator języka, który ma być skojarzony z każdym językiem. Obsługiwane języki można modyfikować po utworzeniu projektu, jednak w przypadku usunięcia języka należy pamiętać, że dane ciągu skojarzone z tym językiem również zostaną usunięte i nie można ich pobrać.

Pole wyboru "**staticly defined**" wskazuje, że wybrany język zostanie statycznie zdefiniowany w formacie kodu źródłowego w wygenerowanym pliku zasobów. Jeśli żaden język nie jest zdefiniowany statycznie, wskaźnik tabeli języka zostanie ustawiony na wartość NULL w generowanej tabeli wyświetlanej, a język musi być załadowany i zainstalowany przez aplikację przy użyciu interfejsów API modułu ładującego zasobów binarnych udostępnianych przez bibliotekę GUIX.

Pole wyboru "**Obsługuj tekst dwukierunkowy**" nakazuje programowi GUIX Studio włączenie obsługi renderowania tekstu dwukierunkowego. Należy włączyć to pole wyboru, jeśli ciągi, które będą wprowadzane dla tego języka, wymagają dwukierunkowego renderowania tekstu.

Pole wyboru "**Generuj tekst dwukierunkowy w kolejności wyświetlania**" nakazuje programowi GUIX Studio Generowanie tekstu dwukierunkowego do pliku wyjściowego w jego kolejności wyświetlania. Jeśli ta opcja jest zaznaczona, nie jest wymagane przetwarzanie w czasie wykonywania w bibliotece GUIX do prawidłowego renderowania tekstu dwukierunkowego. Gdy ta opcja jest zaznaczona, nie należy włączać obsługi tekstu dwukierunkowego w bibliotece GUIX. Ta konfiguracja zapewnia najlepszą wydajność środowiska uruchomieniowego, ale nie obsługuje renderowania dynamicznie zdefiniowanych dwukierunkowych ciągów tekstowych.

Pierwszy język lub język "index 1" jest określany jako "język referencyjny". Jest to język używany przez program GUIX Studio podczas definiowania i edytowania projektu interfejsu użytkownika. Wszystkie inne języki w tabeli ciągów są określane jako Języki tłumaczenia. Program GUIX Studio obsługuje eksportowanie i importowanie danych tabeli ciągów w standardowym formacie XLIFF lub CSV plików danych, wygodnie do wymiany informacji o ciągach z tłumaczami, którzy mogą pomóc deweloperowi aplikacji przy dodawaniu tłumaczeń dla języków, które mają być obsługiwane innym niż język referencyjny. Podczas eksportowania tabeli ciągów GUIX do pliku XLIFF lub CSV, język referencyjny oraz jeden język tłumaczenia są zawarte w pliku wymiany danych w formacie XLIFF lub CSV. Podobnie podczas importowania pliku XLIFF lub CSV zaimportowane dane są używane do wypełniania jednego języka tłumaczenia w tabeli ciągów GUIX.

![Zrzut ekranu edytora tabeli ciągów.](./media/guix-studio/image53.jpg)

**Rysunek 19.**

W oknie dialogowym Edytor tabeli ciągów najpierw jest wyświetlana lista identyfikatorów ciągów po lewej stronie, a następnie dane ciągu języka referencyjnego. Jeśli zdefiniowano więcej niż jeden język, trzecia kolumna zawiera jeden z obsługiwanych języków tłumaczenia. Możesz otworzyć i zamknąć trzecią kolumnę, klikając małą strzałkę w prawym górnym rogu kolumny języka referencyjnego.

Gdy kolumna Language Translation jest widoczna, można przechodzić przez Języki tłumaczenia zawarte w projekcie, klikając małe strzałki w prawym górnym rogu kolumny w języku tłumaczenia listy ciągów.

Można edytować rekord ciągu, klikając rekord w tabeli, aby go zaznaczyć. Po wybraniu rekordu, identyfikator ciągu rekordu i treść ciągu są wyświetlane w polach poniżej widoku tabeli. Możesz wpisać nowe wartości w tych polach, aby zmodyfikować identyfikator ciągu i zawartość ciągu.

Pole znajdujące się po prawej stronie widoku tabeli zawiera podgląd elementów widget, które odwołują się do wybranego ciągu. Jest to przydatne w przypadku przekroczenia określonego obszaru widżetu przez edytowany ciąg.

Pola po prawej stronie zawartości ciągu obejmują:

- "Liczba odwołań": to pole wskazuje, jak często określony identyfikator ciągu jest używany w projekcie GUIX Studio. Jeśli liczba odwołań wynosi 0, ten ciąg może być przestarzały i opcjonalnie może zostać usunięty przez użytkownika.
- Szerokość ciągu (w pikselach) wskazuje szerokość wyświetlania ciągu przy użyciu wskazanej czcionki.
- Pole "uwagi" to opcjonalne pole komentarz, które pozwala dodawać informacje o przeznaczeniu lub użyciu każdego ciągu. Te informacje są zawarte w wyeksportowanych plikach danych ciągów XLIFF w celu ułatwienia tłumaczeń w celu uzyskania dokładnych i zrozumiałych tłumaczeń ciągów.

W dowolnym momencie można otworzyć okno dialogowe ***edytora tabeli ciągów*** , klikając przycisk Dodaj ciąg w górnej części okna dialogowego. Przestarzałe lub nieużywane ciągi można usunąć z projektu, wybierając najpierw ciąg, a następnie klikając przycisk Usuń ciąg w górnej części okna dialogowego.

Oprócz ręcznego dodawania nowych ciągów do projektu za pomocą okna dialogowego edytora tabeli ciągów można również bezpośrednio dodawać nowe ciągi, wpisując tekst w polu "tekst" w widoku właściwości dowolnego widżetu, który obsługuje funkcję Text. Innymi słowy, gdy dodajesz nowe widżety w widoku docelowym lub wpisujesz informacje tekstowe w widoku właściwości, te akcje automatycznie tworzą nowe wpisy w tabeli ciągów projektu.

## <a name="adding-language-translations"></a>Dodawanie tłumaczenia języka

Edytor tabeli ciągów programu GUIX Studio obsługuje przepływ pracy definicji języka, który umożliwia deweloperom tworzenie aplikacji przy użyciu jej języka podstawowego, a następnie eksportowanie danych ciągu do standardowego pliku XML lub CSV schematu, który ma być wysyłany do eksperta tłumaczenia języka. Plik tłumaczenia jest następnie zwracany do dewelopera, który może zaimportować tłumaczenia języka z powrotem do projektu Studio, dodając obsługę nowego języka do swojej aplikacji.

Ta funkcja jest wywoływana za pomocą eksportu (w celu zapisania danych ciągu do pliku) i zaimportowania przycisków (do odczytu przetłumaczonych ciągów) w górnej części edytora tabeli ciągów. Przycisk Eksportuj służy do tworzenia pliku XML lub CSV schematu XLIFF, który zawiera ciągi języka referencyjnego. Ten plik może być używany przez translator przy użyciu narzędzi i edytorów, które obsługują standardowy format plików XLIFF lub CSV.

Gdy ekspert tłumaczy zwróci plik XLIFF do użytkownika z nowymi tłumaczeniami ciągów, można użyć przycisku Importuj, aby odczytać dane z tego pliku XLIFF lub CSV. Jeśli plik XLIFF lub CSV zawiera nowy język, nowy język zostanie dodany do projektu. Jeśli plik XLIFF zawiera nowe dane ciągu dla istniejącego języka, nowe dane zostaną zaimportowane do projektu. Ciągi języka referencyjnego nie są modyfikowane przez operację importu.

Kliknięcie przycisku Eksportuj powoduje wyświetlenie okna dialogowego z kontrolką eksportu w formacie XLIFF/CSV:

![Zrzut ekranu przedstawiający okno dialogowe kontroli eksportu programu XLIFF/CSV.](./media/guix-studio/image54.jpg)

**Rysunek 20**

Pola język źródłowy i język docelowy określają, które kolumny tabeli ciągów będą zapisywane w pliku XLIFF lub CSV jako język referencyjny i język tłumaczenia. Język źródłowy to ciągi odwołań, a język docelowy to język, dla którego tłumaczy dostarczy przetłumaczone dane ciągów.

Pole wersji XLIFF określa jedną z dwóch głównych wersji formatu plików XLIFF:, wersja 1,2 lub wersja 2,0 (i nowsze). Te standardy formatu plików XLIFF są niezgodne i należy wiedzieć, której wersji narzędzia używają przed użyciem poleceń eksportu/importu XLIFF. Więcej informacji na temat schematu XLIFF i standardów XLIFF można znaleźć tutaj:

- Wersja 1,2: [https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html](https://docs.oasis-open.org/xliff/xliff-core/xliff-core.html)
- Wersja 2,0: [https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0os.pdf](https://docs.oasis-open.org/xliff/xliff-core/v2.0/os/xliff-core-v2.0-os.pdf)

Pola Nazwa pliku wyjściowego i Ścieżka wyjściowa umożliwiają określenie nazwy pliku i lokalizacji, do których zostanie zapisany plik wyjściowy. Nazwa pliku jest całkowicie do użytkownika, ale sugerujemy użycie nazw wskazujących język źródłowy i docelowy zawarte w wyeksportowanym pliku.
