---
title: Rozdział 5 — Zagadnienia dotyczące klas urządzeń USBX
description: Dowiedz się więcej o zagadnieniach dotyczących klas urządzeń USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: b8fcfa251df9140d23b50a99f13f2755d2bdfae0ca6b9529633f25e263c7edcc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798744"
---
# <a name="chapter-5---usbx-device-class-considerations"></a>Rozdział 5 — Zagadnienia dotyczące klas urządzeń USBX

## <a name="device-class-registration"></a>Rejestracja klasy urządzeń

Każda klasa urządzenia jest zgodna z tą samą zasadą rejestracji. Struktura zawierająca określone parametry klasy jest przekazywana do funkcji inicjowania klasy.

```c
/* Set the parameters for callback when insertion/extraction of a HID device. */

hid_parameter.ux_slave_class_hid_instance_activate = tx_demo_hid_instance_activate;

hid_parameter.ux_slave_class_hid_instance_deactivate = tx_demo_hid_instance_deactivate;

/* Initialize the hid class parameters for the device. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_device_report;

hid_parameter.ux_device_class_hid_parameter_report_length = HID_DEVICE_REPORT_LENGTH;

hid_parameter.ux_device_class_hid_parameter_report_id = UX_TRUE;
hid_parameter.ux_device_class_hid_parameter_callback = demo_thread_hid_callback;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry,1,0, (VOID *)&hid_parameter);
```

Każda klasa może zarejestrować, opcjonalnie, funkcję wywołania zwrotnego, gdy zostanie aktywowane wystąpienie klasy. Wywołanie zwrotne jest następnie wywoływane przez stos urządzenia w celu poinformowania aplikacji o utworzeniu wystąpienia.

Aplikacja miałaby w swojej treści 2 funkcje aktywacji i dezaktywacji, jak pokazano w poniższym przykładzie.

```c
VOID tx_demo_hid_instance_activate(VOID *hid_instance)
{
    /* Save the HID instance. */
    hid_slave = (UX_SLAVE_CLASS_HID *) hid_instance;
}

VOID tx_demo_hid_instance_deactivate(VOID *hid_instance)
{
    /* Reset the HID instance. */
    hid_slave = UX_NULL;
}
```

Nie zaleca się nic robić w ramach tych funkcji, ale aby zapamiętać wystąpienie klasy i zsynchronizować z pozostałą część aplikacji.

## <a name="general-considerations-for-bulk-transfer"></a>Ogólne zagadnienia dotyczące transferu zbiorczego

Zgodnie ze specyfikacją USB 2.0 punkt końcowy musi zawsze przesyłać ładunki danych z polem danych mniejszym lub równym wartości zgłoszonej przez punkt końcowy wMaxPacketSize. Rozmiar pakietu danych jest ograniczony do bMaxPacketSize. Transfer można zakończyć w następujących przypadkach
1. Punkt końcowy przetransferował dokładnie oczekiwaną ilość danych
2. Gdy urządzenie lub punkt końcowy hosta odechwyci pakiet o rozmiarze mniejszym niż maksymalny rozmiar pakietu (wMaxPacketSize). Ten krótki pakiet wskazuje, że nie ma już pakietów danych i transfer jest ukończony lub gdy wszystkie pakiety danych do przekazania są równe wMaxPacketSize, nie można określić końca transferu. Aby można było zakończyć transfer, należy wysłać pakiety o zerowej długości(ZLP), a pakiety o zerowej długości oznaczają koniec zbiorczego transferu danych. Powyższe zagadnienia dotyczą nieprzetworzonych interfejsów API zbiorczego transferu danych, np. ux_device_class_cdc_acm_read().

## <a name="usb-device-storage-class"></a>Klasa Storage USB

Klasa magazynu urządzeń USB umożliwia, aby urządzenie magazynujące osadzone w systemie było widoczne dla hosta USB.

Klasa magazynu urządzeń USB sama w sobie nie zapewnia rozwiązania magazynu. Jedynie akceptuje i interpretuje żądania SCSI pochodzące z hosta. Gdy jedno z tych żądań jest poleceniem odczytu lub zapisu, wywoła ono wstępnie zdefiniowane wywołanie do obsługi rzeczywistego urządzenia magazynującego, takiego jak sterownik urządzenia usługi ATA lub sterownik urządzenia Flash.

Podczas inicjowania klasy magazynu urządzenia do klasy , która zawiera wszystkie niezbędne informacje, jest nadana struktura wskaźnika. Poniżej przedstawiono przykład.

```c
/* Initialize the storage class parameters to customize vendor strings. */

storage_parameter.ux_slave_class_storage_parameter_vendor_id
    = demo_ux_system_slave_class_storage_vendor_id;

storage_parameter.ux_slave_class_storage_parameter_product_id
    = demo_ux_system_slave_class_storage_product_id;

storage_parameter.ux_slave_class_storage_parameter_product_rev
    = demo_ux_system_slave_class_storage_product_rev;

storage_parameter.ux_slave_class_storage_parameter_product_serial
    = demo_ux_system_slave_class_storage_product_serial;

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read_only_flag
    = UX_FALSE;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read
    = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write
    = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status
    = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,
    ux_device_class_storage_entry, ux_device_class_storage_thread, 0, (VOID *)&storage_parameter);
```

W tym przykładzie ciągi magazynu sterowników są dostosowywane przez przypisanie wskaźników ciągu do odpowiedniego parametru. Jeśli jakikolwiek wskaźnik ciągu jest pozostawiony do UX_NULL, używany jest Azure RTOS ciągu ciągu.

W tym przykładzie jest podany ostatni adres bloku dysku lub lbA, a także rozmiar sektora logicznego. LbA to liczba sektorów dostępnych na nośniku –1. Długość bloku jest ustawiona na 512 na zwykłym nośniku magazynu. Dla dysków optycznech można ustawić wartość 2048.

Aplikacja musi przekazać trzy wskaźniki funkcji wywołania zwrotnego, aby umożliwić klasie magazynu odczytywanie, zapis i uzyskiwanie stanu nośnika.

Prototypy funkcji odczytu i zapisu przedstawiono w poniższym przykładzie.

```c
UINT media_read( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);

UINT media_write( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);
```

Gdzie:

- *storage* to wystąpienie klasy magazynu.
- *LUN* to jednostka LUN, do których jest kierowane polecenie.
- *data_pointer* to adres buforu, który ma być używany do odczytu lub zapisu.
- *number_blocks* to liczba sektorów do odczytu/zapisu.
- *lba* to adres sektora do odczytania.
- *media_status* powinny być wypełnione dokładnie tak samo jak wartość zwracana wywołania zwrotnego stanu nośnika.

Zwracana wartość może mieć wartość UX_SUCCESS lub UX_ERROR wskazującą operację pomyślną lub niepomyślną. Te operacje nie muszą zwracać żadnych innych kodów błędów. Jeśli w dowolnej operacji wystąpi błąd, klasa magazynu wywoła funkcję wywołania wstecz stanu.

Ta funkcja ma następujący prototyp.

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

Parametr wywołujący media_id nie jest obecnie używany i zawsze powinien mieć wartość 0. W przyszłości może służyć do odróżnienia wielu urządzeń magazynujących lub urządzeń magazynujących z wieloma LUN SCSI. Ta wersja klasy magazynu nie obsługuje wielu wystąpień klasy magazynu ani urządzeń magazynujących z wieloma numerami LUN SCSI.

Zwracana wartość to kod błędu SCSI, który może mieć następujący format.

- **Bity 0–7** Sense_key
- **Bity 8–15** Dodatkowy kod sense
- **Bity 16–23** Dodatkowa kwalifikator kodu sense

W poniższej tabeli przedstawiono możliwe kombinacje Sense/ASC/ASCQ.

| Sense Key | ASC | AsCQ | Opis                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| 00        | 00  | 00   | BRAK SENSU                                          |
| 01        | 17  | 01   | ODZYSKANO DANE PRZY UŻYCIU PONOWNYCH PRÓB                       |
| 01        | 18  | 00   | ODZYSKANE DANE ZA POMOCĄ ECC                           |
| 02        | 04  | 01   | DYSK LOGICZNY NIE JEST GOTOWY — GOTOWOŚĆ          |
| 02        | 04  | 02   | DYSK LOGICZNY NIE JEST GOTOWY — WYMAGANA INICJALIZACJA |
| 02        | 04  | 04   | JEDNOSTKA LOGICZNA NIE JEST GOTOWA — FORMATOWANIE W TOKU       |
| 02        | 04  | Ff   | DYSK LOGICZNY NIE JEST GOTOWY — URZĄDZENIE JEST ZAJĘTE          |
| 02        | 06  | 00   | NIE ZNALEZIONO POZYCJI ODWOŁANIA                       |
| 02        | 08  | 00   | BŁĄD KOMUNIKACJI JEDNOSTKI LOGICZNEJ                |
| 02        | 08  | 01   | PRZE WYCHODZĄCY CZAS KOMUNIKACJI JEDNOSTKI LOGICZNEJ               |
| 02        | 08  | 80   | PRZEKROCZENIE KOMUNIKACJI JEDNOSTEK LOGICZNYCH                |
| 02        | 3A  | 00   | ŚREDNI NIE JEST OBECNY                                |
| 02        | 54  | 00   | AWARIA INTERFEJSU SYSTEMOWEGO Z PORTU USB NA HOSTA              |
| 02        | 80  | 00   | NIEWYSTARCZAJĄCE ZASOBY                            |
| 02        | Ff  | Ff   | NIEZNANY BŁĄD                                     |
| 03        | 02  | 00   | NO SEEK COMPLETE                                  |
| 03        | 03  | 00   | BŁĄD ZAPISU                                       |
| 03        | 10  | 00   | BŁĄD CRC IDENTYFIKATORA                                      |
| 03        | 11  | 00   | BŁĄD ODCZYTU NIEODZYSŁANYCH                            |
| 03        | 12  | 00   | NIE ZNALEZIONO ZNACZNIKA ADRESU DLA POLA IDENTYFIKATORA               |
| 03        | 13  | 00   | NIE ZNALEZIONO ZNACZNIKA ADRESU DLA POLA DANYCH             |
| 03        | 14  | 00   | NIE ZNALEZIONO ZAREJESTROWANEJ JEDNOSTKI                         |
| 03        | 30  | 01   | NIE MOŻNA ODCZYTAĆ ŚREDNIEGO — NIEZNANY FORMAT               |
| 03        | 31  | 01   | POLECENIE FORMAT NIE POWIODŁO SIĘ                             |
| 04        | 40  | Nn   | BŁĄD DIAGNOSTYCZNY W SIECI NN SKŁADNIKA (80H-FFH)      |
| 05        | 1A  | 00   | BŁĄD DŁUGOŚCI LISTY PARAMETRÓW                       |
| 05        | 20  | 00   | NIEPRAWIDŁOWY KOD OPERACJI POLECENIA                    |
| 05        | 21  | 00   | ADRES BLOKU LOGICZNEGO POZA ZAKRESEM                |
| 05        | 24  | 00   | NIEPRAWIDŁOWE POLE W PAKIECIE POLECEŃ                   |
| 05        | 25  | 00   | JEDNOSTKA LOGICZNA NIE JEST OBSŁUGIWANA                        |
| 05        | 26  | 00   | NIEPRAWIDŁOWE POLE NA LIŚCIE PARAMETRÓW                   |
| 05        | 26  | 01   | PARAMETR NIE JEST OBSŁUGIWANY                           |
| 05        | 26  | 02   | NIEPRAWIDŁOWA WARTOŚĆ PARAMETRU                           |
| 05        | 39  | 00   | ZAPISYWANIE PARAMETRÓW NIE JEST OBSŁUGA                     |
| 06        | 28  | 00   | PRZEJŚCIE NIE GOTOWE — ZMIENIONO NOŚNIK     |
| 06        | 29  | 00   | RESETOWANIE PRZY WŁ. LUB RESETOWANIE URZĄDZENIA MAGISTRALI WYSTĄPIŁO       |
| 06        | 2f  | 00   | POLECENIA WYCZYSZONE PRZEZ INNEGO INICJATORA             |
| 07        | 27  | 00   | ZAPIS NOŚNIKA CHRONIONEGO                             |
| 0B        | 4E  | 00   | PODJĘTO NAKŁADAJĄCE SIĘ POLECENIE                      |

Istnieją dwa dodatkowe, opcjonalne wywołania zwrotne, które może zaimplementować aplikacja. Jeden z nich odpowiada na polecenie **GET_STATUS_NOTIFICATION,** a drugi odpowiada na polecenie **SYNCHRONIZE_CACHE** polecenia.

Jeśli aplikacja chce obsługiwać polecenie GET_STATUS_NOTIFICATION z hosta, powinna zaimplementować wywołanie zwrotne z następującym prototypem.

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

Gdzie:

- *storage* to wystąpienie klasy magazynu.
- *media_id* nie jest obecnie używany. notification_class określa klasę powiadomienia.
- *media_notification* powinna zostać ustawiona przez aplikację na bufor zawierający odpowiedź na powiadomienie.
- *media_notification_length* powinna zostać ustawiona przez aplikację tak, aby zawierała długość buforu odpowiedzi.

Wartość zwracana wskazuje, czy polecenie zakończyło się  pomyślnie — powinno być UX_SUCCESS lub **UX_ERROR**.

Jeśli aplikacja nie implementuje tego wywołania zwrotnego, po otrzymaniu polecenia **GET_STATUS_NOTIFICATION** USBX powiadomi hosta, że polecenie nie jest zaimplementowane.

Polecenie **SYNCHRONIZE_CACHE** powinno być obsługiwane, jeśli aplikacja korzysta z pamięci podręcznej do zapisu z hosta. Host może wysłać to polecenie, jeśli wie, że urządzenie magazynujące zostanie odłączone, na przykład w programie Windows kliknięcie prawym przyciskiem myszy ikony dysku flash na pasku narzędzi i wybranie opcji "Wysuń nazwę urządzenia \[ \] magazynującego", program **Windows** wyda polecenie SYNCHRONIZE_CACHE temu urządzeniu.

Jeśli aplikacja chce obsługiwać polecenie GET_STATUS_NOTIFICATION **z** hosta, powinna zaimplementować wywołanie zwrotne z następującym prototypem.

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

Gdzie:

- *storage* to wystąpienie klasy magazynu.
- *Parametr lun* określa, do której jednostki LUN jest kierowane polecenie.
- *number_blocks* określa liczbę bloków do zsynchronizowania.
- *lba* to adres sektora pierwszego bloku do zsynchronizowania.
- *media_status* powinny być wypełnione dokładnie tak samo jak wartość zwracana wywołania zwrotnego stanu nośnika.

Wartość zwracana wskazuje, czy polecenie zakończyło się  pomyślnie — powinno być UX_SUCCESS lub **UX_ERROR**.

### <a name="multiple-scsi-lun"></a>Wiele jednostek LUN SCSI

Klasa magazynu urządzeń USBX obsługuje wiele urządzeń LUN. W związku z tym istnieje możliwość utworzenia urządzenia magazynującego, które działa jako dysk CD-ROM i dysk flash w tym samym czasie. W takim przypadku inicjowanie będzie nieco inne. Oto przykład dysku flash i dysku CD-ROM:

```c
/* Store the number of LUN in this device storage instance. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 2;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x7bbff;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the storage class LUN parameters for reading/writing to the CD-ROM. */

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_last_lba = 0x04caaf;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_block_length = 2048;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_type = 5;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_read = tx_demo_thread_cdrom_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_write = tx_demo_thread_cdrom_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_status = tx_demo_thread_cdrom_media_status;

/* Initialize the device storage class for a Flash disk and CD-ROM. The class is connected with interface 0 */ status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *) &storage_parameter);
```

## <a name="usb-device-cdc-acm-class"></a>Klasa CDC-ACM urządzenia USB

Klasa CDC-ACM urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzenie szeregowe. Ta klasa jest oparta na standardzie USB i jest podzbiorem standardu CDC.

Platformę urządzeń zgodną ze standardem CDC-ACM należy zadeklarować w stosie urządzenia. Przykład można znaleźć tutaj poniżej.

```c
unsigned char device_framework_full_speed[] = {

    /*
    Device descriptor 18 bytes
    0x02 bDeviceClass: CDC class code
    0x00 bDeviceSubclass: CDC class sub code 0x00 bDeviceProtocol: CDC Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    0x12, 0x01, 0x10, 0x01,
    0xEF, 0x02, 0x01, 0x08,
    0x84, 0x84, 0x00, 0x00,
    0x00, 0x01, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration 1 descriptor 9 bytes */
    0x09, 0x02, 0x4b, 0x00, 0x02, 0x01, 0x00,0x40, 0x00,

    /* Interface association descriptor. 8 bytes. */
    0x08, 0x0b, 0x00,
    0x02, 0x02, 0x02, 0x00, 0x00,

    /* Communication Class Interface Descriptor Requirement. 9 bytes. */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x02, 0x01, 0x00,

    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00,0x10, 0x01,

    /* ACM Functional Descriptor 4 bytes */
    0x04, 0x24, 0x02,0x0f,

    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,

    /* Master interface */
    0x01, /* Slave interface */

    /* Call Management Functional Descriptor 5 bytes */
    0x05, 0x24, 0x01,0x03, 0x01, /* Data interface */

    /* Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x83, 0x03,0x08, 0x00, 0xFF,

    /* Data Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x02,0x0A, 0x00, 0x00, 0x00,

    /* First alternate setting Endpoint 1 descriptor 7 bytes*/
    0x07, 0x05, 0x02,0x02,0x40, 0x00,0x00,

    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81,0x02,0x40, 0x00, 0x00,

};
```

Klasa CDC-ACM używa złożonej struktury urządzeń do grupowania interfejsów (kontrolek i danych). W związku z tym należy zachować ostrożność podczas definiowania deskryptora urządzenia. UsbX opiera się na deskryptorze IAD, aby wiedzieć wewnętrznie, jak powiązać interfejsy. Deskryptor IAD powinien być zadeklarowany przed interfejsami i zawierać pierwszy interfejs klasy CDC-ACM oraz ile interfejsów jest dołączonych.

Klasa CDC-ACM używa również deskryptora funkcjonalnego unii, który wykonuje tę samą funkcję co nowsze deskryptor IAD. Chociaż deskryptor funkcjonalny unii musi być zadeklarowany ze względów historycznych i zgodności ze stroną hosta, nie jest używany przez USBX.

Inicjowanie klasy CDC-ACM oczekuje następujących parametrów.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

2 zdefiniowane parametry to wskaźniki wywołania zwrotnego do aplikacji użytkownika, które będą wywoływane, gdy stos aktywuje lub dezaktywowa tę klasę.

Trzeci zdefiniowany parametr to wskaźnik wywołania zwrotnego do aplikacji użytkownika, który zostanie wywołany w przypadku zmiany parametru kodowania liniowego lub stanów wiersza. Jeśli na przykład istnieje żądanie od hosta zmiany stanu DTR na **TRUE,** wywoływane jest wywołanie zwrotne, aplikacja użytkownika może sprawdzić stany wiersza za pośrednictwem funkcji IOCTL, aby host kow był gotowy do komunikacji.

CdC-ACM jest oparty na standardzie USB-IF i jest automatycznie rozpoznawany przez systemy operacyjne MACO i Linux. Na Windows tej klasy wymaga pliku inf dla Windows wersji wcześniejszej niż 10. Windows 10 nie wymaga żadnych plików inf. Dostarczamy szablon dla klasy CDC-ACM i można go znaleźć w ***usbx_windows_host_files*** katalogu. W przypadku najnowszej wersji Windows należy użyć pliku CDC_ACM_Template_Win7_64bit.inf (z wyjątkiem Systemu Win10). Ten plik musi zostać zmodyfikowany w celu odzwierciedlenia identyfikatorów PID/VID używanych przez urządzenie. Identyfikator PID/VID będzie specyficzny dla klienta końcowego, gdy firma i produkt zostaną zarejestrowane za pomocą portu USB-IF. W pliku inf pola do zmodyfikowania znajdują się tutaj.

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

W ramach struktury urządzenia CDC-ACM identyfikator PID/VID jest przechowywany w deskryptorze urządzenia (zobacz deskryptor urządzenia zadeklarowany powyżej).

Gdy system hosta USB odnajduje urządzenie USB CDC-ACM, zainstaluje klasę szeregową i urządzenie może być używane z dowolnym programem terminalu szeregowego. Aby uzyskać informacje, zobacz system operacyjny hosta.

Poniżej zdefiniowano funkcje interfejsu API klasy CDC-ACM.

### <a name="ux_device_class_cdc_acm_ioctl"></a>ux_device_class_cdc_acm_ioctl

Wykonywanie operacji we/wy na interfejsie CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi wykonywać różne wywołania Ioctl do interfejsu acm cdc

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **ioctl_function:** funkcja Ioctl do wykonania.
- **parametr**: wskaźnik do parametru specyficznego dla wywołania ioctl.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a>Funkcje Ioctl:

| Funkcja                                        | Wartość |
| ----------------------------------------------- | - |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING    | 1 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING    | 2 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE     | 3 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE         | 4 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE     | 5 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START | 6 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP  | 7 |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING

Wykonywanie kodowania liniowego zestawu IOCTL w interfejsie CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi ustawić parametry kodowania liniowego.

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- **parametr**: Wskaźnik do struktury parametrów wiersza:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>Wartość zwracana

**UX_SUCCESS** (0x00) Ta operacja powiodła się.

### <a name="example"></a>Przykład

```c
/* Change the line coding values. */

line_coding.ux_slave_class_cdc_acm_line_coding_dter = 9600;
line_coding.ux_slave_class_cdc_acm_line_coding_stop_bit =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_STOP_BIT_15;

line_coding.ux_slave_class_cdc_acm_line_coding_parity =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_PARITY_EVEN;

line_coding.ux_slave_class_cdc_acm_line_coding_data_bits = 5;

status = _ux_slave_class_cdc_acm_ioctl(cdc_acm,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING, &line_coding);

if (status != UX_SUCCESS)
    break;
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING

Wykonywanie kodowania IOCTL Get Line w interfejsie CDC-ACM

### <a name="prototype"></a>Prototype

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi pobrać parametry kodowania liniowego.

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING
- **parametr**: Wskaźnik do struktury parametrów wiersza:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.

### <a name="example"></a>Przykład

```c
/* This is to retrieve BAUD rate. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, &line_coding);

/* Any error ? */
if (status == UX_SUCCESS)
{
    /* Decode BAUD rate. */
    switch (line_coding.ux_slave_class_cdc_acm_parameter_baudrate)
    {
        case 1200 :
            status = tx_demo_thread_slave_cdc_acm_response("1200", 4);
            break;
        case 2400 :
            status = tx_demo_thread_slave_cdc_acm_response("2400", 4);
            break;
        case 4800 :
            status = tx_demo_thread_slave_cdc_acm_response("4800", 4);
            break;
        case 9600 :
            status = tx_demo_thread_slave_cdc_acm_response("9600", 4);
            break;
        case 115200 :
            status = tx_demo_thread_slave_cdc_acm_response("115200", 6);
            break;
    }
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE

Wykonywanie operacji IOCTL get line state w interfejsie CDC-ACM

## <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi pobrać parametry stanu wiersza.

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE
- **parametr**: Wskaźnik do struktury parametrów wiersza:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.

### <a name="example"></a>Przykład

```c
/* This is to retrieve RTS state. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE, &line_state);

/* Any error ? */
if (status == UX_SUCCESS)
{
/* Check state. */
    if (line_state.ux_slave_class_cdc_acm_parameter_rts == UX_TRUE)
        /* State is ON. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS ON", 6);
    else
        /* State is OFF. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS OFF", 7);
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE

Wykonywanie polecenia IOCTL Set Line State w interfejsie CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi pobrać parametry stanu wiersza

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- **parametr**: Wskaźnik do struktury parametrów wiersza:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.

### <a name="example"></a>Przykład

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE

Wykonywanie potoku PRZERWANIA IOCTL w interfejsie CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi przerwać potok. Aby na przykład przerwać bieżący zapis, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT zostać przekazana jako parametr.

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE
- **parametr**: Kierunek potoku:

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Nieprawidłowy kierunek potoku.

### <a name="example"></a>Przykład

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START

Uruchamianie transmisji IOCTL w interfejsie CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja chce używać transmisji za pomocą wywołania zwrotnego.

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START
- **parametr**: Wskaźnik do struktury parametru Rozpocznij transmisję:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_ERROR** (0xFF) Transmisja została już uruchomiona.
- **UX_MEMORY_INSUFFICIENT** (0x12) Alokacja pamięci nie powiodła się.

### <a name="example"></a>Przykład

```c
/* Set the callback parameter. */

callback.ux_device_class_cdc_acm_parameter_write_callback
    = tx_demo_thread_slave_write_callback;

callback.ux_device_class_cdc_acm_parameter_read_callback
    = tx_demo_thread_slave_read_callback;

/* Program the start of transmission. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP

Wykonywanie zatrzymania transmisji IOCTL w interfejsie CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja chce przestać używać funkcji transmisji za pomocą wywołania zwrotnego.

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **ioctl_function:** ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP
- **parametr**: Nie jest używany

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_ERROR** (0xFF) Brak ciągłej transmisji.

### <a name="example"></a>Przykład

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a>ux_device_class_cdc_acm_read

Odczyt z potoku CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi odczytywać dane z potoku danych OUT (OUT z hosta, IN z urządzenia). Blokuje.

> [!Note]
> Ta funkcja odczytuje nieprzetworzone dane zbiorcze z hosta, więc oczekuje do momentu zapełnienia buforu lub zakończenia transferu przez krótki pakiet (w tym pakiet o zerowej długości). Aby uzyskać więcej informacji, zapoznaj się z [**sekcją Ogólne zagadnienia dotyczące transferu zbiorczego.**](#general-considerations-for-bulk-transfer)

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **buffer:** adres buforu, na którym będą przechowywane dane.
- **requested_length:** maksymalna oczekiwana długość.
- **actual_length:** długość zwracana do buforu.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Urządzenie nie jest już w stanie skonfigurowanym.
- **UX_TRANSFER_NO_ANSWER** (0x22) Brak odpowiedzi z urządzenia. Urządzenie prawdopodobnie zostało odłączone, gdy transfer był w stanie oczekiwania.

### <a name="example"></a>Przykład

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a>ux_device_class_cdc_acm_write

Zapis w potoku CDC-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi zapisywać dane w potoku danych IN (IN z hosta, OUT z urządzenia). Blokuje.

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **buffer**: adres buforu, na którym są przechowywane dane.
- **requested_length:** długość buforu do zapisu.
- **actual_length:** długość zwracana do buforu po wykonaniu zapisu.

### <a name="return-value"></a>Wartość zwracana
- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Urządzenie nie jest już w stanie skonfigurowanym.
- **UX_TRANSFER_NO_ANSWER** (0x22) Brak odpowiedzi z urządzenia. Urządzenie prawdopodobnie zostało odłączone, gdy transfer był w stanie oczekiwania.

### <a name="example"></a>Przykład

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a>ux_device_class_cdc_acm_write_with_callback

Zapisywanie w potoku CDC-ACM przy użyciu wywołania zwrotnego

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi zapisywać dane w potoku danych IN (IN z hosta, OUT z urządzenia). Ta funkcja nie blokuje, a ukończenie zostanie wykonane za pomocą wywołania zwrotnego ustawionego w UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.

### <a name="parameters"></a>Parametry

- **cdc_acm:** wskaźnik do wystąpienia klasy cdc.
- **buffer**: adres buforu, na którym są przechowywane dane.
- **requested_length:** długość buforu do zapisu.
- **actual_length:** długość zwracana do buforu po wykonaniu zapisu

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Urządzenie nie jest już w stanie skonfigurowanym.
- **UX_TRANSFER_NO_ANSWER** (0x22) Brak odpowiedzi z urządzenia. Urządzenie prawdopodobnie zostało odłączone, gdy transfer był w stanie oczekiwania.

### <a name="example"></a>Przykład

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a>Klasa CDC-ECM urządzenia USB

Klasa CDC-ECM urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzenie ethernet. Ta klasa jest oparta na standardzie USB i jest podzbiorem standardu CDC.

Platformę urządzeń zgodną ze standardem CDC-ACM należy zadeklarować za pomocą stosu urządzeń. Przykład można znaleźć tutaj poniżej.

```c
unsigned char device_framework_full_speed[] = {

    /* Device descriptor 18 bytes
    0x02 bDeviceClass: CDC_ECM class code
    0x06 bDeviceSubclass: CDC_ECM class sub code
    0x00 bDeviceProtocol: CDC_ECM Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    0x3939 idVendor: Azure RTOS test.
    */
    
    0x12, 0x01, 0x10, 0x01,
    0x02, 0x00, 0x00, 0x08,
    0x39, 0x39, 0x08, 0x08, 0x00, 0x01, 0x01, 0x02, 03,0x01,
    
    /* Configuration 1 descriptor 9 bytes. */
    0x09, 0x02, 0x58, 0x00,0x02, 0x01, 0x00,0x40, 0x00,
    
    /* Interface association descriptor. 8 bytes. */
    
    0x08, 0x0b, 0x00, 0x02, 0x02, 0x06, 0x00, 0x00,
    
    /* Communication Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x06, 0x00, 0x00,
    
    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00, 0x10, 0x01,
    
    /* ECM Functional Descriptor 13 bytes */
    0x0D, 0x24, 0x0F, 0x04,0x00, 0x00, 0x00, 0x00, 0xEA, 0x05, 0x00,
    0x00,0x00,
    
    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,0x01,
    
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x08,
    
    /* Data Class Interface Descriptor Alternate Setting 0, 0 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x00, 0x0A, 0x00, 0x00, 0x00,
    
    /* Data Class Interface Descriptor Alternate Setting 1, 2 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x01, 0x02, 0x0A, 0x00, 0x00,0x00,
    
    /* First alternate setting Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x02, 0x02, 0x40, 0x00, 0x00,
    
    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81, 0x02, 0x40, 0x00,0x00

};
```

Klasa CDC-ECM używa bardzo podobnego podejścia deskryptora urządzeń do CDC-ACM, a także wymaga deskryptora IAD. Zobacz definicję klasy CDC-ACM.

Oprócz zwykłej struktury urządzeń CDC-ECM wymaga specjalnych deskryptorów ciągów. Poniżej przedstawiono przykład.

```c
unsigned char string_framework[] = {
    /* Manufacturer string descriptor: Index 1 - "Azure RTOS" */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,
    
    /* Product string descriptor: Index 2 - "EL CDCECM Device" */
    0x09, 0x04, 0x02, 0x10,
    0x45, 0x4c, 0x20, 0x43, 0x44, 0x43, 0x45, 0x43,
    0x4d, 0x20, 0x44, 0x65, 0x76, 0x69, 0x63, 0x64,
    
    /* Serial Number string descriptor: Index 3 - "0001" */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31,
    
    /* MAC Address string descriptor: Index 4 - "001E5841B879" */
    0x09, 0x04, 0x04, 0x0C,
    0x30, 0x30, 0x31, 0x45, 0x35, 0x38,
    0x34, 0x31, 0x42, 0x38, 0x37, 0x39

};
```

Deskryptor ciągu adresu MAC jest używany przez klasę CDC-ECM do odpowiadania na zapytania hosta dotyczące adresu MAC, na który odpowiada urządzenie przy użyciu protokołu TCP/IP. Można go ustawić na wybór urządzenia, ale musi być zdefiniowany w tym miejscu.

Inicjowanie klasy CDC-ECM jest następujące.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_activate = UX_NULL;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_deactivate = UX_NULL;

/* Define a NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[5] = 0x79;

/* Initialize the device cdc_ecm class. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_ecm_name,
    ux_device_class_cdc_ecm_entry, 1,0,&cdc_ecm_parameter);
```

Inicjowanie tej klasy oczekuje tego samego wywołania zwrotnego funkcji w przypadku aktywacji i dezaktywacji, chociaż w tym ćwiczeniu są one ustawione na wartość NULL, dzięki czemu nie jest wykonywane żadne wywołanie zwrotne.

Następne parametry są dla definicji identyfikatorów węzłów. 2 Węzły są niezbędne dla CDC-ECM, węzła lokalnego i węzła zdalnego. Węzeł lokalny określa adres MAC urządzenia, a węzeł zdalny określa adres MAC hosta. Węzeł zdalny musi być tym samym węzłem, który został zadeklarowany w deskryptorze ciągu struktury urządzenia.

Klasa CDC-ECM ma wbudowane interfejsy API do przesyłania danych w obie strony, ale są one ukryte dla aplikacji, ponieważ aplikacja użytkownika będzie komunikować się z urządzeniem USB Ethernet za pośrednictwem netx.

Klasa USBX CDC-ECM jest ściśle powiązana Azure RTOS stosem sieciowym NetX. Aplikacja korzystająca z klasy NetX i USBX CDC-ECM aktywuje stos sieci NetX w zwykły sposób, ale dodatkowo musi aktywować stos sieciowy USB w następujący sposób.

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

Stos sieciOWY USB musi być aktywowany tylko raz i nie jest specyficzny dla CDCECM, ale jest wymagany przez dowolną klasę USB, która wymaga usług NetX.

Klasa CDC-ECM zostanie rozpoznana przez hosty MAC OS i Linux. Firma Microsoft nie dostarcza jednak sterowników do natywnego rozpoznawania Windows CDC-ECM. Niektóre produkty komercyjne istnieją dla Windows platform i dostarczają własny plik inf. Ten plik musi zostać zmodyfikowany w taki sam sposób jak szablon INF CDC-ACM, aby był zgodne z identyfikatorem PID/VID urządzenia sieciowego USB.

## <a name="usb-device-hid-class"></a>Klasa HID urządzenia USB

Klasa HID urządzenia USB umożliwia systemowi hosta USB łączenie się z urządzeniem HID z określonymi możliwościami klienta HID.

Klasa urządzenia USBX HID jest stosunkowo prosta w porównaniu do strony hosta. Jest ona ściśle powiązana z zachowaniem urządzenia i jego deskryptora HID.

Każdy klient HID wymaga najpierw zdefiniowania struktury urządzenia HID jako przykładu poniżej.

```c
UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0x81, 0x0A, 0x01, 0x01, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x22, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x01, 0x03, 0x00, 0x00, 0x00,

    /* HID descriptor */
    0x09, 0x21, 0x10, 0x01, 0x21, 0x01, 0x22, 0x3f, 0x00,

    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x81, 0x03, 0x08, 0x00, 0x08

};
```

Framework HID zawiera deskryptor interfejsu opisujący klasę HID i podklasę urządzenia HID. Interfejs HID może być klasą autonomiczną lub częścią urządzenia złożonego.

Obecnie klasa HID USBX nie obsługuje wielu identyfikatorów raportów, ponieważ większość aplikacji wymaga tylko jednego identyfikatora (ID zero). Jeśli wiele identyfikatorów raportów jest funkcją, która Cię interesuje, skontaktuj się z nami.

Inicjalizacja klasy HID jest w następujący sposób, przy użyciu klawiatury USB jako przykładu.

```c
/* Initialize the hid class parameters for a keyboard. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_keyboard_report;
hid_parameter.ux_device_class_hid_parameter_report_length = HID_KEYBOARD_REPORT_LENGTH;
hid_parameter.ux_device_class_hid_parameter_callback = tx_demo_thread_hid_callback;
hid_parameter.ux_device_class_hid_parameter_report_id = 0;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry, 1,0,(VOID *)&hid_parameter);
if (status!=UX_SUCCESS)
    return;
```

Aplikacja musi przekazać do klasy HID deskryptor raportu HID i jego długość. Deskryptor raportu to kolekcja elementów opisujących urządzenie. Aby uzyskać więcej informacji na temat gramatyki HID, zapoznaj się ze specyfikacją klasy HID USB.

Oprócz deskryptora raportu aplikacja przekazuje wywołanie z powrotem w przypadku wystąpienia zdarzenia HID.

Klasa USBX HID obsługuje następujące standardowe polecenia HID z hosta.

| Nazwa polecenia                             | Wartość | Opis                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT   | 0x01  | Uzyskiwanie raportu z urządzenia                     |
| UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE     | 0x02  | Uzyskiwanie częstotliwości bezczynności punktu końcowego przerwań |
| UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL | 0x03  | Uruchamianie protokołu na urządzeniu           |
| UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT   | 0x09  | Ustawianie raportu na urządzeniu                       |
| UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE     | 0x0a  | Ustawianie częstotliwości bezczynności punktu końcowego przerwań |
| UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL | 0x0b  | Uruchamianie protokołu na urządzeniu           |

Raport Get and Set (Pobierz i ustaw) to najczęściej używane przez program HID polecenia do transferowania danych między hostem a urządzeniem. Najczęściej host wysyła dane do punktu końcowego kontroli, ale może odbierać dane w punkcie końcowym przerwania lub wydając polecenie GET_REPORT w celu pobrania danych w punkcie końcowym kontroli.

Klasa HID może wysyłać dane z powrotem do hosta w punkcie końcowym przerwań przy użyciu ux_device_class_hid_event_set funkcji.

### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

Ustawianie zdarzenia na klasę HID

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi wysłać zdarzenie HID z powrotem do hosta. Funkcja nie blokuje, tylko umieszcza raport w kolejce cyklicznej i wraca do aplikacji.

### <a name="parameters"></a>Parametry

- **hid:** Wskaźnik do wystąpienia hid klasy.
- **hid_event:** Wskaźnik do struktury zdarzenia ukrytego.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0x00) Ta operacja powiodła się.
- **UX_ERROR** (0xFF) Błąd brak dostępnego miejsca w kolejce cyklicznej.

### <a name="example"></a>Przykład

```c
/* Insert a key into the keyboard event. Length is fixed to 8. */
hid_event.ux_device_class_hid_event_length = 8;

/* First byte is a modifier byte. */
hid_event.ux_device_class_hid_event_buffer[0] = 0;

/* Second byte is reserved. */
hid_event.ux_device_class_hid_event_buffer[1] = 0;

/* The 6 next bytes are keys. We only have one key here. */
hid_event.ux_device_class_hid_event_buffer[2] = key;

/* Set the keyboard event. */
ux_device_class_hid_event_set(hid, &hid_event);
```

Wywołanie zwrotne zdefiniowane podczas inicjowania klasy HID wykonuje przeciwieństwo wysyłania zdarzenia. Pobiera jako dane wejściowe zdarzenie wysyłane przez hosta. Prototyp wywołania zwrotnego jest następujący.

### <a name="hid_callback"></a>hid_callback

Pobieranie zdarzenia z klasy HID

### <a name="prototype"></a>Prototype

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy host wysyła raport HID do aplikacji.

### <a name="parameters"></a>Parametry

- **hid:** Wskaźnik do wystąpienia hid klasy.
- **hid_event:** Wskaźnik do struktury zdarzenia ukrytego.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak interpretować zdarzenie dla klawiatury HID:

```c
UINT tx_demo_thread_hid_callback(UX_SLAVE_CLASS_HID *hid, UX_SLAVE_CLASS_HID_EVENT *hid_event
{
/* There was an event. Analyze it. Is it NUM LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_NUM_LOCK_MASK)
    /* Set the Num lock flag. */
    num_lock_flag = UX_TRUE;
else
    /* Reset the Num lock flag. */
    num_lock_flag = UX_FALSE;

/* There was an event. Analyze it. Is it CAPS LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_CAPS_LOCK_MASK)
    /* Set the Caps lock flag. */
    caps_lock_flag = UX_TRUE;
else
    /* Reset the Caps lock flag. */
    caps_lock_flag = UX_FALSE;
}
```
