---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO FileX
description: Ten rozdział zawiera wprowadzenie do usługi Azure RTO FileX oraz opis warunków instalacji, procedur i użycia, w tym następujących
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6703b10d8e0895984bb92d74d5dff809dca1a7f8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821414"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-filex"></a>Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO FileX

Ten rozdział zawiera wprowadzenie do usługi Azure RTO FileX oraz opis warunków instalacji, procedur i użycia. 

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

### <a name="computer-type"></a>Typ komputera

Projektowanie osadzone jest zwykle wykonywane na komputerach hostów z systemem Windows lub Linux (UNIX). Gdy aplikacja zostanie skompilowana, połączona i umieszczona na hoście, zostanie pobrana na docelowy sprzęt do wykonania.

### <a name="download-interfaces"></a>Pobierz interfejsy

Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzia deweloperskiego. Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonania (go, zatrzymania, punktu przerwania itp.) oraz dostęp do rejestrów pamięci i procesora.

### <a name="debugging-tools"></a>Narzędzia debugowania

Większość debugerów narzędzi programistycznych komunikuje się z sprzętem docelowym za pośrednictwem połączeń OCD (on-Chip Debug), takich jak JTAG (IEEE 1149,1) i tryb debugowania w tle (BDM). Debugery komunikują się również z sprzętem docelowym za pomocą połączeń In-Circuit Emulation (lodem). Połączenia OCD i lód zapewniają niezawodne rozwiązania z minimalnym dostępem do docelowego oprogramowania rezydentnego.

### <a name="required-hard-disk-space"></a>Wymagane miejsce na dysku twardym

Kod źródłowy dla FileX jest dostarczany w formacie ASCII i wymaga około 500 KB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące obiektów docelowych

FileX wymaga od 6 kilobajtów do 30 kilobajtów pamięci Read-Only (ROM) w miejscu docelowym. Do globalnych struktur danych FileX są wymagane inne 100 bajtów pamięci RAM. Każdy otwarty nośnik wymaga również 1,5 kilobajtów pamięci RAM dla bloku sterowania oprócz pamięci RAM do przechowywania danych dla jednego sektora (zazwyczaj 512 bajtów).

Aby Sygnatura daty i godziny działała prawidłowo, FileX opiera się na obiektach czasomierza ThreadX. Jest to implementowane przez utworzenie czasomierza specyficznego dla FileX podczas inicjowania FileX. FileX opiera się również na semaforach ThreadX dla wielu wątków ochrony i operacji we/wy.

## <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO FileX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/filex/> .

Poniżej znajduje się lista kilku ważnych plików w repozytorium:

- ***fx_api. h*** : ten plik nagłówka C zawiera wszystkie równe systemowe, struktury danych i prototypy usługi.
- ***fx_port. h*** : ten plik nagłówkowy C zawiera wszystkie definicje i struktury danych specyficzne dla narzędzia deweloperskiego.
- ***demo_filex. c*** : ten plik c zawiera małą aplikację demonstracyjną.
- ***FX. a (lub FX. lib)*** : jest to binarna wersja biblioteki FileX C. Jest dystrybuowana z pakietem standardowym.

> [!IMPORTANT]
> *Wszystkie nazwy plików są w małych przypadkach. Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformy deweloperskie systemu Linux (UNIX).*

## <a name="filex-installation"></a>Instalacja FileX

FileX jest instalowany przez klonowanie repozytorium GitHub na komputerze lokalnym. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium FileX na komputerze:

```c
    git clone https://github.com/azure-rtos/filex
```

Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku Pobierz na stronie głównej usługi GitHub.

Znajdziesz również instrukcje dotyczące tworzenia biblioteki FileX na stronie frontonu repozytorium online.

> [!IMPORTANT]
> Oprogramowanie aplikacji musi mieć dostęp do pliku biblioteki FileX (zwykle nazywanego ***FX. a** _ lub _*_FX. lib_*_) _and plików dołączanych **fx_api. h** i **fx_port. h**. W tym celu należy ustawić odpowiednią ścieżkę dla narzędzi programistycznych lub skopiować te pliki do obszaru projektowania aplikacji.

## <a name="using-filex"></a>Korzystanie z FileX

Korzystanie z FileX jest łatwe. Zasadniczo kod aplikacji musi zawierać ***fx_api. h** _ podczas kompilacji i połączyć z biblioteką uruchomieniową FileX _*_FX. a_*_ (lub _*_FX. lib_*_). Oczywiście są również wymagane pliki ThreadX, a mianowicie _*_tx_api. h_*_ i _*_TX. a_*_ (lub _*_TX. lib_*_) _, *.

> [!IMPORTANT]
> W przypadku korzystania z FileX w trybie autonomicznym (**FX_STANDALONE_ENABLE** musi być zdefiniowana), ThreadX pliki/biblioteki nie są wymagane.

Przy założeniu, że już korzystasz z ThreadX, istnieją cztery kroki wymagane do skompilowania aplikacji FileX:

1. Uwzględnij plik ***fx_api. h*** we wszystkich plikach aplikacji, które korzystają z usług FileX Services lub struktur danych.
1. Zainicjuj system FileX przez wywołanie ***fx_system_initialize** _ z funkcji _ *_tx_application_define_** lub wątku aplikacji.

    > [!IMPORTANT]
    > W przypadku korzystania z FileX w trybie autonomicznym ***fx_system_initialize*** należy bezpośrednio wywołać z kodu aplikacji.

1. Dodaj co najmniej jedno wywołanie do ***fx_media_open*** , aby skonfigurować nośnik FileX. To wywołanie musi być wykonane z kontekstu wątku aplikacji.

    > [!IMPORTANT]
    > *Należy pamiętać, że wywołanie **fx_media_open** wymaga wystarczającej ilości pamięci RAM do przechowywania danych dla jednego sektora.*

1. Kompiluj Źródło aplikacji i połącz je z bibliotekami czasu wykonywania FileX i ThreadX, ***FX. a** _ (lub _*_FX. lib_*_) i _*_TX. a_*_ (lub _ *_TX. lib_* *). Obraz wyników można pobrać do elementu docelowego i wykonać!

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port FileX jest dostarczany z aplikacją demonstracyjną. Zawsze dobrym pomysłem jest rozpoczęcie pierwszego uruchomienia systemu demonstracyjnego — na sprzęcie docelowym lub w konkretnym środowisku demonstracyjnym.

Jeśli system demonstracyjny nie działa, spróbuj wykonać następujące czynności, aby zawęzić ten problem:

1. Określ, jaka część demonstracji jest uruchomiona.
1. Zwiększ rozmiary stosu (jest to ważniejsze w rzeczywistym kodzie aplikacji niż w przypadku pokazu).
1. Upewnij się, że jest wystarczająca ilość pamięci RAM dla 32KBytes domyślnego rozmiaru dysku RAM. System podstawowy będzie działał znacznie mniej pamięci RAM; Jednak w przypadku użycia większej ilości miejsca w pamięci RAM problemy będą dostępne, jeśli nie ma wystarczającej ilości pamięci.
1. Tymczasowo Pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub nie ulegnie zmianie. Takie informacje powinny być przydatne dla inżynierów pomocy technicznej firmy Microsoft. Postępuj zgodnie z procedurami przedstawionymi w centrum pomocy technicznej, aby wysłać informacje zebrane z kroków rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Podczas kompilowania biblioteki FileX i aplikacji przy użyciu FileX istnieje kilka opcji konfiguracji. Poniższe opcje można zdefiniować w źródle aplikacji, w wierszu polecenia lub w pliku ***fx_user. h*** .

> [!IMPORTANT]
> *Opcje zdefiniowane w **fx_user. h** są stosowane tylko wtedy, gdy aplikacja i Biblioteka ThreadX zostały skompilowane z **_FX_INCLUDE_USER_DEFINE_FILE_* _ Defined._ w przypadku używania FileX w trybie autonomicznym (** FX_STANDALONE_ENABLE** musi być zdefiniowana), ThreadX pliki/biblioteki nie są wymagane.

Na poniższej liście opisano szczegółowo każdą opcję konfiguracji:

|Zdefiniować|Znaczenie|
|----------    |-----------|
|FX_MAX_LAST_NAME_LEN        |Ta wartość określa maksymalną długość nazwy pliku, która zawiera pełną nazwę ścieżki. Wartość domyślna to 256.|
|FX_DONT_UPDATE_OPEN_FILES    |Zdefiniowane, FileX nie aktualizuje już otwartych plików.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Zdefiniowane, Optymalizacja pamięci podręcznej wyszukiwania plików jest wyłączona.|
|FX_MEDIA_DISABLE_SEARCH_CACHE    |Zdefiniowane, Optymalizacja pamięci podręcznej wyszukiwania plików jest wyłączona.|
|FX_DISABLE_DIRECT_DATA_READ_CACHE_FILL |Zdefiniowane, Bezpośrednia aktualizacja sektora pamięci podręcznej jest wyłączona.|
|FX_MEDIA_STATISTICS_DISABLE |Zdefiniowane, zbieranie statystyk multimediów jest wyłączone.|
|FX_SINGLE_OPEN_LEGACY |Zdefiniowano starszą, jednokrotną, otwartą logikę dla tego samego pliku.|
|FX_RENAME_PATH_INHERIT    |Zdefiniowane, zmiana nazwy dziedziczy informacje Path.|
|FX_DISABLE_ERROR_CHECKING    |Usuwa interfejs API podstawowego sprawdzania błędów FileX i zwiększa wydajność (nawet 30%) i mniejszy rozmiar kodu.|
|FX_MAX_LONG_NAME_LEN    |Określa maksymalny rozmiar nazwy pliku dla FileX. Wartość domyślna to 256, ale można ją zastąpić przy użyciu wiersza polecenia. Wartości prawne mieszczą się w zakresie od 13 do 256.|
|FX_MAX_SECTOR_CACHE|Określa maksymalną liczbę sektorów logicznych, które mogą być buforowane przez FileX. Rzeczywista liczba sektorów, które mogą być buforowane, jest mniejsza od tej stałej i ile sektorów może zmieścić się w ilości pamięci podanej w fx_media_open. Wartość domyślna to 256. Wszystkie wartości muszą być potęgą liczby 2.|
|FX_FAT_MAP_SIZE    |Określa liczbę sektorów, które mogą być reprezentowane w mapie aktualizacji FAT. Wartość domyślna to 256, ale można ją zastąpić przy użyciu wiersza polecenia. Większe wartości pomagają w zmniejszeniu niepotrzebnych aktualizacji pomocniczych sektorów FAT.|
|FX_MAX_FAT_CACHE    |Określa liczbę wpisów w wewnętrznej pamięci podręcznej FAT. Wartość domyślna to 16, ale można ją zastąpić przy użyciu wiersza polecenia. Wszystkie wartości muszą być potęgą liczby 2.|
|FX_FAULT_TOLERANT    |Po zdefiniowaniu FileX natychmiast przekazuje żądania zapisu wszystkich sektorów systemu (rozruch, FAT i sektory katalogu) do sterownika nośnika. Może to spowodować zmniejszenie wydajności, ale pomaga ograniczyć uszkodzenie do utraconych klastrów. Należy pamiętać, że włączenie tej funkcji nie powoduje automatycznego włączenia modułu odpornego na błędy FileX, który jest włączony przez zdefiniowanie|
|FX_FAULT_TOLERANT_DATA    |Po zdefiniowaniu FileX natychmiast przekazuje wszystkie żądania zapisu danych o plikach do sterownika nośnika. Może to spowodować zmniejszenie wydajności, ale pomaga ograniczyć utratę danych plików. Należy pamiętać, że włączenie tej funkcji nie powoduje automatycznego włączenia modułu odpornego na błędy FileX, który jest włączony przez zdefiniowanie ***FX_ENABLE_FAULT_TOLERANT***|
|FX_NO_LOCAL_PATH|Usuwa logikę ścieżki lokalnej z FileX, co zmniejsza rozmiar kodu.|
|FX_NO_TIMER|Eliminuje konfigurację czasomierza ThreadX, aby zaktualizować datę i godzinę systemu FileX. Wykonanie tej czynności powoduje, że domyślny czas i Data są umieszczane we wszystkich operacjach na plikach.|
|FX_UPDATE_RATE_IN_SECONDS    |Określa częstotliwość, z jaką jest dostosowywany czas systemowy w FileX. Wartość domyślna to 10, co oznacza, że czas systemowy FileX jest aktualizowany co 10 sekund.|
|FX_ENABLE_EXFAT| Po zdefiniowaniu logika obsługi systemu plików exFAT jest włączona w FileX. Domyślnie ten symbol nie jest zdefiniowany.| 
|FX_UPDATE_RATE_IN_TICKS| Określa taką samą stawkę jak ***FX_UPDATE_RATE_IN_SECONDS*** (patrz powyżej), z wyjątkiem postanowień podstawowej częstotliwości czasomierza ThreadX. Wartość domyślna to 1000, w której przyjęto częstotliwość czasomierza ThreadX 10 ms i 10-sekundowy interwał.|
|FX_SINGLE_THREAD|Eliminuje logikę ochrony ThreadX ze źródła FileX. Powinien być używany, jeśli FileX jest używany tylko z jednego wątku lub jeśli FileX jest używany bez ThreadX.|
|FX_DRIVER_USE_64BIT_LBA|Gdy jest zdefiniowany, włącza adresy sektorów 64-bitowych używanych w sterowniku we/wy. Domyślnie ta opcja nie jest zdefiniowana.|
|FX_ENABLE_FAULT_TOLERANT| Po zdefiniowaniu włącza moduł odporny na uszkodzenia FileX. Włączenie odporności na uszkodzenia automatycznie definiuje symbol ***FX_FAULT_TOLERANT** _ i _ *_FX_FAULT_TOLERANT_DATA_* *. Domyślnie ta opcja nie jest zdefiniowana.|
|FX_FAULT_TOLERANT_BOOT_INDEX|Definiuje przesunięcie bajtów w sektorze rozruchowym, w którym znajduje się klaster dla dziennika odpornego na błędy. Wartość domyślna to 116. To pole ma 4 bajty. Liczba bajtów 116 do 119 została wybrana, ponieważ są one oznaczone jako zarezerwowane przez specyfikację FAT 12/16/32/exFAT.|
|FX_FAULT_TOLERANT_MINIMAL_CLUSTER|Ten symbol jest przestarzały. Nie jest już używany przez FileX odporny na uszkodzenia.|
|FX_STANDALONE_ENABLE|Zdefiniowane, umożliwia korzystanie z FileX w trybie autonomicznym (bez usługi Azure RTO). Domyślnie ten symbol nie jest zdefiniowany.|

> [!IMPORTANT]
> W przypadku zdefiniowania **FX_STANDALONE_ENABLE** , konfiguracja logiki lokalnej ścieżki i czasomierza ThreadX są wyłączone.

## <a name="filex-version-id"></a>Identyfikator wersji FileX

Bieżąca wersja programu FileX jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji w czasie wykonywania. Programista może uzyskać wersję FileX z badania pliku **fx_port. h** . Ponadto ten plik zawiera również historię wersji odpowiedniego portu. Oprogramowanie aplikacji może uzyskać wersję FileX, badając ciąg globalny **_ _fx_version_id_**.
