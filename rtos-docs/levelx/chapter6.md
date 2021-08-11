---
title: Rozdział 6 — Azure RTOS LevelX ANI interfejsy API
description: Interfejsy API Azure RTOS LevelX ANI dostępne dla aplikacji.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e109f5916a9e903aa3341f2855ade085e9d9a22b80ec7cb2e0c310e43ff3eac
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790245"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a>Rozdział 6 — Azure RTOS LevelX ANI interfejsy API

Dostępne Azure RTOS interfejsu API LevelX ANI API są następujące.

- ***lx_nor_flash_close** _: _Close ANI flash instance*
- ***lx_nor_flash_defragment** _: _Defragment ANI flash instance*
- ***lx_nor_flash_extended_cache_enable** _: _Enable/wyłącz rozszerzoną pamięć podręczną ANI*
- ***lx_nor_flash_initialize** _: obsługa _Initialize ANI flash*
- ***lx_nor_flash_open** _: _Open ANI flash instance*
- ***lx_nor_flash_partial_defragment** _: _Partial defragmentacji wystąpienia flash NOR*
- ***lx_nor_flash_sector_read** _: _Read ANI sektor flash*
- ***lx_nor_flash_sector_release** _: _Release ANI sektor flash*
- ***lx_nor_flash_sector_write** _: _Write ANI sektor flash*

## <a name="lx_nor_flash_close"></a>lx_nor_flash_close

Zamykanie wystąpienia flash NOR

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Opis

Ta usługa zamyka wcześniej otwarte wystąpienie ANI flash.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash:* ANI flash instance pointer (Wskaźnik wystąpienia flash).

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd podczas zamykania wystąpienia flash.

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

Defragmentacja ANI flash wystąpienia

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a>Opis

Ta usługa defragmentuje wcześniej otwarte wystąpienie flash ANI. Proces defragmentacji maksymalizuje liczbę wolnych sektorów i bloków.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash:* ANI flash instance pointer (Wskaźnik wystąpienia flash).

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd defragmentacji wystąpienia flash.

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

Włączanie/wyłączanie rozszerzonej pamięci podręcznej NOR

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a>Opis

Ta usługa implementuje warstwę pamięci podręcznej sektora NOR w pamięci RAM przy użyciu pamięci dostarczonej przez aplikację. Każde 512 bajtów dostarczonej pamięci przekłada się na jeden sektor NOR, który może być buforowany. Buforowane sektory to te, które zawierają informacje o kontroli bloków, np. liczbę wymazań, mapę wolnych sektorów i informacje o mapowaniu sektorów. Sektory danych nie są przechowywane w tej pamięci podręcznej.

### <a name="input-parameters"></a>Parametry wejściowe

- **nor_flash:** ANI flash instance pointer (Wskaźnik wystąpienia flash).  
- **memory:** adres początkowy pamięci podręcznej wyrównany do dostępu przez program ULONG. Wartość LX_NULL powoduje wyłączenie pamięci podręcznej.  
- **rozmiar:** rozmiar w bajtach dostarczonej pamięci (powinien być wielokrotnością 512 bajtów).

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Za mało pamięci dla jednego sektora NOR.
- **LX_DISABLED:**(0x09) ANI rozszerzona pamięć podręczna wyłączona przez opcję konfiguracji.

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

Obsługa inicjowania ANI flash

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a>Opis

Ta usługa inicjuje obsługę technologii LevelX ANI flash. Musi być wywoływana przed innymi interfejsami API LevelX ANI .

### <a name="input-parameters"></a>Parametry wejściowe

- **Brak**

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd inicjowania ANI obsługa flash.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

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

Otwieranie wystąpienia flash NOR

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a>Opis

Ta usługa otwiera wystąpienie flash NOR z określonym blokiem kontrolki flash NOR i funkcją inicjowania sterownika. Należy pamiętać, że funkcja inicjowania sterownika jest odpowiedzialna za instalowanie różnych wskaźników funkcji do odczytywania, zapisywania i wymazania bloków sprzętu NOR skojarzonego z tym wystąpieniem flash NOR.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash:* ANI flash instance pointer (Wskaźnik wystąpienia flash).
- *name*: nazwa wystąpienia flash NOR.
- *nor_driver_initialize:* Wskaźnik funkcji do funkcji inicjowania sterownika flash NOR. Zapoznaj się z rozdziałem 5 tego przewodnika, aby uzyskać więcej informacji na temat obowiązków dotyczących sterowników flash ANI.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd podczas otwierania ANI wystąpienia flash.
- **LX_NO_MEMORY:** sterownik (0x08) nie zapewnia buforu odczytu z żadnego sektora do pamięci RAM.

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

Częściowa defragmentacja wystąpienia flash NOR

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a>Opis

Ta usługa defragmentuje wcześniej otwarte wystąpienie ani flash do maksymalnej liczby określonych bloków. Proces defragmentacji maksymalizuje liczbę wolnych sektorów i bloków.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash:* ANI flash instance pointer (Wskaźnik wystąpienia flash).
- *max_blocks:* maksymalna liczba bloków.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd defragmentacji wystąpienia flash.

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

Odczytaj sektor flash NOR

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Opis

Ta usługa odczytuje sektor logiczny z wystąpienia flash NOR i w przypadku powodzenia zwraca zawartość w dostarczonym buforze. Należy pamiętać, że rozmiar sektora NOR to zawsze 512 bajtów.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash* ANI wskaźnik wystąpienia flash.
- *logical_sector:* sektor logiczny do odczytania.
- *buffer*: wskaźnik do miejsca docelowego dla zawartości sektora logicznego. Należy pamiętać, że przyjmuje się, że bufor ma rozmiar 512 bajtów i jest wyrównany w celu uzyskania dostępu do programu ULONG.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd odczytu ANI sektora flash.

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

Zwolnij sektor flash NOR

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a>Opis

Ta usługa zwalnia mapowanie sektorów logicznych w wystąpieniu flash NOR. Zwalnianie sektora logicznego, gdy nie jest używany, sprawia, że poziom zużycia LevelX jest bardziej wydajny.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash:* ANI flash instance pointer (Wskaźnik wystąpienia flash).
- *logical_sector:* sektor logiczny do wydania.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_ERROR:**(0x01) Błąd ANI zapis sektora flash.

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

Sektor flash WRITE NOR

### <a name="prototype"></a>Prototype

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a>Opis

Ta usługa zapisuje określony sektor logiczny w wystąpieniu flash NOR.

### <a name="input-parameters"></a>Parametry wejściowe

- *nor_flash:* ANI flash instance pointer (Wskaźnik wystąpienia flash).
- *logical_sector:* sektor logiczny do zapisu.
- *buffer*: wskaźnik do zawartości sektora logicznego. Należy pamiętać, że przyjmuje się, że bufor jest wyrównany o 512 bajtów w celu uzyskania dostępu do programu ULONG.

### <a name="return-values"></a>Wartości zwrócone

- **LX_SUCCESS:**(0x00) Żądanie pomyślne.
- **LX_NO_SECTORS:**(0x02) Nie są dostępne żadne więcej wolnych sektorów do wykonania zapisu.
- **LX_ERROR:**(0x01) Błąd zwalniający sektor flash NOR.

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
