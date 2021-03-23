---
title: Projektant ekranu programu GUIX Studio
description: Projektowanie ekranów aplikacji jest głównym celem programu GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 318e68ab5ab7d841057d65565dfda263597d03e4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822236"
---
# <a name="chapter-5-guix-studio-screen-designer"></a>Rozdział 5: Projektant ekranu programu GUIX Studio

Projektowanie ekranów aplikacji jest głównym celem programu GUIX Studio. Projekt ekranu jest realizowany przez wszystkie różne widoki opisane wcześniej w rozdziale 3. Jednak głównym elementem projektu ekranu w programie GUIX Studio jest ***Widok docelowy***, w którym wszystkie elementy ekranu są wyświetlane wizualnie i w taki sam sposób, jak w przypadku wyświetlania osadzonego elementu docelowego. Te elementy ekranu można zaznaczać, przenosić, zmieniać rozmiar itp. za pomocą prostych operacji myszy i przycisków. Ponadto w wybranych obiektach są dostępne operacje wyrównania i kolejności przycisków. Poniższe podsekcje opisują różne funkcje projektu ekranu programu GUIX Studio. 

## <a name="creatingconfiguring-projects"></a>Tworzenie/Konfigurowanie projektów

Tworzenie projektów w programie GUIX Studio jest proste — wystarczy wybrać przycisk ***Nowy projekt** _ lub menu wyboru _*_projektu, nowy projekt_*_. Następnie GUIX Studio Wyświetla okno dialogowe _ *_Configure Project_**. Z tego okna dialogowego są wyświetlane podstawowe ustawienia wyświetlania, a także informacje o ścieżce lokalizacji, w których określono kod generowany przez program GUIX Studio.

Po utworzeniu nowego projektu zostanie wyświetlone okno dialogowe Konfigurowanie projektu. Jest to miejsce, w którym deweloper określa liczbę wyświetlanych sprzętu w miejscu docelowym i właściwości, które są wyświetlane. Właściwości obejmują nazwę logiczną wyświetlania, rozdzielczość x/y, głębię i format kolorów oraz inne właściwości wyświetlania. Program GUIX Studio obsługuje wiele ekranów w tym samym projekcie. Jeśli są wymagane dodatkowe ekrany, należy zmienić ***liczbę wyświetlanych** _ pola, aby dopasować liczbę wyświetlanych na urządzeniu osadzonym. Maksymalna liczba wyświetleń w projekcie wynosi 4. _ *_Rysunek 21_** wyświetla okno dialogowe Konfigurowanie projektu.

Modyfikowanie ustawień projektu i/lub wyświetlania odbywa się za pomocą opcji menu ***Konfiguruj, projekt/Display** _ lub wybierając projekt lub ekran, klikając prawym przyciskiem myszy i wybierając pozycję _*_Konfiguruj, projekt/Display_*_. W obu przypadkach wyświetlane jest okno dialogowe _ *_Configure Project_**, które ułatwia wprowadzanie zmian w ustawieniach projektu i/lub wyświetlaczach.

![Zrzut ekranu przedstawiający okno dialogowe Konfigurowanie projektu.](./media/guix-studio/config_project.png)

**Rysunek 21**

Grupa katalogi służy do określania domyślnych katalogów wyjściowych dla plików źródłowych i nagłówków języka C utworzonych przez program Studio. Te katalogi są zwykle zapisywane względem lokalizacji projektu, dzięki czemu można łatwo przenosić projekty z jednego komputera do drugiego lub z jednego systemu plików do drugiego.

Pole dodatkowe nagłówki umożliwia określenie niestandardowych plików nagłówkowych. Jeśli jest wymagany więcej niż jeden plik nagłówkowy, użyj średników, aby rozdzielić listę.

Po wywołaniu poleceń Studio "Generuj aplikację" lub "Generuj zasoby" są to domyślne katalogi, w których będą zapisywane te pliki źródłowe. Oczywiście można zastąpić te lokalizacje katalogów w dowolnym momencie, wprowadzając nowe lokalizacje w oknie dialogowym katalog wyjściowy.

## <a name="selecting-widgets"></a>Wybieranie elementów widget

Wybór widżetów odbywa się przez kliknięcie widżetu w drzewie ***Widok projektu** _ widget lub kliknięcie widżetu widocznego w _*_docelowym obszarze widoku_*_ . Po wybraniu pojedynczego elementu widget jego właściwości są wyświetlane w obszarze _*_widoku właściwości_*_ . Na _*_rysunku 22_*_ przedstawiono element widget "_ *_przycisk_* *" wybrany.

![Zrzut ekranu wybranego widżetu.](./media/guix-studio/select_button.png)

**Rysunek 22**

## <a name="using-properties"></a>Używanie właściwości

Jak wspomniano wcześniej, właściwości wybranego widżetu są prezentowane w widoku ***Właściwości** _. Wszystkie widżety mają wspólny zestaw właściwości, a także niektóre właściwości, które są specyficzne dla określonego typu widżetu. Na przykład widżet przycisku ma właściwość _ *_pushd_**, gdy widżet okna nie. Poniżej przedstawiono wspólny zestaw właściwości widżetu:

| Właściwość         | Znaczenie                                                                               |
| ---------------- | ------------------------------------------------------------------------------------- |
| Typ widgetu    | Typ widżetu, dla odwołania                                                                               |
| Nazwa widżetu      | Nazwa widżetu, przeniesiona do funkcji widget Create i używana do nazewnictwa zmiennych w wygenerowanych plikach źródłowych.               |
| Identyfikator elementu widget        | Identyfikator elementu widget. Ta wartość identyfikatora jest używana do generowania sygnałów z elementów widget podrzędnych do ich ekranów nadrzędnych.                            |
| Lewe             | Największa z lewej strony widżetu                                                                                                 |
| Pierwsze              | Górna część elementu widget                                                                                                  |
| Width            | Szerokość widżetu w pikselach                                                                                                      |
| Height           | Wysokość widżetu w pikselach                                                                                                     |
| Obramowanie           | Typ obramowania widżetu                                                                                                          |
| Przezroczyste      | Należy sprawdzić, czy element widget jest częściowo przezroczysty                                                                       |
| Rysuj wybrane    | Należy sprawdzić, czy element widget powinien początkowo być rysowany w wybranym stanie.                                            |
| Włącz           | Należy sprawdzić, czy element widget może zostać wybrany lub kliknięty przez użytkownika końcowego.                                                    |
| Akceptuje fokus    | Należy sprawdzić, czy element widget akceptuje fokus.                                                                                 |
| Przydział środowiska uruchomieniowego | Należy sprawdzić, czy blok kontrolki widget powinien być przydzielany dynamicznie.                                                 |
| Wypełnienie normalne      | Identyfikator zasobu koloru normalnego wypełnienia                                                                                                  |
| Wybrane wypełnienie    | Wybrany identyfikator zasobu koloru wypełnienia                                                                                                |
| Funkcja rysowania    | Nazwa niestandardowej funkcji rysowania zdefiniowanej przez użytkownika. Jeśli to pole jest puste, używana jest standardowa funkcja rysowania dla tego typu widżetu. |
| Funkcja zdarzenia   | Nazwa funkcji niestandardowego obsługi zdarzeń zdefiniowanej przez użytkownika. Jeśli pole pozostanie puste, zostanie użyta Standardowa obsługa zdarzeń dla tego typu widżetu.          |

***Rysunek 23*** pokazuje właściwości prostego widżetu okna.

![Zrzut ekranu przedstawiający właściwości prostego widżetu okna.](./media/guix-studio/image57.jpg)

**Rysunek 23**

Wiele typów widżetów ma dodatkowe właściwości specyficzne dla każdego typu widżetu.

Na przykład, na rysunku 23 powyżej, typ widżetu okna obsługuje tapetę identyfikatora Pixelmap oraz ustawienie stylu wskazujące, czy tapeta powinna być wyśrodkowana lub rozdzielna.

Widżety tekstowe obsługują pole identyfikatora ciągu, a także style wyrównania tekstu i Specyfikacja czcionki. Dodatkowe właściwości widżetu są zwykle bardzo intuicyjne po przeczytaniu opisu każdego typu widżetu i dostępnych stylów oraz tworzeniu parametrów funkcji dla tego typu widżetu.

## <a name="manipulating-widgets"></a>Manipulowanie widżetami

Aby manipulować widżetem, najpierw należy wybrać opcję. W tym celu należy kliknąć pozycję bezpośrednio na widżecie w **widoku * obiekt docelowy** _ lub przez wybranie go w drzewie _ *_widoku projektu_**. Po wybraniu element widget będzie miał kreskowany kontur. W tym stanie można przenieść przez kliknięcie widżetu i przeciągnięcie go do odpowiedniej lokalizacji w jego obiekcie nadrzędnym. Jeśli widżet jest widżetem najwyższego poziomu, przeciąganie widżetu efektywnie ustawia początkową pozycję widżetu na ekranie docelowym. Oczywiście można w dowolnym momencie przenieść lub zmienić rozmiar dowolnego widżetu przy użyciu interfejsu API GUIX.

Aby zmienić wysokość elementu widget, umieść wskaźnik myszy na górnej krawędzi widżetu i poczekaj, aż wskaźnik myszy zmieni się na strzałkę w dół. W tym momencie wysokość widżetu można zmienić, naciskając myszą po naciśnięciu prawego przycisku myszy. Szerokość myszy można zmienić w podobny sposób, umieszczając wskaźnik myszy na lewej krawędzi widżetu. ***Rysunek 24** _ pokazuje, że w lewym/górnym rogu okna nadrzędnego Zmieniono rozmiar i przeniesiono widżet "_ *_przycisk_* *".

![Zrzut ekranu widżetu przycisku.](./media/guix-studio/resize_button.png)

**Rysunek 24**

## <a name="manipulating-multiple-widgets"></a>Manipulowanie wieloma widżetami

Wybranie wielu elementów widget jest realizowane przez kliknięcie wielu widżetów w widoku docelowym, trzymając wciśnięty klawisz ***Ctrl*** . Spowoduje to wyświetlenie wszystkich elementów widget wybranych z kreskowanym obramowaniem. Należy pamiętać, że podczas wybierania wielu elementów widget każdy widżet w grupie wyboru musi być elementem podrzędnym tego samego elementu nadrzędnego.

Po wybraniu wielu elementów widget, mogą one być jednocześnie przenoszone przez kliknięcie wewnątrz jednego na zaznaczonych widżetów i przeniesienie myszą po naciśnięciu prawego przycisku myszy. Dodatkowo przyciski wyrównania na **pasku narzędzi*** _ mogą być używane do wyrównywania grupy wybranych elementów widget. _*_Ilustracja 25_*_ pokazuje, że wybrane elementy widget "_*_Button_*_" i "_*_New Button_*_" i _*_rysunek 26_*_ przedstawiają wynik zaznaczenia przycisku _ *_Wyrównaj do lewej_** podczas zaznaczania tych elementów widget.

![Zrzut ekranu przedstawiający przycisk i nowe widżety przycisku](./media/guix-studio/multiple_select.png)

**Rysunek 25**

![Zrzut ekranu przedstawiający wynik zaznaczenia przycisku Align-Left.](./media/guix-studio/align_left.png)

**Rysunek 26**

## <a name="cutcopypaste-operations"></a>Operacje wycinania/kopiowania/wklejania

Wybrany widżet w **docelowym widoku*** _ może być wycięty, skopiowany i wklejony w standardowy sposób. Widżety i ekrany mogą być kopiowane w ramach jednego projektu lub kopiowane z jednego projektu i wklejane do innego. _*_Pasek narzędzi_*_ ma przyciski do wycinania, kopiowania i wklejania. Dostępne są również te same opcje w menu Edycja. Należy pamiętać, że podczas wklejania widżetu element widget powinien zostać wybrany przed wklejeniem nowego widżetu. _*_Ilustracja 27_*_ przedstawia wynik wyboru widżetu "__ * * *"_, skopiowanie go i wklejenie kopii w tym samym oknie.

![Zrzut ekranu operacji wycinania/kopiowania/wklejania.](./media/guix-studio/copy_paste_button.png)

**Rysunek 27**

Kopiowanie/wklejanie w obrębie jednego projektu jest ogólnie proste, ponieważ zasoby, które mogą być wymagane przez skopiowane widżety, są zawsze obecne podczas pracy w jednym projekcie. Jeśli jednak skopiujesz widżet z projektu A i wkleisz ten widżet do projektu B, mogą wystąpić pewne problemy związane z zależnościami zasobów.

Po skopiowaniu widżetów w programie Studio Aplikacja Studio tworzy listę zasobów wymaganych przez skopiowane widżety i generuje tabelę zależności zasobów przenośnych w postaci kodu XML, która jest kopiowana do Schowka systemu Windows wraz z rzeczywistymi informacjami o widżecie. Gdy wkleisz widżety do innego projektu, Studio najpierw analizuje listę zależności zasobów i dodaje potrzebne zasoby do otwartego projektu, jeśli jeszcze nie istnieją. Program Studio zidentyfikuje pasujące zasoby według nazw identyfikatorów zasobów, a dla programu String Resources Studio porównuje również zawartość ciągu. W przypadku znalezienia pasujących zasobów program Studio aktualizuje identyfikatory zasobów wklejonych widżetów, aby prawidłowo używać zasobów w nowym projekcie. Jeśli zasoby nie zostaną znalezione, zostaną dodane.

Gdy Studio dodaje zasób do projektu w ramach operacji wklejania widżetu, program Studio naprawdę dodaje link do zasobu w przypadku czcionek i Pixelmap zasobów. Ten link jest generowany na podstawie projektu źródłowego i pojawia się komunikat ostrzegawczy, jeśli nie można znaleźć tych zasobów względem lokalizacji projektu projektu, w którym są wklejane. Linki do zasobów zostaną dodane do projektu bez względu na to, ale może być konieczne ręczne skopiowanie czcionek i plików obrazów do odpowiednich lokalizacji w nowym drzewie projektu, aby wyeliminować błędy ładowania zasobów. Program Studio nie kopiuje plików TTF, png ani jpg z jednej lokalizacji do innej.

W łatwy sposób można uniknąć wszelkich problemów w tym zakresie, aby zachować spójną strukturę katalogów między projektami, które chcesz udostępnić. Jeśli chcesz łatwo przenieść elementy z projektu A do projektu B, Zachowaj obrazy graficzne i czcionki używane przez oba projekty w spójnym podkatalogu każdego folderu projektu.

## <a name="changing-z-order"></a>Zmiana kolejności Z

Widżety można łatwo przenieść przed innymi widżetami lub za nie. W tym celu należy zaznaczyć widżet i wybrać przyciski ***Przenieś do przodu** _ lub _*_Przenieś do tyłu_*_ na _*_pasku narzędzi_*_. _ *_Ilustracja 28_** pokazuje przeniesienie drugiego przycisku do tyłu.

![Zrzut ekranu przedstawiający przycisk z kolejnością z.](./media/guix-studio/change_z_order.png)

**Rysunek 28**

## <a name="assigning-colors-fonts-and-pixelmaps"></a>Przypisywanie kolorów, czcionek i Pixelmaps

Oprócz wyboru kolorów, czcionek i pixelmaps w widoku właściwości dla wybranego widżetu jest również obsługiwana skrócona Metoda przeciągania i upuszczania przypisywania zasobów do widżetów. Aby użyć tej funkcji, po lewej stronie kliknij zasób, taki jak kolor czcionki w widoku zasobów, a następnie przeciągnij zasób nad odpowiednim widżetem w widoku cel. Usuń zasób, zwalniając lewy przycisk myszy nad widżetem.

Zasoby koloru są zawsze przypisywane do normalnego koloru tła widżetu przy użyciu metody przeciągania i upuszczania. Inne kolory, takie jak wybrany kolor lub wybrany kolor tekstu, muszą być przypisane przy użyciu widoku właściwości.

Podobnie zasoby Pixelmap są przypisywane do pola "normal" lub "Fill" Pixelmap elementu widget, który obsługuje wyświetlanie Pixelmap. Aby przypisać inne pola do widżetu, który obsługuje wiele pixelmaps, należy użyć widoku właściwości.

## <a name="using-templates"></a>Korzystanie z szablonów

Dowolny ekran lub kolekcja elementów widget, które można zaprojektować w programie Studio, może być używana jako szablon dla nowych ekranów i nowych formantów podrzędnych. Użycie szablonu jest podobne do kopiowania i wklejania widżetu, z tą różnicą, że wszystkie elementy pochodne z szablonu są automatycznie modyfikowane, gdy szablon, na którym jest oparty, jest modyfikowany. Nie można modyfikować właściwości widżetu szablonu podczas pracy z ekranem pochodnym lub dziedziczonym wystąpieniem szablonu. Jednak po zmodyfikowaniu właściwości szablonu wszystkie wystąpienia odwołujące się do tego szablonu są automatycznie aktualizowane, ponieważ pochodzą z tego szablonu.

Inną zaletą korzystania z szablonów dla powtarzających się elementów jest to, że plik specyfikacji generowanych przez Studio zwykle będzie mniejszy niż w przypadku ponownego tworzenia powtarzających się elementów za każdym razem, gdy są one używane.

Aby wyznaczyć, że ekran lub kolekcja elementów widget elementu podrzędnego ma być używana jako szablon, należy włączyć pole wyboru "szablon" w widoku właściwości widżetu. Po włączeniu pola wyboru "szablon" widżet szablon zostanie wyświetlony w obszarze ***Wstaw |*** Menu ściągania szablonu.

Przykładem użycia szablonu może być zdefiniowanie okna, które jest używane jako pasek przycisku. To okno może zawierać kilka przycisków podrzędnych, a ten pasek przycisków jest często używany na różnych ekranach. Można zdefiniować małe autonomiczne okno w projekcie Studio, który zawiera wymagane przyciski podrzędne i nadać temu oknie nazwę "button_bar". Następnie zaznacz to okno i Włącz Właściwość "template". Następnie wybierz ekran, na którym chcesz dodać ten pasek przycisku. Użyj Wstaw | Szablon | button_bar polecenie menu, aby wstawić wystąpienie okna button_bar na ekranie. Należy zauważyć, że można zmienić położenie paska przycisku, ale nie można zmieniać większości właściwości. Można jednak użyć widżetu button_bar (i wszelkich elementów podrzędnych) tak samo jak w przypadku wszystkich innych wstępnie zdefiniowanych typów widżetów GUIX. Aby zmodyfikować button_bar, musisz wybrać szablon button_bar, aby wprowadzić zmiany.

Innym przykładem typowego użycia szablonu jest aplikacja, która zawiera wiele podobnych ekranów. Na przykład aplikacja może mieć 10 różnych ekranów, które współdzielą wspólny pasek tytułu, kolor wypełnienia, rozmiar itd. W takim przypadku można zdefiniować ekran szablonu, który zawiera widżety potomne paska tytułu i konfiguruje rozmiar ekranu, kolor wypełnienia i inne właściwości. Po zdefiniowaniu tego ekranu szablonu można następnie utworzyć 10 różnych ekranów z tego szablonu. Przy użyciu Wstaw | Szablon | \<base_screen> polecenie menu, ekran zostanie uruchomiony ze wszystkimi elementami widget i ustawieniami ekranu szablonu. Należy zauważyć, że każdy ekran pochodzący z ekranu szablonu nie jest kopią szablonu, ale jest naprawdę wystąpieniem pochodnym ekranu szablonu. Następnie można dostosować każdy ekran pochodny do przechowywania dowolnej dodatkowej zawartości.

Należy pamiętać, że oprócz zapisywania rozmiaru wygenerowanego pliku specyfikacji używanie szablonów może ułatwić zarządzanie zmianami w wyglądzie aplikacji. W powyższym przykładzie Załóżmy, że konieczna jest zmiana koloru tła 10 podobnych ekranów. Nie jest wymagane, aby zaznaczyć każdy ekran i zmienić ustawienia koloru wypełnienia, wystarczy wybrać podstawowy szablon i zmienić jego kolor wypełnienia, a ta zmiana zostanie natychmiast odzwierciedlona we wszystkich ekranach pochodnych.

Dodatkowy komentarz dotyczący szablonów: należy upewnić się, że przepływ przetwarzania zdarzeń jest obsługiwany, co oznacza, że jeśli podajesz program obsługi zdarzeń dla ekranu podstawowego (na potrzeby obsługi wspólnych zdarzeń widżetu) i dla ekranu pochodnego, program obsługi zdarzeń ekranu pochodnego powinien wywoływać base_screen obsługi zdarzeń w domyślnym przypadku. Pozwoli to programowi obsługi zdarzeń ekranu podstawowego na przetwarzanie zdarzeń generowanych przez widżety wspólne dla wszystkich ekranów pochodnych z tego szablonu.

## <a name="record-and-playback-macro"></a>Rejestruj i Odtwarzaj makro

Funkcja rejestrowania i zapisywania oraz odtwarzania i wyświetlania zdarzeń myszy ułatwia nagrywanie i odtwarzanie klawiszy.

Nagrywanie do pliku makr jest realizowane przez wybranie przycisku ***zarejestruj makro** _ paska narzędzi lub menu wybierz polecenie _*_Edytuj, rejestruj makro_*_. Program GUIX Studio wyświetli okno dialogowe _*_rejestrowania makr_*_ , które pozwala określić nazwę ścieżki pliku makra. Po wybraniu tej opcji kliknij przycisk _*_Rejestruj_*_ , aby rozpocząć nagrywanie. Po zakończeniu nagrywania należy ponownie wybrać przycisk paska narzędzi _*_rejestrowanie makra_*_ lub użyć menu rozwijanego z poleceniem *_Edytuj i Zakończ makro *,_* aby zakończyć nagrywanie makra.

Odtwarzanie pliku makra jest realizowane przez wybranie przycisku paska narzędzi ***odtwarzanie makra** _ przy użyciu głównego menu rozwijanego, aby wybrać polecenie _*_Edytuj, Odtwórz makro_*_ . GUIX Studio przedstawia okno dialogowe _ *_odtwarzania makro_**, które pozwala na określenie wcześniej zapisanego pliku makra do uruchomienia.

Podczas rejestrowania makr, które wybierają pliki wejściowe lub wyjściowe, takie jak dodanie czcionki lub obrazu, ważne jest, aby użyć klawiatury do wpisywania nazwy pliku, a nie przy użyciu myszy do wybrania z przeglądarki plików. Ponieważ Rejestrator makr rejestruje zdarzenia myszy i klawiatury, a ponieważ przeglądarka plików może ulec zmianie z upływem czasu, bardziej niezawodne jest wpisywanie nazwy pliku, niż w celu wybrania pliku graficznie.

## <a name="zooming-target-view"></a>Widok docelowy powiększenia

Powiększ funkcję pomaga uzyskać widok do końca ekranu docelowego.

Możesz wybrać ustawienie procentu powiększenia, które ma być używane w programie ***Configure | Widok docelowy |** Opcja menu Zoom _. _ *_Pasek narzędzi_** ma także przyciski do powiększania/wypełniania.

## <a name="gridsnap-settings"></a>Ustawienia siatki/przyciągania

Okno dialogowe ***Ustawienia siatki i przyciągania** _ zawiera kilka ustawień i opcji siatki i przyciągania. _*_Rysunek 29_*_ pokazuje okno dialogowe _*_Siatka i ustawienia przyciągania_*_ , gdy menu _ *_Congigure | Widok docelowy | Wybrano siatkę/Snap_**.

![Zrzut ekranu przedstawiający ustawienia siatki i przyciągania.](./media/guix-studio/image63.jpg)

**Rysunek 29**

Włącz opcję ***Pokaż siatkę**, aby wyświetlić siatkę na ekranie docelowym, możesz określić przyrost siatki (w pikselach) w polu _*_odstępy siatki_*_ . Opcja _ *_Przyciągaj do siatki_** ułatwia uzyskanie właściwego elementu widgetu. Ta opcja zostanie uaktywniona.

Gdy jest włączona opcja ***siatki i przyciągania*** :

- Jeśli przeciągniesz obiekt za pomocą myszy w widoku docelowym, obiekt zostałby przeniesiony przez przyrost siatki.
- Jeśli przeciągniesz krawędź obiektu do rozmiaru, krawędź, którą przeciągasz, zostanie przyciągnięta do pozycji siatki.
- W przypadku wybrania obiektu i użycia klawiszy w górę/w lewo/w dół/w prawo wybrany widżet zostałby przesunięty o przyrost przyciągania, można określić przyrostek (w pikselach) w polu ***odstępy przyciągania*** .
