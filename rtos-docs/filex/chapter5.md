---
title: Rozdział 5 — sterowniki we/wy dla usługi Azure RTO FileX
description: Ten rozdział zawiera opis sterowników we/wy dla usługi Azure RTO FileX i został zaprojektowany, aby pomóc deweloperom w pisaniu sterowników specyficznych dla aplikacji.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b44822b9d8f16208cf470a84013be5a5ff833325
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822441"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a>Rozdział 5 — sterowniki we/wy dla usługi Azure RTO FileX

Ten rozdział zawiera opis sterowników we/wy dla usługi Azure RTO FileX i został zaprojektowany, aby pomóc deweloperom w pisaniu sterowników specyficznych dla aplikacji.

## <a name="io-driver-introduction"></a>Wprowadzenie do sterownika we/wy

FileX obsługuje wiele urządzeń multimedialnych. Struktura FX_MEDIA definiuje wszystko wymagane do zarządzania urządzeniem multimedialnym. Ta struktura zawiera wszystkie informacje o nośnikach, w tym sterownik we/wy charakterystyczny dla nośnika i powiązane parametry umożliwiające przekazywanie informacji i stanu między sterownikiem i FileX. W większości systemów istnieje unikatowy sterownik we/wy dla każdego wystąpienia nośnika FileX.

## <a name="io-driver-entry"></a>Wpis sterownika we/wy

Każdy sterownik we/wy FileX ma funkcję pojedynczego wpisu, która jest definiowana przez wywołanie usługi ***fx_media_open*** . Funkcja wprowadzania sterowników ma następujący format:

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

FileX wywołuje funkcję wejścia sterownika we/wy, aby zażądać dostępu do nośników fizycznych, w tym wczytywania i odczytywania sektora rozruchowego. Żądania kierowane do sterownika są wykonywane sekwencyjnie; oznacza to, że FileX czeka na zakończenie bieżącego żądania przed wysłaniem innego żądania.

## <a name="io-driver-requests"></a>Żądania sterowników we/wy

Ze względu na to, że każdy sterownik we/wy ma jedną funkcję wejścia, FileX wykonuje określone żądania za pomocą bloku sterowania nośnika. W konkretnym przypadku  **fx_media_driver_request** członkiem **FX_MEDIA** jest używany do określenia dokładnego żądania sterownika. Sterownik we/wy komunikuje sukces lub niepowodzenie żądania przez **fx_media_driver_status** członkiem **FX_MEDIA**. Jeśli żądanie sterownika zakończyło się pomyślnie, **FX_SUCCESS** jest umieszczane w tym polu przed zwróceniem sterownika. W przeciwnym razie, jeśli zostanie wykryty błąd, FX_IO_ERROR jest umieszczany w tym polu.

### <a name="driver-initialization"></a>Inicjowanie sterownika

Chociaż rzeczywiste przetwarzanie inicjacji sterownika jest specyficzne dla aplikacji, zwykle składa się ona z inicjalizacji struktury danych i ewentualnej wstępnej inicjalizacji sprzętowej. To żądanie jest najpierw wykonywane przez FileX i jest wykonywane z poziomu usługi fx_media_open.

Jeśli zostanie wykryta ochrona przed zapisem na nośniku, fx_media_driver_write_protect członkiem FX_MEDIA powinna być ustawiona wartość FX_TRUE.

Następujące elementy członkowskie FX_MEDIA są używane dla żądania inicjacji sterownika we/wy:

|FX_MEDIA składową|Znaczenie|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_INIT|

FileX zapewnia mechanizm do informowania sterownika aplikacji, gdy sektory nie są już używane. Jest to szczególnie przydatne w przypadku menedżerów pamięci FLASH, którzy muszą zarządzać wszystkimi używanymi sektorami logicznymi, które są mapowane na LAMPę BŁYSKową.

Jeśli wymagane jest powiadomienie o bezpłatnych sektorach, sterownik aplikacji po prostu ustawi pole *fx_media_driver_free_sector_update* w skojarzonej strukturze **FX_MEDIA** do **FX_TRUE**. Po ustawieniu FileX **_FX_DRIVER_RELEASE_SECTORS_** wywołanie sterownika we/wy wskazujące, kiedy jeden lub więcej kolejnych sektorów staje się bezpłatny.

### <a name="boot-sector-read"></a>Odczyt sektora rozruchowego

Zamiast używać standardowego żądania odczytu, FileX wykonuje konkretne żądanie odczytu sektora rozruchowego nośnika. Następujące **FX_MEDIA** elementy członkowskie są używane dla żądania odczytu sektora rozruchu sterownika we/wy:

|FX_MEDIA składową|Znaczenie|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_READ|
|fx_media_driver_buffer| Adres docelowy sektora rozruchowego.|

### <a name="boot-sector-write"></a>Zapis sektora rozruchowego

Zamiast używać standardowego żądania zapisu, FileX wykonuje określone żądanie zapisania sektora rozruchowego nośnika. Następujące składowe **FX_MEDIA** są używane dla żądania zapisu sektora rozruchu sterownika we/wy:

|FX_MEDIA składową|Znaczenie|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_WRITE|
|fx_media_driver_buffer| Adres źródła dla sektora rozruchowego.|

### <a name="sector-read"></a>Odczyt sektora

FileX odczytuje jeden lub więcej sektorów do pamięci, wydając żądanie odczytu do sterownika we/wy. Następujące elementy członkowskie **FX_MEDIA** są używane dla żądania odczytu sterownika we/wy:

|FX_MEDIA składową|Znaczenie|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_READ|
|fx_media_driver_logical_sector|Sektor logiczny do odczytania|
|fx_media_driver_sectors|Liczba sektorów do odczytania|
|fx_media_driver_buffer|Odczytaj bufor docelowy dla sektorów|
|fx_media_driver_data_sector_read|Ustaw, aby FX_TRUE, jeśli zażądano sektora danych pliku. W przeciwnym razie FX_FALSE, jeśli zażądano sektora systemowego (FAT lub sektor katalogu).|
|fx_media_driver_sector_type|Definiuje jawny typ żądanego sektora w następujący sposób:<br />FX_FAT_SECTOR (2)<br />FX_DIRECTORY_SECTOR (3)<br />FX_DATA_SECTOR (4)|

### <a name="sector-write"></a>Zapis sektora

FileX zapisuje jeden lub więcej sektorów na nośniku fizycznym, wysyłając żądanie zapisu do sterownika we/wy. Następujące składowe FX_MEDIA są używane dla żądania zapisu sterowników we/wy:

|FX_MEDIA składową| Znaczenie|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_WRITE|
|fx_media_driver_logical_sector|Sektor logiczny do zapisu|
|fx_media_driver_sectors|Liczba sektorów do zapisu|
|fx_media_driver_buffer|Bufor źródłowy dla sektorów do zapisu|
|fx_media_driver_system_write| Ustaw na FX_TRUE w przypadku żądania sektora systemu (FAT lub sektor katalogu). W przeciwnym razie FX_FALSE, jeśli zażądano sektora danych pliku.|
|fx_media_driver_sector_type|Definiuje jawny typ żądanego sektora w następujący sposób:
FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4) |

### <a name="driver-flush"></a>Opróżnianie sterownika

FileX opróżnia wszystkie sektory znajdujące się obecnie w pamięci podręcznej sektora sterownika do nośnika fizycznego, wysyłając żądanie opróżnienia do sterownika we/wy. Oczywiście, jeśli sterownik nie jest buforowany w sektorach, to żądanie nie wymaga przetwarzania sterownika. Następujące elementy członkowskie FX_MEDIA są używane dla żądania opróżnienia sterownika we/wy:

|FX_MEDIA składową| Znaczenie|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_FLUSH|

### <a name="driver-abort"></a>Przerwanie sterownika

FileX informuje sterownik, aby przerwać wszystkie dalsze fizyczne operacje we/wy z nośnikiem fizycznym przez wystawienie żądania przerwania dla sterownika we/wy. Sterownik nie powinien wykonać żadnych operacji we/wy ponownie, dopóki nie zostanie ponownie zainicjowany. Następujące elementy członkowskie FX_MEDIA są używane dla żądania przerwania sterownika we/wy:

|FX_MEDIA składową| Znaczenie|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_ABORT|

### <a name="release-sectors"></a>Sektory wydania

Jeśli wcześniej została wybrana przez sterownik podczas inicjowania, FileX informuje sterownik za każdym razem, gdy jeden lub kilka kolejnych sektorów staną się bezpłatne. Jeśli sterownik jest w rzeczywistości programem FLASH Manager, te informacje mogą być używane do poinformowania Menedżera programu FLASH o tym, że te sektory nie są już potrzebne. Następujące **FX_MEDIA** elementy członkowskie są używane dla żądania sektorów wydania we/wy:

|FX_MEDIA składową| Znaczenie|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_RELEASE_SECTORS|
|fx_media_driver_logical_sector|Początek wolnego sektora|
|fx_media_driver_sectors|Liczba wolnych sektorów|

### <a name="driver-suspension"></a>Zawieszenie sterownika

Ponieważ we/wy z nośnika fizycznego może upłynąć trochę czasu, wstrzymanie wątku wywołującego jest często pożądane. Oczywiście założono, że wykonywanie bazowej operacji we/wy jest zależne od przerwań. W takim przypadku zawieszenie wątku jest łatwo implementowane przy użyciu semafora ThreadX. Po uruchomieniu operacji wejściowej lub wyjściowej sterownik we/wy zawiesza się we własnym wewnętrznym czasie we/wy (utworzony z początkową liczbą zero podczas inicjowania sterownika). W ramach przetwarzania przerwań we/wy sterownika jest ustawiony ten sam semafor we/wy, który z kolei wznawia zawieszony wątek.

### <a name="sector-translation"></a>Tłumaczenie sektora

Ponieważ FileX przegląda nośnik jako liniowe sektory logiczne, żądania we/wy wykonywane do sterownika we/wy są tworzone z sektorami logicznymi. Jest on odpowiedzialny za przetłumaczenie sektorów logicznych i fizycznej geometrii nośnika, który może obejmować głowice, ścieżki i sektory fizyczne. W przypadku nośników dysków FLASH i RAM sektory logiczne zwykle mapują katalog na sektory fizyczne. W każdym przypadku poniżej przedstawiono typowe formuły umożliwiające przeprowadzenie mapowania między logicznymi a fizycznymi w sterowniku we/wy:

```c
media_ptr -> fx_media_driver_physical_sector =
    (media_ptr -> fx_media_driver_logical_sector % media_ptr -> fx_media_sectors_per_track) + 1;

media_ptr -> fx_media_driver_physical_head =
    (media_ptr -> fx_media_driver_logical_sector/ media_ptr ->
    fx_media_sectors_per_track) % media_ptr -> fx_media_heads;

media_ptr -> fx_media_driver_physical_track =(media_ptr ->
    fx_media_driver_logical_sector/ (media_ptr -> fx_media_sectors_per_track *
    media_ptr -> fx_media_heads)));
```

Należy zauważyć, że sektory fizyczne zaczynają się na jednym, podczas gdy sektory logiczne zaczynają się od zera.

### <a name="hidden-sectors"></a>Ukryte sektory

Ukryte sektory zostały zamieszkałe przed rekordem rozruchowym na nośniku. Ponieważ są one naprawdę poza zakresem układu systemu plików FAT, muszą być uwzględnione w każdej operacji sektora logicznego.

### <a name="media-write-protect"></a>Ochrona przed zapisem multimediów

Sterownik FileX może włączyć ochronę przed zapisem przez ustawienie pola fx_media_driver_write_protect w bloku kontroli nośnika. Spowoduje to zwrócenie błędu, jeśli jakiekolwiek wywołania FileX zostaną wykonane podczas próby zapisu na nośniku.

## <a name="sample-ram-driver"></a>Przykładowy sterownik pamięci RAM

System demonstracyjny FileX jest dostarczany z małym sterownikiem dysku RAM, który jest zdefiniowany w pliku fx_ram_driver. c. Sterownik zakłada miejsce w pamięci 32 KB i tworzy rekord rozruchowy dla sektorów 256 128-bajtowych. Ten plik zawiera dobry przykład implementacji sterowników we/wy FileX specyficznych dla aplikacji.

```c
/*FUNCTION: _fx_ram_driver
RELEASE: PORTABLE C 5.7
AUTHOR: William E. Lamie, Microsoft, Inc.
DESCRIPTION: This function is the entry point to the generic
    RAM disk driver that is delivered with all versions of FileX.
    The format of the RAM disk is easily modified by calling fx_media_format prior to opening the media.

    This driver also serves as a template for developing FileX drivers
    for actual devices. Simply replace the read/write sector logic
    with calls to read/write from the appropriate physical device.

FileX RAM/FLASH structures look like the following:
Physical Sector             Contents
    0                         Boot record
    1                         FAT Area Start
    +FAT Sectors             Root Directory Start
    +Directory Sectors         Data Sector Start

INPUT: media_ptr Media control block pointer
OUTPUT: None
CALLS:     _fx_utility_memory_copy Copy sector memory
        _fx_utility_16_unsigned_read Read 16-bit unsigned
CALLED BY: FileX System Functions
RELEASE HISTORY:

    DATE         NAME         DESCRIPTION
    12-12-2005     William E.     Lamie Initial Version 5.0
    07-18-2007     William E.     Lamie Modified comment(s),
                                resulting in version 5.1
    03-01-2009     William E.     Lamie Modified comment(s),
                                resulting in version 5.2
    11-01-2015     William E.     Lamie Modified comment(s),
                                resulting in version 5.3
    04-15-2016     William E.     Lamie Modified comment(s),
                                resulting in version 5.4
    04-03-2017     William E.     Lamie Modified comment(s),
                                fixed compiler warnings,
                                resulting in version 5.5
    12-01-2018     William E.     Lamie Modified comment(s),
                                checked buffer overflow,
                                resulting in version 5.6
    08-15-2019     William E.     Lamie Modified comment(s),
                                resulting in version 5.7
*/

VOID _fx_ram_driver(FX_MEDIA *media_ptr) { UCHAR *source_buffer;
                                           UCHAR *destination_buffer;
                                           UINT bytes_per_sector;

    /* There are several useful/important pieces of information contained
        in the media structure, some of which are supplied by FileX and
        others are for the driver to setup. The following
        is a summary of the necessary FX_MEDIA structure members:
    FX_MEDIA Member                     Meaning

    fx_media_driver_request             FileX request type.
        Valid requests from FileX are as follows:
        FX_DRIVER_READ
        FX_DRIVER_WRITE
        FX_DRIVER_FLUSH
        FX_DRIVER_ABORT
        FX_DRIVER_INIT
        FX_DRIVER_BOOT_READ
        FX_DRIVER_RELEASE_SECTORS
        FX_DRIVER_BOOT_WRITE FX_DRIVER_UNINIT

    fx_media_driver_status              This value is RETURNED by the driver.
        If the operation is successful, this field should be set to FX_SUCCESS
        for before returning. Otherwise, if an error occurred, this field should be set to FX_IO_ERROR.

    fx_media_driver_buffer              Pointer to buffer to read or write sector data. This is supplied by FileX.

    fx_media_driver_logical_sector      Logical sector FileX is requesting.
    fx_media_driver_sectors             Number of sectors FileX is requesting.

    The following is a summary of the optional FX_MEDIA structure members: FX_MEDIA Member Meaning

    fx_media_driver_info                Pointer to any additional information or memory.
        This is optional for the driver use and is setup from the fx_media_open call.
        The RAM disk uses this pointer for the RAM disk memory itself.

    fx_media_driver_write_protect       The DRIVER sets this to FX_TRUE when media is write protected.
        This is typically done in initialization, but can be done anytime.

    fx_media_driver_free_sector_update  The DRIVER sets this to FX_TRUE when it needs
        to know when clusters are released. This is important for FLASH wear-leveling drivers.

    fx_media_driver_system_write        FileX sets this flag to FX_TRUE if the sector
        being written is a system sector, e.g., a boot, FAT, or directory sector.
        The driver may choose to use this to initiate error recovery logic for greater fault
        tolerance. fx_media_driver_data_sector_read FileX sets this flag to FX_TRUE
        if the sector(s) being read are file data sectors, i.e., NOT system sectors.

    fx_media_driver_sector_type         FileX sets this variable to the specific type of
        sector being read or written. The following sector types are identified:
            FX_UNKNOWN_SECTOR
            FX_BOOT_SECTOR
            FX_FAT_SECTOR
            FX_DIRECTORY_SECTOR
            FX_DATA_SECTOR */

    /* Process the driver request specified in the media control block. */

    switch (media_ptr -> fx_media_driver_request){

        case FX_DRIVER_READ: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
            is pointed to by the fx_media_driver_info pointer, which is supplied
            by the application in the call to fx_media_open. */

            source_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the RAM sector into the destination. */

             _fx_utility_memory_copy(source_buffer,
                media_ptr -> fx_media_driver_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_WRITE: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
                is pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */

            destination_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the source to the RAM sector. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_FLUSH: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_ABORT: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_INIT: {

            /* FLASH drivers are responsible for setting several fields
                in the media structure, as follows:
                media_ptr -> fx_media_driver_free_sector_update media_ptr ->
                fx_media_driver_write_protect
                The fx_media_driver_free_sector_update flag is used to instruct
                FileX to inform the driver whenever sectors are not being used.
                This is especially useful for FLASH managers so they don't have
                maintain mapping for sectors no longer in use.
                The fx_media_driver_write_protect flag can be set anytime by
                the driver to indicate the media is not writable. Write attempts
                made when this flag is set are returned as errors. */
            /* Perform basic initialization here... since the boot record is going
                to be read subsequently and again for volume name requests. */
            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

         case FX_DRIVER_UNINIT: {

            /* There is nothing to do in this case for the RAM driver.
                For actual devices some shutdown processing may be necessary. */

            /* Successful driver request. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_READ: {
            /* Read the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is pointed
                to by the fx_media_driver_info pointer, which is supplied by the
                application in the call to fx_media_open. */

            source_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* For RAM driver, determine if the boot record is valid. */

            if ((source_buffer[0] != (UCHAR)0xEB) ||

            ((source_buffer[1] != (UCHAR)0x34) &&

            (source_buffer[1] != (UCHAR)0x76)) || /* exFAT jump code. */

            (source_buffer[2] != (UCHAR)0x90)) {

            /* Invalid boot record, return an error! */
            media_ptr -> fx_media_driver_status = FX_MEDIA_INVALID; return; }

            /* For RAM disk only, pickup the bytes per sector. */

            bytes_per_sector =
                _fx_utility_16_unsigned_read(&source_buffer[FX_BYTES_SECTOR]); #ifdef FX_ENABLE_EXFAT

            /* if byte per sector is zero, then treat it as exFAT volume. */

            if (bytes_per_sector == 0 && (source_buffer[1] == (UCHAR)0x76)) {

            /* Pickup the byte per sector shift, and calculate byte per sector. */ 
            bytes_per_sector = (UINT)(1 << source_buffer[FX_EF_BYTE_PER_SECTOR_SHIFT]);

            }

            #endif /* FX_ENABLE_EXFAT */

            /* Ensure this is less than the media memory size. */
            if (bytes_per_sector \media_ptr -> fx_media_memory_size) {

            media_ptr -> fx_media_driver_status = FX_BUFFER_ERROR; break; }

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(source_buffer, media_ptr -> fx_media_driver_buffer, bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_WRITE: {

            /* Write the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is
                pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */ 
            destination_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        default: {
            /* Invalid driver request. */
            media_ptr -> fx_media_driver_status = FX_IO_ERROR; break;}
    }
}
```
