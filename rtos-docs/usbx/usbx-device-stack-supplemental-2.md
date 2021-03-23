---
title: Rozdział 2 — zagadnienia dotyczące klas urządzeń USBX
description: Klasa RNDIS urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzeniem Ethernet. Ta klasa jest oparta na implementacji zastrzeżonej firmy Microsoft i jest zależna od platformy systemu Windows.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8104f00e192486f57fe9c22b2c83aa9a22954739
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824318"
---
# <a name="chapter-2---usbx-device-class-considerations"></a><span data-ttu-id="993e6-104">Rozdział 2 — zagadnienia dotyczące klas urządzeń USBX</span><span class="sxs-lookup"><span data-stu-id="993e6-104">Chapter 2 - USBX Device Class Considerations</span></span>

## <a name="usb-device-rndis-class"></a><span data-ttu-id="993e6-105">Klasa RNDIS urządzenia USB</span><span class="sxs-lookup"><span data-stu-id="993e6-105">USB Device RNDIS Class</span></span>

<span data-ttu-id="993e6-106">Klasa RNDIS urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzeniem Ethernet.</span><span class="sxs-lookup"><span data-stu-id="993e6-106">The USB device RNDIS class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="993e6-107">Ta klasa jest oparta na implementacji zastrzeżonej firmy Microsoft i jest zależna od platformy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="993e6-107">This class is based on the Microsoft proprietary implementation and is specific to Windows platforms.</span></span>

<span data-ttu-id="993e6-108">Architektura urządzenia zgodna z RNDIS musi być zadeklarowana przez stos urządzeń.</span><span class="sxs-lookup"><span data-stu-id="993e6-108">A RNDIS compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="993e6-109">Poniżej znajduje się przykład.</span><span class="sxs-lookup"><span data-stu-id="993e6-109">An example is found below.</span></span>

```C
unsigned char device_framework_full_speed[] = {
    /* VID: 0x04b4
    PID: 0x1127
    */

    /* Device Descriptor */
    0x12, /* bLength */
    0x01, /* bDescriptorType */
    0x10, 0x01, /* bcdUSB */
    0x02, /* bDeviceClass - CDC */
    0x00, /* bDeviceSubClass */
    0x00, /* bDeviceProtocol */
    0x40, /* bMaxPacketSize0 */
    0xb4, 0x04, /* idVendor */
    0x27, 0x11, /* idProduct */
    0x00, 0x01, /* bcdDevice */
    0x01, /* iManufacturer */
    0x02, /* iProduct */
    0x03, /* iSerialNumber */
    0x01, /* bNumConfigurations */

    /* Configuration Descriptor */
    0x09, /* bLength */
    0x02, /* bDescriptorType */
    0x38, 0x00, /* wTotalLength */
    0x02, /* bNumInterfaces */
    0x01, /* bConfigurationValue */
    0x00, /* iConfiguration */
    0x40, /* bmAttributes - Self-powered */
    0x00, /* bMaxPower */

    /* Interface Association Descriptor */
    0x08, /* bLength */
    0x0b, /* bDescriptorType */
    0x00, /* bFirstInterface */
    0x02, /* bInterfaceCount */
    0x02, /* bFunctionClass - CDC - Communication */
    0xff, /* bFunctionSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bFunctionProtocol - No class specific protocol required */
    0x00, /* iFunction */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x00, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x01, /* bNumEndpoints */
    0x02, /* bInterfaceClass - CDC - Communication */
    0xff, /* bInterfaceSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x83, /* bEndpointAddress */
    0x03, /* bmAttributes - Interrupt */
    0x08, 0x00, /* wMaxPacketSize */
    0xff, /* bInterval */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x01, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x02, /* bNumEndpoints */
    0x0a, /* bInterfaceClass - CDC - Data */
    0x00, /* bInterfaceSubClass - Should be 0x00 */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x02, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x81, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */
};
```

<span data-ttu-id="993e6-110">Klasa RNDIS używa bardzo podobnego podejścia do deskryptora urządzenia do przechwytywania danych typu reklasy — ACM i przechwytywania-ECM, a także wymaga deskryptora IAD.</span><span class="sxs-lookup"><span data-stu-id="993e6-110">The RNDIS class uses a very similar device descriptor approach to the CDC-ACM and CDC-ECM and also requires a IAD descriptor.</span></span> <span data-ttu-id="993e6-111">Zapoznaj się z klasą przechwytywania zmian-ACM dla definicji i wymagań dla deskryptora urządzenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-111">See the CDC-ACM class for definition and requirements for the device descriptor.</span></span>

<span data-ttu-id="993e6-112">Aktywacja klasy RNDIS jest następująca.</span><span class="sxs-lookup"><span data-stu-id="993e6-112">The activation of the RNDIS class is as follows.</span></span>

```C
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/

parameter.ux_slave_class_rndis_instance_activate = UX_NULL;
parameter.ux_slave_class_rndis_instance_deactivate = UX_NULL;

/* Define a local NODE ID. */

parameter.ux_slave_class_rndis_parameter_local_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_local_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_local_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_local_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_local_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */

parameter.ux_slave_class_rndis_parameter_remote_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_remote_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_remote_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_remote_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_remote_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_remote_node_id[5] = 0x79;

/* Set extra parameters used by the RNDIS query command with certain OIDs. */

parameter.ux_slave_class_rndis_parameter_vendor_id = 0x04b4 ;
parameter.ux_slave_class_rndis_parameter_driver_version = 0x1127;
ux_utility_memory_copy(parameter.ux_slave_class_rndis_parameter_vendor_description,
    "ELOGIC RNDIS", 12);

/* Initialize the device rndis class. This class owns both interfaces. */
status = ux_device_stack_class_register(_ux_system_slave_class_rndis_name,
    ux_device_class_rndis_entry, 1,0, &parameter);
```

<span data-ttu-id="993e6-113">Podobnie jak w przypadku opcji Przeciąganie do ECM, Klasa RNDIS wymaga 2 węzłów, jednego lokalnego i jednego zdalnego, ale nie wymaga się posiadania deskryptora ciągu opisującego węzeł zdalny.</span><span class="sxs-lookup"><span data-stu-id="993e6-113">As for the CDC-ECM, the RNDIS class requires 2 nodes, one local and one remote but there is no requirement to have a string descriptor describing the remote node.</span></span>

<span data-ttu-id="993e6-114">Jednak ze względu na własny mechanizm obsługi komunikatów firmy Microsoft wymagane są pewne dodatkowe parametry.</span><span class="sxs-lookup"><span data-stu-id="993e6-114">However due to Microsoft proprietary messaging mechanism, some extra parameters are required.</span></span> <span data-ttu-id="993e6-115">Najpierw należy przesłać identyfikator dostawcy.</span><span class="sxs-lookup"><span data-stu-id="993e6-115">First the vendor ID has to be passed.</span></span> <span data-ttu-id="993e6-116">Podobnie wersja sterownika RNDIS.</span><span class="sxs-lookup"><span data-stu-id="993e6-116">Likewise, the driver version of the RNDIS.</span></span> <span data-ttu-id="993e6-117">Należy również udzielić ciągu dostawcy.</span><span class="sxs-lookup"><span data-stu-id="993e6-117">A vendor string must also be given.</span></span>

<span data-ttu-id="993e6-118">Klasa RNDIS ma wbudowane interfejsy API do przesyłania danych w obu kierunkach, ale są ukryte dla aplikacji, ponieważ aplikacja użytkownika komunikuje się z urządzeniem USB Ethernet za pośrednictwem usługi NetX.</span><span class="sxs-lookup"><span data-stu-id="993e6-118">The RNDIS class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="993e6-119">Klasa USBX RNDIS jest ściśle związana z stosem sieci usługi Azure RTO NetX.</span><span class="sxs-lookup"><span data-stu-id="993e6-119">The USBX RNDIS class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="993e6-120">Aplikacja, która korzysta z klasy NetX i USBX RNDIS, będzie aktywować stos sieci NetX w zwykły sposób, ale dodatkowo należy aktywować stos sieci USB w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="993e6-120">An application using both NetX and USBX RNDIS class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="993e6-121">Stos sieci USB musi być aktywowany tylko raz i nie jest specyficzny dla RNDIS, ale jest wymagany przez dowolną klasę USB wymagającą usług NetX Services.</span><span class="sxs-lookup"><span data-stu-id="993e6-121">The USB network stack needs to be activated only once and is not specific to RNDIS but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="993e6-122">Klasa RNDIS nie zostanie rozpoznana przez hosty z systemem MAC OS i Linux zgodnie z konkretnymi systemami operacyjnymi firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="993e6-122">The RNDIS class will not be recognized by MAC OS and Linux hosts as it is specific to Microsoft operating systems.</span></span> <span data-ttu-id="993e6-123">Na platformach systemu Windows plik inf musi znajdować się na hoście, który jest zgodny z deskryptorem urządzenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-123">On windows platforms a .inf file needs to be present on the host that matches the device descriptor.</span></span> <span data-ttu-id="993e6-124">Firma Microsoft dostarcza szablon klasy RNDIS i znajduje się w katalogu usbx_windows_host_files.</span><span class="sxs-lookup"><span data-stu-id="993e6-124">Microsoft supplies a template for the RNDIS class and it can be found in the usbx_windows_host_files directory.</span></span> <span data-ttu-id="993e6-125">W przypadku nowszej wersji systemu Windows należy użyć pliku RNDIS_Template. inf.</span><span class="sxs-lookup"><span data-stu-id="993e6-125">For more recent version of Windows the file RNDIS_Template.inf should be used.</span></span> <span data-ttu-id="993e6-126">Ten plik musi zostać zmodyfikowany w celu odzwierciedlenia identyfikatora PID/VID używanego przez urządzenie.</span><span class="sxs-lookup"><span data-stu-id="993e6-126">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="993e6-127">Identyfikator PID/VID będzie charakterystyczny dla klienta końcowego, gdy firma i produkt zostaną zarejestrowane przy użyciu portu USB.</span><span class="sxs-lookup"><span data-stu-id="993e6-127">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="993e6-128">W pliku inf pola do zmodyfikowania znajdują się tutaj.</span><span class="sxs-lookup"><span data-stu-id="993e6-128">In the inf file, the fields to modify are located here.</span></span>

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

<span data-ttu-id="993e6-129">W środowisku urządzenia urządzenia RNDIS Identyfikator PID/VID jest przechowywany w deskryptorze urządzenia (patrz deskryptor urządzenia zadeklarowany powyżej)</span><span class="sxs-lookup"><span data-stu-id="993e6-129">In the device framework of the RNDIS device, the PID/VID are stored in the device descriptor (see the device descriptor declared above)</span></span>

<span data-ttu-id="993e6-130">W przypadku odnajdywania urządzenia USB RNDIS przez systemy hosta USB program zainstaluje interfejs sieciowy, a urządzenie może być używane z stosem protokołu sieciowego.</span><span class="sxs-lookup"><span data-stu-id="993e6-130">When a USB host systems discovers the USB RNDIS device, it will mount a network interface and the device can be used with network protocol stack.</span></span> <span data-ttu-id="993e6-131">Aby uzyskać informacje, zobacz system operacyjny hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-131">See the host Operating System for reference.</span></span>

## <a name="usb-device-dfu-class"></a><span data-ttu-id="993e6-132">Klasa DFU urządzenia USB</span><span class="sxs-lookup"><span data-stu-id="993e6-132">USB Device DFU Class</span></span>

<span data-ttu-id="993e6-133">Klasa DFU urządzenia USB umożliwia systemowi hosta USB aktualizowanie oprogramowania układowego urządzenia w oparciu o aplikację hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-133">The USB device DFU class allows for a USB host system to update the device firmware based on a host application.</span></span> <span data-ttu-id="993e6-134">Klasa DFU jest klasą standardową USB.</span><span class="sxs-lookup"><span data-stu-id="993e6-134">The DFU class is a USB-IF standard class.</span></span>

<span data-ttu-id="993e6-135">Klasa USBX DFU jest stosunkowo prosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-135">USBX DFU class is relatively simple.</span></span> <span data-ttu-id="993e6-136">Deskryptor urządzenia IT nie wymaga żadnego punktu końcowego kontrolki.</span><span class="sxs-lookup"><span data-stu-id="993e6-136">It device descriptor does not require anything but a control endpoint.</span></span> <span data-ttu-id="993e6-137">W większości przypadków ta klasa zostanie osadzona w urządzeniu kompozytowym USB.</span><span class="sxs-lookup"><span data-stu-id="993e6-137">Most of the time, this class will be embedded into a USB composite device.</span></span> <span data-ttu-id="993e6-138">Urządzenie może być takie samo jak urządzenie magazynujące lub urządzenie komunikacyjne, a dodany interfejs DFU może poinformować hosta, że urządzenie może być zaktualizowane przez oprogramowanie układowe na bieżąco.</span><span class="sxs-lookup"><span data-stu-id="993e6-138">The device can be anything such as a storage device or a comm device and the added DFU interface can inform the host that the device can have its firmware updated on the fly.</span></span>

<span data-ttu-id="993e6-139">Klasa DFU działa w 3 krokach.</span><span class="sxs-lookup"><span data-stu-id="993e6-139">The DFU class works in 3 steps.</span></span> <span data-ttu-id="993e6-140">Najpierw urządzenie jest instalowane jako normalne przy użyciu wyeksportowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="993e6-140">First the device mounts as normal using the class exported.</span></span> <span data-ttu-id="993e6-141">Aplikacja na hoście (Windows lub Linux) będzie korzystać z klasy DFU i wysyłać żądania resetowania urządzenia do trybu DFU.</span><span class="sxs-lookup"><span data-stu-id="993e6-141">An application on the host (Windows or Linux) will exercise the DFU class and send a request to reset the device into DFU mode.</span></span> <span data-ttu-id="993e6-142">Urządzenie pozostanie nieprzerwanie z magistrali przez krótki czas (wystarczające dla hosta i urządzenia w celu wykrycia sekwencji RESETowania), a po ponownym uruchomieniu urządzenie będzie działać wyłącznie w trybie DFU, czekając na wysłanie przez aplikację hosta uaktualnienia oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="993e6-142">The device will disappear from the bus for a short time (enough for the host and the device to detect a RESET sequence) and upon restarting, the device will be exclusively in DFU mode, waiting for the host application to send a firmware upgrade.</span></span> <span data-ttu-id="993e6-143">Po zakończeniu uaktualniania oprogramowania układowego aplikacja hosta resetuje urządzenie i po ponownym wyliczeniu zostanie przywrócone jego normalne działanie z nowym oprogramowaniem układowym.</span><span class="sxs-lookup"><span data-stu-id="993e6-143">When the firmware upgrade has been completed, the host application resets the device and upon re-enumeration the device will revert to its normal operation with the new firmware.</span></span>

<span data-ttu-id="993e6-144">Platforma urządzeń DFU będzie wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="993e6-144">A DFU device framework will look like this.</span></span>

```C
UCHAR device_framework_full_speed[] = {

    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x40,
    0x99, 0x99, 0x00, 0x00, 0x00, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x1b, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor for DFU. */
    0x09, 0x04, 0x00, 0x00, 0x00, 0xFE, 0x01, 0x01, 0x00,

    /* Functional descriptor for DFU. */
    0x09, 0x21, 0x0f, 0xE8, 0x03, 0x40, 0x00, 0x00,
    0x01,

};
```

<span data-ttu-id="993e6-145">W tym przykładzie deskryptor DFU nie jest skojarzony z żadną inną klasą.</span><span class="sxs-lookup"><span data-stu-id="993e6-145">In this example, the DFU descriptor is not associated with any other classes.</span></span> <span data-ttu-id="993e6-146">Ma prosty deskryptor interfejsu i nie dołączono do niego żadnych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="993e6-146">It has a simple interface descriptor and no other endpoints attached to it.</span></span> <span data-ttu-id="993e6-147">Istnieje deskryptor funkcjonalny opisujący szczegóły możliwości DFU urządzenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-147">There is a Functional descriptor that describes the specifics of the DFU capabilities of the device.</span></span>

<span data-ttu-id="993e6-148">Opis funkcji DFU są następujące.</span><span class="sxs-lookup"><span data-stu-id="993e6-148">The description of the DFU capabilities are as follows.</span></span>

| <span data-ttu-id="993e6-149">Nazwa</span><span class="sxs-lookup"><span data-stu-id="993e6-149">Name</span></span>             | <span data-ttu-id="993e6-150">Przesunięcie</span><span class="sxs-lookup"><span data-stu-id="993e6-150">Offset</span></span>  | <span data-ttu-id="993e6-151">Rozmiar</span><span class="sxs-lookup"><span data-stu-id="993e6-151">Size</span></span> | <span data-ttu-id="993e6-152">typ</span><span class="sxs-lookup"><span data-stu-id="993e6-152">type</span></span>      | <span data-ttu-id="993e6-153">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-153">Description</span></span> |
|------------------|----------|------|-----------|------------|
| <span data-ttu-id="993e6-154">bmAttributes</span><span class="sxs-lookup"><span data-stu-id="993e6-154">bmAttributes</span></span>  | <span data-ttu-id="993e6-155">2</span><span class="sxs-lookup"><span data-stu-id="993e6-155">2</span></span>     | <span data-ttu-id="993e6-156">1</span><span class="sxs-lookup"><span data-stu-id="993e6-156">1</span></span>   | <span data-ttu-id="993e6-157">Pole bitowe</span><span class="sxs-lookup"><span data-stu-id="993e6-157">Bit field</span></span> | <span data-ttu-id="993e6-158">Bit 3: urządzenie przeprowadzi sekwencję odłączania do magistrali, gdy odbierze żądanie DFU_DETACH.</span><span class="sxs-lookup"><span data-stu-id="993e6-158">Bit 3: device will perform a bus detach-attach sequence when it receives a DFU_DETACH request.</span></span> <span data-ttu-id="993e6-159">Host nie może wydać resetu USB.</span><span class="sxs-lookup"><span data-stu-id="993e6-159">The host must not issue a USB Reset.</span></span> <span data-ttu-id="993e6-160">(bitWillDetach) 0 = No 1 = Yes bit 2: urządzenie może komunikować się za pośrednictwem portu USB po fazie manifestu.</span><span class="sxs-lookup"><span data-stu-id="993e6-160">(bitWillDetach) 0 = no 1 = yes Bit 2: device is able to communicate via USB after Manifestation phase.</span></span> <span data-ttu-id="993e6-161">(bitManifestationTolerant) 0 = nie, należy zobaczyć Resetowanie magistrali 1 = Yes bit 1: możliwe do przekazania (bitCanUpload) 0 = 1 = Yes bit 0: pobieranie z obsługą (bitCanDnload) 0 = No 1 = tak</span><span class="sxs-lookup"><span data-stu-id="993e6-161">(bitManifestationTolerant) 0 = no, must see bus reset 1 = yes Bit 1: upload capable (bitCanUpload) 0 = no 1 = yes Bit 0: download capable (bitCanDnload) 0 = no 1 = yes</span></span>  |
| <span data-ttu-id="993e6-162">wDetachTimeOut</span><span class="sxs-lookup"><span data-stu-id="993e6-162">wDetachTimeOut</span></span>  | <span data-ttu-id="993e6-163">3</span><span class="sxs-lookup"><span data-stu-id="993e6-163">3</span></span>      | <span data-ttu-id="993e6-164">2</span><span class="sxs-lookup"><span data-stu-id="993e6-164">2</span></span>  | <span data-ttu-id="993e6-165">liczba</span><span class="sxs-lookup"><span data-stu-id="993e6-165">number</span></span>    | <span data-ttu-id="993e6-166">Czas (w milisekundach), po upływie którego urządzenie będzie oczekiwać po odebraniu żądania DFU_DETACH.</span><span class="sxs-lookup"><span data-stu-id="993e6-166">Time, in milliseconds, that the device will wait after receipt of the DFU_DETACH request.</span></span> <span data-ttu-id="993e6-167">Jeśli ten czas upłynie bez resetowania USB, urządzenie zakończy fazę ponownej konfiguracji i wróci do normalnego działania.</span><span class="sxs-lookup"><span data-stu-id="993e6-167">If this time elapses without a USB reset, then the device will terminate the Reconfiguration phase and revert back to normal operation.</span></span> <span data-ttu-id="993e6-168">Oznacza to maksymalny czas oczekiwania urządzenia (w zależności od jego czasomierzy itp.).</span><span class="sxs-lookup"><span data-stu-id="993e6-168">This represents the maximum time that the device can wait (depending on its timers, etc.).</span></span> <span data-ttu-id="993e6-169">USBX ustawia tę wartość na 1000 ms.</span><span class="sxs-lookup"><span data-stu-id="993e6-169">USBX sets this value to 1000 ms.</span></span>  |
| <span data-ttu-id="993e6-170">wTransferSize</span><span class="sxs-lookup"><span data-stu-id="993e6-170">wTransferSize</span></span>  | <span data-ttu-id="993e6-171">5</span><span class="sxs-lookup"><span data-stu-id="993e6-171">5</span></span>      | <span data-ttu-id="993e6-172">2</span><span class="sxs-lookup"><span data-stu-id="993e6-172">2</span></span>  | <span data-ttu-id="993e6-173">liczba</span><span class="sxs-lookup"><span data-stu-id="993e6-173">number</span></span>    | <span data-ttu-id="993e6-174">Maksymalna liczba bajtów akceptowanych przez urządzenie dla \- operacji zapisu kontroli.</span><span class="sxs-lookup"><span data-stu-id="993e6-174">Maximum number of bytes that the device can accept per control\-write operation.</span></span> <span data-ttu-id="993e6-175">USBX ustawia tę wartość na 64 bajtów.</span><span class="sxs-lookup"><span data-stu-id="993e6-175">USBX sets this value to 64 bytes.</span></span> |

<span data-ttu-id="993e6-176">Deklaracja klasy DFU jest następująca:</span><span class="sxs-lookup"><span data-stu-id="993e6-176">The declaration of the DFU class is as follows:</span></span>

```C
/* Store the DFU parameters. */

dfu_parameter.ux_slave_class_dfu_parameter_instance_activate =
    tx_demo_thread_dfu_activate;

dfu_parameter.ux_slave_class_dfu_parameter_instance_deactivate =
    tx_demo_thread_dfu_deactivate;

dfu_parameter.ux_slave_class_dfu_parameter_read =
    tx_demo_thread_dfu_read;

dfu_parameter.ux_slave_class_dfu_parameter_write =
    tx_demo_thread_dfu_write;

dfu_parameter.ux_slave_class_dfu_parameter_get_status =
    tx_demo_thread_dfu_get_status;

dfu_parameter.ux_slave_class_dfu_parameter_notify =
    tx_demo_thread_dfu_notify;

dfu_parameter.ux_slave_class_dfu_parameter_framework =
    device_framework_dfu;

dfu_parameter.ux_slave_class_dfu_parameter_framework_length =
    DEVICE_FRAMEWORK_LENGTH_DFU;

/* Initialize the device dfu class. The class is connected with interface
1 on configuration 1. */
status = ux_device_stack_class_register(_ux_system_slave_class_dfu_name,
    ux_device_class_dfu_entry, 1, 0,
    (VOID *)&dfu_parameter);

if (status!=UX_SUCCESS) return;
```

<span data-ttu-id="993e6-177">Klasa DFU musi współpracować z aplikacją oprogramowania układowego urządzenia specyficzną dla elementu docelowego.</span><span class="sxs-lookup"><span data-stu-id="993e6-177">The DFU class needs to work with a device firmware application specific to the target.</span></span> <span data-ttu-id="993e6-178">W związku z tym definiuje kilka wywołań z powrotem do odczytu i zapisu bloków oprogramowania układowego oraz do pobierania stanu z aplikacji oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="993e6-178">Therefore it defines several call back to read and write blocks of firmware and to get status from the firmware update application.</span></span> <span data-ttu-id="993e6-179">Klasa DFU ma również funkcję powiadamiania zwrotnego, aby poinformować aplikację, gdy wystąpi rozpoczęcie i zakończenie transferu oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="993e6-179">The DFU class also has a notify callback function to inform the application when a begin and end of transfer of the firmware occur.</span></span>

<span data-ttu-id="993e6-180">Poniżej znajduje się opis typowego przepływu aplikacji DFU.</span><span class="sxs-lookup"><span data-stu-id="993e6-180">Following is the description of a typical DFU application flow.</span></span>

![Przepływ aplikacji DFU](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

<span data-ttu-id="993e6-182">Najważniejszym wyzwaniem klasy DFU jest uzyskanie odpowiedniej aplikacji na hoście w celu przeprowadzenia pobierania oprogramowania układowego.</span><span class="sxs-lookup"><span data-stu-id="993e6-182">The major challenge of the DFU class is getting the right application on the host to perform the download the firmware.</span></span> <span data-ttu-id="993e6-183">Firma Microsoft nie oferuje aplikacji ani magistrali USB — Jeśli nie.</span><span class="sxs-lookup"><span data-stu-id="993e6-183">There is no application supplied by Microsoft or the USB-IF.</span></span> <span data-ttu-id="993e6-184">Niektóre "shareware" istnieją i działają odpowiednio w systemie Linux i w mniejszym stopniu w przypadku systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="993e6-184">Some shareware exist and they work reasonably well on Linux and to a lesser extent on Windows.</span></span>

<span data-ttu-id="993e6-185">W systemie Linux jeden z nich może używać DFU-narzędzia, które można znaleźć tutaj: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) wiele informacji na temat DFU można znaleźć na tym linku: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span><span class="sxs-lookup"><span data-stu-id="993e6-185">On Linux, one can use dfu-utils to be found here: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) A lot of information on dfu utils can also be found on this link: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span></span>

<span data-ttu-id="993e6-186">Implementacja systemu Linux DFU wykonuje prawidłowo sekwencję resetowania między hostem i urządzeniem, dlatego nie trzeba tego robić.</span><span class="sxs-lookup"><span data-stu-id="993e6-186">The Linux implementation of DFU performs correctly the reset sequence between the host and the device and therefore the device does not need to do it.</span></span> <span data-ttu-id="993e6-187">System Linux może akceptować bmAttributes *bitWillDetach* na 0.</span><span class="sxs-lookup"><span data-stu-id="993e6-187">Linux can accept for the bmAttributes *bitWillDetach* to be 0.</span></span> <span data-ttu-id="993e6-188">System Windows po drugiej stronie wymaga, aby urządzenie przeprowadził Reset.</span><span class="sxs-lookup"><span data-stu-id="993e6-188">Windows on the other side requires the device to perform the reset.</span></span>

<span data-ttu-id="993e6-189">W systemie Windows rejestr USB musi być w stanie skojarzyć urządzenie USB z jego identyfikatorem PID/VID i biblioteką USB, która będzie używana przez aplikację DFU.</span><span class="sxs-lookup"><span data-stu-id="993e6-189">On Windows, the USB registry must be able to associate the USB device with its PID/VID and the USB library which will in turn be used by the DFU application.</span></span> <span data-ttu-id="993e6-190">Można to łatwo zrobić przy użyciu bezpłatnego narzędzia Zadig, które można znaleźć tutaj: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/) .</span><span class="sxs-lookup"><span data-stu-id="993e6-190">This can be easily done with the free utility Zadig which can be found here: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).</span></span>

<span data-ttu-id="993e6-191">Po pierwszym uruchomieniu programu Zadig zostanie wyświetlony następujący ekran:</span><span class="sxs-lookup"><span data-stu-id="993e6-191">Running Zadig for the first time will show this screen:</span></span>

![Uruchamianie Zadig po raz pierwszy](./media/usbx-device-stack-supplemental/zadig.png)

<span data-ttu-id="993e6-193">Z listy urządzeń Znajdź urządzenie i skojarz je z libusbm sterownikiem systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="993e6-193">From the device list, find your device and associate it with the libusb windows driver.</span></span> <span data-ttu-id="993e6-194">Spowoduje to powiązanie identyfikatora PID/VID urządzenia z biblioteką USB systemu Windows używaną przez narzędzia DFU.</span><span class="sxs-lookup"><span data-stu-id="993e6-194">This will bind the PID/VID of the device with the Windows USB library used by the DFU utilities.</span></span>

<span data-ttu-id="993e6-195">Aby obsłużyć polecenie DFU, po prostu Rozpakuj spakowane narzędzia DFU do katalogu, aby upewnić się, że biblioteka libusb dll znajduje się w tym samym katalogu.</span><span class="sxs-lookup"><span data-stu-id="993e6-195">To operate the DFU command, simply unpack the zipped dfu utilities into a directory, making sure the libusb dll is also present in the same directory.</span></span> <span data-ttu-id="993e6-196">Narzędzia DFU muszą być uruchamiane z okna DOS w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-196">The DFU utilities must be run from a DOS box at the command line.</span></span>

<span data-ttu-id="993e6-197">Najpierw wpisz polecenie **DFU-util – l** , aby określić, czy urządzenie jest wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="993e6-197">First, type the command **dfu-util –l** to determine whether the device is listed.</span></span> <span data-ttu-id="993e6-198">Jeśli nie, uruchom program Zadig, aby upewnić się, że urządzenie jest wyświetlane i skojarzone z biblioteką USB.</span><span class="sxs-lookup"><span data-stu-id="993e6-198">If not, run Zadig to make sure the device is listed and associated with the USB library.</span></span> <span data-ttu-id="993e6-199">Powinien zostać wyświetlony ekran w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="993e6-199">You should see a screen as follows:</span></span>

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

<span data-ttu-id="993e6-200">Następnym krokiem będzie przygotowanie pliku do pobrania.</span><span class="sxs-lookup"><span data-stu-id="993e6-200">The next step will be to prepare the file to be downloaded.</span></span> <span data-ttu-id="993e6-201">Klasa USBX DFU nie wykonuje żadnej weryfikacji dla tego pliku i jest niezależny od jej format wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="993e6-201">The USBX DFU class does not perform any verification on this file and is agnostic of its internal format.</span></span> <span data-ttu-id="993e6-202">Ten plik oprogramowania układowego jest bardzo specyficzny dla elementu docelowego, ale nie do DFU ani do USBX.</span><span class="sxs-lookup"><span data-stu-id="993e6-202">This firmware file is very specific to the target but not to DFU nor to USBX.</span></span>

<span data-ttu-id="993e6-203">Następnie DFU-util można wysłać do pliku, wpisując następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="993e6-203">Then the dfu-util can be instructed to send the file by typing the following command:</span></span>

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

<span data-ttu-id="993e6-204">DFU-util powinien wyświetlić proces pobierania pliku, dopóki oprogramowanie układowe nie zostanie całkowicie pobrane.</span><span class="sxs-lookup"><span data-stu-id="993e6-204">The dfu-util should display the file download process until the firmware has been completely downloaded.</span></span>

## <a name="usb-device-pima-class-ptp-responder"></a><span data-ttu-id="993e6-205">Klasa PIMA urządzenia USB (obiekt odpowiadający PTP)</span><span class="sxs-lookup"><span data-stu-id="993e6-205">USB Device PIMA Class (PTP Responder)</span></span>

<span data-ttu-id="993e6-206">Klasa PIMA urządzenia USB umożliwia systemowi hosta USB (inicjator) łączenie się z</span><span class="sxs-lookup"><span data-stu-id="993e6-206">The USB device PIMA class allows for a USB host system (Initiator) to connect to a</span></span>

<span data-ttu-id="993e6-207">Urządzenie PIMA (Resonder) do transferowania plików multimedialnych.</span><span class="sxs-lookup"><span data-stu-id="993e6-207">PIMA device (Resonder) to transfer media files.</span></span> <span data-ttu-id="993e6-208">Klasa USBX Pima jest zgodna z klasą protokołu PTP, jeśli PIMA 15740, zwaną również klasą NNTP (w celu przesyłania obrazów).</span><span class="sxs-lookup"><span data-stu-id="993e6-208">USBX Pima Class is conforming to the USB-IF PIMA 15740 class also known as PTP class (for Picture Transfer Protocol).</span></span>

<span data-ttu-id="993e6-209">Klasa PIMA po stronie urządzenia USBX obsługuje następujące operacje.</span><span class="sxs-lookup"><span data-stu-id="993e6-209">USBX device side PIMA class supports the following operations.</span></span>

| <span data-ttu-id="993e6-210">Kod operacji</span><span class="sxs-lookup"><span data-stu-id="993e6-210">Operation code</span></span>                                    | <span data-ttu-id="993e6-211">Wartość</span><span class="sxs-lookup"><span data-stu-id="993e6-211">Value</span></span> | <span data-ttu-id="993e6-212">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-212">Description</span></span>                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| <span data-ttu-id="993e6-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span><span class="sxs-lookup"><span data-stu-id="993e6-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span></span>    | <span data-ttu-id="993e6-214">0x1001</span><span class="sxs-lookup"><span data-stu-id="993e6-214">0x1001</span></span>  | <span data-ttu-id="993e6-215">Uzyskaj obsługiwane operacje i zdarzenia dotyczące urządzeń</span><span class="sxs-lookup"><span data-stu-id="993e6-215">Obtain the device supported operations and events</span></span>                                                         |
| <span data-ttu-id="993e6-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span><span class="sxs-lookup"><span data-stu-id="993e6-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span></span>        | <span data-ttu-id="993e6-217">0x1002</span><span class="sxs-lookup"><span data-stu-id="993e6-217">0x1002</span></span>  | <span data-ttu-id="993e6-218">Otwieranie sesji między hostem i urządzeniem</span><span class="sxs-lookup"><span data-stu-id="993e6-218">Open a session between the host and the device</span></span>                                                            |
| <span data-ttu-id="993e6-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span><span class="sxs-lookup"><span data-stu-id="993e6-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span></span>       | <span data-ttu-id="993e6-220">0x1003</span><span class="sxs-lookup"><span data-stu-id="993e6-220">0x1003</span></span>  | <span data-ttu-id="993e6-221">Zamykanie sesji między hostem a urządzeniem</span><span class="sxs-lookup"><span data-stu-id="993e6-221">Close a session between the host and the device</span></span>                                                           |
| <span data-ttu-id="993e6-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span><span class="sxs-lookup"><span data-stu-id="993e6-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span></span>    | <span data-ttu-id="993e6-223">0x1004</span><span class="sxs-lookup"><span data-stu-id="993e6-223">0x1004</span></span>  | <span data-ttu-id="993e6-224">Zwraca identyfikator magazynu dla urządzenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-224">Returns the storage ID for the device.</span></span> <span data-ttu-id="993e6-225">USBX PIMA używa tylko jednego identyfikatora magazynu</span><span class="sxs-lookup"><span data-stu-id="993e6-225">USBX PIMA uses one storage ID only</span></span> |
| <span data-ttu-id="993e6-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span><span class="sxs-lookup"><span data-stu-id="993e6-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span></span>   | <span data-ttu-id="993e6-227">0x1005</span><span class="sxs-lookup"><span data-stu-id="993e6-227">0x1005</span></span>  | <span data-ttu-id="993e6-228">Zwróć informacje o obiekcie magazynu, takie jak Maksymalna pojemność i wolne miejsce</span><span class="sxs-lookup"><span data-stu-id="993e6-228">Return information about the storage object such as max capacity and free space</span></span>                           |
| <span data-ttu-id="993e6-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="993e6-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span></span>    | <span data-ttu-id="993e6-230">0x1006</span><span class="sxs-lookup"><span data-stu-id="993e6-230">0x1006</span></span>  | <span data-ttu-id="993e6-231">Zwróć liczbę obiektów zawartych w urządzeniu magazynującym</span><span class="sxs-lookup"><span data-stu-id="993e6-231">Return the number of objects contained in the storage device</span></span>                                              |
| <span data-ttu-id="993e6-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span><span class="sxs-lookup"><span data-stu-id="993e6-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span></span> | <span data-ttu-id="993e6-233">0x1007</span><span class="sxs-lookup"><span data-stu-id="993e6-233">0x1007</span></span>  | <span data-ttu-id="993e6-234">Zwróć tablicę dojść do obiektów na urządzeniu magazynującym</span><span class="sxs-lookup"><span data-stu-id="993e6-234">Return an array of handles of the objects on the storage device</span></span>                                           |
| <span data-ttu-id="993e6-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="993e6-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span></span>    | <span data-ttu-id="993e6-236">0x1008</span><span class="sxs-lookup"><span data-stu-id="993e6-236">0x1008</span></span>  | <span data-ttu-id="993e6-237">Zwracają informacje dotyczące obiektu, takie jak nazwa obiektu, jego Data utworzenia, Data modyfikacji</span><span class="sxs-lookup"><span data-stu-id="993e6-237">Return information about an object such as the name of the object, its creation date, modification date</span></span> |
| <span data-ttu-id="993e6-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="993e6-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span></span>          | <span data-ttu-id="993e6-239">0x1009</span><span class="sxs-lookup"><span data-stu-id="993e6-239">0x1009</span></span>  | <span data-ttu-id="993e6-240">Zwracanie danych odnoszących się do określonego obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-240">Return the data pertaining to a specific object</span></span>                                                         |
| <span data-ttu-id="993e6-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span><span class="sxs-lookup"><span data-stu-id="993e6-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span></span>           | <span data-ttu-id="993e6-242">0x100A</span><span class="sxs-lookup"><span data-stu-id="993e6-242">0x100A</span></span>  | <span data-ttu-id="993e6-243">Wyślij miniaturę, jeśli jest dostępna o obiekcie</span><span class="sxs-lookup"><span data-stu-id="993e6-243">Send the thumbnail if available about an object</span></span>                                                           |
| <span data-ttu-id="993e6-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="993e6-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span></span>       | <span data-ttu-id="993e6-245">0x100B</span><span class="sxs-lookup"><span data-stu-id="993e6-245">0x100B</span></span>  | <span data-ttu-id="993e6-246">Usuwanie obiektu na nośniku</span><span class="sxs-lookup"><span data-stu-id="993e6-246">Delete an object on the media</span></span>                                                                             |
| <span data-ttu-id="993e6-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="993e6-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span></span>   | <span data-ttu-id="993e6-248">0x100C</span><span class="sxs-lookup"><span data-stu-id="993e6-248">0x100C</span></span>  | <span data-ttu-id="993e6-249">Wyślij do informacji o urządzeniu dla jego utworzenia na nośniku</span><span class="sxs-lookup"><span data-stu-id="993e6-249">Send to the device information about an object for its creation on the media</span></span>                              |
| <span data-ttu-id="993e6-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span><span class="sxs-lookup"><span data-stu-id="993e6-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span></span>         | <span data-ttu-id="993e6-251">0x100D</span><span class="sxs-lookup"><span data-stu-id="993e6-251">0x100D</span></span>  | <span data-ttu-id="993e6-252">Wyślij dane dla obiektu do urządzenia</span><span class="sxs-lookup"><span data-stu-id="993e6-252">Send data for an object to the device</span></span>                                                                     |
| <span data-ttu-id="993e6-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span><span class="sxs-lookup"><span data-stu-id="993e6-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span></span>        | <span data-ttu-id="993e6-254">0x100F</span><span class="sxs-lookup"><span data-stu-id="993e6-254">0x100F</span></span>  | <span data-ttu-id="993e6-255">Czyszczenie nośnika urządzenia</span><span class="sxs-lookup"><span data-stu-id="993e6-255">Clean the device media</span></span>                                                                                    |
| <span data-ttu-id="993e6-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span><span class="sxs-lookup"><span data-stu-id="993e6-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span></span>        | <span data-ttu-id="993e6-257">0x0110</span><span class="sxs-lookup"><span data-stu-id="993e6-257">0x0110</span></span>  | <span data-ttu-id="993e6-258">Zresetuj urządzenie docelowe</span><span class="sxs-lookup"><span data-stu-id="993e6-258">Reset the target device</span></span>                                                                                   |

| <span data-ttu-id="993e6-259">Kod operacji</span><span class="sxs-lookup"><span data-stu-id="993e6-259">Operation Code</span></span>                                         | <span data-ttu-id="993e6-260">Wartość</span><span class="sxs-lookup"><span data-stu-id="993e6-260">Value</span></span> | <span data-ttu-id="993e6-261">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-261">Description</span></span> |
|--------------------------------------------------------|-------|-----------------------------------------|
| <span data-ttu-id="993e6-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="993e6-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span></span>       | <span data-ttu-id="993e6-263">0x4001</span><span class="sxs-lookup"><span data-stu-id="993e6-263">0x4001</span></span>  | <span data-ttu-id="993e6-264">Anuluje bieżącą transakcję</span><span class="sxs-lookup"><span data-stu-id="993e6-264">Cancels the current transaction</span></span>                                                 |
| <span data-ttu-id="993e6-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span><span class="sxs-lookup"><span data-stu-id="993e6-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span></span>             | <span data-ttu-id="993e6-266">0x4002</span><span class="sxs-lookup"><span data-stu-id="993e6-266">0x4002</span></span>  | <span data-ttu-id="993e6-267">Obiekt został dodany do nośnika urządzenia i może być pobrany przez host\.</span><span class="sxs-lookup"><span data-stu-id="993e6-267">An object has been added to the device media and can be retrieved by the host\.</span></span> |
| <span data-ttu-id="993e6-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span><span class="sxs-lookup"><span data-stu-id="993e6-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span></span>           | <span data-ttu-id="993e6-269">0x4003</span><span class="sxs-lookup"><span data-stu-id="993e6-269">0x4003</span></span>  | <span data-ttu-id="993e6-270">Usunięto obiekt z nośnika urządzenia</span><span class="sxs-lookup"><span data-stu-id="993e6-270">An object has been deleted from the device media</span></span>                                |
| <span data-ttu-id="993e6-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span><span class="sxs-lookup"><span data-stu-id="993e6-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span></span>              | <span data-ttu-id="993e6-272">0x4004</span><span class="sxs-lookup"><span data-stu-id="993e6-272">0x4004</span></span>  | <span data-ttu-id="993e6-273">Dodano nośnik do urządzenia</span><span class="sxs-lookup"><span data-stu-id="993e6-273">A media has been added to the device</span></span>                                            |
| <span data-ttu-id="993e6-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span><span class="sxs-lookup"><span data-stu-id="993e6-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span></span>            | <span data-ttu-id="993e6-275">0x4005</span><span class="sxs-lookup"><span data-stu-id="993e6-275">0x4005</span></span>  | <span data-ttu-id="993e6-276">Usunięto nośnik z urządzenia</span><span class="sxs-lookup"><span data-stu-id="993e6-276">A media has been deleted from the device</span></span>                                        |
| <span data-ttu-id="993e6-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span><span class="sxs-lookup"><span data-stu-id="993e6-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span></span>     | <span data-ttu-id="993e6-278">0x4006</span><span class="sxs-lookup"><span data-stu-id="993e6-278">0x4006</span></span>  | <span data-ttu-id="993e6-279">Zmieniono właściwości urządzenia</span><span class="sxs-lookup"><span data-stu-id="993e6-279">Device properties have changed</span></span>                                                  |
| <span data-ttu-id="993e6-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="993e6-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span></span>     | <span data-ttu-id="993e6-281">0x4007</span><span class="sxs-lookup"><span data-stu-id="993e6-281">0x4007</span></span>  | <span data-ttu-id="993e6-282">Informacje o obiekcie zostały zmienione</span><span class="sxs-lookup"><span data-stu-id="993e6-282">An object information has changed</span></span>                                               |
| <span data-ttu-id="993e6-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span><span class="sxs-lookup"><span data-stu-id="993e6-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span></span>      | <span data-ttu-id="993e6-284">0x4008</span><span class="sxs-lookup"><span data-stu-id="993e6-284">0x4008</span></span>  | <span data-ttu-id="993e6-285">Urządzenie zostało zmienione</span><span class="sxs-lookup"><span data-stu-id="993e6-285">A device has changed</span></span>                                                            |
| <span data-ttu-id="993e6-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span><span class="sxs-lookup"><span data-stu-id="993e6-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span></span> | <span data-ttu-id="993e6-287">0x4009</span><span class="sxs-lookup"><span data-stu-id="993e6-287">0x4009</span></span>  | <span data-ttu-id="993e6-288">Urządzenie żąda transferu obiektu z hosta</span><span class="sxs-lookup"><span data-stu-id="993e6-288">The device requests the transfer of an object from the host</span></span>                     |
| <span data-ttu-id="993e6-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span><span class="sxs-lookup"><span data-stu-id="993e6-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span></span>               | <span data-ttu-id="993e6-290">0x400A</span><span class="sxs-lookup"><span data-stu-id="993e6-290">0x400A</span></span>  | <span data-ttu-id="993e6-291">Urządzenie raportuje nośnik jest zapełniony</span><span class="sxs-lookup"><span data-stu-id="993e6-291">Device reports the media is full</span></span>                                                |
| <span data-ttu-id="993e6-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span><span class="sxs-lookup"><span data-stu-id="993e6-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span></span>             | <span data-ttu-id="993e6-293">0x400B</span><span class="sxs-lookup"><span data-stu-id="993e6-293">0x400B</span></span>  | <span data-ttu-id="993e6-294">Raporty urządzenia, które zostały zresetowane</span><span class="sxs-lookup"><span data-stu-id="993e6-294">Device reports it was reset</span></span>                                                     |
| <span data-ttu-id="993e6-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="993e6-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span></span>    | <span data-ttu-id="993e6-296">0x400C</span><span class="sxs-lookup"><span data-stu-id="993e6-296">0x400C</span></span>  | <span data-ttu-id="993e6-297">Informacje o magazynie zostały zmienione na urządzeniu</span><span class="sxs-lookup"><span data-stu-id="993e6-297">Storage information has changed on the device</span></span>                                   |
| <span data-ttu-id="993e6-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span><span class="sxs-lookup"><span data-stu-id="993e6-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span></span>         | <span data-ttu-id="993e6-299">0x400D</span><span class="sxs-lookup"><span data-stu-id="993e6-299">0x400D</span></span>  | <span data-ttu-id="993e6-300">Przechwytywanie zostało zakończone</span><span class="sxs-lookup"><span data-stu-id="993e6-300">Capture is completed</span></span>                                                            |

<span data-ttu-id="993e6-301">Klasa urządzenia USBX PIMA używa wątku TX do nasłuchiwania poleceń PIMA z hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-301">The USBX PIMA device class uses a TX Thread to listen to PIMA commands from the host.</span></span>

<span data-ttu-id="993e6-302">Polecenie PIMA składa się z bloku poleceń, bloku danych i fazy stanu.</span><span class="sxs-lookup"><span data-stu-id="993e6-302">A PIMA command is composed of a command block, a data block and a status phase.</span></span>

<span data-ttu-id="993e6-303">Funkcja ux_device_class_pima_thread ogłasza żądanie do stosu, aby otrzymać polecenie PIMA ze strony hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-303">The function ux_device_class_pima_thread posts a request to the stack to receive a PIMA command from the host side.</span></span> <span data-ttu-id="993e6-304">Polecenie PIMA jest zdekodowane i zweryfikowane pod kątem zawartości.</span><span class="sxs-lookup"><span data-stu-id="993e6-304">The PIMA command is decoded and verified for content.</span></span> <span data-ttu-id="993e6-305">Jeśli blok poleceń jest prawidłowy, rozgałęzienia do odpowiedniej procedury obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="993e6-305">If the command block is valid, it branches to the appropriate command handler.</span></span>

<span data-ttu-id="993e6-306">Większość poleceń PIMA można wykonać tylko wtedy, gdy sesja została otwarta przez hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-306">Most PIMA commands can only be executed when a session has been opened by the host.</span></span> <span data-ttu-id="993e6-307">Jedynym wyjątkiem jest polecenie **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span><span class="sxs-lookup"><span data-stu-id="993e6-307">The only exception is the command **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span></span> <span data-ttu-id="993e6-308">W przypadku implementacji USBX PIMA można otworzyć tylko jedną sesję między inicjatorem a obiektem odpowiadającym w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="993e6-308">With USBX PIMA implementation, only one session can be opened between an Initiator and Responder at any time.</span></span> <span data-ttu-id="993e6-309">Wszystkie transakcje w ramach jednej sesji są blokowane i nie można rozpocząć nowej transakcji przed ukończeniem poprzedniej.</span><span class="sxs-lookup"><span data-stu-id="993e6-309">All transactions within the single session are blocking and no new transaction can begin before the previous one completed.</span></span>

<span data-ttu-id="993e6-310">Transakcje PIMA składają się z 3 faz, fazy polecenia, opcjonalnej fazy danych i fazy odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="993e6-310">PIMA transactions are composed of 3 phases, a command phase, an optional data phase and a response phase.</span></span> <span data-ttu-id="993e6-311">Jeśli faza danych jest obecna, może ona znajdować się tylko w jednym kierunku.</span><span class="sxs-lookup"><span data-stu-id="993e6-311">If a data phase is present, it can only be in one direction.</span></span>

<span data-ttu-id="993e6-312">Inicjator zawsze określa przepływ operacji PIMA, ale obiekt odpowiadający może inicjować zdarzenia z powrotem do inicjatora, aby poinformować o zmianach stanu, które wystąpiły podczas sesji.</span><span class="sxs-lookup"><span data-stu-id="993e6-312">The Initiator always determines the flow of the PIMA operations but the Responder can initiate events back to the Initiator to inform status changes that happened during a session.</span></span>

<span data-ttu-id="993e6-313">Na poniższym diagramie przedstawiono transfer obiektu danych między hostem a klasą urządzenia PIMA.</span><span class="sxs-lookup"><span data-stu-id="993e6-313">The following diagram shows the transfer of a data object between the host and the PIMA device class.</span></span>

![PIMA transakcji](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a><span data-ttu-id="993e6-315">Inicjalizacja klasy urządzenia PIMA</span><span class="sxs-lookup"><span data-stu-id="993e6-315">Initialization of the PIMA device class</span></span>

<span data-ttu-id="993e6-316">Klasa urządzenia PIMA wymaga pewnych parametrów dostarczonych przez aplikację podczas inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="993e6-316">The PIMA device class needs some parameters supplied by the application during the initialization.</span></span>

<span data-ttu-id="993e6-317">Poniższe parametry opisują informacje o urządzeniu i magazynie.</span><span class="sxs-lookup"><span data-stu-id="993e6-317">The following parameters describe the device and storage information.</span></span>

- `ux_device_class_pima_manufacturer`
- `ux_device_class_pima_model`
- `ux_device_class_pima_device_version`
- `ux_device_class_pima_serial_number`
- `ux_device_class_pima_storage_id`
- `ux_device_class_pima_storage_type`
- `ux_device_class_pima_storage_file_system_type`
- `ux_device_class_pima_storage_access_capability`
- `ux_device_class_pima_storage_max_capacity_low`
- `ux_device_class_pima_storage_max_capacity_high`
- `ux_device_class_pima_storage_free_space_low`
- `ux_device_class_pima_storage_free_space_high`
- `ux_device_class_pima_storage_free_space_image`
- `ux_device_class_pima_storage_description`
- `ux_device_class_pima_storage_volume_label`

<span data-ttu-id="993e6-318">Klasa PIMA wymaga również rejestracji wywołania zwrotnego w aplikacji w celu powiadomienia aplikacji o określonych zdarzeniach lub pobrania/przechowania danych z/do nośnika lokalnego.</span><span class="sxs-lookup"><span data-stu-id="993e6-318">The PIMA class also requires the registration of callback into the application to inform the application of certain events or retrieve/store data from/to the local media.</span></span> <span data-ttu-id="993e6-319">Wywołania zwrotne są następujące.</span><span class="sxs-lookup"><span data-stu-id="993e6-319">The callbacks are as follows.</span></span>

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

<span data-ttu-id="993e6-320">Poniższy przykład pokazuje, jak zainicjować po stronie klienta PIMA.</span><span class="sxs-lookup"><span data-stu-id="993e6-320">The following example shows how to initialize the client side of PIMA.</span></span> <span data-ttu-id="993e6-321">Ten przykład używa technologii PictBridge jako klienta dla PIMA.</span><span class="sxs-lookup"><span data-stu-id="993e6-321">This example uses Pictbridge as a client for PIMA.</span></span>

```C
/* Initialize the first XML object valid in the pictbridge instance.

Initialize the handle, type and file name.

The storage handle and the object handle have a fixed value of 1 in our implementation. */

object_info = pictbridge -> ux_pictbridge_object_client;

object_info -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_SCRIPT;
object_info -> ux_device_class_pima_object_storage_id = 1;
object_info -> ux_device_class_pima_object_handle_id = 2;

ux_utility_string_to_unicode(_ux_pictbridge_ddiscovery_name,
    object_info -> ux_device_class_pima_object_filename);

/* Initialize the head and tail of the notification round robin buffers.
   At first, the head and tail are pointing to the beginning of the array.
*/

pictbridge -> ux_pictbridge_event_array_head =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_tail =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_end =
    pictbridge -> ux_pictbridge_event_array +
    UX_PICTBRIDGE_MAX_EVENT_NUMBER;

/* Initialialize the pima device parameter. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_manufacturer =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_model =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_serial_number =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_id = 1;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_type =
    UX_DEVICE_CLASS_PIMA_STC_FIXED_RAM;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_file_system_type =
    UX_DEVICE_CLASS_PIMA_FSTC_GENERIC_FLAT;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_access_capability =
    UX_DEVICE_CLASS_PIMA_AC_READ_WRITE;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_image = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_description =
    _ux_pictbridge_volume_description;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_volume_label =
    _ux_pictbridge_volume_label;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_number_get =
    ux_pictbridge_dpsclient_object_number_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_handles_get =
    ux_pictbridge_dpsclient_object_handles_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_get =
    ux_pictbridge_dpsclient_object_info_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_get =
    ux_pictbridge_dpsclient_object_data_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_send =
    ux_pictbridge_dpsclient_object_info_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_send =
    ux_pictbridge_dpsclient_object_data_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_delete =
    ux_pictbridge_dpsclient_object_delete;

/* Store the instance owner. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_application =
    (VOID *) pictbridge;

/* Initialize the device pima class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_pima_name,
    ux_device_class_pima_entry, 1, 0, (VOID *)&pictbridge -> ux_pictbridge_pima_parameter);

/* Check status. */
if (status != UX_SUCCESS)
```

## <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="993e6-322">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="993e6-322">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="993e6-323">Dodawanie obiektu i wysyłanie zdarzenia do hosta</span><span class="sxs-lookup"><span data-stu-id="993e6-323">Adding an object and sending the event to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-324">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-324">Prototype</span></span>

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="993e6-325">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-325">Description</span></span>

<span data-ttu-id="993e6-326">Ta funkcja jest wywoływana, gdy Klasa PIMA musi dodać obiekt i poinformować hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-326">This function is called when the PIMA class needs to add an object and inform the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-327">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-327">Parameters</span></span>

- <span data-ttu-id="993e6-328">**Pima**: wskaźnik do wystąpienia klasy Pima</span><span class="sxs-lookup"><span data-stu-id="993e6-328">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="993e6-329">**object_handle**: uchwyt obiektu.</span><span class="sxs-lookup"><span data-stu-id="993e6-329">**object_handle**: Handle of the object.</span></span>

### <a name="example"></a><span data-ttu-id="993e6-330">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-330">Example</span></span>

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a><span data-ttu-id="993e6-331">ux_device_class_pima_object_number_get</span><span class="sxs-lookup"><span data-stu-id="993e6-331">ux_device_class_pima_object_number_get</span></span>

<span data-ttu-id="993e6-332">Pobieranie numeru obiektu z aplikacji</span><span class="sxs-lookup"><span data-stu-id="993e6-332">Getting the object number from the application</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-333">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-333">Prototype</span></span>

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a><span data-ttu-id="993e6-334">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-334">Description</span></span>

<span data-ttu-id="993e6-335">Ta funkcja jest wywoływana, gdy Klasa PIMA musi pobierać liczbę obiektów w systemie lokalnym i wysyłać ją z powrotem do hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-335">This function is called when the PIMA class needs to retrieve the number of objects in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-336">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-336">Parameters</span></span>

- <span data-ttu-id="993e6-337">**Pima**: wskaźnik do wystąpienia klasy Pima</span><span class="sxs-lookup"><span data-stu-id="993e6-337">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="993e6-338">**object_number**: adres liczby obiektów do zwrócenia</span><span class="sxs-lookup"><span data-stu-id="993e6-338">**object_number**: Address of the number of objects to be returned</span></span>

### <a name="example"></a><span data-ttu-id="993e6-339">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-339">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a><span data-ttu-id="993e6-340">ux_device_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="993e6-340">ux_device_class_pima_object_handles_get</span></span>

<span data-ttu-id="993e6-341">Zwróć tablicę uchwytów obiektów</span><span class="sxs-lookup"><span data-stu-id="993e6-341">Return the object handle array</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-342">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-342">Prototype</span></span>

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a><span data-ttu-id="993e6-343">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-343">Description</span></span>

<span data-ttu-id="993e6-344">Ta funkcja jest wywoływana, gdy Klasa PIMA musi pobrać obiekt obsługujący tablicę w systemie lokalnym i wysyłać ją z powrotem do hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-344">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-345">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-345">Parameters</span></span>

- <span data-ttu-id="993e6-346">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="993e6-346">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="993e6-347">**object_handles_format_code**: Formatuj kod dla uchwytów</span><span class="sxs-lookup"><span data-stu-id="993e6-347">**object_handles_format_code**: Format code for the handles</span></span>
- <span data-ttu-id="993e6-348">**object_handles_association**: Kod powiązania obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-348">**object_handles_association**: Object association code</span></span>
- <span data-ttu-id="993e6-349">**object_handle_array**: adres, na którym mają być przechowywane uchwyty</span><span class="sxs-lookup"><span data-stu-id="993e6-349">**object_handle_array**: Address where to store the handles</span></span>
- <span data-ttu-id="993e6-350">**object_handles_max_number**: Maksymalna liczba dojść w tablicy</span><span class="sxs-lookup"><span data-stu-id="993e6-350">**object_handles_max_number**: Maximum number of handles in the array</span></span>

### <a name="example"></a><span data-ttu-id="993e6-351">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-351">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_handles_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *) pima -> ux_device_class_pima_application;

    /* Set the pima pointer to the pictbridge instance. */
    pictbridge -> ux_pictbridge_pima = (VOID *) pima;

    /* We say we have one object but the caller might specify different format code and associations. */
    object_info = pictbridge -> ux_pictbridge_object_client;

    /* Insert in the array the number of found handles so far: 0. */
    ux_utility_long_put((UCHAR *)object_handles_array, 0);

    /* Check the type demanded. */

    if (object_handles_format_code == 0 || object_handles_format_code ==
        0xFFFFFFFF || object_info -> ux_device_class_pima_object_format ==
        object_handles_format_code)
    {
        /* Insert in the array the number of found handles. This handle is for the client XML script. */
        ux_utility_long_put((UCHAR *)object_handles_array, 1);

        /* Adjust the array to point after the number of elements. */
        object_handles_array++;

        /* We have a candicate. Store the handle. */
        ux_utility_long_put((UCHAR *)object_handles_array, object_info ->
            ux_device_class_pima_object_handle_id);
    }

    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_info_get"></a><span data-ttu-id="993e6-352">ux_device_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="993e6-352">ux_device_class_pima_object_info_get</span></span>

<span data-ttu-id="993e6-353">Zwróć informacje o obiekcie</span><span class="sxs-lookup"><span data-stu-id="993e6-353">Return the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-354">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-354">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a><span data-ttu-id="993e6-355">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-355">Description</span></span>

<span data-ttu-id="993e6-356">Ta funkcja jest wywoływana, gdy Klasa PIMA musi pobrać obiekt obsługujący tablicę w systemie lokalnym i wysyłać ją z powrotem do hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-356">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-357">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-357">Parameters</span></span>

- <span data-ttu-id="993e6-358">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="993e6-358">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="993e6-359">**object_handles**: uchwyt obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-359">**object_handles**: Handle of the object</span></span>
- <span data-ttu-id="993e6-360">**obiekt**: adres wskaźnika obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-360">**object**: Object pointer address</span></span>

### <a name="example"></a><span data-ttu-id="993e6-361">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-361">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UX_SLAVE_CLASS_PIMA_OBJECT **object)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST)) {

        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge -> ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;
    } else
        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;
    /* Return the pointer to this object. */
    *object = object_info;

    /* We are done. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="993e6-362">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="993e6-362">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="993e6-363">Zwracanie danych obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-363">Return the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-364">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-364">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a><span data-ttu-id="993e6-365">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-365">Description</span></span>

<span data-ttu-id="993e6-366">Ta funkcja jest wywoływana, gdy Klasa PIMA musi pobrać dane obiektu w systemie lokalnym i wysłać je z powrotem do hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-366">This function is called when the PIMA class needs to retrieve the object data in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-367">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-367">Parameters</span></span>

- <span data-ttu-id="993e6-368">**Pima**: wskaźnik do wystąpienia klasy Pima.</span><span class="sxs-lookup"><span data-stu-id="993e6-368">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="993e6-369">**object_handle**: uchwyt obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-369">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="993e6-370">**object_buffer**: adres buforu obiektów</span><span class="sxs-lookup"><span data-stu-id="993e6-370">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="993e6-371">**object_length_requested**: długość danych obiektu żądana przez klienta do aplikacji</span><span class="sxs-lookup"><span data-stu-id="993e6-371">**object_length_requested**: Object data length requested by the client to the application</span></span>
- <span data-ttu-id="993e6-372">**object_actual_length**: długość danych obiektu zwracana przez aplikację</span><span class="sxs-lookup"><span data-stu-id="993e6-372">**object_actual_length**: Object data length returned by the application</span></span>

### <a name="example"></a><span data-ttu-id="993e6-373">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-373">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UCHAR *object_buffer, ULONG object_offset,
    ULONG object_length_requested, ULONG *object_actual_length)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    UCHAR *pima_object_buffer;
    ULONG actual_length;
    UINT status;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST))
    {
        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;

       /* Is this the corrent handle ? */
       if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
       {
           /* Get the pointer to the object buffer. */
           pima_object_buffer = object_info -> ux_device_class_pima_object_buffer;

           /* Copy the demanded object data portion. */
           ux_utility_memory_copy(object_buffer, pima_object_buffer +
               object_offset, object_length_requested);

           /* Update the length requested. for a demo, we do not do any checking. */
           *object_actual_length = object_length_requested;

           /* What cycle are we in ? */
           if (pictbridge -> ux_pictbridge_host_client_state_machine &
               UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST)
            {
                /* Check if we are blocking for a client request. */
                if (pictbridge -> ux_pictbridge_host_client_state_machine &
                    UX_PICTBRIDGE_STATE_MACHINE_CLIENT_REQUEST_PENDING)

                    /* Yes we are pending, send an event to release the pending request. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_STATE_MACHINE_READY, TX_OR);

               /* Since we are in host request, this indicates we are done with the cycle. */
               pictbridge -> ux_pictbridge_host_client_state_machine =
                   UX_PICTBRIDGE_STATE_MACHINE_IDLE;

            }

            /* We have copied the requested data. Return OK. */
            return(UX_SUCCESS);

        }
    }
    else
    {

        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;

        /* Obtain the data from the application jobinfo callback. */
        status = pictbridge -> ux_pictbridge_jobinfo.
            ux_pictbridge_jobinfo_object_data_read(pictbridge, object_buffer, object_offset,
            object_length_requested, &actual_length);

        /* Save the length returned. */
        *object_actual_length = actual_length;

        /* Return the application status. */
        return(status);

    }

    /* Could not find the handle. */

    return(UX_DEVICE_CLASS_PIMA_RC_INVALID_OBJECT_HANDLE);
}
```

## <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="993e6-374">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="993e6-374">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="993e6-375">Host wysyła informacje o obiekcie</span><span class="sxs-lookup"><span data-stu-id="993e6-375">Host sends the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-376">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-376">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a><span data-ttu-id="993e6-377">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-377">Description</span></span>

<span data-ttu-id="993e6-378">Ta funkcja jest wywoływana, gdy Klasa PIMA musi odbierać informacje o obiekcie w systemie lokalnym w celu przechowywania w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="993e6-378">This function is called when the PIMA class needs to receive the object information in the local system for future storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-379">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-379">Parameters</span></span>

- <span data-ttu-id="993e6-380">**Pima**: wskaźnik do wystąpienia klasy Pima</span><span class="sxs-lookup"><span data-stu-id="993e6-380">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="993e6-381">**Object**: wskaźnik do obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-381">**object**:  Pointer to the object</span></span>
- <span data-ttu-id="993e6-382">**object_handle**: uchwyt obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-382">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="993e6-383">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-383">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_send(UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, ULONG *object_handle)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info; UCHAR
    string_discovery_name[UX_PICTBRIDGE_MAX_FILE_NAME_SIZE];

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* We only have one object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Copy the demanded object info set. */
    ux_utility_memory_copy(object_info, object,
        UX_SLAVE_CLASS_PIMA_OBJECT_DATA_LENGTH);

    /* Store the object handle. In Pictbridge we only receive XML scripts so the handle is hardwired to 1. */
    object_info -> ux_device_class_pima_object_handle_id = 1;
    *object_handle = 1;

    /* Check state machine. If we are in discovery pending mode, check file name of this object. */
    if (pictbridge -> ux_pictbridge_discovery_state ==
        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_PENDING)
    {
        /* We are in the discovery mode. Check for file name. It must match
           HDISCVRY.DPS in Unicode mode. */

        /* Check if this is a script. */
        if (object_info -> ux_device_class_pima_object_format ==
            UX_DEVICE_CLASS_PIMA_OFC_SCRIPT)
        {

            /* Yes this is a script. We need to search for the HDISCVRY.DPS file name. Get the file name in a ascii format. */
            ux_utility_unicode_to_string(object_info ->
                ux_device_class_pima_object_filename,
                string_discovery_name);

            /* Now, compare it to the HDISCVRY.DPS file name. Check length first. */
            if (ux_utility_string_length_get(_ux_pictbridge_hdiscovery_name)
                == ux_utility_string_length_get(string_discovery_name))
            {

                /* So far, the length of name of the files are the same. Compare names now. */
                if(ux_utility_memory_compare(_ux_pictbridge_hdiscovery_name,
                    string_discovery_name,
                    ux_utility_string_length_get(string_discovery_name)) == UX_SUCCESS)
                {
                    /* We are done with discovery of the printer. We can now send notifications when the camera wants to print an object. */
                    pictbridge -> ux_pictbridge_discovery_state =
                        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_COMPLETE;

                    /* Set an event flag if the application is listening. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY, TX_OR);

                    /* There is no object during th discovery cycle. */
                    return(UX_SUCCESS);
                }
            }
        }
    }
    /* What cycle are we in ? */
    if (pictbridge -> ux_pictbridge_host_client_state_machine ==
        UX_PICTBRIDGE_STATE_MACHINE_IDLE)

        /* Since we are in idle state, we must have received a request from the host. */
        pictbridge -> ux_pictbridge_host_client_state_machine =
            UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="993e6-384">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="993e6-384">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="993e6-385">Host wysyła dane obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-385">Host sends the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-386">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-386">Prototype</span></span>

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a><span data-ttu-id="993e6-387">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-387">Description</span></span>

<span data-ttu-id="993e6-388">Ta funkcja jest wywoływana, gdy Klasa PIMA musi odbierać dane obiektów w systemie lokalnym dla magazynu.</span><span class="sxs-lookup"><span data-stu-id="993e6-388">This function is called when the PIMA class needs to receive the object data in the local system for storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-389">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-389">Parameters</span></span>

- <span data-ttu-id="993e6-390">**Pima**: wskaźnik do wystąpienia klasy Pima</span><span class="sxs-lookup"><span data-stu-id="993e6-390">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="993e6-391">**object_handle**: uchwyt obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-391">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="993e6-392">**faza**: faza transferu (aktywna lub ukończona)</span><span class="sxs-lookup"><span data-stu-id="993e6-392">**phase**: phase of the transfer (active or complete)</span></span>
- <span data-ttu-id="993e6-393">**object_buffer**: adres buforu obiektów</span><span class="sxs-lookup"><span data-stu-id="993e6-393">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="993e6-394">**object_offset**: adres danych</span><span class="sxs-lookup"><span data-stu-id="993e6-394">**object_offset**: Address of data</span></span>
- <span data-ttu-id="993e6-395">**object_length**: długość danych obiektu wysłana przez aplikację</span><span class="sxs-lookup"><span data-stu-id="993e6-395">**object_length**: Object data length sent by application</span></span>

### <a name="example"></a><span data-ttu-id="993e6-396">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-396">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_send(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    ULONG phase,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length)
{
    UINT status;
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    ULONG event_flag;
    UCHAR *pima_object_buffer;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Get the pointer to the pima object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Is this the corrent handle ? */
    if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
    {
        /* Get the pointer to the object buffer. */
        pima_object_buffer = object_info ->
            ux_device_class_pima_object_buffer;

        /* Check the phase. We should wait for the object to be completed and the response sent back before parsing the object. */
        if (phase == UX_DEVICE_CLASS_PIMA_OBJECT_TRANSFER_PHASE_ACTIVE)
        {
            /* Copy the demanded object data portion. */
            ux_utility_memory_copy(pima_object_buffer + object_offset,
                object_buffer, object_length);

            /* Save the length of this object. */
            object_info -> ux_device_class_pima_object_length = object_length;

            /* We are not done yet. */
            return(UX_SUCCESS);
        }
        else
        {
            /* Completion of transfer. We are done. */
            return(UX_SUCCESS);
        }
    }
}
```

## <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="993e6-397">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="993e6-397">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="993e6-398">Usuwanie obiektu lokalnego</span><span class="sxs-lookup"><span data-stu-id="993e6-398">Delete a local object</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-399">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-399">Prototype</span></span>

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="993e6-400">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-400">Description</span></span>

<span data-ttu-id="993e6-401">Ta funkcja jest wywoływana, gdy Klasa PIMA musi usunąć obiekt z magazynu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="993e6-401">This function is called when the PIMA class needs to delete an object on the local storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-402">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-402">Parameters</span></span>

- <span data-ttu-id="993e6-403">**Pima**: wskaźnik do wystąpienia klasy Pima</span><span class="sxs-lookup"><span data-stu-id="993e6-403">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="993e6-404">**object_handle**: uchwyt obiektu</span><span class="sxs-lookup"><span data-stu-id="993e6-404">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="993e6-405">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-405">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a><span data-ttu-id="993e6-406">Klasa audio urządzenia USB</span><span class="sxs-lookup"><span data-stu-id="993e6-406">USB Device Audio Class</span></span>

<span data-ttu-id="993e6-407">Klasa audio urządzenia USB umożliwia systemowi hosta USB komunikowanie się z urządzeniem jako urządzeniem audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-407">The USB device Audio class allows for a USB host system to communicate with the device as an audio device.</span></span> <span data-ttu-id="993e6-408">Ta klasa jest oparta na standardowym standardzie USB i USB audio klasy 1,0 lub 2,0.</span><span class="sxs-lookup"><span data-stu-id="993e6-408">This class is based on the USB standard and USB Audio Class 1.0 or 2.0 standard.</span></span>

<span data-ttu-id="993e6-409">Architektura urządzenia zgodna z dźwiękiem USB musi być zadeklarowana przez stos urządzeń.</span><span class="sxs-lookup"><span data-stu-id="993e6-409">A USB audio compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="993e6-410">Przykładowy głośnik audio 2,0:</span><span class="sxs-lookup"><span data-stu-id="993e6-410">An example of an Audio 2.0 speaker follows:</span></span>

```C
unsigned char device_framework_high_speed[] = {

    /* --- Device Descriptor 18 bytes
    0x00 bDeviceClass: Refer to interface
    0x00 bDeviceSubclass: Refer to interface
    0x00 bDeviceProtocol: Refer to interface

    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    /* 0 bLength, bDescriptorType */ 18, 0x01,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00, 0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 0x08,
    /* 8 idVendor, idProduct */ 0x84, 0x84, 0x03, 0x00,
    /* 12 bcdDevice */ 0x00, 0x02,
    /* 14 iManufacturer, iProduct, iSerialNumber */ 0, 0, 0,
    /* 17 bNumConfigurations */ 1,
    /* ---------------- Device Qualifier Descriptor */
    /* 0 bLength, bDescriptorType */ 10, 0x06,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00,0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 8,
    /* 8 bNumConfigurations */ 1,
    /* 9 bReserved */ 0,
    /* --- Configuration Descriptor (9+8+73+55=145, 0x91) */
    /* 0 bLength, bDescriptorType */ 9, 0x02,
    /* 2 wTotalLength */ 145, 0,
    /* 4 bNumInterfaces, bConfigurationValue */ 2, 1,
    /* 6 iConfiguration */ 0,
    /* 7 bmAttributes, bMaxPower */ 0x80, 50,
    /* ----------- Interface Association Descriptor */
    /* 0 bLength, bDescriptorType */ 8, 0x0B,
    /* 2 bFirstInterface, bInterfaceCount */ 0, 2,
    /* 4 bFunctionClass : 0x01 (Audio) */ 0x01,
    /* 5 bFunctionSubClass : 0x00 (UNDEFINED) */ 0x00,
    /* 6 bFunctionProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 7 iFunction */ 0,
    /* --- Interface Descriptor #0: Control (9+64=73) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 0, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioControl) */ 0x01,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* --- Audio 2.0 AC Interface Header Descriptor (9+8+17+18+12=64, 0x40) */
    /* 0 bLength */ 9,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bcdADC */ 0x00, 0x02,
    /* 5 bCategory : 0x08 (IO Box) */ 0x08,
    /* 6 wTotalLength */ 64, 0,
    /* 8 bmControls */ 0x00,
    /* -------- Audio 2.0 AC Clock Source Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x0A,
    /* 3 bClockID */ 0x10,
    /* 4 bmAttributes : 0x05 (Sync|InternalFixedClk) */ 0x05,
    /* 5 bmControls : 0x01 (FreqReadOnly) */ 0x01,
    /* 6 bAssocTerminal, iClockSource */ 0x00, 0,
    /* ------ Audio 2.0 AC Input Terminal Descriptor */
    /* 0 bLength */ 17,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02, /* 3 bTerminalID */ 0x04,
    /* 4 wTerminalType : 0x0101 (USB Streaming) */ 0x01, 0x01,
    /* 6 bAssocTerminal, bCSourceID */ 0x00, 0x10,
    /* 8 bNrChannels */ 2,
    /* 9 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 13 iChannelNames, bmControls, iTerminal */ 0, 0x00, 0x00, 0,
    /* -------- Audio 2.0 AC Feature Unit Descriptor */
    /* 0 bLength */ 18,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x06,
    /* 3 bUnitID, bSourceID */ 0x05, 0x04,
    /* 5 bmaControls(0) : 0x0F (VolumeRW|MuteRW) */ 0x0F, 0x00, 0x00, 0x00,
    /* 9 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* 13 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* . iFeature */ 0,
    /* ----- Audio 2.0 AC Output Terminal Descriptor */
    /* 0 bLength */ 12,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x03, /* 3 bTerminalID */ 0x06,
    /* 4 wTerminalType : 0x0301 (Speaker) */ 0x01, 0x03,
    /* 6 bAssocTerminal, bSourceID, bCSourceID */ 0x00, 0x05, 0x10,
    /* 9 bmControls, iTerminal */ 0x00, 0x00, 0,
    /* --- Interface Descriptor #1: Stream OUT (9+9+16+6+7+8=55) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------------------- Interface Descriptor */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 1,
    /* 4 bNumEndpoints */ 1,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------- Audio 2.0 AS Interface Descriptor */
    /* 0 bLength */ 16,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bTerminalLink, bmControls */ 0x04, 0x00,
    /* 5 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 6 bmFormats : 0x000000001 (PCM) */ 0x01, 0x00, 0x00, 0x00, /* 10 bNrChannels */ 2,
    /* 11 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 15 iChannelNames */ 0, /* --------- Audio 2.0 AS Format Type Descriptor */
    /* 0 bLength */ 6,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02,
    /* 3 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 4 bSubslotSize, bBitResolution */ 2, 16,
    /* ------------------------- Endpoint Descriptor */
    /* 0 bLength, bDescriptorType */ 7, 0x05,
    /* 2 bEndpointAddress */ 0x02,
    /* 3 bmAttributes : 0x0D (Sync|ISO) */ 0x0D,
    /* 4 wMaxPacketSize : 0x0100 (256) */ 0x00, 0x01,
    /* 6 bInterval : 0x04 (1ms) */ 4,
    /* - Audio 2.0 AS ISO Audio Data Endpoint Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x25, 0x01,
    /* 3 bmAttributes, bmControls */ 0x00, 0x00,
    /* 5 bLockDelayUnits, wLockDelay */ 0x00, 0x00, 0x00,
};
```

<span data-ttu-id="993e6-411">Klasa audio używa złożonej struktury urządzenia do grupowania interfejsów (kontroli i przesyłania strumieniowego).</span><span class="sxs-lookup"><span data-stu-id="993e6-411">The Audio class uses a composite device framework to group interfaces (control and streaming).</span></span> <span data-ttu-id="993e6-412">W związku z tym należy wziąć pod uwagę podczas definiowania deskryptora urządzenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-412">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="993e6-413">USBX opiera się na deskryptorze IAD, aby wiedzieć, jak powiązać interfejsy.</span><span class="sxs-lookup"><span data-stu-id="993e6-413">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="993e6-414">Deskryptor IAD należy zadeklarować przed interfejsami (interfejsem AudioControl, po którym następuje co najmniej jeden interfejs AudioStreaming) i zawierać pierwszy interfejs klasy audio (interfejs AudioControl) oraz liczbę podłączonych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="993e6-414">The IAD descriptor should be declared before the interfaces (an AudioControl interface followed by one or more AudioStreaming interfaces) and contain the first interface of the Audio class (the AudioControl interface) and how many interfaces are attached.</span></span>

<span data-ttu-id="993e6-415">Sposób działania klasy audio zależy od tego, czy urządzenie wysyła lub odbierało dźwięk, ale oba przypadki używają FIFO do przechowywania buforów ramek audio: Jeśli urządzenie wysyła dźwięk do hosta, aplikacja dodaje bufory ramki audio do FIFO, które są później wysyłane do hosta przez USBX; Jeśli urządzenie odbiera dźwięk z hosta, USBX dodaje bufory ramki audio otrzymane od hosta do FIFO, które są później odczytywane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="993e6-415">The way the audio class works depends on whether the device is sending or receiving audio, but both cases use a FIFO for storing audio frame buffers: if the device is sending audio to the host, then the application adds audio frame buffers to the FIFO which are later sent to the host by USBX; if the device is receiving audio from the host, then USBX adds the audio frame buffers received from the host to the FIFO which are later read by the application.</span></span> <span data-ttu-id="993e6-416">Każdy strumień audio ma własną FIFO, a każdy bufor ramki audio składa się z wielu przykładów.</span><span class="sxs-lookup"><span data-stu-id="993e6-416">Each audio stream has its own FIFO, and each audio frame buffer consists of multiple samples.</span></span>

<span data-ttu-id="993e6-417">Inicjalizacja klasy audio oczekuje następujących części.</span><span class="sxs-lookup"><span data-stu-id="993e6-417">The initialization of the Audio class expects the following parts.</span></span>

1. <span data-ttu-id="993e6-418">Klasa audio oczekuje następujących parametrów przesyłania strumieniowego:</span><span class="sxs-lookup"><span data-stu-id="993e6-418">Audio class expects the following streaming parameters:</span></span>

   ```C
   /* Set the parameters for Audio streams. */
   /* Set the application-defined callback that is invoked when the
      host requests a change to the alternate setting. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_change = demo_audio_read_change;

   /* Set the application-defined callback that is invoked whenever
      a USB packet (audio frame) is sent to or received from the host. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_frame_done = demo_audio_read_done;

   /* Set the number of audio frame buffers in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_nb = UX_DEMO_FRAME_BUFFER_NB;

   /* Set the maximum size of each audio frame buffer in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_size = UX_DEMO_MAX_FRAME_SIZE;

   /* Set the internally-defined audio processing thread entry pointer. If the application wishes to receive audio from the host
      (which is the case in this example), ux_device_class_audio_read_thread_entry should be used;
      if the application wishes to send data to the host, ux_device_class_audio_write_thread_entry should be used. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry = ux_device_class_audio_read_thread_entry;
   ```

2. <span data-ttu-id="993e6-419">Klasa audio oczekuje następujących parametrów funkcji.</span><span class="sxs-lookup"><span data-stu-id="993e6-419">Audio class expects the following function parameters.</span></span>

   ```C
   /* Set the parameters for Audio device. */

   /* Set the number of streams. */
   audio_parameter.ux_device_class_audio_parameter_streams_nb = 1;

   /* Set the pointer to the first audio stream parameter.
      Note that we initialized this parameter in the previous section.
      Also note that for more than one streams, this should be an array. */
   audio_parameter.ux_device_class_audio_parameter_streams = audio_stream_parameter;

   /* Set the application-defined callback that is invoked when the audio class
      is activated i.e. device is connected to host. */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_activate = demo_audio_instance_activate;

   /* Set the application-defined callback that is invoked when the audio class
      is deactivated i.e. device is disconnected from host. */

   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_deactivate = demo_audio_instance_deactivate;

   /* Set the application-defined callback that is invoked when the stack receives a control request from the host.
      See below for more details.
   */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_device_class_audio_control_process = demo_audio20_request_process;

   /* Initialize the device Audio class. This class owns interfaces starting with 0. */
   status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   <span data-ttu-id="993e6-420">Zdefiniowane przez aplikację wywołanie zwrotne żądania sterowania (***ux_device_class_audio_control_process***; ustawione w poprzednim przykładzie) jest wywoływane, gdy stos odbiera żądanie sterowania od hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-420">The application-defined control request callback (***ux_device_class_audio_control_process***; set in the previous example) is invoked when the stack receives a control request from the host.</span></span> <span data-ttu-id="993e6-421">Jeśli żądanie zostało zaakceptowane i obsłużone (potwierdzone lub zawiesić), wywołanie zwrotne musi zwracać sukces, w przeciwnym razie błąd powinien zostać zwrócony.</span><span class="sxs-lookup"><span data-stu-id="993e6-421">If the request is accepted and handled (acknowledged or stalled) the callback must return success, otherwise error should be returned.</span></span>

   <span data-ttu-id="993e6-422">Proces żądania kontroli specyficzny dla klasy jest zdefiniowany jako wywołanie zwrotne zdefiniowane przez aplikację, ponieważ żądania sterujące są bardzo różne w różnych wersjach audio USB, a duża część procesu żądania odnosi się do platformy urządzeń.</span><span class="sxs-lookup"><span data-stu-id="993e6-422">The class-specific control request process is defined as an application-defined callback because the control requests are very different between USB Audio versions and a large part of the request process relates to the device framework.</span></span> <span data-ttu-id="993e6-423">Aplikacja powinna prawidłowo obsługiwać żądania, aby zapewnić funkcjonalność urządzenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-423">The application should handle requests correctly to make the device functional.</span></span>

   <span data-ttu-id="993e6-424">Ze względu na to, że w przypadku urządzenia audio dyski, wyciszenie i częstotliwość próbkowania są typowymi żądaniami kontroli, proste, zdefiniowane wewnętrznie wywołania zwrotne dla różnych wersji audio USB są wprowadzane w kolejnych sekcjach dla aplikacji, które mają być używane.</span><span class="sxs-lookup"><span data-stu-id="993e6-424">Since for an audio device, volume, mute and sampling frequency are common control requests, simple, internally-defined callbacks for different USB audio versions are introduced in later sections for applications to use.</span></span> <span data-ttu-id="993e6-425">Aby uzyskać więcej informacji, zobacz \***ux_device_class_audio10_control_process** _ i _ \*_ux_device_class_audio_control_request_\*\*.</span><span class="sxs-lookup"><span data-stu-id="993e6-425">Refer to ***ux_device_class_audio10_control_process** _ and _ *_ux_device_class_audio_control_request_** for more details.</span></span>

<span data-ttu-id="993e6-426">W środowisku urządzenia audio Identyfikator PID/VID jest przechowywany w deskryptorze urządzenia (patrz deskryptor urządzenia zadeklarowany powyżej).</span><span class="sxs-lookup"><span data-stu-id="993e6-426">In the device framework of the Audio device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="993e6-427">Gdy system hosta USB odnajduje urządzenie audio USB i instaluje klasę audio, urządzenie może być używane z dowolnym odtwarzaczem audio lub rejestratorem (w zależności od platformy).</span><span class="sxs-lookup"><span data-stu-id="993e6-427">When a USB host system discovers the USB Audio device and mounts the audio class, the device can be used with any audio player or recorder (depending on the framework).</span></span> <span data-ttu-id="993e6-428">Aby uzyskać informacje, zobacz system operacyjny hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-428">See the host Operating System for reference.</span></span>

<span data-ttu-id="993e6-429">Interfejsy API klasy audio są zdefiniowane poniżej.</span><span class="sxs-lookup"><span data-stu-id="993e6-429">The Audio class APIs are defined below.</span></span>

## <a name="ux_device_class_audio_read_thread_entry"></a><span data-ttu-id="993e6-430">ux_device_class_audio_read_thread_entry</span><span class="sxs-lookup"><span data-stu-id="993e6-430">ux_device_class_audio_read_thread_entry</span></span>

<span data-ttu-id="993e6-431">Wpis wątku służący do odczytywania danych dla funkcji audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-431">Thread entry for reading data for the Audio function.</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-432">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-432">Prototype</span></span>

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="993e6-433">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-433">Description</span></span>

<span data-ttu-id="993e6-434">Ta funkcja jest przenoszona do parametru inicjowania strumienia audio, jeśli jest wymagane odczytanie dźwięku z hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-434">This function is passed to the audio stream initialization parameter if reading audio from the host is desired.</span></span> <span data-ttu-id="993e6-435">Wewnętrznie wątek jest tworzony za pomocą tej funkcji jako funkcji Wejścia; sam wątek odczytuje dane audio za pomocą punktu końcowego Isochronous OUT w funkcji audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-435">Internally, a thread is created with this function as its entry function; the thread itself reads audio data through the isochronous OUT endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-436">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-436">Parameters</span></span>

- <span data-ttu-id="993e6-437">**audio_stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-437">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="993e6-438">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-438">Example</span></span>

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a><span data-ttu-id="993e6-439">ux_device_class_audio_write_thread_entry</span><span class="sxs-lookup"><span data-stu-id="993e6-439">ux_device_class_audio_write_thread_entry</span></span>

<span data-ttu-id="993e6-440">Wpis wątku służący do zapisywania danych dla funkcji audio</span><span class="sxs-lookup"><span data-stu-id="993e6-440">Thread entry for writing data for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-441">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-441">Prototype</span></span>

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="993e6-442">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-442">Description</span></span>

<span data-ttu-id="993e6-443">Ta funkcja jest przenoszona do parametru inicjowania strumienia audio, jeśli jest wymagane zapisanie dźwięku na hoście.</span><span class="sxs-lookup"><span data-stu-id="993e6-443">This function is passed to the audio stream initialization parameter if writing audio to the host is desired.</span></span> <span data-ttu-id="993e6-444">Wewnętrznie wątek jest tworzony za pomocą tej funkcji jako funkcji Wejścia; sam wątek zapisuje dane audio za pomocą Isochronous w punkcie końcowym w funkcji audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-444">Internally, a thread is created with this function as its entry function; the thread itself writes audio data through the isochronous IN endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-445">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-445">Parameters</span></span>

- <span data-ttu-id="993e6-446">**audio_stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-446">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="993e6-447">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-447">Example</span></span>

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a><span data-ttu-id="993e6-448">ux_device_class_audio_stream_get</span><span class="sxs-lookup"><span data-stu-id="993e6-448">ux_device_class_audio_stream_get</span></span>

<span data-ttu-id="993e6-449">Pobierz określone wystąpienie strumienia dla funkcji audio</span><span class="sxs-lookup"><span data-stu-id="993e6-449">Get specific stream instance for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-450">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-450">Prototype</span></span>

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a><span data-ttu-id="993e6-451">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-451">Description</span></span>

<span data-ttu-id="993e6-452">Ta funkcja służy do uzyskiwania wystąpienia strumienia klasy audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-452">This function is used to get a stream instance of audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-453">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-453">Parameters</span></span>

- <span data-ttu-id="993e6-454">**audio**: wskaźnik do wystąpienia audio</span><span class="sxs-lookup"><span data-stu-id="993e6-454">**audio**: Pointer to the audio instance</span></span>
- <span data-ttu-id="993e6-455">**stream_index**: indeks wystąpienia strumienia na podstawie 0</span><span class="sxs-lookup"><span data-stu-id="993e6-455">**stream_index**: Stream instance index based on 0</span></span>
- <span data-ttu-id="993e6-456">**Stream**: wskaźnik do buforu do przechowywania wskaźnika wystąpienia strumienia audio</span><span class="sxs-lookup"><span data-stu-id="993e6-456">**stream**: Pointer to buffer to store the audio stream instance pointer</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-457">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-457">Return Value</span></span>

- <span data-ttu-id="993e6-458">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie</span><span class="sxs-lookup"><span data-stu-id="993e6-458">**UX_SUCCESS** (0x00) This operation was successful</span></span>
- <span data-ttu-id="993e6-459">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-459">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-460">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-460">Example</span></span>

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a><span data-ttu-id="993e6-461">ux_device_class_audio_reception_start</span><span class="sxs-lookup"><span data-stu-id="993e6-461">ux_device_class_audio_reception_start</span></span>

<span data-ttu-id="993e6-462">Rozpocznij odbieranie danych audio dla strumienia audio</span><span class="sxs-lookup"><span data-stu-id="993e6-462">Start audio data reception for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-463">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-463">Prototype</span></span>

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="993e6-464">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-464">Description</span></span>

<span data-ttu-id="993e6-465">Ta funkcja służy do uruchamiania odczytywania danych audio w strumieniach audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-465">This function is used to start audio data reading in audio streams.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-466">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-466">Parameters</span></span>

- <span data-ttu-id="993e6-467">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-467">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-468">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-468">Return Value</span></span>

- <span data-ttu-id="993e6-469">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-469">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-471">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) jest pełny.</span><span class="sxs-lookup"><span data-stu-id="993e6-471">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="993e6-472">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-472">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-473">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-473">Example</span></span>

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a><span data-ttu-id="993e6-474">ux_device_class_audio_sample_read8</span><span class="sxs-lookup"><span data-stu-id="993e6-474">ux_device_class_audio_sample_read8</span></span>

<span data-ttu-id="993e6-475">Odczytaj 8-bitowy przykład ze strumienia audio</span><span class="sxs-lookup"><span data-stu-id="993e6-475">Read 8-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-476">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-476">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="993e6-477">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-477">Description</span></span>

<span data-ttu-id="993e6-478">Ta funkcja odczytuje 8-bitowe dane audio próbki z określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="993e6-478">This function reads 8-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="993e6-479">W każdym przypadku odczytuje przykładowe dane z bieżącego buforu klatek audio w tabeli FIFO.</span><span class="sxs-lookup"><span data-stu-id="993e6-479">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="993e6-480">Po odczytaniu ostatniego przykładu w ramce audio ramka zostanie automatycznie zwolniona, aby mogła zostać użyta w celu zaakceptowania większej ilości danych z hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-480">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-481">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-481">Parameters</span></span>

- <span data-ttu-id="993e6-482">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-482">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="993e6-483">**bufor**: wskaźnik do buforu w celu zapisania przykładowego bajtu.</span><span class="sxs-lookup"><span data-stu-id="993e6-483">**buffer**: Pointer to the buffer to save sample byte.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-484">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-484">Return Value</span></span>

- <span data-ttu-id="993e6-485">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-485">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-487">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="993e6-487">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="993e6-488">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-488">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-489">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-489">Example</span></span>

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a><span data-ttu-id="993e6-490">ux_device_class_audio_sample_read16</span><span class="sxs-lookup"><span data-stu-id="993e6-490">ux_device_class_audio_sample_read16</span></span>

<span data-ttu-id="993e6-491">Odczytaj 16-bitowy przykład ze strumienia audio</span><span class="sxs-lookup"><span data-stu-id="993e6-491">Read 16-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-492">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-492">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a><span data-ttu-id="993e6-493">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-493">Description</span></span>

<span data-ttu-id="993e6-494">Ta funkcja odczytuje 16-bitowe dane audio z określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="993e6-494">This function reads 16-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="993e6-495">W każdym przypadku odczytuje przykładowe dane z bieżącego buforu klatek audio w tabeli FIFO.</span><span class="sxs-lookup"><span data-stu-id="993e6-495">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="993e6-496">Po odczytaniu ostatniego przykładu w ramce audio ramka zostanie automatycznie zwolniona, aby mogła zostać użyta w celu zaakceptowania większej ilości danych z hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-496">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-497">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-497">Parameters</span></span>

- <span data-ttu-id="993e6-498">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-498">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="993e6-499">**bufor**: wskaźnik do buforu, aby zapisać próbkę 16-bitową.</span><span class="sxs-lookup"><span data-stu-id="993e6-499">**buffer**: Pointer to the buffer to save the 16-bit sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-500">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-500">Return Value</span></span>

- <span data-ttu-id="993e6-501">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-501">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-503">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="993e6-503">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="993e6-504">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-504">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-505">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-505">Example</span></span>

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a><span data-ttu-id="993e6-506">ux_device_class_audio_sample_read24</span><span class="sxs-lookup"><span data-stu-id="993e6-506">ux_device_class_audio_sample_read24</span></span>

<span data-ttu-id="993e6-507">Przeczytaj przykład 24-bitowy ze strumienia audio</span><span class="sxs-lookup"><span data-stu-id="993e6-507">Read 24-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-508">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-508">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="993e6-509">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-509">Description</span></span>

<span data-ttu-id="993e6-510">Ta funkcja odczytuje dane 24-bitowe audio z określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="993e6-510">This function reads 24-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="993e6-511">W każdym przypadku odczytuje przykładowe dane z bieżącego buforu klatek audio w tabeli FIFO.</span><span class="sxs-lookup"><span data-stu-id="993e6-511">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="993e6-512">Po odczytaniu ostatniego przykładu w ramce audio ramka zostanie automatycznie zwolniona, aby mogła zostać użyta w celu zaakceptowania większej ilości danych z hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-512">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-513">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-513">Parameters</span></span>

- <span data-ttu-id="993e6-514">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-514">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="993e6-515">**bufor**: wskaźnik do buforu w celu zapisania przykładu 3-bajtowego.</span><span class="sxs-lookup"><span data-stu-id="993e6-515">**buffer**: Pointer to the buffer to save the 3-byte sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-516">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-516">Return Value</span></span>

- <span data-ttu-id="993e6-517">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-517">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-519">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="993e6-519">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="993e6-520">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-520">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-521">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-521">Example</span></span>

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a><span data-ttu-id="993e6-522">ux_device_class_audio_sample_read32</span><span class="sxs-lookup"><span data-stu-id="993e6-522">ux_device_class_audio_sample_read32</span></span>

<span data-ttu-id="993e6-523">Odczytaj 32-bitowy przykład ze strumienia audio</span><span class="sxs-lookup"><span data-stu-id="993e6-523">Read 32-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-524">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-524">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="993e6-525">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-525">Description</span></span>

<span data-ttu-id="993e6-526">Ta funkcja odczytuje 32-bitowe dane audio z określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="993e6-526">This function reads 32-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="993e6-527">W każdym przypadku odczytuje przykładowe dane z bieżącego buforu klatek audio w tabeli FIFO.</span><span class="sxs-lookup"><span data-stu-id="993e6-527">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="993e6-528">Po odczytaniu ostatniego przykładu w ramce audio ramka zostanie automatycznie zwolniona, aby mogła zostać użyta w celu zaakceptowania większej ilości danych z hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-528">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-529">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-529">Parameters</span></span>

- <span data-ttu-id="993e6-530">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-530">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="993e6-531">**bufor**: wskaźnik do buforu, aby zapisać dane 4-bajtowe.</span><span class="sxs-lookup"><span data-stu-id="993e6-531">**buffer**: Pointer to the buffer to save the 4-byte data.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-532">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-532">Return Value</span></span>

- <span data-ttu-id="993e6-533">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-533">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-535">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="993e6-535">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="993e6-536">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-536">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-537">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-537">Example</span></span>

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a><span data-ttu-id="993e6-538">ux_device_class_audio_read_frame_get</span><span class="sxs-lookup"><span data-stu-id="993e6-538">ux_device_class_audio_read_frame_get</span></span>

<span data-ttu-id="993e6-539">Uzyskiwanie dostępu do ramki audio w strumieniu audio</span><span class="sxs-lookup"><span data-stu-id="993e6-539">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-540">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-540">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="993e6-541">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-541">Description</span></span>

<span data-ttu-id="993e6-542">Ta funkcja zwraca pierwszy bufor ramki audio i jego długość z kolejki FIFO określonego strumienia.</span><span class="sxs-lookup"><span data-stu-id="993e6-542">This function returns the first audio frame buffer and its length in the specified stream's FIFO.</span></span> <span data-ttu-id="993e6-543">Gdy aplikacja zakończy przetwarzanie danych, ux_device_class_audio_read_frame_free musi być używana do zwolnienia bufora ramek w FIFO.</span><span class="sxs-lookup"><span data-stu-id="993e6-543">When the application is done processing the data, ux_device_class_audio_read_frame_free must be used to free the frame buffer in the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-544">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-544">Parameters</span></span>

- <span data-ttu-id="993e6-545">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-545">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="993e6-546">**frame_data**: wskaźnik do wskaźnika danych, na który ma zostać zwrócony wskaźnik danych.</span><span class="sxs-lookup"><span data-stu-id="993e6-546">**frame_data**: Pointer to data pointer to return the data pointer in.</span></span>
- <span data-ttu-id="993e6-547">**frame_length**: wskaźnik do buforu, aby zapisać długość ramki w liczbie bajtów.</span><span class="sxs-lookup"><span data-stu-id="993e6-547">**frame_length**: Pointer to buffer to save the frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-548">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-548">Return Value</span></span>

- <span data-ttu-id="993e6-549">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-549">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-551">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="993e6-551">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="993e6-552">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-552">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-553">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-553">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a><span data-ttu-id="993e6-554">ux_device_class_audio_read_frame_free</span><span class="sxs-lookup"><span data-stu-id="993e6-554">ux_device_class_audio_read_frame_free</span></span>

<span data-ttu-id="993e6-555">Zwolnij bufor ramki dźwiękowej w strumieniu audio</span><span class="sxs-lookup"><span data-stu-id="993e6-555">Free an audio frame buffer in Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-556">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-556">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="993e6-557">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-557">Description</span></span>

<span data-ttu-id="993e6-558">Ta funkcja zwalnia bufor ramki dźwiękowej na przedniej stronie FIFO określonego strumienia, aby mógł odbierać dane z hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-558">This function frees the audio frame buffer at the front of the specified stream's FIFO so that it can receive data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-559">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-559">Parameters</span></span>

- <span data-ttu-id="993e6-560">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-560">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-561">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-561">Return Value</span></span>

- <span data-ttu-id="993e6-562">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-562">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-564">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="993e6-564">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="993e6-565">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-565">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-566">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-566">Example</span></span>

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a><span data-ttu-id="993e6-567">ux_device_class_audio_transmission_start</span><span class="sxs-lookup"><span data-stu-id="993e6-567">ux_device_class_audio_transmission_start</span></span>

<span data-ttu-id="993e6-568">Rozpocznij transmisję danych audio dla strumienia audio</span><span class="sxs-lookup"><span data-stu-id="993e6-568">Start audio data transmission for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-569">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-569">Prototype</span></span>

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="993e6-570">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-570">Description</span></span>

<span data-ttu-id="993e6-571">Ta funkcja służy do rozpoczynania wysyłania danych audio zapisanych do FIFO w klasie audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-571">This function is used to start sending audio data written to the FIFO in the audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-572">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-572">Parameters</span></span>

- <span data-ttu-id="993e6-573">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-573">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-574">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-574">Return Value</span></span>

- <span data-ttu-id="993e6-575">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-575">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-577">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="993e6-577">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="993e6-578">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-578">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-579">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-579">Example</span></span>

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a><span data-ttu-id="993e6-580">ux_device_class_audio_frame_write</span><span class="sxs-lookup"><span data-stu-id="993e6-580">ux_device_class_audio_frame_write</span></span>

<span data-ttu-id="993e6-581">Napisz ramkę audio do strumienia audio</span><span class="sxs-lookup"><span data-stu-id="993e6-581">Write an audio frame into the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-582">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-582">Prototype</span></span>

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a><span data-ttu-id="993e6-583">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-583">Description</span></span>

<span data-ttu-id="993e6-584">Ta funkcja zapisuje ramkę do kolejki FIFO strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-584">This function writes a frame to the audio stream's FIFO.</span></span> <span data-ttu-id="993e6-585">Dane ramki są kopiowane do dostępnego buforu w tabeli FIFO, aby można było je wysyłać do hosta.</span><span class="sxs-lookup"><span data-stu-id="993e6-585">The frame data is copied to the available buffer in the FIFO so that it can be sent to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-586">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-586">Parameters</span></span>

- <span data-ttu-id="993e6-587">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-587">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="993e6-588">**ramka**: wskaźnik do danych ramek.</span><span class="sxs-lookup"><span data-stu-id="993e6-588">**frame**: Pointer to frame data.</span></span>
- <span data-ttu-id="993e6-589">**frame_length** Długość ramki w liczbie bajtów.</span><span class="sxs-lookup"><span data-stu-id="993e6-589">**frame_length** Frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-590">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-590">Return Value</span></span>

- <span data-ttu-id="993e6-591">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-591">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-593">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) jest pełny.</span><span class="sxs-lookup"><span data-stu-id="993e6-593">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="993e6-594">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-594">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-595">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-595">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a><span data-ttu-id="993e6-596">ux_device_class_audio_write_frame_get</span><span class="sxs-lookup"><span data-stu-id="993e6-596">ux_device_class_audio_write_frame_get</span></span>

<span data-ttu-id="993e6-597">Uzyskiwanie dostępu do ramki audio w strumieniu audio</span><span class="sxs-lookup"><span data-stu-id="993e6-597">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-598">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-598">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="993e6-599">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-599">Description</span></span>

<span data-ttu-id="993e6-600">Ta funkcja pobiera adres ostatniego buforu ramki audio FIFO; Pobiera również długość buforu ramki audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-600">This function retrieves the address of the last audio frame buffer of the FIFO; it also retrieves the length of the audio frame buffer.</span></span> <span data-ttu-id="993e6-601">Gdy aplikacja wypełni bufor ramki audio odpowiednimi danymi, ***ux_device_class_audio_write_frame_commit*** musi być używana do dodawania/zatwierdzania bufora RAMEK do FIFO.</span><span class="sxs-lookup"><span data-stu-id="993e6-601">After the application fills the audio frame buffer with its desired data, ***ux_device_class_audio_write_frame_commit*** must be used to add/commit the frame buffer to the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-602">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-602">Parameters</span></span>

- <span data-ttu-id="993e6-603">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-603">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="993e6-604">**frame_data**: wskaźnik do wskaźnika danych ramek, który ma zwracać wskaźnik danych ramki w.</span><span class="sxs-lookup"><span data-stu-id="993e6-604">**frame_data**: Pointer to frame data pointer to return the frame data pointer in.</span></span>
- <span data-ttu-id="993e6-605">**frame_length** Wskaźnik do buforu, aby zapisać długość ramki w liczbie bajtów.</span><span class="sxs-lookup"><span data-stu-id="993e6-605">**frame_length** Pointer to the buffer to save frame length in number of bytes .</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-606">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-606">Return Value</span></span>

- <span data-ttu-id="993e6-607">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-607">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-609">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) jest pełny.</span><span class="sxs-lookup"><span data-stu-id="993e6-609">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="993e6-610">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-610">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-611">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-611">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a><span data-ttu-id="993e6-612">ux_device_class_audio_write_frame_commit</span><span class="sxs-lookup"><span data-stu-id="993e6-612">ux_device_class_audio_write_frame_commit</span></span>

<span data-ttu-id="993e6-613">Zatwierdź bufor ramki audio w strumieniu audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-613">Commit an audio frame buffer in Audio stream.</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-614">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-614">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="993e6-615">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-615">Description</span></span>

<span data-ttu-id="993e6-616">Ta funkcja dodaje/zatwierdza ostatni bufor ramki audio do FIFO, aby bufor był gotowy do przekazania do hosta; Należy zauważyć, że ostatni bufor ramki audio powinien zostać wypełniony za pośrednictwem ux_device_class_write_frame_get.</span><span class="sxs-lookup"><span data-stu-id="993e6-616">This function adds/commits the last audio frame buffer to the FIFO so the buffer is ready to be transferred to host; note the last audio frame buffer should have been filled out via ux_device_class_write_frame_get.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-617">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-617">Parameters</span></span>

- <span data-ttu-id="993e6-618">**Stream**: wskaźnik do wystąpienia strumienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-618">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="993e6-619">**Długość**: liczba bajtów gotowych w buforze.</span><span class="sxs-lookup"><span data-stu-id="993e6-619">**length**: Number of bytes ready in the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-620">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-620">Return Value</span></span>

- <span data-ttu-id="993e6-621">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-621">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) interfejs nie działa.</span><span class="sxs-lookup"><span data-stu-id="993e6-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="993e6-623">Bufor FIFO **UX_BUFFER_OVERFLOW** (0x5D) to fssull.</span><span class="sxs-lookup"><span data-stu-id="993e6-623">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is fssull.</span></span>
- <span data-ttu-id="993e6-624">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-624">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-625">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-625">Example</span></span>

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a><span data-ttu-id="993e6-626">ux_device_class_audio10_control_process</span><span class="sxs-lookup"><span data-stu-id="993e6-626">ux_device_class_audio10_control_process</span></span>

<span data-ttu-id="993e6-627">Przetwarzanie żądań kontroli audio USB 1,0</span><span class="sxs-lookup"><span data-stu-id="993e6-627">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-628">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-628">Prototype</span></span>

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="993e6-629">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-629">Description</span></span>

<span data-ttu-id="993e6-630">Ta funkcja zarządza żądaniami podstawowymi wysyłanymi przez hosta w punkcie końcowym kontroli przy użyciu określonego typu USB audio 1,0.</span><span class="sxs-lookup"><span data-stu-id="993e6-630">This function manages basic requests sent by the host on the control endpoint with a USB Audio 1.0 specific type.</span></span>

<span data-ttu-id="993e6-631">Funkcje audio 1,0 dla woluminów i wyciszania żądań są przetwarzane w funkcji.</span><span class="sxs-lookup"><span data-stu-id="993e6-631">Audio 1.0 features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="993e6-632">Podczas przetwarzania żądań, wstępnie zdefiniowane dane przesyłane przez ostatni parametr (Grupa) są używane do odpowiedzi na żądania i zmiany kontroli magazynu.</span><span class="sxs-lookup"><span data-stu-id="993e6-632">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-633">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-633">Parameters</span></span>

- <span data-ttu-id="993e6-634">**audio**: wskaźnik do wystąpienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-634">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="993e6-635">**transfer**: wskaźnik do wystąpienia żądania transferu.</span><span class="sxs-lookup"><span data-stu-id="993e6-635">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="993e6-636">**Grupa**: Grupa danych dla procesu żądania.</span><span class="sxs-lookup"><span data-stu-id="993e6-636">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-637">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-637">Return Value</span></span>

- <span data-ttu-id="993e6-638">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-638">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-639">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-639">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-640">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-640">Example</span></span>

```C
/* Initialize audio 1.0 control values. */

audio_control[0].ux_device_class_audio10_control_fu_id = 2;
audio_control[0].ux_device_class_audio10_control_mute[0] = 0;
audio_control[0].ux_device_class_audio10_control_volume[0] = 0;
audio_control[1].ux_device_class_audio10_control_fu_id = 5;
audio_control[1].ux_device_class_audio10_control_mute[0] = 0;
audio_control[1].ux_device_class_audio10_control_volume[0] = 0;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio10_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio10_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```

## <a name="ux_device_class_audio20_control_process"></a><span data-ttu-id="993e6-641">ux_device_class_audio20_control_process</span><span class="sxs-lookup"><span data-stu-id="993e6-641">ux_device_class_audio20_control_process</span></span>

<span data-ttu-id="993e6-642">Przetwarzanie żądań kontroli audio USB 1,0</span><span class="sxs-lookup"><span data-stu-id="993e6-642">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="993e6-643">Prototype</span><span class="sxs-lookup"><span data-stu-id="993e6-643">Prototype</span></span>
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="993e6-644">Opis</span><span class="sxs-lookup"><span data-stu-id="993e6-644">Description</span></span>

<span data-ttu-id="993e6-645">Ta funkcja zarządza żądaniami podstawowymi wysyłanymi przez hosta w punkcie końcowym kontroli przy użyciu określonego typu USB audio 2,0.</span><span class="sxs-lookup"><span data-stu-id="993e6-645">This function manages basic requests sent by the host on the control endpoint with a USB Audio 2.0 specific type.</span></span>

<span data-ttu-id="993e6-646">Częstotliwość próbkowania audio 2,0 (przyjęto pojedynczą stałą częstotliwość), funkcje woluminu i wyciszania są przetwarzane w funkcji.</span><span class="sxs-lookup"><span data-stu-id="993e6-646">Audio 2.0 sampling rate (assumed single fixed frequency), features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="993e6-647">Podczas przetwarzania żądań, wstępnie zdefiniowane dane przesyłane przez ostatni parametr (Grupa) są używane do odpowiedzi na żądania i zmiany kontroli magazynu.</span><span class="sxs-lookup"><span data-stu-id="993e6-647">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="993e6-648">Parametry</span><span class="sxs-lookup"><span data-stu-id="993e6-648">Parameters</span></span>

- <span data-ttu-id="993e6-649">**audio**: wskaźnik do wystąpienia audio.</span><span class="sxs-lookup"><span data-stu-id="993e6-649">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="993e6-650">**transfer**: wskaźnik do wystąpienia żądania transferu.</span><span class="sxs-lookup"><span data-stu-id="993e6-650">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="993e6-651">**Grupa**: Grupa danych dla procesu żądania.</span><span class="sxs-lookup"><span data-stu-id="993e6-651">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="993e6-652">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="993e6-652">Return Value</span></span>

- <span data-ttu-id="993e6-653">**UX_SUCCESS** (0X00) ta operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="993e6-653">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="993e6-654">Błąd **UX_ERROR** (0xFF) z funkcji</span><span class="sxs-lookup"><span data-stu-id="993e6-654">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="993e6-655">Przykład</span><span class="sxs-lookup"><span data-stu-id="993e6-655">Example</span></span>

```C
/* Initialize audio 2.0 control values. */

audio_control[0].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[0].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[0].ux_device_class_audio20_control_fu_id = 2;
audio_control[0].ux_device_class_audio20_control_mute[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[0].ux_device_class_audio20_control_volume[0] = 50;
audio_control[1].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[1].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[1].ux_device_class_audio20_control_fu_id = 5;
audio_control[1].ux_device_class_audio20_control_mute[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[1].ux_device_class_audio20_control_volume[0] = 50;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio20_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio20_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```
