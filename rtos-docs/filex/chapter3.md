---
title: Rozdział 3 — Składniki funkcjonalne Azure RTOS FileX
description: Ten rozdział zawiera opis systemu plików Azure RTOS FileX o wysokiej wydajności z perspektywy funkcjonalnej
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bb2e1d7f10d71ed01a040cea63e9e469855525d89dd6318f3147c61ed166ee4c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783087"
---
# <a name="chapter-3---functional-components-of-azure-rtos-filex"></a>Rozdział 3 — Składniki funkcjonalne Azure RTOS FileX

Ten rozdział zawiera opis systemu plików Azure RTOS FileX o wysokiej wydajności z perspektywy funkcjonalnej.

## <a name="media-description"></a>Opis nośnika

FileX to osadzony system plików o wysokiej wydajności, który jest zgodny z formatem systemu plików FAT. Plik FileX widokuje nośnik fizyczny jako tablicę sektorów logicznych. Sposób zamapowania tych sektorów na podstawowy nośnik fizyczny jest określany przez sterownik we/wy połączony z nośnikami FileX podczas fx_media_open ***wywołania.***

### <a name="fat121632-logical-sectors"></a>Sektory logiczne FAT12/16/32

Dokładna organizacja sektorów logicznych nośnika zależy od zawartości rekordu rozruchowego nośnika fizycznego. Ogólny układ sektorów logicznych nośnika przedstawiono na rysunku 1.

Sektory logiczne FileX zaczynają się od sektora logicznego 1, który wskazuje pierwszy zarezerwowany sektor nośnika. Sektory zarezerwowane są opcjonalne, ale gdy są używane, zwykle zawierają informacje o systemie, takie jak kod rozruchowy.

### <a name="fat121632-media-boot-record"></a>Rekord rozruchowy nośnika FAT12/16/32

Dokładne przesunięcie sektora innych obszarów w widoku sektora logicznego nośnika pochodzi od zawartości *rekordu rozruchowego nośnika*. Lokalizacja rekordu rozruchowego zwykle znajduje się w sektorze 0. Jeśli jednak nośnik ma ukryte sektory *,* przesunięcie do sektora rozruchowego musi uwzględniać je (znajdują się one bezpośrednio przed sektorem rozruchowym). Tabela 1 zawiera listę składników rekordu rozruchowego nośnika, a składniki zostały opisane w akapitach.

- **Instrukcja skoku** Pole *instrukcji skoku* to trzy bajtowe pole reprezentujące instrukcję maszyny Intel x86 dla skoku procesora. Jest to starsze pole w większości sytuacji.

  ![Widok sektora logicznego nośnika FileX](./media/user-guide/filex-media-logical-sector-view.png)

  **RYSUNEK 1. Widok sektora logicznego nośnika FileX**

- **Nazwa OEM** Pole *Nazwa producenta OEM* jest zarezerwowane dla producentów, aby umieścić ich nazwę lub nazwę urządzenia.
- **Bajty na sektor** Pole *bajtów na sektor* w rekordzie rozruchowym nośnika definiuje, ile bajtów jest w każdym sektorze — podstawowym elementem nośnika.
- **Sektory na klaster** Sektory *na pole klastra* w rekordzie rozruchowym nośnika definiują liczbę sektorów przypisanych do klastra. Klaster jest podstawowym elementem alokacji w systemie plików zgodnym z systemem PLIKÓW FAT. Wszystkie informacje o plikach i podkatalogach są przydzielane z dostępnych klastrów nośników określonych przez tabelę alokacji plików (FAT).

    **TABELA 1. Rekord rozruchowy nośnika FileX**
    
    |Przesunięcie  |Pole  |Liczba bajtów|
    |----------|-----------|------------|
    |0x00|Instrukcja skoku (e9,xx,xx lub eb,xx,90)|3|
    |0x03|Nazwa OEM|8|
    |0x0B|Bajty na sektor|2|
    |0x0D|Sektory na klaster|1|
    |0x0E|Liczba zarezerwowanych sektorów|2|
    |0x10|Liczba fajerzy|1|
    |0x11|Rozmiar katalogu głównego|2|
    |0x13|Liczba sektorów FAT-12 &amp; FAT-16|2|
    |0x15|Typ nośnika|1|
    |0x16|Liczba sektorów na FAT|2|
    |0x18|Sektory na ścieżkę|2|
    |0x1A|Liczba orzeł|2|
    |0x1C|Liczba ukrytych sektorów|4|
    |0x20|Liczba sektorów — FAT-32|4|
    |0x24|Sektory na FAT (FAT-32)|4|
    |0x2C|Klaster katalogu głównego|4|
    |0x3E|Kod rozruchu systemu|448
    |0x1FE|0x55AA|2|

- **Sektory zarezerwowane** Pole *zarezerwowanych sektorów* w rekordzie rozruchowym nośnika definiuje liczbę sektorów zarezerwowanych między rekordem rozruchowym a pierwszym sektorem obszaru FAT. W większości przypadków ten wpis ma wartość zero.
- **Liczba fajerzy** Liczba *wpisów fajerzy* w rekordzie rozruchowym nośnika definiuje liczbę otchłani na nośniku. W nośniku musi zawsze znajdować się co najmniej jeden fat. Dodatkowe fajerzy to tylko zduplikowane kopie podstawowego (pierwszego) systemu PLIKÓW FAT i są zwykle używane przez oprogramowanie diagnostyczne lub odzyskiwania.
- **Rozmiar katalogu głównego** Wpis *rozmiaru katalogu głównego* w rekordzie rozruchowym nośnika definiuje stałą liczbę wpisów w katalogu głównym nośnika. To pole nie ma zastosowania do podkatalogów i katalogu głównego FAT-32, ponieważ są one przydzielone z klastrów nośników.
- **Liczba sektorów FAT-12 & FAT-16** Pole *liczba sektorów* w rekordzie rozruchowym nośnika zawiera łączną liczbę sektorów w nośniku. Jeśli to pole ma wartość zero, łączna liczba sektorów jest zawarta w polu *fat-32* sektorów, które znajduje się w dalszej części rekordu rozruchowego.
- **Typ nośnika** Pole *typ nośnika* służy do identyfikowania typu nośnika obecnego w sterowniku urządzenia. Jest to starsze pole.
- **Sektory na FAT** Sektory *na FAT* zgłoszone w rekordzie rozruchu nośnika zawiera liczbę sektorów skojarzonych z każdym FAT w obszarze FAT. Liczba sektorów FAT musi być wystarczająco duża, aby uwzględnić maksymalną możliwą liczbę klastrów, które można przydzielić na nośniku.
- **Sektory na ścieżkę** Sektory *na pole ścieżki* w rekordzie rozruchowym nośnika definiują liczbę sektorów na ścieżkę. Zazwyczaj dotyczy to tylko rzeczywistego nośnika dysku. Urządzenia FLASH nie używają tego mapowania.
- **Liczba orzeł** Liczba *orzeł* w rekordzie rozruchowym nośnika definiuje liczbę orzeł w nośniku. Zazwyczaj dotyczy to tylko rzeczywistego nośnika dysku. Urządzenia FLASH nie używają tego mapowania.
- **Ukryte sektory** Pole *ukrytych sektorów* w rekordzie rozruchowym nośnika definiuje liczbę sektorów przed rekordem rozruchowym. To pole jest utrzymywane w bloku **sterowania FX_MEDIA** i musi być uwzględnione w sterownikach We/Wy FileX we wszystkich żądaniach odczytu i zapisu wykonanych przez plik FileX.
- **Liczba sektorów FAT-32** Pole *liczba sektorów* w rekordzie rozruchowym nośnika jest prawidłowe tylko wtedy, gdy dwu bajtowa *liczba sektorów* jest równa zero. W takim przypadku to cztero bajtowe pole zawiera liczbę sektorów w nośniku.
- **Sektory na FAT (FAT-32)** Sektory *na fat (FAT-32)* pole jest prawidłowe tylko w formacie FAT-32 i zawiera liczbę sektorów przydzielonych dla każdego FAT nośnika.
- **Klaster katalogu głównego** Pole *klastra katalogu głównego* jest prawidłowe tylko w formacie FAT-32 i zawiera numer początkowego klastra katalogu głównego.
- **Kod rozruchu systemu** Pole *kod rozruchu* systemu jest obszarem do przechowywania niewielkiej części kodu rozruchowego. Obecnie w większości urządzeń jest to starsze pole.
- **Sygnatura 0x55AA** Pole *podpisu* jest wzorcem danych używanym do identyfikowania rekordu rozruchowego. Jeśli to pole nie istnieje, rekord rozruchowy jest nieprawidłowy.

### <a name="exfat"></a>Exfat

Maksymalny rozmiar plików w systemie FAT32 wynosi 4 GB, co ogranicza szerokie wdrożenie plików multimedialnych o wysokiej rozdzielczości. Domyślnie system FAT32 obsługuje nośniki magazynu o rozmiarze do 32 GB. Zwiększając pojemność karty flash i SD, system FAT32 staje się mniej wydajny w zarządzaniu dużymi woluminami. Projekt exFAT został zaprojektowany w celu pokonania tych ograniczeń. System exFAT obsługuje rozmiar pliku do jednego eksabajta (EB), czyli około miliarda GB. Inną istotną różnicą między exFAT i FAT32 jest to, że exFAT używa mapy bitowej do zarządzania dostępnego miejsca w woluminie, dzięki czemu exFAT wydajniejsze znajdowanie dostępnego miejsca podczas zapisywania danych w pliku. W przypadku plików przechowywanych w ciągłych klastrach funkcja exFAT eliminuje chodzenie w dół łańcucha FAT w celu znalezienia wszystkich klastrów, co zapewnia większą wydajność podczas uzyskiwania dostępu do dużych plików. System exFAT jest wymagany w przypadku pamięci flash i kart SD większych niż 32 GB.

### <a name="exfat-logical-sectors"></a>Sektory logiczne exFAT

Ogólny układ sektorów logicznych nośnika w exFAT został zilustrowany na rysunku 2. W systemie exFAT blok rozruchowy i obszar FAT należą do obszaru systemu. Pozostałe klastry to obszar użytkownika. Chociaż nie jest to wymagane, standard exFAT zaleca, aby mapowanie bitowe alokacji znajduje się na początku obszaru użytkownika, po którym następuje tabela przypadków up-case i katalog główny.

### <a name="exfat-media-boot-record"></a>ExFAT Media Boot Record

Zawartość rekordu rozruchowego nośnika w exFAT różni się od tych w FAT12/16/32. Są one wymienione w tabeli 2. Aby uniknąć nieporozumień, obszar między 0x0B i 0x40, który zawiera różne parametry nośnika w FAT12/16/32, jest oznaczony jako zarezerwowany w exFAT.  Ten zarezerwowany obszar musi być zaprogramowany zerami, aby uniknąć błędnej interpretacji rekordu rozruchowego nośnika.

![Sektory logiczne exFAT](./media/user-guide/exfat-logical-sectors.png)

**RYSUNEK 2. Sektory logiczne exFAT**

- **Instrukcja skoku** Pole *instrukcji skoku* to trzy bajtowe pole reprezentujące instrukcję maszyny Intel x86 dla skoku procesora. Jest to starsze pole w większości sytuacji.

    **TABELA 2. ExFAT Media Boot Record**

    |Przesunięcie  |Pole  |Liczba bajtów|
    |----------|-----------|------------|
    |0x00|Instrukcja skoku|3|
    |0x03|Nazwa systemu plików|8|
    |0x0B|Zarezerwowany|53|
    |0x40|Przesunięcie partycji|8|
    |0x48|Długość woluminu|8|
    |0x50|Przesunięcie FAT|4|
    |0x54|Długość FAT|4|
    |0x58|Przesunięcie sterty klastra|4|
    |0x5C|Liczba klastrów|4|
    |0x60|Pierwszy klaster katalogu głównego|4|
    |0x64|Numer seryjny woluminu|4|
    |0x68|Poprawka systemu plików|2|
    |0x6A|Flagi woluminu|2|
    |0x6C|Przesunięcie w bajtach na sektor|1|
    |0x6D|Przesunięcie sektora na klaster|1|
    |0x6E|Liczba otów|1|
    |0x6F|Wybieranie dysku|1|
    |0x70|Procent użycia|7|
    |0x71|Zarezerwowany|1|
    |0x78|Kod rozruchowy|390|
    |0x1FE|Podpis rozruchu|2|

- **Nazwa systemu plików** W przypadku exFAT *pole nazwy systemu* plików musi być "EXFAT", po którym nasuną się trzy końcowe białe spacje.
- **Zarezerwowane** Zawartość pola *zarezerwowanego musi* być równa zero. Ten region nakłada się na rekordy rozruchu w FAT12/16/32. Dzięki temu obszarowi zero unika systemom plików błędnej interpretacji tego woluminu.
- **Przesunięcie partycji** Pole *przesunięcia partycji* wskazuje początek tej partycji.
- **Długość woluminu** Pole *długości woluminu* definiuje rozmiar tej partycji (w liczbie sektorów).
- **Przesunięcie FAT** W *polu przesunięcia FAT* zdefiniowano początkowy numer sektora względem początku tej partycji tabeli FAT dla tej partycji.
- **Długość FAT** Pole *Długość FAT* definiuje rozmiar tabeli FAT w liczbie sektorów.
- **Przesunięcie sterty klastra** Pole *przesunięcia sterty* klastra definiuje początkowy numer sektora względem początku partycji sterty klastra. Sterta klastra to obszar, w którym są przechowywane informacje o katalogach i danych plików.
- **Liczba klastrów** Pole *liczba klastrów* definiuje liczbę klastrów, które zawiera ta partycja.
- **Pierwszy klaster katalogu głównego** Pierwszy *klaster w* polu katalogu głównego definiuje lokalizację początkową katalogu głównego, co jest zalecane bezpośrednio po mapie bitowej alokacji i tabeli przypadków początkowych.
- **Numer seryjny woluminu** Pole *numeru seryjnego* woluminu definiuje numer seryjny dla tej partycji.
- **Poprawka systemu plików** Pole *poprawki systemu plików* definiuje wersję główną i pomocniczą exFAT.
- **Flagi woluminu** Pole *flag woluminu* zawiera flagi wskazujące stan tego woluminu.
- **Przesunięcie w bajtach na sektor** Pole *przesunięcia liczby* bajtów na sektor definiuje liczbę bajtów na sektor w log2(n), gdzie n to liczba bajtów na sektor. Na przykład w przypadku karty SD rozmiar sektora wynosi 512 bajtów. Dlatego to pole musi mieć wartość 9 (log2(512) = 9).
- **Sektory na przesunięcie klastra** Sektory *na pole zmiany* klastra definiują liczbę sektorów w klastrze, w dzienniku log2(n), gdzie n to liczba sektorów na klaster.
- **Liczba fajerzy** Liczba *pól FATs* definiuje liczbę tabel FAT w tej partycji. W przypadku tabeli exFAT zaleca się użycie wartości 1 dla jednej tabeli FAT.
- **Wybieranie dysku** Pole *wyboru sterownika* definiuje rozszerzony numer dysku INT 13h.
- **Procent użycia** Pole *procentu użycia* definiuje procent przydzielanych klastrów w stercie klastra. Prawidłowe wartości to od 0 do 100 (włącznie).
- **Zarezerwowane** To pole jest zarezerwowane do użytku w przyszłości.
- **Kod rozruchowy** Pole *kodu rozruchowego* to obszar do przechowywania niewielkiej części kodu rozruchowego. Obecnie w większości urządzeń jest to starsze pole.
- **Sygnatura 0x55AA** Pole *podpis rozruchu* jest wzorcem danych używanym do identyfikowania rekordu rozruchowego. Jeśli to pole nie istnieje, rekord rozruchowy jest nieprawidłowy.

### <a name="file-allocation-table-fat"></a>Tabela alokacji plików (FAT)

Tabela *alokacji plików (FAT) rozpoczyna* się po zarezerwowanych sektorach nośnika. Obszar FAT jest zasadniczo tablicą 12-bitowych, 16-bitowych lub 32-bitowych wpisów, które określają, czy ten klaster jest przydzielony, czy częścią łańcucha klastrów składającego się z podkatalogu lub pliku. Rozmiar każdego wpisu FAT zależy od liczby klastrów, które muszą być reprezentowane. Jeśli liczba klastrów (pochodzących z całkowitej liczby sektorów podzielonych przez sektory na klaster) jest mniejsza lub równa 4086, używane są 12-bitowe wpisy FAT. Jeśli łączna liczba klastrów jest większa niż 4086 i mniejsza niż 65 525, używane są 16-bitowe wpisy FAT. W przeciwnym razie, jeśli łączna liczba klastrów jest większa lub równa 65 525, używane są 32-bitowe fat lub exFAT.

W przypadku systemu FAT12/16/32 tabela FAT nie tylko utrzymuje łańcuch klastrów, ale także zawiera informacje na temat alokacji klastra: czy klaster jest dostępny. W programie exFAT informacje o alokacji klastra są utrzymywane przez wpis katalogu map bitowych alokacji. Każda partycja ma własną mapę bitową alokacji. Rozmiar mapy bitowej jest wystarczająco duży, aby zakrywać wszystkie dostępne klastry. Jeśli klaster jest dostępny do alokacji, odpowiedni bit w mapie bitowej alokacji jest ustawiony na 0. W przeciwnym razie bit jest ustawiony na 1. W przypadku pliku, który zajmuje kolejne klastry, exFAT nie wymaga łańcucha FAT do śledzenia wszystkich klastrów. Jednak w przypadku pliku, który nie zajmuje kolejnych klastrów, nadal należy zachować łańcuch FAT.

### <a name="fat-entry-contents"></a>Zawartość wpisu FAT

Pierwsze dwa wpisy w tabeli FAT nie są używane i zwykle mają następującą zawartość.

|Wpis FAT |12-bitowy fat|16-bitowy fat|32-bitowy fat| Exfat|
|----------|-----------|------------|-------|------|
|Wpis 0|0x0F0|0x00F0|0x000000F0|0xF8FFFFFF|
|Wpis 1|0xFFF|0xFFFF|0x0FFFFFFF|0xFFFFFFFF|

Numer wpisu FAT 2 reprezentuje pierwszy klaster w obszarze danych nośnika. Zawartość każdego wpisu klastra określa, czy jest on bezpłatny, czy też jest częścią połączonej listy klastrów przydzielonych dla pliku lub podkatalogu. Jeśli wpis klastra zawiera inny prawidłowy wpis klastra, zostanie przydzielony klaster, a jego wartość wskazuje następny klaster przydzielony w łańcuchu klastra.

Możliwe wpisy klastra są zdefiniowane w następujący sposób.

|Znaczenie|12-bitowy fat|16-bitowy fat|32-bitowy fat| Exfat|
|----------|-----------|------------|-------|------|
|Klaster bezpłatny|0x000|0x0000|0x00000000|0x00000000|
|Nie używane|0x001|0x0001|0x00000001|0x00000001|
|Zarezerwowany|0xFF0-FF6|0xFFF0-FFF6|0x0FFFFFF0–6|ClusterCounter +2 do 0xFFFFFFF6|
|Zły klaster|0xFF7|0xFFF7|0x0FFFFFF7|0xFFFFFFF7|
|Zarezerwowany| - | - | - | 0xFFFFFFF8-E|
|Ostatni klaster| 0xFF8-FFF| 0xFFF8-FFFF| 0x0FFFFFF8-F| 0xFFFFFFFF|
|Łącze klastra| 0x002-0xFEF| 0x0002-FFEF| 0x2-0x0FFFFFEF | 0x2 — ClusterCount + 1|

Ostatni klaster w przydzielonym łańcuchu klastrów zawiera wartość Ostatni klaster (zdefiniowaną powyżej). Pierwszy numer klastra znajduje się we wpisie katalogu pliku lub podkatalogu.

### <a name="internal-logical-cache"></a>Wewnętrzna pamięć podręczna logiczna

Plik FileX przechowuje *ostatnio używaną pamięć podręczną* sektorów logicznych dla każdego otwartego nośnika. Maksymalny rozmiar pamięci podręcznej sektora logicznego jest definiowany przez stałą **FX_MAX_SECTOR_CACHE** i znajduje się w **_fx_api.h._** Jest to pierwszy czynnik określający rozmiar wewnętrznej pamięci podręcznej sektora logicznego.

Innym czynnikiem, który określa rozmiar pamięci podręcznej sektora logicznego, jest ilość pamięci dostarczonej do wywołania ***fx_media_open** _ przez aplikację. Musi być wystarczająca ilość pamięci dla co najmniej jednego sektora logicznego. Jeśli wymaganych jest więcej niż _ *FX_MAX_SECTOR_CACHE** sektory logiczne, należy zmienić stałą w pliku **_fx_api.h_** i całą bibliotekę FileX należy ponownie sbudować.

> [!IMPORTANT]
> *Każdy otwarty nośnik w pliku FileX może mieć inny rozmiar pamięci podręcznej w zależności od pamięci dostarczonej podczas otwartego wywołania.*

### <a name="write-protect"></a>Ochrona zapisu

FileX zapewnia sterownikowi aplikacji możliwość dynamicznego ustawienia ochrony zapisu na nośniku. Jeśli ochrona zapisu jest wymagana, sterownik ustawia FX_TRUE *fx_media_driver_write_protect* w skojarzonej FX_MEDIA struktury. Po jego skonfigurowaniu wszystkie próby zmodyfikowania nośnika przez aplikację są odrzucane, a także próby otwarcia plików do zapisu. Sterownik może również wyłączyć ochronę zapisu, czyszcząc to pole.

### <a name="free-sector-update"></a>Aktualizacja wolnych sektorów

FileX udostępnia mechanizm informowania sterownika aplikacji, gdy sektory nie są już w użyciu. Jest to szczególnie przydatne w przypadku menedżerów pamięci FLASH, które zarządzają wszystkimi sektorami logicznymi używanymi przez system FileX.

Jeśli wymagane jest powiadomienie o wolnych sektorach, sterownik aplikacji ustawia FX_TRUE fx_media_driver_free_sector_update *polu* w skojarzonej FX_MEDIA danych. To przypisanie jest zwykle wykonywane podczas inicjowania sterownika.

Ustawienie tego pola, FileX sprawia, **że FX_DRIVER_RELEASE_SECTORS** sterowników wskazujące, kiedy co najmniej jeden kolejny sektor stają się wolne.

### <a name="media-control-block-fx_media"></a>Blokuj kontrolkę multimediów FX_MEDIA

Cechy każdego otwartego nośnika w pliku FileX znajdują się w bloku sterowania nośnikami. Ta struktura jest zdefiniowana w ***pliku fx_api.h.***

Blok sterowania multimediami może być umieszczony w dowolnym miejscu w pamięci, ale najczęściej blok sterujący jest strukturą globalną przez zdefiniowanie jej poza zakresem dowolnej funkcji.

Lokalizowanie bloku sterującego w innych obszarach wymaga nieco więcej ostrożności, podobnie jak w przypadku całej pamięci przydzielanej dynamicznie. Jeśli blok sterujący jest przydzielany w ramach funkcji języka C, skojarzona z nim pamięć jest częścią stosu wątku wywołującego.

> [!WARNING]
>*Ogólnie rzecz biorąc, unikaj używania magazynu lokalnego dla bloków sterujących, ponieważ po zwracaniu funkcji zwalniana jest cała jej przestrzeń stosu zmiennych lokalnych — niezależnie od tego, czy jest nadal w użyciu!*

## <a name="fat121632-directory-description"></a>**Opis katalogu FAT12/16/32**

FileX obsługuje formaty nazw LFN (Long File Name) Windows 8.3 i LFN. Oprócz nazwy każdy wpis katalogu zawiera atrybuty wpisu, datę i czas ostatniej modyfikacji, początkowy indeks klastra oraz rozmiar w bajtach wpisu. Tabela 3 przedstawia zawartość i rozmiar wpisu katalogu FileX 8.3.

- **Nazwa katalogu**

    FileX obsługuje nazwy plików o rozmiarze od 1 do 255 znaków. Standardowe 8-znakowe nazwy plików są reprezentowane w pojedynczym wpisie katalogu na nośniku. Są one w lewo uzasadnione w polu nazwy katalogu i są puste w dolicie. Ponadto znaki ASCII, które składają się na nazwę, są zawsze oznaczane literami.

    Długie nazwy plików (LFN) są reprezentowane przez kolejne wpisy katalogu w odwrotnej kolejności, po których natychmiast następuje standardowa nazwa pliku 8.3. Utworzona nazwa 8.3 zawiera wszystkie opisowe informacje o katalogu skojarzone z nazwą. Tabela 4 przedstawia zawartość wpisów katalogu używanych do przechowywania informacji o długiej nazwie pliku, a tabela 5 przedstawia przykład 39-znakowej nazwy LFN, która wymaga łącznie czterech wpisów katalogu.

> [!IMPORTANT]
> *Stała **FX_MAX_LONG_NAME_LEN** zdefiniowana w **pliku fx_api.h** zawiera maksymalną długość obsługiwaną przez plik FileX.*

- **Rozszerzenie nazwy pliku katalogu**

    W przypadku standardowych nazw plików w wersji 8.3 plik FileX obsługuje również opcjonalne trzyznakowe *rozszerzenie nazwy pliku katalogu*. Podobnie jak w przypadku 8-znakowej nazwy pliku rozszerzenia nazw plików są uzasadnione w polu rozszerzenia nazwy pliku katalogu, są puste, a ich nazwa jest zawsze wyliowana na literę.

    **TABELA 3. Wpis katalogu FileX 8.3**

    |Przesunięcie|Pole|Liczba bajtów|
    |------------|-----------|------------|
    |0x00|Nazwa wpisu katalogu|8|
    |0x08|Rozszerzenie katalogu|3|
    |0x0B|Atrybuty|1|
    |0x0C|NT (wprowadzone przez długi format nazwy pliku i jest zarezerwowany dla NT [zawsze 0])|1|
    |0x0D|Godzina utworzenia w milisekundach (wprowadzona przez długi format nazwy pliku i reprezentuje liczbę milisekund podczas tworzenia pliku).|1|
    |0x0E|Godzina utworzenia w godzinach minut (wprowadzona przez długi format nazwy pliku i reprezentuje godzinę i minutę &amp; utworzenia pliku)|2|
    |0x10|Data utworzenia (wprowadzona przez długi format nazwy pliku i reprezentująca datę utworzenia pliku).|2|
    |0x12|Data ostatniego dostępu (wprowadzona przez długi format nazwy pliku i reprezentuje datę ostatniego dostępu do pliku).|2|
    |0x14|Uruchamianie klastra (tylko 16-bitowy górny limit fat-32)|2|
    |0x16|Czas modyfikacji|2|
    |0x18|Data modyfikacji|2|
    |0x1A|Klaster początkowy (niższe 16 bitów FAT-32, FAT-12 lub FAT-16)|2|
    |0x1C|Rozmiar pliku|4|


- **Atrybuty katalogu**

    Wpis pola atrybutu *katalogu* jedno bajtów zawiera szereg bitów, które określają różne właściwości wpisu katalogu. Definicje atrybutów katalogu są następujące:

    |Bit atrybutu|Znaczenie|
    |------------|-----------|
    |0x01|Wpis jest tylko do odczytu.|
    |0x02|Wpis jest ukryty.|
    |0x04|Wpis jest wpisem systemowym.|
    |0x08|Wpis jest etykietą woluminu|
    |0x10|Wpis jest katalogiem.|
    |0x20|Wpis został zmodyfikowany.|

    Ponieważ wszystkie bity atrybutów wzajemnie się wykluczają, może być ustawiony więcej niż jeden bit atrybutu na raz.

- **Czas katalogu**

    Dwu bajtowe *pole czasu katalogu* zawiera godziny, minuty i sekundy ostatniej zmiany wpisu określonego katalogu. Bity 15–11 zawierają godziny, bity od 10 do 5 zawierają minuty, a bity od 4 do 0 zawierają pół sekundy. Rzeczywiste sekundy są dzielone przez dwie, zanim zostaną zapisane w tym polu.

- **Data katalogu**

    Dwu *bajtowe* pole daty katalogu zawiera rok (przesunięcie od 1980 r.), miesiąc i dzień ostatniej zmiany wpisu określonego katalogu. Bity od 15 do 9 zawierają przesunięcie roku, bity od 8 do 5 zawierają przesunięcie miesiąca, a bity od 4 do 0 zawierają dzień.

- **Klaster początkowy katalogu**

    To pole zajmuje 2 bajty dla fat-12 i FAT-16. W przypadku fat-32 to pole zajmuje 4 bajty. To pole zawiera pierwszy numer klastra przydzielony do wpisu (podkatalog lub plik).

    > [!NOTE]
    > *Należy pamiętać, że plik FileX tworzy nowe pliki bez początkowego klastra (początkowe pole klastra równe zero), aby umożliwić użytkownikom opcjonalne przydzielanie ciągłej liczby klastrów dla nowo utworzonego pliku. *

- **Rozmiar pliku katalogu**

    Cztero bajtowe *pole rozmiaru* pliku *katalogu* zawiera liczbę bajtów w pliku. Jeśli wpis jest tak naprawdę podkatalog, pole rozmiaru ma wartość zero.

### <a name="long-file-name-directory"></a>Długi katalog nazw plików

- **Liczba porządkowa**

    Jedno bajtowe *pole porządkowe,* które określa numer wpisu LFN. Ponieważ wpisy LFN są pozycjonowane w odwrotnej kolejności, wartości porządkowe wpisów katalogu LFN składających się na jeden LFN zmniejszyć o jeden. Ponadto wartość porządkowa nazwy LFN bezpośrednio przed nazwą pliku 8.3 musi być jedna.

    **TABELA 4. Wpis katalogu długich nazw plików**

    | Przesunięcie | Pole | Liczba bajtów |
    |------------|-----------|------------|
    | 0x00 | Pole porządkowe | 1 |
    | 0x01 | Znak Unicode 1 | 2 |
    | 0x03 | Znak Unicode 2 | 2 |
    | 0x05 | Znak Unicode 3 | 2 |
    | 0x07 | Znak Unicode 4 | 2 |
    | 0x09 | Znak Unicode 5 | 2 |
    | 0x0B | Atrybuty LFN | 1 |
    | 0x0C | Typ LFN (zarezerwowane zawsze 0) | 1 |
    | 0x0D | LFN Checksum | 1 |
    | 0x0E | Znak Unicode 6 | 2 | 
    | 0x10 | Znak Unicode 7 | 2 |
    | 0x12 | Znak Unicode 8 | 2 |
    | 0x14 | Znak Unicode 9 | 2 |
    | 0x16 | Znak Unicode 10 | 2 |
    | 0x18 | Znak Unicode 11 | 2 |
    | 0x1A | Klaster LFN (nieużywany zawsze 0) | 2 |
    | 0x1C | Znak Unicode 12 | 2 |
    | 0x1e | Znak Unicode 13 | 2 |

- **Znak Unicode**

    Dwu bajtowe pola znaków *Unicode* są przeznaczone do obsługi znaków w wielu różnych językach. Standardowe znaki ASCII są reprezentowane przez znak ASCII przechowywany w pierwszym bajtze znaku Unicode, po którym następuje znak spacji.

- **Atrybuty LFN**

    Jedno bajtowe *atrybuty LFN* pole zawiera atrybuty, które identyfikują wpis katalogu jako wpis katalogu LFN. Jest to realizowane przez ustawienie atrybutów tylko do odczytu, systemowych, ukrytych i woluminów.

- **Typ LFN**

    Jedno bajtowe *pole typu LFN* jest zarezerwowane i zawsze ma 0.

- **LFN Checksum**

    Jedno bajtowe pole sumy kontrolnej *LFN* reprezentuje sumy kontrolne z 11 znaków skojarzonej nazwy pliku MSDOS 8.3. Ta liczba kontrolna jest przechowywana w każdym wpisie LFN, aby upewnić się, że wpis LFN odpowiada odpowiedniej nazwie pliku 8.3.

- **Klaster LFN**

    Dwu bajtowe *pole klastra LFN* jest nieużywane i zawsze ma 0.

    **TABELA 5. Wpisy katalogu składające się z 39-znakowego LFN**

    |Wpis|Znaczenie|
    |------------|-----------|
    |1|LFN Directory Entry 3|
    |2|LFN Directory Entry 2|
    |3|LFN Directory Entry 1|
    |4|8.3 Wpis katalogu (ttttt~n.xx)|

### <a name="exfat-directory-description"></a>exFAT Directory Description (Opis katalogu exFAT)

System plików exFAT inaczej przechowuje wpis katalogu i nazwę pliku. Wpis katalogu zawiera atrybuty wpisu, różne znaczniki czasu w momencie utworzenia, zmodyfikowania i dostępu do wpisu. Inne informacje, takie jak rozmiar pliku i klaster początkowy, są przechowywane w wpisie katalogu rozszerzenia usługi Stream, który bezpośrednio następuje po wpisie katalogu podstawowego. ExFAT obsługuje tylko format długich nazw plików (LFN). Który jest przechowywany w pliku nazwa katalogu wpis bezpośrednio następuje wpis katalogu rozszerzenia strumienia, jak pokazano w tabeli 2.

### <a name="exfat-file-directory-entry"></a>Wpis katalogu plików exFAT

Opis wpisu katalogu plików exFAT i jego zawartości znajduje się w poniższej tabeli i akapitach.

- **Typ wpisu**

    Pole typu wpisu wskazuje typ tego wpisu. W polu Wpis katalogu plików to pole musi być 0x85.

- **Liczba wpisów pomocniczych**

    Pole *liczba wpisów pomocniczych* wskazuje liczbę wpisów pomocniczych bezpośrednio po tym wpisie podstawowym. Wpisy pomocnicze skojarzone z wpisem katalogu plików obejmują jeden wpis katalogu rozszerzenia strumienia i jeden lub więcej wpisów katalogu nazwy pliku.

    **TABELA 6. Wpis katalogu plików exFAT**

    |Przesunięcie|Pole|Liczba bajtów|
    |----|-----------|-|
    |0x00|Typ wpisu|1|
    |0x01|Wpis pomocniczy|1|
    |0x02|Suma kontrolna|2|
    |0x04|Atrybuty pliku|2|
    |0x06|Zarezerwowane 1|2|
    |0x08|Utwórz sygnaturę czasową|4|
    |0x0C|Znacznik czasu ostatniej modyfikacji|4|
    |0x10|Sygnatura czasowa ostatniego dostępu|4|
    |0x14|Tworzenie przyrostu o 10 m|1|
    |0x15|Ostatni zmodyfikowany przyrost o 10 m|1|
    |0x16|Tworzenie przesunięcia czasu UTC|1|
    |0x17|Przesunięcie czasu UTC ostatniej modyfikacji|1|
    |0x18|Przesunięcie czasu UTC ostatniego dostępu|1|
    |0x19|Zarezerwowane 2|7|

- **Suma kontrolna**

    Pole *sumy kontrolnej* zawiera wartość sumy kontrolnej dla wszystkich wpisów w zestawie wpisów katalogu (wpis katalogu pliku i jego wpisy pomocnicze).

- **Atrybuty pliku**

    Wpis pola atrybuty jedno bajtowe zawiera szereg bitów, które określają różne właściwości wpisu katalogu. Definicja większości bitów atrybutów jest taka sama jak FAT 12/16/32. Definicje atrybutów katalogu są następujące:

    |Bit atrybutu|Znaczenie|
    |------------|-----------|
    |0x01| Wpis jest tylko do odczytu|
    |0x02|Wpis jest ukryty|
    |0x04|Wpis jest wpisem systemowym|
    |0x08|Wpis jest zarezerwowany|
    |0x10|Wpis jest katalogiem|
    |0x20|Wpis został zmodyfikowany|
    |Wszystkie inne bity|Zarezerwowany|

- **Reserved1**

    To pole powinno mieć wartość zero.

- **Utwórz sygnaturę czasową**

    Pole *tworzenia znacznika czasu,* łączące informacje z pola Utwórz *10ms* Inkrementacja, opisuje lokalną datę i czas utworzenia pliku lub katalogu.

- **Znacznik czasu ostatniej modyfikacji**

    Pole *znacznika czasu* ostatniej modyfikacji, łączące informacje z pola przyrostu o *10* m, opisuje lokalną datę i czas ostatniej modyfikacji pliku lub katalogu. Zapoznaj się z poniższymi uwagami na temat znaczników czasu.

- **Sygnatura czasowa ostatniego dostępu**

    Pole *znacznika czasu ostatniego* dostępu opisuje lokalną datę i czas ostatniego dostępu do pliku lub katalogu. Zapoznaj się z poniższymi uwagami na temat znaczników czasu.

- **Tworzenie przyrostu o 10 m**

    Utwórz *10ms* inkrementacja pola, łącząc informacje z tworzenie znacznika czasu pola, opisuje lokalną datę i czas pliku lub katalogu został utworzony.  Zapoznaj się z poniższymi uwagami na temat znaczników czasu.

- **Ostatni zmodyfikowany przyrost o 10 m**

    Ostatnie zmodyfikowane pole inkrementujące o *10ms,* które łączy informacje z pola znacznika czasu ostatniej modyfikacji, opisuje lokalną datę i czas ostatniej modyfikacji pliku lub katalogu.  Zapoznaj się z poniższymi uwagami na temat znaczników czasu.

- **Tworzenie przesunięcia czasu UTC**

    Pole *przesunięcia Create UTC* opisuje różnicę między czasem lokalnym a czasem UTC, kiedy plik lub katalog został utworzony. Zapoznaj się z poniższymi uwagami na temat znaczników czasu.

- **Przesunięcie czasu UTC ostatniej modyfikacji**

    Pole *przesunięcia czasu UTC* ostatniej modyfikacji opisuje różnicę między czasem lokalnym a czasem UTC, kiedy plik lub katalog został ostatnio zmodyfikowany. Zapoznaj się z poniższymi uwagami na temat znaczników czasu.

- **Przesunięcie czasu UTC ostatniego dostępu**

    Pole *przesunięcia czasu UTC* ostatniego dostępu opisuje różnicę między czasem lokalnym i czasem UTC, kiedy ostatnio uzyskano dostęp do pliku lub katalogu. Zapoznaj się z poniższymi uwagami na temat znaczników czasu.

- **Zarezerwowane 2**

    To pole powinno mieć wartość zero.

### <a name="notes-on-timestamps"></a>Uwagi dotyczące sygnatur czasowych

- **Wpis znacznika czasu** Pola znacznika czasu są interpretowane w następujący sposób:

- **Pola inkrementacja o 10 m** Wartość w polu inkrementacji 10ms zapewnia bardziej szczegółowy poziom szczegółowości do wartości znacznika czasu. Prawidłowe wartości to od 0 (0ms) do 199 (1990 ms).

     ![Pola inkrementacja o 10 m](./media/user-guide/10ms-increment-fields.png)

- **Pole przesunięcia CZASU UTC**

     ![Pole przesunięcia CZASU UTC](./media/user-guide/utc-offset-field.png)

- **Wartość przesunięcia**

    7-bitowa liczba całkowita ze podpisem reprezentuje przesunięcie w 15-minutowych przyrostach od czasu UTC.

- **Prawidłowe**

    Określa, czy wartość w polu przesunięcia jest prawidłowa. 0 wskazuje, że wartość w polu wartości przesunięcia jest nieprawidłowa. 1 wskazuje, że wartość jest prawidłowa.

### <a name="stream-extension-directory-entry"></a>Wpis katalogu rozszerzenia strumienia

Opis wpisu katalogu rozszerzenia usługi Stream i jego zawartości znajduje się w poniższej tabeli.

**TABELA 7. Wpis katalogu rozszerzenia strumienia**

|Przesunięcie|Pole| Liczba bajtów|
|------------|-----------|-------|
|0x00|Typ wpisu|1|
|0x01|Flagi|1|
|0x02|Zarezerwowane 1|1|
|0x03|Długość nazwy|1|
|0x04|Skrót nazwy|2|
|0x06|Zarezerwowane 2|2|
|0x08|Prawidłowa długość danych|8|
|0x10|Zarezerwowane 3|4|
|0x14|Pierwszy klaster|4|
|0x18|Długość danych|8|

- **Typ wpisu**

    Pole *typu* wpisu wskazuje typ tego wpisu. W przypadku wpisu katalogu rozszerzenia przesyłania strumieniowego to pole musi być 0xC0.

- **Flagi**

    To pole zawiera szereg bitów, które określają różne właściwości:
    
    |Bit flagi|Znaczenie    |
    |-----------------|-----------|
    |0x01            |To pole wskazuje, czy jest możliwa alokacja klastrów. To pole powinno mieć 1.|
    |0x02            |To pole wskazuje, czy skojarzone klastry są ciągłe. Wartość 0 oznacza, że wpis FAT jest prawidłowy, a plik FileX musi być zgodne z łańcuchem FAT. Wartość 1 oznacza, że wpis FAT jest nieprawidłowy, a klastry są ciągłe.|
    |Wszystkie inne bity    |Zarezerwowany.|

- **Zarezerwowane 1**

    To pole powinno mieć 0.

- **Długość nazwy**

    Pole *długości nazwy* zawiera długość ciągu Unicode w zbiorczo zawartych wpisach katalogu nazw plików. Wpisy katalogu nazw plików muszą być natychmiast zgodne z tym wpisem katalogu rozszerzenia strumienia.

- **Skrót nazwy**

    Pole *skrótu* nazwy jest wpisem 2-bajtowym zawierającym wartość skrótu nazwy pliku z up-cased. Wartość skrótu umożliwia szybsze wyszukiwania nazw plików/katalogów: jeśli wartości skrótu nie są zgodne, nazwa pliku skojarzona z tym wpisem nie jest dopasowana.

- **Zarezerwowane 2**

    To pole powinno mieć 0.

- **Prawidłowa długość danych**

    Prawidłowe *pole długości danych* wskazuje ilość prawidłowych danych w pliku.

- **Zarezerwowane 3**

    Ta zdjęła powinna mieć 0.

- **Pierwszy klaster**

    Pierwsze *pole klastra* zawiera indeks pierwszego klastra strumienia danych.

- **Długość danych**

    Pole *długość danych* zawiera łączną liczbę bajtów w przydzielonych klastrach. Ta wartość może być większa niż *prawidłowa długość danych,* ponieważ funkcja exFAT umożliwia wstępną alokację klastrów danych.

### <a name="root-directory"></a>Katalog główny

W formatach FAT 12- i 16-bitowych katalog główny znajduje się natychmiast po wszystkich sektorach FAT na nośniku i można go zlokalizować, sprawdzając ***fx_media_root_sector_start** _ w otwartych _ *FX_MEDIA** bloku sterowania.  Rozmiar katalogu głównego pod względem liczby wpisów katalogu (każdy 32 bajty) jest określany przez odpowiedni wpis w rekordzie rozruchowym nośnika.

Katalog główny w systemach FAT-32 i exFAT może się znaleźć w dowolnym miejscu w dostępnych klastrach. Jego lokalizacja i rozmiar są określane na podstawie rekordu rozruchowego po otwarciu nośnika. Po otwarciu nośnika można użyć ***fx_media_root_sector_start,*** aby znaleźć klaster początkowy katalogu głównego FAT-32 lub exFAT.

### <a name="subdirectories"></a>Podkatalogów

W systemie FAT istnieje dowolna liczba podkatalogów. Nazwa podkatalogu znajduje się we wpisie katalogu, podobnie jak nazwa pliku. Jednak specyfikacja atrybutu katalogu (0x10) jest ustawiona, aby wskazać, że wpis jest podkatalogiem, a rozmiar pliku jest zawsze zero.
Rysunek 3 pokazuje, jak wygląda typowa struktura podkatalogu dla nowego podkatalogu singlecluster o nazwie ***SAMPLE. DIR** _ z jednym plikiem o nazwie _*_FILE.TXT_**.
W większości przypadków podkatalogi są bardzo podobne do wpisów plików. Pierwsze pole klastra wskazuje pierwszy klaster połączonej listy klastrów. Po utworzeniu podkatalogu dwa pierwsze wpisy katalogu zawierają katalogi domyślne, czyli katalog "." i katalog "..". Katalog "." wskazuje sam podkatalog, a katalog ".", na katalog poprzedni lub nadrzędny.

### <a name="global-default-path"></a>Domyślna ścieżka globalna

Plik FileX udostępnia globalną ścieżkę domyślną dla nośnika. Ścieżka domyślna jest używana w dowolnym pliku lub usłudze katalogowej, która nie określa jawnie pełnej ścieżki.

Początkowo domyślny katalog globalny jest ustawiony na katalog główny nośnika. Może to zostać zmienione przez aplikację przez wywołanie ***fx_directory_default_set***.

Bieżącą ścieżkę domyślną nośnika można zbadać przez wywołanie ***** fx_directory_default_get _. Ta procedura zapewnia wskaźnik ciągu do domyślnego ciągu ścieżki utrzymywanego wewnątrz bloku kontrolki _ *FX_MEDIA**.

### <a name="local-default-path"></a>Ścieżka domyślna lokalna

FileX udostępnia również domyślną ścieżkę specyficzną dla wątku, która umożliwia różnym wątkom korzystanie z unikatowych ścieżek bez konfliktu. Struktura **FX_LOCAL_PATH** jest dostarczana przez aplikację podczas wywołań do fx_directory_local_path_set _ i ***_*_fx_directory_local_path_restore_** w celu zmodyfikowania ścieżki lokalnej dla wątku wywołującego.

Jeśli istnieje ścieżka lokalna, ścieżka lokalna ma pierwszeństwo przed globalną domyślną ścieżką nośnika. Jeśli ścieżka lokalna nie jest konfigurowana lub zostanie wyczyszona za pomocą ***usługi fx_directory_local_path_clear,*** ponownie zostanie użyta domyślna ścieżka globalna nośnika.

## <a name="file-description"></a>Opis pliku

Plik FileX obsługuje standardowe nazwy znaków 8.3 i długich plików z rozszerzeniami trzy znakami. Oprócz nazwy ASCII każdy wpis pliku zawiera atrybuty wpisu, datę i czas ostatniej modyfikacji, początkowy indeks klastra oraz rozmiar w bajtach wpisu.

### <a name="file-allocation"></a>Alokacja plików

FileX obsługuje standardowy schemat alokacji klastra w formacie FAT. Ponadto plik FileX obsługuje alokację przed klastrem ciągłych klastrów. W tym celu każdy plik FileX jest tworzony bez przydzielonych klastrów. Klastry są przydzielane w kolejnych żądaniach zapisu lub ***fx_file_allocate*** żądania wstępnego przydzielenia ciągłych klastrów.

Rysunek 4, "Przykład pliku FileX FAT-16", przedstawia plik o nazwie ***FILE.TXTz*** dwoma sekwencyjnymi klastrami przydzielonymi od klastra 101, rozmiarem 26 i alfabetem jako danymi w pierwszym klastrze danych pliku o numerze 101.

### <a name="file-access"></a>Dostęp do plików

Plik FileX może być otwierany wiele razy jednocześnie w celu uzyskania dostępu do odczytu. Plik można jednak otworzyć tylko raz w celu zapisu. Informacje używane do obsługi dostępu do plików znajdują się w bloku ***kontroli FX_FILE*** pliku.

> [!NOTE]
> *Należy pamiętać, że sterownik multimediów może dynamicznie ustawiać ochronę zapisu. W takim przypadku wszystkie żądania zapisu są odrzucane, a także próby otwarcia pliku do zapisu.*

### <a name="file-layout-in-exfat"></a>Układ pliku w exFAT

Projekt exFAT nie wymaga utrzymania łańcucha FAT dla pliku, jeśli dane są przechowywane w klastrach przejściowych. Bit *NoFATChain* we wpisie katalogu rozszerzenia strumienia wskazuje, czy należy użyć łańcucha FAT podczas odczytywania danych z pliku. Jeśli *ustawiono NoFATChain,* FileX odczytuje sekwencyjnie z klastra wskazanego w pierwszym klastrze w wpisie katalogu rozszerzenia strumienia. 

Z drugiej strony, jeśli *NoFATChain* jest jasne, FileX będzie podążać łańcuchem FAT w celu przechodzenia przez cały plik, podobnie jak łańcuch FAT w FAT12/16/32.

Rysunek 3 przedstawia dwa przykładowe pliki, jeden nie wymaga łańcucha FAT, a drugi wymaga łańcucha FAT.

## <a name="system-information"></a>Informacje o systemie

Informacje o systemie FileX obejmują śledzenie wystąpień otwartych nośników oraz utrzymywanie globalnej daty i czasu systemu.

![Plik z ciągłymi klastrami a plik wymagający łącza FAT](./media/user-guide/system-information.png)

**RYSUNEK 3. Plik z ciągłymi klastrami a plik wymagający łącza FAT**

Domyślnie data i godzina systemowa są ustawione na datę ostatniej wersji pliku FileX. Aby mieć dokładną datę i czas systemowy, aplikacja musi wywołać ***fx_system_time_set** _ i _ *_fx_system_date_set_** podczas inicjowania.

### <a name="system-date"></a>Data systemowa

Data systemu FileX jest zachowywana w globalnej ***_fx_system_date*** zmiennej. Bity 15–9 zawierają przesunięcie roku z 1980 r., bity od 8 do 5 zawierają przesunięcie miesiąca, a bity od 4 do 0 zawierają dzień. |

### <a name="system-time"></a>Czas systemowy

Czas systemowy PlikuX jest utrzymywany w globalnej ***_fx_system_time*** zmiennej. Bity 15–11 zawierają godziny, bity 10–5 zawierają minuty, a bity od 4 do 0 zawierają połowę sekund.

### <a name="periodic-time-update"></a>Okresowa aktualizacja czasu

Podczas inicjowania systemu plik FileX tworzy czasomierz aplikacji ThreadX w celu okresowego aktualizowania daty i czasu systemu. Szybkość, z jaką aktualizacja daty i godziny systemu jest określana przez dwie stałe używane przez ***_fx_system_initialize*** funkcji.

Stałe **FX_UPDATE_RATE_IN_SECONDS** i **FX_UPDATE_RATE_IN_TICKS** reprezentują ten sam okres czasu. Stała **FX_UPDATE_RATE_IN_TICKS** to liczba takt czasomierza ThreadX, która reprezentuje liczbę sekund określoną przez stałą **FX_UPDATE_RATE_IN_SECONDS**. Stała **FX_UPDATE_RATE_IN_SECONDS** określa liczbę sekund między poszczególnymi aktualizacjami czasu FileX. W związku z tym wewnętrzny czas PlikuX zwiększa się w interwałach **FX_UPDATE_RATE_IN_SECONDS**. Te stałe mogą być dostarczane podczas kompilacji fx_system_initialize _, lub deweloper może zmodyfikować wartości domyślne znalezione w ***pliku _*_fx_port.h_** wersji FileX.

Okresowy czasomierz FileX jest używany tylko do aktualizowania globalnej daty i godzin systemowej, która jest używana wyłącznie do oznaczania znacznikami czasu plików. Jeśli oznaczanie znacznikami czasu nie jest **konieczne,** po prostu zdefiniuj FX_NO_TIMER podczas kompilowania pliku **_fx_system_initialize.c,_** aby wyeliminować tworzenie czasomierza okresowego FileX.

![Przykład pliku FileX FAT-16](./media/user-guide/fat-16-file-example.png)

**RYSUNEK 4. Przykład pliku FileX FAT-16**
