---
title: Opis Azure RTOS FileX
description: Azure RTOS FileX to system plików zgodny z tabelą alokacji plików (FAT) o wysokiej wydajności, który jest w pełni zintegrowany z systemem Azure RTOS ThreadX i dostępny dla wszystkich obsługiwanych procesorów. Podobnie jak Azure RTOS ThreadX, plik Azure RTOS FileX został zaprojektowany tak, aby miał niewielkie rozmiary i wysoką wydajność, dzięki czemu idealnie nadaje się do współczesnych głęboko osadzonych aplikacji, które wymagają operacji zarządzania plikami. Plik FileX obsługuje większość nośników fizycznych, w tym pamięci RAM, Azure RTOS USBX, SD CARD i pamięci flash NAND/NOR za pośrednictwem Azure RTOS LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 399586eca18ef9345b94cc577bdacbf3c3a591bcd22b474b4e3d4ca4eefb4432
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782854"
---
# <a name="overview-of-azure-rtos-filex"></a>Omówienie Azure RTOS FileX

Azure RTOS fileX embedded file system Azure RTOS to zaawansowane rozwiązanie klasy przemysłowej dla formatów plików Fat firmy Microsoft, zaprojektowane specjalnie z myślą o aplikacjach głęboko osadzonych, w czasie rzeczywistym i IoT. Azure RTOS FileX obsługuje wszystkie formaty plików firmy Microsoft, w tym FAT12, FAT16, FAT32 i exFAT. FileX oferuje również opcjonalną odporność na uszkodzenia i poziom zużycia pamięci FLASH za pośrednictwem produktu dodatku [o nazwie Azure RTOS LevelX.](https://docs.microsoft.com/azure/rtos/levelx/) Wszystko to w połączeniu z niewielkim zużyciem pamięci, szybkim wykonywaniem i doskonałą łatwością użycia sprawiają, że plik Azure RTOS FileX jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT.

## <a name="api-protocols"></a>Protokoły interfejsu API

### <a name="media-services"></a>Media Services

- Obsługa plików FAT 12/16/32 i exFAT
- Minimalna 6 KB pamięci FLASH, 2,5 KB pamięci RAM
- Pełne usługi dostępu do multimediów
- Nieograniczona liczba wystąpień multimediów
- Prosty interfejs sterownika sektora logicznego odczytu/zapisu
- Obsługa wielu partycji
- Pamięć podręczna sektora logicznego
- Pamięć podręczna wpisów FAT
- Opcjonalna obsługa odporności na uszkodzenia
- Odroczona pomocnicza aktualizacja FAT
- Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
- Intuicyjne interfejsy API dostępu do multimediów, w tym:
  - fx_media_open
  - fx_media_close
  - fx_media_format
  - fx_media_space_available

### <a name="directory-services"></a>Usługi katalogowe

- Maksymalnie 256 ścieżek bajtowych
- Obsługiwane nazwy katalogów long i 8.3
- Tworzenie katalogu & usuwanie
- Przechodzenie i nawigacja w katalogu
- Zarządzanie atrybutami katalogu
- Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
- Intuicyjne interfejsy API dostępu do katalogów, w tym:
  - fx_directory_create
  - fx_directory_delete
  - fx_directory_attributes_set
  - fx_directory_attributes_read
  - fx_directory_first_entry_find
  - fx_directory_next_entry_find

### <a name="file-services"></a>Usługi plików

- Minimalna ilość pamięci FLASH: 3,3 KB
- Nieograniczona liczba otwartych plików
- Pliki tylko do odczytu można otwierać wiele razy
- Obsługiwane nazwy katalogów long i 8.3
- Obsługa ciągłych plików
- Logika szybkiego szukania
- Wstępna alokacja klastrów
- Tworzenie, usuwanie i zmienianie nazwy pliku
- Odczyt, zapis i wyświetlanie plików
- Zarządzanie atrybutami plików
- Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX
- Intuicyjne interfejsy API dostępu do plików, w tym:
  - fx_file_create
  - fx_file_delete
  - fx_file_attributes_set
  - fx_file_attributes_read
  - fx_file_read
  - fx_file_seek
  - fx_file_write

## <a name="advanced-technology"></a>Zaawansowana technologia

Azure RTOS FileX to zaawansowana technologia, w tym następująca.

- Obsługa plików FAT 12/16/32 i exFAT
- Obsługa wielu partycji
- Automatyczne skalowanie
- Neutralność endianowa
- Obsługa długich nazw plików i 8.3
- Opcjonalna obsługa odporności na uszkodzenia
- Pamięć podręczna sektora logicznego
- Pamięć podręczna wpisów FAT
- Wstępna alokacja klastrów
- Obsługa ciągłych plików
- Opcjonalne metryki wydajności
- Azure RTOS analizy systemu TraceX

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a>NOR/NAND Wear Leveling (Azure RTOS LevelX)

Azure RTOS LevelX to produkt firmy Microsoft do wyrównania zużycia w technologii NOR/NAND FLASH. Azure RTOS LevelX może być używany w połączeniu z plikiem FileX lub jako autonomiczna, bezpośrednia biblioteka sektorów flash do odczytu/zapisu dla aplikacji.
