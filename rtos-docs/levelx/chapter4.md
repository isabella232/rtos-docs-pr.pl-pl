---
title: Rozdział 4 — interfejsy API usługi Azure RTO LevelX ni
description: Interfejsy API usługi Azure RTO LevelX ni dostępne dla aplikacji.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73bb94768396b4b8461791a164a102d1f8ef159f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822968"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a>Rozdział 4 — interfejsy API usługi Azure RTO LevelX ni

Dostępne dla aplikacji interfejsy API platformy Azure RTO LevelX ni:

- ***lx_nand_flash_close** _: _Close ni Flash *
- ***lx_nand_flash_defragment** _: _Defragment ni Flash *
- ***lx_nand_flash_extended_cache_enable** _: _Enable/Disable Extended ni cache *
- ***lx_nand_flash_initialize** _: _Initialize ni lampy błyskowej *
- ***lx_nand_flash_open** _: _Open ni Flash *
- ***lx_nand_flash_page_ecc_check** _: Strona _Check dla błędów ECC z poprawką *
- ***lx_nand_flash_page_ecc_compute** _: _Computes ECC dla strony *
- ***lx_nand_flash_partial_defragment** _: _Partial defragmentacji wystąpienia ni Flash *
- ***lx_nand_flash_sector_read** _: _Read ni Flash *
- ***lx_nand_flash_sector_release** _: _Release ni Flash *
- ***lx_nand_flash_sector_write** _: _Write ni Flash *

## <a name="lx_nand_flash_close"></a>lx_nand_flash_close

Zamknij wystąpienie ni Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Opis

Ta usługa zamyka poprzednio otwarte wystąpienie ni Flash.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash**: wskaźnik wystąpienia Flash ni.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd podczas zamykania wystąpienia Flash.

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

Defragmentacja wystąpienia programu ni Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a>Opis

Ta usługa defragmentuje poprzednio otwarte wystąpienie ni Flash. Proces defragmentacji maksymalizuje liczbę bezpłatnych stron i bloków.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash**: wskaźnik wystąpienia Flash ni.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd podczas defragmentowania wystąpienia Flash.

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

Włącz/Wyłącz rozszerzoną pamięć podręczną ni

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

Jeśli dostarczona pamięć nie jest wystarczająco duża, aby pomieścić pełną pamięć podręczną ni, ta procedura spowoduje włączenie tak dużej ilości pamięci podręcznej ni Flash, jak to możliwe, na podstawie dostarczonej pamięci.

Pamięć podręczna ni jest wyłączona, jeśli określony adres pamięci ma wartość NULL. W związku z tym pamięć podręczna ni może być używana w sposób tymczasowy.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash**: wskaźnik wystąpienia Flash ni.  
- **pamięć**: adres początkowy dla pamięci podręcznej wyrównany do ULONG dostępu. Wartość LX_NULL powoduje wyłączenie pamięci podręcznej.  
- **rozmiar**: rozmiar w bajtach dostarczonej pamięci.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0x01) za mało pamięci dla jednego elementu pamięci podręcznej ni.

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

Inicjowanie obsługi ni Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a>Opis

Ta usługa Inicjuje obsługę LevelX ni Flash. Musi być wywoływana przed innymi interfejsami API LevelX ni.

### <a name="input-parameters"></a>Parametry wejściowe

- **Brak**

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd podczas inicjowania obsługi ni Flash.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Otwórz wystąpienie ni Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a>Opis

Ta usługa otwiera wystąpienie ni Flash z określonym blokiem sterowania Flash ni i funkcją inicjowania sterownika. Należy pamiętać, że funkcja inicjowania sterownika jest odpowiedzialna za Instalowanie różnych wskaźników funkcji do odczytu, zapisu i wymazywania bloków/stron sprzętu ni skojarzonego z tym wystąpieniem programu ni Flash.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash**: wskaźnik wystąpienia Flash ni.
- **name**: nazwa wystąpienia Flash ni.
- **nand_driver_initialize**: wskaźnik funkcji do funkcji inicjowania sterownika Flash ni. Więcej informacji na temat obowiązków dotyczących sterownika ni można znaleźć w rozdziale 3 tego przewodnika.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) wystąpił błąd podczas otwierania wystąpienia Flash ni.
- **LX_NO_MEMORY**: (0X08) sterownik nie dostarczył buforu do odczytu jednej strony do pamięci RAM.

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

Sprawdź, czy na stronie błędów ECC zostały skorygowane

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Opis

Ta usługa weryfikuje integralność podanego buforu stronicowania ni przy użyciu dostarczonej ECC. Rozmiar strony (zdefiniowany w wskaźniku wystąpienia Flash ni) zakłada się, że jest wielokrotnością 256-bajtów, a dostarczony kod ECC jest w stanie skorygować 1 bit błędu w każdej części 256-bajtowej strony.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash**: wskaźnik wystąpienia Flash ni.
- **page_buffer**: wskaźnik do niego buforu strony Flash.
- **ecc_buffer**: wskaźnik do strony ni na potrzeby technologii ECC. Należy zauważyć, że liczba bajtów ECC na 256 część strony wynosi 3.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0x00) Strona ni nie ma błędów.
- **LX_NAND_ERROR_CORRECTED**: (0X06) co najmniej jeden błąd 1-bitowy został poprawiony na stronie ni — poprawki są w buforze strony.
- **LX_NAND_ERROR_NOT_CORRECTED**: (0X07) zbyt wiele błędów do poprawienia na stronie ni.

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

Obliczenia ECC dla strony

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a>Opis

Ta usługa oblicza wartość ECC dostarczonego buforu stronicowania ni i zwraca wartość ECC w dostarczonym buforze ECC. Przyjmuje się, że rozmiar strony jest wielokrotnością 256-bajtów (zdefiniowaną w wskaźniku wystąpienia ni Flash). Kod ECC służy do weryfikowania integralności strony, gdy jest odczytywana w późniejszym czasie.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash**: wskaźnik wystąpienia Flash ni.
- **page_buffer**: wskaźnik do niego buforu strony Flash.
- **ecc_buffer**: wskaźnik do miejsca docelowego dla ECC na stronie ni Flash. Należy pamiętać, że musi to być 3 bajty magazynu ECC na 256-bajtowej części strony. Na przykład strona 2048 bajtów będzie wymagała 24 bajtów dla ECC.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0x00) pomyślnie obliczono ECC.
- **LX_ERROR**: (0X01) błąd podczas obliczania ECC.

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

Częściowa defragmentacja wystąpienia programu ni Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a>Opis

Ta usługa defragmentuje poprzednio otwarte wystąpienie ni Flash do maksymalnej liczby określonych bloków. Proces defragmentacji maksymalizuje liczbę bezpłatnych stron i bloków.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash**: wskaźnik wystąpienia Flash ni.
- **max_blocks**: Maksymalna liczba bloków.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd podczas defragmentowania wystąpienia Flash.

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

Odczytaj NIy sektor Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Opis

Ta usługa odczytuje sektor logiczny z wystąpienia ni Flash i jeśli pomyślnie zwróci zawartość w podanym buforze. Należy pamiętać, że rozmiar sektora ni jest zawsze rozmiarem strony podstawowego sprzętu ni.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash**: wskaźnik wystąpienia Flash ni.
- **logical_sector**: sektor logiczny do odczytania.
- **bufor**: wskaźnik do miejsca docelowego dla zawartości sektora logicznego. Należy pamiętać, że bufor jest przyjmowana jako rozmiar rozmiaru strony ni Flash i wyrównany do ULONG Access.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd podczas odczytywania sektora Flash ni.

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

NI wersja sektora Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Opis

Ta usługa zwalnia mapowanie sektora logicznego w wystąpieniu Flash ni. Zwolnienie sektora logicznego, gdy nie jest używany, sprawia, że LevelX zwiększa wydajność.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash**: wskaźnik wystąpienia Flash ni.
- **logical_sector**: sektor logiczny do wydania.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd ni sektora Flash.

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

Pisanie sektora Flash ni

### <a name="prototype"></a>Prototype

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Opis

Ta usługa Zapisuje określony sektor logiczny w wystąpieniu Flash ni.

### <a name="input-parameters"></a>Parametry wejściowe

- **nand_flash**: wskaźnik wystąpienia Flash ni.
- **logical_sector**: sektor logiczny do zapisu.
- **bufor**: wskaźnik do zawartości sektora logicznego. Należy pamiętać, że bufor jest przyjmowana jako rozmiar rozmiaru strony ni Flash i wyrównany do ULONG Access.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_NO_SECTORS**: (0X02) nie ma więcej dostępnych wolnych sektorów do przeprowadzenia zapisu.
- **LX_ERROR**: (0X01) błąd podczas zwalniania sektora Flash ni.

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
