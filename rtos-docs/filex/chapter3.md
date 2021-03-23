---
title: Rozdział 3 — funkcjonalne składniki platformy Azure RTO FileX
description: Ten rozdział zawiera opis o wysokiej wydajności osadzony system plików platformy Azure RTO FileX z perspektywy funkcjonalnej
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1e1e1a1dbd844d811c7ee3122113f28162639fb4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821438"
---
# <a name="chapter-3---functional-components-of-azure-rtos-filex"></a>Rozdział 3 — funkcjonalne składniki platformy Azure RTO FileX

Ten rozdział zawiera opis o wysokiej wydajności osadzony system plików platformy Azure RTO FileX z perspektywy funkcjonalnej.

## <a name="media-description"></a>Opis nośnika

FileX to osadzony system plików o wysokiej wydajności, który jest zgodny z formatem systemu plików FAT. FileX Wyświetla nośnik fizyczny jako tablicę sektorów logicznych. Sposób, w jaki te sektory są mapowane na bazowy nośnik fizyczny, jest określany przez sterownik we/wy połączony z nośnikiem FileX podczas wywołania ***fx_media_open*** .

### <a name="fat121632-logical-sectors"></a>FAT12/16/32 sektory logiczne

Dokładna organizacja sektorów logicznych nośnika jest określana na podstawie zawartości rekordu rozruchowego nośnika fizycznego. Ogólny układ sektorów logicznych nośnika przedstawiono na rysunku 1.

FileX sektory logiczne zaczynają się w logicznym sektorze 1, który wskazuje na pierwszy zastrzeżony sektor nośnika. Sektory zarezerwowane są opcjonalne, ale w przypadku korzystania z nich zazwyczaj zawierają informacje o systemie, takie jak kod rozruchowy.

### <a name="fat121632-media-boot-record"></a>Rekord rozruchowy FAT12/16/32

Dokładne przesunięcie sektora innych obszarów w widoku sektora logicznego nośnika jest uzyskiwane z zawartości *rekordu rozruchowego nośnika*. Lokalizacja rekordu rozruchowego jest zwykle w sektorze 0. Jeśli jednak nośnik ma *ukryte sektory*, przesunięcie do sektora rozruchowego musi je uwzględnić (znajdują się bezpośrednio przed sektorem rozruchu). Tabela 1 zawiera składniki rekordu rozruchowego nośnika, a składniki są opisane w akapitach.

- **Instrukcja skoku** Pole *instrukcji skoku* jest polem zawierającym trzy bajty, które reprezentuje instrukcję maszyny Intel x86 na potrzeby przeskoczenia procesora. Jest to starsze pole w większości sytuacji.

  ![Widok sektora logicznego multimediów FileX](./media/user-guide/filex-media-logical-sector-view.png)

  **RYSUNEK 1. Widok sektora logicznego multimediów FileX**

- **Nazwa producenta OEM** Pole *nazwy OEM* jest zarezerwowane dla producentów do umieszczenia ich nazwy lub nazwy urządzenia.
- **Bajtów na sektor** Pole *bajty na sektor* w rekordzie rozruchowym multimediów definiuje liczbę bajtów w każdym sektorze — podstawowy element nośnika.
- **Sektory na klaster** Pola *sektory na klaster* w rekordzie rozruchowym multimediów definiują liczbę sektorów przypisanych do klastra. Klaster jest podstawowym elementem alokacji w systemie plików zgodnym ze standardem FAT. Wszystkie informacje o pliku i podkatalogach są przydzielane z dostępnych klastrów nośnika zgodnie z opisem w tabeli alokacji plików (FAT).

    **TABELA 1. Rekord rozruchowy multimediów FileX**
    |Przesunięcie  |Pole  |Liczba bajtów|
    |----------|-----------|------------|
    |0x00|Instrukcje skoku (E9, XX, XX lub EB, XX, 90)|3|
    |0x03|Nazwa producenta OEM|8|
    |0x0B|Bajtów na sektor|2|
    |0x0D|Sektory na klaster|1|
    |0x0E|Liczba zarezerwowanych sektorów|2|
    |0x10|Liczba tłuszczów|1|
    |0x11|Rozmiar katalogu głównego|2|
    |0x13|Liczba sektorów FAT-12 &amp; FAT-16|2|
    |0x15|Typ nośnika|1|
    |0x16|Liczba sektorów na system plików FAT|2|
    |0x18|Sektory na śledzenie|2|
    |0x1A|Liczba główek|2|
    |0x1C|Liczba ukrytych sektorów|4|
    |0x20|Liczba sektorów-FAT-32|4|
    |0x24|Sektory na tłuszcz (FAT-32)|4|
    |0x2C|Klaster katalogów głównych|4|
    |0x3E|Kod rozruchowy systemu|448
    |0x1FE|0x55AA|2|

- **Zarezerwowane sektory** Pole *sektory zarezerwowane* w rekordzie rozruchowym multimediów definiuje liczbę sektorów zarezerwowanych między rekordem rozruchowym a pierwszym sektorem obszaru FAT. W większości przypadków ten wpis jest równy zero.
- **Liczba tłuszczów** *Liczba wpisów FATS* w rekordzie rozruchowym multimediów definiuje liczbę tłuszczów w nośniku. W nośniku musi znajdować się co najmniej jeden FAT. Dodatkowe tłuszcze są tylko duplikatami kopii podstawowego (pierwszego) systemu FAT i są zwykle używane przez oprogramowanie diagnostyczne lub odzyskiwania.
- **Rozmiar katalogu głównego** Wpis *rozmiaru katalogu głównego* w rekordzie rozruchowym multimediów definiuje stałą liczbę wpisów w katalogu głównym nośnika. To pole nie ma zastosowania do podkatalogów i katalogu głównego FAT-32, ponieważ są one przydzieleni z klastrów na nośniku.
- **Liczba sektorów FAT-12 & FAT-16** Pole *liczba sektorów* w rekordzie rozruchowym multimediów zawiera łączną liczbę sektorów na nośniku. Jeśli to pole ma wartość zero, Łączna liczba sektorów jest zawarta w polu *liczba sektorów FAT-32* znajdujących się w dalszej części rekordu rozruchowego.
- **Typ nośnika** Pole *Typ nośnika* służy do identyfikowania typu nośnika obecnego dla sterownika urządzenia. To pole jest starsze.
- **Sektory na system plików FAT** *Sektory na system plików FAT* zapisane w rekordzie rozruchowym multimediów zawierają liczbę sektorów skojarzonych z każdym tłuszczem w obszarze FAT. Liczba sektorów FAT musi być wystarczająco duża, aby można było uwzględnić maksymalną możliwą liczbę klastrów, które mogą być przydzieloną na nośniku.
- **Sektory na śledzenie** Pola *sektory na śledzenie* w rekordzie rozruchowym multimediów definiują liczbę sektorów na ścieżkę. Jest to zazwyczaj przydatne tylko w przypadku rzeczywistego nośnika typu dyskowego. Urządzenia FLASH nie używają tego mapowania.
- **Liczba główek** *Liczba główek* w rekordzie rozruchowym multimediów definiuje liczbę głowic na nośniku. Jest to zazwyczaj przydatne tylko w przypadku rzeczywistego nośnika typu dyskowego. Urządzenia FLASH nie używają tego mapowania.
- **Ukryte sektory** Pole *ukryte sektory* w rekordzie rozruchowym multimediów definiuje liczbę sektorów przed rekordem rozruchowym. To pole jest obsługiwane w bloku sterowania **FX_MEDIA** i należy je uwzględnić w sterownikach we/wy FileX we wszystkich żądaniach odczytu i zapisu wykonywanych przez FileX.
- **Liczba sektorów FAT-32** Pole *liczba sektorów* w rekordzie rozruchowym multimediów jest prawidłowe tylko wtedy, gdy w polu dwubajtowa *liczba sektorów* jest równa zero. W takim przypadku pole cztery-bajtowe zawiera liczbę sektorów na nośniku.
- **Sektory na tłuszcz (FAT-32)** Pole *sektory na tłuszcz (FAT-32)* jest prawidłowe tylko w formacie tłuszczu-32 i zawiera liczbę sektorów przyznanych dla każdego tłuszczu nośnika.
- **Klaster katalogów głównych** Pole *klaster katalogu głównego* jest prawidłowe tylko w formacie tłuszczu-32 i zawiera początkowy numer klastra katalogu głównego.
- **Kod rozruchowy systemu** Pole *Kod rozruchowy systemu* to obszar, w którym przechowywana jest mała część kodu rozruchowego. Obecnie w większości urządzeń jest to pole starsze.
- **0X55AA podpisu** Pole *podpisu* jest wzorcem danych używanym do identyfikowania rekordu rozruchowego. Jeśli to pole jest nieobecne, rekord rozruchowy jest nieprawidłowy.

### <a name="exfat"></a>exFAT

Maksymalny rozmiar pliku w systemie FAT32 to 4 GB, co ogranicza szerokie wdrażanie plików multimedialnych o wysokiej rozdzielczości. Domyślnie system FAT32 obsługuje nośniki magazynu o pojemności do 32 GB. Dzięki zwiększeniu wydajności kart Flash i SD system FAT32 jest mniej wydajny w zarządzaniu dużymi woluminami. exFAT zaprojektowano w celu pokonania tych ograniczeń. exFAT obsługuje rozmiar pliku do jednego rozmiaru Exabyte (EB), czyli około 1 000 000 000 GB. Kolejną istotną różnicą między exFAT i FAT32 jest to, że exFAT korzysta z mapy bitowej do zarządzania dostępnymi miejscami w woluminie, co sprawia, że exFAT bardziej wydajne Znajdowanie dostępnego miejsca podczas zapisywania danych do pliku. W przypadku pliku przechowywanego w ciągłych klastrach exFAT eliminuje przechodzenie łańcucha FAT w celu znalezienia wszystkich klastrów, co zwiększa efektywność podczas uzyskiwania dostępu do dużych plików. exFAT jest wymagany w przypadku usługi Flash Storage i kart SD o rozmiarze większym niż 32 GB.

### <a name="exfat-logical-sectors"></a>exFAT sektory logiczne

Ogólny układ sektorów logicznych nośnika w exFAT przedstawiono na rysunku 2. W exFAT blok rozruchowy i obszar FAT należą do obszaru systemowego. Pozostałe klastry są obszarami użytkownika. Mimo że nie jest to wymagane, standard exFAT zaleca, aby mapa bitowa alokacji była umieszczona na początku obszaru użytkownika, a następnie w tabeli w górę i w katalogu głównym.

### <a name="exfat-media-boot-record"></a>Rekord rozruchowy multimediów exFAT

Zawartość rekordu rozruchowego multimediów w programie exFAT różni się od tych w FAT12/16/32. Są one wymienione w tabeli 2. Aby uniknąć nieporozumień, obszar między 0x0B i 0x40, który zawiera różne parametry nośnika w FAT12/16/32 jest oznaczony jako *zarezerwowany* w exFAT. Ten zarezerwowany obszar musi być zaprogramowany przez zero, unikając wszelkich błędnych interpretacji rekordu rozruchowego multimediów.

![exFAT sektory logiczne](./media/user-guide/exfat-logical-sectors.png)

**RYSUNEK 2. exFAT sektory logiczne**

- **Instrukcja skoku** Pole *instrukcji skoku* jest polem zawierającym trzy bajty, które reprezentuje instrukcję maszyny Intel x86 na potrzeby przeskoczenia procesora. Jest to starsze pole w większości sytuacji.

    **TABELA 2. Rekord rozruchowy multimediów exFAT**

    |Przesunięcie  |Pole  |Liczba bajtów|
    |----------|-----------|------------|
    |0x00|Instrukcja skoku|3|
    |0x03|Nazwa systemu plików|8|
    |0x0B|Zarezerwowany|53|
    |0x40|Przesunięcie partycji|8|
    |0x48|Długość woluminu|8|
    |0x50|Przesunięcie systemu FAT|4|
    |0x54|Długość tłuszczu|4|
    |0x58|Przesunięcie sterty klastra|4|
    |0x5C|Liczba klastrów|4|
    |0x60|Pierwszy klaster katalogu głównego|4|
    |0x64|Numer seryjny woluminu|4|
    |0x68|Poprawka systemu plików|2|
    |0x6A|Flagi woluminu|2|
    |0x6C|Przesunięcie bajtów na sektor|1|
    |0x6D|Przesunięcia sektorów na klaster|1|
    |0x6E|Liczba tłuszczów|1|
    |0x6F|Wybór dysku|1|
    |0x70|Procent użycia|7|
    |0x71|Zarezerwowany|1|
    |0x78|Kod rozruchowy|390|
    |0x1FE|Podpis rozruchowy|2|

- **Nazwa systemu plików** W przypadku exFAT pole *Nazwa systemu plików* musi mieć wartość "exFAT", a następnie trzy białe znaki.
- **Zarezerwowane** Zawartość pola *zastrzeżonego* musi wynosić zero. Ten region nakłada się na rekordy rozruchowe w FAT12/16/32. Wprowadzenie tego obszaru w ten sposób nie pozwala na uniknięcie nieprawidłowego interpretowania tego woluminu przez systemy plików.
- **Przesunięcie partycji** Pole *przesunięcia partycji* wskazuje początkową tę partycję.
- **Długość woluminu** Pole *Długość woluminu* określa rozmiar (w liczbie sektorów) tej partycji.
- **Przesunięcie systemu FAT** Pole *przesunięcie systemu FAT* definiuje numer sektora początkowego względem początku tej partycji tabeli FAT dla tej partycji.
- **Długość tłuszczu** Pole *Długość tłuszczu* definiuje rozmiar tabeli FAT, w liczbie sektorów.
- **Przesunięcie sterty klastra** Pole *przesunięcie sterty klastra* definiuje numer sektora początkowego względem początku partycji w stosie klastra. Sterta klastra to obszar, w którym są przechowywane informacje o katalogach i dane plików.
- **Liczba klastrów** Pole *liczba klastrów* definiuje liczbę klastrów, których dotyczy ta partycja.
- **Pierwszy klaster katalogu głównego** *Pierwszy klaster w polu Katalog główny* definiuje początkową lokalizację katalogu głównego, który zaleca się bezpośrednio po mapie bitowej alokacji i tabeli w przypadku tworzenia wielkości liter.
- **Numer seryjny woluminu** Pole *numer seryjny woluminu* określa numer seryjny dla tej partycji.
- **Poprawka systemu plików** Pole *poprawka systemu plików* definiuje wersję główną i pomocniczą exFAT.
- **Flagi woluminu** Pole *flagi woluminu* zawiera flagi wskazujące stan tego woluminu.
- **Przesunięcie bajtów na sektor** Pole *przesunięcie bajtów na sektor* definiuje liczbę bajtów na sektor w log2 — (n), gdzie n to liczba bajtów na sektor. Na przykład w karcie SD rozmiar sektora to 512 bajtów. W związku z tym to pole powinno mieć wartość 9 (log2 — (512) = 9).
- **Przesunięcia sektorów na klaster** Pole *przesunięcia sektorów na klaster* definiuje liczbę sektorów w klastrze, w log2 — (n), gdzie n jest liczbą sektorów na klaster.
- **Liczba tłuszczów** Pole *Liczba FATs* definiuje liczbę tabel FAT w tej partycji. W przypadku exFAT wartość jest zalecana dla jednej tabeli FAT równa 1.
- **Wybór dysku** Pole *wyboru sterownika* definiuje rozszerzony numer dysku int 13h.
- **Procent użycia** Pole *procent użycia* definiuje wartość procentową klastrów w stercie klastra jest przydzielana. Prawidłowe wartości należą do zakresu od 0 do 100 włącznie.
- **Zarezerwowane** To pole jest zarezerwowane do użytku w przyszłości.
- **Kod rozruchowy** Pole *Kod rozruchowy* to obszar służący do przechowywania niewielkiej części kodu rozruchowego. Obecnie w większości urządzeń jest to pole starsze.
- **0X55AA podpisu** Pole *podpis rozruchowy* jest wzorcem danych używanym do identyfikowania rekordu rozruchowego. Jeśli to pole jest nieobecne, rekord rozruchowy jest nieprawidłowy.

### <a name="file-allocation-table-fat"></a>Tabela alokacji plików (FAT)

*Tabela alokacji plików (FAT)* rozpoczyna się po zarezerwowanych sektorach na nośniku. Obszar tłuszczu jest zasadniczo tablicą 12-bitowego, 16-bitowego lub 32-bitowego wpisów, które określają, czy ten klaster jest przydzielony lub jest częścią łańcucha klastrów składających się z podkatalogu lub pliku. Rozmiar każdego wpisu systemu FAT jest określany przez liczbę klastrów, które muszą być reprezentowane. Jeśli liczba klastrów (pochodzących od łącznego sektora podzielone przez sektory na klaster) jest mniejsza lub równa 4 086, używane są 12-bitowe wpisy FAT. Jeśli łączna liczba klastrów jest większa niż 4 086 i jest mniejsza niż 65 525, używane są 16-bitowe wpisy FAT. W przeciwnym razie, jeśli łączna liczba klastrów jest większa lub równa 65 525, są używane wartości 32-bitowe FAT lub exFAT.

W przypadku FAT12/16/32 tabela FAT nie tylko utrzymuje łańcuch klastrów, ale również zawiera informacje dotyczące alokacji klastra: czy klaster jest dostępny. W exFAT informacje o alokacji klastra są obsługiwane przez wpis w katalogu mapy bitowej alokacji. Każda partycja ma własną mapę bitową alokacji. Rozmiar mapy bitowej jest wystarczająco duży, aby pokryć wszystkie dostępne klastry. Jeśli klaster jest dostępny do alokacji, odpowiedni bit w mapie bitowej alokacji ma wartość 0. W przeciwnym razie bit jest ustawiony na 1. W przypadku pliku, który zajmuje kolejne klastry, exFAT nie wymaga łańcucha FAT do śledzenia wszystkich klastrów. Jednak w przypadku pliku, który nie zajmuje kolejnych klastrów, nadal trzeba utrzymywać łańcuch systemu plików FAT.

### <a name="fat-entry-contents"></a>Zawartość wpisu FAT

Pierwsze dwa wpisy w tabeli FAT nie są używane i zazwyczaj mają poniższą zawartość.

|Wpis FAT |12-bitowy system plików FAT|16-bitowy system plików FAT|32 — bit FAT| exFAT|
|----------|-----------|------------|-------|------|
|Wpis 0|0x0F0|0x00F0|0x000000F0|0xF8FFFFFF|
|Wpis 1|0xFFF|0xFFFF|0x0FFFFFFF|0xFFFFFFFF|

Numer wpisu systemu FAT 2 reprezentuje pierwszy klaster w obszarze danych nośnika. Zawartość każdego wpisu klastra określa, czy jest to wolna czy część połączonej listy klastrów przyznanych dla pliku lub podkatalogu. Jeśli wpis klastra zawiera inny prawidłowy wpis klastra, zostanie przydzielony klaster, a jego wartość wskazuje następny klaster przydzielony w łańcuchu klastra.

Możliwe wpisy klastra są zdefiniowane w następujący sposób.
|Znaczenie|12-bitowy system plików FAT|16-bitowy system plików FAT|32 — bit FAT| exFAT|
|----------|-----------|------------|-------|------|
|Bezpłatny klaster|0x000|0x0000|0x00000000|0x00000000|
|Nieużywane|0x001|0x0001|0x00000001|0x00000001|
|Zarezerwowany|0xFF0-FF6|0xFFF0-FFF6|0x0FFFFFF0-6|ClusterCounter + 2 do 0xFFFFFFF6|
|Zły klaster|0xFF7|0xFFF7|0x0FFFFFF7|0xFFFFFFF7|
|Zarezerwowany| - | - | - | 0xFFFFFFF8-E|
|Ostatni klaster| 0xFF8 — FFF| 0xFFF8 — FFFF| 0x0FFFFFF8 — F| 0xFFFFFFFF|
|Link klastra| 0x002-0xFEF| 0x0002-FFEF| 0x2 — 0x0FFFFFEF | 0x2-ClusterCount + 1|

Ostatni klaster w przydzielonym łańcuchu klastrów zawiera ostatnią wartość klastra (zdefiniowaną powyżej). Pierwszy numer klastra znajduje się w wpisie katalogu pliku lub podkatalogu.

### <a name="internal-logical-cache"></a>Wewnętrzna logiczna pamięć podręczna

FileX utrzymuje *ostatnio używaną* pamięć podręczną sektorów logicznych dla każdego otwartego nośnika. Maksymalny rozmiar pamięci podręcznej sektora logicznego jest definiowany przez stałą **FX_MAX_SECTOR_CACHE** i znajduje się w **_fx_api. h_**. Jest to pierwszy czynnik określający rozmiar wewnętrznej pamięci podręcznej sektora logicznego.

Drugim czynnikiem decydującym o rozmiarze pamięci podręcznej sektora logicznego jest ilość pamięci dostarczanej do wywołania ***fx_media_open** _ przez aplikację. Za mało pamięci dla co najmniej jednego sektora logicznego. Jeśli wymagane są więcej niż _ *FX_MAX_SECTOR_CACHE** sektory logiczne, stała musi zostać zmieniona w **_fx_api. h_** , a cała biblioteka FileX musi zostać odbudowana.

> [!IMPORTANT]
> *Każdy otwarty nośnik w programie FileX może mieć inny rozmiar pamięci podręcznej w zależności od pamięci podanej podczas otwartego wywołania.*

### <a name="write-protect"></a>Ochrona przed zapisem

FileX udostępnia sterownik aplikacji możliwość dynamicznego ustawiania ochrony przed zapisem na nośniku. Jeśli wymagana jest ochrona przed zapisem, zestaw sterowników ustawia FX_TRUE pole *fx_media_driver_write_protect* w skojarzonej strukturze FX_MEDIA. Po ustawieniu wszystkie próby modyfikacji nośnika przez aplikację są odrzucane, a także próbuje otworzyć pliki do zapisu. Sterownik może również wyłączyć ochronę przed zapisem przez wyczyszczenie tego pola.

### <a name="free-sector-update"></a>Aktualizacja sektora wolnego

FileX zapewnia mechanizm do informowania sterownika aplikacji, gdy sektory nie są już używane. Jest to szczególnie przydatne w przypadku menedżerów pamięci FLASH zarządzających wszystkimi sektorami logicznymi używanymi przez FileX.

Jeśli wymagane jest powiadomienie o wolnych sektorach, sterownik aplikacji ustawia FX_TRUE pole *fx_media_driver_free_sector_update* w skojarzonej strukturze FX_MEDIA. To przypisanie jest zazwyczaj wykonywane podczas inicjowania sterownika.

Ustawienie tego pola FileX powoduje wywołanie sterownika **FX_DRIVER_RELEASE_SECTORS** wskazujące, kiedy jeden lub więcej kolejnych sektorów staje się bezpłatny.

### <a name="media-control-block-fx_media"></a>FX_MEDIA bloku sterowania nośnikami

Właściwości każdego otwartego nośnika w FileX są zawarte w bloku kontroli nośnika. Ta struktura jest zdefiniowana w pliku ***fx_api. h***.

Blok sterowania nośnikami może znajdować się w dowolnym miejscu w pamięci, ale najczęściej jest to, że formant blokuje strukturę globalną poprzez definiowanie jej poza zakresem dowolnej funkcji.

Lokalizowanie bloku sterowania w innych obszarach wymaga nieco więcej informacji, podobnie jak wszystkie dynamicznie przydzieloną pamięć. Jeśli blok sterowania jest przypisywany w ramach funkcji języka C, skojarzona z nim pamięć jest częścią stosu wywołującego wątku.

> [!WARNING]
>*Ogólnie rzecz biorąc, należy unikać używania lokalnego magazynu dla bloków kontroli, ponieważ po powrocie funkcji jest wydawana cała jego przestrzeń na stosie zmiennych lokalnych — bez względu na to, czy jest on nadal używany.*

## <a name="fat121632-directory-description"></a>**Opis usługi FAT12/16/32**

FileX obsługuje 8,3 zarówno formaty nazw, jak i LFN (Windows Long File Name). Oprócz nazwy, każdy wpis katalogu zawiera atrybuty wpisu, godzinę ostatniej modyfikacji i datę, początkowy indeks klastra oraz rozmiar w bajtach wpisu. W tabeli 3 przedstawiono zawartość i rozmiar wpisu katalogu FileX 8,3.

- **Nazwa katalogu**

    FileX obsługuje nazwy plików o wielkości od 1 do 255 znaków. Standardowe osiem znaków nazwy plików są reprezentowane w pojedynczym wpisie katalogu na nośniku. Są one wyrównane do pola Nazwa katalogu i są puste. Ponadto znaki ASCII składające się na nazwę są zawsze pisane wielkimi literami.

    Długie nazwy plików (LFNs) są reprezentowane przez kolejne wpisy katalogu w odwrotnej kolejności, a następnie bezpośrednio przez standardową nazwę pliku 8,3. Utworzona nazwa 8,3 zawiera wszystkie zrozumiałe informacje o katalogu skojarzone z nazwą. W tabeli 4 przedstawiono zawartość wpisów w katalogu użytych do przechowywania informacji o długich nazwach plików, a w tabeli 5 przedstawiono przykład 39-znakowej LFN, który wymaga łącznie czterech wpisów w katalogu.

> [!IMPORTANT]
> *Stała **FX_MAX_LONG_NAME_LEN**, zdefiniowana w **fx_api. h**, zawiera maksymalną długość obsługiwaną przez FileX.*

- **Rozszerzenie nazwy pliku**

    W przypadku standardowych nazw plików 8,3 FileX również obsługuje opcjonalne *rozszerzenie nazwy pliku* z trzema znakami. Podobnie jak osiem znaków nazwa pliku, rozszerzenia nazw plików są wyrównane do pola rozszerzenie nazwy pliku, puste uzupełnione i zawsze pisane wielkimi literami.

    **TABELA 3. Wpis w katalogu FileX 8,3**

    |Przesunięcie|Pole|Liczba bajtów|
    |------------|-----------|------------|
    |0x00|Nazwa wpisu katalogu|8|
    |0x08|Rozszerzenie katalogu|3|
    |0x0B|Atrybuty|1|
    |0x0C|NT (wprowadzony przez format długiej nazwy pliku i jest zarezerwowany dla NT [zawsze 0])|1|
    |0x0D|Czas utworzenia w milisekundach (wprowadzony przez format długiej nazwy pliku i reprezentuje liczbę milisekund czasu utworzenia pliku).|1|
    |0x0E|Czas utworzenia w godzinach &amp; (w minutach) (wprowadzony przez długi format nazwy pliku i reprezentuje godzinę i minutę utworzenia pliku)|2|
    |0x10|Data utworzenia (wprowadzona w formacie długiej nazwy pliku i reprezentuje datę utworzenia pliku).|2|
    |0x12|Data ostatniego dostępu (wprowadzona w formacie długiej nazwy pliku i reprezentuje datę ostatniego dostępu do pliku).|2|
    |0x14|Uruchamianie klastra (Wielka część 16 bitów FAT-32)|2|
    |0x16|Godzina modyfikacji|2|
    |0x18|Data modyfikacji|2|
    |0x1A|Uruchamianie klastra (Obniż 16 bitów FAT-32 lub FAT-12 lub FAT-16)|2|
    |0x1C|Rozmiar pliku|4|


- **Atrybuty katalogu**

    Wpis pola *atrybutu katalogu* jednobajtowego zawiera serię bitów, która określa różne właściwości wpisu katalogu. Definicje atrybutów katalogu są następujące:

    |Atrybut bit|Znaczenie|
    |------------|-----------|
    |0x01|Wpis jest tylko do odczytu.|
    |0x02|Wpis jest ukryty.|
    |0x04|Wpis jest wpisem systemowym.|
    |0x08|Wpis jest etykietą woluminu|
    |0x10|Wpis jest katalogiem.|
    |0x20|Wpis został zmodyfikowany.|

    Ponieważ wszystkie bity atrybutów wykluczają się wzajemnie, w danej chwili może istnieć więcej niż jeden bit atrybutu.

- **Czas katalogu**

    Pole dwubajtowego *czasu katalogu* zawiera godziny, minuty i sekundy ostatniej zmiany do określonego wpisu katalogu. Bity od 15 do 11 zawierają godziny, bity 10, jeśli 5 zawiera minuty, a bity 4, jeśli 0 zawierają połowę sekund. Rzeczywista liczba sekund jest dzielona przez dwa przed zapisaniem w tym polu.

- **Data katalogu**

    Pole *daty katalogu* dwubajtowego zawiera rok (przesunięcie od 1980), miesiąc i dzień ostatniej zmiany do określonego wpisu katalogu. Bity od 15 do 9 zawierają przesunięcie roku, bity od 8 do 5 zawierają przesunięcie miesiąca, a bity od 4 do 0 zawierają dzień.

- **Początkowy klaster katalogu**

    To pole zajmuje 2 bajty dla plików FAT-12 i FAT-16. W przypadku systemu FAT-32 to pole zajmuje 4 bajty. To pole zawiera numer pierwszego klastra przydzieloną do wpisu (podkatalog lub plik).

    > [!NOTE]
    > * Należy zauważyć, że FileX tworzy nowe pliki bez wstępnego klastra (początkowy pole klastra równe zero), aby umożliwić użytkownikom opcjonalne przydzielanie ciągłej liczby klastrów dla nowo utworzonego pliku. *

- **Rozmiar pliku katalogu**

    Pole *rozmiar pliku* z czterema bajtami zawiera liczbę bajtów *w pliku.* Jeśli wpis jest w rzeczywistości podkatalogu, pole size ma wartość zero.

### <a name="long-file-name-directory"></a>Katalog długich nazw plików

- **Liczba porządkowa**

    Jednobajtowe pole *porządkowe* , które określa numer wpisu LFN. Ponieważ wpisy LFN są umieszczane w kolejności odwrotnej, wartości porządkowe wpisów w katalogu LFN składających się z jednego LFNu zmniejszają o jeden. Ponadto wartość porządkowa LFN bezpośrednio przed nazwą pliku 8,3 musi być taka.

    **TABELA 4. Wpis katalogu długich nazw plików**

    |Przesunięcie|Pole|Liczba bajtów|
    |------------|-----------|------------|
    0x00|Pole porządkowe|1|
    0x01|Unicode — znak 1|2|
    0x03|Unicode — znak 2|2|
    0x05|Unicode — znak 3|2|
    0x07|Unicode — znak 4|2|
    0x09|Znak Unicode 5|2|
    0x0B|LFN — atrybuty|1|
    0x0C|Typ LFN (zarezerwowane zawsze 0)|1|
    0x0D|Suma kontrolna LFN|1|
    0x0E|Unicode — znak 6|2|
    0x10|Znak Unicode 7|2|
    0x12|Znak Unicode 8|2|
    0x14|Unicode — znak 9|2|
    0x16|Unicode — znak 10|2|
    0x18|Znak Unicode 11|2|
    0x1A|Klaster LFN (nieużywany zawsze 0)|2|
    0x1C|Znak Unicode 12|2|
    0x1E|Znak Unicode |13|2|

- **Znak Unicode**

    Dwubajtowe pola *znaków Unicode* są przeznaczone do obsługi znaków w wielu różnych językach. Standardowe znaki ASCII są reprezentowane przy użyciu znaku ASCII przechowywanego w pierwszym bajcie znaku Unicode, po którym następuje znak spacji.

- **LFN — atrybuty**

    Jednobajtowe pole *atrybutów LFN* zawiera atrybuty, które identyfikują wpis katalogu jako wpis katalogu LFN. W tym celu należy mieć ustawioną opcję tylko do odczytu, system, ukryty i wolumin.

- **Typ LFN**

    Pole *typu LFN* z jednym bajtem jest zarezerwowane i ma zawsze wartość 0.

- **Suma kontrolna LFN**

    Pole *sumy kontrolnej LFN* z jednym bajtem przedstawia sumę kontrolną 11 znaków skojarzonej nazwy pliku Msdos 8,3. Ta suma kontrolna jest przechowywana w każdym wpisie LFN, aby pomóc w zapewnieniu, że wpis LFN odpowiada odpowiedniej nazwie pliku 8,3.

- **Klaster LFN**

    Pole wielobajtowego *klastra LFN* jest nieużywane i ma zawsze wartość 0.

    **TABELA 5. Wpisy katalogu składające się z 39 znaków LFN**

    |Wpis|Znaczenie|
    |------------|-----------|
    |1|LFN — wpis w katalogu 3|
    |2|LFN — wpis w katalogu 2|
    |3|Wpis w katalogu LFN 1|
    |4|Wpis w katalogu 8,3 (ttttt ~ n. XX)|

### <a name="exfat-directory-description"></a>Opis katalogu exFAT

System plików exFAT zapisuje wpis w katalogu i nazwę pliku w różny sposób. Wpis katalogu zawiera atrybuty wpisu, różne sygnatury czasowe podczas tworzenia, modyfikowania i uzyskiwania dostępu do wpisu. Inne informacje, takie jak rozmiar pliku i początkowy klaster, są przechowywane w pozycji katalog rozszerzenia strumienia, która jest bezpośrednio zgodna z wpisem w katalogu podstawowym. exFAT obsługuje tylko format nazw Long File Name (LFN). który jest przechowywany w katalogu nazw plików bezpośrednio po wpisie katalogu rozszerzenia strumienia, jak pokazano w tabeli 2.

### <a name="exfat-file-directory-entry"></a>exFAT wpis w katalogu plików

Opis wpisu katalogu plików exFAT i jego zawartości znajdują się w poniższej tabeli i ustępach.

- **Typ wpisu**

    Pole Typ wpisu wskazuje typ tego wpisu. W przypadku wpisu katalogu plików to pole musi być 0x85.

- **Dodatkowa liczba wpisów**

    Pole *Liczba wejść dodatkowych* wskazuje liczbę wpisów pomocniczych bezpośrednio po tym wpisie głównym. Wpisy pomocnicze skojarzone z wpisem w katalogu plików obejmują jeden wpis katalogu rozszerzenia strumienia i co najmniej jedną pozycję katalogu nazw plików.

    **TABELA 6. exFAT wpis w katalogu plików**

    |Przesunięcie|Pole|Liczba bajtów|
    |----|-----------|-|
    |0x00|Typ wpisu|1|
    |0x01|Wpis pomocniczy|1|
    |0x02|Suma kontrolna|2|
    |0x04|Atrybuty pliku|2|
    |0x06|Zarezerwowane 1|2|
    |0x08|Utwórz sygnaturę czasową|4|
    |0x0C|Sygnatura czasowa ostatniej modyfikacji|4|
    |0x10|Sygnatura czasowa ostatniego dostępu|4|
    |0x14|Utwórz przyrost 10 ms|1|
    |0x15|Ostatni zmodyfikowany 10 ms przyrostu|1|
    |0x16|Utwórz przesunięcie czasu UTC|1|
    |0x17|Przesunięcie czasu UTC ostatniej modyfikacji|1|
    |0x18|Przesunięcie czasu UTC ostatniego dostępu|1|
    |0x19|Zarezerwowane 2|7|

- **Suma**

    Pole *sumy kontrolnej* zawiera wartość sumy kontrolnej dla wszystkich wpisów w zestawie wpisów katalogu (wpis w katalogu plików i jego wpisy pomocnicze).

- **Atrybuty pliku**

    Wpis pola atrybutów jednobajtowych zawiera serię bitów, która określa różne właściwości wpisu katalogu. Definicja większości atrybutów bitów jest taka sama jak w przypadku systemu FAT 12/16/32. Definicje atrybutów katalogu są następujące:

    |Atrybut bit|Znaczenie|
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

    Pole *Utwórz sygnaturę czasową* , łącząc informacje z pola *tworzenia przyrostu 10 ms* , opisuje lokalną datę i godzinę utworzenia pliku lub katalogu.

- **Sygnatura czasowa ostatniej modyfikacji**

    Pole *sygnatura czasowa ostatniej modyfikacji* , łączące informacje z *ostatniej modyfikacji pola przyrostu 10 ms* , opisujące lokalną datę i godzinę ostatniej modyfikacji pliku lub katalogu. Poniżej znajdują się uwagi dotyczące sygnatur czasowych.

- **Sygnatura czasowa ostatniego dostępu**

    W polu *ostatnio używane sygnatura czasowa* opisano datę i godzinę ostatniego dostępu do pliku lub katalogu. Poniżej znajdują się uwagi dotyczące sygnatur czasowych.

- **Utwórz przyrost 10 ms**

    Pole *tworzenia 10 ms* , łączące informacje z pola *Utwórz sygnaturę czasową* , opisuje lokalną datę i godzinę utworzenia pliku lub katalogu. Poniżej znajdują się uwagi dotyczące sygnatur czasowych.

- **Ostatni zmodyfikowany 10 ms przyrostu**

    *Ostatnie zmodyfikowane pole przyrostu 10 ms* , łączące informacje z *ostatniej modyfikacji pola sygnatury czasowej* , opisujące lokalną datę i godzinę ostatniej modyfikacji pliku lub katalogu. Poniżej znajdują się uwagi dotyczące sygnatur czasowych.

- **Utwórz przesunięcie czasu UTC**

    Pole *Utwórz przesunięcie UTC* opisuje różnicę między czasem lokalnym i czasem UTC, gdy plik lub katalog został utworzony. Poniżej znajdują się uwagi dotyczące sygnatur czasowych.

- **Przesunięcie czasu UTC ostatniej modyfikacji**

    Pole *przesunięcie godzina ostatniej modyfikacji* zawiera informacje o różnicy między czasem lokalnym i czasem UTC, gdy plik lub katalog został ostatnio zmodyfikowany. Poniżej znajdują się uwagi dotyczące sygnatur czasowych.

- **Przesunięcie UTC ostatniego dostępu**

    Pole *przesunięcia ostatniego dostępu UTC* opisuje różnicę między czasem lokalnym i czasem UTC, kiedy ostatnio uzyskano dostęp do pliku lub katalogu. Poniżej znajdują się uwagi dotyczące sygnatur czasowych.

- **Reserved2**

    To pole powinno mieć wartość zero.

### <a name="notes-on-timestamps"></a>Uwagi dotyczące sygnatur czasowych

- **Wpis znacznika czasu** Pola sygnatur czasowych są interpretowane w następujący sposób:

- **pola przyrostu 10 ms** Wartość w polu przyrostu 10 ms zapewnia bardziej szczegółowy stopień szczegółowości wartości sygnatury czasowej. Prawidłowe wartości należą do zakresu od 0 (0ms) do 199 (1990ms).

     ![Pola przyrostu 10 ms](./media/user-guide/10ms-increment-fields.png)

- **Pole przesunięcia czasu UTC**

     ![Pole przesunięcia czasu UTC](./media/user-guide/utc-offset-field.png)

- **Wartość przesunięcia**

    7-bitowa liczba całkowita ze znakiem reprezentuje przesunięcie od czasu UTC, w ciągu 15 minut.

- **Prawidłowe**

    Czy wartość w polu przesunięcia jest prawidłowa. 0 wskazuje, że wartość w polu wartość przesunięcia jest nieprawidłowa. 1 wskazuje, że wartość jest prawidłowa.

### <a name="stream-extension-directory-entry"></a>Wpis katalogu rozszerzenia strumienia

Opis wpisu katalogu rozszerzenia strumienia i jego zawartości znajduje się w poniższej tabeli.

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

    Pole *Typ wpisu* wskazuje typ tego wpisu. W przypadku wpisu katalogu rozszerzenia przesyłania strumieniowego pole to musi być 0xC0.

- **Znaczników**

    To pole zawiera serię bitów, która określa różne właściwości:
    |Bit flagi|Znaczenie    |
    |-----------------|-----------|
    |0x01            |To pole wskazuje, czy jest możliwe przydzielenie klastrów. To pole powinno mieć 1.|
    |0x02            |To pole wskazuje, czy skojarzone klastry są ciągłe. Wartość 0 oznacza, że wpis FAT jest prawidłowy, a FileX powinien być zgodny z łańcuchem FAT. Wartość 1 oznacza, że wpis FAT jest nieprawidłowy, a klastry są ciągłe.|
    |Wszystkie inne bity    |Zarezerwowany.|

- **Zarezerwowane 1**

    To pole powinno mieć wartość 0.

- **Długość nazwy**

    Pole *Długość nazwy* zawiera długość ciągu Unicode w nazwach plików wpisy katalogu zbiorczo zawiera. Wpisy katalogu nazw plików są natychmiast zgodne z tym wpisem katalogu rozszerzenia strumienia.

- **Skrót nazwy**

    Pole *skrótu nazwy* jest wpisem 2-bajtowym zawierającym wartość skrótu nazwy pliku z wielkością liter. Wartość skrótu umożliwia szybsze wyszukiwanie nazw plików i katalogów: Jeśli wartości skrótu nie są zgodne, nazwa pliku skojarzona z tym wpisem nie jest zgodna.

- **Zarezerwowane 2**

    To pole powinno mieć wartość 0.

- **Prawidłowa długość danych**

    Pole *prawidłowej długości danych* wskazuje ilość prawidłowych danych w pliku.

- **Zarezerwowane 3**

    Ta wartość powinna być równa 0.

- **Pierwszy klaster**

    *Pierwszy klaster* zawiera indeks pierwszego klastra strumienia danych.

- **Długość danych**

    Pole *długość danych* zawiera łączną liczbę bajtów w przydzielonych klastrach. Ta wartość może być większa niż *prawidłowa długość danych*, ponieważ exFAT umożliwia wstępne przydzielanie klastrów danych.

### <a name="root-directory"></a>Katalog główny

W formatach w formacie 12-i 16-bitowym *katalog główny* znajduje się bezpośrednio po wszystkich sektorach FAT na nośniku i może być lokalizowany przez zbadanie ***fx_media_root_sector_start** _ w otwartym _ *FX_MEDIA** bloku sterowania. Rozmiar katalogu głównego, w odniesieniu do liczby wpisów w katalogu (każdy 32 bajtów w rozmiarze) jest określany przez odpowiadający mu wpis w rekordzie rozruchowym nośnika.

Katalog główny w systemach FAT-32 i exFAT może znajdować się w dowolnym miejscu w dostępnym klastrze. Jej lokalizacja i rozmiar są określane na podstawie rekordu rozruchowego, gdy zostanie otwarty nośnik. Po otwarciu nośnika można użyć pola ***fx_media_root_sector_start*** , aby znaleźć początkowy klaster w katalogu głównym FAT-32 lub exFAT.

### <a name="subdirectories"></a>Podkatalogów

W systemie FAT istnieje dowolna liczba podkatalogów. Nazwa podkatalogu znajduje się w pozycji katalogu, podobnie jak nazwa pliku. Jednak Specyfikacja atrybutu katalogu (0x10) jest ustawiona na wskazywanie, że wpis jest podkatalogiem, a rozmiar pliku jest zawsze równy zero.
Rysunek 3 pokazuje, jak wygląda struktura typowych podkatalogów dla nowego podkatalogu singlecluster o nazwie ***. DIR** _ o jednym pliku o nazwie _ *_FILE.TXT_* *.
W większości sposobów podkatalogi są bardzo podobne do wpisów plików. Pierwsze pole klastra wskazuje pierwszy klaster połączonej listy klastrów. Po utworzeniu podkatalogu pierwsze dwa wpisy katalogu zawierają katalogi domyślne, a mianowicie katalog "." i katalog "..". Katalog "." wskazuje sam katalog, podczas gdy katalog ".." wskazuje poprzedni lub katalog nadrzędny.

### <a name="global-default-path"></a>Globalna ścieżka domyślna

FileX zapewnia globalną ścieżkę domyślną dla nośnika. Ścieżka domyślna jest używana w dowolnym pliku lub usłudze katalogowej, która nie określa jawnie pełnej ścieżki.

Początkowo domyślny katalog globalny jest ustawiany na katalog główny nośnika. Może to zostać zmienione przez aplikację przez wywołanie ***fx_directory_default_set***.

Bieżącą domyślną ścieżką dla nośnika można sprawdzić przez wywołanie ***fx_directory_default_get** _. Ta procedura zawiera wskaźnik ciągu do domyślnego ciągu ścieżki, który jest obsługiwany w bloku _ *FX_MEDIA**.

### <a name="local-default-path"></a>Lokalna ścieżka domyślna

FileX udostępnia również ścieżkę domyślną specyficzną dla wątku, która umożliwia różnym wątkom posiadanie unikatowych ścieżek bez konfliktu. Struktura **FX_LOCAL_PATH** jest dostarczana przez aplikację podczas wywołań do **_fx_directory_local_path_set_*_ i _*_fx_directory_local_path_restore_** modyfikacji ścieżki lokalnej dla wątku wywołującego.

Jeśli ścieżka lokalna jest obecna, ścieżka lokalna ma pierwszeństwo przed globalną ścieżką nośnika. Jeśli ścieżka lokalna nie jest skonfigurowana lub jeśli zostanie wyczyszczona przy użyciu usługi ***fx_directory_local_path_clear*** , ponownie zostanie użyta globalna ścieżka domyślna nośnika.

## <a name="file-description"></a>Opis pliku

FileX obsługuje standardowy znak 8,3 i długie nazwy plików z rozszerzeniami trzech znaków. Oprócz nazwy ASCII każdy wpis w pliku zawiera atrybuty wpisu, godzinę ostatniej modyfikacji i datę, początkowy indeks klastra oraz rozmiar w bajtach wpisu.

### <a name="file-allocation"></a>Alokacja plików

FileX obsługuje standardowy schemat alokacji klastra w formacie FAT. Ponadto FileX obsługuje wstępne przydzielanie klastrów ciągłego klastra. Aby to umożliwić, każdy plik FileX jest tworzony bez przyznanych klastrów. Klastry są przydzielane do kolejnych żądań zapisu lub na żądania ***fx_file_allocate*** w celu wstępnego przydzielenia klastrów ciągłych.

Rysunek 4. "FileX plików FAT-16" zawiera plik o nazwie ***FILE.TXT*** z dwoma kolejnymi klastrami przydzielonymi, rozpoczynając od klastra 101, o rozmiarze 26 i alfabet jako dane w pierwszym klastrze danych pliku o numerze 101.

### <a name="file-access"></a>Dostęp do plików

Plik FileX może być otwarty wielokrotnie na potrzeby dostępu do odczytu. Plik można jednak otworzyć tylko raz do zapisu. Informacje używane do obsługi dostępu do pliku znajdują się w bloku kontroli plików ***FX_FILE*** .

> [!NOTE]
> *Należy pamiętać, że sterownik multimediów umożliwia dynamiczne ustawianie ochrony przed zapisem. W takim przypadku wszystkie żądania zapisu są odrzucane, a także próbuje otworzyć plik do zapisu.*

### <a name="file-layout-in-exfat"></a>Układ pliku w exFAT

Projekt exFAT nie wymaga utrzymywania łańcucha FAT dla pliku, jeśli dane są przechowywane w oddziałach. *NoFATChain* bit we wpisie katalogu rozszerzenia strumienia wskazuje, czy należy użyć łańcucha FAT podczas odczytywania danych z pliku. Jeśli *NoFATChain* jest ustawiony, FileX odczytuje sekwencyjnie z klastra wskazanego w pierwszym polu *klastra* we wpisie katalogu rozszerzenia strumienia.

Z drugiej strony, jeśli *NoFATChain* jest jasne, FileX będzie podążać za łańcuchem FAT w celu przechodzenia całego pliku, podobnie jak w przypadku łańcucha FAT w FAT12/16/32.

Rysunek 3 przedstawia dwa pliki przykładowe, jeden nie wymaga łańcucha FAT, a drugi wymaga łańcucha FAT.

## <a name="system-information"></a>Informacje o systemie

Informacje o systemie FileX obejmują śledzenie otwartych wystąpień nośników oraz utrzymanie globalnego czasu i daty systemowej.

![Plik z ciągłymi klastrami a plikiem wymagającym linku FAT](./media/user-guide/system-information.png)

**RYSUNEK 3. Plik z ciągłymi klastrami a plikiem wymagającym linku FAT**

Domyślnie Data i godzina systemowa są ustawiane na datę ostatniej wersji FileX. Aby uzyskać dokładną datę i godzinę systemową, aplikacja musi wywoływać ***fx_system_time_set** _ i _ *_fx_system_date_set_** podczas inicjowania.

### <a name="system-date"></a>Data systemowa

Data systemowa FileX jest utrzymywana w globalnej zmiennej ***_fx_system_date*** . Bity od 15 do 9 zawierają przesunięcie roku od 1980, bity od 8 do 5 zawierają przesunięcie miesiąca, a bity od 4 do 0 zawierają dzień. |

### <a name="system-time"></a>Czas systemowy

Czas systemowy FileX jest przechowywany w globalnej zmiennej ***_fx_system_time*** . Bity od 15 do 11 zawierają godziny, bity 10, jeśli 5 zawiera minuty, a bity 4, jeśli 0 zawierają połowę sekund.

### <a name="periodic-time-update"></a>Okresowa aktualizacja czasu

Podczas inicjowania systemu FileX tworzy czasomierz aplikacji ThreadX, aby okresowo aktualizować datę i godzinę systemową. Częstotliwość, z jaką aktualizacja daty i godziny systemowej jest określana przez dwie stałe używane przez funkcję ***_fx_system_initialize*** .

Stałe **FX_UPDATE_RATE_IN_SECONDS** i **FX_UPDATE_RATE_IN_TICKS** reprezentują ten sam okres czasu. Stała **FX_UPDATE_RATE_IN_TICKS** to liczba cykli czasomierza ThreadX, która reprezentuje liczbę sekund określoną przez **FX_UPDATE_RATE_IN_SECONDS** stałej. Stała **FX_UPDATE_RATE_IN_SECONDS** określa, ile sekund między każdą aktualizacją czasu FileX. W związku z tym wewnętrzny czas FileX jest zwiększany w interwałach **FX_UPDATE_RATE_IN_SECONDS**. Te stałe mogą być dostarczone podczas kompilacji **_fx_system_initialize_*_ lub deweloper może zmodyfikować wartości domyślne znalezione w pliku _*_fx_port. h_** FileX wersji.

Czasomierz okresowy FileX służy tylko do aktualizowania globalnej daty i godziny systemowej, która jest używana wyłącznie dla sygnatur czasowych plików. Jeśli sygnatura czasowa nie jest konieczna, po prostu Zdefiniuj **FX_NO_TIMER** podczas kompilowania **_fx_system_initialize. c_** , aby wyeliminować tworzenie czasomierza okresowego FileX.

![Przykład pliku FileX FAT-16](./media/user-guide/fat-16-file-example.png)

**RYSUNEK 4. Przykład pliku FileX FAT-16**
