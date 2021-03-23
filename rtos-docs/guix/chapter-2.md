---
title: Rozdział 2 — Instalowanie i korzystanie z GUIX
description: Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem HighPerformance produktu interfejsu użytkownika GUIX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6527227062fc667b3f527a798d6621914c374c5c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822296"
---
# <a name="chapter-2---installation-and-use-of-guix"></a>Rozdział 2 — Instalowanie i korzystanie z GUIX

Ten rozdział zawiera opis różnych problemów związanych z instalacją, konfiguracją i użyciem HighPerformance produktu interfejsu użytkownika GUIX.  

## <a name="host-considerations"></a>Zagadnienia dotyczące hosta

Projektowanie osadzone jest zwykle wykonywane na komputerach hostów z systemem Windows lub Linux (UNIX). Gdy aplikacja zostanie skompilowana, połączona, a plik wykonywalny jest generowany na hoście, zostanie pobrany na docelowy sprzęt do wykonania.

Zazwyczaj pobieranie docelowe odbywa się z poziomu debugera narzędzia deweloperskiego. Po pobraniu debuger jest odpowiedzialny za zapewnienie docelowej kontroli wykonania (go, zatrzymania, punktu przerwania itp.) oraz dostęp do rejestrów pamięci i procesora.

Większość debugerów narzędzi programistycznych komunikuje się z sprzętem docelowym za pośrednictwem połączeń OCD (on-Chip Debug), takich jak JTAG (IEEE 1149,1) i tryb debugowania w tle (BDM). Debugery komunikują się również z sprzętem docelowym za pomocą połączeń In-Circuit Emulation (lodem). Połączenia OCD i lód zapewniają niezawodne rozwiązania z minimalnym dostępem do docelowego oprogramowania rezydentnego.

Podobnie jak w przypadku zasobów używanych na hoście, kod źródłowy dla GUXI jest dostarczany w formacie ASCII i wymaga około 30 MB miejsca na dysku twardym komputera hosta.

## <a name="target-considerations"></a>Zagadnienia dotyczące obiektów docelowych

GUIX wymaga od 5 kilobajtów do 80 Read-Only KB pamięci (ROM) w miejscu docelowym. Kolejną 10KBytes pamięci (RAM) obiektu docelowego są wymagane dla stosu wątku GUIX i innych struktur danych globalnych.

Ponadto GUIX wymaga użycia czasomierza ThreadX i obiektu mutex ThreadX. Te urządzenia są używane do okresowego przetwarzania i ochrony wątków wewnątrz GUIX.

## <a name="product-distribution"></a>Dystrybucja produktu

Usługę Azure RTO GUIX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/guix/> .

Poniżej znajduje się lista ważnych plików wspólnych dla większości dystrybucji produktów:

| Nazwa pliku&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;| Opis   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| gx_api. h        | Ten plik nagłówkowy C zawiera wszystkie równe systemowe, struktury danych i prototypy usługi. |
| gx_port. h       | Ten plik nagłówkowy C zawiera wszystkie definicje i struktury danych specyficzne dla określonego narzędzia.                                                                                                                                         |
| GX. a (lub GX. lib) | Jest to wersja binarna biblioteki GUIX C. Jest to zwykle kompilowane przez kompilowanie i archiwizowanie dostarczonych plików źródłowych biblioteki GUIX, jednak ta biblioteka może być dostępna w wstępnie skompilowanym formularzu, w zależności od docelowego sprzętu i typu licencji. |
|

> [!IMPORTANT]
> *Wszystkie pliki są w małych przypadkach, co ułatwia konwertowanie poleceń na platformy deweloperskie systemu Linux (UNIX).*

## <a name="guix-installation"></a>Instalacja GUIX

GUIX jest instalowany przez klonowanie repozytorium GitHub na komputerze lokalnym. Poniżej przedstawiono typową składnię tworzenia klonu repozytorium GUIX na komputerze:

```c
    git clone https://github.com/azure-rtos/guix
```

Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku Pobierz na stronie głównej usługi GitHub.

Znajdziesz również instrukcje dotyczące tworzenia biblioteki GUIX na stronie frontonu repozytorium online.

>[!NOTE]  
> *Oprogramowanie aplikacji musi mieć dostęp do pliku biblioteki GUIX, zazwyczaj o nazwie **GX. a** (lub **GX. lib**) i plików dołączanych C **gx_api. h** i **gx_port. h**. W tym celu należy ustawić odpowiednią ścieżkę dla narzędzi programistycznych lub skopiować te pliki do obszaru projektowania aplikacji.*

## <a name="using-guix"></a>Korzystanie z GUIX

Korzystanie z GUIX jest łatwe. Zasadniczo kod aplikacji musi zawierać ***gx_api. h** _ podczas kompilacji i link z biblioteką GUIX _*_GX. a_*_ (lub _ *_GX. lib_*) *.

Do kompilowania aplikacji GUIX są wymagane cztery proste kroki:

| Kroki   | Opis    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Krok &nbsp; 1: | Uwzględnij plik ***gx_api. h*** we wszystkich plikach aplikacji, które korzystają z usług GUIX Services lub struktur danych.                                                               |
| Krok &nbsp; 2: | Zainicjuj system GUIX przez wywołanie ***gx_system_initialize** _ z funkcji _ *_tx_application_define_** lub wątku aplikacji.                       |
| Krok &nbsp; 3. | Utwórz wystąpienie ekranu, utwórz kanwę do wyświetlania i Utwórz okno główne oraz wszystkie inne wymagane okna lub elementy widget.                                 |
| Krok &nbsp; 4. | Skompiluj Źródło aplikacji i połącz je z biblioteką uruchomieniową GUIX ***GX. a** _ (lub _ *_GX. lib_* *). Obraz wyników można pobrać do elementu docelowego i wykonać! |

## <a name="troubleshooting"></a>Rozwiązywanie problemów

Każdy port GUIX jest dostarczany z aplikacją demonstracyjną, która jest wykonywana na określonym sprzęcie ekranu. Ta sama Demonstracja podstawowa jest dostarczana ze wszystkimi wersjami programu GUIX. Zawsze dobrym pomysłem jest rozpoczęcie pierwszego uruchomienia systemu demonstracyjnego.

Jeśli system demonstracyjny nie działa prawidłowo, wykonaj następujące operacje, aby zawęzić ten problem:

1. Określ, jaka część demonstracji jest uruchomiona.

2. Zwiększenie rozmiaru stosu wątku GUIX przez zmianę stałej czasu kompilacji **GX_THREAD_STACK_SIZE** i ponowne skompilowanie biblioteki GUIX

3. Ponownie skompiluj bibliotekę GUIX z odpowiednimi opcjami debugowania wymienionymi w sekcji opcji konfiguracji.

4. Sprawdzanie stanu powrotu ze wszystkich wywołań interfejsu API.

5. Ustal, czy występuje wewnętrzny błąd systemu przez ustawienie punktu przerwania w funkcji ***_gx_system_error_process***. Kod błędu i obiekt wywołujący powinny dać wskazówki co do tego, co może być błędne.

6. Tymczasowo Pomiń wszystkie ostatnie zmiany, aby sprawdzić, czy problem znika lub nie ulegnie zmianie. Takie informacje powinny być przydatne dla inżynierów pomocy technicznej firmy Microsoft.

Postępuj zgodnie z procedurami opisanymi w sekcji "czego potrzebujemy", aby wysłać informacje zebrane z kroków rozwiązywania problemów.

## <a name="configuration-options"></a>Opcje konfiguracji

Podczas kompilowania biblioteki GUIX i aplikacji przy użyciu GUIX istnieje kilka opcji konfiguracji. Te opcje służą do dostrajania rozmiaru biblioteki i zestawu funkcji najlepiej dopasowanego do wymagań aplikacji. Na przykład, jeśli aplikacja będzie mieć tylko jeden wątek korzystający z usług interfejsu API GUIX, należy zdefiniować **GX_DISABLE_MULTITHREAD_SUPPORT** flagę konfiguracji, aby wyeliminować obciążenie związane z ochroną krytycznych sekcji kodu z wywłaszczania przez wiele wątków. Różne flagi konfiguracji można definiować w źródle aplikacji, w wierszu polecenia lub w pliku **_gx_user. h_** .

Za każdym razem, gdy flagi konfiguracji biblioteki GUIX są modyfikowane, należy ponownie skompilować bibliotekę GUIX i moduły aplikacji, aby zmiany konfiguracji zaczęły obowiązywać.

Pełna lista flag konfiguracji została udokumentowana w dodatku H: GUIX Build-Time flagi konfiguracji.

## <a name="guix-version-id"></a>Identyfikator wersji GUIX

Bieżąca wersja programu GUIX jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji podczas wykonywania. Programista może uzyskać wersję GUIX z badania pliku ***gx_port. h** _. Ponadto ten plik zawiera również historię wersji odpowiedniego oprogramowania aplikacji portowej może uzyskać wersję GUIX, badając ciąg globalny _ _ *_gx_version_id_* _ w _ *_gx_port. h_* *.

Oprogramowanie aplikacji może również uzyskać informacje o wersji ze stałych przedstawionych poniżej zdefiniowanych w ***gx_api. h**. * te stałe określają bieżącą wersję produktu według nazwy i wersję główną i pomocniczą produktu.

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
