---
title: Rozdział 3-funkcjonalne składniki stosu urządzeń USBX
description: Ten rozdział zawiera opis stosu urządzenia USB o wysokiej wydajności USBX Embedded z perspektywy funkcjonalnej.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dc57f3e0f6aa6731f4aaedee8169313ca7276cff
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082204"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a><span data-ttu-id="d3b3c-103">Rozdział 3-funkcjonalne składniki stosu urządzeń USBX</span><span class="sxs-lookup"><span data-stu-id="d3b3c-103">Chapter 3 - Functional Components of USBX Device Stack</span></span>

<span data-ttu-id="d3b3c-104">Ten rozdział zawiera opis stosu urządzenia USB o wysokiej wydajności USBX Embedded z perspektywy funkcjonalnej.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-104">This chapter contains a description of the high performance USBX embedded USB device stack from a functional perspective.</span></span>

## <a name="execution-overview"></a><span data-ttu-id="d3b3c-105">Przegląd wykonywania</span><span class="sxs-lookup"><span data-stu-id="d3b3c-105">Execution Overview</span></span>

<span data-ttu-id="d3b3c-106">USBX dla urządzenia składa się z kilku składników.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-106">USBX for the device is composed of several components.</span></span>

- <span data-ttu-id="d3b3c-107">Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="d3b3c-107">Initialization</span></span>
- <span data-ttu-id="d3b3c-108">Wywołania interfejsu aplikacji</span><span class="sxs-lookup"><span data-stu-id="d3b3c-108">Application interface calls</span></span>
- <span data-ttu-id="d3b3c-109">Klasy urządzeń</span><span class="sxs-lookup"><span data-stu-id="d3b3c-109">Device Classes</span></span>
- <span data-ttu-id="d3b3c-110">Stos urządzeń USB</span><span class="sxs-lookup"><span data-stu-id="d3b3c-110">USB Device Stack</span></span>
- <span data-ttu-id="d3b3c-111">Kontroler urządzenia</span><span class="sxs-lookup"><span data-stu-id="d3b3c-111">Device controller</span></span>
- <span data-ttu-id="d3b3c-112">VBUS Manager</span><span class="sxs-lookup"><span data-stu-id="d3b3c-112">VBUS manager</span></span>

<span data-ttu-id="d3b3c-113">Na poniższym diagramie przedstawiono stos urządzeń USBX.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-113">The following diagram illustrates the USBX Device stack.</span></span>

![Stos urządzeń USBX](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a><span data-ttu-id="d3b3c-115">Inicjalizacja</span><span class="sxs-lookup"><span data-stu-id="d3b3c-115">Initialization</span></span>

<span data-ttu-id="d3b3c-116">W celu aktywowania USBX należy wywołać funkcję ***ux_system_initialize*** .</span><span class="sxs-lookup"><span data-stu-id="d3b3c-116">In order to activate USBX, the function ***ux_system_initialize*** must be called.</span></span> <span data-ttu-id="d3b3c-117">Ta funkcja inicjuje zasoby pamięci z USBX.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-117">This function initializes the memory resources of USBX.</span></span>

<span data-ttu-id="d3b3c-118">Aby można było aktywować urządzenia USBX, należy wywołać funkcję ***ux_device_stack_initialize*** .</span><span class="sxs-lookup"><span data-stu-id="d3b3c-118">In order to activate USBX device facilities, the function ***ux_device_stack_initialize*** must be called.</span></span> <span data-ttu-id="d3b3c-119">Ta funkcja spowoduje zainicjowanie wszystkich zasobów używanych przez stos urządzeń USBX, takich jak wątki ThreadX, muteksy i semafory.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-119">This function will in turn initialize all the resources used by the USBX device stack such as ThreadX threads, mutexes, and semaphores.</span></span>

<span data-ttu-id="d3b3c-120">Do inicjalizacji aplikacji można aktywować kontroler urządzeń USB i co najmniej jedną klasę USB.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-120">It is up to the application initialization to activate the USB device controller and one or more USB classes.</span></span> <span data-ttu-id="d3b3c-121">W przeciwieństwie do strony hosta USB po stronie urządzenia może być uruchomiony tylko jeden sterownik kontrolera USB w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-121">Contrary to the USB host side, the device side can have only one USB controller driver running at any time.</span></span> <span data-ttu-id="d3b3c-122">Gdy klasy zostały zarejestrowane na stosie, a funkcja inicjowania kontrolerów urządzeń została wywołana, magistrala jest aktywna, a stos odpowiada na polecenia resetowania magistrali i hosta.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-122">When the classes have been registered to the stack and the device controller(s) initialization function has been called, the bus is active and the stack will reply to bus reset and host enumeration commands.</span></span>

### <a name="application-interface-calls"></a><span data-ttu-id="d3b3c-123">Wywołania interfejsu aplikacji</span><span class="sxs-lookup"><span data-stu-id="d3b3c-123">Application Interface Calls</span></span>

<span data-ttu-id="d3b3c-124">Istnieją dwa poziomy interfejsów API w USBX.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-124">There are two levels of APIs in USBX.</span></span>

- <span data-ttu-id="d3b3c-125">Interfejsy API stosu urządzeń USB</span><span class="sxs-lookup"><span data-stu-id="d3b3c-125">USB Device Stack APIs</span></span>
- <span data-ttu-id="d3b3c-126">Interfejsy API klas urządzeń USB</span><span class="sxs-lookup"><span data-stu-id="d3b3c-126">USB Device Class APIs</span></span>

<span data-ttu-id="d3b3c-127">Zwykle aplikacja USBX nie powinna wywołać żadnego z interfejsów API stosu urządzeń USB.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-127">Normally, a USBX application should not have to call any of the USB device stack APIs.</span></span> <span data-ttu-id="d3b3c-128">Większość aplikacji będzie uzyskiwać dostęp tylko do interfejsów API klasy USB.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-128">Most applications will only access the USB Class APIs.</span></span>

### <a name="usb-device-stack-apis"></a><span data-ttu-id="d3b3c-129">Interfejsy API stosu urządzeń USB</span><span class="sxs-lookup"><span data-stu-id="d3b3c-129">USB Device Stack APIs</span></span>

<span data-ttu-id="d3b3c-130">Interfejsy API stosu urządzeń są odpowiedzialne za rejestrację składników urządzeń USBX, takich jak klasy i platforma urządzeń.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-130">The device stack APIs are responsible for the registration of USBX device components such as classes and the device framework.</span></span>

### <a name="usb-device-class-apis"></a><span data-ttu-id="d3b3c-131">Interfejsy API klas urządzeń USB</span><span class="sxs-lookup"><span data-stu-id="d3b3c-131">USB Device Class APIs</span></span>

<span data-ttu-id="d3b3c-132">Interfejsy API klas są bardzo specyficzne dla każdej klasy USB.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-132">The Class APIs are very specific to each USB class.</span></span> <span data-ttu-id="d3b3c-133">Większość typowych interfejsów API dla klas USB zapewnia usługi, takie jak otwieranie/zamykanie urządzenia oraz odczytywanie i zapisywanie na urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-133">Most of the common APIs for USB classes provided services such as opening/closing a device and reading from and writing to a device.</span></span> <span data-ttu-id="d3b3c-134">Interfejsy API są podobne do strony hosta.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-134">The APIs are similar in nature to the host side.</span></span>

## <a name="device-framework"></a><span data-ttu-id="d3b3c-135">Platforma urządzeń</span><span class="sxs-lookup"><span data-stu-id="d3b3c-135">Device Framework</span></span>

<span data-ttu-id="d3b3c-136">Urządzenie USB jest odpowiedzialne za definicję platformy urządzeń.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-136">The USB device side is responsible for the definition of the device framework.</span></span> <span data-ttu-id="d3b3c-137">Platforma urządzeń jest podzielona na trzy kategorie, zgodnie z opisem w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-137">The device framework is divided into three categories, as described in the following sections.</span></span>

### <a name="definition-of-the-components-of-the-device-framework"></a><span data-ttu-id="d3b3c-138">Definicja składników platformy urządzenia</span><span class="sxs-lookup"><span data-stu-id="d3b3c-138">Definition of the Components of the Device Framework</span></span>

<span data-ttu-id="d3b3c-139">Definicja każdego składnika platformy urządzenia jest związana z charakterem urządzenia i zasobami wykorzystywanymi przez urządzenie.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-139">The definition of each component of the device framework is related to the nature of the device and the resources utilized by the device.</span></span> <span data-ttu-id="d3b3c-140">Poniżej przedstawiono główne kategorie.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-140">Following are the main categories.</span></span>

- <span data-ttu-id="d3b3c-141">Deskryptor urządzenia</span><span class="sxs-lookup"><span data-stu-id="d3b3c-141">Device Descriptor</span></span>
- <span data-ttu-id="d3b3c-142">Deskryptor konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d3b3c-142">Configuration Descriptor</span></span>
- <span data-ttu-id="d3b3c-143">Deskryptor interfejsu</span><span class="sxs-lookup"><span data-stu-id="d3b3c-143">Interface Descriptor</span></span>
- <span data-ttu-id="d3b3c-144">Deskryptor punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="d3b3c-144">Endpoint Descriptor</span></span>

<span data-ttu-id="d3b3c-145">USBX obsługuje definicję składnika urządzenia zarówno dla wysokiej, jak i pełnej prędkości (niska szybkość jest traktowana tak samo jak Pełna szybkość).</span><span class="sxs-lookup"><span data-stu-id="d3b3c-145">USBX supports device component definition for both high and full speed (low speed being treated the same way as full speed).</span></span> <span data-ttu-id="d3b3c-146">Dzięki temu urządzenie może działać inaczej po połączeniu z hostem o dużej szybkości lub w trybie szybkim.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-146">This allows the device to operate differently when connected to a high speed or full speed host.</span></span> <span data-ttu-id="d3b3c-147">Typowymi różnicami są rozmiary poszczególnych punktów końcowych i moc zużywaną przez urządzenie.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-147">The typical differences are the size of each endpoint and the power consumed by the device.</span></span>

<span data-ttu-id="d3b3c-148">Definicja składnika urządzenia przyjmuje postać ciągu bajtowego, który jest zgodny ze specyfikacją USB.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-148">The definition of the device component takes the form of a byte string that follows the USB specification.</span></span> <span data-ttu-id="d3b3c-149">Definicja jest ciągła i kolejność, w jakiej struktura jest reprezentowana w pamięci, będzie taka sama jak wartość zwracana do hosta podczas wyliczania.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-149">The definition is contiguous and the order in which the framework is represented in memory will be the same as the one returned to the host during enumeration.</span></span>

<span data-ttu-id="d3b3c-150">Poniżej przedstawiono przykładową platformę urządzenia dla dysku flash USB o dużej szybkości.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-150">Following is an example of a device framework for a high speed USB Flash Disk.</span></span>

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a><span data-ttu-id="d3b3c-151">Definicja ciągów struktury urządzenia</span><span class="sxs-lookup"><span data-stu-id="d3b3c-151">Definition of the Strings of the Device Framework</span></span>

<span data-ttu-id="d3b3c-152">Ciągi są opcjonalne w urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-152">Strings are optional in a device.</span></span> <span data-ttu-id="d3b3c-153">Celem jest umożliwienie hostowi USB znajomości producenta urządzenia, nazwy produktu i numeru poprawki za pośrednictwem ciągów Unicode.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-153">Their purpose is to let the USB host know about the manufacturer of the device, the product name, and the revision number through Unicode strings.</span></span>

<span data-ttu-id="d3b3c-154">Główne ciągi są indeksami osadzonymi w deskryptorach urządzeń.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-154">The main strings are indexes embedded in the device descriptors.</span></span> <span data-ttu-id="d3b3c-155">Dodatkowe indeksy ciągów można osadzić w poszczególnych interfejsach.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-155">Additional strings indexes can be embedded into individual interfaces.</span></span>

<span data-ttu-id="d3b3c-156">Zakładając, że powyższa platforma urządzenia ma trzy indeksy ciągu osadzone w deskryptorze urządzenia, Definicja struktury ciągu może wyglądać podobnie jak w przypadku tego przykładowego kodu.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-156">Assuming the device framework above has three string indexes embedded into the device descriptor, the string framework definition could look like this example code.</span></span>

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38
UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

<span data-ttu-id="d3b3c-157">Jeśli różne ciągi muszą być używane dla każdej szybkości, należy użyć różnych indeksów, ponieważ indeksy są szybkością niezależny od.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-157">If different strings have to be used for each speed, different indexes must be used as the indexes are speed agnostic.</span></span>

<span data-ttu-id="d3b3c-158">Kodowanie ciągu jest oparte na formacie UNICODE.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-158">The encoding of the string is UNICODE-based.</span></span> <span data-ttu-id="d3b3c-159">Aby uzyskać więcej informacji na temat standardu kodowania UNICODE, zapoznaj się z następującą publikacją:</span><span class="sxs-lookup"><span data-stu-id="d3b3c-159">For more information on the UNICODE encoding standard refer to the following publication:</span></span>

<span data-ttu-id="d3b3c-160">*Standard Unicode, na całym świecie kodowanie znaków, wersja 1,, woluminy 1 i 2, konsorcjum Unicode, Addison-Wesley firmy Publishing, odczyt MA.*</span><span class="sxs-lookup"><span data-stu-id="d3b3c-160">*The Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 and 2, The Unicode Consortium, Addison-Wesley Publishing Company, Reading MA.*</span></span>

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a><span data-ttu-id="d3b3c-161">Definicja języków obsługiwanych przez urządzenie dla każdego ciągu</span><span class="sxs-lookup"><span data-stu-id="d3b3c-161">Definition of the Languages Supported by the Device for each String</span></span>

<span data-ttu-id="d3b3c-162">Usługa USBX ma możliwość obsługi wielu języków, chociaż jest to ustawienie domyślne w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-162">USBX has the ability to support multiple languages although English is the default.</span></span> <span data-ttu-id="d3b3c-163">Definicja każdego języka dla deskryptorów ciągów ma postać tablicy definicji języka zdefiniowanej w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-163">The definition of each language for the string descriptors is in the form of an array of languages definition defined as follows.</span></span>

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="d3b3c-164">Aby zapewnić obsługę dodatkowych języków, po prostu Dodaj kod języka podwójnego bajtu po domyślnym kodzie w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-164">To support additional languages, simply add the language code double-byte definition after the default English code.</span></span> <span data-ttu-id="d3b3c-165">Kod języka został zdefiniowany przez firmę Microsoft w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-165">The language code has been defined by Microsoft in the document.</span></span>

<span data-ttu-id="d3b3c-166">*Opracowywanie międzynarodowego oprogramowania dla systemów Windows 95 i Windows NT, Nadine Kano, Microsoft Press, Redmond WA*</span><span class="sxs-lookup"><span data-stu-id="d3b3c-166">*Developing International Software for Windows 95 and Windows NT, Nadine Kano, Microsoft Press, Redmond WA*</span></span>

## <a name="vbus-manager"></a><span data-ttu-id="d3b3c-167">VBUS Manager</span><span class="sxs-lookup"><span data-stu-id="d3b3c-167">VBUS Manager</span></span>

<span data-ttu-id="d3b3c-168">W większości projektów urządzeń USB VBUS nie jest częścią podstawowego urządzenia USB, ale nie jest podłączony do zewnętrznego interfejsu GPIO, który monitoruje sygnał liniowy.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-168">In most USB device designs, VBUS is not part of the USB Device core but rather connected to an external GPIO, which monitors the line signal.</span></span>

<span data-ttu-id="d3b3c-169">W związku z tym VBUS musi być zarządzany niezależnie od sterownika kontrolera urządzenia.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-169">As a result, VBUS has to be managed separately from the device controller driver.</span></span>

<span data-ttu-id="d3b3c-170">Jest ona do aplikacji, aby zapewnić kontrolerowi urządzenia adres VBUS we/wy.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-170">It is up to the application to provide the device controller with the address of the VBUS IO.</span></span> <span data-ttu-id="d3b3c-171">VBUS musi zostać zainicjowany przed inicjalizacją kontrolera urządzenia.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-171">VBUS must be initialized prior to the device controller initialization.</span></span>

<span data-ttu-id="d3b3c-172">W zależności od specyfikacji platformy dla monitorowania VBUS można pozwolić, aby sterownik kontrolera obsługiwał sygnały VBUS po zainicjowaniu operacji we/wy VBUS lub jeśli nie jest to możliwe, aplikacja musi dostarczyć kod do obsługi VBUS.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-172">Depending on the platform specification for monitoring VBUS, it is possible to let the controller driver handle VBUS signals after the VBUS IO is initialized or if this is not possible, the application has to provide the code for handling VBUS.</span></span>

<span data-ttu-id="d3b3c-173">Jeśli aplikacja chce obsłużyć VBUS samodzielnie, Jedynym wymaganiem jest wywołanie funkcji ***ux_device_stack_disconnect*** , gdy wykryje, że urządzenie zostało wyodrębnione.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-173">If the application wishes to handle VBUS by itself, its only requirement is to call the function ***ux_device_stack_disconnect*** when it detects that a device has been extracted.</span></span> <span data-ttu-id="d3b3c-174">Nie jest konieczne informowanie kontrolera, gdy urządzenie zostanie wstawione, ponieważ kontroler zostanie wznowiony, gdy zostanie wykryty sygnał potwierdzenia/potwierdzeń MAGISTRALi.</span><span class="sxs-lookup"><span data-stu-id="d3b3c-174">It is not necessary to inform the controller when a device is inserted because the controller will wake up when the BUS RESET assert/deassert signal is detected.</span></span>
