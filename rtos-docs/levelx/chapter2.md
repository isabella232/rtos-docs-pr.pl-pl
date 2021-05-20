---
title: Rozdział 2 — Instalowanie i używanie Azure RTOS LevelX
description: Instalacja i użycie oprogramowania LevelX jest proste i opisane w poniższych sekcjach tego rozdziału.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 34110e74e8ad0a6acd376c00c1284a3ea715c5f5
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223319"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a><span data-ttu-id="e0870-103">Rozdział 2 — Instalowanie i używanie Azure RTOS LevelX</span><span class="sxs-lookup"><span data-stu-id="e0870-103">Chapter 2 - Installation and use of Azure RTOS LevelX</span></span>

<span data-ttu-id="e0870-104">Instalacja i korzystanie z Azure RTOS LevelX jest proste i opisane w poniższych sekcjach tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="e0870-104">Installation and use of Azure RTOS LevelX is straightforward and described in the following sections of this chapter.</span></span>

## <a name="distribution"></a><span data-ttu-id="e0870-105">Dystrybucja</span><span class="sxs-lookup"><span data-stu-id="e0870-105">Distribution</span></span>

<span data-ttu-id="e0870-106">LevelX jest dystrybuowany w języku ANSI C, gdzie każda funkcja znajduje się we własnym oddzielnym pliku C.</span><span class="sxs-lookup"><span data-stu-id="e0870-106">LevelX is distributed in ANSI C where each function is contained in its own separate C file.</span></span> <span data-ttu-id="e0870-107">Pliki w dystrybucji LevelX są następujące.</span><span class="sxs-lookup"><span data-stu-id="e0870-107">The files in the LevelX distribution are as follows.</span></span>
- <span data-ttu-id="e0870-108">lx_api.h</span><span class="sxs-lookup"><span data-stu-id="e0870-108">lx_api.h</span></span>
- <span data-ttu-id="e0870-109">lx_nand_flash_256byte_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="e0870-109">lx_nand_flash_256byte_ecc_check.c</span></span>
- <span data-ttu-id="e0870-110">lx_nand_flash_256byte_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="e0870-110">lx_nand_flash_256byte_ecc_compute.c</span></span>
- <span data-ttu-id="e0870-111">lx_nand_flash_block_full_update.c</span><span class="sxs-lookup"><span data-stu-id="e0870-111">lx_nand_flash_block_full_update.c</span></span>
- <span data-ttu-id="e0870-112">lx_nand_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="e0870-112">lx_nand_flash_block_reclaim.c</span></span>
- <span data-ttu-id="e0870-113">lx_nand_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="e0870-113">lx_nand_flash_close.c</span></span>
- <span data-ttu-id="e0870-114">lx_nand_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="e0870-114">lx_nand_flash_defragment.c</span></span>  
- <span data-ttu-id="e0870-115">lx_nand_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="e0870-115">lx_nand_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="e0870-116">lx_nand_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="e0870-116">lx_nand_flash_initialize.c</span></span>
- <span data-ttu-id="e0870-117">lx_nand_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="e0870-117">lx_nand_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="e0870-118">lx_nand_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="e0870-118">lx_nand_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="e0870-119">lx_nand_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="e0870-119">lx_nand_flash_open.c</span></span>
- <span data-ttu-id="e0870-120">lx_nand_flash_page_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="e0870-120">lx_nand_flash_page_ecc_check.c</span></span>
- <span data-ttu-id="e0870-121">lx_nand_flash_page_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="e0870-121">lx_nand_flash_page_ecc_compute.c</span></span>  
- <span data-ttu-id="e0870-122">lx_nand_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="e0870-122">lx_nand_flash_partial_defragment.c</span></span>
- <span data-ttu-id="e0870-123">lx_nand_flash_physical_page_allocate.c</span><span class="sxs-lookup"><span data-stu-id="e0870-123">lx_nand_flash_physical_page_allocate.c</span></span>
- <span data-ttu-id="e0870-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="e0870-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="e0870-125">lx_nand_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="e0870-125">lx_nand_flash_sector_read.c</span></span>
- <span data-ttu-id="e0870-126">lx_nand_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="e0870-126">lx_nand_flash_sector_release.c</span></span>
- <span data-ttu-id="e0870-127">lx_nand_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="e0870-127">lx_nand_flash_sector_write.c</span></span>
- <span data-ttu-id="e0870-128">lx_nand_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="e0870-128">lx_nand_flash_system_error.c</span></span>
- <span data-ttu-id="e0870-129">lx_nor_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="e0870-129">lx_nor_flash_block_reclaim.c</span></span>
- <span data-ttu-id="e0870-130">lx_nor_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="e0870-130">lx_nor_flash_close.c</span></span>
- <span data-ttu-id="e0870-131">lx_nor_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="e0870-131">lx_nor_flash_defragment.c</span></span>  
- <span data-ttu-id="e0870-132">lx_nor_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="e0870-132">lx_nor_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="e0870-133">lx_nor_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="e0870-133">lx_nor_flash_initialize.c</span></span>
- <span data-ttu-id="e0870-134">lx_nor_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="e0870-134">lx_nor_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="e0870-135">lx_nor_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="e0870-135">lx_nor_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="e0870-136">lx_nor_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="e0870-136">lx_nor_flash_open.c</span></span>
- <span data-ttu-id="e0870-137">lx_nor_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="e0870-137">lx_nor_flash_partial_defragment.c</span></span>
- <span data-ttu-id="e0870-138">lx_nor_flash_physical_sector_allocate.c</span><span class="sxs-lookup"><span data-stu-id="e0870-138">lx_nor_flash_physical_sector_allocate.c</span></span>
- <span data-ttu-id="e0870-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="e0870-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="e0870-140">lx_nor_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="e0870-140">lx_nor_flash_sector_read.c</span></span>
- <span data-ttu-id="e0870-141">lx_nor_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="e0870-141">lx_nor_flash_sector_release.c</span></span>
- <span data-ttu-id="e0870-142">lx_nor_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="e0870-142">lx_nor_flash_sector_write.c</span></span>
- <span data-ttu-id="e0870-143">lx_nor_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="e0870-143">lx_nor_flash_system_error.c</span></span>

<span data-ttu-id="e0870-144">Dostępne są również przykłady sterowników Symulator i FileX dla wystąpień LevelX NAND i NOR w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e0870-144">There are also simulator and FileX driver samples for both LevelX NAND and NOR instances, as follows.</span></span>

- <span data-ttu-id="e0870-145">demo_filex_nand_flash.c</span><span class="sxs-lookup"><span data-stu-id="e0870-145">demo_filex_nand_flash.c</span></span>  
- <span data-ttu-id="e0870-146">fx_nand_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="e0870-146">fx_nand_flash_simulated_driver.c</span></span>
- <span data-ttu-id="e0870-147">lx_nand_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="e0870-147">lx_nand_flash_simulator.c</span></span>
- <span data-ttu-id="e0870-148">demo_filex_nor_flash.c</span><span class="sxs-lookup"><span data-stu-id="e0870-148">demo_filex_nor_flash.c</span></span>  
- <span data-ttu-id="e0870-149">fx_nor_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="e0870-149">fx_nor_flash_simulated_driver.c</span></span>
- <span data-ttu-id="e0870-150">lx_nor_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="e0870-150">lx_nor_flash_simulator.c</span></span>

<span data-ttu-id="e0870-151">Oczywiście jeśli wymagana jest tylko flash NAND, potrzebne są tylko pliki flash NaND LevelX (***lx_nand_ \* .c).***</span><span class="sxs-lookup"><span data-stu-id="e0870-151">Of course, if only NAND flash is required, only the LevelX NAND flash files (***lx_nand_\*.c***) are needed.</span></span> <span data-ttu-id="e0870-152">Podobnie, jeśli wymagany jest tylko flash NOR, tylko pliki flash NOR (\*\*_lx_nor_ \_ .c!) są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="e0870-152">Similarly, if only NOR flash is required, only the NOR flash files (\*\*_lx_nor_\_.c\*\*\*) are needed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="e0870-153">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="e0870-153">Configuration Options</span></span>

<span data-ttu-id="e0870-154">LevelX można skonfigurować w czasie kompilacji za pomocą opisanych poniżej zdefiniowania warunkowego.</span><span class="sxs-lookup"><span data-stu-id="e0870-154">LevelX can be configured at compile time via the conditional defines described below.</span></span> <span data-ttu-id="e0870-155">Wystarczy dodać żądaną definicję do kompilacji każdego źródła LevelX, aby użyć opcji .</span><span class="sxs-lookup"><span data-stu-id="e0870-155">Simply add the desired define to the compilation of each LevelX source to use the option.</span></span>

- <span data-ttu-id="e0870-156">**LX_DIRECT_READ:** zdefiniowana, ta opcja pomija procedurę odczytu sterownika flash NOR na korzyść lub bezpośrednie odczytywanie pamięci NOR, co powoduje znaczny wzrost wydajności.</span><span class="sxs-lookup"><span data-stu-id="e0870-156">**LX_DIRECT_READ**:  Defined, this option bypasses the NOR flash driver read routine in favor or reading the NOR memory directly, resulting in a significant performance increase.</span></span>
- <span data-ttu-id="e0870-157">**LX_FREE_SECTOR_DATA_VERIFY:** Zdefiniowane, powoduje to, że otwarta logika LevelX NOR wystąpienia sprawdza, czy wszystkie sektory NIE są wolnymi sektorami.</span><span class="sxs-lookup"><span data-stu-id="e0870-157">**LX_FREE_SECTOR_DATA_VERIFY**: Defined, this causes the LevelX NOR instance open logic to verify free NOR sectors are all ones.</span></span>
- <span data-ttu-id="e0870-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE:** domyślnie ta wartość to 16 i definiuje rozmiar pamięci podręcznej mapowania sektorów logicznych.</span><span class="sxs-lookup"><span data-stu-id="e0870-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**:  By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="e0870-159">Duże wartości poprawiają wydajność, ale kosztują pamięć.</span><span class="sxs-lookup"><span data-stu-id="e0870-159">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="e0870-160">Minimalny rozmiar to 8, a wszystkie wartości muszą mieć potęgę 2.</span><span class="sxs-lookup"><span data-stu-id="e0870-160">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="e0870-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE:** zdefiniowane, powoduje utworzenie pamięci podręcznej mapowania bezpośredniego, tak aby nie było żadnych chybień pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="e0870-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Defined, this creates a direct mapping cache, such that there are no cache misses.</span></span> <span data-ttu-id="e0870-162">Wymaga to również LX_NAND_SECTOR_MAPPING_CACHE_SIZE reprezentuje dokładną liczbę wszystkich stron w urządzeniu flash.</span><span class="sxs-lookup"><span data-stu-id="e0870-162">It also requires that LX_NAND_SECTOR_MAPPING_CACHE_SIZE represents the exact number of total pages in your flash device.</span></span>
- <span data-ttu-id="e0870-163">**LX_NOR_DISABLE_EXTENDED_CACHE:** zdefiniowane, to wyłączyło rozszerzoną pamięć podręczną NOR.</span><span class="sxs-lookup"><span data-stu-id="e0870-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Defined, this disabled the extended NOR cache.</span></span>
- <span data-ttu-id="e0870-164">**LX_NOR_EXTENDED_CACHE_SIZE:** domyślnie ta wartość to 8, która reprezentuje maksymalnie 8 sektorów, które mogą być buforowane w wystąpieniu NOR.</span><span class="sxs-lookup"><span data-stu-id="e0870-164">**LX_NOR_EXTENDED_CACHE_SIZE**: By default this value is 8, which represents a maximum of 8 sectors that can be cached in a NOR instance.</span></span>
- <span data-ttu-id="e0870-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE:** domyślnie ta wartość to 16 i definiuje rozmiar pamięci podręcznej mapowania sektorów logicznych.</span><span class="sxs-lookup"><span data-stu-id="e0870-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="e0870-166">Duże wartości poprawiają wydajność, ale kosztują pamięć.</span><span class="sxs-lookup"><span data-stu-id="e0870-166">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="e0870-167">Minimalny rozmiar to 8, a wszystkie wartości muszą mieć potęgę 2.</span><span class="sxs-lookup"><span data-stu-id="e0870-167">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="e0870-168">**LX_THREAD_SAFE_ENABLE:** zdefiniowane, dzięki temu poziomX jest bezpieczny wątkowo przy użyciu obiektu mutex ThreadX w całym interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="e0870-168">**LX_THREAD_SAFE_ENABLE**: Defined, this makes LevelX thread-safe by using a ThreadX mutex object throughout the API.</span></span>
- <span data-ttu-id="e0870-169">**LX_STANDALONE_ENABLE:** zdefiniowane, umożliwia korzystanie z levelX w trybie autonomicznym (bez Azure RTOS).</span><span class="sxs-lookup"><span data-stu-id="e0870-169">**LX_STANDALONE_ENABLE**: Defined, enables LevelX to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="e0870-170">Domyślnie ten symbol nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="e0870-170">By default this symbol is not defined.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0870-171">W przypadku korzystania z bibliotek LevelX w trybie **autonomicznym (LX_STANDALONE_ENABLE** musi być zdefiniowany), pliki/biblioteki ThreadX nie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="e0870-171">When using LevelX in Standalone mode (**LX_STANDALONE_ENABLE** must be defined), ThreadX files/libraries are not required.</span></span> <span data-ttu-id="e0870-172">Funkcja bezpiecznej wątkowo funkcji LevelX jest wyłączona w tym trybie.</span><span class="sxs-lookup"><span data-stu-id="e0870-172">LevelX thread-safe feature is disabled in this mode.</span></span>

## <a name="using-levelx"></a><span data-ttu-id="e0870-173">Korzystanie z LevelX</span><span class="sxs-lookup"><span data-stu-id="e0870-173">Using LevelX</span></span>

<span data-ttu-id="e0870-174">Aby użyć levelX, samodzielnie lub z FileX, należy dołączyć plik \***lx_api.h** _ w kodzie, który odwołuje się do interfejsu API LevelX.</span><span class="sxs-lookup"><span data-stu-id="e0870-174">To use LevelX, either by itself or with FileX, include the file \***lx_api.h** _ in the code that references the LevelX API.</span></span> <span data-ttu-id="e0870-175">Upewnij się również, że kod obiektu LevelX jest dostępny w czasie łączenia.</span><span class="sxs-lookup"><span data-stu-id="e0870-175">Also ensure that the LevelX object code is available at link time.</span></span> <span data-ttu-id="e0870-176">Zapoznaj się z _*_plikami demo_filex_nand_flash.c_*_ i _ \*_demo_filex_nor_flash.c_\*\*, aby uzyskać przykłady użycia levelX.</span><span class="sxs-lookup"><span data-stu-id="e0870-176">Please examine the files _*_demo_filex_nand_flash.c_*_ and _ *_demo_filex_nor_flash.c_*\* for examples of how to use LevelX.</span></span>
