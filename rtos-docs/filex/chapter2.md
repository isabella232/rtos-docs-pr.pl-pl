---
title: Rozdział 2 — Instalowanie i używanie Azure RTOS FileX
description: Ten rozdział zawiera wprowadzenie do Azure RTOS FileX oraz opis warunków instalacji, procedur i użycia, w tym następujące
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2f064fc65ef8445ea33590f23d5a040ed8b07c6c651ea4cf5c4aaef4b6c4fa7b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783853"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-filex"></a>Rozdział 2 — Instalowanie i używanie Azure RTOS FileX

Ten rozdział zawiera wprowadzenie do Azure RTOS FileX oraz opis warunków instalacji, procedur i użycia. 

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

### <a name="computer-type"></a>Typ komputera

Opracowywanie osadzone jest zwykle wykonywane na komputerach Windows komputerach hostów z systemem Linux (Unix). Gdy aplikacja zostanie skompilowana, połączona i zlokalizowana na hoście, zostanie pobrana na docelowy sprzęt w celu wykonania.

### <a name="download-interfaces"></a>Interfejsy pobierania

Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzia dewelopera. Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonywania (go, halt, breakpoint itp.), a także dostęp do rejestrów pamięci i procesora.

### <a name="debugging-tools"></a>Narzędzia debugowania

Większość debugerów narzędzi deweloperskie komunikuje się ze sprzętem docelowym za pośrednictwem połączeń debugowania na mikroukładach (OCD), takich jak JTAG (IEEE 1149.1) i tryb debugowania w tle (BDM). Debugerzy komunikują się również ze sprzętem docelowym za pośrednictwem In-Circuit emulacji (ICE). Zarówno połączenia OCD, jak i ICE zapewniają niezawodne rozwiązania z minimalnym wtargnięciem do docelowego oprogramowania rezydatora.

### <a name="required-hard-disk-space"></a>Wymagane miejsce na dysku twardym

Kod źródłowy pliku FileX jest dostarczany w formacie ASCII i wymaga około 500 KB miejsca na dysku twardym komputera hosta

## <a name="target-considerations"></a>Zagadnienia dotyczące celu

Plik FileX wymaga od 6 KB do 30 KB Read-Only pamięci (ROM) na komputerze docelowym. Kolejne 100 bajtów pamięci RAM (Random Access Memory) obiektu docelowego są wymagane dla globalnych struktur danych FileX. Każdy otwarty nośnik wymaga również 1,5 KB pamięci RAM dla bloku sterowania oprócz pamięci RAM do przechowywania danych dla jednego sektora (zwykle 512 bajtów).

Aby sygnatury daty/czasu działały prawidłowo, plik FileX opiera się na funkcjach czasomierza ThreadX. Jest to implementowane przez utworzenie czasomierza specyficznego dla pliku FileX podczas inicjowania pliku FileX. Plik FileX korzysta również z semaforów ThreadX w celu ochrony wielu wątków i zawieszania we/wy.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS plik FileX można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie <https://github.com/azure-rtos/filex/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium:

- ***fx_api.h:*** ten plik nagłówkowy języka C zawiera wszystkie elementy systemowe, struktury danych i prototypy usług.
- ***fx_port.h:*** ten plik nagłówkowy języka C zawiera wszystkie struktury i definicje danych specyficzne dla narzędzia deweloperskich.
- ***demo_filex.c:*** ten plik C zawiera małą aplikację demonstracyjną.
- ***fx.a (lub fx.lib)*** : jest to wersja binarna biblioteki FileX C. Jest on dystrybuowany za pomocą pakietu standardowego.

> [!IMPORTANT]
> *Wszystkie nazwy plików są małe. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformy programowe Linux (Unix).*

## <a name="filex-installation"></a>Instalacja pliku FileX

Plik FileX jest instalowany przez GitHub repozytorium na komputer lokalny. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium FileX na komputerze:

```c
    git clone https://github.com/azure-rtos/filex
```

Możesz też pobrać kopię repozytorium przy użyciu przycisku pobierania na stronie GitHub głównej.

Instrukcje dotyczące tworzenia biblioteki FileX znajdują się również na pierwszej stronie repozytorium online.

> [!IMPORTANT]
> Oprogramowanie aplikacji wymaga dostępu do pliku biblioteki FileX (zazwyczaj nazywanego * zazwyczaj ***fx.a** _ lub _*_fx.lib_*_) _and pliki dołączane W **fx_api.h** i **fx_port.h.** W tym celu należy wybrać odpowiednią ścieżkę dla narzędzi programistyki lub skopiować te pliki do obszaru tworzenia aplikacji.

## <a name="using-filex"></a>Korzystanie z pliku FileX

Korzystanie z pliku FileX jest łatwe. Zasadniczo kod aplikacji musi zawierać plik ***fx_api.h** _ podczas kompilacji i połączyć go z biblioteką uruchomieniową FileX _*_fx.a_*_ (lub _*_fx.lib)._*_ Oczywiście wymagane są również pliki ThreadX, _*_tx_api.h_*_ i _*_tx.a_*_ (lub _*_tx.lib_*_)_,*.

> [!IMPORTANT]
> W przypadku używania pliku FileX w trybie autonomicznym **(FX_STANDALONE_ENABLE** musi być zdefiniowany), pliki/biblioteki ThreadX nie są wymagane.

Przy założeniu, że używasz już threadX, istnieją cztery kroki wymagane do skompilowania aplikacji FileX:

1. Dołącz plik ***fx_api.h*** do wszystkich plików aplikacji, które używają usług FileX lub struktur danych.
1. Zaimicjuj system FileX, wywołując funkcję ***fx_system_initialize** _ z funkcji _ *_tx_application_define_** lub wątku aplikacji.

    > [!IMPORTANT]
    > W przypadku korzystania z pliku FileX w trybie ***autonomicznym fx_system_initialize*** wywoływane bezpośrednio z kodu aplikacji.

1. Dodaj jedno lub więcej wywołań ***fx_media_open*** w celu skonfigurowania nośnika FileX. To wywołanie musi być wykonane z kontekstu wątku aplikacji.

    > [!IMPORTANT]
    > *Należy pamiętać, **że fx_media_open** wymaga wystarczającej ilości pamięci RAM do przechowywania danych dla jednego sektora.*

1. Skompiluj źródło aplikacji i połącz je za pomocą bibliotek czasu uruchomieniowego FileX i ThreadX, ***fx.a** _ (lub _*_fx.lib_*_) i _*_tx.a_*_ (lub _*_tx.lib_**). Wynikowy obraz można pobrać do obiektu docelowego i wykonać!

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port FileX jest dostarczany z demonstracyjną aplikacją. Zawsze dobrym pomysłem jest uruchomienie systemu pokazowego jako pierwszego — na sprzęcie docelowym lub w określonym środowisku pokazowym.

Jeśli system pokazowy nie działa, spróbuj wykonać następujące czynności, aby zawęzić problem:

1. Określ, jaka część pokazu jest uruchomiona.
1. Zwiększ rozmiary stosów (jest to ważniejsze w rzeczywistym kodzie aplikacji niż w przypadku pokazu).
1. Upewnij się, że jest wystarczająca ilość pamięci RAM dla domyślnego rozmiaru dysku RAM 32 KB. System podstawowy będzie działać na znacznie mniejszej ilości pamięci RAM; Jednak w przypadku użycia większej ilości pamięci RAM, problemy będą pojawiać się, jeśli nie ma wystarczającej ilości pamięci.
1. Tymczasowo pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem zniknie lub zmieni się. Takie informacje powinny okazać się przydatne dla inżynierów pomocy technicznej firmy Microsoft. Postępuj zgodnie z procedurami opisanymi w "Centrum obsługi klienta", aby wysłać informacje zebrane w krokach rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji podczas budowania biblioteki FileX i aplikacji przy użyciu pliku FileX. Poniższe opcje można zdefiniować w źródle aplikacji, w wierszu polecenia lub w ***pliku dołączania fx_user.h.***

> [!IMPORTANT]
> Opcje zdefiniowane w pliku fx_user.h są stosowane tylko wtedy, gdy aplikacja i biblioteka ThreadX są budowane za pomocą ***_biblioteki FX_INCLUDE_USER_DEFINE_FILE_*_ defined._*** W przypadku używania pliku FileX w trybie autonomicznym ( FX_STANDALONE_ENABLE należy zdefiniować biblioteki/pliki ThreadX) nie są wymagane.

Na poniższej liście szczegółowo opisano każdą opcję konfiguracji:

|Zdefiniować|Znaczenie|
|----------    |-----------|
|FX_MAX_LAST_NAME_LEN        |Ta wartość definiuje maksymalną długość nazwy pliku, która zawiera pełną nazwę ścieżki. Domyślnie ta wartość to 256.|
|FX_DONT_UPDATE_OPEN_FILES    |Zdefiniowano, plik FileX nie aktualizuje już otwartych plików.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Zdefiniowano, optymalizacja pamięci podręcznej wyszukiwania plików jest wyłączona.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Zdefiniowano, optymalizacja pamięci podręcznej wyszukiwania plików jest wyłączona.|
|FX_DISABLE_DIRECT_DATA_READ_CACHE_FILL |Zdefiniowano, że bezpośrednia aktualizacja sektora odczytu pamięci podręcznej jest wyłączona.|
|FX_MEDIA_STATISTICS_DISABLE |Zdefiniowane, zbieranie statystyk multimediów jest wyłączone.|
|FX_SINGLE_OPEN_LEGACY |Zdefiniowano, że włączono starszą pojedynczą logikę otwierania dla tego samego pliku.|
|FX_RENAME_PATH_INHERIT    |Zdefiniowana zmiana nazwy dziedziczy informacje o ścieżce.|
|FX_DISABLE_ERROR_CHECKING    |Usuwa podstawowy interfejs API sprawdzania błędów fileX i powoduje zwiększenie wydajności (nawet o 30%) i mniejszego rozmiaru kodu.|
|FX_MAX_LONG_NAME_LEN    |Określa maksymalny rozmiar nazwy pliku dla FileX. Wartość domyślna to 256, ale można ją zastąpić definicją wiersza polecenia. Wartości prawne to od 13 do 256.|
|FX_MAX_SECTOR_CACHE|Określa maksymalną liczbę sektorów logicznych, które mogą być buforowane przez PlikX. Rzeczywista liczba sektorów, które mogą być buforowane, jest mniejsza od tej stałej i ile sektorów może zmieścić się w ilości pamięci dostarczonej w fx_media_open. Wartość domyślna to 256. Wszystkie wartości muszą mieć potęgę 2.|
|FX_FAT_MAP_SIZE    |Określa liczbę sektorów, które mogą być reprezentowane w mapie aktualizacji FAT. Wartość domyślna to 256, ale można ją zastąpić definicją wiersza polecenia. Większe wartości pomagają zmniejszyć niepotrzebnych aktualizacji pomocniczych sektorów FAT.|
|FX_MAX_FAT_CACHE    |Określa liczbę wpisów w wewnętrznej pamięci podręcznej FAT. Wartość domyślna to 16, ale można ją zastąpić definicją wiersza polecenia. Wszystkie wartości muszą mieć potęgę 2.|
|FX_FAULT_TOLERANT    |Po zdefiniowanym pliku FileX natychmiast przekazuje żądania zapisu wszystkich sektorów systemu (rozruchu, FAT i katalogów) do sterownika nośnika. Potencjalnie zmniejsza to wydajność, ale pomaga ograniczyć uszkodzenie utraconych klastrów. Należy pamiętać, że włączenie tej funkcji nie powoduje automatycznego włączenia modułu odporności na błędy FileX, który jest włączany przez zdefiniowanie|
|FX_FAULT_TOLERANT_DATA    |Po zdefiniowanym pliku FileX natychmiast przekazuje wszystkie żądania zapisu danych do sterownika nośnika. Może to obniżyć wydajność, ale pomaga ograniczyć utracone dane plików. Należy pamiętać, że włączenie tej funkcji nie powoduje automatycznego włączenia modułu odporności na błędy FileX, który jest włączany przez ***zdefiniowanie FX_ENABLE_FAULT_TOLERANT***|
|FX_NO_LOCAL_PATH|Usuwa logikę ścieżki lokalnej z pliku FileX, co powoduje mniejszy rozmiar kodu.|
|FX_NO_TIMER|Eliminuje konfigurację czasomierza ThreadX w celu zaktualizowania daty i czasu systemu FileX. Spowoduje to ustawienie domyślnej daty i czasu we wszystkich operacjach na plikach.|
|FX_UPDATE_RATE_IN_SECONDS    |Określa szybkość dostosowania czasu systemowego w pliku FileX. Domyślnie wartość to 10, określając, że czas systemowy FileX jest aktualizowany co 10 sekund.|
|FX_ENABLE_EXFAT| W przypadku definicji logika obsługi systemu plików exFAT jest włączona w pliku FileX. Domyślnie ten symbol nie jest zdefiniowany.| 
|FX_UPDATE_RATE_IN_TICKS| Określa tę samą częstotliwość co ***FX_UPDATE_RATE_IN_SECONDS*** (patrz powyżej), z wyjątkiem częstotliwości czasomierza ThreadX bazowej. Wartość domyślna to 1000, która zakłada czasomierz ThreadX o rozmiarze 10 m i interwał 10 sekund.|
|FX_SINGLE_THREAD|Eliminuje logikę ochrony ThreadX ze źródła FileX. Należy go używać, jeśli plik FileX jest używany tylko z jednego wątku lub jeśli plik FileX jest używany bez ThreadX.|
|FX_DRIVER_USE_64BIT_LBA|W przypadku zdefiniowanych włącza 64-bitowe adresy sektorów używane w sterowniku We/Wy. Domyślnie ta opcja nie jest zdefiniowana.|
|FX_ENABLE_FAULT_TOLERANT| Po zdefiniowanym w programie włączany jest moduł tolerantny błędów FileX. Włączenie odporności na uszkodzenia automatycznie definiuje symbol ***** FX_FAULT_TOLERANT _ i __*_ FX_FAULT_TOLERANT_DATA **. Domyślnie ta opcja nie jest zdefiniowana.|
|FX_FAULT_TOLERANT_BOOT_INDEX|Definiuje przesunięcie bajtów w sektorze rozruchu, w którym znajduje się klaster dla dziennika odporności na uszkodzenia. Domyślnie ta wartość to 116. To pole zajmuje 4 bajty. Wybierane są bajty od 116 do 119, ponieważ są oznaczone jako zarezerwowane przez specyfikację FAT 12/16/32/exFAT.|
|FX_FAULT_TOLERANT_MINIMAL_CLUSTER|Ten symbol jest przestarzały. Nie jest on już używany przez system FileX Fault Tolerant.|
|FX_STANDALONE_ENABLE|Zdefiniowane umożliwia korzystanie z pliku FileX w trybie autonomicznym (bez Azure RTOS). Domyślnie ten symbol nie jest zdefiniowany.|

> [!IMPORTANT]
> Po **FX_STANDALONE_ENABLE** logiki ścieżki lokalnej i czasomierza ThreadX są wyłączone.

## <a name="filex-version-id"></a>Identyfikator wersji pliku FileX

Bieżąca wersja pliku FileX jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji w czasie uruchamiania. Programista może uzyskać wersję FileX z badania **fx_port.h.** Ponadto ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję FileX, sprawdzając globalny ciąg **_ _fx_version_id_**.
