---
title: Opis Azure RTOS FileX
description: Azure RTOS FileX to system plików zgodny z tabelą alokacji plików (FAT) o wysokiej wydajności, który jest w pełni zintegrowany z systemem Azure RTOS ThreadX i dostępny dla wszystkich obsługiwanych procesorów. Podobnie jak Azure RTOS ThreadX, Azure RTOS FileX został zaprojektowany tak, aby miał niewielkie rozmiary i wysoką wydajność, dzięki czemu idealnie nadaje się do współczesnych głęboko osadzonych aplikacji, które wymagają operacji zarządzania plikami. Plik FileX obsługuje większość nośników fizycznych, w tym pamięci RAM, Azure RTOS USBX, SD CARD i pamięci flash NAND/NOR za pośrednictwem Azure RTOS LevelX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a54f160c96fb3e90c2295ae72020c121d367a12
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171357"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="6700e-105">Omówienie Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="6700e-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="6700e-106">Azure RTOS plików FileX to zaawansowane rozwiązanie klasy przemysłowej firmy Azure RTOS dla formatów plików Fat firmy Microsoft, zaprojektowane specjalnie z myślą o aplikacjach głęboko osadzonych, w czasie rzeczywistym i IoT.</span><span class="sxs-lookup"><span data-stu-id="6700e-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="6700e-107">Azure RTOS FileX obsługuje wszystkie formaty plików firmy Microsoft, w tym FAT12, FAT16, FAT32 i exFAT.</span><span class="sxs-lookup"><span data-stu-id="6700e-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="6700e-108">System FileX oferuje również opcjonalną odporność na uszkodzenia i poziom zużycia pamięci FLASH za pośrednictwem dodatku o [nazwie Azure RTOS LevelX.](https://docs.microsoft.com/azure/rtos/levelx/)</span><span class="sxs-lookup"><span data-stu-id="6700e-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="6700e-109">Wszystko to w połączeniu z niewielkim zużyciem pamięci, szybkim wykonywaniem i doskonałą łatwością użycia sprawiają, że Azure RTOS FileX jest idealnym wyborem dla najbardziej wymagających osadzonych aplikacji IoT.</span><span class="sxs-lookup"><span data-stu-id="6700e-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="6700e-110">Protokoły interfejsu API</span><span class="sxs-lookup"><span data-stu-id="6700e-110">API protocols</span></span>

### <a name="media-services"></a><span data-ttu-id="6700e-111">Media Services</span><span class="sxs-lookup"><span data-stu-id="6700e-111">Media Services</span></span>

- <span data-ttu-id="6700e-112">Obsługa plików FAT 12/16/32 i exFAT</span><span class="sxs-lookup"><span data-stu-id="6700e-112">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="6700e-113">Minimalna 6 KB pamięci FLASH, 2,5 KB pamięci RAM</span><span class="sxs-lookup"><span data-stu-id="6700e-113">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="6700e-114">Pełne usługi dostępu do multimediów</span><span class="sxs-lookup"><span data-stu-id="6700e-114">Complete media access services</span></span>
- <span data-ttu-id="6700e-115">Nieograniczona liczba wystąpień multimediów</span><span class="sxs-lookup"><span data-stu-id="6700e-115">Unlimited number of media instance</span></span>
- <span data-ttu-id="6700e-116">Prosty interfejs sterownika sektora logicznego odczytu/zapisu</span><span class="sxs-lookup"><span data-stu-id="6700e-116">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="6700e-117">Obsługa wielu partycji</span><span class="sxs-lookup"><span data-stu-id="6700e-117">Multiple partition support</span></span>
- <span data-ttu-id="6700e-118">Pamięć podręczna sektora logicznego</span><span class="sxs-lookup"><span data-stu-id="6700e-118">Logical sector cache</span></span>
- <span data-ttu-id="6700e-119">Pamięć podręczna wpisów FAT</span><span class="sxs-lookup"><span data-stu-id="6700e-119">FAT entry cache</span></span>
- <span data-ttu-id="6700e-120">Opcjonalna obsługa odporności na uszkodzenia</span><span class="sxs-lookup"><span data-stu-id="6700e-120">Optional fault tolerance support</span></span>
- <span data-ttu-id="6700e-121">Odroczona pomocnicza aktualizacja FAT</span><span class="sxs-lookup"><span data-stu-id="6700e-121">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="6700e-122">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="6700e-122">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="6700e-123">Intuicyjne interfejsy API dostępu do multimediów, w tym:</span><span class="sxs-lookup"><span data-stu-id="6700e-123">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="6700e-124">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="6700e-124">fx_media_open</span></span>
  - <span data-ttu-id="6700e-125">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="6700e-125">fx_media_close</span></span>
  - <span data-ttu-id="6700e-126">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="6700e-126">fx_media_format</span></span>
  - <span data-ttu-id="6700e-127">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="6700e-127">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="6700e-128">Usługi katalogowe</span><span class="sxs-lookup"><span data-stu-id="6700e-128">Directory Services</span></span>

- <span data-ttu-id="6700e-129">Maksymalnie 256 ścieżek bajtów</span><span class="sxs-lookup"><span data-stu-id="6700e-129">Up to 256 byte paths</span></span>
- <span data-ttu-id="6700e-130">Obsługiwane nazwy katalogów long i 8.3</span><span class="sxs-lookup"><span data-stu-id="6700e-130">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="6700e-131">Tworzenie i usuwanie & katalogu</span><span class="sxs-lookup"><span data-stu-id="6700e-131">Directory create & delete</span></span>
- <span data-ttu-id="6700e-132">Przechodzenie i nawigacja w katalogu</span><span class="sxs-lookup"><span data-stu-id="6700e-132">Directory navigation and traversal</span></span>
- <span data-ttu-id="6700e-133">Zarządzanie atrybutami katalogu</span><span class="sxs-lookup"><span data-stu-id="6700e-133">Directory attributes management</span></span>
- <span data-ttu-id="6700e-134">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="6700e-134">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="6700e-135">Intuicyjne interfejsy API dostępu do katalogu, w tym:</span><span class="sxs-lookup"><span data-stu-id="6700e-135">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="6700e-136">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="6700e-136">fx_directory_create</span></span>
  - <span data-ttu-id="6700e-137">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="6700e-137">fx_directory_delete</span></span>
  - <span data-ttu-id="6700e-138">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="6700e-138">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="6700e-139">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="6700e-139">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="6700e-140">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="6700e-140">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="6700e-141">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="6700e-141">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="6700e-142">Usługi plików</span><span class="sxs-lookup"><span data-stu-id="6700e-142">File Services</span></span>

- <span data-ttu-id="6700e-143">Minimalna 3,3 KB pamięci FLASH</span><span class="sxs-lookup"><span data-stu-id="6700e-143">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="6700e-144">Nieograniczona liczba otwartych plików</span><span class="sxs-lookup"><span data-stu-id="6700e-144">Unlimited open files</span></span>
- <span data-ttu-id="6700e-145">Pliki tylko do odczytu można otwierać wiele razy</span><span class="sxs-lookup"><span data-stu-id="6700e-145">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="6700e-146">Obsługiwane nazwy katalogów long i 8.3</span><span class="sxs-lookup"><span data-stu-id="6700e-146">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="6700e-147">Obsługa ciągłych plików</span><span class="sxs-lookup"><span data-stu-id="6700e-147">Contiguous file support</span></span>
- <span data-ttu-id="6700e-148">Logika szybkiego szukania</span><span class="sxs-lookup"><span data-stu-id="6700e-148">Fast seek logic</span></span>
- <span data-ttu-id="6700e-149">Wstępna alokacja klastrów</span><span class="sxs-lookup"><span data-stu-id="6700e-149">Pre-allocation of clusters</span></span>
- <span data-ttu-id="6700e-150">Tworzenie, usuwanie i zmienianie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="6700e-150">File create, delete, and rename</span></span>
- <span data-ttu-id="6700e-151">Odczyt, zapis i wyświetlanie plików</span><span class="sxs-lookup"><span data-stu-id="6700e-151">File read, write, and see</span></span>
- <span data-ttu-id="6700e-152">Zarządzanie atrybutami plików</span><span class="sxs-lookup"><span data-stu-id="6700e-152">File attributes management</span></span>
- <span data-ttu-id="6700e-153">Śledzenie na poziomie systemu za pośrednictwem Azure RTOS TraceX</span><span class="sxs-lookup"><span data-stu-id="6700e-153">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="6700e-154">Intuicyjne interfejsy API dostępu do plików, w tym:</span><span class="sxs-lookup"><span data-stu-id="6700e-154">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="6700e-155">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="6700e-155">fx_file_create</span></span>
  - <span data-ttu-id="6700e-156">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="6700e-156">fx_file_delete</span></span>
  - <span data-ttu-id="6700e-157">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="6700e-157">fx_file_attributes_set</span></span>
  - <span data-ttu-id="6700e-158">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="6700e-158">fx_file_attributes_read</span></span>
  - <span data-ttu-id="6700e-159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="6700e-159">fx_file_read</span></span>
  - <span data-ttu-id="6700e-160">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="6700e-160">fx_file_seek</span></span>
  - <span data-ttu-id="6700e-161">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="6700e-161">fx_file_write</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="6700e-162">Zaawansowana technologia</span><span class="sxs-lookup"><span data-stu-id="6700e-162">Advanced technology</span></span>

<span data-ttu-id="6700e-163">Azure RTOS FileX to zaawansowana technologia, w tym następująca.</span><span class="sxs-lookup"><span data-stu-id="6700e-163">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="6700e-164">Obsługa plików FAT 12/16/32 i exFAT</span><span class="sxs-lookup"><span data-stu-id="6700e-164">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="6700e-165">Obsługa wielu partycji</span><span class="sxs-lookup"><span data-stu-id="6700e-165">Multiple partition support</span></span>
- <span data-ttu-id="6700e-166">Automatyczne skalowanie</span><span class="sxs-lookup"><span data-stu-id="6700e-166">Automatic scaling</span></span>
- <span data-ttu-id="6700e-167">Neutralność endianowa</span><span class="sxs-lookup"><span data-stu-id="6700e-167">Endian neutral</span></span>
- <span data-ttu-id="6700e-168">Obsługa długich nazw plików i 8.3</span><span class="sxs-lookup"><span data-stu-id="6700e-168">Long file name and 8.3 support</span></span>
- <span data-ttu-id="6700e-169">Opcjonalna obsługa odporności na uszkodzenia</span><span class="sxs-lookup"><span data-stu-id="6700e-169">Optional fault tolerance support</span></span>
- <span data-ttu-id="6700e-170">Pamięć podręczna sektorów logicznych</span><span class="sxs-lookup"><span data-stu-id="6700e-170">Logical sector cache</span></span>
- <span data-ttu-id="6700e-171">Pamięć podręczna wpisów FAT</span><span class="sxs-lookup"><span data-stu-id="6700e-171">FAT entry cache</span></span>
- <span data-ttu-id="6700e-172">Wstępna alokacja klastrów</span><span class="sxs-lookup"><span data-stu-id="6700e-172">Pre-allocation of clusters</span></span>
- <span data-ttu-id="6700e-173">Ciągła obsługa plików</span><span class="sxs-lookup"><span data-stu-id="6700e-173">Contiguous file support</span></span>
- <span data-ttu-id="6700e-174">Opcjonalne metryki wydajności</span><span class="sxs-lookup"><span data-stu-id="6700e-174">Optional performance metrics</span></span>
- <span data-ttu-id="6700e-175">Azure RTOS analizy systemu TraceX</span><span class="sxs-lookup"><span data-stu-id="6700e-175">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="6700e-176">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span><span class="sxs-lookup"><span data-stu-id="6700e-176">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="6700e-177">Azure RTOS LevelX to produkt firmy Microsoft do wyrównania zużycia w technologii NOR/NAND FLASH.</span><span class="sxs-lookup"><span data-stu-id="6700e-177">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="6700e-178">Azure RTOS LevelX może być używany w połączeniu z fileX lub jako autonomiczna, bezpośrednia biblioteka sektorów odczytu/zapisu FLASH dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6700e-178">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>
