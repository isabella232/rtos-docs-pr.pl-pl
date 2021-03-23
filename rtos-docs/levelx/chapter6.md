---
title: Rozdział 6 — usługa Azure RTO LevelX lub interfejsy API
description: Usługa Azure RTO LevelX ani interfejsy API dostępne dla aplikacji.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ab7d3a7e431d7c8f49ef4f5cab9216dc77c8d33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822956"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a><span data-ttu-id="a1a9d-103">Rozdział 6 — usługa Azure RTO LevelX lub interfejsy API</span><span class="sxs-lookup"><span data-stu-id="a1a9d-103">Chapter 6 - Azure RTOS LevelX NOR APIs</span></span>

<span data-ttu-id="a1a9d-104">Usługa Azure RTO LevelX lub funkcje interfejsu API dostępne dla aplikacji są następujące.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-104">The Azure RTOS LevelX NOR API functions available to the application are as follows.</span></span>

- <span data-ttu-id="a1a9d-105">\***lx_nor_flash_close** _: _Close lub Flash wystąpienie \*</span><span class="sxs-lookup"><span data-stu-id="a1a9d-105">***lx_nor_flash_close** _: _Close NOR flash instance*</span></span>
- <span data-ttu-id="a1a9d-106">\***lx_nor_flash_defragment** _: _Defragment lub Flash wystąpienie \*</span><span class="sxs-lookup"><span data-stu-id="a1a9d-106">***lx_nor_flash_defragment** _: _Defragment NOR flash instance*</span></span>
- <span data-ttu-id="a1a9d-107">\***lx_nor_flash_extended_cache_enable** _: _Enable/Disable Extended lub cache \*</span><span class="sxs-lookup"><span data-stu-id="a1a9d-107">***lx_nor_flash_extended_cache_enable** _: _Enable/disable extended NOR cache*</span></span>
- <span data-ttu-id="a1a9d-108">\***lx_nor_flash_initialize** _: _Initialize lub Flash support \*</span><span class="sxs-lookup"><span data-stu-id="a1a9d-108">***lx_nor_flash_initialize** _: _Initialize NOR flash support*</span></span>
- <span data-ttu-id="a1a9d-109">\***lx_nor_flash_open** _: _Open lub Flash wystąpienie \*</span><span class="sxs-lookup"><span data-stu-id="a1a9d-109">***lx_nor_flash_open** _: _Open NOR flash instance*</span></span>
- <span data-ttu-id="a1a9d-110">\***lx_nor_flash_partial_defragment** _: _Partial defragmentacji wystąpienia lub Flash \*</span><span class="sxs-lookup"><span data-stu-id="a1a9d-110">***lx_nor_flash_partial_defragment** _: _Partial defragment of NOR flash instance*</span></span>
- <span data-ttu-id="a1a9d-111">\***lx_nor_flash_sector_read** _: _Read lub sektor Flash \*</span><span class="sxs-lookup"><span data-stu-id="a1a9d-111">***lx_nor_flash_sector_read** _: _Read NOR flash sector*</span></span>
- <span data-ttu-id="a1a9d-112">\***lx_nor_flash_sector_release** _: _Release lub sektor Flash \*</span><span class="sxs-lookup"><span data-stu-id="a1a9d-112">***lx_nor_flash_sector_release** _: _Release NOR flash sector*</span></span>
- <span data-ttu-id="a1a9d-113">\***lx_nor_flash_sector_write** _: _Write lub sektor Flash \*</span><span class="sxs-lookup"><span data-stu-id="a1a9d-113">***lx_nor_flash_sector_write** _: _Write NOR flash sector*</span></span>

## <a name="lx_nor_flash_close"></a><span data-ttu-id="a1a9d-114">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="a1a9d-114">lx_nor_flash_close</span></span>

<span data-ttu-id="a1a9d-115">Zamknij lub Flash wystąpienie</span><span class="sxs-lookup"><span data-stu-id="a1a9d-115">Close NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a1a9d-116">Prototype</span><span class="sxs-lookup"><span data-stu-id="a1a9d-116">Prototype</span></span>

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="a1a9d-117">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a9d-117">Description</span></span>

<span data-ttu-id="a1a9d-118">Ta usługa zamyka poprzednio otwarte i nieflash wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-118">This service closes the previously opened NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1a9d-119">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a1a9d-119">Input Parameters</span></span>

- <span data-ttu-id="a1a9d-120">*nor_flash*: ani na Flash wskaźnik wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-120">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1a9d-121">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a1a9d-121">Return Values</span></span>

- <span data-ttu-id="a1a9d-122">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-122">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="a1a9d-123">**LX_ERROR**: (0X01) błąd podczas zamykania wystąpienia Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-123">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1a9d-124">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a1a9d-124">Allowed From</span></span>

<span data-ttu-id="a1a9d-125">Wątki</span><span class="sxs-lookup"><span data-stu-id="a1a9d-125">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1a9d-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a9d-126">Example</span></span>

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="a1a9d-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1a9d-127">See Also</span></span>

- <span data-ttu-id="a1a9d-128">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-128">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="a1a9d-129">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="a1a9d-129">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="a1a9d-130">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="a1a9d-130">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="a1a9d-131">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="a1a9d-131">lx_nor_flash_open</span></span>
- <span data-ttu-id="a1a9d-132">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-132">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="a1a9d-133">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="a1a9d-133">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="a1a9d-134">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="a1a9d-134">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="a1a9d-135">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="a1a9d-135">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_defragment"></a><span data-ttu-id="a1a9d-136">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-136">lx_nor_flash_defragment</span></span>

<span data-ttu-id="a1a9d-137">Defragmentacja i wystąpienie programu Flash</span><span class="sxs-lookup"><span data-stu-id="a1a9d-137">Defragment NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a1a9d-138">Prototype</span><span class="sxs-lookup"><span data-stu-id="a1a9d-138">Prototype</span></span>

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="a1a9d-139">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a9d-139">Description</span></span>

<span data-ttu-id="a1a9d-140">Ta usługa defragmentuje poprzednio otwarte i nieflash wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-140">This service defragments the previously opened NOR flash instance.</span></span> <span data-ttu-id="a1a9d-141">Proces defragmentacji maksymalizuje liczbę wolnych sektorów i bloków.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-141">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1a9d-142">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a1a9d-142">Input Parameters</span></span>

- <span data-ttu-id="a1a9d-143">*nor_flash*: ani na Flash wskaźnik wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-143">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1a9d-144">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a1a9d-144">Return Values</span></span>

- <span data-ttu-id="a1a9d-145">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-145">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="a1a9d-146">**LX_ERROR**: (0X01) błąd podczas defragmentowania wystąpienia Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-146">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1a9d-147">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a1a9d-147">Allowed From</span></span>

<span data-ttu-id="a1a9d-148">Wątki</span><span class="sxs-lookup"><span data-stu-id="a1a9d-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1a9d-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a9d-149">Example</span></span>

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="a1a9d-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1a9d-150">See Also</span></span>

- <span data-ttu-id="a1a9d-151">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="a1a9d-151">lx_nor_flash_close</span></span>
- <span data-ttu-id="a1a9d-152">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="a1a9d-152">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="a1a9d-153">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="a1a9d-153">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="a1a9d-154">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="a1a9d-154">lx_nor_flash_open</span></span>
- <span data-ttu-id="a1a9d-155">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-155">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="a1a9d-156">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="a1a9d-156">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="a1a9d-157">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="a1a9d-157">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="a1a9d-158">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="a1a9d-158">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_extended_cache_enable"></a><span data-ttu-id="a1a9d-159">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="a1a9d-159">lx_nor_flash_extended_cache_enable</span></span>

<span data-ttu-id="a1a9d-160">Włącz/Wyłącz rozszerzoną lub buforowaną pamięć podręczną</span><span class="sxs-lookup"><span data-stu-id="a1a9d-160">Enable/disable extended NOR cache</span></span>

### <a name="prototype"></a><span data-ttu-id="a1a9d-161">Prototype</span><span class="sxs-lookup"><span data-stu-id="a1a9d-161">Prototype</span></span>

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="a1a9d-162">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a9d-162">Description</span></span>

<span data-ttu-id="a1a9d-163">Ta usługa służy do implementowania warstwy pamięci podręcznej sektora i w pamięci RAM przy użyciu pamięci dostarczonej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-163">This service implements a NOR sector cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="a1a9d-164">Każde 512 bajtów dostarczonej pamięci jest tłumaczone do jednego lub sektora, który może być buforowany.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-164">Each 512 bytes of memory supplied translates to one NOR sector that can be cached.</span></span> <span data-ttu-id="a1a9d-165">W pamięci podręcznej sektory są te, które zawierają informacje o kontrolkach bloku, np., liczba wymazów, Mapa wolnego sektora i informacje o mapowaniu sektorów.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-165">The sectors cached are those that contain the block control information, e.g., erase count, free sector map, and sector mapping information.</span></span> <span data-ttu-id="a1a9d-166">Sektory danych nie są przechowywane w tej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-166">Data sectors are not stored in this cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1a9d-167">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a1a9d-167">Input Parameters</span></span>

- <span data-ttu-id="a1a9d-168">**nor_flash**: ani na Flash wskaźnik wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-168">**nor_flash**: NOR flash instance pointer.</span></span>  
- <span data-ttu-id="a1a9d-169">**pamięć**: początkowy adres pamięci podręcznej wyrównany do ULONG dostępu.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-169">**memory**: Starting address for cache memory, aligned for ULONG access.</span></span> <span data-ttu-id="a1a9d-170">Wartość LX_NULL powoduje wyłączenie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-170">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="a1a9d-171">**rozmiar**: rozmiar w bajtach dostarczonej pamięci (powinien być wielokrotnością 512 bajtów).</span><span class="sxs-lookup"><span data-stu-id="a1a9d-171">**size**: The size in bytes of the memory supplied (should be multiple of 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="a1a9d-172">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a1a9d-172">Return Values</span></span>

- <span data-ttu-id="a1a9d-173">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-173">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="a1a9d-174">**LX_ERROR**: (0x01) za mało pamięci dla jednego i sektora.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-174">**LX_ERROR**: (0x01) Not enough memory for one NOR sector.</span></span>
- <span data-ttu-id="a1a9d-175">**LX_DISABLED**: (0X09) lub rozszerzona pamięć podręczna wyłączona przez opcję konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-175">**LX_DISABLED**: (0x09) NOR extended cache disabled by configuration option.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1a9d-176">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a1a9d-176">Allowed From</span></span>

<span data-ttu-id="a1a9d-177">Wątki</span><span class="sxs-lookup"><span data-stu-id="a1a9d-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1a9d-178">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a9d-178">Example</span></span>

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="a1a9d-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1a9d-179">See Also</span></span>

- <span data-ttu-id="a1a9d-180">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="a1a9d-180">lx_nor_flash_close</span></span>
- <span data-ttu-id="a1a9d-181">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-181">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="a1a9d-182">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="a1a9d-182">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="a1a9d-183">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="a1a9d-183">lx_nor_flash_open</span></span>
- <span data-ttu-id="a1a9d-184">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-184">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="a1a9d-185">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="a1a9d-185">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="a1a9d-186">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="a1a9d-186">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="a1a9d-187">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="a1a9d-187">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_initialize"></a><span data-ttu-id="a1a9d-188">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="a1a9d-188">lx_nor_flash_initialize</span></span>

<span data-ttu-id="a1a9d-189">Obsługa inicjowania i Flash</span><span class="sxs-lookup"><span data-stu-id="a1a9d-189">Initialize NOR flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="a1a9d-190">Prototype</span><span class="sxs-lookup"><span data-stu-id="a1a9d-190">Prototype</span></span>

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="a1a9d-191">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a9d-191">Description</span></span>

<span data-ttu-id="a1a9d-192">Ta usługa inicjuje usługę LevelX lub Flash support.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-192">This service initializes LevelX NOR flash support.</span></span> <span data-ttu-id="a1a9d-193">Musi być wywoływana przed wszystkimi innymi LevelXami i interfejsami API.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-193">It must be called before any other LevelX NOR APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1a9d-194">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a1a9d-194">Input Parameters</span></span>

- <span data-ttu-id="a1a9d-195">**Brak**</span><span class="sxs-lookup"><span data-stu-id="a1a9d-195">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="a1a9d-196">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a1a9d-196">Return Values</span></span>

- <span data-ttu-id="a1a9d-197">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-197">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="a1a9d-198">**LX_ERROR**: (0X01) błąd podczas inicjowania i obsługi Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-198">**LX_ERROR**: (0x01) Error initializing NOR flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1a9d-199">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a1a9d-199">Allowed From</span></span>

<span data-ttu-id="a1a9d-200">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="a1a9d-200">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1a9d-201">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a9d-201">Example</span></span>

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="a1a9d-202">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1a9d-202">See Also</span></span>

- <span data-ttu-id="a1a9d-203">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="a1a9d-203">lx_nor_flash_close</span></span>
- <span data-ttu-id="a1a9d-204">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-204">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="a1a9d-205">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="a1a9d-205">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="a1a9d-206">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-206">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="a1a9d-207">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="a1a9d-207">lx_nor_flash_open</span></span>
- <span data-ttu-id="a1a9d-208">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="a1a9d-208">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="a1a9d-209">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="a1a9d-209">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="a1a9d-210">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="a1a9d-210">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_open"></a><span data-ttu-id="a1a9d-211">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="a1a9d-211">lx_nor_flash_open</span></span>

<span data-ttu-id="a1a9d-212">Otwórz i uruchom wystąpienie</span><span class="sxs-lookup"><span data-stu-id="a1a9d-212">Open NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a1a9d-213">Prototype</span><span class="sxs-lookup"><span data-stu-id="a1a9d-213">Prototype</span></span>

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a><span data-ttu-id="a1a9d-214">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a9d-214">Description</span></span>

<span data-ttu-id="a1a9d-215">Ta usługa otwiera wystąpienie a i Flash z określonym i funkcją inicjowania sterownika.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-215">This service opens a NOR flash instance with the specified NOR flash control block and driver initialization function.</span></span> <span data-ttu-id="a1a9d-216">Należy pamiętać, że funkcja inicjowania sterownika jest odpowiedzialna za Instalowanie różnych wskaźników funkcji do odczytywania, pisania i wymazywania bloków sprzętu i niezwiązanych z tym wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-216">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks of the NOR hardware associated with this NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1a9d-217">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a1a9d-217">Input Parameters</span></span>

- <span data-ttu-id="a1a9d-218">*nor_flash*: ani na Flash wskaźnik wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-218">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="a1a9d-219">*Nazwa*: Nazwa i wystąpienie programu Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-219">*name*: Name of NOR flash instance.</span></span>
- <span data-ttu-id="a1a9d-220">*nor_driver_initialize*: wskaźnik funkcji do i funkcji inicjowania sterownika Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-220">*nor_driver_initialize*: Function pointer to NOR flash driver Initialization function.</span></span> <span data-ttu-id="a1a9d-221">Więcej informacji na temat obowiązków związanych z sterownikiem i ich Flash można znaleźć w rozdziale 5 tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-221">Please refer to Chapter 5 of this guide for more details on NOR flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1a9d-222">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a1a9d-222">Return Values</span></span>

- <span data-ttu-id="a1a9d-223">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-223">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="a1a9d-224">**LX_ERROR**: (0X01) błąd otwierania i wystąpienia Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-224">**LX_ERROR**: (0x01) Error opening NOR flash instance.</span></span>
- <span data-ttu-id="a1a9d-225">**LX_NO_MEMORY**: (0X08) sterownik nie dostarczył buforu do odczytu sektora none w pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-225">**LX_NO_MEMORY**:  (0x08) Driver did not provide buffer for reading none sector into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1a9d-226">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a1a9d-226">Allowed From</span></span>

<span data-ttu-id="a1a9d-227">Wątki</span><span class="sxs-lookup"><span data-stu-id="a1a9d-227">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1a9d-228">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a9d-228">Example</span></span>

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="a1a9d-229">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1a9d-229">See Also</span></span>

- <span data-ttu-id="a1a9d-230">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="a1a9d-230">lx_nor_flash_close</span></span>
- <span data-ttu-id="a1a9d-231">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-231">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="a1a9d-232">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="a1a9d-232">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="a1a9d-233">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="a1a9d-233">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="a1a9d-234">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-234">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="a1a9d-235">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="a1a9d-235">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="a1a9d-236">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="a1a9d-236">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="a1a9d-237">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="a1a9d-237">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_partial_defragment"></a><span data-ttu-id="a1a9d-238">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-238">lx_nor_flash_partial_defragment</span></span>

<span data-ttu-id="a1a9d-239">Częściowa defragmentacja lub wystąpienie programu Flash</span><span class="sxs-lookup"><span data-stu-id="a1a9d-239">Partial defragment of NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a1a9d-240">Prototype</span><span class="sxs-lookup"><span data-stu-id="a1a9d-240">Prototype</span></span>

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="a1a9d-241">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a9d-241">Description</span></span>

<span data-ttu-id="a1a9d-242">Ta usługa defragmentuje poprzednio otwarte lub Flash wystąpienie do maksymalnej liczby określonych bloków.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-242">This service defragments the previously opened NOR flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="a1a9d-243">Proces defragmentacji maksymalizuje liczbę wolnych sektorów i bloków.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-243">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1a9d-244">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a1a9d-244">Input Parameters</span></span>

- <span data-ttu-id="a1a9d-245">*nor_flash*: ani na Flash wskaźnik wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-245">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="a1a9d-246">*max_blocks*: Maksymalna liczba bloków.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-246">*max_blocks*: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1a9d-247">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a1a9d-247">Return Values</span></span>

- <span data-ttu-id="a1a9d-248">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-248">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="a1a9d-249">**LX_ERROR**: (0X01) błąd podczas defragmentowania wystąpienia Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-249">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1a9d-250">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a1a9d-250">Allowed From</span></span>

<span data-ttu-id="a1a9d-251">Wątki</span><span class="sxs-lookup"><span data-stu-id="a1a9d-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1a9d-252">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a9d-252">Example</span></span>

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="a1a9d-253">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1a9d-253">See Also</span></span>

- <span data-ttu-id="a1a9d-254">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="a1a9d-254">lx_nor_flash_close</span></span>
- <span data-ttu-id="a1a9d-255">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-255">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="a1a9d-256">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="a1a9d-256">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="a1a9d-257">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="a1a9d-257">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="a1a9d-258">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="a1a9d-258">lx_nor_flash_open</span></span>
- <span data-ttu-id="a1a9d-259">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="a1a9d-259">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="a1a9d-260">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="a1a9d-260">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="a1a9d-261">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="a1a9d-261">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_read"></a><span data-ttu-id="a1a9d-262">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="a1a9d-262">lx_nor_flash_sector_read</span></span>

<span data-ttu-id="a1a9d-263">Odczytaj i wycinek</span><span class="sxs-lookup"><span data-stu-id="a1a9d-263">Read NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="a1a9d-264">Prototype</span><span class="sxs-lookup"><span data-stu-id="a1a9d-264">Prototype</span></span>

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="a1a9d-265">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a9d-265">Description</span></span>

<span data-ttu-id="a1a9d-266">Ta usługa odczytuje sektor logiczny z wystąpienia i programu Flash i jeśli pomyślnie zwraca zawartość z podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-266">This service reads the logical sector from the NOR flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="a1a9d-267">Należy pamiętać, że rozmiar sektora nie jest zawsze 512 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-267">Note that NOR sector size is always 512 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1a9d-268">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a1a9d-268">Input Parameters</span></span>

- <span data-ttu-id="a1a9d-269">*nor_flash* LUB wskaźnik wystąpienia programu Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-269">*nor_flash* NOR flash instance pointer.</span></span>
- <span data-ttu-id="a1a9d-270">*logical_sector*: sektor logiczny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-270">*logical_sector*: Logical sector to read.</span></span>
- <span data-ttu-id="a1a9d-271">*bufor*: wskaźnik do miejsca docelowego dla zawartości sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-271">*buffer*: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="a1a9d-272">Należy pamiętać, że bufor jest przyjmowana jako 512 bajtów i wyrównany do ULONG dostępu.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-272">Note that the buffer is assumed to be 512 bytes and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1a9d-273">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a1a9d-273">Return Values</span></span>

- <span data-ttu-id="a1a9d-274">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-274">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="a1a9d-275">**LX_ERROR**: (0x01) odczytywanie błędów i sektory Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-275">**LX_ERROR**: (0x01) Error reading NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1a9d-276">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a1a9d-276">Allowed From</span></span>

<span data-ttu-id="a1a9d-277">Wątki</span><span class="sxs-lookup"><span data-stu-id="a1a9d-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1a9d-278">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a9d-278">Example</span></span>

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="a1a9d-279">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1a9d-279">See Also</span></span>

- <span data-ttu-id="a1a9d-280">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="a1a9d-280">lx_nor_flash_close</span></span>
- <span data-ttu-id="a1a9d-281">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-281">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="a1a9d-282">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="a1a9d-282">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="a1a9d-283">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="a1a9d-283">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="a1a9d-284">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="a1a9d-284">lx_nor_flash_open</span></span>
- <span data-ttu-id="a1a9d-285">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-285">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="a1a9d-286">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="a1a9d-286">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="a1a9d-287">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="a1a9d-287">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_release"></a><span data-ttu-id="a1a9d-288">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="a1a9d-288">lx_nor_flash_sector_release</span></span>

<span data-ttu-id="a1a9d-289">Wydanie lub sektor Flash</span><span class="sxs-lookup"><span data-stu-id="a1a9d-289">Release NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="a1a9d-290">Prototype</span><span class="sxs-lookup"><span data-stu-id="a1a9d-290">Prototype</span></span>

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="a1a9d-291">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a9d-291">Description</span></span>

<span data-ttu-id="a1a9d-292">Ta usługa zwalnia mapowanie sektora logicznego w wystąpieniu programu i programu Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-292">This service releases the logical sector mapping in the NOR flash instance.</span></span> <span data-ttu-id="a1a9d-293">Zwolnienie sektora logicznego, gdy nie jest używany, sprawia, że LevelX zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-293">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1a9d-294">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a1a9d-294">Input Parameters</span></span>

- <span data-ttu-id="a1a9d-295">*nor_flash*: ani na Flash wskaźnik wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-295">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="a1a9d-296">*logical_sector*: sektor logiczny do wydania.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-296">*logical_sector*: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1a9d-297">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a1a9d-297">Return Values</span></span>

- <span data-ttu-id="a1a9d-298">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-298">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="a1a9d-299">**LX_ERROR**: (0X01) błąd ani zapis sektora programu Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-299">**LX_ERROR**: (0x01) Error NOR flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1a9d-300">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a1a9d-300">Allowed From</span></span>

<span data-ttu-id="a1a9d-301">Wątki</span><span class="sxs-lookup"><span data-stu-id="a1a9d-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1a9d-302">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a9d-302">Example</span></span>

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="a1a9d-303">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1a9d-303">See Also</span></span>

- <span data-ttu-id="a1a9d-304">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="a1a9d-304">lx_nor_flash_close</span></span>
- <span data-ttu-id="a1a9d-305">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-305">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="a1a9d-306">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="a1a9d-306">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="a1a9d-307">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="a1a9d-307">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="a1a9d-308">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="a1a9d-308">lx_nor_flash_open</span></span>
- <span data-ttu-id="a1a9d-309">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-309">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="a1a9d-310">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="a1a9d-310">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="a1a9d-311">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="a1a9d-311">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_write"></a><span data-ttu-id="a1a9d-312">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="a1a9d-312">lx_nor_flash_sector_write</span></span>

<span data-ttu-id="a1a9d-313">Pisanie i sektory w programie Flash</span><span class="sxs-lookup"><span data-stu-id="a1a9d-313">Write NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="a1a9d-314">Prototype</span><span class="sxs-lookup"><span data-stu-id="a1a9d-314">Prototype</span></span>

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="a1a9d-315">Opis</span><span class="sxs-lookup"><span data-stu-id="a1a9d-315">Description</span></span>

<span data-ttu-id="a1a9d-316">Ta usługa Zapisuje określony sektor logiczny w wystąpieniu i programie Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-316">This service writes the specified logical sector in the NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a1a9d-317">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="a1a9d-317">Input Parameters</span></span>

- <span data-ttu-id="a1a9d-318">*nor_flash*: ani na Flash wskaźnik wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-318">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="a1a9d-319">*logical_sector*: sektor logiczny do zapisu.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-319">*logical_sector*: Logical sector to write.</span></span>
- <span data-ttu-id="a1a9d-320">*bufor*: wskaźnik do zawartości sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-320">*buffer*: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="a1a9d-321">Należy pamiętać, że bufor jest przyjmowana jako 512 bajtów wyrównany do ULONG dostępu.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-321">Note that the buffer is assumed to be 512 bytes aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="a1a9d-322">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="a1a9d-322">Return Values</span></span>

- <span data-ttu-id="a1a9d-323">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-323">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="a1a9d-324">**LX_NO_SECTORS**: (0X02) nie ma więcej dostępnych wolnych sektorów do przeprowadzenia zapisu.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-324">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="a1a9d-325">**LX_ERROR**: (0X01) błąd podczas zwalniania ani sektora Flash.</span><span class="sxs-lookup"><span data-stu-id="a1a9d-325">**LX_ERROR**: (0x01) Error releasing NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a1a9d-326">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="a1a9d-326">Allowed From</span></span>

<span data-ttu-id="a1a9d-327">Wątki</span><span class="sxs-lookup"><span data-stu-id="a1a9d-327">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a1a9d-328">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1a9d-328">Example</span></span>

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="a1a9d-329">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1a9d-329">See Also</span></span>

- <span data-ttu-id="a1a9d-330">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="a1a9d-330">lx_nor_flash_close</span></span>
- <span data-ttu-id="a1a9d-331">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-331">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="a1a9d-332">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="a1a9d-332">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="a1a9d-333">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="a1a9d-333">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="a1a9d-334">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="a1a9d-334">lx_nor_flash_open</span></span>
- <span data-ttu-id="a1a9d-335">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="a1a9d-335">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="a1a9d-336">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="a1a9d-336">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="a1a9d-337">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="a1a9d-337">lx_nor_flash_sector_release</span></span>
