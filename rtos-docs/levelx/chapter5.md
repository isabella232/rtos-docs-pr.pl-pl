---
title: Rozdział 5 — usługa Azure RTO LevelX i pomoc techniczna
description: ANI pamięć flash składa się z bloków, które są zwykle równo widoczne przez 512 bajtów. Usługa Azure RTO LevelX dzieli każdy lub blok Flash na 512-bajtowe sektory logiczne.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3a0c73c2b45c32bf3f1ef56de684fa83c334b59e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822164"
---
# <a name="chapter-5---azure-rtos-levelx-nor-support"></a>Rozdział 5 — usługa Azure RTO LevelX i pomoc techniczna

ANI pamięć flash składa się z *bloków* , które są zwykle równo widoczne przez 512 bajtów. Brak koncepcji *strony* Flash w programie ani w pamięci flash. Ponadto nie ma bajtów *zapasowych* w wersji ani w pamięci flash, dlatego usługa Azure RTO LevelX musi korzystać z samej pamięci lub samego programu Flash dla wszystkich informacji o zarządzaniu. Bezpośredni dostęp do odczytu jest możliwy w pamięci lub na platformie Flash. Dostęp do zapisu zwykle wymaga specjalnej sekwencji operacji. LUB pamięć Flash może być wielokrotnie zapisywana, co oznacza, że bity są usuwane. Bity w pamięci programu ani Flash można ustawić tylko raz, za pośrednictwem operacji wymazywania bloku.

LevelX dzieli każdy lub blok Flash na 512-bajtowe *sektory* logiczne. Ponadto LevelX używa pierwszych "n" sektorów każdego lub bloku Flash do przechowywania informacji o zarządzaniu. Format informacji o zarządzaniu pamięcią LevelX lub Flash to:

**LevelX i format bloku**

| Przesunięcie bajtów  | Zawartość                     |
| ------------ | ---------------------------- |
| 0            | [Liczba wymazanych bloków]          |
| 4            | [Minimalny zamapowany sektor]      |
| 8            | [Maksymalny zamapowany sektor]      |
| 12           | [Mapa bitowa wolnego sektora]        |
| m            | [Wpis mapowania sektora 0]     |
|              | …                            |
| m + 4 * (n-1)    | [Sektor "n" — wpis mapowania]   |
|              | …                            |
| s            | [Zawartość sektora 0]          |
|              | …                            |
| s + 512 * (n-1) | [Zawartość sektora "n"]         |

*Liczba wymazania bloku* 32-bitowego zawiera liczbę wymazanych bloków. Głównym celem LevelX jest zachowanie liczby wymazywań wszystkich bloków stosunkowo blisko, aby zapobiec przedwczesnemu wykorzystaniu jednego bloku. 32-bitowy *minimalny zamapowany sektor* i pola *maksymalnego zamapowanego sektora* są zapisywane tylko wtedy, gdy wszystkie sektory logiczne w bloku zostały zamapowane i zapisana. Te pola są przydatne do optymalizacji operacji odczytu sektora. Wpis *mapy bitowej wolnego sektora* jest mapą bitową, w której każdy bit zestawu odpowiada niezamapowanemu sektorowi w bloku. To pole służy do zwiększania wydajności wyszukiwania wolnych sektorów. Jest to pole o zmiennej długości, które wymaga jednego słowa dla każdego 32 sektorów w bloku. Tablica *wpisów mapowania sektorów* zawiera informacje o mapowaniu dla każdego sektora w bloku. Każdy wpis ma następujący format:

**Wpis mapowania sektora**

| Liczba bitów: | Znaczenie  |
| ------ | -------- |
| 31     | Prawidłowa flaga. Gdy zestaw i sektor logiczny nie są wszystkie, oznacza to, że mapowanie jest prawidłowe |
| 30     | Flaga przestarzała. Po wyczyszczeniu to mapowanie jest przestarzałe lub jest w stanie przestarzałe. |
| 29     | Zapis mapowania wpisu jest zakończony, gdy ten bit ma wartość 0 |
| 0-28   | Sektor logiczny mapowany na ten sektor fizyczny — bez wszystkich. |

Górny bit pola 32-bitowego (bit 31) jest używany do wskazania, że mapowanie sektora logicznego jest prawidłowe. Jeśli ten bit ma wartość 0, informacje zawarte w tym wpisie (i jego zawartość sektora) nie są już prawidłowe. Kolejny bit-bit 30-jest używany do wskazania, że ten sektor jest w stanie przestarzały, i trwa zapisywanie nowego sektora. Bit 29 służy do wskazania, kiedy zapis mapowania jest zakończony. Jeśli bit 29 ma wartość 0, zakończono zapisywanie wpisu mapowania. Jeśli ustawiono bit 29, wpis mapowania był w trakcie zapisywania. Bity 30 i 29 są używane podczas odzyskiwania po potencjalnej utracie mocy podczas aktualizowania nowego mapowania sektorów. Na koniec niższa 29 bitów (28-0) zawiera numer sektora logicznego dla sektora. Jeśli sektor nie został zmapowany, zostaną ustawione wszystkie bity, tj. wartość 0xFFFFFFFF.

## <a name="nor-driver-requirements"></a>LUB wymagania dotyczące sterowników

LevelX wymaga podstawowego lub Flash sterownika, który jest specyficzny dla bazowej części Flash i implementacji sprzętowej. Sterownik jest określany do LevelX podczas inicjowania za pośrednictwem interfejsu API ***lx_nor_flash_open***. Prototyp sterownika LevelX:

```c
INT nor_driver_initialize(LX_NOR_FLASH *instance);
```

Parametr "*instance*" określa LevelX lub blok sterujący. Funkcja inicjowania sterownika jest odpowiedzialna za konfigurowanie wszystkich innych usług na poziomie sterowników dla skojarzonego wystąpienia LevelX. Usługi wymagane dla każdego LevelXu i wystąpienia są następujące:

- Odczytaj sektor
- Sektor zapisu
- Blokuj wymazywanie
- Blokuj wymazywanie
- Program obsługi błędów systemu

## <a name="driver-initialization"></a>Inicjowanie sterownika

Te usługi są skonfigurowane za pośrednictwem ustawień wskaźników funkcji w wystąpieniu **LX_NOR_FLASH** w ramach funkcji inicjowania sterownika. Funkcja inicjowania sterownika jest również odpowiedzialna za:

1. Określanie adresu podstawowego dla lampy błyskowej.
1. Określanie całkowitej liczby bloków i liczby wyrazów na blok.
1. Bufor pamięci RAM służący do odczytywania jednego sektora Flash (512 bajtów) i wyrównany do ULONG dostępu.

Funkcja inicjacji sterownika, która umożliwia również wykonywanie dodatkowych obowiązków inicjalizacji dotyczących urządzeń i/lub implementacji przed zwróceniem **LX_SUCCESS**.

## <a name="driver-read-sector"></a>Sektor odczytu sterownika

Usługa LevelX lub sterownik "Ready" sektora jest odpowiedzialny za odczytywanie określonego sektora w określonym bloku i na potrzeby lampy błyskowej. Wszystkie błędy sprawdzania i poprawiania logiki są odpowiedzialne za usługę sterownika. Jeśli to się powiedzie, LevelX lub sterownik zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, LevelX lub sterownik zwraca *LX_ERROR*. Prototyp usługi LevelX lub sterownika "Read sektora" to:

```c
INT nor_driver_read_sector(
    ULONG *flash_address,
    ULONG *destination, 
    ULONG words);
```

Gdzie "*flash_address*" określa adres sektora logicznego w bloku i i Flash pamięci oraz "*miejsce docelowe*" i "*słowa*" określają miejsce umieszczenia zawartości sektora oraz liczbę słów 32-bitowych do odczytania.

## <a name="driver-write-sector"></a>Sektor zapisu sterowników

Usługa LevelX lub "sektora zapisu" jest odpowiedzialna za pisanie określonego sektora w bloku i na potrzeby lampy błyskowej. Wszystkie sprawdzanie błędów jest odpowiedzialne za usługę sterownika. Jeśli to się powiedzie, LevelX lub sterownik zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, LevelX lub sterownik zwraca **LX_ERROR**. Prototyp usługi LevelX lub "sektora zapisu" jest:

```c
INT nor_driver_write_sector(
    ULONG *flash_address,
    ULONG *source, 
    ULONG words);
```

Gdzie "*flash_address*" określa adres sektora logicznego w bloku i lub flash pamięci, a "*Źródło*" i "*słowa*" określają Źródło zapisu oraz liczbę słów 32-bitowych do zapisu.

> [!NOTE]
> LevelX opiera się na sterowniku, aby sprawdzić, czy sektor zapisu zakończył się pomyślnie. Jest to zazwyczaj wykonywane przez odczytanie zaprogramowanej wartości, aby upewnić się, że jest ona zgodna z żądaną wartością do zapisania.

## <a name="driver-block-erase"></a>Blok sterownika — wymazywanie

Usługa LevelX i sterownik "Blokuj wymazywanie" jest odpowiedzialny za wymazywanie określonego bloku i błysku. Jeśli to się powiedzie, LevelX lub sterownik zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, LevelX lub sterownik zwraca **LX_ERROR**. Prototyp usługi LevelX lub sterownika "Blokuj wymazywanie" jest:

```c
INT nor_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Gdzie "*Block*" identyfikuje, które nie są blokowane. Parametr "*erase_count*" jest dostarczany do celów diagnostycznych. Na przykład sterownik może chcieć ostrzec inną część oprogramowania aplikacji, gdy liczba wymazywań przekroczy określony próg.

> [!NOTE]
> LevelX polega na sterowniku, aby sprawdzić wszystkie bajty bloku, aby upewnić się, że zostały wymazane (zawierają wszystkie).

## <a name="driver-block-erased-verify"></a>Blok sterownika został wymazany

Usługa LevelX lub sterownik "Blokuj wymazywanie weryfikacji" jest odpowiedzialny za sprawdzenie, czy określony blok i błysk zostały wymazane. W przypadku wymazania LevelX lub sterownik zwraca **LX_SUCCESS**. Jeśli blok nie zostanie wymazany, LevelX lub sterownik zwraca **LX_ERROR**. Prototyp usługi LevelX lub sterownika "Blokuj wymazywane sprawdzanie" to:

```c
INT nor_driver_block_erased_verify(ULONG block);
```

Gdzie "*Block*" określa, który blok, aby sprawdzić, czy został wymazany.

> [!NOTE]
> LevelX polega na sterowniku, aby sprawdzić wszystkie bajty określonego, aby upewnić się, że zostały wymazane (zawierają wszystkie).

## <a name="driver-system-error"></a>Błąd systemu sterownika

Usługa LevelX lub sterownik programu obsługi błędów systemu jest odpowiedzialny za ustawienie obsługi błędów systemu wykrytych przez LevelX. Przetwarzanie w tej procedurze jest zależne od aplikacji. Jeśli to się powiedzie, LevelX lub sterownik zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, LevelX lub sterownik zwraca **LX_ERROR**. Prototyp usługi LevelX lub sterownika "Error system" jest następujący:

```c
INT nor_driver_system_error(UINT error_code);
```

Gdzie "*error_code*" reprezentuje błąd, który wystąpił.

## <a name="nor-simulated-driver"></a>LUB symulowany sterownik

LevelX zapewnia symulowane lub nieflash sterownika, który po prostu używa pamięci RAM do symulowania operacji części a i programu Flash. Domyślnie niesymulowany sterownik zawiera 8 i bloki Flash z 16 512-bajtowymi sektorami na blok.

Funkcja inicjalizacji sterownika symulowane i Flash to ***lx_nor_flash_simulator_initialize** _ i jest zdefiniowana w _ *_lx_nor_flash_simulator. c_* *. Ten sterownik zapewnia również dobry szablon do pisania określonych lub sterowników Flash.

## <a name="nor-filex-integration"></a>ANI integracja FileX

Jak wspomniano wcześniej, LevelX nie polega na FileX dla operacji. Wszystkie interfejsy API LevelX mogą być wywoływane bezpośrednio przez oprogramowanie aplikacji do przechowywania/pobierania nieprzetworzonych danych do sektorów logicznych dostarczonych przez LevelX. Jednak LevelX obsługuje również FileX.

Plik ***fx_nor_flash_simulated_driver. c*** zawiera przykładowy sterownik FileX do użycia z symulacją i funkcją Flash. Sterownik programu ani Flash FileX dla LevelX zapewnia dobry punkt wyjścia do pisania niestandardowych sterowników FileX.

> [!NOTE]
> FileX ani format Flash powinny mieć jeden pełny rozmiar bloku sektorów mniejszy niż wartość i błysk. Pomoże to zapewnić najlepszą wydajność podczas przetwarzania poziomu zużycia. Dodatkowe techniki zwiększające wydajność zapisu w algorytmie LevelXego zużycia są następujące:
> 1. Upewnij się, że wszystkie zapisy mają dokładnie jeden lub więcej klastrów o rozmiarze i Rozpocznij na dokładnych granicach klastra.
> 2. Przed wykonaniem operacji zapisu dużych plików za pośrednictwem klasy FileX ***Fx_file_allocate*** interfejsów API należy wstępnie przydzielić klastry.
> 3.  Okresowe korzystanie z ***lx_nor_flash_defragment*** w celu zwolnienia możliwie największej liczby lub bloków, a tym samym zwiększenie wydajności zapisu.
> 4. Upewnij się, że sterownik FileX jest włączony, aby otrzymywać informacje o sektorach wydania i żądania wysyłane do sterownika w celu wydania sektorów są obsługiwane w sterowniku przez wywołanie ***lx_nor_flash_sector_release***.
