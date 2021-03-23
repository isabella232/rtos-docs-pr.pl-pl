---
title: Informacje o platformie Azure RTO GUIX i platformie Azure RTO GUIX Studio
description: Usługa Azure RTO GUIX to pakiet z jakością profesjonalną, utworzony w celu spełnienia wymagań deweloperów systemów osadzonych.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0d0ff37784673f851ab918e20b255d19ddf98b0f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822998"
---
# <a name="overview-of-azure-rtos-guix-and-azure-rtos-guix-studio"></a>Omówienie usług Azure RTO GUIX i Azure RTO GUIX Studio

Interfejs GUI platformy Azure GUIX Embedded to zaawansowane rozwiązanie klasy korporacyjnej GUI firmy Microsoft zaprojektowane specjalnie pod kątem głęboko osadzonych, w czasie rzeczywistym i IoT. Firma Microsoft udostępnia również w pełni funkcjonalne narzędzie do projektowania w systemie WYSIWYG o nazwie Azure RTO GUIX Studio, które umożliwia deweloperom projektowanie graficznego interfejsu użytkownika na pulpicie i generowanie kodu graficznego interfejsu GUI platformy Azure RTO GUIX, który można następnie wyeksportować do obiektu docelowego. Usługa Azure RTO GUIX jest w pełni zintegrowana z platformą Azure RTO ThreadX RTO i jest dostępna dla wielu procesorów obsługiwanych przez platformę Azure RTO ThreadX. Wszystko to w połączeniu z bardzo małym zasięgiem, szybkim wykonaniem i najbardziej łatwym w użyciu, dzięki czemu usługa Azure RTO GUIX idealny wybór dla najbardziej wymagających aplikacji IoT, które wymagają interfejsu użytkownika. 

## <a name="azure-rtos-guix-api"></a>Interfejs API usługi Azure RTO GUIX

### <a name="intuitive-and-consistent-api"></a>Intuicyjny i spójny interfejs API

* W konwencji nazewnictwa czasowników

* Wszystkie interfejsy API mają wiodące *gx_* do łatwej identyfikacji jako Azure RTO GUIX

* Model programowania oparty na zdarzeniach (API)

* Pełna obsługa bezpośredniego rysowania kanwy w razie potrzeby

* Prosta do współpracy z wygenerowanym kodem usługi Azure RTO GUIX Studio

* Interfejsy API dla linii, prostokątów, wielokątów itp.

* Interfejsy API dla okręgu, łuku, koła, skrót, elipsy itp.

* Interfejsy API do rysowania i pozycjonowania tekstu

* Wygładzanie, wypełnienia tekstury i wypełnienia kryjące

* Interfejsy API do tworzenia i modifing ekranów i widżetów

### <a name="azure-rtos-guix-studio-generated-files"></a>Pliki wygenerowane przez usługę Azure RTO GUIX Studio

* Automatycznie wygenerowane pliki źródłowe ANSI C

* Izolowanie oprogramowania aplikacji od szczegółów układu

* Zawiera czcionki i obrazy wymagane przez Projektowanie interfejsu użytkownika

* Wygenerowane pliki skompilowane przy użyciu kodu aplikacji

* Układ ekranu można zaktualizować bez wpływu na logikę aplikacji

* Identyfikatory zasobów Utwórz niezależność języka i motywu

* Funkcje niestandardowego rysowania i przetwarzania zdarzeń dostarczone przez użytkownika

### <a name="widget-library"></a>Biblioteka widżetów

* Wstępnie zdefiniowany, ale dostosowywalny zestaw wspólnych elementów interfejsu

* Niezwykle małe, kompaktowe i wydajne

* Biblioteka zawiera przycisk, miernik, listę, okno, przewijanie, suwak, pasek postępu, monit i wiele innych

* W pełni dostosowywalny rysunek i wygląd

* W pełni dostosowywalna obsługa operacji i zdarzeń

* Tylko użyte elementy widget są połączone z oprogramowaniem aplikacji

### <a name="math-and-utilities"></a>Math i narzędzia

* Funkcje dla Sin, cos, łuków, ARccOS, tangens, pierwiastek kwadratowy

* Funkcje manipulowania regionami ekranu

* Konfiguracja systemu i uruchamianie

* Definicja puli pamięci (opcjonalnie)

* Zarządzanie czasomierzem

* Zarządzanie animacją

* Konserwacja listy zanieczyszczonej

### <a name="image-processing"></a>Przetwarzanie obrazów

* Funkcje dekodowania środowiska uruchomieniowego obrazów JPEG i PNG

* Stosowanie symulowania i konwersji przestrzeni kolorów

* Obrót obrazu

* Skalowanie obrazów

* Mieszanie obrazów

### <a name="event-processing"></a>Przetwarzanie zdarzeń

* Automatycznie wstrzymuje wątek usługi Azure RTO GUIX, gdy jest on bezczynny

* Model programowania oparty na zdarzeniach popularne w projekcie interfejsu użytkownika

* Izolowanie sterowników wejściowych z wątku rysowania usługi Azure RTO GUIX

* Funkcje wysyłania i otrzymywania zdarzeń

* Wstępnie zdefiniowane typy zdarzeń dla wszystkich typów widżetów GUIX usługi Azure RTO

* Obsługiwane zdarzenia niestandardowe zdefiniowane przez użytkownika

### <a name="canvas-processing"></a>Przetwarzanie kanwy

* Przycinanie i obsługa porządku osi Z

* Izolowanie biblioteki widget ze szczegółowych informacji o sprzęcie

* Izolowanie aplikacji od szczegółów sprzętu

* Automatyczne odświeżanie w tle obszarów zanieczyszczonych

* Obsługa wielu kanw z obsługą warstw i mieszania

* Może być wywoływana bezpośrednio przez oprogramowanie aplikacji

### <a name="input-device-drivers"></a>Sterowniki urządzeń wejściowych

* Obsługa specyficzna dla sprzętu, usługa Azure RTO GUIX i aplikacja izolowana ze szczegółowych informacji o sprzęcie

* Obsługiwane są odporne na dotknięcia, dotknięcie i klawiatura

* Zdarzenia wejściowe przesłane do kolejki zdarzeń usługi Azure RTO GUIX

### <a name="display-drivers"></a>Sterowniki ekranu

* Obsługa sprzętowa

* Ogólne sterowniki dostarczone dla całej głębi kolorów i formatów

* Dostosowany do korzystania z dostępnych akceleratorów grafiki

### <a name="target-hardware"></a>Sprzęt docelowy

* Niemal każdy sprzęt z możliwością grafiki wyjściowej jest zgodny z GUIX

* Obsługiwane są wiele fizycznych wyświetlaczy

* Minimalna ilość pamięci RAM i wymagania dotyczące programu Flash

## <a name="create-elegant-user-interfaces"></a>Tworzenie eleganckich interfejsów użytkownika

Usługi Azure RTO GUIX i Azure RTO GUIX Studio oferują wszystkie funkcje niezbędne do tworzenia unikatowych interfejsów użytkownika. Standardowy pakiet platformy Azure RTO GUIX obejmuje różne przykładowe interfejsy użytkownika, w tym informacje dotyczące urządzeń medycznych, odwołanie do inteligentnej czujki, odwołanie do automatyzacji domu, odwołanie do kontroli przemysłowej, odwołanie do sieci samochodowej i różne przykłady ikon i animacji. Kliknij przykłady referencyjne poniżej.

### <a name="home-automation"></a>Automatyzacja domu

<img alt="Screenshot of the GUIX home automation" class="img-responsive" src="./media/overview/guix_home_automation.png"/>

### <a name="medical"></a>Leczniczych

<img alt="Screenshot of the GUIX medical device" class="img-responsive" src="./media/overview/demo_guix_medical.png"/>

### <a name="consumer"></a>Produkty konsumenckie

<img alt="Screenshot of the GUIX Consumer smart watch" class="img-responsive" src="./media/overview/demo_guix_smart_watch.png"/>

### <a name="white-goods"></a>Białe towary

<img alt="Screenshot of the GUIX white goods exaample" class="img-responsive" src="./media/overview/demo_guix_white_goods.png"/>

### <a name="automotive"></a>Motoryzacja

<img alt="Screenshot of the GUIX automotive" class="img-responsive" src="./media/overview/demo_guix_infotainment.png"/>

### <a name="industrial"></a>Branżowe

<img alt="Screenshot of the GUIX industrial control" class="img-responsive" src="./media/overview/demo_guix_industrial.png"/>

Każda dokumentacja usługi Azure RTO GUIX ma odpowiedni projekt platformy Azure RTO GUIX Studio, który definiuje wszystkie elementy graficzne w projekcie referencyjnym. Zmiana projektu referencyjnego jest prosta. Po prostu otwórz odpowiedni projekt usługi Azure RTO GUIX, wprowadź żądane zmiany, Zapisz projekt, a następnie wybierz pozycję *projekt*.

Generuj wszystkie pliki wyjściowe, aby wygenerować kod języka C dla usługi Azure RTO GUIX. Następnie po prostu Skompiluj ponownie aplikację docelową i uruchom polecenie, aby obserwować zmodyfikowany projekt odwołań.

### <a name="small-footprint"></a>Niewielkie rozmiary

Usługa Azure RTO GUIX ma niewielką minimalną wartość 13.2 KB i 4 KB pamięci RAM na potrzeby podstawowej pomocy technicznej, bez uwzględnienia pamięci wymaganej dla kanwy.

Do wyświetlania z wewnętrzną technologią uczenia i samodzielnego odświeżania nie jest wymagana żadna pamięć kanwy. Jednak aby zwiększyć wydajność rysowania lub dla konfiguracji wyświetlania, która nie korzysta z lokalnego do wyświetlania, obszar pamięci kanwy jest definiowany przez aplikację.

Wymagania dotyczące pamięci kanwy są funkcją rozmiaru kanwy oraz głębią kolorów i są zdefiniowane przez formułę:

<i>Pamięć RAM kanwy (w bajtach) = (x * y * (BPP/8))</i>

Gdzie "x" i "y" są wymiarami kanwy (Display).

Większość aplikacji korzysta również z zasobów graficznych, które nie są uwzględnione w podstawowych wymaganiach dotyczących magazynu biblioteki usługi Azure RTO GUIX. Te zasoby obejmują czcionki, graficzne ikony (pixelmaps) i ciągi statyczne. Te dane mogą być przechowywane w sekcji Pamięć stała (tj. FLASH).

Rozmiar tego obszaru pamięci zależy od wielu czynników, w tym liczby i rozmiaru używanych czcionek, liczby i rozmiaru używanych ikon graficznych, formatu koloru wyjściowego oraz tego, czy każdy zasób korzysta z skompresowanych danych, ponieważ usługa Azure RTO GUIX obsługuje kompresję RLE zarówno czcionki, jak i Pixelmap. Wymagania dotyczące magazynu dla każdego zasobu są wyświetlane w aplikacji Azure RTO GUIX Studio, co umożliwia użytkownikowi śledzenie i monitorowanie ilości pamięci flash, która będzie używana przez zasoby aplikacji.

Podobnie jak w przypadku usługi Azure RTO ThreadX, rozmiar usługi Azure RTO GUIX jest automatycznie skalowany w oparciu o usługi faktycznie używane przez aplikację. To praktycznie eliminuje konieczność tworzenia skomplikowanych parametrów konfiguracji i kompilacji, co ułatwia deweloperom.

### <a name="fast-execution"></a>Szybkie wykonywanie

Usługa Azure RTO GUIX jest zapisywana wyłącznie w języku C i została zaprojektowana z myślą o szybkości. Usługa Azure RTO GUIX wymaga minimalnej warstwy wywołań wewnętrznych funkcji.

Ponadto usługa Azure RTO GUIX zapewnia zoptymalizowane obcinanie, rysowanie i obsługę zdarzeń. Wszystkie te i ogólne zasady projektowania zorientowane na wydajność ułatwiają platformie Azure RTO GUIX osiąganie najszybszej możliwej wydajności.

### <a name="pre-certified--by-tuv-to-many-safety-standards"></a>Certyfikowane przed certyfikatami przez TUV z wieloma standardami bezpieczeństwa

Usługa Azure RTO GUIX została certyfikowana przez moimi-TUV Saar do użytku w systemach krytycznych dla bezpieczeństwa, zgodnie z IEC-61508 SIL 4, IEC-62304, Klasa bezpieczeństwa SW, ISO 26262 ASIL D i EN 50128. Certyfikat potwierdza, że usługa Azure RTO GUIX może być używana w rozwoju oprogramowania związanego z bezpieczeństwem w celu uzyskania najwyższych poziomów integralności zabezpieczeń IEC-61508, IEC-62304, ISO 26262 i EN 50128 na potrzeby "bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego systemów związanych z bezpieczeństwem". MOIMI-TUV Saar, utworzone za pomocą wspólnego przedsiębiorstwa z Niemiec SGS-Group i TUV Saarland, stał się wiodącą, niezależną firmą do testowania, przeprowadzania inspekcji, sprawdzania i certyfikowania oprogramowania osadzonego dla systemów związanych z bezpieczeństwem na całym świecie. Standard bezpieczeństwa przemysłowego IEC 61508, a także wszystkie standardy, które są od niego pochodzące, w tym IEC-62304, ISO 26262 i EN 50128, są używane do zapewnienia bezpieczeństwa funkcjonalnego, elektronicznego i programowalnego elektronicznego sprzętu medycznego, systemów kontroli procesów, maszyn przemysłowych, samochodów i systemów kontroli szynowej.

<img alt="SGS-TUV Saar" class="img-responsive" src="https://rtos.com/wp-content/uploads/2017/10/partener-logo-sgs-tuv-saar-2.png"/>

#### <a name="simple-easy-to-use"></a>Proste i łatwe w użyciu

Korzystanie z usługi Azure RTO GUIX jest bardzo proste, a usługa Azure RTO GUIX Studio ułatwia deweloperom wizualne projektowanie na pulpicie i generowanie kodu języka C, który jest uruchamiany w rzeczywistym miejscu docelowym. Aplikacje mogą następnie dodać własne niestandardowe funkcje obsługi zdarzeń i rysowania, aby zakończyć ich graficzny interfejs użytkownika.

Korzystanie z interfejsu API usługi Azure RTO GUIX jest proste. Interfejs API usługi Azure RTO GUIX jest intuicyjny i wysoce funkcjonalny. Nazwy interfejsów API są prawdziwe mówiące i nie są "alfabetem" i/lub bardzo skróconymi nazwami, które są powszechnie używane w innych produktach systemu plików. Wszystkie interfejsy API usługi Azure RTO GUIX mają wiodące *gx_* i są zgodne z konwencją nazewnictwa czasowników. Ponadto istnieje spójność funkcjonalna w całym interfejsie API. Na przykład wszystkie interfejsy API, które inicjują blok kontrolki widżetu, mają nazwę &lt; widget_type &gt; _create, a parametry funkcji tworzenia dla każdego typu widżetu są zawsze zdefiniowane w tej samej kolejności.

### <a name="comprehensive-set-of-built-in-widgets"></a>Kompleksowy zestaw wbudowanych elementów widget

* Usługa Azure RTO GUIX oferuje bogaty zestaw wbudowanych elementów widget, takich jak:

* Menu przyznane

* Przycisk

* Pole wyboru

* Miernik kołowy

* Lista rozwijana

* Lista pozioma

* Poziome okno przewijania

* Ikona

* Przycisk ikony

* Wykres liniowy

* Menu

* Przycisk tekstu wielowierszowego

* Wprowadzanie tekstu wielowierszowego

* Widok tekstu wielowierszowego

* Numeryczny monit Pixelmap

* Monit liczbowy

* Pokrętło przewijania liczbowego

* Przycisk Pixelmap

* Pixelmap monit

* Suwak Pixelmap

* Pixelmap Sprite

* pasek postępu

* Monit

* Pasek postępu promieniowego

* przycisk radiowy

* Kółko przewijania

* Wejście tekstu jednowierszowego

* Suwak

* Kółko przewijania ciągów

* Przycisk tekstu

* Widok drzewa

* Lista pionowa

* Pionowy pasek przewijania

Aplikacja może również łatwo tworzyć własne widżety klienta.

### <a name="complete-low-level-drawing-api"></a>Kompletny interfejs API rysowania niskiego poziomu

Usługa Azure RTO GUIX zapewnia niezawodny interfejs API rysowania kanwy, co pozwala aplikacji na renderowanie złożonych kształtów graficznych.

Wszystkie funkcje obsługują wygładzanie w przypadku obiektów docelowych o dużej głębi kolorów, a wszystkie kształty mogą być wypełniane, w tym wypełnieniami pełnymi i Pixelmap. Wszystkie elementy pierwotne rysowania obsługują alfa pędzla, gdy działa o 16 BPP i większej głębi kolorów. Funkcje rysowania obejmują:

* Rysuj łuk

* Okrąg rysowania

* Rysowanie linii

* Rysowanie wykresu kołowego

* Pixelmap Blend

* Kafelek Pixelmap

* Rysowanie wielokątów

* Rysowanie tekstu

* Skrót remis

* Rysowanie elips

* Rysowanie pikseli

* Pixelmap remis

* Pixelmap

* Rysowanie prostokąta

* Mieszanie tekstu

### <a name="default-free-fonts-and-easy-to-add-more"></a>Domyślne czcionki bezpłatne i łatwe dodawanie

Usługa Azure RTO GUIX oferuje bezpłatny zestaw czcionek TrueType. Deweloperzy mogą dodawać dodatkowe czcionki TrueType zgodnie z potrzebami.

Format czcionki GUIX usługi Azure RTO obsługuje 8bpp Anti-aliasing, 4bpp Anti-aliasing i 1bpp monochromatyczne czcionki. W przypadku większości aplikacji z ograniczeniami zasobów usługa Azure RTO GUIX wstępnie renderuje czcionki TrueType do formatu skompresowanej mapy bitowej przy użyciu narzędzia klasycznego GUIX Studio.

### <a name="custom-jpg-and-png-decoder-implementation"></a>Implementacja niestandardowego dekodera JPG i PNG

Implementacja niestandardowego dekodera JPG i PNG, implementacja dekodera pliku JPG i PNG. Ta implementacja obsługuje konwersję przestrzeni kolorów, symulowanie i tworzenie obrazów formatu Pixelmap zgodnych z usługą Azure RTO GUIX.

### <a name="extensive-display-and-touchscreen-support"></a>Rozbudowana obsługa wyświetlania i ekranu dotykowego

Usługa Azure RTO GUIX udostępnia ogólne sterowniki wyświetlania dla niemal wszystkich formatów kolorów, w tym 1bpp monochromatyczny, 8 palety BPP, 8 BPP 3:3:2,

16 BPP 565 RGB, format 16 BPP 4:4:4:4, 32 BPP x:r: g:b format i 32 BPP a:r: g:b format. Ponadto usługa Azure RTO GUIX jest zintegrowana z wieloma najpopularniejszymi kontrolerami LCD i akceleratorami sprzętowymi (ST ChromeArt, Renesas synergia itp.).

Usługa Azure RTO GUIX w pełni obsługuje ekran dotykowy (w tym obsługę gestów), pióro i wirtualne urządzenia wejściowe z klawiatury.

### <a name="azure-rtos-guix-studio-desktop-wysiwyg-tool"></a>Narzędzie Azure RTO GUIX Studio w trybie WYSIWYG

Usługa Azure RTO GUIX Studio oferuje kompletne środowisko projektowania ekranu, które pozwala użytkownikowi na przeciąganie i upuszczanie elementów graficznych używanych do tworzenia ekranów graficznego interfejsu użytkownika. Usługa Azure RTO GUIX Studio automatycznie generuje kod C zgodny z biblioteką GUIX RTO platformy Azure, gotowy do skompilowania i uruchomienia w miejscu docelowym. Deweloperzy mogą tworzyć wstępnie renderowane czcionki do użycia w aplikacji przy użyciu zintegrowanego narzędzia do generowania czcionek usługi Azure RTO GUIX Studio. Czcionki można generować w formatach monochromatycznych lub z wygładzaniem i są zoptymalizowane pod kątem oszczędzania miejsca na miejscu docelowym. Czcionki mogą zawierać dowolny zestaw znaków, w tym znaki Unicode dla aplikacji wielojęzycznych.

<img alt="Diagram of SGS-TUV Saar certification logo" class="alignnone size-full wp-image-1500" height="341" sizes="(max-width: 535px) 100vw, 535px" src="./media/overview/studio_screen_shot.png"/>

Usługa Azure RTO GUIX Studio ułatwia importowanie grafiki z plików PNG lub JPG z konwersją na skompresowany system Azure RTO GUIX Pixelmaps do użycia w systemie docelowym. Wiele typów widżetów GUIX usługi Azure RTO została zaprojektowana w celu uwzględnienia grafiki użytkownika w celu uzyskania niestandardowego wyglądu i działania. Ponadto usługa Azure RTO GUIX Studio umożliwia dostosowanie domyślnych kolorów i stylów rysowania używanych przez widżety GUIX platformy Azure RTO, dzięki czemu deweloperzy mogą łatwo dostosowywać wygląd rozwiązań Azure RTO GUIX. Generowanie i obsługa ciągów aplikacji jest kolejną wbudowaną funkcją platformy Azure RTO GUIX Studio. Pozwala to deweloperom na projektowanie aplikacji przy użyciu jednego języka do opracowania i szybkie i łatwe dodawanie obsługi dodatkowych języków po wydaniu produktu. Kompletna aplikacja usługi Azure RTO GUIX może być wykonywana na komputerze stacjonarnym w środowisku usługi Azure RTO GUIX Studio, co pozwala na szybkie i łatwe generowanie i demonstrację pojęć GUI, testowanie przepływów ekranu oraz obserwacje przejść ekranu i animacji. Po zakończeniu projektowania można eksportować jako docelowe struktury danych języka C gotowe do skompilowania i połączoną z bibliotekami Azure RTO GUIX i Azure RTO ThreadX.

Usługa Azure RTO GUIX i usługa Azure RTO GUIX Studio obsługują wiele kompozycji zasobów, dzięki czemu aplikacja może być łatwo w czasie wykonywania. Czcionki, kolory i pixelmaps można zmieniać w czasie wykonywania za pomocą jednego prostego interfejsu API.

Dowiedz się więcej o programie GUIX Studio

### <a name="complete-win32-simulation"></a>Ukończ symulację Win32

Usługa Azure RTO GUIX działa na komputerze z systemem Windows, używając dokładnie tej samej biblioteki rysowania, która jest uruchamiana na tablicy docelowej. Za pomocą usługi Azure RTO GUIX można kompilować i uruchamiać aplikację graficznego interfejsu użytkownika na komputerze oraz korzystać z tego samego kodu aplikacji w celu debugowania, szybkiego tworzenia prototypów, demonstracyjnej i docelowej operacji WYSIWYG.

### <a name="advanced-technology"></a>Technologia zaawansowana

* Zaawansowana technologia Azure RTO GUIX:

* Mieszanie alfa

* Wygładzanie

* Automatyczne skalowanie

* Kompresja mapy bitowej

* Mieszanie kanwy

* Obsługa niestandardowego widżetu

* Obsługa rysowania odroczonego

* Obsługa symulowania

* Programowanie neutralne endian

* Obsługa akceleratora sprzętowego

* Obsługa wielojęzyczna i kodowanie UTF-8

* Obsługa wielu wyświetlaczy i kanwy

* Zoptymalizowane obcinanie, rysowanie i obsługa zdarzeń

* Dekoder plików JPEG i PNG

* Karnacje i motywy

* Obsługuje monochromatyczny do 32-bitowego True-Color z formatami grafiki alfa

* Przejścia, sprites i obsługa animacji

* Symulacja Win32

* Zarządzanie oknami, w tym okienka ekranu i konserwacja Z kolejnością Z

### <a name="fastest-time-to-market"></a>Najszybszy czas wprowadzenia na rynek

Usługa Azure RTO GUIX jest łatwa do zainstalowania, uczenia się, używania, debugowania, weryfikowania, certyfikowania i konserwowania. Usługa Azure RTO GUIX Studio pomaga również uprościć projektowanie i implementację osadzonego interfejsu użytkownika. W związku z tym usługa Azure RTO GUIX jest jednym z najpopularniejszych rozwiązań interfejsu GUI dla osadzonych urządzeń IoT. Nasza spójna przedział czasu na rynek jest oparta na:

* Dokumentacja dotycząca jakości — zapoznaj się z naszym [podręcznikiem użytkownika usługi Azure RTO GUIX](about-guix.md) i zapoznaj się z Tobą.

* Ukończ dostępność kodu źródłowego

* Łatwy w użyciu interfejs API

* Kompleksowy i zaawansowany zestaw funkcji

## <a name="one-simple-license"></a>Jedna prosta licencja

Nie ma kosztu użycia i przetestowania kodu źródłowego bez ponoszenia kosztów dla licencji produkcyjnych po wdrożeniu na wstępnie licencjonowanych urządzeniach. wszystkie inne urządzenia wymagają prostej licencji rocznej.

## <a name="full-highest-quality-source-code"></a>Pełny kod źródłowy o najwyższej jakości

W ciągu lat kod źródłowy usługi Azure RTO NetX ustawił na pasku jakość i łatwość interpretacji. Ponadto Konwencja o jednej funkcji na plik umożliwia łatwe nawigowanie po źródle.

## <a name="supports-most-popular-architectures"></a>Obsługuje najpopularniejsze architektury

Usługa Azure RTO GUIX działa na najpopularniejszych mikroprocesorach 32-bitowych, w pełni przetestowanych i w pełni obsługiwanych, w tym:

Architektury zaawansowane:

**Urządzenia analogowe**: SHARC, Blackfin, CM4xx

**Andes rdzeń**: RISC-V

**Ambiqmicro**: Apollo MCUs

**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/wy/A8/A9/A5x 64-BI/A7x 64-bit/R4/R5, TrustZone ARMv8-M

**Erze**: Xtensa, romb

**Ceva**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0 +, FM3, MF4, wiced Wi-Fi

**Cypress**: RISC-V

**EnSilica**: ESI-RISC

**Infineon**: XMC1000, XMC4000, TriCore

**Intel; Intel FPGA**: x36/Pentium, XScale, Nios II, Cyclone, Arria 10

**Chip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/g/L/SV, PIC24/PIC32

**Mikrośrednik**: RISC-V

**NXP**: LPC, ARM7, ARM9, PowerPC, 68K, I.MX, ColdFire, Kinetis Cortex-M3/M4

**Renesas**: sh, HS, V850, RX, rz, synergia

**Krzem Labs**: EFM32

**SynopSYS**: Arc 600, 700, łuk em, łuk HS

**St**: STM32, ARM7, ARM9, Cortex-M3/M4/M7

**: C5xxx**, C6xxx, Stellaris, Sitara, Tiva-C

**Przetwarzanie Wave**: MIPS32 4K, 24K, 34K, 1004K, MIPS64 5 K, MicroAptiv, InterAptiv, ProAptiv, Klasa M

**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE
