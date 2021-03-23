---
title: Rozdział 4 — Opis usług Azure RTO FileX Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO FileX w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c9e91244856b322d53f85bdd572bd317a055776a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822447"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="2d0d2-103">Rozdział 4 — Opis usług Azure RTO FileX Services</span><span class="sxs-lookup"><span data-stu-id="2d0d2-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="2d0d2-104">Ten rozdział zawiera opis wszystkich usług Azure RTO FileX w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="2d0d2-105">Nazwy usług są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="2d0d2-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="2d0d2-107">Odczytuje atrybuty katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-108">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="2d0d2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-109">Description</span></span>

<span data-ttu-id="2d0d2-110">Ta usługa odczytuje atrybuty katalogu z określonego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-111">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-111">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-112">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-113">**directory_name**: wskaźnik do nazwy żądanego katalogu (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="2d0d2-114">**atrybuty** _Ptr: wskaźnik do miejsca docelowego dla atrybutów katalogu, które mają zostać umieszczone.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="2d0d2-115">Atrybuty katalogu są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="2d0d2-116">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="2d0d2-117">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="2d0d2-118">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="2d0d2-119">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="2d0d2-120">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="2d0d2-121">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-122">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-122">Return Values</span></span>

- <span data-ttu-id="2d0d2-123">Odczytane atrybuty katalogu pomyślnego **FX_SUCCESS** (0x00)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="2d0d2-124">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="2d0d2-125">**Znaleziono _NOT FX** (0X04) określony katalog nie został znaleziony na nośniku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="2d0d2-126">Wpis **FX_NOT_DIRECTORY** (0x0E) nie jest katalogiem</span><span class="sxs-lookup"><span data-stu-id="2d0d2-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="2d0d2-127">Błąd we/wy sterownika **FX_IO_ERROR** (0x90)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="2d0d2-128">Plik **FX_FILE_CORRUPT** 0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-129">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="2d0d2-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="2d0d2-130">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT</span><span class="sxs-lookup"><span data-stu-id="2d0d2-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="2d0d2-131">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-132">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="2d0d2-133">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="2d0d2-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="2d0d2-134">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-135">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-135">Allowed From</span></span>

<span data-ttu-id="2d0d2-136">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-138">See Also</span></span>

- <span data-ttu-id="2d0d2-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-140">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-141">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-142">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-143">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-146">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-152">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-155">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="2d0d2-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="2d0d2-160">Ustawia atrybuty katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="2d0d2-162">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-162">Description</span></span>

<span data-ttu-id="2d0d2-163">Ta usługa Ustawia atrybuty katalogu dla obiektów określonych przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-164">*Ta aplikacja może modyfikować podzestaw atrybutów katalogu w tej usłudze. Wszystkie próby ustawienia dodatkowych atrybutów spowodują wystąpienie błędu.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-165">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-165">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-166">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-167">**directory_name**: wskaźnik do nazwy żądanego katalogu (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="2d0d2-168">**atrybuty**: nowe atrybuty do tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="2d0d2-169">Prawidłowe atrybuty katalogu są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="2d0d2-170">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="2d0d2-171">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="2d0d2-172">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="2d0d2-173">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-174">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-174">Return Values</span></span>

- <span data-ttu-id="2d0d2-175">**FX_SUCCESS** (0x00) — pomyślny zestaw atrybutów katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="2d0d2-176">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="2d0d2-177">Nie znaleziono podanego katalogu **FX_NOT_FOUND** (0x04) na nośniku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="2d0d2-178">Wpis **FX_NOT_DIRECTORY** (0x0E) nie jest katalogiem</span><span class="sxs-lookup"><span data-stu-id="2d0d2-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="2d0d2-179">Błąd we/wy sterownika **FX_IO_ERROR** (0x90)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="2d0d2-180">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem</span><span class="sxs-lookup"><span data-stu-id="2d0d2-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="2d0d2-181">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-182">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="2d0d2-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="2d0d2-183">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT</span><span class="sxs-lookup"><span data-stu-id="2d0d2-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="2d0d2-184">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-185">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="2d0d2-186">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="2d0d2-187">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="2d0d2-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="2d0d2-188">**FX_INVALID_ATTR** (0x19) wybrano nieprawidłowe atrybuty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="2d0d2-189">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-190">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-190">Allowed From</span></span>

<span data-ttu-id="2d0d2-191">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-192">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-193">See Also</span></span>

- <span data-ttu-id="2d0d2-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-195">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-196">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-197">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-198">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-201">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-207">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-210">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="2d0d2-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-214">fx_directory_create</span></span>

<span data-ttu-id="2d0d2-215">Tworzy podkatalog</span><span class="sxs-lookup"><span data-stu-id="2d0d2-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-216">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="2d0d2-217">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-217">Description</span></span>

<span data-ttu-id="2d0d2-218">Ta usługa tworzy podkatalog w bieżącym katalogu domyślnym lub w ścieżce podanej w nazwie katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="2d0d2-219">W przeciwieństwie do katalogu głównego w podkatalogach nie ma limitu liczby plików, które mogą być przechowywane.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="2d0d2-220">Katalog główny może zawierać tylko liczbę wpisów określoną przez rekord rozruchowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-221">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-221">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-222">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-223">**directory_name**: wskaźnik do nazwy katalogu do utworzenia (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-224">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-224">Return Values</span></span>

- <span data-ttu-id="2d0d2-225">**FX_SUCCESS** (0X00) pomyślne utworzenie katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="2d0d2-226">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="2d0d2-227">Nie znaleziono podanego katalogu **FX_NOT_FOUND** (0x04) na nośniku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="2d0d2-228">Wpis **FX_NOT_DIRECTORY** (0x0E) nie jest katalogiem</span><span class="sxs-lookup"><span data-stu-id="2d0d2-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="2d0d2-229">Błąd we/wy sterownika **FX_IO_ERROR** (0x90)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="2d0d2-230">Plik **_CORRUPT FX_FILE** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-231">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="2d0d2-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="2d0d2-232">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT</span><span class="sxs-lookup"><span data-stu-id="2d0d2-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="2d0d2-233">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-234">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="2d0d2-235">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="2d0d2-236">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="2d0d2-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="2d0d2-237">**FX_INVALID_ATTR** (0x19) wybrano nieprawidłowe atrybuty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="2d0d2-238">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-239">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-239">Allowed From</span></span>

<span data-ttu-id="2d0d2-240">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-241">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-242">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-242">See Also</span></span>

- <span data-ttu-id="2d0d2-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-245">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-246">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-247">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-250">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-256">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-259">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="2d0d2-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-263">fx_directory_default_get</span></span>

<span data-ttu-id="2d0d2-264">Pobiera ostatni katalog domyślny</span><span class="sxs-lookup"><span data-stu-id="2d0d2-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-265">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-266">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-266">Description</span></span>

<span data-ttu-id="2d0d2-267">Ta usługa zwraca wskaźnik do ścieżki ostatnio ustawionej przez ***fx_directory_default_set***.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="2d0d2-268">Jeśli domyślny katalog nie został ustawiony lub bieżący katalog domyślny jest katalogiem głównym, zwracana jest wartość FX_NULL.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-269">*Domyślny rozmiar ciągu ścieżki wewnętrznej to 256 znaków; można ją zmienić, modyfikując **FX_MAXIMUM_PATH** w **fx_api. h** i przebudować całą bibliotekę FileX. Ścieżka ciągu znaków jest utrzymywana dla aplikacji i nie jest używana wewnętrznie przez FileX.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-270">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-270">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-271">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-272">**return_path_name**: wskaźnik do lokalizacji docelowej dla ostatniego ciągu katalogu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="2d0d2-273">Wartość FX_NULL jest zwracana, jeśli bieżące ustawienie domyślnego katalogu jest katalogiem głównym.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="2d0d2-274">Gdy nośnik zostanie otwarty, domyślnie jest to katalog główny.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-275">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-275">Return Values</span></span>

- <span data-ttu-id="2d0d2-276">**FX_SUCCESS** (0X00) pomyślne pobieranie katalogu domyślnego</span><span class="sxs-lookup"><span data-stu-id="2d0d2-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="2d0d2-277">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="2d0d2-278">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="2d0d2-279">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-280">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-280">Allowed From</span></span>

<span data-ttu-id="2d0d2-281">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-282">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-283">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-283">See Also</span></span>

- <span data-ttu-id="2d0d2-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-286">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-287">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-288">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-291">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-297">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-300">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="2d0d2-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-304">fx_directory_default_set</span></span>

<span data-ttu-id="2d0d2-305">Ustawia domyślny katalog</span><span class="sxs-lookup"><span data-stu-id="2d0d2-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-306">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-307">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-307">Description</span></span>

<span data-ttu-id="2d0d2-308">Ta usługa ustawia domyślny katalog nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="2d0d2-309">Jeśli zostanie podana wartość FX_NULL, domyślny katalog jest ustawiany na katalog główny nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="2d0d2-310">Wszystkie kolejne operacje na plikach, które nie określają jawnie ścieżki, będą domyślnie w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-311">*Domyślny rozmiar ciągu ścieżki wewnętrznej to 256 znaków; można ją zmienić, modyfikując **FX_MAXIMUM_PATH** w **fx_api. h** i przebudować całą bibliotekę FileX. Ścieżka ciągu znaków jest utrzymywana dla aplikacji i nie jest używana wewnętrznie przez FileX.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-312">*W przypadku nazw dostarczonych przez aplikację FileX obsługuje zarówno ukośniki odwrotne ( \\ ), jak i ukośniki (/) do oddzielnych katalogów, podkatalogów i nazw plików. Jednak FileX używa tylko znaku ukośnika odwrotnego w ścieżkach zwracanych do aplikacji.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-313">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-313">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-314">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-315">**new_path_name**: wskaźnik do nowej domyślnej nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="2d0d2-316">Jeśli zostanie podana wartość FX_NULL, domyślny katalog nośnika jest ustawiany na katalog główny nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-317">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-317">Return Values</span></span>

- <span data-ttu-id="2d0d2-318">**FX_SUCCESS** (0x00) pomyślnego domyślnego zestawu katalogów</span><span class="sxs-lookup"><span data-stu-id="2d0d2-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="2d0d2-319">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="2d0d2-320">Nie można odnaleźć nowego katalogu **FX_INVALID_PATH** (0x0D)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="2d0d2-321">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-322">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-323">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-323">Allowed From</span></span>

<span data-ttu-id="2d0d2-324">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-325">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-326">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-326">See Also</span></span>

- <span data-ttu-id="2d0d2-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-329">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-330">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-331">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-334">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-340">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-343">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="2d0d2-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-347">fx_directory_delete</span></span>

<span data-ttu-id="2d0d2-348">Usuwa podkatalog</span><span class="sxs-lookup"><span data-stu-id="2d0d2-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-349">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-350">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-350">Description</span></span>

<span data-ttu-id="2d0d2-351">Ta usługa usuwa określony katalog.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-351">This service deletes the specified directory.</span></span> <span data-ttu-id="2d0d2-352">Należy pamiętać, że katalog musi być pusty, aby go usunąć.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-353">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-353">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-354">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-355">**directory_name**: wskaźnik do nazwy katalogu do usunięcia (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-356">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-356">Return Values</span></span>

- <span data-ttu-id="2d0d2-357">**FX_SUCCESS** (0X00) pomyślne usunięcie katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="2d0d2-358">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="2d0d2-359">Nie znaleziono podanego katalogu **FX_NOT_FOUND** (0x04)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="2d0d2-360">**FX_DIR_NOT_EMPTY** (0X10) określony katalog nie jest pusty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="2d0d2-361">Błąd we/wy sterownika **FX_IO_ERROR** (0x90)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="2d0d2-362">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem</span><span class="sxs-lookup"><span data-stu-id="2d0d2-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="2d0d2-363">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-364">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="2d0d2-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="2d0d2-365">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT</span><span class="sxs-lookup"><span data-stu-id="2d0d2-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="2d0d2-366">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-367">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="2d0d2-368">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="2d0d2-369">**FX_NOT_DIRECTORY** (0X0E) nie jest pozycją katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="2d0d2-370">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="2d0d2-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="2d0d2-371">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-372">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-372">Allowed From</span></span>

<span data-ttu-id="2d0d2-373">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-374">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-375">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-375">See Also</span></span>

- <span data-ttu-id="2d0d2-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-378">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-379">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-380">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-383">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-389">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-392">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="2d0d2-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="2d0d2-397">Pobiera pierwszy wpis katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-398">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-399">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-399">Description</span></span>

<span data-ttu-id="2d0d2-400">Ta usługa Pobiera pierwszą nazwę wpisu w domyślnym katalogu i kopiuje ją do określonego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-401">*Określona lokalizacja docelowa musi być wystarczająco duża, aby pomieścić nazwę FileX o maksymalnym rozmiarze zdefiniowanym przez **FX_MAX_LONG_NAME_LEN.***</span><span class="sxs-lookup"><span data-stu-id="2d0d2-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-402">*Jeśli używasz ścieżki nielokalnej, ważne jest, aby zapobiec (z ThreadX semaforem, muteksem lub zmianami poziomu priorytetu) innych wątków aplikacji od zmiany tego katalogu podczas przechodzenia do katalogu. W przeciwnym razie można uzyskać nieprawidłowe wyniki.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-403">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-403">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-404">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-405">**return_entry_name**: wskaźnik do miejsca docelowego dla pierwszej nazwy wpisu w domyślnym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-406">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-406">Return Values</span></span>

- <span data-ttu-id="2d0d2-407">**FX_SUCCESS** (0X00) powodzenie pierwszego wpisu katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="2d0d2-408">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="2d0d2-409">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="2d0d2-410">Błąd we/wy sterownika **FX_IO_ERROR** (0x90)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="2d0d2-411">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-412">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="2d0d2-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="2d0d2-413">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT</span><span class="sxs-lookup"><span data-stu-id="2d0d2-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="2d0d2-414">**FX_PTR_ERROR** (0X18) nieprawidłowy nośnik lub wskaźnik docelowy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="2d0d2-415">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem</span><span class="sxs-lookup"><span data-stu-id="2d0d2-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-416">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-416">Allowed From</span></span>

<span data-ttu-id="2d0d2-417">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-418">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-419">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-419">See Also</span></span>

- <span data-ttu-id="2d0d2-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-422">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-423">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-424">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-425">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-427">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-433">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-436">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="2d0d2-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="2d0d2-441">Pobiera pierwszy wpis katalogu z pełnymi informacjami</span><span class="sxs-lookup"><span data-stu-id="2d0d2-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-442">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="2d0d2-443">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-443">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-444">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-445">**directory_name**: wskaźnik do lokalizacji docelowej dla nazwy wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="2d0d2-446">Musi być co najmniej tak duże jak FX_MAX_LONG_NAME_LEN.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="2d0d2-447">**atrybuty**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla atrybutów wpisu, które mają zostać umieszczone.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="2d0d2-448">Atrybuty są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="2d0d2-449">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="2d0d2-450">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="2d0d2-451">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="2d0d2-452">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="2d0d2-453">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="2d0d2-454">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="2d0d2-455">**rozmiar**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla rozmiaru wpisu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="2d0d2-456">**Year**: Jeśli wartość nie jest równa null, wskaźnik do lokalizacji docelowej dla pozycji rok modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="2d0d2-457">**miesiąc**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego w miesiącu modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="2d0d2-458">**dzień**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego w dniu modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="2d0d2-459">**godzina**: Jeśli wartość nie jest równa null, wskaźnik do lokalizacji docelowej dla godziny modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="2d0d2-460">**minuta**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla minuty modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="2d0d2-461">**Second**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla drugiej modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-462">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-462">Return Values</span></span>

- <span data-ttu-id="2d0d2-463">**FX_SUCCESS** (0X00) powodzenie pierwszego wpisu katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="2d0d2-464">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="2d0d2-465">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="2d0d2-466">Błąd we/wy sterownika **FX_IO_ERROR** (0x90)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="2d0d2-467">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem</span><span class="sxs-lookup"><span data-stu-id="2d0d2-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="2d0d2-468">Plik **_CORRUPT FX_FILE** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-469">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="2d0d2-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="2d0d2-470">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT</span><span class="sxs-lookup"><span data-stu-id="2d0d2-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="2d0d2-471">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-472">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="2d0d2-473">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="2d0d2-474">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-475">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-475">Allowed From</span></span>

<span data-ttu-id="2d0d2-476">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-477">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-477">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-478">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-478">See Also</span></span>

- <span data-ttu-id="2d0d2-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-481">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-482">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-483">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-484">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-486">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-492">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-495">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="2d0d2-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-499">fx_directory_information_get:</span></span>

<span data-ttu-id="2d0d2-500">Pobiera informacje o wpisie katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-501">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="2d0d2-502">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-502">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-503">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-504">**directory_name**: wskaźnik na nazwę wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="2d0d2-505">**atrybuty**: wskaźnik do miejsca docelowego dla atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="2d0d2-506">**rozmiar**: wskaźnik do miejsca docelowego dla rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="2d0d2-507">**Year**: wskaźnik do miejsca docelowego dla roku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="2d0d2-508">**miesiąc**: wskaźnik do miejsca docelowego dla miesiąca.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="2d0d2-509">**dzień**: wskaźnik do miejsca docelowego dla dnia.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="2d0d2-510">**Hour**: wskaźnik do miejsca docelowego dla godziny.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="2d0d2-511">**minuta**: wskaźnik do miejsca docelowego dla minuty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="2d0d2-512">**sekundę**: wskaźnik do miejsca docelowego dla drugiego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-513">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-513">Return Values</span></span>

- <span data-ttu-id="2d0d2-514">**FX_SUCCESS** (0X00) powodzenie pierwszego wpisu katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="2d0d2-515">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="2d0d2-516">Nie znaleziono podanego katalogu **FX_NOT_FOUND** (0x04) na nośniku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="2d0d2-517">Błąd we/wy sterownika **FX_IO_ERROR** (0x90)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="2d0d2-518">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="2d0d2-519">Plik **_CORRUPT FX_FILE** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-520">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT</span><span class="sxs-lookup"><span data-stu-id="2d0d2-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="2d0d2-521">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-522">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="2d0d2-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="2d0d2-523">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="2d0d2-524">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-525">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-525">Allowed From</span></span>

<span data-ttu-id="2d0d2-526">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-527">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-527">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-528">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-528">See Also</span></span>

- <span data-ttu-id="2d0d2-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-531">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-532">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-533">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-534">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-542">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-545">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="2d0d2-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="2d0d2-550">Czyści domyślną ścieżkę lokalną</span><span class="sxs-lookup"><span data-stu-id="2d0d2-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-551">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="2d0d2-552">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-552">Description</span></span>

<span data-ttu-id="2d0d2-553">Ta usługa czyści poprzednią ścieżkę lokalną skonfigurowaną dla wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-554">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-554">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-555">**media_ptr**: wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-556">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-556">Return Values</span></span>

- <span data-ttu-id="2d0d2-557">**FX_SUCCESS** (0x00) pomyślna ścieżka lokalna została wyczyszczona.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="2d0d2-558">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest obecnie otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="2d0d2-559">Zdefiniowano FX_NO_LCOAL_PATH **FX_NOT_IMPLEMENTED** (0x22)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="2d0d2-560">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="2d0d2-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-561">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-561">Allowed From</span></span>

<span data-ttu-id="2d0d2-562">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-563">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-564">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-564">See Also</span></span>

- <span data-ttu-id="2d0d2-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-567">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-568">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-569">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-570">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-573">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-578">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-581">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="2d0d2-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="2d0d2-586">Pobiera bieżący ciąg ścieżki lokalnej</span><span class="sxs-lookup"><span data-stu-id="2d0d2-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-587">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-588">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-588">Description</span></span>

<span data-ttu-id="2d0d2-589">Ta usługa zwraca wskaźnik ścieżki lokalnej określonego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="2d0d2-590">Jeśli nie ma ustawionej ścieżki lokalnej, do obiektu wywołującego zostaje zwrócona wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-591">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-591">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-592">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-593">**return_path_name**: wskaźnik do docelowego wskaźnika ciągu dla ciągu ścieżki lokalnej, który ma być przechowywany.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-594">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-594">Return Values</span></span>

- <span data-ttu-id="2d0d2-595">**FX_SUCCESS** (0x00) pomyślna ścieżka lokalna get.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="2d0d2-596">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest obecnie otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="2d0d2-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="2d0d2-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="2d0d2-598">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika</span><span class="sxs-lookup"><span data-stu-id="2d0d2-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="2d0d2-599">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-599">Allowed From</span></span>

<span data-ttu-id="2d0d2-600">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-601">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-602">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-602">See Also</span></span>

- <span data-ttu-id="2d0d2-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-605">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-606">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-607">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-608">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-611">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-616">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-619">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="2d0d2-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="2d0d2-624">Przywraca poprzednią ścieżkę lokalną</span><span class="sxs-lookup"><span data-stu-id="2d0d2-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-625">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="2d0d2-626">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-626">Description</span></span>

<span data-ttu-id="2d0d2-627">Ta usługa przywraca wcześniej ustawioną ścieżkę lokalną.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-627">This service restores a previously set local path.</span></span> <span data-ttu-id="2d0d2-628">Przywrócono także pozycję wyszukiwania w katalogu dla tej ścieżki lokalnej, co sprawia, że ta procedura jest przydatna w przechodzeniu katalogu cyklicznego przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-629">*Każda ścieżka lokalna zawiera ciąg **FX_MAXIMUM_PATH** w rozmiarze lokalnym, który domyślnie ma 256 znaków. Ten ciąg ścieżki wewnętrznej nie jest używany przez FileX i jest dostępny tylko dla użycia aplikacji. Jeśli **FX_LOCAL_PATH** ma być zadeklarowana jako zmienna lokalna, użytkownicy powinni mieć możliwość zmiany rozmiaru stosu. Użytkownicy mogą zmniejszyć rozmiar **FX_MAXIMUM_PATH** i ponownie skompilować Źródło biblioteki FileX.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-630">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-630">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-631">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-632">**local_path_ptr**: wskaźnik do wcześniej ustawionej ścieżki lokalnej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="2d0d2-633">Bardzo ważne jest, aby upewnić się, że ten wskaźnik faktycznie wskazuje poprzednio użytą i nadal niezmienioną ścieżkę lokalną.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-634">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-634">Return Values</span></span>

- <span data-ttu-id="2d0d2-635">**FX_SUCCESS** (0X00) pomyślne przywrócenie ścieżki lokalnej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="2d0d2-636">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="2d0d2-637">Zdefiniowano FX_NO_LCOAL_PATH **FX_NOT_IMPLEMENTED** (0x22).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="2d0d2-638">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik ścieżki lub nośnika lokalnego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-639">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-639">Allowed From</span></span>

<span data-ttu-id="2d0d2-640">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-641">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-642">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-642">See Also</span></span>

- <span data-ttu-id="2d0d2-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-645">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-646">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-647">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-648">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-651">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-656">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-659">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="2d0d2-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="2d0d2-664">Konfiguruje ścieżkę lokalną specyficzną dla wątku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-665">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-666">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-666">Description</span></span>

<span data-ttu-id="2d0d2-667">Ta usługa konfiguruje ścieżkę specyficzną dla wątku określoną przez \***new_path_string** _.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="2d0d2-668">Po pomyślnym zakończeniu tej procedury informacje o ścieżce lokalnej przechowywane w _ *_local_path_ptr_*\* mają pierwszeństwo przed globalną ścieżką nośnika dla wszystkich operacji plików i katalogów wykonywanych przez ten wątek.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="2d0d2-669">Nie będzie to miało wpływu na żaden inny wątek w systemie.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="2d0d2-670">*Domyślny rozmiar ciągu ścieżki lokalnej to 256 znaków; można ją zmienić, modyfikując **FX_MAXIMUM_PATH** w **fx_api. h** i przebudować całą bibliotekę FileX. Ścieżka ciągu znaków jest utrzymywana dla aplikacji i nie jest używana wewnętrznie przez FileX.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-671">*W przypadku nazw dostarczonych przez aplikację FileX obsługuje zarówno ukośniki odwrotne ( \\ ), jak i ukośniki (/) do oddzielnych katalogów, podkatalogów i nazw plików. Jednak FileX używa tylko znaku ukośnika odwrotnego w ścieżkach zwracanych do aplikacji.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-672">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-672">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-673">**media_ptr**: wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="2d0d2-674">**local_path_ptr**: miejsce docelowe przechowywania informacji o ścieżce lokalnej dla określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="2d0d2-675">Adres tej struktury może być dostarczony do funkcji przywracania ścieżki lokalnej w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="2d0d2-676">**new_path_name**: Określa ścieżkę lokalną do Instalatora.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-677">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-677">Return Values</span></span>

- <span data-ttu-id="2d0d2-678">**FX_SUCCESS** (0x00) pomyślnego domyślnego zestawu katalogów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="2d0d2-679">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-680">**FX_NOT_IMPLEMENTED** (0x22) \* \* FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="2d0d2-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="2d0d2-681">Nie można odnaleźć nowego katalogu **FX_INVALID_PATH** (0x0D).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="2d0d2-682">**FX_NOT_IMPLEMENTED** (0x22)-\* \* FX_NO_LOCAL_PATH jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="2d0d2-683">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik ścieżki lub nośnika lokalnego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-684">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-684">Allowed From</span></span>

<span data-ttu-id="2d0d2-685">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-686">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-686">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-687">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-687">See Also</span></span>

- <span data-ttu-id="2d0d2-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-690">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-691">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-692">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-693">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-696">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-701">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-704">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="2d0d2-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="2d0d2-709">Pobiera długą nazwę z krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-710">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-711">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-711">Description</span></span>

<span data-ttu-id="2d0d2-712">Ta usługa pobiera długą nazwę (jeśli istnieje) skojarzoną z nazwą podanej krótkiej (8,3 formatu).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="2d0d2-713">Krótką nazwą może być nazwa pliku lub nazwa katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-714">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-714">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-715">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-716">**short_name**: wskaźnik na krótką nazwę źródła (format 8,3).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="2d0d2-717">**long_name**: wskaźnik do miejsca docelowego dla długiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="2d0d2-718">Jeśli nie ma długiej nazwy, zwracana jest krótka nazwa.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="2d0d2-719">Należy pamiętać, że miejsce docelowe dla długiej nazwy musi być wystarczająco duże, aby pomieścić FX_MAX_LONG_NAME_LEN znaki.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-720">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-720">Return Values</span></span>

- <span data-ttu-id="2d0d2-721">**FX_SUCCESS** (0x00) pomyślnej długiej nazwy Get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="2d0d2-722">Nie znaleziono krótkiej nazwy **FX_NOT_FOUND** (0x04)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="2d0d2-723">Błąd we/wy sterownika **FX_IO_ERROR** (0x90)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="2d0d2-724">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="2d0d2-725">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-726">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor</span><span class="sxs-lookup"><span data-stu-id="2d0d2-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="2d0d2-727">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT</span><span class="sxs-lookup"><span data-stu-id="2d0d2-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="2d0d2-728">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-729">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="2d0d2-730">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem</span><span class="sxs-lookup"><span data-stu-id="2d0d2-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-731">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-731">Allowed From</span></span>

<span data-ttu-id="2d0d2-732">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-733">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-734">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-734">See Also</span></span>

- <span data-ttu-id="2d0d2-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-737">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-738">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-739">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-740">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-743">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-748">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-751">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="2d0d2-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="2d0d2-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="2d0d2-756">Pobiera długą nazwę z krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-757">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="2d0d2-758">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-758">Description</span></span>

<span data-ttu-id="2d0d2-759">Ta usługa pobiera długą nazwę (jeśli istnieje) skojarzoną z nazwą podanej krótkiej (8,3 formatu).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="2d0d2-760">Krótką nazwą może być nazwa pliku lub nazwa katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-761">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-761">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-762">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-763">**short_name**: wskaźnik na krótką nazwę źródła (format 8,3).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="2d0d2-764">**long_name**: wskaźnik do miejsca docelowego dla długiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="2d0d2-765">Jeśli nie ma długiej nazwy, zwracana jest krótka nazwa.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="2d0d2-766">Uwaga: miejsce docelowe dla długiej nazwy musi być wystarczająco duże, aby można było przechowywać **FX_MAX_LONG_NAME_LEN** znaków.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="2d0d2-767">**long_file_name_buffer_length**: długość buforu długiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-768">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-768">Return Values</span></span>

- <span data-ttu-id="2d0d2-769">**FX_SUCCESS** (0x00) pomyślnej długiej nazwy get.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="2d0d2-770">Nie znaleziono krótkiej nazwy **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="2d0d2-771">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-772">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="2d0d2-773">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-774">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-775">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-776">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="2d0d2-777">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="2d0d2-778">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-779">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-779">Allowed From</span></span>

<span data-ttu-id="2d0d2-780">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-781">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-782">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-782">See Also</span></span>

- <span data-ttu-id="2d0d2-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-785">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-786">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-787">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-788">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-791">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-799">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="2d0d2-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-803">fx_directory_name_test</span></span>

<span data-ttu-id="2d0d2-804">Testy katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-805">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-806">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-806">Description</span></span>

<span data-ttu-id="2d0d2-807">Ta usługa sprawdza, czy podana nazwa jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="2d0d2-808">Jeśli tak, zwracany jest FX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-809">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-809">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-810">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-811">**directory_name**: wskaźnik na nazwę wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-812">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-812">Return Values</span></span>

- <span data-ttu-id="2d0d2-813">Nazwa podana **FX_SUCCESS** (0x00) jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="2d0d2-814">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty</span><span class="sxs-lookup"><span data-stu-id="2d0d2-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="2d0d2-815">Nie można odnaleźć wpisu katalogu **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="2d0d2-816">Wpis **FX_NOT_DIRECTORY** (0x0E) nie jest katalogiem</span><span class="sxs-lookup"><span data-stu-id="2d0d2-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="2d0d2-817">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-818">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="2d0d2-819">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-820">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-821">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-822">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="2d0d2-823">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="2d0d2-824">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-825">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-825">Allowed From</span></span>

<span data-ttu-id="2d0d2-826">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-827">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-828">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-828">See Also</span></span>

- <span data-ttu-id="2d0d2-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-831">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-832">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-833">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-834">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-837">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-845">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="2d0d2-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="2d0d2-849">Wybiera Następny wpis katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-850">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-851">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-851">Description</span></span>

<span data-ttu-id="2d0d2-852">Ta usługa zwraca następną nazwę wpisu w bieżącym katalogu domyślnym.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-853">*Jeśli używasz ścieżki nielokalnej, ważne jest również, aby zapobiegać (z ThreadX semaforem lub priorytetem wątku) innych wątków aplikacji od zmiany tego katalogu podczas przechodzenia do katalogu. W przeciwnym razie można uzyskać nieprawidłowe wyniki.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-854">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-854">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-855">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-856">**return_entry_name**: wskaźnik do miejsca docelowego dla kolejnej nazwy wpisu w domyślnym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="2d0d2-857">Bufor, do którego wskazuje, musi być wystarczająco duży, aby pomieścić maksymalny rozmiar nazwy FileX zdefiniowanej przez **_FX_MAX_LONG_NAME_LEN_**.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-858">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-858">Return Values</span></span>

- <span data-ttu-id="2d0d2-859">**FX_SUCCESS** (0X00) pomyślne znalezienie następnego wpisu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="2d0d2-860">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-861">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="2d0d2-862">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-863">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-864">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-865">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-866">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-867">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-868">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-869">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-869">Allowed From</span></span>

<span data-ttu-id="2d0d2-870">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-871">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-872">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-872">See Also</span></span>

- <span data-ttu-id="2d0d2-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-875">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-876">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-877">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-878">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-881">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-887">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-889">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="2d0d2-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="2d0d2-894">Pobiera Następny wpis katalogu z pełnymi informacjami</span><span class="sxs-lookup"><span data-stu-id="2d0d2-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-895">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-895">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="2d0d2-896">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-896">Description</span></span>

<span data-ttu-id="2d0d2-897">Ta usługa pobiera następną nazwę wpisu w domyślnym katalogu i kopiuje ją do określonego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="2d0d2-898">Zwraca również pełne informacje o wpisie określone przez dodatkowe parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-899">\* Określone miejsce docelowe musi być wystarczająco duże, aby pomieścić maksymalną FileX nazwę, zgodnie z definicją przez \* \* \* FX_MAX_LONG_NAME_LEN \* \* \* \*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-900">*Jeśli używasz ścieżki nielokalnej, ważne jest, aby zapobiec (z ThreadX semaforem, muteksem lub zmianami poziomu priorytetu) innych wątków aplikacji od zmiany tego katalogu podczas przechodzenia do katalogu. W przeciwnym razie można uzyskać nieprawidłowe wyniki.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-901">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-901">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-902">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-903">**directory_name**: wskaźnik do lokalizacji docelowej dla nazwy wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="2d0d2-904">Musi być co najmniej tak duże jak **FX_MAX_LONG_NAME_LEN**.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="2d0d2-905">**atrybuty**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla atrybutów wpisu, które mają zostać umieszczone. Atrybuty są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="2d0d2-906">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="2d0d2-907">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="2d0d2-908">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="2d0d2-909">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="2d0d2-910">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="2d0d2-911">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="2d0d2-912">**rozmiar**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla rozmiaru wpisu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="2d0d2-913">**miesiąc**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego w miesiącu modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="2d0d2-914">**Year**: Jeśli wartość nie jest równa null, wskaźnik do lokalizacji docelowej dla pozycji rok modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="2d0d2-915">**dzień**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego w dniu modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="2d0d2-916">**godzina**: Jeśli wartość nie jest równa null, wskaźnik do lokalizacji docelowej dla godziny modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="2d0d2-917">**minuta**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla minuty modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="2d0d2-918">**Second**: Jeśli wartość nie jest równa null, wskaźnik do miejsca docelowego dla drugiej modyfikacji wpisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-919">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-919">Return Values</span></span>

- <span data-ttu-id="2d0d2-920">**FX_SUCCESS** (0X00) powodzenie następnego wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="2d0d2-921">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-922">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="2d0d2-923">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-924">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-925">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-926">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-927">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="2d0d2-928">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="2d0d2-929">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub wszystkie parametry wejściowe mają wartość null.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="2d0d2-930">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-931">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-931">Allowed From</span></span>

<span data-ttu-id="2d0d2-932">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-933">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-933">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-934">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-934">See Also</span></span>

- <span data-ttu-id="2d0d2-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-937">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-938">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-939">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-940">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-943">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-949">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-951">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="2d0d2-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-955">fx_directory_rename</span></span>

<span data-ttu-id="2d0d2-956">Zmienia nazwę katalogu</span><span class="sxs-lookup"><span data-stu-id="2d0d2-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-957">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-958">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-958">Description</span></span>

<span data-ttu-id="2d0d2-959">Ta usługa zmienia nazwę katalogu na określoną nazwę nowego katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="2d0d2-960">Zmiana nazwy jest również wykonywana względem określonej ścieżki lub ścieżki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="2d0d2-961">Jeśli ścieżka zostanie określona w nowej nazwie katalogu, katalog nazw zostanie skutecznie przeniesiony do określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="2d0d2-962">Jeśli ścieżka nie zostanie określona, katalog o zmienionej nazwie zostanie umieszczony w bieżącej ścieżce domyślnej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-963">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-963">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-964">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-965">**old_directory_name**: wskaźnik do bieżącej nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="2d0d2-966">**new_directory_name**: wskaźnik do nowej nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-967">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-967">Return Values</span></span>

- <span data-ttu-id="2d0d2-968">**FX_SUCCESS** (0x00) pomyślna zmiana nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="2d0d2-969">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-970">Nie można odnaleźć wpisu katalogu **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="2d0d2-971">Wpis **FX_NOT_DIRECTORY** (0x0E) nie jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="2d0d2-972">**FX_INVALID_NAME** (0x0c) Nazwa nowego katalogu jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="2d0d2-973">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-974">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-975">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-976">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-977">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-978">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="2d0d2-979">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="2d0d2-980">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="2d0d2-981">**FX_INVALID_PATH** (0x0D) podano nieprawidłową ścieżkę z nazwą katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="2d0d2-982">**FX_ALREADY_CREATED** (0X0B) określony katalog został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="2d0d2-983">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-984">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-985">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-985">Allowed From</span></span>

<span data-ttu-id="2d0d2-986">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-987">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-988">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-988">See Also</span></span>

- <span data-ttu-id="2d0d2-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-991">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-992">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-993">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-994">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-997">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="2d0d2-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="2d0d2-1010">Pobiera krótką nazwę z długiej nazwy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1011">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-1012">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1012">Description</span></span>

<span data-ttu-id="2d0d2-1013">Ta usługa pobiera krótką nazwę (8,3 format) skojarzoną z podaną długą nazwą.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="2d0d2-1014">Długa nazwa może być nazwą pliku lub nazwą katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1015">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1015">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1016">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-1017">**long_name**: wskaźnik do długiej nazwy źródłowej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="2d0d2-1018">**short_name**: wskaźnik do lokalizacji docelowej short name (format 8,3).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="2d0d2-1019">Należy pamiętać, że miejsce docelowe dla krótkiej nazwy musi być wystarczająco duże, aby pomieścić 14 znaków.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1020">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1020">Return Values</span></span>

- <span data-ttu-id="2d0d2-1021">**FX_SUCCESS** (0x00) pomyślna krótka nazwa get.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="2d0d2-1022">Nie znaleziono długiej nazwy **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="2d0d2-1023">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1024">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1025">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1026">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1027">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1028">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-1029">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="2d0d2-1030">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="2d0d2-1031">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1032">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1032">Allowed From</span></span>

<span data-ttu-id="2d0d2-1033">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1034">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1035">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1035">See Also</span></span>

- <span data-ttu-id="2d0d2-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1038">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1041">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1053">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="2d0d2-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="2d0d2-1057">Pobiera krótką nazwę z długiej nazwy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1058">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="2d0d2-1059">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1059">Description</span></span>

<span data-ttu-id="2d0d2-1060">Ta usługa pobiera krótką nazwę (8,3 format) skojarzoną z podaną długą nazwą.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="2d0d2-1061">Długa nazwa może być nazwą pliku lub nazwą katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1062">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1062">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1063">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-1064">**long_name**: wskaźnik do długiej nazwy źródłowej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="2d0d2-1065">**short_name**: wskaźnik do lokalizacji docelowej short name (format 8,3).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="2d0d2-1066">Uwaga: miejsce docelowe dla krótkiej nazwy musi być wystarczająco duże, aby można było zawierać 14 znaków.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="2d0d2-1067">**short_file_name_length**: długość buforu krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1068">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1068">Return Values</span></span>

- <span data-ttu-id="2d0d2-1069">**FX_SUCCESS** (0x00) pomyślna krótka nazwa get.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="2d0d2-1070">Nie znaleziono długiej nazwy **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="2d0d2-1071">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1072">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1073">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1074">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1075">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1076">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-1077">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="2d0d2-1078">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="2d0d2-1079">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1080">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1080">Allowed From</span></span>

<span data-ttu-id="2d0d2-1081">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1082">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1083">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1083">See Also</span></span>

- <span data-ttu-id="2d0d2-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1086">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1089">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1101">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="2d0d2-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="2d0d2-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="2d0d2-1105">Włącza usługę odporną na uszkodzenia</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1106">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="2d0d2-1107">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1107">Description</span></span>

<span data-ttu-id="2d0d2-1108">Ta usługa umożliwia korzystanie z modułu odpornego na błędy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="2d0d2-1109">Po uruchomieniu moduł odporny na uszkodzenia wykrywa, czy system plików jest w obszarze Ochrona odporna na uszkodzenia FileX.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="2d0d2-1110">Jeśli tak nie jest, usługa odnajdzie dostępne sektory w systemie plików w celu przechowywania dzienników w transakcjach w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="2d0d2-1111">Jeśli system plików jest w obszarze Ochrona odporna na uszkodzenia FileX, stosuje dzienniki do systemu plików, aby zachować jego integralność.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1112">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1112">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1113">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-1114">**memory_ptr**: wskaźnik do bloku pamięci używanej przez moduł odporny na uszkodzenia jako pamięć zapasową.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="2d0d2-1115">**memory_size**: rozmiar pamięci tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="2d0d2-1116">Aby odporność na uszkodzenia działała prawidłowo, rozmiar pamięci podręcznej wynosi co najmniej 3072 bajtów i musi być wielokrotnością rozmiaru sektora.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1117">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1117">Return Values</span></span>

- <span data-ttu-id="2d0d2-1118">**FX_SUCCESS** (0X00) pomyślnie włączyła odporność na uszkodzenia.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="2d0d2-1119">Rozmiar pamięci **FX_NOT_ENOUGH_MEMORY** (0x91) jest za mały.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="2d0d2-1120">Błąd sektora rozruchowego **FX_BOOT_ERROR** (0x01).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="2d0d2-1121">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1122">**FX_NO_MORE_ENTRIES** (0X0F) nie jest dostępny żaden bezpłatny klaster.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="2d0d2-1123">Nośnik **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej liczby dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="2d0d2-1124">Sektor **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="2d0d2-1125">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1126">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-1127">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1128">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1128">Allowed From</span></span>

<span data-ttu-id="2d0d2-1129">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1130">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1131">See Also</span></span>

- <span data-ttu-id="2d0d2-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1132">fx_system_initialize</span></span>
- <span data-ttu-id="2d0d2-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1133">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1135">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1136">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1140">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1141">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1142">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1144">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1145">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="2d0d2-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1149">fx_file_allocate</span></span>

<span data-ttu-id="2d0d2-1150">Przydziela miejsce dla pliku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1151">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1152">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1152">Description</span></span>

<span data-ttu-id="2d0d2-1153">Ta usługa przydziela i łączy co najmniej jeden klaster ciągły na końcu określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="2d0d2-1154">FileX określa liczbę klastrów wymaganych przez podzielenie żądanego rozmiaru przez liczbę bajtów na klaster.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="2d0d2-1155">Następnie wynik zostanie zaokrąglony do następnego całego klastra.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="2d0d2-1156">Aby przydzielić miejsce poza 4 GB, aplikacja używa *fx_file_extended_allocate* usługi.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1157">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1157">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1158">**file_ptr**: wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="2d0d2-1159">**rozmiar**: liczba bajtów do przydzielenia dla pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1160">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1160">Return Values</span></span>

- <span data-ttu-id="2d0d2-1161">Pomyślna alokacja pliku **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="2d0d2-1162">Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="2d0d2-1163">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1164">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1165">Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="2d0d2-1166">**FX_NO_MORE_ENTRIES** (0X0F) nie jest dostępny żaden bezpłatny klaster.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="2d0d2-1167">Nośnik **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej liczby dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="2d0d2-1168">Sektor **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="2d0d2-1169">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1170">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1171">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-1172">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1173">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1173">Allowed From</span></span>

<span data-ttu-id="2d0d2-1174">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1175">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1176">See Also</span></span>

- <span data-ttu-id="2d0d2-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1180">fx_file_close — fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1182">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1189">fx_file_open — fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1191">fx_file_rename — fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1192">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1194">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="2d0d2-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="2d0d2-1201">Odczytuje atrybuty pliku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1202">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1203">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1203">Description</span></span>

<span data-ttu-id="2d0d2-1204">Ta usługa odczytuje atrybuty pliku z określonego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1205">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1205">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1206">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-1207">**file_name**: wskaźnik do nazwy żądanego pliku (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="2d0d2-1208">**attributes_ptr**: wskaźnik do miejsca docelowego dla atrybutów pliku, które mają zostać umieszczone.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="2d0d2-1209">Atrybuty pliku są zwracane w formacie mapy bitowej z następującymi możliwymi ustawieniami:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="2d0d2-1210">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="2d0d2-1211">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="2d0d2-1212">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="2d0d2-1213">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="2d0d2-1214">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="2d0d2-1215">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1216">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1216">Return Values</span></span>

- <span data-ttu-id="2d0d2-1217">Odczytano atrybut **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="2d0d2-1218">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-1219">Nie znaleziono określonego pliku **FX_NOT_FOUND** (0x04) na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="2d0d2-1220">**FX_NOT_A_FILE** (0X05) określony plik jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="2d0d2-1221">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1222">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1223">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-1224">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-1225">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1226">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="2d0d2-1227">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1228">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1228">Allowed From</span></span>

<span data-ttu-id="2d0d2-1229">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1230">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1231">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1231">See Also</span></span>

- <span data-ttu-id="2d0d2-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1232">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1235">fx_file_close — fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1237">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1244">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1245">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1247">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1248">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1249">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1251">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="2d0d2-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="2d0d2-1258">Ustawia atrybuty plików</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1259">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1260">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1260">Description</span></span>

<span data-ttu-id="2d0d2-1261">Ta usługa Ustawia atrybuty pliku na określone przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-1262">*Aplikacja może tylko modyfikować podzestaw atrybutów pliku za pomocą tej usługi. Wszystkie próby ustawienia dodatkowych atrybutów spowodują wystąpienie błędu.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1263">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1263">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1264">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-1265">**file_name**: wskaźnik do nazwy żądanego pliku \* \* (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="2d0d2-1266">**atrybuty**: nowe atrybuty dla tego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="2d0d2-1267">Prawidłowe atrybuty pliku są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="2d0d2-1268">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="2d0d2-1269">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="2d0d2-1270">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="2d0d2-1271">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1272">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1272">Return Values</span></span>

- <span data-ttu-id="2d0d2-1273">Pomyślny zestaw atrybutów **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="2d0d2-1274">Plik **FX_ACCESS_ERROR** (0x06) jest otwarty i nie może mieć ustawionych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="2d0d2-1275">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1276">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1277">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-1278">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w tabeli FAT lub exFAT klastra.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="2d0d2-1279">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="2d0d2-1280">Nie znaleziono określonego pliku **FX_NOT_FOUND** (0x04) na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="2d0d2-1281">**FX_NOT_A_FILE** (0X05) określony plik jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="2d0d2-1282">Sektor **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="2d0d2-1283">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1284">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1285">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="2d0d2-1286">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-1287">**FX_INVALID_ATTR** (0x19) wybrano nieprawidłowe atrybuty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="2d0d2-1288">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1289">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1289">Allowed From</span></span>

<span data-ttu-id="2d0d2-1290">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1291">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1292">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1292">See Also</span></span>

- <span data-ttu-id="2d0d2-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1293">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1296">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1297">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1299">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1306">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1307">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1309">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1310">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1311">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1313">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="2d0d2-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="2d0d2-1320">Najlepsze wysiłki w celu przydzielenia miejsca na plik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1321">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1322">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1322">Description</span></span>

<span data-ttu-id="2d0d2-1323">Ta usługa przydziela i łączy co najmniej jeden klaster ciągły na końcu określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="2d0d2-1324">FileX określa liczbę klastrów wymaganych przez podzielenie żądanego rozmiaru przez liczbę bajtów na klaster.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="2d0d2-1325">Następnie wynik zostanie zaokrąglony do następnego całego klastra.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="2d0d2-1326">Jeśli nie ma wystarczającej liczby kolejnych klastrów dostępnych na nośniku, ta usługa łączy największy dostępny blok kolejnych klastrów do pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="2d0d2-1327">Ilość miejsca, w którym faktycznie przydzielono plik, jest zwracana do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="2d0d2-1328">Aby przydzielić miejsce poza 4 GB, aplikacja używa *fx_file_extended_best_effort_allocate* usługi.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1329">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1329">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1330">**file_ptr**: wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="2d0d2-1331">**rozmiar**: liczba bajtów do przydzielenia dla pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1332">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1332">Return Values</span></span>

- <span data-ttu-id="2d0d2-1333">**FX_SUCCESS** (0X00) pomyślne przydzielenie plików o najlepszej nakładności.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="2d0d2-1334">Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="2d0d2-1335">Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="2d0d2-1336">Nośnik **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej liczby dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="2d0d2-1337">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1338">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1339">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1340">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-1341">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1342">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1343">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku lub miejsce docelowe.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="2d0d2-1344">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1345">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1345">Allowed From</span></span>

<span data-ttu-id="2d0d2-1346">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1347">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1348">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1348">See Also</span></span>

- <span data-ttu-id="2d0d2-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1349">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1352">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1353">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1355">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1362">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1363">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1365">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1366">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1367">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1369">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="2d0d2-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1375">fx_file_close</span></span>

<span data-ttu-id="2d0d2-1376">Zamyka plik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1377">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1378">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1378">Description</span></span>

<span data-ttu-id="2d0d2-1379">Ta usługa zamyka określony plik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1379">This service closes the specified file.</span></span> <span data-ttu-id="2d0d2-1380">Jeśli plik był otwarty do zapisu i jeśli został zmodyfikowany, ta usługa ukończy proces modyfikacji plików przez zaktualizowanie jego wpisu katalogu o nowy rozmiar i bieżącą datę i godzinę systemową.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1381">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1381">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1382">**file_ptr**: wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1383">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1383">Return Values</span></span>

- <span data-ttu-id="2d0d2-1384">Plik **FX_SUCCESS** (0x00) został pomyślnie zamknięty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="2d0d2-1385">**FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="2d0d2-1386">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1387">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1388">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1389">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="2d0d2-1390">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1391">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1391">Allowed From</span></span>

<span data-ttu-id="2d0d2-1392">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1393">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1394">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1394">See Also</span></span>

- <span data-ttu-id="2d0d2-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1395">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1399">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1401">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1408">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1409">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1411">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1412">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1413">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1415">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="2d0d2-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1421">fx_file_create</span></span>

<span data-ttu-id="2d0d2-1422">Tworzy plik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1423">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1424">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1424">Description</span></span>

<span data-ttu-id="2d0d2-1425">Ta usługa tworzy określony plik w katalogu domyślnym lub w ścieżce katalogu podanej z nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-1426">*Ta usługa tworzy plik o zerowej długości, czyli nie przydzielono żadnych klastrów. Alokacja będzie odbywać się automatycznie przy kolejnych zapisach plików lub może zostać wykonana z wyprzedzeniem za pomocą usługi fx_file_allocate lub fx_file_extended_allocate miejsca na miejsce poza 4 GB).*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1427">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1427">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1428">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-1429">**file_name**: wskaźnik do nazwy pliku do utworzenia (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1430">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1430">Return Values</span></span>

- <span data-ttu-id="2d0d2-1431">**FX_SUCCESS** (0X00) pomyślnie utworzono plik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="2d0d2-1432">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-1433">**FX_ALREADY_CREATED** (0X0B) określony plik został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="2d0d2-1434">**FX_NO_MORE_SPACE** (0x0A) nie ma więcej wpisów w katalogu głównym lub nie ma więcej dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="2d0d2-1435">**FX_INVALID_PATH** (0x0D) podano nieprawidłową ścieżkę z nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="2d0d2-1436">Nazwa pliku **FX_INVALID_NAME** (0x0c) jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="2d0d2-1437">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1438">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1439">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1440">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-1441">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-1442">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="2d0d2-1443">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1444">Nośnik bazowy **FX_WRITE_PROTECT** (0x23) jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1445">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nazwy nośnika lub pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="2d0d2-1446">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1447">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1447">Allowed From</span></span>

<span data-ttu-id="2d0d2-1448">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1449">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1450">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1450">See Also</span></span>
- <span data-ttu-id="2d0d2-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1451">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1455">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1457">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1464">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1465">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1467">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1468">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1469">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1471">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="2d0d2-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="2d0d2-1478">Ustawia datę i godzinę pliku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1478">Sets file date and time</span></span>

<span data-ttu-id="2d0d2-1479">Ustawianie daty i godziny pliku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1480">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1480">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="2d0d2-1481">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1481">Description</span></span>

<span data-ttu-id="2d0d2-1482">Ta usługa ustawia datę i godzinę określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1483">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1483">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1484">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-1485">**file_name**: wskaźnik na nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="2d0d2-1486">**Year**: wartość roku (1980-2107 włącznie).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="2d0d2-1487">**miesiąc**: wartość miesiąca (1-12 włącznie).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="2d0d2-1488">**dzień**: wartość dnia (1-31 włącznie).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="2d0d2-1489">**godzina**: wartość godziny (0-23 włącznie).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="2d0d2-1490">**minuta**: wartość minuty (0-59 włącznie).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="2d0d2-1491">**sekunda**: wartość sekunda (0-59 włącznie).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1492">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1492">Return Values</span></span>

- <span data-ttu-id="2d0d2-1493">Data i godzina pomyślnego **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="2d0d2-1494">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-1495">Nie znaleziono pliku **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="2d0d2-1496">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1497">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1498">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1499">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-1500">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="2d0d2-1501">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1502">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1503">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="2d0d2-1504">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="2d0d2-1505">**FX_INVALID_YEAR** (0x12) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="2d0d2-1506">**FX_INVALID_MONTH** (0X13) miesiąc jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="2d0d2-1507">**FX_INVALID_DAY** (0x14) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="2d0d2-1508">**FX_INVALID_HOUR** (0X15) godzina jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="2d0d2-1509">**FX_INVALID_MINUTE** (0X16) minuta jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="2d0d2-1510">**FX_INVALID_SECOND** (0X17) s jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1511">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1511">Allowed From</span></span>

<span data-ttu-id="2d0d2-1512">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1513">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1514">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1514">See Also</span></span>

- <span data-ttu-id="2d0d2-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1515">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1519">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1520">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1521">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1528">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1529">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1531">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1532">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1533">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1535">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="2d0d2-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="2d0d2-1542">Usuwa plik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1542">Deletes file</span></span>

<span data-ttu-id="2d0d2-1543">Usuwanie pliku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1544">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1545">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1545">Description</span></span>

<span data-ttu-id="2d0d2-1546">Ta usługa usuwa określony plik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1547">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1547">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1548">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-1549">**file_name**: wskaźnik do nazwy pliku do usunięcia (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1550">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1550">Return Values</span></span>

- <span data-ttu-id="2d0d2-1551">Pomyślnie usunięto plik **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="2d0d2-1552">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-1553">Nie znaleziono określonego pliku **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="2d0d2-1554">**FX_NOT_A_FILE** (0X05) określona nazwa pliku jest katalogiem lub woluminem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="2d0d2-1555">**FX_ACCESS_ERROR** (0X06) określony plik jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="2d0d2-1556">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1557">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1558">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1559">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-1560">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-1561">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1562">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1563">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="2d0d2-1564">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-1565">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1566">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1566">Allowed From</span></span>

<span data-ttu-id="2d0d2-1567">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1568">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1569">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1569">See Also</span></span>

- <span data-ttu-id="2d0d2-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1570">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1574">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1575">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1583">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1584">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1586">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1587">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1588">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1590">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="2d0d2-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="2d0d2-1597">Przydziela miejsce dla pliku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1598">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1599">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1599">Description</span></span>

<span data-ttu-id="2d0d2-1600">Ta usługa przydziela i łączy co najmniej jeden klaster ciągły na końcu określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="2d0d2-1601">FileX określa liczbę klastrów wymaganych przez podzielenie żądanego rozmiaru przez liczbę bajtów na klaster.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="2d0d2-1602">Następnie wynik zostanie zaokrąglony do następnego całego klastra.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="2d0d2-1603">Ta usługa została zaprojektowana do exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="2d0d2-1604">Parametr *size* przyjmuje 64-bitową wartość całkowitą, która umożliwia obiektowi wywołującemu wstępne przydzielanie miejsca poza 4 GB zakresem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1605">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1605">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1606">**file_ptr**: wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="2d0d2-1607">**rozmiar**: liczba bajtów do przydzielenia dla pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1608">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1608">Return Values</span></span>

- <span data-ttu-id="2d0d2-1609">Pomyślna alokacja pliku **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="2d0d2-1610">Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="2d0d2-1611">Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="2d0d2-1612">Nośnik **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej liczby dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="2d0d2-1613">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1614">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1615">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1616">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-1617">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1618">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1619">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-1620">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1621">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1621">Allowed From</span></span>

<span data-ttu-id="2d0d2-1622">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1623">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1624">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1624">See Also</span></span>

- <span data-ttu-id="2d0d2-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1625">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1629">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1630">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1632">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1638">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1639">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1641">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1642">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1643">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1645">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="2d0d2-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="2d0d2-1652">Najlepsze wysiłki w celu przydzielenia miejsca na plik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1653">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1654">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1654">Description</span></span>

<span data-ttu-id="2d0d2-1655">Ta usługa przydziela i łączy co najmniej jeden klaster ciągły na końcu określonego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="2d0d2-1656">FileX określa liczbę klastrów wymaganych przez podzielenie żądanego rozmiaru przez liczbę bajtów na klaster.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="2d0d2-1657">Następnie wynik zostanie zaokrąglony do następnego całego klastra.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="2d0d2-1658">Jeśli nie ma wystarczającej liczby kolejnych klastrów dostępnych na nośniku, ta usługa łączy największy dostępny blok kolejnych klastrów do pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="2d0d2-1659">Ilość miejsca, w którym faktycznie przydzielono plik, jest zwracana do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="2d0d2-1660">Ta usługa została zaprojektowana do exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="2d0d2-1661">Parametr *size* przyjmuje 64-bitową wartość całkowitą, która umożliwia obiektowi wywołującemu wstępne przydzielanie miejsca poza 4 GB zakresem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1662">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1662">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1663">**file_ptr**: wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="2d0d2-1664">**rozmiar**: liczba bajtów do przydzielenia dla pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1665">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1665">Return Values</span></span>

- <span data-ttu-id="2d0d2-1666">Pomyślna alokacja pliku **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="2d0d2-1667">Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="2d0d2-1668">Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="2d0d2-1669">Nośnik **FX_NO_MORE_SPACE** (0x0A) skojarzony z tym plikiem nie ma wystarczającej liczby dostępnych klastrów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="2d0d2-1670">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1671">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1672">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1673">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-1674">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1675">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1676">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-1677">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1678">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1678">Allowed From</span></span>

<span data-ttu-id="2d0d2-1679">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1680">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1680">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-1681">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1681">See Also</span></span>

- <span data-ttu-id="2d0d2-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1682">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1686">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1687">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1689">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1695">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1696">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1698">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1699">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1700">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1702">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="2d0d2-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="2d0d2-1709">Położenie do względnego przesunięcia bajtów</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1710">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1711">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1711">Description</span></span>

<span data-ttu-id="2d0d2-1712">Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego względnego przesunięcia bajtu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="2d0d2-1713">Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="2d0d2-1714">Ta usługa została zaprojektowana do exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="2d0d2-1715">*Byte_offset* parametr przyjmuje wartość 64-bitową, która umożliwia wywołującemu zmianę położenia wskaźnika odczytu/zapisu poza 4 GB zakresu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-1716">*Jeśli operacja wyszukiwania próbuje przejść poza końcem pliku, wskaźnik odczytu/zapisu pliku jest umieszczany na końcu pliku. Z drugiej strony, jeśli operacja wyszukiwania próbuje nawiązać miejsce poza początkiem pliku, wskaźnik odczytu/zapisu pliku jest umieszczany na początku pliku.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1717">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1717">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1718">**file_ptr**: wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="2d0d2-1719">**byte_offset**: żądane względne przesunięcie bajtów w pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="2d0d2-1720">**seek_from**: kierunek i lokalizacja, z której ma zostać wykonane wyszukiwanie względne.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="2d0d2-1721">Prawidłowe opcje wyszukiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="2d0d2-1722">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="2d0d2-1723">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="2d0d2-1724">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="2d0d2-1725">FX_SEEK_BACK (0x03) Jeśli określono FX_SEEK_BEGIN, operacja wyszukiwania jest wykonywana od początku pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="2d0d2-1726">Jeśli FX_SEEK_END jest określony, operacja wyszukiwania jest wykonywana wstecz od końca pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="2d0d2-1727">Jeśli FX_SEEK_FORWARD jest określony, operacja wyszukiwania jest wykonywana w przód od bieżącego położenia pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="2d0d2-1728">Jeśli FX_SEEK_BACK jest określony, operacja wyszukiwania jest wykonywana wstecz od bieżącego położenia pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1729">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1729">Return Values</span></span>

- <span data-ttu-id="2d0d2-1730">**FX_SUCCESS** (0X00) pomyślne wyszukiwanie względem pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="2d0d2-1731">Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="2d0d2-1732">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1733">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1734">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-1735">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1736">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-1737">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1738">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1738">Allowed From</span></span>

<span data-ttu-id="2d0d2-1739">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1740">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1741">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1741">See Also</span></span>

- <span data-ttu-id="2d0d2-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1742">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1746">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1747">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1749">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1755">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1756">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1758">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1759">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1760">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1762">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="2d0d2-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="2d0d2-1769">Położenie do przesunięcia bajtów</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1770">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1771">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1771">Description</span></span>

<span data-ttu-id="2d0d2-1772">Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego przesunięcia bajtu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="2d0d2-1773">Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="2d0d2-1774">Ta usługa została zaprojektowana do exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="2d0d2-1775">*Byte_offset* parametr przyjmuje wartość 64-bitową, która umożliwia wywołującemu zmianę położenia wskaźnika odczytu/zapisu poza 4 GB zakresu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1776">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1776">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1777">**file_ptr**: wskaźnik do bloku kontroli pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="2d0d2-1778">**byte_offset**: wymagane przesunięcie bajtów w pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="2d0d2-1779">Wartość zero spowoduje umieszczenie wskaźnika odczytu/zapisu na początku pliku, podczas gdy wartość większa od rozmiaru pliku będzie umieścić wskaźnik odczytu/zapisu na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1780">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1780">Return Values</span></span>

- <span data-ttu-id="2d0d2-1781">Zakończono wyszukiwanie pliku **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="2d0d2-1782">**FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="2d0d2-1783">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1784">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1785">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-1786">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1787">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-1788">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1789">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1789">Allowed From</span></span>

<span data-ttu-id="2d0d2-1790">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1791">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1792">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1792">See Also</span></span>

- <span data-ttu-id="2d0d2-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1793">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1797">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1798">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1800">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1806">fx_file_open — fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1808">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1809">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1810">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1812">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="2d0d2-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="2d0d2-1819">Obcina plik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1820">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1821">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1821">Description</span></span>

<span data-ttu-id="2d0d2-1822">Ta usługa obcina rozmiar pliku do określonego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="2d0d2-1823">Jeśli podany rozmiar jest większy niż rozmiar rzeczywistego pliku, ta usługa nie wykonuje żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="2d0d2-1824">Żaden z klastrów multimedialnych skojarzonych z plikiem nie zostanie opublikowany.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-1825">*Należy zachować ostrożność obcinanie plików, które mogą być również otwierane w celu odczytu. Obcinanie pliku otwartego także do odczytu może spowodować odczytanie nieprawidłowych danych.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="2d0d2-1826">Ta usługa została zaprojektowana do exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="2d0d2-1827">Parametr *size* przyjmuje 64-bitową wartość całkowitą, która umożliwia wywołującemu działanie poza 4 GB zakresu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1828">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1828">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1829">**file_ptr**: wskaźnik do bloku kontroli pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="2d0d2-1830">**rozmiar**: nowy rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1830">**size**: New file size.</span></span> <span data-ttu-id="2d0d2-1831">Bajty znajdujące się przed nowym rozmiarem pliku są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1832">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1832">Return Values</span></span>

- <span data-ttu-id="2d0d2-1833">**FX_SUCCESS** (0X00) pomyślne Obcinanie pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="2d0d2-1834">**FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="2d0d2-1835">Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="2d0d2-1836">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1837">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1838">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-1839">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-1840">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1841">Nośnik bazowy **FX_WRITE_PROTECT** (0x23) jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1842">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-1843">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1844">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1844">Allowed From</span></span>

<span data-ttu-id="2d0d2-1845">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1846">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1847">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1847">See Also</span></span>

- <span data-ttu-id="2d0d2-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1848">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1852">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1853">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1855">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1861">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1862">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1864">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1865">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1866">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1868">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="2d0d2-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="2d0d2-1875">Obcina plik i zwalnia klastry</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1876">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="2d0d2-1877">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1877">Description</span></span>

<span data-ttu-id="2d0d2-1878">Ta usługa obcina rozmiar pliku do określonego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="2d0d2-1879">Jeśli podany rozmiar jest większy niż rozmiar rzeczywistego pliku, ta usługa nie wykonuje żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="2d0d2-1880">W przeciwieństwie do usługi ***fx_file_extended_truncate*** , ta usługa zwalnia wszystkie nieużywane klastry.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-1881">*Należy zachować ostrożność obcinanie plików, które mogą być również otwierane w celu odczytu. Obcinanie pliku otwartego także do odczytu może spowodować odczytanie nieprawidłowych danych.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="2d0d2-1882">Ta usługa została zaprojektowana do exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="2d0d2-1883">Parametr *size* przyjmuje 64-bitową wartość całkowitą, która umożliwia wywołującemu działanie poza 4 GB zakresu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1884">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1884">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1885">**file_ptr**: wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="2d0d2-1886">**rozmiar**: nowy rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1886">**size**: New file size.</span></span> <span data-ttu-id="2d0d2-1887">Bajty znajdujące się przed nowym rozmiarem pliku są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1888">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1888">Return Values</span></span>

- <span data-ttu-id="2d0d2-1889">**FX_SUCCESS** (0X00) pomyślne Obcinanie pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="2d0d2-1890">Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="2d0d2-1891">Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="2d0d2-1892">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1893">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-1894">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1895">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-1896">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-1897">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1898">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1899">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-1900">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1901">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1901">Allowed From</span></span>

<span data-ttu-id="2d0d2-1902">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1903">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1904">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1904">See Also</span></span>

- <span data-ttu-id="2d0d2-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1905">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1909">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1910">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1912">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1918">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1919">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1921">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1922">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1923">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1925">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="2d0d2-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1931">fx_file_open</span></span>

<span data-ttu-id="2d0d2-1932">Otwiera plik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1933">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1934">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1934">Description</span></span>

<span data-ttu-id="2d0d2-1935">Ta usługa otwiera określony plik do odczytu lub zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="2d0d2-1936">Plik może być otwarty do odczytu wiele razy, podczas gdy plik może być otwarty tylko raz do momentu zamknięcia pliku przez moduł zapisujący.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-1937">*Należy zwrócić uwagę, jeśli plik jest jednocześnie otwarty do odczytu i zapisu. Zapis pliku wykonywany, gdy plik jest otwarty do odczytu, może nie być widoczny dla czytnika, chyba że czytnik zamknie i ponownie otworzy plik do odczytu. Podobnie podczas korzystania z usług obcinania plików należy zachować ostrożność zapisywania plików. Jeśli plik zostanie obcięty przez składnik zapisywania, czytelnicy tego samego pliku mogą zwrócić nieprawidłowe dane.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-1938">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1938">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-1939">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-1940">**file_ptr**: wskaźnik do bloku kontroli pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="2d0d2-1941">**file_name**: wskaźnik do nazwy pliku do otwarcia (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="2d0d2-1942">**open_type**: typ otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="2d0d2-1943">Prawidłowe opcje otwartego typu są następujące:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="2d0d2-1944">FX_OPEN_FOR_READ (0x00)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="2d0d2-1945">FX_OPEN_FOR_WRITE (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="2d0d2-1946">FX_OPEN_FOR_READ_FAST (0x02)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="2d0d2-1947">Otwieranie plików z FX_OPEN_FOR_READ i FX_OPEN_FOR_READ_FAST jest podobne:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="2d0d2-1948">FX_OPEN_FOR_READ obejmuje sprawdzenie, czy połączona lista klastrów składających się na plik jest nienaruszona, a FX_OPEN_FOR_READ_FAST nie przeprowadza tej weryfikacji, co przyspiesza.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-1949">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1949">Return Values</span></span>

- <span data-ttu-id="2d0d2-1950">Plik **FX_SUCCESS** (0x00) został pomyślnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="2d0d2-1951">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-1952">Nie znaleziono określonego pliku **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="2d0d2-1953">**FX_NOT_A_FILE** (0X05) określona nazwa pliku jest katalogiem lub woluminem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="2d0d2-1954">**FX_FILE_CORRUPT** (0X08) określony plik jest uszkodzony i nie można otworzyć pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="2d0d2-1955">**FX_ACCESS_ERROR** (0X06) określony plik jest już otwarty lub typ otwarcia jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="2d0d2-1956">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-1957">**FX_MEDIA_INVALID** (0X02) nieprawidłowy nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="2d0d2-1958">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-1959">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-1960">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-1961">Nośnik bazowy **FX_WRITE_PROTECT** (0x23) jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="2d0d2-1962">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="2d0d2-1963">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-1964">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1964">Allowed From</span></span>

<span data-ttu-id="2d0d2-1965">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-1966">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-1967">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1967">See Also</span></span>

- <span data-ttu-id="2d0d2-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1968">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1972">fx_file_close — fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="2d0d2-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1974">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1981">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1983">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1984">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1985">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1987">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="2d0d2-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1993">fx_file_read</span></span>

<span data-ttu-id="2d0d2-1994">Odczytuje bajty z pliku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-1995">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="2d0d2-1996">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1996">Description</span></span>

<span data-ttu-id="2d0d2-1997">Ta usługa odczytuje bajty z pliku i zapisuje je w podanym buforze.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="2d0d2-1998">Po zakończeniu odczytu wewnętrzny wskaźnik odczytu pliku jest dostosowywany do punktu w następnym bajcie pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="2d0d2-1999">Jeśli liczba pozostałych bajtów w żądaniu jest mniejsza, tylko pozostałe bajty są przechowywane w buforze.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="2d0d2-2000">W każdym przypadku całkowita liczba bajtów umieszczonych w buforze jest zwracana do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2001">*Aplikacja musi upewnić się, że podany bufor jest w stanie przechowywać określoną liczbę żądanych bajtów.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2002">*Większa wydajność jest osiągana, jeśli bufor docelowy znajduje się na granicy długiego słowa i żądany rozmiar jest równo widoczny przez sizeof (**ULONG**).*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2003">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2003">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2004">**file_ptr**: wskaźnik do bloku kontroli pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="2d0d2-2005">**buffer_ptr**: wskaźnik do buforu docelowego dla odczytu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="2d0d2-2006">**request_size**: Maksymalna liczba bajtów do odczytania.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="2d0d2-2007">**actual_size**: wskaźnik do zmiennej, aby pomieścić rzeczywistą liczbę bajtów odczytywanych do podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2008">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2008">Return Values</span></span>

- <span data-ttu-id="2d0d2-2009">Odczytano plik **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="2d0d2-2010">**FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="2d0d2-2011">**FX_FILE_CORRUPT** (0X08) określony plik jest uszkodzony, a odczyt nie powiódł się.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="2d0d2-2012">Osiągnięto koniec pliku **FX_END_OF_FILE** (0x09).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="2d0d2-2013">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-2014">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-2015">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2016">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku lub buforu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="2d0d2-2017">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2018">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2018">Allowed From</span></span>

<span data-ttu-id="2d0d2-2019">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2020">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2020">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="2d0d2-2021">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2021">See Also</span></span>

- <span data-ttu-id="2d0d2-2022">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="2d0d2-2023">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="2d0d2-2024">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="2d0d2-2025">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="2d0d2-2026">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2026">fx_file_close,</span></span>
- <span data-ttu-id="2d0d2-2027">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2027">fx_file_create,</span></span>
- <span data-ttu-id="2d0d2-2028">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="2d0d2-2029">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2029">fx_file_delete,</span></span>
- <span data-ttu-id="2d0d2-2030">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="2d0d2-2031">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="2d0d2-2032">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="2d0d2-2033">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="2d0d2-2034">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="2d0d2-2035">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="2d0d2-2036">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2036">fx_file_open,</span></span>
- <span data-ttu-id="2d0d2-2037">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="2d0d2-2038">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2038">fx_file_rename,</span></span>
- <span data-ttu-id="2d0d2-2039">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2039">fx_file_seek,</span></span>
- <span data-ttu-id="2d0d2-2040">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="2d0d2-2041">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="2d0d2-2042">fx_file_write,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2042">fx_file_write,</span></span>
- <span data-ttu-id="2d0d2-2043">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="2d0d2-2044">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="2d0d2-2045">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="2d0d2-2046">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="2d0d2-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="2d0d2-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="2d0d2-2049">Położenie do względnego przesunięcia bajtów</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2050">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2051">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2051">Description</span></span>

<span data-ttu-id="2d0d2-2052">Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego względnego przesunięcia bajtu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="2d0d2-2053">Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-2054">*Jeśli operacja wyszukiwania próbuje przejść poza końcem pliku, wskaźnik odczytu/zapisu pliku jest umieszczany na końcu pliku. Z drugiej strony, jeśli operacja wyszukiwania próbuje nawiązać miejsce poza początkiem pliku, wskaźnik odczytu/zapisu pliku jest umieszczany na początku pliku.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="2d0d2-2055">Aby wyszukać wartość przesunięcia przekraczającą 4 GB, aplikacja używa *fx_file_extended_relative_seek* usługi.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2056">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2056">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2057">**file_ptr**: wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="2d0d2-2058">**byte_offset**: żądane względne przesunięcie bajtów w pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="2d0d2-2059">**seek_from**: kierunek i lokalizacja, z której ma zostać wykonane wyszukiwanie względne.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="2d0d2-2060">Prawidłowe opcje wyszukiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="2d0d2-2061">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="2d0d2-2062">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="2d0d2-2063">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="2d0d2-2064">FX_SEEK_BACK (0x03)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="2d0d2-2065">Jeśli FX_SEEK_BEGIN jest określony, operacja wyszukiwania jest wykonywana od początku pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="2d0d2-2066">Jeśli FX_SEEK_END jest określony, operacja wyszukiwania jest wykonywana wstecz od końca pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="2d0d2-2067">Jeśli FX_SEEK_FORWARD jest określony, operacja wyszukiwania jest wykonywana w przód od bieżącego położenia pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="2d0d2-2068">Jeśli FX_SEEK_BACK jest określony, operacja wyszukiwania jest wykonywana wstecz od bieżącego położenia pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2069">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2069">Return Values</span></span>

- <span data-ttu-id="2d0d2-2070">**FX_SUCCESS** (0X00) pomyślne wyszukiwanie względem pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="2d0d2-2071">Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="2d0d2-2072">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2073">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-2074">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-2075">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-2076">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-2077">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2078">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2078">Allowed From</span></span>

<span data-ttu-id="2d0d2-2079">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2080">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2081">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2081">See Also</span></span>

- <span data-ttu-id="2d0d2-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2082">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2086">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2087">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2089">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2096">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2097">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2098">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2099">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2100">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2102">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="2d0d2-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2108">fx_file_rename</span></span>

<span data-ttu-id="2d0d2-2109">Zmienia nazwę pliku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2110">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2111">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2111">Description</span></span>

<span data-ttu-id="2d0d2-2112">Ta usługa zmienia nazwę pliku określonego przez *old_file_name*.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="2d0d2-2113">Zmiana nazwy jest również wykonywana względem określonej ścieżki lub ścieżki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="2d0d2-2114">Jeśli ścieżka zostanie określona w nowej nazwie pliku, plik o zmienionej nazwie jest skutecznie przenoszony do określonej ścieżki.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="2d0d2-2115">Jeśli ścieżka nie zostanie określona, plik o zmienionej nazwie zostanie umieszczony w bieżącej ścieżce domyślnej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2116">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2116">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2117">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="2d0d2-2118">**old_file_name**: wskaźnik do nazwy pliku do zmiany nazwy (ścieżka katalogu jest opcjonalna).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="2d0d2-2119">**new_file_name**: wskaźnik na nową nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="2d0d2-2120">Ścieżka katalogu jest niedozwolona.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2121">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2121">Return Values</span></span>

- <span data-ttu-id="2d0d2-2122">**FX_SUCCESS** (0X00) pomyślnie zmieniono nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="2d0d2-2123">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-2124">Nie znaleziono określonego pliku **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="2d0d2-2125">**FX_NOT_A_FILE** (0X05) określony plik jest katalogiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="2d0d2-2126">**FX_ACCESS_ERROR** (0X06) określony plik jest już otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="2d0d2-2127">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2128">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-2129">**FX_INVALID_NAME** (0X0C) określona nazwa nowego pliku nie jest prawidłową nazwą pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="2d0d2-2130">Ścieżka do **FX_INVALID_PATH** (0x0D) jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="2d0d2-2131">**FX_ALREADY_CREATED** (0x0B) zostanie użyta Nowa nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="2d0d2-2132">Nośnik **FX_MEDIA_INVALID** (0x02) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="2d0d2-2133">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-2134">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-2135">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-2136">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-2137">**FX_FAT_READ_ERROR** (0X03) nie może odczytać tabeli FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="2d0d2-2138">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-2139">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2140">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2140">Allowed From</span></span>

<span data-ttu-id="2d0d2-2141">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2142">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2143">See Also</span></span>

- <span data-ttu-id="2d0d2-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2144">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2148">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2149">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2151">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2158">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2159">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2161">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2162">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2164">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="2d0d2-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2170">fx_file_seek</span></span>

<span data-ttu-id="2d0d2-2171">Położenie do przesunięcia bajtów</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2172">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2173">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2173">Description</span></span>

<span data-ttu-id="2d0d2-2174">Ta usługa umieszcza wewnętrzny wskaźnik odczytu/zapisu pliku do określonego przesunięcia bajtu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="2d0d2-2175">Każde kolejne żądanie odczytu lub zapisu pliku rozpocznie się w tej lokalizacji w pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="2d0d2-2176">Aby wyszukać wartość przesunięcia przekraczającą 4 GB, aplikacja używa *fx_file_extended_seek* usługi.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2177">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2177">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2178">**file_ptr**: wskaźnik do bloku kontroli pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="2d0d2-2179">**byte_offset**: wymagane przesunięcie bajtów w pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="2d0d2-2180">Wartość zero spowoduje umieszczenie wskaźnika odczytu/zapisu na początku pliku, podczas gdy wartość większa od rozmiaru pliku będzie umieścić wskaźnik odczytu/zapisu na końcu pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2181">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2181">Return Values</span></span>

- <span data-ttu-id="2d0d2-2182">Zakończono wyszukiwanie pliku **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="2d0d2-2183">**FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="2d0d2-2184">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2185">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-2186">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-2187">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-2188">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-2189">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2190">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2190">Allowed From</span></span>

<span data-ttu-id="2d0d2-2191">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2192">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2193">See Also</span></span>

- <span data-ttu-id="2d0d2-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2194">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2198">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2199">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2201">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2208">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2209">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2210">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2211">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2212">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2214">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="2d0d2-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2220">fx_file_truncate</span></span>

<span data-ttu-id="2d0d2-2221">Obcina plik</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2222">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="2d0d2-2223">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2223">Description</span></span>

<span data-ttu-id="2d0d2-2224">Ta usługa obcina rozmiar pliku do określonego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="2d0d2-2225">Jeśli podany rozmiar jest większy niż rozmiar rzeczywistego pliku, ta usługa nie wykonuje żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="2d0d2-2226">Żaden z klastrów multimedialnych skojarzonych z plikiem nie zostanie opublikowany.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2227">*Należy zachować ostrożność obcinanie plików, które mogą być również otwierane w celu odczytu. Obcinanie pliku otwartego także do odczytu może spowodować odczytanie nieprawidłowych danych.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="2d0d2-2228">Aby działać poza 4 GB, aplikacja używa *fx_file_extended_truncate* usługi.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2229">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2229">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2230">**file_ptr**: wskaźnik do bloku kontroli pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="2d0d2-2231">**rozmiar**: nowy rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2231">**size**: New file size.</span></span> <span data-ttu-id="2d0d2-2232">Bajty znajdujące się przed nowym rozmiarem pliku są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2233">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2233">Return Values</span></span>

- <span data-ttu-id="2d0d2-2234">**FX_SUCCESS** (0X00) pomyślne Obcinanie pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="2d0d2-2235">**FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="2d0d2-2236">Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="2d0d2-2237">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2238">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-2239">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-2240">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-2241">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-2242">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="2d0d2-2243">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-2244">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2245">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2245">Allowed From</span></span>

<span data-ttu-id="2d0d2-2246">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2247">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2248">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2248">See Also</span></span>

- <span data-ttu-id="2d0d2-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2249">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2253">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2254">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2256">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2263">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2264">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2266">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2267">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2269">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="2d0d2-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="2d0d2-2276">Obcina plik i zwalnia klastry</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2277">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2278">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2278">Description</span></span>

<span data-ttu-id="2d0d2-2279">Ta usługa obcina rozmiar pliku do określonego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="2d0d2-2280">Jeśli podany rozmiar jest większy niż rozmiar rzeczywistego pliku, ta usługa nie wykonuje żadnych działań.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="2d0d2-2281">W przeciwieństwie do usługi ***fx_file_truncate*** , ta usługa zwalnia wszystkie nieużywane klastry.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2282">*Należy zachować ostrożność obcinanie plików, które mogą być również otwierane w celu odczytu. Obcinanie pliku otwartego także do odczytu może spowodować odczytanie nieprawidłowych danych.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="2d0d2-2283">Aby działać poza 4 GB, aplikacja używa *fx_file_extended_truncate_release* usługi.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2284">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2284">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2285">**file_ptr**: wskaźnik do wcześniej otwartego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="2d0d2-2286">**rozmiar**: nowy rozmiar pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2286">**size**: New file size.</span></span> <span data-ttu-id="2d0d2-2287">Bajty znajdujące się przed nowym rozmiarem pliku są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2288">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2288">Return Values</span></span>

- <span data-ttu-id="2d0d2-2289">**FX_SUCCESS** (0X00) pomyślne Obcinanie pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="2d0d2-2290">Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="2d0d2-2291">Plik **FX_NOT_OPEN** (0x07) nie jest obecnie otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="2d0d2-2292">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2293">Nośnik bazowy **FX_WRITE_PROTECT** (0x23) jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="2d0d2-2294">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-2295">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-2296">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-2297">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-2298">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca do ukończenia operacji.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="2d0d2-2299">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="2d0d2-2300">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2301">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2301">Allowed From</span></span>

<span data-ttu-id="2d0d2-2302">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2303">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="2d0d2-2304">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2304">See Also</span></span>

- <span data-ttu-id="2d0d2-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2305">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2309">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2310">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2312">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2319">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2320">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2322">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2323">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2324">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2325">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="2d0d2-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2331">fx_file_write</span></span>

<span data-ttu-id="2d0d2-2332">Zapisuje bajty do pliku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2333">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2334">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2334">Description</span></span>

<span data-ttu-id="2d0d2-2335">Ta usługa zapisuje bajty z określonego buforu, rozpoczynając od bieżącego położenia pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="2d0d2-2336">Po zakończeniu zapisu wewnętrzny wskaźnik odczytu pliku jest dostosowywany do punktu w następnym bajcie pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2337">*Większa wydajność jest osiągana, jeśli bufor źródłowy znajduje się na granicy długiego słowa, a żądany rozmiar jest równo widoczny przez sizeof (**ULONG**).*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2338">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2338">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2339">**file_ptr**: wskaźnik do bloku kontroli pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="2d0d2-2340">**buffer_ptr**: wskaźnik do bufora źródłowego zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="2d0d2-2341">**rozmiar**: liczba bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2342">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2342">Return Values</span></span>

- <span data-ttu-id="2d0d2-2343">Zakończono zapis pliku **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="2d0d2-2344">**FX_NOT_OPEN** (0X07) określony plik nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="2d0d2-2345">Plik **FX_ACCESS_ERROR** (0x06) nie jest otwarty do zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="2d0d2-2346">**FX_NO_MORE_SPACE** (0x0A) nie ma więcej wolnego miejsca na nośniku, aby wykonać ten zapis.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="2d0d2-2347">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2348">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-2349">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-2350">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-2351">**FX_FAT_READ_ERROR** (0X03) nie może odczytać wpisu systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="2d0d2-2352">**FX_NO_MORE_ENTRIES** (0X0F) nie ma więcej wpisów w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="2d0d2-2353">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik pliku lub buforu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="2d0d2-2354">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2355">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2355">Allowed From</span></span>

<span data-ttu-id="2d0d2-2356">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2357">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2358">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2358">See Also</span></span>

- <span data-ttu-id="2d0d2-2359">fx_file_allocate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="2d0d2-2360">fx_file_attributes_read,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="2d0d2-2361">fx_file_attributes_set,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="2d0d2-2362">fx_file_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="2d0d2-2363">fx_file_close,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2363">fx_file_close,</span></span>
- <span data-ttu-id="2d0d2-2364">fx_file_create,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2364">fx_file_create,</span></span>
- <span data-ttu-id="2d0d2-2365">fx_file_date_time_set,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="2d0d2-2366">fx_file_delete,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2366">fx_file_delete,</span></span>
- <span data-ttu-id="2d0d2-2367">fx_file_extended_allocate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="2d0d2-2368">fx_file_extended_best_effort_allocate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="2d0d2-2369">fx_file_extended_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="2d0d2-2370">fx_file_extended_seek,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="2d0d2-2371">fx_file_extended_truncate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="2d0d2-2372">fx_file_extended_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="2d0d2-2373">fx_file_open,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2373">fx_file_open,</span></span>
- <span data-ttu-id="2d0d2-2374">fx_file_read,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2374">fx_file_read,</span></span>
- <span data-ttu-id="2d0d2-2375">fx_file_relative_seek,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="2d0d2-2376">fx_file_rename,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2376">fx_file_rename,</span></span>
- <span data-ttu-id="2d0d2-2377">fx_file_seek,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2377">fx_file_seek,</span></span>
- <span data-ttu-id="2d0d2-2378">fx_file_truncate,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="2d0d2-2379">fx_file_truncate_release,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="2d0d2-2380">fx_file_write_notify_set,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="2d0d2-2381">fx_unicode_file_create,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="2d0d2-2382">fx_unicode_file_rename,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="2d0d2-2383">fx_unicode_name_get,</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="2d0d2-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="2d0d2-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="2d0d2-2386">Ustawia funkcję powiadamiania o zapisie pliku</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2387">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="2d0d2-2388">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2388">Description</span></span>

<span data-ttu-id="2d0d2-2389">Ta usługa instaluje funkcję wywołania zwrotnego, która jest wywoływana po pomyślnym wykonaniu operacji zapisu w pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2390">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2390">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2391">**file_ptr**: wskaźnik do bloku kontroli pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="2d0d2-2392">**file_write_notify**: funkcja wywołania zwrotnego zapisu pliku do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="2d0d2-2393">Ustawienie funkcji wywołania zwrotnego na wartość NULL powoduje wyłączenie funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2394">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2394">Return Values</span></span>

- <span data-ttu-id="2d0d2-2395">**FX_SUCCESS** (0X00) pomyślnie zainstalował funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="2d0d2-2396">**FX_PTR_ERROR** (0x18) file_ptr ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="2d0d2-2397">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2398">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2398">Allowed From</span></span>

<span data-ttu-id="2d0d2-2399">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2400">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2401">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2401">See Also</span></span>

- <span data-ttu-id="2d0d2-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2402">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2406">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2407">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2409">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2416">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2417">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2419">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2420">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2421">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2423">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="2d0d2-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2428">fx_media_abort</span></span>

<span data-ttu-id="2d0d2-2429">Przerywa działania multimedialne</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2430">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2431">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2431">Description</span></span>

<span data-ttu-id="2d0d2-2432">Ta usługa przerywa wszystkie bieżące działania związane z nośnikiem, w tym zamknięcie wszystkich otwartych plików, wysłanie żądania przerwania do skojarzonego sterownika i umieszczenie nośnika w stanie przerwania.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="2d0d2-2433">Ta usługa jest zazwyczaj wywoływana w przypadku wykrycia błędów we/wy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2434">*Przed wykonaniem operacji przerwania należy ponownie otworzyć nośnik.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2435">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2435">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2436">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2437">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2437">Return Values</span></span>

- <span data-ttu-id="2d0d2-2438">Pomyślne przerwanie nośnika **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="2d0d2-2439">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-2440">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-2441">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2442">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2442">Allowed From</span></span>

<span data-ttu-id="2d0d2-2443">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2444">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2445">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2445">See Also</span></span>

- <span data-ttu-id="2d0d2-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2448">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2449">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2453">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2454">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2455">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2457">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2458">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2461">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="2d0d2-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="2d0d2-2464">Unieważnia pamięć podręczną sektora logicznego</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2465">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="2d0d2-2466">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2466">Description</span></span>

<span data-ttu-id="2d0d2-2467">Ta usługa opróżnia wszystkie sektory zanieczyszczone w pamięci podręcznej, a następnie unieważnia całą pamięć podręczną sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2468">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2468">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2469">**media_ptr**: wskaźnik do bloku sterowania nośnikami</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2470">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2470">Return Values</span></span>

- <span data-ttu-id="2d0d2-2471">**FX_SUCCESS** (0X00) pomyślne unieważnienie pamięci podręcznej nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="2d0d2-2472">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-2473">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2474">**FX_PTR_ERROR** (0X18) nieprawidłowy nośnik lub wskaźnik magazynujący.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="2d0d2-2475">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2476">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2476">Allowed From</span></span>

<span data-ttu-id="2d0d2-2477">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2478">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2479">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2479">See Also</span></span>

- <span data-ttu-id="2d0d2-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2481">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2482">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2483">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2487">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2488">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2489">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2491">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2492">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2495">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="2d0d2-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2497">fx_media_check</span></span>

<span data-ttu-id="2d0d2-2498">Sprawdza nośniki pod kątem błędów</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2499">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2500">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2500">Description</span></span>

<span data-ttu-id="2d0d2-2501">Ta usługa sprawdza określony nośnik dla podstawowych błędów strukturalnych, w tym między innymi łączenie plików/katalogów, nieprawidłowe łańcuchy FAT i utracone klastry.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="2d0d2-2502">Ta usługa zapewnia również możliwość poprawiania wykrytych błędów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="2d0d2-2503">Usługa fx_media_check wymaga pamięci podręcznej na potrzeby pierwszej analizy katalogów i plików na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="2d0d2-2504">W przypadku pamięci poddanej do usługi sprawdzania nośników musi być wystarczająco duży, aby można było przechowywać kilka wpisów w katalogu, ze strukturą danych "Stack" w bieżącym położeniu katalogu przed wprowadzeniem do podkatalogów i na końcu mapy logicznej FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="2d0d2-2505">Pamięć zapasowa powinna wynosić co najmniej 512-1024 bajtów i pamięć dla mapy bitowej FAT, która wymaga tylu bitów, ile jest klastrów na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="2d0d2-2506">Na przykład urządzenie z 8000 klastrów będzie wymagało, aby reprezentować 1000 bajtów i w ten sposób wymagać całkowitej ilości miejsca w kolejności od 2048 bajtów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2507">*Ta usługa powinna być wywoływana tylko natychmiast po fx_media_open i bez żadnych innych działań systemu plików.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2508">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2508">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2509">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-2510">**scratch_memory_ptr**: wskaźnik do początku pamięci początkowej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="2d0d2-2511">**scratch_memory_size**: rozmiar pamięci zapasowej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="2d0d2-2512">**error_correction_option**: opcja korekcji błędów BITS, gdy bit jest ustawiony, Korekcja błędów jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="2d0d2-2513">Opcja korekcji błędów jest definiowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="2d0d2-2514">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="2d0d2-2515">FX_DIRECTORY_ERROR (0x02)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="2d0d2-2516">FX_LOST_CLUSTER_ERROR (0x04) po prostu lub łącznie z wymaganymi opcjami korekcji błędów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="2d0d2-2517">Jeśli nie jest wymagana Korekcja błędów, należy podać wartość 0.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="2d0d2-2518">**errors_detected_ptr**: miejsce docelowe dla bitów wykrywania błędów, zgodnie z definicją poniżej:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="2d0d2-2519">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="2d0d2-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="2d0d2-2521">FX_FILE_SIZE_ERROR (0x08)</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2522">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2522">Return Values</span></span>

- <span data-ttu-id="2d0d2-2523">Zakończono sprawdzanie nośnika **FX_SUCCESS** (0x00), aby uzyskać szczegółowe informacje, zobacz temat błędy wykryte w miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="2d0d2-2524">**FX_ACCESS_ERROR** (0X06) nie może wykonać kontroli otwartych plików.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="2d0d2-2525">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-2526">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-2527">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej miejsca na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="2d0d2-2528">Ilość pamięci poddanej **FX_NOT_ENOUGH_MEMORY** (0x91) nie jest wystarczająco duża.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="2d0d2-2529">**FX_ERROR_NOT_FIXED** (0X93) uszkodzenie katalogu głównego FAT32, którego nie można naprawić.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="2d0d2-2530">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2531">Sektor **FX_SECTOR_INVALID** (0x89) jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="2d0d2-2532">**FX_PTR_ERROR** (0X18) nieprawidłowy nośnik lub wskaźnik magazynujący.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="2d0d2-2533">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2534">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2534">Allowed From</span></span>

<span data-ttu-id="2d0d2-2535">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2536">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2536">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-2537">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2537">See Also</span></span>

- <span data-ttu-id="2d0d2-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2539">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2541">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2545">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2546">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2547">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2549">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2550">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2553">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="2d0d2-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2555">fx_media_close</span></span>

<span data-ttu-id="2d0d2-2556">Zamyka nośniki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2557">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2558">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2558">Description</span></span>

<span data-ttu-id="2d0d2-2559">Ta usługa zamyka określony nośnik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2559">This service closes the specified media.</span></span> <span data-ttu-id="2d0d2-2560">W procesie zamykania nośnika wszystkie otwarte pliki są zamknięte, a wszystkie pozostałe bufory są opróżniane na nośnik fizyczny.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2561">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2561">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2562">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2563">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2563">Return Values</span></span>

- <span data-ttu-id="2d0d2-2564">Pomyślnie zamknięto nośnik **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="2d0d2-2565">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-2566">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2567">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-2568">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2569">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2569">Allowed From</span></span>

<span data-ttu-id="2d0d2-2570">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2571">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2572">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2572">See Also</span></span>

- <span data-ttu-id="2d0d2-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2574">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2576">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2580">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2581">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2582">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2584">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2585">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2588">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="2d0d2-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="2d0d2-2591">Ustawia funkcję powiadamiania o zamknięciu nośnika</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2592">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="2d0d2-2593">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2593">Description</span></span>

<span data-ttu-id="2d0d2-2594">Ta usługa ustawia funkcję wywołania zwrotnego powiadomienia, która zostanie wywołana po pomyślnym zamknięciu nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2595">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2595">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2596">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-2597">**media_close_notify**: funkcja wywołania zwrotnego z powiadomieniem o zamknięciu nośnika zostanie zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="2d0d2-2598">Przekazywanie wartości NULL jako funkcji wywołania zwrotnego powoduje wyłączenie wywołania zwrotnego zamknięcia nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2599">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2599">Return Values</span></span>

- <span data-ttu-id="2d0d2-2600">**FX_SUCCESS** (0X00) pomyślnie zainstalował funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="2d0d2-2601">**FX_PTR_ERROR** (0x18) media_ptr ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="2d0d2-2602">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2603">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2603">Allowed From</span></span>

<span data-ttu-id="2d0d2-2604">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2605">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="2d0d2-2606">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2606">See Also</span></span>

- <span data-ttu-id="2d0d2-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2608">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2610">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2611">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2614">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2615">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2616">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2618">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2619">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2622">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="2d0d2-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="2d0d2-2625">Formatuje multimedia</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2626">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2626">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="2d0d2-2627">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2627">Description</span></span>

<span data-ttu-id="2d0d2-2628">Ta usługa formatuje dostarczone multimedia w zgodnym exFAT sposób na podstawie podanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="2d0d2-2629">Ta usługa musi zostać wywołana przed otwarciem nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2630">*Formatowanie już sformatowanego nośnika skutecznie kasuje wszystkie pliki i katalogi na nośniku.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2631">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2631">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2632">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2632">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="2d0d2-2633">Jest on używany tylko w celu zapewnienia pewnych podstawowych informacji niezbędnych do działania sterownika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2633">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="2d0d2-2634">**Driver**: wskaźnik do sterownika we/wy dla tego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2634">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="2d0d2-2635">Zwykle jest to ten sam sterownik dostarczony do kolejnego wywołania fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2635">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="2d0d2-2636">**driver_info_ptr**: wskaźnik do opcjonalnych informacji, które mogą być używane przez sterownik we/wy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2636">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="2d0d2-2637">**memory_ptr**: wskaźnik do pamięci roboczej dla nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2637">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="2d0d2-2638">memory_size określa rozmiar działającej pamięci multimedialnej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2638">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="2d0d2-2639">Rozmiar musi być co najmniej tak duży, jak rozmiar sektora nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2639">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="2d0d2-2640">**volume_name**: wskaźnik do ciągu nazwy woluminu, który ma maksymalnie 11 znaków.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2640">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="2d0d2-2641">**number_of_fats**: liczba tłuszczów na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2641">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="2d0d2-2642">Bieżąca implementacja obsługuje jeden FAT na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2642">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="2d0d2-2643">**hidden_sectors**: liczba sektorów ukryta przed sektorem rozruchowym tego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2643">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="2d0d2-2644">Jest to typowe w przypadku obecności wielu partycji.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2644">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="2d0d2-2645">**total_sectors**: Łączna liczba sektorów na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2645">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="2d0d2-2646">**bytes_per_sector**: liczba bajtów na sektor, co jest zwykle 512.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2646">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="2d0d2-2647">FileX wymaga, aby była to wielokrotność 32.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2647">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="2d0d2-2648">**sectors_per_cluster**: liczba sektorów w każdym klastrze.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2648">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="2d0d2-2649">Klaster jest minimalną jednostką alokacji w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2649">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="2d0d2-2650">**volumne_serial_number**: numer seryjny, który ma być używany dla tego woluminu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2650">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="2d0d2-2651">**boundary_unit**: rozmiar fizycznego wyrównania obszaru danych, w liczbie sektorów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2651">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2652">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2652">Return Values</span></span>

- <span data-ttu-id="2d0d2-2653">Format nośnika **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2653">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="2d0d2-2654">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2654">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2655">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika, sterownika lub pamięci.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2655">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="2d0d2-2656">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2656">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2657">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2657">Allowed From</span></span>

<span data-ttu-id="2d0d2-2658">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2658">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2659">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2659">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-2660">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2660">See Also</span></span>

- <span data-ttu-id="2d0d2-2661">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2661">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2662">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2662">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2663">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2663">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2664">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2664">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2665">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2665">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2666">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2666">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2667">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2667">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2668">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2668">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2669">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2669">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2670">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2670">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2671">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2671">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2672">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2672">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2673">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2673">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2674">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2674">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2675">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2675">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2676">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2676">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2677">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2677">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="2d0d2-2678">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2678">fx_media_extended_space_available</span></span>

<span data-ttu-id="2d0d2-2679">Zwraca dostępne miejsce na multimediach</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2679">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2680">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2680">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2681">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2681">Description</span></span>

<span data-ttu-id="2d0d2-2682">Ta usługa zwraca liczbę bajtów dostępnych na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2682">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="2d0d2-2683">Ta usługa została zaprojektowana do exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2683">This service is designed for exFAT.</span></span> <span data-ttu-id="2d0d2-2684">Wskaźnik do *available_bytes* parametr przyjmuje wartość 64-bitową liczbę całkowitą, która umożliwia wywołującemu współpracuję z nośnikami poza 4 GB zakresu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2684">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2685">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2685">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2686">**media_ptr**: wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2686">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="2d0d2-2687">**available_bytes_ptr**: Pozostałe bajty pozostawione na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2687">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2688">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2688">Return Values</span></span>

- <span data-ttu-id="2d0d2-2689">**FX_SUCCESS** (0X00) pomyślnie pobrała ilość miejsca dostępnego na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2689">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="2d0d2-2690">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2690">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-2691">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub wskaźnik dostępnych bajtów ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2691">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="2d0d2-2692">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2692">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2693">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2693">Allowed From</span></span>

<span data-ttu-id="2d0d2-2694">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2694">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2695">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2695">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2696">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2696">See Also</span></span>

- <span data-ttu-id="2d0d2-2697">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2697">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2698">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2698">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2699">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2699">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2700">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2700">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2701">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2701">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2702">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2702">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2703">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2703">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2704">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2704">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2705">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2705">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2706">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2706">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2707">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2707">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2708">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2708">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2709">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2709">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2710">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2710">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2711">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2711">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2712">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2712">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2713">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2713">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="2d0d2-2714">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2714">fx_media_flush</span></span>

<span data-ttu-id="2d0d2-2715">Opróżnianie danych na nośnik fizyczny</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2715">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2716">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2716">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2717">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2717">Description</span></span>

<span data-ttu-id="2d0d2-2718">Ta usługa opróżnia wszystkie pliki w pamięci podręcznej i wpisy katalogu wszystkich zmodyfikowanych plików na nośniku fizycznym.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2718">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2719">*Ta procedura może być okresowo wywoływana przez aplikację w celu zmniejszenia ryzyka uszkodzenia i/lub utraty danych w przypadku nagłej utraty mocy na miejscu docelowym.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2719">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2720">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2720">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2721">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2721">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2722">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2722">Return Values</span></span>

- <span data-ttu-id="2d0d2-2723">Zakończono pomyślne opróżnianie nośnika **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2723">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="2d0d2-2724">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2724">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-2725">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2725">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="2d0d2-2726">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2726">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-2727">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2727">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2728">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2728">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-2729">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2729">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-2730">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2730">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2731">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2731">Allowed From</span></span>

<span data-ttu-id="2d0d2-2732">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2733">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2733">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2734">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2734">See Also</span></span>

- <span data-ttu-id="2d0d2-2735">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2735">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2736">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2736">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2737">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2737">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2738">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2738">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2739">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2739">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2740">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2740">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2741">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2741">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2742">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2742">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2743">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2743">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2744">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2744">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2745">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2745">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2746">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2746">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2747">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2747">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2748">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2748">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2749">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2749">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2750">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2750">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2751">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2751">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="2d0d2-2752">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2752">fx_media_format</span></span>

<span data-ttu-id="2d0d2-2753">Formatuje multimedia</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2753">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2754">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2754">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="2d0d2-2755">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2755">Description</span></span>

<span data-ttu-id="2d0d2-2756">Ta usługa formatuje dostarczone multimedia w zgodnym z systemem plików FAT 12/16/32 na podstawie podanych parametrów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2756">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="2d0d2-2757">Ta usługa musi zostać wywołana przed otwarciem nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2757">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2758">*Formatowanie już sformatowanego nośnika skutecznie kasuje wszystkie pliki i katalogi na nośniku.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2758">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2759">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2759">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2760">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2760">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="2d0d2-2761">Jest on używany tylko w celu zapewnienia pewnych podstawowych informacji niezbędnych do działania sterownika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2761">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="2d0d2-2762">**Driver**: wskaźnik do sterownika we/wy dla tego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2762">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="2d0d2-2763">Zwykle jest to ten sam sterownik dostarczony do kolejnego wywołania fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2763">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="2d0d2-2764">**driver_info_ptr**: wskaźnik do opcjonalnych informacji, które mogą być używane przez sterownik we/wy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2764">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="2d0d2-2765">**memory_ptr**: wskaźnik do pamięci roboczej dla nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2765">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="2d0d2-2766">**memory_size**: Określa rozmiar działającej pamięci multimedialnej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2766">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="2d0d2-2767">Rozmiar musi być co najmniej tak duży, jak rozmiar sektora nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2767">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="2d0d2-2768">**volume_name**: wskaźnik do ciągu nazwy woluminu, który ma maksymalnie 11 znaków.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2768">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="2d0d2-2769">**number_of_fats**: liczba tłuszczów w nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2769">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="2d0d2-2770">Minimalna wartość to 1 dla podstawowego systemu FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2770">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="2d0d2-2771">Wartości większe niż 1 powodują, że dodatkowe kopie FAT są utrzymywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2771">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="2d0d2-2772">**directory_entries**: liczba wpisów w katalogu głównym.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2772">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="2d0d2-2773">**hidden_sectors**: liczba sektorów ukryta przed sektorem rozruchowym tego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2773">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="2d0d2-2774">Jest to typowe w przypadku obecności wielu partycji.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2774">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="2d0d2-2775">**total_sectors**: Łączna liczba sektorów na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2775">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="2d0d2-2776">**bytes_per_sector**: liczba bajtów na sektor, co jest zwykle 512.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2776">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="2d0d2-2777">FileX wymaga, aby była to wielokrotność 32.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2777">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="2d0d2-2778">**sectors_per_cluster**: liczba sektorów w każdym klastrze.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2778">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="2d0d2-2779">Klaster jest minimalną jednostką alokacji w systemie plików FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2779">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="2d0d2-2780">**Headers**: liczba główek fizycznych.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2780">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="2d0d2-2781">**sectors_per_track**: liczba sektorów na ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2781">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2782">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2782">Return Values</span></span>

- <span data-ttu-id="2d0d2-2783">Format nośnika **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2783">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="2d0d2-2784">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2784">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2785">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika, sterownika lub pamięci.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2785">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="2d0d2-2786">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2786">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2787">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2787">Allowed From</span></span>

<span data-ttu-id="2d0d2-2788">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2789">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2789">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-2790">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2790">See Also</span></span>

- <span data-ttu-id="2d0d2-2791">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2791">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2792">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2792">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2793">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2793">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2794">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2794">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2795">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2795">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2796">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2796">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2797">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2797">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2798">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2798">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2799">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2799">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2800">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2800">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2801">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2801">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2802">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2802">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2803">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2803">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2804">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2804">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2805">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2805">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2806">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2806">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2807">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2807">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="2d0d2-2808">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2808">fx_media_open</span></span>

<span data-ttu-id="2d0d2-2809">Otwiera nośnik na potrzeby dostępu do plików</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2809">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2810">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2810">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2811">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2811">Description</span></span>

<span data-ttu-id="2d0d2-2812">Ta usługa otwiera nośnik na potrzeby dostępu do plików przy użyciu dostarczonego sterownika we/wy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2812">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-2813">*Pamięć dostarczona do tej usługi jest używana do implementowania wewnętrznej pamięci podręcznej sektora logicznego, w związku z czym większa ilość pamięci jest mniejsza. FileX wymaga pamięci podręcznej co najmniej jednego sektora logicznego (bajtów na sektor nośnika).*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2813">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2814">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2814">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2815">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2815">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-2816">**media_name**: wskaźnik do nazwy nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2816">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="2d0d2-2817">**media_driver**: wskaźnik do sterownika we/wy dla tego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2817">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="2d0d2-2818">Sterownik we/wy musi być zgodny z wymaganiami dotyczącymi sterownika FileX zdefiniowanymi w rozdziale 5.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2818">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="2d0d2-2819">**driver_info_ptr**: wskaźnik do opcjonalnych informacji, które mogą być używane przez dostarczony sterownik we/wy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2819">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="2d0d2-2820">**memory_ptr**: wskaźnik do pamięci roboczej dla nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2820">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="2d0d2-2821">**memory_size**: Określa rozmiar działającej pamięci multimedialnej.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2821">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="2d0d2-2822">Rozmiar musi być tak duży, jak rozmiar sektora nośnika (zwykle 512 bajtów).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2822">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2823">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2823">Return Values</span></span>

- <span data-ttu-id="2d0d2-2824">Pomyślny otwarty nośnik **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2824">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="2d0d2-2825">**FX_BOOT_ERROR** (0X01) błąd podczas odczytywania sektora rozruchowego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2825">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="2d0d2-2826">**FX_MEDIA_INVALID** (0x02) sektor rozruchowy określonego nośnika jest uszkodzony lub nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2826">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="2d0d2-2827">Dodatkowo ten kod powrotny jest używany do wskazania, że rozmiar pamięci podręcznej sektora logicznego lub rozmiar wpisu FAT nie jest potęgą liczby 2.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2827">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="2d0d2-2828">**FX_FAT_READ_ERROR** (0X03) Błąd odczytywania zawartości multimedialnej FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2828">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="2d0d2-2829">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2829">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2830">**FX_PTR_ERROR** (0X18) co najmniej jeden wskaźnik ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2830">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="2d0d2-2831">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2831">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2832">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2832">Allowed From</span></span>

<span data-ttu-id="2d0d2-2833">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2833">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2834">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2834">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2835">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2835">See Also</span></span>

- <span data-ttu-id="2d0d2-2836">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2836">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2837">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2837">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2838">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2838">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2839">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2839">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2840">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2840">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2841">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2841">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2842">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2842">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2843">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2843">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2844">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2844">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2845">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2845">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2846">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2846">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2847">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2847">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2848">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2848">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2849">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2849">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2850">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2850">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2851">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2851">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2852">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2852">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="2d0d2-2853">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2853">fx_media_open_notify_set</span></span>

<span data-ttu-id="2d0d2-2854">Ustawia funkcję powiadamiania Open nośnika</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2854">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2855">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2855">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="2d0d2-2856">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2856">Description</span></span>

<span data-ttu-id="2d0d2-2857">Ta usługa ustawia funkcję wywołania zwrotnego powiadomienia, która zostanie wywołana po pomyślnym otwarciu nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2857">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2858">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2858">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2859">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2859">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-2860">**media_open_notify**: zostanie zainstalowana funkcja wywołania zwrotnego powiadomienia o otwarciu nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2860">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="2d0d2-2861">Przekazywanie wartości NULL jako funkcji wywołania zwrotnego powoduje wyłączenie wywołania zwrotnego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2861">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2862">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2862">Return Values</span></span>


- <span data-ttu-id="2d0d2-2863">**FX_SUCCESS** (0X00) pomyślnie zainstalował funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2863">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="2d0d2-2864">**FX_PTR_ERROR** (0x18) media_ptr ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2864">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="2d0d2-2865">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2865">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2866">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2866">Allowed From</span></span>

<span data-ttu-id="2d0d2-2867">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2868">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2868">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2869">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2869">See Also</span></span>

- <span data-ttu-id="2d0d2-2870">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2870">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2871">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2871">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2872">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2872">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2873">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2873">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2874">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2874">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2875">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2875">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2876">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2876">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2877">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2877">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2878">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2878">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2879">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2879">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2880">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2880">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2881">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2881">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2882">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2882">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2883">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2883">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2884">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2884">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2885">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2885">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2886">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2886">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="2d0d2-2887">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2887">fx_media_read</span></span>

<span data-ttu-id="2d0d2-2888">Odczytuje sektor logiczny z nośnika</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2888">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2889">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2889">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2890">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2890">Description</span></span>

<span data-ttu-id="2d0d2-2891">Ta usługa odczytuje sektor logiczny z nośnika i umieszcza go w dostarczonym buforze.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2891">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2892">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2892">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2893">**media_ptr**: wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2893">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="2d0d2-2894">**logical_sector**: sektor logiczny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2894">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="2d0d2-2895">**buffer_ptr**: wskaźnik do lokalizacji docelowej dla sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2895">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2896">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2896">Return Values</span></span>

- <span data-ttu-id="2d0d2-2897">Odczytany nośnik **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2897">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="2d0d2-2898">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2898">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-2899">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2899">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2900">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2900">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-2901">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub buforu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2901">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="2d0d2-2902">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2902">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2903">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2903">Allowed From</span></span>

<span data-ttu-id="2d0d2-2904">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2904">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2905">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2905">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2906">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2906">See Also</span></span>

- <span data-ttu-id="2d0d2-2907">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2907">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2908">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2908">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2909">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2909">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2910">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2910">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2911">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2911">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2912">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2912">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2913">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2913">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2914">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2914">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2915">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2915">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2916">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2916">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2917">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2917">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2918">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2918">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2919">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2919">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2920">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2920">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2921">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2921">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2922">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2922">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2923">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2923">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="2d0d2-2924">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2924">fx_media_space_available</span></span>

<span data-ttu-id="2d0d2-2925">Zwraca dostępne miejsce na multimediach</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2925">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2926">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2926">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="2d0d2-2927">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2927">Description</span></span>

<span data-ttu-id="2d0d2-2928">Ta usługa zwraca liczbę bajtów dostępnych na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2928">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="2d0d2-2929">Aby można było współpracować z nośnikiem większym niż 4 GB, aplikacja używa *fx_media_extended_space_available* usługi.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2929">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2930">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2930">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2931">**media_ptr**: wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2931">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="2d0d2-2932">**available_bytes_ptr**: Pozostałe bajty pozostawione na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2932">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2933">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2933">Return Values</span></span>

- <span data-ttu-id="2d0d2-2934">**FX_SUCCESS** (0X00) pomyślnie zwróciło dostępne miejsce na nośniku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2934">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="2d0d2-2935">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2935">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-2936">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub wskaźnik dostępnych bajtów ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2936">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="2d0d2-2937">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2937">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2938">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2938">Allowed From</span></span>

<span data-ttu-id="2d0d2-2939">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2939">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2940">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2940">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2941">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2941">See Also</span></span>

- <span data-ttu-id="2d0d2-2942">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2942">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2943">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2943">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2944">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2944">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2945">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2945">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2946">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2946">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2947">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2947">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2948">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2948">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2949">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2949">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2950">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2950">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2951">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2951">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2952">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2952">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2953">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2953">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2954">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2954">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2955">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2955">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-2956">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2956">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2957">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2957">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2958">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2958">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="2d0d2-2959">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2959">fx_media_volume_get</span></span>

<span data-ttu-id="2d0d2-2960">Pobiera nazwę woluminu multimedialnego</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2960">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-2961">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2961">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="2d0d2-2962">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2962">Description</span></span>

<span data-ttu-id="2d0d2-2963">Ta usługa Pobiera nazwę woluminu poprzednio otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2963">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-2964">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2964">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-2965">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2965">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-2966">**volume_name**: wskaźnik do miejsca docelowego dla nazwy woluminu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2966">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="2d0d2-2967">Należy pamiętać, że miejsce docelowe musi być co najmniej wystarczająco duże, aby pomieścić 12 znaków.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2967">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="2d0d2-2968">**volume_source**: określa, gdzie pobrać nazwę z sektora rozruchowego lub katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2968">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="2d0d2-2969">Prawidłowe wartości tego parametru to:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2969">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="2d0d2-2970">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2970">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="2d0d2-2971">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2971">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-2972">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2972">Return Values</span></span>

- <span data-ttu-id="2d0d2-2973">**FX_SUCCESS** (0X00) pomyślne pobieranie woluminu multimedialnego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2973">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="2d0d2-2974">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2974">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-2975">Nie znaleziono woluminu **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2975">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="2d0d2-2976">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2976">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-2977">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik docelowy nośnika lub woluminu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2977">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="2d0d2-2978">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2978">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-2979">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2979">Allowed From</span></span>

<span data-ttu-id="2d0d2-2980">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2980">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-2981">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2981">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="2d0d2-2982">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2982">See Also</span></span>

- <span data-ttu-id="2d0d2-2983">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2983">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-2984">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2984">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-2985">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2985">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-2986">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2986">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-2987">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2987">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-2988">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2988">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-2989">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2989">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-2990">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2990">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-2991">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2991">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-2992">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2992">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-2993">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2993">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-2994">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2994">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-2995">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2995">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-2996">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2996">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-2997">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2997">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-2998">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2998">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-2999">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-2999">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="2d0d2-3000">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3000">fx_media_volume_get_extended</span></span>

<span data-ttu-id="2d0d2-3001">Pobiera nazwę nośnika z wcześniej otwartym nośnikiem</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3001">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3002">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3002">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="2d0d2-3003">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3003">Description</span></span>

<span data-ttu-id="2d0d2-3004">Ta usługa Pobiera nazwę woluminu poprzednio otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3004">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-3005">Ta usługa jest taka sama jak \***fx_media_volume_get ()** _, z wyjątkiem tego, że obiekt wywołujący ma rozmiar buforu _ \*volume_name\*\*.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3005">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3006">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3006">Input Parameters</span></span>


- <span data-ttu-id="2d0d2-3007">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3007">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-3008">**volume_name**: wskaźnik do miejsca docelowego dla nazwy woluminu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3008">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="2d0d2-3009">Należy pamiętać, że miejsce docelowe musi być co najmniej wystarczająco duże, aby pomieścić 12 znaków.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3009">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="2d0d2-3010">**volume_name_buffer_length**: rozmiar buforu volume_name.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3010">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="2d0d2-3011">**volume_source**: określa, gdzie pobrać nazwę z sektora rozruchowego lub katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3011">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="2d0d2-3012">Prawidłowe wartości tego parametru to:</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3012">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="2d0d2-3013">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3013">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="2d0d2-3014">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3014">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3015">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3015">Return Values</span></span>

- <span data-ttu-id="2d0d2-3016">**FX_SUCCESS** (0X00) pomyślne pobieranie woluminu multimedialnego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3016">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="2d0d2-3017">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3017">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3018">Nie znaleziono woluminu **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3018">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="2d0d2-3019">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3019">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-3020">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik docelowy nośnika lub woluminu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3020">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="2d0d2-3021">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3021">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3022">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3022">Allowed From</span></span>

<span data-ttu-id="2d0d2-3023">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3023">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3024">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3024">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-3025">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3025">See Also</span></span>

- <span data-ttu-id="2d0d2-3026">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3026">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-3027">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3027">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-3028">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3028">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-3029">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3029">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-3030">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3030">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-3031">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3031">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-3032">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3032">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-3033">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3033">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-3034">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3034">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-3035">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3035">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-3036">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3036">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-3037">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3037">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-3038">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3038">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-3039">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3039">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-3040">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3040">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-3041">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3041">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-3042">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3042">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="2d0d2-3043">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3043">fx_media_volume_set</span></span>

<span data-ttu-id="2d0d2-3044">Ustawia nazwę woluminu nośnika</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3044">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3045">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3045">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="2d0d2-3046">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3046">Description</span></span>

<span data-ttu-id="2d0d2-3047">Ta usługa ustawia nazwę woluminu poprzednio otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3047">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3048">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3048">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3049">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3049">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-3050">**volume_name**: wskaźnik do nazwy woluminu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3050">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3051">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3051">Return Values</span></span>

- <span data-ttu-id="2d0d2-3052">**FX_SUCCESS** (0x00) pomyślny zestaw woluminów multimedialnych.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3052">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="2d0d2-3053">**FX_INVALID_NAME** (0x0C) Volume_name jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3053">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="2d0d2-3054">**FX_MEDIA_INVALID** (0X02) nie może ustawić nazwy woluminu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3054">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="2d0d2-3055">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3055">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3056">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3056">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-3057">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3057">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-3058">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nazwy nośnika lub woluminu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3058">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="2d0d2-3059">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3059">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3060">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3060">Allowed From</span></span>

<span data-ttu-id="2d0d2-3061">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3061">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3062">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3062">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-3063">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3063">See Also</span></span>

- <span data-ttu-id="2d0d2-3064">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3064">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-3065">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3065">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-3066">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3066">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-3067">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3067">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-3068">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3068">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-3069">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3069">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-3070">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3070">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-3071">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3071">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-3072">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3072">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-3073">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3073">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-3074">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3074">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-3075">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3075">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-3076">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3076">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-3077">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3077">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-3078">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3078">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-3079">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3079">fx_media_write</span></span>
- <span data-ttu-id="2d0d2-3080">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3080">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="2d0d2-3081">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3081">fx_media_write</span></span>

<span data-ttu-id="2d0d2-3082">Zapisuje sektor logiczny</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3082">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3083">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3083">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="2d0d2-3084">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3084">Description</span></span>

<span data-ttu-id="2d0d2-3085">Ta usługa zapisuje podany bufor do określonego sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3085">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3086">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3086">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3087">**media_ptr**: wskaźnik do wcześniej otwartego nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3087">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="2d0d2-3088">**logical_sector**: sektor logiczny do zapisu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3088">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="2d0d2-3089">**buffer_ptr**: wskaźnik do źródła dla zapisu sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3089">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3090">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3090">Return Values</span></span>

- <span data-ttu-id="2d0d2-3091">Zakończono pomyślnie zapis nośnika **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3091">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="2d0d2-3092">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3092">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3093">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3093">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-3094">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3094">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-3095">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3095">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-3096">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3096">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="2d0d2-3097">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3097">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3098">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3098">Allowed From</span></span>

<span data-ttu-id="2d0d2-3099">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3099">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3100">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3100">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3101">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3101">See Also</span></span>

- <span data-ttu-id="2d0d2-3102">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3102">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="2d0d2-3103">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3103">fx_media_abort</span></span>
- <span data-ttu-id="2d0d2-3104">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3104">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="2d0d2-3105">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3105">fx_media_check</span></span>
- <span data-ttu-id="2d0d2-3106">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3106">fx_media_close</span></span>
- <span data-ttu-id="2d0d2-3107">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3107">fx_media_close_notify_set</span></span>
- <span data-ttu-id="2d0d2-3108">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3108">fx_media_exFAT_format</span></span>
- <span data-ttu-id="2d0d2-3109">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3109">fx_media_extended_space_available</span></span>
- <span data-ttu-id="2d0d2-3110">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3110">fx_media_flush</span></span>
- <span data-ttu-id="2d0d2-3111">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3111">fx_media_format</span></span>
- <span data-ttu-id="2d0d2-3112">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3112">fx_media_open</span></span>
- <span data-ttu-id="2d0d2-3113">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3113">fx_media_open_notify_set</span></span>
- <span data-ttu-id="2d0d2-3114">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3114">fx_media_read</span></span>
- <span data-ttu-id="2d0d2-3115">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3115">fx_media_space_available</span></span>
- <span data-ttu-id="2d0d2-3116">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3116">fx_media_volume_get</span></span>
- <span data-ttu-id="2d0d2-3117">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3117">fx_media_volume_set</span></span>
- <span data-ttu-id="2d0d2-3118">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3118">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="2d0d2-3119">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3119">fx_system_date_get</span></span>

<span data-ttu-id="2d0d2-3120">Pobiera datę systemu plików</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3120">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3121">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3121">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="2d0d2-3122">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3122">Description</span></span>

<span data-ttu-id="2d0d2-3123">Ta usługa zwraca bieżącą datę systemową.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3123">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3124">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3124">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3125">**Year**: wskaźnik do miejsca docelowego dla roku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3125">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="2d0d2-3126">**miesiąc**: wskaźnik do miejsca docelowego dla miesiąca.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3126">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="2d0d2-3127">**dzień**: wskaźnik do miejsca docelowego dla dnia.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3127">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3128">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3128">Return Values</span></span>

- <span data-ttu-id="2d0d2-3129">Pobieranie daty pomyślnego **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3129">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="2d0d2-3130">**FX_PTR_ERROR** (0X18) co najmniej jeden parametr wejściowy ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3130">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3131">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3131">Allowed From</span></span>

<span data-ttu-id="2d0d2-3132">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3133">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3133">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3134">See Also</span></span>

- <span data-ttu-id="2d0d2-3135">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3135">fx_system_date_set</span></span>
- <span data-ttu-id="2d0d2-3136">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3136">fx_system_initialize</span></span>
- <span data-ttu-id="2d0d2-3137">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3137">fx_system_time_get</span></span>
- <span data-ttu-id="2d0d2-3138">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3138">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="2d0d2-3139">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3139">fx_system_date_set</span></span>

<span data-ttu-id="2d0d2-3140">Ustawia datę systemową</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3140">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3141">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3141">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="2d0d2-3142">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3142">Description</span></span>

<span data-ttu-id="2d0d2-3143">Ta usługa ustawia datę systemową jako określoną.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3143">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-3144">*Ta usługa powinna być wywoływana wkrótce po **fx_system_initialize** , aby ustawić początkową datę systemową. Domyślnie Data systemowa to Ostatnia ogólna wersja FileX.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3144">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3145">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3145">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3146">**Year**: nowy rok.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3146">**year**: New year.</span></span> <span data-ttu-id="2d0d2-3147">Prawidłowy zakres jest z zakresu od 1980 do 2107.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3147">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="2d0d2-3148">**miesiąc**: nowy miesiąc.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3148">**month**: New month.</span></span> <span data-ttu-id="2d0d2-3149">Prawidłowy zakres to od 1 do 12.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3149">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="2d0d2-3150">**dzień**: nowy dzień.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3150">**day**: New day.</span></span> <span data-ttu-id="2d0d2-3151">Prawidłowy zakres to od 1 do 31, w zależności od miesiąca i warunków przestępnia.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3151">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3152">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3152">Return Values</span></span>

- <span data-ttu-id="2d0d2-3153">Ustawienie daty pomyślnego **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3153">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="2d0d2-3154">**FX_INVALID_YEAR** (0X12) nieprawidłowy określony rok.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3154">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="2d0d2-3155">**FX_INVALID_MONTH** (0X13) nieprawidłowy miesiąc.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3155">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="2d0d2-3156">Podano nieprawidłowy dzień **FX_INVALID_DAY** (0x14).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3156">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3157">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3157">Allowed From</span></span>

<span data-ttu-id="2d0d2-3158">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3158">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3159">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3159">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-3160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3160">See Also</span></span>

- <span data-ttu-id="2d0d2-3161">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3161">fx_system_date_get</span></span>
- <span data-ttu-id="2d0d2-3162">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3162">fx_system_initialize</span></span>
- <span data-ttu-id="2d0d2-3163">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3163">fx_system_time_get</span></span>
- <span data-ttu-id="2d0d2-3164">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3164">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="2d0d2-3165">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3165">fx_system_initialize</span></span>

<span data-ttu-id="2d0d2-3166">Inicjuje cały system</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3166">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3167">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3167">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="2d0d2-3168">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3168">Description</span></span>

<span data-ttu-id="2d0d2-3169">Ta usługa inicjuje wszystkie główne struktury danych FileX.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3169">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="2d0d2-3170">Powinien być wywoływany w ***tx_application_define*** lub prawdopodobnie z wątku inicjującego i musi zostać wywołany przed użyciem innej usługi FileX.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3170">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-3171">\* Po zainicjowaniu tego wywołania aplikacja powinna wywołać \***fx_system_date_set** _ i _ *fx_system_time_set\*\*, aby rozpocząć od dokładnej daty i godziny systemowej.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3171">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3172">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3172">Input Parameters</span></span>

<span data-ttu-id="2d0d2-3173">Brak</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3173">None</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3174">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3174">Return Values</span></span>

<span data-ttu-id="2d0d2-3175">Brak.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3175">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3176">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3176">Allowed From</span></span>

<span data-ttu-id="2d0d2-3177">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3178">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3178">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3179">See Also</span></span>

- <span data-ttu-id="2d0d2-3180">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3180">fx_system_date_get</span></span>
- <span data-ttu-id="2d0d2-3181">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3181">fx_system_date_set</span></span>
- <span data-ttu-id="2d0d2-3182">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3182">fx_system_time_get</span></span>
- <span data-ttu-id="2d0d2-3183">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3183">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="2d0d2-3184">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3184">fx_system_time_get</span></span>

<span data-ttu-id="2d0d2-3185">Pobiera bieżącą godzinę systemową</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3185">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3186">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3186">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="2d0d2-3187">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3187">Description</span></span>

<span data-ttu-id="2d0d2-3188">Ta usługa Pobiera bieżący czas systemowy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3188">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3189">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3189">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3190">**godzina**: wskaźnik do miejsca docelowego dla godziny.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3190">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="2d0d2-3191">**minuta**: wskaźnik do miejsca docelowego dla minuty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3191">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="2d0d2-3192">**sekundę**: wskaźnik do miejsca docelowego dla sekund.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3192">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3193">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3193">Return Values</span></span>

- <span data-ttu-id="2d0d2-3194">**FX_SUCCESS** (0X00) pomyślne pobieranie czasu systemu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3194">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="2d0d2-3195">**FX_PTR_ERROR** (0X18) co najmniej jeden parametr wejściowy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3195">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3196">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3196">Allowed From</span></span>

<span data-ttu-id="2d0d2-3197">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3197">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3198">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3198">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3199">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3199">See Also</span></span>

- <span data-ttu-id="2d0d2-3200">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3200">fx_system_date_get</span></span>
- <span data-ttu-id="2d0d2-3201">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3201">fx_system_date_set</span></span>
- <span data-ttu-id="2d0d2-3202">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3202">fx_system_initialize</span></span>
- <span data-ttu-id="2d0d2-3203">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3203">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="2d0d2-3204">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3204">fx_system_time_set</span></span>

<span data-ttu-id="2d0d2-3205">Ustawia bieżącą godzinę systemową</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3205">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3206">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3206">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="2d0d2-3207">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3207">Description</span></span>

<span data-ttu-id="2d0d2-3208">Ta usługa ustawia bieżący czas systemowy na określony przez parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3208">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-3209">*Ta usługa powinna być wywoływana wkrótce po **fx_system_initialize** , aby ustawić początkowy czas systemowy. Domyślnie czas systemowy to 0:0:0.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3209">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3210">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3210">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3211">**godzina**: Nowa godzina (0-23).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3211">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="2d0d2-3212">**minuta**: Nowa minuta (0-59).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3212">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="2d0d2-3213">**sekundę**: Nowa sekunda (0-59).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3213">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3214">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3214">Return Values</span></span>

- <span data-ttu-id="2d0d2-3215">**FX_SUCCESS** (0X00) pomyślne pobieranie czasu systemu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3215">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="2d0d2-3216">**FX_INVALID_HOUR**    (0X15) Nowa godzina jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3216">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="2d0d2-3217">**FX_INVALID_MINUTE** (0X16) Nowa minuta jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3217">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="2d0d2-3218">**FX_INVALID_SECOND** (0X17) Nowa sekunda jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3218">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3219">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3219">Allowed From</span></span>

<span data-ttu-id="2d0d2-3220">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3221">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3221">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="2d0d2-3222">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3222">See Also</span></span>

- <span data-ttu-id="2d0d2-3223">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3223">fx_system_date_get</span></span>
- <span data-ttu-id="2d0d2-3224">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3224">fx_system_date_set</span></span>
- <span data-ttu-id="2d0d2-3225">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3225">fx_system_initialize</span></span>
- <span data-ttu-id="2d0d2-3226">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3226">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="2d0d2-3227">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3227">fx_unicode_directory_create</span></span>

<span data-ttu-id="2d0d2-3228">Tworzy katalog Unicode</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3228">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3229">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3229">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="2d0d2-3230">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3230">Description</span></span>

<span data-ttu-id="2d0d2-3231">Ta usługa tworzy podkatalog o nazwie Unicode w bieżącym katalogu domyślnym — informacje o ścieżce nie są dozwolone w parametrze nazwy źródłowej Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3231">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="2d0d2-3232">Jeśli to się powiedzie, Nazwa krótka (format 8,3) nowo utworzonego podkatalogu Unicode jest zwracana przez usługę.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3232">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-3233">*Wszystkie operacje w podkatalogu Unicode (dzięki czemu ścieżka domyślna, usuwanie itp.) powinna zostać wykonana przez dostarczenie zwróconej skróconej nazwy (format 8,3) do standardowych usług katalogowych FileX.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3233">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-3234">*Ta usługa nie jest obsługiwana na nośniku exFAT.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3234">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3235">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3235">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3236">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3236">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-3237">**source_unicode_name**: wskaźnik do nazwy Unicode dla nowego podkatalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3237">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="2d0d2-3238">**source_unicode_length**: długość nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3238">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3239">**short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3) dla nowego podkatalogu Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3239">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3240">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3240">Return Values</span></span>

- <span data-ttu-id="2d0d2-3241">**FX_SUCCESS** (0X00) pomyślne utworzenie katalogu Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3241">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="2d0d2-3242">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3242">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3243">Określony katalog **FX_ALREADY_CREATED** (0x0B) już istnieje.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3243">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="2d0d2-3244">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej klastrów dostępnych w nośniku dla nowego wpisu katalogu.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3244">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="2d0d2-3245">Usługa **FX_NOT_IMPLEMENTED** (0x22) nie została zaimplementowana dla systemu plików exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3245">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="2d0d2-3246">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3246">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-3247">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3247">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="2d0d2-3248">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3248">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="2d0d2-3249">**FX_IO_ERROR (0x90)** Błąd we/wy sterownika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3249">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3250">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3250">Allowed From</span></span>

<span data-ttu-id="2d0d2-3251">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3252">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3252">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3253">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3253">See Also</span></span>

- <span data-ttu-id="2d0d2-3254">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3254">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-3255">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3255">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-3256">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3256">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-3257">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3257">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-3258">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3258">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-3259">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3259">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-3260">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3260">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-3261">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3261">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-3262">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3262">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-3263">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3263">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-3264">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3264">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-3265">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3265">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-3266">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3266">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-3267">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3267">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-3268">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3268">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-3269">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3269">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-3270">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3270">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-3271">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3271">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-3272">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3272">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-3273">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3273">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="2d0d2-3274">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3274">fx_unicode_directory_rename</span></span>

<span data-ttu-id="2d0d2-3275">Zmienia nazwę katalogu przy użyciu ciągu Unicode</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3275">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3276">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3276">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="2d0d2-3277">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3277">Description</span></span>

<span data-ttu-id="2d0d2-3278">Ta usługa zmienia podkatalog o nazwie Unicode na określoną nową nazwę Unicode w bieżącym katalogu roboczym.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3278">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="2d0d2-3279">Parametry nazwy Unicode nie mogą zawierać informacji o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3279">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-3280">*Ta usługa nie jest obsługiwana na nośniku exFAT.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3280">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3281">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3281">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3282">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3282">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-3283">**old_unicode_name**: wskaźnik do nazwy Unicode dla bieżącego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3283">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="2d0d2-3284">**old_unicode_name_length**: długość bieżącej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3284">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3285">**new_unicode_name**: wskaźnik do nowej nazwy pliku Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3285">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="2d0d2-3286">**old_unicode_name_length**: długość nowej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3286">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3287">**new_short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3) dla pliku Unicode o zmienionej nazwie.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3287">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="2d0d2-3288">Zmień nazwę katalogu na Unicode</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3288">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3289">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3289">Return Values</span></span>

- <span data-ttu-id="2d0d2-3290">Pomyślny otwarty nośnik **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3290">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="2d0d2-3291">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3291">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3292">**FX_ALREADY_CREATED** (0X0B) określona nazwa katalogu już istnieje.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3292">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="2d0d2-3293">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3293">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-3294">**FX_PTR_ERROR** (0X18) co najmniej jeden wskaźnik ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3294">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="2d0d2-3295">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3295">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="2d0d2-3296">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3296">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3297">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3297">Allowed From</span></span>

<span data-ttu-id="2d0d2-3298">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3298">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3299">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3299">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3300">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3300">See Also</span></span>

- <span data-ttu-id="2d0d2-3301">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3301">fx_directory_attributes_read</span></span>
- <span data-ttu-id="2d0d2-3302">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3302">fx_directory_attributes_set</span></span>
- <span data-ttu-id="2d0d2-3303">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3303">fx_directory_create</span></span>
- <span data-ttu-id="2d0d2-3304">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3304">fx_directory_default_get</span></span>
- <span data-ttu-id="2d0d2-3305">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3305">fx_directory_default_set</span></span>
- <span data-ttu-id="2d0d2-3306">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3306">fx_directory_delete</span></span>
- <span data-ttu-id="2d0d2-3307">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3307">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="2d0d2-3308">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3308">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-3309">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3309">fx_directory_information_get</span></span>
- <span data-ttu-id="2d0d2-3310">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3310">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="2d0d2-3311">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3311">fx_directory_local_path_get</span></span>
- <span data-ttu-id="2d0d2-3312">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3312">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="2d0d2-3313">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3313">fx_directory_local_path_set</span></span>
- <span data-ttu-id="2d0d2-3314">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3314">fx_directory_long_name_get</span></span>
- <span data-ttu-id="2d0d2-3315">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3315">fx_directory_name_test</span></span>
- <span data-ttu-id="2d0d2-3316">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3316">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="2d0d2-3317">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3317">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="2d0d2-3318">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3318">fx_directory_rename</span></span>
- <span data-ttu-id="2d0d2-3319">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3319">fx_directory_short_name_get</span></span>
- <span data-ttu-id="2d0d2-3320">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3320">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="2d0d2-3321">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3321">fx_unicode_file_create</span></span>

<span data-ttu-id="2d0d2-3322">Tworzy plik Unicode</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3322">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3323">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3323">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-3324">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3324">Description</span></span>

<span data-ttu-id="2d0d2-3325">Ta usługa tworzy plik o nazwie Unicode w bieżącym katalogu domyślnym — w parametrze nazwy źródła Unicode nie można używać informacji o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3325">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="2d0d2-3326">Jeśli to się powiedzie, Nazwa krótka (format 8,3) nowo utworzonego pliku Unicode jest zwracana przez usługę.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3326">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="2d0d2-3327">*Wszystkie operacje na pliku Unicode (otwieranie, zapisywanie, odczytywanie, zamykanie itp.) powinny być wykonywane przez dostarczenie zwróconej krótkiej nazwy (format 8,3) do standardowych usług plików FileX.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3327">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3328">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3328">Input Parameters</span></span>


- <span data-ttu-id="2d0d2-3329">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3329">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-3330">**source_unicode_name**: wskaźnik do nazwy Unicode dla nowego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3330">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="2d0d2-3331">**source_unicode_length**: długość nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3331">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3332">**short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3) dla nowego pliku Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3332">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3333">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3333">Return Values</span></span>

- <span data-ttu-id="2d0d2-3334">**FX_SUCCESS** (0X00) pomyślnie utworzono plik.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3334">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="2d0d2-3335">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3335">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3336">**FX_ALREADY_CREATED** (0X0B) określony plik już istnieje.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3336">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="2d0d2-3337">**FX_NO_MORE_SPACE** (0X0a) nie ma więcej klastrów dostępnych w nośniku dla nowego wpisu pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3337">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="2d0d2-3338">Usługa **FX_NOT_IMPLEMENTED** (0x22) nie została zaimplementowana dla systemu plików exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3338">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="2d0d2-3339">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3339">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-3340">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3340">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="2d0d2-3341">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3341">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="2d0d2-3342">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3342">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3343">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3343">Allowed From</span></span>

<span data-ttu-id="2d0d2-3344">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3344">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3345">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3345">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3346">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3346">See Also</span></span>

- <span data-ttu-id="2d0d2-3347">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3347">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-3348">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3348">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-3349">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3349">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-3350">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3350">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3351">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3351">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-3352">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3352">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-3353">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3353">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-3354">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3354">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-3355">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3355">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-3356">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3356">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3357">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3357">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3358">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3358">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-3359">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3359">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-3360">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3360">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3361">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3361">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-3362">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3362">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-3363">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3363">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3364">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3364">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-3365">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3365">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-3366">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3366">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-3367">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3367">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3368">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3368">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-3369">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3369">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-3370">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3370">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-3371">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3371">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-3372">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3372">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="2d0d2-3373">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3373">fx_unicode_file_rename</span></span>

<span data-ttu-id="2d0d2-3374">Zmienia nazwę pliku przy użyciu ciągu Unicode</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3374">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3375">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3375">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="2d0d2-3376">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3376">Description</span></span>

<span data-ttu-id="2d0d2-3377">Ta usługa zmienia nazwę pliku o nazwie Unicode na określoną nową nazwę Unicode w bieżącym katalogu domyślnym.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3377">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="2d0d2-3378">Parametry nazwy Unicode nie mogą zawierać informacji o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3378">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-3379">*Ta usługa nie jest obsługiwana na nośniku exFAT.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3379">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3380">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3380">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3381">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3381">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-3382">**old_unicode_name**: wskaźnik do nazwy Unicode dla bieżącego pliku.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3382">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="2d0d2-3383">**old_unicode_name_length**: długość bieżącej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3383">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3384">**new_unicode_name**: wskaźnik do nowej nazwy pliku Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3384">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="2d0d2-3385">**new_unicode_name_length**: długość nowej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3385">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3386">**new_short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3) dla pliku Unicode o zmienionej nazwie.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3386">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3387">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3387">Return Values</span></span>


- <span data-ttu-id="2d0d2-3388">Pomyślny otwarty nośnik **FX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3388">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="2d0d2-3389">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3389">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3390">**FX_ALREADY_CREATED** (0X0B) określona nazwa pliku już istnieje.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3390">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="2d0d2-3391">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3391">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-3392">**FX_PTR_ERROR** (0X18) co najmniej jeden wskaźnik ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3392">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="2d0d2-3393">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3393">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="2d0d2-3394">**FX_WRITE_PROTECT** (0X23) określony nośnik jest chroniony przed zapisem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3394">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3395">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3395">Allowed From</span></span>

<span data-ttu-id="2d0d2-3396">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3396">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3397">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3397">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3398">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3398">See Also</span></span>

- <span data-ttu-id="2d0d2-3399">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3399">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-3400">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3400">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-3401">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3401">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-3402">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3402">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3403">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3403">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-3404">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3404">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-3405">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3405">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-3406">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3406">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-3407">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3407">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-3408">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3408">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3409">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3409">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3410">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3410">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-3411">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3411">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-3412">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3412">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3413">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3413">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-3414">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3414">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-3415">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3415">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3416">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3416">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-3417">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3417">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-3418">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3418">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-3419">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3419">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3420">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3420">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-3421">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3421">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-3422">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3422">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-3423">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3423">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-3424">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3424">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="2d0d2-3425">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3425">fx_unicode_length_get</span></span>

<span data-ttu-id="2d0d2-3426">Pobiera długość nazwy Unicode</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3426">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3427">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3427">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="2d0d2-3428">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3428">Description</span></span>

<span data-ttu-id="2d0d2-3429">Ta usługa określa długość podanej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3429">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="2d0d2-3430">Znak Unicode jest reprezentowany przez dwa bajty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3430">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="2d0d2-3431">Nazwa Unicode to seria dwubajtowych znaków Unicode zakończonych przez dwa bajty NULL (dwa bajty wartości 0).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3431">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3432">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3432">Input Parameters</span></span>

<span data-ttu-id="2d0d2-3433">**unicode_name**: wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3433">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3434">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3434">Return Values</span></span>

<span data-ttu-id="2d0d2-3435">**Długość**: długość nazwy Unicode (liczba znaków Unicode w nazwie).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3435">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3436">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3436">Allowed From</span></span>

<span data-ttu-id="2d0d2-3437">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3438">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3438">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3439">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3439">See Also</span></span>

- <span data-ttu-id="2d0d2-3440">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3440">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-3441">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3441">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-3442">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3442">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-3443">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3443">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3444">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3444">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-3445">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3445">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-3446">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3446">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-3447">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3447">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-3448">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3448">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-3449">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3449">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3450">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3450">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3451">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3451">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-3452">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3452">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-3453">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3453">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3454">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3454">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-3455">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3455">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-3456">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3456">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3457">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3457">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-3458">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3458">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-3459">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3459">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-3460">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3460">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3461">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3461">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-3462">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3462">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-3463">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3463">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-3464">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3464">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-3465">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3465">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-3466">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3466">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="2d0d2-3467">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3467">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="2d0d2-3468">Pobiera długość nazwy Unicode</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3468">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3469">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3469">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="2d0d2-3470">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3470">Description</span></span>

<span data-ttu-id="2d0d2-3471">Ta usługa Pobiera długość podanej nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3471">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="2d0d2-3472">Znak Unicode jest reprezentowany przez dwa bajty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3472">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="2d0d2-3473">Nazwa Unicode to seria twobyte znaków Unicode zakończonych przez dwa bajty NULL (dwa bajty wartości 0).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3473">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-3474">*Ta usługa jest taka sama jak **fx_unicode_length_get ()** , z wyjątkiem tego, że obiekt wywołujący przekazuje rozmiar buforu **unicode_name** , łącznie z dwoma znakami null.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3474">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3475">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3475">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3476">**unicode_name**: wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3476">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3477">**BUFFER_LENGTH**: rozmiar buforu nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3477">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3478">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3478">Return Values</span></span>

<span data-ttu-id="2d0d2-3479">**Długość**: długość nazwy Unicode (liczba znaków Unicode w nazwie).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3479">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3480">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3480">Allowed From</span></span>

<span data-ttu-id="2d0d2-3481">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3481">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3482">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3482">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3483">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3483">See Also</span></span>

- <span data-ttu-id="2d0d2-3484">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3484">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-3485">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3485">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-3486">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3486">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-3487">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3487">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3488">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3488">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-3489">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3489">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-3490">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3490">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-3491">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3491">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-3492">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3492">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-3493">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3493">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3494">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3494">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3495">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3495">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-3496">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3496">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-3497">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3497">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3498">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3498">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-3499">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3499">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-3500">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3500">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3501">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3501">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-3502">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3502">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-3503">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3503">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-3504">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3504">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3505">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3505">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-3506">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3506">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-3507">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3507">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-3508">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3508">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-3509">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3509">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-3510">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3510">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="2d0d2-3511">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3511">fx_unicode_name_get</span></span>

<span data-ttu-id="2d0d2-3512">Pobiera nazwę Unicode z krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3512">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3513">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3513">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="2d0d2-3514">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3514">Description</span></span>

<span data-ttu-id="2d0d2-3515">Ta usługa Pobiera nazwę Unicode skojarzoną z podaną krótką nazwą (format 8,3) w bieżącym katalogu domyślnym — w parametrze krótkiej nazwy nie są dozwolone żadne informacje o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3515">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="2d0d2-3516">Jeśli to się powiedzie, nazwa Unicode skojarzona z krótką nazwą zostanie zwrócona przez usługę.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3516">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-3517">*Ta usługa może służyć do pobierania nazw Unicode zarówno dla plików, jak i podkatalogów.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3517">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3518">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3518">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3519">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3519">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-3520">**short_name** Wskaźnik na krótką nazwę (format 8,3).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3520">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="2d0d2-3521">**destination_unicode_name**: wskaźnik do miejsca docelowego dla nazwy Unicode skojarzonej z podaną krótką nazwą.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3521">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="2d0d2-3522">**destination_unicode_length**: wskaźnik do zwróconej długości nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3522">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3523">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3523">Return Values</span></span>

- <span data-ttu-id="2d0d2-3524">**FX_SUCCESS** (0X00) pomyślne pobranie nazwy w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3524">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="2d0d2-3525">**FX_FAT_READ_ERROR** (0X03) nie może odczytać tabeli FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3525">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="2d0d2-3526">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3526">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-3527">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3527">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-3528">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3528">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3529">Nie znaleziono krótkiej nazwy **FX_NOT_FOUND** (0x04) lub rozmiar miejsca docelowego Unicode jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3529">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="2d0d2-3530">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3530">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-3531">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3531">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="2d0d2-3532">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3532">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3533">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3533">Allowed From</span></span>

<span data-ttu-id="2d0d2-3534">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3535">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3535">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3536">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3536">See Also</span></span>

- <span data-ttu-id="2d0d2-3537">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3537">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-3538">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3538">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-3539">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3539">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-3540">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3540">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3541">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3541">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-3542">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3542">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-3543">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3543">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-3544">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3544">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-3545">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3545">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-3546">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3546">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3547">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3547">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3548">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3548">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-3549">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3549">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-3550">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3550">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3551">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3551">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-3552">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3552">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-3553">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3553">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3554">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3554">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-3555">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3555">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-3556">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3556">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-3557">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3557">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3558">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3558">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-3559">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3559">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-3560">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3560">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-3561">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3561">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-3562">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3562">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="2d0d2-3563">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3563">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="2d0d2-3564">Pobiera nazwę Unicode z krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3564">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3565">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3565">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="2d0d2-3566">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3566">Description</span></span>

<span data-ttu-id="2d0d2-3567">Ta usługa Pobiera nazwę Unicode skojarzoną z podaną krótką nazwą (format 8,3) w bieżącym katalogu domyślnym — w parametrze krótkiej nazwy nie są dozwolone żadne informacje o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3567">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="2d0d2-3568">Jeśli to się powiedzie, nazwa Unicode skojarzona z krótką nazwą zostanie zwrócona przez usługę.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3568">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-3569">\* Ta usługa jest taka sama jak \***fx_unicode_name_get**_, z wyjątkiem tego, że obiekt wywołujący dostarcza rozmiar docelowego buforu Unicode jako argument wejściowy. Dzięki temu usługa może zagwarantować, że nie zastąpi docelowego buforu Unicode_</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3569">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-3570">*Ta usługa może służyć do pobierania nazw Unicode zarówno dla plików, jak i podkatalogów.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3570">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3571">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3571">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3572">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3572">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-3573">**short_name**: wskaźnik do krótkiej nazwy (format 8,3).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3573">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="2d0d2-3574">**destination_unicode_name**: wskaźnik do miejsca docelowego dla nazwy Unicode skojarzonej z podaną krótką nazwą.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3574">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="2d0d2-3575">**destination_unicode_length**: wskaźnik do zwróconej długości nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3575">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="2d0d2-3576">**unicode_name_buffer_length**: rozmiar buforu nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3576">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="2d0d2-3577">Uwaga: wymagany jest terminator o wartości NULL, co powoduje dodatkowy bajt.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3577">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3578">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3578">Return Values</span></span>

- <span data-ttu-id="2d0d2-3579">**FX_SUCCESS** (0X00) pomyślne pobranie nazwy w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3579">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="2d0d2-3580">**FX_FAT_READ_ERROR** (0X03) nie może odczytać tabeli FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3580">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="2d0d2-3581">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3581">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-3582">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3582">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-3583">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3583">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3584">Nie znaleziono krótkiej nazwy **FX_NOT_FOUND** (0x04) lub rozmiar miejsca docelowego Unicode jest zbyt mały.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3584">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="2d0d2-3585">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3585">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-3586">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3586">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="2d0d2-3587">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3587">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3588">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3588">Allowed From</span></span>

<span data-ttu-id="2d0d2-3589">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3589">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3590">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3590">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3591">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3591">See Also</span></span>

- <span data-ttu-id="2d0d2-3592">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3592">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-3593">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3593">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-3594">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3594">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-3595">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3595">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3596">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3596">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-3597">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3597">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-3598">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3598">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-3599">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3599">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-3600">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3600">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-3601">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3601">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3602">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3602">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3603">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3603">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-3604">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3604">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-3605">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3605">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3606">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3606">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-3607">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3607">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-3608">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3608">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3609">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3609">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-3610">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3610">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-3611">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3611">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-3612">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3612">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3613">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3613">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-3614">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3614">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-3615">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3615">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-3616">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3616">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-3617">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3617">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="2d0d2-3618">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3618">fx_unicode_short_name_get</span></span>

<span data-ttu-id="2d0d2-3619">Pobiera krótką nazwę z nazwy Unicode</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3619">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3620">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3620">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="2d0d2-3621">Ta usługa pobiera krótką nazwę (format 8,3) skojarzoną z nazwą Unicode w bieżącym katalogu domyślnym — w parametrze nazwy Unicode nie można używać informacji o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3621">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="2d0d2-3622">Jeśli to się powiedzie, krótka nazwa skojarzona z nazwą Unicode jest zwracana przez usługę.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3622">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-3623">*Ta usługa może służyć do uzyskiwania krótkich nazw zarówno dla plików, jak i podkatalogów.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3623">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3624">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3624">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3625">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3625">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-3626">**source_unicode_name**: wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3626">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3627">**source_unicode_length**: długość nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3627">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3628">**destination_short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3628">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="2d0d2-3629">Musi mieć rozmiar co najmniej 13 bajtów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3629">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3630">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3630">Return Values</span></span>

- <span data-ttu-id="2d0d2-3631">**FX_SUCCESS** (0X00) pomyślne pobranie krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3631">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="2d0d2-3632">**FX_FAT_READ_ERROR** (0X03) nie może odczytać tabeli FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3632">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="2d0d2-3633">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3633">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="2d0d2-3634">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3634">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-3635">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3635">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3636">Nie znaleziono nazwy Unicode **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3636">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="2d0d2-3637">Usługa **FX_NOT_IMPLEMENTED** (0x22) nie została zaimplementowana dla systemu plików exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3637">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="2d0d2-3638">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3638">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-3639">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3639">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="2d0d2-3640">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3640">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3641">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3641">Allowed From</span></span>

<span data-ttu-id="2d0d2-3642">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3642">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3643">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3643">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3644">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3644">See Also</span></span>

- <span data-ttu-id="2d0d2-3645">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3645">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-3646">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3646">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-3647">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3647">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-3648">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3648">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3649">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3649">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-3650">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3650">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-3651">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3651">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-3652">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3652">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-3653">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3653">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-3654">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3654">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3655">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3655">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3656">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3656">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-3657">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3657">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-3658">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3658">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3659">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3659">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-3660">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3660">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-3661">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3661">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3662">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3662">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-3663">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3663">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-3664">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3664">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-3665">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3665">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3666">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3666">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-3667">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3667">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-3668">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3668">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-3669">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3669">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-3670">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3670">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="2d0d2-3671">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3671">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="2d0d2-3672">Pobiera krótką nazwę z nazwy Unicode</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3672">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="2d0d2-3673">Prototype</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3673">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="2d0d2-3674">Opis</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3674">Description</span></span>

<span data-ttu-id="2d0d2-3675">Ta usługa pobiera krótką nazwę (format 8,3) skojarzoną z nazwą Unicode w bieżącym katalogu domyślnym — w parametrze nazwy Unicode nie można używać informacji o ścieżce.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3675">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="2d0d2-3676">Jeśli to się powiedzie, krótka nazwa skojarzona z nazwą Unicode jest zwracana przez usługę.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3676">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2d0d2-3677">*Ta usługa jest taka sama jak **fx_unicode_short_name_get ()**, z wyjątkiem tego, że obiekt wywołujący dostarcza rozmiar buforu docelowego jako argument wejściowy. Dzięki temu usługa może zagwarantować, że krótka nazwa nie przekroczy bufora docelowego.*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3677">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="2d0d2-3678">*Ta usługa może służyć do uzyskiwania krótkich nazw zarówno dla plików, jak i podkatalogów*</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3678">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2d0d2-3679">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3679">Input Parameters</span></span>

- <span data-ttu-id="2d0d2-3680">**media_ptr**: wskaźnik do bloku kontroli nośnika.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3680">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="2d0d2-3681">**source_unicode_name**: wskaźnik do nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3681">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3682">**source_unicode_length**: długość nazwy Unicode.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3682">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="2d0d2-3683">**destination_short_name**: wskaźnik do miejsca docelowego dla krótkiej nazwy (format 8,3).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3683">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="2d0d2-3684">Musi mieć rozmiar co najmniej 13 bajtów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3684">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="2d0d2-3685">**short_name_buffer_length**: rozmiar buforu docelowego.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3685">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="2d0d2-3686">Rozmiar buforu musi wynosić co najmniej 14 bajtów.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3686">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="2d0d2-3687">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3687">Return Values</span></span>

- <span data-ttu-id="2d0d2-3688">**FX_SUCCESS** (0X00) pomyślne pobranie krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3688">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="2d0d2-3689">**FX_FAT_READ_ERROR** (0X03) nie może odczytać tabeli FAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3689">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="2d0d2-3690">Plik **FX_FILE_CORRUPT** (0x08) jest uszkodzony</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3690">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="2d0d2-3691">Błąd we/wy sterownika **FX_IO_ERROR** (0x90).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3691">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="2d0d2-3692">Określony nośnik **FX_MEDIA_NOT_OPEN** (0x11) nie jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3692">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="2d0d2-3693">Nie znaleziono nazwy Unicode **FX_NOT_FOUND** (0x04).</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3693">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="2d0d2-3694">Usługa **FX_NOT_IMPLEMENTED** (0x22) nie została zaimplementowana dla systemu plików exFAT.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3694">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="2d0d2-3695">**FX_SECTOR_INVALID** (0X89) nieprawidłowy sektor.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3695">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="2d0d2-3696">**FX_PTR_ERROR** (0X18) Nieprawidłowy wskaźnik nośnika lub nazwy.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3696">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="2d0d2-3697">Obiekt wywołujący **FX_CALLER_ERROR** (0x20) nie jest wątkiem.</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3697">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2d0d2-3698">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3698">Allowed From</span></span>

<span data-ttu-id="2d0d2-3699">Wątki</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3699">Threads</span></span>

### <a name="example"></a><span data-ttu-id="2d0d2-3700">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3700">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="2d0d2-3701">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3701">See Also</span></span>

- <span data-ttu-id="2d0d2-3702">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3702">fx_file_allocate</span></span>
- <span data-ttu-id="2d0d2-3703">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3703">fx_file_attributes_read</span></span>
- <span data-ttu-id="2d0d2-3704">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3704">fx_file_attributes_set</span></span>
- <span data-ttu-id="2d0d2-3705">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3705">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3706">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3706">fx_file_close</span></span>
- <span data-ttu-id="2d0d2-3707">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3707">fx_file_create</span></span>
- <span data-ttu-id="2d0d2-3708">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3708">fx_file_date_time_set</span></span>
- <span data-ttu-id="2d0d2-3709">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3709">fx_file_delete</span></span>
- <span data-ttu-id="2d0d2-3710">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3710">fx_file_extended_allocate</span></span>
- <span data-ttu-id="2d0d2-3711">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3711">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="2d0d2-3712">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3712">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3713">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3713">fx_file_extended_seek</span></span>
- <span data-ttu-id="2d0d2-3714">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3714">fx_file_extended_truncate</span></span>
- <span data-ttu-id="2d0d2-3715">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3715">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3716">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3716">fx_file_open</span></span>
- <span data-ttu-id="2d0d2-3717">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3717">fx_file_read</span></span>
- <span data-ttu-id="2d0d2-3718">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3718">fx_file_relative_seek</span></span>
- <span data-ttu-id="2d0d2-3719">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3719">fx_file_rename</span></span>
- <span data-ttu-id="2d0d2-3720">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3720">fx_file_seek</span></span>
- <span data-ttu-id="2d0d2-3721">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3721">fx_file_truncate</span></span>
- <span data-ttu-id="2d0d2-3722">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3722">fx_file_truncate_release</span></span>
- <span data-ttu-id="2d0d2-3723">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3723">fx_file_write</span></span>
- <span data-ttu-id="2d0d2-3724">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3724">fx_file_write_notify_set</span></span>
- <span data-ttu-id="2d0d2-3725">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3725">fx_unicode_file_create</span></span>
- <span data-ttu-id="2d0d2-3726">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3726">fx_unicode_file_rename</span></span>
- <span data-ttu-id="2d0d2-3727">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3727">fx_unicode_name_get</span></span>
- <span data-ttu-id="2d0d2-3728">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="2d0d2-3728">fx_unicode_short_name_get</span></span>
