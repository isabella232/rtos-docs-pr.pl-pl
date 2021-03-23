---
title: Rozdział 4 — Opis usług Azure RTO FileX Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO FileX w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9e91244856b322d53f85bdd572bd317a055776a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822447"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a>Rozdział 4 — Opis usług Azure RTO FileX Services

Ten rozdział zawiera opis wszystkich usług Azure RTO FileX w porządku alfabetycznym. Nazwy usług są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem.

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

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **directory_name**: wskaźnik do nazwy żądanego katalogu (ścieżka katalogu jest opcjonalna).
- **atrybuty** _Ptr: wskaźnik do miejsca docelowego dla atrybutów katalogu, które mają zostać umieszczone. Atrybuty katalogu są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Wartości zwrócone

- Odczytane atrybuty katalogu pomyślnego **FX_SUCCESS** (0x00)
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty
- **Znaleziono _NOT FX** (0X04) określony katalog nie został znaleziony na nośniku
- Wpis **FX_NOT_DIRECTORY** (0x0E) nie jest katalogiem
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90)
- Plik **FX_FILE_CORRUPT** 0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa Ustawia atrybuty katalogu dla obiektów określonych przez wywołującego.

> [!WARNING]
> *Ta aplikacja może modyfikować podzestaw atrybutów katalogu w tej usłudze. Wszystkie próby ustawienia dodatkowych atrybutów spowodują wystąpienie błędu.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **directory_name**: wskaźnik do nazwy żądanego katalogu (ścieżka katalogu jest opcjonalna).
- **atrybuty**: nowe atrybuty do tego katalogu. Prawidłowe atrybuty katalogu są zdefiniowane w następujący sposób:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) — pomyślny zestaw atrybutów katalogu
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty
- Nie znaleziono podanego katalogu **FX_NOT_FOUND** (0x04) na nośniku
- Wpis **FX_NOT_DIRECTORY** (0x0E) nie jest katalogiem
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90)
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika
- **FX_INVALID_ATTR** (0x19) wybrano nieprawidłowe atrybuty.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa tworzy podkatalog w bieżącym katalogu domyślnym lub w ścieżce podanej w nazwie katalogu. W przeciwieństwie do katalogu głównego w podkatalogach nie ma limitu liczby plików, które mogą być przechowywane. Katalog główny może zawierać tylko liczbę wpisów określoną przez rekord rozruchowy.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **directory_name**: wskaźnik do nazwy katalogu do utworzenia (ścieżka katalogu jest opcjonalna).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne utworzenie katalogu.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty
- Nie znaleziono podanego katalogu **FX_NOT_FOUND** (0x04) na nośniku
- Wpis **FX_NOT_DIRECTORY** (0x0E) nie jest katalogiem
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90)
- Plik **_CORRUPT FX_FILE** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika
- **FX_INVALID_ATTR** (0x19) wybrano nieprawidłowe atrybuty.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa zwraca wskaźnik do ścieżki ostatnio ustawionej przez ***fx_directory_default_set***. Jeśli domyślny katalog nie został ustawiony lub bieżący katalog domyślny jest katalogiem głównym, zwracana jest wartość FX_NULL.

> [!IMPORTANT]
> *Domyślny rozmiar ciągu ścieżki wewnętrznej to 256 znaków; można ją zmienić, modyfikując **FX_MAXIMUM_PATH** w **fx_api. h** i przebudować całą bibliotekę FileX. Ścieżka ciągu znaków jest utrzymywana dla aplikacji i nie jest używana wewnętrznie przez FileX.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **return_path_name**: wskaźnik do lokalizacji docelowej dla ostatniego ciągu katalogu domyślnego. Wartość FX_NULL jest zwracana, jeśli bieżące ustawienie domyślnego katalogu jest katalogiem głównym. Gdy nośnik zostanie otwarty, domyślnie jest to katalog główny.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne pobieranie katalogu domyślnego
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub miejsca docelowego.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ustawia domyślny katalog

### <a name="prototype"></a>Prototype

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a>Opis

Ta usługa ustawia domyślny katalog nośnika. Jeśli zostanie podana wartość FX_NULL, domyślny katalog jest ustawiany na katalog główny nośnika. Wszystkie kolejne operacje na plikach, które nie określają jawnie ścieżki, będą domyślnie w tym katalogu.

> [!IMPORTANT]
> *Domyślny rozmiar ciągu ścieżki wewnętrznej to 256 znaków; można ją zmienić, modyfikując **FX_MAXIMUM_PATH** w **fx_api. h** i przebudować całą bibliotekę FileX. Ścieżka ciągu znaków jest utrzymywana dla aplikacji i nie jest używana wewnętrznie przez FileX.*

> [!IMPORTANT]
> *W przypadku nazw dostarczonych przez aplikację FileX obsługuje zarówno ukośniki odwrotne ( \\ ), jak i ukośniki (/) do oddzielnych katalogów, podkatalogów i nazw plików. Jednak FileX używa tylko znaku ukośnika odwrotnego w ścieżkach zwracanych do aplikacji.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **new_path_name**: wskaźnik do nowej domyślnej nazwy katalogu. Jeśli zostanie podana wartość FX_NULL, domyślny katalog nośnika jest ustawiany na katalog główny nośnika.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) pomyślnego domyślnego zestawu katalogów
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty
- Nie można odnaleźć nowego katalogu **FX_INVALID_PATH** (0x0D)
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa usuwa określony katalog. Należy pamiętać, że katalog musi być pusty, aby go usunąć.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **directory_name**: wskaźnik do nazwy katalogu do usunięcia (ścieżka katalogu jest opcjonalna).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne usunięcie katalogu
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty
- Nie znaleziono podanego katalogu **FX_NOT_FOUND** (0x04)
- **FX_DIR_NOT_EMPTY** (0X10) określony katalog nie jest pusty
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90)
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu
- **FX_NOT_DIRECTORY** (0X0E) nie jest pozycją katalogu
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa Pobiera pierwszą nazwę wpisu w domyślnym katalogu i kopiuje ją do określonego miejsca docelowego.

> [!WARNING]
> *Określona lokalizacja docelowa musi być wystarczająco duża, aby pomieścić nazwę FileX o maksymalnym rozmiarze zdefiniowanym przez **FX_MAX_LONG_NAME_LEN.***

> [!WARNING]
> *Jeśli używasz ścieżki nielokalnej, ważne jest, aby zapobiec (z ThreadX semaforem, muteksem lub zmianami poziomu priorytetu) innych wątków aplikacji od zmiany tego katalogu podczas przechodzenia do katalogu. W przeciwnym razie można uzyskać nieprawidłowe wyniki.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **return_entry_name**: wskaźnik do miejsca docelowego dla pierwszej nazwy wpisu w domyślnym katalogu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) powodzenie pierwszego wpisu katalogu
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90)
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT
- **FX_PTR_ERROR** (0X18) nieprawidłowy nośnik lub wskaźnik docelowy
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem

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

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **directory_name**: wskaźnik do lokalizacji docelowej dla nazwy wpisu katalogu. Musi być co najmniej tak duże jak FX_MAX_LONG_NAME_LEN.
- **atrybuty**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla atrybutów wpisu, które mają zostać umieszczone. Atrybuty są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **rozmiar**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla rozmiaru wpisu w bajtach.
- **Year**: Jeśli wartość nie jest równa null, wskaźnik do lokalizacji docelowej dla pozycji rok modyfikacji wpisu.
- **miesiąc**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego w miesiącu modyfikacji wpisu.
- **dzień**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego w dniu modyfikacji wpisu.
- **godzina**: Jeśli wartość nie jest równa null, wskaźnik do lokalizacji docelowej dla godziny modyfikacji wpisu.
- **minuta**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla minuty modyfikacji wpisu.
- **Second**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla drugiej modyfikacji wpisu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) powodzenie pierwszego wpisu katalogu
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90)
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem
- Plik **_CORRUPT FX_FILE** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub miejsca docelowego.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **directory_name**: wskaźnik na nazwę wpisu katalogu.
- **atrybuty**: wskaźnik do miejsca docelowego dla atrybutów.
- **rozmiar**: wskaźnik do miejsca docelowego dla rozmiaru.
- **Year**: wskaźnik do miejsca docelowego dla roku.
- **miesiąc**: wskaźnik do miejsca docelowego dla miesiąca.
- **dzień**: wskaźnik do miejsca docelowego dla dnia.
- **Hour**: wskaźnik do miejsca docelowego dla godziny.
- **minuta**: wskaźnik do miejsca docelowego dla minuty.
- **sekundę**: wskaźnik do miejsca docelowego dla drugiego.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) powodzenie pierwszego wpisu katalogu
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty
- Nie znaleziono podanego katalogu **FX_NOT_FOUND** (0x04) na nośniku
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90)
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik
- Plik **_CORRUPT FX_FILE** (0x08) jest uszkodzony
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub miejsca docelowego.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Czyści domyślną ścieżkę lokalną

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Opis

Ta usługa czyści poprzednią ścieżkę lokalną skonfigurowaną dla wątku wywołującego.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do wcześniej otwartego nośnika.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) pomyślna ścieżka lokalna została wyczyszczona.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest obecnie otwarty
- Zdefiniowano FX_NO_LCOAL_PATH **FX_NOT_IMPLEMENTED** (0x22)
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika

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

Ta usługa zwraca wskaźnik ścieżki lokalnej określonego nośnika. Jeśli nie ma ustawionej ścieżki lokalnej, do obiektu wywołującego zostaje zwrócona wartość NULL.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **return_path_name**: wskaźnik do docelowego wskaźnika ciągu dla ciągu ścieżki lokalnej, który ma być przechowywany.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) pomyślna ścieżka lokalna get.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest obecnie otwarty
- **FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika


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

Ta usługa przywraca wcześniej ustawioną ścieżkę lokalną. Przywrócono także pozycję wyszukiwania w katalogu dla tej ścieżki lokalnej, co sprawia, że ta procedura jest przydatna w przechodzeniu katalogu cyklicznego przez aplikację.

> [!IMPORTANT]
> *Każda ścieżka lokalna zawiera ciąg **FX_MAXIMUM_PATH** w rozmiarze lokalnym, który domyślnie ma 256 znaków. Ten ciąg ścieżki wewnętrznej nie jest używany przez FileX i jest dostępny tylko dla użycia aplikacji. Jeśli **FX_LOCAL_PATH** ma być zadeklarowana jako zmienna lokalna, użytkownicy powinni mieć możliwość zmiany rozmiaru stosu. Użytkownicy mogą zmniejszyć rozmiar **FX_MAXIMUM_PATH** i ponownie skompilować Źródło biblioteki FileX.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **local_path_ptr**: wskaźnik do wcześniej ustawionej ścieżki lokalnej. Bardzo ważne jest, aby upewnić się, że ten wskaźnik faktycznie wskazuje poprzednio użytą i nadal niezmienioną ścieżkę lokalną.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne przywrócenie ścieżki lokalnej.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest obecnie otwarty.
- Zdefiniowano FX_NO_LCOAL_PATH **FX_NOT_IMPLEMENTED** (0x22).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik ścieżki lub nośnika lokalnego.

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

Ta usługa konfiguruje ścieżkę specyficzną dla wątku określoną przez ***new_path_string** _. Po pomyślnym zakończeniu tej procedury informacje o ścieżce lokalnej przechowywane w _ *_local_path_ptr_** mają pierwszeństwo przed globalną ścieżką nośnika dla wszystkich operacji plików i katalogów wykonywanych przez ten wątek. Nie będzie to miało wpływu na żaden inny wątek w systemie. 
> [!IMPORTANT]
> *Domyślny rozmiar ciągu ścieżki lokalnej to 256 znaków; można ją zmienić, modyfikując **FX_MAXIMUM_PATH** w **fx_api. h** i przebudować całą bibliotekę FileX. Ścieżka ciągu znaków jest utrzymywana dla aplikacji i nie jest używana wewnętrznie przez FileX.*

> [!IMPORTANT]
> *W przypadku nazw dostarczonych przez aplikację FileX obsługuje zarówno ukośniki odwrotne ( \\ ), jak i ukośniki (/) do oddzielnych katalogów, podkatalogów i nazw plików. Jednak FileX używa tylko znaku ukośnika odwrotnego w ścieżkach zwracanych do aplikacji.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do wcześniej otwartego nośnika.
- **local_path_ptr**: miejsce docelowe przechowywania informacji o ścieżce lokalnej dla określonego wątku. Adres tej struktury może być dostarczony do funkcji przywracania ścieżki lokalnej w przyszłości.
- **new_path_name**: Określa ścieżkę lokalną do Instalatora.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) pomyślnego domyślnego zestawu katalogów.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_NOT_IMPLEMENTED** (0x22) * * FX_NO_LCOAL_PATH
- Nie można odnaleźć nowego katalogu **FX_INVALID_PATH** (0x0D).
- **FX_NOT_IMPLEMENTED** (0x22)-* * FX_NO_LOCAL_PATH jest zdefiniowany.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik ścieżki lub nośnika lokalnego.

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

Ta usługa pobiera długą nazwę (jeśli istnieje) skojarzoną z nazwą podanej krótkiej (8,3 formatu). Krótką nazwą może być nazwa pliku lub nazwa katalogu.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **short_name**: wskaźnik na krótką nazwę źródła (format 8,3).
- **long_name**: wskaźnik do miejsca docelowego dla długiej nazwy. Jeśli nie ma długiej nazwy, zwracana jest krótka nazwa. Należy pamiętać, że miejsce docelowe dla długiej nazwy musi być wystarczająco duże, aby pomieścić FX_MAX_LONG_NAME_LEN znaki.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) pomyślnej długiej nazwy Get
- Nie znaleziono krótkiej nazwy **FX_NOT_FOUND** (0x04)
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90)
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem

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

Ta usługa pobiera długą nazwę (jeśli istnieje) skojarzoną z nazwą podanej krótkiej (8,3 formatu). Krótką nazwą może być nazwa pliku lub nazwa katalogu.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **short_name**: wskaźnik na krótką nazwę źródła (format 8,3).
- **long_name**: wskaźnik do miejsca docelowego dla długiej nazwy. Jeśli nie ma długiej nazwy, zwracana jest krótka nazwa. Uwaga: miejsce docelowe dla długiej nazwy musi być wystarczająco duże, aby można było przechowywać **FX_MAX_LONG_NAME_LEN** znaków.
- **long_file_name_buffer_length**: długość buforu długiej nazwy.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) pomyślnej długiej nazwy get.
- Nie znaleziono krótkiej nazwy **FX_NOT_FOUND** (0x04).
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa sprawdza, czy podana nazwa jest katalogiem. Jeśli tak, zwracany jest FX_SUCCESS.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **directory_name**: wskaźnik na nazwę wpisu katalogu.

### <a name="return-values"></a>Wartości zwrócone

- Nazwa podana **FX_SUCCESS** (0x00) jest katalogiem.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty
- Nie można odnaleźć wpisu katalogu **FX_NOT_FOUND** (0x04).
- Wpis **FX_NOT_DIRECTORY** (0x0E) nie jest katalogiem
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Wybiera Następny wpis katalogu

### <a name="prototype"></a>Prototype

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a>Opis

Ta usługa zwraca następną nazwę wpisu w bieżącym katalogu domyślnym.

> [!WARNING]
> *Jeśli używasz ścieżki nielokalnej, ważne jest również, aby zapobiegać (z ThreadX semaforem lub priorytetem wątku) innych wątków aplikacji od zmiany tego katalogu podczas przechodzenia do katalogu. W przeciwnym razie można uzyskać nieprawidłowe wyniki.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **return_entry_name**: wskaźnik do miejsca docelowego dla kolejnej nazwy wpisu w domyślnym katalogu. Bufor, do którego wskazuje, musi być wystarczająco duży, aby pomieścić maksymalny rozmiar nazwy FileX zdefiniowanej przez **_FX_MAX_LONG_NAME_LEN_**.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne znalezienie następnego wpisu
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Pobiera Następny wpis katalogu z pełnymi informacjami

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

Ta usługa pobiera następną nazwę wpisu w domyślnym katalogu i kopiuje ją do określonego miejsca docelowego. Zwraca również pełne informacje o wpisie określone przez dodatkowe parametry wejściowe.

> [!WARNING]
> * Określone miejsce docelowe musi być wystarczająco duże, aby pomieścić maksymalną FileX nazwę, zgodnie z definicją przez * * * FX_MAX_LONG_NAME_LEN * * * *

> [!WARNING]
> *Jeśli używasz ścieżki nielokalnej, ważne jest, aby zapobiec (z ThreadX semaforem, muteksem lub zmianami poziomu priorytetu) innych wątków aplikacji od zmiany tego katalogu podczas przechodzenia do katalogu. W przeciwnym razie można uzyskać nieprawidłowe wyniki.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **directory_name**: wskaźnik do lokalizacji docelowej dla nazwy wpisu katalogu. Musi być co najmniej tak duże jak **FX_MAX_LONG_NAME_LEN**.
- **atrybuty**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla atrybutów wpisu, które mają zostać umieszczone. Atrybuty są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:
  - **FX_READ_ONLY** (0x01)
  - **FX_HIDDEN** (0x02)
  - **FX_SYSTEM** (0x04)
  - **FX_VOLUME** (0x08)
  - **FX_DIRECTORY** (0x10)
  - **FX_ARCHIVE** (0x20)
- **rozmiar**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla rozmiaru wpisu w bajtach.
- **miesiąc**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego w miesiącu modyfikacji wpisu.
- **Year**: Jeśli wartość nie jest równa null, wskaźnik do lokalizacji docelowej dla pozycji rok modyfikacji wpisu.
- **dzień**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego w dniu modyfikacji wpisu.
- **godzina**: Jeśli wartość nie jest równa null, wskaźnik do lokalizacji docelowej dla godziny modyfikacji wpisu.
- **minuta**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla minuty modyfikacji wpisu.
- **Second**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla drugiej modyfikacji wpisu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) powodzenie następnego wpisu katalogu.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub wszystkie parametry wejściowe mają wartość null.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa zmienia nazwę katalogu na określoną nazwę nowego katalogu. Zmiana nazwy jest również wykonywana względem określonej ścieżki lub ścieżki domyślnej. Jeśli ścieżka zostanie określona w nowej nazwie katalogu, katalog nazw zostanie skutecznie przeniesiony do określonej ścieżki. Jeśli ścieżka nie zostanie określona, katalog o zmienionej nazwie zostanie umieszczony w bieżącej ścieżce domyślnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **old_directory_name**: wskaźnik do bieżącej nazwy katalogu.
- **new_directory_name**: wskaźnik do nowej nazwy katalogu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) pomyślna zmiana nazwy katalogu.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie można odnaleźć wpisu katalogu **FX_NOT_FOUND** (0x04).
- Wpis **FX_NOT_DIRECTORY** (0x0E) nie jest katalogiem.
- **FX_INVALID_NAME** (0x0c) Nazwa nowego katalogu jest nieprawidłowa.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu.
- **FX_INVALID_PATH** (0x0D) podano nieprawidłową ścieżkę z nazwą katalogu.
- **FX_ALREADY_CREATED** (0X0B) określony katalog został już utworzony.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa pobiera krótką nazwę (8,3 format) skojarzoną z podaną długą nazwą. Długa nazwa może być nazwą pliku lub nazwą katalogu.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **long_name**: wskaźnik do długiej nazwy źródłowej.
- **short_name**: wskaźnik do lokalizacji docelowej short name (format 8,3). Należy pamiętać, że miejsce docelowe dla krótkiej nazwy musi być wystarczająco duże, aby pomieścić 14 znaków.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) pomyślna krótka nazwa get.
- Nie znaleziono długiej nazwy **FX_NOT_FOUND** (0x04).
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa pobiera krótką nazwę (8,3 format) skojarzoną z podaną długą nazwą. Długa nazwa może być nazwą pliku lub nazwą katalogu.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **long_name**: wskaźnik do długiej nazwy źródłowej.
- **short_name**: wskaźnik do lokalizacji docelowej short name (format 8,3). Uwaga: miejsce docelowe dla krótkiej nazwy musi być wystarczająco duże, aby można było zawierać 14 znaków.
- **short_file_name_length**: długość buforu krótkiej nazwy.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) pomyślna krótka nazwa get.
- Nie znaleziono długiej nazwy **FX_NOT_FOUND** (0x04).
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Włącza usługę odporną na uszkodzenia

### <a name="prototype"></a>Prototype

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a>Opis

Ta usługa umożliwia korzystanie z modułu odpornego na błędy. Po uruchomieniu moduł odporny na uszkodzenia wykrywa, czy system plików jest w obszarze Ochrona odporna na uszkodzenia FileX. Jeśli tak nie jest, usługa odnajdzie dostępne sektory w systemie plików w celu przechowywania dzienników w transakcjach w systemie plików. Jeśli system plików jest w obszarze Ochrona odporna na uszkodzenia FileX, stosuje dzienniki do systemu plików, aby zachować jego integralność.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **memory_ptr**: wskaźnik do bloku pamięci używanej przez moduł odporny na uszkodzenia jako pamięć zapasową.
- **memory_size**: rozmiar pamięci tymczasowej. Aby odporność na uszkodzenia działała prawidłowo, rozmiar pamięci podręcznej wynosi co najmniej 3072 bajtów i musi być wielokrotnością rozmiaru sektora.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślnie włączyła odporność na uszkodzenia.
- Rozmiar pamięci **FX_NOT_ENOUGH_MEMORY** (0x91) jest za mały.
- Błąd sektora rozruchowego **FX_BOOT_ERROR** (0x01).
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_NO_MORE_ENTRIES** (0X0F) nie jest dostępny żaden bezpłatny klaster.
- Nośnik **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej liczby dostępnych klastrów.
- Sektor **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa przydziela i łączy co najmniej jeden klaster ciągły na końcu określonego pliku. FileX określa liczbę klastrów wymaganych przez podzielenie żądanego rozmiaru przez liczbę bajtów na klaster. Następnie wynik zostanie zaokrąglony do następnego całego klastra.

Aby przydzielić miejsce poza 4 GB, aplikacja używa *fx_file_extended_allocate* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do wcześniej otwartego pliku.
- **rozmiar**: liczba bajtów do przydzielenia dla pliku.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna alokacja pliku **FX_SUCCESS** (0x00).
- Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.
- **FX_NO_MORE_ENTRIES** (0X0F) nie jest dostępny żaden bezpłatny klaster.
- Nośnik **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej liczby dostępnych klastrów.
- Sektor **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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
- fx_file_close — fx_file_create
- fx_file_date_time_set
- fx_file_delete
- fx_file_extended_allocate
- fx_file_extended_best_effort_allocate
- fx_file_extended_relative_seek
- fx_file_extended_seek
- fx_file_extended_truncate
- fx_file_extended_truncate_release
- fx_file_open — fx_file_read
- fx_file_relative_seek
- fx_file_rename — fx_file_seek
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

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **file_name**: wskaźnik do nazwy żądanego pliku (ścieżka katalogu jest opcjonalna).
- **attributes_ptr**: wskaźnik do miejsca docelowego dla atrybutów pliku, które mają zostać umieszczone. Atrybuty pliku są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_VOLUME (0x08)
  - FX_DIRECTORY (0x10)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Wartości zwrócone

- Odczytano atrybut **FX_SUCCESS** (0x00).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono określonego pliku **FX_NOT_FOUND** (0x04) na nośniku.
- **FX_NOT_A_FILE** (0X05) określony plik jest katalogiem.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub atrybutów.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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
- fx_file_close — fx_file_create
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

Ustawia atrybuty plików

### <a name="prototype"></a>Prototype

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a>Opis

Ta usługa Ustawia atrybuty pliku na określone przez wywołującego.

> [!WARNING]
> *Aplikacja może tylko modyfikować podzestaw atrybutów pliku za pomocą tej usługi. Wszystkie próby ustawienia dodatkowych atrybutów spowodują wystąpienie błędu.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **file_name**: wskaźnik do nazwy żądanego pliku * * (ścieżka katalogu jest opcjonalna).
- **atrybuty**: nowe atrybuty dla tego pliku. Prawidłowe atrybuty pliku są zdefiniowane w następujący sposób:
  - FX_READ_ONLY (0x01)
  - FX_HIDDEN (0x02)
  - FX_SYSTEM (0x04)
  - FX_ARCHIVE (0x20)

### <a name="return-values"></a>Wartości zwrócone

- Pomyślny zestaw atrybutów **FX_SUCCESS** (0x00).
- Plik **FX_ACCESS_ERROR** (0x06) jest otwarty i nie może mieć ustawionych atrybutów.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tabeli FAT lub exFAT klastra.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.
- Nie znaleziono określonego pliku **FX_NOT_FOUND** (0x04) na nośniku.
- **FX_NOT_A_FILE** (0X05) określony plik jest katalogiem.
- Sektor **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- **FX_INVALID_ATTR** (0x19) wybrano nieprawidłowe atrybuty.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Najlepsze wysiłki w celu przydzielenia miejsca na plik

### <a name="prototype"></a>Prototype

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a>Opis

Ta usługa przydziela i łączy co najmniej jeden klaster ciągły na końcu określonego pliku. FileX określa liczbę klastrów wymaganych przez podzielenie żądanego rozmiaru przez liczbę bajtów na klaster. Następnie wynik zostanie zaokrąglony do następnego całego klastra. Jeśli nie ma wystarczającej liczby kolejnych klastrów dostępnych na nośniku, ta usługa łączy największy dostępny blok kolejnych klastrów do pliku. Ilość miejsca, w którym faktycznie przydzielono plik, jest zwracana do obiektu wywołującego.

Aby przydzielić miejsce poza 4 GB, aplikacja używa *fx_file_extended_best_effort_allocate* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do wcześniej otwartego pliku.
- **rozmiar**: liczba bajtów do przydzielenia dla pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne przydzielenie plików o najlepszej nakładności.
- Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.
- Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.
- Nośnik **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej liczby dostępnych klastrów.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku lub miejsce docelowe.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa zamyka określony plik. Jeśli plik był otwarty do zapisu i jeśli został zmodyfikowany, ta usługa ukończy proces modyfikacji plików przez zaktualizowanie jego wpisu katalogu o nowy rozmiar i bieżącą datę i godzinę systemową.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do wcześniej otwartego pliku.

### <a name="return-values"></a>Wartości zwrócone

- Plik **FX_SUCCESS** (0x00) został pomyślnie zamknięty.
- **FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub atrybutów.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa tworzy określony plik w katalogu domyślnym lub w ścieżce katalogu podanej z nazwą pliku.

> [!WARNING]
> *Ta usługa tworzy plik o zerowej długości, czyli nie przydzielono żadnych klastrów. Alokacja będzie odbywać się automatycznie przy kolejnych zapisach plików lub może zostać wykonana z wyprzedzeniem za pomocą usługi fx_file_allocate lub fx_file_extended_allocate miejsca na miejsce poza 4 GB).*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **file_name**: wskaźnik do nazwy pliku do utworzenia (ścieżka katalogu jest opcjonalna).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślnie utworzono plik.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_ALREADY_CREATED** (0X0B) określony plik został już utworzony.
- **FX_NO_MORE_SPACE** (0x0A) nie ma więcej wpisów w katalogu głównym lub nie ma więcej dostępnych klastrów.
- **FX_INVALID_PATH** (0x0D) podano nieprawidłową ścieżkę z nazwą pliku.
- Nazwa pliku **FX_INVALID_NAME** (0x0c) jest nieprawidłowa.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Nośnik bazowy **FX_WRITE_PROTECT** (0x23) jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nazwy nośnika lub pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

### <a name="sets-file-date-and-time"></a>Ustawia datę i godzinę pliku

Ustawianie daty i godziny pliku

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

Ta usługa ustawia datę i godzinę określonego pliku.

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **file_name**: wskaźnik na nazwę pliku.
- **Year**: wartość roku (1980-2107 włącznie).
- **miesiąc**: wartość miesiąca (1-12 włącznie).
- **dzień**: wartość dnia (1-31 włącznie).
- **godzina**: wartość godziny (0-23 włącznie).
- **minuta**: wartość minuty (0-59 włącznie).
- **sekunda**: wartość sekunda (0-59 włącznie).

### <a name="return-values"></a>Wartości zwrócone

- Data i godzina pomyślnego **FX_SUCCESS** (0x00).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono pliku **FX_NOT_FOUND** (0x04).
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.
- **FX_INVALID_YEAR** (0x12) jest nieprawidłowy.
- **FX_INVALID_MONTH** (0X13) miesiąc jest nieprawidłowy.
- **FX_INVALID_DAY** (0x14) jest nieprawidłowy.
- **FX_INVALID_HOUR** (0X15) godzina jest nieprawidłowa.
- **FX_INVALID_MINUTE** (0X16) minuta jest nieprawidłowa.
- **FX_INVALID_SECOND** (0X17) s jest nieprawidłowy.

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

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **file_name**: wskaźnik do nazwy pliku do usunięcia (ścieżka katalogu jest opcjonalna).

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie usunięto plik **FX_SUCCESS** (0x00).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono określonego pliku **FX_NOT_FOUND** (0x04).
- **FX_NOT_A_FILE** (0X05) określona nazwa pliku jest katalogiem lub woluminem.
- **FX_ACCESS_ERROR** (0X06) określony plik jest obecnie otwarty.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa przydziela i łączy co najmniej jeden klaster ciągły na końcu określonego pliku. FileX określa liczbę klastrów wymaganych przez podzielenie żądanego rozmiaru przez liczbę bajtów na klaster. Następnie wynik zostanie zaokrąglony do następnego całego klastra.

Ta usługa została zaprojektowana do exFAT. Parametr *size* przyjmuje 64-bitową wartość całkowitą, która umożliwia obiektowi wywołującemu wstępne przydzielanie miejsca poza 4 GB zakresem.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do wcześniej otwartego pliku.
- **rozmiar**: liczba bajtów do przydzielenia dla pliku.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna alokacja pliku **FX_SUCCESS** (0x00).
- Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.
- Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.
- Nośnik **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej liczby dostępnych klastrów.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Najlepsze wysiłki w celu przydzielenia miejsca na plik

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a>Opis

Ta usługa przydziela i łączy co najmniej jeden klaster ciągły na końcu określonego pliku. FileX określa liczbę klastrów wymaganych przez podzielenie żądanego rozmiaru przez liczbę bajtów na klaster. Następnie wynik zostanie zaokrąglony do następnego całego klastra. Jeśli nie ma wystarczającej liczby kolejnych klastrów dostępnych na nośniku, ta usługa łączy największy dostępny blok kolejnych klastrów do pliku. Ilość miejsca, w którym faktycznie przydzielono plik, jest zwracana do obiektu wywołującego.

Ta usługa została zaprojektowana do exFAT. Parametr *size* przyjmuje 64-bitową wartość całkowitą, która umożliwia obiektowi wywołującemu wstępne przydzielanie miejsca poza 4 GB zakresem.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do wcześniej otwartego pliku.
- **rozmiar**: liczba bajtów do przydzielenia dla pliku.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślna alokacja pliku **FX_SUCCESS** (0x00).
- Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.
- Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.
- Nośnik **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej liczby dostępnych klastrów.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Położenie do względnego przesunięcia bajtów

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego względnego przesunięcia bajtu. Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.

Ta usługa została zaprojektowana do exFAT. *Byte_offset* parametr przyjmuje wartość 64-bitową, która umożliwia wywołującemu zmianę położenia wskaźnika odczytu/zapisu poza 4 GB zakresu.

> [!IMPORTANT]
> *Jeśli operacja wyszukiwania próbuje przejść poza końcem pliku, wskaźnik odczytu/zapisu pliku jest umieszczany na końcu pliku. Z drugiej strony, jeśli operacja wyszukiwania próbuje nawiązać miejsce poza początkiem pliku, wskaźnik odczytu/zapisu pliku jest umieszczany na początku pliku.*

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do wcześniej otwartego pliku.
- **byte_offset**: żądane względne przesunięcie bajtów w pliku.
- **seek_from**: kierunek i lokalizacja, z której ma zostać wykonane wyszukiwanie względne. Prawidłowe opcje wyszukiwania są zdefiniowane w następujący sposób:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03) Jeśli określono FX_SEEK_BEGIN, operacja wyszukiwania jest wykonywana od początku pliku. Jeśli FX_SEEK_END jest określony, operacja wyszukiwania jest wykonywana wstecz od końca pliku. Jeśli FX_SEEK_FORWARD jest określony, operacja wyszukiwania jest wykonywana w przód od bieżącego położenia pliku. Jeśli FX_SEEK_BACK jest określony, operacja wyszukiwania jest wykonywana wstecz od bieżącego położenia pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne wyszukiwanie względem pliku.
- Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Położenie do przesunięcia bajtów

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego przesunięcia bajtu. Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.

Ta usługa została zaprojektowana do exFAT. *Byte_offset* parametr przyjmuje wartość 64-bitową, która umożliwia wywołującemu zmianę położenia wskaźnika odczytu/zapisu poza 4 GB zakresu.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do bloku kontroli pliku.
- **byte_offset**: wymagane przesunięcie bajtów w pliku. Wartość zero spowoduje umieszczenie wskaźnika odczytu/zapisu na początku pliku, podczas gdy wartość większa od rozmiaru pliku będzie umieścić wskaźnik odczytu/zapisu na końcu pliku.

### <a name="return-values"></a>Wartości zwrócone

- Zakończono wyszukiwanie pliku **FX_SUCCESS** (0x00).
- **FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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
- fx_file_open — fx_file_read
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

Ta usługa obcina rozmiar pliku do określonego rozmiaru. Jeśli podany rozmiar jest większy niż rozmiar rzeczywistego pliku, ta usługa nie wykonuje żadnych działań. Żaden z klastrów multimedialnych skojarzonych z plikiem nie zostanie opublikowany.

> [!WARNING]
> *Należy zachować ostrożność obcinanie plików, które mogą być również otwierane w celu odczytu. Obcinanie pliku otwartego także do odczytu może spowodować odczytanie nieprawidłowych danych.*

Ta usługa została zaprojektowana do exFAT. Parametr *size* przyjmuje 64-bitową wartość całkowitą, która umożliwia wywołującemu działanie poza 4 GB zakresu.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do bloku kontroli pliku.
- **rozmiar**: nowy rozmiar pliku. Bajty znajdujące się przed nowym rozmiarem pliku są odrzucane.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne Obcinanie pliku.
- **FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.
- Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Nośnik bazowy **FX_WRITE_PROTECT** (0x23) jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Obcina plik i zwalnia klastry

### <a name="prototype"></a>Prototype

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a>Opis

Ta usługa obcina rozmiar pliku do określonego rozmiaru. Jeśli podany rozmiar jest większy niż rozmiar rzeczywistego pliku, ta usługa nie wykonuje żadnych działań. W przeciwieństwie do usługi ***fx_file_extended_truncate*** , ta usługa zwalnia wszystkie nieużywane klastry.

> [!WARNING]
> *Należy zachować ostrożność obcinanie plików, które mogą być również otwierane w celu odczytu. Obcinanie pliku otwartego także do odczytu może spowodować odczytanie nieprawidłowych danych.*

Ta usługa została zaprojektowana do exFAT. Parametr *size* przyjmuje 64-bitową wartość całkowitą, która umożliwia wywołującemu działanie poza 4 GB zakresu.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do wcześniej otwartego pliku.
- **rozmiar**: nowy rozmiar pliku. Bajty znajdujące się przed nowym rozmiarem pliku są odrzucane.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne Obcinanie pliku.
- Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.
- Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa otwiera określony plik do odczytu lub zapisu. Plik może być otwarty do odczytu wiele razy, podczas gdy plik może być otwarty tylko raz do momentu zamknięcia pliku przez moduł zapisujący.

> [!IMPORTANT]
> *Należy zwrócić uwagę, jeśli plik jest jednocześnie otwarty do odczytu i zapisu. Zapis pliku wykonywany, gdy plik jest otwarty do odczytu, może nie być widoczny dla czytnika, chyba że czytnik zamknie i ponownie otworzy plik do odczytu. Podobnie podczas korzystania z usług obcinania plików należy zachować ostrożność zapisywania plików. Jeśli plik zostanie obcięty przez składnik zapisywania, czytelnicy tego samego pliku mogą zwrócić nieprawidłowe dane.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **file_ptr**: wskaźnik do bloku kontroli pliku.
- **file_name**: wskaźnik do nazwy pliku do otwarcia (ścieżka katalogu jest opcjonalna).
- **open_type**: typ otwartego pliku. Prawidłowe opcje otwartego typu są następujące:
  - FX_OPEN_FOR_READ (0x00)
  - FX_OPEN_FOR_WRITE (0x01)
  - FX_OPEN_FOR_READ_FAST (0x02)

Otwieranie plików z FX_OPEN_FOR_READ i FX_OPEN_FOR_READ_FAST jest podobne:

- FX_OPEN_FOR_READ obejmuje sprawdzenie, czy połączona lista klastrów składających się na plik jest nienaruszona, a FX_OPEN_FOR_READ_FAST nie przeprowadza tej weryfikacji, co przyspiesza.

### <a name="return-values"></a>Wartości zwrócone

- Plik **FX_SUCCESS** (0x00) został pomyślnie otwarty.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono określonego pliku **FX_NOT_FOUND** (0x04).
- **FX_NOT_A_FILE** (0X05) określona nazwa pliku jest katalogiem lub woluminem.
- **FX_FILE_CORRUPT** (0X08) określony plik jest uszkodzony i nie można otworzyć pliku.
- **FX_ACCESS_ERROR** (0X06) określony plik jest już otwarty lub typ otwarcia jest nieprawidłowy.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Nośnik bazowy **FX_WRITE_PROTECT** (0x23) jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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
- fx_file_close — fx_file_create
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

Ta usługa odczytuje bajty z pliku i zapisuje je w podanym buforze. Po zakończeniu odczytu wewnętrzny wskaźnik odczytu pliku jest dostosowywany do punktu w następnym bajcie pliku. Jeśli liczba pozostałych bajtów w żądaniu jest mniejsza, tylko pozostałe bajty są przechowywane w buforze. W każdym przypadku całkowita liczba bajtów umieszczonych w buforze jest zwracana do obiektu wywołującego.

> [!WARNING]
> *Aplikacja musi upewnić się, że podany bufor jest w stanie przechowywać określoną liczbę żądanych bajtów.*

> [!WARNING]
> *Większa wydajność jest osiągana, jeśli bufor docelowy znajduje się na granicy długiego słowa i żądany rozmiar jest równo widoczny przez sizeof (**ULONG**).*

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do bloku kontroli pliku.
- **buffer_ptr**: wskaźnik do buforu docelowego dla odczytu.
- **request_size**: Maksymalna liczba bajtów do odczytania.
- **actual_size**: wskaźnik do zmiennej, aby pomieścić rzeczywistą liczbę bajtów odczytywanych do podanego buforu.

### <a name="return-values"></a>Wartości zwrócone

- Odczytano plik **FX_SUCCESS** (0x00).
- **FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.
- **FX_FILE_CORRUPT** (0X08) określony plik jest uszkodzony, a odczyt nie powiódł się.
- Osiągnięto koniec pliku **FX_END_OF_FILE** (0x09).
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku lub buforu.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Położenie do względnego przesunięcia bajtów

### <a name="prototype"></a>Prototype

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego względnego przesunięcia bajtu. Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.

> [!IMPORTANT]
> *Jeśli operacja wyszukiwania próbuje przejść poza końcem pliku, wskaźnik odczytu/zapisu pliku jest umieszczany na końcu pliku. Z drugiej strony, jeśli operacja wyszukiwania próbuje nawiązać miejsce poza początkiem pliku, wskaźnik odczytu/zapisu pliku jest umieszczany na początku pliku.*

Aby wyszukać wartość przesunięcia przekraczającą 4 GB, aplikacja używa *fx_file_extended_relative_seek* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do wcześniej otwartego pliku.
- **byte_offset**: żądane względne przesunięcie bajtów w pliku.
- **seek_from**: kierunek i lokalizacja, z której ma zostać wykonane wyszukiwanie względne. Prawidłowe opcje wyszukiwania są zdefiniowane w następujący sposób:
  - FX_SEEK_BEGIN (0x00)
  - FX_SEEK_END (0x01)
  - FX_SEEK_FORWARD (0x02)
  - FX_SEEK_BACK (0x03)

Jeśli FX_SEEK_BEGIN jest określony, operacja wyszukiwania jest wykonywana od początku pliku. Jeśli FX_SEEK_END jest określony, operacja wyszukiwania jest wykonywana wstecz od końca pliku. Jeśli FX_SEEK_FORWARD jest określony, operacja wyszukiwania jest wykonywana w przód od bieżącego położenia pliku. Jeśli FX_SEEK_BACK jest określony, operacja wyszukiwania jest wykonywana wstecz od bieżącego położenia pliku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne wyszukiwanie względem pliku.
- Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa zmienia nazwę pliku określonego przez *old_file_name*. Zmiana nazwy jest również wykonywana względem określonej ścieżki lub ścieżki domyślnej. Jeśli ścieżka zostanie określona w nowej nazwie pliku, plik o zmienionej nazwie jest skutecznie przenoszony do określonej ścieżki. Jeśli ścieżka nie zostanie określona, plik o zmienionej nazwie zostanie umieszczony w bieżącej ścieżce domyślnej.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **old_file_name**: wskaźnik do nazwy pliku do zmiany nazwy (ścieżka katalogu jest opcjonalna).
- **new_file_name**: wskaźnik na nową nazwę pliku. Ścieżka katalogu jest niedozwolona.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślnie zmieniono nazwę pliku.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono określonego pliku **FX_NOT_FOUND** (0x04).
- **FX_NOT_A_FILE** (0X05) określony plik jest katalogiem.
- **FX_ACCESS_ERROR** (0X06) określony plik jest już otwarty.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_INVALID_NAME** (0X0C) określona nazwa nowego pliku nie jest prawidłową nazwą pliku.
- Ścieżka do **FX_INVALID_PATH** (0x0D) jest nieprawidłowa.
- **FX_ALREADY_CREATED** (0x0B) zostanie użyta Nowa nazwa pliku.
- Nośnik **FX_MEDIA_INVALID** (0x02) jest nieprawidłowy.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać tabeli FAT.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Położenie do przesunięcia bajtów

### <a name="prototype"></a>Prototype

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a>Opis

Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego przesunięcia bajtu. Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.

Aby wyszukać wartość przesunięcia przekraczającą 4 GB, aplikacja używa *fx_file_extended_seek* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do bloku kontroli pliku.
- **byte_offset**: wymagane przesunięcie bajtów w pliku. Wartość zero spowoduje umieszczenie wskaźnika odczytu/zapisu na początku pliku, podczas gdy wartość większa od rozmiaru pliku będzie umieścić wskaźnik odczytu/zapisu na końcu pliku.

### <a name="return-values"></a>Wartości zwrócone

- Zakończono wyszukiwanie pliku **FX_SUCCESS** (0x00).
- **FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Obcina plik

### <a name="prototype"></a>Prototype

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a>Opis

Ta usługa obcina rozmiar pliku do określonego rozmiaru. Jeśli podany rozmiar jest większy niż rozmiar rzeczywistego pliku, ta usługa nie wykonuje żadnych działań. Żaden z klastrów multimedialnych skojarzonych z plikiem nie zostanie opublikowany.

> [!WARNING]
> *Należy zachować ostrożność obcinanie plików, które mogą być również otwierane w celu odczytu. Obcinanie pliku otwartego także do odczytu może spowodować odczytanie nieprawidłowych danych.*

Aby działać poza 4 GB, aplikacja używa *fx_file_extended_truncate* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do bloku kontroli pliku.
- **rozmiar**: nowy rozmiar pliku. Bajty znajdujące się przed nowym rozmiarem pliku są odrzucane.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne Obcinanie pliku.
- **FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.
- Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Obcina plik i zwalnia klastry

### <a name="prototype"></a>Prototype

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a>Opis

Ta usługa obcina rozmiar pliku do określonego rozmiaru. Jeśli podany rozmiar jest większy niż rozmiar rzeczywistego pliku, ta usługa nie wykonuje żadnych działań. W przeciwieństwie do usługi ***fx_file_truncate*** , ta usługa zwalnia wszystkie nieużywane klastry.

> [!WARNING]
> *Należy zachować ostrożność obcinanie plików, które mogą być również otwierane w celu odczytu. Obcinanie pliku otwartego także do odczytu może spowodować odczytanie nieprawidłowych danych.*

Aby działać poza 4 GB, aplikacja używa *fx_file_extended_truncate_release* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do wcześniej otwartego pliku.
- **rozmiar**: nowy rozmiar pliku. Bajty znajdujące się przed nowym rozmiarem pliku są odrzucane.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne Obcinanie pliku.
- Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.
- Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Nośnik bazowy **FX_WRITE_PROTECT** (0x23) jest chroniony przed zapisem.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Zapisuje bajty do pliku

### <a name="prototype"></a>Prototype

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a>Opis

Ta usługa zapisuje bajty z określonego buforu, rozpoczynając od bieżącego położenia pliku. Po zakończeniu zapisu wewnętrzny wskaźnik odczytu pliku jest dostosowywany do punktu w następnym bajcie pliku.

> [!WARNING]
> *Większa wydajność jest osiągana, jeśli bufor źródłowy znajduje się na granicy długiego słowa, a żądany rozmiar jest równo widoczny przez sizeof (**ULONG**).*

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do bloku kontroli pliku.
- **buffer_ptr**: wskaźnik do bufora źródłowego zapisu.
- **rozmiar**: liczba bajtów do zapisania.

### <a name="return-values"></a>Wartości zwrócone

- Zakończono zapis pliku **FX_SUCCESS** (0x00).
- **FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.
- Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.
- **FX_NO_MORE_SPACE** (0x0A) nie ma więcej wolnego miejsca na nośniku, aby wykonać ten zapis.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.
- **FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku lub buforu.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa instaluje funkcję wywołania zwrotnego, która jest wywoływana po pomyślnym wykonaniu operacji zapisu w pliku.

### <a name="input-parameters"></a>Parametry wejściowe

- **file_ptr**: wskaźnik do bloku kontroli pliku.
- **file_write_notify**: funkcja wywołania zwrotnego zapisu pliku do zainstalowania. Ustawienie funkcji wywołania zwrotnego na wartość NULL powoduje wyłączenie funkcji wywołania zwrotnego.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślnie zainstalował funkcję wywołania zwrotnego.
- **FX_PTR_ERROR** (0x18) file_ptr ma wartość null.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Przerywa działania multimedialne

### <a name="prototype"></a>Prototype

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Opis

Ta usługa przerywa wszystkie bieżące działania związane z nośnikiem, w tym zamknięcie wszystkich otwartych plików, wysłanie żądania przerwania do skojarzonego sterownika i umieszczenie nośnika w stanie przerwania. Ta usługa jest zazwyczaj wywoływana w przypadku wykrycia błędów we/wy.

> [!WARNING]
> *Przed wykonaniem operacji przerwania należy ponownie otworzyć nośnik.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślne przerwanie nośnika **FX_SUCCESS** (0x00).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Unieważnia pamięć podręczną sektora logicznego

### <a name="prototype"></a>Prototype

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a>Opis

Ta usługa opróżnia wszystkie sektory zanieczyszczone w pamięci podręcznej, a następnie unieważnia całą pamięć podręczną sektora logicznego.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku sterowania nośnikami

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne unieważnienie pamięci podręcznej nośnika.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) nieprawidłowy nośnik lub wskaźnik magazynujący.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Sprawdza nośniki pod kątem błędów

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

Ta usługa sprawdza określony nośnik dla podstawowych błędów strukturalnych, w tym między innymi łączenie plików/katalogów, nieprawidłowe łańcuchy FAT i utracone klastry. Ta usługa zapewnia również możliwość poprawiania wykrytych błędów.

Usługa fx_media_check wymaga pamięci podręcznej na potrzeby pierwszej analizy katalogów i plików na nośniku. W przypadku pamięci poddanej do usługi sprawdzania nośników musi być wystarczająco duży, aby można było przechowywać kilka wpisów w katalogu, ze strukturą danych "Stack" w bieżącym położeniu katalogu przed wprowadzeniem do podkatalogów i na końcu mapy logicznej FAT. Pamięć zapasowa powinna wynosić co najmniej 512-1024 bajtów i pamięć dla mapy bitowej FAT, która wymaga tylu bitów, ile jest klastrów na nośniku. Na przykład urządzenie z 8000 klastrów będzie wymagało, aby reprezentować 1000 bajtów i w ten sposób wymagać całkowitej ilości miejsca w kolejności od 2048 bajtów.

> [!WARNING]
> *Ta usługa powinna być wywoływana tylko natychmiast po fx_media_open i bez żadnych innych działań systemu plików.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **scratch_memory_ptr**: wskaźnik do początku pamięci początkowej.
- **scratch_memory_size**: rozmiar pamięci zapasowej w bajtach.
- **error_correction_option**: opcja korekcji błędów BITS, gdy bit jest ustawiony, Korekcja błędów jest wykonywana. Opcja korekcji błędów jest definiowana w następujący sposób:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02)
  - FX_LOST_CLUSTER_ERROR (0x04) po prostu lub łącznie z wymaganymi opcjami korekcji błędów. Jeśli nie jest wymagana Korekcja błędów, należy podać wartość 0.
- **errors_detected_ptr**: miejsce docelowe dla bitów wykrywania błędów, zgodnie z definicją poniżej:
  - FX_FAT_CHAIN_ERROR (0x01)
  - FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)
  - FX_FILE_SIZE_ERROR (0x08)

### <a name="return-values"></a>Wartości zwrócone

- Zakończono sprawdzanie nośnika **FX_SUCCESS** (0x00), aby uzyskać szczegółowe informacje, zobacz temat błędy wykryte w miejscu docelowym.
- **FX_ACCESS_ERROR** (0X06) nie może wykonać kontroli otwartych plików.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca na nośniku.
- Ilość pamięci poddanej **FX_NOT_ENOUGH_MEMORY** (0x91) nie jest wystarczająco duża.
- **FX_ERROR_NOT_FIXED** (0X93) uszkodzenie katalogu głównego FAT32, którego nie można naprawić.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Sektor **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy.
- **FX_PTR_ERROR** (0X18) nieprawidłowy nośnik lub wskaźnik magazynujący.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.


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

Zamyka nośniki

### <a name="prototype"></a>Prototype

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Opis

Ta usługa zamyka określony nośnik. W procesie zamykania nośnika wszystkie otwarte pliki są zamknięte, a wszystkie pozostałe bufory są opróżniane na nośnik fizyczny.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.

### <a name="return-values"></a>Wartości zwrócone

- Pomyślnie zamknięto nośnik **FX_SUCCESS** (0x00).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa ustawia funkcję wywołania zwrotnego powiadomienia, która zostanie wywołana po pomyślnym zamknięciu nośnika.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **media_close_notify**: funkcja wywołania zwrotnego z powiadomieniem o zamknięciu nośnika zostanie zainstalowana. Przekazywanie wartości NULL jako funkcji wywołania zwrotnego powoduje wyłączenie wywołania zwrotnego zamknięcia nośnika.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślnie zainstalował funkcję wywołania zwrotnego.
- **FX_PTR_ERROR** (0x18) media_ptr ma wartość null.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Formatuje multimedia

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

Ta usługa formatuje dostarczone multimedia w zgodnym exFAT sposób na podstawie podanych parametrów. Ta usługa musi zostać wywołana przed otwarciem nośnika.

> [!WARNING]
> *Formatowanie już sformatowanego nośnika skutecznie kasuje wszystkie pliki i katalogi na nośniku.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika. Jest on używany tylko w celu zapewnienia pewnych podstawowych informacji niezbędnych do działania sterownika.
- **Driver**: wskaźnik do sterownika we/wy dla tego nośnika. Zwykle jest to ten sam sterownik dostarczony do kolejnego wywołania fx_media_open.
- **driver_info_ptr**: wskaźnik do opcjonalnych informacji, które mogą być używane przez sterownik we/wy.
- **memory_ptr**: wskaźnik do pamięci roboczej dla nośnika. memory_size określa rozmiar działającej pamięci multimedialnej. Rozmiar musi być co najmniej tak duży, jak rozmiar sektora nośnika.
- **volume_name**: wskaźnik do ciągu nazwy woluminu, który ma maksymalnie 11 znaków.
- **number_of_fats**: liczba tłuszczów na nośniku. Bieżąca implementacja obsługuje jeden FAT na nośniku.
- **hidden_sectors**: liczba sektorów ukryta przed sektorem rozruchowym tego nośnika. Jest to typowe w przypadku obecności wielu partycji.
- **total_sectors**: Łączna liczba sektorów na nośniku.
- **bytes_per_sector**: liczba bajtów na sektor, co jest zwykle 512. FileX wymaga, aby była to wielokrotność 32.
- **sectors_per_cluster**: liczba sektorów w każdym klastrze. Klaster jest minimalną jednostką alokacji w systemie plików FAT.
- **volumne_serial_number**: numer seryjny, który ma być używany dla tego woluminu.
- **boundary_unit**: rozmiar fizycznego wyrównania obszaru danych, w liczbie sektorów.

### <a name="return-values"></a>Wartości zwrócone

- Format nośnika **FX_SUCCESS** (0x00).
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika, sterownika lub pamięci.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Zwraca dostępne miejsce na multimediach

### <a name="prototype"></a>Prototype

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a>Opis

Ta usługa zwraca liczbę bajtów dostępnych na nośniku.

Ta usługa została zaprojektowana do exFAT. Wskaźnik do *available_bytes* parametr przyjmuje wartość 64-bitową liczbę całkowitą, która umożliwia wywołującemu współpracuję z nośnikami poza 4 GB zakresu.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do wcześniej otwartego nośnika.
- **available_bytes_ptr**: Pozostałe bajty pozostawione na nośniku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślnie pobrała ilość miejsca dostępnego na nośniku.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub wskaźnik dostępnych bajtów ma wartość null.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Opróżnianie danych na nośnik fizyczny

### <a name="prototype"></a>Prototype

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a>Opis

Ta usługa opróżnia wszystkie pliki w pamięci podręcznej i wpisy katalogu wszystkich zmodyfikowanych plików na nośniku fizycznym.

> [!WARNING]
> *Ta procedura może być okresowo wywoływana przez aplikację w celu zmniejszenia ryzyka uszkodzenia i/lub utraty danych w przypadku nagłej utraty mocy na miejscu docelowym.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.

### <a name="return-values"></a>Wartości zwrócone

- Zakończono pomyślne opróżnianie nośnika **FX_SUCCESS** (0x00).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa formatuje dostarczone multimedia w zgodnym z systemem plików FAT 12/16/32 na podstawie podanych parametrów. Ta usługa musi zostać wywołana przed otwarciem nośnika.

> [!WARNING]
> *Formatowanie już sformatowanego nośnika skutecznie kasuje wszystkie pliki i katalogi na nośniku.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika. Jest on używany tylko w celu zapewnienia pewnych podstawowych informacji niezbędnych do działania sterownika.
- **Driver**: wskaźnik do sterownika we/wy dla tego nośnika. Zwykle jest to ten sam sterownik dostarczony do kolejnego wywołania fx_media_open.
- **driver_info_ptr**: wskaźnik do opcjonalnych informacji, które mogą być używane przez sterownik we/wy.
- **memory_ptr**: wskaźnik do pamięci roboczej dla nośnika.
- **memory_size**: Określa rozmiar działającej pamięci multimedialnej. Rozmiar musi być co najmniej tak duży, jak rozmiar sektora nośnika.
- **volume_name**: wskaźnik do ciągu nazwy woluminu, który ma maksymalnie 11 znaków.
- **number_of_fats**: liczba tłuszczów w nośniku. Minimalna wartość to 1 dla podstawowego systemu FAT. Wartości większe niż 1 powodują, że dodatkowe kopie FAT są utrzymywane w czasie wykonywania.
- **directory_entries**: liczba wpisów w katalogu głównym.
- **hidden_sectors**: liczba sektorów ukryta przed sektorem rozruchowym tego nośnika. Jest to typowe w przypadku obecności wielu partycji.
- **total_sectors**: Łączna liczba sektorów na nośniku.
- **bytes_per_sector**: liczba bajtów na sektor, co jest zwykle 512. FileX wymaga, aby była to wielokrotność 32.
- **sectors_per_cluster**: liczba sektorów w każdym klastrze. Klaster jest minimalną jednostką alokacji w systemie plików FAT.
- **Headers**: liczba główek fizycznych.
- **sectors_per_track**: liczba sektorów na ścieżkę.

### <a name="return-values"></a>Wartości zwrócone

- Format nośnika **FX_SUCCESS** (0x00).
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika, sterownika lub pamięci.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Otwiera nośnik na potrzeby dostępu do plików

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

Ta usługa otwiera nośnik na potrzeby dostępu do plików przy użyciu dostarczonego sterownika we/wy.

> [!WARNING]
> *Pamięć dostarczona do tej usługi jest używana do implementowania wewnętrznej pamięci podręcznej sektora logicznego, w związku z czym większa ilość pamięci jest mniejsza. FileX wymaga pamięci podręcznej co najmniej jednego sektora logicznego (bajtów na sektor nośnika).*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **media_name**: wskaźnik do nazwy nośnika.
- **media_driver**: wskaźnik do sterownika we/wy dla tego nośnika. Sterownik we/wy musi być zgodny z wymaganiami dotyczącymi sterownika FileX zdefiniowanymi w rozdziale 5.
- **driver_info_ptr**: wskaźnik do opcjonalnych informacji, które mogą być używane przez dostarczony sterownik we/wy.
- **memory_ptr**: wskaźnik do pamięci roboczej dla nośnika.
- **memory_size**: Określa rozmiar działającej pamięci multimedialnej. Rozmiar musi być tak duży, jak rozmiar sektora nośnika (zwykle 512 bajtów).

### <a name="return-values"></a>Wartości zwrócone

- Pomyślny otwarty nośnik **FX_SUCCESS** (0x00).
- **FX_BOOT_ERROR** (0X01) błąd podczas odczytywania sektora rozruchowego nośnika.
- **FX_MEDIA_INVALID** (0x02) sektor rozruchowy określonego nośnika jest uszkodzony lub nieprawidłowy. Dodatkowo ten kod powrotny jest używany do wskazania, że rozmiar pamięci podręcznej sektora logicznego lub rozmiar wpisu FAT nie jest potęgą liczby 2.
- **FX_FAT_READ_ERROR** (0X03) Błąd odczytywania zawartości multimedialnej FAT.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) co najmniej jeden wskaźnik ma wartość null.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ustawia funkcję powiadamiania Open nośnika

### <a name="prototype"></a>Prototype

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a>Opis

Ta usługa ustawia funkcję wywołania zwrotnego powiadomienia, która zostanie wywołana po pomyślnym otwarciu nośnika.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **media_open_notify**: zostanie zainstalowana funkcja wywołania zwrotnego powiadomienia o otwarciu nośnika. Przekazywanie wartości NULL jako funkcji wywołania zwrotnego powoduje wyłączenie wywołania zwrotnego nośnika.

### <a name="return-values"></a>Wartości zwrócone


- **FX_SUCCESS** (0X00) pomyślnie zainstalował funkcję wywołania zwrotnego.
- **FX_PTR_ERROR** (0x18) media_ptr ma wartość null.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

- **media_ptr**: wskaźnik do wcześniej otwartego nośnika.
- **logical_sector**: sektor logiczny do odczytania.
- **buffer_ptr**: wskaźnik do lokalizacji docelowej dla sektora logicznego.

### <a name="return-values"></a>Wartości zwrócone

- Odczytany nośnik **FX_SUCCESS** (0x00).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub buforu.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Zwraca dostępne miejsce na multimediach

### <a name="prototype"></a>Prototype

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a>Opis

Ta usługa zwraca liczbę bajtów dostępnych na nośniku.

Aby można było współpracować z nośnikiem większym niż 4 GB, aplikacja używa *fx_media_extended_space_available* usługi.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do wcześniej otwartego nośnika.
- **available_bytes_ptr**: Pozostałe bajty pozostawione na nośniku.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślnie zwróciło dostępne miejsce na nośniku.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub wskaźnik dostępnych bajtów ma wartość null.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Pobiera nazwę woluminu multimedialnego

### <a name="prototype"></a>Prototype

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a>Opis

Ta usługa Pobiera nazwę woluminu poprzednio otwartego nośnika.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **volume_name**: wskaźnik do miejsca docelowego dla nazwy woluminu. Należy pamiętać, że miejsce docelowe musi być co najmniej wystarczająco duże, aby pomieścić 12 znaków.
- **volume_source**: określa, gdzie pobrać nazwę z sektora rozruchowego lub katalogu głównego. Prawidłowe wartości tego parametru to:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne pobieranie woluminu multimedialnego.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono woluminu **FX_NOT_FOUND** (0x04).
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik docelowy nośnika lub woluminu.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Pobiera nazwę nośnika z wcześniej otwartym nośnikiem

### <a name="prototype"></a>Prototype

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a>Opis

Ta usługa Pobiera nazwę woluminu poprzednio otwartego nośnika.

> [!IMPORTANT]
> Ta usługa jest taka sama jak ***fx_media_volume_get ()** _, z wyjątkiem tego, że obiekt wywołujący ma rozmiar buforu _ *volume_name**.

### <a name="input-parameters"></a>Parametry wejściowe


- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **volume_name**: wskaźnik do miejsca docelowego dla nazwy woluminu. Należy pamiętać, że miejsce docelowe musi być co najmniej wystarczająco duże, aby pomieścić 12 znaków.
- **volume_name_buffer_length**: rozmiar buforu volume_name.
- **volume_source**: określa, gdzie pobrać nazwę z sektora rozruchowego lub katalogu głównego. Prawidłowe wartości tego parametru to:
  - FX_BOOT_SECTOR
  - FX_DIRECTORY_SECTOR

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne pobieranie woluminu multimedialnego.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono woluminu **FX_NOT_FOUND** (0x04).
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik docelowy nośnika lub woluminu.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa ustawia nazwę woluminu poprzednio otwartego nośnika.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **volume_name**: wskaźnik do nazwy woluminu.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0x00) pomyślny zestaw woluminów multimedialnych.
- **FX_INVALID_NAME** (0x0C) Volume_name jest nieprawidłowy.
- **FX_MEDIA_INVALID** (0X02) nie może ustawić nazwy woluminu.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nazwy nośnika lub woluminu.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa zapisuje podany bufor do określonego sektora logicznego.

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do wcześniej otwartego nośnika.
- **logical_sector**: sektor logiczny do zapisu.
- **buffer_ptr**: wskaźnik do źródła dla zapisu sektora logicznego.

### <a name="return-values"></a>Wartości zwrócone

- Zakończono pomyślnie zapis nośnika **FX_SUCCESS** (0x00).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

- **Year**: wskaźnik do miejsca docelowego dla roku.
- **miesiąc**: wskaźnik do miejsca docelowego dla miesiąca.
- **dzień**: wskaźnik do miejsca docelowego dla dnia.

### <a name="return-values"></a>Wartości zwrócone

- Pobieranie daty pomyślnego **FX_SUCCESS** (0x00).
- **FX_PTR_ERROR** (0X18) co najmniej jeden parametr wejściowy ma wartość null.

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

Ustawia datę systemową

### <a name="prototype"></a>Prototype

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a>Opis

Ta usługa ustawia datę systemową jako określoną.

> [!WARNING]
> *Ta usługa powinna być wywoływana wkrótce po **fx_system_initialize** , aby ustawić początkową datę systemową. Domyślnie Data systemowa to Ostatnia ogólna wersja FileX.*

### <a name="input-parameters"></a>Parametry wejściowe

- **Year**: nowy rok. Prawidłowy zakres jest z zakresu od 1980 do 2107.
- **miesiąc**: nowy miesiąc. Prawidłowy zakres to od 1 do 12.
- **dzień**: nowy dzień. Prawidłowy zakres to od 1 do 31, w zależności od miesiąca i warunków przestępnia.

### <a name="return-values"></a>Wartości zwrócone

- Ustawienie daty pomyślnego **FX_SUCCESS** (0x00).
- **FX_INVALID_YEAR** (0X12) nieprawidłowy określony rok.
- **FX_INVALID_MONTH** (0X13) nieprawidłowy miesiąc.
- Podano nieprawidłowy dzień **FX_INVALID_DAY** (0x14).

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Ta usługa inicjuje wszystkie główne struktury danych FileX. Powinien być wywoływany w ***tx_application_define*** lub prawdopodobnie z wątku inicjującego i musi zostać wywołany przed użyciem innej usługi FileX.

> [!WARNING]
> * Po zainicjowaniu tego wywołania aplikacja powinna wywołać ***fx_system_date_set** _ i _ *fx_system_time_set**, aby rozpocząć od dokładnej daty i godziny systemowej.*

### <a name="input-parameters"></a>Parametry wejściowe

Brak

### <a name="return-values"></a>Wartości zwrócone

Brak.

### <a name="allowed-from"></a>Dozwolone z

Inicjalizacja, wątki

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

Pobiera bieżącą godzinę systemową

### <a name="prototype"></a>Prototype

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a>Opis

Ta usługa Pobiera bieżący czas systemowy.

### <a name="input-parameters"></a>Parametry wejściowe

- **godzina**: wskaźnik do miejsca docelowego dla godziny.
- **minuta**: wskaźnik do miejsca docelowego dla minuty.
- **sekundę**: wskaźnik do miejsca docelowego dla sekund.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne pobieranie czasu systemu.
- **FX_PTR_ERROR** (0X18) co najmniej jeden parametr wejściowy

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

Ustawia bieżącą godzinę systemową

### <a name="prototype"></a>Prototype

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a>Opis

Ta usługa ustawia bieżący czas systemowy na określony przez parametry wejściowe.

> [!WARNING]
> *Ta usługa powinna być wywoływana wkrótce po **fx_system_initialize** , aby ustawić początkowy czas systemowy. Domyślnie czas systemowy to 0:0:0.*

### <a name="input-parameters"></a>Parametry wejściowe

- **godzina**: Nowa godzina (0-23).
- **minuta**: Nowa minuta (0-59).
- **sekundę**: Nowa sekunda (0-59).

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne pobieranie czasu systemu.
- **FX_INVALID_HOUR**    (0X15) Nowa godzina jest nieprawidłowa.
- **FX_INVALID_MINUTE** (0X16) Nowa minuta jest nieprawidłowa.
- **FX_INVALID_SECOND** (0X17) Nowa sekunda jest nieprawidłowa.

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

Ta usługa tworzy podkatalog o nazwie Unicode w bieżącym katalogu domyślnym — informacje o ścieżce nie są dozwolone w parametrze nazwy źródłowej Unicode. Jeśli to się powiedzie, Nazwa krótka (format 8,3) nowo utworzonego podkatalogu Unicode jest zwracana przez usługę.

> [!WARNING]
> *Wszystkie operacje w podkatalogu Unicode (dzięki czemu ścieżka domyślna, usuwanie itp.) powinna zostać wykonana przez dostarczenie zwróconej skróconej nazwy (format 8,3) do standardowych usług katalogowych FileX.*

> [!IMPORTANT]
> *Ta usługa nie jest obsługiwana na nośniku exFAT.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **source_unicode_name**: wskaźnik do nazwy Unicode dla nowego podkatalogu.
- **source_unicode_length**: długość nazwy Unicode.
- **short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3) dla nowego podkatalogu Unicode.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne utworzenie katalogu Unicode.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Określony katalog **FX_ALREADY_CREATED** (0x0B) już istnieje.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej klastrów dostępnych w nośniku dla nowego wpisu katalogu.
- Usługa **FX_NOT_IMPLEMENTED** (0x22) nie została zaimplementowana dla systemu plików exFAT.
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.
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

Ta usługa zmienia podkatalog o nazwie Unicode na określoną nową nazwę Unicode w bieżącym katalogu roboczym. Parametry nazwy Unicode nie mogą zawierać informacji o ścieżce.

> [!IMPORTANT]
> *Ta usługa nie jest obsługiwana na nośniku exFAT.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **old_unicode_name**: wskaźnik do nazwy Unicode dla bieżącego pliku.
- **old_unicode_name_length**: długość bieżącej nazwy Unicode.
- **new_unicode_name**: wskaźnik do nowej nazwy pliku Unicode.
- **old_unicode_name_length**: długość nowej nazwy Unicode.
- **new_short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3) dla pliku Unicode o zmienionej nazwie. Zmień nazwę katalogu na Unicode

### <a name="return-values"></a>Wartości zwrócone

- Pomyślny otwarty nośnik **FX_SUCCESS** (0x00).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_ALREADY_CREATED** (0X0B) określona nazwa katalogu już istnieje.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) co najmniej jeden wskaźnik ma wartość null.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.

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

Ta usługa tworzy plik o nazwie Unicode w bieżącym katalogu domyślnym — w parametrze nazwy źródła Unicode nie można używać informacji o ścieżce. Jeśli to się powiedzie, Nazwa krótka (format 8,3) nowo utworzonego pliku Unicode jest zwracana przez usługę.

> [!WARNING]
> *Wszystkie operacje na pliku Unicode (otwieranie, zapisywanie, odczytywanie, zamykanie itp.) powinny być wykonywane przez dostarczenie zwróconej krótkiej nazwy (format 8,3) do standardowych usług plików FileX.*

### <a name="input-parameters"></a>Parametry wejściowe


- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **source_unicode_name**: wskaźnik do nazwy Unicode dla nowego pliku.
- **source_unicode_length**: długość nazwy Unicode.
- **short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3) dla nowego pliku Unicode.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślnie utworzono plik.
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_ALREADY_CREATED** (0X0B) określony plik już istnieje.
- **FX_NO_MORE_SPACE** (0X0a) nie ma więcej klastrów dostępnych w nośniku dla nowego wpisu pliku.
- Usługa **FX_NOT_IMPLEMENTED** (0x22) nie została zaimplementowana dla systemu plików exFAT.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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
> *Ta usługa nie jest obsługiwana na nośniku exFAT.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **old_unicode_name**: wskaźnik do nazwy Unicode dla bieżącego pliku.
- **old_unicode_name_length**: długość bieżącej nazwy Unicode.
- **new_unicode_name**: wskaźnik do nowej nazwy pliku Unicode.
- **new_unicode_name_length**: długość nowej nazwy Unicode.
- **new_short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3) dla pliku Unicode o zmienionej nazwie.

### <a name="return-values"></a>Wartości zwrócone


- Pomyślny otwarty nośnik **FX_SUCCESS** (0x00).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- **FX_ALREADY_CREATED** (0X0B) określona nazwa pliku już istnieje.
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- **FX_PTR_ERROR** (0X18) co najmniej jeden wskaźnik ma wartość null.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.
- **FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.

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

Ta usługa określa długość podanej nazwy Unicode. Znak Unicode jest reprezentowany przez dwa bajty. Nazwa Unicode to seria dwubajtowych znaków Unicode zakończonych przez dwa bajty NULL (dwa bajty wartości 0).

### <a name="input-parameters"></a>Parametry wejściowe

**unicode_name**: wskaźnik do nazwy Unicode.

### <a name="return-values"></a>Wartości zwrócone

**Długość**: długość nazwy Unicode (liczba znaków Unicode w nazwie).

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

Ta usługa Pobiera długość podanej nazwy Unicode. Znak Unicode jest reprezentowany przez dwa bajty. Nazwa Unicode to seria twobyte znaków Unicode zakończonych przez dwa bajty NULL (dwa bajty wartości 0).

> [!IMPORTANT]
> *Ta usługa jest taka sama jak **fx_unicode_length_get ()** , z wyjątkiem tego, że obiekt wywołujący przekazuje rozmiar buforu **unicode_name** , łącznie z dwoma znakami null.*

### <a name="input-parameters"></a>Parametry wejściowe

- **unicode_name**: wskaźnik do nazwy Unicode.
- **BUFFER_LENGTH**: rozmiar buforu nazw Unicode.

### <a name="return-values"></a>Wartości zwrócone

**Długość**: długość nazwy Unicode (liczba znaków Unicode w nazwie).

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

Ta usługa Pobiera nazwę Unicode skojarzoną z podaną krótką nazwą (format 8,3) w bieżącym katalogu domyślnym — w parametrze krótkiej nazwy nie są dozwolone żadne informacje o ścieżce. Jeśli to się powiedzie, nazwa Unicode skojarzona z krótką nazwą zostanie zwrócona przez usługę.

> [!IMPORTANT]
> *Ta usługa może służyć do pobierania nazw Unicode zarówno dla plików, jak i podkatalogów.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **short_name** Wskaźnik na krótką nazwę (format 8,3).
- **destination_unicode_name**: wskaźnik do miejsca docelowego dla nazwy Unicode skojarzonej z podaną krótką nazwą.
- **destination_unicode_length**: wskaźnik do zwróconej długości nazwy Unicode.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne pobranie nazwy w formacie Unicode.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać tabeli FAT.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono krótkiej nazwy **FX_NOT_FOUND** (0x04) lub rozmiar miejsca docelowego Unicode jest zbyt mały.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa Pobiera nazwę Unicode skojarzoną z podaną krótką nazwą (format 8,3) w bieżącym katalogu domyślnym — w parametrze krótkiej nazwy nie są dozwolone żadne informacje o ścieżce. Jeśli to się powiedzie, nazwa Unicode skojarzona z krótką nazwą zostanie zwrócona przez usługę.

> [!IMPORTANT]
> * Ta usługa jest taka sama jak ***fx_unicode_name_get**_, z wyjątkiem tego, że obiekt wywołujący dostarcza rozmiar docelowego buforu Unicode jako argument wejściowy. Dzięki temu usługa może zagwarantować, że nie zastąpi docelowego buforu Unicode_

> [!IMPORTANT]
> *Ta usługa może służyć do pobierania nazw Unicode zarówno dla plików, jak i podkatalogów.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **short_name**: wskaźnik do krótkiej nazwy (format 8,3).
- **destination_unicode_name**: wskaźnik do miejsca docelowego dla nazwy Unicode skojarzonej z podaną krótką nazwą.
- **destination_unicode_length**: wskaźnik do zwróconej długości nazwy Unicode.
- **unicode_name_buffer_length**: rozmiar buforu nazw Unicode. Uwaga: wymagany jest terminator o wartości NULL, co powoduje dodatkowy bajt.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne pobranie nazwy w formacie Unicode.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać tabeli FAT.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono krótkiej nazwy **FX_NOT_FOUND** (0x04) lub rozmiar miejsca docelowego Unicode jest zbyt mały.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa pobiera krótką nazwę (format 8,3) skojarzoną z nazwą Unicode w bieżącym katalogu domyślnym — w parametrze nazwy Unicode nie można używać informacji o ścieżce. Jeśli to się powiedzie, krótka nazwa skojarzona z nazwą Unicode jest zwracana przez usługę.

> [!IMPORTANT]
> *Ta usługa może służyć do uzyskiwania krótkich nazw zarówno dla plików, jak i podkatalogów.*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **source_unicode_name**: wskaźnik do nazwy Unicode.
- **source_unicode_length**: długość nazwy Unicode.
- **destination_short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3). Musi mieć rozmiar co najmniej 13 bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne pobranie krótkiej nazwy.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać tabeli FAT.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono nazwy Unicode **FX_NOT_FOUND** (0x04).
- Usługa **FX_NOT_IMPLEMENTED** (0x22) nie została zaimplementowana dla systemu plików exFAT.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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

Ta usługa pobiera krótką nazwę (format 8,3) skojarzoną z nazwą Unicode w bieżącym katalogu domyślnym — w parametrze nazwy Unicode nie można używać informacji o ścieżce. Jeśli to się powiedzie, krótka nazwa skojarzona z nazwą Unicode jest zwracana przez usługę.

> [!IMPORTANT]
> *Ta usługa jest taka sama jak **fx_unicode_short_name_get ()**, z wyjątkiem tego, że obiekt wywołujący dostarcza rozmiar buforu docelowego jako argument wejściowy. Dzięki temu usługa może zagwarantować, że krótka nazwa nie przekroczy bufora docelowego.*

*Ta usługa może służyć do uzyskiwania krótkich nazw zarówno dla plików, jak i podkatalogów*

### <a name="input-parameters"></a>Parametry wejściowe

- **media_ptr**: wskaźnik do bloku kontroli nośnika.
- **source_unicode_name**: wskaźnik do nazwy Unicode.
- **source_unicode_length**: długość nazwy Unicode.
- **destination_short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3). Musi mieć rozmiar co najmniej 13 bajtów.
- **short_name_buffer_length**: rozmiar buforu docelowego. Rozmiar buforu musi wynosić co najmniej 14 bajtów.

### <a name="return-values"></a>Wartości zwrócone

- **FX_SUCCESS** (0X00) pomyślne pobranie krótkiej nazwy.
- **FX_FAT_READ_ERROR** (0X03) nie może odczytać tabeli FAT.
- Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony
- Błąd we/wy sterownika **FX_IO_ERROR** (0x90).
- Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.
- Nie znaleziono nazwy Unicode **FX_NOT_FOUND** (0x04).
- Usługa **FX_NOT_IMPLEMENTED** (0x22) nie została zaimplementowana dla systemu plików exFAT.
- **FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.
- **FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.
- Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.

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
