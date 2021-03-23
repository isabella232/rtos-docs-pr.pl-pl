---
title: Implementacja USBX PictBridge
description: UBSX obsługuje pełną implementację technologii PictBridge zarówno na hoście, jak i urządzeniu. PictBridge znajduje się na szczycie klasy USBX PIMA po obu stronach.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ce291f794cbc458d402cbefa3fd81dcc6f371b57
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104823941"
---
# <a name="chapter-4-usbx-pictbridge-implementation"></a>Rozdział 4: implementacja USBX PictBridge

UBSX obsługuje pełną implementację technologii PictBridge zarówno na hoście, jak i urządzeniu. PictBridge znajduje się na szczycie klasy USBX PIMA po obu stronach. 

Standardy PictBridge umożliwiają połączenie cyfrowego aparatu fotograficznego lub inteligentnego telefonu bezpośrednio z drukarką bez komputera, co umożliwia bezpośrednie drukowanie na określonych drukarkach z obsługą technologii PictBridge.

Gdy do drukarki jest podłączony aparat lub telefon, drukarka jest hostem USB, a aparat jest urządzeniem USB. Jednak w przypadku technologii PictBridge aparat będzie wyświetlany jako host, a polecenia są sterowane przez aparat. Aparat jest serwerem magazynu, drukarką klienta magazynu. Aparat jest klientem drukowania, a drukarka jest oczywiście serwerem wydruku.

PictBridge korzysta z portów USB jako warstwy transportowej, ale korzysta z protokołu PTP (Picture Transfering Protocol) dla protokołu komunikacyjnego.

Poniżej znajduje się Diagram poleceń/odpowiedzi między klientem DPS a serwerem DPS w przypadku wystąpienia zadania drukowania.

![Diagram poleceń/odpowiedzi między klientem D P S a serwerem D P S w przypadku wystąpienia zadania drukowania.](./media/usbx-host-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a>Implementacja klienta PictBridge

Aby program PictBridge na kliencie wymagał pierwszego uruchomienia stosu urządzenia USBX oraz klasy PIMA.

Platforma urządzeń opisuje klasę PIMA w następujący sposób.

```C
UCHAR device_framework_full_speed[] =
{
    /* Device descriptor */
       0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x20,
       0xA9, 0x04, 0xB6, 0x30, 0x00, 0x00, 0x00, 0x00,
       0x00, 0x01,
    /* Configuration descriptor */
       0x09, 0x02, 0x27, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,
    /* Interface descriptor */
       0x09, 0x04, 0x00, 0x00, 0x03, 0x06, 0x01, 0x01, 0x00,
    /* Endpoint descriptor (Bulk Out) */
       0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Bulk In) */
       0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Interrupt) */
       0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x60
};
```

Klasa Pima używa pola ID 0x06 i ma jego podklasę na wartość 0x01 dla obrazu wciąż, a protokół to 0x01 dla PIMA 15740.

3 punkty końcowe są zdefiniowane w tej klasie, 2 zbiorczo do wysyłania/otrzymywania danych i jednego przerwania dla zdarzeń.

W przeciwieństwie do innych implementacji urządzeń USBX, aplikacja PictBridge nie musi definiować samej klasy. Zamiast wywołuje funkcję ***ux_pictbridge_dpsclient_start***. Poniżej znajduje się przykład:

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "Azure RTOS",10);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.
    ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

Parametry przesłane do klienta PictBridge są następujące:

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no,
    : String of serial number pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version pictbridge.ux_pictbridge_dpslocal. ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

Następnym krokiem jest zasynchronizowanie urządzenia i hosta oraz gotowość do wymiany informacji.

Jest to realizowane przez oczekiwanie na flagę zdarzenia w następujący sposób:

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get
    (&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR, &actual_flags,
    UX_PICTBRIDGE_EVENT_TIMEOUT);
```

Jeśli stan komputera jest w stanie **DISCOVERY_COMPLETE** , Strona aparatu (klient DPS) będzie zbierać informacje dotyczące drukarki i jej możliwości.

Jeśli klient DPS jest gotowy do zaakceptowania zadania drukowania, jego stan zostanie ustawiony na **UX_PICTBRIDGE_NEW_JOB_TRUE**. Można to sprawdzić poniżej:

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)

    /* We can print something … */
```

Kolejne przykłady dla deskryptorów joib drukowania muszą zostać wypełnione w następujący sposób:

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo ->ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo ->ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo ->ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo ->ux_pictbridge_jobinfo_object_data_read =
    ux_demo_object_data_copy;

/* This is a demo, the fileID is hardwired (1 and 2 for scripts, 3 for photo to be printed. */

printinfo.ux_pictbridge_printinfo_fileid =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;

ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_filename,
    "Pictbridge demo file", 20);
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_date, "01/01/2008",
    10);

/* Fill in the object info to be printed. First get the pointer to the object container in the job info structure. */
object = (UX_SLAVE_CLASS_PIMA_OBJECT *) jobinfo ->
    ux_pictbridge_jobinfo_object;

/* Store the object format: JPEG picture. */
object ->ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object ->ux_device_class_pima_object_compressed_size = IMAGE_LEN; object ->ux_device_class_pima_object_offset = 0;
object ->ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object ->ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

Klient PictBridge ma teraz zadanie drukowania do wykonania i pobierze bloki obrazu z aplikacji za pośrednictwem wywołania zwrotnego zdefiniowanego w tym polu.

```C
jobinfo ->ux_pictbridge_jobinfo_object_data_read
```

Prototyp tej funkcji jest definiowany w następujący sposób.

## <a name="ux_pictbridge_jobinfo_object_data_read"></a>ux_pictbridge_jobinfo_object_data_read

Kopiowanie bloku danych z obszaru użytkownika do drukowania.

### <a name="prototype"></a>Prototype

```C
UINT **ux_pictbridge_jobinfo_object_data_read(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy klient DPS musi pobrać blok danych w celu drukowania do docelowej drukarki PictBridge.

### <a name="parameters"></a>Parametry

- **PictBridge**: wskaźnik do wystąpienia klasy PictBridge.
- **object_buffer**: wskaźnik do buforu obiektów
- **object_offset**: gdzie zaczynamy odczytywanie bloku danych
- **object_length**: długość do zwrócenia
- **actual_length**: zwrócono rzeczywistą Długość

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0X00) ta operacja zakończyła się pomyślnie.
- **UX_ERROR**: (0x01) aplikacja nie może pobrać danych.

### <a name="example"></a>Przykład

```C
/* Copy the object data. */

UINT ux_demo_object_data_copy(UX_PICTBRIDGE *pictbridge,UCHAR *object_buffer,
    ULONG object_offset, ULONG object_length, ULONG *actual_length)
{
    /* Copy the demanded object data portion. */
    ux_utility_memory_copy(object_buffer, image + object_offset,
        object_length);

    /* Update the actual length. */
    *actual_length = object_length;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="pictbridge-host-implementation"></a>Implementacja hosta PictBridge

Implementacja hosta PictBridge różni się od klienta.

Pierwsza czynność do wykonania w środowisku hosta PictBridge polega na zarejestrowaniu klasy Pima, jak pokazano na poniższym przykładzie:

```C
status = ux_host_stack_class_register(ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

Ta klasa jest ogólną warstwą PTP znajdującą się między stosem hosta USB a warstwą PictBridge.

Następnym krokiem jest zainicjowanie wartości domyślnych PictBridge dla usług drukowania w następujący sposób.

| Pole PictBridge       | Wartość                                  |
|------------------------|----------------------------------------|
| DpsVersion [0]          | 0x00010000                             |
| DpsVersion [1]          | 0x00010001                             |
| DpsVersion [2]          | 0x00000000                             |
| VendorSpecificVersion  | 0x00010000                             |
| PrintServiceAvailable  | 0x30010000                             |
| Jakość [0]           | UX_PICTBRIDGE_QUALITIES_DEFAULT        |
| Jakość [1]           | UX_PICTBRIDGE_QUALITIES_NORMAL         |
| Jakość [2]           | UX_PICTBRIDGE_QUALITIES_DRAFT          |
| Jakość [3]           | UX_PICTBRIDGE_QUALITIES_FINE           |
| Wartości PaperSize [0]          | UX_PICTBRIDGE_PAPER_SIZES_DEFAULT      |
| Moje PaperSize [1]          | UX_PICTBRIDGE_PAPER_SIZES_4IX6I        |
| Moje PaperSize [2]          | UX_PICTBRIDGE_PAPER_SIZES_L            |
| Moje PaperSize [3]          | UX_PICTBRIDGE_PAPER_SIZES_2L           |
| Moje PaperSize [4]          | UX_PICTBRIDGE_PAPER_SIZES_LETTER       |
| PaperTypes [0]          | UX_PICTBRIDGE_PAPER_TYPES_DEFAULT      |
| PaperTypes [1]          | UX_PICTBRIDGE_PAPER_TYPES_PLAIN        |
| PaperTypes [2]          | UX_PICTBRIDGE_PAPER_TYPES_PHOTO        |
| Typ_plikus [0]           | UX_PICTBRIDGE_FILE_TYPES_DEFAULT       |
| Typ_plikus [1]           | UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG     |
| Typ_plikus [2]           | UX_PICTBRIDGE_FILE_TYPES_JFIF          |
| Typ_plikus [3]           | UX_PICTBRIDGE_FILE_TYPES_DPOF          |
| DatePrints [0]          | UX_PICTBRIDGE_DATE_PRINTS_DEFAULT      |
| DatePrints [1]          | UX_PICTBRIDGE_DATE_PRINTS_OFF          |
| DatePrints [2]          | UX_PICTBRIDGE_DATE_PRINTS_ON           |
| FileNamePrints [0]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT |
| FileNamePrints [1]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF     |
| FileNamePrints [2]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_ON      |
| ImageOptimizes [0]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT  |
| ImageOptimizes [1]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF      |
| ImageOptimizes [2]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON       |
| Układy [0]             | UX_PICTBRIDGE_LAYOUTS_DEFAULT          |
| Układy [1]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER      |
| Układy [2]             | UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT      |
| Układy [3]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS  |
| FixedSizes [0]          | UX_PICTBRIDGE_FIXED_SIZE_DEFAULT       |
| FixedSizes [1]          | UX_PICTBRIDGE_FIXED_SIZE_35IX5I        |
| FixedSizes [2]          | UX_PICTBRIDGE_FIXED_SIZE_4IX6I         |
| FixedSizes [3]          | UX_PICTBRIDGE_FIXED_SIZE_5IX7I         |
| FixedSizes [4]          | UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM      |
| FixedSizes [5]          | UX_PICTBRIDGE_FIXED_SIZE_LETTER        |
| FixedSizes [6]          | UX_PICTBRIDGE_FIXED_SIZE_A4            |
| Przycinanie [0]           | UX_PICTBRIDGE_CROPPINGS_DEFAULT        |
| Przycinanie [1]           | UX_PICTBRIDGE_CROPPINGS_OFF            |
| Przycinanie [2]           | UX_PICTBRIDGE_CROPPINGS_ON             |

Komputer stanu hosta DPS zostanie ustawiony na wartość bezczynną i będzie gotowy do zaakceptowania nowego zadania drukowania.

Część hosta PictBridge może teraz zostać uruchomiona, jak pokazano w poniższym przykładzie.

```C
/* Activate the pictbridge dpshost. */

status = ux_pictbridge_dpshost_start(&pictbridge, pima);
if (status != UX_SUCCESS)
    return;
```

Funkcja hosta PictBridge wymaga wywołania zwrotnego, gdy dane są gotowe do wydrukowania. W tym celu należy przekazać wskaźnik funkcji do struktury hosta PictBridge w następujący sposób.

```C
/* Set a callback when an object is being received. */

pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

Ta funkcja ma następujące właściwości:

## <a name="ux_pictbridge_application_object_data_write"></a>ux_pictbridge_application_object_data_write

Zapisywanie bloku danych do drukowania.

### <a name="prototype"></a>Prototype

```C
UINT **ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a>Opis

Ta funkcja jest wywoływana, gdy serwer DPS musi pobrać blok danych z klienta usługi DPS, aby drukować na drukarce lokalnej.

### <a name="parameters"></a>Parametry

- **PictBridge**: wskaźnik do wystąpienia klasy PictBridge.
- **object_buffer**: wskaźnik do buforu obiektów
- **object_offset**: gdzie zaczynamy odczytywanie bloku danych
- **total_length**: cała długość obiektu
- **Długość**: długość tego buforu

### <a name="return-value"></a>Wartość zwracana

- **UX_SUCCESS**: (0X00) ta operacja zakończyła się pomyślnie.
- **UX_ERROR**: (0x01) aplikacja nie mogła wydrukować danych.

### <a name="example"></a>Przykład

```C
/* Copy the object data. */

UINT tx_demo_object_data_write(UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer, ULONG offset, ULONG total_length, ULONG length);
{
    UINT status;

    /* Send the data to the local printer. */
    status = local_printer_data_send(object_buffer, length);

    /* We have printed the requested data. Return status. */
    return(status);
}
```
