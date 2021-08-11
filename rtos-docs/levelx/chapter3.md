---
title: Azure RTOS NAND LevelX
description: Pamięć flash NAND jest często używana na poziomie LevelX do przechowywania dużych ilości danych, co jest typowe dla systemów plików.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 950a4f260d032ebe032aca79ac99cc8217915a3b21b230be9475d82b267da18c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790585"
---
# <a name="chapter-3---azure-rtos-levelx-nand-support"></a>Rozdział 3 — obsługa Azure RTOS NAND LevelX

Pamięć flash NAND jest często używana do przechowywania dużych ilości danych, co jest typowe dla systemów plików. Pamięć NAND składa się z *bloków*. W każdym bloku NAND znajduje się seria *stron*. Bloki NAND można wymazać, co oznacza, że wszystkie strony w bloku NAND są usuwane (ustawione na wszystkie). Każda strona bloku NAND  ma zestaw bajtów zapasowych, które są używane przez usługę Azure RTOS LevelX do obsługi księgowania, zarządzania złymi blokami i wykrywania błędów. Strony blokowe NAND są dostępne w różnych rozmiarach. Najbardziej typowe rozmiary stron to: 

| **Rozmiar strony** | **Bajty zapasowe** |
| ------------- | --------------- |
| 256           | 8               |
| 512           | 16              |
| 2048          | 64              |

Pamięć NAND różni się od pamięci NOR tym, że nie ma bezpośredniego dostępu, tj. pamięci NAND nie można odczytać bezpośrednio z procesora, takiego jak pamięć NOR. Pamięć NAND można zapisywać tylko po kilku razy wymazywania pamięci. Ponownie różni się to od pamięci NOR, która może być zapisywana nieograniczoną liczbę razy, pod ile żądanie zapisu czyszczy bity zestawu. Na koniec bajty zapasowe skojarzone z każdą stroną są unikatowe dla flasha NAND. Typowe konfiguracje bajtów zapasowych są pokazane w poniższej tabeli.

| **Bajty zapasowe** | **Liczby bajtów** | **Konfiguracja**     |
| ------------------------- | -------------- | --------------------- |
| 8                         | Bajty 0–2:     | Bajty ECC             |
|                           | Bajty 3,4,6,7: | Mapowanie sektorów LevelX |
|                           | Bajt 5:        | Flaga złych bloków        |
| 16                        | Bajty 0–3,6–7: | Bajty ECC             |
|                           | Bajty 8–11:    | Mapowanie sektorów LevelX |
|                           | Bajty 12–15:   | Nieużywane                |
|                           | Bajt 5:        | Flaga złych bloków        |
| 64                        | Bajt 0:        | Flaga złych bloków        |
|                           | Bajty 2–5:     | Mapowanie sektorów LevelX |
|                           | Bajty 6–39:    | Nieużywane                |
|                           | Bajty 40–63:   | Bajty ECC             |

LevelX wykorzystuje 4 bajty zapasowe każdej strony NAND do śledzenia sektora logicznego zamapowanych na fizyczną stronę NAND. Te 4 bajty są używane do zaimplementowania 32-bitowej liczby całkowitej bez znaku z zastrzeżonym formatem LevelX. Górny bit pola 32-bitowego (bit 31) służy do wskazywania, że mapowanie między sektorami logicznymi jest prawidłowe. Jeśli ten bit ma 0, informacje na tej stronie nie są już prawidłowe. Następny bit — bit 30 — jest używany, aby wskazać, że ta strona jest w trakcie staje się przestarzała i jest pisany nowy sektor. Bit 29 służy do wskazywania, kiedy zapis wpisu mapowania jest ukończony. Jeśli bit 29 ma 0, zapis wpisu mapowania jest ukończony. Jeśli bit 29 jest ustawiony, wpis mapowania był w trakcie pisano. Bity 30 i 29 są używane do odzyskiwania po potencjalnej utracie zasilania podczas aktualizowania nowej strony flash. Na koniec niższe 29-bitowe (28-0) zawierają numer sektora logicznego dla strony.

**Wpis mapowania LevelX**

| Bity | Znaczenie |
| ------ | ------- |
| 31     | Prawidłowa flaga. Gdy ustawiono i nie wszystkie sektory logiczne wskazują, że mapowanie jest prawidłowe |
| 30     | Przestarzała flaga. Gdy to mapowanie jest jasne, jest przestarzałe lub trwa jego przestarzałe. |
| 29     | Zapis wpisu mapowania jest ukończony, gdy ten bit ma 0 |
| 0-28   | Sektor logiczny zamapowany na tę stronę fizyczną — gdy nie wszystkie z nich. |

LevelX wykorzystuje również pierwszą stronę każdego bloku NAND dla liczby wymazywania bloków, a także listę zamapowanych stron, gdy blok jest pełny. Poniżej przedstawiono format pierwszej strony bloku NAND na poziomie LevelX:

| Format bloku LevelX na stronie 0 |
|:--------------------------:|
| [Blokuj liczbę wymazywania]        |
| [Mapowanie sektorów strony 1]    |
| ...                        |
| [Page "n" Sector Mapping (Mapowanie sektorów na stronie "n])  |
| [0xF0F0F0F0]               |

> [!NOTE]
> Informacje dotyczące mapowania strony są zapisywane tylko wtedy, gdy blok jest pełny, tj. wszystkie strony bloku zostały zapisane w. Umożliwia to szybsze wyszukiwanie wolnych stron i mapowanie sektorów logicznych w czasie uruchamiania.

## <a name="nand-bad-block-support"></a>Obsługa złych bloków NAND

Ponadto istnieje większe prawdopodobieństwo, że pamięć NAND będzie mieć złe bloki niż pamięć NOR. Jest to spowodowane głównie tym, że producenci nandów mogą zwiększyć rentowność, zezwalając na złe bloki i wymagając oprogramowania do ominiania takich złych bloków. LevelX obsługuje zarządzanie złymi blokami NAND, po prostu mapując wokół złych bloków.

LevelX udostępnia również interfejsy API dla 256-bajtowych kodów korekty błędów Hamminga (ECC) dla bazowego sterownika LevelX do obliczania nowych kodów ECC lub wykonywania 1-bitowej korekty błędów podczas odczytywania strony w każdej 256-bajtowej sekcji strony.

## <a name="nand-driver-requirements"></a>Wymagania dotyczące sterownika NAND

LevelX wymaga źródłowego sterownika flash NAND, który jest specyficzny dla bazowej implementacji sprzętowej i części flash. Sterownik jest określony na LevelX podczas inicjowania za pośrednictwem interfejsu API ***lx_nand_flash_open***. Prototyp sterownika LevelX jest następujący.

```c
INT nand_driver_initialize(LX_NAND_FLASH *instance);
```

Parametr *wystąpienia* określa blok sterowania NaND LevelX. Funkcja inicjowania sterownika jest odpowiedzialna za konfigurowanie wszystkich innych usług na poziomie sterownika dla skojarzonego wystąpienia LevelX. Usługi wymagane dla każdego wystąpienia nand LevelX są wyświetlane na poniższej liście.

- Strona odczytu
- Strona zapisu
- Blokuj wymazywanie
- Blokuj wymazane weryfikacje
- Weryfikacja wymazywania strony
- Uzyskiwanie stanu bloku
- Blokuj zestaw stanu
- Blokuj uzyskiwanie dodatkowych bajtów
- Blokuj zestaw dodatkowych bajtów
- Program obsługi błędów systemu

## <a name="driver-initialization"></a>Inicjowanie sterownika

Te usługi są konfigurowe za pośrednictwem ustawiania wskaźników funkcji LX_NAND_FLASH **wystąpieniu** w ramach funkcji inicjowania sterownika. Funkcja inicjowania sterownika określa również łączną liczbę bloków, stron na blok, bajtów na stronę i obszar pamięci RAM wystarczająco duży, aby odczytać jedną stronę do pamięci. Funkcja inicjowania sterownika prawdopodobnie wykonuje również dodatkowe obowiązki dotyczące inicjowania urządzenia i/lub implementacji przed zwróceniem **LX_SUCCESS**.

## <a name="driver-read-page"></a>Strona odczytu sterownika

Usługa "strona odczytu" sterownika NaND LevelX jest odpowiedzialna za odczytywanie określonej strony w określonym bloku flash NAND. Za całą logikę sprawdzania i poprawiania błędów odpowiada usługa sterowników. Jeśli to się powiedzie, sterownik NaND LevelX zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik NaND LevelX zwraca **LX_ERROR**. Poniżej przedstawiono prototyp usługi "strona odczytu" sterownika LevelX NAND.

```c
INT nand_driver_read_page(
    ULONG block,
    ULONG page,
    ULONG *destination, 
    ULONG words);
```

Gdzie *blok* i *strona określają,* która  strona ma być odczytywana, miejsce docelowe i wyrazy określają miejsce, w którym ma być umieszczana zawartość strony, oraz liczbę 32-bitowych słów do odczytania. 

## <a name="driver-write-page"></a>Strona zapisu sterownika

Usługa "strony zapisu" sterownika NAND LevelX jest odpowiedzialna za zapisywanie określonej strony w określonym bloku flash NAND. Wszystkie sprawdzenia błędów i obliczenia ECC są odpowiedzialne za usługę sterowników. Jeśli to się powiedzie, sterownik NaND LevelX zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik NaND LevelX zwraca **LX_ERROR**. Poniżej przedstawiono prototyp usługi "strona zapisu" sterownika LevelX NAND.

```c
INT nand_driver_write_page(
    ULONG block, 
    ULONG page,
    ULONG *source, 
    ULONG words);
```

Gdzie *blok* i *strona identyfikują*  stronę  do zapisu, źródło i wyrazy określają źródło zapisu oraz liczbę 32-bitowych słów do zapisu.

> [!NOTE]
> LevelX opiera się na sterowniku do wykrywania błędów niskiego poziomu podczas zapisywania na stronie flash, co zwykle obejmuje odczytywanie z powrotem strony i porównywanie z buforem zapisu w celu zapewnienia pomyślnego zapisu.

## <a name="driver-block-erase"></a>Wymazywanie bloku sterownika

Usługa "blokuj wymazywanie" sterownika NAND LevelX jest odpowiedzialna za wymazywanie określonego bloku flash NAND. Jeśli to się powiedzie, sterownik NaND LevelX zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik NaND LevelX zwraca **LX_ERROR**. Prototyp usługi "blokuj wymazywanie" sterownika LevelX NAND jest następujący.

```c
INT nand_driver_block_erase(ULONG block,  
    ULONG erase_count);
```

Blok *where określa,* który blok ma zostać wymazany. Parametr *erase_count* jest dostarczany do celów diagnostycznych. Na przykład sterownik może chcieć ostrzec inną część oprogramowania aplikacji, gdy liczba wymazywania przekroczy określony próg.

> [!NOTE]
> Narzędzie LevelX polega na sterowniku do wykrywania błędów niskiego poziomu podczas wymazywania bloku, co zwykle obejmuje upewnienie się, że wszystkie strony bloku są jedynami.

## <a name="driver-block-erased-verify"></a>Weryfikacja wymazanych bloków sterowników

Usługa "blokuj wymazaną weryfikację" sterownika LevelX NAND jest odpowiedzialna za sprawdzenie, czy określony blok pamięci flash NAND został usunięty. Jeśli zostanie on wymazany, sterownik LevelX NAND zwróci **wartość LX_SUCCESS**. Jeśli blok nie zostanie wymazany, sterownik NAND LevelX zwróci **wartość LX_ERROR**. Prototyp usługi "blokuj wymazaną weryfikację" sterownika LevelX NAND to:

```c
INT nand_driver_block_erased_verify(ULONG block);
```

Gdzie *bloku* określa, który blok, aby sprawdzić, czy został usunięty.

> [!NOTE]
> Narzędzie LevelX polega na tym, że sterownik sprawdza wszystkie strony i wszystkie bajty każdej strony — w tym bajty zapasowe i bajty danych — aby upewnić się, że zostały usunięte (zawierają wszystkie).

## <a name="driver-page-erased-verify"></a>Weryfikacja wymazywania strony sterownika

Usługa "weryfikacji wymazanej strony" sterownika LevelX NAND jest odpowiedzialna za sprawdzenie, czy określona strona określonego bloku flash NAND jest wymazana. Jeśli zostanie on wymazany, sterownik LevelX NAND zwróci **wartość LX_SUCCESS**. Jeśli strona nie zostanie wymazana, sterownik NaND LevelX zwróci **wartość LX_ERROR**. Prototyp usługi "page erased verify" sterownika LevelX NAND to:

```c
INT nand_driver_page_erased_verify(
    ULONG block,  
    ULONG page);
```
Gdzie *bloku* określa, który blok *i strona* określa stronę, aby sprawdzić, czy jest ona wymazana.

> [!NOTE]
> Narzędzie LevelX polega na tym, że sterownik sprawdza wszystkie bajty określonej strony — w tym bajty zapasowe i bajty danych — w celu upewniania się, że zostały usunięte (zawierają wszystkie bajty).

## <a name="driver-block-status-get"></a>Uzyskiwanie stanu bloku sterownika

Usługa "pobieranie stanu bloku" sterownika LevelX NAND jest odpowiedzialna za pobieranie flagi złych bloków określonego bloku flash NAND. Jeśli to się powiedzie, sterownik NaND LevelX zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik NAND LevelX zwraca **LX_ERROR**. Prototyp usługi "block status get" sterownika LevelX NAND to: pokazany poniżej.

```c
INT nand_driver_block_status_get(
    ULONG block,  
    UCHAR *bad_block_byte);
```

Where *block* określa, który blok *bad_block_byte* określa miejsce docelowe dla flagi bad block.

## <a name="driver-block-status-set"></a>Zestaw stanu bloku sterowników

Usługa "blokuj zestaw stanu" sterownika LevelX NAND jest odpowiedzialna za ustawienie flagi złych bloków określonego bloku flash NAND. Jeśli to się powiedzie, sterownik NaND LevelX zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik NAND LevelX zwraca **LX_ERROR**. Prototyp usługi "blokuj zestaw stanu" sterownika NAND LevelX to:

```c
INT nand_driver_block_status_set(
    ULONG block,
    UCHAR bad_block_byte);
```

Where *block* określa, który blok *bad_block_byte* określa wartość flagi bad block.

## <a name="driver-block-extra-bytes-get"></a>Uzyskiwanie dodatkowych bajtów bloku sterownika

Usługa sterownika NAND LevelX "blokuj pobieranie dodatkowych bajtów" jest odpowiedzialna za pobieranie dodatkowych bajtów skojarzonych z określoną stroną określonego bloku flash NAND. Jeśli to się powiedzie, sterownik NaND LevelX zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik NAND LevelX zwraca **LX_ERROR**. Prototyp usługi "Blokuj dodatkowe bajty get" sterownika LevelX NAND to:

```c
INT nand_driver_block_extra_bytes_get(
    ULONG block,  
    ULONG page, 
    UCHAR *destination, 
    UINT size);
```

Gdzie *blok* określa blok, *strona* określa określoną stronę, a *miejsce* docelowe określa miejsce docelowe dodatkowych bajtów. Rozmiar *parametru* określa liczbę dodatkowych bajtów do uzyskania.

## <a name="driver-block-extra-bytes-set"></a>Zestaw dodatkowych bajtów bloku sterownika

Usługa sterownika NAND LevelX "blokuj zestaw dodatkowych bajtów" jest odpowiedzialna za ustawianie dodatkowych bajtów na określonej stronie określonego bloku flash NAND. Jeśli to się powiedzie, sterownik NaND LevelX zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik NAND LevelX zwraca **LX_ERROR**. Prototyp usługi "blokuj zestaw dodatkowych bajtów" sterownika LevelX NAND to:

```c
INT nand_driver_block_extra_bytes_set(
    ULONG block,  
    ULONG page, 
    UCHAR *source, 
    UINT size);
```

Gdzie *blok* określa, który blok, *strona* określa określoną stronę, a *źródło* określa źródło dodatkowych bajtów. Rozmiar *parametru* określa liczbę dodatkowych bajtów do ustawienia.

## <a name="driver-system-error"></a>Błąd systemu sterowników

Usługa "obsługi błędów systemu" sterownika LevelX NAND jest odpowiedzialna za ustawianie obsługi błędów systemowych wykrytych przez system LevelX. Przetwarzanie w tej procedury jest zależne od aplikacji. Jeśli to się powiedzie, sterownik NaND LevelX zwraca **LX_SUCCESS**. Jeśli to się nie powiedzie, sterownik NAND LevelX zwraca **LX_ERROR**. Prototyp usługi "błąd systemu" sterownika LevelX NAND to:

```c
INT nand_driver_system_error(
    UINT error_code,  
    ULONG block, 
    ULONG page);
```

Gdzie *blok* określa, który blok, a *strona* określa określoną stronę, błąd reprezentowany przez *error_code* wystąpił.

## <a name="nand-simulated-driver"></a>Symulowany sterownik NAND

LevelX udostępnia symulowany sterownik flash NAND, który po prostu używa pamięci RAM do symulowania działania części flash NAND. Domyślnie symulowany sterownik NAND udostępnia 8 bloków flash NAND z 16 stronami na blok i 2048 bajtów na stronę.

Symulowana funkcja inicjowania sterownika flash NAND to ***lx_nand_flash_simulator_initialize** _ i jest zdefiniowana w _*_lx_nand_flash_simulator.c_**. Ten sterownik udostępnia również dobry szablon do pisania określonych sterowników flash NAND.

## <a name="nand-filex-integration"></a>Integracja z plikiem NAND FileX

Jak wspomniano wcześniej, levelX nie polega na pliku FileX w przypadku operacji. Wszystkie interfejsy API LevelX mogą być wywoływane bezpośrednio przez oprogramowanie aplikacji w celu przechowywania/pobierania danych pierwotnych do sektorów logicznych dostarczanych przez levelX. Jednak system LevelX obsługuje również plik FileX.

Plik ***fx_nand_flash_simulated_driver.c*** zawiera przykładowy sterownik FileX do użycia z symulacją flash NAND. Interesującym aspektem tego sterownika jest to, że łączy on 512-bajtowe sektory logiczne zwykle używane przez plik FileX w żądania odczytu/zapisu pojedynczego sektora logicznego do symulatora LevelX przy użyciu stron 2048-bajtowych. W ten sposób można wydajniej korzystać z pamięci flash NAND. Sterownik NaND flash FileX dla levelX zapewnia dobry punkt wyjścia do pisania niestandardowych sterowników FileX.  
  
> [!NOTE]
> Format flash NAND pliku FileX powinien mieć rozmiar jednego pełnego bloku sektorów mniejszy niż rozmiar zapewniany przez flash NAND. Pomoże to zapewnić najlepszą wydajność podczas przetwarzania poziomu zużycia. Poniżej przedstawiono dodatkowe techniki poprawiające wydajność zapisu w algorytmie levelingu poziomu zużycia LevelX.

1. Upewnij się, że wszystkie zapis mają dokładnie jeden lub więcej klastrów o rozmiarze, i rozpocznij od dokładnych granic klastra.
1. Wstępnie przydziel klastry przed wykonaniem operacji zapisu dużych plików za pośrednictwem klasy ***fx_file_allocate*** FileX interfejsów API.
1. Upewnij się, że sterownik FileX jest włączony do odbierania informacji o sektorze wydania, a żądania do sterownika dotyczące zwalniania sektorów są obsługiwane w sterowniku przez wywołanie lx_nor_flash_sector_release ***.***
1. Okresowe użycie ***lx_nand_flash_defragment,*** aby jak najwięcej bloków NAND było wolnych, a tym samym poprawić wydajność zapisu.
1. Użyj ***interfejsu API lx_nand_flash_extended_cache_enable,*** aby zapewnić pamięć podręczną RAM różnych zasobów bloku NAND w celu zapewnienia szybszej wydajności.
