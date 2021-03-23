---
title: Rozdział 2 — Instalacja stosu urządzeń usługi Azure RTO USBX
description: Dowiedz się, jak zainstalować USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 097fdd3c6f09c666ec3ad6eda9e5ba3fa159cb4d
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104824354"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a><span data-ttu-id="04f05-103">Rozdział 2 — Instalacja stosu urządzeń usługi Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="04f05-103">Chapter 2 - Azure RTOS USBX Device Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="04f05-104">Zagadnienia dotyczące hosta</span><span class="sxs-lookup"><span data-stu-id="04f05-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="04f05-105">Typ komputera</span><span class="sxs-lookup"><span data-stu-id="04f05-105">Computer Type</span></span>

<span data-ttu-id="04f05-106">Projektowanie osadzone jest zwykle wykonywane na komputerach hosta z systemem Windows lub UNIX.</span><span class="sxs-lookup"><span data-stu-id="04f05-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="04f05-107">Gdy aplikacja zostanie skompilowana, połączona i umieszczona na hoście, zostanie pobrana na docelowy sprzęt do wykonania.</span><span class="sxs-lookup"><span data-stu-id="04f05-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="04f05-108">Pobierz interfejsy</span><span class="sxs-lookup"><span data-stu-id="04f05-108">Download Interfaces</span></span>

<span data-ttu-id="04f05-109">Zazwyczaj pobieranie docelowe odbywa się za pośrednictwem interfejsu szeregowego RS-232, chociaż interfejsy równoległe, USB i Ethernet są coraz bardziej popularne.</span><span class="sxs-lookup"><span data-stu-id="04f05-109">Usually the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="04f05-110">Zobacz dokumentację narzędzia deweloperskiego, aby poznać dostępne opcje.</span><span class="sxs-lookup"><span data-stu-id="04f05-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="04f05-111">Narzędzia debugowania</span><span class="sxs-lookup"><span data-stu-id="04f05-111">Debugging Tools</span></span>

<span data-ttu-id="04f05-112">Debugowanie odbywa się zwykle nad tym samym łączem, co w przypadku pobierania obrazu programu.</span><span class="sxs-lookup"><span data-stu-id="04f05-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="04f05-113">Istnieje wiele różnych debugerów, począwszy od małych programów monitorujących uruchomionych w miejscu docelowym za pomocą narzędzia Monitor debugowania w tle (BDM) i In-Circuit emulatora (lodem).</span><span class="sxs-lookup"><span data-stu-id="04f05-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="04f05-114">Narzędzie do ELIMINACJi oprogramowania zapewnia najbardziej niezawodne debugowanie rzeczywistego sprzętu docelowego.</span><span class="sxs-lookup"><span data-stu-id="04f05-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="04f05-115">Wymagane miejsce na dysku twardym</span><span class="sxs-lookup"><span data-stu-id="04f05-115">Required Hard Disk Space</span></span>

<span data-ttu-id="04f05-116">Kod źródłowy dla USBX jest dostarczany w formacie ASCII i wymaga około 500 KB miejsca na dysku twardym komputera hosta.</span><span class="sxs-lookup"><span data-stu-id="04f05-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

### <a name="target-considerations"></a><span data-ttu-id="04f05-117">Zagadnienia dotyczące obiektów docelowych</span><span class="sxs-lookup"><span data-stu-id="04f05-117">Target Considerations</span></span>

<span data-ttu-id="04f05-118">USBX wymaga od 24 kilobajtów do 64 kilobajtów pamięci tylko do odczytu (ROM) w obszarze docelowym w trybie hosta.</span><span class="sxs-lookup"><span data-stu-id="04f05-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="04f05-119">Wymagana ilość pamięci zależy od typu używanego kontrolera i klas USB połączonych z USBX.</span><span class="sxs-lookup"><span data-stu-id="04f05-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="04f05-120">Do USBX globalnych struktur danych i puli pamięci wymagane są inne 32 kilobajty pamięci docelowej (RAM).</span><span class="sxs-lookup"><span data-stu-id="04f05-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="04f05-121">Tę pulę pamięci można również dostosować w zależności od oczekiwanej liczby urządzeń USB i typu kontrolera USB.</span><span class="sxs-lookup"><span data-stu-id="04f05-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="04f05-122">Po stronie urządzenia USBX wymagane jest około 10-12 K pamięci ROM w zależności od typu kontrolera urządzenia.</span><span class="sxs-lookup"><span data-stu-id="04f05-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="04f05-123">Użycie pamięci RAM zależy od typu klasy emulowanej przez urządzenie.</span><span class="sxs-lookup"><span data-stu-id="04f05-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="04f05-124">USBX opiera się również na semaforach ThreadX, muteksach i wątkach na potrzeby ochrony wielu wątków oraz zawieszania operacji we/wy i okresowego przetwarzania dla monitorowania topologii magistrali USB.</span><span class="sxs-lookup"><span data-stu-id="04f05-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="04f05-125">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="04f05-125">Product Distribution</span></span>

<span data-ttu-id="04f05-126">Usługę Azure RTO USBX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/usbx/> .</span><span class="sxs-lookup"><span data-stu-id="04f05-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="04f05-127">Poniżej znajduje się lista kilku ważnych plików w repozytorium.</span><span class="sxs-lookup"><span data-stu-id="04f05-127">The following is a list of several important files in the repository.</span></span>

* <span data-ttu-id="04f05-128">***ux_api. h***: ten plik nagłówka C zawiera wszystkie równe systemowe, struktury danych i prototypy usługi.</span><span class="sxs-lookup"><span data-stu-id="04f05-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
* <span data-ttu-id="04f05-129">***ux_port. h***: ten plik nagłówkowy C zawiera wszystkie definicje i struktury danych specyficzne dla narzędzia deweloperskiego.</span><span class="sxs-lookup"><span data-stu-id="04f05-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
* <span data-ttu-id="04f05-130">***UX. lib***: jest to wersja binarna biblioteki USBX C.</span><span class="sxs-lookup"><span data-stu-id="04f05-130">***ux.lib***:  This is the binary version of the USBX C library.</span></span> <span data-ttu-id="04f05-131">Jest dystrybuowana z pakietem standardowym.</span><span class="sxs-lookup"><span data-stu-id="04f05-131">It is distributed with the standard package.</span></span>
* <span data-ttu-id="04f05-132">***demo_usbx. c***: plik c zawierający prostą wersję DEMONSTRACYJNą USBx</span><span class="sxs-lookup"><span data-stu-id="04f05-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="04f05-133">Wszystkie nazwy plików są małymi literami.</span><span class="sxs-lookup"><span data-stu-id="04f05-133">All filenames are in lower-case.</span></span> <span data-ttu-id="04f05-134">Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformę deweloperskią systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="04f05-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="04f05-135">Instalacja USBX</span><span class="sxs-lookup"><span data-stu-id="04f05-135">USBX Installation</span></span>

<span data-ttu-id="04f05-136">USBX jest instalowany przez klonowanie repozytorium GitHub na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="04f05-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="04f05-137">Poniżej przedstawiono typową składnię tworzenia klonu repozytorium USBX na komputerze:</span><span class="sxs-lookup"><span data-stu-id="04f05-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="04f05-138">Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku Pobierz na stronie głównej usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="04f05-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="04f05-139">Znajdziesz również instrukcje dotyczące tworzenia biblioteki USBX na stronie frontonu repozytorium online.</span><span class="sxs-lookup"><span data-stu-id="04f05-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="04f05-140">Poniższe instrukcje ogólne dotyczą niemal każdej instalacji:</span><span class="sxs-lookup"><span data-stu-id="04f05-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="04f05-141">Użyj tego samego katalogu, w którym wcześniej zainstalowano ThreadX na dysku twardym hosta.</span><span class="sxs-lookup"><span data-stu-id="04f05-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="04f05-142">Wszystkie nazwy USBX są unikatowe i nie zakłócają instalacji poprzedniej USBX.</span><span class="sxs-lookup"><span data-stu-id="04f05-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
1. <span data-ttu-id="04f05-143">Dodaj wywołanie do \***ux_system_initialize** _ lub blisko początku _ *_tx_application_define_* \*.</span><span class="sxs-lookup"><span data-stu-id="04f05-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _*_tx_application_define_\*\*.</span></span> <span data-ttu-id="04f05-144">Jest to miejsce, w którym zainicjowano zasoby USBX.</span><span class="sxs-lookup"><span data-stu-id="04f05-144">This is where the USBX resources are initialized.</span></span>
1. <span data-ttu-id="04f05-145">Dodaj wywołanie do \*\**ux_device_stack_initialize *.**</span><span class="sxs-lookup"><span data-stu-id="04f05-145">Add a call to \***ux_device_stack_initialize\*.**</span></span>
1. <span data-ttu-id="04f05-146">Dodaj co najmniej jedno wywołanie, aby zainicjować wymagane klasy USBX (klasy hosta i/lub urządzeń)</span><span class="sxs-lookup"><span data-stu-id="04f05-146">Add one or more calls to initialize the required USBX classes (either host and/or devices classes)</span></span>
1. <span data-ttu-id="04f05-147">Dodaj co najmniej jedno wywołanie w celu zainicjowania kontrolera urządzenia dostępnego w systemie.</span><span class="sxs-lookup"><span data-stu-id="04f05-147">Add one or more calls to initialize the device controller available in the system.</span></span>
1. <span data-ttu-id="04f05-148">Może być konieczne zmodyfikowanie pliku tx_low_level_initialize. c, aby dodać inicjalizację sprzętu niskiego poziomu i Routing wektora przerwania.</span><span class="sxs-lookup"><span data-stu-id="04f05-148">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="04f05-149">Jest to specyficzne dla platformy sprzętowej i nie zostanie omówiona w tym miejscu. |</span><span class="sxs-lookup"><span data-stu-id="04f05-149">This is specific to the hardware platform and will not be discussed here.|</span></span>
1. <span data-ttu-id="04f05-150">Kompiluj kod źródłowy aplikacji i linki z bibliotekami czasu wykonywania USBX i ThreadX (FileX i/lub NetX mogą być również wymagane, jeśli Klasa magazynu USB i/lub klasy sieci USB mają być kompilowane), UX. a (lub UX. lib) i TX. a (lub TX. lib).</span><span class="sxs-lookup"><span data-stu-id="04f05-150">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="04f05-151">Wyniki można pobrać do elementu docelowego i wykonać!</span><span class="sxs-lookup"><span data-stu-id="04f05-151">The resulting can be downloaded to the target and executed!</span></span>

## <a name="configuration-options"></a><span data-ttu-id="04f05-152">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="04f05-152">Configuration Options</span></span>

<span data-ttu-id="04f05-153">Istnieje kilka opcji konfiguracji do kompilowania biblioteki USBX.</span><span class="sxs-lookup"><span data-stu-id="04f05-153">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="04f05-154">Wszystkie opcje znajdują się w ***ux_user. h***.</span><span class="sxs-lookup"><span data-stu-id="04f05-154">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="04f05-155">Poniższa lista zawiera szczegóły każdej opcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="04f05-155">The list below details each configuration option.</span></span>

| <span data-ttu-id="04f05-156">&nbsp;Opcja konfiguracji</span><span class="sxs-lookup"><span data-stu-id="04f05-156">Configuration&nbsp;Option</span></span> | <span data-ttu-id="04f05-157">Opis</span><span class="sxs-lookup"><span data-stu-id="04f05-157">Description</span></span> |
| --- | --- |
| <span data-ttu-id="04f05-158">**UX_PERIODIC_RATE**</span><span class="sxs-lookup"><span data-stu-id="04f05-158">**UX_PERIODIC_RATE**</span></span> | <span data-ttu-id="04f05-159">Ta wartość reprezentuje liczbę taktów (w sekundach) dla określonej platformy sprzętowej.</span><span class="sxs-lookup"><span data-stu-id="04f05-159">This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="04f05-160">Wartość domyślna to 1000 wskazujący 1 takt na milisekundy.</span><span class="sxs-lookup"><span data-stu-id="04f05-160">The default is 1000 indicating 1 tick per millisecond.</span></span> |
| <span data-ttu-id="04f05-161">**UX_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="04f05-161">**UX_THREAD_STACK_SIZE**</span></span> | <span data-ttu-id="04f05-162">Ta wartość to rozmiar stosu w bajtach dla wątków USBX.</span><span class="sxs-lookup"><span data-stu-id="04f05-162">This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="04f05-163">Może to być zwykle 1024 bajtów lub 2048 bajtów w zależności od używanego procesora i kontrolera hosta.</span><span class="sxs-lookup"><span data-stu-id="04f05-163">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span> |
| <span data-ttu-id="04f05-164">**UX_THREAD_PRIORITY_ENUM**</span><span class="sxs-lookup"><span data-stu-id="04f05-164">**UX_THREAD_PRIORITY_ENUM**</span></span> | <span data-ttu-id="04f05-165">Jest to wartość priorytetu ThreadX dla wątków wyliczenia USBX, które monitorują topologię magistrali.</span><span class="sxs-lookup"><span data-stu-id="04f05-165">This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span> |
| <span data-ttu-id="04f05-166">**UX_THREAD_PRIORITY_CLASS**</span><span class="sxs-lookup"><span data-stu-id="04f05-166">**UX_THREAD_PRIORITY_CLASS**</span></span> | <span data-ttu-id="04f05-167">Jest to wartość priorytetu ThreadX dla standardowych wątków USBX.</span><span class="sxs-lookup"><span data-stu-id="04f05-167">This is the ThreadX priority value for the standard USBX threads.</span></span> |
| <span data-ttu-id="04f05-168">**UX_THREAD_PRIORITY_KEYBOARD**</span><span class="sxs-lookup"><span data-stu-id="04f05-168">**UX_THREAD_PRIORITY_KEYBOARD**</span></span> | <span data-ttu-id="04f05-169">Jest to wartość priorytetu ThreadX dla klasy klawiatury HID USBX.</span><span class="sxs-lookup"><span data-stu-id="04f05-169">This is the ThreadX priority value for the USBX HID keyboard class.</span></span> |
| <span data-ttu-id="04f05-170">**UX_THREAD_PRIORITY_DCD**</span><span class="sxs-lookup"><span data-stu-id="04f05-170">**UX_THREAD_PRIORITY_DCD**</span></span> | <span data-ttu-id="04f05-171">Jest to wartość priorytetu ThreadX dla wątku kontrolera urządzenia.</span><span class="sxs-lookup"><span data-stu-id="04f05-171">This is the ThreadX priority value for the device controller thread.</span></span> |
| <span data-ttu-id="04f05-172">**UX_NO_TIME_SLICE**</span><span class="sxs-lookup"><span data-stu-id="04f05-172">**UX_NO_TIME_SLICE**</span></span> | <span data-ttu-id="04f05-173">Ta wartość w rzeczywistości definiuje wycinek czasu, który będzie używany dla wątków.</span><span class="sxs-lookup"><span data-stu-id="04f05-173">This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="04f05-174">Na przykład, jeśli określono wartość 0, port docelowy ThreadX nie korzysta z wycinków czasu.</span><span class="sxs-lookup"><span data-stu-id="04f05-174">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span> |
| <span data-ttu-id="04f05-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span><span class="sxs-lookup"><span data-stu-id="04f05-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span></span> | <span data-ttu-id="04f05-176">Jest to maksymalna liczba klas USBX, które mogą być rejestrowane za pośrednictwem ux_device_stack_class_register.</span><span class="sxs-lookup"><span data-stu-id="04f05-176">This is the maximum number of USBX classes that can be registered via ux_device_stack_class_register.</span></span> |
| <span data-ttu-id="04f05-177">**UX_MAX_SLAVE_LUN**</span><span class="sxs-lookup"><span data-stu-id="04f05-177">**UX_MAX_SLAVE_LUN**</span></span> | <span data-ttu-id="04f05-178">Ta wartość reprezentuje bieżącą liczbę jednostek logicznych SCSI przedstawionych w sterowniku klasy magazynu urządzeń.</span><span class="sxs-lookup"><span data-stu-id="04f05-178">This value represents the current number of SCSI logical units represented in the device storage class driver.</span></span> |
| <span data-ttu-id="04f05-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span><span class="sxs-lookup"><span data-stu-id="04f05-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span></span> | <span data-ttu-id="04f05-180">W przypadku zdefiniowania klasy Storage będzie obsługiwać polecenia wielonośnikowe (MMC), czyli DVD-ROM.</span><span class="sxs-lookup"><span data-stu-id="04f05-180">If defined, the storage class will handle Multi-Media Commands (MMC) that is, DVD-ROM.</span></span> |
| <span data-ttu-id="04f05-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span><span class="sxs-lookup"><span data-stu-id="04f05-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span></span> | <span data-ttu-id="04f05-182">Ta wartość reprezentuje liczbę pakietów NetX w puli pakietów przechwytywania zmian-ECM.</span><span class="sxs-lookup"><span data-stu-id="04f05-182">This value represents the number of NetX packets in the CDC-ECM class' packet pool.</span></span> <span data-ttu-id="04f05-183">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="04f05-183">The default is 16.</span></span> |
| <span data-ttu-id="04f05-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="04f05-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span></span> | <span data-ttu-id="04f05-185">Ta wartość reprezentuje maksymalną liczbę bajtów odebranych w punkcie końcowym kontrolki w stosie urządzeń.</span><span class="sxs-lookup"><span data-stu-id="04f05-185">This value represents the maximum number of bytes received on a control endpoint in the device stack.</span></span> <span data-ttu-id="04f05-186">Wartość domyślna to 256 bajtów, ale można ją zmniejszyć w środowiskach ograniczeń pamięci.</span><span class="sxs-lookup"><span data-stu-id="04f05-186">The default is 256 bytes but can be reduced in memory constraint environments.</span></span> |
| <span data-ttu-id="04f05-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="04f05-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span></span> | <span data-ttu-id="04f05-188">Ta wartość reprezentuje maksymalną długość w bajtach raportu HID.</span><span class="sxs-lookup"><span data-stu-id="04f05-188">This value represents the maximum length in bytes of a HID report.</span></span> |
| <span data-ttu-id="04f05-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span><span class="sxs-lookup"><span data-stu-id="04f05-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span></span> | <span data-ttu-id="04f05-190">Ta wartość reprezentuje maksymalną liczbę raportów HID, które mogą być umieszczone w kolejce jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="04f05-190">This value represents the maximum number of HID reports that can be queued at once.</span></span> |
| <span data-ttu-id="04f05-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="04f05-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span></span> | <span data-ttu-id="04f05-192">Ta wartość reprezentuje maksymalną liczbę bajtów odebranych w zbiorczym punkcie końcowym w stosie urządzeń.</span><span class="sxs-lookup"><span data-stu-id="04f05-192">This value represents the maximum number of bytes received on a bulk endpoint in the device stack.</span></span> <span data-ttu-id="04f05-193">Wartość domyślna to 4096 bajtów, ale można ją zmniejszyć w środowiskach ograniczeń pamięci.</span><span class="sxs-lookup"><span data-stu-id="04f05-193">The default is 4096 bytes but can be reduced in memory constraint environments.</span></span> |

## <a name="source-code-tree"></a><span data-ttu-id="04f05-194">Drzewo kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="04f05-194">Source Code Tree</span></span>

<span data-ttu-id="04f05-195">Pliki USBX są dostępne w kilku katalogach.</span><span class="sxs-lookup"><span data-stu-id="04f05-195">The USBX files are provided in several directories.</span></span>

![Drzewo kodu źródłowego](media/usbx-device-stack/source-code-tree.png)

<span data-ttu-id="04f05-197">Aby pliki były rozpoznawane według ich nazw, przyjęto następującą konwencję:</span><span class="sxs-lookup"><span data-stu-id="04f05-197">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="04f05-198">Nazwa sufiksu pliku</span><span class="sxs-lookup"><span data-stu-id="04f05-198">File Suffix Name</span></span>  | <span data-ttu-id="04f05-199">Opis pliku</span><span class="sxs-lookup"><span data-stu-id="04f05-199">File description</span></span>                          |
| ----------------- | ----------------------------------------- |
| <span data-ttu-id="04f05-200">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="04f05-200">ux_host_stack</span></span>   | <span data-ttu-id="04f05-201">podstawowe pliki stosu hosta USBx</span><span class="sxs-lookup"><span data-stu-id="04f05-201">usbx host stack core files</span></span>                |
| <span data-ttu-id="04f05-202">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="04f05-202">ux_host_class</span></span>   | <span data-ttu-id="04f05-203">pliki klas stosu hosta USBx</span><span class="sxs-lookup"><span data-stu-id="04f05-203">usbx host stack classes files</span></span>             |
| <span data-ttu-id="04f05-204">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="04f05-204">ux_hcd</span></span>           | <span data-ttu-id="04f05-205">pliki sterowników kontrolera stosu hosta USBx</span><span class="sxs-lookup"><span data-stu-id="04f05-205">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="04f05-206">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="04f05-206">ux_device_stack</span></span> | <span data-ttu-id="04f05-207">podstawowe pliki stosu urządzeń USBx</span><span class="sxs-lookup"><span data-stu-id="04f05-207">usbx device stack core files</span></span>              |
| <span data-ttu-id="04f05-208">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="04f05-208">ux_device_class</span></span> | <span data-ttu-id="04f05-209">pliki klas stosu urządzeń USBx</span><span class="sxs-lookup"><span data-stu-id="04f05-209">usbx device stack classes files</span></span>           |
| <span data-ttu-id="04f05-210">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="04f05-210">ux_dcd</span></span>           | <span data-ttu-id="04f05-211">pliki sterowników kontrolera stosu urządzeń USBx</span><span class="sxs-lookup"><span data-stu-id="04f05-211">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="04f05-212">ux_otg</span><span class="sxs-lookup"><span data-stu-id="04f05-212">ux_otg</span></span>           | <span data-ttu-id="04f05-213">pliki powiązane z sterownikiem kontrolera OTG USBx</span><span class="sxs-lookup"><span data-stu-id="04f05-213">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="04f05-214">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="04f05-214">ux_pictbridge</span></span>    | <span data-ttu-id="04f05-215">Pliki USBx PictBridge</span><span class="sxs-lookup"><span data-stu-id="04f05-215">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="04f05-216">ux_utility</span><span class="sxs-lookup"><span data-stu-id="04f05-216">ux_utility</span></span>       | <span data-ttu-id="04f05-217">funkcje narzędzia USBx</span><span class="sxs-lookup"><span data-stu-id="04f05-217">usbx utility functions</span></span>                    |
| <span data-ttu-id="04f05-218">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="04f05-218">demo_usbx</span></span>        | <span data-ttu-id="04f05-219">pliki demonstracyjne dla USBX</span><span class="sxs-lookup"><span data-stu-id="04f05-219">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="04f05-220">Inicjowanie zasobów USBX</span><span class="sxs-lookup"><span data-stu-id="04f05-220">Initialization of USBX resources</span></span>

<span data-ttu-id="04f05-221">USBX ma własny Menedżer pamięci.</span><span class="sxs-lookup"><span data-stu-id="04f05-221">USBX has its own memory manager.</span></span> <span data-ttu-id="04f05-222">Pamięć należy przydzielyć do USBX przed zainicjowaniem hosta lub po stronie urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="04f05-222">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="04f05-223">Menedżer pamięci USBX może obsługiwać systemy, w których pamięć może być buforowana.</span><span class="sxs-lookup"><span data-stu-id="04f05-223">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="04f05-224">Poniższa funkcja inicjuje zasoby pamięci USBX z 128 K zwykłej pamięci i nie ma oddzielnej puli pamięci podręcznej w bezpiecznym miejscu:</span><span class="sxs-lookup"><span data-stu-id="04f05-224">The following function initializes USBX memory resources with 128 K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="04f05-225">Prototyp ux_system_initialize jest następujący:</span><span class="sxs-lookup"><span data-stu-id="04f05-225">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

<span data-ttu-id="04f05-226">Parametry wejściowe:</span><span class="sxs-lookup"><span data-stu-id="04f05-226">Input parameters:</span></span>

| <span data-ttu-id="04f05-227">Parametr</span><span class="sxs-lookup"><span data-stu-id="04f05-227">Parameter</span></span>                          | <span data-ttu-id="04f05-228">Opis</span><span class="sxs-lookup"><span data-stu-id="04f05-228">Description</span></span>                             |
| ---------------------------------- | --------------------------------------- |
| <span data-ttu-id="04f05-229">VOID \* regular_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="04f05-229">VOID \*regular_memory_pool_start</span></span>    | <span data-ttu-id="04f05-230">Początek zwykłej puli pamięci</span><span class="sxs-lookup"><span data-stu-id="04f05-230">Beginning of the regular memory pool</span></span>    |
| <span data-ttu-id="04f05-231">ULONG regular_memory_size</span><span class="sxs-lookup"><span data-stu-id="04f05-231">ULONG regular_memory_size</span></span>          | <span data-ttu-id="04f05-232">Rozmiar zwykłej puli pamięci</span><span class="sxs-lookup"><span data-stu-id="04f05-232">Size of the regular memory pool</span></span>         |
| <span data-ttu-id="04f05-233">VOID \* cache_safe_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="04f05-233">VOID \*cache_safe_memory_pool_start</span></span> | <span data-ttu-id="04f05-234">Początek bezpiecznej puli pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="04f05-234">Beginning of the cache safe memory pool</span></span> |
| <span data-ttu-id="04f05-235">ULONG cache_safe_memory_size</span><span class="sxs-lookup"><span data-stu-id="04f05-235">ULONG cache_safe_memory_size</span></span>       | <span data-ttu-id="04f05-236">Rozmiar bezpiecznej puli pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="04f05-236">Size of the cache safe memory pool</span></span>      |

<span data-ttu-id="04f05-237">Nie wszystkie systemy wymagają definicji bezpiecznej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="04f05-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="04f05-238">W takim systemie wartości przesyłane podczas inicjalizacji wskaźnika pamięci będą ustawione na UX_NULL i rozmiar puli do 0.</span><span class="sxs-lookup"><span data-stu-id="04f05-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="04f05-239">Następnie USBX będzie używać zwykłej puli pamięci w miejsce pamięci podręcznej w bezpiecznej puli.</span><span class="sxs-lookup"><span data-stu-id="04f05-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="04f05-240">W systemie, w którym zwykła pamięć nie jest bezpieczna w pamięci podręcznej, a kontroler wymaga przeprowadzenia pamięci DMA, należy zdefiniować pulę pamięci w bezpiecznej strefie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="04f05-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="04f05-241">Odinicjowanie zasobów USBX</span><span class="sxs-lookup"><span data-stu-id="04f05-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="04f05-242">USBX można przerwać, zwalniając jego zasoby.</span><span class="sxs-lookup"><span data-stu-id="04f05-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="04f05-243">Przed zakończeniem USBx należy prawidłowo zakończyć wszystkie klasy i zasoby kontrolerów.</span><span class="sxs-lookup"><span data-stu-id="04f05-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="04f05-244">Następująca funkcja nie inicjuje USBX zasobów pamięci:</span><span class="sxs-lookup"><span data-stu-id="04f05-244">The following function uninitializes USBX memory resources:</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="04f05-245">Prototyp ux_system_initialize jest następujący:</span><span class="sxs-lookup"><span data-stu-id="04f05-245">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a><span data-ttu-id="04f05-246">Definicja kontrolera urządzenia USB</span><span class="sxs-lookup"><span data-stu-id="04f05-246">Definition of USB Device Controller</span></span>

<span data-ttu-id="04f05-247">W dowolnym momencie można zdefiniować tylko jeden kontroler urządzenia USB do działania w trybie urządzenia.</span><span class="sxs-lookup"><span data-stu-id="04f05-247">Only one USB device controller can be defined at any time to operate in device mode.</span></span> <span data-ttu-id="04f05-248">Plik inicjujący aplikacji powinien zawierać tę definicję.</span><span class="sxs-lookup"><span data-stu-id="04f05-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="04f05-249">W poniższym wierszu jest wykonywana definicja ogólnego kontrolera USB:</span><span class="sxs-lookup"><span data-stu-id="04f05-249">The following line performs the definition of a generic usb controller:</span></span>

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

<span data-ttu-id="04f05-250">Inicjalizacja urządzenia USB ma następujący prototyp:</span><span class="sxs-lookup"><span data-stu-id="04f05-250">The USB device initialization has the following prototype:</span></span>

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

<span data-ttu-id="04f05-251">z następującymi parametrami:</span><span class="sxs-lookup"><span data-stu-id="04f05-251">with the following parameters:</span></span>

| <span data-ttu-id="04f05-252">Pararmeter</span><span class="sxs-lookup"><span data-stu-id="04f05-252">Pararmeter</span></span>               | <span data-ttu-id="04f05-253">Opis</span><span class="sxs-lookup"><span data-stu-id="04f05-253">Description</span></span>                      |
| ------------------------ | -------------------------------- |
| <span data-ttu-id="04f05-254">ULONG dcd_io</span><span class="sxs-lookup"><span data-stu-id="04f05-254">ULONG dcd_io</span></span>            | <span data-ttu-id="04f05-255">Adres operacji we/wy kontrolera</span><span class="sxs-lookup"><span data-stu-id="04f05-255">Address of the controller IO</span></span>     |
| <span data-ttu-id="04f05-256">ULONG dcd_irq</span><span class="sxs-lookup"><span data-stu-id="04f05-256">ULONG dcd_irq</span></span>           | <span data-ttu-id="04f05-257">Przerwanie używane przez kontroler</span><span class="sxs-lookup"><span data-stu-id="04f05-257">Interrupt used by the controller</span></span> |
| <span data-ttu-id="04f05-258">ULONG dcd_vbus_address</span><span class="sxs-lookup"><span data-stu-id="04f05-258">ULONG dcd_vbus_address</span></span> | <span data-ttu-id="04f05-259">Adres VBUS GPIO</span><span class="sxs-lookup"><span data-stu-id="04f05-259">Address of the VBUS GPIO</span></span>         |

<span data-ttu-id="04f05-260">Poniższy przykład to Inicjalizacja USBX w trybie urządzenia z klasą urządzenia magazynującego i ogólnym kontrolerem:</span><span class="sxs-lookup"><span data-stu-id="04f05-260">The following example is the initialization of USBX in device mode with the storage device class and a generic controller:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a><span data-ttu-id="04f05-261">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="04f05-261">Troubleshooting</span></span>

<span data-ttu-id="04f05-262">USBX jest dostarczany z plikiem demonstracyjnym i środowiskiem symulacji.</span><span class="sxs-lookup"><span data-stu-id="04f05-262">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="04f05-263">Zawsze dobrym pomysłem jest rozpoczęcie od pierwszego uruchomienia platformy demonstracyjnej — na sprzęcie docelowym lub na określonej platformie demonstracyjnej.</span><span class="sxs-lookup"><span data-stu-id="04f05-263">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="04f05-264">Identyfikator wersji USBX</span><span class="sxs-lookup"><span data-stu-id="04f05-264">USBX Version ID</span></span>

<span data-ttu-id="04f05-265">Bieżąca wersja programu USBX jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="04f05-265">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="04f05-266">Programista może uzyskać wersję USBX z badania pliku \***ux_port. h** _.</span><span class="sxs-lookup"><span data-stu-id="04f05-266">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="04f05-267">Ponadto ten plik zawiera również historię wersji odpowiedniego portu.</span><span class="sxs-lookup"><span data-stu-id="04f05-267">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="04f05-268">Oprogramowanie aplikacji może uzyskać wersję USBX, badając ciąg globalny _ _ *_ux_version_id_* _, który jest zdefiniowany w _ *_ux_port. h_* \*.</span><span class="sxs-lookup"><span data-stu-id="04f05-268">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
