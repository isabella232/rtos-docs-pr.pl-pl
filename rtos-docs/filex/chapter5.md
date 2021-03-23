---
title: Rozdział 5 — sterowniki we/wy dla usługi Azure RTO FileX
description: Ten rozdział zawiera opis sterowników we/wy dla usługi Azure RTO FileX i został zaprojektowany, aby pomóc deweloperom w pisaniu sterowników specyficznych dla aplikacji.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b44822b9d8f16208cf470a84013be5a5ff833325
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822441"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a><span data-ttu-id="668d5-103">Rozdział 5 — sterowniki we/wy dla usługi Azure RTO FileX</span><span class="sxs-lookup"><span data-stu-id="668d5-103">Chapter 5 - I/O Drivers for Azure RTOS FileX</span></span>

<span data-ttu-id="668d5-104">Ten rozdział zawiera opis sterowników we/wy dla usługi Azure RTO FileX i został zaprojektowany, aby pomóc deweloperom w pisaniu sterowników specyficznych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="668d5-104">This chapter contains a description of I/O drivers for Azure RTOS FileX and is designed to help developers write application-specific drivers.</span></span>

## <a name="io-driver-introduction"></a><span data-ttu-id="668d5-105">Wprowadzenie do sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="668d5-105">I/O Driver Introduction</span></span>

<span data-ttu-id="668d5-106">FileX obsługuje wiele urządzeń multimedialnych.</span><span class="sxs-lookup"><span data-stu-id="668d5-106">FileX supports multiple media devices.</span></span> <span data-ttu-id="668d5-107">Struktura FX_MEDIA definiuje wszystko wymagane do zarządzania urządzeniem multimedialnym.</span><span class="sxs-lookup"><span data-stu-id="668d5-107">The FX_MEDIA structure defines everything required to manage a media device.</span></span> <span data-ttu-id="668d5-108">Ta struktura zawiera wszystkie informacje o nośnikach, w tym sterownik we/wy charakterystyczny dla nośnika i powiązane parametry umożliwiające przekazywanie informacji i stanu między sterownikiem i FileX.</span><span class="sxs-lookup"><span data-stu-id="668d5-108">This structure contains all media information, including the media-specific I/O driver and associated parameters for passing information and status between the driver and FileX.</span></span> <span data-ttu-id="668d5-109">W większości systemów istnieje unikatowy sterownik we/wy dla każdego wystąpienia nośnika FileX.</span><span class="sxs-lookup"><span data-stu-id="668d5-109">In most systems, there is a unique I/O driver for each FileX media instance.</span></span>

## <a name="io-driver-entry"></a><span data-ttu-id="668d5-110">Wpis sterownika we/wy</span><span class="sxs-lookup"><span data-stu-id="668d5-110">I/O Driver Entry</span></span>

<span data-ttu-id="668d5-111">Każdy sterownik we/wy FileX ma funkcję pojedynczego wpisu, która jest definiowana przez wywołanie usługi ***fx_media_open*** .</span><span class="sxs-lookup"><span data-stu-id="668d5-111">Each FileX I/O driver has a single entry function that is defined by the ***fx_media_open*** service call.</span></span> <span data-ttu-id="668d5-112">Funkcja wprowadzania sterowników ma następujący format:</span><span class="sxs-lookup"><span data-stu-id="668d5-112">The driver entry function has the following format:</span></span>

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

<span data-ttu-id="668d5-113">FileX wywołuje funkcję wejścia sterownika we/wy, aby zażądać dostępu do nośników fizycznych, w tym wczytywania i odczytywania sektora rozruchowego.</span><span class="sxs-lookup"><span data-stu-id="668d5-113">FileX calls the I/O driver entry function to request all physical media access, including initialization and boot sector reading.</span></span> <span data-ttu-id="668d5-114">Żądania kierowane do sterownika są wykonywane sekwencyjnie; oznacza to, że FileX czeka na zakończenie bieżącego żądania przed wysłaniem innego żądania.</span><span class="sxs-lookup"><span data-stu-id="668d5-114">Requests made to the driver are done sequentially; i.e., FileX waits for the current request to complete before another request is sent.</span></span>

## <a name="io-driver-requests"></a><span data-ttu-id="668d5-115">Żądania sterowników we/wy</span><span class="sxs-lookup"><span data-stu-id="668d5-115">I/O Driver Requests</span></span>

<span data-ttu-id="668d5-116">Ze względu na to, że każdy sterownik we/wy ma jedną funkcję wejścia, FileX wykonuje określone żądania za pomocą bloku sterowania nośnika.</span><span class="sxs-lookup"><span data-stu-id="668d5-116">Because each I/O driver has a single entry function, FileX makes specific requests through the media control block.</span></span> <span data-ttu-id="668d5-117">W konkretnym przypadku  **fx_media_driver_request** członkiem **FX_MEDIA** jest używany do określenia dokładnego żądania sterownika.</span><span class="sxs-lookup"><span data-stu-id="668d5-117">Specifically, the  **fx_media_driver_request** member of **FX_MEDIA** is used to specify the exact driver request.</span></span> <span data-ttu-id="668d5-118">Sterownik we/wy komunikuje sukces lub niepowodzenie żądania przez **fx_media_driver_status** członkiem **FX_MEDIA**.</span><span class="sxs-lookup"><span data-stu-id="668d5-118">The I/O driver communicates the success or failure of the request through the **fx_media_driver_status** member of **FX_MEDIA**.</span></span> <span data-ttu-id="668d5-119">Jeśli żądanie sterownika zakończyło się pomyślnie, **FX_SUCCESS** jest umieszczane w tym polu przed zwróceniem sterownika.</span><span class="sxs-lookup"><span data-stu-id="668d5-119">If the driver request was successful, **FX_SUCCESS** is placed in this field before the driver returns.</span></span> <span data-ttu-id="668d5-120">W przeciwnym razie, jeśli zostanie wykryty błąd, FX_IO_ERROR jest umieszczany w tym polu.</span><span class="sxs-lookup"><span data-stu-id="668d5-120">Otherwise, if an error is detected, FX_IO_ERROR is placed in this field.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="668d5-121">Inicjowanie sterownika</span><span class="sxs-lookup"><span data-stu-id="668d5-121">Driver Initialization</span></span>

<span data-ttu-id="668d5-122">Chociaż rzeczywiste przetwarzanie inicjacji sterownika jest specyficzne dla aplikacji, zwykle składa się ona z inicjalizacji struktury danych i ewentualnej wstępnej inicjalizacji sprzętowej.</span><span class="sxs-lookup"><span data-stu-id="668d5-122">Although the actual driver initialization processing is application specific, it usually consists of data structure initialization and possibly some preliminary hardware initialization.</span></span> <span data-ttu-id="668d5-123">To żądanie jest najpierw wykonywane przez FileX i jest wykonywane z poziomu usługi fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="668d5-123">This request is the first made by FileX and is done from within the fx_media_open service.</span></span>

<span data-ttu-id="668d5-124">Jeśli zostanie wykryta ochrona przed zapisem na nośniku, fx_media_driver_write_protect członkiem FX_MEDIA powinna być ustawiona wartość FX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="668d5-124">If media write protection is detected, the driver fx_media_driver_write_protect member of FX_MEDIA should be set to FX_TRUE.</span></span>

<span data-ttu-id="668d5-125">Następujące elementy członkowskie FX_MEDIA są używane dla żądania inicjacji sterownika we/wy:</span><span class="sxs-lookup"><span data-stu-id="668d5-125">The following FX_MEDIA members are used for the I/O driver initialization request:</span></span>

|<span data-ttu-id="668d5-126">FX_MEDIA składową</span><span class="sxs-lookup"><span data-stu-id="668d5-126">FX_MEDIA member</span></span>|<span data-ttu-id="668d5-127">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="668d5-127">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="668d5-128">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="668d5-128">fx_media_driver_request</span></span>|<span data-ttu-id="668d5-129">FX_DRIVER_INIT</span><span class="sxs-lookup"><span data-stu-id="668d5-129">FX_DRIVER_INIT</span></span>|

<span data-ttu-id="668d5-130">FileX zapewnia mechanizm do informowania sterownika aplikacji, gdy sektory nie są już używane.</span><span class="sxs-lookup"><span data-stu-id="668d5-130">FileX provides a mechanism to inform the application driver when sectors are no longer being used.</span></span> <span data-ttu-id="668d5-131">Jest to szczególnie przydatne w przypadku menedżerów pamięci FLASH, którzy muszą zarządzać wszystkimi używanymi sektorami logicznymi, które są mapowane na LAMPę BŁYSKową.</span><span class="sxs-lookup"><span data-stu-id="668d5-131">This is especially useful for FLASH memory managers that must manage all in-use logical sectors mapped to the FLASH.</span></span>

<span data-ttu-id="668d5-132">Jeśli wymagane jest powiadomienie o bezpłatnych sektorach, sterownik aplikacji po prostu ustawi pole *fx_media_driver_free_sector_update* w skojarzonej strukturze **FX_MEDIA** do **FX_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="668d5-132">If such notification of free sectors is required, the application driver simply sets the *fx_media_driver_free_sector_update* field in the associated **FX_MEDIA** structure to **FX_TRUE**.</span></span> <span data-ttu-id="668d5-133">Po ustawieniu FileX **_FX_DRIVER_RELEASE_SECTORS_** wywołanie sterownika we/wy wskazujące, kiedy jeden lub więcej kolejnych sektorów staje się bezpłatny.</span><span class="sxs-lookup"><span data-stu-id="668d5-133">After set, FileX makes a **_FX_DRIVER_RELEASE_SECTORS_** I/O driver call indicating when one or more consecutive sectors becomes free.</span></span>

### <a name="boot-sector-read"></a><span data-ttu-id="668d5-134">Odczyt sektora rozruchowego</span><span class="sxs-lookup"><span data-stu-id="668d5-134">Boot Sector Read</span></span>

<span data-ttu-id="668d5-135">Zamiast używać standardowego żądania odczytu, FileX wykonuje konkretne żądanie odczytu sektora rozruchowego nośnika.</span><span class="sxs-lookup"><span data-stu-id="668d5-135">Instead of using a standard read request, FileX makes a specific request to read the media's boot sector.</span></span> <span data-ttu-id="668d5-136">Następujące **FX_MEDIA** elementy członkowskie są używane dla żądania odczytu sektora rozruchu sterownika we/wy:</span><span class="sxs-lookup"><span data-stu-id="668d5-136">The following **FX_MEDIA** members are used for the I/O driver boot sector read request:</span></span>

|<span data-ttu-id="668d5-137">FX_MEDIA składową</span><span class="sxs-lookup"><span data-stu-id="668d5-137">FX_MEDIA member</span></span>|<span data-ttu-id="668d5-138">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="668d5-138">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="668d5-139">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="668d5-139">fx_media_driver_request</span></span>| <span data-ttu-id="668d5-140">FX_DRIVER_BOOT_READ</span><span class="sxs-lookup"><span data-stu-id="668d5-140">FX_DRIVER_BOOT_READ</span></span>|
|<span data-ttu-id="668d5-141">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="668d5-141">fx_media_driver_buffer</span></span>| <span data-ttu-id="668d5-142">Adres docelowy sektora rozruchowego.</span><span class="sxs-lookup"><span data-stu-id="668d5-142">Address of destination for boot sector.</span></span>|

### <a name="boot-sector-write"></a><span data-ttu-id="668d5-143">Zapis sektora rozruchowego</span><span class="sxs-lookup"><span data-stu-id="668d5-143">Boot Sector Write</span></span>

<span data-ttu-id="668d5-144">Zamiast używać standardowego żądania zapisu, FileX wykonuje określone żądanie zapisania sektora rozruchowego nośnika.</span><span class="sxs-lookup"><span data-stu-id="668d5-144">Instead of using a standard write request, FileX makes a specific request to write the media's boot sector.</span></span> <span data-ttu-id="668d5-145">Następujące składowe **FX_MEDIA** są używane dla żądania zapisu sektora rozruchu sterownika we/wy:</span><span class="sxs-lookup"><span data-stu-id="668d5-145">The following **FX_MEDIA** members are used for the I/O driver boot sector write request:</span></span>

|<span data-ttu-id="668d5-146">FX_MEDIA składową</span><span class="sxs-lookup"><span data-stu-id="668d5-146">FX_MEDIA member</span></span>|<span data-ttu-id="668d5-147">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="668d5-147">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="668d5-148">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="668d5-148">fx_media_driver_request</span></span>| <span data-ttu-id="668d5-149">FX_DRIVER_BOOT_WRITE</span><span class="sxs-lookup"><span data-stu-id="668d5-149">FX_DRIVER_BOOT_WRITE</span></span>|
|<span data-ttu-id="668d5-150">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="668d5-150">fx_media_driver_buffer</span></span>| <span data-ttu-id="668d5-151">Adres źródła dla sektora rozruchowego.</span><span class="sxs-lookup"><span data-stu-id="668d5-151">Address of source for boot sector.</span></span>|

### <a name="sector-read"></a><span data-ttu-id="668d5-152">Odczyt sektora</span><span class="sxs-lookup"><span data-stu-id="668d5-152">Sector Read</span></span>

<span data-ttu-id="668d5-153">FileX odczytuje jeden lub więcej sektorów do pamięci, wydając żądanie odczytu do sterownika we/wy.</span><span class="sxs-lookup"><span data-stu-id="668d5-153">FileX reads one or more sectors into memory by issuing a read request to the I/O driver.</span></span> <span data-ttu-id="668d5-154">Następujące elementy członkowskie **FX_MEDIA** są używane dla żądania odczytu sterownika we/wy:</span><span class="sxs-lookup"><span data-stu-id="668d5-154">The following **FX_MEDIA** members are used for the I/O driver read request:</span></span>

|<span data-ttu-id="668d5-155">FX_MEDIA składową</span><span class="sxs-lookup"><span data-stu-id="668d5-155">FX_MEDIA member</span></span>|<span data-ttu-id="668d5-156">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="668d5-156">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="668d5-157">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="668d5-157">fx_media_driver_request</span></span>| <span data-ttu-id="668d5-158">FX_DRIVER_READ</span><span class="sxs-lookup"><span data-stu-id="668d5-158">FX_DRIVER_READ</span></span>|
|<span data-ttu-id="668d5-159">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="668d5-159">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="668d5-160">Sektor logiczny do odczytania</span><span class="sxs-lookup"><span data-stu-id="668d5-160">Logical sector to read</span></span>|
|<span data-ttu-id="668d5-161">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="668d5-161">fx_media_driver_sectors</span></span>|<span data-ttu-id="668d5-162">Liczba sektorów do odczytania</span><span class="sxs-lookup"><span data-stu-id="668d5-162">Number of sectors to read</span></span>|
|<span data-ttu-id="668d5-163">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="668d5-163">fx_media_driver_buffer</span></span>|<span data-ttu-id="668d5-164">Odczytaj bufor docelowy dla sektorów</span><span class="sxs-lookup"><span data-stu-id="668d5-164">Destination buffer for sector(s) read</span></span>|
|<span data-ttu-id="668d5-165">fx_media_driver_data_sector_read</span><span class="sxs-lookup"><span data-stu-id="668d5-165">fx_media_driver_data_sector_read</span></span>|<span data-ttu-id="668d5-166">Ustaw, aby FX_TRUE, jeśli zażądano sektora danych pliku.</span><span class="sxs-lookup"><span data-stu-id="668d5-166">Set to FX_TRUE if a file data sector is requested.</span></span> <span data-ttu-id="668d5-167">W przeciwnym razie FX_FALSE, jeśli zażądano sektora systemowego (FAT lub sektor katalogu).</span><span class="sxs-lookup"><span data-stu-id="668d5-167">Otherwise, FX_FALSE if a system sector (FAT or directory sector) is requested.</span></span>|
|<span data-ttu-id="668d5-168">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="668d5-168">fx_media_driver_sector_type</span></span>|<span data-ttu-id="668d5-169">Definiuje jawny typ żądanego sektora w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="668d5-169">Defines the explicit type of sector requested, as follows:</span></span><br /><span data-ttu-id="668d5-170">FX_FAT_SECTOR (2)</span><span class="sxs-lookup"><span data-stu-id="668d5-170">FX_FAT_SECTOR (2)</span></span><br /><span data-ttu-id="668d5-171">FX_DIRECTORY_SECTOR (3)</span><span class="sxs-lookup"><span data-stu-id="668d5-171">FX_DIRECTORY_SECTOR (3)</span></span><br /><span data-ttu-id="668d5-172">FX_DATA_SECTOR (4)</span><span class="sxs-lookup"><span data-stu-id="668d5-172">FX_DATA_SECTOR (4)</span></span>|

### <a name="sector-write"></a><span data-ttu-id="668d5-173">Zapis sektora</span><span class="sxs-lookup"><span data-stu-id="668d5-173">Sector Write</span></span>

<span data-ttu-id="668d5-174">FileX zapisuje jeden lub więcej sektorów na nośniku fizycznym, wysyłając żądanie zapisu do sterownika we/wy.</span><span class="sxs-lookup"><span data-stu-id="668d5-174">FileX writes one or more sectors to the physical media by issuing a write request to the I/O driver.</span></span> <span data-ttu-id="668d5-175">Następujące składowe FX_MEDIA są używane dla żądania zapisu sterowników we/wy:</span><span class="sxs-lookup"><span data-stu-id="668d5-175">The following FX_MEDIA members are used for the I/O driver write request:</span></span>

|<span data-ttu-id="668d5-176">FX_MEDIA składową</span><span class="sxs-lookup"><span data-stu-id="668d5-176">FX_MEDIA member</span></span>| <span data-ttu-id="668d5-177">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="668d5-177">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="668d5-178">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="668d5-178">fx_media_driver_request</span></span>|<span data-ttu-id="668d5-179">FX_DRIVER_WRITE</span><span class="sxs-lookup"><span data-stu-id="668d5-179">FX_DRIVER_WRITE</span></span>|
|<span data-ttu-id="668d5-180">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="668d5-180">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="668d5-181">Sektor logiczny do zapisu</span><span class="sxs-lookup"><span data-stu-id="668d5-181">Logical sector to write</span></span>|
|<span data-ttu-id="668d5-182">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="668d5-182">fx_media_driver_sectors</span></span>|<span data-ttu-id="668d5-183">Liczba sektorów do zapisu</span><span class="sxs-lookup"><span data-stu-id="668d5-183">Number of sectors to write</span></span>|
|<span data-ttu-id="668d5-184">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="668d5-184">fx_media_driver_buffer</span></span>|<span data-ttu-id="668d5-185">Bufor źródłowy dla sektorów do zapisu</span><span class="sxs-lookup"><span data-stu-id="668d5-185">Source buffer for sector(s) to write</span></span>|
|<span data-ttu-id="668d5-186">fx_media_driver_system_write</span><span class="sxs-lookup"><span data-stu-id="668d5-186">fx_media_driver_system_write</span></span>| <span data-ttu-id="668d5-187">Ustaw na FX_TRUE w przypadku żądania sektora systemu (FAT lub sektor katalogu).</span><span class="sxs-lookup"><span data-stu-id="668d5-187">Set to FX_TRUE if a system sector is requested (FAT or directory sector).</span></span> <span data-ttu-id="668d5-188">W przeciwnym razie FX_FALSE, jeśli zażądano sektora danych pliku.</span><span class="sxs-lookup"><span data-stu-id="668d5-188">Otherwise, FX_FALSE if a file data sector is requested.</span></span>|
|<span data-ttu-id="668d5-189">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="668d5-189">fx_media_driver_sector_type</span></span>|<span data-ttu-id="668d5-190">Definiuje jawny typ żądanego sektora w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="668d5-190">Defines the explicit type of sector requested, as follows:</span></span>
<span data-ttu-id="668d5-191">FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4) |</span><span class="sxs-lookup"><span data-stu-id="668d5-191">FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4)|</span></span>

### <a name="driver-flush"></a><span data-ttu-id="668d5-192">Opróżnianie sterownika</span><span class="sxs-lookup"><span data-stu-id="668d5-192">Driver Flush</span></span>

<span data-ttu-id="668d5-193">FileX opróżnia wszystkie sektory znajdujące się obecnie w pamięci podręcznej sektora sterownika do nośnika fizycznego, wysyłając żądanie opróżnienia do sterownika we/wy.</span><span class="sxs-lookup"><span data-stu-id="668d5-193">FileX flushes all sectors currently in the driver's sector cache to the physical media by issuing a flush request to the I/O driver.</span></span> <span data-ttu-id="668d5-194">Oczywiście, jeśli sterownik nie jest buforowany w sektorach, to żądanie nie wymaga przetwarzania sterownika.</span><span class="sxs-lookup"><span data-stu-id="668d5-194">Of course, if the driver is not caching sectors, this request requires no driver processing.</span></span> <span data-ttu-id="668d5-195">Następujące elementy członkowskie FX_MEDIA są używane dla żądania opróżnienia sterownika we/wy:</span><span class="sxs-lookup"><span data-stu-id="668d5-195">The following FX_MEDIA members are used for the I/O driver flush request:</span></span>

|<span data-ttu-id="668d5-196">FX_MEDIA składową</span><span class="sxs-lookup"><span data-stu-id="668d5-196">FX_MEDIA member</span></span>| <span data-ttu-id="668d5-197">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="668d5-197">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="668d5-198">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="668d5-198">fx_media_driver_request</span></span>|<span data-ttu-id="668d5-199">FX_DRIVER_FLUSH</span><span class="sxs-lookup"><span data-stu-id="668d5-199">FX_DRIVER_FLUSH</span></span>|

### <a name="driver-abort"></a><span data-ttu-id="668d5-200">Przerwanie sterownika</span><span class="sxs-lookup"><span data-stu-id="668d5-200">Driver Abort</span></span>

<span data-ttu-id="668d5-201">FileX informuje sterownik, aby przerwać wszystkie dalsze fizyczne operacje we/wy z nośnikiem fizycznym przez wystawienie żądania przerwania dla sterownika we/wy.</span><span class="sxs-lookup"><span data-stu-id="668d5-201">FileX informs the driver to abort all further physical I/O activity with the physical media by issuing an abort request to the I/O driver.</span></span> <span data-ttu-id="668d5-202">Sterownik nie powinien wykonać żadnych operacji we/wy ponownie, dopóki nie zostanie ponownie zainicjowany.</span><span class="sxs-lookup"><span data-stu-id="668d5-202">The driver should not perform any I/O again until it is re-initialized.</span></span> <span data-ttu-id="668d5-203">Następujące elementy członkowskie FX_MEDIA są używane dla żądania przerwania sterownika we/wy:</span><span class="sxs-lookup"><span data-stu-id="668d5-203">The following FX_MEDIA members are used for the I/O driver abort request:</span></span>

|<span data-ttu-id="668d5-204">FX_MEDIA składową</span><span class="sxs-lookup"><span data-stu-id="668d5-204">FX_MEDIA member</span></span>| <span data-ttu-id="668d5-205">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="668d5-205">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="668d5-206">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="668d5-206">fx_media_driver_request</span></span>| <span data-ttu-id="668d5-207">FX_DRIVER_ABORT</span><span class="sxs-lookup"><span data-stu-id="668d5-207">FX_DRIVER_ABORT</span></span>|

### <a name="release-sectors"></a><span data-ttu-id="668d5-208">Sektory wydania</span><span class="sxs-lookup"><span data-stu-id="668d5-208">Release Sectors</span></span>

<span data-ttu-id="668d5-209">Jeśli wcześniej została wybrana przez sterownik podczas inicjowania, FileX informuje sterownik za każdym razem, gdy jeden lub kilka kolejnych sektorów staną się bezpłatne.</span><span class="sxs-lookup"><span data-stu-id="668d5-209">If previously selected by the driver during initialization, FileX informs the driver whenever one or more consecutive sectors become free.</span></span> <span data-ttu-id="668d5-210">Jeśli sterownik jest w rzeczywistości programem FLASH Manager, te informacje mogą być używane do poinformowania Menedżera programu FLASH o tym, że te sektory nie są już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="668d5-210">If the driver is actually a FLASH manager, this information can be used to tell the FLASH manager that these sectors are no longer needed.</span></span> <span data-ttu-id="668d5-211">Następujące **FX_MEDIA** elementy członkowskie są używane dla żądania sektorów wydania we/wy:</span><span class="sxs-lookup"><span data-stu-id="668d5-211">The following **FX_MEDIA** members are used for the I/O release sectors request:</span></span>

|<span data-ttu-id="668d5-212">FX_MEDIA składową</span><span class="sxs-lookup"><span data-stu-id="668d5-212">FX_MEDIA member</span></span>| <span data-ttu-id="668d5-213">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="668d5-213">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="668d5-214">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="668d5-214">fx_media_driver_request</span></span>|<span data-ttu-id="668d5-215">FX_DRIVER_RELEASE_SECTORS</span><span class="sxs-lookup"><span data-stu-id="668d5-215">FX_DRIVER_RELEASE_SECTORS</span></span>|
|<span data-ttu-id="668d5-216">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="668d5-216">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="668d5-217">Początek wolnego sektora</span><span class="sxs-lookup"><span data-stu-id="668d5-217">Start of free sector</span></span>|
|<span data-ttu-id="668d5-218">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="668d5-218">fx_media_driver_sectors</span></span>|<span data-ttu-id="668d5-219">Liczba wolnych sektorów</span><span class="sxs-lookup"><span data-stu-id="668d5-219">Number of free sectors</span></span>|

### <a name="driver-suspension"></a><span data-ttu-id="668d5-220">Zawieszenie sterownika</span><span class="sxs-lookup"><span data-stu-id="668d5-220">Driver Suspension</span></span>

<span data-ttu-id="668d5-221">Ponieważ we/wy z nośnika fizycznego może upłynąć trochę czasu, wstrzymanie wątku wywołującego jest często pożądane.</span><span class="sxs-lookup"><span data-stu-id="668d5-221">Because I/O with physical media may take some time, suspending the calling thread is often desirable.</span></span> <span data-ttu-id="668d5-222">Oczywiście założono, że wykonywanie bazowej operacji we/wy jest zależne od przerwań.</span><span class="sxs-lookup"><span data-stu-id="668d5-222">Of course, this assumes completion of the underlying I/O operation is interrupt driven.</span></span> <span data-ttu-id="668d5-223">W takim przypadku zawieszenie wątku jest łatwo implementowane przy użyciu semafora ThreadX.</span><span class="sxs-lookup"><span data-stu-id="668d5-223">If so, thread suspension is easily implemented with a ThreadX semaphore.</span></span> <span data-ttu-id="668d5-224">Po uruchomieniu operacji wejściowej lub wyjściowej sterownik we/wy zawiesza się we własnym wewnętrznym czasie we/wy (utworzony z początkową liczbą zero podczas inicjowania sterownika).</span><span class="sxs-lookup"><span data-stu-id="668d5-224">After starting the input or output operation, the I/O driver suspends on its own internal I/O semaphore (created with an initial count of zero during driver initialization).</span></span> <span data-ttu-id="668d5-225">W ramach przetwarzania przerwań we/wy sterownika jest ustawiony ten sam semafor we/wy, który z kolei wznawia zawieszony wątek.</span><span class="sxs-lookup"><span data-stu-id="668d5-225">As part of the driver I/O completion interrupt processing, the same I/O semaphore is set, which in turn wakes up the suspended thread.</span></span>

### <a name="sector-translation"></a><span data-ttu-id="668d5-226">Tłumaczenie sektora</span><span class="sxs-lookup"><span data-stu-id="668d5-226">Sector Translation</span></span>

<span data-ttu-id="668d5-227">Ponieważ FileX przegląda nośnik jako liniowe sektory logiczne, żądania we/wy wykonywane do sterownika we/wy są tworzone z sektorami logicznymi.</span><span class="sxs-lookup"><span data-stu-id="668d5-227">Because FileX views the media as linear logical sectors, I/O requests made to the I/O driver are made with logical sectors.</span></span> <span data-ttu-id="668d5-228">Jest on odpowiedzialny za przetłumaczenie sektorów logicznych i fizycznej geometrii nośnika, który może obejmować głowice, ścieżki i sektory fizyczne.</span><span class="sxs-lookup"><span data-stu-id="668d5-228">It is the driver's responsibility to translate between logical sectors and the physical geometry of the media, which may include heads, tracks, and physical sectors.</span></span> <span data-ttu-id="668d5-229">W przypadku nośników dysków FLASH i RAM sektory logiczne zwykle mapują katalog na sektory fizyczne.</span><span class="sxs-lookup"><span data-stu-id="668d5-229">For FLASH and RAM disk media, the logical sectors typically map directory to physical sectors.</span></span> <span data-ttu-id="668d5-230">W każdym przypadku poniżej przedstawiono typowe formuły umożliwiające przeprowadzenie mapowania między logicznymi a fizycznymi w sterowniku we/wy:</span><span class="sxs-lookup"><span data-stu-id="668d5-230">In any case, here are the typical formulas to perform the logical to physical sector mapping in the I/O driver:</span></span>

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

<span data-ttu-id="668d5-231">Należy zauważyć, że sektory fizyczne zaczynają się na jednym, podczas gdy sektory logiczne zaczynają się od zera.</span><span class="sxs-lookup"><span data-stu-id="668d5-231">Note that physical sectors start at one, while logical sectors start at zero.</span></span>

### <a name="hidden-sectors"></a><span data-ttu-id="668d5-232">Ukryte sektory</span><span class="sxs-lookup"><span data-stu-id="668d5-232">Hidden Sectors</span></span>

<span data-ttu-id="668d5-233">Ukryte sektory zostały zamieszkałe przed rekordem rozruchowym na nośniku.</span><span class="sxs-lookup"><span data-stu-id="668d5-233">Hidden sectors resided prior to the boot record on the media.</span></span> <span data-ttu-id="668d5-234">Ponieważ są one naprawdę poza zakresem układu systemu plików FAT, muszą być uwzględnione w każdej operacji sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="668d5-234">Because they are really outside the scope of the FAT file system layout, they must be accounted for in each logical sector operation the driver does.</span></span>

### <a name="media-write-protect"></a><span data-ttu-id="668d5-235">Ochrona przed zapisem multimediów</span><span class="sxs-lookup"><span data-stu-id="668d5-235">Media Write Protect</span></span>

<span data-ttu-id="668d5-236">Sterownik FileX może włączyć ochronę przed zapisem przez ustawienie pola fx_media_driver_write_protect w bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="668d5-236">The FileX driver can turn on write protect by setting the fx_media_driver_write_protect field in the media control block.</span></span> <span data-ttu-id="668d5-237">Spowoduje to zwrócenie błędu, jeśli jakiekolwiek wywołania FileX zostaną wykonane podczas próby zapisu na nośniku.</span><span class="sxs-lookup"><span data-stu-id="668d5-237">This will cause an error to be returned if any FileX calls are made in an attempt to write to the media.</span></span>

## <a name="sample-ram-driver"></a><span data-ttu-id="668d5-238">Przykładowy sterownik pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="668d5-238">Sample RAM Driver</span></span>

<span data-ttu-id="668d5-239">System demonstracyjny FileX jest dostarczany z małym sterownikiem dysku RAM, który jest zdefiniowany w pliku fx_ram_driver. c.</span><span class="sxs-lookup"><span data-stu-id="668d5-239">The FileX demonstration system is delivered with a small RAM disk driver, which is defined in the file fx_ram_driver.c.</span></span> <span data-ttu-id="668d5-240">Sterownik zakłada miejsce w pamięci 32 KB i tworzy rekord rozruchowy dla sektorów 256 128-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="668d5-240">The driver assumes a 32K memory space and creates a boot record for 256 128-byte sectors.</span></span> <span data-ttu-id="668d5-241">Ten plik zawiera dobry przykład implementacji sterowników we/wy FileX specyficznych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="668d5-241">This file provides a good example of how to implement application specific FileX I/O drivers.</span></span>

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
