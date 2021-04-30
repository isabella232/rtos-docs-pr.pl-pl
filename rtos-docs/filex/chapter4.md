---
title: Rozdział 4 — Opis Azure RTOS FileX
description: Ten rozdział zawiera opis wszystkich Azure RTOS FileX w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f70b8890be6b12f917ac1724a29559afab33b88d
ms.sourcegitcommit: 0520b2afb6b7f8ae1ea48581e160459fc9292ca7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2021
ms.locfileid: "108297500"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a>Rozdział 4 — Opis Azure RTOS FileX

Ten rozdział zawiera opis wszystkich Azure RTOS FileX w kolejności alfabetycznej. Nazwy usług zostały zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem.

## <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read

Odczytuje atrybuty katalogu

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a>Opis

Ta usługa odczytuje atrybuty katalogu z określonego nośnika.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **directory_name:** wskaźnik do nazwy żądanego katalogu (ścieżka katalogu jest opcjonalna).
- **atrybuty** _ptr: wskaźnik do miejsca docelowego dla atrybutów katalogu do umieszczenia. Atrybuty katalogu są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Atrybuty katalogu pomyślne odczytu
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty
- **FX _NOT FOUND** (0x04) Określony katalog nie został znaleziony na nośniku
- **FX_NOT_DIRECTORY** (0x0E) Entry nie jest katalogiem
- **FX_IO_ERROR** (0x90) sterownika We/Wy
- **FX_FILE_CORRUPT** 0x08) Plik jest uszkodzony
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT
- **FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set

Ustawia atrybuty katalogu

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a>Opis

Ta usługa ustawia atrybuty katalogu na te określone przez wywołującego.

> [!WARNING]
> *Ta aplikacja może modyfikować tylko podzbiór atrybutów katalogu za pomocą tej usługi. Każda próba ustawienia dodatkowych atrybutów spowoduje błąd.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **directory_name:** wskaźnik do nazwy żądanego katalogu (ścieżka katalogu jest opcjonalna).
- **atrybuty:** nowe atrybuty do tego katalogu. Prawidłowe atrybuty katalogu są zdefiniowane w następujący sposób:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Zestaw atrybutów katalogu successful
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty
- **FX_NOT_FOUND** (0x04) Określony katalog nie został znaleziony na nośniku
- **FX_NOT_DIRECTORY** (0x0E) Entry nie jest katalogiem
- **FX_IO_ERROR** (0x90) sterownika We/Wy
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT
- **FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik
- **FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tym katalogu
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika
- **FX_INVALID_ATTR** (0x19) Wybrane nieprawidłowe atrybuty.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_create"></a>fx_directory_create

Tworzy podkatalog

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a>Opis

Ta usługa tworzy podkatalog w bieżącym katalogu domyślnym lub w ścieżce podanej w nazwie katalogu. W przeciwieństwie do katalogu głównego podkatalogi nie mają ograniczenia liczby plików, które mogą przechowywać. Katalog główny może zawierać tylko liczbę wpisów określonych przez rekord rozruchowy.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **directory_name:** wskaźnik do nazwy katalogu do utworzenia (ścieżka katalogu jest opcjonalna).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne utworzenie katalogu.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty
- **FX_NOT_FOUND** (0x04) Określony katalog nie został znaleziony na nośniku
- **FX_NOT_DIRECTORY** (0x0E) Entry nie jest katalogiem
- **FX_IO_ERROR** (0x90) sterownika We/Wy
- **FX_FILE _CORRUPT** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT
- **FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik
- **FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tym katalogu
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika
- **FX_INVALID_ATTR** (0x19) Wybrane nieprawidłowe atrybuty.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_get"></a>fx_directory_default_get

Pobiera ostatni katalog domyślny

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Opis

Ta usługa zwraca wskaźnik do ostatniej ścieżki ustawionej przez ***fx_directory_default_set***. Jeśli katalog domyślny nie został ustawiony lub jeśli bieżący katalog domyślny jest katalogiem głównym, zwracana jest FX_NULL wartość .

> [!IMPORTANT]
> *Domyślny rozmiar ciągu ścieżki wewnętrznej to 256 znaków. Można go zmienić przez zmodyfikowanie FX_MAXIMUM_PATH **w** pliku **fx_api.h** i ponowne skompilowanie całej biblioteki FileX. Ścieżka ciągu znaków jest zachowywana dla aplikacji i nie jest używana wewnętrznie przez plik FileX.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **return_path_name:** wskaźnik do miejsca docelowego dla ostatniego domyślnego ciągu katalogu. Jeśli bieżącym ustawieniem katalogu domyślnego jest katalog główny, jest zwracana wartość FX_NULL zwracana. Po otwarciu nośnika ustawieniem domyślnym jest katalog główny.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne uzyskiwanie katalogu domyślnego
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty
- **FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik docelowy.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_default_set"></a>fx_directory_default_set

Ustawia katalog domyślny

### <a name="prototype"></a>Prototype

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Opis

Ta usługa ustawia domyślny katalog nośnika. Jeśli zostanie FX_NULL, domyślny katalog zostanie ustawiony na katalog główny nośnika. Wszystkie kolejne operacje na plikach, które nie określają jawnie ścieżki, będą domyślnie wykonywane w tym katalogu.

> [!IMPORTANT]
> *Domyślny rozmiar ciągu ścieżki wewnętrznej to 256 znaków. Można go zmienić przez zmodyfikowanie FX_MAXIMUM_PATH **w** pliku **fx_api.h** i ponowne skompilowanie całej biblioteki FileX. Ścieżka ciągu znaków jest zachowywana dla aplikacji i nie jest używana wewnętrznie przez plik FileX.*

> [!IMPORTANT]
> *W przypadku nazw dostarczonych przez aplikację plik FileX obsługuje zarówno ukośnik odwrotny ( ), jak i ukośnik (/) do oddzielnych \\ katalogów, podkatalogów i nazw plików. Jednak plik FileX używa znaku ukośnika odwrotnego tylko w ścieżkach zwracanych do aplikacji.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **new_path_name:** Wskaźnik do nowej domyślnej nazwy katalogu. Jeśli zostanie FX_NULL, domyślny katalog nośnika zostanie ustawiony na katalog główny nośnika.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Zestaw katalogów domyślnych powodzenie
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty
- **FX_INVALID_PATH** (0x0D) Nie można odnaleźć nowego katalogu
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_delete"></a>fx_directory_delete

Usuwa podkatalog

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Opis

Ta usługa usuwa określony katalog. Pamiętaj, że katalog musi być pusty, aby go usunąć.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **directory_name:** wskaźnik do nazwy katalogu do usunięcia (ścieżka katalogu jest opcjonalna).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne usunięcie katalogu
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty
- **FX_NOT_FOUND** (0x04) Nie znaleziono określonego katalogu
- **FX_DIR_NOT_EMPTY** (0x10) Określony katalog nie jest pusty
- **FX_IO_ERROR** (0x90) sterownika We/Wy
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT
- **FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik
- **FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tym katalogu
- **FX_NOT_DIRECTORY** (0x0E) Nie jest wpisem katalogu
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

Pobiera pierwszy wpis katalogu

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Opis

Ta usługa pobiera nazwę pierwszego wpisu w katalogu domyślnym i kopiuje ją do określonego miejsca docelowego.

> [!WARNING]
> *Określone miejsce docelowe musi być wystarczająco duże, aby pomieścić maksymalną nazwę FileX o maksymalnym rozmiarze, zgodnie z definicją **FX_MAX_LONG_NAME_LEN.***

> [!WARNING]
> *Jeśli używasz ścieżki innej niż lokalna, ważne jest, aby uniemożliwić innym wątkom aplikacji (ze zmianą poziomu semafora, mutexu lub priorytetu ThreadX) zmianę tego katalogu w innych wątkach aplikacji podczas przechodzenia przez katalog. W przeciwnym razie mogą zostać uzyskane nieprawidłowe wyniki.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **return_entry_name:** wskaźnik do miejsca docelowego dla pierwszej nazwy wpisu w katalogu domyślnym.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Znajdowanie pomyślnego pierwszego wpisu katalogu
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty
- **FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tym katalogu
- **FX_IO_ERROR** (0x90) sterownika We/Wy
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT
- **FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik docelowy
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

Pobiera pierwszy wpis katalogu z pełnymi informacjami

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **directory_name:** wskaźnik do miejsca docelowego dla nazwy wpisu katalogu. Musi być co najmniej tak duży, jak FX_MAX_LONG_NAME_LEN.
- **atrybuty:** Jeśli nie ma wartości null, wskaźnik do miejsca docelowego dla atrybutów wpisu do umieszczenia. Atrybuty są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **size:** jeśli wartość nie ma wartości null, wskaźnik do miejsca docelowego dla rozmiaru wpisu w bajtach.
- **year:** Jeśli wartość nie ma wartości null, wskaźnik do miejsca docelowego dla roku modyfikacji wpisu.
- **month:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla miesiąca modyfikacji wpisu.
- **day:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla daty modyfikacji wpisu.
- **hour:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla godziny modyfikacji wpisu.
- **minute:** jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla minuty modyfikacji wpisu.
- **second:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla drugiej modyfikacji wpisu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Znajdowanie pomyślnego pierwszego wpisu katalogu
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty
- **FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tym katalogu
- **FX_IO_ERROR** (0x90) sterownika We/Wy
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem
- **FX_FILE _CORRUPT** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT
- **FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub miejsca docelowego.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_information_get"></a>fx_directory_information_get:

Pobiera informacje o wpisie katalogu

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **directory_name:** wskaźnik do nazwy wpisu katalogu.
- **atrybuty:** wskaźnik do miejsca docelowego dla atrybutów.
- **size**: wskaźnik do miejsca docelowego rozmiaru.
- **year**: wskaźnik do miejsca docelowego dla roku.
- **month:** wskaźnik do miejsca docelowego dla miesiąca.
- **day**: wskaźnik do miejsca docelowego dla dnia.
- **hour**: wskaźnik do miejsca docelowego dla godziny.
- **minute:** wskaźnik do miejsca docelowego dla minuty.
- **second**: wskaźnik do miejsca docelowego dla sekundy.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Znajdowanie pomyślnego pierwszego wpisu katalogu
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty
- **FX_NOT_FOUND** (0x04) Określony katalog nie został znaleziony na nośniku
- **FX_IO_ERROR** (0x90) sterownika We/Wy
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik
- **FX_FILE _CORRUPT** (0x08) jest uszkodzony
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub miejsca docelowego.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear:

Czyszczy domyślną ścieżkę lokalną

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Opis

Ta usługa wyczyści poprzednią ścieżkę lokalną ustawioną dla wątku wywołującego.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do wcześniej otwartego nośnika.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Ścieżka lokalna pomyślna.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest obecnie otwarty
- **FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH zdefiniowane
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get:

Pobiera bieżący ciąg ścieżki lokalnej

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a>Opis

Ta usługa zwraca wskaźnik ścieżki lokalnej określonego nośnika. Jeśli nie ma ustawionej ścieżki lokalnej, do wywołującego jest zwracana wartość NULL.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **return_path_name:** wskaźnik do docelowego wskaźnika ciągu dla ciągu ścieżki lokalnej, który ma być przechowywany.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Uzyskiwanie pomyślnej ścieżki lokalnej.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest obecnie otwarty
- **FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika


### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore:

Przywraca poprzednią ścieżkę lokalną

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a>Opis

Ta usługa przywraca wcześniej ustawioną ścieżkę lokalną. Przywracana jest również pozycja wyszukiwania katalogu w tej ścieżce lokalnej, co sprawia, że ta procedura jest przydatna w cyklicznych przechodzeniach katalogów przez aplikację.

> [!IMPORTANT]
> *Każda ścieżka lokalna zawiera ciąg ścieżki lokalnej **o FX_MAXIMUM_PATH** rozmiarze, który domyślnie ma 256 znaków. Ten wewnętrzny ciąg ścieżki nie jest używany przez plik FileX i jest dostarczany tylko do użytku przez aplikację. Jeśli **FX_LOCAL_PATH** zostanie zadeklarowana jako zmienna lokalna, użytkownicy powinni uważać na wzrost stosu o rozmiarze tej struktury. Użytkownicy mogą zmniejszyć rozmiar biblioteki FX_MAXIMUM_PATH **ponownie** skompilować źródło biblioteki FileX.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **local_path_ptr:** wskaźnik do wcześniej ustawionej ścieżki lokalnej. Bardzo ważne jest, aby upewnić się, że ten wskaźnik rzeczywiście wskazuje wcześniej używaną i nadal nienaruszoną ścieżkę lokalną.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne przywracanie ścieżki lokalnej.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest obecnie otwarty.
- **FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH jest zdefiniowana.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik ścieżki nośnika lub ścieżki lokalnej.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

Konfiguruje ścieżkę lokalną specyficzną dla wątku

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Opis

Ta usługa konfiguruje ścieżkę specyficzną dla wątku określoną przez ***** new_path_string _. Po pomyślnym zakończeniu tej procedury informacje o ścieżce lokalnej przechowywane w _ *_local_path_ptr_** będą miały pierwszeństwo przed globalną ścieżką nośnika dla wszystkich operacji na plikach i katalogach wykonywanych przez ten wątek. Nie będzie to miało wpływu na żaden inny wątek w systemie 
> [!IMPORTANT]
> *Domyślny rozmiar ciągu ścieżki lokalnej to 256 znaków. Można go zmienić, **modyfikując** FX_MAXIMUM_PATH w pliku **fx_api.h** i ponownie przebudowując całą bibliotekę FileX. Ścieżka ciągu znaków jest utrzymywana dla aplikacji i nie jest używana wewnętrznie przez plik FileX.*

> [!IMPORTANT]
> *W przypadku nazw dostarczonych przez aplikację plik FileX obsługuje zarówno ukośnik odwrotny ( ), jak i ukośnik (/) do oddzielnych \\ katalogów, podkatalogów i nazw plików. Jednak plik FileX używa znaku ukośnika odwrotnego tylko w ścieżkach zwracanych do aplikacji.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do wcześniej otwartego nośnika.
- **local_path_ptr:** miejsce docelowe do przechowywania informacji o ścieżce lokalnej specyficznej dla wątku. Adres tej struktury może zostać podany w funkcji przywracania ścieżki lokalnej w przyszłości.
- **new_path_name:** określa ścieżkę lokalną do instalacji.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Zestaw katalogów domyślnych Powodzenie.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_IMPLEMENTED** (0x22) **FX_NO_LCOAL_PATH
- **FX_INVALID_PATH** (0x0D) Nie można odnaleźć nowego katalogu.
- **FX_NOT_IMPLEMENTED** (0x22)- **FX_NO_LOCAL_PATH jest zdefiniowany.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik ścieżki nośnika lub ścieżki lokalnej.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get:

Pobiera długą nazwę z krótkiej nazwy

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a>Opis

Ta usługa pobiera długą nazwę (jeśli jest) skojarzoną z podaną krótką nazwą (format 8.3). Krótka nazwa może być nazwą pliku lub nazwą katalogu.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **short_name:** Wskaźnik do źródła skróconej nazwy (format 8.3).
- **long_name:** Wskaźnik do miejsca docelowego dla długiej nazwy. Jeśli nie ma długiej nazwy, zwracana jest krótka nazwa. Należy pamiętać, że miejsce docelowe długiej nazwy musi być wystarczająco duże, aby FX_MAX_LONG_NAME_LEN znaków.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne długie uzyskiwanie nazwy
- **FX_NOT_FOUND** (0x04) Nie znaleziono krótkiej nazwy
- **FX_IO_ERROR** (0x90) Sterownik We/Wy
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub nazwy
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_long_name_get_extended"></a>fx_directory_long_name_get_extended

Pobiera długą nazwę z krótkiej nazwy

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a>Opis

Ta usługa pobiera długą nazwę (jeśli jest) skojarzoną z podaną krótką nazwą (format 8.3). Krótka nazwa może być nazwą pliku lub nazwą katalogu.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **short_name:** Wskaźnik do źródła skróconej nazwy (format 8.3).
- **long_name:** Wskaźnik do miejsca docelowego dla długiej nazwy. Jeśli nie ma długiej nazwy, zwracana jest krótka nazwa. Uwaga: miejsce docelowe długiej nazwy musi być wystarczająco duże, aby **FX_MAX_LONG_NAME_LEN** znaków.
- **long_file_name_buffer_length:** długość buforu długich nazw.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Długi czas uzyskania pomyślnej nazwy.
- **FX_NOT_FOUND** (0x04) Nie znaleziono krótkiej nazwy.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_name_test"></a>fx_directory_name_test

Testy katalogu

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a>Opis

Ta usługa sprawdza, czy podana nazwa jest katalogiem. Jeśli tak, jest FX_SUCCESS zwracana.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **directory_name:** wskaźnik do nazwy wpisu katalogu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Nazwa jest katalogiem.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty
- **FX_NOT_FOUND** (0x04) Nie można odnaleźć wpisu katalogu.
- **FX_NOT_DIRECTORY** (0x0E) Entry nie jest katalogiem
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find:

Przejmuje następny wpis katalogu

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Opis

Ta usługa zwraca nazwę następnego wpisu w bieżącym katalogu domyślnym.

> [!WARNING]
> *Jeśli używasz ścieżki innej niż lokalna, ważne jest również, aby uniemożliwić (z poziomem semafora ThreadX lub priorytetem wątku) zmianę tego katalogu przez inne wątki aplikacji podczas przechodzenia przez katalog. W przeciwnym razie mogą zostać uzyskane nieprawidłowe wyniki.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **return_entry_name:** wskaźnik do miejsca docelowego dla następnej nazwy wpisu w katalogu domyślnym. Bufor, do który wskazuje ten wskaźnik, musi być wystarczająco duży, aby pomieścić maksymalny rozmiar nazwy FileX zdefiniowany przez FX_MAX_LONG_NAME_LEN **_._**

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne następne wyszukiwanie wpisu
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NO_MORE_ENTRIES** (0x0F) Nie więcej wpisów w tym katalogu.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find:

Pobiera wpis następnego katalogu z pełnymi informacjami

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a>Opis

Ta usługa pobiera nazwę następnego wpisu w katalogu domyślnym i kopiuje ją do określonego miejsca docelowego. Zwraca również pełne informacje o wpisie określone przez dodatkowe parametry wejściowe.

> [!WARNING]
> *Określone miejsce docelowe musi być wystarczająco duże, aby pomieścić maksymalną nazwę FileX o maksymalnym rozmiarze, zgodnie z definicją za pomocą wartości ,FX_MAX_LONG_NAME_LEN***

> [!WARNING]
> *Jeśli używasz ścieżki innej niż lokalna, ważne jest, aby uniemożliwić innym wątkom aplikacji (ze zmianą poziomu semafora, mutexu lub priorytetu ThreadX) zmianę tego katalogu w innych wątkach aplikacji podczas przechodzenia przez katalog. W przeciwnym razie mogą zostać uzyskane nieprawidłowe wyniki.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **directory_name:** wskaźnik do miejsca docelowego dla nazwy wpisu katalogu. Musi być co najmniej tak duży, **jak FX_MAX_LONG_NAME_LEN**.
- **atrybuty:** Jeśli nie ma wartości null, wskaźnik do miejsca docelowego dla atrybutów wpisu do umieszczenia. Atrybuty są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **size:** jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego rozmiaru wpisu w bajtach.
- **month:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla miesiąca modyfikacji wpisu.
- **year:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla roku modyfikacji wpisu.
- **day:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla dnia modyfikacji wpisu.
- **hour**: Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla godziny modyfikacji wpisu.
- **minute:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla minuty modyfikacji wpisu.
- **second**: Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego drugiej modyfikacji wpisu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Znajdź następny wpis w katalogu successful.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NO_MORE_ENTRIES** (0x0F) Nie ma więcej wpisów w tym katalogu.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub wszystkie parametry wejściowe mają wartość NULL.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_rename"></a>fx_directory_rename

Zmienia nazwę katalogu

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a>Opis

Ta usługa zmienia nazwę katalogu na określoną nową nazwę katalogu. Zmiana nazwy jest również wykonywana względem określonej ścieżki lub ścieżki domyślnej. Jeśli ścieżka jest określona w nowej nazwie katalogu, zmieniona nazwa katalogu jest skutecznie przenoszony do określonej ścieżki. Jeśli ścieżka nie zostanie określona, zmieniono nazwę katalogu jest umieszczana w bieżącej ścieżce domyślnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **old_directory_name:** Wskaźnik do bieżącej nazwy katalogu.
- **new_directory_name:** Wskaźnik do nowej nazwy katalogu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślna zmiana nazwy katalogu.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Nie można odnaleźć wpisu katalogu.
- **FX_NOT_DIRECTORY** (0x0E) Entry nie jest katalogiem.
- **FX_INVALID_NAME** (0x0C) Nazwa nowego katalogu jest nieprawidłowa.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.
- **FX_NO_MORE_ENTRIES** (0x0F) Nie ma więcej wpisów w tym katalogu.
- **FX_INVALID_PATH** (0x0D) Nieprawidłowa ścieżka dostarczona z nazwą katalogu.
- **FX_ALREADY_CREATED** (0x0B) Określony katalog został już utworzony.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_short_name_get
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get:

Pobiera krótką nazwę z długiej nazwy

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a>Opis

Ta usługa pobiera krótką nazwę (format 8.3) skojarzoną z podaną długą nazwą. Długa nazwa może być nazwą pliku lub nazwą katalogu.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **long_name:** Wskaźnik do długiej nazwy źródła.
- **short_name:** Wskaźnik do docelowej krótkiej nazwy (format 8.3). Należy pamiętać, że miejsce docelowe krótkiej nazwy musi być wystarczająco duże, aby pomieścić 14 znaków.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Uzyskiwanie pomyślnej krótkiej nazwy.
- **FX_NOT_FOUND** (0x04) Nie znaleziono długiej nazwy.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik nazwy.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_directory_short_name_get_extended"></a>fx_directory_short_name_get_extended

Pobiera krótką nazwę z długiej nazwy

### <a name="prototype"></a>Prototype

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a>Opis

Ta usługa pobiera krótką nazwę (format 8.3) skojarzoną z podaną długą nazwą. Długa nazwa może być nazwą pliku lub nazwą katalogu.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **long_name:** Wskaźnik do długiej nazwy źródła.
- **short_name:** Wskaźnik do docelowej krótkiej nazwy (format 8.3). Uwaga: miejsce docelowe krótkiej nazwy musi być wystarczająco duże, aby pomieścić 14 znaków.
- **short_file_name_length:** długość bufora krótkich nazw.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Uzyskiwanie pomyślnej krótkiej nazwy.
- **FX_NOT_FOUND** (0x04) Nie znaleziono długiej nazwy.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik nazwy.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_unicode_directory_create
- fx_unicode_directory_rename

## <a name="fx_fault_tolerant_enable"></a>fx_fault_tolerant_enable

Włącza usługę tolerancji błędów

### <a name="prototype"></a>Prototype

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a>Opis

Ta usługa włącza moduł odporności na uszkodzenia. Po uruchomieniu moduł odporności na uszkodzenia wykrywa, czy system plików jest w ramach ochrony przed uszkodzeniami w pliku FileX. Jeśli tak nie jest, usługa znajduje dostępne sektory w systemie plików do przechowywania dzienników transakcji systemu plików. Jeśli system plików jest w ramach ochrony przed błędami FileX, stosuje dzienniki do systemu plików, aby zachować jego integralność.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **memory_ptr:** wskaźnik do bloku pamięci używanego przez moduł odporny na uszkodzenia jako pamięć na początku.
- **memory_size:** rozmiar pamięci dla plików scratch. Aby zapewnić odporność na uszkodzenia, rozmiar pamięci na początku musi być co najmniej 3072 bajty i musi być wielokrotnością rozmiaru sektora.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślnie włączono tolerancję błędów.
- **FX_NOT_ENOUGH_MEMORY** (0x91) pamięci jest za mały.
- **FX_BOOT_ERROR** (0x01) Błąd sektora rozruchowego.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z bezpłatnym klastrem.
- **FX_NO_MORE_SPACE** (0x0A) nośnik skojarzony z tym plikiem nie ma wystarczającej ilości dostępnych klastrów.
- **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a>Zobacz też

- fx_system_initialize
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write

## <a name="fx_file_allocate"></a>fx_file_allocate

Przydziela miejsce dla pliku

### <a name="prototype"></a>Prototype

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a>Opis

Ta usługa przydziela i łączy co najmniej jeden ciągły klaster na końcu określonego pliku. Plik FileX określa wymaganą liczbę klastrów, dzieląc żądany rozmiar przez liczbę bajtów na klaster. Wynik jest następnie zaokrąglany w górę do następnego całego klastra.

Aby przydzielić miejsce o pojemności spoza 4 GB, aplikacja musi używać usługi *fx_file_extended_allocate*.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do wcześniej otwartego pliku.
- **rozmiar:** liczba bajtów do przydzielenia dla pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Alokacja pliku powiodła się.
- **FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z bezpłatnym klastrem.
- **FX_NO_MORE_SPACE** (0x0A) nośnik skojarzony z tym plikiem nie ma wystarczającej ilości dostępnych klastrów.
- **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close— fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open— fx_file_read
- fx_file_relative_seek
- fx_file_rename— fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_read"></a>fx_file_attributes_read

Odczytuje atrybuty pliku

### <a name="prototype"></a>Prototype

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a>Opis

Ta usługa odczytuje atrybuty pliku z określonego nośnika.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **file_name:** wskaźnik do nazwy żądanego pliku (ścieżka katalogu jest opcjonalna).
- **attributes_ptr:** wskaźnik do miejsca docelowego dla atrybutów pliku do umieszczenia. Atrybuty pliku są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne odczytanie atrybutu.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Określony plik nie został znaleziony na nośniku.
- **FX_NOT_A_FILE** (0x05) Określony plik jest katalogiem.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_PTR_ERROR** (0x18) Wskaźnik nieprawidłowych nośników lub atrybutów.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close— fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_attributes_set"></a>fx_file_attributes_set

Ustawia atrybuty pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a>Opis

Ta usługa ustawia atrybuty pliku na atrybuty określone przez wywołujący.

> [!WARNING]
> *Aplikacja może modyfikować tylko podzbiór atrybutów pliku za pomocą tej usługi. Każda próba ustawienia dodatkowych atrybutów spowoduje błąd.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **file_name:** Wskaźnik do nazwy żądanego pliku** (ścieżka katalogu jest opcjonalna).
- **atrybuty:** nowe atrybuty dla pliku. Prawidłowe atrybuty pliku są zdefiniowane w następujący sposób:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Zestaw atrybutów Powodzenie.
- **FX_ACCESS_ERROR** (0x06) jest otwarty i nie można ustawić jego atrybutów.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NO_MORE_ENTRIES** (0x0F) Brak kolejnych wpisów w tabeli FAT lub mapie klastra exFAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.
- **FX_NOT_FOUND** (0x04) Określony plik nie został znaleziony na nośniku.
- **FX_NOT_A_FILE** (0x05) Określony plik jest katalogiem.
- **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_INVALID_ATTR** (0x19) Wybrane nieprawidłowe atrybuty.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

Najlepszy sposób przydzielania miejsca dla pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a>Opis

Ta usługa przydziela i łączy co najmniej jeden ciągły klaster na końcu określonego pliku. FileX określa wymaganą liczbę klastrów, dzieląc żądany rozmiar przez liczbę bajtów na klaster. Wynik jest następnie zaokrąglany w górę do następnego całego klastra. Jeśli na nośniku nie ma wystarczającej ilości kolejnych klastrów, ta usługa łączy z plikiem największy dostępny blok kolejnych klastrów. Ilość miejsca rzeczywiście przydzielonego do pliku jest zwracana do wywołującego.

Aby przydzielić miejsce poza 4 GB, aplikacja musi używać usługi *fx_file_extended_best_effort_allocate*.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do wcześniej otwartego pliku.
- **size:** liczba bajtów do przydzielenia dla pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne przydzielanie plików z najlepszymi rozwiązaniami.
- **FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.
- **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej ilości dostępnych klastrów.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku lub miejsce docelowe.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_close"></a>fx_file_close

Zamyka plik

### <a name="prototype"></a>Prototype

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a>Opis

Ta usługa zamyka określony plik. Jeśli plik był otwarty do zapisu, a jeśli został zmodyfikowany, ta usługa kończy proces modyfikacji pliku, aktualizując jego wpis katalogu przy użyciu nowego rozmiaru oraz bieżącej daty i czasu systemowego.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do wcześniej otwartego pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne zamknięcie pliku.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_PTR_ERROR** (0x18) Wskaźnik nieprawidłowych nośników lub atrybutów.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_create"></a>fx_file_create

Tworzy plik

### <a name="prototype"></a>Prototype

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a>Opis

Ta usługa tworzy określony plik w katalogu domyślnym lub w ścieżce katalogu dostarczonej z nazwą pliku.

> [!WARNING]
> *Ta usługa tworzy plik o zerowej długości, tj. nie przydzielone klastry. Alokacja będzie automatycznie odbywać się przy kolejnych zapisach plików lub może być wykonywana z wyprzedzeniem za pomocą usługi fx_file_allocate lub fx_file_extended_allocate dla miejsca spoza 4 GB).*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **file_name:** wskaźnik do nazwy pliku do utworzenia (ścieżka katalogu jest opcjonalna).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne utworzenie pliku.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_ALREADY_CREATED** (0x0B) Określony plik został już utworzony.
- **FX_NO_MORE_SPACE** (0x0A) W katalogu głównym nie ma już żadnych wpisów lub nie ma już dostępnych klastrów.
- **FX_INVALID_PATH** (0x0D) Nieprawidłowa ścieżka dostarczona z nazwą pliku.
- **FX_INVALID_NAME** (0x0C) Nazwa pliku jest nieprawidłowa.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji
- **FX_MEDIA_INVALID** (0x02)Nieprawidłowy nośnik.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Nośniki bazowe są chronione przed zapisem.
- **FX_PTR_ERROR** (0x18) Wskaźnik nieprawidłowego nośnika lub nazwy pliku.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a>Zobacz też
- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_date_time_set"></a>fx_file_date_time_set

### <a name="sets-file-date-and-time"></a>Ustawia datę i godzina pliku

Ustawianie daty i godzin pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a>Opis

Ta usługa ustawia datę i czas określonego pliku.

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **file_name:** Wskaźnik do nazwy pliku.
- **year**: wartość roku (1980–2107 włącznie).
- **month:** wartość miesiąca (1–12 włącznie).
- **day:** wartość dnia (od 1 do 31 włącznie).
- **hour:** wartość godziny (0–23 włącznie).
- **minute:** wartość minuty (0–59 włącznie).
- **second:** wartość sekundy (0–59 włącznie).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Data/godzina pomyślnego zakończenia.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Nie znaleziono pliku .
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.
- **FX_INVALID_YEAR** (0x12) Rok jest nieprawidłowy.
- **FX_INVALID_MONTH** (0x13) Month (Miesiąc) jest nieprawidłowy.
- **FX_INVALID_DAY** (0x14) jest nieprawidłowy.
- **FX_INVALID_HOUR** (0x15) Godzina jest nieprawidłowa.
- **FX_INVALID_MINUTE** (0x16) Minuta jest nieprawidłowa.
- **FX_INVALID_SECOND** (0x17) Sekunda jest nieprawidłowa.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_delete"></a>fx_file_delete

### <a name="deletes-file"></a>Usuwa plik

Usuwanie pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a>Opis

Ta usługa usuwa określony plik.


### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **file_name:** wskaźnik do nazwy pliku do usunięcia (ścieżka katalogu jest opcjonalna).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne usunięcie pliku.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Nie znaleziono określonego pliku.
- **FX_NOT_A_FILE** (0x05) Określona nazwa pliku to katalog lub wolumin.
- **FX_ACCESS_ERROR** (0x06) Określony plik jest obecnie otwarty.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_allocate"></a>fx_file_extended_allocate

Przydziela miejsce dla pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a>Opis

Ta usługa przydziela i łączy co najmniej jeden ciągły klaster na końcu określonego pliku. FileX określa wymaganą liczbę klastrów, dzieląc żądany rozmiar przez liczbę bajtów na klaster. Wynik jest następnie zaokrąglany w górę do następnego całego klastra.

Ta usługa jest przeznaczona dla usługi exFAT. Parametr *size* przyjmuje wartość 64-bitowej liczby całkowitej, co umożliwia funkcji wywołującej wstępne przydzielenie miejsca poza zakresem 4 GB.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do wcześniej otwartego pliku.
- **size:** liczba bajtów do przydzielenia dla pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślna alokacja pliku.
- **FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.
- **FX_NO_MORE_SPACE** (0x0A) nośnik skojarzony z tym plikiem nie ma wystarczającej ilości dostępnych klastrów.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_best_effort_allocate"></a>fx_file_extended_best_effort_allocate

Najlepszy sposób przydzielania miejsca dla pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a>Opis

Ta usługa przydziela i łączy co najmniej jeden ciągły klaster na końcu określonego pliku. FileX określa wymaganą liczbę klastrów, dzieląc żądany rozmiar przez liczbę bajtów na klaster. Wynik jest następnie zaokrąglany w górę do następnego całego klastra. Jeśli na nośniku nie ma wystarczającej ilości kolejnych klastrów, ta usługa łączy z plikiem największy dostępny blok kolejnych klastrów. Ilość miejsca rzeczywiście przydzielonego do pliku jest zwracana do wywołującego.

Ta usługa jest przeznaczona dla usługi exFAT. Parametr *size* przyjmuje 64-bitową wartość całkowitą, co umożliwia funkcji wywołującej wstępne przydzielenie miejsca poza zakresem 4 GB.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do wcześniej otwartego pliku.
- **rozmiar:** liczba bajtów do przydzielenia dla pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Alokacja pliku powiodła się.
- **FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.
- **FX_NO_MORE_SPACE** (0x0A) nośnik skojarzony z tym plikiem nie ma wystarczającej ilości dostępnych klastrów.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_relative_seek"></a>fx_file_extended_relative_seek

Pozycje względem względnego przesunięcia bajtowego

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego względnego przesunięcia bajtu. Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.

Ta usługa jest przeznaczona dla usługi exFAT. Parametr *byte_offset* przyjmuje 64-bitową wartość całkowitą, co umożliwia wywołującym zmienienie położenia wskaźnika odczytu/zapisu poza zakres 4 GB.

> [!IMPORTANT]
> *Jeśli operacja szukania próbuje poszukować po końcu pliku, wskaźnik odczytu/zapisu pliku jest umieszczony na końcu pliku. I odwrotnie, jeśli operacja seek próbuje umieścić się na początku pliku, wskaźnik odczytu/zapisu pliku jest umieszczony na początku pliku.*

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do wcześniej otwartego pliku.
- **byte_offset:** żądane względne przesunięcie bajtów w pliku.
- **seek_from:** kierunek i lokalizacja miejsca, w którym ma być przeprowadzane względne szukanie. Prawidłowe opcje wyszukiwania są zdefiniowane w następujący sposób:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03) Jeśli FX_SEEK_BEGIN, operacja szukania jest wykonywana od początku pliku. Jeśli FX_SEEK_END określono, operacja szukania jest wykonywana wstecz od końca pliku. Jeśli FX_SEEK_FORWARD określono, operacja szukania jest wykonywana od bieżącej pozycji pliku. Jeśli FX_SEEK_BACK określono, operacja szukania jest wykonywana wstecz od bieżącej pozycji pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Udane względne szukanie pliku.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_seek"></a>fx_file_extended_seek

Pozycje do przesunięcia bajtowego

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego przesunięcia bajtów. Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.

Ta usługa jest przeznaczona dla usługi exFAT. Parametr *byte_offset* przyjmuje 64-bitową wartość całkowitą, co pozwala funkcji wywołującej zmienić położenie wskaźnika odczytu/zapisu poza zakres 4 GB.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do bloku sterowania plikami.
- **byte_offset:** żądane przesunięcie bajtów w pliku. Wartość zero spowoduje położenie wskaźnika odczytu/zapisu na początku pliku, podczas gdy wartość większa niż rozmiar pliku ustawi wskaźnik odczytu/zapisu na końcu pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne szukanie pliku.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open— fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate"></a>fx_file_extended_truncate

Obcina plik

### <a name="prototype"></a>Prototype

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a>Opis

Ta usługa obcina rozmiar pliku do określonego rozmiaru. Jeśli dostarczony rozmiar jest większy niż rzeczywisty rozmiar pliku, ta usługa nie robi niczego. Żaden z klastrów multimediów skojarzonych z plikiem nie jest zwalniany.

> [!WARNING]
> *Należy zachować ostrożność przy obcinaniu plików, które również mogą być jednocześnie otwarte do odczytu. Obcinanie pliku otwartego również do odczytu może spowodować odczytanie nieprawidłowych danych.*

Ta usługa jest przeznaczona dla usługi exFAT. Parametr *size* przyjmuje wartość 64-bitowej liczby całkowitej, co umożliwia funkcji wywołującej działanie poza zakresem 4 GB.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do bloku sterowania plikami.
- **size:** nowy rozmiar pliku. Bajty po tym nowym rozmiarze pliku są odrzucane.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne obcinanie pliku.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.
- **FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Nośniki bazowe są chronione przed zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_extended_truncate_release"></a>fx_file_extended_truncate_release

Obcina klastry plików i wydań

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a>Opis

Ta usługa obcina rozmiar pliku do określonego rozmiaru. Jeśli dostarczony rozmiar jest większy niż rzeczywisty rozmiar pliku, ta usługa nie robi niczego. W przeciwieństwie ***fx_file_extended_truncate*** usługa ta zwalnia wszystkie nieużywane klastry.

> [!WARNING]
> *Należy zachować ostrożność przy obcinaniu plików, które również mogą być jednocześnie otwarte do odczytu. Obcinanie pliku otwartego również do odczytu może spowodować odczytanie nieprawidłowych danych.*

Ta usługa jest przeznaczona dla usługi exFAT. Parametr *size* przyjmuje wartość 64-bitowej liczby całkowitej, co umożliwia funkcji wywołującej działanie poza zakresem 4 GB.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do wcześniej otwartego pliku.
- **rozmiar:** nowy rozmiar pliku. Bajty po tym nowym rozmiarze pliku są odrzucane.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne obcinanie pliku.
- **FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_open"></a>fx_file_open

Otwiera plik

### <a name="prototype"></a>Prototype

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a>Opis

Ta usługa otwiera określony plik do odczytu lub zapisu. Plik może być otwierany do wielokrotnego odczytu, a plik do zapisu można otworzyć tylko raz, dopóki autor nie zamknie pliku.

> [!IMPORTANT]
> *Należy zadbać o to, aby plik był jednocześnie otwarty do odczytu i zapisu. Zapisywanie plików wykonywane, gdy plik jest jednocześnie otwierany do odczytu, może nie być widoczne dla czytnika, chyba że czytnik zamknie i ponownie otworzy plik do odczytu. Podobnie podczas korzystania z usług obcinania plików należy zachować ostrożność. Jeśli plik zostanie obcięty przez twórcę, czytelnicy tego samego pliku mogą zwrócić nieprawidłowe dane.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **file_ptr:** wskaźnik do bloku sterowania plikami.
- **file_name:** wskaźnik do nazwy pliku do otwarcia (ścieżka katalogu jest opcjonalna).
- **open_type:** typ otwartego pliku. Prawidłowe opcje typu otwartego to:
  - FX_OPEN_FOR_READ (0x00)
  - FX_OPEN_FOR_WRITE (0x01)
  - FX_OPEN_FOR_READ_FAST (0x02)

Otwieranie plików z FX_OPEN_FOR_READ i FX_OPEN_FOR_READ_FAST jest podobne:

- FX_OPEN_FOR_READ obejmuje weryfikację, czy połączona lista klastrów, które składają się na plik, jest nienaruszona, FX_OPEN_FOR_READ_FAST nie wykonuje tej weryfikacji, co przyspiesza.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślnie otwarty plik.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Nie znaleziono określonego pliku.
- **FX_NOT_A_FILE** (0x05) Określona nazwa pliku to katalog lub wolumin.
- **FX_FILE_CORRUPT** (0x08) Określony plik jest uszkodzony i otwarcie nie powiodło się.
- **FX_ACCESS_ERROR** (0x06) Określony plik jest już otwarty lub otwarty typ jest nieprawidłowy.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_WRITE_PROTECT** (0x23) Nośniki bazowe są chronione przed zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub pliku.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close— fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_read"></a>fx_file_read

Odczytuje bajty z pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a>Opis

Ta usługa odczytuje bajty z pliku i zapisuje je w dostarczonym buforze. Po zakończeniu odczytu wewnętrzny wskaźnik odczytu pliku jest dostosowywany tak, aby wskazać następny bajt w pliku. Jeśli w żądaniu pozostało mniej bajtów, w buforze są przechowywane tylko pozostałe bajty. W każdym przypadku do wywołującego jest zwracana łączna liczba bajtów umieszczonych w buforze.

> [!WARNING]
> *Aplikacja musi upewnić się, że dostarczony bufor może przechowywać określoną liczbę żądanych bajtów.*

> [!WARNING]
> *Wyższa wydajność jest osiągana, jeśli bufor docelowy znajduje się na granicy długich słów, a żądany rozmiar jest równomiernie podzielny według sizeof(**ULONG**).*

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do bloku sterowania plikami.
- **buffer_ptr:** Wskaźnik do buforu docelowego dla odczytu.
- **request_size:** maksymalna liczba bajtów do odczytania.
- **actual_size:** Wskaźnik do zmiennej do przechowywania rzeczywistej liczby bajtów odczytanych do podanego buforu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślnie odczytany plik.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.
- **FX_FILE_CORRUPT** (0x08) Określony plik jest uszkodzony i odczyt nie powiódł się.
- **FX_END_OF_FILE** (0x09) osiągnięto koniec pliku.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku lub buforu.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a>Zobacz też

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_relative_seek"></a>fx_file_relative_seek

Pozycje względnego przesunięcia bajtowego

### <a name="prototype"></a>Prototype

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego względnego przesunięcia bajtów. Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.

> [!IMPORTANT]
> *Jeśli operacja seek próbuje pominąć koniec pliku, wskaźnik odczytu/zapisu pliku jest umieszczony na końcu pliku. I odwrotnie, jeśli operacja seek próbuje umieścić się na początku pliku, wskaźnik odczytu/zapisu pliku jest umieszczony na początku pliku.*

Aby poszukać wartości przesunięcia spoza 4 GB, aplikacja musi użyć usługi *fx_file_extended_relative_seek*.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do wcześniej otwartego pliku.
- **byte_offset:** żądane względne przesunięcie bajtów w pliku.
- **seek_from:** kierunek i lokalizacja miejsca, z którego ma być przeprowadzane względne szukanie. Prawidłowe opcje wyszukiwania są zdefiniowane w następujący sposób:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03)

Jeśli FX_SEEK_BEGIN określono wartość , operacja szukania jest wykonywana od początku pliku. Jeśli FX_SEEK_END określono, operacja szukania jest wykonywana wstecz od końca pliku. Jeśli FX_SEEK_FORWARD określono, operacja szukania jest wykonywana do przodu od bieżącej pozycji pliku. Jeśli FX_SEEK_BACK określono, operacja szukania jest wykonywana wstecz od bieżącej pozycji pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Udane względne szukanie pliku.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_rename"></a>fx_file_rename

Zmienia nazwę pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a>Opis

Ta usługa zmienia nazwę pliku określoną przez old_file_name *.* Zmiana nazwy jest również wykonywana względem określonej ścieżki lub ścieżki domyślnej. Jeśli ścieżka jest określona w nowej nazwie pliku, nazwa pliku zostanie skutecznie przeniesiona do określonej ścieżki. Jeśli ścieżka nie zostanie określona, nazwa pliku zostanie umieszczona w bieżącej ścieżce domyślnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **old_file_name:** wskaźnik do nazwy pliku do zmiany nazwy (ścieżka katalogu jest opcjonalna).
- **new_file_name:** Wskaźnik do nowej nazwy pliku. Ścieżka katalogu jest niedozwolone.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślna zmiana nazwy pliku.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Nie znaleziono określonego pliku.
- **FX_NOT_A_FILE** (0x05) Określony plik jest katalogiem.
- **FX_ACCESS_ERROR** (0x06) Określony plik jest już otwarty.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_INVALID_NAME** (0x0C) Określona nazwa nowego pliku nie jest prawidłową nazwą pliku.
- **FX_INVALID_PATH** (0x0D) jest nieprawidłowa.
- **FX_ALREADY_CREATED** (0x0B) Używana jest nowa nazwa pliku.
- **FX_MEDIA_INVALID** (0x02) Jest nieprawidłowy.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać tabeli FAT.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_seek"></a>fx_file_seek

Pozycje do przesunięcia bajtowego

### <a name="prototype"></a>Prototype

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego przesunięcia bajtów. Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.

Aby szukać wartości przesunięcia spoza 4 GB, aplikacja musi używać usługi fx_file_extended_seek *.*

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do bloku sterowania plikami.
- **byte_offset:** żądane przesunięcie bajtów w pliku. Wartość zero spowoduje położenie wskaźnika odczytu/zapisu na początku pliku, a wartość większa niż rozmiar pliku spowoduje położenie wskaźnika odczytu/zapisu na końcu pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne szukanie pliku.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate"></a>fx_file_truncate

Obcinanie pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a>Opis

Ta usługa obcina rozmiar pliku do określonego rozmiaru. Jeśli podany rozmiar jest większy niż rzeczywisty rozmiar pliku, ta usługa nie robi niczego. Żaden z klastrów multimediów skojarzonych z plikiem nie jest zwalniany.

> [!WARNING]
> *Należy zachować ostrożność przy obcinaniu plików, które również mogą być jednocześnie otwarte do odczytu. Obcinanie pliku otwartego również do odczytu może spowodować odczytanie nieprawidłowych danych.*

Aby działać dłużej niż 4 GB, aplikacja musi korzystać z *usługi* fx_file_extended_truncate .

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do bloku sterowania plikami.
- **size:** nowy rozmiar pliku. Bajty po tym nowym rozmiarze pliku są odrzucane.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne obcinanie pliku.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.
- **FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_truncate_release"></a>fx_file_truncate_release

Obcina klastry plików i wydań

### <a name="prototype"></a>Prototype

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a>Opis

Ta usługa obcina rozmiar pliku do określonego rozmiaru. Jeśli dostarczony rozmiar jest większy niż rzeczywisty rozmiar pliku, ta usługa nie robi niczego. W przeciwieństwie ***fx_file_truncate*** usługa ta zwalnia wszystkie nieużywane klastry.

> [!WARNING]
> *Należy zachować ostrożność przy obcinaniu plików, które również mogą być jednocześnie otwarte do odczytu. Obcinanie pliku otwartego również do odczytu może spowodować odczytanie nieprawidłowych danych.*

Aby działać dłużej niż 4 GB, aplikacja musi korzystać z usługi *fx_file_extended_truncate_release*.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do wcześniej otwartego pliku.
- **size:** nowy rozmiar pliku. Bajty po tym nowym rozmiarze pliku są odrzucane.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne obcinanie pliku.
- **FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_WRITE_PROTECT** (0x23) Nośniki bazowe są chronione przed zapisem.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_file_write"></a>fx_file_write

Zapisuje bajty w pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a>Opis

Ta usługa zapisuje bajty z określonego buforu, zaczynając od bieżącej pozycji pliku. Po zakończeniu zapisu wewnętrzny wskaźnik odczytu pliku jest dostosowywany tak, aby wskazać następny bajt w pliku.

> [!WARNING]
> *Wyższa wydajność jest osiągana, jeśli bufor źródłowy znajduje się na granicy długich słów, a żądany rozmiar jest równomiernie podzielny według sizeof(**ULONG**).*

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do bloku sterowania plikami.
- **buffer_ptr:** Wskaźnik do buforu źródłowego zapisu.
- **size:** liczba bajtów do zapisu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślny zapis pliku.
- **FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.
- **FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.
- **FX_NO_MORE_SPACE** (0x0A) Na nośniku nie ma już miejsca na wykonanie tego zapisu.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.
- **FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku lub buforu.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate,
- fx_file_attributes_read,
- fx_file_attributes_set,
- fx_file_best_effort_allocate,
- fx_file_close,
- fx_file_create,
- fx_file_date_time_set,
- fx_file_delete,
- fx_file_extended_allocate,
- fx_file_extended_best_effort_allocate,
- fx_file_extended_relative_seek,
- fx_file_extended_seek,
- fx_file_extended_truncate,
- fx_file_extended_truncate_release,
- fx_file_open,
- fx_file_read,
- fx_file_relative_seek,
- fx_file_rename,
- fx_file_seek,
- fx_file_truncate,
- fx_file_truncate_release,
- fx_file_write_notify_set,
- fx_unicode_file_create,
- fx_unicode_file_rename,
- fx_unicode_name_get,
- fx_unicode_short_name_get

## <a name="fx_file_write_notify_set"></a>fx_file_write_notify_set

Ustawia funkcję powiadamiania o zapisie pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a>Opis

Ta usługa instaluje funkcję wywołania zwrotnego wywoływaną po pomyślnej operacji zapisu pliku.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr:** wskaźnik do bloku sterowania plikami.
- **file_write_notify:** Funkcja wywołania zwrotnego zapisu pliku do zainstalowania. Ustawienie funkcji wywołania zwrotnego na wartość NULL powoduje wyłączenie funkcji wywołania zwrotnego.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślnie zainstalowano funkcję wywołania zwrotnego.
- **FX_PTR_ERROR** (0x18) file_ptr wartość NULL.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_media_abort"></a>fx_media_abort

Przerywa działania związane z multimediami

### <a name="prototype"></a>Prototype

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Opis

Ta usługa przerywa wszystkie bieżące działania związane z nośnikiem, łącznie z zamknięciem wszystkich otwartych plików, wysłaniem żądania przerwania do skojarzonego sterownika i umieszczeniem nośnika w stanie przerwania. Ta usługa jest zwykle wywoływana w przypadku wykrycia błędów we/wy.

> [!WARNING]
> *Nośnik musi zostać ponownie otwarty, aby można było z niego korzystać ponownie po wykonaniu operacji przerwania.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Przerwanie nośnika pomyślnie.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

Unieważnia pamięć podręczną sektorów logicznych

### <a name="prototype"></a>Prototype

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Opis

Ta usługa opróżnia wszystkie zanieczyszczone sektory w pamięci podręcznej, a następnie unieważnia całą pamięć podręczną sektorów logicznych.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Unieważnij pomyślną pamięć podręczną nośnika.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub podstaw.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_check"></a>fx_media_check

Sprawdza, czy na nośniku występują błędy

### <a name="prototype"></a>Prototype

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a>Opis

Ta usługa sprawdza na określonym nośniku podstawowe błędy strukturalne, w tym łączenie krzyżowe plików/katalogów, nieprawidłowe łańcuchy FAT i utracone klastry. Ta usługa umożliwia również korygowanie wykrytych błędów.

Usługa fx_media_check wymaga pamięci tymczasowej do pierwszej analizy katalogów i plików na nośniku. W szczególności pamięć dla plików scratch dostarczona do usługi sprawdzania multimediów musi być wystarczająco duża, aby pomieścić kilka wpisów w katalogu, strukturę danych do "stosu" bieżącej pozycji wpisu katalogu przed wprowadzeniem do podkatalogów, a na koniec logiczną mapę bitów FAT. Pamięć na początku powinna mieć co najmniej 512–1024 bajty oraz pamięć dla logicznej mapy bitów FAT, co wymaga tylu bitów, ile jest klastrów na nośniku. Na przykład urządzenie z 8000 klastrami wymagałoby 1000 bajtów do reprezentowania i w związku z tym wymagałoby całkowitego obszaru na początku w kolejności 2048 bajtów.

> [!WARNING]
> *Ta usługa powinna być wywoływana natychmiast po fx_media_open i bez żadnej innej aktywności systemu plików.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **scratch_memory_ptr:** Wskaźnik do początku pamięci na początku pamięci.
- **scratch_memory_size:** rozmiar pamięci dla plików scratch w bajtach.
- **error_correction_option:** Bity opcji korekcji błędów, gdy bit jest ustawiony, wykonywana jest korekta błędu. Bity opcji korekcji błędów są zdefiniowane w następujący sposób:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02)
  - FX_LOST_CLUSTER_ERROR (0x04) Po prostu LUB razem wymagane opcje korekcji błędów. Jeśli nie jest wymagana żadna korekta błędu, należy dostarczyć wartość 0.
- **errors_detected_ptr:** miejsce docelowe bitów wykrywania błędów, zgodnie z definicją poniżej:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)
  - FX_FILE_SIZE_ERROR (0x08)

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne sprawdzenie nośnika, aby uzyskać szczegółowe informacje o wykrytych błędach.
- **FX_ACCESS_ERROR** (0x06) Nie można wykonać sprawdzania otwartych plików.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NO_MORE_SPACE** (0x0A) Brak więcej miejsca na nośniku.
- **FX_NOT_ENOUGH_MEMORY** (0x91) Dostarczona pamięć na początku nie jest wystarczająco duża.
- **FX_ERROR_NOT_FIXED** (0x93) uszkodzenie katalogu głównego FAT32, których nie można naprawić.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik podstaw.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.


### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close"></a>fx_media_close

Zamyka nośnik

### <a name="prototype"></a>Prototype

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Opis

Ta usługa zamyka określony nośnik. W procesie zamykania nośnika wszystkie otwarte pliki są zamykane, a pozostałe bufory są opróżnione do nośnika fizycznego.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne zamknięcie nośnika.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_CALLER_ERROR**    (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_close_notify_set"></a>fx_media_close_notify_set

Ustawia funkcję powiadamiania o zamknięciu nośnika

### <a name="prototype"></a>Prototype

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a>Opis

Ta usługa ustawia funkcję wywołania zwrotnego powiadamiania, która zostanie wywołana po pomyślnym zamknięciu nośnika.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **media_close_notify:** Funkcja powiadamiania o zamknięciu nośnika powiadamia o instalacji funkcji wywołania zwrotnego. Przekazanie wartości NULL jako funkcji wywołania zwrotnego powoduje wyłączenie wywołania zwrotnego zamknięcia nośnika.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślnie zainstalowano funkcję wywołania zwrotnego.
- **FX_PTR_ERROR** (0x18) media_ptr wartość NULL.
- **FX_CALLER_ERROR**    (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_exfat_format"></a>fx_media_exFAT_format

Formatuje nośniki

### <a name="prototype"></a>Prototype

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a>Opis

Ta usługa formatuje dostarczony nośnik w sposób zgodny z exFAT na podstawie podanych parametrów. Ta usługa musi zostać wywołana przed otwarciem nośnika.

> [!WARNING]
> *Formatowanie już sformatowanego nośnika skutecznie wymazuje wszystkie pliki i katalogi na nośniku.*

> [!IMPORTANT]
> *Rozmiar woluminu exFAT powinien odpowiadać rozmiarowi partycji (jeśli istnieje układ MBR lub GPT) lub rozmiar całego urządzenia, jeśli nie ma układu partycji (bez MBR lub GPT). W systemie Windows istnieje ograniczenie, że dysk exFAT nie zostanie ponownie sformatowany w przypadku formatowania z pewnymi wartościami całkowitej liczby sektorów, które są mniejsze niż dostępne sektory*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami. Służy to tylko do podania podstawowych informacji niezbędnych do działania sterownika.
- **sterownik:** wskaźnik do sterownika We/Wy dla tego nośnika. Zazwyczaj będzie to ten sam sterownik dostarczony do kolejnego wywołania fx_media_open wywołania.
- **driver_info_ptr:** Wskaźnik do opcjonalnych informacji, które mogą być używane przez sterownik We/Wy.
- **memory_ptr:** wskaźnik do pamięci roboczej nośnika. memory_size określa rozmiar pamięci nośnika roboczego. Rozmiar musi być co najmniej tak duży, jak rozmiar sektora nośnika.
- **volume_name:** wskaźnik do ciągu nazwy woluminu, który ma maksymalnie 11 znaków.
- **number_of_fats:** liczba fajerzy na nośniku. Bieżąca implementacja obsługuje jeden system PLIKÓW FAT na nośniku.
- **hidden_sectors:** Liczba sektorów ukrytych przed sektorem rozruchowym tego nośnika. Jest to typowe w przypadku wielu partycji.
- **total_sectors:** Łączna liczba sektorów w nośniku.
- **bytes_per_sector:** liczba bajtów na sektor, która zazwyczaj wynosi 512. Plik FileX wymaga, aby była wielokrotnością 32.
- **sectors_per_cluster:** liczba sektorów w każdym klastrze. Klaster jest minimalną jednostką alokacji w systemie plików FAT.
- **volumne_serial_number:** numer seryjny używany dla tego woluminu.
- **boundary_unit:** rozmiar wyrównania obszaru danych fizycznych w liczbie sektorów.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślny format nośnika.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik, sterownik lub wskaźnik pamięci.
- **FX_CALLER_ERROR**    (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_extended_space_available"></a>fx_media_extended_space_available

Zwraca dostępne miejsce na nośniku

### <a name="prototype"></a>Prototype

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a>Opis

Ta usługa zwraca liczbę bajtów dostępnych na nośniku.

Ta usługa jest przeznaczona dla usługi exFAT. Wskaźnik do *available_bytes* przyjmuje wartość 64-bitowej liczby całkowitej, co umożliwia funkcji wywołującej pracę z nośnikiem przekraczacym zakres 4 GB.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do wcześniej otwartego nośnika.
- **available_bytes_ptr:** dostępne bajty pozostawione na nośniku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślnie pobrano miejsce dostępne na nośniku.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub wskaźnik dostępnych bajtów ma wartość NULL.
- **FX_CALLER_ERROR**    (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_flush"></a>fx_media_flush

Opróżnia dane na nośnik fizyczny

### <a name="prototype"></a>Prototype

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Opis

Ta usługa opróżnia wszystkie buforowane sektory i wpisy katalogów wszystkich zmodyfikowanych plików na nośnik fizyczny.

> [!WARNING]
> *Ta procedura może być okresowo wywoływana przez aplikację w celu zmniejszenia ryzyka uszkodzenia plików i/lub utraty danych w przypadku nagłej utraty zasilania w celu.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne opróżnienie nośnika.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_FILE_CORRUPT**    (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_CALLER_ERROR**    (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_format"></a>fx_media_format

Formatuje multimedia

### <a name="prototype"></a>Prototype

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a>Opis

Ta usługa formatuje dostarczony nośnik w sposób zgodny ze standardem FAT 12/16/32 na podstawie podanych parametrów. Ta usługa musi zostać wywołana przed otwarciem nośnika.

> [!WARNING]
> *Formatowanie już sformatowanego nośnika skutecznie wymazuje wszystkie pliki i katalogi na nośniku.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami. Służy to tylko do podania podstawowych informacji niezbędnych do działania sterownika.
- **sterownik:** wskaźnik do sterownika We/Wy dla tego nośnika. Zazwyczaj będzie to ten sam sterownik, który został dostarczony do następnego fx_media_open wywołania.
- **driver_info_ptr:** Wskaźnik do opcjonalnych informacji, które mogą być używane przez sterownik we/wy.
- **memory_ptr:** wskaźnik do pamięci roboczej nośnika.
- **memory_size:** określa rozmiar pamięci nośnika roboczego. Rozmiar musi być co najmniej tak duży, jak rozmiar sektora nośnika.
- **volume_name:** wskaźnik do ciągu nazwy woluminu, który ma maksymalnie 11 znaków.
- **number_of_fats:** liczba otchłani na nośniku. Minimalna wartość wynosi 1 dla podstawowego FAT. Wartości większe niż 1 spowodować dodatkowe kopie FAT są utrzymywane w czasie uruchamiania.
- **directory_entries:** liczba wpisów katalogu w katalogu głównym.
- **hidden_sectors:** Liczba sektorów ukrytych przed sektorem rozruchowym tego nośnika. Jest to typowe w przypadku wielu partycji.
- **total_sectors:** Łączna liczba sektorów w nośniku.
- **bytes_per_sector:** liczba bajtów na sektor, która zazwyczaj wynosi 512. Plik FileX wymaga, aby była wielokrotnością 32.
- **sectors_per_cluster:** liczba sektorów w każdym klastrze. Klaster jest minimalną jednostką alokacji w systemie plików FAT.
- **"orły":** liczba orzeł fizycznych.
- **sectors_per_track:** liczba sektorów na ścieżkę.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślny format nośnika.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_PTR_ERROR** (0x18) Wskaźnik nieprawidłowego nośnika, sterownika lub pamięci.
- **FX_CALLER_ERROR**    (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open"></a>fx_media_open

Otwiera nośnik w celu uzyskania dostępu do plików

### <a name="prototype"></a>Prototype

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a>Opis

Ta usługa otwiera nośnik w celu uzyskania dostępu do plików przy użyciu dostarczonego sterownika We/Wy.

> [!WARNING]
> *Pamięć dostarczana do tej usługi jest używana do implementowania wewnętrznej pamięci podręcznej sektora logicznego, dlatego im więcej pamięci jest dostarczanych, tym mniejsza jest liczba fizycznych we/wy. Plik FileX wymaga pamięci podręcznej z co najmniej jednym sektorem logicznym (bajty na sektor nośnika).*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **media_name:** wskaźnik do nazwy nośnika.
- **media_driver:** Wskaźnik do sterownika We/Wy dla tego nośnika. Sterownik We/Wy musi być zgodny z wymaganiami sterownika FileX zdefiniowanymi w rozdziale 5.
- **driver_info_ptr:** wskaźnik do opcjonalnych informacji, z których może korzystać dostarczony sterownik We/Wy.
- **memory_ptr:** wskaźnik do pamięci roboczej nośnika.
- **memory_size:** określa rozmiar pamięci nośnika roboczego. Rozmiar musi być tak duży, jak rozmiar sektora nośnika (zazwyczaj 512 bajtów).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Nośnik został otwarty pomyślnie.
- **FX_BOOT_ERROR** (0x01) Błąd podczas odczytywania sektora rozruchowego nośnika.
- **FX_MEDIA_INVALID** (0x02) Sektor rozruchowy określonego nośnika jest uszkodzony lub nieprawidłowy. Ponadto ten kod zwracany służy do wskazania, że rozmiar pamięci podręcznej sektora logicznego lub rozmiar wpisu FAT nie jest potęgą 2.
- **FX_FAT_READ_ERROR** (0x03) Błąd podczas odczytywania informacji fat nośnika.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_PTR_ERROR** (0x18) Co najmniej jeden wskaźnik ma wartość NULL.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_open_notify_set"></a>fx_media_open_notify_set

Ustawia funkcję powiadamiania o otwarciu nośnika

### <a name="prototype"></a>Prototype

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a>Opis

Ta usługa ustawia funkcję wywołania zwrotnego powiadamiania, która zostanie wywołana po pomyślnym otwarciu nośnika.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **media_open_notify:** Funkcja wywołania zwrotnego powiadomienia o otwarciu nośnika do zainstalowania. Przekazywanie wartości NULL jako funkcji wywołania zwrotnego wyłącza otwarte wywołanie zwrotne multimediów.

### <a name="return-values"></a>Wartości zwrócone


- **FX_SUCCESS** (0x00) Pomyślnie zainstalowano funkcję wywołania zwrotnego.
- **FX_PTR_ERROR** (0x18) media_ptr wartość NULL.
- **FX_CALLER_ERROR**    (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_read"></a>fx_media_read

Odczytuje sektor logiczny z nośnika

### <a name="prototype"></a>Prototype

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a>Opis

Ta usługa odczytuje sektor logiczny z nośnika i umieszcza go w dostarczonym buforze.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do wcześniej otwartego nośnika.
- **logical_sector:** Sektor logiczny do odczytania.
- **buffer_ptr:** wskaźnik do miejsca docelowego odczytu sektora logicznego.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne odczytanie nośnika.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub buforu.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_space_available"></a>fx_media_space_available

Zwraca dostępne miejsce na nośniku

### <a name="prototype"></a>Prototype

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca liczbę bajtów dostępnych na nośniku.

Aby pracować z nośnikiem większym niż 4 GB, aplikacja musi używać usługi *fx_media_extended_space_available*.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do wcześniej otwartego nośnika.
- **available_bytes_ptr:** dostępne bajty pozostawione na nośniku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślnie zwrócono dostępne miejsce na nośniku.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub wskaźnik dostępnych bajtów ma wartość NULL.
- **FX_CALLER_ERROR**    (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_volume_get
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get"></a>fx_media_volume_get

Pobiera nazwę woluminu nośnika

### <a name="prototype"></a>Prototype

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a>Opis

Ta usługa pobiera nazwę woluminu wcześniej otwartego nośnika.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **volume_name:** wskaźnik do miejsca docelowego dla nazwy woluminu. Należy pamiętać, że miejsce docelowe musi być co najmniej wystarczająco duże, aby pomieścić 12 znaków.
- **volume_source:** określa, gdzie pobrać nazwę z sektora rozruchowego lub katalogu głównego. Prawidłowe wartości dla tego parametru to:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne uzyskiwanie woluminu multimedialnego.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Wolumin nie został znaleziony.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_PTR_ERROR** (0x18) Wskaźnik miejsca docelowego nieprawidłowego nośnika lub woluminu.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_get_extended"></a>fx_media_volume_get_extended

Pobiera nazwę woluminu nośnika wcześniej otwartego nośnika

### <a name="prototype"></a>Prototype

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a>Opis

Ta usługa pobiera nazwę woluminu wcześniej otwartego nośnika.

> [!IMPORTANT]
> Ta usługa jest taka sama jak ***fx_media_volume_get()** _ z wyjątkiem tego, że wywołujący przekazuje rozmiar buforu _ *volume_name**.

### <a name="input-parameters"></a>Parametry wejściowe


- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **volume_name:** wskaźnik do miejsca docelowego dla nazwy woluminu. Należy pamiętać, że miejsce docelowe musi być co najmniej wystarczająco duże, aby pomieścić 12 znaków.
- **volume_name_buffer_length:** rozmiar volume_name buforu.
- **volume_source:** Określa, gdzie pobrać nazwę z sektora rozruchowego lub katalogu głównego. Prawidłowe wartości dla tego parametru to:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne uzyskiwanie woluminu multimedialnego.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Wolumin nie został znaleziony.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_PTR_ERROR** (0x18) Wskaźnik miejsca docelowego nieprawidłowego nośnika lub woluminu.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_set
- fx_media_write
- fx_system_initialize

## <a name="fx_media_volume_set"></a>fx_media_volume_set

Ustawia nazwę woluminu nośnika

### <a name="prototype"></a>Prototype

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a>Opis

Ta usługa ustawia nazwę woluminu wcześniej otwartego nośnika.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **volume_name:** wskaźnik do nazwy woluminu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Zestaw woluminów nośników pomyślnych.
- **FX_INVALID_NAME** (0x0C) Volume_name jest nieprawidłowy.
- **FX_MEDIA_INVALID** (0x02) Nie można ustawić nazwy woluminu.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nazwy nośnika lub woluminu.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_write
- fx_system_initialize

## <a name="fx_media_write"></a>fx_media_write

Zapisuje sektor logiczny

### <a name="prototype"></a>Prototype

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a>Opis

Ta usługa zapisuje dostarczony bufor do określonego sektora logicznego.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do wcześniej otwartego nośnika.
- **logical_sector:** sektor logiczny do zapisu.
- **buffer_ptr:** wskaźnik do źródła zapisu w sektorze logicznym.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślny zapis w nośnikach.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.
- **FX_CALLER_ERROR**    (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a>Zobacz też

- fx_fault_tolerant_enable
- fx_media_abort
- fx_media_cache_invalidate
- fx_media_check
- fx_media_close
- fx_media_close_notify_set
- fx_media_exFAT_format
- fx_media_extended_space_available
- fx_media_flush
- fx_media_format
- fx_media_open
- fx_media_open_notify_set
- fx_media_read
- fx_media_space_available
- fx_media_volume_get
- fx_media_volume_set
- fx_system_initialize

## <a name="fx_system_date_get"></a>fx_system_date_get

Pobiera datę systemu plików

### <a name="prototype"></a>Prototype

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a>Opis

Ta usługa zwraca bieżącą datę systemową.

### <a name="input-parameters"></a>Parametry wejściowe

- **year**: wskaźnik do miejsca docelowego dla roku.
- **month:** wskaźnik do miejsca docelowego dla miesiąca.
- **day**: wskaźnik do miejsca docelowego dla dnia.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pobieranie daty pomyślnej.
- **FX_PTR_ERROR** (0x18) Co najmniej jeden z parametrów wejściowych ma wartość NULL.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a>Zobacz też

- fx_system_date_set
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_date_set"></a>fx_system_date_set

Ustawia datę systemowa

### <a name="prototype"></a>Prototype

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a>Opis

Ta usługa ustawia datę systemową w określony sposób.

> [!WARNING]
> *Ta usługa powinna zostać wywołana wkrótce po **fx_system_initialize,** aby ustawić początkową datę systemową. Domyślnie data systemowa to data ostatniej ogólnej wersji pliku FileX.*

### <a name="input-parameters"></a>Parametry wejściowe

- **year**: Nowy rok. Prawidłowy zakres to od 1980 do 2107 roku.
- **month**: New month (miesiąc): Nowy miesiąc. Prawidłowy zakres wynosi od 1 do 12.
- **day**: Nowy dzień. Prawidłowy zakres wynosi od 1 do 31, w zależności od miesiąca i roku przestępnych warunków.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Ustawienie daty Powodzenie.
- **FX_INVALID_YEAR** (0x12) Określono nieprawidłowy rok.
- **FX_INVALID_MONTH** (0x13) Określono nieprawidłowy miesiąc.
- **FX_INVALID_DAY** (0x14) Określono nieprawidłowy dzień.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a>Zobacz też

- fx_system_date_get
- fx_system_initialize
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_initialize"></a>fx_system_initialize

Inicjuje cały system

### <a name="prototype"></a>Prototype

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a>Opis

Ta usługa inicjuje wszystkie główne struktury danych FileX. Powinien być wywoływany w ***tx_application_define*** lub prawdopodobnie z wątku inicjowania i musi być wywoływany przed użyciem jakiejkolwiek innej usługi FileX.

> [!WARNING]
> *Po zainicjowaniu przez to wywołanie aplikacja powinna wywołać fx_system_date_set _ i _ fx_system_time_set *, aby rozpocząć od dokładnej *daty i czasu systemowego.*

### <a name="input-parameters"></a>Parametry wejściowe

Brak

### <a name="return-values"></a>Wartości zwrócone

Brak.

### <a name="allowed-from"></a>Dozwolone z

Inicjowanie, wątki

### <a name="example"></a>Przykład

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a>Zobacz też

- fx_system_date_get
- fx_system_date_set
- fx_system_time_get
- fx_system_time_set

## <a name="fx_system_time_get"></a>fx_system_time_get

Pobiera bieżący czas systemowy

### <a name="prototype"></a>Prototype

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a>Opis

Ta usługa pobiera bieżący czas systemowy.

### <a name="input-parameters"></a>Parametry wejściowe

- **hour**: wskaźnik do miejsca docelowego na godzinę.
- **minute:** wskaźnik do miejsca docelowego na minutę.
- **second**: wskaźnik do miejsca docelowego na sekundę.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne pobieranie czasu systemowego.
- **FX_PTR_ERROR** (0x18) Co najmniej jeden z parametrów wejściowych

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a>Zobacz też

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_set

## <a name="fx_system_time_set"></a>fx_system_time_set

Ustawia bieżący czas systemowy

### <a name="prototype"></a>Prototype

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a>Opis

Ta usługa ustawia bieżący czas systemowy na określony przez parametry wejściowe.

> [!WARNING]
> *Ta usługa powinna zostać wywołana wkrótce po **fx_system_initialize,** aby ustawić początkowy czas systemowy. Domyślnie czas systemowy to 0:0:0.*

### <a name="input-parameters"></a>Parametry wejściowe

- **hour**: nowa godzina (0–23).
- **minute:** nowa minuta (0–59).
- **sekunda:** nowa sekunda (0–59).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne pobieranie czasu systemu.
- **FX_INVALID_HOUR**    (0x15) Nowa godzina jest nieprawidłowa.
- **FX_INVALID_MINUTE** (0x16) Nowa minuta jest nieprawidłowa.
- **FX_INVALID_SECOND** (0x17) Nowa sekunda jest nieprawidłowa.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a>Zobacz też

- fx_system_date_get
- fx_system_date_set
- fx_system_initialize
- fx_system_time_get

## <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create

Tworzy katalog Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a>Opis

Ta usługa tworzy podkatalog o nazwie Unicode w bieżącym katalogu domyślnym — żadne informacje o ścieżce nie są dozwolone w parametrze nazwy źródła Unicode. Jeśli to się powiedzie, usługa zwraca krótką nazwę (format 8.3) nowo utworzonego podkatalogu Unicode.

> [!WARNING]
> *Wszystkie operacje w podkatalogu Unicode (dzięki czemu jest to ścieżka domyślna, usuwanie itp.) powinny być wykonywane przez dostarczenie zwróconej krótkiej nazwy (w formacie 8.3) do standardowych usług katalogowych FileX.*

> [!IMPORTANT]
> *Ta usługa nie jest obsługiwana na nośnikach exFAT.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **source_unicode_name:** wskaźnik do nazwy Unicode dla nowego podkatalogu.
- **source_unicode_length:** długość nazwy Unicode.
- **short_name:** wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3) dla nowego podkatalogu Unicode.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne utworzenie katalogu Unicode.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_ALREADY_CREATED** (0x0B) Określony katalog już istnieje.
- **FX_NO_MORE_SPACE** (0x0A) Brak dostępnych klastrów na nośniku dla nowego wpisu katalogu.
- **FX_NOT_IMPLEMENTED** (0x22) nie jest zaimplementowana dla systemu plików exFAT.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.
- **FX_IO_ERROR (0x90)** Błąd we/wy sterownika.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_rename

## <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

Zmienia nazwę katalogu przy użyciu ciągu Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a>Opis

Ta usługa zmienia podkatalog o nazwie Unicode, aby określić nową nazwę Unicode w bieżącym katalogu roboczy. Parametry nazwy Unicode nie mogą zawierać informacji o ścieżce.

> [!IMPORTANT]
> *Ta usługa nie jest obsługiwana na nośnikach exFAT.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **old_unicode_name:** wskaźnik do nazwy Unicode dla bieżącego pliku.
- **old_unicode_name_length:** długość bieżącej nazwy Unicode.
- **new_unicode_name:** wskaźnik do nowej nazwy pliku Unicode.
- **old_unicode_name_length:** długość nowej nazwy Unicode.
- **new_short_name:** wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3) dla zmienionego pliku Unicode. Zmiana nazwy katalogu na Unicode

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Nośnik został otwarty pomyślnie.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_ALREADY_CREATED** (0x0B) Określona nazwa katalogu już istnieje.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_PTR_ERROR** (0x18) Co najmniej jeden wskaźnik ma wartość NULL.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony przed zapisem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Zobacz też

- fx_directory_attributes_read
- fx_directory_attributes_set
- fx_directory_create
- fx_directory_default_get
- fx_directory_default_set
- fx_directory_delete
- fx_directory_first_entry_find
- fx_directory_first_full_entry_find
- fx_directory_information_get
- fx_directory_local_path_clear
- fx_directory_local_path_get
- fx_directory_local_path_restore
- fx_directory_local_path_set
- fx_directory_long_name_get
- fx_directory_name_test
- fx_directory_next_entry_find
- fx_directory_next_full_entry_find
- fx_directory_rename
- fx_directory_short_name_get
- fx_unicode_directory_create

## <a name="fx_unicode_file_create"></a>fx_unicode_file_create

Tworzy plik Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a>Opis

Ta usługa tworzy plik o nazwie Unicode w bieżącym katalogu domyślnym — żadne informacje o ścieżce nie są dozwolone w parametrze nazwy źródła Unicode. Jeśli to się powiedzie, usługa zwraca krótką nazwę (format 8.3) nowo utworzonego pliku Unicode.

> [!WARNING]
> *Wszystkie operacje na pliku Unicode (otwieranie, zapisywanie, odczytywanie, zamykanie itp.) powinny być wykonywane przez dostarczenie zwróconej krótkiej nazwy (format 8.3) do standardowych usług plików FileX.*

### <a name="input-parameters"></a>Parametry wejściowe


- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **source_unicode_name:** wskaźnik do nazwy Unicode dla nowego pliku.
- **source_unicode_length:** długość nazwy Unicode.
- **short_name:** wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3) dla nowego pliku Unicode.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne utworzenie pliku.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_ALREADY_CREATED** (0x0B) Określony plik już istnieje.
- **FX_NO_MORE_SPACE** (0x0A) Brak dostępnych klastrów na nośniku dla nowego wpisu pliku.
- **FX_NOT_IMPLEMENTED** (0x22) nie jest zaimplementowana dla systemu plików exFAT.
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.
- **FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

Zmienia nazwę pliku przy użyciu ciągu Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a>Opis

Ta usługa zmienia nazwę pliku o nazwie Unicode na określoną nową nazwę Unicode w bieżącym katalogu domyślnym. Parametry nazwy Unicode nie mogą zawierać informacji o ścieżce.

> [!IMPORTANT]
> *Ta usługa nie jest obsługiwana na nośnikach exFAT.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **old_unicode_name:** wskaźnik do nazwy Unicode dla bieżącego pliku.
- **old_unicode_name_length:** długość bieżącej nazwy Unicode.
- **new_unicode_name:** wskaźnik do nowej nazwy pliku Unicode.
- **new_unicode_name_length:** długość nowej nazwy Unicode.
- **new_short_name:** wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3) dla zmienionego pliku Unicode.

### <a name="return-values"></a>Wartości zwrócone


- **FX_SUCCESS** (0x00) Nośnik został otwarty pomyślnie.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_ALREADY_CREATED** (0x0B) Określona nazwa pliku już istnieje.
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_PTR_ERROR** (0x18) Co najmniej jeden wskaźnik ma wartość NULL.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.
- **FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony przed zapisem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get"></a>fx_unicode_length_get

Pobiera długość nazwy Unicode

### <a name="prototype"></a>Prototype

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a>Opis

Ta usługa określa długość podanej nazwy Unicode. Znak Unicode jest reprezentowany przez dwa bajty. Nazwa Unicode to seria dwóch bajtów znaków Unicode zakończonych przez dwa bajty NULL (dwa bajty o wartości 0).

### <a name="input-parameters"></a>Parametry wejściowe

**unicode_name:** Wskaźnik do nazwy Unicode.

### <a name="return-values"></a>Wartości zwrócone

**length:** długość nazwy Unicode (liczba znaków Unicode w nazwie).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_length_get_extended"></a>fx_unicode_length_get_extended

Pobiera długość nazwy Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a>Opis

Ta usługa pobiera długość podanej nazwy Unicode. Znak Unicode jest reprezentowany przez dwa bajty. Nazwa Unicode to seria dwubajtowych znaków Unicode zakończonych przez dwa bajty NULL (dwa bajty o wartości 0).

> [!IMPORTANT]
> *Ta usługa jest taka sama **jak fx_unicode_length_get(),** z wyjątkiem tego, że wywołujący przekazuje rozmiar **buforu unicode_name,** w tym dwa znaki NULL.*

### <a name="input-parameters"></a>Parametry wejściowe

- **unicode_name:** Wskaźnik do nazwy Unicode.
- **buffer_length:** rozmiar bufora nazw Unicode.

### <a name="return-values"></a>Wartości zwrócone

**length:** długość nazwy Unicode (liczba znaków Unicode w nazwie).

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get"></a>fx_unicode_name_get

Pobiera nazwę Unicode z krótkiej nazwy

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a>Opis

Ta usługa pobiera nazwę Unicode skojarzoną z podaną krótką nazwą (format 8.3) w bieżącym katalogu domyślnym — żadne informacje o ścieżce nie są dozwolone w parametrze krótkiej nazwy. Jeśli to się powiedzie, usługa zwraca nazwę Unicode skojarzoną z krótką nazwą.

> [!IMPORTANT]
> *Ta usługa może służyć do uzyskania nazw Unicode dla plików i podkatalogów.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **short_name** Wskaźnik do krótkiej nazwy (format 8.3).
- **destination_unicode_name:** wskaźnik do miejsca docelowego dla nazwy Unicode skojarzonej z podaną krótką nazwą.
- **destination_unicode_length:** wskaźnik do zwracania długości nazwy Unicode.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne pobranie nazwy Unicode.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać tabeli FAT.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_IO_ERROR** (0x90) sterownika We/Wy.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Nie znaleziono krótkiej nazwy lub rozmiar docelowy Unicode jest zbyt mały.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_name_get_extended"></a>fx_unicode_name_get_extended

Pobiera nazwę Unicode z krótkiej nazwy

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a>Opis

Ta usługa pobiera nazwę Unicode skojarzoną z podaną krótką nazwą (format 8.3) w bieżącym katalogu domyślnym — żadne informacje o ścieżce nie są dozwolone w parametrze krótkiej nazwy. Jeśli to się powiedzie, usługa zwraca nazwę Unicode skojarzoną z krótką nazwą.

> [!IMPORTANT]
> *Ta usługa jest taka sama jak ***fx_unicode_name_get**, z tą różnicą, że obiekt wywołujący dostarcza rozmiar docelowego _bufora Unicode jako argument wejściowy. Dzięki temu usługa może zagwarantować, że nie zastąpi docelowego buforu Unicode_

> [!IMPORTANT]
> *Ta usługa może służyć do uzyskania nazw Unicode dla plików i podkatalogów.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** Wskaźnik do bloku sterowania multimediami.
- **short_name:** Wskaźnik do krótkiej nazwy (format 8.3).
- **destination_unicode_name:** wskaźnik do miejsca docelowego dla nazwy Unicode skojarzonej z podaną krótką nazwą.
- **destination_unicode_length:** wskaźnik do zwracania długości nazwy Unicode.
- **unicode_name_buffer_length:** rozmiar bufora nazw Unicode. Uwaga: Wymagany jest terminator o wartości NULL, co sprawia, że dodatkowy bajt.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne pobranie nazwy Unicode.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać tabeli FAT.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Nie znaleziono krótkiej nazwy lub rozmiar docelowy Unicode jest zbyt mały.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.
- **FX_CALLER_ERROR** (0x20) Nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_short_name_get

## <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

Pobiera krótką nazwę z nazwy Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

Ta usługa pobiera krótką nazwę (format 8.3) skojarzoną z nazwą Unicode w bieżącym katalogu domyślnym — żadne informacje o ścieżce nie są dozwolone w parametrze nazwy Unicode. Jeśli to się powiedzie, usługa zwraca krótką nazwę skojarzoną z nazwą Unicode.

> [!IMPORTANT]
> *Ta usługa może służyć do uzyskania krótkich nazw dla plików i podkatalogów.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **source_unicode_name:** Wskaźnik na nazwę Unicode.
- **source_unicode_length:** długość nazwy Unicode.
- **destination_short_name:** wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3). Musi to być co najmniej 13 bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne pobranie krótkiej nazwy.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać tabeli FAT.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Nie znaleziono nazwy Unicode.
- **FX_NOT_IMPLEMENTED** (0x22) Nie zaimplementowano usługi dla systemu plików exFAT.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get

## <a name="fx_unicode_short_name_get_extended"></a>fx_unicode_short_name_get_extended

Pobiera krótką nazwę z nazwy Unicode

### <a name="prototype"></a>Prototype

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a>Opis

Ta usługa pobiera krótką nazwę (format 8.3) skojarzoną z nazwą Unicode w bieżącym katalogu domyślnym — żadne informacje o ścieżce nie są dozwolone w parametrze nazwy Unicode. Jeśli to się powiedzie, usługa zwróci krótką nazwę skojarzoną z nazwą Unicode.

> [!IMPORTANT]
> *Ta usługa jest taka sama **fx_unicode_short_name_get()**, z tą różnicą, że obiekt wywołujący dostarcza rozmiar buforu docelowego jako argument wejściowy. Dzięki temu usługa może zagwarantować, że krótka nazwa nie przekroczy buforu docelowego.*

*Ta usługa może służyć do uzyskania krótkich nazw dla plików i podkatalogów*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr:** wskaźnik do bloku sterowania multimediami.
- **source_unicode_name:** Wskaźnik na nazwę Unicode.
- **source_unicode_length:** długość nazwy Unicode.
- **destination_short_name:** wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3). Musi to być co najmniej 13 bajtów.
- **short_name_buffer_length:** rozmiar buforu docelowego. Rozmiar buforu musi być co najmniej 14 bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) Pomyślne pobranie krótkiej nazwy.
- **FX_FAT_READ_ERROR** (0x03) Nie można odczytać tabeli FAT.
- **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_IO_ERROR** (0x90) Sterownik We/Wy.
- **FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.
- **FX_NOT_FOUND** (0x04) Nie znaleziono nazwy Unicode.
- **FX_NOT_IMPLEMENTED** (0x22) nie jest zaimplementowana dla systemu plików exFAT.
- **FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.
- **FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.
- **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Wątki

### <a name="example"></a>Przykład

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a>Zobacz też

- fx_file_allocate
- fx_file_attributes_read
- fx_file_attributes_set
- fx_file_best_effort_allocate
- fx_file_close
- fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open
- fx_file_read
- fx_file_relative_seek
- fx_file_rename
- fx_file_seek
- fx_file_truncate
- fx_file_truncate_release
- fx_file_write
- fx_file_write_notify_set
- fx_unicode_file_create
- fx_unicode_file_rename
- fx_unicode_name_get
- fx_unicode_short_name_get
