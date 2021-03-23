---
title: Obsługa usługi Azure RTO LevelX ni
description: NI pamięć flash jest często używana w LevelX w przypadku dużych magazynów danych, które są typowymi systemami plików.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3286e4ea7f16b28ff55fc95a87a1e0c313ec4240
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822171"
---
# <a name="chapter-3---azure-rtos-levelx-nand-support"></a>Rozdział 3 — Obsługa platformy Azure RTO LevelX ni

NI pamięć flash jest często wykorzystywana w przypadku dużych magazynów danych, które są typowymi systemami plików. Pamięć ni składa się z *bloków*. W każdym bloku ni jest serią *stron*. Bloki ni są wymazywane, co oznacza, że wszystkie strony w bloku ni są wymazywane (ustawiane na wszystkie). Każda Strona bloku ni ma zestaw *bajtów zapasowych* , które są używane przez usługę Azure RTO LevelX do księgowania, niewłaściwego zarządzania blokami i wykrywania błędów. Strony blokowe ni są dostępne w różnych rozmiarach. Najczęstsze rozmiary stron to: 

| **Rozmiar strony** | **Bajty zapasowe** |
| ------------- | --------------- |
| 256           | 8               |
| 512           | 16              |
| 2048          | 64              |

Pamięć ni różni się od programu lub pamięci, w której nie ma bezpośredniego dostępu, czyli nie można odczytać pamięci ni bezpośrednio z procesora, takiego jak lub pamięci. Pamięć ni można zapisywać tylko po wymazaniu ograniczonej liczby razy. Ponownie różni się od programu lub pamięci, które mogą być pisane nieograniczoną liczbę razy, gdy żądanie zapisu jest czyszczone. Na koniec bajty zapasowe skojarzone z każdą stroną są unikatowe dla ni Flash. Typowe konfiguracje zapasowych bajtów są przedstawione w poniższej tabeli.

| **Bajty zapasowe** | **Liczby bajtów** | **Konfiguracja**     |
| ------------------------- | -------------- | --------------------- |
| 8                         | Bajty 0-2:     | Bajty ECC             |
|                           | Bajty 3, 4, 6, 7: | Mapowanie sektora LevelX |
|                           | Bajt 5:        | Zła flaga bloku        |
| 16                        | Bajty 0-3, 6-7: | Bajty ECC             |
|                           | Bajty 8-11:    | Mapowanie sektora LevelX |
|                           | Bajty 12-15:   | Nieużywane                |
|                           | Bajt 5:        | Zła flaga bloku        |
| 64                        | Bajt 0:        | Zła flaga bloku        |
|                           | Bajty 2-5:     | Mapowanie sektora LevelX |
|                           | Bajty 6-39:    | Nieużywane                |
|                           | Bajty 40-63:   | Bajty ECC             |

LevelX wykorzystuje 4 zapasowe bajty każdej strony ni do śledzenia sektora logicznego zamapowanego na fizyczną stronę ni. Te 4 bajty są używane do implementacji 32-bitową liczbę całkowitą bez znaku przy użyciu zastrzeżonego formatu LevelX. Górny bit pola 32-bitowego (bit 31) jest używany do wskazania, że mapowanie sektora logicznego na stronę jest prawidłowe. Jeśli ten bit ma wartość 0, informacje na tej stronie nie są już prawidłowe. Następny bit — bit 30 — służy do wskazywania, że ta strona jest w toku, a nowy sektor jest zapisywany. Bit 29 służy do wskazania, kiedy zapis mapowania jest zakończony. Jeśli bit 29 ma wartość 0, zakończono zapisywanie wpisu mapowania. Jeśli ustawiono bit 29, wpis mapowania był w trakcie zapisywania. Bity 30 i 29 są używane podczas odzyskiwania po potencjalnej utracie mocy podczas aktualizowania nowej strony Flash. Na koniec niższa 29 bitów (28-0) zawiera numer sektora logicznego dla strony.

**LevelX — wpis mapowania**

| Liczba bitów: | Znaczenie |
| ------ | ------- |
| 31     | Prawidłowa flaga. Gdy zestaw i sektor logiczny nie są wszystkie, oznacza to, że mapowanie jest prawidłowe |
| 30     | Flaga przestarzała. Po wyczyszczeniu to mapowanie jest przestarzałe lub jest w stanie przestarzałe. |
| 29     | Zapis mapowania wpisu jest zakończony, gdy ten bit ma wartość 0 |
| 0-28   | Sektor logiczny zmapowany na Tę stronę fizyczną — gdy nie wszystkie te. |

LevelX używa również pierwszej strony każdego bloku ni dla liczby wymazywania bloku oraz listy mapowanych stron, gdy blok jest pełny. Poniżej przedstawiono format pierwszej strony bloku ni w LevelX:

| LevelX bloku strony 0 |
|:--------------------------:|
| [Liczba wymazanych bloków]        |
| [Mapowanie sektorów strony 1]    |
| ...                        |
| Mapowanie sektora [Strona "n"]  |
| [0xF0F0F0F0]               |

> [!NOTE]
> Informacje o mapowaniu stron są zapisywane tylko wtedy, gdy blok jest pełny, tj. wszystkie strony bloku zostały zapisaną w. Umożliwia to szybsze wyszukiwanie bezpłatnych stron i mapowań sektorów logicznych w czasie wykonywania.

## <a name="nand-bad-block-support"></a>Obsługa nieprawidłowego bloku ni

Pamięć ni jest również prawdopodobnie nieprawidłowymi blokadami lub pamięcią. Jest to bardzo duże działanie, ponieważ ni producenci mogą zwiększyć wzrost, umożliwiając korzystanie z nieprawidłowych bloków i wymaganie, aby oprogramowanie działało w przypadku takich nieprawidłowych bloków. LevelX obsługuje ni niewłaściwe zarządzanie blokami przez proste mapowanie wokół nieprawidłowych bloków.

Program LevelX udostępnia również interfejsy API dla 256-bajtowych kodów korekcji błędów (ECC) dla podstawowego sterownika LevelX, które będą używane do obliczania nowych kodów ECC lub w celu przeprowadzenia 1-bitowej korekcji błędów podczas odczytywania stron w każdej sekcji 256-bajtowej strony.

## <a name="nand-driver-requirements"></a>Wymagania dotyczące sterownika ni

LevelX wymaga podstawowego sterownika Flash ni, który jest specyficzny dla bazowej części Flash i implementacji sprzętowej. Sterownik jest określany do LevelX podczas inicjowania za pośrednictwem interfejsu API ***lx_nand_flash_open***. Prototyp sterownika LevelX jest następujący.

```c
INT nand_driver_initialize(LX_NAND_FLASH *instance);
```

Parametr *instance* określa blok sterowania LevelX ni. Funkcja inicjowania sterownika jest odpowiedzialna za konfigurowanie wszystkich innych usług na poziomie sterowników dla skojarzonego wystąpienia LevelX. Na poniższej liście przedstawiono usługi wymagane przez każde wystąpienie LevelX ni.

- Strona odczytu
- Strona zapisu
- Blokuj wymazywanie
- Blokuj wymazywanie
- Strona została wymazana
- Pobieranie stanu blokowania
- Zablokuj ustawienie stanu
- Pobieranie dodatkowych bajtów
- Zablokuj dodatkowe bajty
- Program obsługi błędów systemu

## <a name="driver-initialization"></a>Inicjowanie sterownika

Te usługi są skonfigurowane za pośrednictwem ustawień wskaźników funkcji w wystąpieniu **LX_NAND_FLASH** w ramach funkcji inicjowania sterownika. Funkcja inicjacji sterownika określa również łączną liczbę bloków, stron na blok, bajty na stronę, a obszar pamięci RAM jest wystarczająco duży, aby można było odczytać jedną stronę do pamięci. Funkcja inicjacji sterownika, która umożliwia również wykonywanie dodatkowych obowiązków inicjalizacji dotyczących urządzeń i/lub implementacji przed zwróceniem **LX_SUCCESS**.

## <a name="driver-read-page"></a>Strona odczytu sterownika

Usługa LevelX ni Driver "Read Page" jest odpowiedzialna za odczytywanie określonej strony w określonym bloku ni Flash. Wszystkie błędy sprawdzania i poprawiania logiki są odpowiedzialne za usługę sterownika. Jeśli to się powiedzie, sterownik LevelX ni zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX ni zwraca **LX_ERROR**. Poniżej przedstawiono prototyp usługi LevelX ni sterownika.

```c
INT nand_driver_read_page(
    ULONG block,
    ULONG page,
    ULONG *destination, 
    ULONG words);
```

Miejsce, w którym *blok* i *Strona* identyfikują, którą stronę odczytać i *miejsce docelowe* oraz *słowa* określają miejsce umieszczenia zawartości strony oraz liczbę słów 32-bitowych do odczytania.

## <a name="driver-write-page"></a>Strona zapisu sterownika

Usługa LevelX ni Driver "Write Page" jest odpowiedzialna za pisanie określonej strony w określonym bloku ni Flash. Wszystkie sprawdzanie błędów i obliczenia ECC są odpowiedzialne za usługę sterownika. Jeśli to się powiedzie, sterownik LevelX ni zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX ni zwraca **LX_ERROR**. Poniżej przedstawiono prototyp usługi LevelX ni sterownika "Write Page".

```c
INT nand_driver_write_page(
    ULONG block, 
    ULONG page,
    ULONG *source, 
    ULONG words);
```

Miejsce, w którym *blok* i *Strona* identyfikują, która strona do *zapisu i* *słowa* określają Źródło zapisu oraz liczbę słów 32-bitowych do zapisu.

> [!NOTE]
> LevelX polega na sterowniku wykrywania błędów niskiego poziomu podczas zapisywania na stronie Flash, która zwykle obejmuje odczytywanie strony i porównywanie z buforem zapisu w celu upewnienia się, że zapis zakończył się pomyślnie.

## <a name="driver-block-erase"></a>Blok sterownika — wymazywanie

Usługa LevelX ni Driver "Block Erase" jest odpowiedzialna za wymazywanie określonego bloku ni Flash. Jeśli to się powiedzie, sterownik LevelX ni zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX ni zwraca **LX_ERROR**. Prototyp usługi LevelX ni sterownika "Blokuj wymazywanie" jest następujący:

```c
INT nand_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

*Blok* WHERE wskazuje, który blok należy wymazać. Parametr *erase_count* jest udostępniany do celów diagnostycznych. Na przykład sterownik może chcieć ostrzec inną część oprogramowania aplikacji, gdy liczba wymazywań przekroczy określony próg.

> [!NOTE]
> LevelX opiera się na sterowniku wykrywania błędów niskiego poziomu, gdy blok zostanie wymazany, co zazwyczaj polega na zapewnieniu, że wszystkie strony bloku są wszystkie.

## <a name="driver-block-erased-verify"></a>Blok sterownika został wymazany

Usługa LevelX ni Driver "Block Erase verify" jest odpowiedzialna za sprawdzenie, czy określony blok ni błysku jest wymazany. W przypadku wymazania sterownik LevelX ni zwraca **LX_SUCCESS**. Jeśli blok nie zostanie wymazany, sterownik LevelX ni zwraca **LX_ERROR**. Prototyp usługi LevelX ni Driver "Block Erase verify" to:

```c
INT nand_driver_block_erased_verify(ULONG block);
```

*Blok* WHERE określa, który blok sprawdza, czy jest wymazany.

> [!NOTE]
> LevelX opiera się na sterowniku, aby sprawdzić wszystkie strony i wszystkie bajty każdej strony, w tym bajty zapasowe i dane, aby upewnić się, że zostały wymazane (zawierają wszystkie).

## <a name="driver-page-erased-verify"></a>Zweryfikowano stronę sterownika

Usługa LevelX ni sterownika "Strona została zweryfikowana" jest odpowiedzialna za sprawdzenie, czy określona strona określonego bloku ni lampy błyskowej została wymazana. W przypadku wymazania sterownik LevelX ni zwraca **LX_SUCCESS**. Jeśli strona nie zostanie wymazana, sterownik LevelX ni zwraca **LX_ERROR**. Prototyp sterownika LevelX ni "Page Erase verify" jest:

```c
INT nand_driver_page_erased_verify(
    ULONG block,  
    ULONG page);
```
*Blok* WHERE określa, który blok i *Strona* określa stronę, aby sprawdzić, czy została wymazana.

> [!NOTE]
> LevelX polega na sterowniku, aby sprawdzić wszystkie bajty określonej strony, w tym bajty zapasowe i dane, aby upewnić się, że zostały wymazane (zawierają wszystkie).

## <a name="driver-block-status-get"></a>Pobieranie stanu bloku sterownika

Usługa LevelX ni Driver "Block status Get" jest odpowiedzialna za pobieranie nieprawidłowej flagi bloku określonego bloku ni Flash. Jeśli to się powiedzie, sterownik LevelX ni zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX ni zwraca **LX_ERROR**. Prototyp usługi LevelX ni Driver "Block status Get" jest następujący: pokazano poniżej.

```c
INT nand_driver_block_status_get(
    ULONG block,  
    UCHAR *bad_block_byte);
```

*Blok* WHERE określa, który blok i *bad_block_byte* określa miejsce docelowe dla nieprawidłowej flagi bloku.

## <a name="driver-block-status-set"></a>Ustawienie stanu bloku sterownika

Usługa LevelX ni Driver "Block status Set" jest odpowiedzialna za ustawienie nieprawidłowej flagi bloku określonego bloku ni Flash. Jeśli to się powiedzie, sterownik LevelX ni zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX ni zwraca **LX_ERROR**. Prototyp usługi LevelX ni Driver "Block status Set":

```c
INT nand_driver_block_status_set(
    ULONG block,
    UCHAR bad_block_byte);
```

*Blok* WHERE określa, który blok i *bad_block_byte* określa wartość nieprawidłowej flagi bloku.

## <a name="driver-block-extra-bytes-get"></a>Pobieranie dodatkowych bajtów w bloku sterownika

Usługa LevelX ni Driver "Blokuj dodatkową liczbę bajtów" jest odpowiedzialna za pobieranie dodatkowych bajtów skojarzonych z konkretną stroną określonego bloku ni Flash. Jeśli to się powiedzie, sterownik LevelX ni zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX ni zwraca **LX_ERROR**. Prototyp usługi LevelX ni Driver "Block Extra Bytes Get" to:

```c
INT nand_driver_block_extra_bytes_get(
    ULONG block,  
    ULONG page, 
    UCHAR *destination, 
    UINT size);
```

*Blok* WHERE określa, który blok, *Strona* określa określoną stronę i *miejsce docelowe* określa miejsce docelowe dla dodatkowych bajtów. *Rozmiar* parametru określa liczbę dodatkowych bajtów do pobrania.

## <a name="driver-block-extra-bytes-set"></a>Zestaw dodatkowych bajtów bloku sterownika

Usługa LevelX ni Driver "Block Extra Bytes Set" jest odpowiedzialna za ustawienie dodatkowych bajtów na określonej stronie określonego bloku ni Flash. Jeśli to się powiedzie, sterownik LevelX ni zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX ni zwraca **LX_ERROR**. Prototyp usługi LevelX ni Driver "Block Extra Bytes Set" to:

```c
INT nand_driver_block_extra_bytes_set(
    ULONG block,  
    ULONG page, 
    UCHAR *source, 
    UINT size);
```

*Blok* WHERE określa, który blok, *Strona* określa określoną stronę i *Źródło* określa źródło dodatkowych bajtów. *Rozmiar* parametru określa liczbę dodatkowych bajtów do ustawienia.

## <a name="driver-system-error"></a>Błąd systemu sterownika

Usługa programu obsługi błędów systemu LevelX ni jest odpowiedzialna za ustawienie obsługi błędów systemu wykrytych przez LevelX. Przetwarzanie w tej procedurze jest zależne od aplikacji. Jeśli to się powiedzie, sterownik LevelX ni zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik LevelX ni zwraca **LX_ERROR**. Prototyp usługi LevelX ni sterownika "System Error" jest następujący:

```c
INT nand_driver_system_error(
    UINT error_code,  
    ULONG block, 
    ULONG page);
```

*Blok* WHERE określa, który blok i *Strona* określa określoną stronę, w której wystąpił błąd reprezentowany przez *error_code* .

## <a name="nand-simulated-driver"></a>Sterownik symulowany ni

LevelX udostępnia symulowany sterownik Flash ni, który po prostu używa pamięci RAM do symulowania operacji części Flash ni. Domyślnie ni symulowany sterownik zawiera 8 ni bloków Flash z 16 stronami na blok i 2048 bajtów na stronę.

Symulowana Funkcja inicjowania sterownika ni Flash to ***lx_nand_flash_simulator_initialize** _ i jest zdefiniowana w _ *_lx_nand_flash_simulator. c_* *. Ten sterownik zapewnia również dobry szablon do pisania określonych sterowników ni Flash.

## <a name="nand-filex-integration"></a>Integracja z programem ni FileX

Jak wspomniano wcześniej, LevelX nie polega na FileX dla operacji. Wszystkie interfejsy API LevelX mogą być wywoływane bezpośrednio przez oprogramowanie aplikacji do przechowywania/pobierania nieprzetworzonych danych do sektorów logicznych dostarczonych przez LevelX. Jednak LevelX obsługuje również FileX.

Plik ***fx_nand_flash_simulated_driver. c*** zawiera przykładowy sterownik FileX do użycia z symulacją Flash ni. Interesujący aspekt tego sterownika polega na tym, że łączy on 512-bajtowe sektory logiczne zwykle używane przez FileX do pojedynczego sektora logicznego żądania odczytu/zapisu do symulatora LevelX przy użyciu stron 2048-bajtowych. Powoduje to wydajniejsze wykorzystanie pamięci flash ni. Sterownik ni Flash FileX dla LevelX zapewnia dobry punkt wyjścia do pisania niestandardowych sterowników FileX.  
  
> [!NOTE]
> Format Flash ni FileX powinien mieć jeden pełny rozmiar bloku dla sektorów niższy niż program ni Flash. Pomoże to zapewnić najlepszą wydajność podczas przetwarzania poziomu zużycia. Dodatkowe techniki zwiększające wydajność zapisu w algorytmie LevelXego zużycia są następujące:

1. Upewnij się, że wszystkie zapisy mają dokładnie jeden lub więcej klastrów o rozmiarze i Rozpocznij na dokładnych granicach klastra.
1. Przed wykonaniem operacji zapisu dużych plików za pośrednictwem klasy FileX ***Fx_file_allocate*** interfejsów API należy wstępnie przydzielić klastry.
1. Upewnij się, że sterownik FileX jest włączony, aby otrzymywać informacje o sektorach wydania i żądania wysyłane do sterownika w celu wydania sektorów są obsługiwane w sterowniku przez wywołanie ***lx_nor_flash_sector_release***.
1. Okresowe korzystanie z ***lx_nand_flash_defragment*** , aby zwolnić tyle bloków ni, jak to możliwe, a tym samym zwiększyć wydajność zapisu.
1. Użyj interfejsu API ***lx_nand_flash_extended_cache_enable*** , aby zapewnić pamięć podręczną pamięci RAM różnych zasobów ni, aby zwiększyć wydajność.
