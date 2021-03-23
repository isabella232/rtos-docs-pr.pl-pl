---
title: Rozdział 6 — usługa Azure RTO LevelX lub interfejsy API
description: Usługa Azure RTO LevelX ani interfejsy API dostępne dla aplikacji.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ab7d3a7e431d7c8f49ef4f5cab9216dc77c8d33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822956"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a>Rozdział 6 — usługa Azure RTO LevelX lub interfejsy API

Usługa Azure RTO LevelX lub funkcje interfejsu API dostępne dla aplikacji są następujące.

- ***lx_nor_flash_close** _: _Close lub Flash wystąpienie *
- ***lx_nor_flash_defragment** _: _Defragment lub Flash wystąpienie *
- ***lx_nor_flash_extended_cache_enable** _: _Enable/Disable Extended lub cache *
- ***lx_nor_flash_initialize** _: _Initialize lub Flash support *
- ***lx_nor_flash_open** _: _Open lub Flash wystąpienie *
- ***lx_nor_flash_partial_defragment** _: _Partial defragmentacji wystąpienia lub Flash *
- ***lx_nor_flash_sector_read** _: _Read lub sektor Flash *
- ***lx_nor_flash_sector_release** _: _Release lub sektor Flash *
- ***lx_nor_flash_sector_write** _: _Write lub sektor Flash *

## <a name="lx_nor_flash_close"></a>lx_nor_flash_close

Zamknij lub Flash wystąpienie

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Opis

Ta usługa zamyka poprzednio otwarte i nieflash wystąpienie.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash*: ani na Flash wskaźnik wystąpienia.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd podczas zamykania wystąpienia Flash.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_defragment"></a>lx_nor_flash_defragment

Defragmentacja i wystąpienie programu Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Opis

Ta usługa defragmentuje poprzednio otwarte i nieflash wystąpienie. Proces defragmentacji maksymalizuje liczbę wolnych sektorów i bloków.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash*: ani na Flash wskaźnik wystąpienia.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd podczas defragmentowania wystąpienia Flash.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nor_flash_close
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_extended_cache_enable"></a>lx_nor_flash_extended_cache_enable

Włącz/Wyłącz rozszerzoną lub buforowaną pamięć podręczną

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Opis

Ta usługa służy do implementowania warstwy pamięci podręcznej sektora i w pamięci RAM przy użyciu pamięci dostarczonej przez aplikację. Każde 512 bajtów dostarczonej pamięci jest tłumaczone do jednego lub sektora, który może być buforowany. W pamięci podręcznej sektory są te, które zawierają informacje o kontrolkach bloku, np., liczba wymazów, Mapa wolnego sektora i informacje o mapowaniu sektorów. Sektory danych nie są przechowywane w tej pamięci podręcznej.

### <a name="input-parameters"></a>Parametry wejściowe

- **nor_flash**: ani na Flash wskaźnik wystąpienia.  
- **pamięć**: początkowy adres pamięci podręcznej wyrównany do ULONG dostępu. Wartość LX_NULL powoduje wyłączenie pamięci podręcznej.  
- **rozmiar**: rozmiar w bajtach dostarczonej pamięci (powinien być wielokrotnością 512 bajtów).

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0x01) za mało pamięci dla jednego i sektora.
- **LX_DISABLED**: (0X09) lub rozszerzona pamięć podręczna wyłączona przez opcję konfiguracji.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_initialize"></a>lx_nor_flash_initialize

Obsługa inicjowania i Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a>Opis

Ta usługa inicjuje usługę LevelX lub Flash support. Musi być wywoływana przed wszystkimi innymi LevelXami i interfejsami API.

### <a name="input-parameters"></a>Parametry wejściowe

- **Brak**

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd podczas inicjowania i obsługi Flash.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

### <a name="example"></a>Przykład

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_partial_defragment
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_open"></a>lx_nor_flash_open

Otwórz i uruchom wystąpienie

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a>Opis

Ta usługa otwiera wystąpienie a i Flash z określonym i funkcją inicjowania sterownika. Należy pamiętać, że funkcja inicjowania sterownika jest odpowiedzialna za Instalowanie różnych wskaźników funkcji do odczytywania, pisania i wymazywania bloków sprzętu i niezwiązanych z tym wystąpieniem.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash*: ani na Flash wskaźnik wystąpienia.
- *Nazwa*: Nazwa i wystąpienie programu Flash.
- *nor_driver_initialize*: wskaźnik funkcji do i funkcji inicjowania sterownika Flash. Więcej informacji na temat obowiązków związanych z sterownikiem i ich Flash można znaleźć w rozdziale 5 tego przewodnika.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd otwierania i wystąpienia Flash.
- **LX_NO_MEMORY**: (0X08) sterownik nie dostarczył buforu do odczytu sektora none w pamięci RAM.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_partial_defragment"></a>lx_nor_flash_partial_defragment

Częściowa defragmentacja lub wystąpienie programu Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a>Opis

Ta usługa defragmentuje poprzednio otwarte lub Flash wystąpienie do maksymalnej liczby określonych bloków. Proces defragmentacji maksymalizuje liczbę wolnych sektorów i bloków.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash*: ani na Flash wskaźnik wystąpienia.
- *max_blocks*: Maksymalna liczba bloków.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd podczas defragmentowania wystąpienia Flash.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a>Zobacz też

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_read"></a>lx_nor_flash_sector_read

Odczytaj i wycinek

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Opis

Ta usługa odczytuje sektor logiczny z wystąpienia i programu Flash i jeśli pomyślnie zwraca zawartość z podanego buforu. Należy pamiętać, że rozmiar sektora nie jest zawsze 512 bajtów.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash* LUB wskaźnik wystąpienia programu Flash.
- *logical_sector*: sektor logiczny do odczytania.
- *bufor*: wskaźnik do miejsca docelowego dla zawartości sektora logicznego. Należy pamiętać, że bufor jest przyjmowana jako 512 bajtów i wyrównany do ULONG dostępu.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0x01) odczytywanie błędów i sektory Flash.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a>Zobacz też

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_release
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_release"></a>lx_nor_flash_sector_release

Wydanie lub sektor Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Opis

Ta usługa zwalnia mapowanie sektora logicznego w wystąpieniu programu i programu Flash. Zwolnienie sektora logicznego, gdy nie jest używany, sprawia, że LevelX zwiększa wydajność.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash*: ani na Flash wskaźnik wystąpienia.
- *logical_sector*: sektor logiczny do wydania.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_ERROR**: (0X01) błąd ani zapis sektora programu Flash.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a>Zobacz też

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_write

## <a name="lx_nor_flash_sector_write"></a>lx_nor_flash_sector_write

Pisanie i sektory w programie Flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Opis

Ta usługa Zapisuje określony sektor logiczny w wystąpieniu i programie Flash.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash*: ani na Flash wskaźnik wystąpienia.
- *logical_sector*: sektor logiczny do zapisu.
- *bufor*: wskaźnik do zawartości sektora logicznego. Należy pamiętać, że bufor jest przyjmowana jako 512 bajtów wyrównany do ULONG dostępu.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS**: (0X00) pomyślne żądanie.
- **LX_NO_SECTORS**: (0X02) nie ma więcej dostępnych wolnych sektorów do przeprowadzenia zapisu.
- **LX_ERROR**: (0X01) błąd podczas zwalniania ani sektora Flash.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a>Zobacz też

- lx_nor_flash_close
- lx_nor_flash_defragment
- lx_nor_flash_extended_cache_enable
- lx_nor_flash_initialize
- lx_nor_flash_open
- lx_nor_flash_partial_defragment
- lx_nor_flash_sector_read
- lx_nor_flash_sector_release
