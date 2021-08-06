---
title: GUIX Studio Screen Designer
description: Projektowanie ekranów aplikacji jest głównym celem programu GUIX Studio.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 91377a663dfb605caa33ab019f437f2c3ed1adc7
ms.sourcegitcommit: 62cfdf02628530807f4d9c390d6ab623e2973fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2021
ms.locfileid: "115178310"
---
# <a name="chapter-5-guix-studio-screen-designer"></a>Rozdział 5: GUIX Studio Screen Designer

Projektowanie ekranów aplikacji jest głównym celem programu GUIX Studio. Projektowanie ekranu jest realizowane za pośrednictwem wszystkich różnych widoków opisanych wcześniej w rozdziale 3. Jednak głównym elementem projektu ekranu w programie GUIX Studio jest widok docelowy ***,*** w którym wszystkie elementy ekranu są wyświetlane wizualnie i w dokładnie taki sam sposób, w jaki będą wyświetlane na osadzonym ekranie docelowym. Te elementy ekranu można wybierać, przenosić, zmieniać rozmiar itp. za pomocą prostych operacji myszy i przycisków. Ponadto operacje wyrównania i przycisku porządek osi Z są dostępne dla wybranych obiektów. W poniższych sekcjach podrzędnych opisano różne funkcje projektowania ekranu w programie GUIX Studio. 

## <a name="creatingconfiguring-projects"></a>Tworzenie/konfigurowanie projektów

Tworzenie projektów w programie GUIX Studio jest proste — po **prostu** wybierz przycisk * Nowy Project _ lub wybierz menu _*_Project, Nowy Project_*_. Następnie w programie GUIX Studio zostanie wyświetlone okno dialogowe _ *_Project_** . W tym oknie dialogowym określono podstawowe ustawienia wyświetlania, a także informacje o ścieżce lokalizacji kodu wygenerowanego przez program GUIX Studio.

Po utworzeniu nowego projektu zostanie wyświetlone okno dialogowe konfigurowania projektu. W tym miejscu deweloper określa liczbę ekranów sprzętowych dostępnych dla obiektu docelowego oraz właściwości poszczególnych ekranów. Właściwości obejmują nazwę logiczną ekranu, rozdzielczość x/y, głębokość i format koloru oraz inne właściwości wyświetlania. Program GUIX Studio obsługuje wiele ekranów w tym samym projekcie. Jeśli wymagane są dodatkowe ekrany, należy zmienić * wartość pola **Liczba** ekranów _ w celu dopasowania do liczby ekranów na urządzeniu osadzonym. Maksymalna liczba ekranów w projekcie wynosi 4. _ *_Rysunek 21_** pokazuje okno dialogowe Project konfiguracji.

Modyfikowanie ustawień projektu i/lub wyświetlania jest realizowane za pomocą opcji menu ***Konfiguruj, Project/Display** _ lub wybierając projekt lub ekran, klikając prawym przyciskiem myszy i wybierając polecenie _*_Konfiguruj, Project/Wyświetl._*_ W obu przypadkach zostanie wyświetlone *_okno dialogowe_* _ Project * w celu ułatwienia zmian ustawień projektu i/lub wyświetlania.

![Zrzut ekranu przedstawiający okno dialogowe Project konfiguracji.](./media/guix-studio/config_project.png)

**Rysunek 21**

Grupa Katalogi umożliwia określenie domyślnych katalogów wyjściowych dla plików źródłowych i nagłówkowych języka C wytwarzanych przez program Studio. Te katalogi są zwykle zapisywane względem lokalizacji projektu, aby ułatwić przenoszenie projektów z jednego komputera na inny lub z jednego systemu plików na inny.

Pole Dodatkowe nagłówki umożliwia określenie niestandardowych plików nagłówków. Jeśli jest potrzebny więcej niż jeden plik nagłówkowy, użyj średników do rozdzielania listy.

Po wywołaniu poleceń "Generuj aplikację" lub "Generuj zasoby" w programie Studio są to domyślne katalogi, w których będą zapisywane te pliki źródłowe. Oczywiście możesz zastąpić te lokalizacje katalogów w dowolnym momencie, wprowadzając nowe lokalizacje w oknie dialogowym Katalog wyjściowy.

## <a name="selecting-widgets"></a>Wybieranie widżetów

Wybieranie widżetów odbywa się przez kliknięcie widżetu w drzewie widżetu ***Project View** _ lub kliknięcie widżetu widocznego w obszarze _*_Widok_*_ docelowy. Po wybraniu pojedynczego widżetu jego właściwości są wyświetlane w obszarze _*_Widok_*_ właściwości. _*_Rysunek 22 przedstawia_*_ wybrany widżet "_*_przycisk_**".

![Zrzut ekranu przedstawiający wybrany widżet.](./media/guix-studio/select_button.png)

**Rysunek 22**

## <a name="using-properties"></a>Używanie właściwości

Jak wspomniano wcześniej, właściwości wybranego widżetu są prezentowane w widoku ***właściwości** _. Wszystkie widżety mają wspólny zestaw właściwości, a także niektóre właściwości specyficzne dla określonego typu widżetu. Na przykład widżet przycisku ma właściwość _ *_Pushed_**, a widżet okna nie. Poniżej przedstawiono wspólny zestaw właściwości widżetu:

| Właściwość         | Znaczenie                                                                               |
| ---------------- | ------------------------------------------------------------------------------------- |
| Typ widżetu    | Typ widżetu do odwołania                                                                               |
| Nazwa widżetu      | Nazwa widżetu, przekazana do funkcji create widżetu i używana do nazewnictwa zmiennych w wygenerowanych plikach źródłowych.               |
| Identyfikator widżetu        | Identyfikator widżetu. Ta wartość identyfikatora służy do generowania sygnałów z widżetów nadrzędnych na ich ekranach nadrzędnych.                            |
| Lewe             | Współrzędna widżetu z lewej strony                                                                                                 |
| Pierwsze              | Najwyższa współrzędna widżetu                                                                                                  |
| Width            | Szerokość widżetu w pikselach                                                                                                      |
| Height           | Wysokość widżetu w pikselach                                                                                                     |
| Obramowanie           | Typ obramowania widżetu                                                                                                          |
| Przezroczyste      | Należy sprawdzić, czy widżet jest częściowo przezroczysty                                                                       |
| Rysowanie wybrane    | Należy sprawdzić, czy widżet powinien początkowo być rysowany w wybranym stanie.                                            |
| Włącz           | Należy sprawdzić, czy widżet może zostać wybrany lub klikowany przez użytkownika końcowego.                                                    |
| Akceptuje fokus    | Należy sprawdzić, czy widżet akceptuje fokus.                                                                                 |
| Przydzielanie środowiska uruchomieniowego | Należy sprawdzić, czy blok sterowania widżetu powinien być przydzielany dynamicznie.                                                 |
| Wypełnienie normalne      | Identyfikator zasobu koloru wypełnienia normalnego                                                                                                  |
| Wybrane wypełnienie    | Wybrany identyfikator zasobu koloru wypełnienia                                                                                                |
| Draw, funkcja    | Zdefiniowana przez użytkownika niestandardowa funkcja rysowania Name. Jeśli to pole jest puste, zostanie użyta standardowa funkcja rysowania dla tego typu widżetu. |
| Event, funkcja   | Zdefiniowana przez użytkownika niestandardowa nazwa funkcji obsługi zdarzeń. Jeśli ta wartość jest pusta, używana jest standardowa obsługa zdarzeń dla tego typu widżetu.          |

***Rysunek 23*** przedstawia właściwości prostego widżetu okna.

![Zrzut ekranu przedstawiający właściwości prostego widżetu okna.](./media/guix-studio/image57.jpg)

**Rysunek 23**

Wiele typów widżetów ma dodatkowe właściwości specyficzne dla każdego typu widżetu.

Na przykład na rysunku 23 powyżej typ widżetu Okno obsługuje identyfikator mapy pikseli tapety oraz ustawienie stylu wskazujące, czy tapeta ma być wyśrodkowana, czy kafelkowana.

Widżety tekstu obsługują pole identyfikatora ciągu, a także style wyrównania tekstu i specyfikację czcionki. Dodatkowe właściwości widżetu są zwykle bardzo intuicyjne po przeczytaniu opisu każdego typu widżetu oraz dostępnych stylów i parametrów funkcji Utwórz dla tego typu widżetu.

## <a name="manipulating-widgets"></a>Manipulowanie widżetami

Aby manipulować widżetem, najpierw należy wybrać element . W tym celu należy kliknąć widżet bezpośrednio w widoku ***Widok** docelowy _ lub wybrać go w drzewie widżetu _ *_Project View_**. Po wybraniu widżet będzie miał konspekt przerywany. W tym stanie można go przenieść, klikając widżet i przeciągając go do żądanej lokalizacji na jego elementach nadrzędnych. Jeśli widżet jest widżetem najwyższego poziomu, przeciągnięcie widżetu efektywnie ustawia jego początkową pozycję na ekranie docelowym. Oczywiście zawsze można przenieść lub zmienić rozmiar dowolnego widżetu w dowolnym momencie przy użyciu interfejsu API GUIX.

Aby zmienić rozmiar wysokości widżetu, umieść wskaźnik myszy na górnej krawędzi widżetu i poczekaj, aż wskaźnik myszy zmieni się na strzałkę w górę w dół. W tym momencie wysokość widżetu można zmienić, po prostu przesuwając mysz, gdy prawy przycisk myszy jest zaciśony. Rozmiar szerokości myszy można zmienić w podobny sposób, pozycjonowanie wskaźnika myszy na lewej krawędzi widżetu. ***Rysunek 24** _ przedstawiawidżet "_* przycisk **", który został zmieniony i przeniesiony do lewego/górnego obszaru okna nadrzędnego.

![Zrzut ekranu przedstawiający widżet przycisku.](./media/guix-studio/resize_button.png)

**Rysunek 24**

## <a name="manipulating-multiple-widgets"></a>Manipulowanie wieloma widżetami

Wybranie wielu widżetów jest realizowane przez kliknięcie wielu widżetów w widoku docelowym przy przytrzymaniu ***klawisza Ctrl*** w dół. Spowoduje to pokazanie każdego z wybranych widżetów z konturem kreskowany wokół niego. Należy pamiętać, że w przypadku wybrania wielu widżetów każdy widżet w grupie wyboru musi być elementem podrzędnym tego samego elementu nadrzędnego.

Po wybraniu wielu widżetów można je jednocześnie przenosić, klikając jeden na wybranych widżetach i przesuwając myszą prawym przyciskiem myszy wypchniętą w dół. Ponadto przyciski wyrównania na pasku narzędzi ***Tool Bar** _ mogą służyć do wyrównywania grupy wybranych widżetów. _*_Rysunek 25_*_ przedstawia wybrane widżety _*_"_*_ przycisk " i _*_"_*_ nowy przycisk ", a na rysunku _*_26_*_ — wynik wyboru przycisku *___* Wyrównaj do lewej * podczas wyboru tych widżetów.

![Zrzut ekranu przedstawiający wybrany przycisk i nowe widżety przycisków](./media/guix-studio/multiple_select.png)

**Rysunek 25**

![Zrzut ekranu przedstawiający wynik wyboru Align-Left przycisku.](./media/guix-studio/align_left.png)

**Rysunek 26**

## <a name="cutcopypaste-operations"></a>Operacje wycinania/kopiowania/wklejania

Wybrany widżet w widoku ***Widok docelowy** _ może być wycinany, kopiowany i wklejony w standardowy sposób. Widżety i ekrany można kopiować w ramach jednego projektu lub kopiować z jednego projektu i wklejać do innego. Pasek _*_narzędzi ma_*_ przyciski do wycinania, kopiowania i wklejania. W menu Edycja są również dostępne te same opcje. Pamiętaj, że podczas wklejania widżetu należy wybrać widżet nadrzędny przed wklejonym nowym widżetem. _*_Rysunek 27_*_ przedstawia wynik wyboruwidżetu "_* przycisku **", skopiowania go i wklejania kopii w tym samym oknie.

![Zrzut ekranu przedstawiający operacje wycinania/kopiowania/wklejania.](./media/guix-studio/copy_paste_button.png)

**Rysunek 27**

Kopiowanie/wklejanie w ramach jednego projektu jest zwykle proste, ponieważ zasoby, które mogą być wymagane przez skopiowane widżety, są zawsze obecne podczas pracy w jednym projekcie. Jeśli jednak skopiujemy widżet z projektu A i wkleimy go do projektu B, mogą wystąpić problemy z zależnościami zasobów.

Podczas kopiowania widżetów w programie Studio aplikacja Studio tworzy listę zasobów wymaganych przez skopiowane widżety i generuje tabelę zależności zasobów przenośnych w postaci kodu XML, która jest kopiowana do schowka systemu Windows, wraz z rzeczywistymi informacjami o skopiowanym widżecie. Po wklejeniu widżetów do innego projektu program Studio najpierw sprawdza listę zależności zasobów i dodaje wymagane zasoby do otwartego projektu, jeśli jeszcze nie istnieją. Program Studio identyfikuje pasujące zasoby według nazw identyfikatorów zasobów, a w przypadku zasobów ciągów program Studio porównuje również zawartość ciągu. Jeśli pasujące zasoby zostaną znalezione, program Studio aktualizuje identyfikatory zasobów wklejonych widżetów, aby prawidłowo używać zasobów w nowym projekcie. Jeśli zasoby nie zostaną znalezione, zostaną dodane.

Gdy program Studio dodaje zasób do projektu w ramach operacji wklejania widżetu, program Studio naprawdę dodaje link do zasobu w przypadku zasobów czcionek i pikselimapy. Ten link jest generowany z projektu źródłowego i otrzymasz komunikaty ostrzegawcze, jeśli nie można znaleźć tych zasobów względem lokalizacji projektu projektu, do którego jest wklejanie. Linki zasobów zostaną dodane do projektu niezależnie od tego, ale może być konieczne ręczne skopiowanie czcionek i plików obrazów do odpowiednich lokalizacji w nowym drzewie projektu, aby wyeliminować błędy ładowania zasobów. Program Studio nie kopiuje plików ttf, .png ani .jpg plików z jednej lokalizacji do innej.

Łatwym sposobem uniknięcia problemów w tym zakresie jest zachowanie spójnej struktury katalogów między projektami, które chcesz udostępnić. Jeśli chcesz łatwo przenieść elementy z usługi Project A do usługi Project B, zachowaj obrazy graficzne i czcionki używane przez oba projekty w spójnym podkatasie każdego folderu projektu.

## <a name="changing-z-order"></a>Zmiana kolejności Z

Widżety można łatwo przenosić przed innymi widżetami lub za nimi. W tym celu należy wybrać widżet i wybrać przyciski ***Przejdź** do przodu _ lub Przenieś do _*_tyłu_*_ na pasku _*_narzędzi_*_. _ *_Rysunek 28_** pokazuje przeniesienie drugiego przycisku do tyłu.

![Zrzut ekranu przedstawiający przycisk Z-order.](./media/guix-studio/change_z_order.png)

**Rysunek 28**

## <a name="assigning-colors-fonts-and-pixelmaps"></a>Przypisywanie kolorów, czcionek i map pikseli

Oprócz wybierania kolorów, czcionek i map pikseli w widoku właściwości dla wybranego widżetu obsługiwana jest również skrócona metoda przeciągania i upuszczania w celu przypisywania zasobów do widżetów. Aby użyć tej funkcji, po prostu kliknij lewym przyciskiem myszy zasób, taki jak kolor czcionki w widoku zasobów, i przeciągnij zasób na żądany widżet w widoku docelowym. Upuść zasób, zwalniając lewy przycisk myszy nad widżetem.

Zasoby kolorów są zawsze przypisywane do normalnego koloru tła widżetu podczas korzystania z metody przeciągania i upuszczania. Inne kolory, takie jak wybrany kolor lub wybrany kolor tekstu, muszą być przypisane przy użyciu widoku właściwości.

Podobnie zasoby mapy pikseli są przypisywane do pola mapy pikseli "normalny" lub "wypełnienie" widżetu obsługującego wyświetlanie mapy pikseli. Aby przypisać inne pola do widżetu obsługującego wiele map pikseli, należy użyć widoku właściwości.

## <a name="using-templates"></a>Korzystanie z szablonów

Dowolny ekran lub kolekcja widżetów podrzędnych, które projektujesz w programie Studio, może służyć jako szablon dla nowych ekranów i nowych kontrolek podrzędnych. Szablon można utworzyć na podstawie widżetu Typu okna, czyli normalnego przypadku użycia, lub dowolnego innego typu widżetu. Użycie szablonu jest podobne do kopiowania i wklejania widżetu, z tą różnicą, że wszystkie elementy pochodzące z szablonu są automatycznie modyfikowane, gdy szablon, na którym się opiera, jest modyfikowany. Nie można modyfikować właściwości widżetu szablonu podczas pracy z ekranem pochodnym lub dziedziczonym wystąpieniem szablonu. Jednak podczas modyfikowania właściwości szablonu w jakikolwiek sposób wszystkie wystąpienia odwołujące się do tego szablonu są automatycznie aktualizowane, ponieważ pochodzą z tego szablonu.

Kolejną zaletą używania szablonów dla powtarzanych elementów jest to, że plik specyfikacji wygenerowany przez program Studio będzie zazwyczaj mieć mniejszy rozmiar niż w przypadku ponownego tworzenia powtarzających się elementów za każdym razem, gdy są używane.

Aby wyznaczyć, że ekran lub kolekcja widżetów podrzędnych ma być używana jako szablon, należy włączyć pole wyboru "Szablon" w widoku właściwości widżetu. Po włączeniu pola wyboru "Szablon" widżet szablonu zostanie wyświetlony w oknie ***Wstaw| Menu*** rozwijane szablonów.

Na przykład przy użyciu szablonu można zdefiniować okno, które będzie używane jako pasek przycisku. To okno może zawierać kilka przycisków podrzędnych, a ten pasek przycisku jest często używany na różnych ekranach. W projekcie programu Studio możesz zdefiniować małe okno autonomiczne, które zawiera wymagane przyciski podrzędne, i nadać temu oknie nazwę "button_bar". Następnie wybierz to okno i włącz właściwość "Szablon". Następnie wybierz ekran, na którym chcesz dodać ten pasek przycisku. Użyj przycisku Wstaw| Szablon|button_bar polecenia menu, aby wstawić wystąpienie button_bar okna na ekranie. Pamiętaj, że możesz zmienić położenie paska przycisku, ale nie możesz zmieniać większości właściwości. Możesz jednak używać widżetu button_bar (i wszystkich elementów children) tak samo jak innych wstępnie zdefiniowanych typów widżetów GUIX. Aby zmodyfikować button_bar, należy wybrać szablon button_bar, aby wprowadzić zmiany.

Innym przykładem typowego użycia szablonu jest aplikacja, która zawiera wiele podobnych ekranów. Na przykład aplikacja może mieć 10 różnych ekranów, które mają wspólny pasek tytułu, kolor wypełnienia, rozmiar itp. W takim przypadku można zdefiniować ekran szablonu, który zawiera widżety podrzędne paska tytułu i konfiguruje rozmiar ekranu, kolor wypełnienia i inne właściwości. Po zdefiniowanym ekranie szablonu możesz utworzyć 10 różnych ekranów na podstawie tego szablonu. W przypadku korzystania z funkcji Wstaw| Szablon| \<base_screen> menu , ekran zacznie się od wszystkich widżetów i ustawień podrzędnego ekranu szablonu. Należy pamiętać, że każdy ekran pochodzący z ekranu szablonu nie jest kopią szablonu, ale naprawdę jest pochodnym wystąpieniem ekranu szablonu. Następnie można dostosować każdy ekran pochodny tak, aby pomieścić wymaganą dodatkową zawartość.

Należy pamiętać, że oprócz zapisywania rozmiaru wygenerowanego pliku specyfikacji użycie szablonów może ułatwić zarządzanie zmianami w wyglądzie aplikacji. W powyższym przykładzie załóżmy, że musisz zmienić kolor tła 10 podobnych ekranów. Zamiast wybierać poszczególne ekrany i zmieniać ustawienia koloru wypełnienia, wystarczy wybrać szablon podstawowy i zmienić jego kolor wypełnienia, a ta zmiana zostanie natychmiast odzwierciedlona na wszystkich ekranach pochodnych.

Kolejny komentarz dotyczący szablonów: należy zadbać o utrzymanie przepływu przetwarzania zdarzeń, co oznacza, że jeśli udostępnisz program obsługi zdarzeń zarówno dla ekranu podstawowego (do obsługi typowych zdarzeń widżetu), jak i dla ekranu pochodnego, program obsługi zdarzeń pochodnego ekranu powinien w domyślnym przypadku wywołać program obsługi zdarzeń programu base_screen. Umożliwi to programowi obsługi zdarzeń ekranu podstawowego przetwarzanie zdarzeń generowanych przez widżety wspólne dla wszystkich ekranów pochodzących z tej bazy szablonów.

## <a name="record-and-playback-macro"></a>Makro rekordu i odtwarzania

Funkcje rekordu i odtwarzania makra ułatwiają rejestrowanie i odtwarzanie naciśnięć klawiszy i zdarzeń myszy.

Rejestrowanie w pliku makra jest realizowane przez wybranie przycisku ***** Rejestruj makro _ na pasku narzędzi lub menu, wybierając pozycję _*_Edytuj, Zapisz makro._*_ W programie GUIX Studio zostanie wyświetlone _*_okno dialogowe Makro_*_ rekordu, w którym można określić nazwę ścieżki pliku makra. Po dokonaniu tego wyboru kliknij przycisk _*_Nagraj,_*_ aby rozpocząć nagrywanie. Po zakończeniu rejestrowania ponownie _**_ wybierz przycisk na pasku narzędzi Makra rekordu lub użyj menu rozwijanego, wybierając pozycję *__Edytuj,_* Zakończ makro *, aby zakończyć nagrywanie makra.

Odtwarzanie pliku makra jest realizowane przez wybranie przycisku ***** Odtwarzanie makra _ paska narzędzi przy użyciu głównego menu rozwijanego, aby wybrać polecenie _*_Edytuj, Odtwarzaj makro._*_ W programie GUIX Studio jest wyświetlane okno dialogowe _ *_Makro_* odtwarzania *, które umożliwia określenie wcześniej zarejestrowanego pliku makra do uruchomienia.

Podczas rejestrowania makr, które wybierają pliki wejściowe lub wyjściowe, takie jak dodanie czcionki lub obrazu, ważne jest, aby użyć klawiatury do wpisania nazwy pliku, zamiast wybierać z przeglądarki plików za pomocą myszy. Ponieważ rejestrator makr rejestruje zdarzenia myszy i klawiatury, a przeglądarka plików może zmieniać się z czasem, bardziej niezawodne jest wpisywanie nazwy pliku niż graficzne wybieranie pliku.

## <a name="zooming-target-view"></a>Powiększanie widoku docelowego

Funkcja Zoom In pomaga w zbliżeniu ekranu docelowego.

Możesz wybrać ustawienie powiększenia procentowego, które ma być dostępne w ***Konfiguracji| Widok docelowy| Opcja** menu Zoom _ . Pasek *_narzędzi_* _ * zawiera również przyciski powiększania/pomniejszanie.

## <a name="gridsnap-settings"></a>Siatka/przyciąganie Ustawienia

***Siatka i przyciąganie Ustawienia** _ zawierają niektóre ustawienia i opcje siatki i przyciągania. _*_Rysunek 29_*_ przedstawia okno _*_dialogowe Siatka i ustawienie przyciągania,_*_ gdy menu _ *_Sprzęgamie| Widok docelowy| Wybrana jest opcja Siatka/Przyciągaj_**.

![Zrzut ekranu przedstawiający ekran siatki i Ustawienia.](./media/guix-studio/image63.jpg)

**Rysunek 29**

Włącz opcję ***Pokaż siatkę** _ spowoduje wyświetlenie siatki na ekranie docelowym. Możesz określić przyrost siatki (w pikselach) w polu _*_Odstępy siatki._*_ Opcja *__Przyciągaj_* do siatki * pomaga uzyskać odpowiednie położenie widżetu. Włączenie tej opcji spowoduje aktywne przyciąganie.

Gdy ***opcja Siatki i przyciągania*** jest włączona:

- Jeśli przeciągniesz obiekt za pomocą myszy w widoku docelowym, obiekt będzie przesuwany o przyrost siatki.
- Przeciągnięcie krawędzi obiektu w celu zmiany rozmiaru będzie przyciągane do pozycji siatki.
- Jeśli wybierzesz obiekt i użyjesz klawiszy w górę/w lewo/w dół/w prawo, wybrany widżet będzie przesuwany według przyrostu przyciągania, będzie można określić przyrost przyciągania (w pikselach) w polu Odstępy w ***przyciąganiu.***
