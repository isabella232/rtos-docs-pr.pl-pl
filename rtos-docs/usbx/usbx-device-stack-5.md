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
# <a name="chapter-5---usbx-device-class-considerations"></a><span data-ttu-id="195be-103">Rozdział 5 — zagadnienia dotyczące klas urządzeń USBX</span><span class="sxs-lookup"><span data-stu-id="195be-103">Chapter 5 - USBX Device Class Considerations</span></span>

## <a name="device-class-registration"></a><span data-ttu-id="195be-104">Rejestracja klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="195be-104">Device Class registration</span></span>

<span data-ttu-id="195be-105">Każda klasa urządzeń jest zgodna z tą samą zasadą w przypadku rejestracji.</span><span class="sxs-lookup"><span data-stu-id="195be-105">Each device class follows the same principle for registration.</span></span> <span data-ttu-id="195be-106">Struktura zawierająca określone parametry klasy jest przenoszona do funkcji inicjowania klasy.</span><span class="sxs-lookup"><span data-stu-id="195be-106">A structure containing specific class parameters is passed to the class initialize function.</span></span>

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

<span data-ttu-id="195be-107">Każda klasa może zarejestrować, opcjonalnie, funkcję wywołania zwrotnego, gdy wystąpienie klasy zostanie aktywowane.</span><span class="sxs-lookup"><span data-stu-id="195be-107">Each class can register, optionally, a callback function when a instance of the class gets activated.</span></span> <span data-ttu-id="195be-108">Wywołanie zwrotne jest następnie wywoływane przez stos urządzeń w celu powiadomienia aplikacji o utworzeniu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="195be-108">The callback is then called by the device stack to inform the application that an instance was created.</span></span>

<span data-ttu-id="195be-109">Aplikacja będzie miała w swojej treści 2 funkcje do aktywacji i dezaktywacji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="195be-109">The application would have in its body the 2 functions for activation and deactivation, as shown in the following example.</span></span>

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

<span data-ttu-id="195be-110">Nie zaleca się wykonywania żadnych czynności w ramach tych funkcji, ale w celu znają wystąpienia klasy i zsynchronizowania z pozostałą częścią aplikacji.</span><span class="sxs-lookup"><span data-stu-id="195be-110">It is not recommended to do anything within these functions but to memorize the instance of the class and synchronize with the rest of the application.</span></span>

## <a name="usb-device-storage-class"></a><span data-ttu-id="195be-111">Klasa magazynu urządzenia USB</span><span class="sxs-lookup"><span data-stu-id="195be-111">USB Device Storage Class</span></span>

<span data-ttu-id="195be-112">Klasa magazynu urządzenia USB pozwala na udostępnienie urządzenia magazynującego w systemie jako widocznego dla hosta USB.</span><span class="sxs-lookup"><span data-stu-id="195be-112">The USB device storage class allows for a storage device embedded in the system to be made visible to a USB host.</span></span>

<span data-ttu-id="195be-113">Klasa magazynu urządzeń USB nie udostępnia rozwiązania do magazynowania.</span><span class="sxs-lookup"><span data-stu-id="195be-113">The USB device storage class does not by itself provide a storage solution.</span></span> <span data-ttu-id="195be-114">Tylko akceptuje i interpretuje żądania SCSI pochodzące z hosta.</span><span class="sxs-lookup"><span data-stu-id="195be-114">It merely accepts and interprets SCSI requests coming from the host.</span></span> <span data-ttu-id="195be-115">Gdy jeden z tych żądań jest poleceniem odczytu lub zapisu, wywoła wstępnie zdefiniowane wywołanie z powrotem do obsługi rzeczywistego urządzenia magazynującego, np. sterownika urządzenia usługi ATA lub sterownika urządzenia flash.</span><span class="sxs-lookup"><span data-stu-id="195be-115">When one of these requests is a read or a write command, it will invoke a pre-defined call back to a real storage device handler, such as an ATA device driver or a Flash device driver.</span></span>

<span data-ttu-id="195be-116">Podczas inicjowania klasy magazynu urządzeń struktura wskaźnika jest przyznany do klasy, która zawiera wszystkie wymagane informacje.</span><span class="sxs-lookup"><span data-stu-id="195be-116">When initializing the device storage class, a pointer structure is given to the class that contains all the information necessary.</span></span> <span data-ttu-id="195be-117">Poniżej znajduje się przykład.</span><span class="sxs-lookup"><span data-stu-id="195be-117">An example is given below.</span></span>

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

<span data-ttu-id="195be-118">W tym przykładzie ciągi magazynu sterowników są dostosowane przez przypisanie wskaźników ciągu do odpowiadającego parametru.</span><span class="sxs-lookup"><span data-stu-id="195be-118">In this example, the driver storage strings are customized by assigning string pointers to corresponding parameter.</span></span> <span data-ttu-id="195be-119">Jeśli jeden z wskaźników ciągu zostanie pozostawiony do UX_NULL, używany jest domyślny ciąg usługi Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="195be-119">If any one of the string pointer is left to UX_NULL, the default Azure RTOS string is used.</span></span>

<span data-ttu-id="195be-120">W tym przykładzie adres ostatniego bloku dysku lub LBA jest określony, a także rozmiar sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="195be-120">In this example, the drive's last block address or LBA is given as well as the logical sector size.</span></span> <span data-ttu-id="195be-121">LBA to liczba sektorów dostępnych w nośniku — 1.</span><span class="sxs-lookup"><span data-stu-id="195be-121">The LBA is the number of sectors available in the media –1.</span></span> <span data-ttu-id="195be-122">Długość bloku jest ustawiona na 512 w zwykłych nośnikach magazynu.</span><span class="sxs-lookup"><span data-stu-id="195be-122">The block length is set to 512 in regular storage media.</span></span> <span data-ttu-id="195be-123">Dla dysków optycznych można ustawić wartość 2048.</span><span class="sxs-lookup"><span data-stu-id="195be-123">It can be set to 2048 for optical drives.</span></span>

<span data-ttu-id="195be-124">Aplikacja musi przekazać trzy wskaźniki funkcji wywołania zwrotnego, aby umożliwić klasie magazynu odczytywanie, zapisywanie i uzyskiwanie stanu nośnika.</span><span class="sxs-lookup"><span data-stu-id="195be-124">The application needs to pass three callback function pointers to allow the storage class to read, write and obtain status for the media.</span></span>

<span data-ttu-id="195be-125">W poniższym przykładzie przedstawiono prototypy funkcji odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="195be-125">The prototypes for the read and write functions are shown in the example below.</span></span>

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

<span data-ttu-id="195be-126">Gdzie:</span><span class="sxs-lookup"><span data-stu-id="195be-126">Where:</span></span>

- <span data-ttu-id="195be-127">*Magazyn* jest wystąpieniem klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="195be-127">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="195be-128">*LUN* to numer LUN, do którego jest kierowane polecenie.</span><span class="sxs-lookup"><span data-stu-id="195be-128">*lun* is the LUN the command is directed to.</span></span>
- <span data-ttu-id="195be-129">*data_pointer* to adres buforu, który ma być używany do odczytu lub zapisu.</span><span class="sxs-lookup"><span data-stu-id="195be-129">*data_pointer* is the address of the buffer to be used for reading or writing.</span></span>
- <span data-ttu-id="195be-130">*number_blocks* to liczba sektorów do odczytu/zapisu.</span><span class="sxs-lookup"><span data-stu-id="195be-130">*number_blocks* is the number of sectors to read/write.</span></span>
- <span data-ttu-id="195be-131">*LBA* jest adresem sektora, który ma zostać odczytany.</span><span class="sxs-lookup"><span data-stu-id="195be-131">*lba* is the sector address to read.</span></span>
- <span data-ttu-id="195be-132">*media_status* powinna zostać uzupełniona dokładnie tak, jak wartość zwrotna wywołania zwrotnego stanu nośnika.</span><span class="sxs-lookup"><span data-stu-id="195be-132">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="195be-133">Wartość zwracana może mieć wartość UX_SUCCESS lub UX_ERROR wskazującą, że operacja powiodła się lub nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="195be-133">The return value can have either the value UX_SUCCESS or UX_ERROR indicating a successful or unsuccessful operation.</span></span> <span data-ttu-id="195be-134">Te operacje nie muszą zwracać żadnych innych kodów błędów.</span><span class="sxs-lookup"><span data-stu-id="195be-134">These operations do not need to return any other error codes.</span></span> <span data-ttu-id="195be-135">Jeśli wystąpi błąd w żadnej operacji, Klasa magazynu wywoła funkcję wywołania zwrotnego stanu.</span><span class="sxs-lookup"><span data-stu-id="195be-135">If there is an error in any operation, the storage class will invoke the status call back function.</span></span>

<span data-ttu-id="195be-136">Ta funkcja ma następujący prototyp.</span><span class="sxs-lookup"><span data-stu-id="195be-136">This function has the following prototype.</span></span>

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

<span data-ttu-id="195be-137">Parametr wywołujący media_id nie jest obecnie używany i powinien być zawsze równy 0.</span><span class="sxs-lookup"><span data-stu-id="195be-137">The calling parameter media_id is not currently used and should always be 0.</span></span> <span data-ttu-id="195be-138">W przyszłości może służyć do rozróżnienia wielu urządzeń magazynujących lub urządzeń magazynujących z wieloma jednostkami LUN SCSI.</span><span class="sxs-lookup"><span data-stu-id="195be-138">In the future it may be used to distinguish multiple storage devices or storage devices with multiple SCSI LUNs.</span></span> <span data-ttu-id="195be-139">Ta wersja klasy magazynu nie obsługuje wielu wystąpień klasy magazynu ani urządzeń magazynujących z wieloma jednostkami LUN SCSI.</span><span class="sxs-lookup"><span data-stu-id="195be-139">This version of the storage class does not support multiple instances of the storage class or storage devices with multiple SCSI LUNs.</span></span>

<span data-ttu-id="195be-140">Wartość zwracana jest kodem błędu SCSI, który może mieć następujący format.</span><span class="sxs-lookup"><span data-stu-id="195be-140">The return value is a SCSI error code that can have the following format.</span></span>

- <span data-ttu-id="195be-141">**Bity 0-7** Sense_key</span><span class="sxs-lookup"><span data-stu-id="195be-141">**Bits 0-7** Sense_key</span></span>
- <span data-ttu-id="195be-142">**Bity 8-15** Dodatkowy kod wykrywania</span><span class="sxs-lookup"><span data-stu-id="195be-142">**Bits 8-15** Additional Sense Code</span></span>
- <span data-ttu-id="195be-143">**Bity 16-23** Dodatkowy kwalifikator kodu wykrywania</span><span class="sxs-lookup"><span data-stu-id="195be-143">**Bits 16-23** Additional Sense Code Qualifier</span></span>

<span data-ttu-id="195be-144">Poniższa tabela zawiera możliwe kombinacje sensu/ASC/ASCQ.</span><span class="sxs-lookup"><span data-stu-id="195be-144">The following table provides the possible Sense/ASC/ASCQ combinations.</span></span>

| <span data-ttu-id="195be-145">Klucz wykrywania</span><span class="sxs-lookup"><span data-stu-id="195be-145">Sense Key</span></span> | <span data-ttu-id="195be-146">ASC</span><span class="sxs-lookup"><span data-stu-id="195be-146">ASC</span></span> | <span data-ttu-id="195be-147">ASCQ</span><span class="sxs-lookup"><span data-stu-id="195be-147">ASCQ</span></span> | <span data-ttu-id="195be-148">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-148">Description</span></span>                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| <span data-ttu-id="195be-149">00</span><span class="sxs-lookup"><span data-stu-id="195be-149">00</span></span>        | <span data-ttu-id="195be-150">00</span><span class="sxs-lookup"><span data-stu-id="195be-150">00</span></span>  | <span data-ttu-id="195be-151">00</span><span class="sxs-lookup"><span data-stu-id="195be-151">00</span></span>   | <span data-ttu-id="195be-152">NIE MA SENSU</span><span class="sxs-lookup"><span data-stu-id="195be-152">NO SENSE</span></span>                                          |
| <span data-ttu-id="195be-153">01</span><span class="sxs-lookup"><span data-stu-id="195be-153">01</span></span>        | <span data-ttu-id="195be-154">17</span><span class="sxs-lookup"><span data-stu-id="195be-154">17</span></span>  | <span data-ttu-id="195be-155">01</span><span class="sxs-lookup"><span data-stu-id="195be-155">01</span></span>   | <span data-ttu-id="195be-156">ODZYSKANE DANE Z PONOWNYMI PRÓBAMI</span><span class="sxs-lookup"><span data-stu-id="195be-156">RECOVERED DATA WITH RETRIES</span></span>                       |
| <span data-ttu-id="195be-157">01</span><span class="sxs-lookup"><span data-stu-id="195be-157">01</span></span>        | <span data-ttu-id="195be-158">18</span><span class="sxs-lookup"><span data-stu-id="195be-158">18</span></span>  | <span data-ttu-id="195be-159">00</span><span class="sxs-lookup"><span data-stu-id="195be-159">00</span></span>   | <span data-ttu-id="195be-160">ODZYSKIWANIE DANYCH PRZY UŻYCIU ECC</span><span class="sxs-lookup"><span data-stu-id="195be-160">RECOVERED DATA WITH ECC</span></span>                           |
| <span data-ttu-id="195be-161">02</span><span class="sxs-lookup"><span data-stu-id="195be-161">02</span></span>        | <span data-ttu-id="195be-162">04</span><span class="sxs-lookup"><span data-stu-id="195be-162">04</span></span>  | <span data-ttu-id="195be-163">01</span><span class="sxs-lookup"><span data-stu-id="195be-163">01</span></span>   | <span data-ttu-id="195be-164">DYSK LOGICZNY NIE JEST GOTOWY — STAJE SIĘ GOTOWY</span><span class="sxs-lookup"><span data-stu-id="195be-164">LOGICAL DRIVE NOT READY - BECOMING READY</span></span>          |
| <span data-ttu-id="195be-165">02</span><span class="sxs-lookup"><span data-stu-id="195be-165">02</span></span>        | <span data-ttu-id="195be-166">04</span><span class="sxs-lookup"><span data-stu-id="195be-166">04</span></span>  | <span data-ttu-id="195be-167">02</span><span class="sxs-lookup"><span data-stu-id="195be-167">02</span></span>   | <span data-ttu-id="195be-168">DYSK LOGICZNY NIE JEST GOTOWY — WYMAGANE JEST ZAINICJOWANIE</span><span class="sxs-lookup"><span data-stu-id="195be-168">LOGICAL DRIVE NOT READY - INITIALIZATION REQUIRED</span></span> |
| <span data-ttu-id="195be-169">02</span><span class="sxs-lookup"><span data-stu-id="195be-169">02</span></span>        | <span data-ttu-id="195be-170">04</span><span class="sxs-lookup"><span data-stu-id="195be-170">04</span></span>  | <span data-ttu-id="195be-171">04</span><span class="sxs-lookup"><span data-stu-id="195be-171">04</span></span>   | <span data-ttu-id="195be-172">NIEGOTOWY FORMAT JEDNOSTKI LOGICZNEJ</span><span class="sxs-lookup"><span data-stu-id="195be-172">LOGICAL UNIT NOT READY - FORMAT IN PROGRESS</span></span>       |
| <span data-ttu-id="195be-173">02</span><span class="sxs-lookup"><span data-stu-id="195be-173">02</span></span>        | <span data-ttu-id="195be-174">04</span><span class="sxs-lookup"><span data-stu-id="195be-174">04</span></span>  | <span data-ttu-id="195be-175">ZZ</span><span class="sxs-lookup"><span data-stu-id="195be-175">FF</span></span>   | <span data-ttu-id="195be-176">DYSK LOGICZNY NIE JEST GOTOWY — URZĄDZENIE JEST ZAJĘTE</span><span class="sxs-lookup"><span data-stu-id="195be-176">LOGICAL DRIVE NOT READY - DEVICE IS BUSY</span></span>          |
| <span data-ttu-id="195be-177">02</span><span class="sxs-lookup"><span data-stu-id="195be-177">02</span></span>        | <span data-ttu-id="195be-178">06</span><span class="sxs-lookup"><span data-stu-id="195be-178">06</span></span>  | <span data-ttu-id="195be-179">00</span><span class="sxs-lookup"><span data-stu-id="195be-179">00</span></span>   | <span data-ttu-id="195be-180">NIE ZNALEZIONO POZYCJI ODWOŁANIA</span><span class="sxs-lookup"><span data-stu-id="195be-180">NO REFERENCE POSITION FOUND</span></span>                       |
| <span data-ttu-id="195be-181">02</span><span class="sxs-lookup"><span data-stu-id="195be-181">02</span></span>        | <span data-ttu-id="195be-182">08</span><span class="sxs-lookup"><span data-stu-id="195be-182">08</span></span>  | <span data-ttu-id="195be-183">00</span><span class="sxs-lookup"><span data-stu-id="195be-183">00</span></span>   | <span data-ttu-id="195be-184">BŁĄD KOMUNIKACJI JEDNOSTKI LOGICZNEJ</span><span class="sxs-lookup"><span data-stu-id="195be-184">LOGICAL UNIT COMMUNICATION FAILURE</span></span>                |
| <span data-ttu-id="195be-185">02</span><span class="sxs-lookup"><span data-stu-id="195be-185">02</span></span>        | <span data-ttu-id="195be-186">08</span><span class="sxs-lookup"><span data-stu-id="195be-186">08</span></span>  | <span data-ttu-id="195be-187">01</span><span class="sxs-lookup"><span data-stu-id="195be-187">01</span></span>   | <span data-ttu-id="195be-188">LIMIT CZASU KOMUNIKACJI JEDNOSTKI LOGICZNEJ</span><span class="sxs-lookup"><span data-stu-id="195be-188">LOGICAL UNIT COMMUNICATION TIME-OUT</span></span>               |
| <span data-ttu-id="195be-189">02</span><span class="sxs-lookup"><span data-stu-id="195be-189">02</span></span>        | <span data-ttu-id="195be-190">08</span><span class="sxs-lookup"><span data-stu-id="195be-190">08</span></span>  | <span data-ttu-id="195be-191">80</span><span class="sxs-lookup"><span data-stu-id="195be-191">80</span></span>   | <span data-ttu-id="195be-192">PRZEPEŁNIENIE KOMUNIKACJI JEDNOSTKI LOGICZNEJ</span><span class="sxs-lookup"><span data-stu-id="195be-192">LOGICAL UNIT COMMUNICATION OVERRUN</span></span>                |
| <span data-ttu-id="195be-193">02</span><span class="sxs-lookup"><span data-stu-id="195be-193">02</span></span>        | <span data-ttu-id="195be-194">Art</span><span class="sxs-lookup"><span data-stu-id="195be-194">3A</span></span>  | <span data-ttu-id="195be-195">00</span><span class="sxs-lookup"><span data-stu-id="195be-195">00</span></span>   | <span data-ttu-id="195be-196">BRAK ŚREDNIEJ</span><span class="sxs-lookup"><span data-stu-id="195be-196">MEDIUM NOT PRESENT</span></span>                                |
| <span data-ttu-id="195be-197">02</span><span class="sxs-lookup"><span data-stu-id="195be-197">02</span></span>        | <span data-ttu-id="195be-198">54</span><span class="sxs-lookup"><span data-stu-id="195be-198">54</span></span>  | <span data-ttu-id="195be-199">00</span><span class="sxs-lookup"><span data-stu-id="195be-199">00</span></span>   | <span data-ttu-id="195be-200">BŁĄD INTERFEJSU USB DO HOSTA SYSTEMU</span><span class="sxs-lookup"><span data-stu-id="195be-200">USB TO HOST SYSTEM INTERFACE FAILURE</span></span>              |
| <span data-ttu-id="195be-201">02</span><span class="sxs-lookup"><span data-stu-id="195be-201">02</span></span>        | <span data-ttu-id="195be-202">80</span><span class="sxs-lookup"><span data-stu-id="195be-202">80</span></span>  | <span data-ttu-id="195be-203">00</span><span class="sxs-lookup"><span data-stu-id="195be-203">00</span></span>   | <span data-ttu-id="195be-204">NIEWYSTARCZAJĄCE ZASOBY</span><span class="sxs-lookup"><span data-stu-id="195be-204">INSUFFICIENT RESOURCES</span></span>                            |
| <span data-ttu-id="195be-205">02</span><span class="sxs-lookup"><span data-stu-id="195be-205">02</span></span>        | <span data-ttu-id="195be-206">ZZ</span><span class="sxs-lookup"><span data-stu-id="195be-206">FF</span></span>  | <span data-ttu-id="195be-207">ZZ</span><span class="sxs-lookup"><span data-stu-id="195be-207">FF</span></span>   | <span data-ttu-id="195be-208">NIEZNANY BŁĄD</span><span class="sxs-lookup"><span data-stu-id="195be-208">UNKNOWN ERROR</span></span>                                     |
| <span data-ttu-id="195be-209">03</span><span class="sxs-lookup"><span data-stu-id="195be-209">03</span></span>        | <span data-ttu-id="195be-210">02</span><span class="sxs-lookup"><span data-stu-id="195be-210">02</span></span>  | <span data-ttu-id="195be-211">00</span><span class="sxs-lookup"><span data-stu-id="195be-211">00</span></span>   | <span data-ttu-id="195be-212">NIE ZAKOŃCZONO WYSZUKIWANIA</span><span class="sxs-lookup"><span data-stu-id="195be-212">NO SEEK COMPLETE</span></span>                                  |
| <span data-ttu-id="195be-213">03</span><span class="sxs-lookup"><span data-stu-id="195be-213">03</span></span>        | <span data-ttu-id="195be-214">03</span><span class="sxs-lookup"><span data-stu-id="195be-214">03</span></span>  | <span data-ttu-id="195be-215">00</span><span class="sxs-lookup"><span data-stu-id="195be-215">00</span></span>   | <span data-ttu-id="195be-216">BŁĄD ZAPISU</span><span class="sxs-lookup"><span data-stu-id="195be-216">WRITE FAULT</span></span>                                       |
| <span data-ttu-id="195be-217">03</span><span class="sxs-lookup"><span data-stu-id="195be-217">03</span></span>        | <span data-ttu-id="195be-218">10</span><span class="sxs-lookup"><span data-stu-id="195be-218">10</span></span>  | <span data-ttu-id="195be-219">00</span><span class="sxs-lookup"><span data-stu-id="195be-219">00</span></span>   | <span data-ttu-id="195be-220">BŁĄD CRC IDENTYFIKATORA</span><span class="sxs-lookup"><span data-stu-id="195be-220">ID CRC ERROR</span></span>                                      |
| <span data-ttu-id="195be-221">03</span><span class="sxs-lookup"><span data-stu-id="195be-221">03</span></span>        | <span data-ttu-id="195be-222">11</span><span class="sxs-lookup"><span data-stu-id="195be-222">11</span></span>  | <span data-ttu-id="195be-223">00</span><span class="sxs-lookup"><span data-stu-id="195be-223">00</span></span>   | <span data-ttu-id="195be-224">NIEODWRACALNY BŁĄD ODCZYTU</span><span class="sxs-lookup"><span data-stu-id="195be-224">UNRECOVERED READ ERROR</span></span>                            |
| <span data-ttu-id="195be-225">03</span><span class="sxs-lookup"><span data-stu-id="195be-225">03</span></span>        | <span data-ttu-id="195be-226">12</span><span class="sxs-lookup"><span data-stu-id="195be-226">12</span></span>  | <span data-ttu-id="195be-227">00</span><span class="sxs-lookup"><span data-stu-id="195be-227">00</span></span>   | <span data-ttu-id="195be-228">NIE ZNALEZIONO ZNACZNIKA ADRESU DLA POLA IDENTYFIKATORA</span><span class="sxs-lookup"><span data-stu-id="195be-228">ADDRESS MARK NOT FOUND FOR ID FIELD</span></span>               |
| <span data-ttu-id="195be-229">03</span><span class="sxs-lookup"><span data-stu-id="195be-229">03</span></span>        | <span data-ttu-id="195be-230">13</span><span class="sxs-lookup"><span data-stu-id="195be-230">13</span></span>  | <span data-ttu-id="195be-231">00</span><span class="sxs-lookup"><span data-stu-id="195be-231">00</span></span>   | <span data-ttu-id="195be-232">NIE ZNALEZIONO ZNACZNIKA ADRESU DLA POLA DANYCH</span><span class="sxs-lookup"><span data-stu-id="195be-232">ADDRESS MARK NOT FOUND FOR DATA FIELD</span></span>             |
| <span data-ttu-id="195be-233">03</span><span class="sxs-lookup"><span data-stu-id="195be-233">03</span></span>        | <span data-ttu-id="195be-234">14</span><span class="sxs-lookup"><span data-stu-id="195be-234">14</span></span>  | <span data-ttu-id="195be-235">00</span><span class="sxs-lookup"><span data-stu-id="195be-235">00</span></span>   | <span data-ttu-id="195be-236">NIE ZNALEZIONO ZAPISANEJ JEDNOSTKI</span><span class="sxs-lookup"><span data-stu-id="195be-236">RECORDED ENTITY NOT FOUND</span></span>                         |
| <span data-ttu-id="195be-237">03</span><span class="sxs-lookup"><span data-stu-id="195be-237">03</span></span>        | <span data-ttu-id="195be-238">30</span><span class="sxs-lookup"><span data-stu-id="195be-238">30</span></span>  | <span data-ttu-id="195be-239">01</span><span class="sxs-lookup"><span data-stu-id="195be-239">01</span></span>   | <span data-ttu-id="195be-240">NIE MOŻNA ODCZYTAĆ FORMATU ŚREDNI-NIEZNANY</span><span class="sxs-lookup"><span data-stu-id="195be-240">CANNOT READ MEDIUM - UNKNOWN FORMAT</span></span>               |
| <span data-ttu-id="195be-241">03</span><span class="sxs-lookup"><span data-stu-id="195be-241">03</span></span>        | <span data-ttu-id="195be-242">31</span><span class="sxs-lookup"><span data-stu-id="195be-242">31</span></span>  | <span data-ttu-id="195be-243">01</span><span class="sxs-lookup"><span data-stu-id="195be-243">01</span></span>   | <span data-ttu-id="195be-244">POLECENIE FORMATOWANIA NIE POWIODŁO SIĘ</span><span class="sxs-lookup"><span data-stu-id="195be-244">FORMAT COMMAND FAILED</span></span>                             |
| <span data-ttu-id="195be-245">04</span><span class="sxs-lookup"><span data-stu-id="195be-245">04</span></span>        | <span data-ttu-id="195be-246">40</span><span class="sxs-lookup"><span data-stu-id="195be-246">40</span></span>  | <span data-ttu-id="195be-247">NN</span><span class="sxs-lookup"><span data-stu-id="195be-247">NN</span></span>   | <span data-ttu-id="195be-248">BŁĄD DIAGNOSTYKI SKŁADNIKA NN (80H-FFH)</span><span class="sxs-lookup"><span data-stu-id="195be-248">DIAGNOSTIC FAILURE ON COMPONENT NN (80H-FFH)</span></span>      |
| <span data-ttu-id="195be-249">05</span><span class="sxs-lookup"><span data-stu-id="195be-249">05</span></span>        | <span data-ttu-id="195be-250">Ust</span><span class="sxs-lookup"><span data-stu-id="195be-250">1A</span></span>  | <span data-ttu-id="195be-251">00</span><span class="sxs-lookup"><span data-stu-id="195be-251">00</span></span>   | <span data-ttu-id="195be-252">BŁĄD DŁUGOŚCI LISTY PARAMETRÓW</span><span class="sxs-lookup"><span data-stu-id="195be-252">PARAMETER LIST LENGTH ERROR</span></span>                       |
| <span data-ttu-id="195be-253">05</span><span class="sxs-lookup"><span data-stu-id="195be-253">05</span></span>        | <span data-ttu-id="195be-254">20</span><span class="sxs-lookup"><span data-stu-id="195be-254">20</span></span>  | <span data-ttu-id="195be-255">00</span><span class="sxs-lookup"><span data-stu-id="195be-255">00</span></span>   | <span data-ttu-id="195be-256">NIEPRAWIDŁOWY KOD OPERACJI POLECENIA</span><span class="sxs-lookup"><span data-stu-id="195be-256">INVALID COMMAND OPERATION CODE</span></span>                    |
| <span data-ttu-id="195be-257">05</span><span class="sxs-lookup"><span data-stu-id="195be-257">05</span></span>        | <span data-ttu-id="195be-258">21</span><span class="sxs-lookup"><span data-stu-id="195be-258">21</span></span>  | <span data-ttu-id="195be-259">00</span><span class="sxs-lookup"><span data-stu-id="195be-259">00</span></span>   | <span data-ttu-id="195be-260">ADRES BLOKU LOGICZNEGO POZA ZAKRESEM</span><span class="sxs-lookup"><span data-stu-id="195be-260">LOGICAL BLOCK ADDRESS OUT OF RANGE</span></span>                |
| <span data-ttu-id="195be-261">05</span><span class="sxs-lookup"><span data-stu-id="195be-261">05</span></span>        | <span data-ttu-id="195be-262">24</span><span class="sxs-lookup"><span data-stu-id="195be-262">24</span></span>  | <span data-ttu-id="195be-263">00</span><span class="sxs-lookup"><span data-stu-id="195be-263">00</span></span>   | <span data-ttu-id="195be-264">NIEPRAWIDŁOWE POLE W PAKIECIE POLECEŃ</span><span class="sxs-lookup"><span data-stu-id="195be-264">INVALID FIELD IN COMMAND PACKET</span></span>                   |
| <span data-ttu-id="195be-265">05</span><span class="sxs-lookup"><span data-stu-id="195be-265">05</span></span>        | <span data-ttu-id="195be-266">25</span><span class="sxs-lookup"><span data-stu-id="195be-266">25</span></span>  | <span data-ttu-id="195be-267">00</span><span class="sxs-lookup"><span data-stu-id="195be-267">00</span></span>   | <span data-ttu-id="195be-268">JEDNOSTKA LOGICZNA NIE JEST OBSŁUGIWANA</span><span class="sxs-lookup"><span data-stu-id="195be-268">LOGICAL UNIT NOT SUPPORTED</span></span>                        |
| <span data-ttu-id="195be-269">05</span><span class="sxs-lookup"><span data-stu-id="195be-269">05</span></span>        | <span data-ttu-id="195be-270">26</span><span class="sxs-lookup"><span data-stu-id="195be-270">26</span></span>  | <span data-ttu-id="195be-271">00</span><span class="sxs-lookup"><span data-stu-id="195be-271">00</span></span>   | <span data-ttu-id="195be-272">NIEPRAWIDŁOWE POLE NA LIŚCIE PARAMETRÓW</span><span class="sxs-lookup"><span data-stu-id="195be-272">INVALID FIELD IN PARAMETER LIST</span></span>                   |
| <span data-ttu-id="195be-273">05</span><span class="sxs-lookup"><span data-stu-id="195be-273">05</span></span>        | <span data-ttu-id="195be-274">26</span><span class="sxs-lookup"><span data-stu-id="195be-274">26</span></span>  | <span data-ttu-id="195be-275">01</span><span class="sxs-lookup"><span data-stu-id="195be-275">01</span></span>   | <span data-ttu-id="195be-276">PARAMETR NIE JEST OBSŁUGIWANY</span><span class="sxs-lookup"><span data-stu-id="195be-276">PARAMETER NOT SUPPORTED</span></span>                           |
| <span data-ttu-id="195be-277">05</span><span class="sxs-lookup"><span data-stu-id="195be-277">05</span></span>        | <span data-ttu-id="195be-278">26</span><span class="sxs-lookup"><span data-stu-id="195be-278">26</span></span>  | <span data-ttu-id="195be-279">02</span><span class="sxs-lookup"><span data-stu-id="195be-279">02</span></span>   | <span data-ttu-id="195be-280">NIEPRAWIDŁOWA WARTOŚĆ PARAMETRU</span><span class="sxs-lookup"><span data-stu-id="195be-280">PARAMETER VALUE INVALID</span></span>                           |
| <span data-ttu-id="195be-281">05</span><span class="sxs-lookup"><span data-stu-id="195be-281">05</span></span>        | <span data-ttu-id="195be-282">39</span><span class="sxs-lookup"><span data-stu-id="195be-282">39</span></span>  | <span data-ttu-id="195be-283">00</span><span class="sxs-lookup"><span data-stu-id="195be-283">00</span></span>   | <span data-ttu-id="195be-284">ZAPISYWANIE PARAMETRÓW NIE JEST OBSŁUGIWANE</span><span class="sxs-lookup"><span data-stu-id="195be-284">SAVING PARAMETERS NOT SUPPORT</span></span>                     |
| <span data-ttu-id="195be-285">06</span><span class="sxs-lookup"><span data-stu-id="195be-285">06</span></span>        | <span data-ttu-id="195be-286">28</span><span class="sxs-lookup"><span data-stu-id="195be-286">28</span></span>  | <span data-ttu-id="195be-287">00</span><span class="sxs-lookup"><span data-stu-id="195be-287">00</span></span>   | <span data-ttu-id="195be-288">NIE GOTOWY DO PRZEJŚCIA DO GOTOWOŚCI — ZMIENIONO NOŚNIK</span><span class="sxs-lookup"><span data-stu-id="195be-288">NOT READY TO READY TRANSITION – MEDIA CHANGED</span></span>     |
| <span data-ttu-id="195be-289">06</span><span class="sxs-lookup"><span data-stu-id="195be-289">06</span></span>        | <span data-ttu-id="195be-290">29</span><span class="sxs-lookup"><span data-stu-id="195be-290">29</span></span>  | <span data-ttu-id="195be-291">00</span><span class="sxs-lookup"><span data-stu-id="195be-291">00</span></span>   | <span data-ttu-id="195be-292">WYSTĄPIŁO RESETOWANIE LUB ZRESETOWANIE URZĄDZENIA MAGISTRALI</span><span class="sxs-lookup"><span data-stu-id="195be-292">POWER ON RESET OR BUS DEVICE RESET OCCURRED</span></span>       |
| <span data-ttu-id="195be-293">06</span><span class="sxs-lookup"><span data-stu-id="195be-293">06</span></span>        | <span data-ttu-id="195be-294">2F</span><span class="sxs-lookup"><span data-stu-id="195be-294">2F</span></span>  | <span data-ttu-id="195be-295">00</span><span class="sxs-lookup"><span data-stu-id="195be-295">00</span></span>   | <span data-ttu-id="195be-296">POLECENIA WYCZYSZCZONE PRZEZ INNEGO INICJATORA</span><span class="sxs-lookup"><span data-stu-id="195be-296">COMMANDS CLEARED BY ANOTHER INITIATOR</span></span>             |
| <span data-ttu-id="195be-297">07</span><span class="sxs-lookup"><span data-stu-id="195be-297">07</span></span>        | <span data-ttu-id="195be-298">27</span><span class="sxs-lookup"><span data-stu-id="195be-298">27</span></span>  | <span data-ttu-id="195be-299">00</span><span class="sxs-lookup"><span data-stu-id="195be-299">00</span></span>   | <span data-ttu-id="195be-300">ZAPISZ NOŚNIK CHRONIONY</span><span class="sxs-lookup"><span data-stu-id="195be-300">WRITE PROTECTED MEDIA</span></span>                             |
| <span data-ttu-id="195be-301">0B</span><span class="sxs-lookup"><span data-stu-id="195be-301">0B</span></span>        | <span data-ttu-id="195be-302">4E</span><span class="sxs-lookup"><span data-stu-id="195be-302">4E</span></span>  | <span data-ttu-id="195be-303">00</span><span class="sxs-lookup"><span data-stu-id="195be-303">00</span></span>   | <span data-ttu-id="195be-304">PODJĘTO PRÓBĘ NAKŁADAJĄCEGO POLECENIA</span><span class="sxs-lookup"><span data-stu-id="195be-304">OVERLAPPED COMMAND ATTEMPTED</span></span>                      |

<span data-ttu-id="195be-305">Istnieją dwa dodatkowe, opcjonalne wywołania zwrotne, które aplikacja może zaimplementować; jeden jest do odpowiadania na polecenie **GET_STATUS_NOTIFICATION** , a drugi jest do odpowiadania na polecenie **SYNCHRONIZE_CACHE** .</span><span class="sxs-lookup"><span data-stu-id="195be-305">There are two additional, optional callbacks the application may implement; one is for responding to a **GET_STATUS_NOTIFICATION** command and the other is for responding to the **SYNCHRONIZE_CACHE** command.</span></span>

<span data-ttu-id="195be-306">Jeśli aplikacja chce obsłużyć GET_STATUS_NOTIFICATION polecenie z hosta, powinien zaimplementować wywołanie zwrotne z następującym prototypem.</span><span class="sxs-lookup"><span data-stu-id="195be-306">If the application would like to handle the GET_STATUS_NOTIFICATION command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

<span data-ttu-id="195be-307">Gdzie:</span><span class="sxs-lookup"><span data-stu-id="195be-307">Where:</span></span>

- <span data-ttu-id="195be-308">*Magazyn* jest wystąpieniem klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="195be-308">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="195be-309">*media_id* nie jest obecnie używana.</span><span class="sxs-lookup"><span data-stu-id="195be-309">*media_id* is not currently used.</span></span> <span data-ttu-id="195be-310">notification_class określa klasę powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="195be-310">notification_class specifies the class of notification.</span></span>
- <span data-ttu-id="195be-311">*media_notification* powinna być ustawiona przez aplikację w buforze zawierającym odpowiedź na powiadomienie.</span><span class="sxs-lookup"><span data-stu-id="195be-311">*media_notification* should be set by the application to the buffer containing the response for the notification.</span></span>
- <span data-ttu-id="195be-312">*media_notification_length* powinna być ustawiona przez aplikację w taki sposób, aby zawierała długość buforu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="195be-312">*media_notification_length* should be set by the application to contain the length of the response buffer.</span></span>

<span data-ttu-id="195be-313">Wartość zwracana wskazuje, czy polecenie powiodło się — powinno być **UX_SUCCESS** lub **UX_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="195be-313">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

<span data-ttu-id="195be-314">Jeśli aplikacja nie implementuje tego wywołania zwrotnego, po odebraniu polecenia **GET_STATUS_NOTIFICATION** program USBX powiadomi hosta, że polecenie nie zostało zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="195be-314">If the application does not implement this callback, then upon receiving the **GET_STATUS_NOTIFICATION** command, USBX will notify the host that the command is not implemented.</span></span>

<span data-ttu-id="195be-315">Polecenie **SYNCHRONIZE_CACHE** powinno być obsługiwane, jeśli aplikacja korzysta z pamięci podręcznej do zapisu z hosta.</span><span class="sxs-lookup"><span data-stu-id="195be-315">The **SYNCHRONIZE_CACHE** command should be handled if the application is utilizing a cache for writes from the host.</span></span> <span data-ttu-id="195be-316">Host może wysłać to polecenie, jeśli wie, że urządzenie magazynujące zostanie odłączone, na przykład w systemie Windows, jeśli klikniesz prawym przyciskiem myszy ikonę dysku flash na pasku narzędzi i wybierzesz pozycję "Wysuń \[ nazwę urządzenia magazynującego \] ", system Windows wyda polecenie **SYNCHRONIZE_CACHE** na tym urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="195be-316">A host may send this command if it knows the storage device is about to be disconnected, for example, in Windows, if you right click a flash drive icon in the toolbar and select "Eject \[storage device name\]", Windows will issue the **SYNCHRONIZE_CACHE** command to that device.</span></span>

<span data-ttu-id="195be-317">Jeśli aplikacja chce obsłużyć **GET_STATUS_NOTIFICATION** polecenie z hosta, powinien zaimplementować wywołanie zwrotne z następującym prototypem.</span><span class="sxs-lookup"><span data-stu-id="195be-317">If the application would like to handle the **GET_STATUS_NOTIFICATION** command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

<span data-ttu-id="195be-318">Gdzie:</span><span class="sxs-lookup"><span data-stu-id="195be-318">Where:</span></span>

- <span data-ttu-id="195be-319">*Magazyn* jest wystąpieniem klasy magazynu.</span><span class="sxs-lookup"><span data-stu-id="195be-319">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="195be-320">wartość parametru *LUN* określa numer LUN, do którego jest kierowane polecenie.</span><span class="sxs-lookup"><span data-stu-id="195be-320">*lun* parameter specifies which LUN the command is directed to.</span></span>
- <span data-ttu-id="195be-321">*number_blocks* określa liczbę bloków do zsynchronizowania.</span><span class="sxs-lookup"><span data-stu-id="195be-321">*number_blocks* specifies the number of blocks to synchronize.</span></span>
- <span data-ttu-id="195be-322">*LBA* jest adresem sektora pierwszego bloku do synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="195be-322">*lba* is the sector address of the first block to synchronize.</span></span>
- <span data-ttu-id="195be-323">*media_status* powinna zostać uzupełniona dokładnie tak, jak wartość zwrotna wywołania zwrotnego stanu nośnika.</span><span class="sxs-lookup"><span data-stu-id="195be-323">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="195be-324">Wartość zwracana wskazuje, czy polecenie powiodło się — powinno być **UX_SUCCESS** lub **UX_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="195be-324">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

### <a name="multiple-scsi-lun"></a><span data-ttu-id="195be-325">Wiele jednostek LUN SCSI</span><span class="sxs-lookup"><span data-stu-id="195be-325">Multiple SCSI LUN</span></span>

<span data-ttu-id="195be-326">Klasa magazynu urządzeń USBX obsługuje wiele jednostek LUN.</span><span class="sxs-lookup"><span data-stu-id="195be-326">The USBX device storage class supports multiple LUNs.</span></span> <span data-ttu-id="195be-327">W związku z tym można utworzyć urządzenie magazynujące, które jednocześnie działa jak dysk CD-ROM i dysk flash.</span><span class="sxs-lookup"><span data-stu-id="195be-327">It is therefore possible to create a storage device that acts as a CD-ROM and a Flash disk at the same time.</span></span> <span data-ttu-id="195be-328">W takim przypadku Inicjalizacja byłaby nieco inna.</span><span class="sxs-lookup"><span data-stu-id="195be-328">In such a case, the initialization would be slightly different.</span></span> <span data-ttu-id="195be-329">Oto przykład dysku flash i dysku CD-ROM:</span><span class="sxs-lookup"><span data-stu-id="195be-329">Here is an example for a Flash Disk and CD-ROM:</span></span>

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

## <a name="usb-device-cdc-acm-class"></a><span data-ttu-id="195be-330">Przechwytywanie urządzenia USB — Klasa ACM</span><span class="sxs-lookup"><span data-stu-id="195be-330">USB Device CDC-ACM Class</span></span>

<span data-ttu-id="195be-331">Klasa przełączenia urządzenia USB do grupy ACM umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzenie szeregowe.</span><span class="sxs-lookup"><span data-stu-id="195be-331">The USB device CDC-ACM class allows for a USB host system to communicate with the device as a serial device.</span></span> <span data-ttu-id="195be-332">Ta klasa jest oparta na standardzie USB i jest podzbiorem standardu przechwytywania zmian.</span><span class="sxs-lookup"><span data-stu-id="195be-332">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="195be-333">Architektura urządzenia zgodna z przeskakującą zmianą musi być zadeklarowana przez stos urządzeń.</span><span class="sxs-lookup"><span data-stu-id="195be-333">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="195be-334">Poniżej znajduje się przykład.</span><span class="sxs-lookup"><span data-stu-id="195be-334">An example is found here below.</span></span>

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

<span data-ttu-id="195be-335">Klasa przechwytywania odporności — ACM używa złożonej struktury urządzenia do grupowania interfejsów (kontroli i danych).</span><span class="sxs-lookup"><span data-stu-id="195be-335">The CDC-ACM class uses a composite device framework to group interfaces (control and data).</span></span> <span data-ttu-id="195be-336">W związku z tym należy wziąć pod uwagę podczas definiowania deskryptora urządzenia.</span><span class="sxs-lookup"><span data-stu-id="195be-336">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="195be-337">USBX opiera się na deskryptorze IAD, aby wiedzieć, jak powiązać interfejsy.</span><span class="sxs-lookup"><span data-stu-id="195be-337">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="195be-338">Deskryptor IAD powinien zostać zadeklarowany przed interfejsami i zawierać pierwszy interfejs klasy przechwytywania-ACM oraz liczbę interfejsów, które są dołączone.</span><span class="sxs-lookup"><span data-stu-id="195be-338">The IAD descriptor should be declared before the interfaces and contain the first interface of the CDC-ACM class and how many interfaces are attached.</span></span>

<span data-ttu-id="195be-339">Klasa przechwytywania odporności — ACM używa również deskryptora funkcjonalnego Union, który wykonuje tę samą funkcję co nowszy deskryptor IAD.</span><span class="sxs-lookup"><span data-stu-id="195be-339">The CDC-ACM class also uses a union functional descriptor which performs the same function as the newer IAD descriptor.</span></span> <span data-ttu-id="195be-340">Chociaż deskryptor funkcjonalny Union musi być zadeklarowany ze względu na historyczne przyczyny i zgodność ze stroną hosta, nie jest używany przez USBX.</span><span class="sxs-lookup"><span data-stu-id="195be-340">Although a Union Functional descriptor must be declared for historical reasons and compatibility with the host side, it is not used by USBX.</span></span>

<span data-ttu-id="195be-341">Inicjalizacja klasy przechwytywania zmian-ACM oczekuje następujących parametrów.</span><span class="sxs-lookup"><span data-stu-id="195be-341">The initialization of the CDC-ACM class expects the following parameters.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

<span data-ttu-id="195be-342">Zdefiniowane dwa parametry są wskaźnikami wywołania zwrotnego do aplikacji użytkownika, które będą wywoływane, gdy stos aktywuje lub dezaktywuje tę klasę.</span><span class="sxs-lookup"><span data-stu-id="195be-342">The 2 parameters defined are callback pointers into the user applications that will be called when the stack activates or deactivate this class.</span></span>

<span data-ttu-id="195be-343">Trzeci zdefiniowany parametr jest wskaźnikiem wywołania zwrotnego do aplikacji użytkownika, który zostanie wywołany, gdy występuje zmiana parametrów kodowania lub wierszy.</span><span class="sxs-lookup"><span data-stu-id="195be-343">The third parameter defined is a callback pointer to the user application that will be called when there is line coding or line states parameter change.</span></span> <span data-ttu-id="195be-344">Na przykład, gdy istnieje żądanie od hosta, aby zmienić stan DTR na **true**, wywołanie zwrotne jest wywoływane, w aplikacji użytkownika IT może sprawdzać stan wiersza za pomocą funkcji IOCTL do Kow host jest gotowy do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="195be-344">E.g., when there is request from host to change DTR state to **TRUE**, the callback is invoked, in it user application can check line states through IOCTL function to kow host is ready for communication.</span></span>

<span data-ttu-id="195be-345">Replika przestawna — ACM jest oparta na standardzie USB i jest automatycznie rozpoznawana przez systemy operacyjne MACOs i Linux.</span><span class="sxs-lookup"><span data-stu-id="195be-345">The CDC-ACM is based on a USB-IF standard and is automatically recognized by MACOs and Linux operating systems.</span></span> <span data-ttu-id="195be-346">Na platformach Windows ta klasa wymaga pliku inf dla systemu Windows w wersji starszej niż 10.</span><span class="sxs-lookup"><span data-stu-id="195be-346">On Windows platforms, this class requires a .inf file for Windows version prior to 10.</span></span> <span data-ttu-id="195be-347">System Windows 10 nie wymaga żadnych plików inf.</span><span class="sxs-lookup"><span data-stu-id="195be-347">Windows 10 does not require any .inf files.</span></span> <span data-ttu-id="195be-348">Dostarczamy szablon klasy przechwytywania zmian-ACM i można ją znaleźć w katalogu ***usbx_windows_host_files*** .</span><span class="sxs-lookup"><span data-stu-id="195be-348">We supply a template for the CDC-ACM class and it can be found in the ***usbx_windows_host_files*** directory.</span></span> <span data-ttu-id="195be-349">W przypadku nowszej wersji systemu Windows należy użyć pliku CDC_ACM_Template_Win7_64bit. inf (z wyjątkiem Win10).</span><span class="sxs-lookup"><span data-stu-id="195be-349">For more recent version of Windows the file CDC_ACM_Template_Win7_64bit.inf should be used (except Win10).</span></span> <span data-ttu-id="195be-350">Ten plik musi zostać zmodyfikowany w celu odzwierciedlenia identyfikatora PID/VID używanego przez urządzenie.</span><span class="sxs-lookup"><span data-stu-id="195be-350">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="195be-351">Identyfikator PID/VID będzie charakterystyczny dla klienta końcowego, gdy firma i produkt zostaną zarejestrowane przy użyciu portu USB.</span><span class="sxs-lookup"><span data-stu-id="195be-351">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="195be-352">W pliku inf pola do zmodyfikowania znajdują się tutaj.</span><span class="sxs-lookup"><span data-stu-id="195be-352">In the inf file, the fields to modify are located here.</span></span>

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

<span data-ttu-id="195be-353">W środowisku urządzenia urządzenia typu "przechwytywanie zmian typu" Identyfikator PID/VID są przechowywane w deskryptorze urządzenia (Sprawdź zadeklarowany powyżej deskryptor urządzenia).</span><span class="sxs-lookup"><span data-stu-id="195be-353">In the device framework of the CDC-ACM device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="195be-354">Gdy systemy hosta USB odnajdują urządzenie przełączenia do sieci USB z funkcją przechwytywania, zainstaluje klasę seryjną, a urządzenie może być używane z dowolnym seryjnym programem terminala.</span><span class="sxs-lookup"><span data-stu-id="195be-354">When a USB host systems discovers the USB CDC-ACM device, it will mount a serial class and the device can be used with any serial terminal program.</span></span> <span data-ttu-id="195be-355">Aby uzyskać informacje, zobacz system operacyjny hosta.</span><span class="sxs-lookup"><span data-stu-id="195be-355">See the host Operating System for reference.</span></span>

<span data-ttu-id="195be-356">Poniżej przedstawiono funkcje interfejsu API klasy przechwytywania zmian-ACM.</span><span class="sxs-lookup"><span data-stu-id="195be-356">The CDC-ACM class API functions are defined below.</span></span>

### <a name="ux_device_class_cdc_acm_ioctl"></a><span data-ttu-id="195be-357">ux_device_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="195be-357">ux_device_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="195be-358">Wykonywanie operacji IOCTL w interfejsie przechwytywania zmian-ACM</span><span class="sxs-lookup"><span data-stu-id="195be-358">Perform IOCTL on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-359">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-359">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="195be-360">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-360">Description</span></span>

<span data-ttu-id="195be-361">Ta funkcja jest wywoływana, gdy aplikacja musi wykonać różne wywołania IOCTL do interfejsu przechwytywania zmian</span><span class="sxs-lookup"><span data-stu-id="195be-361">This function is called when an application needs to perform various ioctl calls to the cdc acm interface</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-362">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-362">Parameters</span></span>

- <span data-ttu-id="195be-363">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-363">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-364">**ioctl_function**: funkcja IOCTL, która ma zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="195be-364">**ioctl_function**: Ioctl function to be performed.</span></span>
- <span data-ttu-id="195be-365">**parametr**: wskaźnik do parametru, który jest specyficzny dla wywołania IOCTL.</span><span class="sxs-lookup"><span data-stu-id="195be-365">**parameter**: Pointer to a parameter specific to the ioctl call.</span></span>

### <a name="return-value"></a><span data-ttu-id="195be-366">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-366">Return Value</span></span>

- <span data-ttu-id="195be-367">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-367">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="195be-368">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="195be-368">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="195be-369">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-369">Example</span></span>

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a><span data-ttu-id="195be-370">Funkcje IOCTL:</span><span class="sxs-lookup"><span data-stu-id="195be-370">Ioctl functions:</span></span>

| <span data-ttu-id="195be-371">Funkcja</span><span class="sxs-lookup"><span data-stu-id="195be-371">Function</span></span>                                        | <span data-ttu-id="195be-372">Wartość</span><span class="sxs-lookup"><span data-stu-id="195be-372">Value</span></span> |
| ----------------------------------------------- | - |
| <span data-ttu-id="195be-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="195be-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>    | <span data-ttu-id="195be-374">1</span><span class="sxs-lookup"><span data-stu-id="195be-374">1</span></span> |
| <span data-ttu-id="195be-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="195be-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>    | <span data-ttu-id="195be-376">2</span><span class="sxs-lookup"><span data-stu-id="195be-376">2</span></span> |
| <span data-ttu-id="195be-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="195be-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>     | <span data-ttu-id="195be-378">3</span><span class="sxs-lookup"><span data-stu-id="195be-378">3</span></span> |
| <span data-ttu-id="195be-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="195be-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>         | <span data-ttu-id="195be-380">4</span><span class="sxs-lookup"><span data-stu-id="195be-380">4</span></span> |
| <span data-ttu-id="195be-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="195be-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>     | <span data-ttu-id="195be-382">5</span><span class="sxs-lookup"><span data-stu-id="195be-382">5</span></span> |
| <span data-ttu-id="195be-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="195be-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span> | <span data-ttu-id="195be-384">6</span><span class="sxs-lookup"><span data-stu-id="195be-384">6</span></span> |
| <span data-ttu-id="195be-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="195be-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>  | <span data-ttu-id="195be-386">7</span><span class="sxs-lookup"><span data-stu-id="195be-386">7</span></span> |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="195be-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="195be-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>

<span data-ttu-id="195be-388">Wykonaj kodowanie liniowe zestawu IOCTL w interfejsie przechwytywania zmian-ACM</span><span class="sxs-lookup"><span data-stu-id="195be-388">Perform IOCTL Set Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-389">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-389">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="195be-390">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-390">Description</span></span>

<span data-ttu-id="195be-391">Ta funkcja jest wywoływana, gdy aplikacja wymaga ustawienia parametrów kodowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="195be-391">This function is called when an application needs to Set the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-392">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-392">Parameters</span></span>

- <span data-ttu-id="195be-393">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-393">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="195be-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="195be-395">**parametr**: wskaźnik do struktury parametru wiersza:</span><span class="sxs-lookup"><span data-stu-id="195be-395">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="195be-396">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-396">Return Value</span></span>

<span data-ttu-id="195be-397">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-397">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="195be-398">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-398">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="195be-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="195be-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>

<span data-ttu-id="195be-400">Wykonaj polecenie IOCTL pobieranie kodowania wierszy w interfejsie przechwytywania zmian-ACM</span><span class="sxs-lookup"><span data-stu-id="195be-400">Perform IOCTL Get Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-401">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-401">Prototype</span></span>

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="195be-402">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-402">Description</span></span>

<span data-ttu-id="195be-403">Ta funkcja jest wywoływana, gdy aplikacja wymaga pobrania parametrów kodowania wiersza.</span><span class="sxs-lookup"><span data-stu-id="195be-403">This function is called when an application needs to Get the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-404">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-404">Parameters</span></span>

- <span data-ttu-id="195be-405">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-405">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="195be-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span></span>
- <span data-ttu-id="195be-407">**parametr**: wskaźnik do struktury parametru wiersza:</span><span class="sxs-lookup"><span data-stu-id="195be-407">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="195be-408">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-408">Return Value</span></span>

- <span data-ttu-id="195be-409">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-409">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="195be-410">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-410">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a><span data-ttu-id="195be-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="195be-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>

<span data-ttu-id="195be-412">Wykonaj polecenie IOCTL Pobierz stan wiersza w interfejsie przechwytywania zmian-ACM</span><span class="sxs-lookup"><span data-stu-id="195be-412">Perform IOCTL Get Line State on the CDC-ACM interface</span></span>

## <a name="prototype"></a><span data-ttu-id="195be-413">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-413">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="195be-414">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-414">Description</span></span>

<span data-ttu-id="195be-415">Ta funkcja jest wywoływana, gdy aplikacja wymaga pobrania parametrów stanu wiersza.</span><span class="sxs-lookup"><span data-stu-id="195be-415">This function is called when an application needs to Get the Line State parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-416">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-416">Parameters</span></span>

- <span data-ttu-id="195be-417">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-417">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="195be-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>
- <span data-ttu-id="195be-419">**parametr**: wskaźnik do struktury parametru wiersza:</span><span class="sxs-lookup"><span data-stu-id="195be-419">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="195be-420">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-420">Return Value</span></span>

- <span data-ttu-id="195be-421">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-421">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="195be-422">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-422">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="195be-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="195be-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>

<span data-ttu-id="195be-424">Wykonaj ustawiony stan wiersza polecenia IOCTL w interfejsie przechwytywania zmian-ACM</span><span class="sxs-lookup"><span data-stu-id="195be-424">Perform IOCTL Set Line State on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-425">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-425">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="195be-426">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-426">Description</span></span>

<span data-ttu-id="195be-427">Ta funkcja jest wywoływana, gdy aplikacja wymaga pobrania parametrów stanu wiersza</span><span class="sxs-lookup"><span data-stu-id="195be-427">This function is called when an application needs to Get the Line State parameters</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-428">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-428">Parameters</span></span>

- <span data-ttu-id="195be-429">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-429">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="195be-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="195be-431">**parametr**: wskaźnik do struktury parametru wiersza:</span><span class="sxs-lookup"><span data-stu-id="195be-431">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="195be-432">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-432">Return Value</span></span>

- <span data-ttu-id="195be-433">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-433">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="195be-434">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-434">Example</span></span>

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a><span data-ttu-id="195be-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="195be-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>

<span data-ttu-id="195be-436">Wykonaj potok PRZERWAnia IOCTL w interfejsie przechwytywania zmian-ACM</span><span class="sxs-lookup"><span data-stu-id="195be-436">Perform IOCTL ABORT PIPE on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-437">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-437">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="195be-438">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-438">Description</span></span>

<span data-ttu-id="195be-439">Ta funkcja jest wywoływana, gdy aplikacja musi przerwać potok.</span><span class="sxs-lookup"><span data-stu-id="195be-439">This function is called when an application needs to abort a pipe.</span></span> <span data-ttu-id="195be-440">Na przykład, aby przerwać trwający zapis, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT powinien zostać przesłany jako parametr.</span><span class="sxs-lookup"><span data-stu-id="195be-440">For example, to abort an ongoing write, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT should be passed as the parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-441">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-441">Parameters</span></span>

- <span data-ttu-id="195be-442">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-442">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="195be-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>
- <span data-ttu-id="195be-444">**Parameter**: kierunek potoku:</span><span class="sxs-lookup"><span data-stu-id="195be-444">**parameter**: The pipe direction:</span></span>

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a><span data-ttu-id="195be-445">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-445">Return Value</span></span>

- <span data-ttu-id="195be-446">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-446">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="195be-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0X53) nieprawidłowy kierunek potoku.</span><span class="sxs-lookup"><span data-stu-id="195be-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Invalid pipe direction.</span></span>

### <a name="example"></a><span data-ttu-id="195be-448">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-448">Example</span></span>

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a><span data-ttu-id="195be-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="195be-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>

<span data-ttu-id="195be-450">Wykonaj transmisję IOCTL na interfejsie przechwytywania zmian-ACM</span><span class="sxs-lookup"><span data-stu-id="195be-450">Perform IOCTL Transmission Start on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-451">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-451">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="195be-452">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-452">Description</span></span>

<span data-ttu-id="195be-453">Ta funkcja jest wywoływana, gdy aplikacja chce używać transmisji z wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="195be-453">This function is called when an application wants to use transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-454">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-454">Parameters</span></span>

- <span data-ttu-id="195be-455">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-455">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="195be-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>
- <span data-ttu-id="195be-457">**parametr**: wskaźnik do struktury parametru rozpoczęcia transmisji:</span><span class="sxs-lookup"><span data-stu-id="195be-457">**parameter**: Pointer to the Start Transmission parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="195be-458">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-458">Return Value</span></span>

- <span data-ttu-id="195be-459">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-459">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="195be-460">**UX_ERROR** (0Xff) transmisja została już rozpoczęta.</span><span class="sxs-lookup"><span data-stu-id="195be-460">**UX_ERROR** (0xFF) Transmission already started.</span></span>
- <span data-ttu-id="195be-461">**UX_MEMORY_INSUFFICIENT** (0x12) alokacja pamięci nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="195be-461">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="195be-462">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-462">Example</span></span>

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a><span data-ttu-id="195be-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="195be-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>

<span data-ttu-id="195be-464">Wykonaj zatrzymanie transmisji IOCTL w interfejsie przechwytywania zmian-ACM</span><span class="sxs-lookup"><span data-stu-id="195be-464">Perform IOCTL Transmission Stop on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-465">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-465">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="195be-466">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-466">Description</span></span>

<span data-ttu-id="195be-467">Ta funkcja jest wywoływana, gdy aplikacja chce przestać używać transmisji z wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="195be-467">This function is called when an application wants to stop using transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-468">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-468">Parameters</span></span>

- <span data-ttu-id="195be-469">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-469">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span><span class="sxs-lookup"><span data-stu-id="195be-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span></span>
- <span data-ttu-id="195be-471">**parametr**: nieużywany</span><span class="sxs-lookup"><span data-stu-id="195be-471">**parameter**: Not used</span></span>

### <a name="return-value"></a><span data-ttu-id="195be-472">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-472">Return Value</span></span>

- <span data-ttu-id="195be-473">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-473">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="195be-474">**UX_ERROR** (0Xff) brak ciągłej transmisji.</span><span class="sxs-lookup"><span data-stu-id="195be-474">**UX_ERROR** (0xFF) No ongoing transmission.</span></span>

### <a name="example"></a><span data-ttu-id="195be-475">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-475">Example</span></span>

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a><span data-ttu-id="195be-476">ux_device_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="195be-476">ux_device_class_cdc_acm_read</span></span>

<span data-ttu-id="195be-477">Odczytaj z potoku przechwytywania zmian-ACM</span><span class="sxs-lookup"><span data-stu-id="195be-477">Read from CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-478">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-478">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="195be-479">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-479">Description</span></span>

<span data-ttu-id="195be-480">Ta funkcja jest wywoływana, gdy aplikacja musi odczytywać dane z potoku danych OUT z hosta (z urządzenia).</span><span class="sxs-lookup"><span data-stu-id="195be-480">This function is called when an application needs to read from the OUT data pipe (OUT from the host, IN from the device).</span></span> <span data-ttu-id="195be-481">Jest blokowany.</span><span class="sxs-lookup"><span data-stu-id="195be-481">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-482">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-482">Parameters</span></span>

- <span data-ttu-id="195be-483">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-483">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-484">**bufor**: adres bufora, w którym będą przechowywane dane.</span><span class="sxs-lookup"><span data-stu-id="195be-484">**buffer**: Buffer address where data will be stored.</span></span>
- <span data-ttu-id="195be-485">**requested_length**: Maksymalna oczekiwana długość.</span><span class="sxs-lookup"><span data-stu-id="195be-485">**requested_length**: The maximum length we expect.</span></span>
- <span data-ttu-id="195be-486">**actual_length**: długość zwrócona do buforu.</span><span class="sxs-lookup"><span data-stu-id="195be-486">**actual_length**: The length returned into the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="195be-487">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-487">Return Value</span></span>

- <span data-ttu-id="195be-488">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-488">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="195be-489">Urządzenie **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) nie jest już w skonfigurowanym stanie.</span><span class="sxs-lookup"><span data-stu-id="195be-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="195be-490">**UX_TRANSFER_NO_ANSWER** (0X22) Brak odpowiedzi z urządzenia.</span><span class="sxs-lookup"><span data-stu-id="195be-490">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="195be-491">Urządzenie zostało prawdopodobnie rozłączone w czasie oczekiwania na przeniesienie.</span><span class="sxs-lookup"><span data-stu-id="195be-491">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="195be-492">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-492">Example</span></span>

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a><span data-ttu-id="195be-493">ux_device_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="195be-493">ux_device_class_cdc_acm_write</span></span>

<span data-ttu-id="195be-494">Zapisywanie w potoku przechwytywania</span><span class="sxs-lookup"><span data-stu-id="195be-494">Write to a CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-495">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-495">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="195be-496">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-496">Description</span></span>

<span data-ttu-id="195be-497">Ta funkcja jest wywoływana, gdy aplikacja musi zapisywać w potoku danych (w ramach hosta z poziomu urządzenia).</span><span class="sxs-lookup"><span data-stu-id="195be-497">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="195be-498">Jest blokowany.</span><span class="sxs-lookup"><span data-stu-id="195be-498">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-499">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-499">Parameters</span></span>

- <span data-ttu-id="195be-500">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-500">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-501">**bufor**: adres bufora, w którym są przechowywane dane.</span><span class="sxs-lookup"><span data-stu-id="195be-501">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="195be-502">**requested_length**: długość buforu do zapisania.</span><span class="sxs-lookup"><span data-stu-id="195be-502">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="195be-503">**actual_length**: długość zwrócona do buforu po wykonaniu operacji zapisu.</span><span class="sxs-lookup"><span data-stu-id="195be-503">**actual_length**: The length returned into the buffer after write is performed.</span></span>

### <a name="return-value"></a><span data-ttu-id="195be-504">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-504">Return Value</span></span>
- <span data-ttu-id="195be-505">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-505">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="195be-506">Urządzenie **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) nie jest już w skonfigurowanym stanie.</span><span class="sxs-lookup"><span data-stu-id="195be-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="195be-507">**UX_TRANSFER_NO_ANSWER** (0X22) Brak odpowiedzi z urządzenia.</span><span class="sxs-lookup"><span data-stu-id="195be-507">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="195be-508">Urządzenie zostało prawdopodobnie rozłączone w czasie oczekiwania na przeniesienie.</span><span class="sxs-lookup"><span data-stu-id="195be-508">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="195be-509">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-509">Example</span></span>

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a><span data-ttu-id="195be-510">ux_device_class_cdc_acm_write_with_callback</span><span class="sxs-lookup"><span data-stu-id="195be-510">ux_device_class_cdc_acm_write_with_callback</span></span>

<span data-ttu-id="195be-511">Zapisywanie w potoku funkcji przechwytywania</span><span class="sxs-lookup"><span data-stu-id="195be-511">Writing to a CDC-ACM pipe with callback</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-512">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-512">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a><span data-ttu-id="195be-513">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-513">Description</span></span>

<span data-ttu-id="195be-514">Ta funkcja jest wywoływana, gdy aplikacja musi zapisywać w potoku danych (w ramach hosta z poziomu urządzenia).</span><span class="sxs-lookup"><span data-stu-id="195be-514">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="195be-515">Ta funkcja nie jest zablokowana i uzupełnianie zostanie wykonane za pomocą wywołania zwrotnego w UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span><span class="sxs-lookup"><span data-stu-id="195be-515">This function is non-blocking and the completion will be done through a callback set in UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-516">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-516">Parameters</span></span>

- <span data-ttu-id="195be-517">**cdc_acm**: wskaźnik do wystąpienia klasy przechwytywania.</span><span class="sxs-lookup"><span data-stu-id="195be-517">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="195be-518">**bufor**: adres bufora, w którym są przechowywane dane.</span><span class="sxs-lookup"><span data-stu-id="195be-518">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="195be-519">**requested_length**: długość buforu do zapisania.</span><span class="sxs-lookup"><span data-stu-id="195be-519">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="195be-520">**actual_length**: długość zwrócona do buforu po wykonaniu zapisu</span><span class="sxs-lookup"><span data-stu-id="195be-520">**actual_length**: The length returned into the buffer after write is performed</span></span>

### <a name="return-value"></a><span data-ttu-id="195be-521">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-521">Return Value</span></span>

- <span data-ttu-id="195be-522">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-522">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="195be-523">Urządzenie **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) nie jest już w skonfigurowanym stanie.</span><span class="sxs-lookup"><span data-stu-id="195be-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="195be-524">**UX_TRANSFER_NO_ANSWER** (0X22) Brak odpowiedzi z urządzenia.</span><span class="sxs-lookup"><span data-stu-id="195be-524">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="195be-525">Urządzenie zostało prawdopodobnie rozłączone w czasie oczekiwania na przeniesienie.</span><span class="sxs-lookup"><span data-stu-id="195be-525">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="195be-526">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-526">Example</span></span>

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a><span data-ttu-id="195be-527">Przechwytywanie urządzenia USB — Klasa ECM</span><span class="sxs-lookup"><span data-stu-id="195be-527">USB Device CDC-ECM Class</span></span>

<span data-ttu-id="195be-528">Klasa przełączania urządzenia USB ECM umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzeniem Ethernet.</span><span class="sxs-lookup"><span data-stu-id="195be-528">The USB device CDC-ECM class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="195be-529">Ta klasa jest oparta na standardzie USB i jest podzbiorem standardu przechwytywania zmian.</span><span class="sxs-lookup"><span data-stu-id="195be-529">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="195be-530">Architektura urządzenia zgodna z przeskakującą zmianą musi być zadeklarowana przez stos urządzeń.</span><span class="sxs-lookup"><span data-stu-id="195be-530">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="195be-531">Poniżej znajduje się przykład.</span><span class="sxs-lookup"><span data-stu-id="195be-531">An example is found here below.</span></span>

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

<span data-ttu-id="195be-532">Klasa przechwytywania zmian-ECM używa bardzo podobnego podejścia deskryptora urządzenia do przechwytywania zmian-ACM, a także wymaga deskryptora IAD.</span><span class="sxs-lookup"><span data-stu-id="195be-532">The CDC-ECM class uses a very similar device descriptor approach to the CDC-ACM and also requires an IAD descriptor.</span></span> <span data-ttu-id="195be-533">Zobacz Klasa przechwytywania zmian-ACM dla definicji.</span><span class="sxs-lookup"><span data-stu-id="195be-533">See the CDC-ACM class for definition.</span></span>

<span data-ttu-id="195be-534">Oprócz zwykłej struktury urządzeń Funkcja przechwytywania zmian ECM wymaga specjalnych deskryptorów ciągów.</span><span class="sxs-lookup"><span data-stu-id="195be-534">In addition to the regular device framework, the CDC-ECM requires special string descriptors.</span></span> <span data-ttu-id="195be-535">Poniżej znajduje się przykład.</span><span class="sxs-lookup"><span data-stu-id="195be-535">An example is given below.</span></span>

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

<span data-ttu-id="195be-536">Deskryptor ciągu adresu MAC jest używany przez klasę "reECMd" w celu odpowiedzi na zapytania hosta dotyczące adresu MAC, na którym urządzenie odpowiada, w protokole TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="195be-536">The MAC address string descriptor is used by the CDC-ECM class to reply to the host queries as to what MAC address the device is answering to at the TCP/IP protocol.</span></span> <span data-ttu-id="195be-537">Może być ustawiony na wybór urządzenia, ale musi być tutaj zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="195be-537">It can be set to the device choice but must be defined here.</span></span>

<span data-ttu-id="195be-538">Zainicjowanie klasy przechwytywania zmian-ECM jest następujące.</span><span class="sxs-lookup"><span data-stu-id="195be-538">The initialization of the CDC-ECM class is as follows.</span></span>

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

<span data-ttu-id="195be-539">Inicjalizacja tej klasy oczekuje tego samego wywołania zwrotnego funkcji dla aktywacji i dezaktywacji, chociaż tutaj jako ćwiczenie są ustawione na wartość NULL, co oznacza, że wywołanie zwrotne nie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="195be-539">The initialization of this class expects the same function callback for activation and deactivation, although here as an exercise they are set to NULL so that no callback is performed.</span></span>

<span data-ttu-id="195be-540">Następne parametry są dla definicji identyfikatorów węzłów.</span><span class="sxs-lookup"><span data-stu-id="195be-540">The next parameters are for the definition of the node IDs.</span></span> <span data-ttu-id="195be-541">2 węzły są niezbędne do przechwytywania zmian-ECM, węzła lokalnego i węzła zdalnego.</span><span class="sxs-lookup"><span data-stu-id="195be-541">2 Nodes are necessary for the CDC-ECM, a local node and a remote node.</span></span> <span data-ttu-id="195be-542">Węzeł lokalny określa adres MAC urządzenia, natomiast węzeł zdalny określa adres MAC hosta.</span><span class="sxs-lookup"><span data-stu-id="195be-542">The local node specifies the MAC address of the device, while the remote node specifies the MAC address of the host.</span></span> <span data-ttu-id="195be-543">Węzeł zdalny musi być taki sam jak jeden zadeklarowany w deskryptorze ciągu Framework urządzenia.</span><span class="sxs-lookup"><span data-stu-id="195be-543">The remote node must be the same one as the one declared in the device framework string descriptor.</span></span>

<span data-ttu-id="195be-544">Klasa przechwytywania zmian-ECM ma wbudowane interfejsy API służące do transferowania danych, ale są one ukryte dla aplikacji, ponieważ aplikacja użytkownika komunikuje się z urządzeniem USB Ethernet za pośrednictwem usługi NetX.</span><span class="sxs-lookup"><span data-stu-id="195be-544">The CDC-ECM class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="195be-545">Klasa USBX przechwytywania-ECM jest ściśle związana z stosem sieci usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="195be-545">The USBX CDC-ECM class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="195be-546">Aplikacja, która korzysta z klasy NetX i USBX Reporting-ECM, umożliwia aktywowanie stosu sieci NetX w zwykły sposób, ale dodatkowo wymaga aktywowania stosu sieci USB w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="195be-546">An application using both NetX and USBX CDC-ECM class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="195be-547">Stos sieci USB musi być aktywowany tylko raz i nie jest specyficzny dla CDCECM, ale jest wymagany przez dowolną klasę USB wymagającą usług NetX Services.</span><span class="sxs-lookup"><span data-stu-id="195be-547">The USB network stack needs to be activated only once and is not specific to CDCECM but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="195be-548">Klasa przechwytywania zmian-ECM jest rozpoznawana przez hosty z systemem MAC OS i Linux.</span><span class="sxs-lookup"><span data-stu-id="195be-548">The CDC-ECM class will be recognized by MAC OS and Linux hosts.</span></span> <span data-ttu-id="195be-549">Nie ma jednak sterownika dostarczonego przez system Microsoft Windows do rozpoznawania natywnych danych przechwytywania ECM.</span><span class="sxs-lookup"><span data-stu-id="195be-549">But there is no driver supplied by Microsoft Windows to recognize CDC-ECM natively.</span></span> <span data-ttu-id="195be-550">Niektóre produkty komercyjne istnieją dla platform systemu Windows i dostarczają własnych plików inf.</span><span class="sxs-lookup"><span data-stu-id="195be-550">Some commercial products do exist for Windows platforms and they supply their own .inf file.</span></span> <span data-ttu-id="195be-551">Ten plik musi być zmodyfikowany w taki sam sposób, jak szablon inf przechwytywania zmian systemu w celu dopasowania do identyfikatora PID/VID urządzenia sieciowego USB.</span><span class="sxs-lookup"><span data-stu-id="195be-551">This file will need to be modified the same way as the CDC-ACM inf template to match the PID/VID of the USB network device.</span></span>

## <a name="usb-device-hid-class"></a><span data-ttu-id="195be-552">Klasa HID urządzenia USB</span><span class="sxs-lookup"><span data-stu-id="195be-552">USB Device HID Class</span></span>

<span data-ttu-id="195be-553">Klasa HID urządzenia USB umożliwia systemowi hosta USB łączenie się z urządzeniem HID z konkretnymi możliwościami klienta HID.</span><span class="sxs-lookup"><span data-stu-id="195be-553">The USB device HID class allows for a USB host system to connect to a HID device with specific HID client capabilities.</span></span>

<span data-ttu-id="195be-554">Klasa urządzenia HID USBX jest stosunkowo prosta w porównaniu do strony hosta.</span><span class="sxs-lookup"><span data-stu-id="195be-554">USBX HID device class is relatively simple compared to the host side.</span></span> <span data-ttu-id="195be-555">Jest ściśle powiązane z zachowaniem urządzenia i jego deskryptora HID.</span><span class="sxs-lookup"><span data-stu-id="195be-555">It is closely tied to the behavior of the device and its HID descriptor.</span></span>

<span data-ttu-id="195be-556">Każdy klient HID musi najpierw zdefiniować strukturę urządzenia HID, jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="195be-556">Any HID client requires first to define a HID device framework as the example below.</span></span>

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

<span data-ttu-id="195be-557">Struktura HID zawiera deskryptor interfejsu, który opisuje klasę HID i podklasę urządzenia HID.</span><span class="sxs-lookup"><span data-stu-id="195be-557">The HID framework contains an interface descriptor that describes the HID class and the HID device subclass.</span></span> <span data-ttu-id="195be-558">Interfejs HID może być klasą autonomiczną lub częścią urządzenia złożonego.</span><span class="sxs-lookup"><span data-stu-id="195be-558">The HID interface can be a standalone class or part of a composite device.</span></span>

<span data-ttu-id="195be-559">Obecnie Klasa USBX HID nie obsługuje wielu identyfikatorów raportów, ponieważ większość aplikacji wymaga tylko jednego identyfikatora (identyfikator zero).</span><span class="sxs-lookup"><span data-stu-id="195be-559">Currently, the USBX HID class does not support multiple report IDs, as most applications only require one ID (ID zero).</span></span> <span data-ttu-id="195be-560">Jeśli potrzebujesz wielu identyfikatorów raportów, skontaktuj się z nami.</span><span class="sxs-lookup"><span data-stu-id="195be-560">If multiple report IDs is a feature you are interested in, please contact us.</span></span>

<span data-ttu-id="195be-561">Inicjalizacja klasy HID odbywa się tak, jak na przykład przy użyciu klawiatury USB.</span><span class="sxs-lookup"><span data-stu-id="195be-561">The initialization of the HID class is as follow, using a USB keyboard as an example.</span></span>

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

<span data-ttu-id="195be-562">Aplikacja musi przekazać do klasy HID deskryptor raportu HID i jego długość.</span><span class="sxs-lookup"><span data-stu-id="195be-562">The application needs to pass to the HID class a HID report descriptor and its length.</span></span> <span data-ttu-id="195be-563">Deskryptor raportu to kolekcja elementów, które opisują urządzenie.</span><span class="sxs-lookup"><span data-stu-id="195be-563">The report descriptor is a collection of items that describe the device.</span></span> <span data-ttu-id="195be-564">Aby uzyskać więcej informacji na temat gramatyki HID, zobacz specyfikację klasy USB HID.</span><span class="sxs-lookup"><span data-stu-id="195be-564">For more information on the HID grammar refer to the HID USB class specification.</span></span>

<span data-ttu-id="195be-565">Oprócz deskryptora raportu aplikacja przekazuje wywołanie z powrotem, gdy wystąpi zdarzenie HID.</span><span class="sxs-lookup"><span data-stu-id="195be-565">In addition to the report descriptor, the application passes a call back when a HID event happens.</span></span>

<span data-ttu-id="195be-566">Klasa HID USBX obsługuje następujące standardowe polecenia HID z hosta.</span><span class="sxs-lookup"><span data-stu-id="195be-566">The USBX HID class supports the following standard HID commands from the host.</span></span>

| <span data-ttu-id="195be-567">Nazwa polecenia</span><span class="sxs-lookup"><span data-stu-id="195be-567">Command name</span></span>                             | <span data-ttu-id="195be-568">Wartość</span><span class="sxs-lookup"><span data-stu-id="195be-568">Value</span></span> | <span data-ttu-id="195be-569">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-569">Description</span></span>                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| <span data-ttu-id="195be-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span><span class="sxs-lookup"><span data-stu-id="195be-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span></span>   | <span data-ttu-id="195be-571">0x01</span><span class="sxs-lookup"><span data-stu-id="195be-571">0x01</span></span>  | <span data-ttu-id="195be-572">Pobierz Raport z urządzenia</span><span class="sxs-lookup"><span data-stu-id="195be-572">Get a report from the device</span></span>                     |
| <span data-ttu-id="195be-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span><span class="sxs-lookup"><span data-stu-id="195be-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span></span>     | <span data-ttu-id="195be-574">0x02</span><span class="sxs-lookup"><span data-stu-id="195be-574">0x02</span></span>  | <span data-ttu-id="195be-575">Pobierz częstotliwość bezczynności punktu końcowego przerwania</span><span class="sxs-lookup"><span data-stu-id="195be-575">Get the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="195be-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="195be-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span></span> | <span data-ttu-id="195be-577">0x03</span><span class="sxs-lookup"><span data-stu-id="195be-577">0x03</span></span>  | <span data-ttu-id="195be-578">Pobieranie protokołu uruchomionego na urządzeniu</span><span class="sxs-lookup"><span data-stu-id="195be-578">Get the protocol running on the device</span></span>           |
| <span data-ttu-id="195be-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span><span class="sxs-lookup"><span data-stu-id="195be-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span></span>   | <span data-ttu-id="195be-580">0x09</span><span class="sxs-lookup"><span data-stu-id="195be-580">0x09</span></span>  | <span data-ttu-id="195be-581">Ustawianie raportu na urządzeniu</span><span class="sxs-lookup"><span data-stu-id="195be-581">Set a report to the device</span></span>                       |
| <span data-ttu-id="195be-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span><span class="sxs-lookup"><span data-stu-id="195be-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span></span>     | <span data-ttu-id="195be-583">0x0A</span><span class="sxs-lookup"><span data-stu-id="195be-583">0x0a</span></span>  | <span data-ttu-id="195be-584">Ustaw częstotliwość bezczynności punktu końcowego przerwania</span><span class="sxs-lookup"><span data-stu-id="195be-584">Set the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="195be-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="195be-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span></span> | <span data-ttu-id="195be-586">0x0b</span><span class="sxs-lookup"><span data-stu-id="195be-586">0x0b</span></span>  | <span data-ttu-id="195be-587">Pobieranie protokołu uruchomionego na urządzeniu</span><span class="sxs-lookup"><span data-stu-id="195be-587">Get the protocol running on the device</span></span>           |

<span data-ttu-id="195be-588">Raport pobieranie i Ustawianie jest najczęściej używanymi poleceniami przez HID do przesyłania danych z powrotem i do przodu między hostem i urządzeniem.</span><span class="sxs-lookup"><span data-stu-id="195be-588">The Get and Set report are the most commonly used commands by HID to transfer data back and forth between the host and the device.</span></span> <span data-ttu-id="195be-589">Najczęściej Host wysyła dane w punkcie końcowym kontroli, ale może odbierać dane w punkcie końcowym przerwania lub przez wydawanie GET_REPORT polecenia w celu pobrania danych w punkcie końcowym sterowania.</span><span class="sxs-lookup"><span data-stu-id="195be-589">Most commonly the host sends data on the control endpoint but can receive data either on the interrupt endpoint or by issuing a GET_REPORT command to fetch the data on the control endpoint.</span></span>

<span data-ttu-id="195be-590">Klasa HID może wysyłać dane z powrotem do hosta w punkcie końcowym przerwania za pomocą funkcji ux_device_class_hid_event_set.</span><span class="sxs-lookup"><span data-stu-id="195be-590">The HID class can send data back to the host on the interrupt endpoint by using the ux_device_class_hid_event_set function.</span></span>

### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="195be-591">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="195be-591">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="195be-592">Ustawianie zdarzenia na klasę HID</span><span class="sxs-lookup"><span data-stu-id="195be-592">Setting an event to the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-593">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-593">Prototype</span></span>

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="195be-594">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-594">Description</span></span>

<span data-ttu-id="195be-595">Ta funkcja jest wywoływana, gdy aplikacja wymaga wysłania zdarzenia HID z powrotem do hosta.</span><span class="sxs-lookup"><span data-stu-id="195be-595">This function is called when an application needs to send a HID event back to the host.</span></span> <span data-ttu-id="195be-596">Funkcja nie blokuje, tylko umieszcza raport w kolejce cyklicznej i zwraca do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="195be-596">The function is not blocking, it merely puts the report into a circular queue and returns to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-597">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-597">Parameters</span></span>

- <span data-ttu-id="195be-598">**HID**: wskaźnik do wystąpienia klasy HID.</span><span class="sxs-lookup"><span data-stu-id="195be-598">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="195be-599">**hid_event**: wskaźnik do struktury zdarzenia HID.</span><span class="sxs-lookup"><span data-stu-id="195be-599">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="return-value"></a><span data-ttu-id="195be-600">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="195be-600">Return Value</span></span>

- <span data-ttu-id="195be-601">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="195be-601">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="195be-602">**UX_ERROR** (0Xff) błąd: Brak dostępnego miejsca w kolejce cyklicznej.</span><span class="sxs-lookup"><span data-stu-id="195be-602">**UX_ERROR** (0xFF) Error no space available in circular queue.</span></span>

### <a name="example"></a><span data-ttu-id="195be-603">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-603">Example</span></span>

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

<span data-ttu-id="195be-604">Wywołanie zwrotne zdefiniowane podczas inicjowania klasy HID wykonuje przeciwieństwo do wysyłania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="195be-604">The callback defined at the initialization of the HID class performs the opposite of sending an event.</span></span> <span data-ttu-id="195be-605">Jest ona pobierana jako dane wejściowe dla zdarzenia wysyłanego przez hosta.</span><span class="sxs-lookup"><span data-stu-id="195be-605">It gets as input the event sent by the host.</span></span> <span data-ttu-id="195be-606">Prototyp wywołania zwrotnego jest następujący.</span><span class="sxs-lookup"><span data-stu-id="195be-606">The prototype of the callback is as follows.</span></span>

### <a name="hid_callback"></a><span data-ttu-id="195be-607">hid_callback</span><span class="sxs-lookup"><span data-stu-id="195be-607">hid_callback</span></span>

<span data-ttu-id="195be-608">Pobieranie zdarzenia z klasy HID</span><span class="sxs-lookup"><span data-stu-id="195be-608">Getting an event from the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="195be-609">Prototype</span><span class="sxs-lookup"><span data-stu-id="195be-609">Prototype</span></span>

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="195be-610">Opis</span><span class="sxs-lookup"><span data-stu-id="195be-610">Description</span></span>

<span data-ttu-id="195be-611">Ta funkcja jest wywoływana, gdy Host wysyła raport HID do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="195be-611">This function is called when the host sends a HID report to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="195be-612">Parametry</span><span class="sxs-lookup"><span data-stu-id="195be-612">Parameters</span></span>

- <span data-ttu-id="195be-613">**HID**: wskaźnik do wystąpienia klasy HID.</span><span class="sxs-lookup"><span data-stu-id="195be-613">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="195be-614">**hid_event**: wskaźnik do struktury zdarzenia HID.</span><span class="sxs-lookup"><span data-stu-id="195be-614">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="example"></a><span data-ttu-id="195be-615">Przykład</span><span class="sxs-lookup"><span data-stu-id="195be-615">Example</span></span>

<span data-ttu-id="195be-616">Poniższy przykład pokazuje, jak interpretować zdarzenie dla klawiatury HID:</span><span class="sxs-lookup"><span data-stu-id="195be-616">The following example shows how to interpret an event for a HID keyboard:</span></span>

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
