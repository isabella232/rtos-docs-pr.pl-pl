---
title: Rozdział 7 — Azure RTOS śledzenia FileX
description: Ten rozdział zawiera opis zdarzeń Azure RTOS FileX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 8668f0867e205afdeab112dfedd257998a5f5b7ff256f27298072dde3e9019b0
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116803304"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a>Rozdział 7 — Azure RTOS śledzenia FileX

Ten rozdział zawiera opis zdarzeń Azure RTOS FileX. 

## <a name="list-of-events-and-icons"></a>Lista zdarzeń i ikon

**Poniżej znajduje się lista zdarzeń FileX wyświetlanych przez traceX.**

Poniżej opisano każde zdarzenie:

| **Ikona**                         | **Znaczenie**                               |
| -------------------------------- | ----------------------------------------- |
| ![Ikona chybienia wewnętrznej pamięci podręcznej sektorów logicznych](./media/user-guide/fx-events/image1.png)    | Chybienie pamięci podręcznej wewnętrznego sektora logicznego |
| ![Ikona Chybienia pamięci podręcznej katalogu wewnętrznego](./media/user-guide/fx-events/image2.png)    | Chybienie pamięci podręcznej katalogu wewnętrznego |
| ![Ikona opróżnień nośników wewnętrznych](./media/user-guide/fx-events/image3.png)    | Opróżnienie nośnika wewnętrznego |
| ![Ikona odczytu wpisu katalogu wewnętrznego](./media/user-guide/fx-events/image4.png)    | Odczytanie wpisu katalogu wewnętrznego |
| ![Ikona zapisu wpisu katalogu wewnętrznego](./media/user-guide/fx-events/image5.png)    | Wewnętrzny zapis wpisu katalogu |
| ![Ikona odczytu wewnętrznego sterownika We/Wy](./media/user-guide/fx-events/image6.png)    | Odczyt wewnętrznego sterownika We/Wy |
| ![Ikona wewnętrznego zapisu sterownika We/Wy](./media/user-guide/fx-events/image7.png)    | Wewnętrzny zapis sterownika We/Wy |
| ![Ikona Opróżnienie wewnętrznego we/wy sterownika](./media/user-guide/fx-events/image8.png)    | Opróżnienie wewnętrznego sterownika we/wy |
| ![Ikona przerwania wewnętrznego we/wy sterownika](./media/user-guide/fx-events/image9.png)    | Przerwanie wewnętrznego sterownika we/wy |
| ![Ikona inicjowania wewnętrznego sterownika We/Wy](./media/user-guide/fx-events/image10.png)    | Inicjowanie wewnętrznego sterownika we/wy |
| ![Ikona odczytu wewnętrznego sterownika We/Wy](./media/user-guide/fx-events/image11.png)    | Odczyt rozruchu wewnętrznego sterownika we/wy |
| ![Ikona Wewnętrzne sektory zwalniania sterowników we/wy](./media/user-guide/fx-events/image12.png)    | Sektory wydania sterowników we/wy wewnętrznego |
| ![Ikona wewnętrznego zapisu rozruchu sterownika We/Wy](./media/user-guide/fx-events/image13.png)    | Wewnętrzny zapis rozruchu sterownika We/Wy |
| ![Ikona inicjowania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image14.png)    | Inicjowanie wewnętrznego sterownika we/wy |
| ![Ikona Odczytuj atrybuty katalogu](./media/user-guide/fx-events/image15.png)    | **Odczytane atrybuty katalogu** (*fx_directory_attributes_read*) |
| ![Ikona Zestaw atrybutów katalogu](./media/user-guide/fx-events/image16.png)    | **Zestaw atrybutów katalogu** (*fx_directory_attributes_set*) |
| ![Ikona Tworzenia katalogu](./media/user-guide/fx-events/image17.png)    | **Tworzenie katalogu** (*fx_directory_create*) |
| ![Domyślna ikona pobierz katalogu](./media/user-guide/fx-events/image18.png)    | **Domyślne uzyskiwanie katalogu** (*fx_directory_default_get*) |
| ![Ikona Zestaw domyślny katalogu](./media/user-guide/fx-events/image19.png)    | **Zestaw domyślny katalogu** (*fx_directory_default_set*) |
| ![Ikona Usuń katalog](./media/user-guide/fx-events/image20.png)    | **Usuwanie katalogu** *(fx_directory_delete*) |
| ![Ikona Znajdowanie pierwszego wpisu katalogu](./media/user-guide/fx-events/image21.png)    | **Znajdowanie pierwszego wpisu katalogu** (*fx_directory_first_entry_find*) |
| ![Ikona Znajdowanie pierwszego pełnego wpisu katalogu](./media/user-guide/fx-events/image22.png)    | **Znajdowanie pierwszego pełnego wpisu** katalogu (*fx_directory_first_full_entry_find*) |
| ![Ikona Pobierz informacje o katalogu](./media/user-guide/fx-events/image23.png)    | **Uzyskiwanie informacji o katalogu** (*fx_directory_information_get*) |
| ![Ikona Wyczyść ścieżkę lokalną katalogu](./media/user-guide/fx-events/image24.png)    | **Wyczyść ścieżkę lokalną** katalogu (*fx_directory_local_path_clear*) |
| ![Ikona Pobierz ścieżkę lokalną katalogu](./media/user-guide/fx-events/image25.png)    | **Pobierz ścieżkę lokalną** katalogu (*fx_directory_local_path_get*) |
| ![Ikona przywracania ścieżki lokalnej katalogu](./media/user-guide/fx-events/image26.png)    | **Przywracanie ścieżki lokalnej katalogu** *(fx_directory_local_path_restore*) |
| ![Ikona Zestaw ścieżek lokalnych katalogu](./media/user-guide/fx-events/image27.png)    | **Zestaw ścieżek lokalnych katalogu** (*fx_directory_local_path_set*) |
| ![Ikona Pobierz długą nazwę katalogu](./media/user-guide/fx-events/image28.png)    | **Uzyskiwanie długiej nazwy katalogu** *(fx_directory_long_name_get*) |
| ![Ikona Testuj nazwę katalogu](./media/user-guide/fx-events/image29.png)    | **Test nazwy katalogu** (*fx_directory_name_test*) |
| ![Ikona Znajdowanie następnego wpisu katalogu](./media/user-guide/fx-events/image30.png)    | **Znajdowanie następnego wpisu katalogu** (*fx_directory_next_entry_find*) |
| ![Ikona Znajdź następny pełny wpis katalogu](./media/user-guide/fx-events/image31.png)    | **Znajdź następny pełny wpis katalogu** (*fx_directory_next_full_entry_find*) |
| ![Ikona zmiany nazwy katalogu](./media/user-guide/fx-events/image32.png)    | **Zmiana nazwy katalogu** (*fx_directory_rename*) |
| ![Ikona Pobierz krótką nazwę katalogu](./media/user-guide/fx-events/image33.png)    | **Pobierz krótką nazwę katalogu** (*fx_directory_short_name_get*) |
| ![Ikona Przydzielanie pliku](./media/user-guide/fx-events/image34.png)    | **Przydziel plik** *(fx_file_allocate*) |
| ![Ikona Odczyt atrybutów pliku](./media/user-guide/fx-events/image35.png)    | **Odczytane atrybuty pliku** (*fx_file_attributes_read*) |
| ![Ikona Zestaw atrybutów pliku](./media/user-guide/fx-events/image36.png)    | **Zestaw atrybutów pliku** (*fx_file_attributes_set*) |
| ![Ikona przydzielania najlepszego nakładu pracy nad plikiem](./media/user-guide/fx-events/image37.png)    | **Najlepsze przydzielanie plików** *(fx_file_best_effort_allocate*) |
| ![Ikona Zamykanie pliku](./media/user-guide/fx-events/image38.png)    | **Zamknięcie pliku** *(fx_file_close*) |
| ![Ikona Utwórz plik](./media/user-guide/fx-events/image39.png)    | **Tworzenie pliku** *(fx_file_create*) |
| ![Ikona zestawu dat i godzin pliku](./media/user-guide/fx-events/image40.png)    | **Zestaw dat i godzin pliku** *(fx_file_date_time_set*) |
| ![Ikona Usuń plik](./media/user-guide/fx-events/image41.png)    | **Usuwanie pliku** *(fx_file_delete*) |
| ![Ikona Otwórz plik](./media/user-guide/fx-events/image42.png)    | **Plik otwarty** *(fx_file_open*) |
| ![Ikona Odczyt pliku](./media/user-guide/fx-events/image43.png)    | **Odczyt pliku** *(fx_file_read*) |
| ![Ikona względnego szukania pliku](./media/user-guide/fx-events/image44.png)    | **Względne szukanie** pliku (*fx_file_relative_seek*) |
| ![Ikona zmiany nazwy pliku](./media/user-guide/fx-events/image45.png)    | **Zmiana nazwy pliku** (*fx_file_rename*) |
| ![Ikona szukania pliku](./media/user-guide/fx-events/image46.png)    | **Szukanie pliku** *(fx_file_seek*) |
| ![Ikona obcinania pliku](./media/user-guide/fx-events/image47.png)    | **File Truncate** *(fx_file_truncate*) |
| ![File Truncate Release icon (Ikona obcinania wersji pliku)](./media/user-guide/fx-events/image48.png)    | **Wydanie truncate pliku** *(fx_file_truncate_release*) |
| ![Ikona Zapisu pliku](./media/user-guide/fx-events/image49.png)    | **Zapis pliku** *(fx_file_write*) |
| ![Ikona przerwania multimediów](./media/user-guide/fx-events/image50.png)    | **Przerwanie multimediów** (*fx_media_abort*) |
| ![Ikona unieważniaj pamięć podręczną multimediów](./media/user-guide/fx-events/image51.png)    | **Unieważnij pamięć podręczną multimediów** (*fx_media_cache_invalidate*) |
| ![Ikona sprawdzania multimediów](./media/user-guide/fx-events/image52.png)    | **Sprawdzanie multimediów** *(fx_media_check*) |
| ![*Ikona zamykania nośnika](./media/user-guide/fx-events/image53.png)    | **Zamknięcie nośnika** *(fx_media_close*) |
| ![Ikona opróżnień nośnika](./media/user-guide/fx-events/image54.png)    | **Opróżnienie** nośnika (*fx_media_flush*) |
| ![Ikona Formatu multimediów](./media/user-guide/fx-events/image55.png)    | **Format nośnika** *(fx_media_format*) |
| ![Ikona Otwórz multimedia](./media/user-guide/fx-events/image56.png)    | **Media Open** (*fx_media_open*) |
| ![Ikona Odczyt multimediów](./media/user-guide/fx-events/image57.png)    | **Odczyt z nośnika** (*fx_media_read*) |
| ![Ikona Dostępne miejsce na nośniku](./media/user-guide/fx-events/image58.png)    | **Dostępne miejsce na nośniku** *(fx_media_space_available*) |
| ![Ikona Pobierz wolumin multimediów](./media/user-guide/fx-events/image59.png)    | **Pobierz wolumin multimedialny** *(fx_media_volume_get*) |
| ![Ikona zestawu woluminów multimedialnych](./media/user-guide/fx-events/image60.png)    | **Zestaw woluminów multimediów** *(fx_media_volume_set*) |
| ![Ikona zapisu multimediów](./media/user-guide/fx-events/image61.png)    | **Zapis multimediów** *(fx_media_write*) |
| ![Ikona Pobierz datę systemu](./media/user-guide/fx-events/image62.png)    | **System Date Get** (*fx_system_date_get*) |
| ![Ikona systemowego zestawu dat](./media/user-guide/fx-events/image63.png)    | **System Date Set** *(fx_system_date_set*) |
| ![Ikona Inicjowanie systemu](./media/user-guide/fx-events/image64.png)    | **Inicjowanie systemu** (*fx_system_initialize*) |
| ![Ikona Pobierz czas systemowy](./media/user-guide/fx-events/image65.png)    | **System Time Get** (*fx_system_time_get*) |
| ![Ikona systemowego zestawu czasu](./media/user-guide/fx-events/image66.png)    | **System Time Set** *(fx_system_time_set*) |
| ![Ikona Tworzenia katalogu Unicode](./media/user-guide/fx-events/image67.png)    | **Tworzenie katalogu Unicode** *(fx_unicode_directory_create*) |
| ![Ikona zmiany nazwy katalogu Unicode](./media/user-guide/fx-events/image68.png)    | **Zmiana nazwy katalogu Unicode** (*fx_unicode_directory_rename*) |
| ![Ikona Tworzenia pliku Unicode](./media/user-guide/fx-events/image69.png)    | **Tworzenie pliku Unicode** *(fx_unicode_file_create*) |
| ![Ikona zmiany nazwy pliku Unicode](./media/user-guide/fx-events/image70.png)    | **Zmiana nazwy pliku Unicode** (*fx_unicode_file_rename*) |
| ![Unicode Lenght Ikona Pobierz](./media/user-guide/fx-events/image71.png)    | **Unicode Lenght Get** (*fx_unicode_length_get*) |
| ![Ikona Pobierz nazwę Unicode](./media/user-guide/fx-events/image72.png)    | **Unicode Name Get** *(fx_unicode_name_get*) |
| ![Ikona Pobierz krótką nazwę Unicode](./media/user-guide/fx-events/image73.png)    | **Unicode Short Name Get** *(fx_unicode_short_name_get*) |

## <a name="event-descriptions"></a>Opisy zdarzeń

Poniżej opisano poszczególne zdarzenia.

### <a name="internal-logical-sector-cache-miss"></a>Chybienie pamięci podręcznej wewnętrznego sektora logicznego 

#### <a name="internal-logical-sector-cache-miss"></a>Chybienie pamięci podręcznej wewnętrznego sektora logicznego

**Ikona** ![ Ikona chybień w pamięci podręcznej wewnętrznego sektora logicznego](./media/user-guide/fx-events/image1.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne chybienie w pamięci podręcznej sektora logicznego FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Sektor.
- Pole informacji 3: Łączna liczba chybień.
- Pole informacyjne 4: Rozmiar pamięci podręcznej.

### <a name="internal-directory-cache-miss"></a>Chybienie pamięci podręcznej katalogu wewnętrznego

#### <a name="internal-directory-cache-miss"></a>Chybienie pamięci podręcznej katalogu wewnętrznego

**Ikona** ![ Ikona chybień pamięci podręcznej katalogu wewnętrznego](./media/user-guide/fx-events/image2.png)

**Opis** 

To zdarzenie reprezentuje wewnętrzne chybienie w pamięci podręcznej katalogu FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Łączna liczba chybień.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="internal-media-flush"></a>Opróżnienie nośnika wewnętrznego 

#### <a name="internal-media-flush"></a>Opróżnienie nośnika wewnętrznego

**Ikona** ![ Ikona opróżnień nośników wewnętrznych](./media/user-guide/fx-events/image3.png)

**Opis**

To zdarzenie reprezentuje opróżnienie wewnętrznego nośnika FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Liczba zanieczyszczonych sektorów.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.


### <a name="internal-directory-entry-read"></a>Odczytanie wpisu katalogu wewnętrznego 

#### <a name="internal-directory-entry-read"></a>Odczytanie wpisu katalogu wewnętrznego

**Ikona** ![ Ikona odczytu wpisu katalogu wewnętrznego](./media/user-guide/fx-events/image4.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu wpisu wewnętrznego katalogu FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="internal-directory-entry-write"></a>Zapis wpisu katalogu wewnętrznego

#### <a name="internal-directory-entry-write"></a>Zapis wpisu katalogu wewnętrznego

**Ikona** ![ Ikona zapisu wpisu katalogu wewnętrznego](./media/user-guide/fx-events/image5.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu wpisu wewnętrznego katalogu FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="internal-io-driver-read"></a>Odczyt sterownika we/wy wewnętrznego 

#### <a name="internal-io-driver-read"></a>Odczyt sterownika we/wy wewnętrznego 

**Ikona** ![ Ikona odczytu wewnętrznego sterownika We/Wy](./media/user-guide/fx-events/image6.png)

**Opis** 

To zdarzenie reprezentuje wewnętrzne zdarzenie odczytu we/wy sterownika FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Sektor.
- Pole informacyjne 3: Liczba sektorów.
- Pole informacyjne 4: wskaźnik buforu.

### <a name="internal-io-driver-write"></a>Wewnętrzny zapis sterownika We/Wy 

#### <a name="internal-io-driver-write"></a>Wewnętrzny zapis sterownika We/Wy 

**Ikona** ![ Ikona zapisu wewnętrznego sterownika We/Wy](./media/user-guide/fx-events/image7.png)

**Opis** 

To zdarzenie reprezentuje wewnętrzne zdarzenie zapisu we/wy sterownika FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Sektor.
- Pole informacyjne 3: Liczba sektorów.
- Pole informacyjne 4: wskaźnik buforu.

### <a name="internal-io-driver-flush"></a>Opróżnienie wewnętrznego sterownika We/Wy 

#### <a name="internal-io-driver-flush"></a>Opróżnienie wewnętrznego sterownika We/Wy 

**Ikona** ![ Ikona opróżniania wewnętrznego sterownika We/Wy](./media/user-guide/fx-events/image8.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie opróżnienie wewnętrznego sterownika We/Wy pliku FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="internal-io-driver-abort"></a>Przerwanie wewnętrznego sterownika we/wy 

#### <a name="internal-io-dirver-abort"></a>Przerwanie wewnętrznego we/wy

**Ikona** ![ Ikona przerwania sterownika wewnętrznego we/wy](./media/user-guide/fx-events/image9.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania wewnętrznego sterownika We/Wy FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="internal-io-driver-initialize"></a>Inicjowanie wewnętrznego sterownika We/Wy 

#### <a name="internal-io-driver-initialize"></a>Inicjowanie wewnętrznego sterownika We/Wy 

**Ikona** ![ Ikona inicjowania wewnętrznego sterownika We/Wy](./media/user-guide/fx-events/image10.png)

**Opis** 

To zdarzenie reprezentuje wewnętrzny sterownik We/Wy FileX, który inicjuje zdarzenie.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="internal-io-driver-boot-sector-read"></a>Odczyt sektora rozruchowego wewnętrznego we/wy sterownika 

#### <a name="internal-io-driver-boot-sector-read"></a>Odczyt sektora rozruchowego wewnętrznego sterownika we/wy 

**Ikona** ![ Ikona odczytu wewnętrznego sektora rozruchowego sterownika We/Wy](./media/user-guide/fx-events/image11.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie odczytu sektora rozruchowego wewnętrznego we/wy sterownika FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Wskaźnik buforu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="internal-io-driver-release-sectors"></a>Wewnętrzne sektory zwolnienia sterowników we/wy 

#### <a name="internal-io-driver-release-sectors"></a>Wewnętrzne sektory zwalniania sterowników We/Wy 

**Ikona** ![ Ikona wewnętrznych sektorów zwalniania sterowników We/Wy](./media/user-guide/fx-events/image12.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie wewnętrznego zwalniania sterowników We/Wy pliku FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Sektor.
- Pole informacyjne 3: Liczba sektorów.
- Pole informacji 4: nie jest używane.

### <a name="internal-io-driver-boot-sector-write"></a>Wewnętrzny zapis sektora rozruchowego sterownika we/wy

#### <a name="internal-io-driver-boot-sector-write"></a>Wewnętrzny zapis sektora rozruchowego sterownika We/Wy 

**Ikona** ![ Ikona zapisu sektora rozruchowego wewnętrznego we/wy sterownika](./media/user-guide/fx-events/image13.png)

**Opis** 

To zdarzenie reprezentuje zdarzenia zapisu sektora rozruchowego sterownika FileX We/Wy.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Wskaźnik buforu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="internal-io-driver-un-initialize"></a>Cofnie zainicjowanie wewnętrznego sterownika We/Wy 

#### <a name="internal-io-driver-un-initialize"></a>Cofniesz inicjowanie wewnętrznego sterownika We/Wy 

**Ikona** ![ Ikona cofnia inicjowania sterownika wewnętrznego we/wy](./media/user-guide/fx-events/image14.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie inicjowania wewnętrznego sterownika We/Wy pliku FileX.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.
</blockquote></td>

### <a name="directory-attributes-read"></a>Odczytanie atrybutów katalogu 

#### <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read 

**Ikona** ![ Ikona odczytu atrybutów katalogu](./media/user-guide/fx-events/image15.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie odczytu atrybutów katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy katalogu.
- Pole informacyjne 3: Mapa bitowa atrybutów:

  | Atrybut                         | Wartość        |
  |---------------------------------- | --------|
  |  Tylko do odczytu                        | (0x01)  |
  |  Ukryty                           | (0x02)  |
  |  System                           | (0x04)  |
  |  Wolumin                           | (0x08)  |
  |  Katalog                        | (0x10)  |
  |  Archiwum                          | (0x20)  |
- Pole informacji 4: nie jest używane.

### <a name="directory-attributes-set"></a>Zestaw atrybutów katalogu 

#### <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set 

**Ikona** ![ Ikona zestawu atrybutów](./media/user-guide/fx-events/image16.png)

**Opis** 

To zdarzenie reprezentuje katalog, w którym ustawiono zdarzenie atrybutów katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy katalogu.
- Pole informacyjne 3: Mapa bitowa atrybutów:

  |  Atrybut                        | Wartość        |
  |---------------------------------- | --------|
  |  Tylko do odczytu                        | (0x01)  |
  |  Ukryty                           | (0x02)  |
  |  System                           | (0x04)  |
  |  Archiwum                          | (0x20)  |
- Pole informacji 4: nie jest używane.

### <a name="directory-create"></a>Tworzenie katalogu 

#### <a name="fx_directory_create"></a>fx_directory_create

**Ikona** ![ Ikona tworzenia katalogu](./media/user-guide/fx-events/image17.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie tworzenia katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy katalogu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-default-get"></a>Directory Default Get 

#### <a name="fx_directory_default_get"></a>fx_directory_default_get 

**Ikona** ![ Domyślna ikona pobierz katalogu](./media/user-guide/fx-events/image18.png)

**Opis** 

To zdarzenie reprezentuje domyślne zdarzenie zestawu katalogów.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do zwracania nazwy ścieżki.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-default-set"></a>Zestaw domyślny katalogu 

#### <a name="fx_directory_default_set"></a>fx_directory_default_set 

**Ikona** ![ Ikona zestawu domyślnego katalogu](./media/user-guide/fx-events/image19.png)

**Opis** 

To zdarzenie reprezentuje domyślne zdarzenie zestawu katalogów.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Wskaźnik do nowej domyślnej nazwy ścieżki.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-delete"></a>Usuwanie katalogu 

#### <a name="fx_directory_delete"></a>fx_directory_delete

**Ikona** ![ Ikona usuwania katalogu](./media/user-guide/fx-events/image20.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie usuwania katalogu.

**Pola informacji**
- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy katalogu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-first-entry-find"></a>Znajdowanie pierwszego wpisu katalogu 

#### <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

**Ikona** ![ Ikona znajdź pierwszy wpis katalogu](./media/user-guide/fx-events/image21.png)

**Opis** 

To zdarzenie reprezentuje katalogu pierwszy wpis znaleźć zdarzenia.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy katalogu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-first-full-entry-find"></a>Znajdowanie pierwszego pełnego wpisu katalogu 

#### <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

**Ikona** ![ Ikona znajdź pierwszy pełny wpis katalogu](./media/user-guide/fx-events/image22.png)

**Opis** 

To zdarzenie reprezentuje katalogu pierwszego pełnego wpisu znaleźć zdarzenia.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy katalogu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-information-get"></a>Uzyskiwanie informacji o katalogu 

#### <a name="fx_directory_information_get"></a>fx_directory_information_get

**Ikona** ![ Ikona pobierz informacje o katalogu](./media/user-guide/fx-events/image23.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie get informacji o katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy katalogu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-local-path-clear"></a>Wyczyść ścieżkę lokalną katalogu 

#### <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear

**Ikona** ![ Ikona wyczyść ścieżkę lokalną katalogu](./media/user-guide/fx-events/image24.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie wyczyść ścieżkę lokalną katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-local-path-get"></a>Pobierz ścieżkę lokalną katalogu 

#### <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get

**Ikona** ![ Ikona pobierz ścieżkę lokalną katalogu](./media/user-guide/fx-events/image25.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie get ścieżki lokalnej katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do zwracania nazwy ścieżki.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-local-path-restore"></a>Przywracanie ścieżki lokalnej katalogu 

#### <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore

**Ikona** ![ Ikona przywracania ścieżki lokalnej katalogu](./media/user-guide/fx-events/image26.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie przywracania ścieżki lokalnej katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Wskaźnik do lokalnej struktury ścieżki.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-local-path-set"></a>Zestaw ścieżek lokalnych katalogu 

#### <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

**Ikona** ![ Ikona zestawu ścieżek lokalnych katalogu](./media/user-guide/fx-events/image27.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie zestawu ścieżek lokalnych katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Wskaźnik do lokalnej struktury ścieżki.
- Pole informacji 3: Wskaźnik do nowej nazwy ścieżki.
- Pole informacji 4: nie jest używane.

### <a name="directory-long-name-get"></a>Uzyskiwanie długiej nazwy katalogu 

#### <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get

**Ikona** ![ Ikona pobierz długie nazwy katalogu](./media/user-guide/fx-events/image28.png)

**Opis** 

To zdarzenie reprezentuje długiej nazwy katalogu get zdarzenia.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: wskaźnik do krótkiej nazwy pliku.
- Pole informacji 3: wskaźnik do długiej nazwy pliku.
- Pole informacji 4: nie jest używane.

### <a name="directory-name-test"></a>Test nazwy katalogu 

#### <a name="fx_directory_name_test"></a>fx_directory_name_test

**Ikona** ![ Ikona testu nazwy katalogu](./media/user-guide/fx-events/image29.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie testowe nazwy katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy katalogu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-next-entry-find"></a>Znajdowanie następnego wpisu katalogu 

#### <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find

**Ikona** ![ Ikona znajdź następny wpis katalogu](./media/user-guide/fx-events/image30.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie znajdowanie następnego wpisu w katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy katalogu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-next-full-entry-find"></a>Znajdowanie następnego pełnego wpisu katalogu 

#### <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find

**Ikona** ![ Ikona znajdź następny pełny wpis w katalogu](./media/user-guide/fx-events/image31.png)

**Opis**

To zdarzenie reprezentuje katalog następnego pełnego wpisu znaleźć zdarzenia.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy katalogu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="directory-rename"></a>Zmiana nazwy katalogu 

#### <a name="fx_directory_rename-event"></a>fx_directory_rename zdarzeń

**Ikona** ![ Ikona zmiany nazwy katalogu](./media/user-guide/fx-events/image32.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zmiany nazwy katalogu.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do starej nazwy katalogu.
- Pole informacji 3: Wskaźnik do nowej nazwy katalogu.
- Pole informacji 4: nie jest używane.

### <a name="directory-short-name-get"></a>Uzyskiwanie krótkiej nazwy katalogu 

#### <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get

**Ikona** ![ Ikona pobierz krótką nazwę katalogu](./media/user-guide/fx-events/image33.png)

**Opis**

To zdarzenie reprezentuje nazwę krótką katalogu get zdarzenia.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do długiej nazwy pliku.
- Pole informacji 3: Wskaźnik do krótkiej nazwy pliku.
- Pole informacji 4: nie jest używane.

### <a name="file-allocate"></a>Przydzielanie pliku 

#### <a name="fx_file_allocate"></a>fx_file_allocate

**Ikona** ![ Ikona przydzielania pliku](./media/user-guide/fx-events/image34.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przydzielania pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: żądany rozmiar.
- Pole informacji 3: bieżący rozmiar.
- Pole informacji 4: Nowy rozmiar.

### <a name="file-attributes-read"></a>Odczytane atrybuty pliku 

#### <a name="fx_file_attributes_read"></a>fx_file_attributes_read

**Ikona** ![ Ikona odczytu atrybutów pliku](./media/user-guide/fx-events/image35.png)

**Opis**

To zdarzenie reprezentuje zdarzenia odczytu atrybutów pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika. 
- Pole informacji 2: Mapa bitowa atrybutów:

  |  Attribut                         | Wartość        |
  |---------------------------------- | --------|
  |  Tylko do odczytu                        | (0x01)  |
  |  Ukryty                           | (0x02)  |
  |  System                           | (0x04)  |
  |  Wolumin                           | (0x08)  |
  |  Katalog                        | (0x10)  |
  |  Archiwum                          | (0x20)  |
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="file-attributes-set"></a>Zestaw atrybutów pliku 

#### <a name="fx_file_attributes_set"></a>fx_file_attributes_set

**Ikona** ![ Ikona zestawu atrybutów pliku](./media/user-guide/fx-events/image36.png)

**Opis** 

To zdarzenie reprezentuje zdarzenia zestaw atrybutów pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy pliku. 
- Pole informacji 3: Mapa bitów atrybutów:

  | Atrybut                         | Wartość        |
  |---------------------------------- | --------|
  |  Tylko do odczytu                        | (0x01)  |
  |  Ukryty                           | (0x02)  |
  |  System                           | (0x04)  |
  |  Archiwum                          | (0x20)  |
- Pole informacji 4: nie jest używane.

### <a name="file-best-effort-allocate"></a>Przydziel najlepszą nakład pracy na plik 

#### <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

**Ikona** ![ Ikona przydzielania najlepszego nakładu pracy nad plikiem](./media/user-guide/fx-events/image37.png)

**Opis** 

To zdarzenie reprezentuje plik najlepiej przydzielić zdarzenie.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: żądany rozmiar.
- Pole informacji 3: Przydzielony rzeczywisty rozmiar.
- Pole informacji 4: nie jest używane.

### <a name="file-close"></a>Zamykanie pliku 

#### <a name="fx_file_close"></a>fx_file_close

**Ikona** ![ Ikona zamykania pliku](./media/user-guide/fx-events/image38.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie zamknięcia pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: Rozmiar pliku.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="file-create"></a>Tworzenie pliku

#### <a name="fx_file_create"></a>fx_file_create

**Ikona** ![ Ikona tworzenia pliku](./media/user-guide/fx-events/image39.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy pliku.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="file-date-time-set"></a>Zestaw dat i godzin pliku 

#### <a name="fx_file_date_time_set"></a>fx_file_date_time_set

**Ikona** ![ Ikona zestawu dat i godzin pliku](./media/user-guide/fx-events/image40.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu dat/godzin pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy pliku.
- Pole informacji 3: Rok.
- Pole informacji 4: Miesiąc.

### <a name="file-delete"></a>Usuwanie pliku 

#### <a name="fx_file_delete"></a>fx_file_delete

**Ikona** ![ Ikona usuwania pliku](./media/user-guide/fx-events/image41.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy pliku.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="file-open"></a>Plik otwarty 

#### <a name="fx_file_open"></a>fx_file_open

**Ikona** ![ Ikona otwierania pliku](./media/user-guide/fx-events/image42.png)

**Opis**

To zdarzenie reprezentuje zdarzenie otwarcia pliku.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do bloku kontrolki pliku.
- Pole informacji 3: Wskaźnik do nazwy pliku.
- Pole informacji 4: Otwórz typ:

  |  Typ otwierania                        | Wartość        |
  |---------------------------------- | --------|
  |  Otwórz do odczytu                    | (0x00)  |
  |  Otwórz do zapisu                   | (0x01)  |
  |  Szybkie otwieranie do odczytu               | (0x02)  |

### <a name="file-read"></a>Odczyt pliku 

#### <a name="fx_file_read"></a>fx_file_read

**Ikona** ![ Ikona odczytu pliku](./media/user-guide/fx-events/image43.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: wskaźnik buforu.
- Pole informacji 3: Rozmiar żądania.
- Pole informacji 4: odczytany rozmiar rzeczywisty.

### <a name="file-relative-seek"></a>Względne szukanie pliku 

#### <a name="fx_file_relative_seek"></a>fx_file_relative_seek

**Ikona** ![ Ikona względnego szukania pliku](./media/user-guide/fx-events/image44.png)

**Opis**

To zdarzenie reprezentuje zdarzenie względnego szukania pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: Przesunięcie bajtów.
- Pole informacji 3: Szukaj w:

  | Zdarzenie                             | Wartość        |
  |---------------------------------- | --------|
  |  Od początku                   | (0x00)  |
  |  Od końca                         | (0x01)  | 
  |  do przodu                          | (0x02)  |
  |  do tyłu                         | (0x03)  |
- Pole informacji 4: Poprzednie przesunięcie.

### <a name="file-rename"></a>Zmiana nazwy pliku 

#### <a name="fx_file_rename"></a>fx_file_rename

**Ikona** ![ Ikona zmiany nazwy pliku](./media/user-guide/fx-events/image45.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zmiany nazwy pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do starej nazwy pliku.
- Pole informacji 3: Wskaźnik do nowej nazwy pliku.
- Pole informacji 4: nie jest używane.

### <a name="file-seek"></a>Szukanie pliku 

#### <a name="fx_file_seek"></a>fx_file_seek

**Ikona** ![ Ikona szukania pliku](./media/user-guide/fx-events/image46.png)

**Opis**

To zdarzenie reprezentuje zdarzenie szukania pliku.

**Pola informacji** 

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: Przesunięcie bajtów.
- Pole informacji 3: Poprzednie przesunięcie.
- Pole informacji 4: nie jest używane.

### <a name="file-truncate"></a>Obcinanie pliku 

#### <a name="fx_file_truncate"></a>fx_file_truncate

**Ikona** ![ Ikona obcinania pliku](./media/user-guide/fx-events/image47.png)

**Opis**

To zdarzenie reprezentuje zdarzenie obcinania pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: żądany rozmiar.
- Pole informacji 3: poprzedni rozmiar.
- Pole informacji 4: Nowy rozmiar.

### <a name="file-truncate-release"></a>Wydanie truncate pliku 

#### <a name="fx_file_truncate_release"></a>fx_file_truncate_release 

**Ikona** ![ Ikona obcinania pliku wydania](./media/user-guide/fx-events/image48.png)

**Opis**

To zdarzenie reprezentuje zdarzenie obcinania pliku wydania.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: żądany rozmiar.
- Pole informacyjne 3: poprzedni rozmiar.
- Pole informacji 4: Nowy rozmiar.

### <a name="file-write"></a>Zapis pliku 

#### <a name="fx_file_write"></a>fx_file_write 

**Ikona** ![ Ikona zapisu pliku](./media/user-guide/fx-events/image49.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacyjne 2: Wskaźnik buforu.
- Pole informacji 3: Rozmiar żądania.
- Pole informacji 4: zapisany rzeczywisty rozmiar.

### <a name="media-abort"></a>Przerwanie multimediów 

#### <a name="fx_media_abort"></a>fx_media_abort 

**Ikona** ![ Ikona przerwania multimediów](./media/user-guide/fx-events/image50.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania multimediów.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="media-cache-invalidate"></a>Unieważnij pamięć podręczną multimediów

#### <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

**Ikona** ![ Ikona unieważniaj pamięć podręczną multimediów](./media/user-guide/fx-events/image51.png)

**Opis**

To zdarzenie reprezentuje unieważnione zdarzenie pamięci podręcznej multimediów.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="media-check"></a>Sprawdzanie multimediów 

#### <a name="fx_media_check"></a>fx_media_check

**Ikona** ![ Ikona sprawdzania multimediów](./media/user-guide/fx-events/image52.png)

**Opis**

To zdarzenie reprezentuje zdarzenie sprawdzania multimediów.

**Pola informacji** 

- Pole informacyjne 1: wskaźnik do nośnika.
- Info Field 2: Scratch memory pointer (Pole informacyjne 2: wskaźnik pamięci na początku).
- Pole informacyjne 3: Rozmiar pamięci na początku.
- Pole informacji 4: Mapa bitowa błędów:

  | Typ błędu                        | Wartość        |
  |---------------------------------- | --------|
  |  Błąd łańcucha FAT                  | (0x01)  |
  |  Błąd katalogu                  | (0x02)  |
  |  Błąd utraconego klastra               | (0x04)  |
  |  Błąd rozmiaru pliku                  | (0x08)  |

### <a name="media-close"></a>Zamykanie nośnika 

#### <a name="fx_media_close"></a>fx_media_close

**Ikona** ![ Ikona Zamykanie nośnika](./media/user-guide/fx-events/image53.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zamknięcia nośnika.

**Pola informacji** 

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="media-flush"></a>Opróżnienie nośnika 

#### <a name="fx_media_flush"></a>fx_media_flush

**Ikona** ![ Ikona opróżnień nośników](./media/user-guide/fx-events/image54.png)

**Opis**

To zdarzenie reprezentuje zdarzenie opróżnień nośnika.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="media-format"></a>Format multimediów 

#### <a name="fx_media_format"></a>fx_media_format

**Ikona** ![ Ikona formatu multimediów](./media/user-guide/fx-events/image55.png)

**Opis**

To zdarzenie reprezentuje zdarzenie formatu nośnika.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacji 2: liczba wpisów głównych.
- Pole informacyjne 3: Sektory.
- Pole informacyjne 4: Sektory na klaster.

### <a name="media-open"></a>Otwieranie multimediów 

#### <a name="fx_media_open"></a>fx_media_open

**Ikona** ![ Ikona otwierania nośnika](./media/user-guide/fx-events/image56.png)

**Opis**

To zdarzenie reprezentuje otwarte wydarzenie multimedialne.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: wskaźnik do wpisu sterownika multimediów.
- Pole informacyjne 3: Wskaźnik pamięci.
- Pole informacyjne 4: Rozmiar pamięci.

### <a name="media-read-media-read"></a>Odczytywanie multimediów z nośników 

#### <a name="fx_media_read"></a>fx_media_read

**Ikona** ![ Ikona odczytywania multimediów](./media/user-guide/fx-events/image57.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu z nośnika.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: Sektor logiczny.
- Pole informacji 3: wskaźnik buforu.
- Pole informacji 4: odczytane bajty.

### <a name="media-space-available"></a>Dostępne miejsce na nośniku 

#### <a name="fx_media_space_available"></a>fx_media_space_available

**Ikona** ![ Ikona dostępnego miejsca na nośniku](./media/user-guide/fx-events/image58.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dostępne w przestrzeni multimedialnej.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik dostępnych bajtów.
- Pole informacyjne 3: liczba bezpłatnych klastrów.
- Pole informacji 4: nie jest używane.

### <a name="media-volume-get"></a>Pobierz wolumin multimediów 

#### <a name="fx_media_volume_get"></a>fx_media_volume_get

**Ikona** ![ Ikona get woluminu multimedialnego](./media/user-guide/fx-events/image59.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get woluminu multimedialnego.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy woluminu.
- Pole informacji 3: Źródło woluminu.
- Pole informacji 4: nie jest używane.

### <a name="media-volume-set"></a>Zestaw woluminów multimedialnych 

#### <a name="fx_media_volume_set"></a>fx_media_volume_set

**Ikona** ![ Ikona zestawu woluminów multimedialnych](./media/user-guide/fx-events/image60.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu woluminów multimedialnych.

**Pola informacji** 
- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: Wskaźnik do nazwy woluminu.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="media-write"></a>Zapis multimediów 

#### <a name="fx_media_write"></a>fx_media_write

**Ikona** ![ Ikona zapisu multimediów](./media/user-guide/fx-events/image61.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu multimediów.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacyjne 2: Sektor logiczny.
- Pole informacji 3: wskaźnik buforu.
- Pole informacji 4: zapisane bajty.

### <a name="system-date-get"></a>Data systemowa get 

#### <a name="fx_system_date_get"></a>fx_system_date_get 

**Ikona** ![ Ikona pobierz datę systemu](./media/user-guide/fx-events/image62.png)

**Opis**

To zdarzenie reprezentuje datę systemowa get zdarzenia.

**Pola informacji**

- Pole informacji 1: Rok.
- Pole informacji 2: Miesiąc.
- Pole informacji 3: dzień.
- Pole informacji 4: nie jest używane.

### <a name="system-date-set"></a>Zestaw dat systemowych 

#### <a name="fx_system_date_set"></a>fx_system_date_set 

**Ikona** ![ Ikona systemowego zestawu dat](./media/user-guide/fx-events/image63.png)

**Opis**

To zdarzenie reprezentuje zdarzenie systemowe zestawu dat.

**Pola informacji**

- Pole informacji 1: Rok.
- Pole informacji 2: Miesiąc.
- Pole informacji 3: dzień.
- Pole informacji 4: nie jest używane.

### <a name="system-initialize"></a>Inicjowanie systemu 

#### <a name="fx_system_initialize"></a>fx_system_initialize 

**Ikona** ![ Ikona inicjowania systemu](./media/user-guide/fx-events/image64.png)

**Opis**

To zdarzenie reprezentuje system inicjuje zdarzenie.

**Pola informacji**

- Pole informacji 1: nie jest używane.
- Pole informacji 2: nie jest używane.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="system-time-get"></a>Uzyskiwanie czasu systemowego 

#### <a name="fx_system_time_get"></a>fx_system_time_get 

**Ikona** ![ Ikona pobierz czas systemowy](./media/user-guide/fx-events/image65.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get czasu systemowego.

**Pola informacji** 

- Pole informacji 1: godzina.
- Pole informacji 2: minuta.
- Pole informacji 3: drugie.
- Pole informacji 4: nie jest używane.

### <a name="system-time-set"></a>System Time Set 

#### <a name="fx_system_time_set"></a>fx_system_time_set 

**Ikona** ![ Ikona systemowego zestawu czasu](./media/user-guide/fx-events/image66.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu czasowego systemu.

**Pola informacji**

- Pole informacji 1: godzina.
- Pole informacji 2: minuta.
- Pole informacji 3: drugie.
- Pole informacji 4: nie jest używane.

### <a name="unicode-directory-create"></a>Tworzenie katalogu Unicode 

#### <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create 

**Ikona** ![ Ikona tworzenia katalogu Unicode](./media/user-guide/fx-events/image67.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia katalogu Unicode.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacyjne 2: wskaźnik do nazwy Unicode.
- Pole informacyjne 3: rozmiar nazwy Unicode.
- Pole informacyjne 4: Wskaźnik do krótkiej nazwy.

### <a name="unicode-directory-rename"></a>Zmiana nazwy katalogu Unicode 

#### <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

**Ikona** ![ Ikona zmiany nazwy katalogu Unicode](./media/user-guide/fx-events/image68.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zmiany nazwy katalogu Unicode.

**Pola informacji** 

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: wskaźnik do nazwy Unicode.
- Pole informacyjne 3: rozmiar nazwy Unicode.
- Pole informacyjne 4: Wskaźnik do krótkiej nazwy.

### <a name="unicode-file-create"></a>Tworzenie pliku Unicode 

#### <a name="fx_unicode_file_create"></a>fx_unicode_file_create

**Ikona** ![ Ikona tworzenia pliku Unicode](./media/user-guide/fx-events/image69.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia pliku Unicode.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: wskaźnik do nazwy Unicode.
- Pole informacyjne 3: rozmiar nazwy Unicode.
- Pole informacyjne 4: Wskaźnik do krótkiej nazwy.

### <a name="unicode-file-rename"></a>Zmiana nazwy pliku Unicode 

#### <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

**Ikona** ![ Ikona zmiany nazwy pliku Unicode](./media/user-guide/fx-events/image70.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zmiany nazwy pliku Unicode.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: wskaźnik do nazwy Unicode.
- Pole informacyjne 3: rozmiar nazwy Unicode.
- Pole informacyjne 4: Wskaźnik do krótkiej nazwy.

### <a name="unicode-length-get"></a>Unicode Length Get 

#### <a name="fx_unicode_length_get"></a>fx_unicode_length_get

**Ikona** ![ Ikona get długości kodu Unicode](./media/user-guide/fx-events/image71.png)

**Opis**

To zdarzenie reprezentuje zdarzenie get o długości Unicode.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nazwy Unicode.
- Pole informacyjne 2: Długość.
- Pole informacji 3: nie jest używane.
- Pole informacji 4: nie jest używane.

### <a name="unicode-name-get"></a>Uzyskiwanie nazwy Unicode 

#### <a name="fx_unicode_name_get"></a>fx_unicode_name_get

**Ikona** ![ Ikona get nazwy Unicode](./media/user-guide/fx-events/image72.png)

**Opis**

To zdarzenie reprezentuje nazwę Unicode get zdarzenia.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: krótka nazwa źródła.
- Pole informacyjne 3: docelowy wskaźnik nazwy Unicode.
- Pole informacyjne 4: docelowa długość nazwy Unicode.

### <a name="unicode-short-name-get"></a>Unicode Short Name Get 

#### <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

**Ikona** ![ Ikona pobierz krótką nazwę Unicode](./media/user-guide/fx-events/image73.png)

**Opis**

To zdarzenie reprezentuje skróconą nazwę Unicode get event.

**Pola informacji**

- Pole informacyjne 1: wskaźnik do nośnika.
- Pole informacyjne 2: wskaźnik do źródłowej nazwy Unicode.
- Pole informacyjne 3: długość nazwy Unicode.
- Pole informacyjne 4: Wskaźnik do krótkiej nazwy.