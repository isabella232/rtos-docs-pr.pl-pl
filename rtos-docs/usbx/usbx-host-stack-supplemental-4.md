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
# <a name="chapter-4-usbx-pictbridge-implementation"></a><span data-ttu-id="e20d4-104">Rozdział 4: implementacja USBX PictBridge</span><span class="sxs-lookup"><span data-stu-id="e20d4-104">Chapter 4: USBX Pictbridge implementation</span></span>

<span data-ttu-id="e20d4-105">UBSX obsługuje pełną implementację technologii PictBridge zarówno na hoście, jak i urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="e20d4-105">UBSX supports the full Pictbridge implementation both on the host and the device.</span></span> <span data-ttu-id="e20d4-106">PictBridge znajduje się na szczycie klasy USBX PIMA po obu stronach.</span><span class="sxs-lookup"><span data-stu-id="e20d4-106">Pictbridge sits on top of USBX PIMA class on both sides.</span></span> 

<span data-ttu-id="e20d4-107">Standardy PictBridge umożliwiają połączenie cyfrowego aparatu fotograficznego lub inteligentnego telefonu bezpośrednio z drukarką bez komputera, co umożliwia bezpośrednie drukowanie na określonych drukarkach z obsługą technologii PictBridge.</span><span class="sxs-lookup"><span data-stu-id="e20d4-107">The PictBridge standards allows the connection of a digital still camera or a smart phone directly to a printer without a PC, enabling direct printing to certain Pictbridge aware printers.</span></span>

<span data-ttu-id="e20d4-108">Gdy do drukarki jest podłączony aparat lub telefon, drukarka jest hostem USB, a aparat jest urządzeniem USB.</span><span class="sxs-lookup"><span data-stu-id="e20d4-108">When a camera or phone is connected to a printer, the printer is the USB host and the camera is the USB device.</span></span> <span data-ttu-id="e20d4-109">Jednak w przypadku technologii PictBridge aparat będzie wyświetlany jako host, a polecenia są sterowane przez aparat.</span><span class="sxs-lookup"><span data-stu-id="e20d4-109">However, with Pictbridge, the camera will appear as being the host and commands are driven from the camera.</span></span> <span data-ttu-id="e20d4-110">Aparat jest serwerem magazynu, drukarką klienta magazynu.</span><span class="sxs-lookup"><span data-stu-id="e20d4-110">The camera is the storage server, the printer the storage client.</span></span> <span data-ttu-id="e20d4-111">Aparat jest klientem drukowania, a drukarka jest oczywiście serwerem wydruku.</span><span class="sxs-lookup"><span data-stu-id="e20d4-111">The camera is the print client and the printer is, of course, the print server.</span></span>

<span data-ttu-id="e20d4-112">PictBridge korzysta z portów USB jako warstwy transportowej, ale korzysta z protokołu PTP (Picture Transfering Protocol) dla protokołu komunikacyjnego.</span><span class="sxs-lookup"><span data-stu-id="e20d4-112">Pictbridge uses USB as a transport layer but relies on PTP (Picture Transfer Protocol) for the communication protocol.</span></span>

<span data-ttu-id="e20d4-113">Poniżej znajduje się Diagram poleceń/odpowiedzi między klientem DPS a serwerem DPS w przypadku wystąpienia zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="e20d4-113">The following is a diagram of the commands/responses between the DPS client and the DPS server when a print job occurs.</span></span>

![Diagram poleceń/odpowiedzi między klientem D P S a serwerem D P S w przypadku wystąpienia zadania drukowania.](./media/usbx-host-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a><span data-ttu-id="e20d4-115">Implementacja klienta PictBridge</span><span class="sxs-lookup"><span data-stu-id="e20d4-115">Pictbridge client implementation</span></span>

<span data-ttu-id="e20d4-116">Aby program PictBridge na kliencie wymagał pierwszego uruchomienia stosu urządzenia USBX oraz klasy PIMA.</span><span class="sxs-lookup"><span data-stu-id="e20d4-116">The Pictbridge on the client requires the USBX device stack and the PIMA class to be running first.</span></span>

<span data-ttu-id="e20d4-117">Platforma urządzeń opisuje klasę PIMA w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e20d4-117">A device framework describes the PIMA class in the following way.</span></span>

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

<span data-ttu-id="e20d4-118">Klasa Pima używa pola ID 0x06 i ma jego podklasę na wartość 0x01 dla obrazu wciąż, a protokół to 0x01 dla PIMA 15740.</span><span class="sxs-lookup"><span data-stu-id="e20d4-118">The Pima class is using the ID field 0x06 and has its subclass is 0x01 for Still Image and the protocol is 0x01 for PIMA 15740.</span></span>

<span data-ttu-id="e20d4-119">3 punkty końcowe są zdefiniowane w tej klasie, 2 zbiorczo do wysyłania/otrzymywania danych i jednego przerwania dla zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e20d4-119">3 endpoints are defined in this class, 2 bulks for sending/receiving data and one interrupt for events.</span></span>

<span data-ttu-id="e20d4-120">W przeciwieństwie do innych implementacji urządzeń USBX, aplikacja PictBridge nie musi definiować samej klasy.</span><span class="sxs-lookup"><span data-stu-id="e20d4-120">Unlike other USBX device implementations, the Pictbridge application does not need to define a class itself.</span></span> <span data-ttu-id="e20d4-121">Zamiast wywołuje funkcję ***ux_pictbridge_dpsclient_start***.</span><span class="sxs-lookup"><span data-stu-id="e20d4-121">Rather it invokes the function ***ux_pictbridge_dpsclient_start***.</span></span> <span data-ttu-id="e20d4-122">Poniżej znajduje się przykład:</span><span class="sxs-lookup"><span data-stu-id="e20d4-122">An example is below:</span></span>

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

<span data-ttu-id="e20d4-123">Parametry przesłane do klienta PictBridge są następujące:</span><span class="sxs-lookup"><span data-stu-id="e20d4-123">The parameters passed to the pictbridge client are as follows:</span></span>

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no,
    : String of serial number pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version pictbridge.ux_pictbridge_dpslocal. ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

<span data-ttu-id="e20d4-124">Następnym krokiem jest zasynchronizowanie urządzenia i hosta oraz gotowość do wymiany informacji.</span><span class="sxs-lookup"><span data-stu-id="e20d4-124">The next step is for the device and the host to synchronize and be ready to exchange information.</span></span>

<span data-ttu-id="e20d4-125">Jest to realizowane przez oczekiwanie na flagę zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e20d4-125">This is done by waiting on an event flag as follows:</span></span>

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get
    (&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR, &actual_flags,
    UX_PICTBRIDGE_EVENT_TIMEOUT);
```

<span data-ttu-id="e20d4-126">Jeśli stan komputera jest w stanie **DISCOVERY_COMPLETE** , Strona aparatu (klient DPS) będzie zbierać informacje dotyczące drukarki i jej możliwości.</span><span class="sxs-lookup"><span data-stu-id="e20d4-126">If the state machine is in the **DISCOVERY_COMPLETE** state, the camera side (the DPS client) will gather information regarding the printer and its capabilities.</span></span>

<span data-ttu-id="e20d4-127">Jeśli klient DPS jest gotowy do zaakceptowania zadania drukowania, jego stan zostanie ustawiony na **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="e20d4-127">If the DPS client is ready to accept a print job, its status will be set to **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span></span> <span data-ttu-id="e20d4-128">Można to sprawdzić poniżej:</span><span class="sxs-lookup"><span data-stu-id="e20d4-128">It can be checked below:</span></span>

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)

    /* We can print something … */
```

<span data-ttu-id="e20d4-129">Kolejne przykłady dla deskryptorów joib drukowania muszą zostać wypełnione w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e20d4-129">Next some print joib descriptors need to be filled as follows:</span></span>

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

<span data-ttu-id="e20d4-130">Klient PictBridge ma teraz zadanie drukowania do wykonania i pobierze bloki obrazu z aplikacji za pośrednictwem wywołania zwrotnego zdefiniowanego w tym polu.</span><span class="sxs-lookup"><span data-stu-id="e20d4-130">The Pictbridge client now has a print job to do and will fetch the image blocks at a time from the application through the callback defined in the field.</span></span>

```C
jobinfo ->ux_pictbridge_jobinfo_object_data_read
```

<span data-ttu-id="e20d4-131">Prototyp tej funkcji jest definiowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e20d4-131">The prototype of that function is defined as follows.</span></span>

## <a name="ux_pictbridge_jobinfo_object_data_read"></a><span data-ttu-id="e20d4-132">ux_pictbridge_jobinfo_object_data_read</span><span class="sxs-lookup"><span data-stu-id="e20d4-132">ux_pictbridge_jobinfo_object_data_read</span></span>

<span data-ttu-id="e20d4-133">Kopiowanie bloku danych z obszaru użytkownika do drukowania.</span><span class="sxs-lookup"><span data-stu-id="e20d4-133">Copying a block of data from user space for printing.</span></span>

### <a name="prototype"></a><span data-ttu-id="e20d4-134">Prototype</span><span class="sxs-lookup"><span data-stu-id="e20d4-134">Prototype</span></span>

```C
UINT **ux_pictbridge_jobinfo_object_data_read(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="e20d4-135">Opis</span><span class="sxs-lookup"><span data-stu-id="e20d4-135">Description</span></span>

<span data-ttu-id="e20d4-136">Ta funkcja jest wywoływana, gdy klient DPS musi pobrać blok danych w celu drukowania do docelowej drukarki PictBridge.</span><span class="sxs-lookup"><span data-stu-id="e20d4-136">This function is called when the DPS client needs to retrieve a data block to print to the target Pictbridge printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="e20d4-137">Parametry</span><span class="sxs-lookup"><span data-stu-id="e20d4-137">Parameters</span></span>

- <span data-ttu-id="e20d4-138">**PictBridge**: wskaźnik do wystąpienia klasy PictBridge.</span><span class="sxs-lookup"><span data-stu-id="e20d4-138">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="e20d4-139">**object_buffer**: wskaźnik do buforu obiektów</span><span class="sxs-lookup"><span data-stu-id="e20d4-139">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="e20d4-140">**object_offset**: gdzie zaczynamy odczytywanie bloku danych</span><span class="sxs-lookup"><span data-stu-id="e20d4-140">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="e20d4-141">**object_length**: długość do zwrócenia</span><span class="sxs-lookup"><span data-stu-id="e20d4-141">**object_length**: Length to be returned</span></span>
- <span data-ttu-id="e20d4-142">**actual_length**: zwrócono rzeczywistą Długość</span><span class="sxs-lookup"><span data-stu-id="e20d4-142">**actual_length**: Actual length returned</span></span>

### <a name="return-value"></a><span data-ttu-id="e20d4-143">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e20d4-143">Return Value</span></span>

- <span data-ttu-id="e20d4-144">**UX_SUCCESS**: (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e20d4-144">**UX_SUCCESS**: (0x00) This operation was successful.</span></span>
- <span data-ttu-id="e20d4-145">**UX_ERROR**: (0x01) aplikacja nie może pobrać danych.</span><span class="sxs-lookup"><span data-stu-id="e20d4-145">**UX_ERROR**: (0x01) The application could not retrieve data.</span></span>

### <a name="example"></a><span data-ttu-id="e20d4-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="e20d4-146">Example</span></span>

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

## <a name="pictbridge-host-implementation"></a><span data-ttu-id="e20d4-147">Implementacja hosta PictBridge</span><span class="sxs-lookup"><span data-stu-id="e20d4-147">Pictbridge host implementation</span></span>

<span data-ttu-id="e20d4-148">Implementacja hosta PictBridge różni się od klienta.</span><span class="sxs-lookup"><span data-stu-id="e20d4-148">The host implementation of Pictbridge is different from the client.</span></span>

<span data-ttu-id="e20d4-149">Pierwsza czynność do wykonania w środowisku hosta PictBridge polega na zarejestrowaniu klasy Pima, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e20d4-149">The first thing to do in a Pictbridge host environment is to register the Pima class as the example below shows:</span></span>

```C
status = ux_host_stack_class_register(ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="e20d4-150">Ta klasa jest ogólną warstwą PTP znajdującą się między stosem hosta USB a warstwą PictBridge.</span><span class="sxs-lookup"><span data-stu-id="e20d4-150">This class is the generic PTP layer sitting between the USB host stack and the Pictbridge layer.</span></span>

<span data-ttu-id="e20d4-151">Następnym krokiem jest zainicjowanie wartości domyślnych PictBridge dla usług drukowania w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e20d4-151">The next step is to initialize the Pictbridge default values for print services as follows.</span></span>

| <span data-ttu-id="e20d4-152">Pole PictBridge</span><span class="sxs-lookup"><span data-stu-id="e20d4-152">Pictbridge field</span></span>       | <span data-ttu-id="e20d4-153">Wartość</span><span class="sxs-lookup"><span data-stu-id="e20d4-153">Value</span></span>                                  |
|------------------------|----------------------------------------|
| <span data-ttu-id="e20d4-154">DpsVersion [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-154">DpsVersion[0]</span></span>          | <span data-ttu-id="e20d4-155">0x00010000</span><span class="sxs-lookup"><span data-stu-id="e20d4-155">0x00010000</span></span>                             |
| <span data-ttu-id="e20d4-156">DpsVersion [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-156">DpsVersion[1]</span></span>          | <span data-ttu-id="e20d4-157">0x00010001</span><span class="sxs-lookup"><span data-stu-id="e20d4-157">0x00010001</span></span>                             |
| <span data-ttu-id="e20d4-158">DpsVersion [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-158">DpsVersion[2]</span></span>          | <span data-ttu-id="e20d4-159">0x00000000</span><span class="sxs-lookup"><span data-stu-id="e20d4-159">0x00000000</span></span>                             |
| <span data-ttu-id="e20d4-160">VendorSpecificVersion</span><span class="sxs-lookup"><span data-stu-id="e20d4-160">VendorSpecificVersion</span></span>  | <span data-ttu-id="e20d4-161">0x00010000</span><span class="sxs-lookup"><span data-stu-id="e20d4-161">0x00010000</span></span>                             |
| <span data-ttu-id="e20d4-162">PrintServiceAvailable</span><span class="sxs-lookup"><span data-stu-id="e20d4-162">PrintServiceAvailable</span></span>  | <span data-ttu-id="e20d4-163">0x30010000</span><span class="sxs-lookup"><span data-stu-id="e20d4-163">0x30010000</span></span>                             |
| <span data-ttu-id="e20d4-164">Jakość [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-164">Qualities[0]</span></span>           | <span data-ttu-id="e20d4-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e20d4-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span></span>        |
| <span data-ttu-id="e20d4-166">Jakość [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-166">Qualities[1]</span></span>           | <span data-ttu-id="e20d4-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span><span class="sxs-lookup"><span data-stu-id="e20d4-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span></span>         |
| <span data-ttu-id="e20d4-168">Jakość [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-168">Qualities[2]</span></span>           | <span data-ttu-id="e20d4-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span><span class="sxs-lookup"><span data-stu-id="e20d4-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span></span>          |
| <span data-ttu-id="e20d4-170">Jakość [3]</span><span class="sxs-lookup"><span data-stu-id="e20d4-170">Qualities[3]</span></span>           | <span data-ttu-id="e20d4-171">UX_PICTBRIDGE_QUALITIES_FINE</span><span class="sxs-lookup"><span data-stu-id="e20d4-171">UX_PICTBRIDGE_QUALITIES_FINE</span></span>           |
| <span data-ttu-id="e20d4-172">Wartości PaperSize [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-172">PaperSizes[0]</span></span>          | <span data-ttu-id="e20d4-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e20d4-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span></span>      |
| <span data-ttu-id="e20d4-174">Moje PaperSize [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-174">PaperSizes[1]</span></span>          | <span data-ttu-id="e20d4-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span><span class="sxs-lookup"><span data-stu-id="e20d4-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span></span>        |
| <span data-ttu-id="e20d4-176">Moje PaperSize [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-176">PaperSizes[2]</span></span>          | <span data-ttu-id="e20d4-177">UX_PICTBRIDGE_PAPER_SIZES_L</span><span class="sxs-lookup"><span data-stu-id="e20d4-177">UX_PICTBRIDGE_PAPER_SIZES_L</span></span>            |
| <span data-ttu-id="e20d4-178">Moje PaperSize [3]</span><span class="sxs-lookup"><span data-stu-id="e20d4-178">PaperSizes[3]</span></span>          | <span data-ttu-id="e20d4-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span><span class="sxs-lookup"><span data-stu-id="e20d4-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span></span>           |
| <span data-ttu-id="e20d4-180">Moje PaperSize [4]</span><span class="sxs-lookup"><span data-stu-id="e20d4-180">PaperSizes[4]</span></span>          | <span data-ttu-id="e20d4-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span><span class="sxs-lookup"><span data-stu-id="e20d4-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span></span>       |
| <span data-ttu-id="e20d4-182">PaperTypes [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-182">PaperTypes[0]</span></span>          | <span data-ttu-id="e20d4-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e20d4-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span></span>      |
| <span data-ttu-id="e20d4-184">PaperTypes [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-184">PaperTypes[1]</span></span>          | <span data-ttu-id="e20d4-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span><span class="sxs-lookup"><span data-stu-id="e20d4-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span></span>        |
| <span data-ttu-id="e20d4-186">PaperTypes [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-186">PaperTypes[2]</span></span>          | <span data-ttu-id="e20d4-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span><span class="sxs-lookup"><span data-stu-id="e20d4-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span></span>        |
| <span data-ttu-id="e20d4-188">Typ_plikus [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-188">FileTypes[0]</span></span>           | <span data-ttu-id="e20d4-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e20d4-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span></span>       |
| <span data-ttu-id="e20d4-190">Typ_plikus [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-190">FileTypes[1]</span></span>           | <span data-ttu-id="e20d4-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="e20d4-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span></span>     |
| <span data-ttu-id="e20d4-192">Typ_plikus [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-192">FileTypes[2]</span></span>           | <span data-ttu-id="e20d4-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span><span class="sxs-lookup"><span data-stu-id="e20d4-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span></span>          |
| <span data-ttu-id="e20d4-194">Typ_plikus [3]</span><span class="sxs-lookup"><span data-stu-id="e20d4-194">FileTypes[3]</span></span>           | <span data-ttu-id="e20d4-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span><span class="sxs-lookup"><span data-stu-id="e20d4-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span></span>          |
| <span data-ttu-id="e20d4-196">DatePrints [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-196">DatePrints[0]</span></span>          | <span data-ttu-id="e20d4-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e20d4-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span></span>      |
| <span data-ttu-id="e20d4-198">DatePrints [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-198">DatePrints[1]</span></span>          | <span data-ttu-id="e20d4-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="e20d4-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span></span>          |
| <span data-ttu-id="e20d4-200">DatePrints [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-200">DatePrints[2]</span></span>          | <span data-ttu-id="e20d4-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="e20d4-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span></span>           |
| <span data-ttu-id="e20d4-202">FileNamePrints [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-202">FileNamePrints[0]</span></span>      | <span data-ttu-id="e20d4-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e20d4-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span></span> |
| <span data-ttu-id="e20d4-204">FileNamePrints [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-204">FileNamePrints[1]</span></span>      | <span data-ttu-id="e20d4-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="e20d4-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span></span>     |
| <span data-ttu-id="e20d4-206">FileNamePrints [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-206">FileNamePrints[2]</span></span>      | <span data-ttu-id="e20d4-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="e20d4-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span></span>      |
| <span data-ttu-id="e20d4-208">ImageOptimizes [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-208">ImageOptimizes[0]</span></span>      | <span data-ttu-id="e20d4-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e20d4-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span></span>  |
| <span data-ttu-id="e20d4-210">ImageOptimizes [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-210">ImageOptimizes[1]</span></span>      | <span data-ttu-id="e20d4-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span><span class="sxs-lookup"><span data-stu-id="e20d4-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span></span>      |
| <span data-ttu-id="e20d4-212">ImageOptimizes [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-212">ImageOptimizes[2]</span></span>      | <span data-ttu-id="e20d4-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span><span class="sxs-lookup"><span data-stu-id="e20d4-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span></span>       |
| <span data-ttu-id="e20d4-214">Układy [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-214">Layouts[0]</span></span>             | <span data-ttu-id="e20d4-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e20d4-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span></span>          |
| <span data-ttu-id="e20d4-216">Układy [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-216">Layouts[1]</span></span>             | <span data-ttu-id="e20d4-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span><span class="sxs-lookup"><span data-stu-id="e20d4-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span></span>      |
| <span data-ttu-id="e20d4-218">Układy [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-218">Layouts[2]</span></span>             | <span data-ttu-id="e20d4-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span><span class="sxs-lookup"><span data-stu-id="e20d4-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span></span>      |
| <span data-ttu-id="e20d4-220">Układy [3]</span><span class="sxs-lookup"><span data-stu-id="e20d4-220">Layouts[3]</span></span>             | <span data-ttu-id="e20d4-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span><span class="sxs-lookup"><span data-stu-id="e20d4-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span></span>  |
| <span data-ttu-id="e20d4-222">FixedSizes [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-222">FixedSizes[0]</span></span>          | <span data-ttu-id="e20d4-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e20d4-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span></span>       |
| <span data-ttu-id="e20d4-224">FixedSizes [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-224">FixedSizes[1]</span></span>          | <span data-ttu-id="e20d4-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span><span class="sxs-lookup"><span data-stu-id="e20d4-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span></span>        |
| <span data-ttu-id="e20d4-226">FixedSizes [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-226">FixedSizes[2]</span></span>          | <span data-ttu-id="e20d4-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span><span class="sxs-lookup"><span data-stu-id="e20d4-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span></span>         |
| <span data-ttu-id="e20d4-228">FixedSizes [3]</span><span class="sxs-lookup"><span data-stu-id="e20d4-228">FixedSizes[3]</span></span>          | <span data-ttu-id="e20d4-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span><span class="sxs-lookup"><span data-stu-id="e20d4-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span></span>         |
| <span data-ttu-id="e20d4-230">FixedSizes [4]</span><span class="sxs-lookup"><span data-stu-id="e20d4-230">FixedSizes[4]</span></span>          | <span data-ttu-id="e20d4-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span><span class="sxs-lookup"><span data-stu-id="e20d4-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span></span>      |
| <span data-ttu-id="e20d4-232">FixedSizes [5]</span><span class="sxs-lookup"><span data-stu-id="e20d4-232">FixedSizes[5]</span></span>          | <span data-ttu-id="e20d4-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span><span class="sxs-lookup"><span data-stu-id="e20d4-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span></span>        |
| <span data-ttu-id="e20d4-234">FixedSizes [6]</span><span class="sxs-lookup"><span data-stu-id="e20d4-234">FixedSizes[6]</span></span>          | <span data-ttu-id="e20d4-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span><span class="sxs-lookup"><span data-stu-id="e20d4-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span></span>            |
| <span data-ttu-id="e20d4-236">Przycinanie [0]</span><span class="sxs-lookup"><span data-stu-id="e20d4-236">Croppings[0]</span></span>           | <span data-ttu-id="e20d4-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e20d4-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span></span>        |
| <span data-ttu-id="e20d4-238">Przycinanie [1]</span><span class="sxs-lookup"><span data-stu-id="e20d4-238">Croppings[1]</span></span>           | <span data-ttu-id="e20d4-239">UX_PICTBRIDGE_CROPPINGS_OFF</span><span class="sxs-lookup"><span data-stu-id="e20d4-239">UX_PICTBRIDGE_CROPPINGS_OFF</span></span>            |
| <span data-ttu-id="e20d4-240">Przycinanie [2]</span><span class="sxs-lookup"><span data-stu-id="e20d4-240">Croppings[2]</span></span>           | <span data-ttu-id="e20d4-241">UX_PICTBRIDGE_CROPPINGS_ON</span><span class="sxs-lookup"><span data-stu-id="e20d4-241">UX_PICTBRIDGE_CROPPINGS_ON</span></span>             |

<span data-ttu-id="e20d4-242">Komputer stanu hosta DPS zostanie ustawiony na wartość bezczynną i będzie gotowy do zaakceptowania nowego zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="e20d4-242">The state machine of the DPS host will be set to Idle and ready to accept a new print job.</span></span>

<span data-ttu-id="e20d4-243">Część hosta PictBridge może teraz zostać uruchomiona, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e20d4-243">The host portion of Pictbridge can now be started as the example below shows.</span></span>

```C
/* Activate the pictbridge dpshost. */

status = ux_pictbridge_dpshost_start(&pictbridge, pima);
if (status != UX_SUCCESS)
    return;
```

<span data-ttu-id="e20d4-244">Funkcja hosta PictBridge wymaga wywołania zwrotnego, gdy dane są gotowe do wydrukowania.</span><span class="sxs-lookup"><span data-stu-id="e20d4-244">The Pictbridge host function requires a callback when data is ready to be printed.</span></span> <span data-ttu-id="e20d4-245">W tym celu należy przekazać wskaźnik funkcji do struktury hosta PictBridge w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e20d4-245">This is accomplished by passing a function pointer in the pictbridge host structure as follows.</span></span>

```C
/* Set a callback when an object is being received. */

pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

<span data-ttu-id="e20d4-246">Ta funkcja ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e20d4-246">This function has the following properties:</span></span>

## <a name="ux_pictbridge_application_object_data_write"></a><span data-ttu-id="e20d4-247">ux_pictbridge_application_object_data_write</span><span class="sxs-lookup"><span data-stu-id="e20d4-247">ux_pictbridge_application_object_data_write</span></span>

<span data-ttu-id="e20d4-248">Zapisywanie bloku danych do drukowania.</span><span class="sxs-lookup"><span data-stu-id="e20d4-248">Writing a block of data for printing.</span></span>

### <a name="prototype"></a><span data-ttu-id="e20d4-249">Prototype</span><span class="sxs-lookup"><span data-stu-id="e20d4-249">Prototype</span></span>

```C
UINT **ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="e20d4-250">Opis</span><span class="sxs-lookup"><span data-stu-id="e20d4-250">Description</span></span>

<span data-ttu-id="e20d4-251">Ta funkcja jest wywoływana, gdy serwer DPS musi pobrać blok danych z klienta usługi DPS, aby drukować na drukarce lokalnej.</span><span class="sxs-lookup"><span data-stu-id="e20d4-251">This function is called when the DPS server needs to retrieve a data block from the DPS client to print to the local printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="e20d4-252">Parametry</span><span class="sxs-lookup"><span data-stu-id="e20d4-252">Parameters</span></span>

- <span data-ttu-id="e20d4-253">**PictBridge**: wskaźnik do wystąpienia klasy PictBridge.</span><span class="sxs-lookup"><span data-stu-id="e20d4-253">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="e20d4-254">**object_buffer**: wskaźnik do buforu obiektów</span><span class="sxs-lookup"><span data-stu-id="e20d4-254">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="e20d4-255">**object_offset**: gdzie zaczynamy odczytywanie bloku danych</span><span class="sxs-lookup"><span data-stu-id="e20d4-255">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="e20d4-256">**total_length**: cała długość obiektu</span><span class="sxs-lookup"><span data-stu-id="e20d4-256">**total_length**: Entire length of object</span></span>
- <span data-ttu-id="e20d4-257">**Długość**: długość tego buforu</span><span class="sxs-lookup"><span data-stu-id="e20d4-257">**length**: Length of this buffer</span></span>

### <a name="return-value"></a><span data-ttu-id="e20d4-258">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e20d4-258">Return Value</span></span>

- <span data-ttu-id="e20d4-259">**UX_SUCCESS**: (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e20d4-259">**UX_SUCCESS**: (0x00) This operation was successful.</span></span>
- <span data-ttu-id="e20d4-260">**UX_ERROR**: (0x01) aplikacja nie mogła wydrukować danych.</span><span class="sxs-lookup"><span data-stu-id="e20d4-260">**UX_ERROR**: (0x01) The application could not print data.</span></span>

### <a name="example"></a><span data-ttu-id="e20d4-261">Przykład</span><span class="sxs-lookup"><span data-stu-id="e20d4-261">Example</span></span>

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
