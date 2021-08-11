---
title: Rozdział 2 — Instalacja i korzystanie z graficznego interfejsu użytkownika
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem graficznego interfejsu użytkownika produktu o wysokiej wydajności.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a4572dbf4691869d9a1c32d68fbf9cc1c7dbfbee7e58ad69dd944e668e382b76
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116784119"
---
# <a name="chapter-2---installation-and-use-of-guix"></a>Rozdział 2 — Instalacja i korzystanie z graficznego interfejsu użytkownika

Ten rozdział zawiera opis różnych problemów związanych z instalacją, instalacją i użyciem graficznego interfejsu użytkownika produktu o wysokiej wydajności.  

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

Opracowywanie osadzone jest zwykle wykonywane na komputerach Windows komputerach hostów z systemem Linux (Unix). Gdy aplikacja zostanie skompilowana, połączona i plik wykonywalny zostanie wygenerowany na hoście, zostanie on pobrany na docelowy sprzęt w celu wykonania.

Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzia dewelopera. Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonywania (go, halt, breakpoint itp.), a także dostęp do rejestrów pamięci i procesora.

Większość debugerów narzędzi deweloperskie komunikuje się ze sprzętem docelowym za pośrednictwem połączeń debugowania na mikroukładach (OCD), takich jak JTAG (IEEE 1149.1) i tryb debugowania w tle (BDM). Debugerzy komunikują się również ze sprzętem docelowym za pośrednictwem In-Circuit emulacji (ICE). Zarówno połączenia OCD, jak i ICE zapewniają niezawodne rozwiązania z minimalnym wtargnięciem do docelowego oprogramowania rezydatora.

Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy interfejsu GUXI jest dostarczany w formacie ASCII i wymaga około 30 MB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące celu

Graficzny interfejs użytkownika wymaga od 5 KB do 80 kb pamięci Read-Only (ROM) na komputerze docelowym. Kolejne 5–10 KB pamięci RAM (Random Access Memory) obiektu docelowego są wymagane dla stosu wątków GUIX i innych globalnych struktur danych.

Ponadto guix wymaga użycia czasomierza ThreadX i obiektu mutex ThreadX. Te obiekty są używane na potrzeby okresowego przetwarzania i ochrony wątków w graficznym interfejsie użytkownika.

## <a name="product-distribution"></a>Dystrybucja produktów

Azure RTOS GUIX można uzyskać z naszego publicznego repozytorium kodu źródłowego na stronie <https://github.com/azure-rtos/guix/> .

Poniżej znajduje się lista ważnych plików wspólnych dla większości dystrybucji produktów:

| Pod nazwą&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| Opis   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| gx_api.h        | Ten plik nagłówkowy języka C zawiera wszystkie elementy systemowe, struktury danych i prototypy usług. |
| gx_port.h       | Ten plik nagłówkowy języka C zawiera wszystkie struktury i definicje danych specyficzne dla określonego celu oraz narzędzia deweloperskich.                                                                                                                                         |
| gx.a (lub gx.lib) | Jest to wersja binarna biblioteki GUIX C. Zwykle jest to kompilowanie i archiwizowanie dostarczonych plików źródłowych biblioteki GUIX, jednak ta biblioteka może być dostarczana we wstępnie skompilowanej postaci w zależności od używanego sprzętu docelowego i typu licencji. |
|

> [!IMPORTANT]
> *Wszystkie pliki są małe, co ułatwia konwertowanie poleceń na platformy programowe Linux (Unix).*

## <a name="guix-installation"></a>Instalacja graficznego interfejsu użytkownika

Interfejs GUIX jest instalowany przez GitHub repozytorium na komputer lokalny. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium GUIX na komputerze:

```c
    git clone https://github.com/azure-rtos/guix
```

Możesz też pobrać kopię repozytorium przy użyciu przycisku pobierania na stronie GitHub głównej.

Instrukcje dotyczące tworzenia biblioteki GUIX można również znaleźć na pierwszej stronie repozytorium online.

>[!NOTE]  
> *Oprogramowanie aplikacji wymaga dostępu do pliku biblioteki GUIX, zwykle nazywanego **gx.a** (lub **gx.lib**), a pliki dołączane w języku C **gx_api.h** **i gx_port.h.** W tym celu należy wybrać odpowiednią ścieżkę dla narzędzi programistyki lub skopiować te pliki do obszaru tworzenia aplikacji.*

## <a name="using-guix"></a>Korzystanie z graficznego interfejsu użytkownika

Korzystanie z graficznego interfejsu użytkownika jest łatwe. Zasadniczo kod aplikacji musi zawierać plik ***gx_api.h** _ podczas kompilacji i połączyć go z biblioteką GUIX _*_gx.a_*_ (lub _ *_gx.lib_*)*.

Istnieją cztery proste kroki wymagane do skompilowania aplikacji GUIX:

| Kroki   | Opis    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Krok &nbsp; 1. | Dołącz plik ***gx_api.h*** do wszystkich plików aplikacji, które używają usług GUIX lub struktur danych.                                                               |
| Krok &nbsp; 2. | Zaimicjuj system GUIX, wywołując funkcję ***gx_system_initialize** _ z funkcji _ *_tx_application_define_** lub wątku aplikacji.                       |
| Krok &nbsp; 3. | Utwórz wystąpienie wyświetlania, utwórz kanwę do wyświetlania i utwórz okno główne oraz inne wymagane okna lub widżety.                                 |
| Krok &nbsp; 4. | Kompilowanie źródła aplikacji i łączenie za pomocą biblioteki środowiska uruchomieniowego GUIX ***gx.a** _ (lub _*_gx.lib_**). Wynikowy obraz można pobrać do obiektu docelowego i wykonać! |

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port GUIX jest dostarczany z demonstracyjną aplikacją, która jest wykonywana na określonym sprzęcie wyświetlania. Ta sama podstawowa demonstracja jest dostarczana ze wszystkimi wersjami interfejsu GUIX. Zawsze dobrym pomysłem jest uruchomienie najpierw systemu pokazowego.

Jeśli system pokazowy nie działa prawidłowo, wykonaj następujące operacje, aby zawęzić problem:

1. Określ, jaka część pokazu jest uruchomiona.

2. Zwiększ rozmiar stosu wątku GUIX, zmieniając stałą w czasie kompilacji **GX_THREAD_STACK_SIZE** i ponownie skompiluj bibliotekę GUIX

3. Ponownie skompiluj bibliotekę GUIX z odpowiednimi opcjami debugowania wymienionymi w sekcji opcji konfiguracji.

4. Sprawdź stan zwracany ze wszystkich wywołań interfejsu API.

5. Ustal, czy wystąpił wewnętrzny błąd systemu, ustawiając punkt przerwania w funkcji ***_gx_system_error_process***. Kod błędu i wywołujący powinien dać wskazówki co do tego, co może dzieje się źle.

6. Tymczasowo pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem zniknie lub zmieni się. Takie informacje powinny okazać się przydatne dla inżynierów pomocy technicznej firmy Microsoft.

Postępuj zgodnie z procedurami opisanymi w sekcji "Czego potrzebujemy od Ciebie", aby wysłać informacje zebrane z kroków rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Istnieje kilka opcji konfiguracji podczas budowania biblioteki GUIX i aplikacji przy użyciu interfejsu GUIX. Te opcje służą do dostrajania rozmiaru biblioteki i zestawu funkcji w celu najlepszego dopasowania do wymagań aplikacji. Jeśli na przykład aplikacja będzie mieć tylko jeden wątek korzystający z usług interfejsu API GUIX, należy zdefiniować flagę **konfiguracji GX_DISABLE_MULTITHREAD_SUPPORT** w celu wyeliminowania narzutu związanego z ochroną krytycznych sekcji kodu przed wstępnego opróżnienia przez wiele wątków. Różne flagi konfiguracji można zdefiniować w źródle aplikacji, w wierszu polecenia lub **_w pliku dołączania gx_user.h._**

Za każdym razem, gdy flagi konfiguracji biblioteki GUIX są modyfikowane, wymagane jest ponowne skompilowanie biblioteki GUIX i modułów aplikacji, aby zmiany konfiguracji zostały wprowadzone.

Pełna lista flag konfiguracji jest udokumentowana w dodatek H: GUIX Build-Time flagi konfiguracji.

## <a name="guix-version-id"></a>Identyfikator wersji GUIX

Bieżąca wersja graficznego interfejsu użytkownika (GUIX) jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji w czasie wykonywania. Programista może uzyskać wersję GUIX z badania pliku ***gx_port.h_.** Ponadto ten plik zawiera również historię wersji odpowiedniego portu Oprogramowanie aplikacji może uzyskać wersję GUIX, sprawdzając ciąg globalny _ *_ _gx_version_id_* _ w _*_gx_port.h_**.

Oprogramowanie aplikacji może również uzyskać informacje o wersji ze stałych pokazanych poniżej zdefiniowanych w pliku ***gx_api.h**.* Te stałe identyfikują bieżące wydanie produktu według nazwy oraz wersji wersji głównych i pomocniczej produktu.

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
