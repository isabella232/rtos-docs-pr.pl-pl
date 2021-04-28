---
title: Opis Azure RTOS GUIX i Azure RTOS GUIX Studio
description: Azure RTOS GUIX to profesjonalny pakiet, który spełnia potrzeby deweloperów systemów osadzonych.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 8f4a1578fcabdabfb213ced9c6593f6cffc964aa
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171407"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a>Omówienie graficznego Azure RTOS GUIX i Azure RTOS GUIX Studio

Osadzony interfejs GUIX platformy Azure to zaawansowane rozwiązanie z graficznym interfejsem użytkownika klasy przemysłowej firmy Microsoft zaprojektowane specjalnie z myślą o aplikacjach z głębokiego osadzoną platformą, w czasie rzeczywistym i aplikacjach IoT. Firma Microsoft udostępnia również w pełni funkcjonalne narzędzie do projektowania aplikacji klasycznych WYSIWYG o nazwie Azure RTOS GUIX Studio, które umożliwia deweloperom projektowanie graficznego interfejsu użytkownika na pulpicie i generowanie osadzonego kodu graficznego graficznego interfejsu użytkownika AZURE RTOS GUIX, który można następnie wyeksportować do obiektu docelowego. Azure RTOS GUIX jest w pełni zintegrowany z systemem Azure RTOS ThreadX RTOS i jest dostępny dla wielu tych samych procesorów obsługiwanych przez Azure RTOS ThreadX. Wszystko to w połączeniu z bardzo małym zużyciem pamięci, szybkim wykonywaniem i doskonałą łatwością użycia sprawia, że interfejs GUIX Azure RTOS jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT wymagających interfejsu użytkownika. 

## <a name="azure-rtos-guix-api"></a>Azure RTOS GUIX API

### <a name="powerful-apis"></a>Zaawansowane interfejsy API

* Pełna obsługa bezpośredniego rysowania kanwy w razie potrzeby
* Prosta w interakcji Azure RTOS wygenerowanym kodem GUIX Studio
* Interfejsy API dla linii, prostokąta, wielokąta itp.
* Interfejsy API dla okręgu, łuku, koła, rąbka, wielokropka itp.
* Interfejsy API do rysowania i pozycjonowania tekstu
* Anty aliasy, wypełnienia tekstury i wypełnienia pełne
* Interfejsy API do tworzenia i modyfikacji ekranów i widżetów

### <a name="azure-rtos-guix-studio-generated-files"></a>Azure RTOS plików generowanych przez program GUIX Studio

* Automatycznie generowane pliki źródłowe ANSI C
* Odizoluje oprogramowanie aplikacji od szczegółów układu
* Zawiera czcionki i obrazy wymagane przez projekt interfejsu użytkownika
* Wygenerowane pliki skompilowane przy użyciu kodu aplikacji
* Układ ekranu można aktualizować bez wpływu na logikę aplikacji
* Identyfikatory zasobów tworzą niezależność języka i motywu
* Niestandardowe funkcje rysowania i przetwarzania zdarzeń dostarczane przez użytkownika

### <a name="widget-library"></a>Biblioteka widżetów

* Wstępnie zdefiniowany, ale dostosowywalny zestaw typowych elementów interfejsu
* Bardzo mała, kompaktowa i wydajna
* Biblioteka zawiera przycisk, miernik, listę, okno, przewijanie, suwak, pasek postępu, monit i wiele innych
* W pełni dostosowywalny wygląd i rysunek
* W pełni dostosowywalna obsługa operacji i zdarzeń
* Tylko używane widżety są połączone z oprogramowaniem aplikacji

### <a name="math-and-utilities"></a>Obliczenia matematyczne i narzędzia

* Funkcje dla sin, cos, arcsin, arccos, tangens, square root
* Funkcje do manipulowania regionami ekranu
* Konfiguracja i uruchamianie systemu
* Definicja puli pamięci (opcjonalnie)
* Zarządzanie czasomierzem
* Zarządzanie animacjami
* Konserwacja zanieczyszczonej listy

### <a name="image-processing"></a>Przetwarzanie obrazów

* Funkcje dekodowania środowiska uruchomieniowego obrazów JPEG i PNG
* Stosowanie ditheringu i konwersji przestrzeni kolorów
* Obracanie obrazów
* Skalowanie obrazów
* Łączenie obrazów

### <a name="event-processing"></a>Przetwarzanie zdarzeń

* Automatycznie wstrzymuje Azure RTOS GUIX, gdy jest w stanie bezczynności
* Model programowania sterowanego zdarzeniami popularny w projektowaniu interfejsu użytkownika
* Odszybnia sterowniki wejściowe Azure RTOS wątku rysowania GUIX
* Funkcje do wysyłania i odbierania zdarzeń
* Wstępnie zdefiniowane typy zdarzeń dla wszystkich typów Azure RTOS guix
* Obsługiwane zdarzenia niestandardowe zdefiniowane przez użytkownika

### <a name="canvas-processing"></a>Przetwarzanie kanwy

* Przycinanie i konserwacja w kolejności Z
* Odizoluje bibliotekę widżetów od szczegółów sprzętu
* Odizoluje aplikację od szczegółów sprzętu
* Automatyczne odświeżanie w tle obszarów zanieczyszczonych
* Obsługiwane jest wiele kanwy z warstwami i mieszaniem
* Może być wywoływana bezpośrednio przez oprogramowanie aplikacji

### <a name="input-device-drivers"></a>Wejściowe sterowników urządzeń

* Obsługa specyficzna dla sprzętu, Azure RTOS GRAFICZNEGO interfejsu użytkownika i aplikacji odizolowane od szczegółów sprzętu
* Obsługiwane są: odporność na dotyk, cap Touch i klawiatura
* Zdarzenia wejściowe przekazywane do Azure RTOS guix

### <a name="display-drivers"></a>Wyświetlanie sterowników

* Obsługa specyficzna dla sprzętu
* Sterowniki ogólne dostępne dla wszystkich formatów i głębokości kolorów
* Dostosowane do korzystania z dostępnych akceleratorów graficznych

### <a name="target-hardware"></a>Sprzęt docelowy

* Niemal każdy sprzęt z możliwością graficznego wyjścia jest zgodny z graficznym interfejsem użytkownika (GUIX)
* Obsługiwanych jest wiele ekranów fizycznych
* Minimalne wymagania dotyczące pamięci RAM i pamięci flash

## <a name="create-elegant-user-interfaces"></a>Tworzenie eleganckich interfejsów użytkownika

Azure RTOS GUIX i Azure RTOS GUIX Studio zapewniają wszystkie funkcje niezbędne do tworzenia wyjątkowo eleganckich interfejsów użytkownika. Standardowy pakiet Azure RTOS GUIX zawiera różne przykładowe interfejsy użytkownika, w tym dokumentację urządzeń medycznych, dokumentację inteligentnych zegarków, dokumentację automatyzacji domu, dokumentację kontrolek przemysłowych, informacje o przemyśle samochodowym oraz różne przykłady sprite i animacji. Kliknij przykłady referencyjne pokazane poniżej.

### <a name="home-automation"></a>Home Automation

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a>Medycznych

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a>Produkty konsumenckie

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a>Towary białe

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a>Motoryzacja

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a>Przemysłowe

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

Każdy Azure RTOS GUIX ma odpowiedni Azure RTOS GUIX Studio, który definiuje wszystkie elementy graficzne projektu referencyjnego. Zmiana projektu odwołania jest łatwa. Wystarczy otworzyć odpowiedni Azure RTOS GUIX, wprowadzić żądane zmiany, zapisać projekt, a następnie wybrać pozycję *Projekt*.

Wygeneruj wszystkie pliki wyjściowe, aby wygenerować kod C dla Azure RTOS GUIX. Następnie po prostu ponownie skompilować aplikację docelową i uruchomić ją, aby zaobserwować zmodyfikowany projekt odwołania.

### <a name="memory-footprint"></a>Zużycie pamięci

Azure RTOS GUIX ma znacząco niewielką ilość pamięci RAM 13,2 KB pamięci FLASH i 4 KB na potrzeby podstawowej obsługi, bez uwzględnienia pamięci wymaganej dla kanwy.

W przypadku ekranu z wewnętrzną technologią GRAM i własnym odświeżaniem nie jest wymagana żadna pamięć kanwy. Jednak w celu poprawienia wydajności rysowania lub w przypadku konfiguracji wyświetlania, która nie korzysta z lokalnego programu GRAM na ekranie, aplikacja definiuje obszar pamięci kanwy.

Wymagania dotyczące pamięci kanwy są funkcją rozmiaru kanwy oraz głębokości koloru i są definiowane przez formułę:

<i>Pamięć RAM kanwy (w bajtach) = (x * y * (bpp/8))</i>

Gdzie "x" i "y" to wymiary kanwy (ekranu).

Większość aplikacji korzysta również z zasobów graficznych, które nie są uwzględnione w podstawowych wymaganiach Azure RTOS magazynu biblioteki GUIX. Te zasoby obejmują czcionki, ikony graficzne (mapy pikseli) i ciągi statyczne. Te dane mogą być przechowywane w sekcji pamięci const (tj. flash).

Rozmiar tego obszaru pamięci zależy od wielu czynników, takich jak liczba i rozmiar użytych unikatowych czcionek, liczba i rozmiar używanych ikon graficznych, format koloru danych wyjściowych oraz to, czy każdy zasób używa skompresowanych danych, ponieważ interfejs GUIX programu Azure RTOS obsługuje kompresję RLE danych czcionek i map pikseli. Wymagania dotyczące magazynu dla każdego zasobu są wyświetlane w aplikacji Azure RTOS GUIX Studio, dzięki czemu użytkownik może śledzić i monitorować ilość pamięci flash, która będzie zużywana przez zasoby aplikacji.

Podobnie Azure RTOS ThreadX, rozmiar Azure RTOS GUIX jest automatycznie skalowany na podstawie usług faktycznie używanych przez aplikację. To praktycznie eliminuje potrzebę skomplikowanej konfiguracji i parametrów kompilacji, co ułatwia deweloperom pracę.

#### <a name="simple-easy-to-use"></a>Proste, łatwe w użyciu

Azure RTOS GUIX jest bardzo prosty w użyciu, a program Azure RTOS GUIX Studio jeszcze bardziej ułatwia deweloperom wizualne projektowanie na pulpicie i generowanie kodu C, który działa w rzeczywistym celu. Aplikacje mogą następnie dodawać własne niestandardowe funkcje obsługi zdarzeń i rysowania w celu ukończenia graficznego interfejsu użytkownika.

Korzystanie z interfejsu AZURE RTOS GUIX jest proste. Interfejs AZURE RTOS GUIX jest intuicyjny i wysoce funkcjonalny. Nazwy interfejsu API składa się z rzeczywistych słów, a nie "alfabetu" i/lub wysoce skróconych nazw, które są tak popularne w innych produktach systemu plików. Wszystkie Azure RTOS GUIX mają wiodącą gx_ *i* są zgodne z konwencją nazewnictwa rzeczowników. Ponadto w całym interfejsie API istnieje spójność funkcjonalna. Na przykład wszystkie interfejsy API, które inicjują blok kontrolki widżetu, mają nazwy widget_type _create, a parametry funkcji create dla każdego typu widżetu są zawsze zdefiniowane w &lt; &gt; tej samej kolejności.

### <a name="comprehensive-set-of-built-in-widgets"></a>Kompleksowy zestaw wbudowanych widżetów

* Azure RTOS GUIX udostępnia bogaty zestaw wbudowanych widżetów, w tym:
* Accordion Menu
* Przycisk
* Pole wyboru
* Okrągły miernik
* Lista rozwijana
* Lista pozioma
* Poziome okno paska przewijania
* Ikona
* Przycisk ikony
* Wykres liniowy
* Menu
* Przycisk tekstowy z wieloma wierszami
* Wprowadzanie tekstu w wielu wierszach
* Widok tekstu wielo wierszowego
* Monit o numeryczne mapowanie pikseli
* Monit liczbowy
* Numeryczne kółka przewijania
* Przycisk Pixelmap
* Monit o mapowanie pikseli
* Suwak mapy pikseli
* Sprite mapy pikseli
* pasek postępu
* Monit
* Pasek postępu promieniowego
* przycisk radiowy
* Kółko
* Wprowadzanie tekstu w jednym wierszu
* Suwak
* Kółka przewijania ciągów
* Przycisk tekstowy
* Widok drzewa
* Lista pionowa
* Pionowy pasek przewijania

Aplikacja może łatwo tworzyć własne widżety klienta.

### <a name="complete-low-level-drawing-api"></a>Kompletny interfejs API rysowania niskiego poziomu

Azure RTOS GUIX zapewnia niezawodny interfejs API rysowania kanwy, który umożliwia aplikacji renderowanie złożonych kształtów graficznych.

Wszystkie funkcje obsługują anty aliasy dla obiektów docelowych o dużej głębokości kolorów, a wszystkie kształty mogą być wypełniane naszym konturem, w tym wypełnieniem wzorca pełnej mapy i mapy pikseli. Wszystkie typy pierwotne rysowania obsługują pędzla alpha w przypadku uruchamiania z 16 bpp i większą głębokością koloru. Funkcje rysowania obejmują:

* Rysowanie arc
* Rysowanie okręgu
* Rysowanie liniowe
* Rysowanie kołowe
* Pixelmap Blend
* Kafelek mapa pikseli
* Rysowanie wielokąta
* Rysowanie tekstu
* Chord Draw
* Rysowanie wielokropka
* Rysowanie pikseli
* Rysowanie mapy pikseli
* Obracanie mapy pikseli
* Rysowanie prostokąta
* Text Blend

### <a name="default-free-fonts-and-easy-to-add-more"></a>Domyślne bezpłatne czcionki i łatwe dodawanie kolejnych czcionek

Azure RTOS GUIX udostępnia bezpłatny zestaw czcionek TrueType. Deweloperzy mogą dodawać dodatkowe czcionki TrueType zgodnie z potrzebami.

Format Azure RTOS GUIX obsługuje anty aliasy 8bpp, anty aliasing 4bpp i czcionki monochromatyczne 1bpp. W przypadku aplikacji z ograniczeniami zasobów Azure RTOS GUIX wstępnie renderuje czcionki TrueType do skompresowanego formatu mapy bitowej przy użyciu naszego narzędzia klasycznego GUIX Studio.

### <a name="custom-jpg-and-png-decoder-implementation"></a>Niestandardowa implementacja dekodera JPG i PNG

Implementacja niestandardowego dekodera JPG i PNG w implementacji dekodera plików JPG i PNG. Ta implementacja obsługuje konwersję przestrzeni kolorów, dithering i tworzenie środowiska uruchomieniowego Azure RTOS obrazów w formacie pikseli zgodnych z guix.

### <a name="extensive-display-and-touchscreen-support"></a>Rozbudowana obsługa ekranu i ekranu dotykowego

Azure RTOS GUIX udostępnia ogólne sterowniki wyświetlania dla niemal wszystkich formatów kolorów, w tym monochromatycznych 1bpp, palety 8 bpp, formatu 8 bpp 3:3:2,

16 bpp 565 rgb, format 16 bpp 4:4:4:4, 32 format bpp x:r:g:b i 32 bpp a:r:g:b. Ponadto Azure RTOS GUIX jest zintegrowany z wieloma najpopularniejszymi kontrolerami i akceleratorami sprzętowym (ST ChromeArt, Renesas Aby itp.).

Azure RTOS GUIX w pełni obsługuje ekran dotykowy (w tym obsługę gestów), piórem i wirtualnymi urządzeniami wejściowymi klawiatury.

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a>Azure RTOS GUIX Studio desktop WYSIWYG tool

Azure RTOS GUIX Studio udostępnia kompletne środowisko projektowe ekranu WYSIWYG, które umożliwia użytkownikowi przeciąganie i upuszczanie elementów graficznych używanych do tworzenia ekranów graficznego interfejsu użytkownika. Azure RTOS GUIX Studio automatycznie generuje kod C zgodny z biblioteką Azure RTOS GUIX, gotowy do skompilowania i uruchomienia na komputerze docelowym. Deweloperzy mogą tworzyć wstępnie wyrenderowane czcionki do użycia w aplikacji przy użyciu zintegrowanego Azure RTOS generowania czcionek w programie GUIX Studio. Czcionki mogą być generowane w formatach monochromatycznych lub anty aliasów i są zoptymalizowane pod kątem oszczędzania miejsca w miejscu docelowym. Czcionki mogą zawierać dowolny zestaw znaków, w tym znaki Unicode dla aplikacji wielojęzycznych.

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

Azure RTOS GUIX Studio ułatwia importowanie grafiki z plików PNG lub JPG z konwersją na skompresowane Azure RTOS GUIX Pixelmaps do użycia w systemie docelowym. Wiele typów widżetów AZURE RTOS GUIX zaprojektowano w celu uwzględnienia grafiki użytkownika w celu niestandardowego wyglądu i wyglądu. Ponadto program AZURE RTOS GUIX Studio umożliwia dostosowywanie domyślnych kolorów i stylów rysowania używanych przez widżety GUIX Azure RTOS, dzięki czemu deweloperzy mogą bardzo łatwo dostroić wygląd Azure RTOS GUIX. Generowanie i konserwacja ciągów aplikacji to kolejna wbudowana Azure RTOS GUIX Studio. Dzięki temu deweloperzy mogą projektować aplikację przy użyciu jednego języka do programowania oraz szybko i łatwo dodawać obsługę dodatkowych języków po zwolnieniu produktu. Kompletną aplikację AZURE RTOS GUIX można wykonać na komputerze stacjonarnym w środowisku programu Azure RTOS GUIX Studio, co umożliwia szybkie i łatwe generowanie i demonstrację koncepcji graficznego interfejsu użytkownika, testowanie przepływów ekranu oraz obserwowanie przejść ekranu i animacji. Po zakończeniu projekt można wyeksportować jako gotowe do użycia w celu struktury danych języka C gotowe do skompilowania i powiązać za pomocą interfejsu GUIX Azure RTOS i Azure RTOS ThreadX.

Azure RTOS GUIX i Azure RTOS GUIX Studio obsługują wiele motywów zasobów, dzięki czemu aplikację można łatwo rozetykieć w czasie uruchamiania. Czcionki, kolory i mapy pikseli można zmieniać w czasie rzeczywistym za pomocą jednego prostego interfejsu API.

Dowiedz się więcej o programie GUIX Studio

### <a name="complete-win32-simulation"></a>Ukończ symulację win32

Azure RTOS GUIX działa na komputerze z systemem Windows przy użyciu dokładnie tej samej biblioteki rysowania, która jest uruchamiana na tablicy docelowej. Za Azure RTOS GUIX można skompilować i uruchomić aplikację z graficznym interfejsem użytkownika na komputerze, a następnie użyć tego samego kodu aplikacji w celu debugowania, szybkiego tworzenia prototypów, pokazu i docelowej operacji WYSIWYG.

### <a name="advanced-technology"></a>Zaawansowana technologia

* Azure RTOS technologia GUIX obejmuje:
* Łączenie alfa
* Anty aliasy
* Automatyczne skalowanie
* Kompresja mapy bitowej
* Łączenie kanwy
* Obsługa widżetów niestandardowych
* Obsługa rysowania odroczonego
* Obsługa ditheringu
* Programowanie neutralne dla endian
* Obsługa akceleratora sprzętowego
* Obsługa wielu języków i kodowanie UTF-8
* Obsługa wielu ekranów i kanwy
* Zoptymalizowane przycinanie, rysowanie i obsługa zdarzeń
* Dekoder PLIKÓW JPEG i PNG środowiska uruchomieniowego
* Osłanianie i motywy
* Obsługuje monochromatyczne za pośrednictwem 32-bitowej wartości true-color w formatach alfagraficznych
* Obsługa przejść, sprite'ów i animacji
* Symulacja win32
* Zarządzanie oknami, w tym okienka widoków i konserwacja w kolejności Z
