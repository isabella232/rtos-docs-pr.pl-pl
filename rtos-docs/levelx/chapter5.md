---
title: Rozdział 5 — obsługa Azure RTOS LevelX ANI
description: Pamięć flash ANI nie składa się z bloków, które zwykle są równomiernie podzielne przez 512 bajtów. Azure RTOS LevelX dzieli każdy blok flash NOR na 512-bajtowe sektory logiczne.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d5d06fa66f0cae29eeb2a89560704b2ef510597e44a565499bf672a75555f208
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790568"
---
# <a name="chapter-5---azure-rtos-levelx-nor-support"></a>Rozdział 5 — obsługa Azure RTOS LevelX ANI

Pamięć flash ANI nie składa się *z bloków,* które zwykle są równomiernie podzielne przez 512 bajtów. Nie ma koncepcji strony flash w *PAMIĘCI* FLASH ANI . Ponadto w pamięci  flash ANI nie ma żadnych bajtów zapasowych, dlatego Azure RTOS LevelX musi używać samej pamięci flash NOR do wszystkich informacji dotyczących zarządzania. Bezpośredni dostęp do odczytu jest możliwy w pamięci FLASH ANI . Dostęp do zapisu zwykle wymaga specjalnej sekwencji operacji. Pamięć flash NIE może być zapisywana wielokrotnie, pod ile bity są czyszowane. Bity w pamięci flash NOR można ustawić tylko raz za pośrednictwem operacji wymazywania bloku.

LevelX dzieli każdy blok flash NOR na 512-bajtowe sektory *logiczne*. Ponadto levelX używa pierwszych "n" sektorów każdego bloku flash NOR do przechowywania informacji o zarządzaniu. Format informacji o zarządzaniu pamięcią flash LevelX NOR jest:

**Format bloku LevelX NOR**

| Przesunięcie bajtów  | Zawartość                     |
| ------------ | ---------------------------- |
| 0            | [Blokuj liczbę wymazywania]          |
| 4            | [Minimum Zamapowany sektor]      |
| 8            | [Maksymalna zmapowana sektora]      |
| 12           | [Free Sector Bit Map]        |
| m            | [Wpis mapowania sektora 0]     |
|              | …                            |
| m+4*(n-1)    | [Sektor "n" wpis mapowania]   |
|              | …                            |
| s            | [Zawartość sektora 0]          |
|              | …                            |
| s+512*(n-1) | [Zawartość sektora "n"]         |

32-bitowa *liczba wymazywania* bloków zawiera liczbę wymazanych bloków. Głównym celem narzędzia LevelX jest utrzymanie względnie zbliżonej liczby wymazanych bloków, aby zapobiec przedwcześnie wyekserowania żadnego z bloków. 32-bitowe pola *Minimalne*  zamapowane sektory i Maksymalne zmapowane sektory są zapisywane tylko wtedy, gdy wszystkie sektory logiczne w bloku zostały zamapowane i zapisane w. Te pola są przydatne do optymalizacji operacji odczytu sektora. Wpis *mapa bitów wolnych* sektorów jest mapą bitową, gdzie każdy bit zestawu odpowiada niezamapowanemu sektorowi w bloku. To pole służy do tego, aby wyszukiwanie wolnych sektorów było bardziej wydajne. Jest to pole o zmiennej długości, które wymaga jednego wyrazu dla każdego 32 sektorów w bloku. Tablica *Entry mapowania sektorów* zawiera informacje o mapowaniu dla każdego sektora w bloku. Każdy wpis ma następujący format:

**Wpis mapowania sektorów**

| Bity | Znaczenie  |
| ------ | -------- |
| 31     | Prawidłowa flaga. W przypadku ustawienia i sektora logicznego nie wszystkie z nich wskazują, że mapowanie jest prawidłowe |
| 30     | Przestarzała flaga. Gdy to mapowanie jest jasne, jest przestarzałe lub trwa jego przestarzałe. |
| 29     | Zapis wpisu mapowania jest ukończony, gdy ten bit ma 0 |
| 0-28   | Sektor logiczny zamapowany na ten sektor fizyczny — gdy nie wszystkie z nich. |

Górny bit pola 32-bitowego (bit 31) służy do wskazywania, że mapowanie sektora logicznego jest prawidłowe. Jeśli ten bit ma wartość 0, informacje zawarte w tym wpisie (i odpowiedniej zawartości sektora) nie są już prawidłowe. Następny bit — bit 30 — służy do wskazywania, że ten sektor jest w trakcie procesu przestarzałego i jest pisany nowy sektor. Bit 29 służy do wskazywania, kiedy zapis wpisu mapowania jest ukończony. Jeśli bit 29 ma 0, zapis wpisu mapowania jest ukończony. Jeśli bit 29 jest ustawiony, wpis mapowania był w trakcie pisano. Bity 30 i 29 są używane do odzyskiwania po potencjalnej utracie zasilania podczas aktualizowania nowego mapowania sektorów. Na koniec niższe 29-bitowe (28-0) zawierają numer sektora logicznego dla sektora. Jeśli sektor nie został zamapowany, wszystkie bity zostaną ustawione, tj. będzie miał wartość 0xFFFFFFFF.

## <a name="nor-driver-requirements"></a>Wymagania dotyczące sterowników NOR

LevelX wymaga źródłowego sterownika flash NOR, który jest specyficzny dla bazowej implementacji sprzętu i części flash. Sterownik jest określony na LevelX podczas inicjowania za pośrednictwem interfejsu API ***lx_nor_flash_open***. Prototyp sterownika LevelX to:

```c
INT nor_driver_initialize(LX_NOR_FLASH *instance);
```

Parametr "*instance*" określa blok sterujący LevelX NOR. Funkcja inicjowania sterownika jest odpowiedzialna za konfigurowanie wszystkich innych usług na poziomie sterownika dla skojarzonego wystąpienia LevelX. Usługi wymagane dla każdego wystąpienia LevelX NOR są:

- Sektor odczytu
- Sektor zapisu
- Blokuj wymazywanie
- Blokuj wymazane weryfikacje
- Program obsługi błędów systemu

## <a name="driver-initialization"></a>Inicjowanie sterownika

Te usługi są konfigurowe za pośrednictwem ustawiania wskaźników funkcji LX_NOR_FLASH **wystąpieniu** w ramach funkcji inicjowania sterownika. Funkcja inicjowania sterownika jest również odpowiedzialna za:

1. Określanie podstawowego adresu flash.
1. Określanie łącznej liczby bloków i liczby wyrazów na blok.
1. Bufor pamięci RAM do odczytywania jednego sektora pamięci flash (512 bajtów) i wyrównany w celu uzyskania dostępu do programu ULONG.

Funkcja inicjowania sterownika prawdopodobnie wykonuje również dodatkowe obowiązki dotyczące inicjowania urządzenia i/lub implementacji przed zwróceniem **LX_SUCCESS**.

## <a name="driver-read-sector"></a>Sektor odczytu sterowników

Usługa "sektora odczytu" sterownika LevelX NOR jest odpowiedzialna za odczytywanie określonego sektora w określonym bloku flash NOR. Za całą logikę sprawdzania i poprawiania błędów odpowiada usługa sterowników. Jeśli to się powiedzie, sterownik LevelX NOR zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX NOR zwróci *LX_ERROR*. Prototyp usługi "sektora odczytu" sterownika LevelX NOR jest:

```c
INT nor_driver_read_sector(
    ULONG *flash_address,
    ULONG *destination, 
    ULONG words);
```

Gdzie "*flash_address*" określa adres sektora logicznego w bloku flash NOR pamięci i "*docelowy*" i "*wyrazy*" określ, gdzie umieścić zawartość sektora i ile słów 32-bitowych do odczytania.

## <a name="driver-write-sector"></a>Sektor zapisu sterowników

Usługa "sektora zapisu" sterownika LevelX NOR jest odpowiedzialna za zapisywanie określonego sektora w bloku flash NOR. Wszystkie kontrole błędów są odpowiedzialne za usługę sterowników. Jeśli to się powiedzie, sterownik LevelX NOR zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX NOR zwróci **LX_ERROR**. Prototyp usługi "sektora zapisu" sterownika LevelX NOR jest:

```c
INT nor_driver_write_sector(
    ULONG *flash_address,
    ULONG *source, 
    ULONG words);
```

Gdzie "*flash_address*" określa adres sektora logicznego w bloku flash NOR pamięci oraz "*source*" i "*words*" określ źródło zapisu oraz liczbę słów 32-bitowych do zapisu.

> [!NOTE]
> PoziomX opiera się na sterowniku, aby sprawdzić, czy sektor zapisu został pomyślnie. Zwykle jest to wykonywane przez odczytanie zaprogramowanej wartości, aby upewnić się, że pasuje ona do żądanej wartości do napisano.

## <a name="driver-block-erase"></a>Wymazywanie bloku sterownika

Usługa "blokuj wymazywanie" sterownika LevelX NOR jest odpowiedzialna za wymazywanie określonego bloku flash NOR. Jeśli to się powiedzie, sterownik LevelX NOR zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX NOR zwraca **LX_ERROR**. Prototyp usługi "blokuj wymazywanie" sterownika LevelX NOR to:

```c
INT nor_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Gdzie "*block*" określa, który blok ANI wymazać. Parametr *"erase_count"* jest dostarczany do celów diagnostycznych. Na przykład sterownik może chcieć powiadamiać inną część oprogramowania aplikacji, gdy liczba wymazywania przekroczy określony próg.

> [!NOTE]
> LevelX polega na sterowniku, aby zbadać wszystkie bajty bloku, aby upewnić się, że zostały usunięte (zawierają wszystkie).

## <a name="driver-block-erased-verify"></a>Weryfikacja wymazanych bloków sterowników

Usługa "blokuj wymazaną weryfikację" sterownika LevelX NOR jest odpowiedzialna za sprawdzenie, czy określony blok pamięci flash NOR został wymazany. Jeśli został usunięty, sterownik LevelX NOR zwraca **LX_SUCCESS**. Jeśli blok nie zostanie wymazany, sterownik LevelX NOR zwróci **wartość LX_ERROR**. Prototyp usługi "blokuj weryfikację wymazaną" sterownika LevelX NOR to:

```c
INT nor_driver_block_erased_verify(ULONG block);
```

Gdzie "*bloku*" określa, który blok, aby sprawdzić, czy jest usunięty.

> [!NOTE]
> LevelX polega na sterowniku, aby sprawdzić wszystkie bajty określonego, aby upewnić się, że są one wymazane (zawierają wszystkie).

## <a name="driver-system-error"></a>Błąd systemu sterowników

Usługa "obsługi błędów systemu" sterownika LevelX NOR jest odpowiedzialna za ustawianie obsługi błędów systemowych wykrytych przez platformę LevelX. Przetwarzanie w tej procedury jest zależne od aplikacji. Jeśli to się powiedzie, sterownik LevelX NOR zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX NOR zwraca **LX_ERROR**. Prototyp usługi "błędu systemu" sterownika LevelX NOR to:

```c
INT nor_driver_system_error(UINT error_code);
```

Gdzie "*error_code*" reprezentuje błąd, który wystąpił.

## <a name="nor-simulated-driver"></a>Symulowany sterownik NOR

LevelX udostępnia symulowany sterownik flash NOR, który po prostu używa pamięci RAM do symulowania działania części flash ANI. Domyślnie symulowany sterownik NOR udostępnia 8 bloków flash NOR z 16 512 bajtami sektorów na blok.

Funkcja inicjowania symulowanego sterownika flash NOR to ***lx_nor_flash_simulator_initialize** _ i jest zdefiniowana w _*_lx_nor_flash_simulator.c_**. Ten sterownik zawiera również dobry szablon do pisania określonych sterowników flash NOR.

## <a name="nor-filex-integration"></a>INTEGRACJA NOR FileX

Jak wspomniano wcześniej, poziom LevelX nie polega na pliku FileX w operacji. Wszystkie interfejsy API LevelX mogą być wywoływane bezpośrednio przez oprogramowanie aplikacji w celu przechowywania/pobierania danych pierwotnych do sektorów logicznych dostarczanych przez levelX. Jednak system LevelX obsługuje również plik FileX.

Plik ***fx_nor_flash_simulated_driver.c zawiera*** przykładowy sterownik FileX do użycia z symulacją flash NOR. Sterownik NOR flash FileX dla LevelX zapewnia dobry punkt wyjścia do pisania niestandardowych sterowników FileX.

> [!NOTE]
> Format flash FileX NOR powinien mieć rozmiar jednego pełnego bloku sektorów mniejszy niż rozmiar zapewniany przez flash NOR. Pomoże to zapewnić najlepszą wydajność podczas przetwarzania na poziomie zużycia. Dodatkowe techniki poprawiające wydajność zapisu w algorytmie levelingu zużycia LevelX obejmują:
> 1. Upewnij się, że wszystkie zapis mają dokładnie jeden lub więcej klastrów o rozmiarze i rozpocznij od dokładnych granic klastra.
> 2. Wstępnie przydziel klastry przed wykonaniem operacji zapisu dużych plików za pośrednictwem klasy fx_file_allocate ***FileX*** interfejsów API.
> 3.  Okresowe użycie ***lx_nor_flash_defragment*** w celu jak najbardziej wolnego użycia bloków ANI i w związku z tym zwiększenia wydajności zapisu.
> 4. Upewnij się, że sterownik FileX jest włączony, aby odbierać informacje o sektorach wydania, a żądania do sterownika dotyczące zwalniania sektorów są obsługiwane w sterowniku przez wywołanie lx_nor_flash_sector_release ***.***
