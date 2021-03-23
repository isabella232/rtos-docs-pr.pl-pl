---
title: Rozdział 7 — zdarzenia śledzenia usługi Azure RTO FileX
description: Ten rozdział zawiera opis zdarzeń usługi Azure RTO FileX.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: c3cbc945e33b87b6759c56ec1429d6bf57259bd9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823395"
---
# <a name="chapter-7---azure-rtos-filex-trace-events"></a>Rozdział 7 — zdarzenia śledzenia usługi Azure RTO FileX

Ten rozdział zawiera opis zdarzeń usługi Azure RTO FileX. 

## <a name="list-of-events-and-icons"></a>Lista zdarzeń i ikon

**Poniżej znajduje się lista zdarzeń FileX wyświetlanych przez TraceX.**

Poniżej opisano każde zdarzenie:

| **Ikona**                         | **Znaczenie**                               |
| -------------------------------- | ----------------------------------------- |
| ![Ikona chybień wewnętrznej pamięci podręcznej sektora logicznego](./media/user-guide/fx-events/image1.png)    | Chybienia w pamięci podręcznej wewnętrznego sektora logicznego |
| ![Ikona chybień w pamięci podręcznej katalogów wewnętrznych](./media/user-guide/fx-events/image2.png)    | Chybienia w pamięci podręcznej katalogów wewnętrznych |
| ![Ikona opróżniania nośnika wewnętrznego](./media/user-guide/fx-events/image3.png)    | Wewnętrzne opróżnianie nośnika |
| ![Ikona odczytu wpisu katalogu wewnętrznego](./media/user-guide/fx-events/image4.png)    | Odczyt wpisu katalogu wewnętrznego |
| ![Ikona zapisu w katalogu wewnętrznym](./media/user-guide/fx-events/image5.png)    | Zapis wpisu w katalogu wewnętrznym |
| ![Ikona odczytu wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image6.png)    | Odczyt wewnętrznego sterownika we/wy |
| ![Ikona wewnętrznego zapisu sterownika we/wy](./media/user-guide/fx-events/image7.png)    | Zapis wewnętrznego sterownika we/wy |
| ![Ikona opróżniania sterownika wewnętrznego we/wy](./media/user-guide/fx-events/image8.png)    | Wewnętrzny opróżnia sterownika we/wy |
| ![Ikona przerwania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image9.png)    | Przerwanie wewnętrznego sterownika we/wy |
| ![Ikona inicjowania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image10.png)    | Inicjowanie wewnętrznego sterownika we/wy |
| ![Ikona odczytu wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image11.png)    | Odczyt wewnętrznego sterownika we/wy |
| ![Ikona wewnętrznych sektorów sterowników we/wy](./media/user-guide/fx-events/image12.png)    | Sektory wersji wewnętrznego sterownika we/wy |
| ![Ikona zapisu wewnętrznego rozruchowego sterownika we/wy](./media/user-guide/fx-events/image13.png)    | Zapis rozruchowy wewnętrznego sterownika we/wy |
| ![Ikona cofnięcia inicjalizacji sterownika sterownika wewnętrznego we/wy](./media/user-guide/fx-events/image14.png)    | Wewnętrzny sterownik sterownika we/wy nie został zainicjowany |
| ![Ikona odczytu atrybutów katalogu](./media/user-guide/fx-events/image15.png)    | **Odczyt atrybutów katalogu** (*fx_directory_attributes_read*) |
| ![Ikona zestawu atrybutów katalogu](./media/user-guide/fx-events/image16.png)    | **Zestaw atrybutów katalogu** (*fx_directory_attributes_set*) |
| ![Ikona tworzenia katalogu](./media/user-guide/fx-events/image17.png)    | **Tworzenie katalogu** (*fx_directory_create*) |
| ![Ikona pobierania domyślnego katalogu](./media/user-guide/fx-events/image18.png)    | **Domyślne pobieranie katalogu** (*fx_directory_default_get*) |
| ![Ikona domyślnego zestawu katalogów](./media/user-guide/fx-events/image19.png)    | **Domyślny zestaw katalogów** (*fx_directory_default_set*) |
| ![Ikona usuwania katalogu](./media/user-guide/fx-events/image20.png)    | **Usuwanie katalogu** (*fx_directory_delete*) |
| ![Ikona wyszukiwania pierwszego wpisu katalogu](./media/user-guide/fx-events/image21.png)    | **Znajdź pierwszy wpis w katalogu** (*fx_directory_first_entry_find*) |
| ![Ikona wyszukiwania pierwszego wpisu katalogu](./media/user-guide/fx-events/image22.png)    | **Znajdowanie pierwszego wpisu katalogu** (*fx_directory_first_full_entry_find*) |
| ![Ikona uzyskiwania informacji o katalogu](./media/user-guide/fx-events/image23.png)    | **Pobieranie informacji o katalogu** (*fx_directory_information_get*) |
| ![Ikona czyszczenia ścieżki lokalnej katalogu](./media/user-guide/fx-events/image24.png)    | **Ścieżka lokalna katalogu jest niezrozumiała** (*fx_directory_local_path_clear*) |
| ![Ikona pobierania ścieżki lokalnej katalogu](./media/user-guide/fx-events/image25.png)    | **Pobieranie ścieżki lokalnej katalogu** (*fx_directory_local_path_get*) |
| ![Ikona przywracania ścieżki lokalnej katalogu](./media/user-guide/fx-events/image26.png)    | **Przywracanie ścieżki lokalnej katalogu** (*fx_directory_local_path_restore*) |
| ![Ikona zestawu ścieżek lokalnych katalogu](./media/user-guide/fx-events/image27.png)    | **Zestaw ścieżek lokalnych katalogu** (*fx_directory_local_path_set*) |
| ![Ikona pobierania długich nazw katalogów](./media/user-guide/fx-events/image28.png)    | **Pobieranie długiej nazwy katalogu** (*fx_directory_long_name_get*) |
| ![Ikona testu nazwy katalogu](./media/user-guide/fx-events/image29.png)    | **Test nazwy katalogu** (*fx_directory_name_test*) |
| ![Ikona wyszukiwania następnego wpisu w katalogu](./media/user-guide/fx-events/image30.png)    | **Znajdź wpis w katalogu** (*fx_directory_next_entry_find*) |
| ![Ikona wyszukiwania następnego wpisu w katalogu](./media/user-guide/fx-events/image31.png)    | **Znajdź następny pełny wpis w katalogu** (*fx_directory_next_full_entry_find*) |
| ![Ikona zmiany nazwy katalogu](./media/user-guide/fx-events/image32.png)    | **Zmiana nazwy katalogu** (*fx_directory_rename*) |
| ![Ikona pobierania krótkiej nazwy katalogu](./media/user-guide/fx-events/image33.png)    | **Krótka nazwa katalogu Get** (*fx_directory_short_name_get*) |
| ![Ikona alokacji plików](./media/user-guide/fx-events/image34.png)    | **Przydzielenie pliku** (*fx_file_allocate*) |
| ![Ikona odczytu atrybutów plików](./media/user-guide/fx-events/image35.png)    | **Odczyt atrybutów pliku** (*fx_file_attributes_read*) |
| ![Ikona zestawu atrybutów pliku](./media/user-guide/fx-events/image36.png)    | **Zestaw atrybutów pliku** (*fx_file_attributes_set*) |
| ![Ikona przydziału najlepszego nakładu pracy pliku](./media/user-guide/fx-events/image37.png)    | **Przydział najlepszego nakładu pracy w pliku** (*fx_file_best_effort_allocate*) |
| ![Ikona zamykania pliku](./media/user-guide/fx-events/image38.png)    | **Zamknij plik** (*fx_file_close*) |
| ![Ikona tworzenia pliku](./media/user-guide/fx-events/image39.png)    | **Tworzenie pliku** (*fx_file_create*) |
| ![Ikona Ustawienia daty i godziny pliku](./media/user-guide/fx-events/image40.png)    | **Data i godzina ustawienia pliku** (*fx_file_date_time_set*) |
| ![Ikona usuwania pliku](./media/user-guide/fx-events/image41.png)    | **Usuwanie pliku** (*fx_file_delete*) |
| ![Ikona otwierania pliku](./media/user-guide/fx-events/image42.png)    | **Otwieranie pliku** (*fx_file_open*) |
| ![Ikona odczytu pliku](./media/user-guide/fx-events/image43.png)    | **Odczyt pliku** (*fx_file_read*) |
| ![Ikona wyszukiwania względnego pliku](./media/user-guide/fx-events/image44.png)    | **Wyszukiwanie względne plików** (*fx_file_relative_seek*) |
| ![Ikona zmiany nazwy pliku](./media/user-guide/fx-events/image45.png)    | **Zmiana nazwy pliku** (*fx_file_rename*) |
| ![Ikona wyszukiwania plików](./media/user-guide/fx-events/image46.png)    | **Wyszukiwanie plików** (*fx_file_seek*) |
| ![Ikona obcinania plików](./media/user-guide/fx-events/image47.png)    | **Obcinanie pliku** (*fx_file_truncate*) |
| ![Ikona wycięcia plików](./media/user-guide/fx-events/image48.png)    | **Wydanie obcinania plików** (*fx_file_truncate_release*) |
| ![Ikona zapisu pliku](./media/user-guide/fx-events/image49.png)    | **Zapis pliku** (*fx_file_write*) |
| ![Ikona przerwania nośnika](./media/user-guide/fx-events/image50.png)    | **Przerwanie nośnika** (*fx_media_abort*) |
| ![Ikona unieważniania pamięci podręcznej multimediów](./media/user-guide/fx-events/image51.png)    | **Unieważnienie pamięci podręcznej multimediów** (*fx_media_cache_invalidate*) |
| ![Ikona Sprawdź multimedia](./media/user-guide/fx-events/image52.png)    | **Sprawdzenie multimediów** (*fx_media_check*) |
| ![* Ikona zamykania nośnika](./media/user-guide/fx-events/image53.png)    | **Zamknięcie nośnika** (*fx_media_close*) |
| ![Ikona opróżniania nośnika](./media/user-guide/fx-events/image54.png)    | **Opróżnianie multimediów** (*fx_media_flush*) |
| ![Ikona formatu multimediów](./media/user-guide/fx-events/image55.png)    | **Format multimediów** (*fx_media_format*) |
| ![Ikona otwarcia nośnika](./media/user-guide/fx-events/image56.png)    | **Otwarte multimedia** (*fx_media_open*) |
| ![Ikona odczytu multimediów](./media/user-guide/fx-events/image57.png)    | **Odczyt z nośnika** (*fx_media_read*) |
| ![Ikona dostępnego miejsca na multimediach](./media/user-guide/fx-events/image58.png)    | **Dostępne miejsce na nośniku** (*fx_media_space_available*) |
| ![Ikona pobierania woluminu multimedialnego](./media/user-guide/fx-events/image59.png)    | **Pobieranie woluminu multimedialnego** (*fx_media_volume_get*) |
| ![Ikona zestawu woluminów multimedialnych](./media/user-guide/fx-events/image60.png)    | **Zestaw woluminów multimedialnych** (*fx_media_volume_set*) |
| ![Ikona zapisu multimediów](./media/user-guide/fx-events/image61.png)    | **Zapis multimediów** (*fx_media_write*) |
| ![Ikona pobierania daty systemu](./media/user-guide/fx-events/image62.png)    | **Data systemu Get** (*fx_system_date_get*) |
| ![Ikona zestawu dat systemu](./media/user-guide/fx-events/image63.png)    | **Zestaw dat systemu** (*fx_system_date_set*) |
| ![Ikona inicjowania systemu](./media/user-guide/fx-events/image64.png)    | **Inicjowanie systemu** (*fx_system_initialize*) |
| ![Ikona uzyskiwania czasu systemowego](./media/user-guide/fx-events/image65.png)    | **Pobieranie czasu systemu** (*fx_system_time_get*) |
| ![Ikona Ustawienia czasu systemowego](./media/user-guide/fx-events/image66.png)    | **Zestaw czasu systemu** (*fx_system_time_set*) |
| ![Ikona tworzenia katalogu Unicode](./media/user-guide/fx-events/image67.png)    | **Tworzenie katalogu Unicode** (*fx_unicode_directory_create*) |
| ![Ikona zmiany nazwy katalogu Unicode](./media/user-guide/fx-events/image68.png)    | **Zmiana nazwy katalogu Unicode** (*fx_unicode_directory_rename*) |
| ![Ikona tworzenia pliku Unicode](./media/user-guide/fx-events/image69.png)    | **Tworzenie pliku Unicode** (*fx_unicode_file_create*) |
| ![Ikona zmiany nazwy pliku Unicode](./media/user-guide/fx-events/image70.png)    | **Zmiana nazwy pliku Unicode** (*fx_unicode_file_rename*) |
| ![Ikona pobierania Unicode Długość](./media/user-guide/fx-events/image71.png)    | **Długość Unicode — pobieranie** (*fx_unicode_length_get*) |
| ![Ikona pobierania nazwy Unicode](./media/user-guide/fx-events/image72.png)    | **Pobieranie nazwy Unicode** (*fx_unicode_name_get*) |
| ![Ikona pobierania krótkiej nazwy Unicode](./media/user-guide/fx-events/image73.png)    | **Pobieranie krótkiej nazwy Unicode** (*fx_unicode_short_name_get*) |

## <a name="event-descriptions"></a>Opisy zdarzeń

Poniżej opisano poszczególne zdarzenia.

### <a name="internal-logical-sector-cache-miss"></a>Chybienia w pamięci podręcznej wewnętrznego sektora logicznego 

#### <a name="internal-logical-sector-cache-miss"></a>Chybienia w pamięci podręcznej wewnętrznego sektora logicznego

**Ikona** ![ Ikona chybień wewnętrznej pamięci podręcznej sektora logicznego](./media/user-guide/fx-events/image1.png)

**Opis**

To zdarzenie reprezentuje błąd wewnętrzny FileX pamięci podręcznej sektora logicznego.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: sektor.
- Pole informacji 3: całkowita liczba chybień.
- Pole informacji 4: rozmiar pamięci podręcznej.

### <a name="internal-directory-cache-miss"></a>Chybienia w pamięci podręcznej katalogów wewnętrznych

#### <a name="internal-directory-cache-miss"></a>Chybienia w pamięci podręcznej katalogów wewnętrznych

**Ikona** ![ Ikona chybień w pamięci podręcznej katalogów wewnętrznych](./media/user-guide/fx-events/image2.png)

**Opis** 

To zdarzenie reprezentuje wewnętrzny chybień w pamięci podręcznej usługi FileX.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: całkowita liczba chybień.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="internal-media-flush"></a>Wewnętrzne opróżnianie nośnika 

#### <a name="internal-media-flush"></a>Wewnętrzne opróżnianie nośnika

**Ikona** ![ Ikona opróżniania nośnika wewnętrznego](./media/user-guide/fx-events/image3.png)

**Opis**

To zdarzenie reprezentuje wewnętrzne opróżnianie nośnika FileX.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: liczba zanieczyszczonych sektorów.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.


### <a name="internal-directory-entry-read"></a>Odczyt wpisu katalogu wewnętrznego 

#### <a name="internal-directory-entry-read"></a>Odczyt wpisu katalogu wewnętrznego

**Ikona** ![ Ikona odczytu wpisu katalogu wewnętrznego](./media/user-guide/fx-events/image4.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu wewnętrznego katalogu FileX.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="internal-directory-entry-write"></a>Zapis wpisu w katalogu wewnętrznym

#### <a name="internal-directory-entry-write"></a>Zapis wpisu w katalogu wewnętrznym

**Ikona** ![ Ikona zapisu w katalogu wewnętrznym](./media/user-guide/fx-events/image5.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu wewnętrznego wpisu katalogu FileX.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="internal-io-driver-read"></a>Odczyt wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-read"></a>Odczyt wewnętrznego sterownika we/wy 

**Ikona** ![ Ikona odczytu wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image6.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie odczytu sterownika wewnętrznego FileX we/wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: sektor.
- Pole informacji 3: liczba sektorów.
- Pole informacji 4: wskaźnik buforu.

### <a name="internal-io-driver-write"></a>Zapis wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-write"></a>Zapis wewnętrznego sterownika we/wy 

**Ikona** ![ Ikona wewnętrznego zapisu sterownika we/wy](./media/user-guide/fx-events/image7.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie zapisu wewnętrznego FileX we/wy sterownika.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: sektor.
- Pole informacji 3: liczba sektorów.
- Pole informacji 4: wskaźnik buforu.

### <a name="internal-io-driver-flush"></a>Wewnętrzny opróżnia sterownika we/wy 

#### <a name="internal-io-driver-flush"></a>Wewnętrzny opróżnia sterownika we/wy 

**Ikona** ![ Ikona opróżniania sterownika wewnętrznego we/wy](./media/user-guide/fx-events/image8.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie FileX wewnętrznego opróżniania sterownika we/wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="internal-io-driver-abort"></a>Przerwanie wewnętrznego sterownika we/wy 

#### <a name="internal-io-dirver-abort"></a>Przerwanie wewnętrznego wejścia/wyjścia dirver

**Ikona** ![ Ikona przerwania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image9.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania wewnętrznego sterownika wejścia/wyjścia FileX.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="internal-io-driver-initialize"></a>Inicjowanie wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-initialize"></a>Inicjowanie wewnętrznego sterownika we/wy 

**Ikona** ![ Ikona inicjowania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image10.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie inicjowania sterownika wewnętrznego FileX we/wy.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="internal-io-driver-boot-sector-read"></a>Odczyt wewnętrznego sektora rozruchowego sterownika we/wy 

#### <a name="internal-io-driver-boot-sector-read"></a>Odczyt wewnętrznego sektora rozruchowego sterownika we/wy 

**Ikona** ![ Ikona odczytu wewnętrznego sektora rozruchowego sterownika we/wy](./media/user-guide/fx-events/image11.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie odczytu sektora rozruchowego wewnętrznego sterownika we/wy FileX.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik buforu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="internal-io-driver-release-sectors"></a>Sektory wersji wewnętrznego sterownika we/wy 

#### <a name="internal-io-driver-release-sectors"></a>Sektory wersji wewnętrznego sterownika we/wy 

**Ikona** ![ Ikona wewnętrznych sektorów sterowników we/wy](./media/user-guide/fx-events/image12.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie wewnętrznego sektora FileX we/wy sterownika.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: sektor.
- Pole informacji 3: liczba sektorów.
- Pole informacji 4: nieużywane.

### <a name="internal-io-driver-boot-sector-write"></a>Zapis wewnętrznego sektora rozruchowego sterownika we/wy

#### <a name="internal-io-driver-boot-sector-write"></a>Zapis wewnętrznego sektora rozruchowego sterownika we/wy 

**Ikona** ![ Ikona zapisu wewnętrznego sektora rozruchowego sterownika we/wy](./media/user-guide/fx-events/image13.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie zapisu sektora rozruchowego wewnętrznego sterownika we/wy FileX.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik buforu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="internal-io-driver-un-initialize"></a>Wewnętrzny sterownik we/wy — anulowanie inicjalizacji 

#### <a name="internal-io-driver-un-initialize"></a>Wewnętrzny sterownik we/wy — anulowanie inicjalizacji 

**Ikona** ![ Ikona anulowania inicjowania wewnętrznego sterownika we/wy](./media/user-guide/fx-events/image14.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie anulowania inicjalizacji wewnętrznego sterownika we/wy FileX.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.
</blockquote></td>

### <a name="directory-attributes-read"></a>Odczyt atrybutów katalogu 

#### <a name="fx_directory_attributes_read"></a>fx_directory_attributes_read 

**Ikona** ![ Ikona odczytu atrybutów katalogu](./media/user-guide/fx-events/image15.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie odczytu atrybutów katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy katalogu.
- Pole informacji 3: Mapa bitów atrybutów:

  | Atrybut                         | Wartość        |
  |---------------------------------- | --------|
  |  Tylko do odczytu                        | 0x01  |
  |  Ukryty                           | 0x02  |
  |  System                           | (0x04)  |
  |  Wolumin                           | (0x08)  |
  |  Katalog                        | 0x10  |
  |  Archiwum                          | 0x20  |
- Pole informacji 4: nieużywane.

### <a name="directory-attributes-set"></a>Zestaw atrybutów katalogu 

#### <a name="fx_directory_attributes_set"></a>fx_directory_attributes_set 

**Ikona** ![ Ikona zestawu atrybutów](./media/user-guide/fx-events/image16.png)

**Opis** 

To zdarzenie reprezentuje katalog a zdarzenia zestawu atrybutów katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy katalogu.
- Pole informacji 3: Mapa bitów atrybutów:

  |  Atrybut                        | Wartość        |
  |---------------------------------- | --------|
  |  Tylko do odczytu                        | 0x01  |
  |  Ukryty                           | 0x02  |
  |  System                           | (0x04)  |
  |  Archiwum                          | 0x20  |
- Pole informacji 4: nieużywane.

### <a name="directory-create"></a>Tworzenie katalogu 

#### <a name="fx_directory_create"></a>fx_directory_create

**Ikona** ![ Ikona tworzenia katalogu](./media/user-guide/fx-events/image17.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie utworzenia katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy katalogu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-default-get"></a>Domyślne pobieranie katalogu 

#### <a name="fx_directory_default_get"></a>fx_directory_default_get 

**Ikona** ![ Ikona pobierania domyślnego katalogu](./media/user-guide/fx-events/image18.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie domyślnego zestawu katalogów.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do zwrócenia nazwy ścieżki.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-default-set"></a>Domyślny zestaw katalogów 

#### <a name="fx_directory_default_set"></a>fx_directory_default_set 

**Ikona** ![ Ikona domyślnego zestawu katalogów](./media/user-guide/fx-events/image19.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie domyślnego zestawu katalogów.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nowej nazwy ścieżki domyślnej.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-delete"></a>Usuwanie katalogu 

#### <a name="fx_directory_delete"></a>fx_directory_delete

**Ikona** ![ Ikona usuwania katalogu](./media/user-guide/fx-events/image20.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie usunięcia katalogu.

**Pola informacji**
- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy katalogu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-first-entry-find"></a>Znajdowanie pierwszego wpisu katalogu 

#### <a name="fx_directory_first_entry_find"></a>fx_directory_first_entry_find

**Ikona** ![ Ikona wyszukiwania pierwszego wpisu katalogu](./media/user-guide/fx-events/image21.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie Find pierwszego wpisu katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy katalogu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-first-full-entry-find"></a>Znajdź pierwszy pełny wpis w katalogu 

#### <a name="fx_directory_first_full_entry_find"></a>fx_directory_first_full_entry_find

**Ikona** ![ Ikona wyszukiwania pierwszego wpisu katalogu](./media/user-guide/fx-events/image22.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie znajdowania pierwszego pełnego wpisu katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy katalogu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-information-get"></a>Pobieranie informacji o katalogu 

#### <a name="fx_directory_information_get"></a>fx_directory_information_get

**Ikona** ![ Ikona uzyskiwania informacji o katalogu](./media/user-guide/fx-events/image23.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie pobrania informacji o katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy katalogu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-local-path-clear"></a>Ścieżka lokalna katalogu jest niezrozumiała 

#### <a name="fx_directory_local_path_clear"></a>fx_directory_local_path_clear

**Ikona** ![ Ikona czyszczenia ścieżki lokalnej katalogu](./media/user-guide/fx-events/image24.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie czyszczenia ścieżki lokalnej dla katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-local-path-get"></a>Pobieranie ścieżki lokalnej katalogu 

#### <a name="fx_directory_local_path_get"></a>fx_directory_local_path_get

**Ikona** ![ Ikona pobierania ścieżki lokalnej katalogu](./media/user-guide/fx-events/image25.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie pobrania ścieżki lokalnej katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do zwrócenia nazwy ścieżki.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-local-path-restore"></a>Przywracanie ścieżki lokalnej katalogu 

#### <a name="fx_directory_local_path_restore"></a>fx_directory_local_path_restore

**Ikona** ![ Ikona przywracania ścieżki lokalnej katalogu](./media/user-guide/fx-events/image26.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie przywracania ścieżki lokalnej katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do struktury ścieżki lokalnej.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-local-path-set"></a>Ustawiona ścieżka lokalna katalogu 

#### <a name="fx_directory_local_path_set"></a>fx_directory_local_path_set

**Ikona** ![ Ikona zestawu ścieżek lokalnych katalogu](./media/user-guide/fx-events/image27.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie lokalnego ustawienia ścieżki katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do struktury ścieżki lokalnej.
- Pole informacji 3: wskaźnik do nowej nazwy ścieżki.
- Pole informacji 4: nieużywane.

### <a name="directory-long-name-get"></a>Pobieranie długiej nazwy katalogu 

#### <a name="fx_directory_long_name_get"></a>fx_directory_long_name_get

**Ikona** ![ Ikona pobierania długich nazw katalogów](./media/user-guide/fx-events/image28.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie pobrania długich nazw katalogów.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do krótkiej nazwy pliku.
- Pole informacji 3: wskaźnik do długiej nazwy pliku.
- Pole informacji 4: nieużywane.

### <a name="directory-name-test"></a>Test nazwy katalogu 

#### <a name="fx_directory_name_test"></a>fx_directory_name_test

**Ikona** ![ Ikona testu nazwy katalogu](./media/user-guide/fx-events/image29.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie testowe nazwy katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy katalogu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-next-entry-find"></a>Znajdowanie wpisu w katalogu 

#### <a name="fx_directory_next_entry_find"></a>fx_directory_next_entry_find

**Ikona** ![ Ikona wyszukiwania następnego wpisu w katalogu](./media/user-guide/fx-events/image30.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie znajdowania następnego wpisu w katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy katalogu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-next-full-entry-find"></a>Znajdź następny pełny wpis w katalogu 

#### <a name="fx_directory_next_full_entry_find"></a>fx_directory_next_full_entry_find

**Ikona** ![ Ikona wyszukiwania następnego wpisu w katalogu](./media/user-guide/fx-events/image31.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Znajdź następny pełny wpis w katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy katalogu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="directory-rename"></a>Zmiana nazwy katalogu 

#### <a name="fx_directory_rename-event"></a>zdarzenie fx_directory_rename

**Ikona** ![ Ikona zmiany nazwy katalogu](./media/user-guide/fx-events/image32.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zmiany nazwy katalogu.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do starej nazwy katalogu.
- Pole informacji 3: wskaźnik do nowej nazwy katalogu.
- Pole informacji 4: nieużywane.

### <a name="directory-short-name-get"></a>Krótka nazwa katalogu Get 

#### <a name="fx_directory_short_name_get"></a>fx_directory_short_name_get

**Ikona** ![ Ikona pobierania krótkiej nazwy katalogu](./media/user-guide/fx-events/image33.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania krótkiej nazwy katalogu.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do długiej nazwy pliku.
- Pole informacji 3: wskaźnik do krótkiej nazwy pliku.
- Pole informacji 4: nieużywane.

### <a name="file-allocate"></a>Przydział pliku 

#### <a name="fx_file_allocate"></a>fx_file_allocate

**Ikona** ![ Ikona alokacji plików](./media/user-guide/fx-events/image34.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przydzielenia pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: żądany rozmiar.
- Pole informacji 3: bieżący rozmiar.
- Pole informacji 4: nowy rozmiar.

### <a name="file-attributes-read"></a>Odczyt atrybutów pliku 

#### <a name="fx_file_attributes_read"></a>fx_file_attributes_read

**Ikona** ![ Ikona odczytu atrybutów plików](./media/user-guide/fx-events/image35.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu atrybutów pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika. 
- Pole informacji 2: Mapa bitów atrybutów:

  |  Stanowiąc                         | Wartość        |
  |---------------------------------- | --------|
  |  Tylko do odczytu                        | 0x01  |
  |  Ukryty                           | 0x02  |
  |  System                           | (0x04)  |
  |  Wolumin                           | (0x08)  |
  |  Katalog                        | 0x10  |
  |  Archiwum                          | 0x20  |
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="file-attributes-set"></a>Zestaw atrybutów pliku 

#### <a name="fx_file_attributes_set"></a>fx_file_attributes_set

**Ikona** ![ Ikona zestawu atrybutów pliku](./media/user-guide/fx-events/image36.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie zestawu atrybutów pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy pliku. 
- Pole informacji 3: Mapa bitów atrybutów:

  | Atrybut                         | Wartość        |
  |---------------------------------- | --------|
  |  Tylko do odczytu                        | 0x01  |
  |  Ukryty                           | 0x02  |
  |  System                           | (0x04)  |
  |  Archiwum                          | 0x20  |
- Pole informacji 4: nieużywane.

### <a name="file-best-effort-allocate"></a>Przydział najlepszego nakładu pracy pliku 

#### <a name="fx_file_best_effort_allocate"></a>fx_file_best_effort_allocate

**Ikona** ![ Ikona przydziału najlepszego nakładu pracy pliku](./media/user-guide/fx-events/image37.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie dotyczące przydziału najlepszego nakładu pracy.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: żądany rozmiar.
- Pole informacji 3: przydzielono rzeczywisty rozmiar.
- Pole informacji 4: nieużywane.

### <a name="file-close"></a>Zamknij plik 

#### <a name="fx_file_close"></a>fx_file_close

**Ikona** ![ Ikona zamykania pliku](./media/user-guide/fx-events/image38.png)

**Opis** 

To zdarzenie reprezentuje zdarzenie zamknięcia pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: rozmiar pliku.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="file-create"></a>Tworzenie pliku

#### <a name="fx_file_create"></a>fx_file_create

**Ikona** ![ Ikona tworzenia pliku](./media/user-guide/fx-events/image39.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy pliku.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="file-date-time-set"></a>Ustawiono datę i godzinę pliku 

#### <a name="fx_file_date_time_set"></a>fx_file_date_time_set

**Ikona** ![ Ikona Ustawienia daty i godziny pliku](./media/user-guide/fx-events/image40.png)

**Opis**

To zdarzenie reprezentuje zdarzenie ustawienia daty/godziny pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy pliku.
- Pole informacji 3: rok.
- Pole informacji 4: miesiąc.

### <a name="file-delete"></a>Usuwanie pliku 

#### <a name="fx_file_delete"></a>fx_file_delete

**Ikona** ![ Ikona usuwania pliku](./media/user-guide/fx-events/image41.png)

**Opis**

To zdarzenie reprezentuje zdarzenie usunięcia pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy pliku.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="file-open"></a>Otwieranie pliku 

#### <a name="fx_file_open"></a>fx_file_open

**Ikona** ![ Ikona otwierania pliku](./media/user-guide/fx-events/image42.png)

**Opis**

To zdarzenie reprezentuje zdarzenie otwierania pliku.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do bloku kontroli pliku.
- Pole informacji 3: wskaźnik do nazwy pliku.
- Pole informacji 4: typ otwarty:

  |  Typ otwarcia                        | Wartość        |
  |---------------------------------- | --------|
  |  Otwórz do odczytu                    | 0x00  |
  |  Otwórz do zapisu                   | 0x01  |
  |  Szybkie otwieranie dla odczytu               | 0x02  |

### <a name="file-read"></a>Odczyt pliku 

#### <a name="fx_file_read"></a>fx_file_read

**Ikona** ![ Ikona odczytu pliku](./media/user-guide/fx-events/image43.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: wskaźnik buforu.
- Pole informacji 3: rozmiar żądania.
- Pole informacji 4: rzeczywisty rozmiar odczytywany.

### <a name="file-relative-seek"></a>Wyszukiwanie względem pliku 

#### <a name="fx_file_relative_seek"></a>fx_file_relative_seek

**Ikona** ![ Ikona wyszukiwania względnego pliku](./media/user-guide/fx-events/image44.png)

**Opis**

To zdarzenie reprezentuje względne dla pliku zdarzenie wyszukiwania.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: przesunięcie bajtu.
- Pole informacji 3: wyszukiwanie:

  | Zdarzenie                             | Wartość        |
  |---------------------------------- | --------|
  |  Od początku                   | 0x00  |
  |  Od końca                         | 0x01  | 
  |  do przodu                          | 0x02  |
  |  do tyłu                         | (0x03)  |
- Pole informacji 4: poprzednie przesunięcie.

### <a name="file-rename"></a>Zmiana nazwy pliku 

#### <a name="fx_file_rename"></a>fx_file_rename

**Ikona** ![ Ikona zmiany nazwy pliku](./media/user-guide/fx-events/image45.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zmiany nazwy pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do starej nazwy pliku.
- Pole informacji 3: wskaźnik do nowej nazwy pliku.
- Pole informacji 4: nieużywane.

### <a name="file-seek"></a>Wyszukiwanie plików 

#### <a name="fx_file_seek"></a>fx_file_seek

**Ikona** ![ Ikona wyszukiwania plików](./media/user-guide/fx-events/image46.png)

**Opis**

To zdarzenie reprezentuje zdarzenie wyszukiwania plików.

**Pola informacji** 

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: przesunięcie bajtu.
- Pole informacji 3: poprzednie przesunięcie.
- Pole informacji 4: nieużywane.

### <a name="file-truncate"></a>Obcinanie pliku 

#### <a name="fx_file_truncate"></a>fx_file_truncate

**Ikona** ![ Ikona obcinania plików](./media/user-guide/fx-events/image47.png)

**Opis**

To zdarzenie reprezentuje zdarzenie obcinania pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: żądany rozmiar.
- Pole informacji 3: Poprzedni rozmiar.
- Pole informacji 4: nowy rozmiar.

### <a name="file-truncate-release"></a>Wydanie obcinania plików 

#### <a name="fx_file_truncate_release"></a>fx_file_truncate_release 

**Ikona** ![ Ikona wycięcia plików](./media/user-guide/fx-events/image48.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zwolnienia obcinania plików.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: żądany rozmiar.
- Pole informacji 3: Poprzedni rozmiar.
- Pole informacji 4: nowy rozmiar.

### <a name="file-write"></a>Zapis pliku 

#### <a name="fx_file_write"></a>fx_file_write 

**Ikona** ![ Ikona zapisu pliku](./media/user-guide/fx-events/image49.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu pliku.

**Pola informacji**

- Pole informacji 1: wskaźnik do pliku.
- Pole informacji 2: wskaźnik buforu.
- Pole informacji 3: rozmiar żądania.
- Pole informacji 4: rzeczywisty rozmiar zapisany.

### <a name="media-abort"></a>Przerwanie nośnika 

#### <a name="fx_media_abort"></a>fx_media_abort 

**Ikona** ![ Ikona przerwania nośnika](./media/user-guide/fx-events/image50.png)

**Opis**

To zdarzenie reprezentuje zdarzenie przerwania nośnika.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="media-cache-invalidate"></a>Unieważnienie pamięci podręcznej multimediów

#### <a name="fx_media_cache_invalidate"></a>fx_media_cache_invalidate

**Ikona** ![ Ikona unieważniania pamięci podręcznej multimediów](./media/user-guide/fx-events/image51.png)

**Opis**

To zdarzenie reprezentuje zdarzenie unieważnienia pamięci podręcznej multimediów.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="media-check"></a>Sprawdzenie nośnika 

#### <a name="fx_media_check"></a>fx_media_check

**Ikona** ![ Ikona Sprawdź multimedia](./media/user-guide/fx-events/image52.png)

**Opis**

To zdarzenie reprezentuje zdarzenie sprawdzania nośnika.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik pamięci tymczasowej.
- Pole informacji 3: rozmiar pamięci tymczasowej.
- Pole informacyjne 4: Błędy mapy bitowej:

  | Typ błędu                        | Wartość        |
  |---------------------------------- | --------|
  |  Błąd łańcucha FAT                  | 0x01  |
  |  Błąd katalogu                  | 0x02  |
  |  Utracony błąd klastra               | (0x04)  |
  |  Błąd rozmiaru pliku                  | (0x08)  |

### <a name="media-close"></a>Zamknij nośnik 

#### <a name="fx_media_close"></a>fx_media_close

**Ikona** ![ Ikona zamykania nośnika](./media/user-guide/fx-events/image53.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zamknięcia nośnika.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="media-flush"></a>Opróżnianie multimediów 

#### <a name="fx_media_flush"></a>fx_media_flush

**Ikona** ![ Ikona opróżniania nośnika](./media/user-guide/fx-events/image54.png)

**Opis**

To zdarzenie reprezentuje zdarzenie opróżniania nośnika.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="media-format"></a>Format multimediów 

#### <a name="fx_media_format"></a>fx_media_format

**Ikona** ![ Ikona formatu multimediów](./media/user-guide/fx-events/image55.png)

**Opis**

To zdarzenie reprezentuje zdarzenie w formacie nośnika.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: liczba wpisów głównych.
- Pole informacji 3: sektory.
- Pole informacji 4: sektory na klaster.

### <a name="media-open"></a>Otwarte multimedia 

#### <a name="fx_media_open"></a>fx_media_open

**Ikona** ![ Ikona otwarcia nośnika](./media/user-guide/fx-events/image56.png)

**Opis**

To zdarzenie reprezentuje zdarzenie otwarcia nośnika.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do wpisu sterownika nośnika.
- Pole informacji 3: wskaźnik pamięci.
- Pole informacji 4: rozmiar pamięci.

### <a name="media-read-media-read"></a>Odczyt nośnika odczytu multimediów 

#### <a name="fx_media_read"></a>fx_media_read

**Ikona** ![ Ikona odczytu multimediów](./media/user-guide/fx-events/image57.png)

**Opis**

To zdarzenie reprezentuje zdarzenie odczytu nośnika.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: sektor logiczny.
- Pole informacji 3: wskaźnik buforu.
- Pole informacji 4: Bajty odczytane.

### <a name="media-space-available"></a>Dostępne miejsce na multimediach 

#### <a name="fx_media_space_available"></a>fx_media_space_available

**Ikona** ![ Ikona dostępnego miejsca na multimediach](./media/user-guide/fx-events/image58.png)

**Opis**

To zdarzenie reprezentuje zdarzenie dostępne w obszarze nośnika.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik dostępnych bajtów.
- Pole informacji 3: liczba wolnych klastrów.
- Pole informacji 4: nieużywane.

### <a name="media-volume-get"></a>Pobieranie woluminu multimedialnego 

#### <a name="fx_media_volume_get"></a>fx_media_volume_get

**Ikona** ![ Ikona pobierania woluminu multimedialnego](./media/user-guide/fx-events/image59.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania woluminu multimedialnego.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy woluminu.
- Pole informacji 3: Źródło woluminu.
- Pole informacji 4: nieużywane.

### <a name="media-volume-set"></a>Zestaw woluminów multimedialnych 

#### <a name="fx_media_volume_set"></a>fx_media_volume_set

**Ikona** ![ Ikona zestawu woluminów multimedialnych](./media/user-guide/fx-events/image60.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zestawu woluminu multimedialnego.

**Pola informacji** 
- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy woluminu.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="media-write"></a>Zapis nośnika 

#### <a name="fx_media_write"></a>fx_media_write

**Ikona** ![ Ikona zapisu multimediów](./media/user-guide/fx-events/image61.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zapisu nośnika.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: sektor logiczny.
- Pole informacji 3: wskaźnik buforu.
- Pole informacji 4: bajty zapisywane.

### <a name="system-date-get"></a>Data systemu Get 

#### <a name="fx_system_date_get"></a>fx_system_date_get 

**Ikona** ![ Ikona pobierania daty systemu](./media/user-guide/fx-events/image62.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania daty systemowej.

**Pola informacji**

- Pole informacji 1: rok.
- Pole informacji 2: miesiąc.
- Pole informacji 3: dzień.
- Pole informacji 4: nieużywane.

### <a name="system-date-set"></a>Systemowy zestaw dat 

#### <a name="fx_system_date_set"></a>fx_system_date_set 

**Ikona** ![ Ikona zestawu dat systemu](./media/user-guide/fx-events/image63.png)

**Opis**

To zdarzenie reprezentuje zdarzenie systemowego ustawiania daty.

**Pola informacji**

- Pole informacji 1: rok.
- Pole informacji 2: miesiąc.
- Pole informacji 3: dzień.
- Pole informacji 4: nieużywane.

### <a name="system-initialize"></a>Inicjowanie systemu 

#### <a name="fx_system_initialize"></a>fx_system_initialize 

**Ikona** ![ Ikona inicjowania systemu](./media/user-guide/fx-events/image64.png)

**Opis**

To zdarzenie reprezentuje zdarzenie inicjowania systemu.

**Pola informacji**

- Pole informacji 1: nie zostało użyte.
- Pole informacji 2: nie zostało użyte.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="system-time-get"></a>Pobieranie czasu systemowego 

#### <a name="fx_system_time_get"></a>fx_system_time_get 

**Ikona** ![ Ikona uzyskiwania czasu systemowego](./media/user-guide/fx-events/image65.png)

**Opis**

To zdarzenie reprezentuje zdarzenie Get Time system.

**Pola informacji** 

- Pole informacji 1: godzina.
- Pole informacji 2: minuta.
- Pole informacyjne 3: Second.
- Pole informacji 4: nieużywane.

### <a name="system-time-set"></a>Ustawiony czas systemowy 

#### <a name="fx_system_time_set"></a>fx_system_time_set 

**Ikona** ![ Ikona Ustawienia czasu systemowego](./media/user-guide/fx-events/image66.png)

**Opis**

To zdarzenie reprezentuje zdarzenie ustawienia czasu systemowego.

**Pola informacji**

- Pole informacji 1: godzina.
- Pole informacji 2: minuta.
- Pole informacyjne 3: Second.
- Pole informacji 4: nieużywane.

### <a name="unicode-directory-create"></a>Tworzenie katalogu Unicode 

#### <a name="fx_unicode_directory_create"></a>fx_unicode_directory_create 

**Ikona** ![ Ikona tworzenia katalogu Unicode](./media/user-guide/fx-events/image67.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia katalogu w formacie Unicode.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy Unicode.
- Pole informacji 3: rozmiar nazwy Unicode.
- Pole informacji 4: wskaźnik do krótkiej nazwy.

### <a name="unicode-directory-rename"></a>Zmiana nazwy katalogu Unicode 

#### <a name="fx_unicode_directory_rename"></a>fx_unicode_directory_rename

**Ikona** ![ Ikona zmiany nazwy katalogu Unicode](./media/user-guide/fx-events/image68.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zmiany nazwy katalogu w formacie Unicode.

**Pola informacji** 

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy Unicode.
- Pole informacji 3: rozmiar nazwy Unicode.
- Pole informacji 4: wskaźnik do krótkiej nazwy.

### <a name="unicode-file-create"></a>Tworzenie pliku Unicode 

#### <a name="fx_unicode_file_create"></a>fx_unicode_file_create

**Ikona** ![ Ikona tworzenia pliku Unicode](./media/user-guide/fx-events/image69.png)

**Opis**

To zdarzenie reprezentuje zdarzenie tworzenia pliku w formacie Unicode.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy Unicode.
- Pole informacji 3: rozmiar nazwy Unicode.
- Pole informacji 4: wskaźnik do krótkiej nazwy.

### <a name="unicode-file-rename"></a>Zmiana nazwy pliku Unicode 

#### <a name="fx_unicode_file_rename"></a>fx_unicode_file_rename

**Ikona** ![ Ikona zmiany nazwy pliku Unicode](./media/user-guide/fx-events/image70.png)

**Opis**

To zdarzenie reprezentuje zdarzenie zmiany nazwy pliku w formacie Unicode.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do nazwy Unicode.
- Pole informacji 3: rozmiar nazwy Unicode.
- Pole informacji 4: wskaźnik do krótkiej nazwy.

### <a name="unicode-length-get"></a>Pobieranie długości Unicode 

#### <a name="fx_unicode_length_get"></a>fx_unicode_length_get

**Ikona** ![ Ikona pobierania długości Unicode](./media/user-guide/fx-events/image71.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania długości Unicode.

**Pola informacji**

- Pole informacji 1: wskaźnik do nazwy Unicode.
- Pole informacji 2: długość.
- Pole informacji 3: nie zostało użyte.
- Pole informacji 4: nieużywane.

### <a name="unicode-name-get"></a>Pobieranie nazwy Unicode 

#### <a name="fx_unicode_name_get"></a>fx_unicode_name_get

**Ikona** ![ Ikona pobierania nazwy Unicode](./media/user-guide/fx-events/image72.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania nazwy Unicode.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: krótka nazwa źródła.
- Pole informacji 3: docelowy wskaźnik nazwy Unicode.
- Pole informacji 4: docelowa długość nazwy w formacie Unicode.

### <a name="unicode-short-name-get"></a>Pobieranie krótkiej nazwy w formacie Unicode 

#### <a name="fx_unicode_short_name_get"></a>fx_unicode_short_name_get

**Ikona** ![ Ikona pobierania krótkiej nazwy Unicode](./media/user-guide/fx-events/image73.png)

**Opis**

To zdarzenie reprezentuje zdarzenie pobrania krótkiej nazwy w formacie Unicode.

**Pola informacji**

- Pole informacji 1: wskaźnik do nośnika.
- Pole informacji 2: wskaźnik do źródłowej nazwy Unicode.
- Pole informacji 3: długość nazwy Unicode.
- Pole informacji 4: wskaźnik do krótkiej nazwy.