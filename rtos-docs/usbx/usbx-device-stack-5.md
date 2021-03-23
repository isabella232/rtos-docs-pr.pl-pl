---
title: Rozdział 5 — zagadnienia dotyczące klas urządzeń USBX
description: Dowiedz się więcej na temat zagadnień dotyczących klas urządzeń USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 84f215ad990a2fe185a08f3876276528787ef8bc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822446"
---
# <a name="chapter-5---usbx-device-class-considerations"></a>Rozdział 5 — zagadnienia dotyczące klas urządzeń USBX

## <a name="device-class-registration"></a>Rejestracja klasy urządzeń

Każda klasa urządzeń jest zgodna z tą samą zasadą w przypadku rejestracji. Struktura zawierająca określone parametry klasy jest przenoszona do funkcji inicjowania klasy.

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

Każda klasa może zarejestrować, opcjonalnie, funkcję wywołania zwrotnego, gdy wystąpienie klasy zostanie aktywowane. Wywołanie zwrotne jest następnie wywoływane przez stos urządzeń w celu powiadomienia aplikacji o utworzeniu wystąpienia.

Aplikacja będzie miała w swojej treści 2 funkcje do aktywacji i dezaktywacji, jak pokazano w poniższym przykładzie.

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

Nie zaleca się wykonywania żadnych czynności w ramach tych funkcji, ale w celu znają wystąpienia klasy i zsynchronizowania z pozostałą częścią aplikacji.

## <a name="usb-device-storage-class"></a>Klasa magazynu urządzenia USB

Klasa magazynu urządzenia USB pozwala na udostępnienie urządzenia magazynującego w systemie jako widocznego dla hosta USB.

Klasa magazynu urządzeń USB nie udostępnia rozwiązania do magazynowania. Tylko akceptuje i interpretuje żądania SCSI pochodzące z hosta. Gdy jeden z tych żądań jest poleceniem odczytu lub zapisu, wywoła wstępnie zdefiniowane wywołanie z powrotem do obsługi rzeczywistego urządzenia magazynującego, np. sterownika urządzenia usługi ATA lub sterownika urządzenia flash.

Podczas inicjowania klasy magazynu urządzeń struktura wskaźnika jest przyznany do klasy, która zawiera wszystkie wymagane informacje. Poniżej znajduje się przykład.

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

W tym przykładzie ciągi magazynu sterowników są dostosowane przez przypisanie wskaźników ciągu do odpowiadającego parametru. Jeśli jeden z wskaźników ciągu zostanie pozostawiony do UX_NULL, używany jest domyślny ciąg usługi Azure RTO.

W tym przykładzie adres ostatniego bloku dysku lub LBA jest określony, a także rozmiar sektora logicznego. LBA to liczba sektorów dostępnych w nośniku — 1. Długość bloku jest ustawiona na 512 w zwykłych nośnikach magazynu. Dla dysków optycznych można ustawić wartość 2048.

Aplikacja musi przekazać trzy wskaźniki funkcji wywołania zwrotnego, aby umożliwić klasie magazynu odczytywanie, zapisywanie i uzyskiwanie stanu nośnika.

W poniższym przykładzie przedstawiono prototypy funkcji odczytu i zapisu.

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

- *Magazyn* jest wystąpieniem klasy magazynu.
- *LUN* to numer LUN, do którego jest kierowane polecenie.
- *data_pointer* to adres buforu, który ma być używany do odczytu lub zapisu.
- *number_blocks* to liczba sektorów do odczytu/zapisu.
- *LBA* jest adresem sektora, który ma zostać odczytany.
- *media_status* powinna zostać uzupełniona dokładnie tak, jak wartość zwrotna wywołania zwrotnego stanu nośnika.

Wartość zwracana może mieć wartość UX_SUCCESS lub UX_ERROR wskazującą, że operacja powiodła się lub nie powiodła się. Te operacje nie muszą zwracać żadnych innych kodów błędów. Jeśli wystąpi błąd w żadnej operacji, Klasa magazynu wywoła funkcję wywołania zwrotnego stanu.

Ta funkcja ma następujący prototyp.

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

Parametr wywołujący media_id nie jest obecnie używany i powinien być zawsze równy 0. W przyszłości może służyć do rozróżnienia wielu urządzeń magazynujących lub urządzeń magazynujących z wieloma jednostkami LUN SCSI. Ta wersja klasy magazynu nie obsługuje wielu wystąpień klasy magazynu ani urządzeń magazynujących z wieloma jednostkami LUN SCSI.

Wartość zwracana jest kodem błędu SCSI, który może mieć następujący format.

- **Bity 0-7** Sense_key
- **Bity 8-15** Dodatkowy kod wykrywania
- **Bity 16-23** Dodatkowy kwalifikator kodu wykrywania

Poniższa tabela zawiera możliwe kombinacje sensu/ASC/ASCQ.

| Klucz wykrywania | ASC | ASCQ | Opis                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| 00        | 00  | 00   | NIE MA SENSU                                          |
| 01        | 17  | 01   | ODZYSKANE DANE Z PONOWNYMI PRÓBAMI                       |
| 01        | 18  | 00   | ODZYSKIWANIE DANYCH PRZY UŻYCIU ECC                           |
| 02        | 04  | 01   | DYSK LOGICZNY NIE JEST GOTOWY — STAJE SIĘ GOTOWY          |
| 02        | 04  | 02   | DYSK LOGICZNY NIE JEST GOTOWY — WYMAGANE JEST ZAINICJOWANIE |
| 02        | 04  | 04   | NIEGOTOWY FORMAT JEDNOSTKI LOGICZNEJ       |
| 02        | 04  | ZZ   | DYSK LOGICZNY NIE JEST GOTOWY — URZĄDZENIE JEST ZAJĘTE          |
| 02        | 06  | 00   | NIE ZNALEZIONO POZYCJI ODWOŁANIA                       |
| 02        | 08  | 00   | BŁĄD KOMUNIKACJI JEDNOSTKI LOGICZNEJ                |
| 02        | 08  | 01   | LIMIT CZASU KOMUNIKACJI JEDNOSTKI LOGICZNEJ               |
| 02        | 08  | 80   | PRZEPEŁNIENIE KOMUNIKACJI JEDNOSTKI LOGICZNEJ                |
| 02        | Art  | 00   | BRAK ŚREDNIEJ                                |
| 02        | 54  | 00   | BŁĄD INTERFEJSU USB DO HOSTA SYSTEMU              |
| 02        | 80  | 00   | NIEWYSTARCZAJĄCE ZASOBY                            |
| 02        | ZZ  | ZZ   | NIEZNANY BŁĄD                                     |
| 03        | 02  | 00   | NIE ZAKOŃCZONO WYSZUKIWANIA                                  |
| 03        | 03  | 00   | BŁĄD ZAPISU                                       |
| 03        | 10  | 00   | BŁĄD CRC IDENTYFIKATORA                                      |
| 03        | 11  | 00   | NIEODWRACALNY BŁĄD ODCZYTU                            |
| 03        | 12  | 00   | NIE ZNALEZIONO ZNACZNIKA ADRESU DLA POLA IDENTYFIKATORA               |
| 03        | 13  | 00   | NIE ZNALEZIONO ZNACZNIKA ADRESU DLA POLA DANYCH             |
| 03        | 14  | 00   | NIE ZNALEZIONO ZAPISANEJ JEDNOSTKI                         |
| 03        | 30  | 01   | NIE MOŻNA ODCZYTAĆ FORMATU ŚREDNI-NIEZNANY               |
| 03        | 31  | 01   | POLECENIE FORMATOWANIA NIE POWIODŁO SIĘ                             |
| 04        | 40  | NN   | BŁĄD DIAGNOSTYKI SKŁADNIKA NN (80H-FFH)      |
| 05        | Ust  | 00   | BŁĄD DŁUGOŚCI LISTY PARAMETRÓW                       |
| 05        | 20  | 00   | NIEPRAWIDŁOWY KOD OPERACJI POLECENIA                    |
| 05        | 21  | 00   | ADRES BLOKU LOGICZNEGO POZA ZAKRESEM                |
| 05        | 24  | 00   | NIEPRAWIDŁOWE POLE W PAKIECIE POLECEŃ                   |
| 05        | 25  | 00   | JEDNOSTKA LOGICZNA NIE JEST OBSŁUGIWANA                        |
| 05        | 26  | 00   | NIEPRAWIDŁOWE POLE NA LIŚCIE PARAMETRÓW                   |
| 05        | 26  | 01   | PARAMETR NIE JEST OBSŁUGIWANY                           |
| 05        | 26  | 02   | NIEPRAWIDŁOWA WARTOŚĆ PARAMETRU                           |
| 05        | 39  | 00   | ZAPISYWANIE PARAMETRÓW NIE JEST OBSŁUGIWANE                     |
| 06        | 28  | 00   | NIE GOTOWY DO PRZEJŚCIA DO GOTOWOŚCI — ZMIENIONO NOŚNIK     |
| 06        | 29  | 00   | WYSTĄPIŁO RESETOWANIE LUB ZRESETOWANIE URZĄDZENIA MAGISTRALI       |
| 06        | 2F  | 00   | POLECENIA WYCZYSZCZONE PRZEZ INNEGO INICJATORA             |
| 07        | 27  | 00   | ZAPISZ NOŚNIK CHRONIONY                             |
| 0B        | 4E  | 00   | PODJĘTO PRÓBĘ NAKŁADAJĄCEGO POLECENIA                      |

Istnieją dwa dodatkowe, opcjonalne wywołania zwrotne, które aplikacja może zaimplementować; jeden jest do odpowiadania na polecenie **GET_STATUS_NOTIFICATION** , a drugi jest do odpowiadania na polecenie **SYNCHRONIZE_CACHE** .

Jeśli aplikacja chce obsłużyć GET_STATUS_NOTIFICATION polecenie z hosta, powinien zaimplementować wywołanie zwrotne z następującym prototypem.

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

- *Magazyn* jest wystąpieniem klasy magazynu.
- *media_id* nie jest obecnie używana. notification_class określa klasę powiadomienia.
- *media_notification* powinna być ustawiona przez aplikację w buforze zawierającym odpowiedź na powiadomienie.
- *media_notification_length* powinna być ustawiona przez aplikację w taki sposób, aby zawierała długość buforu odpowiedzi.

Wartość zwracana wskazuje, czy polecenie powiodło się — powinno być **UX_SUCCESS** lub **UX_ERROR**.

Jeśli aplikacja nie implementuje tego wywołania zwrotnego, po odebraniu polecenia **GET_STATUS_NOTIFICATION** program USBX powiadomi hosta, że polecenie nie zostało zaimplementowane.

Polecenie **SYNCHRONIZE_CACHE** powinno być obsługiwane, jeśli aplikacja korzysta z pamięci podręcznej do zapisu z hosta. Host może wysłać to polecenie, jeśli wie, że urządzenie magazynujące zostanie odłączone, na przykład w systemie Windows, jeśli klikniesz prawym przyciskiem myszy ikonę dysku flash na pasku narzędzi i wybierzesz pozycję "Wysuń \[ nazwę urządzenia magazynującego \] ", system Windows wyda polecenie **SYNCHRONIZE_CACHE** na tym urządzeniu.

Jeśli aplikacja chce obsłużyć **GET_STATUS_NOTIFICATION** polecenie z hosta, powinien zaimplementować wywołanie zwrotne z następującym prototypem.

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

Gdzie:

- *Magazyn* jest wystąpieniem klasy magazynu.
- wartość parametru *LUN* określa numer LUN, do którego jest kierowane polecenie.
- *number_blocks* określa liczbę bloków do zsynchronizowania.
- *LBA* jest adresem sektora pierwszego bloku do synchronizacji.
- *media_status* powinna zostać uzupełniona dokładnie tak, jak wartość zwrotna wywołania zwrotnego stanu nośnika.

Wartość zwracana wskazuje, czy polecenie powiodło się — powinno być **UX_SUCCESS** lub **UX_ERROR**.

### <a name="multiple-scsi-lun"></a>Wiele jednostek LUN SCSI

Klasa magazynu urządzeń USBX obsługuje wiele jednostek LUN. W związku z tym można utworzyć urządzenie magazynujące, które jednocześnie działa jak dysk CD-ROM i dysk flash. W takim przypadku Inicjalizacja byłaby nieco inna. Oto przykład dysku flash i dysku CD-ROM:

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

## <a name="usb-device-cdc-acm-class"></a>Przechwytywanie urządzenia USB — Klasa ACM

Klasa przełączenia urządzenia USB do grupy ACM umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzenie szeregowe. Ta klasa jest oparta na standardzie USB i jest podzbiorem standardu przechwytywania zmian.

Architektura urządzenia zgodna z przeskakującą zmianą musi być zadeklarowana przez stos urządzeń. Poniżej znajduje się przykład.

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

Klasa przechwytywania odporności — ACM używa złożonej struktury urządzenia do grupowania interfejsów (kontroli i danych). W związku z tym należy wziąć pod uwagę podczas definiowania deskryptora urządzenia. USBX opiera się na deskryptorze IAD, aby wiedzieć, jak powiązać interfejsy. Deskryptor IAD powinien zostać zadeklarowany przed interfejsami i zawierać pierwszy interfejs klasy przechwytywania-ACM oraz liczbę interfejsów, które są dołączone.

Klasa przechwytywania odporności — ACM używa również deskryptora funkcjonalnego Union, który wykonuje tę samą funkcję co nowszy deskryptor IAD. Chociaż deskryptor funkcjonalny Union musi być zadeklarowany ze względu na historyczne przyczyny i zgodność ze stroną hosta, nie jest używany przez USBX.

Inicjalizacja klasy przechwytywania zmian-ACM oczekuje następujących parametrów.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

Zdefiniowane dwa parametry są wskaźnikami wywołania zwrotnego do aplikacji użytkownika, które będą wywoływane, gdy stos aktywuje lub dezaktywuje tę klasę.

Trzeci zdefiniowany parametr jest wskaźnikiem wywołania zwrotnego do aplikacji użytkownika, który zostanie wywołany, gdy występuje zmiana parametrów kodowania lub wierszy. Na przykład, gdy istnieje żądanie od hosta, aby zmienić stan DTR na **true**, wywołanie zwrotne jest wywoływane, w aplikacji użytkownika IT może sprawdzać stan wiersza za pomocą funkcji IOCTL do Kow host jest gotowy do komunikacji.

Replika przestawna — ACM jest oparta na standardzie USB i jest automatycznie rozpoznawana przez systemy operacyjne MACOs i Linux. Na platformach Windows ta klasa wymaga pliku inf dla systemu Windows w wersji starszej niż 10. System Windows 10 nie wymaga żadnych plików inf. Dostarczamy szablon klasy przechwytywania zmian-ACM i można ją znaleźć w katalogu ***usbx_windows_host_files*** . W przypadku nowszej wersji systemu Windows należy użyć pliku CDC_ACM_Template_Win7_64bit. inf (z wyjątkiem Win10). Ten plik musi zostać zmodyfikowany w celu odzwierciedlenia identyfikatora PID/VID używanego przez urządzenie. Identyfikator PID/VID będzie charakterystyczny dla klienta końcowego, gdy firma i produkt zostaną zarejestrowane przy użyciu portu USB. W pliku inf pola do zmodyfikowania znajdują się tutaj.

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

W środowisku urządzenia urządzenia typu "przechwytywanie zmian typu" Identyfikator PID/VID są przechowywane w deskryptorze urządzenia (Sprawdź zadeklarowany powyżej deskryptor urządzenia).

Gdy systemy hosta USB odnajdują urządzenie przełączenia do sieci USB z funkcją przechwytywania, zainstaluje klasę seryjną, a urządzenie może być używane z dowolnym seryjnym programem terminala. Aby uzyskać informacje, zobacz system operacyjny hosta.

Poniżej przedstawiono funkcje interfejsu API klasy przechwytywania zmian-ACM.

### <a name="ux_device_class_cdc_acm_ioctl"></a>ux_device_class_cdc_acm_ioctl

Wykonywanie operacji IOCTL w interfejsie przechwytywania zmian-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi wykonać różne wywołania IOCTL do interfejsu przechwytywania zmian

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **ioctl_function**: funkcja IOCTL, która ma zostać wykonana.
- **parametr**: wskaźnik do parametru, który jest specyficzny dla wywołania IOCTL.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- Błąd **UX_ERROR** (0xFF) z funkcji

### <a name="example"></a>Przykład

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a>Funkcje IOCTL:

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

Wykonaj kodowanie liniowe zestawu IOCTL w interfejsie przechwytywania zmian-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja wymaga ustawienia parametrów kodowania wiersza.

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING
- **parametr**: wskaźnik do struktury parametru wiersza:

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

**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.

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

Wykonaj polecenie IOCTL pobieranie kodowania wierszy w interfejsie przechwytywania zmian-ACM

### <a name="prototype"></a>Prototype

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja wymaga pobrania parametrów kodowania wiersza.

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING
- **parametr**: wskaźnik do struktury parametru wiersza:

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

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.

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

Wykonaj polecenie IOCTL Pobierz stan wiersza w interfejsie przechwytywania zmian-ACM

## <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja wymaga pobrania parametrów stanu wiersza.

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE
- **parametr**: wskaźnik do struktury parametru wiersza:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.

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

Wykonaj ustawiony stan wiersza polecenia IOCTL w interfejsie przechwytywania zmian-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja wymaga pobrania parametrów stanu wiersza

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE
- **parametr**: wskaźnik do struktury parametru wiersza:

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.

### <a name="example"></a>Przykład

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE

Wykonaj potok PRZERWAnia IOCTL w interfejsie przechwytywania zmian-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi przerwać potok. Na przykład, aby przerwać trwający zapis, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT powinien zostać przesłany jako parametr.

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE
- **Parameter**: kierunek potoku:

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0X53) nieprawidłowy kierunek potoku.

### <a name="example"></a>Przykład

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START

Wykonaj transmisję IOCTL na interfejsie przechwytywania zmian-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja chce używać transmisji z wywołaniem zwrotnym.

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START
- **parametr**: wskaźnik do struktury parametru rozpoczęcia transmisji:

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

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_ERROR** (0Xff) transmisja została już rozpoczęta.
- **UX_MEMORY_INSUFFICIENT** (0x12) alokacja pamięci nie powiodła się.

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

Wykonaj zatrzymanie transmisji IOCTL w interfejsie przechwytywania zmian-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja chce przestać używać transmisji z wywołaniem zwrotnym.

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP
- **parametr**: nieużywany

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_ERROR** (0Xff) brak ciągłej transmisji.

### <a name="example"></a>Przykład

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a>ux_device_class_cdc_acm_read

Odczytaj z potoku przechwytywania zmian-ACM

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi odczytywać dane z potoku danych OUT z hosta (z urządzenia). Jest blokowany.

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **bufor**: adres bufora, w którym będą przechowywane dane.
- **requested_length**: Maksymalna oczekiwana długość.
- **actual_length**: długość zwrócona do buforu.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- Urządzenie **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) nie jest już w skonfigurowanym stanie.
- **UX_TRANSFER_NO_ANSWER** (0X22) Brak odpowiedzi z urządzenia. Urządzenie zostało prawdopodobnie rozłączone w czasie oczekiwania na przeniesienie.

### <a name="example"></a>Przykład

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a>ux_device_class_cdc_acm_write

Zapisywanie w potoku przechwytywania

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi zapisywać w potoku danych (w ramach hosta z poziomu urządzenia). Jest blokowany.

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **bufor**: adres bufora, w którym są przechowywane dane.
- **requested_length**: długość buforu do zapisania.
- **actual_length**: długość zwrócona do buforu po wykonaniu operacji zapisu.

### <a name="return-value"></a>Wartość zwracana
- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- Urządzenie **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) nie jest już w skonfigurowanym stanie.
- **UX_TRANSFER_NO_ANSWER** (0X22) Brak odpowiedzi z urządzenia. Urządzenie zostało prawdopodobnie rozłączone w czasie oczekiwania na przeniesienie.

### <a name="example"></a>Przykład

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a>ux_device_class_cdc_acm_write_with_callback

Zapisywanie w potoku funkcji przechwytywania

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja musi zapisywać w potoku danych (w ramach hosta z poziomu urządzenia). Ta funkcja nie jest zablokowana i uzupełnianie zostanie wykonane za pomocą wywołania zwrotnego w UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.

### <a name="parameters"></a>Parametry

- **cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.
- **bufor**: adres bufora, w którym są przechowywane dane.
- **requested_length**: długość buforu do zapisania.
- **actual_length**: długość zwrócona do buforu po wykonaniu zapisu

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- Urządzenie **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) nie jest już w skonfigurowanym stanie.
- **UX_TRANSFER_NO_ANSWER** (0X22) Brak odpowiedzi z urządzenia. Urządzenie zostało prawdopodobnie rozłączone w czasie oczekiwania na przeniesienie.

### <a name="example"></a>Przykład

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a>Przechwytywanie urządzenia USB — Klasa ECM

Klasa przełączania urządzenia USB ECM umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzeniem Ethernet. Ta klasa jest oparta na standardzie USB i jest podzbiorem standardu przechwytywania zmian.

Architektura urządzenia zgodna z przeskakującą zmianą musi być zadeklarowana przez stos urządzeń. Poniżej znajduje się przykład.

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

Klasa przechwytywania zmian-ECM używa bardzo podobnego podejścia deskryptora urządzenia do przechwytywania zmian-ACM, a także wymaga deskryptora IAD. Zobacz Klasa przechwytywania zmian-ACM dla definicji.

Oprócz zwykłej struktury urządzeń Funkcja przechwytywania zmian ECM wymaga specjalnych deskryptorów ciągów. Poniżej znajduje się przykład.

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

Deskryptor ciągu adresu MAC jest używany przez klasę "reECMd" w celu odpowiedzi na zapytania hosta dotyczące adresu MAC, na którym urządzenie odpowiada, w protokole TCP/IP. Może być ustawiony na wybór urządzenia, ale musi być tutaj zdefiniowany.

Zainicjowanie klasy przechwytywania zmian-ECM jest następujące.

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

Inicjalizacja tej klasy oczekuje tego samego wywołania zwrotnego funkcji dla aktywacji i dezaktywacji, chociaż tutaj jako ćwiczenie są ustawione na wartość NULL, co oznacza, że wywołanie zwrotne nie jest wykonywane.

Następne parametry są dla definicji identyfikatorów węzłów. 2 węzły są niezbędne do przechwytywania zmian-ECM, węzła lokalnego i węzła zdalnego. Węzeł lokalny określa adres MAC urządzenia, natomiast węzeł zdalny określa adres MAC hosta. Węzeł zdalny musi być taki sam jak jeden zadeklarowany w deskryptorze ciągu Framework urządzenia.

Klasa przechwytywania zmian-ECM ma wbudowane interfejsy API służące do transferowania danych, ale są one ukryte dla aplikacji, ponieważ aplikacja użytkownika komunikuje się z urządzeniem USB Ethernet za pośrednictwem usługi NetX.

Klasa USBX przechwytywania-ECM jest ściśle związana z stosem sieci usługi Azure RTO NetX. Aplikacja, która korzysta z klasy NetX i USBX Reporting-ECM, umożliwia aktywowanie stosu sieci NetX w zwykły sposób, ale dodatkowo wymaga aktywowania stosu sieci USB w następujący sposób.

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

Stos sieci USB musi być aktywowany tylko raz i nie jest specyficzny dla CDCECM, ale jest wymagany przez dowolną klasę USB wymagającą usług NetX Services.

Klasa przechwytywania zmian-ECM jest rozpoznawana przez hosty z systemem MAC OS i Linux. Nie ma jednak sterownika dostarczonego przez system Microsoft Windows do rozpoznawania natywnych danych przechwytywania ECM. Niektóre produkty komercyjne istnieją dla platform systemu Windows i dostarczają własnych plików inf. Ten plik musi być zmodyfikowany w taki sam sposób, jak szablon inf przechwytywania zmian systemu w celu dopasowania do identyfikatora PID/VID urządzenia sieciowego USB.

## <a name="usb-device-hid-class"></a>Klasa HID urządzenia USB

Klasa HID urządzenia USB umożliwia systemowi hosta USB łączenie się z urządzeniem HID z konkretnymi możliwościami klienta HID.

Klasa urządzenia HID USBX jest stosunkowo prosta w porównaniu do strony hosta. Jest ściśle powiązane z zachowaniem urządzenia i jego deskryptora HID.

Każdy klient HID musi najpierw zdefiniować strukturę urządzenia HID, jak pokazano poniżej.

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

Struktura HID zawiera deskryptor interfejsu, który opisuje klasę HID i podklasę urządzenia HID. Interfejs HID może być klasą autonomiczną lub częścią urządzenia złożonego.

Obecnie Klasa USBX HID nie obsługuje wielu identyfikatorów raportów, ponieważ większość aplikacji wymaga tylko jednego identyfikatora (identyfikator zero). Jeśli potrzebujesz wielu identyfikatorów raportów, skontaktuj się z nami.

Inicjalizacja klasy HID odbywa się tak, jak na przykład przy użyciu klawiatury USB.

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

Aplikacja musi przekazać do klasy HID deskryptor raportu HID i jego długość. Deskryptor raportu to kolekcja elementów, które opisują urządzenie. Aby uzyskać więcej informacji na temat gramatyki HID, zobacz specyfikację klasy USB HID.

Oprócz deskryptora raportu aplikacja przekazuje wywołanie z powrotem, gdy wystąpi zdarzenie HID.

Klasa HID USBX obsługuje następujące standardowe polecenia HID z hosta.

| Nazwa polecenia                             | Wartość | Opis                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT   | 0x01  | Pobierz Raport z urządzenia                     |
| UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE     | 0x02  | Pobierz częstotliwość bezczynności punktu końcowego przerwania |
| UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL | 0x03  | Pobieranie protokołu uruchomionego na urządzeniu           |
| UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT   | 0x09  | Ustawianie raportu na urządzeniu                       |
| UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE     | 0x0A  | Ustaw częstotliwość bezczynności punktu końcowego przerwania |
| UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL | 0x0b  | Pobieranie protokołu uruchomionego na urządzeniu           |

Raport pobieranie i Ustawianie jest najczęściej używanymi poleceniami przez HID do przesyłania danych z powrotem i do przodu między hostem i urządzeniem. Najczęściej Host wysyła dane w punkcie końcowym kontroli, ale może odbierać dane w punkcie końcowym przerwania lub przez wydawanie GET_REPORT polecenia w celu pobrania danych w punkcie końcowym sterowania.

Klasa HID może wysyłać dane z powrotem do hosta w punkcie końcowym przerwania za pomocą funkcji ux_device_class_hid_event_set.

### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

Ustawianie zdarzenia na klasę HID

### <a name="prototype"></a>Prototype

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy aplikacja wymaga wysłania zdarzenia HID z powrotem do hosta. Funkcja nie blokuje, tylko umieszcza raport w kolejce cyklicznej i zwraca do aplikacji.

### <a name="parameters"></a>Parametry

- **HID**: wskaźnik do wystąpienia klasy HID.
- **hid_event**: wskaźnik do struktury zdarzenia HID.

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.
- **UX_ERROR** (0Xff) błąd: Brak dostępnego miejsca w kolejce cyklicznej.

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

Wywołanie zwrotne zdefiniowane podczas inicjowania klasy HID wykonuje przeciwieństwo do wysyłania zdarzenia. Jest ona pobierana jako dane wejściowe dla zdarzenia wysyłanego przez hosta. Prototyp wywołania zwrotnego jest następujący.

### <a name="hid_callback"></a>hid_callback

Pobieranie zdarzenia z klasy HID

### <a name="prototype"></a>Prototype

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy Host wysyła raport HID do aplikacji.

### <a name="parameters"></a>Parametry

- **HID**: wskaźnik do wystąpienia klasy HID.
- **hid_event**: wskaźnik do struktury zdarzenia HID.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak interpretować zdarzenie dla klawiatury HID:

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
