---
title: Rozdział 5 — Sterowniki we/wy dla Azure RTOS FileX
description: Ten rozdział zawiera opis sterowników we/wy dla aplikacji Azure RTOS FileX i ma na celu pomoc deweloperom w pisanych sterownikach specyficznych dla aplikacji.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 163893119837a46479b3f346c2bd47d200de2af75232f91a23bbc3f64e20ea50
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782918"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a>Rozdział 5 — Sterowniki we/wy dla Azure RTOS FileX

Ten rozdział zawiera opis sterowników we/wy dla aplikacji Azure RTOS FileX i ma na celu pomoc deweloperom w pisanych sterownikach specyficznych dla aplikacji.

## <a name="io-driver-introduction"></a>Wprowadzenie do sterownika We/Wy

Plik FileX obsługuje wiele urządzeń multimedialnych. Struktura FX_MEDIA definiuje wszystko, co jest wymagane do zarządzania urządzeniem multimedialnym. Ta struktura zawiera wszystkie informacje o nośniku, w tym sterownik we/wy specyficzny dla nośnika i skojarzone parametry przekazywania informacji i stanu między sterownikiem a plikiem FileX. W większości systemów istnieje unikatowy sterownik we/wy dla każdego wystąpienia nośnika FileX.

## <a name="io-driver-entry"></a>Wpis sterownika We/Wy

Każdy sterownik We/Wy FileX ma jedną funkcję wpisu, która jest definiowana przez ***fx_media_open*** wywołania usługi. Funkcja wprowadzania sterownika ma następujący format:

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

Plik FileX wywołuje funkcję wpisu sterownika We/Wy, aby zażądać dostępu do wszystkich nośników fizycznych, w tym inicjowania i odczytywania sektorów rozruchu. Żądania do sterownika są wykonywane sekwencyjnie; Tj. plik FileX czeka na ukończenie bieżącego żądania przed wysłaniem innego żądania.

## <a name="io-driver-requests"></a>Żądania sterowników We/Wy

Ponieważ każdy sterownik We/Wy ma jedną funkcję wprowadzania, plik FileX wykonuje określone żądania za pośrednictwem bloku sterowania multimediami. W szczególności  **fx_media_driver_request** jest FX_MEDIA **służy** do określania dokładnego żądania sterownika. Sterownik We/Wy informuje o sukcesie lub niepowodzeniu żądania za pośrednictwem **fx_media_driver_status** członkowskiego **FX_MEDIA**. Jeśli żądanie sterownika powiodło się, **FX_SUCCESS** zostanie umieszczone w tym polu przed jego zwrotem. W przeciwnym razie, jeśli zostanie wykryty błąd, FX_IO_ERROR zostanie umieszczony w tym polu.

### <a name="driver-initialization"></a>Inicjowanie sterownika

Mimo że rzeczywiste przetwarzanie inicjowania sterownika jest specyficzne dla aplikacji, zwykle składa się z inicjowania struktury danych i prawdopodobnie wstępnej inicjalizacji sprzętu. To żądanie jest pierwszym żądaniem wykonanym przez plik FileX i jest wykonywane z poziomu fx_media_open usługi.

Jeśli zostanie wykryta ochrona zapisu multimediów, fx_media_driver_write_protect należy ustawić FX_MEDIA na FX_TRUE.

Następujące elementy FX_MEDIA są używane do żądania inicjowania sterownika We/Wy:

|FX_MEDIA członkowski|Znaczenie|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_INIT|

Plik FileX udostępnia mechanizm informowania sterownika aplikacji, gdy sektory nie są już używane. Jest to szczególnie przydatne w przypadku menedżerów pamięci FLASH, które muszą zarządzać wszystkimi w użyciu sektorami logicznymi zamapowanych na flash.

Jeśli takie powiadomienie o wolnych sektorach jest wymagane, sterownik aplikacji po prostu *ustawia* pole fx_media_driver_free_sector_update w skojarzonej FX_MEDIA **na** **FX_TRUE**. Po skonfigurowaniu plik FileX wykonuje **_wywołanie FX_DRIVER_RELEASE_SECTORS_** we/wy wskazujące, kiedy co najmniej jeden kolejny sektor staje się wolny.

### <a name="boot-sector-read"></a>Odczyt sektora rozruchowego

Zamiast używać standardowego żądania odczytu, plik FileX wykonuje określone żądanie odczytu sektora rozruchowego nośnika. Następujące elementy **FX_MEDIA** są używane dla żądania odczytu sektora rozruchowego sterownika We/Wy:

|FX_MEDIA członkowski|Znaczenie|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_READ|
|fx_media_driver_buffer| Adres miejsca docelowego dla sektora rozruchowego.|

### <a name="boot-sector-write"></a>Zapis sektora rozruchowego

Zamiast używać standardowego żądania zapisu, plik FileX wykonuje określone żądanie zapisu sektora rozruchowego nośnika. Następujące elementy **FX_MEDIA** są używane dla żądania zapisu sektora rozruchowego sterownika we/wy:

|FX_MEDIA członkowski|Znaczenie|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_WRITE|
|fx_media_driver_buffer| Adres źródła dla sektora rozruchowego.|

### <a name="sector-read"></a>Odczyt sektora

Plik FileX odczytuje co najmniej jeden sektor w pamięci, wydając żądanie odczytu do sterownika We/Wy. Następujące elementy **FX_MEDIA** są używane dla żądania odczytu sterownika We/Wy:

|FX_MEDIA członkowski|Znaczenie|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_READ|
|fx_media_driver_logical_sector|Sektor logiczny do odczytania|
|fx_media_driver_sectors|Liczba sektorów do odczytania|
|fx_media_driver_buffer|Bufor docelowy dla odczytanych sektorów|
|fx_media_driver_data_sector_read|Ustaw wartość FX_TRUE jeśli żądany jest sektor danych plików. W przeciwnym razie FX_FALSE jeśli jest żądany sektor systemowy (FAT lub katalogowy).|
|fx_media_driver_sector_type|Definiuje jawny typ żądanego sektora w następujący sposób:<br />FX_FAT_SECTOR (2)<br />FX_DIRECTORY_SECTOR (3)<br />FX_DATA_SECTOR (4)|

### <a name="sector-write"></a>Zapis sektora

Plik FileX zapisuje co najmniej jeden sektor na nośniku fizycznym, wydając żądanie zapisu do sterownika We/Wy. Następujące elementy FX_MEDIA są używane dla żądania zapisu sterownika We/Wy:

|FX_MEDIA członkowski| Znaczenie|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_WRITE|
|fx_media_driver_logical_sector|Sektor logiczny do zapisu|
|fx_media_driver_sectors|Liczba sektorów do zapisu|
|fx_media_driver_buffer|Bufor źródłowy dla sektorów do zapisu|
|fx_media_driver_system_write| Ustaw wartość FX_TRUE jeśli żądany jest sektor systemowy (FAT lub katalogowy). W przeciwnym FX_FALSE, jeśli jest żądany sektor danych plików.|
|fx_media_driver_sector_type|Definiuje jawny typ żądanego sektora w następujący sposób:<br> <br>FX_FAT_SECTOR (2) <br> FX_DIRECTORY_SECTOR (3) <br>FX_DATA_SECTOR (4).|

### <a name="driver-flush"></a>Opróżnienie sterownika

Plik FileX opróżnia wszystkie sektory aktualnie w pamięci podręcznej sektorów sterownika na nośnik fizyczny, wydając żądanie opróżniania do sterownika We/Wy. Oczywiście jeśli sterownik nie jest w sektorach buforowania, to żądanie nie wymaga przetwarzania sterowników. Następujące elementy FX_MEDIA są używane do żądania opróżninia sterownika We/Wy:

|FX_MEDIA członkowski| Znaczenie|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_FLUSH|

### <a name="driver-abort"></a>Przerwanie sterownika

FileX informuje sterownik, aby przerwać wszystkie dalsze działania fizyczne we/wy z nośnika fizycznego, wystawiając żądanie przerwania do sterownika We/Wy. Sterownik nie powinien ponownie wykonywać żadnych operacji we/wy, dopóki nie zostanie ponownie zainicjowany. Następujące elementy FX_MEDIA są używane dla żądania przerwania sterownika We/Wy:

|FX_MEDIA członkowski| Znaczenie|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_ABORT|

### <a name="release-sectors"></a>Sektory wydania

Jeśli sterownik został wcześniej wybrany podczas inicjowania, FileX informuje sterownik zawsze, gdy co najmniej jeden kolejny sektor staje się wolny. Jeśli sterownik jest w rzeczywistości menedżerem FLASH, te informacje mogą służyć do poinformuj menedżera FLASH, że te sektory nie są już potrzebne. Następujące elementy **FX_MEDIA** są używane w żądaniu sektorów wydania We/Wy:

|FX_MEDIA członkowski| Znaczenie|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_RELEASE_SECTORS|
|fx_media_driver_logical_sector|Początek wolnego sektora|
|fx_media_driver_sectors|Liczba wolnych sektorów|

### <a name="driver-suspension"></a>Zawieszenie sterownika

Ze względu na to, że we/wy z nośnikiem fizycznym może trochę potrwać, często pożądane jest wstrzymanie wątku wywołującego. Oczywiście zakłada się, że ukończenie podstawowej operacji We/Wy jest przerywane. Jeśli tak, zawieszenie wątku można łatwo zaimplementować za pomocą semafora ThreadX. Po uruchomieniu operacji wejściowej lub wyjściowej sterownik we/wy zawiesza się na własnym wewnętrznym semaforze we/wy (utworzonym z początkową wartością 0 podczas inicjowania sterownika). W ramach przetwarzania przerwań zakończenia we/wy sterownika ustawiany jest ten sam semafor we/wy, który z kolei wznawia wstrzymany wątek.

### <a name="sector-translation"></a>Tłumaczenie sektorów

Ponieważ system FileX widokuje nośnik jako liniowe sektory logiczne, żądania we/wy do sterownika We/Wy są dokonywane z sektorami logicznymi. To sterownik odpowiada za tłumaczenie między sektorami logicznymi a fizyczną geometrią nośnika, która może obejmować orły, ścieżki i sektory fizyczne. W przypadku nośników dyskowych FLASH i RAM sektory logiczne zazwyczaj mapają katalog na sektory fizyczne. W każdym przypadku poniżej podano typowe formuły do wykonania mapowania sektorów logicznych na fizyczne w sterowniku We/Wy:

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

Należy pamiętać, że sektory fizyczne zaczynają się od jednego, a sektory logiczne zaczynają się od zera.

### <a name="hidden-sectors"></a>Ukryte sektory

Ukryte sektory znajdowały się przed rekordem rozruchowym na nośniku. Ponieważ tak naprawdę są one poza zakresem układu systemu plików FAT, należy uwzględnić je w każdej operacji sektora logicznego sterownika.

### <a name="media-write-protect"></a>Ochrona zapisu multimediów

Sterownik FileX może włączyć ochronę zapisu, ustawiając pole fx_media_driver_write_protect w bloku sterowania multimediami. Spowoduje to zwrócenie błędu, jeśli jakiekolwiek wywołania FileX zostaną wykonane podczas próby zapisu na nośniku.

## <a name="sample-ram-driver"></a>Przykładowy sterownik pamięci RAM

System pokazowy FileX jest dostarczany z małym sterownikem dysku RAM, który jest zdefiniowany w pliku fx_ram_driver.c. Sterownik przyjmuje miejsce w pamięci 32K i tworzy rekord rozruchowy dla 256 128-bajtowych sektorów. Ten plik zawiera dobry przykład sposobu implementacji sterowników we/wy FileX specyficznych dla aplikacji.

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
