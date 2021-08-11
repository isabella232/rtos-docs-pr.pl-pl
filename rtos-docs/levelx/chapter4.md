---
title: Rozdział 4 — Azure RTOS API NAND LevelX
description: Interfejsy AZURE RTOS NAND LevelX dostępne dla aplikacji.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d92b6c10921b4d04345610e139101e93c7a439ff695a89a79245894ad9ef1fec
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790286"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a>Rozdział 4 — Azure RTOS API NAND LevelX

Interfejsy API NAND Azure RTOS LevelX dostępne dla aplikacji to:

- ***lx_nand_flash_close** _: _Close wystąpienia flash NAND*
- ***lx_nand_flash_defragment** _: _Defragment wystąpienia flash NAND*
- ***lx_nand_flash_extended_cache_enable** _: _Enable/wyłącz rozszerzoną pamięć podręczną NAND*
- ***lx_nand_flash_initialize** _: _Initialize obsługi flash NAND*
- ***lx_nand_flash_open** _: _Open wystąpienia flash NAND*
- ***lx_nand_flash_page_ecc_check** _: _Check błędy ECC z poprawką*
- ***lx_nand_flash_page_ecc_compute** _: _Computes ECC dla strony*
- ***lx_nand_flash_partial_defragment** _: _Partial defragmentacji wystąpienia flash NAND*
- ***lx_nand_flash_sector_read** _: _Read flash NAND*
- ***lx_nand_flash_sector_release** _: _Release flash NAND*
- ***lx_nand_flash_sector_write** _: _Write sektora flash NAND*

## <a name="lx_nand_flash_close"></a>lx_nand_flash_close

Zamykanie wystąpienia flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Opis

Ta usługa zamyka wcześniej otwarte wystąpienie flash NAND.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash:** wskaźnik wystąpienia flash NAND.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd podczas zamykania wystąpienia flash.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_defragment"></a>lx_nand_flash_defragment

Defragmentacja wystąpienia flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Opis

Ta usługa defragmentuje wcześniej otwarte wystąpienie flash NAND. Proces defragmentacji maksymalizuje liczbę wolnych stron i bloków.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash:** wskaźnik wystąpienia flash NAND.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd defragmentacji wystąpienia flash.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_close
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_extended_cache_enable"></a>lx_nand_flash_extended_cache_enable

Włączanie/wyłączanie rozszerzonej pamięci podręcznej NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Opis

Ta usługa implementuje warstwę pamięci podręcznej w pamięci RAM przy użyciu pamięci dostarczonej przez aplikację. Łączną ilość pamięci wymaganą do pełnej operacji pamięci podręcznej można obliczyć w następujący sposób:

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

Jeśli dostarczona pamięć nie jest wystarczająco duża, aby pomieścić pełną pamięć podręczną NAND, ta procedura umożliwi jak najwięcej pamięci podręcznej flash NAND na podstawie dostarczonej pamięci.

Pamięć podręczna NAND jest wyłączona, jeśli określony adres pamięci ma wartość NULL. W związku z tym pamięć podręczna NAND może być używana w sposób tymczasowy.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash:** wskaźnik wystąpienia flash NAND.  
- **memory:** adres początkowy pamięci podręcznej wyrównany w celu uzyskania dostępu do programu ULONG. Wartość LX_NULL powoduje wyłączenie pamięci podręcznej.  
- **rozmiar:** rozmiar w bajtach dostarczonej pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Za mało pamięci dla jednego elementu pamięci podręcznej NAND.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_initialize"></a>lx_nand_flash_initialize

Inicjowanie obsługi flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a>Opis

Ta usługa inicjuje obsługę flash NAND LevelX. Musi być wywoływana przed innymi interfejsami API NAND LevelX.

### <a name="input-parameters"></a>Parametry wejściowe

- **Brak**

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd podczas inicjowania obsługi pamięci flash NAND.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_open"></a>lx_nand_flash_open

Otwieranie wystąpienia flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a>Opis

Ta usługa otwiera wystąpienie flash NAND z określonym blokiem kontrolki flash NAND i funkcją inicjowania sterownika. Należy pamiętać, że funkcja inicjowania sterownika jest odpowiedzialna za instalowanie różnych wskaźników funkcji do odczytywania, zapisywania i wymazania bloków/stron sprzętu NAND skojarzonego z tym wystąpieniem flash NAND.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash:** wskaźnik wystąpienia flash NAND.
- **name**: nazwa wystąpienia flash NAND.
- **nand_driver_initialize:** wskaźnik funkcji do funkcji inicjowania sterownika flash NAND. Więcej informacji na temat obowiązków dotyczących sterowników flash NAND można znaleźć w rozdziale 3 tego przewodnika.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd podczas otwierania wystąpienia flash NAND.
- **LX_NO_MEMORY:** sterownik (0x08) nie zapewnia buforu do odczytu jednej strony do pamięci RAM.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_check"></a>lx_nand_flash_page_ecc_check

Sprawdzanie strony pod błędami ECC z korektą

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Opis

Ta usługa weryfikuje integralność dostarczonego buforu strony NAND z dostarczonym ecc. Przyjmuje się, że rozmiar strony (zdefiniowany we wskaźniku wystąpienia flash NAND) jest wielokrotnością 256 bajtów, a dostarczony kod ECC może naprawić błąd 1-bitowy w każdej 256-bajtowej części strony.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash:** wskaźnik wystąpienia flash NAND.
- **page_buffer:** wskaźnik do buforu strony flash NAND.
- **ecc_buffer:** wskaźnik do ECC dla strony flash NAND. Należy pamiętać, że strona zawiera 3 bajty ECC na 256-bajtową część strony.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) NAND nie ma błędów.
- **LX_NAND_ERROR_CORRECTED:**(0x06) Co najmniej jeden błąd 1-bitowy został poprawiony na stronie NAND — poprawki znajdują się w buforze strony.
- **LX_NAND_ERROR_NOT_CORRECTED:**(0x07) Zbyt wiele błędów do poprawienia na stronie NAND.

### <a name="allowed-from"></a>Dozwolone z

Sterownik LevelX

### <a name="example"></a>Przykład

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_page_ecc_compute"></a>lx_nand_flash_page_ecc_compute

Obliczanie ecc dla strony

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Opis

Ta usługa oblicza ecc dostarczonego buforu strony NAND i zwraca ECC w dostarczonym buforze ECC. Przyjmuje się, że rozmiar strony ma wielokrotność 256 bajtów (zdefiniowanych we wskaźniku wystąpienia flash NAND). Kod ECC służy do weryfikowania integralności strony, gdy zostanie odczytana w późniejszym czasie.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash:** wskaźnik wystąpienia flash NAND.
- **page_buffer:** wskaźnik do buforu strony flash NAND.
- **ecc_buffer:** wskaźnik do miejsca docelowego ecc strony flash NAND. Należy pamiętać, że musi to być 3 bajty magazynu ECC na 256-bajtową część strony. Na przykład strona z 2048 bajtami wymagałaby 24 bajtów dla ecc.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) ECC pomyślnie obliczona.
- **LX_ERROR:**(0x01) Błąd podczas obliczania ECC.

### <a name="allowed-from"></a>Dozwolone z

Sterownik LevelX

### <a name="example"></a>Przykład

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_partial_defragment"></a>lx_nand_flash_partial_defragment

Częściowa defragmentacja wystąpienia flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a>Opis

Ta usługa defragmentuje wcześniej otwarte wystąpienie flash NAND do maksymalnej określonej liczby bloków. Proces defragmentacji maksymalizuje liczbę wolnych stron i bloków.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash:** wskaźnik wystąpienia flash NAND.
- **max_blocks:** Maksymalna liczba bloków.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd defragmentacji wystąpienia flash.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_read"></a>lx_nand_flash_sector_read

Odczyt sektora flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Opis

Ta usługa odczytuje sektor logiczny z wystąpienia flash NAND i, jeśli to się powiedzie, zwraca zawartość w dostarczonym buforze. Należy pamiętać, że rozmiar sektora NAND jest zawsze rozmiarem strony bazowego sprzętu NAND.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash:** wskaźnik wystąpienia flash NAND.
- **logical_sector:** Sektor logiczny do odczytania.
- **buffer**: wskaźnik do miejsca docelowego zawartości sektora logicznego. Należy pamiętać, że przyjmuje się, że bufor jest rozmiarem strony flash NAND i jest wyrównany w celu uzyskania dostępu do programu ULONG.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd odczytu sektora flash NAND.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_release
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_release"></a>lx_nand_flash_sector_release

Zwolnij sektor flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Opis

Ta usługa zwalnia mapowanie sektorów logicznych w wystąpieniu flash NAND. Zwalnianie sektora logicznego, gdy nie jest używany, sprawia, że poziom zużycia LevelX jest bardziej wydajny.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash:** wskaźnik wystąpienia flash NAND.
- **logical_sector:** sektor logiczny do wydania.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd zapisu sektora flash NAND.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_write

## <a name="lx_nand_flash_sector_write"></a>lx_nand_flash_sector_write

Zapis sektora flash NAND

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Opis

Ta usługa zapisuje określony sektor logiczny w wystąpieniu flash NAND.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash:** wskaźnik wystąpienia flash NAND.
- **logical_sector:** sektor logiczny do zapisu.
- **buffer**: wskaźnik do zawartości sektora logicznego. Należy pamiętać, że przyjmuje się, że bufor jest rozmiarem strony flash NAND i jest wyrównany w celu uzyskania dostępu do programu ULONG.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_NO_SECTORS:**(0x02) Nie ma więcej wolnych sektorów do wykonania zapisu.
- **LX_ERROR:**(0x01) Błąd zwalniający sektor flash NAND.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>Zobacz też

- lx_nand_flash_close
- lx_nand_flash_defragment
- lx_nand_flash_extended_cache_enable
- lx_nand_flash_initialize
- lx_nand_flash_open
- lx_nand_flash_page_ecc_check
- lx_nand_flash_page_ecc_compute
- lx_nand_flash_partial_defragment
- lx_nand_flash_sector_read
- lx_nand_flash_sector_release
