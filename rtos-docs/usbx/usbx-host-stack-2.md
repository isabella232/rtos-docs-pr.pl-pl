---
title: Rozdział 2 — Instalacja stosu hosta usługi Azure RTO USBX
description: Dowiedz się, jak zainstalować stos hosta USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 4c33f95b8ac268c557fd947a1303ec3af315a37e
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377088"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a><span data-ttu-id="aacc9-103">Rozdział 2 — Instalacja stosu hosta usługi Azure RTO USBX</span><span class="sxs-lookup"><span data-stu-id="aacc9-103">Chapter 2 - Azure RTOS USBX Host Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="aacc9-104">Zagadnienia dotyczące hosta</span><span class="sxs-lookup"><span data-stu-id="aacc9-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="aacc9-105">Typ komputera</span><span class="sxs-lookup"><span data-stu-id="aacc9-105">Computer Type</span></span>

<span data-ttu-id="aacc9-106">Projektowanie osadzone jest zwykle wykonywane na komputerach hosta z systemem Windows lub UNIX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="aacc9-107">Gdy aplikacja zostanie skompilowana, połączona i umieszczona na hoście, zostanie pobrana na docelowy sprzęt do wykonania.</span><span class="sxs-lookup"><span data-stu-id="aacc9-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="aacc9-108">Pobierz interfejsy</span><span class="sxs-lookup"><span data-stu-id="aacc9-108">Download Interfaces</span></span>

<span data-ttu-id="aacc9-109">Zazwyczaj pobieranie docelowe odbywa się za pośrednictwem interfejsu szeregowego RS-232, chociaż interfejsy równoległe, USB i Ethernet są coraz bardziej popularne.</span><span class="sxs-lookup"><span data-stu-id="aacc9-109">Usually, the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="aacc9-110">Zobacz dokumentację narzędzia deweloperskiego, aby poznać dostępne opcje.</span><span class="sxs-lookup"><span data-stu-id="aacc9-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="aacc9-111">Narzędzia debugowania</span><span class="sxs-lookup"><span data-stu-id="aacc9-111">Debugging Tools</span></span>

<span data-ttu-id="aacc9-112">Debugowanie odbywa się zwykle nad tym samym łączem, co w przypadku pobierania obrazu programu.</span><span class="sxs-lookup"><span data-stu-id="aacc9-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="aacc9-113">Istnieje wiele różnych debugerów, począwszy od małych programów monitorujących uruchomionych w miejscu docelowym za pomocą narzędzia Monitor debugowania w tle (BDM) i In-Circuit emulatora (lodem).</span><span class="sxs-lookup"><span data-stu-id="aacc9-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="aacc9-114">Narzędzie do ELIMINACJi oprogramowania zapewnia najbardziej niezawodne debugowanie rzeczywistego sprzętu docelowego.</span><span class="sxs-lookup"><span data-stu-id="aacc9-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="aacc9-115">Wymagane miejsce na dysku twardym</span><span class="sxs-lookup"><span data-stu-id="aacc9-115">Required Hard Disk Space</span></span>

<span data-ttu-id="aacc9-116">Kod źródłowy dla USBX jest dostarczany w formacie ASCII i wymaga około 500 KB miejsca na dysku twardym komputera hosta.</span><span class="sxs-lookup"><span data-stu-id="aacc9-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="aacc9-117">Zagadnienia dotyczące obiektów docelowych</span><span class="sxs-lookup"><span data-stu-id="aacc9-117">Target Considerations</span></span>

<span data-ttu-id="aacc9-118">USBX wymaga od 24 kilobajtów do 64 kilobajtów pamięci tylko do odczytu (ROM) w obszarze docelowym w trybie hosta.</span><span class="sxs-lookup"><span data-stu-id="aacc9-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="aacc9-119">Wymagana ilość pamięci zależy od typu używanego kontrolera i klas USB połączonych z USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="aacc9-120">Do USBX globalnych struktur danych i puli pamięci wymagane są inne 32 kilobajty pamięci docelowej (RAM).</span><span class="sxs-lookup"><span data-stu-id="aacc9-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="aacc9-121">Tę pulę pamięci można również dostosować w zależności od oczekiwanej liczby urządzeń USB i typu kontrolera USB.</span><span class="sxs-lookup"><span data-stu-id="aacc9-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="aacc9-122">Po stronie urządzenia USBX wymagane jest około 10-12 K pamięci ROM w zależności od typu kontrolera urządzenia.</span><span class="sxs-lookup"><span data-stu-id="aacc9-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="aacc9-123">Użycie pamięci RAM zależy od typu klasy emulowanej przez urządzenie.</span><span class="sxs-lookup"><span data-stu-id="aacc9-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="aacc9-124">USBX opiera się również na semaforach ThreadX, muteksach i wątkach na potrzeby ochrony wielu wątków oraz zawieszania operacji we/wy i okresowego przetwarzania dla monitorowania topologii magistrali USB.</span><span class="sxs-lookup"><span data-stu-id="aacc9-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="aacc9-125">Dystrybucja produktu</span><span class="sxs-lookup"><span data-stu-id="aacc9-125">Product Distribution</span></span>

<span data-ttu-id="aacc9-126">Usługę Azure RTO USBX można uzyskać z naszego publicznego repozytorium kodu źródłowego w lokalizacji <https://github.com/azure-rtos/usbx/> .</span><span class="sxs-lookup"><span data-stu-id="aacc9-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="aacc9-127">Poniżej znajduje się lista kilku ważnych plików w repozytorium:</span><span class="sxs-lookup"><span data-stu-id="aacc9-127">The following is a list of several important files in the repository:</span></span>

- <span data-ttu-id="aacc9-128">***ux_api. h***: ten plik nagłówka C zawiera wszystkie równe systemowe, struktury danych i prototypy usługi.</span><span class="sxs-lookup"><span data-stu-id="aacc9-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
- <span data-ttu-id="aacc9-129">***ux_port. h***: ten plik nagłówkowy C zawiera wszystkie definicje i struktury danych specyficzne dla narzędzia deweloperskiego.</span><span class="sxs-lookup"><span data-stu-id="aacc9-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
- <span data-ttu-id="aacc9-130">***UX. lib***: jest to wersja binarna biblioteki USBX C.</span><span class="sxs-lookup"><span data-stu-id="aacc9-130">***ux.lib***: This is the binary version of the USBX C library.</span></span> <span data-ttu-id="aacc9-131">Jest dystrybuowana z pakietem standardowym.</span><span class="sxs-lookup"><span data-stu-id="aacc9-131">It is distributed with the standard package.</span></span>
- <span data-ttu-id="aacc9-132">***demo_usbx. c***: plik c zawierający prostą wersję DEMONSTRACYJNą USBx</span><span class="sxs-lookup"><span data-stu-id="aacc9-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="aacc9-133">Wszystkie nazwy plików są małymi literami.</span><span class="sxs-lookup"><span data-stu-id="aacc9-133">All filenames are in lower-case.</span></span> <span data-ttu-id="aacc9-134">Ta konwencja nazewnictwa ułatwia konwertowanie poleceń na platformę deweloperskią systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="aacc9-135">Instalacja USBX</span><span class="sxs-lookup"><span data-stu-id="aacc9-135">USBX Installation</span></span>

<span data-ttu-id="aacc9-136">USBX jest instalowany przez klonowanie repozytorium GitHub na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="aacc9-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="aacc9-137">Poniżej przedstawiono typową składnię tworzenia klonu repozytorium USBX na komputerze:</span><span class="sxs-lookup"><span data-stu-id="aacc9-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```powershell
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="aacc9-138">Alternatywnie możesz pobrać kopię repozytorium za pomocą przycisku Pobierz na stronie głównej usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="aacc9-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="aacc9-139">Znajdziesz również instrukcje dotyczące tworzenia biblioteki USBX na stronie frontonu repozytorium online.</span><span class="sxs-lookup"><span data-stu-id="aacc9-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="aacc9-140">Poniższe instrukcje ogólne dotyczą niemal każdej instalacji:</span><span class="sxs-lookup"><span data-stu-id="aacc9-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="aacc9-141">Użyj tego samego katalogu, w którym wcześniej zainstalowano ThreadX na dysku twardym hosta.</span><span class="sxs-lookup"><span data-stu-id="aacc9-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="aacc9-142">Wszystkie nazwy USBX są unikatowe i nie zakłócają instalacji poprzedniej USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
2. <span data-ttu-id="aacc9-143">Dodaj wywołanie do \***ux_system_initialize** _ lub blisko początku _ *_tx_application_define_.* \* Jest to miejsce, w którym zainicjowano zasoby USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _ *_tx_application_define_.** This is where the USBX resources are initialized.</span></span>
3. <span data-ttu-id="aacc9-144">Dodaj wywołanie do \*\**ux_host_stack_initialize *.**</span><span class="sxs-lookup"><span data-stu-id="aacc9-144">Add a call to \***ux_host_stack_initialize\*.**</span></span>
4. <span data-ttu-id="aacc9-145">Dodaj co najmniej jedno wywołanie, aby zainicjować wymagane USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-145">Add one or more calls to initialize the required USBX.</span></span>
5. <span data-ttu-id="aacc9-146">Dodaj co najmniej jedno wywołanie w celu zainicjowania kontrolerów hosta dostępnych w systemie.</span><span class="sxs-lookup"><span data-stu-id="aacc9-146">Add one or more calls to initialize the host controllers available in the system.</span></span>
6. <span data-ttu-id="aacc9-147">Może być konieczne zmodyfikowanie pliku tx_low_level_initialize. c, aby dodać inicjalizację sprzętu niskiego poziomu i Routing wektora przerwania.</span><span class="sxs-lookup"><span data-stu-id="aacc9-147">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="aacc9-148">Jest to specyficzne dla platformy sprzętowej i nie zostanie omówiona w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="aacc9-148">This is specific to the hardware platform and will not be discussed here.</span></span>
7. <span data-ttu-id="aacc9-149">Kompiluj kod źródłowy aplikacji i linki z bibliotekami czasu wykonywania USBX i ThreadX (FileX i/lub NetX mogą być również wymagane, jeśli Klasa magazynu USB i/lub klasy sieci USB mają być kompilowane), UX. a (lub UX. lib) i TX. a (lub TX. lib).</span><span class="sxs-lookup"><span data-stu-id="aacc9-149">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="aacc9-150">Wyniki można pobrać do elementu docelowego i wykonać.</span><span class="sxs-lookup"><span data-stu-id="aacc9-150">The resulting can be downloaded to the target and executed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="aacc9-151">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="aacc9-151">Configuration Options</span></span>

<span data-ttu-id="aacc9-152">Istnieje kilka opcji konfiguracji do kompilowania biblioteki USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-152">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="aacc9-153">Wszystkie opcje znajdują się w ***ux_user. h***.</span><span class="sxs-lookup"><span data-stu-id="aacc9-153">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="aacc9-154">Poniższa lista zawiera szczegóły każdej opcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="aacc9-154">The list below details each configuration option.</span></span>


- <span data-ttu-id="aacc9-155">**UX_PERIODIC_RATE**: Ta wartość reprezentuje liczbę taktów na sekundę dla określonej platformy sprzętowej.</span><span class="sxs-lookup"><span data-stu-id="aacc9-155">**UX_PERIODIC_RATE**: This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="aacc9-156">Wartość domyślna to 1000 wskazujący jeden takt na milisekund.</span><span class="sxs-lookup"><span data-stu-id="aacc9-156">The default is 1000 indicating one tick per millisecond.</span></span>
- <span data-ttu-id="aacc9-157">**UX_MAX_CLASS_DRIVER**: Ta wartość to maksymalna liczba klas, które mogą być ładowane przez USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-157">**UX_MAX_CLASS_DRIVER**: This value is the maximum number of classes that can be loaded by USBX.</span></span> <span data-ttu-id="aacc9-158">Ta wartość reprezentuje kontener klasy, a nie liczbę wystąpień klasy.</span><span class="sxs-lookup"><span data-stu-id="aacc9-158">This value represents the class container and not the number of instances of a class.</span></span> <span data-ttu-id="aacc9-159">Na przykład jeśli określona implementacja USBX wymaga klasy centrów, klasy drukarki i klasy magazynu, wartość UX_MAX_CLASS_DRIVER można ustawić na 3 niezależnie od liczby urządzeń należących do tych klas.</span><span class="sxs-lookup"><span data-stu-id="aacc9-159">For instance, if a particular implementation of USBX needs the hub class, the printer class, and the storage class, then the UX_MAX_CLASS_DRIVER value can be set to 3 regardless of the number of devices that belong to these classes.</span></span>
- <span data-ttu-id="aacc9-160">**UX_MAX_HCD**: Ta wartość reprezentuje liczbę różnych kontrolerów hosta dostępnych w systemie.</span><span class="sxs-lookup"><span data-stu-id="aacc9-160">**UX_MAX_HCD**: This value represents the number of different host controllers that are available in the system.</span></span> <span data-ttu-id="aacc9-161">W przypadku obsługi USB 1,1 Ta wartość będzie w większości równa 1.</span><span class="sxs-lookup"><span data-stu-id="aacc9-161">For USB 1.1 support, this value will mostly be 1.</span></span> <span data-ttu-id="aacc9-162">Dla magistrali USB 2,0 ta wartość może być większa niż 1.</span><span class="sxs-lookup"><span data-stu-id="aacc9-162">For USB 2.0 support this value can be more than 1.</span></span> <span data-ttu-id="aacc9-163">Ta wartość reprezentuje liczbę współbieżnych kontrolerów hosta uruchomionych w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="aacc9-163">This value represents the number of concurrent host controllers running at the same time.</span></span> <span data-ttu-id="aacc9-164">Jeśli na przykład istnieją dwa wystąpienia z OHCI lub jeden EHCI i jeden kontroler OHCI z systemem, wartość UX_MAX_HCD powinna być ustawiona na 2.</span><span class="sxs-lookup"><span data-stu-id="aacc9-164">If for instance, there are two instances of OHCI running or one EHCI and one OHCI controllers running, the UX_MAX_HCD should be set to 2.</span></span> 
- <span data-ttu-id="aacc9-165">**UX_MAX_DEVICES**: Ta wartość reprezentuje maksymalną liczbę urządzeń, które mogą być dołączone do portu USB.</span><span class="sxs-lookup"><span data-stu-id="aacc9-165">**UX_MAX_DEVICES**: This value represents the maximum number of devices that can be attached to the USB.</span></span> <span data-ttu-id="aacc9-166">Zwykle teoretyczna maksymalna liczba na jednym urządzeniu USB to 127.</span><span class="sxs-lookup"><span data-stu-id="aacc9-166">Normally, the theoretical maximum number on a single USB is 127 devices.</span></span> <span data-ttu-id="aacc9-167">Ta wartość może być skalowana w dół w celu zaoszczędność pamięci.</span><span class="sxs-lookup"><span data-stu-id="aacc9-167">This value can be scaled down to conserve memory.</span></span> <span data-ttu-id="aacc9-168">Należy zauważyć, że ta wartość reprezentuje całkowitą liczbę urządzeń bez względu na liczbę magistrali USB w systemie.</span><span class="sxs-lookup"><span data-stu-id="aacc9-168">It should be noted that this value represents the total number of devices regardless of the number of USB buses in the system.</span></span>
- <span data-ttu-id="aacc9-169">**UX_MAX_ED**: Ta wartość reprezentuje maksymalną liczbę raportów EDS w puli kontrolerów.</span><span class="sxs-lookup"><span data-stu-id="aacc9-169">**UX_MAX_ED**: This value represents the maximum number of EDs in the controller pool.</span></span> <span data-ttu-id="aacc9-170">Ta liczba jest przypisana tylko do jednego kontrolera.</span><span class="sxs-lookup"><span data-stu-id="aacc9-170">This number is assigned to one controller only.</span></span> <span data-ttu-id="aacc9-171">Jeśli istnieją wiele wystąpień kontrolerów, ta wartość jest używana przez poszczególne kontrolery.</span><span class="sxs-lookup"><span data-stu-id="aacc9-171">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="aacc9-172">**UX_MAX_TD i UX_MAX_ISO_TD**: Ta wartość reprezentuje maksymalną liczbę Isochronous TDS w puli kontrolerów.</span><span class="sxs-lookup"><span data-stu-id="aacc9-172">**UX_MAX_TD and UX_MAX_ISO_TD**: This value represents the maximum number of regular and isochronous TDs in the controller pool.</span></span> <span data-ttu-id="aacc9-173">Ta liczba jest przypisana tylko do jednego kontrolera.</span><span class="sxs-lookup"><span data-stu-id="aacc9-173">This number is assigned to one controller only.</span></span> <span data-ttu-id="aacc9-174">Jeśli istnieją wiele wystąpień kontrolerów, ta wartość jest używana przez poszczególne kontrolery.</span><span class="sxs-lookup"><span data-stu-id="aacc9-174">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="aacc9-175">**UX_THREAD_STACK_SIZE**: wartość jest rozmiar stosu w bajtach dla wątków USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-175">**UX_THREAD_STACK_SIZE**: This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="aacc9-176">Może to być zwykle 1024 bajtów lub 2048 bajtów w zależności od używanego procesora i kontrolera hosta.</span><span class="sxs-lookup"><span data-stu-id="aacc9-176">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span>
- <span data-ttu-id="aacc9-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: wartość to rozmiar stosu dla wątku WYLICZENIA hosta USB.</span><span class="sxs-lookup"><span data-stu-id="aacc9-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: This value is the stack size of the USB host enumeration thread.</span></span> <span data-ttu-id="aacc9-178">Jeśli ten symbol nie jest ustawiony, rozmiar stosu dla wątku wyliczenia hosta USBX jest ustawiony na **UX_THREAD_STACK_SIZE**.</span><span class="sxs-lookup"><span data-stu-id="aacc9-178">If this symbol I not set, the USBX host enumeration thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span> 
- <span data-ttu-id="aacc9-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: wartość to rozmiar stosu wątku HCD hosta USB.</span><span class="sxs-lookup"><span data-stu-id="aacc9-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: This value is the stack size of the USB host HCD thread.</span></span> <span data-ttu-id="aacc9-180">Jeśli ten symbol nie jest ustawiony, rozmiar stosu wątku HCD hosta USBX jest ustawiony na **UX_THREAD_STACK_SIZE**.</span><span class="sxs-lookup"><span data-stu-id="aacc9-180">If this symbol I not set, the USBX host HCD thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span>
- <span data-ttu-id="aacc9-181">**UX_THREAD_PRIORITY_ENUM**: jest to wartość priorytetu ThreadX dla wątków wyliczenia USBX, które monitorują topologię magistrali.</span><span class="sxs-lookup"><span data-stu-id="aacc9-181">**UX_THREAD_PRIORITY_ENUM**: This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span>
- <span data-ttu-id="aacc9-182">**UX_THREAD_PRIORITY_CLASS**: jest to wartość priorytetu ThreadX dla standardowych wątków USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-182">**UX_THREAD_PRIORITY_CLASS**: This is the ThreadX priority value for the standard USBX threads.</span></span>
- <span data-ttu-id="aacc9-183">**UX_THREAD_PRIORITY_KEYBOARD**: jest to wartość priorytetu ThreadX dla klasy klawiatury HID USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-183">**UX_THREAD_PRIORITY_KEYBOARD**: This is the ThreadX priority value for the USBX HID keyboard class.</span></span>
- <span data-ttu-id="aacc9-184">**UX_THREAD_PRIORITY_HCD**: jest to wartość priorytetu ThreadX dla wątku kontrolera hosta.</span><span class="sxs-lookup"><span data-stu-id="aacc9-184">**UX_THREAD_PRIORITY_HCD**: This is the ThreadX priority value for the host controller thread.</span></span>
- <span data-ttu-id="aacc9-185">**UX_NO_TIME_SLICE**: Ta wartość w rzeczywistości definiuje wycinek czasu, który będzie używany dla wątków.</span><span class="sxs-lookup"><span data-stu-id="aacc9-185">**UX_NO_TIME_SLICE**: This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="aacc9-186">Na przykład, jeśli określono wartość 0, port docelowy ThreadX nie korzysta z wycinków czasu.</span><span class="sxs-lookup"><span data-stu-id="aacc9-186">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span>
- <span data-ttu-id="aacc9-187">**UX_MAX_HOST_LUN**: Ta wartość reprezentuje maksymalną liczbę jednostek logicznych SCSI przedstawionych w sterowniku klasy magazynu hosta.</span><span class="sxs-lookup"><span data-stu-id="aacc9-187">**UX_MAX_HOST_LUN**: This value represents the maximum number of SCSI logical units represented in the host storage class driver.</span></span>
- <span data-ttu-id="aacc9-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: Jeśli jest zdefiniowany, ta wartość obejmuje kod obsługujący urządzenia magazynujące korzystające z protokołu CB lub CBI (na przykład dyskietek).</span><span class="sxs-lookup"><span data-stu-id="aacc9-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: If defined, this value includes code to handle storage devices that use the CB or CBI protocol (such as floppy disks).</span></span> <span data-ttu-id="aacc9-189">Jest ona domyślnie wyłączona, ponieważ te protokoły są przestarzałe i zastępowane przez transport tylko zbiorczy (protokół BOT, który praktycznie wszystkie nowoczesne urządzenia magazynujące używają.</span><span class="sxs-lookup"><span data-stu-id="aacc9-189">It is off by default because these protocols are obsolete, being superseded by the Bulk Only Transport (BOT protocol, which virtually all modern storage devices use.</span></span>
- <span data-ttu-id="aacc9-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: Jeśli jest zdefiniowana, ta wartość powoduje, że ux_host_class_hid_keyboard_key_get tylko do raportowania zmian kluczy, które są, naciśnięcia kluczy i wydań klawiszy.</span><span class="sxs-lookup"><span data-stu-id="aacc9-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: If defined, this value causes ux_host_class_hid_keyboard_key_get to only report key changes that is, key presses and key releases.</span></span> <span data-ttu-id="aacc9-191">Domyślnie jest on raportowany tylko wtedy, gdy klucz nie działa.</span><span class="sxs-lookup"><span data-stu-id="aacc9-191">By default, it only reports when a key is down.</span></span>
- <span data-ttu-id="aacc9-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: używany tylko wtedy, gdy **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="aacc9-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="aacc9-193">Jeśli jest zdefiniowany, powoduje, że ux_host_class_hid_keyboard_key_get tylko do zmian naciśniętego klucza raportu lub w dół. wydane klucze/zmiany nie są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="aacc9-193">If defined, causes ux_host_class_hid_keyboard_key_get to only report key pressed/down changes; key released/up changes are not reported.</span></span>
- <span data-ttu-id="aacc9-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: używany tylko wtedy, gdy **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="aacc9-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="aacc9-195">Jeśli jest zdefiniowany, powoduje, że ux_host_class_hid_keyboard_key_get do raportu zmiany klucza blokady (CapsLock/NumLock/ScrollLock).</span><span class="sxs-lookup"><span data-stu-id="aacc9-195">If defined, causes ux_host_class_hid_keyboard_key_get to report lock key (CapsLock/NumLock/ScrollLock) changes.</span></span>
- <span data-ttu-id="aacc9-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: używany tylko wtedy, gdy **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="aacc9-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="aacc9-197">Jeśli jest zdefiniowany, powoduje, że zmiany w ux_host_class_hid_keyboard_key_get na klucz modyfikujący raport (Ctrl/Alt/Shift/GUI).</span><span class="sxs-lookup"><span data-stu-id="aacc9-197">If defined, causes ux_host_class_hid_keyboard_key_get to report modifier key (Ctrl/Alt/Shift/GUI) changes.</span></span>
- <span data-ttu-id="aacc9-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: Jeśli jest zdefiniowana, ta wartość reprezentuje liczbę pakietów w klasie hosta przechwytywania zmian-ECM.</span><span class="sxs-lookup"><span data-stu-id="aacc9-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: If defined, this value represents the number of packets in the CDC-ECM host class.</span></span> <span data-ttu-id="aacc9-199">Wartość domyślna to 16.</span><span class="sxs-lookup"><span data-stu-id="aacc9-199">The default is 16.</span></span>

## <a name="source-code-tree"></a><span data-ttu-id="aacc9-200">Drzewo kodu źródłowego</span><span class="sxs-lookup"><span data-stu-id="aacc9-200">Source Code Tree</span></span>

<span data-ttu-id="aacc9-201">Pliki USBX są dostępne w kilku katalogach.</span><span class="sxs-lookup"><span data-stu-id="aacc9-201">The USBX files are provided in several directories.</span></span>

![Drzewo kodu źródłowego](media/usbx-host-stack/source-code-tree.png)

<span data-ttu-id="aacc9-203">Aby pliki były rozpoznawane według ich nazw, przyjęto następującą konwencję:</span><span class="sxs-lookup"><span data-stu-id="aacc9-203">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="aacc9-204">Nazwa sufiksu pliku</span><span class="sxs-lookup"><span data-stu-id="aacc9-204">File Suffix Name</span></span> | <span data-ttu-id="aacc9-205">Opis pliku</span><span class="sxs-lookup"><span data-stu-id="aacc9-205">File description</span></span>                          |
| ---------------- | ----------------------------------------- |
| <span data-ttu-id="aacc9-206">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="aacc9-206">ux_host_stack</span></span>    | <span data-ttu-id="aacc9-207">podstawowe pliki stosu hosta USBx</span><span class="sxs-lookup"><span data-stu-id="aacc9-207">usbx host stack core files</span></span>                |
| <span data-ttu-id="aacc9-208">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="aacc9-208">ux_host_class</span></span>    | <span data-ttu-id="aacc9-209">pliki klas stosu hosta USBx</span><span class="sxs-lookup"><span data-stu-id="aacc9-209">usbx host stack classes files</span></span>             |
| <span data-ttu-id="aacc9-210">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="aacc9-210">ux_hcd</span></span>           | <span data-ttu-id="aacc9-211">pliki sterowników kontrolera stosu hosta USBx</span><span class="sxs-lookup"><span data-stu-id="aacc9-211">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="aacc9-212">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="aacc9-212">ux_device_stack</span></span>  | <span data-ttu-id="aacc9-213">podstawowe pliki stosu urządzeń USBx</span><span class="sxs-lookup"><span data-stu-id="aacc9-213">usbx device stack core files</span></span>              |
| <span data-ttu-id="aacc9-214">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="aacc9-214">ux_device_class</span></span>  | <span data-ttu-id="aacc9-215">pliki klas stosu urządzeń USBx</span><span class="sxs-lookup"><span data-stu-id="aacc9-215">usbx device stack classes files</span></span>           |
| <span data-ttu-id="aacc9-216">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="aacc9-216">ux_dcd</span></span>           | <span data-ttu-id="aacc9-217">pliki sterowników kontrolera stosu urządzeń USBx</span><span class="sxs-lookup"><span data-stu-id="aacc9-217">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="aacc9-218">ux_otg</span><span class="sxs-lookup"><span data-stu-id="aacc9-218">ux_otg</span></span>           | <span data-ttu-id="aacc9-219">pliki powiązane z sterownikiem kontrolera OTG USBx</span><span class="sxs-lookup"><span data-stu-id="aacc9-219">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="aacc9-220">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="aacc9-220">ux_pictbridge</span></span>    | <span data-ttu-id="aacc9-221">Pliki USBx PictBridge</span><span class="sxs-lookup"><span data-stu-id="aacc9-221">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="aacc9-222">ux_utility</span><span class="sxs-lookup"><span data-stu-id="aacc9-222">ux_utility</span></span>       | <span data-ttu-id="aacc9-223">funkcje narzędzia USBx</span><span class="sxs-lookup"><span data-stu-id="aacc9-223">usbx utility functions</span></span>                    |
| <span data-ttu-id="aacc9-224">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="aacc9-224">demo_usbx</span></span>        | <span data-ttu-id="aacc9-225">pliki demonstracyjne dla USBX</span><span class="sxs-lookup"><span data-stu-id="aacc9-225">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="aacc9-226">Inicjowanie zasobów USBX</span><span class="sxs-lookup"><span data-stu-id="aacc9-226">Initialization of USBX resources</span></span>

<span data-ttu-id="aacc9-227">USBX ma własny Menedżer pamięci.</span><span class="sxs-lookup"><span data-stu-id="aacc9-227">USBX has its own memory manager.</span></span> <span data-ttu-id="aacc9-228">Pamięć należy przydzielyć do USBX przed zainicjowaniem hosta lub po stronie urządzenia USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-228">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="aacc9-229">Menedżer pamięci USBX może obsługiwać systemy, w których pamięć może być buforowana.</span><span class="sxs-lookup"><span data-stu-id="aacc9-229">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="aacc9-230">Poniższa funkcja inicjuje zasoby pamięci USBX z 128Kem zwykłej pamięci i nie ma oddzielnej puli pamięci podręcznej w bezpiecznym miejscu:</span><span class="sxs-lookup"><span data-stu-id="aacc9-230">The following function initializes USBX memory resources with 128K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="aacc9-231">Prototyp ux_system_initialize jest następujący.</span><span class="sxs-lookup"><span data-stu-id="aacc9-231">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a><span data-ttu-id="aacc9-232">Parametry wejściowe:</span><span class="sxs-lookup"><span data-stu-id="aacc9-232">Input parameters:</span></span>

- <span data-ttu-id="aacc9-233">**regular_memory_pool_start** Początek zwykłej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="aacc9-233">**regular_memory_pool_start** Beginning of the regular memory pool.</span></span>
- <span data-ttu-id="aacc9-234">**regular_memory_size** Rozmiar zwykłej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="aacc9-234">**regular_memory_size** Size of the regular memory pool.</span></span>
- <span data-ttu-id="aacc9-235">**cache_safe_memory_pool_start** Początek bezpiecznego buforowania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="aacc9-235">**cache_safe_memory_pool_start** Beginning of the cache safe memory pool.</span></span>
- <span data-ttu-id="aacc9-236">**cache_safe_memory_size** Rozmiar bezpiecznej puli pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="aacc9-236">**cache_safe_memory_size** Size of the cache safe memory pool.</span></span>    |

<span data-ttu-id="aacc9-237">Nie wszystkie systemy wymagają definicji bezpiecznej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="aacc9-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="aacc9-238">W takim systemie wartości przesyłane podczas inicjalizacji wskaźnika pamięci będą ustawione na UX_NULL i rozmiar puli do 0.</span><span class="sxs-lookup"><span data-stu-id="aacc9-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="aacc9-239">Następnie USBX będzie używać zwykłej puli pamięci w miejsce pamięci podręcznej w bezpiecznej puli.</span><span class="sxs-lookup"><span data-stu-id="aacc9-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="aacc9-240">W systemie, w którym zwykła pamięć nie jest bezpieczna w pamięci podręcznej, a kontroler wymaga przeprowadzenia pamięci DMA (podobnie jak w przypadku OHCI, kontrolerów EHCI między innymi), konieczne jest zdefiniowanie puli pamięci w bezpiecznym obszarze pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="aacc9-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory (like OHCI, EHCI controllers amongst others) it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="aacc9-241">Odinicjowanie zasobów USBX</span><span class="sxs-lookup"><span data-stu-id="aacc9-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="aacc9-242">USBX można przerwać, zwalniając jego zasoby.</span><span class="sxs-lookup"><span data-stu-id="aacc9-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="aacc9-243">Przed zakończeniem USBx należy prawidłowo zakończyć wszystkie klasy i zasoby kontrolerów.</span><span class="sxs-lookup"><span data-stu-id="aacc9-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="aacc9-244">Następująca funkcja nie inicjuje USBX zasobów pamięci:</span><span class="sxs-lookup"><span data-stu-id="aacc9-244">The following function uninitializes USBX memory resources :</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="aacc9-245">Prototyp ux_system_initialize jest następujący.</span><span class="sxs-lookup"><span data-stu-id="aacc9-245">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a><span data-ttu-id="aacc9-246">Definicja kontrolerów hosta USB</span><span class="sxs-lookup"><span data-stu-id="aacc9-246">Definition of USB Host Controllers</span></span>

<span data-ttu-id="aacc9-247">Należy zdefiniować co najmniej jeden kontroler hosta USB dla USBX do działania w trybie hosta.</span><span class="sxs-lookup"><span data-stu-id="aacc9-247">It is required to define at least one USB host controller for USBX to operate in host mode.</span></span> <span data-ttu-id="aacc9-248">Plik inicjujący aplikacji powinien zawierać tę definicję.</span><span class="sxs-lookup"><span data-stu-id="aacc9-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="aacc9-249">W poniższym wierszu jest wykonywana definicja ogólnego kontrolera hosta.</span><span class="sxs-lookup"><span data-stu-id="aacc9-249">The following line performs the definition of a generic host controller.</span></span>

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

<span data-ttu-id="aacc9-250">Ux_host_stack_hcd_register ma następujący prototyp.</span><span class="sxs-lookup"><span data-stu-id="aacc9-250">The ux_host_stack_hcd_register has the following prototype.</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

<span data-ttu-id="aacc9-251">Funkcja ux_host_stack_hcd_register ma następujące parametry.</span><span class="sxs-lookup"><span data-stu-id="aacc9-251">The ux_host_stack_hcd_register function has the following parameters.</span></span>

- <span data-ttu-id="aacc9-252">**hcd_name**: ciąg nazwy kontrolera</span><span class="sxs-lookup"><span data-stu-id="aacc9-252">**hcd_name**: string of the controller name</span></span>
- <span data-ttu-id="aacc9-253">**hcd_initialize_function**: Funkcja inicjowania kontrolera</span><span class="sxs-lookup"><span data-stu-id="aacc9-253">**hcd_initialize_function**: initialization function of the controller</span></span>
- <span data-ttu-id="aacc9-254">**hcd_param1**: zazwyczaj wartość operacji we/wy lub pamięć używana przez kontroler</span><span class="sxs-lookup"><span data-stu-id="aacc9-254">**hcd_param1**: usually the IO value or Memory used by the controller</span></span>
- <span data-ttu-id="aacc9-255">**hcd_param2**: zwykle przerwanie używane przez kontroler</span><span class="sxs-lookup"><span data-stu-id="aacc9-255">**hcd_param2**: usually the IRQ used by the controller</span></span>

<span data-ttu-id="aacc9-256">W poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="aacc9-256">In our previous example:</span></span>

- <span data-ttu-id="aacc9-257">"ux_hcd_controller" jest nazwą kontrolera</span><span class="sxs-lookup"><span data-stu-id="aacc9-257">"ux_hcd_controller" is the name of the controller</span></span>
- <span data-ttu-id="aacc9-258">"ux_hcd_controller_initialize" to procedura inicjowania kontrolera hosta</span><span class="sxs-lookup"><span data-stu-id="aacc9-258">"ux_hcd_controller_initialize" is the initialization routine for the host controller</span></span>
- <span data-ttu-id="aacc9-259">0xd0000 to adres, pod którym rejestry kontrolera hosta są widoczne w pamięci</span><span class="sxs-lookup"><span data-stu-id="aacc9-259">0xd0000 is the address at which the host controller registers are visible in memory</span></span>
- <span data-ttu-id="aacc9-260">i 0x0A to PRZERWAnie używane przez kontroler hosta.</span><span class="sxs-lookup"><span data-stu-id="aacc9-260">and 0x0a is the IRQ used by the host controller.</span></span>

<span data-ttu-id="aacc9-261">Poniżej znajduje się przykład inicjalizacji USBX w trybie hosta z jednym kontrolerem hosta i kilkoma klasami.</span><span class="sxs-lookup"><span data-stu-id="aacc9-261">Following is an example of the initialization of USBX in host mode with one host controller and several classes.</span></span>

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a><span data-ttu-id="aacc9-262">Definicja klas hosta</span><span class="sxs-lookup"><span data-stu-id="aacc9-262">Definition of Host Classes</span></span>

<span data-ttu-id="aacc9-263">Należy zdefiniować co najmniej jedną klasę hosta z USBX.</span><span class="sxs-lookup"><span data-stu-id="aacc9-263">It is required to define one or more host classes with USBX.</span></span> <span data-ttu-id="aacc9-264">Klasa USB jest wymagana do podłączenia urządzenia USB po skonfigurowaniu urządzenia USB przez stos USB.</span><span class="sxs-lookup"><span data-stu-id="aacc9-264">A USB class is required to drive a USB device after the USB stack has configured the USB device.</span></span> <span data-ttu-id="aacc9-265">Klasa USB jest specyficzna dla urządzenia.</span><span class="sxs-lookup"><span data-stu-id="aacc9-265">A USB class is specific to the device.</span></span> <span data-ttu-id="aacc9-266">W zależności od liczby interfejsów zawartych w deskryptorach urządzeń USB może być wymagana co najmniej jedna Klasa.</span><span class="sxs-lookup"><span data-stu-id="aacc9-266">One or more classes may be required to drive a USB device depending on the number of interfaces contained in the USB device descriptors.</span></span>

<span data-ttu-id="aacc9-267">Jest to przykład rejestracji klasy centrum.</span><span class="sxs-lookup"><span data-stu-id="aacc9-267">This is an example of the registration of the HUB class.</span></span>

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

<span data-ttu-id="aacc9-268">Funkcja ux_host_class_register ma następujący prototyp.</span><span class="sxs-lookup"><span data-stu-id="aacc9-268">The function ux_host_class_register has the following prototype.</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- <span data-ttu-id="aacc9-269">**class_name** jest nazwą klasy</span><span class="sxs-lookup"><span data-stu-id="aacc9-269">**class_name** is the name of the class</span></span>
- <span data-ttu-id="aacc9-270">**class_entry_address** jest punktem wejścia klasy</span><span class="sxs-lookup"><span data-stu-id="aacc9-270">**class_entry_address** is the entry point of the class</span></span>

<span data-ttu-id="aacc9-271">Przykład inicjowania klasy centrum:</span><span class="sxs-lookup"><span data-stu-id="aacc9-271">In the example of the HUB class initialization:</span></span>

- <span data-ttu-id="aacc9-272">"ux_host_class_hub" jest nazwą klasy centrum</span><span class="sxs-lookup"><span data-stu-id="aacc9-272">"ux_host_class_hub" is the name of the hub class</span></span>
- <span data-ttu-id="aacc9-273">ux_host_class_hub_entry jest punktem wejścia klasy centrum.</span><span class="sxs-lookup"><span data-stu-id="aacc9-273">ux_host_class_hub_entry is the entry point of the HUB class.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="aacc9-274">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="aacc9-274">Troubleshooting</span></span>

<span data-ttu-id="aacc9-275">USBX jest dostarczany z plikiem demonstracyjnym i środowiskiem symulacji.</span><span class="sxs-lookup"><span data-stu-id="aacc9-275">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="aacc9-276">Zawsze dobrym pomysłem jest rozpoczęcie od pierwszego uruchomienia platformy demonstracyjnej — na sprzęcie docelowym lub na określonej platformie demonstracyjnej.</span><span class="sxs-lookup"><span data-stu-id="aacc9-276">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

<span data-ttu-id="aacc9-277">Jeśli system demonstracyjny nie działa, spróbuj wykonać następujące czynności, aby zawęzić problem.</span><span class="sxs-lookup"><span data-stu-id="aacc9-277">If the demonstration system does not work, try the following things to narrow the problem.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="aacc9-278">Identyfikator wersji USBX</span><span class="sxs-lookup"><span data-stu-id="aacc9-278">USBX Version ID</span></span>

<span data-ttu-id="aacc9-279">Bieżąca wersja programu USBX jest dostępna zarówno dla użytkownika, jak i oprogramowania aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="aacc9-279">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="aacc9-280">Programista może uzyskać wersję USBX z badania pliku \***ux_port. h** _.</span><span class="sxs-lookup"><span data-stu-id="aacc9-280">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="aacc9-281">Ponadto ten plik zawiera również historię wersji odpowiedniego portu.</span><span class="sxs-lookup"><span data-stu-id="aacc9-281">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="aacc9-282">Oprogramowanie aplikacji może uzyskać wersję USBX, badając ciąg globalny _ _ *_ux_version_id_* _, który jest zdefiniowany w _ *_ux_port. h_* \*.</span><span class="sxs-lookup"><span data-stu-id="aacc9-282">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
