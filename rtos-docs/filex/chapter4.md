---
title: Rozdział 4 — Opis Azure RTOS FileX
description: Ten rozdział zawiera opis wszystkich usług FileX Azure RTOS w kolejności alfabetycznej.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c24259fb9b6b212dda99422e3ee1ad0e2fd970ce
ms.sourcegitcommit: dbbec3ba6a7eb6097c7888b235c433a2efd6e5b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2021
ms.locfileid: "113754883"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="b9b02-103">Rozdział 4 — Opis Azure RTOS FileX</span><span class="sxs-lookup"><span data-stu-id="b9b02-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="b9b02-104">Ten rozdział zawiera opis wszystkich usług FileX Azure RTOS w kolejności alfabetycznej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="b9b02-105">Nazwy usług są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="b9b02-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="b9b02-107">Odczytuje atrybuty katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="b9b02-109">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-109">Description</span></span>

<span data-ttu-id="b9b02-110">Ta usługa odczytuje atrybuty katalogu z określonego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-111">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-111">Input Parameters</span></span>

- <span data-ttu-id="b9b02-112">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-113">**directory_name:** wskaźnik do nazwy żądanego katalogu (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="b9b02-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="b9b02-114">**atrybuty** _ptr: wskaźnik do miejsca docelowego dla atrybutów katalogu do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="b9b02-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="b9b02-115">Atrybuty katalogu są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:</span><span class="sxs-lookup"><span data-stu-id="b9b02-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="b9b02-116">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="b9b02-117">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="b9b02-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="b9b02-118">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="b9b02-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="b9b02-119">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="b9b02-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="b9b02-120">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="b9b02-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="b9b02-121">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="b9b02-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-122">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-122">Return Values</span></span>

- <span data-ttu-id="b9b02-123">**FX_SUCCESS** (0x00) Atrybuty katalogu pomyślnie odczytane</span><span class="sxs-lookup"><span data-stu-id="b9b02-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="b9b02-124">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="b9b02-125">**FX _NOT FOUND** (0x04) Określony katalog nie został znaleziony na nośniku</span><span class="sxs-lookup"><span data-stu-id="b9b02-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="b9b02-126">**FX_NOT_DIRECTORY** (0x0E) Entry nie jest katalogiem</span><span class="sxs-lookup"><span data-stu-id="b9b02-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="b9b02-127">**FX_IO_ERROR** (0x90) sterownika We/Wy</span><span class="sxs-lookup"><span data-stu-id="b9b02-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="b9b02-128">**FX_FILE_CORRUPT** 0x08) Plik jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-129">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="b9b02-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="b9b02-130">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT</span><span class="sxs-lookup"><span data-stu-id="b9b02-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="b9b02-131">**FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-132">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="b9b02-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="b9b02-133">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="b9b02-134">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-135">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-135">Allowed From</span></span>

<span data-ttu-id="b9b02-136">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-138">See Also</span></span>

- <span data-ttu-id="b9b02-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-140">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-141">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-142">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-143">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-146">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-152">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-155">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="b9b02-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="b9b02-160">Ustawia atrybuty katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="b9b02-162">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-162">Description</span></span>

<span data-ttu-id="b9b02-163">Ta usługa ustawia atrybuty katalogu na atrybuty określone przez wywołujący.</span><span class="sxs-lookup"><span data-stu-id="b9b02-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-164">*Ta aplikacja może modyfikować tylko podzbiór atrybutów katalogu za pomocą tej usługi. Każda próba ustawienia dodatkowych atrybutów spowoduje błąd.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-165">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-165">Input Parameters</span></span>

- <span data-ttu-id="b9b02-166">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-167">**directory_name:** wskaźnik do nazwy żądanego katalogu (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="b9b02-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="b9b02-168">**atrybuty:** nowe atrybuty tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="b9b02-169">Prawidłowe atrybuty katalogu są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b9b02-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="b9b02-170">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="b9b02-171">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="b9b02-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="b9b02-172">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="b9b02-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="b9b02-173">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="b9b02-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-174">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-174">Return Values</span></span>

- <span data-ttu-id="b9b02-175">**FX_SUCCESS** (0x00) Zestaw atrybutów katalogu successful</span><span class="sxs-lookup"><span data-stu-id="b9b02-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="b9b02-176">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="b9b02-177">**FX_NOT_FOUND** (0x04) Określony katalog nie został znaleziony na nośniku</span><span class="sxs-lookup"><span data-stu-id="b9b02-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="b9b02-178">**FX_NOT_DIRECTORY** (0x0E) Entry nie jest katalogiem</span><span class="sxs-lookup"><span data-stu-id="b9b02-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="b9b02-179">**FX_IO_ERROR** (0x90) sterownika We/Wy</span><span class="sxs-lookup"><span data-stu-id="b9b02-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="b9b02-180">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem</span><span class="sxs-lookup"><span data-stu-id="b9b02-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="b9b02-181">**FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-182">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="b9b02-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="b9b02-183">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT</span><span class="sxs-lookup"><span data-stu-id="b9b02-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="b9b02-184">**FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-185">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="b9b02-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="b9b02-186">**FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tym katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="b9b02-187">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="b9b02-188">**FX_INVALID_ATTR** (0x19) Wybrane nieprawidłowe atrybuty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="b9b02-189">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-190">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-190">Allowed From</span></span>

<span data-ttu-id="b9b02-191">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-192">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-193">See Also</span></span>

- <span data-ttu-id="b9b02-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-195">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-196">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-197">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-198">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-201">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-207">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-210">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="b9b02-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-214">fx_directory_create</span></span>

<span data-ttu-id="b9b02-215">Tworzy podkatalog</span><span class="sxs-lookup"><span data-stu-id="b9b02-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-216">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="b9b02-217">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-217">Description</span></span>

<span data-ttu-id="b9b02-218">Ta usługa tworzy podkatalog w bieżącym katalogu domyślnym lub w ścieżce podanej w nazwie katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="b9b02-219">W przeciwieństwie do katalogu głównego podkatalogi nie mają ograniczenia liczby plików, które mogą przechowywać.</span><span class="sxs-lookup"><span data-stu-id="b9b02-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="b9b02-220">Katalog główny może zawierać tylko liczbę wpisów określonych przez rekord rozruchowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-221">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-221">Input Parameters</span></span>

- <span data-ttu-id="b9b02-222">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-223">**directory_name:** wskaźnik do nazwy katalogu do utworzenia (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="b9b02-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-224">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-224">Return Values</span></span>

- <span data-ttu-id="b9b02-225">**FX_SUCCESS** (0x00) Pomyślne utworzenie katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="b9b02-226">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="b9b02-227">**FX_NOT_FOUND** (0x04) Określony katalog nie został znaleziony na nośniku</span><span class="sxs-lookup"><span data-stu-id="b9b02-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="b9b02-228">**FX_NOT_DIRECTORY** (0x0E) Entry nie jest katalogiem</span><span class="sxs-lookup"><span data-stu-id="b9b02-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="b9b02-229">**FX_IO_ERROR** (0x90) sterownika We/Wy</span><span class="sxs-lookup"><span data-stu-id="b9b02-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="b9b02-230">**FX_FILE _CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-231">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="b9b02-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="b9b02-232">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT</span><span class="sxs-lookup"><span data-stu-id="b9b02-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="b9b02-233">**FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-234">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="b9b02-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="b9b02-235">**FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tym katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="b9b02-236">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="b9b02-237">**FX_INVALID_ATTR** (0x19) Wybrane nieprawidłowe atrybuty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="b9b02-238">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-239">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-239">Allowed From</span></span>

<span data-ttu-id="b9b02-240">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-241">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-242">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-242">See Also</span></span>

- <span data-ttu-id="b9b02-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-245">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-246">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-247">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-250">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-256">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-259">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="b9b02-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-263">fx_directory_default_get</span></span>

<span data-ttu-id="b9b02-264">Pobiera ostatni katalog domyślny</span><span class="sxs-lookup"><span data-stu-id="b9b02-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-265">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-266">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-266">Description</span></span>

<span data-ttu-id="b9b02-267">Ta usługa zwraca wskaźnik do ostatniej ścieżki ustawionej przez ***fx_directory_default_set***.</span><span class="sxs-lookup"><span data-stu-id="b9b02-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="b9b02-268">Jeśli katalog domyślny nie został ustawiony lub jeśli bieżący katalog domyślny jest katalogiem głównym, zwracana jest FX_NULL wartość .</span><span class="sxs-lookup"><span data-stu-id="b9b02-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-269">*Domyślny rozmiar ciągu ścieżki wewnętrznej to 256 znaków. Można go zmienić przez zmodyfikowanie FX_MAXIMUM_PATH **w** pliku **fx_api.h** i ponowne skompilowanie całej biblioteki FileX. Ścieżka ciągu znaków jest zachowywana dla aplikacji i nie jest używana wewnętrznie przez plik FileX.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-270">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-270">Input Parameters</span></span>

- <span data-ttu-id="b9b02-271">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-272">**return_path_name:** wskaźnik do miejsca docelowego dla ostatniego domyślnego ciągu katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="b9b02-273">Jeśli bieżącym ustawieniem katalogu domyślnego jest katalog główny, jest zwracana wartość FX_NULL zwracana.</span><span class="sxs-lookup"><span data-stu-id="b9b02-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="b9b02-274">Po otwarciu nośnika ustawieniem domyślnym jest katalog główny.</span><span class="sxs-lookup"><span data-stu-id="b9b02-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-275">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-275">Return Values</span></span>

- <span data-ttu-id="b9b02-276">**FX_SUCCESS** (0x00) Pomyślne uzyskiwanie katalogu domyślnego</span><span class="sxs-lookup"><span data-stu-id="b9b02-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="b9b02-277">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="b9b02-278">**FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik docelowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="b9b02-279">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-280">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-280">Allowed From</span></span>

<span data-ttu-id="b9b02-281">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-282">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="b9b02-283">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-283">See Also</span></span>

- <span data-ttu-id="b9b02-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-286">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-287">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-288">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-291">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-297">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-300">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="b9b02-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-304">fx_directory_default_set</span></span>

<span data-ttu-id="b9b02-305">Ustawia katalog domyślny</span><span class="sxs-lookup"><span data-stu-id="b9b02-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-306">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-307">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-307">Description</span></span>

<span data-ttu-id="b9b02-308">Ta usługa ustawia domyślny katalog nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="b9b02-309">Jeśli zostanie FX_NULL, domyślny katalog zostanie ustawiony na katalog główny nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="b9b02-310">Wszystkie kolejne operacje na plikach, które nie określają jawnie ścieżki, będą domyślnie wykonywane w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-311">*Domyślny rozmiar ciągu ścieżki wewnętrznej to 256 znaków. Można go zmienić, **modyfikując** FX_MAXIMUM_PATH w pliku **fx_api.h** i ponownie przebudowując całą bibliotekę FileX. Ścieżka ciągu znaków jest utrzymywana dla aplikacji i nie jest używana wewnętrznie przez plik FileX.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-312">*W przypadku nazw dostarczonych przez aplikację plik FileX obsługuje zarówno ukośnik odwrotny ( ), jak i ukośnik (/) do oddzielnych \\ katalogów, podkatalogów i nazw plików. Jednak plik FileX używa znaku ukośnika odwrotnego tylko w ścieżkach zwracanych do aplikacji.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-313">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-313">Input Parameters</span></span>

- <span data-ttu-id="b9b02-314">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-315">**new_path_name:** Wskaźnik do nowej domyślnej nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="b9b02-316">Jeśli zostanie FX_NULL, domyślny katalog nośnika zostanie ustawiony na katalog główny nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-317">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-317">Return Values</span></span>

- <span data-ttu-id="b9b02-318">**FX_SUCCESS** (0x00) Zestaw katalogów domyślnych pomyślnych</span><span class="sxs-lookup"><span data-stu-id="b9b02-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="b9b02-319">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="b9b02-320">**FX_INVALID_PATH** (0x0D) Nie można odnaleźć nowego katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="b9b02-321">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-322">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-323">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-323">Allowed From</span></span>

<span data-ttu-id="b9b02-324">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-325">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-326">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-326">See Also</span></span>

- <span data-ttu-id="b9b02-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-329">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-330">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-331">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-334">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-340">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-343">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="b9b02-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-347">fx_directory_delete</span></span>

<span data-ttu-id="b9b02-348">Usuwa podkatalog</span><span class="sxs-lookup"><span data-stu-id="b9b02-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-349">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-350">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-350">Description</span></span>

<span data-ttu-id="b9b02-351">Ta usługa usuwa określony katalog.</span><span class="sxs-lookup"><span data-stu-id="b9b02-351">This service deletes the specified directory.</span></span> <span data-ttu-id="b9b02-352">Pamiętaj, że katalog musi być pusty, aby go usunąć.</span><span class="sxs-lookup"><span data-stu-id="b9b02-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-353">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-353">Input Parameters</span></span>

- <span data-ttu-id="b9b02-354">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-355">**directory_name:** wskaźnik do nazwy katalogu do usunięcia (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="b9b02-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-356">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-356">Return Values</span></span>

- <span data-ttu-id="b9b02-357">**FX_SUCCESS** (0x00) Pomyślne usunięcie katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="b9b02-358">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="b9b02-359">**FX_NOT_FOUND** (0x04) Nie znaleziono określonego katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="b9b02-360">**FX_DIR_NOT_EMPTY** (0x10) Określony katalog nie jest pusty</span><span class="sxs-lookup"><span data-stu-id="b9b02-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="b9b02-361">**FX_IO_ERROR** (0x90) Sterownik We/Wy</span><span class="sxs-lookup"><span data-stu-id="b9b02-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="b9b02-362">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem</span><span class="sxs-lookup"><span data-stu-id="b9b02-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="b9b02-363">**FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-364">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="b9b02-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="b9b02-365">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT</span><span class="sxs-lookup"><span data-stu-id="b9b02-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="b9b02-366">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-367">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="b9b02-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="b9b02-368">**FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tym katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="b9b02-369">**FX_NOT_DIRECTORY** (0x0E) Nie jest wpisem katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="b9b02-370">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="b9b02-371">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-372">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-372">Allowed From</span></span>

<span data-ttu-id="b9b02-373">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-374">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-375">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-375">See Also</span></span>

- <span data-ttu-id="b9b02-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-378">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-379">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-380">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-383">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-389">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-392">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="b9b02-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="b9b02-397">Pobiera pierwszy wpis katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-398">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-399">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-399">Description</span></span>

<span data-ttu-id="b9b02-400">Ta usługa pobiera nazwę pierwszego wpisu w katalogu domyślnym i kopiuje ją do określonego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-401">*Określone miejsce docelowe musi być wystarczająco duże, aby pomieścić maksymalną nazwę FileX o maksymalnym rozmiarze, zgodnie z **definicją FX_MAX_LONG_NAME_LEN.***</span><span class="sxs-lookup"><span data-stu-id="b9b02-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-402">*Jeśli używasz ścieżki innej niż lokalna, ważne jest, aby uniemożliwić innym wątkom aplikacji zmianę tego katalogu (ze zmianą poziomu semafora, mutexu lub priorytetu ThreadX) przez inne wątki aplikacji podczas przechodzenia do katalogu. W przeciwnym razie można uzyskać nieprawidłowe wyniki.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-403">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-403">Input Parameters</span></span>

- <span data-ttu-id="b9b02-404">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-405">**return_entry_name:** wskaźnik do miejsca docelowego dla pierwszej nazwy wpisu w katalogu domyślnym.</span><span class="sxs-lookup"><span data-stu-id="b9b02-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-406">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-406">Return Values</span></span>

- <span data-ttu-id="b9b02-407">**FX_SUCCESS** (0x00) Znajdowanie pomyślnego pierwszego wpisu katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="b9b02-408">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="b9b02-409">**FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tym katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="b9b02-410">**FX_IO_ERROR** (0x90) sterownika We/Wy</span><span class="sxs-lookup"><span data-stu-id="b9b02-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="b9b02-411">**FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-412">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="b9b02-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="b9b02-413">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT</span><span class="sxs-lookup"><span data-stu-id="b9b02-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="b9b02-414">**FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik docelowy</span><span class="sxs-lookup"><span data-stu-id="b9b02-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="b9b02-415">**FX_CALLER_ERROR** (0x20) nie jest wątkiem</span><span class="sxs-lookup"><span data-stu-id="b9b02-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-416">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-416">Allowed From</span></span>

<span data-ttu-id="b9b02-417">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-418">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-419">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-419">See Also</span></span>

- <span data-ttu-id="b9b02-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-422">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-423">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-424">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-425">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-427">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-433">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-436">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="b9b02-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="b9b02-441">Pobiera pierwszy wpis katalogu z pełnymi informacjami</span><span class="sxs-lookup"><span data-stu-id="b9b02-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-442">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="b9b02-443">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-443">Input Parameters</span></span>

- <span data-ttu-id="b9b02-444">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-445">**directory_name:** wskaźnik do miejsca docelowego dla nazwy wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="b9b02-446">Musi być co najmniej tak duży, jak FX_MAX_LONG_NAME_LEN.</span><span class="sxs-lookup"><span data-stu-id="b9b02-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="b9b02-447">**atrybuty:** jeśli wartość nie ma wartości null, wskaźnik do miejsca docelowego dla atrybutów wpisu do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="b9b02-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="b9b02-448">Atrybuty są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:</span><span class="sxs-lookup"><span data-stu-id="b9b02-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="b9b02-449">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="b9b02-450">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="b9b02-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="b9b02-451">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="b9b02-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="b9b02-452">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="b9b02-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="b9b02-453">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="b9b02-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="b9b02-454">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="b9b02-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="b9b02-455">**size:** jeśli wartość nie ma wartości null, wskaźnik do miejsca docelowego dla rozmiaru wpisu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="b9b02-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="b9b02-456">**year:** Jeśli wartość nie ma wartości null, wskaźnik do miejsca docelowego dla roku modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="b9b02-457">**month:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla miesiąca modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="b9b02-458">**day:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla daty modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="b9b02-459">**hour:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla godziny modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="b9b02-460">**minute:** jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla minuty modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="b9b02-461">**second:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla drugiej modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-462">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-462">Return Values</span></span>

- <span data-ttu-id="b9b02-463">**FX_SUCCESS** (0x00) Znajdowanie pomyślnego pierwszego wpisu katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="b9b02-464">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="b9b02-465">**FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tym katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="b9b02-466">**FX_IO_ERROR** (0x90) sterownika We/Wy</span><span class="sxs-lookup"><span data-stu-id="b9b02-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="b9b02-467">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem</span><span class="sxs-lookup"><span data-stu-id="b9b02-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="b9b02-468">**FX_FILE _CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-469">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="b9b02-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="b9b02-470">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT</span><span class="sxs-lookup"><span data-stu-id="b9b02-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="b9b02-471">**FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-472">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="b9b02-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="b9b02-473">**FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik docelowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="b9b02-474">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-475">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-475">Allowed From</span></span>

<span data-ttu-id="b9b02-476">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-477">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-477">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-478">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-478">See Also</span></span>

- <span data-ttu-id="b9b02-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-481">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-482">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-483">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-484">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-486">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-492">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-495">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="b9b02-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="b9b02-499">fx_directory_information_get:</span></span>

<span data-ttu-id="b9b02-500">Pobiera informacje o wpisie katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-501">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="b9b02-502">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-502">Input Parameters</span></span>

- <span data-ttu-id="b9b02-503">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-504">**directory_name:** wskaźnik do nazwy wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="b9b02-505">**atrybuty:** wskaźnik do miejsca docelowego dla atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="b9b02-506">**size**: wskaźnik do miejsca docelowego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="b9b02-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="b9b02-507">**year**: wskaźnik do miejsca docelowego dla roku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="b9b02-508">**month:** wskaźnik do miejsca docelowego dla miesiąca.</span><span class="sxs-lookup"><span data-stu-id="b9b02-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="b9b02-509">**day**: wskaźnik do miejsca docelowego dla dnia.</span><span class="sxs-lookup"><span data-stu-id="b9b02-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="b9b02-510">**hour**: wskaźnik do miejsca docelowego dla godziny.</span><span class="sxs-lookup"><span data-stu-id="b9b02-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="b9b02-511">**minute:** wskaźnik do miejsca docelowego dla minuty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="b9b02-512">**second**: wskaźnik do miejsca docelowego dla sekundy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-513">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-513">Return Values</span></span>

- <span data-ttu-id="b9b02-514">**FX_SUCCESS** (0x00) Znajdowanie pomyślnego pierwszego wpisu katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="b9b02-515">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="b9b02-516">**FX_NOT_FOUND** (0x04) Określony katalog nie został znaleziony na nośniku</span><span class="sxs-lookup"><span data-stu-id="b9b02-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="b9b02-517">**FX_IO_ERROR** (0x90) sterownika We/Wy</span><span class="sxs-lookup"><span data-stu-id="b9b02-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="b9b02-518">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="b9b02-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="b9b02-519">**FX_FILE _CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-520">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT</span><span class="sxs-lookup"><span data-stu-id="b9b02-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="b9b02-521">**FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-522">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="b9b02-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="b9b02-523">**FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik docelowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="b9b02-524">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-525">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-525">Allowed From</span></span>

<span data-ttu-id="b9b02-526">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-527">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-527">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-528">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-528">See Also</span></span>

- <span data-ttu-id="b9b02-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-531">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-532">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-533">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-534">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-542">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-545">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="b9b02-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="b9b02-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="b9b02-550">Czyszczy domyślną ścieżkę lokalną</span><span class="sxs-lookup"><span data-stu-id="b9b02-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-551">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="b9b02-552">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-552">Description</span></span>

<span data-ttu-id="b9b02-553">Ta usługa wyczyści poprzednią ścieżkę lokalną ustawioną dla wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-554">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-554">Input Parameters</span></span>

- <span data-ttu-id="b9b02-555">**media_ptr:** Wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-556">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-556">Return Values</span></span>

- <span data-ttu-id="b9b02-557">**FX_SUCCESS** (0x00) Ścieżka lokalna pomyślna.</span><span class="sxs-lookup"><span data-stu-id="b9b02-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="b9b02-558">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest obecnie otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="b9b02-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH zdefiniowane</span><span class="sxs-lookup"><span data-stu-id="b9b02-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="b9b02-560">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-561">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-561">Allowed From</span></span>

<span data-ttu-id="b9b02-562">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-563">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-564">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-564">See Also</span></span>

- <span data-ttu-id="b9b02-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-567">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-568">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-569">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-570">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-573">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-578">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-581">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="b9b02-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="b9b02-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="b9b02-586">Pobiera bieżący ciąg ścieżki lokalnej</span><span class="sxs-lookup"><span data-stu-id="b9b02-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-587">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-588">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-588">Description</span></span>

<span data-ttu-id="b9b02-589">Ta usługa zwraca wskaźnik ścieżki lokalnej określonego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="b9b02-590">Jeśli nie ustawiono ścieżki lokalnej, do wywołującego jest zwracana wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-591">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-591">Input Parameters</span></span>

- <span data-ttu-id="b9b02-592">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-593">**return_path_name:** wskaźnik do docelowego wskaźnika ciągu dla ciągu ścieżki lokalnej, który ma być przechowywany.</span><span class="sxs-lookup"><span data-stu-id="b9b02-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-594">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-594">Return Values</span></span>

- <span data-ttu-id="b9b02-595">**FX_SUCCESS** (0x00) Uzyskiwanie pomyślnej ścieżki lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="b9b02-596">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest obecnie otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="b9b02-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="b9b02-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="b9b02-598">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="b9b02-599">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-599">Allowed From</span></span>

<span data-ttu-id="b9b02-600">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-601">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-602">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-602">See Also</span></span>

- <span data-ttu-id="b9b02-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-605">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-606">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-607">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-608">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-611">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-616">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-619">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="b9b02-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="b9b02-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="b9b02-624">Przywraca poprzednią ścieżkę lokalną</span><span class="sxs-lookup"><span data-stu-id="b9b02-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-625">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="b9b02-626">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-626">Description</span></span>

<span data-ttu-id="b9b02-627">Ta usługa przywraca wcześniej ustawioną ścieżkę lokalną.</span><span class="sxs-lookup"><span data-stu-id="b9b02-627">This service restores a previously set local path.</span></span> <span data-ttu-id="b9b02-628">Przywracana jest również pozycja wyszukiwania katalogu w tej ścieżce lokalnej, co sprawia, że ta procedura jest przydatna w cyklicznych przechodzeniach katalogów przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="b9b02-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-629">*Każda ścieżka lokalna zawiera ciąg ścieżki lokalnej **o FX_MAXIMUM_PATH** rozmiarze, który domyślnie ma 256 znaków. Ten wewnętrzny ciąg ścieżki nie jest używany przez plik FileX i jest dostarczany tylko do użytku przez aplikację. Jeśli **FX_LOCAL_PATH** zostanie zadeklarowana jako zmienna lokalna, użytkownicy powinni uważać na wzrost stosu o rozmiarze tej struktury. Użytkownicy mogą zmniejszyć rozmiar biblioteki FX_MAXIMUM_PATH **ponownie** skompilować źródło biblioteki FileX.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-630">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-630">Input Parameters</span></span>

- <span data-ttu-id="b9b02-631">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-632">**local_path_ptr:** Wskaźnik do wcześniej ustawionej ścieżki lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="b9b02-633">Bardzo ważne jest, aby upewnić się, że ten wskaźnik rzeczywiście wskazuje wcześniej używaną i nadal nienaruszoną ścieżkę lokalną.</span><span class="sxs-lookup"><span data-stu-id="b9b02-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-634">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-634">Return Values</span></span>

- <span data-ttu-id="b9b02-635">**FX_SUCCESS** (0x00) Pomyślne przywracanie ścieżki lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="b9b02-636">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="b9b02-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="b9b02-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="b9b02-638">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik ścieżki nośnika lub ścieżki lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-639">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-639">Allowed From</span></span>

<span data-ttu-id="b9b02-640">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-641">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-642">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-642">See Also</span></span>

- <span data-ttu-id="b9b02-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-645">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-646">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-647">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-648">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-651">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-656">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-659">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="b9b02-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="b9b02-664">Konfiguruje ścieżkę lokalną specyficzną dla wątku</span><span class="sxs-lookup"><span data-stu-id="b9b02-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-665">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-666">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-666">Description</span></span>

<span data-ttu-id="b9b02-667">Ta usługa konfiguruje ścieżkę specyficzną dla wątku określoną przez \*\*\*\*\* new_path_string _.</span><span class="sxs-lookup"><span data-stu-id="b9b02-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="b9b02-668">Po pomyślnym zakończeniu tej procedury informacje o ścieżce lokalnej przechowywane w _ *_local_path_ptr_*\* będą miały pierwszeństwo przed globalną ścieżką nośnika dla wszystkich operacji na plikach i katalogach wykonywanych przez ten wątek.</span><span class="sxs-lookup"><span data-stu-id="b9b02-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="b9b02-669">Nie będzie to miało wpływu na żaden inny wątek w systemie</span><span class="sxs-lookup"><span data-stu-id="b9b02-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="b9b02-670">*Domyślny rozmiar ciągu ścieżki lokalnej to 256 znaków. Można go zmienić, **modyfikując** FX_MAXIMUM_PATH w pliku **fx_api.h** i ponownie przebudowując całą bibliotekę FileX. Ścieżka ciągu znaków jest utrzymywana dla aplikacji i nie jest używana wewnętrznie przez plik FileX.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-671">*W przypadku nazw dostarczonych przez aplikację plik FileX obsługuje zarówno ukośnik odwrotny ( ), jak i ukośnik (/) do oddzielnych \\ katalogów, podkatalogów i nazw plików. Jednak plik FileX używa znaku ukośnika odwrotnego tylko w ścieżkach zwracanych do aplikacji.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-672">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-672">Input Parameters</span></span>

- <span data-ttu-id="b9b02-673">**media_ptr:** Wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="b9b02-674">**local_path_ptr:** miejsce docelowe do przechowywania informacji o ścieżce lokalnej specyficznej dla wątku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="b9b02-675">Adres tej struktury może zostać podany w funkcji przywracania ścieżki lokalnej w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="b9b02-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="b9b02-676">**new_path_name:** określa ścieżkę lokalną do instalacji.</span><span class="sxs-lookup"><span data-stu-id="b9b02-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-677">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-677">Return Values</span></span>

- <span data-ttu-id="b9b02-678">**FX_SUCCESS** (0x00) Zestaw katalogów domyślnych powodzenie.</span><span class="sxs-lookup"><span data-stu-id="b9b02-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="b9b02-679">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="b9b02-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="b9b02-681">**FX_INVALID_PATH** (0x0D) Nie można odnaleźć nowego katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="b9b02-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="b9b02-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="b9b02-683">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik ścieżki nośnika lub ścieżki lokalnej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-684">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-684">Allowed From</span></span>

<span data-ttu-id="b9b02-685">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-686">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-686">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a><span data-ttu-id="b9b02-687">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-687">See Also</span></span>

- <span data-ttu-id="b9b02-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-690">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-691">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-692">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-693">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-696">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-701">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-704">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="b9b02-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="b9b02-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="b9b02-709">Pobiera długą nazwę z krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="b9b02-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-710">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-711">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-711">Description</span></span>

<span data-ttu-id="b9b02-712">Ta usługa pobiera długą nazwę (jeśli jest) skojarzoną z podaną krótką nazwą (w formacie 8.3).</span><span class="sxs-lookup"><span data-stu-id="b9b02-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="b9b02-713">Krótka nazwa może być nazwą pliku lub nazwą katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-714">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-714">Input Parameters</span></span>

- <span data-ttu-id="b9b02-715">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-716">**short_name:** Wskaźnik do krótkiej nazwy źródła (format 8.3).</span><span class="sxs-lookup"><span data-stu-id="b9b02-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="b9b02-717">**long_name:** Wskaźnik do miejsca docelowego dla długiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="b9b02-718">Jeśli nie ma długiej nazwy, zwracana jest krótka nazwa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="b9b02-719">Należy pamiętać, że miejsce docelowe długiej nazwy musi być wystarczająco duże, aby FX_MAX_LONG_NAME_LEN znaków.</span><span class="sxs-lookup"><span data-stu-id="b9b02-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-720">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-720">Return Values</span></span>

- <span data-ttu-id="b9b02-721">**FX_SUCCESS** (0x00) Pomyślne długie uzyskiwanie nazwy</span><span class="sxs-lookup"><span data-stu-id="b9b02-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="b9b02-722">**FX_NOT_FOUND** (0x04) Nie znaleziono krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="b9b02-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="b9b02-723">**FX_IO_ERROR** (0x90) Sterownik We/Wy</span><span class="sxs-lookup"><span data-stu-id="b9b02-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="b9b02-724">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="b9b02-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="b9b02-725">**FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-726">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="b9b02-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="b9b02-727">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT</span><span class="sxs-lookup"><span data-stu-id="b9b02-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="b9b02-728">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-729">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub nazwy</span><span class="sxs-lookup"><span data-stu-id="b9b02-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="b9b02-730">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem</span><span class="sxs-lookup"><span data-stu-id="b9b02-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-731">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-731">Allowed From</span></span>

<span data-ttu-id="b9b02-732">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-733">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-734">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-734">See Also</span></span>

- <span data-ttu-id="b9b02-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-737">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-738">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-739">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-740">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-743">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-748">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-751">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="b9b02-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="b9b02-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="b9b02-756">Pobiera długą nazwę z krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="b9b02-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-757">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="b9b02-758">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-758">Description</span></span>

<span data-ttu-id="b9b02-759">Ta usługa pobiera długą nazwę (jeśli jest) skojarzoną z podaną krótką nazwą (w formacie 8.3).</span><span class="sxs-lookup"><span data-stu-id="b9b02-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="b9b02-760">Krótka nazwa może być nazwą pliku lub nazwą katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-761">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-761">Input Parameters</span></span>

- <span data-ttu-id="b9b02-762">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-763">**short_name:** Wskaźnik do krótkiej nazwy źródła (format 8.3).</span><span class="sxs-lookup"><span data-stu-id="b9b02-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="b9b02-764">**long_name:** Wskaźnik do miejsca docelowego dla długiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="b9b02-765">Jeśli nie ma długiej nazwy, zwracana jest krótka nazwa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="b9b02-766">Uwaga: miejsce docelowe długiej nazwy musi być wystarczająco duże, aby **FX_MAX_LONG_NAME_LEN** znaków.</span><span class="sxs-lookup"><span data-stu-id="b9b02-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="b9b02-767">**long_file_name_buffer_length:** długość buforu długich nazw.</span><span class="sxs-lookup"><span data-stu-id="b9b02-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-768">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-768">Return Values</span></span>

- <span data-ttu-id="b9b02-769">**FX_SUCCESS** (0x00) Długi czas uzyskania pomyślnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="b9b02-770">**FX_NOT_FOUND** (0x04) Nie znaleziono krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="b9b02-771">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-772">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="b9b02-773">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-774">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-775">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-776">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="b9b02-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="b9b02-777">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="b9b02-778">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-779">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-779">Allowed From</span></span>

<span data-ttu-id="b9b02-780">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-781">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name, sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-782">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-782">See Also</span></span>

- <span data-ttu-id="b9b02-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-785">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-786">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-787">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-788">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-791">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-799">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="b9b02-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-803">fx_directory_name_test</span></span>

<span data-ttu-id="b9b02-804">Testy katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-805">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-806">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-806">Description</span></span>

<span data-ttu-id="b9b02-807">Ta usługa sprawdza, czy podana nazwa jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="b9b02-808">Jeśli tak, zostanie FX_SUCCESS zwracana.</span><span class="sxs-lookup"><span data-stu-id="b9b02-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-809">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-809">Input Parameters</span></span>

- <span data-ttu-id="b9b02-810">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-811">**directory_name:** wskaźnik do nazwy wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-812">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-812">Return Values</span></span>

- <span data-ttu-id="b9b02-813">**FX_SUCCESS** (0x00) Nazwa jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="b9b02-814">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="b9b02-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="b9b02-815">**FX_NOT_FOUND** (0x04) Nie można odnaleźć wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="b9b02-816">**FX_NOT_DIRECTORY** (0x0E) Entry nie jest katalogiem</span><span class="sxs-lookup"><span data-stu-id="b9b02-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="b9b02-817">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-818">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="b9b02-819">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-820">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-821">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-822">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="b9b02-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="b9b02-823">**FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="b9b02-824">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-825">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-825">Allowed From</span></span>

<span data-ttu-id="b9b02-826">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-827">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-828">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-828">See Also</span></span>

- <span data-ttu-id="b9b02-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-831">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-832">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-833">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-834">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-837">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-845">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="b9b02-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="b9b02-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="b9b02-849">Przejmuje następny wpis katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-850">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-851">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-851">Description</span></span>

<span data-ttu-id="b9b02-852">Ta usługa zwraca nazwę następnego wpisu w bieżącym katalogu domyślnym.</span><span class="sxs-lookup"><span data-stu-id="b9b02-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-853">*Jeśli używasz ścieżki innej niż lokalna, ważne jest również, aby uniemożliwić innym wątkom aplikacji zmianę tego katalogu (przy użyciu semafora ThreadX lub poziomu priorytetu wątku) podczas przechodzenia do katalogu. W przeciwnym razie można uzyskać nieprawidłowe wyniki.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-854">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-854">Input Parameters</span></span>

- <span data-ttu-id="b9b02-855">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-856">**return_entry_name:** wskaźnik do miejsca docelowego dla następnej nazwy wpisu w katalogu domyślnym.</span><span class="sxs-lookup"><span data-stu-id="b9b02-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="b9b02-857">Bufor, do który wskazuje ten wskaźnik, musi być wystarczająco duży, aby pomieścić maksymalny rozmiar nazwy FileX zdefiniowany przez FX_MAX_LONG_NAME_LEN **_._**</span><span class="sxs-lookup"><span data-stu-id="b9b02-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-858">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-858">Return Values</span></span>

- <span data-ttu-id="b9b02-859">**FX_SUCCESS** (0x00) Pomyślne następne wyszukiwanie wpisu</span><span class="sxs-lookup"><span data-stu-id="b9b02-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="b9b02-860">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-861">**FX_NO_MORE_ENTRIES** (0x0F) Nie ma więcej wpisów w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="b9b02-862">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-863">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-864">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-865">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-866">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-867">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-868">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-869">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-869">Allowed From</span></span>

<span data-ttu-id="b9b02-870">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-871">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-872">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-872">See Also</span></span>

- <span data-ttu-id="b9b02-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-875">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-876">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-877">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-878">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-881">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-887">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-889">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="b9b02-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="b9b02-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="b9b02-894">Pobiera wpis następnego katalogu z pełnymi informacjami</span><span class="sxs-lookup"><span data-stu-id="b9b02-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-895">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-895">Prototype</span></span>

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="b9b02-896">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-896">Description</span></span>

<span data-ttu-id="b9b02-897">Ta usługa pobiera nazwę następnego wpisu w katalogu domyślnym i kopiuje ją do określonego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="b9b02-898">Zwraca również pełne informacje o wpisie określone przez dodatkowe parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b9b02-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-899">*Określone miejsce docelowe musi być wystarczająco duże, aby pomieścić maksymalną nazwę FileX o maksymalnym rozmiarze, zgodnie z definicją za pomocą wartości ,FX_MAX_LONG_NAME_LEN*\*\*</span><span class="sxs-lookup"><span data-stu-id="b9b02-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-900">*Jeśli używasz ścieżki innej niż lokalna, ważne jest, aby uniemożliwić innym wątkom aplikacji zmianę tego katalogu (ze zmianą poziomu semafora, mutexu lub priorytetu ThreadX) przez inne wątki aplikacji podczas przechodzenia do katalogu. W przeciwnym razie można uzyskać nieprawidłowe wyniki.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-901">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-901">Input Parameters</span></span>

- <span data-ttu-id="b9b02-902">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-903">**directory_name:** wskaźnik do miejsca docelowego dla nazwy wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="b9b02-904">Musi być co najmniej tak duży, **jak FX_MAX_LONG_NAME_LEN**.</span><span class="sxs-lookup"><span data-stu-id="b9b02-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="b9b02-905">**atrybuty:** jeśli wartość nie ma wartości null, wskaźnik do miejsca docelowego dla atrybutów wpisu do umieszczenia. Atrybuty są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:</span><span class="sxs-lookup"><span data-stu-id="b9b02-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="b9b02-906">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="b9b02-907">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="b9b02-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="b9b02-908">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="b9b02-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="b9b02-909">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="b9b02-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="b9b02-910">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="b9b02-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="b9b02-911">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="b9b02-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="b9b02-912">**size:** jeśli wartość nie ma wartości null, wskaźnik do miejsca docelowego dla rozmiaru wpisu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="b9b02-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="b9b02-913">**month:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla miesiąca modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="b9b02-914">**year:** Jeśli wartość nie ma wartości null, wskaźnik do miejsca docelowego dla roku modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="b9b02-915">**day:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla daty modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="b9b02-916">**hour:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla godziny modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="b9b02-917">**minute:** jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla minuty modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="b9b02-918">**second:** Jeśli wartość jest niezerowa, wskaźnik do miejsca docelowego dla drugiej modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-919">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-919">Return Values</span></span>

- <span data-ttu-id="b9b02-920">**FX_SUCCESS** (0x00) Znajdź następny wpis w katalogu Successful.</span><span class="sxs-lookup"><span data-stu-id="b9b02-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="b9b02-921">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-922">**FX_NO_MORE_ENTRIES** (0x0F) Nie ma więcej wpisów w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="b9b02-923">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-924">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-925">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-926">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-927">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="b9b02-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="b9b02-928">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="b9b02-929">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub wszystkie parametry wejściowe mają wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="b9b02-930">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-931">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-931">Allowed From</span></span>

<span data-ttu-id="b9b02-932">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-933">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-933">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-934">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-934">See Also</span></span>

- <span data-ttu-id="b9b02-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-937">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-938">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-939">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-940">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-943">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-949">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-951">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="b9b02-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-955">fx_directory_rename</span></span>

<span data-ttu-id="b9b02-956">Zmienia nazwę katalogu</span><span class="sxs-lookup"><span data-stu-id="b9b02-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-957">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-958">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-958">Description</span></span>

<span data-ttu-id="b9b02-959">Ta usługa zmienia nazwę katalogu na określoną nową nazwę katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="b9b02-960">Zmiana nazwy jest również wykonywana względem określonej ścieżki lub ścieżki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="b9b02-961">Jeśli ścieżka jest określona w nowej nazwie katalogu, nazwa katalogu zostanie skutecznie przeniesiona do określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b9b02-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="b9b02-962">Jeśli ścieżka nie jest określona, zmieniono nazwę katalogu jest umieszczana w bieżącej ścieżce domyślnej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-963">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-963">Input Parameters</span></span>

- <span data-ttu-id="b9b02-964">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-965">**old_directory_name:** Wskaźnik do bieżącej nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="b9b02-966">**new_directory_name:** Wskaźnik do nowej nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-967">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-967">Return Values</span></span>

- <span data-ttu-id="b9b02-968">**FX_SUCCESS** (0x00) Pomyślna zmiana nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="b9b02-969">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-970">**FX_NOT_FOUND** (0x04) Nie można odnaleźć wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="b9b02-971">**FX_NOT_DIRECTORY** (0x0E) Entry nie jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="b9b02-972">**FX_INVALID_NAME** (0x0C) Nazwa nowego katalogu jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="b9b02-973">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-974">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-975">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-976">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-977">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-978">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="b9b02-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="b9b02-979">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="b9b02-980">**FX_NO_MORE_ENTRIES** (0x0F) Nie ma więcej wpisów w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="b9b02-981">**FX_INVALID_PATH** (0x0D) Nieprawidłowa ścieżka dostarczona z nazwą katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="b9b02-982">**FX_ALREADY_CREATED** (0x0B) Określony katalog został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="b9b02-983">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-984">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-985">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-985">Allowed From</span></span>

<span data-ttu-id="b9b02-986">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-987">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-988">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-988">See Also</span></span>

- <span data-ttu-id="b9b02-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-991">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-992">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-993">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-994">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-997">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="b9b02-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="b9b02-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="b9b02-1010">Pobiera krótką nazwę z długiej nazwy</span><span class="sxs-lookup"><span data-stu-id="b9b02-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1011">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-1012">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1012">Description</span></span>

<span data-ttu-id="b9b02-1013">Ta usługa pobiera krótką nazwę (format 8.3) skojarzoną z podaną długą nazwą.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="b9b02-1014">Długa nazwa może być nazwą pliku lub nazwą katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1015">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1015">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1016">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-1017">**long_name:** Wskaźnik do długiej nazwy źródła.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="b9b02-1018">**short_name:** Wskaźnik do docelowej krótkiej nazwy (format 8.3).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="b9b02-1019">Należy pamiętać, że miejsce docelowe krótkiej nazwy musi być wystarczająco duże, aby pomieścić 14 znaków.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1020">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1020">Return Values</span></span>

- <span data-ttu-id="b9b02-1021">**FX_SUCCESS** (0x00) Pomyślne uzyskiwanie krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="b9b02-1022">**FX_NOT_FOUND** (0x04) Nie znaleziono długiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="b9b02-1023">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1024">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-1025">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1026">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1027">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1028">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-1029">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="b9b02-1030">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="b9b02-1031">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1032">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1032">Allowed From</span></span>

<span data-ttu-id="b9b02-1033">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1034">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1035">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1035">See Also</span></span>

- <span data-ttu-id="b9b02-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1038">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1041">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1053">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="b9b02-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="b9b02-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="b9b02-1057">Pobiera krótką nazwę z długiej nazwy</span><span class="sxs-lookup"><span data-stu-id="b9b02-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1058">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="b9b02-1059">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1059">Description</span></span>

<span data-ttu-id="b9b02-1060">Ta usługa pobiera krótką nazwę (format 8.3) skojarzoną z podaną długą nazwą.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="b9b02-1061">Długa nazwa może być nazwą pliku lub nazwą katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1062">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1062">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1063">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-1064">**long_name:** Wskaźnik do długiej nazwy źródła.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="b9b02-1065">**short_name:** Wskaźnik do docelowej krótkiej nazwy (format 8.3).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="b9b02-1066">Uwaga: miejsce docelowe krótkiej nazwy musi być wystarczająco duże, aby pomieścić 14 znaków.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="b9b02-1067">**short_file_name_length:** długość buforu krótkich nazw.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1068">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1068">Return Values</span></span>

- <span data-ttu-id="b9b02-1069">**FX_SUCCESS** (0x00) Pomyślne uzyskiwanie krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="b9b02-1070">**FX_NOT_FOUND** (0x04) Nie znaleziono długiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="b9b02-1071">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1072">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-1073">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1074">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1075">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1076">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-1077">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="b9b02-1078">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="b9b02-1079">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1080">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1080">Allowed From</span></span>

<span data-ttu-id="b9b02-1081">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1082">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1083">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1083">See Also</span></span>

- <span data-ttu-id="b9b02-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1086">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1089">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1101">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="b9b02-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="b9b02-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="b9b02-1105">Włącza usługę tolerancji błędów</span><span class="sxs-lookup"><span data-stu-id="b9b02-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1106">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="b9b02-1107">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1107">Description</span></span>

<span data-ttu-id="b9b02-1108">Ta usługa włącza moduł odporności na uszkodzenia.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="b9b02-1109">Po uruchomieniu moduł odporności na uszkodzenia wykrywa, czy system plików jest w ramach ochrony przed uszkodzeniami w pliku FileX.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="b9b02-1110">Jeśli tak nie jest, usługa znajduje dostępne sektory w systemie plików do przechowywania dzienników transakcji systemu plików.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="b9b02-1111">Jeśli system plików jest w ramach ochrony przed błędami FileX, stosuje dzienniki do systemu plików, aby zachować jego integralność.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1112">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1112">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1113">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-1114">**memory_ptr:** wskaźnik do bloku pamięci używanego przez moduł odporny na uszkodzenia jako pamięć na początku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="b9b02-1115">**memory_size:** rozmiar pamięci dla plików scratch.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="b9b02-1116">Aby zapewnić odporność na uszkodzenia, rozmiar pamięci na początku musi być co najmniej 3072 bajty i musi być wielokrotnością rozmiaru sektora.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1117">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1117">Return Values</span></span>

- <span data-ttu-id="b9b02-1118">**FX_SUCCESS** (0x00) Pomyślnie włączono tolerancję błędów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="b9b02-1119">**FX_NOT_ENOUGH_MEMORY** (0x91) pamięci jest za mały.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="b9b02-1120">**FX_BOOT_ERROR** (0x01) Błąd sektora rozruchowego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="b9b02-1121">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1122">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z bezpłatnym klastrem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="b9b02-1123">**FX_NO_MORE_SPACE** (0x0A) nośnik skojarzony z tym plikiem nie ma wystarczającej ilości dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="b9b02-1124">**FX_SECTOR_INVALID** (0x89) jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="b9b02-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="b9b02-1125">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1126">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-1127">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1128">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1128">Allowed From</span></span>

<span data-ttu-id="b9b02-1129">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1130">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="b9b02-1131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1131">See Also</span></span>

- <span data-ttu-id="b9b02-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-1132">fx_system_initialize</span></span>
- <span data-ttu-id="b9b02-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-1133">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-1135">fx_media_check</span></span>
- <span data-ttu-id="b9b02-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1136">fx_media_close</span></span>
- <span data-ttu-id="b9b02-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-1140">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-1141">fx_media_format</span></span>
- <span data-ttu-id="b9b02-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1142">fx_media_open</span></span>
- <span data-ttu-id="b9b02-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1144">fx_media_read</span></span>
- <span data-ttu-id="b9b02-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-1145">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="b9b02-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1149">fx_file_allocate</span></span>

<span data-ttu-id="b9b02-1150">Przydziela miejsce dla pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1151">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="b9b02-1152">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1152">Description</span></span>

<span data-ttu-id="b9b02-1153">Ta usługa przydziela i łączy co najmniej jeden ciągły klaster na końcu określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="b9b02-1154">Plik FileX określa wymaganą liczbę klastrów, dzieląc żądany rozmiar przez liczbę bajtów na klaster.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="b9b02-1155">Wynik jest następnie zaokrąglany w górę do następnego całego klastra.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="b9b02-1156">Aby przydzielić miejsce o pojemności spoza 4 GB, aplikacja musi używać usługi *fx_file_extended_allocate*.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1157">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1157">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1158">**file_ptr:** wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="b9b02-1159">**rozmiar:** liczba bajtów do przydzielenia dla pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1160">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1160">Return Values</span></span>

- <span data-ttu-id="b9b02-1161">**FX_SUCCESS** (0x00) Alokacja pliku powiodła się.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="b9b02-1162">**FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="b9b02-1163">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1164">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1165">**FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="b9b02-1166">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z bezpłatnym klastrem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="b9b02-1167">**FX_NO_MORE_SPACE** (0x0A) nośnik skojarzony z tym plikiem nie ma wystarczającej ilości dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="b9b02-1168">**FX_SECTOR_INVALID** (0x89) jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="b9b02-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="b9b02-1169">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1170">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-1171">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-1172">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1173">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1173">Allowed From</span></span>

<span data-ttu-id="b9b02-1174">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1175">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1176">See Also</span></span>

- <span data-ttu-id="b9b02-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1180">fx_file_close— fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="b9b02-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1182">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1189">fx_file_open— fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="b9b02-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1191">fx_file_rename— fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1192">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1194">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="b9b02-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="b9b02-1201">Odczytuje atrybuty pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1202">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="b9b02-1203">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1203">Description</span></span>

<span data-ttu-id="b9b02-1204">Ta usługa odczytuje atrybuty pliku z określonego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1205">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1205">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1206">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-1207">**file_name:** wskaźnik do nazwy żądanego pliku (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="b9b02-1208">**attributes_ptr:** wskaźnik do miejsca docelowego dla atrybutów pliku do umieszczenia.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="b9b02-1209">Atrybuty pliku są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:</span><span class="sxs-lookup"><span data-stu-id="b9b02-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="b9b02-1210">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="b9b02-1211">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="b9b02-1212">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="b9b02-1213">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="b9b02-1214">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="b9b02-1215">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1216">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1216">Return Values</span></span>

- <span data-ttu-id="b9b02-1217">**FX_SUCCESS** (0x00) Pomyślne odczytanie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="b9b02-1218">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-1219">**FX_NOT_FOUND** (0x04) Określony plik nie został znaleziony na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="b9b02-1220">**FX_NOT_A_FILE** (0x05) Określony plik jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="b9b02-1221">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1222">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1223">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-1224">**FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-1225">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1226">**FX_PTR_ERROR** (0x18) Wskaźnik nieprawidłowych nośników lub atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="b9b02-1227">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1228">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1228">Allowed From</span></span>

<span data-ttu-id="b9b02-1229">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1230">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-1231">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1231">See Also</span></span>

- <span data-ttu-id="b9b02-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1232">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1235">fx_file_close— fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="b9b02-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1237">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1244">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1245">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1247">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1248">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1249">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1251">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="b9b02-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="b9b02-1258">Ustawia atrybuty pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1259">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="b9b02-1260">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1260">Description</span></span>

<span data-ttu-id="b9b02-1261">Ta usługa ustawia atrybuty pliku na atrybuty określone przez wywołujący.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-1262">*Aplikacja może modyfikować tylko podzbiór atrybutów pliku za pomocą tej usługi. Każda próba ustawienia dodatkowych atrybutów spowoduje błąd.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1263">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1263">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1264">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-1265">**file_name:** Wskaźnik do nazwy żądanego pliku\*\* (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="b9b02-1266">**atrybuty:** nowe atrybuty dla pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="b9b02-1267">Prawidłowe atrybuty pliku są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b9b02-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="b9b02-1268">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="b9b02-1269">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="b9b02-1270">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="b9b02-1271">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1272">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1272">Return Values</span></span>

- <span data-ttu-id="b9b02-1273">**FX_SUCCESS** (0x00) Zestaw atrybutów Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="b9b02-1274">**FX_ACCESS_ERROR** (0x06) jest otwarty i nie można ustawić jego atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="b9b02-1275">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1276">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1277">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-1278">**FX_NO_MORE_ENTRIES** (0x0F) Brak więcej wpisów w tabeli FAT lub mapie klastra exFAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="b9b02-1279">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="b9b02-1280">**FX_NOT_FOUND** (0x04) Określony plik nie został znaleziony na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="b9b02-1281">**FX_NOT_A_FILE** (0x05) Określony plik jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="b9b02-1282">**FX_SECTOR_INVALID** (0x89) jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="b9b02-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="b9b02-1283">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1284">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-1285">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="b9b02-1286">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-1287">**FX_INVALID_ATTR** (0x19) Wybrane nieprawidłowe atrybuty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="b9b02-1288">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1289">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1289">Allowed From</span></span>

<span data-ttu-id="b9b02-1290">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1291">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-1292">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1292">See Also</span></span>

- <span data-ttu-id="b9b02-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1293">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1296">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1297">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1299">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1306">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1307">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1309">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1310">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1311">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1313">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="b9b02-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="b9b02-1320">Najlepszy sposób przydzielania miejsca dla pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1321">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="b9b02-1322">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1322">Description</span></span>

<span data-ttu-id="b9b02-1323">Ta usługa przydziela i łączy jeden lub więcej ciągłych klastrów na końcu określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="b9b02-1324">FileX określa wymaganą liczbę klastrów, dzieląc żądany rozmiar przez liczbę bajtów na klaster.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="b9b02-1325">Wynik jest następnie zaokrąglany w górę do następnego całego klastra.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="b9b02-1326">Jeśli na nośniku nie ma wystarczającej ilości kolejnych klastrów, ta usługa łączy z plikiem największy dostępny blok kolejnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="b9b02-1327">Ilość miejsca rzeczywiście przydzielonego do pliku jest zwracana do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="b9b02-1328">Aby przydzielić miejsce poza 4 GB, aplikacja musi używać usługi *fx_file_extended_best_effort_allocate*.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1329">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1329">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1330">**file_ptr:** wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="b9b02-1331">**size:** liczba bajtów do przydzielenia dla pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1332">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1332">Return Values</span></span>

- <span data-ttu-id="b9b02-1333">**FX_SUCCESS** (0x00) Pomyślne przydzielanie plików z najlepszymi rozwiązaniami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="b9b02-1334">**FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="b9b02-1335">**FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="b9b02-1336">**FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej ilości dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="b9b02-1337">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1338">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1339">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1340">**FX_NO_MORE_ENTRIES** (0x0F) Nie ma więcej wpisów FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-1341">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1342">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-1343">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku lub miejsce docelowe.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="b9b02-1344">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1345">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1345">Allowed From</span></span>

<span data-ttu-id="b9b02-1346">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1347">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-1348">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1348">See Also</span></span>

- <span data-ttu-id="b9b02-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1349">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1352">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1353">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1355">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1362">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1363">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1365">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1366">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1367">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1369">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="b9b02-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1375">fx_file_close</span></span>

<span data-ttu-id="b9b02-1376">Zamyka plik</span><span class="sxs-lookup"><span data-stu-id="b9b02-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1377">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="b9b02-1378">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1378">Description</span></span>

<span data-ttu-id="b9b02-1379">Ta usługa zamyka określony plik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1379">This service closes the specified file.</span></span> <span data-ttu-id="b9b02-1380">Jeśli plik był otwarty do zapisu, a jeśli został zmodyfikowany, ta usługa kończy proces modyfikacji pliku, aktualizując jego wpis katalogu przy użyciu nowego rozmiaru oraz bieżącej daty i czasu systemowego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1381">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1381">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1382">**file_ptr:** wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1383">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1383">Return Values</span></span>

- <span data-ttu-id="b9b02-1384">**FX_SUCCESS** (0x00) Zamykanie pliku powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="b9b02-1385">**FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="b9b02-1386">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1387">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1388">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1389">**FX_PTR_ERROR** (0x18) Wskaźnik nieprawidłowych nośników lub atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="b9b02-1390">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1391">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1391">Allowed From</span></span>

<span data-ttu-id="b9b02-1392">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1393">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1394">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1394">See Also</span></span>

- <span data-ttu-id="b9b02-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1395">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1399">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1401">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1408">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1409">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1411">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1412">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1413">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1415">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="b9b02-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1421">fx_file_create</span></span>

<span data-ttu-id="b9b02-1422">Tworzy plik</span><span class="sxs-lookup"><span data-stu-id="b9b02-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1423">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="b9b02-1424">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1424">Description</span></span>

<span data-ttu-id="b9b02-1425">Ta usługa tworzy określony plik w katalogu domyślnym lub w ścieżce katalogu dostarczonej z nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-1426">*Ta usługa tworzy plik o zerowej długości, tj. nie przydzielone klastry. Alokacja będzie automatycznie odbywać się przy kolejnych zapisach plików lub może być wykonywana z wyprzedzeniem za pomocą usługi fx_file_allocate lub fx_file_extended_allocate dla miejsca spoza 4 GB).*</span><span class="sxs-lookup"><span data-stu-id="b9b02-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1427">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1427">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1428">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-1429">**file_name:** wskaźnik do nazwy pliku do utworzenia (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1430">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1430">Return Values</span></span>

- <span data-ttu-id="b9b02-1431">**FX_SUCCESS** (0x00) Pomyślne utworzenie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="b9b02-1432">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-1433">**FX_ALREADY_CREATED** (0x0B) Określony plik został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="b9b02-1434">**FX_NO_MORE_SPACE** (0x0A) W katalogu głównym nie ma już żadnych wpisów lub nie ma więcej dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="b9b02-1435">**FX_INVALID_PATH** (0x0D) Nieprawidłowa ścieżka dostarczona z nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="b9b02-1436">**FX_INVALID_NAME** (0x0C) Nazwa pliku jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="b9b02-1437">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1438">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1439">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1440">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-1441">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-1442">**FX_MEDIA_INVALID** (0x02)Nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="b9b02-1443">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1444">**FX_WRITE_PROTECT** (0x23) Nośniki bazowe są chronione przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="b9b02-1445">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nazwy nośnika lub pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="b9b02-1446">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1447">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1447">Allowed From</span></span>

<span data-ttu-id="b9b02-1448">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1449">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1450">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1450">See Also</span></span>
- <span data-ttu-id="b9b02-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1451">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1455">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1457">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1464">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1465">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1467">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1468">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1469">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1471">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="b9b02-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="b9b02-1478">Ustawia datę i godzina pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1478">Sets file date and time</span></span>

<span data-ttu-id="b9b02-1479">Ustawianie daty i czasu pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1480">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1480">Prototype</span></span>

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a><span data-ttu-id="b9b02-1481">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1481">Description</span></span>

<span data-ttu-id="b9b02-1482">Ta usługa ustawia datę i czas określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1483">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1483">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1484">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-1485">**file_name:** wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="b9b02-1486">**year**: wartość roku (1980–2107 włącznie).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="b9b02-1487">**month:** wartość miesiąca (od 1 do 12 włącznie).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="b9b02-1488">**day:** wartość dnia (od 1 do 31 włącznie).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="b9b02-1489">**hour**: wartość godziny (0–23 włącznie).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="b9b02-1490">**minute:** wartość minuty (0–59 włącznie).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="b9b02-1491">**second:** wartość sekundy (0–59 włącznie).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1492">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1492">Return Values</span></span>

- <span data-ttu-id="b9b02-1493">**FX_SUCCESS** (0x00) Data/godzina pomyślnego zakończenia.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="b9b02-1494">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-1495">**FX_NOT_FOUND** (0x04) Nie znaleziono pliku .</span><span class="sxs-lookup"><span data-stu-id="b9b02-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="b9b02-1496">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1497">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1498">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1499">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-1500">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="b9b02-1501">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1502">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-1503">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="b9b02-1504">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="b9b02-1505">**FX_INVALID_YEAR** (0x12) Rok jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="b9b02-1506">**FX_INVALID_MONTH** (0x13) Month (Miesiąc) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="b9b02-1507">**FX_INVALID_DAY** (0x14) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="b9b02-1508">**FX_INVALID_HOUR** (0x15) Godzina jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="b9b02-1509">**FX_INVALID_MINUTE** (0x16) Minuta jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="b9b02-1510">**FX_INVALID_SECOND** (0x17) Sekunda jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1511">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1511">Allowed From</span></span>

<span data-ttu-id="b9b02-1512">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1513">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1514">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1514">See Also</span></span>

- <span data-ttu-id="b9b02-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1515">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1519">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1520">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1521">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1528">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1529">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1531">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1532">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1533">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1535">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="b9b02-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="b9b02-1542">Usuwa plik</span><span class="sxs-lookup"><span data-stu-id="b9b02-1542">Deletes file</span></span>

<span data-ttu-id="b9b02-1543">Usuwanie pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1544">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="b9b02-1545">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1545">Description</span></span>

<span data-ttu-id="b9b02-1546">Ta usługa usuwa określony plik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="b9b02-1547">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1547">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1548">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-1549">**file_name:** wskaźnik do nazwy pliku do usunięcia (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1550">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1550">Return Values</span></span>

- <span data-ttu-id="b9b02-1551">**FX_SUCCESS** (0x00) Pomyślne usunięcie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="b9b02-1552">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-1553">**FX_NOT_FOUND** (0x04) Nie znaleziono określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="b9b02-1554">**FX_NOT_A_FILE** (0x05) Określona nazwa pliku to katalog lub wolumin.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="b9b02-1555">**FX_ACCESS_ERROR** (0x06) Określony plik jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="b9b02-1556">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1557">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1558">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1559">**FX_NO_MORE_ENTRIES** (0x0F) Nie ma więcej wpisów FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-1560">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-1561">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1562">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-1563">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="b9b02-1564">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-1565">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1566">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1566">Allowed From</span></span>

<span data-ttu-id="b9b02-1567">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1568">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1569">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1569">See Also</span></span>

- <span data-ttu-id="b9b02-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1570">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1574">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1575">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1583">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1584">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1586">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1587">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1588">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1590">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="b9b02-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="b9b02-1597">Przydziela miejsce dla pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1598">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="b9b02-1599">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1599">Description</span></span>

<span data-ttu-id="b9b02-1600">Ta usługa przydziela i łączy jeden lub więcej ciągłych klastrów na końcu określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="b9b02-1601">Plik FileX określa wymaganą liczbę klastrów, dzieląc żądany rozmiar przez liczbę bajtów na klaster.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="b9b02-1602">Wynik jest następnie zaokrąglany w górę do następnego całego klastra.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="b9b02-1603">Ta usługa jest przeznaczona dla usługi exFAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="b9b02-1604">Parametr *size* przyjmuje 64-bitową wartość całkowitą, co umożliwia funkcji wywołującej wstępne przydzielenie miejsca poza zakresem 4 GB.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1605">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1605">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1606">**file_ptr:** wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="b9b02-1607">**rozmiar:** liczba bajtów do przydzielenia dla pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1608">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1608">Return Values</span></span>

- <span data-ttu-id="b9b02-1609">**FX_SUCCESS** (0x00) Alokacja pliku powiodła się.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="b9b02-1610">**FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="b9b02-1611">**FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="b9b02-1612">**FX_NO_MORE_SPACE** (0x0A) nośnik skojarzony z tym plikiem nie ma wystarczającej ilości dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="b9b02-1613">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1614">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1615">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1616">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-1617">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1618">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-1619">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-1620">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1621">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1621">Allowed From</span></span>

<span data-ttu-id="b9b02-1622">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1623">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1624">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1624">See Also</span></span>

- <span data-ttu-id="b9b02-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1625">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1629">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1630">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1632">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1638">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1639">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1641">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1642">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1643">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1645">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="b9b02-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="b9b02-1652">Najlepszy sposób przydzielania miejsca dla pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1653">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="b9b02-1654">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1654">Description</span></span>

<span data-ttu-id="b9b02-1655">Ta usługa przydziela i łączy co najmniej jeden ciągły klaster na końcu określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="b9b02-1656">Plik FileX określa wymaganą liczbę klastrów, dzieląc żądany rozmiar przez liczbę bajtów na klaster.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="b9b02-1657">Wynik jest następnie zaokrąglany w górę do następnego całego klastra.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="b9b02-1658">Jeśli na nośniku nie ma wystarczającej ilości kolejnych klastrów, ta usługa łączy z plikiem największy dostępny blok kolejnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="b9b02-1659">Ilość miejsca rzeczywiście przydzielonego do pliku jest zwracana do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="b9b02-1660">Ta usługa jest przeznaczona dla usługi exFAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="b9b02-1661">Parametr *size* przyjmuje 64-bitową wartość całkowitą, co umożliwia funkcji wywołującej wstępne przydzielenie miejsca poza zakresem 4 GB.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1662">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1662">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1663">**file_ptr:** wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="b9b02-1664">**rozmiar:** liczba bajtów do przydzielenia dla pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1665">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1665">Return Values</span></span>

- <span data-ttu-id="b9b02-1666">**FX_SUCCESS** (0x00) Alokacja pliku powiodła się.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="b9b02-1667">**FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="b9b02-1668">**FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="b9b02-1669">**FX_NO_MORE_SPACE** (0x0A) nośnik skojarzony z tym plikiem nie ma wystarczającej ilości dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="b9b02-1670">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1671">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1672">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1673">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-1674">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1675">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-1676">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-1677">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1678">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1678">Allowed From</span></span>

<span data-ttu-id="b9b02-1679">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1680">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1680">Example</span></span>

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1681">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1681">See Also</span></span>

- <span data-ttu-id="b9b02-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1682">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1686">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1687">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1689">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1695">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1696">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1698">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1699">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1700">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1702">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="b9b02-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="b9b02-1709">Pozycje względnego przesunięcia bajtowego</span><span class="sxs-lookup"><span data-stu-id="b9b02-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1710">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="b9b02-1711">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1711">Description</span></span>

<span data-ttu-id="b9b02-1712">Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego względnego przesunięcia bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="b9b02-1713">Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="b9b02-1714">Ta usługa jest przeznaczona dla usługi exFAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="b9b02-1715">Parametr *byte_offset* przyjmuje 64-bitową wartość całkowitą, co pozwala funkcji wywołującej zmienić położenie wskaźnika odczytu/zapisu poza zakres 4 GB.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-1716">*Jeśli operacja seek próbuje pominąć koniec pliku, wskaźnik odczytu/zapisu pliku jest umieszczony na końcu pliku. I odwrotnie, jeśli operacja seek próbuje umieścić się na początku pliku, wskaźnik odczytu/zapisu pliku jest umieszczony na początku pliku.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1717">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1717">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1718">**file_ptr:** wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="b9b02-1719">**byte_offset:** żądane względne przesunięcie bajtów w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="b9b02-1720">**seek_from:** kierunek i lokalizacja miejsca, z którego ma być przeprowadzane względne szukanie.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="b9b02-1721">Prawidłowe opcje wyszukiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b9b02-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="b9b02-1722">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="b9b02-1723">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="b9b02-1724">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="b9b02-1725">FX_SEEK_BACK (0x03) Jeśli FX_SEEK_BEGIN, operacja szukania jest wykonywana od początku pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="b9b02-1726">Jeśli FX_SEEK_END określono, operacja szukania jest wykonywana wstecz od końca pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="b9b02-1727">Jeśli FX_SEEK_FORWARD określono, operacja szukania jest wykonywana od bieżącej pozycji pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="b9b02-1728">Jeśli FX_SEEK_BACK określono, operacja szukania jest wykonywana wstecz od bieżącej pozycji pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1729">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1729">Return Values</span></span>

- <span data-ttu-id="b9b02-1730">**FX_SUCCESS** (0x00) Udane względne szukanie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="b9b02-1731">**FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="b9b02-1732">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1733">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1734">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-1735">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1736">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-1737">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1738">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1738">Allowed From</span></span>

<span data-ttu-id="b9b02-1739">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1740">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1741">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1741">See Also</span></span>

- <span data-ttu-id="b9b02-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1742">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1746">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1747">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1749">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1755">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1756">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1758">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1759">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1760">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1762">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="b9b02-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="b9b02-1769">Pozycje do przesunięcia bajtowego</span><span class="sxs-lookup"><span data-stu-id="b9b02-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1770">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="b9b02-1771">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1771">Description</span></span>

<span data-ttu-id="b9b02-1772">Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego przesunięcia bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="b9b02-1773">Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="b9b02-1774">Ta usługa jest przeznaczona dla usługi exFAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="b9b02-1775">Parametr *byte_offset* przyjmuje 64-bitową wartość całkowitą, co pozwala funkcji wywołującej zmienić położenie wskaźnika odczytu/zapisu poza zakres 4 GB.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1776">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1776">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1777">**file_ptr:** wskaźnik do bloku sterowania plikami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="b9b02-1778">**byte_offset:** przesunięcie żądanego bajtu w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="b9b02-1779">Wartość zero spowoduje położenie wskaźnika odczytu/zapisu na początku pliku, podczas gdy wartość większa niż rozmiar pliku spowoduje położenie wskaźnika odczytu/zapisu na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1780">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1780">Return Values</span></span>

- <span data-ttu-id="b9b02-1781">**FX_SUCCESS** (0x00) Pomyślne szukanie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="b9b02-1782">**FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="b9b02-1783">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1784">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1785">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-1786">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1787">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-1788">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1789">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1789">Allowed From</span></span>

<span data-ttu-id="b9b02-1790">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1791">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1792">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1792">See Also</span></span>

- <span data-ttu-id="b9b02-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1793">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1797">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1798">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1800">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1806">fx_file_open— fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="b9b02-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1808">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1809">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1810">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1812">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="b9b02-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="b9b02-1819">Obcinanie pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1820">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="b9b02-1821">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1821">Description</span></span>

<span data-ttu-id="b9b02-1822">Ta usługa obcina rozmiar pliku do określonego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="b9b02-1823">Jeśli podany rozmiar jest większy niż rzeczywisty rozmiar pliku, ta usługa nie robi niczego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="b9b02-1824">Żaden z klastrów multimediów skojarzonych z plikiem nie jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-1825">*Należy zachować ostrożność przy obcinaniu plików, które również mogą być jednocześnie otwarte do odczytu. Obcinanie pliku również otwartego do odczytu może spowodować odczytanie nieprawidłowych danych.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="b9b02-1826">Ta usługa jest przeznaczona dla usługi exFAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="b9b02-1827">Parametr *size* przyjmuje 64-bitową wartość całkowitą, co umożliwia funkcji wywołującej działanie poza zakresem 4 GB.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1828">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1828">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1829">**file_ptr:** wskaźnik do bloku sterowania plikami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="b9b02-1830">**rozmiar:** nowy rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1830">**size**: New file size.</span></span> <span data-ttu-id="b9b02-1831">Bajty po tym nowym rozmiarze pliku są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1832">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1832">Return Values</span></span>

- <span data-ttu-id="b9b02-1833">**FX_SUCCESS** (0x00) Pomyślne obcinanie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="b9b02-1834">**FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="b9b02-1835">**FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="b9b02-1836">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1837">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1838">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-1839">**FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-1840">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1841">**FX_WRITE_PROTECT** (0x23) Nośniki bazowe są chronione przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="b9b02-1842">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-1843">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1844">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1844">Allowed From</span></span>

<span data-ttu-id="b9b02-1845">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1846">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1847">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1847">See Also</span></span>

- <span data-ttu-id="b9b02-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1848">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1852">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1853">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1855">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1861">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1862">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1864">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1865">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1866">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1868">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="b9b02-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="b9b02-1875">Obcina klastry plików i wydań</span><span class="sxs-lookup"><span data-stu-id="b9b02-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1876">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="b9b02-1877">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1877">Description</span></span>

<span data-ttu-id="b9b02-1878">Ta usługa obcina rozmiar pliku do określonego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="b9b02-1879">Jeśli podany rozmiar jest większy niż rzeczywisty rozmiar pliku, ta usługa nie robi niczego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="b9b02-1880">W przeciwieństwie ***fx_file_extended_truncate*** usługa ta zwalnia wszystkie nieużywane klastry.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-1881">*Należy zachować ostrożność przy obcinaniu plików, które również mogą być jednocześnie otwarte do odczytu. Obcinanie pliku również otwartego do odczytu może spowodować odczytanie nieprawidłowych danych.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="b9b02-1882">Ta usługa jest przeznaczona dla usługi exFAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="b9b02-1883">Parametr *size* przyjmuje 64-bitową wartość całkowitą, co umożliwia funkcji wywołującej działanie poza zakresem 4 GB.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1884">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1884">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1885">**file_ptr:** wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="b9b02-1886">**rozmiar:** nowy rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1886">**size**: New file size.</span></span> <span data-ttu-id="b9b02-1887">Bajty po tym nowym rozmiarze pliku są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1888">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1888">Return Values</span></span>

- <span data-ttu-id="b9b02-1889">**FX_SUCCESS** (0x00) Pomyślne obcinanie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="b9b02-1890">**FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="b9b02-1891">**FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="b9b02-1892">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1893">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-1894">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1895">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-1896">**FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-1897">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1898">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-1899">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-1900">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1901">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1901">Allowed From</span></span>

<span data-ttu-id="b9b02-1902">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1903">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1904">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1904">See Also</span></span>

- <span data-ttu-id="b9b02-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1905">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-1909">fx_file_close</span></span>
- <span data-ttu-id="b9b02-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1910">fx_file_create</span></span>
- <span data-ttu-id="b9b02-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1912">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1918">fx_file_open</span></span>
- <span data-ttu-id="b9b02-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1919">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1921">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1922">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1923">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1925">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="b9b02-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-1931">fx_file_open</span></span>

<span data-ttu-id="b9b02-1932">Otwiera plik</span><span class="sxs-lookup"><span data-stu-id="b9b02-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1933">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="b9b02-1934">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1934">Description</span></span>

<span data-ttu-id="b9b02-1935">Ta usługa otwiera określony plik do odczytu lub zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="b9b02-1936">Plik może być otwierany do wielokrotnego odczytu, a plik do zapisu można otworzyć tylko raz, dopóki autor nie zamknie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-1937">*Należy zadbać o to, aby plik był jednocześnie otwarty do odczytu i zapisu. Zapisywanie plików wykonywane, gdy plik jest jednocześnie otwierany do odczytu, może nie być widoczne dla czytnika, chyba że czytnik zamknie i ponownie otworzy plik do odczytu. Podobnie podczas korzystania z usług obcinania plików należy zachować ostrożność. Jeśli plik zostanie obcięty przez twórcę, czytelnicy tego samego pliku mogą zwrócić nieprawidłowe dane.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-1938">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-1938">Input Parameters</span></span>

- <span data-ttu-id="b9b02-1939">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-1940">**file_ptr:** wskaźnik do bloku sterowania plikami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="b9b02-1941">**file_name:** wskaźnik do nazwy pliku do otwarcia (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="b9b02-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="b9b02-1942">**open_type:** typ otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="b9b02-1943">Prawidłowe opcje typu otwartego to:</span><span class="sxs-lookup"><span data-stu-id="b9b02-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="b9b02-1944">FX_OPEN_FOR_READ (0x00)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="b9b02-1945">FX_OPEN_FOR_WRITE (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="b9b02-1946">FX_OPEN_FOR_READ_FAST (0x02)</span><span class="sxs-lookup"><span data-stu-id="b9b02-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="b9b02-1947">Otwieranie plików z FX_OPEN_FOR_READ i FX_OPEN_FOR_READ_FAST jest podobne:</span><span class="sxs-lookup"><span data-stu-id="b9b02-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="b9b02-1948">FX_OPEN_FOR_READ obejmuje weryfikację, czy połączona lista klastrów, które składają się na plik, jest nienaruszona, FX_OPEN_FOR_READ_FAST nie wykonuje tej weryfikacji, co przyspiesza.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-1949">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-1949">Return Values</span></span>

- <span data-ttu-id="b9b02-1950">**FX_SUCCESS** (0x00) Pomyślnie otwarty plik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="b9b02-1951">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-1952">**FX_NOT_FOUND** (0x04) Nie znaleziono określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="b9b02-1953">**FX_NOT_A_FILE** (0x05) Określona nazwa pliku to katalog lub wolumin.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="b9b02-1954">**FX_FILE_CORRUPT** (0x08) Określony plik jest uszkodzony i otwarcie nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="b9b02-1955">**FX_ACCESS_ERROR** (0x06) Określony plik jest już otwarty lub otwarty typ jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="b9b02-1956">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-1957">**FX_MEDIA_INVALID** (0x02) Nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="b9b02-1958">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-1959">**FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-1960">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-1961">**FX_WRITE_PROTECT** (0x23) Nośniki bazowe są chronione przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="b9b02-1962">**FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="b9b02-1963">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-1964">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-1964">Allowed From</span></span>

<span data-ttu-id="b9b02-1965">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-1966">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-1967">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-1967">See Also</span></span>

- <span data-ttu-id="b9b02-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1968">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1972">fx_file_close— fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="b9b02-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-1974">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1981">fx_file_read</span></span>
- <span data-ttu-id="b9b02-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1983">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-1984">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-1985">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-1987">fx_file_write</span></span>
- <span data-ttu-id="b9b02-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="b9b02-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-1993">fx_file_read</span></span>

<span data-ttu-id="b9b02-1994">Odczytuje bajty z pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-1995">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="b9b02-1996">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-1996">Description</span></span>

<span data-ttu-id="b9b02-1997">Ta usługa odczytuje bajty z pliku i zapisuje je w dostarczonym buforze.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="b9b02-1998">Po zakończeniu odczytu wewnętrzny wskaźnik odczytu pliku jest dostosowywany tak, aby wskazać następny bajt w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="b9b02-1999">Jeśli pozostało mniej bajtów w żądaniu, w buforze są przechowywane tylko pozostałe bajty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="b9b02-2000">W każdym przypadku do wywołującego jest zwracana łączna liczba bajtów umieszczonych w buforze.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2001">*Aplikacja musi upewnić się, że dostarczony bufor może przechowywać określoną liczbę żądanych bajtów.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2002">*Wyższa wydajność jest osiągana, jeśli bufor docelowy znajduje się na granicy długich słów, a żądany rozmiar jest równomiernie podzielny według sizeof(**ULONG**).*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2003">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2003">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2004">**file_ptr:** wskaźnik do bloku sterowania plikami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="b9b02-2005">**buffer_ptr:** Wskaźnik do buforu docelowego dla odczytu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="b9b02-2006">**request_size:** maksymalna liczba bajtów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="b9b02-2007">**actual_size:** Wskaźnik do zmiennej do przechowywania rzeczywistej liczby bajtów odczytanych do podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2008">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2008">Return Values</span></span>

- <span data-ttu-id="b9b02-2009">**FX_SUCCESS** (0x00) Pomyślnie odczytany plik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="b9b02-2010">**FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="b9b02-2011">**FX_FILE_CORRUPT** (0x08) Określony plik jest uszkodzony i odczyt nie powiódł się.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="b9b02-2012">**FX_END_OF_FILE** (0x09) osiągnięto koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="b9b02-2013">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-2014">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-2015">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2016">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku lub buforu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="b9b02-2017">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2018">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2018">Allowed From</span></span>

<span data-ttu-id="b9b02-2019">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2020">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2020">Example</span></span>

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a><span data-ttu-id="b9b02-2021">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2021">See Also</span></span>

- <span data-ttu-id="b9b02-2022">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="b9b02-2023">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="b9b02-2024">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="b9b02-2025">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="b9b02-2026">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2026">fx_file_close,</span></span>
- <span data-ttu-id="b9b02-2027">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2027">fx_file_create,</span></span>
- <span data-ttu-id="b9b02-2028">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="b9b02-2029">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2029">fx_file_delete,</span></span>
- <span data-ttu-id="b9b02-2030">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="b9b02-2031">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="b9b02-2032">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="b9b02-2033">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="b9b02-2034">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="b9b02-2035">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="b9b02-2036">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2036">fx_file_open,</span></span>
- <span data-ttu-id="b9b02-2037">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="b9b02-2038">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2038">fx_file_rename,</span></span>
- <span data-ttu-id="b9b02-2039">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2039">fx_file_seek,</span></span>
- <span data-ttu-id="b9b02-2040">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="b9b02-2041">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="b9b02-2042">fx_file_write,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2042">fx_file_write,</span></span>
- <span data-ttu-id="b9b02-2043">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="b9b02-2044">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="b9b02-2045">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="b9b02-2046">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="b9b02-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="b9b02-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="b9b02-2049">Pozycje względnego przesunięcia bajtowego</span><span class="sxs-lookup"><span data-stu-id="b9b02-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2050">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="b9b02-2051">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2051">Description</span></span>

<span data-ttu-id="b9b02-2052">Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego względnego przesunięcia bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="b9b02-2053">Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-2054">*Jeśli operacja seek próbuje pominąć koniec pliku, wskaźnik odczytu/zapisu pliku jest umieszczony na końcu pliku. I odwrotnie, jeśli operacja seek próbuje umieścić się na początku pliku, wskaźnik odczytu/zapisu pliku jest umieszczony na początku pliku.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="b9b02-2055">Aby poszukać wartości przesunięcia spoza 4 GB, aplikacja musi użyć usługi *fx_file_extended_relative_seek*.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2056">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2056">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2057">**file_ptr:** wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="b9b02-2058">**byte_offset:** żądane względne przesunięcie bajtów w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="b9b02-2059">**seek_from:** kierunek i lokalizacja miejsca, z którego ma być przeprowadzane względne szukanie.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="b9b02-2060">Prawidłowe opcje wyszukiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b9b02-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="b9b02-2061">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="b9b02-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="b9b02-2062">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="b9b02-2063">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="b9b02-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="b9b02-2064">FX_SEEK_BACK (0x03)</span><span class="sxs-lookup"><span data-stu-id="b9b02-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="b9b02-2065">Jeśli FX_SEEK_BEGIN określono wartość , operacja szukania jest wykonywana od początku pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="b9b02-2066">Jeśli FX_SEEK_END określono, operacja szukania jest wykonywana wstecz od końca pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="b9b02-2067">Jeśli FX_SEEK_FORWARD określono, operacja szukania jest wykonywana od bieżącej pozycji pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="b9b02-2068">Jeśli FX_SEEK_BACK określono, operacja szukania jest wykonywana wstecz od bieżącej pozycji pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2069">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2069">Return Values</span></span>

- <span data-ttu-id="b9b02-2070">**FX_SUCCESS** (0x00) Udane względne szukanie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="b9b02-2071">**FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="b9b02-2072">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2073">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-2074">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-2075">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-2076">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-2077">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2078">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2078">Allowed From</span></span>

<span data-ttu-id="b9b02-2079">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2080">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-2081">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2081">See Also</span></span>

- <span data-ttu-id="b9b02-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2082">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2086">fx_file_close</span></span>
- <span data-ttu-id="b9b02-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2087">fx_file_create</span></span>
- <span data-ttu-id="b9b02-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-2089">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2096">fx_file_open</span></span>
- <span data-ttu-id="b9b02-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2097">fx_file_read</span></span>
- <span data-ttu-id="b9b02-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2098">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2099">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2100">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2102">fx_file_write</span></span>
- <span data-ttu-id="b9b02-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="b9b02-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2108">fx_file_rename</span></span>

<span data-ttu-id="b9b02-2109">Zmienia nazwę pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2110">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="b9b02-2111">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2111">Description</span></span>

<span data-ttu-id="b9b02-2112">Ta usługa zmienia nazwę pliku określoną przez old_file_name *.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="b9b02-2113">Zmiana nazwy jest również wykonywana względem określonej ścieżki lub ścieżki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="b9b02-2114">Jeśli ścieżka jest określona w nowej nazwie pliku, plik o zmienionej nazwie jest skutecznie przenoszony do określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="b9b02-2115">Jeśli ścieżka nie zostanie określona, zmieniono nazwę pliku jest umieszczana w bieżącej ścieżce domyślnej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2116">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2116">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2117">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="b9b02-2118">**old_file_name:** wskaźnik do nazwy pliku do zmiany nazwy (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="b9b02-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="b9b02-2119">**new_file_name:** Wskaźnik do nowej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="b9b02-2120">Ścieżka katalogu jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2121">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2121">Return Values</span></span>

- <span data-ttu-id="b9b02-2122">**FX_SUCCESS** (0x00) Pomyślna zmiana nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="b9b02-2123">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-2124">**FX_NOT_FOUND** (0x04) Nie znaleziono określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="b9b02-2125">**FX_NOT_A_FILE** (0x05) Określony plik jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="b9b02-2126">**FX_ACCESS_ERROR** (0x06) Określony plik jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="b9b02-2127">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2128">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-2129">**FX_INVALID_NAME** (0x0C) Określona nazwa nowego pliku nie jest prawidłową nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="b9b02-2130">**FX_INVALID_PATH** (0x0D) jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="b9b02-2131">**FX_ALREADY_CREATED** (0x0B) Używana jest nowa nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="b9b02-2132">**FX_MEDIA_INVALID** (0x02) Nośnik jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="b9b02-2133">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-2134">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-2135">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-2136">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-2137">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać tabeli FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="b9b02-2138">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-2139">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2140">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2140">Allowed From</span></span>

<span data-ttu-id="b9b02-2141">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2142">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-2143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2143">See Also</span></span>

- <span data-ttu-id="b9b02-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2144">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2148">fx_file_close</span></span>
- <span data-ttu-id="b9b02-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2149">fx_file_create</span></span>
- <span data-ttu-id="b9b02-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-2151">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2158">fx_file_open</span></span>
- <span data-ttu-id="b9b02-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2159">fx_file_read</span></span>
- <span data-ttu-id="b9b02-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2161">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2162">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2164">fx_file_write</span></span>
- <span data-ttu-id="b9b02-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="b9b02-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2170">fx_file_seek</span></span>

<span data-ttu-id="b9b02-2171">Pozycje do przesunięcia bajtowego</span><span class="sxs-lookup"><span data-stu-id="b9b02-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2172">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="b9b02-2173">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2173">Description</span></span>

<span data-ttu-id="b9b02-2174">Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego przesunięcia bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="b9b02-2175">Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="b9b02-2176">Aby poszukać wartości przesunięcia spoza 4 GB, aplikacja musi użyć usługi *fx_file_extended_seek*.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2177">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2177">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2178">**file_ptr:** wskaźnik do bloku sterowania plikami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="b9b02-2179">**byte_offset:** przesunięcie żądanego bajtu w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="b9b02-2180">Wartość zero spowoduje położenie wskaźnika odczytu/zapisu na początku pliku, podczas gdy wartość większa niż rozmiar pliku spowoduje położenie wskaźnika odczytu/zapisu na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2181">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2181">Return Values</span></span>

- <span data-ttu-id="b9b02-2182">**FX_SUCCESS** (0x00) Pomyślne szukanie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="b9b02-2183">**FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="b9b02-2184">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2185">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-2186">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-2187">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-2188">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-2189">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2190">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2190">Allowed From</span></span>

<span data-ttu-id="b9b02-2191">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2192">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-2193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2193">See Also</span></span>

- <span data-ttu-id="b9b02-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2194">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2198">fx_file_close</span></span>
- <span data-ttu-id="b9b02-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2199">fx_file_create</span></span>
- <span data-ttu-id="b9b02-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-2201">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2208">fx_file_open</span></span>
- <span data-ttu-id="b9b02-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2209">fx_file_read</span></span>
- <span data-ttu-id="b9b02-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2210">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2211">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2212">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2214">fx_file_write</span></span>
- <span data-ttu-id="b9b02-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="b9b02-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2220">fx_file_truncate</span></span>

<span data-ttu-id="b9b02-2221">Obcinanie pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2222">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="b9b02-2223">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2223">Description</span></span>

<span data-ttu-id="b9b02-2224">Ta usługa obcina rozmiar pliku do określonego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="b9b02-2225">Jeśli podany rozmiar jest większy niż rzeczywisty rozmiar pliku, ta usługa nie robi niczego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="b9b02-2226">Żaden z klastrów multimediów skojarzonych z plikiem nie jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2227">*Należy zachować ostrożność przy obcinaniu plików, które również mogą być jednocześnie otwarte do odczytu. Obcinanie pliku również otwartego do odczytu może spowodować odczytanie nieprawidłowych danych.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="b9b02-2228">Aby działać dłużej niż 4 GB, aplikacja musi korzystać z *usługi* fx_file_extended_truncate .</span><span class="sxs-lookup"><span data-stu-id="b9b02-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2229">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2229">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2230">**file_ptr:** wskaźnik do bloku sterowania plikami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="b9b02-2231">**rozmiar:** nowy rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2231">**size**: New file size.</span></span> <span data-ttu-id="b9b02-2232">Bajty po tym nowym rozmiarze pliku są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2233">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2233">Return Values</span></span>

- <span data-ttu-id="b9b02-2234">**FX_SUCCESS** (0x00) Pomyślne obcinanie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="b9b02-2235">**FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="b9b02-2236">**FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="b9b02-2237">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2238">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-2239">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-2240">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-2241">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-2242">**FX_NO_MORE_SPACE** (0x0A) Brak miejsca na ukończenie operacji</span><span class="sxs-lookup"><span data-stu-id="b9b02-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="b9b02-2243">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-2244">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2245">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2245">Allowed From</span></span>

<span data-ttu-id="b9b02-2246">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2247">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-2248">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2248">See Also</span></span>

- <span data-ttu-id="b9b02-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2249">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2253">fx_file_close</span></span>
- <span data-ttu-id="b9b02-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2254">fx_file_create</span></span>
- <span data-ttu-id="b9b02-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-2256">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2263">fx_file_open</span></span>
- <span data-ttu-id="b9b02-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2264">fx_file_read</span></span>
- <span data-ttu-id="b9b02-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2266">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2267">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2269">fx_file_write</span></span>
- <span data-ttu-id="b9b02-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="b9b02-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="b9b02-2276">Obcina klastry plików i wydań</span><span class="sxs-lookup"><span data-stu-id="b9b02-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2277">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="b9b02-2278">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2278">Description</span></span>

<span data-ttu-id="b9b02-2279">Ta usługa obcina rozmiar pliku do określonego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="b9b02-2280">Jeśli podany rozmiar jest większy niż rzeczywisty rozmiar pliku, ta usługa nie robi niczego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="b9b02-2281">W przeciwieństwie ***fx_file_truncate*** usługa ta zwalnia wszystkie nieużywane klastry.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2282">*Należy zachować ostrożność przy obcinaniu plików, które również mogą być jednocześnie otwarte do odczytu. Obcinanie pliku również otwartego do odczytu może spowodować odczytanie nieprawidłowych danych.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="b9b02-2283">Aby działać dłużej niż 4 GB, aplikacja musi korzystać z *usługi* fx_file_extended_truncate_release .</span><span class="sxs-lookup"><span data-stu-id="b9b02-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2284">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2284">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2285">**file_ptr:** wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="b9b02-2286">**rozmiar:** nowy rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2286">**size**: New file size.</span></span> <span data-ttu-id="b9b02-2287">Bajty po tym nowym rozmiarze pliku są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2288">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2288">Return Values</span></span>

- <span data-ttu-id="b9b02-2289">**FX_SUCCESS** (0x00) Pomyślne obcinanie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="b9b02-2290">**FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="b9b02-2291">**FX_NOT_OPEN** (0x07) Określony plik nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="b9b02-2292">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2293">**FX_WRITE_PROTECT** (0x23) Nośniki bazowe są chronione przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="b9b02-2294">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="b9b02-2295">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-2296">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-2297">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-2298">**FX_NO_MORE_SPACE** (0x0A) Nie ma więcej miejsca na ukończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="b9b02-2299">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="b9b02-2300">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2301">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2301">Allowed From</span></span>

<span data-ttu-id="b9b02-2302">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2303">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="b9b02-2304">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2304">See Also</span></span>

- <span data-ttu-id="b9b02-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2305">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2309">fx_file_close</span></span>
- <span data-ttu-id="b9b02-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2310">fx_file_create</span></span>
- <span data-ttu-id="b9b02-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-2312">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2319">fx_file_open</span></span>
- <span data-ttu-id="b9b02-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2320">fx_file_read</span></span>
- <span data-ttu-id="b9b02-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2322">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2323">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2324">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2325">fx_file_write</span></span>
- <span data-ttu-id="b9b02-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="b9b02-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2331">fx_file_write</span></span>

<span data-ttu-id="b9b02-2332">Zapisuje bajty w pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2333">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="b9b02-2334">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2334">Description</span></span>

<span data-ttu-id="b9b02-2335">Ta usługa zapisuje bajty z określonego buforu, zaczynając od bieżącej pozycji pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="b9b02-2336">Po zakończeniu zapisu wewnętrzny wskaźnik odczytu pliku jest dostosowywany tak, aby wskazać następny bajt w pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2337">*Szybsza wydajność jest osiągana, jeśli bufor źródłowy znajduje się na granicy długich słów, a żądany rozmiar jest równomiernie podzielny według sizeof(**ULONG**).*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2338">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2338">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2339">**file_ptr:** wskaźnik do bloku sterowania plikami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="b9b02-2340">**buffer_ptr:** wskaźnik do buforu źródłowego zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="b9b02-2341">**size:** liczba bajtów do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2342">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2342">Return Values</span></span>

- <span data-ttu-id="b9b02-2343">**FX_SUCCESS** (0x00) Pomyślny zapis pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="b9b02-2344">**FX_NOT_OPEN** (0x07) Określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="b9b02-2345">**FX_ACCESS_ERROR** (0x06) Określony plik nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="b9b02-2346">**FX_NO_MORE_SPACE** (0x0A) Na nośniku nie ma już miejsca na wykonanie tego zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="b9b02-2347">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2348">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-2349">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-2350">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-2351">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać wpisu FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="b9b02-2352">**FX_NO_MORE_ENTRIES** (0x0F) Koniec z wpisami FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="b9b02-2353">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik pliku lub buforu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="b9b02-2354">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2355">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2355">Allowed From</span></span>

<span data-ttu-id="b9b02-2356">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2357">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-2358">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2358">See Also</span></span>

- <span data-ttu-id="b9b02-2359">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="b9b02-2360">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="b9b02-2361">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="b9b02-2362">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="b9b02-2363">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2363">fx_file_close,</span></span>
- <span data-ttu-id="b9b02-2364">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2364">fx_file_create,</span></span>
- <span data-ttu-id="b9b02-2365">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="b9b02-2366">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2366">fx_file_delete,</span></span>
- <span data-ttu-id="b9b02-2367">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="b9b02-2368">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="b9b02-2369">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="b9b02-2370">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="b9b02-2371">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="b9b02-2372">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="b9b02-2373">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2373">fx_file_open,</span></span>
- <span data-ttu-id="b9b02-2374">fx_file_read,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2374">fx_file_read,</span></span>
- <span data-ttu-id="b9b02-2375">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="b9b02-2376">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2376">fx_file_rename,</span></span>
- <span data-ttu-id="b9b02-2377">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2377">fx_file_seek,</span></span>
- <span data-ttu-id="b9b02-2378">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="b9b02-2379">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="b9b02-2380">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="b9b02-2381">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="b9b02-2382">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="b9b02-2383">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="b9b02-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="b9b02-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="b9b02-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="b9b02-2386">Ustawia funkcję powiadamiania o zapisie pliku</span><span class="sxs-lookup"><span data-stu-id="b9b02-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2387">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="b9b02-2388">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2388">Description</span></span>

<span data-ttu-id="b9b02-2389">Ta usługa instaluje funkcję wywołania zwrotnego wywoływaną po pomyślnej operacji zapisu pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2390">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2390">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2391">**file_ptr:** wskaźnik do bloku sterowania plikami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="b9b02-2392">**file_write_notify:** Funkcja wywołania zwrotnego zapisu pliku do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="b9b02-2393">Ustawienie funkcji wywołania zwrotnego na wartość NULL powoduje wyłączenie funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2394">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2394">Return Values</span></span>

- <span data-ttu-id="b9b02-2395">**FX_SUCCESS** (0x00) Pomyślnie zainstalowano funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="b9b02-2396">**FX_PTR_ERROR** (0x18) file_ptr wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="b9b02-2397">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2398">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2398">Allowed From</span></span>

<span data-ttu-id="b9b02-2399">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2400">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2401">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2401">See Also</span></span>

- <span data-ttu-id="b9b02-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2402">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2406">fx_file_close</span></span>
- <span data-ttu-id="b9b02-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2407">fx_file_create</span></span>
- <span data-ttu-id="b9b02-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-2409">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2416">fx_file_open</span></span>
- <span data-ttu-id="b9b02-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2417">fx_file_read</span></span>
- <span data-ttu-id="b9b02-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2419">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-2420">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2421">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2423">fx_file_write</span></span>
- <span data-ttu-id="b9b02-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="b9b02-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2428">fx_media_abort</span></span>

<span data-ttu-id="b9b02-2429">Przerywa działania związane z multimediami</span><span class="sxs-lookup"><span data-stu-id="b9b02-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2430">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="b9b02-2431">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2431">Description</span></span>

<span data-ttu-id="b9b02-2432">Ta usługa przerywa wszystkie bieżące działania związane z nośnikiem, w tym zamykanie wszystkich otwartych plików, wysyłanie żądania przerwania do skojarzonego sterownika i umieszczanie nośnika w stanie przerwania.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="b9b02-2433">Ta usługa jest zwykle wywoływana po wykryciu błędów we/wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2434">*Nośnik musi zostać ponownie otwarty, aby można było z niego korzystać ponownie po wykonaniu operacji przerwania.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2435">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2435">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2436">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2437">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2437">Return Values</span></span>

- <span data-ttu-id="b9b02-2438">**FX_SUCCESS** (0x00) Przerwanie nośnika pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="b9b02-2439">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-2440">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-2441">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2442">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2442">Allowed From</span></span>

<span data-ttu-id="b9b02-2443">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2444">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2445">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2445">See Also</span></span>

- <span data-ttu-id="b9b02-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2448">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2449">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2453">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2454">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2455">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2457">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2458">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2461">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="b9b02-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="b9b02-2464">Unieważnia pamięć podręczną sektora logicznego</span><span class="sxs-lookup"><span data-stu-id="b9b02-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2465">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="b9b02-2466">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2466">Description</span></span>

<span data-ttu-id="b9b02-2467">Ta usługa opróżnia wszystkie zanieczyszczone sektory w pamięci podręcznej, a następnie unieważnia całą pamięć podręczną sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2468">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2468">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2469">**media_ptr:** Wskaźnik do bloku sterowania multimediami</span><span class="sxs-lookup"><span data-stu-id="b9b02-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2470">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2470">Return Values</span></span>

- <span data-ttu-id="b9b02-2471">**FX_SUCCESS** (0x00) Pomyślne unieważnienie pamięci podręcznej multimediów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="b9b02-2472">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-2473">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2474">**FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik podstaw.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="b9b02-2475">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2476">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2476">Allowed From</span></span>

<span data-ttu-id="b9b02-2477">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2478">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2479">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2479">See Also</span></span>

- <span data-ttu-id="b9b02-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2481">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2482">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2483">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2487">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2488">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2489">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2491">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2492">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2495">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="b9b02-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2497">fx_media_check</span></span>

<span data-ttu-id="b9b02-2498">Sprawdza, czy na nośniku występują błędy</span><span class="sxs-lookup"><span data-stu-id="b9b02-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2499">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="b9b02-2500">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2500">Description</span></span>

<span data-ttu-id="b9b02-2501">Ta usługa sprawdza na określonym nośniku podstawowe błędy strukturalne, w tym łączenie krzyżowe plików/katalogów, nieprawidłowe łańcuchy FAT i utracone klastry.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="b9b02-2502">Ta usługa umożliwia również korygowanie wykrytych błędów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="b9b02-2503">Usługa fx_media_check wymaga pamięci tymczasowej do pierwszej analizy katalogów i plików na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="b9b02-2504">W szczególności pamięć dla plików scratch dostarczona do usługi sprawdzania multimediów musi być wystarczająco duża, aby pomieścić kilka wpisów w katalogu, strukturę danych do "stosu" bieżącej pozycji wpisu katalogu przed wprowadzeniem do podkatalogów, a na koniec logiczną mapę bitów FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="b9b02-2505">Pamięć na początku powinna mieć co najmniej 512–1024 bajty oraz pamięć dla logicznej mapy bitów FAT, co wymaga tylu bitów, ile jest klastrów na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="b9b02-2506">Na przykład urządzenie z 8000 klastrami wymagałoby 1000 bajtów do reprezentowania i w związku z tym wymagałoby całkowitego obszaru na początku w kolejności 2048 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2507">*Ta usługa powinna być wywoływana natychmiast po fx_media_open i bez żadnej innej aktywności systemu plików.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2508">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2508">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2509">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-2510">**scratch_memory_ptr:** Wskaźnik na początek pamięci na początku pamięci dla podstaw.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="b9b02-2511">**scratch_memory_size:** rozmiar pamięci na początku w bajtach.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="b9b02-2512">**error_correction_option:** bity opcji korekcji błędów, gdy bit jest ustawiony, wykonywana jest korekta błędu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="b9b02-2513">Bity opcji korekcji błędów są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b9b02-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="b9b02-2514">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="b9b02-2515">FX_DIRECTORY_ERROR (0x02)</span><span class="sxs-lookup"><span data-stu-id="b9b02-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="b9b02-2516">FX_LOST_CLUSTER_ERROR (0x04) Po prostu LUB razem wymagane opcje korekty błędów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="b9b02-2517">Jeśli nie jest wymagana żadna korekta błędu, należy dostarczyć wartość 0.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="b9b02-2518">**errors_detected_ptr:** miejsce docelowe bitów wykrywania błędów, zgodnie z definicją poniżej:</span><span class="sxs-lookup"><span data-stu-id="b9b02-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="b9b02-2519">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="b9b02-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="b9b02-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span><span class="sxs-lookup"><span data-stu-id="b9b02-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="b9b02-2521">FX_FILE_SIZE_ERROR (0x08)</span><span class="sxs-lookup"><span data-stu-id="b9b02-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2522">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2522">Return Values</span></span>

- <span data-ttu-id="b9b02-2523">**FX_SUCCESS** (0x00) Pomyślne sprawdzenie nośnika, aby uzyskać szczegółowe informacje o wykrytych błędach w miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="b9b02-2524">**FX_ACCESS_ERROR** (0x06) Nie można wykonać sprawdzania otwartych plików.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="b9b02-2525">**FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-2526">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-2527">**FX_NO_MORE_SPACE** (0x0A) Brak więcej miejsca na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="b9b02-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Dostarczona pamięć na początku nie jest wystarczająco duża.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="b9b02-2529">**FX_ERROR_NOT_FIXED** (0x93) uszkodzenie katalogu głównego FAT32, których nie można naprawić.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="b9b02-2530">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2531">**FX_SECTOR_INVALID** (0x89) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="b9b02-2532">**FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik lub wskaźnik podstaw.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="b9b02-2533">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="b9b02-2534">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2534">Allowed From</span></span>

<span data-ttu-id="b9b02-2535">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2536">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2536">Example</span></span>

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2537">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2537">See Also</span></span>

- <span data-ttu-id="b9b02-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2539">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2541">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2545">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2546">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2547">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2549">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2550">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2553">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="b9b02-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2555">fx_media_close</span></span>

<span data-ttu-id="b9b02-2556">Zamyka nośnik</span><span class="sxs-lookup"><span data-stu-id="b9b02-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2557">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="b9b02-2558">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2558">Description</span></span>

<span data-ttu-id="b9b02-2559">Ta usługa zamyka określony nośnik.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2559">This service closes the specified media.</span></span> <span data-ttu-id="b9b02-2560">W procesie zamykania nośnika wszystkie otwarte pliki są zamykane, a pozostałe bufory są opróżnione do nośnika fizycznego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2561">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2561">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2562">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2563">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2563">Return Values</span></span>

- <span data-ttu-id="b9b02-2564">**FX_SUCCESS** (0x00) Pomyślne zamknięcie nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="b9b02-2565">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-2566">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2567">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-2568">**FX_CALLER_ERROR**    (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2569">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2569">Allowed From</span></span>

<span data-ttu-id="b9b02-2570">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2571">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2572">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2572">See Also</span></span>

- <span data-ttu-id="b9b02-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2574">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2576">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2580">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2581">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2582">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2584">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2585">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2588">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="b9b02-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="b9b02-2591">Ustawia funkcję powiadamiania o zamknięciu nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2592">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="b9b02-2593">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2593">Description</span></span>

<span data-ttu-id="b9b02-2594">Ta usługa ustawia funkcję wywołania zwrotnego powiadamiania, która zostanie wywołana po pomyślnym zamknięciu nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2595">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2595">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2596">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-2597">**media_close_notify:** Funkcja powiadamiania o zamknięciu nośnika powiadamia o instalacji funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="b9b02-2598">Przekazanie wartości NULL jako funkcji wywołania zwrotnego powoduje wyłączenie wywołania zwrotnego zamknięcia nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2599">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2599">Return Values</span></span>

- <span data-ttu-id="b9b02-2600">**FX_SUCCESS** (0x00) Pomyślnie zainstalowano funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="b9b02-2601">**FX_PTR_ERROR** (0x18) media_ptr wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="b9b02-2602">**FX_CALLER_ERROR**    (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2603">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2603">Allowed From</span></span>

<span data-ttu-id="b9b02-2604">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2605">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="b9b02-2606">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2606">See Also</span></span>

- <span data-ttu-id="b9b02-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2608">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2610">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2611">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2614">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2615">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2616">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2618">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2619">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2622">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="b9b02-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="b9b02-2625">Formatuje nośniki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2626">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2626">Prototype</span></span>

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a><span data-ttu-id="b9b02-2627">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2627">Description</span></span>

<span data-ttu-id="b9b02-2628">Ta usługa formatuje dostarczony nośnik w sposób zgodny z exFAT na podstawie podanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="b9b02-2629">Ta usługa musi zostać wywołana przed otwarciem nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2630">*Formatowanie już sformatowanego nośnika skutecznie wymazuje wszystkie pliki i katalogi na nośniku.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-2631">*Rozmiar woluminu exFAT powinien odpowiadać rozmiarowi partycji (w przypadku układu MBR lub GPT) lub rozmiarowi całego urządzenia, jeśli nie ma układu partycji (bez MBR lub GPT). Istnieje ograniczenie dotyczące Windows, że dysk exFAT nie zostanie ponownie sformatowany w przypadku sformatowania z niektórymi wartościami całkowitej liczby sektorów, które są mniejsze niż dostępne sektory*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2631">*The exFAT volume size should match the size of the partition (if there is an MBR or GPT layout), or the size of the whole device if there is no partition layout (no MBR or GPT). There is a limitation on Windows that exFAT Disk will not be recoginzed if formatted with some values of total sectors that are less than available sectors*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2632">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2632">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2633">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2633">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="b9b02-2634">Służy to tylko do podania podstawowych informacji niezbędnych do działania sterownika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2634">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="b9b02-2635">**sterownik:** wskaźnik do sterownika We/Wy dla tego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2635">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="b9b02-2636">Zazwyczaj będzie to ten sam sterownik dostarczony do następnego fx_media_open wywołania.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2636">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="b9b02-2637">**driver_info_ptr:** Wskaźnik do opcjonalnych informacji, które mogą być używane przez sterownik we/wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2637">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="b9b02-2638">**memory_ptr:** Wskaźnik do pamięci roboczej nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2638">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="b9b02-2639">memory_size określa rozmiar pamięci nośnika roboczego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2639">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="b9b02-2640">Rozmiar musi być co najmniej tak duży, jak rozmiar sektora nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2640">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="b9b02-2641">**volume_name:** wskaźnik do ciągu nazwy woluminu, który ma maksymalnie 11 znaków.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2641">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="b9b02-2642">**number_of_fats:** liczba otchłani na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2642">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="b9b02-2643">Bieżąca implementacja obsługuje jeden system PLIKÓW FAT na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2643">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="b9b02-2644">**hidden_sectors:** Liczba sektorów ukrytych przed sektorem rozruchowym tego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2644">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="b9b02-2645">Jest to typowe w przypadku, gdy istnieje wiele partycji.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2645">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="b9b02-2646">**total_sectors:** Łączna liczba sektorów w nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2646">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="b9b02-2647">**bytes_per_sector:** liczba bajtów na sektor, która zazwyczaj wynosi 512.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2647">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="b9b02-2648">Plik FileX wymaga wielokrotności 32.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2648">FileX requires this to be a multiple of 32.</span></span>
> [!IMPORTANT]
> <span data-ttu-id="b9b02-2649">*W odniesieniu do specyfikacji bajty na sektor mogą przyjmować tylko następujące wartości: 512, 1024, 2048 lub 4096.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2649">*With reference to the specification the bytes per sector may take on only the following values: 512, 1024, 2048 or 4096.*</span></span>

- <span data-ttu-id="b9b02-2650">**sectors_per_cluster:** liczba sektorów w każdym klastrze.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2650">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="b9b02-2651">Klaster jest minimalną jednostką alokacji w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2651">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="b9b02-2652">**volumne_serial_number:** numer seryjny używany dla tego woluminu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2652">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="b9b02-2653">**boundary_unit:** rozmiar wyrównania obszaru danych fizycznych w liczbie sektorów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2653">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2654">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2654">Return Values</span></span>

- <span data-ttu-id="b9b02-2655">**FX_SUCCESS** (0x00) Pomyślny format nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2655">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="b9b02-2656">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2656">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2657">**FX_PTR_ERROR** (0x18) Nieprawidłowy nośnik, sterownik lub wskaźnik pamięci.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2657">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="b9b02-2658">**FX_CALLER_ERROR**    (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2658">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2659">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2659">Allowed From</span></span>

<span data-ttu-id="b9b02-2660">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2660">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2661">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2661">Example</span></span>

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2662">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2662">See Also</span></span>

- <span data-ttu-id="b9b02-2663">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2663">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2664">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2664">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2665">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2665">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2666">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2666">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2667">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2667">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2668">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2668">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2669">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2669">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2670">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2670">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2671">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2671">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2672">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2672">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2673">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2673">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2674">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2674">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2675">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2675">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2676">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2676">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2677">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2677">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2678">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2678">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2679">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2679">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="b9b02-2680">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2680">fx_media_extended_space_available</span></span>

<span data-ttu-id="b9b02-2681">Zwraca dostępne miejsce na nośniku</span><span class="sxs-lookup"><span data-stu-id="b9b02-2681">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2682">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2682">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="b9b02-2683">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2683">Description</span></span>

<span data-ttu-id="b9b02-2684">Ta usługa zwraca liczbę bajtów dostępnych na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2684">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="b9b02-2685">Ta usługa jest przeznaczona dla usługi exFAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2685">This service is designed for exFAT.</span></span> <span data-ttu-id="b9b02-2686">Wskaźnik do *available_bytes* przyjmuje wartość 64-bitowej liczby całkowitej, co umożliwia funkcji wywołującej pracę z nośnikiem przekraczacym zakres 4 GB.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2686">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2687">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2687">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2688">**media_ptr:** Wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2688">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="b9b02-2689">**available_bytes_ptr:** dostępne bajty pozostawione na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2689">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2690">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2690">Return Values</span></span>

- <span data-ttu-id="b9b02-2691">**FX_SUCCESS** (0x00) Pomyślnie pobrano miejsce dostępne na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2691">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="b9b02-2692">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2692">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-2693">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub dostępny wskaźnik bajtów ma wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2693">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="b9b02-2694">**FX_CALLER_ERROR**    (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2694">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2695">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2695">Allowed From</span></span>

<span data-ttu-id="b9b02-2696">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2696">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2697">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2697">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2698">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2698">See Also</span></span>

- <span data-ttu-id="b9b02-2699">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2699">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2700">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2700">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2701">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2701">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2702">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2702">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2703">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2703">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2704">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2704">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2705">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2705">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2706">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2706">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2707">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2707">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2708">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2708">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2709">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2709">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2710">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2710">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2711">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2711">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2712">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2712">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2713">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2713">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2714">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2714">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2715">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2715">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="b9b02-2716">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2716">fx_media_flush</span></span>

<span data-ttu-id="b9b02-2717">Opróżnia dane na nośnik fizyczny</span><span class="sxs-lookup"><span data-stu-id="b9b02-2717">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2718">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2718">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="b9b02-2719">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2719">Description</span></span>

<span data-ttu-id="b9b02-2720">Ta usługa opróżnia wszystkie buforowane sektory i wpisy katalogu wszystkich zmodyfikowanych plików na nośnik fizyczny.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2720">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2721">*Ta procedura może być wywoływana okresowo przez aplikację w celu zmniejszenia ryzyka uszkodzenia plików i/lub utraty danych w przypadku nagłej utraty zasilania w celu.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2721">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2722">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2722">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2723">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2723">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2724">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2724">Return Values</span></span>

- <span data-ttu-id="b9b02-2725">**FX_SUCCESS** (0x00) Pomyślne opróżnienie nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2725">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="b9b02-2726">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2726">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-2727">**FX_FILE_CORRUPT**    (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2727">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="b9b02-2728">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2728">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-2729">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2729">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2730">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2730">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-2731">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2731">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-2732">**FX_CALLER_ERROR**    (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2732">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2733">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2733">Allowed From</span></span>

<span data-ttu-id="b9b02-2734">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2734">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2735">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2735">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2736">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2736">See Also</span></span>

- <span data-ttu-id="b9b02-2737">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2737">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2738">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2738">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2739">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2739">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2740">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2740">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2741">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2741">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2742">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2742">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2743">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2743">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2744">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2744">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2745">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2745">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2746">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2746">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2747">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2747">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2748">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2748">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2749">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2749">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2750">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2750">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2751">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2751">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2752">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2752">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2753">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2753">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="b9b02-2754">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2754">fx_media_format</span></span>

<span data-ttu-id="b9b02-2755">Formatuje nośniki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2755">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2756">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2756">Prototype</span></span>

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a><span data-ttu-id="b9b02-2757">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2757">Description</span></span>

<span data-ttu-id="b9b02-2758">Ta usługa formatuje dostarczony nośnik w sposób zgodny ze standardem FAT 12/16/32 na podstawie podanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2758">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="b9b02-2759">Ta usługa musi zostać wywołana przed otwarciem nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2759">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2760">*Formatowanie już sformatowanego nośnika skutecznie wymazuje wszystkie pliki i katalogi na nośniku.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2760">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2761">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2761">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2762">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2762">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="b9b02-2763">Służy to tylko do podania podstawowych informacji niezbędnych do działania sterownika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2763">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="b9b02-2764">**sterownik:** wskaźnik do sterownika We/Wy dla tego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2764">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="b9b02-2765">Zazwyczaj będzie to ten sam sterownik dostarczony do kolejnego wywołania fx_media_open wywołania.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2765">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="b9b02-2766">**driver_info_ptr:** Wskaźnik do opcjonalnych informacji, które mogą być używane przez sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2766">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="b9b02-2767">**memory_ptr:** wskaźnik do pamięci roboczej nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2767">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="b9b02-2768">**memory_size:** określa rozmiar pamięci nośnika roboczego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2768">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="b9b02-2769">Rozmiar musi być co najmniej tak duży, jak rozmiar sektora nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2769">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="b9b02-2770">**volume_name:** wskaźnik do ciągu nazwy woluminu, który ma maksymalnie 11 znaków.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2770">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="b9b02-2771">**number_of_fats:** liczba fajerzy w nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2771">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="b9b02-2772">Minimalna wartość wynosi 1 dla podstawowego FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2772">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="b9b02-2773">Wartości większe niż 1 spowodować dodatkowe kopie FAT są utrzymywane w czasie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2773">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="b9b02-2774">**directory_entries:** liczba wpisów katalogu w katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2774">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="b9b02-2775">**hidden_sectors:** Liczba sektorów ukrytych przed sektorem rozruchowym tego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2775">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="b9b02-2776">Jest to typowe w przypadku wielu partycji.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2776">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="b9b02-2777">**total_sectors:** Łączna liczba sektorów w nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2777">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="b9b02-2778">**bytes_per_sector:** liczba bajtów na sektor, która zazwyczaj wynosi 512.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2778">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="b9b02-2779">Plik FileX wymaga, aby była wielokrotnością 32.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2779">FileX requires this to be a multiple of 32.</span></span>
> [!IMPORTANT]
> <span data-ttu-id="b9b02-2780">*W odniesieniu do specyfikacji bajty na sektor mogą przyjmować tylko następujące wartości: 512, 1024, 2048 lub 4096.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2780">*With reference to the specification the bytes per sector may take on only the following values: 512, 1024, 2048 or 4096.*</span></span>

- <span data-ttu-id="b9b02-2781">**sectors_per_cluster:** liczba sektorów w każdym klastrze.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2781">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="b9b02-2782">Klaster jest minimalną jednostką alokacji w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2782">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="b9b02-2783">**"orły":** liczba orzeł fizycznych.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2783">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="b9b02-2784">**sectors_per_track:** liczba sektorów na ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2784">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2785">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2785">Return Values</span></span>

- <span data-ttu-id="b9b02-2786">**FX_SUCCESS** (0x00) Pomyślny format nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2786">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="b9b02-2787">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2787">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2788">**FX_PTR_ERROR** (0x18) Wskaźnik nieprawidłowego nośnika, sterownika lub pamięci.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2788">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="b9b02-2789">**FX_CALLER_ERROR**    (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2789">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2790">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2790">Allowed From</span></span>

<span data-ttu-id="b9b02-2791">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2791">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2792">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2792">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2793">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2793">See Also</span></span>

- <span data-ttu-id="b9b02-2794">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2794">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2795">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2795">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2796">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2796">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2797">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2797">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2798">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2798">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2799">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2799">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2800">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2800">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2801">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2801">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2802">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2802">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2803">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2803">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2804">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2804">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2805">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2805">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2806">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2806">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2807">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2807">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2808">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2808">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2809">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2809">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2810">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2810">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="b9b02-2811">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2811">fx_media_open</span></span>

<span data-ttu-id="b9b02-2812">Otwiera nośnik w celu uzyskania dostępu do plików</span><span class="sxs-lookup"><span data-stu-id="b9b02-2812">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2813">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2813">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="b9b02-2814">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2814">Description</span></span>

<span data-ttu-id="b9b02-2815">Ta usługa otwiera nośnik w celu uzyskania dostępu do plików przy użyciu dostarczonego sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2815">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-2816">*Pamięć dostarczana do tej usługi jest używana do implementowania wewnętrznej pamięci podręcznej sektora logicznego, dlatego im więcej pamięci jest dostarczanych, tym mniejsza jest liczba fizycznych we/wy. Plik FileX wymaga pamięci podręcznej z co najmniej jednym sektorem logicznym (bajty na sektor nośnika).*</span><span class="sxs-lookup"><span data-stu-id="b9b02-2816">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2817">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2817">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2818">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2818">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-2819">**media_name:** wskaźnik do nazwy nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2819">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="b9b02-2820">**media_driver:** Wskaźnik do sterownika We/Wy dla tego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2820">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="b9b02-2821">Sterownik We/Wy musi być zgodny z wymaganiami sterownika FileX zdefiniowanymi w rozdziale 5.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2821">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="b9b02-2822">**driver_info_ptr:** Wskaźnik do opcjonalnych informacji, które mogą być używane przez dostarczony sterownik we/wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2822">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="b9b02-2823">**memory_ptr:** Wskaźnik do pamięci roboczej nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2823">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="b9b02-2824">**memory_size:** określa rozmiar pamięci nośnika roboczego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2824">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="b9b02-2825">Rozmiar musi być tak duży, jak rozmiar sektora nośnika (zazwyczaj 512 bajtów).</span><span class="sxs-lookup"><span data-stu-id="b9b02-2825">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2826">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2826">Return Values</span></span>

- <span data-ttu-id="b9b02-2827">**FX_SUCCESS** (0x00) Otwieranie nośnika pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2827">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="b9b02-2828">**FX_BOOT_ERROR** (0x01) Błąd podczas odczytywania sektora rozruchowego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2828">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="b9b02-2829">**FX_MEDIA_INVALID** (0x02) Sektor rozruchowy określonego nośnika jest uszkodzony lub nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2829">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="b9b02-2830">Ponadto ten kod powrotny służy do wskazania, że rozmiar pamięci podręcznej sektora logicznego lub rozmiar wpisu FAT nie jest potęgą 2.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2830">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="b9b02-2831">**FX_FAT_READ_ERROR** (0x03) Błąd podczas odczytywania informacji z nośnika FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2831">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="b9b02-2832">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2832">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2833">**FX_PTR_ERROR** (0x18) Co najmniej jeden wskaźnik ma wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2833">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="b9b02-2834">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2834">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2835">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2835">Allowed From</span></span>

<span data-ttu-id="b9b02-2836">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2836">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2837">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2837">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2838">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2838">See Also</span></span>

- <span data-ttu-id="b9b02-2839">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2839">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2840">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2840">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2841">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2841">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2842">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2842">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2843">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2843">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2844">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2844">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2845">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2845">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2846">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2846">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2847">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2847">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2848">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2848">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2849">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2849">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2850">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2850">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2851">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2851">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2852">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2852">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2853">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2853">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2854">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2854">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2855">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2855">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="b9b02-2856">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2856">fx_media_open_notify_set</span></span>

<span data-ttu-id="b9b02-2857">Ustawia funkcję powiadamiania o otwarciu nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-2857">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2858">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2858">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="b9b02-2859">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2859">Description</span></span>

<span data-ttu-id="b9b02-2860">Ta usługa ustawia funkcję wywołania zwrotnego powiadamiania, która zostanie wywołana po pomyślnym otwarciu nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2860">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2861">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2861">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2862">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2862">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-2863">**media_open_notify:** Funkcja wywołania zwrotnego powiadomienia o otwarciu nośnika do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2863">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="b9b02-2864">Przekazywanie wartości NULL jako funkcji wywołania zwrotnego wyłącza otwarte wywołanie zwrotne multimediów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2864">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2865">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2865">Return Values</span></span>


- <span data-ttu-id="b9b02-2866">**FX_SUCCESS** (0x00) Pomyślnie zainstalowano funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2866">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="b9b02-2867">**FX_PTR_ERROR** (0x18) media_ptr wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2867">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="b9b02-2868">**FX_CALLER_ERROR**    (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2868">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2869">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2869">Allowed From</span></span>

<span data-ttu-id="b9b02-2870">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2871">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2871">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2872">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2872">See Also</span></span>

- <span data-ttu-id="b9b02-2873">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2873">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2874">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2874">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2875">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2875">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2876">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2876">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2877">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2877">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2878">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2878">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2879">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2879">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2880">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2880">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2881">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2881">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2882">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2882">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2883">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2883">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2884">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2884">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2885">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2885">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2886">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2886">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2887">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2887">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2888">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2888">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2889">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2889">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="b9b02-2890">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2890">fx_media_read</span></span>

<span data-ttu-id="b9b02-2891">Odczytuje sektor logiczny z nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-2891">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2892">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2892">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="b9b02-2893">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2893">Description</span></span>

<span data-ttu-id="b9b02-2894">Ta usługa odczytuje sektor logiczny z nośnika i umieszcza go w dostarczonym buforze.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2894">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2895">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2895">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2896">**media_ptr:** Wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2896">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="b9b02-2897">**logical_sector:** Sektor logiczny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2897">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="b9b02-2898">**buffer_ptr:** wskaźnik do miejsca docelowego odczytu sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2898">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2899">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2899">Return Values</span></span>

- <span data-ttu-id="b9b02-2900">**FX_SUCCESS** (0x00) Pomyślne odczytanie nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2900">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="b9b02-2901">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2901">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-2902">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2902">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2903">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2903">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-2904">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub buforu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2904">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="b9b02-2905">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2905">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2906">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2906">Allowed From</span></span>

<span data-ttu-id="b9b02-2907">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2907">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2908">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2908">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-2909">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2909">See Also</span></span>

- <span data-ttu-id="b9b02-2910">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2910">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2911">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2911">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2912">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2912">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2913">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2913">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2914">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2914">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2915">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2915">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2916">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2916">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2917">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2917">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2918">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2918">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2919">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2919">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2920">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2920">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2921">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2921">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2922">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2922">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-2923">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2923">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2924">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2924">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2925">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2925">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2926">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2926">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="b9b02-2927">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2927">fx_media_space_available</span></span>

<span data-ttu-id="b9b02-2928">Zwraca dostępne miejsce na nośniku</span><span class="sxs-lookup"><span data-stu-id="b9b02-2928">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2929">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2929">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="b9b02-2930">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2930">Description</span></span>

<span data-ttu-id="b9b02-2931">Ta usługa zwraca liczbę bajtów dostępnych na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2931">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="b9b02-2932">Aby pracować z nośnikiem większym niż 4 GB, aplikacja musi używać usługi *fx_media_extended_space_available*.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2932">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2933">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2933">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2934">**media_ptr:** Wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2934">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="b9b02-2935">**available_bytes_ptr:** dostępne bajty pozostawione na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2935">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2936">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2936">Return Values</span></span>

- <span data-ttu-id="b9b02-2937">**FX_SUCCESS** (0x00) Pomyślnie zwrócono dostępne miejsce na nośniku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2937">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="b9b02-2938">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2938">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-2939">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika lub dostępny wskaźnik bajtów ma wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2939">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="b9b02-2940">**FX_CALLER_ERROR**    (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2940">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2941">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2941">Allowed From</span></span>

<span data-ttu-id="b9b02-2942">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2942">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2943">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2943">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2944">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2944">See Also</span></span>

- <span data-ttu-id="b9b02-2945">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2945">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2946">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2946">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2947">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2947">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2948">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2948">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2949">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2949">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2950">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2950">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2951">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2951">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2952">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2952">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2953">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2953">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2954">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2954">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2955">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2955">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2956">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2956">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2957">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2957">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2958">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2958">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-2959">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2959">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-2960">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-2960">fx_media_write</span></span>
- <span data-ttu-id="b9b02-2961">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-2961">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="b9b02-2962">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-2962">fx_media_volume_get</span></span>

<span data-ttu-id="b9b02-2963">Pobiera nazwę woluminu nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-2963">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-2964">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-2964">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="b9b02-2965">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-2965">Description</span></span>

<span data-ttu-id="b9b02-2966">Ta usługa pobiera nazwę woluminu wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2966">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-2967">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-2967">Input Parameters</span></span>

- <span data-ttu-id="b9b02-2968">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2968">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-2969">**volume_name:** wskaźnik do miejsca docelowego dla nazwy woluminu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2969">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="b9b02-2970">Należy pamiętać, że miejsce docelowe musi być co najmniej wystarczająco duże, aby pomieścić 12 znaków.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2970">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="b9b02-2971">**volume_source:** Określa, gdzie pobrać nazwę z sektora rozruchowego lub katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2971">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="b9b02-2972">Prawidłowe wartości dla tego parametru to:</span><span class="sxs-lookup"><span data-stu-id="b9b02-2972">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="b9b02-2973">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="b9b02-2973">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="b9b02-2974">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="b9b02-2974">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-2975">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-2975">Return Values</span></span>

- <span data-ttu-id="b9b02-2976">**FX_SUCCESS** (0x00) Pomyślne uzyskiwanie woluminu nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2976">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="b9b02-2977">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2977">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-2978">**FX_NOT_FOUND** (0x04) Wolumin nie został znaleziony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2978">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="b9b02-2979">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2979">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-2980">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik miejsca docelowego nośnika lub woluminu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2980">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="b9b02-2981">**FX_CALLER_ERROR** (0x20) Nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-2981">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-2982">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-2982">Allowed From</span></span>

<span data-ttu-id="b9b02-2983">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-2983">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-2984">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-2984">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="b9b02-2985">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-2985">See Also</span></span>

- <span data-ttu-id="b9b02-2986">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-2986">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-2987">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-2987">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-2988">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-2988">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-2989">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-2989">fx_media_check</span></span>
- <span data-ttu-id="b9b02-2990">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-2990">fx_media_close</span></span>
- <span data-ttu-id="b9b02-2991">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2991">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-2992">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2992">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-2993">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2993">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-2994">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-2994">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-2995">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-2995">fx_media_format</span></span>
- <span data-ttu-id="b9b02-2996">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-2996">fx_media_open</span></span>
- <span data-ttu-id="b9b02-2997">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-2997">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-2998">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-2998">fx_media_read</span></span>
- <span data-ttu-id="b9b02-2999">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-2999">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-3000">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3000">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-3001">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3001">fx_media_write</span></span>
- <span data-ttu-id="b9b02-3002">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-3002">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="b9b02-3003">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="b9b02-3003">fx_media_volume_get_extended</span></span>

<span data-ttu-id="b9b02-3004">Pobiera nazwę woluminu nośnika wcześniej otwartego nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-3004">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3005">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3005">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="b9b02-3006">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3006">Description</span></span>

<span data-ttu-id="b9b02-3007">Ta usługa pobiera nazwę woluminu wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3007">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-3008">Ta usługa jest taka sama jak \***fx_media_volume_get()** _ z wyjątkiem tego, że wywołujący przekazuje rozmiar buforu _ \*volume_name\*\*.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3008">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3009">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3009">Input Parameters</span></span>


- <span data-ttu-id="b9b02-3010">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3010">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-3011">**volume_name:** wskaźnik do miejsca docelowego dla nazwy woluminu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3011">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="b9b02-3012">Należy pamiętać, że miejsce docelowe musi być co najmniej wystarczająco duże, aby pomieścić 12 znaków.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3012">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="b9b02-3013">**volume_name_buffer_length:** rozmiar volume_name buforu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3013">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="b9b02-3014">**volume_source:** określa, gdzie pobrać nazwę z sektora rozruchowego lub katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3014">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="b9b02-3015">Prawidłowe wartości dla tego parametru to:</span><span class="sxs-lookup"><span data-stu-id="b9b02-3015">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="b9b02-3016">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="b9b02-3016">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="b9b02-3017">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="b9b02-3017">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3018">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3018">Return Values</span></span>

- <span data-ttu-id="b9b02-3019">**FX_SUCCESS** (0x00) Pomyślne uzyskiwanie woluminu multimedialnego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3019">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="b9b02-3020">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3020">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3021">**FX_NOT_FOUND** (0x04) Wolumin nie został znaleziony.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3021">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="b9b02-3022">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3022">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-3023">**FX_PTR_ERROR** (0x18) Wskaźnik miejsca docelowego nieprawidłowego nośnika lub woluminu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3023">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="b9b02-3024">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3024">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3025">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3025">Allowed From</span></span>

<span data-ttu-id="b9b02-3026">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3026">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3027">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3027">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3028">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3028">See Also</span></span>

- <span data-ttu-id="b9b02-3029">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-3029">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-3030">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-3030">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-3031">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3031">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-3032">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-3032">fx_media_check</span></span>
- <span data-ttu-id="b9b02-3033">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3033">fx_media_close</span></span>
- <span data-ttu-id="b9b02-3034">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3034">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-3035">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-3035">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-3036">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-3036">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-3037">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-3037">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-3038">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-3038">fx_media_format</span></span>
- <span data-ttu-id="b9b02-3039">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3039">fx_media_open</span></span>
- <span data-ttu-id="b9b02-3040">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3040">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-3041">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3041">fx_media_read</span></span>
- <span data-ttu-id="b9b02-3042">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-3042">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-3043">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3043">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-3044">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3044">fx_media_write</span></span>
- <span data-ttu-id="b9b02-3045">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-3045">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="b9b02-3046">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3046">fx_media_volume_set</span></span>

<span data-ttu-id="b9b02-3047">Ustawia nazwę woluminu nośnika</span><span class="sxs-lookup"><span data-stu-id="b9b02-3047">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3048">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3048">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="b9b02-3049">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3049">Description</span></span>

<span data-ttu-id="b9b02-3050">Ta usługa ustawia nazwę woluminu wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3050">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3051">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3051">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3052">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3052">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-3053">**volume_name:** Wskaźnik do nazwy woluminu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3053">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3054">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3054">Return Values</span></span>

- <span data-ttu-id="b9b02-3055">**FX_SUCCESS** (0x00) Zestaw pomyślnych woluminów multimedialnych.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3055">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="b9b02-3056">**FX_INVALID_NAME** (0x0C) Volume_name jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3056">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="b9b02-3057">**FX_MEDIA_INVALID** (0x02) Nie można ustawić nazwy woluminu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3057">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="b9b02-3058">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3058">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3059">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3059">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-3060">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3060">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-3061">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nazwy nośnika lub woluminu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3061">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="b9b02-3062">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3062">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3063">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3063">Allowed From</span></span>

<span data-ttu-id="b9b02-3064">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3064">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3065">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3065">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3066">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3066">See Also</span></span>

- <span data-ttu-id="b9b02-3067">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-3067">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-3068">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-3068">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-3069">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3069">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-3070">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-3070">fx_media_check</span></span>
- <span data-ttu-id="b9b02-3071">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3071">fx_media_close</span></span>
- <span data-ttu-id="b9b02-3072">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3072">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-3073">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-3073">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-3074">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-3074">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-3075">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-3075">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-3076">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-3076">fx_media_format</span></span>
- <span data-ttu-id="b9b02-3077">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3077">fx_media_open</span></span>
- <span data-ttu-id="b9b02-3078">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3078">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-3079">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3079">fx_media_read</span></span>
- <span data-ttu-id="b9b02-3080">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-3080">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-3081">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3081">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-3082">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3082">fx_media_write</span></span>
- <span data-ttu-id="b9b02-3083">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-3083">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="b9b02-3084">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3084">fx_media_write</span></span>

<span data-ttu-id="b9b02-3085">Zapisuje sektor logiczny</span><span class="sxs-lookup"><span data-stu-id="b9b02-3085">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3086">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3086">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="b9b02-3087">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3087">Description</span></span>

<span data-ttu-id="b9b02-3088">Ta usługa zapisuje dostarczony bufor do określonego sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3088">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3089">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3089">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3090">**media_ptr:** Wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3090">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="b9b02-3091">**logical_sector:** sektor logiczny do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3091">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="b9b02-3092">**buffer_ptr:** wskaźnik do źródła zapisu w sektorze logicznym.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3092">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3093">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3093">Return Values</span></span>

- <span data-ttu-id="b9b02-3094">**FX_SUCCESS** (0x00) Pomyślny zapis nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3094">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="b9b02-3095">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3095">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3096">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3096">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-3097">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3097">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-3098">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3098">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-3099">**FX_PTR_ERROR** (0x18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3099">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="b9b02-3100">**FX_CALLER_ERROR**    (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3100">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3101">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3101">Allowed From</span></span>

<span data-ttu-id="b9b02-3102">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3102">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3103">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3103">Example</span></span>

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3104">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3104">See Also</span></span>

- <span data-ttu-id="b9b02-3105">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="b9b02-3105">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="b9b02-3106">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="b9b02-3106">fx_media_abort</span></span>
- <span data-ttu-id="b9b02-3107">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3107">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="b9b02-3108">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="b9b02-3108">fx_media_check</span></span>
- <span data-ttu-id="b9b02-3109">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3109">fx_media_close</span></span>
- <span data-ttu-id="b9b02-3110">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3110">fx_media_close_notify_set</span></span>
- <span data-ttu-id="b9b02-3111">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-3111">fx_media_exFAT_format</span></span>
- <span data-ttu-id="b9b02-3112">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-3112">fx_media_extended_space_available</span></span>
- <span data-ttu-id="b9b02-3113">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="b9b02-3113">fx_media_flush</span></span>
- <span data-ttu-id="b9b02-3114">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="b9b02-3114">fx_media_format</span></span>
- <span data-ttu-id="b9b02-3115">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3115">fx_media_open</span></span>
- <span data-ttu-id="b9b02-3116">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3116">fx_media_open_notify_set</span></span>
- <span data-ttu-id="b9b02-3117">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3117">fx_media_read</span></span>
- <span data-ttu-id="b9b02-3118">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="b9b02-3118">fx_media_space_available</span></span>
- <span data-ttu-id="b9b02-3119">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3119">fx_media_volume_get</span></span>
- <span data-ttu-id="b9b02-3120">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3120">fx_media_volume_set</span></span>
- <span data-ttu-id="b9b02-3121">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-3121">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="b9b02-3122">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3122">fx_system_date_get</span></span>

<span data-ttu-id="b9b02-3123">Pobiera datę systemu plików</span><span class="sxs-lookup"><span data-stu-id="b9b02-3123">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3124">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3124">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="b9b02-3125">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3125">Description</span></span>

<span data-ttu-id="b9b02-3126">Ta usługa zwraca bieżącą datę systemową.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3126">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3127">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3127">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3128">**year**: wskaźnik do miejsca docelowego dla roku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3128">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="b9b02-3129">**month:** wskaźnik do miejsca docelowego dla miesiąca.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3129">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="b9b02-3130">**day**: wskaźnik do miejsca docelowego dla dnia.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3130">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3131">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3131">Return Values</span></span>

- <span data-ttu-id="b9b02-3132">**FX_SUCCESS** (0x00) Pobieranie daty pomyślnej.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3132">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="b9b02-3133">**FX_PTR_ERROR** (0x18) Co najmniej jeden parametr wejściowy ma wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3133">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3134">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3134">Allowed From</span></span>

<span data-ttu-id="b9b02-3135">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3135">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3136">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3136">Example</span></span>

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3137">See Also</span></span>

- <span data-ttu-id="b9b02-3138">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3138">fx_system_date_set</span></span>
- <span data-ttu-id="b9b02-3139">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-3139">fx_system_initialize</span></span>
- <span data-ttu-id="b9b02-3140">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3140">fx_system_time_get</span></span>
- <span data-ttu-id="b9b02-3141">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3141">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="b9b02-3142">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3142">fx_system_date_set</span></span>

<span data-ttu-id="b9b02-3143">Ustawia datę systemowa</span><span class="sxs-lookup"><span data-stu-id="b9b02-3143">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3144">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3144">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="b9b02-3145">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3145">Description</span></span>

<span data-ttu-id="b9b02-3146">Ta usługa ustawia datę systemową w określony sposób.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3146">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-3147">*Ta usługa powinna zostać wywołana wkrótce po **fx_system_initialize,** aby ustawić początkową datę systemową. Domyślnie data systemowa to data ostatniej ogólnej wersji pliku FileX.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3147">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3148">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3148">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3149">**year**: Nowy rok.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3149">**year**: New year.</span></span> <span data-ttu-id="b9b02-3150">Prawidłowy zakres to od 1980 do 2107 roku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3150">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="b9b02-3151">**month**: New month (miesiąc): Nowy miesiąc.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3151">**month**: New month.</span></span> <span data-ttu-id="b9b02-3152">Prawidłowy zakres to od 1 do 12.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3152">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="b9b02-3153">**day**: Nowy dzień.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3153">**day**: New day.</span></span> <span data-ttu-id="b9b02-3154">Prawidłowy zakres wynosi od 1 do 31 w zależności od miesiąca i roku przestępnych.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3154">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3155">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3155">Return Values</span></span>

- <span data-ttu-id="b9b02-3156">**FX_SUCCESS** (0x00) Ustawienie daty Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3156">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="b9b02-3157">**FX_INVALID_YEAR** (0x12) Określono nieprawidłowy rok.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3157">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="b9b02-3158">**FX_INVALID_MONTH** (0x13) Określono nieprawidłowy miesiąc.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3158">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="b9b02-3159">**FX_INVALID_DAY** (0x14) Określono nieprawidłowy dzień.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3159">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3160">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3160">Allowed From</span></span>

<span data-ttu-id="b9b02-3161">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3161">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3162">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3162">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3163">See Also</span></span>

- <span data-ttu-id="b9b02-3164">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3164">fx_system_date_get</span></span>
- <span data-ttu-id="b9b02-3165">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-3165">fx_system_initialize</span></span>
- <span data-ttu-id="b9b02-3166">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3166">fx_system_time_get</span></span>
- <span data-ttu-id="b9b02-3167">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3167">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="b9b02-3168">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-3168">fx_system_initialize</span></span>

<span data-ttu-id="b9b02-3169">Inicjuje cały system</span><span class="sxs-lookup"><span data-stu-id="b9b02-3169">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3170">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3170">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="b9b02-3171">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3171">Description</span></span>

<span data-ttu-id="b9b02-3172">Ta usługa inicjuje wszystkie główne struktury danych FileX.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3172">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="b9b02-3173">Powinna być wywoływana w ***tx_application_define*** lub prawdopodobnie z wątku inicjowania i musi być wywoływana przed użyciem jakiejkolwiek innej usługi FileX.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3173">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-3174">\* Po zainicjowaniu przez to wywołanie aplikacja powinna wywołać fx_system_date_set _ i _ fx_system_time_set \*, aby rozpocząć od dokładnej *daty i czasu systemowego.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3174">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3175">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3175">Input Parameters</span></span>

<span data-ttu-id="b9b02-3176">Brak</span><span class="sxs-lookup"><span data-stu-id="b9b02-3176">None</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3177">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3177">Return Values</span></span>

<span data-ttu-id="b9b02-3178">Brak.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3178">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3179">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3179">Allowed From</span></span>

<span data-ttu-id="b9b02-3180">Inicjowanie, wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3180">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3181">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3181">Example</span></span>

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3182">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3182">See Also</span></span>

- <span data-ttu-id="b9b02-3183">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3183">fx_system_date_get</span></span>
- <span data-ttu-id="b9b02-3184">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3184">fx_system_date_set</span></span>
- <span data-ttu-id="b9b02-3185">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3185">fx_system_time_get</span></span>
- <span data-ttu-id="b9b02-3186">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3186">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="b9b02-3187">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3187">fx_system_time_get</span></span>

<span data-ttu-id="b9b02-3188">Pobiera bieżący czas systemowy</span><span class="sxs-lookup"><span data-stu-id="b9b02-3188">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3189">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3189">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="b9b02-3190">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3190">Description</span></span>

<span data-ttu-id="b9b02-3191">Ta usługa pobiera bieżący czas systemowy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3191">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3192">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3192">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3193">**hour**: wskaźnik do miejsca docelowego na godzinę.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3193">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="b9b02-3194">**minute:** wskaźnik do miejsca docelowego na minutę.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3194">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="b9b02-3195">**second**: Wskaźnik do miejsca docelowego na sekundę.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3195">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3196">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3196">Return Values</span></span>

- <span data-ttu-id="b9b02-3197">**FX_SUCCESS** (0x00) Pomyślne pobieranie czasu systemu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3197">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="b9b02-3198">**FX_PTR_ERROR** (0x18) Co najmniej jeden z parametrów wejściowych</span><span class="sxs-lookup"><span data-stu-id="b9b02-3198">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3199">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3199">Allowed From</span></span>

<span data-ttu-id="b9b02-3200">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3200">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3201">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3201">Example</span></span>

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3202">See Also</span></span>

- <span data-ttu-id="b9b02-3203">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3203">fx_system_date_get</span></span>
- <span data-ttu-id="b9b02-3204">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3204">fx_system_date_set</span></span>
- <span data-ttu-id="b9b02-3205">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-3205">fx_system_initialize</span></span>
- <span data-ttu-id="b9b02-3206">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3206">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="b9b02-3207">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3207">fx_system_time_set</span></span>

<span data-ttu-id="b9b02-3208">Ustawia bieżący czas systemowy</span><span class="sxs-lookup"><span data-stu-id="b9b02-3208">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3209">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3209">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="b9b02-3210">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3210">Description</span></span>

<span data-ttu-id="b9b02-3211">Ta usługa ustawia bieżący czas systemowy na określony przez parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3211">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-3212">*Ta usługa powinna zostać wywołana wkrótce po **fx_system_initialize,** aby ustawić początkowy czas systemowy. Domyślnie czas systemowy to 0:0:0.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3212">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3213">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3213">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3214">**hour:** nowa godzina (0–23).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3214">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="b9b02-3215">**minute:** nowa minuta (0–59).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3215">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="b9b02-3216">**sekunda:** nowa sekunda (0–59).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3216">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3217">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3217">Return Values</span></span>

- <span data-ttu-id="b9b02-3218">**FX_SUCCESS** (0x00) Pomyślne pobieranie czasu systemowego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3218">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="b9b02-3219">**FX_INVALID_HOUR**    (0x15) Nowa godzina jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3219">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="b9b02-3220">**FX_INVALID_MINUTE** (0x16) Nowa minuta jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3220">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="b9b02-3221">**FX_INVALID_SECOND** (0x17) Nowa sekunda jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3221">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3222">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3222">Allowed From</span></span>

<span data-ttu-id="b9b02-3223">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3223">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3224">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3224">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3225">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3225">See Also</span></span>

- <span data-ttu-id="b9b02-3226">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3226">fx_system_date_get</span></span>
- <span data-ttu-id="b9b02-3227">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3227">fx_system_date_set</span></span>
- <span data-ttu-id="b9b02-3228">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="b9b02-3228">fx_system_initialize</span></span>
- <span data-ttu-id="b9b02-3229">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3229">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="b9b02-3230">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3230">fx_unicode_directory_create</span></span>

<span data-ttu-id="b9b02-3231">Tworzy katalog Unicode</span><span class="sxs-lookup"><span data-stu-id="b9b02-3231">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3232">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3232">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="b9b02-3233">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3233">Description</span></span>

<span data-ttu-id="b9b02-3234">Ta usługa tworzy podkatalog o nazwie Unicode w bieżącym katalogu domyślnym — żadne informacje o ścieżce nie są dozwolone w parametrze nazwy źródła Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3234">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="b9b02-3235">Jeśli to się powiedzie, usługa zwraca krótką nazwę (format 8.3) nowo utworzonego podkatalogu Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3235">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-3236">*Wszystkie operacje w podkatalogu Unicode (dzięki czemu jest to ścieżka domyślna, usuwanie itp.) powinny być wykonywane przez dostarczenie zwróconej krótkiej nazwy (w formacie 8.3) do standardowych usług katalogowych FileX.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3236">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-3237">*Ta usługa nie jest obsługiwana na nośnikach exFAT.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3237">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3238">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3238">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3239">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3239">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-3240">**source_unicode_name:** wskaźnik do nazwy Unicode dla nowego podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3240">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="b9b02-3241">**source_unicode_length:** długość nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3241">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="b9b02-3242">**short_name:** wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3) dla nowego podkatalogu Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3242">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3243">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3243">Return Values</span></span>

- <span data-ttu-id="b9b02-3244">**FX_SUCCESS** (0x00) Pomyślne utworzenie katalogu Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3244">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="b9b02-3245">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3245">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3246">**FX_ALREADY_CREATED** (0x0B) Określony katalog już istnieje.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3246">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="b9b02-3247">**FX_NO_MORE_SPACE** (0x0A) Brak dostępnych klastrów na nośniku dla nowego wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3247">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="b9b02-3248">**FX_NOT_IMPLEMENTED** (0x22) nie jest zaimplementowana dla systemu plików exFAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3248">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="b9b02-3249">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3249">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-3250">**FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3250">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="b9b02-3251">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3251">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="b9b02-3252">**FX_IO_ERROR (0x90)** Błąd we/wy sterownika.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3252">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3253">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3253">Allowed From</span></span>

<span data-ttu-id="b9b02-3254">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3254">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3255">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3255">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3256">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3256">See Also</span></span>

- <span data-ttu-id="b9b02-3257">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3257">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-3258">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3258">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-3259">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3259">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-3260">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3260">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-3261">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3261">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-3262">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-3262">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-3263">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-3263">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-3264">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-3264">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-3265">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3265">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-3266">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-3266">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-3267">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3267">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-3268">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-3268">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-3269">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3269">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-3270">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3270">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-3271">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-3271">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-3272">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-3272">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-3273">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-3273">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-3274">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3274">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-3275">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3275">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-3276">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3276">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="b9b02-3277">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3277">fx_unicode_directory_rename</span></span>

<span data-ttu-id="b9b02-3278">Zmienia nazwę katalogu przy użyciu ciągu Unicode</span><span class="sxs-lookup"><span data-stu-id="b9b02-3278">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3279">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3279">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="b9b02-3280">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3280">Description</span></span>

<span data-ttu-id="b9b02-3281">Ta usługa zmienia podkatalog o nazwie Unicode, aby określić nową nazwę Unicode w bieżącym katalogu roboczy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3281">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="b9b02-3282">Parametry nazwy Unicode nie mogą zawierać informacji o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3282">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-3283">*Ta usługa nie jest obsługiwana na nośnikach exFAT.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3283">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3284">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3284">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3285">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3285">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-3286">**old_unicode_name:** wskaźnik do nazwy Unicode dla bieżącego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3286">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="b9b02-3287">**old_unicode_name_length:** długość bieżącej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3287">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="b9b02-3288">**new_unicode_name:** wskaźnik do nowej nazwy pliku Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3288">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="b9b02-3289">**old_unicode_name_length:** długość nowej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3289">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="b9b02-3290">**new_short_name:** wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3) dla zmienionego pliku Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3290">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="b9b02-3291">Zmiana nazwy katalogu na Unicode</span><span class="sxs-lookup"><span data-stu-id="b9b02-3291">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3292">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3292">Return Values</span></span>

- <span data-ttu-id="b9b02-3293">**FX_SUCCESS** (0x00) Nośnik został otwarty pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3293">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="b9b02-3294">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3294">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3295">**FX_ALREADY_CREATED** (0x0B) Określona nazwa katalogu już istnieje.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3295">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="b9b02-3296">**FX_IO_ERROR** (0x90) sterownika We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3296">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-3297">**FX_PTR_ERROR** (0x18) Co najmniej jeden wskaźnik ma wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3297">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="b9b02-3298">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3298">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="b9b02-3299">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3299">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3300">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3300">Allowed From</span></span>

<span data-ttu-id="b9b02-3301">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3302">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3302">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3303">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3303">See Also</span></span>

- <span data-ttu-id="b9b02-3304">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3304">fx_directory_attributes_read</span></span>
- <span data-ttu-id="b9b02-3305">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3305">fx_directory_attributes_set</span></span>
- <span data-ttu-id="b9b02-3306">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3306">fx_directory_create</span></span>
- <span data-ttu-id="b9b02-3307">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3307">fx_directory_default_get</span></span>
- <span data-ttu-id="b9b02-3308">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3308">fx_directory_default_set</span></span>
- <span data-ttu-id="b9b02-3309">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-3309">fx_directory_delete</span></span>
- <span data-ttu-id="b9b02-3310">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-3310">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="b9b02-3311">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-3311">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="b9b02-3312">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3312">fx_directory_information_get</span></span>
- <span data-ttu-id="b9b02-3313">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="b9b02-3313">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="b9b02-3314">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3314">fx_directory_local_path_get</span></span>
- <span data-ttu-id="b9b02-3315">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="b9b02-3315">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="b9b02-3316">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3316">fx_directory_local_path_set</span></span>
- <span data-ttu-id="b9b02-3317">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3317">fx_directory_long_name_get</span></span>
- <span data-ttu-id="b9b02-3318">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="b9b02-3318">fx_directory_name_test</span></span>
- <span data-ttu-id="b9b02-3319">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-3319">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="b9b02-3320">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="b9b02-3320">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="b9b02-3321">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3321">fx_directory_rename</span></span>
- <span data-ttu-id="b9b02-3322">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3322">fx_directory_short_name_get</span></span>
- <span data-ttu-id="b9b02-3323">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3323">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="b9b02-3324">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3324">fx_unicode_file_create</span></span>

<span data-ttu-id="b9b02-3325">Tworzy plik Unicode</span><span class="sxs-lookup"><span data-stu-id="b9b02-3325">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3326">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3326">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-3327">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3327">Description</span></span>

<span data-ttu-id="b9b02-3328">Ta usługa tworzy plik o nazwie Unicode w bieżącym katalogu domyślnym — żadne informacje o ścieżce nie są dozwolone w parametrze nazwy źródła Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3328">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="b9b02-3329">Jeśli to się powiedzie, usługa zwróci krótką nazwę (format 8.3) nowo utworzonego pliku Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3329">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="b9b02-3330">*Wszystkie operacje na pliku Unicode (otwieranie, zapisywanie, odczytywanie, zamykanie itp.) powinny być wykonywane przez dostarczenie zwracanej krótkiej nazwy (w formacie 8.3) do standardowych usług plików FileX.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3330">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3331">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3331">Input Parameters</span></span>


- <span data-ttu-id="b9b02-3332">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3332">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-3333">**source_unicode_name:** wskaźnik do nazwy Unicode dla nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3333">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="b9b02-3334">**source_unicode_length:** długość nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3334">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="b9b02-3335">**short_name:** Wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3) dla nowego pliku Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3335">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3336">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3336">Return Values</span></span>

- <span data-ttu-id="b9b02-3337">**FX_SUCCESS** (0x00) Pomyślne utworzenie pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3337">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="b9b02-3338">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3338">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3339">**FX_ALREADY_CREATED** (0x0B) Określony plik już istnieje.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3339">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="b9b02-3340">**FX_NO_MORE_SPACE** (0x0A) Brak dostępnych klastrów na nośniku dla nowego wpisu pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3340">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="b9b02-3341">**FX_NOT_IMPLEMENTED** (0x22) service not implemented for exFAT file system (Usługa nie zaimplementowana dla systemu plików exFAT).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3341">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="b9b02-3342">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3342">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-3343">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3343">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="b9b02-3344">**FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3344">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="b9b02-3345">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3345">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3346">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3346">Allowed From</span></span>

<span data-ttu-id="b9b02-3347">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3347">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3348">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3348">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3349">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3349">See Also</span></span>

- <span data-ttu-id="b9b02-3350">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3350">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-3351">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3351">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-3352">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3352">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-3353">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3353">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3354">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3354">fx_file_close</span></span>
- <span data-ttu-id="b9b02-3355">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3355">fx_file_create</span></span>
- <span data-ttu-id="b9b02-3356">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3356">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-3357">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-3357">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-3358">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3358">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-3359">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3359">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3360">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3360">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-3361">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3361">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-3362">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3362">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-3363">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3363">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-3364">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3364">fx_file_open</span></span>
- <span data-ttu-id="b9b02-3365">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3365">fx_file_read</span></span>
- <span data-ttu-id="b9b02-3366">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3366">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-3367">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3367">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-3368">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3368">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-3369">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3369">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-3370">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3370">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-3371">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3371">fx_file_write</span></span>
- <span data-ttu-id="b9b02-3372">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3372">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-3373">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3373">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-3374">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3374">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-3375">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3375">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="b9b02-3376">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3376">fx_unicode_file_rename</span></span>

<span data-ttu-id="b9b02-3377">Zmienia nazwę pliku przy użyciu ciągu Unicode</span><span class="sxs-lookup"><span data-stu-id="b9b02-3377">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3378">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3378">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="b9b02-3379">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3379">Description</span></span>

<span data-ttu-id="b9b02-3380">Ta usługa zmienia nazwę pliku o nazwie Unicode na określoną nową nazwę Unicode w bieżącym katalogu domyślnym.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3380">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="b9b02-3381">Parametry nazwy Unicode nie mogą zawierać informacji o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3381">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-3382">*Ta usługa nie jest obsługiwana na nośnikach exFAT.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3382">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3383">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3383">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3384">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3384">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-3385">**old_unicode_name:** Wskaźnik do nazwy Unicode dla bieżącego pliku.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3385">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="b9b02-3386">**old_unicode_name_length:** długość bieżącej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3386">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="b9b02-3387">**new_unicode_name:** Wskaźnik do nowej nazwy pliku Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3387">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="b9b02-3388">**new_unicode_name_length:** długość nowej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3388">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="b9b02-3389">**new_short_name:** Wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3) dla zmienionego pliku Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3389">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3390">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3390">Return Values</span></span>


- <span data-ttu-id="b9b02-3391">**FX_SUCCESS** (0x00) Otwieranie nośnika pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3391">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="b9b02-3392">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3392">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3393">**FX_ALREADY_CREATED** (0x0B) Określona nazwa pliku już istnieje.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3393">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="b9b02-3394">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3394">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-3395">**FX_PTR_ERROR** (0x18) Co najmniej jeden wskaźnik ma wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3395">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="b9b02-3396">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3396">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="b9b02-3397">**FX_WRITE_PROTECT** (0x23) Określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3397">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3398">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3398">Allowed From</span></span>

<span data-ttu-id="b9b02-3399">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3400">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3400">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3401">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3401">See Also</span></span>

- <span data-ttu-id="b9b02-3402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3402">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-3403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3403">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-3404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3404">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-3405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3406">fx_file_close</span></span>
- <span data-ttu-id="b9b02-3407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3407">fx_file_create</span></span>
- <span data-ttu-id="b9b02-3408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3408">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-3409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-3409">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-3410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-3411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-3413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3413">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-3414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-3415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-3416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3416">fx_file_open</span></span>
- <span data-ttu-id="b9b02-3417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3417">fx_file_read</span></span>
- <span data-ttu-id="b9b02-3418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3418">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-3419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3419">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-3420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3420">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-3421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3421">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-3422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3422">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-3423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3423">fx_file_write</span></span>
- <span data-ttu-id="b9b02-3424">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3424">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-3425">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3425">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-3426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3426">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-3427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3427">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="b9b02-3428">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3428">fx_unicode_length_get</span></span>

<span data-ttu-id="b9b02-3429">Pobiera długość nazwy Unicode</span><span class="sxs-lookup"><span data-stu-id="b9b02-3429">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3430">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3430">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="b9b02-3431">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3431">Description</span></span>

<span data-ttu-id="b9b02-3432">Ta usługa określa długość podanej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3432">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="b9b02-3433">Znak Unicode jest reprezentowany przez dwa bajty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3433">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="b9b02-3434">Nazwa Unicode to seria dwóch bajtów znaków Unicode zakończonych przez dwa bajty NULL (dwa bajty o wartości 0).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3434">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3435">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3435">Input Parameters</span></span>

<span data-ttu-id="b9b02-3436">**unicode_name:** Wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3436">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3437">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3437">Return Values</span></span>

<span data-ttu-id="b9b02-3438">**length:** długość nazwy Unicode (liczba znaków Unicode w nazwie).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3438">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3439">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3439">Allowed From</span></span>

<span data-ttu-id="b9b02-3440">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3440">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3441">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3441">Example</span></span>

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3442">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3442">See Also</span></span>

- <span data-ttu-id="b9b02-3443">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3443">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-3444">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3444">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-3445">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3445">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-3446">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3446">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3447">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3447">fx_file_close</span></span>
- <span data-ttu-id="b9b02-3448">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3448">fx_file_create</span></span>
- <span data-ttu-id="b9b02-3449">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3449">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-3450">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-3450">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-3451">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3451">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-3452">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3452">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3453">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3453">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-3454">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3454">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-3455">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3455">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-3456">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3456">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-3457">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3457">fx_file_open</span></span>
- <span data-ttu-id="b9b02-3458">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3458">fx_file_read</span></span>
- <span data-ttu-id="b9b02-3459">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3459">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-3460">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3460">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-3461">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3461">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-3462">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3462">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-3463">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3463">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-3464">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3464">fx_file_write</span></span>
- <span data-ttu-id="b9b02-3465">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3465">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-3466">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3466">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-3467">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3467">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-3468">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3468">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-3469">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3469">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="b9b02-3470">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="b9b02-3470">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="b9b02-3471">Pobiera długość nazwy Unicode</span><span class="sxs-lookup"><span data-stu-id="b9b02-3471">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3472">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3472">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="b9b02-3473">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3473">Description</span></span>

<span data-ttu-id="b9b02-3474">Ta usługa pobiera długość podanej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3474">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="b9b02-3475">Znak Unicode jest reprezentowany przez dwa bajty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3475">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="b9b02-3476">Nazwa Unicode to seria dwubajtowych znaków Unicode zakończonych przez dwa bajty NULL (dwa bajty o wartości 0).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3476">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-3477">*Ta usługa jest taka sama **jak fx_unicode_length_get(),** z wyjątkiem tego, że wywołujący przekazuje rozmiar **buforu unicode_name,** w tym dwa znaki NULL.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3477">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3478">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3478">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3479">**unicode_name:** Wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3479">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="b9b02-3480">**buffer_length:** rozmiar bufora nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3480">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3481">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3481">Return Values</span></span>

<span data-ttu-id="b9b02-3482">**length:** długość nazwy Unicode (liczba znaków Unicode w nazwie).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3482">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3483">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3483">Allowed From</span></span>

<span data-ttu-id="b9b02-3484">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3484">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3485">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3485">Example</span></span>

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3486">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3486">See Also</span></span>

- <span data-ttu-id="b9b02-3487">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3487">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-3488">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3488">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-3489">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3489">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-3490">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3490">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3491">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3491">fx_file_close</span></span>
- <span data-ttu-id="b9b02-3492">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3492">fx_file_create</span></span>
- <span data-ttu-id="b9b02-3493">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3493">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-3494">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-3494">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-3495">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3495">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-3496">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3496">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3497">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3497">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-3498">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3498">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-3499">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3499">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-3500">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3500">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-3501">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3501">fx_file_open</span></span>
- <span data-ttu-id="b9b02-3502">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3502">fx_file_read</span></span>
- <span data-ttu-id="b9b02-3503">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3503">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-3504">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3504">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-3505">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3505">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-3506">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3506">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-3507">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3507">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-3508">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3508">fx_file_write</span></span>
- <span data-ttu-id="b9b02-3509">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3509">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-3510">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3510">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-3511">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3511">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-3512">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3512">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-3513">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3513">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="b9b02-3514">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3514">fx_unicode_name_get</span></span>

<span data-ttu-id="b9b02-3515">Pobiera nazwę Unicode z krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="b9b02-3515">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3516">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3516">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="b9b02-3517">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3517">Description</span></span>

<span data-ttu-id="b9b02-3518">Ta usługa pobiera nazwę Unicode skojarzoną z podaną krótką nazwą (format 8.3) w bieżącym katalogu domyślnym — w parametrze krótkiej nazwy nie są dozwolone żadne informacje o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3518">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="b9b02-3519">Jeśli to się powiedzie, usługa zwróci nazwę Unicode skojarzoną z krótką nazwą.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3519">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-3520">*Ta usługa może służyć do uzyskania nazw Unicode dla plików i podkatalogów.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3520">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3521">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3521">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3522">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3522">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-3523">**short_name** Wskaźnik na krótką nazwę (format 8.3).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3523">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="b9b02-3524">**destination_unicode_name:** wskaźnik do miejsca docelowego dla nazwy Unicode skojarzonej z podaną krótką nazwą.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3524">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="b9b02-3525">**destination_unicode_length:** Wskaźnik do zwracanych nazw Unicode o długości.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3525">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3526">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3526">Return Values</span></span>

- <span data-ttu-id="b9b02-3527">**FX_SUCCESS** (0x00) Pomyślne pobranie nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3527">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="b9b02-3528">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać tabeli FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3528">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="b9b02-3529">**FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-3529">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-3530">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-3531">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3531">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3532">**FX_NOT_FOUND** (0x04) Nie znaleziono krótkiej nazwy lub rozmiar docelowy Unicode jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3532">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="b9b02-3533">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3533">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-3534">**FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3534">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="b9b02-3535">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3535">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3536">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3536">Allowed From</span></span>

<span data-ttu-id="b9b02-3537">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3537">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3538">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3538">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3539">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3539">See Also</span></span>

- <span data-ttu-id="b9b02-3540">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3540">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-3541">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3541">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-3542">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3542">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-3543">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3543">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3544">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3544">fx_file_close</span></span>
- <span data-ttu-id="b9b02-3545">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3545">fx_file_create</span></span>
- <span data-ttu-id="b9b02-3546">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3546">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-3547">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-3547">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-3548">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3548">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-3549">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3549">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3550">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3550">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-3551">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3551">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-3552">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3552">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-3553">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3553">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-3554">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3554">fx_file_open</span></span>
- <span data-ttu-id="b9b02-3555">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3555">fx_file_read</span></span>
- <span data-ttu-id="b9b02-3556">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3556">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-3557">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3557">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-3558">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3558">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-3559">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3559">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-3560">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3560">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-3561">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3561">fx_file_write</span></span>
- <span data-ttu-id="b9b02-3562">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3562">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-3563">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3563">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-3564">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3564">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-3565">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3565">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="b9b02-3566">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="b9b02-3566">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="b9b02-3567">Pobiera nazwę Unicode z krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="b9b02-3567">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3568">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3568">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="b9b02-3569">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3569">Description</span></span>

<span data-ttu-id="b9b02-3570">Ta usługa pobiera nazwę Unicode skojarzoną z podaną krótką nazwą (format 8.3) w bieżącym katalogu domyślnym — w parametrze krótkiej nazwy nie są dozwolone żadne informacje o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3570">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="b9b02-3571">Jeśli to się powiedzie, usługa zwróci nazwę Unicode skojarzoną z krótką nazwą.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3571">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-3572">\*Ta usługa jest taka sama jak \***fx_unicode_name_get**, z tą różnicą, że obiekt wywołujący dostarcza rozmiar docelowego _bufora Unicode jako argument wejściowy. Dzięki temu usługa może zagwarantować, że docelowy bufor Unicode nie zostanie nadpisyny_</span><span class="sxs-lookup"><span data-stu-id="b9b02-3572">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-3573">*Ta usługa może służyć do uzyskania nazw Unicode dla plików i podkatalogów.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3573">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3574">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3574">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3575">**media_ptr:** wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3575">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-3576">**short_name:** wskaźnik na krótką nazwę (format 8.3).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3576">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="b9b02-3577">**destination_unicode_name:** wskaźnik do miejsca docelowego dla nazwy Unicode skojarzonej z podaną krótką nazwą.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3577">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="b9b02-3578">**destination_unicode_length:** Wskaźnik do zwracanych nazw Unicode o długości.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3578">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="b9b02-3579">**unicode_name_buffer_length:** rozmiar buforu nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3579">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="b9b02-3580">Uwaga: wymagany jest terminator o wartości NULL, co sprawia, że dodatkowy bajt.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3580">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3581">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3581">Return Values</span></span>

- <span data-ttu-id="b9b02-3582">**FX_SUCCESS** (0x00) Pomyślne pobranie nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3582">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="b9b02-3583">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać tabeli FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3583">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="b9b02-3584">**FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-3584">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-3585">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3585">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-3586">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3586">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3587">**FX_NOT_FOUND** (0x04) Nie znaleziono krótkiej nazwy lub rozmiar docelowy Unicode jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3587">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="b9b02-3588">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3588">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-3589">**FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3589">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="b9b02-3590">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3590">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3591">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3591">Allowed From</span></span>

<span data-ttu-id="b9b02-3592">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3592">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3593">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3593">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3594">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3594">See Also</span></span>

- <span data-ttu-id="b9b02-3595">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3595">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-3596">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3596">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-3597">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3597">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-3598">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3598">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3599">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3599">fx_file_close</span></span>
- <span data-ttu-id="b9b02-3600">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3600">fx_file_create</span></span>
- <span data-ttu-id="b9b02-3601">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3601">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-3602">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-3602">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-3603">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3603">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-3604">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3604">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3605">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3605">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-3606">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3606">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-3607">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3607">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-3608">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3608">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-3609">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3609">fx_file_open</span></span>
- <span data-ttu-id="b9b02-3610">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3610">fx_file_read</span></span>
- <span data-ttu-id="b9b02-3611">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3611">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-3612">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3612">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-3613">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3613">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-3614">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3614">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-3615">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3615">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-3616">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3616">fx_file_write</span></span>
- <span data-ttu-id="b9b02-3617">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3617">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-3618">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3618">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-3619">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3619">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-3620">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3620">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="b9b02-3621">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3621">fx_unicode_short_name_get</span></span>

<span data-ttu-id="b9b02-3622">Pobiera krótką nazwę z nazwy Unicode</span><span class="sxs-lookup"><span data-stu-id="b9b02-3622">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3623">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3623">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="b9b02-3624">Ta usługa pobiera krótką nazwę (format 8.3) skojarzoną z nazwą Unicode w bieżącym katalogu domyślnym — żadne informacje o ścieżce nie są dozwolone w parametrze nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3624">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="b9b02-3625">Jeśli to się powiedzie, usługa zwróci krótką nazwę skojarzoną z nazwą Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3625">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-3626">*Ta usługa może służyć do uzyskania krótkich nazw dla plików i podkatalogów.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3626">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3627">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3627">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3628">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3628">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-3629">**source_unicode_name:** Wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3629">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="b9b02-3630">**source_unicode_length:** długość nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3630">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="b9b02-3631">**destination_short_name:** wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3631">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="b9b02-3632">Musi to być co najmniej 13 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3632">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3633">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3633">Return Values</span></span>

- <span data-ttu-id="b9b02-3634">**FX_SUCCESS** (0x00) Pomyślne pobranie krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3634">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="b9b02-3635">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać tabeli FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3635">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="b9b02-3636">**FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-3636">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="b9b02-3637">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3637">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-3638">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3638">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3639">**FX_NOT_FOUND** (0x04) Nie znaleziono nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3639">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="b9b02-3640">**FX_NOT_IMPLEMENTED** (0x22) service not implemented for exFAT file system (Usługa nie zaimplementowana dla systemu plików exFAT).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3640">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="b9b02-3641">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3641">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-3642">**FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3642">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="b9b02-3643">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3643">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3644">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3644">Allowed From</span></span>

<span data-ttu-id="b9b02-3645">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3645">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3646">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3646">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3647">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3647">See Also</span></span>

- <span data-ttu-id="b9b02-3648">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3648">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-3649">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3649">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-3650">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3650">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-3651">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3651">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3652">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3652">fx_file_close</span></span>
- <span data-ttu-id="b9b02-3653">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3653">fx_file_create</span></span>
- <span data-ttu-id="b9b02-3654">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3654">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-3655">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-3655">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-3656">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3656">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-3657">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3657">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3658">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3658">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-3659">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3659">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-3660">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3660">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-3661">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3661">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-3662">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3662">fx_file_open</span></span>
- <span data-ttu-id="b9b02-3663">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3663">fx_file_read</span></span>
- <span data-ttu-id="b9b02-3664">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3664">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-3665">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3665">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-3666">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3666">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-3667">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3667">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-3668">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3668">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-3669">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3669">fx_file_write</span></span>
- <span data-ttu-id="b9b02-3670">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3670">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-3671">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3671">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-3672">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3672">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-3673">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3673">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="b9b02-3674">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="b9b02-3674">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="b9b02-3675">Pobiera krótką nazwę z nazwy Unicode</span><span class="sxs-lookup"><span data-stu-id="b9b02-3675">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="b9b02-3676">Prototype</span><span class="sxs-lookup"><span data-stu-id="b9b02-3676">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="b9b02-3677">Opis</span><span class="sxs-lookup"><span data-stu-id="b9b02-3677">Description</span></span>

<span data-ttu-id="b9b02-3678">Ta usługa pobiera krótką nazwę (format 8.3) skojarzoną z nazwą Unicode w bieżącym katalogu domyślnym — żadne informacje o ścieżce nie są dozwolone w parametrze nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3678">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="b9b02-3679">Jeśli to się powiedzie, usługa zwróci krótką nazwę skojarzoną z nazwą Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3679">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9b02-3680">*Ta usługa jest taka sama **fx_unicode_short_name_get()**, z tą różnicą, że obiekt wywołujący dostarcza rozmiar buforu docelowego jako argument wejściowy. Dzięki temu usługa może zagwarantować, że krótka nazwa nie przekroczy buforu docelowego.*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3680">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="b9b02-3681">*Ta usługa może służyć do uzyskania krótkich nazw dla plików i podkatalogów*</span><span class="sxs-lookup"><span data-stu-id="b9b02-3681">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="b9b02-3682">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="b9b02-3682">Input Parameters</span></span>

- <span data-ttu-id="b9b02-3683">**media_ptr:** Wskaźnik do bloku sterowania multimediami.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3683">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="b9b02-3684">**source_unicode_name:** Wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3684">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="b9b02-3685">**source_unicode_length:** długość nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3685">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="b9b02-3686">**destination_short_name:** wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8.3).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3686">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="b9b02-3687">Musi to być co najmniej 13 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3687">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="b9b02-3688">**short_name_buffer_length:** rozmiar buforu docelowego.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3688">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="b9b02-3689">Rozmiar buforu musi być co najmniej 14 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3689">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="b9b02-3690">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="b9b02-3690">Return Values</span></span>

- <span data-ttu-id="b9b02-3691">**FX_SUCCESS** (0x00) Pomyślne pobranie krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3691">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="b9b02-3692">**FX_FAT_READ_ERROR** (0x03) Nie można odczytać tabeli FAT.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3692">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="b9b02-3693">**FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="b9b02-3693">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="b9b02-3694">**FX_IO_ERROR** (0x90) Sterownik We/Wy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3694">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="b9b02-3695">**FX_MEDIA_NOT_OPEN** (0x11) Określony nośnik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3695">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="b9b02-3696">**FX_NOT_FOUND** (0x04) Nie znaleziono nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3696">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="b9b02-3697">**FX_NOT_IMPLEMENTED** (0x22) service not implemented for exFAT file system (Usługa nie zaimplementowana dla systemu plików exFAT).</span><span class="sxs-lookup"><span data-stu-id="b9b02-3697">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="b9b02-3698">**FX_SECTOR_INVALID** (0x89) Nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3698">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="b9b02-3699">**FX_PTR_ERROR** (0x18) Nieprawidłowe wskaźniki nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3699">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="b9b02-3700">**FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="b9b02-3700">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="b9b02-3701">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="b9b02-3701">Allowed From</span></span>

<span data-ttu-id="b9b02-3702">Wątki</span><span class="sxs-lookup"><span data-stu-id="b9b02-3702">Threads</span></span>

### <a name="example"></a><span data-ttu-id="b9b02-3703">Przykład</span><span class="sxs-lookup"><span data-stu-id="b9b02-3703">Example</span></span>

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="b9b02-3704">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9b02-3704">See Also</span></span>

- <span data-ttu-id="b9b02-3705">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3705">fx_file_allocate</span></span>
- <span data-ttu-id="b9b02-3706">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3706">fx_file_attributes_read</span></span>
- <span data-ttu-id="b9b02-3707">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3707">fx_file_attributes_set</span></span>
- <span data-ttu-id="b9b02-3708">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3708">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3709">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="b9b02-3709">fx_file_close</span></span>
- <span data-ttu-id="b9b02-3710">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3710">fx_file_create</span></span>
- <span data-ttu-id="b9b02-3711">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3711">fx_file_date_time_set</span></span>
- <span data-ttu-id="b9b02-3712">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="b9b02-3712">fx_file_delete</span></span>
- <span data-ttu-id="b9b02-3713">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3713">fx_file_extended_allocate</span></span>
- <span data-ttu-id="b9b02-3714">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3714">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="b9b02-3715">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3715">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="b9b02-3716">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3716">fx_file_extended_seek</span></span>
- <span data-ttu-id="b9b02-3717">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3717">fx_file_extended_truncate</span></span>
- <span data-ttu-id="b9b02-3718">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3718">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="b9b02-3719">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="b9b02-3719">fx_file_open</span></span>
- <span data-ttu-id="b9b02-3720">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="b9b02-3720">fx_file_read</span></span>
- <span data-ttu-id="b9b02-3721">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3721">fx_file_relative_seek</span></span>
- <span data-ttu-id="b9b02-3722">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3722">fx_file_rename</span></span>
- <span data-ttu-id="b9b02-3723">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="b9b02-3723">fx_file_seek</span></span>
- <span data-ttu-id="b9b02-3724">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="b9b02-3724">fx_file_truncate</span></span>
- <span data-ttu-id="b9b02-3725">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="b9b02-3725">fx_file_truncate_release</span></span>
- <span data-ttu-id="b9b02-3726">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="b9b02-3726">fx_file_write</span></span>
- <span data-ttu-id="b9b02-3727">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="b9b02-3727">fx_file_write_notify_set</span></span>
- <span data-ttu-id="b9b02-3728">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="b9b02-3728">fx_unicode_file_create</span></span>
- <span data-ttu-id="b9b02-3729">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="b9b02-3729">fx_unicode_file_rename</span></span>
- <span data-ttu-id="b9b02-3730">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3730">fx_unicode_name_get</span></span>
- <span data-ttu-id="b9b02-3731">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="b9b02-3731">fx_unicode_short_name_get</span></span>
