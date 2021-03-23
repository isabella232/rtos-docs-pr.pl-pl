---
title: Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO LevelX
description: Instalacja i użycie programu LevelX są proste i opisane w poniższych sekcjach tego rozdziału.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 575776875452cfc718401556a6440d787cb18893
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822969"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a><span data-ttu-id="40b66-103">Rozdział 2 — Instalowanie i korzystanie z usługi Azure RTO LevelX</span><span class="sxs-lookup"><span data-stu-id="40b66-103">Chapter 2 - Installation and use of Azure RTOS LevelX</span></span>

<span data-ttu-id="40b66-104">Instalacja i użycie usługi Azure RTO LevelX jest proste i opisane w poniższych sekcjach tego rozdziału.</span><span class="sxs-lookup"><span data-stu-id="40b66-104">Installation and use of Azure RTOS LevelX is straightforward and described in the following sections of this chapter.</span></span>

## <a name="distribution"></a><span data-ttu-id="40b66-105">Dystrybucja</span><span class="sxs-lookup"><span data-stu-id="40b66-105">Distribution</span></span>

<span data-ttu-id="40b66-106">LevelX jest dystrybuowana w standardzie ANSI C, gdzie każda funkcja jest zawarta w osobnym pliku C.</span><span class="sxs-lookup"><span data-stu-id="40b66-106">LevelX is distributed in ANSI C where each function is contained in its own separate C file.</span></span> <span data-ttu-id="40b66-107">Pliki w dystrybucji LevelX są następujące.</span><span class="sxs-lookup"><span data-stu-id="40b66-107">The files in the LevelX distribution are as follows.</span></span>
- <span data-ttu-id="40b66-108">lx_api. h</span><span class="sxs-lookup"><span data-stu-id="40b66-108">lx_api.h</span></span>
- <span data-ttu-id="40b66-109">lx_nand_flash_256byte_ecc_check. c</span><span class="sxs-lookup"><span data-stu-id="40b66-109">lx_nand_flash_256byte_ecc_check.c</span></span>
- <span data-ttu-id="40b66-110">lx_nand_flash_256byte_ecc_compute. c</span><span class="sxs-lookup"><span data-stu-id="40b66-110">lx_nand_flash_256byte_ecc_compute.c</span></span>
- <span data-ttu-id="40b66-111">lx_nand_flash_block_full_update. c</span><span class="sxs-lookup"><span data-stu-id="40b66-111">lx_nand_flash_block_full_update.c</span></span>
- <span data-ttu-id="40b66-112">lx_nand_flash_block_reclaim. c</span><span class="sxs-lookup"><span data-stu-id="40b66-112">lx_nand_flash_block_reclaim.c</span></span>
- <span data-ttu-id="40b66-113">lx_nand_flash_close. c</span><span class="sxs-lookup"><span data-stu-id="40b66-113">lx_nand_flash_close.c</span></span>
- <span data-ttu-id="40b66-114">lx_nand_flash_defragment. c</span><span class="sxs-lookup"><span data-stu-id="40b66-114">lx_nand_flash_defragment.c</span></span>  
- <span data-ttu-id="40b66-115">lx_nand_flash_extended_cache_enable. c</span><span class="sxs-lookup"><span data-stu-id="40b66-115">lx_nand_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="40b66-116">lx_nand_flash_initialize. c</span><span class="sxs-lookup"><span data-stu-id="40b66-116">lx_nand_flash_initialize.c</span></span>
- <span data-ttu-id="40b66-117">lx_nand_flash_logical_sector_find. c</span><span class="sxs-lookup"><span data-stu-id="40b66-117">lx_nand_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="40b66-118">lx_nand_flash_next_block_to_erase_find. c</span><span class="sxs-lookup"><span data-stu-id="40b66-118">lx_nand_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="40b66-119">lx_nand_flash_open. c</span><span class="sxs-lookup"><span data-stu-id="40b66-119">lx_nand_flash_open.c</span></span>
- <span data-ttu-id="40b66-120">lx_nand_flash_page_ecc_check. c</span><span class="sxs-lookup"><span data-stu-id="40b66-120">lx_nand_flash_page_ecc_check.c</span></span>
- <span data-ttu-id="40b66-121">lx_nand_flash_page_ecc_compute. c</span><span class="sxs-lookup"><span data-stu-id="40b66-121">lx_nand_flash_page_ecc_compute.c</span></span>  
- <span data-ttu-id="40b66-122">lx_nand_flash_partial_defragment. c</span><span class="sxs-lookup"><span data-stu-id="40b66-122">lx_nand_flash_partial_defragment.c</span></span>
- <span data-ttu-id="40b66-123">lx_nand_flash_physical_page_allocate. c</span><span class="sxs-lookup"><span data-stu-id="40b66-123">lx_nand_flash_physical_page_allocate.c</span></span>
- <span data-ttu-id="40b66-124">lx_nand_flash_sector_mapping_cache_invalidate. c</span><span class="sxs-lookup"><span data-stu-id="40b66-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="40b66-125">lx_nand_flash_sector_read. c</span><span class="sxs-lookup"><span data-stu-id="40b66-125">lx_nand_flash_sector_read.c</span></span>
- <span data-ttu-id="40b66-126">lx_nand_flash_sector_release. c</span><span class="sxs-lookup"><span data-stu-id="40b66-126">lx_nand_flash_sector_release.c</span></span>
- <span data-ttu-id="40b66-127">lx_nand_flash_sector_write. c</span><span class="sxs-lookup"><span data-stu-id="40b66-127">lx_nand_flash_sector_write.c</span></span>
- <span data-ttu-id="40b66-128">lx_nand_flash_system_error. c</span><span class="sxs-lookup"><span data-stu-id="40b66-128">lx_nand_flash_system_error.c</span></span>
- <span data-ttu-id="40b66-129">lx_nor_flash_block_reclaim. c</span><span class="sxs-lookup"><span data-stu-id="40b66-129">lx_nor_flash_block_reclaim.c</span></span>
- <span data-ttu-id="40b66-130">lx_nor_flash_close. c</span><span class="sxs-lookup"><span data-stu-id="40b66-130">lx_nor_flash_close.c</span></span>
- <span data-ttu-id="40b66-131">lx_nor_flash_defragment. c</span><span class="sxs-lookup"><span data-stu-id="40b66-131">lx_nor_flash_defragment.c</span></span>  
- <span data-ttu-id="40b66-132">lx_nor_flash_extended_cache_enable. c</span><span class="sxs-lookup"><span data-stu-id="40b66-132">lx_nor_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="40b66-133">lx_nor_flash_initialize. c</span><span class="sxs-lookup"><span data-stu-id="40b66-133">lx_nor_flash_initialize.c</span></span>
- <span data-ttu-id="40b66-134">lx_nor_flash_logical_sector_find. c</span><span class="sxs-lookup"><span data-stu-id="40b66-134">lx_nor_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="40b66-135">lx_nor_flash_next_block_to_erase_find. c</span><span class="sxs-lookup"><span data-stu-id="40b66-135">lx_nor_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="40b66-136">lx_nor_flash_open. c</span><span class="sxs-lookup"><span data-stu-id="40b66-136">lx_nor_flash_open.c</span></span>
- <span data-ttu-id="40b66-137">lx_nor_flash_partial_defragment. c</span><span class="sxs-lookup"><span data-stu-id="40b66-137">lx_nor_flash_partial_defragment.c</span></span>
- <span data-ttu-id="40b66-138">lx_nor_flash_physical_sector_allocate. c</span><span class="sxs-lookup"><span data-stu-id="40b66-138">lx_nor_flash_physical_sector_allocate.c</span></span>
- <span data-ttu-id="40b66-139">lx_nor_flash_sector_mapping_cache_invalidate. c</span><span class="sxs-lookup"><span data-stu-id="40b66-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="40b66-140">lx_nor_flash_sector_read. c</span><span class="sxs-lookup"><span data-stu-id="40b66-140">lx_nor_flash_sector_read.c</span></span>
- <span data-ttu-id="40b66-141">lx_nor_flash_sector_release. c</span><span class="sxs-lookup"><span data-stu-id="40b66-141">lx_nor_flash_sector_release.c</span></span>
- <span data-ttu-id="40b66-142">lx_nor_flash_sector_write. c</span><span class="sxs-lookup"><span data-stu-id="40b66-142">lx_nor_flash_sector_write.c</span></span>
- <span data-ttu-id="40b66-143">lx_nor_flash_system_error. c</span><span class="sxs-lookup"><span data-stu-id="40b66-143">lx_nor_flash_system_error.c</span></span>

<span data-ttu-id="40b66-144">Dostępne są również przykłady sterowników i FileX dla LevelX ni i i wystąpień.</span><span class="sxs-lookup"><span data-stu-id="40b66-144">There are also simulator and FileX driver samples for both LevelX NAND and NOR instances, as follows.</span></span>

- <span data-ttu-id="40b66-145">demo_filex_nand_flash. c</span><span class="sxs-lookup"><span data-stu-id="40b66-145">demo_filex_nand_flash.c</span></span>  
- <span data-ttu-id="40b66-146">fx_nand_flash_simulated_driver. c</span><span class="sxs-lookup"><span data-stu-id="40b66-146">fx_nand_flash_simulated_driver.c</span></span>
- <span data-ttu-id="40b66-147">lx_nand_flash_simulator. c</span><span class="sxs-lookup"><span data-stu-id="40b66-147">lx_nand_flash_simulator.c</span></span>
- <span data-ttu-id="40b66-148">demo_filex_nor_flash. c</span><span class="sxs-lookup"><span data-stu-id="40b66-148">demo_filex_nor_flash.c</span></span>  
- <span data-ttu-id="40b66-149">fx_nor_flash_simulated_driver. c</span><span class="sxs-lookup"><span data-stu-id="40b66-149">fx_nor_flash_simulated_driver.c</span></span>
- <span data-ttu-id="40b66-150">lx_nor_flash_simulator. c</span><span class="sxs-lookup"><span data-stu-id="40b66-150">lx_nor_flash_simulator.c</span></span>

<span data-ttu-id="40b66-151">Oczywiście, jeśli tylko ni flash jest wymagany, wymagane są tylko pliki Flash ni LevelX (***lx_nand_ \* . c***).</span><span class="sxs-lookup"><span data-stu-id="40b66-151">Of course, if only NAND flash is required, only the LevelX NAND flash files (***lx_nand_\*.c***) are needed.</span></span> <span data-ttu-id="40b66-152">Podobnie, jeśli wymagany jest tylko plik lub Flash (\* \*_lx_nor_ \_ . c \* \* \*).</span><span class="sxs-lookup"><span data-stu-id="40b66-152">Similarly, if only NOR flash is required, only the NOR flash files (\*\*_lx_nor_\_.c\*\*\*) are needed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="40b66-153">Opcje konfiguracji</span><span class="sxs-lookup"><span data-stu-id="40b66-153">Configuration Options</span></span>

<span data-ttu-id="40b66-154">LevelX można skonfigurować w czasie kompilacji za pośrednictwem warunku zdefiniowanego poniżej.</span><span class="sxs-lookup"><span data-stu-id="40b66-154">LevelX can be configured at compile time via the conditional defines described below.</span></span> <span data-ttu-id="40b66-155">Wystarczy dodać odpowiednie polecenie Definiuj do kompilacji każdego źródła LevelX, aby można było użyć opcji.</span><span class="sxs-lookup"><span data-stu-id="40b66-155">Simply add the desired define to the compilation of each LevelX source to use the option.</span></span>

- <span data-ttu-id="40b66-156">**LX_DIRECT_READ**: zdefiniowane, ta opcja pomija procedurę odczytu lub sterownika programu Flash w celu zapełnienia lub odczytywania bezwolnej pamięci, co znacznie zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="40b66-156">**LX_DIRECT_READ**:  Defined, this option bypasses the NOR flash driver read routine in favor or reading the NOR memory directly, resulting in a significant performance increase.</span></span>
- <span data-ttu-id="40b66-157">**LX_FREE_SECTOR_DATA_VERIFY**: zdefiniowane, spowoduje to, że LevelX i niezależne od wystąpień logikę można zweryfikować bezpłatnie, ani sektorów.</span><span class="sxs-lookup"><span data-stu-id="40b66-157">**LX_FREE_SECTOR_DATA_VERIFY**: Defined, this causes the LevelX NOR instance open logic to verify free NOR sectors are all ones.</span></span>
- <span data-ttu-id="40b66-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: Domyślnie ta wartość to 16 i definiuje rozmiar pamięci podręcznej mapowania sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="40b66-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**:  By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="40b66-159">Duże wartości zwiększają wydajność, ale kosztem pamięci.</span><span class="sxs-lookup"><span data-stu-id="40b66-159">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="40b66-160">Minimalny rozmiar to 8, a wszystkie wartości muszą być potęgą liczby 2.</span><span class="sxs-lookup"><span data-stu-id="40b66-160">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="40b66-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: zdefiniowane, spowoduje to utworzenie bezpośredniej pamięci podręcznej mapowania, tak że nie ma żadnych chybień w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="40b66-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Defined, this creates a direct mapping cache, such that there are no cache misses.</span></span> <span data-ttu-id="40b66-162">Wymaga również, aby LX_NAND_SECTOR_MAPPING_CACHE_SIZE reprezentuje dokładną liczbę stron na urządzeniu Flash.</span><span class="sxs-lookup"><span data-stu-id="40b66-162">It also requires that LX_NAND_SECTOR_MAPPING_CACHE_SIZE represents the exact number of total pages in your flash device.</span></span>
- <span data-ttu-id="40b66-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: zdefiniowane, wyłączono rozszerzoną pamięć podręczną.</span><span class="sxs-lookup"><span data-stu-id="40b66-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Defined, this disabled the extended NOR cache.</span></span>
- <span data-ttu-id="40b66-164">**LX_NOR_EXTENDED_CACHE_SIZE**: Domyślnie ta wartość to 8, która reprezentuje maksymalnie 8 sektorów, które mogą być buforowane w wystąpieniu i.</span><span class="sxs-lookup"><span data-stu-id="40b66-164">**LX_NOR_EXTENDED_CACHE_SIZE**: By default this value is 8, which represents a maximum of 8 sectors that can be cached in a NOR instance.</span></span>
- <span data-ttu-id="40b66-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: Domyślnie ta wartość to 16 i definiuje rozmiar pamięci podręcznej mapowania sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="40b66-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="40b66-166">Duże wartości zwiększają wydajność, ale kosztem pamięci.</span><span class="sxs-lookup"><span data-stu-id="40b66-166">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="40b66-167">Minimalny rozmiar to 8, a wszystkie wartości muszą być potęgą liczby 2.</span><span class="sxs-lookup"><span data-stu-id="40b66-167">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="40b66-168">**LX_THREAD_SAFE_ENABLE**: zdefiniowane, sprawia, że LevelX bezpieczne wątki przy użyciu obiektu mutex ThreadX w całym interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="40b66-168">**LX_THREAD_SAFE_ENABLE**: Defined, this makes LevelX thread-safe by using a ThreadX mutex object throughout the API.</span></span>

## <a name="using-levelx"></a><span data-ttu-id="40b66-169">Korzystanie z LevelX</span><span class="sxs-lookup"><span data-stu-id="40b66-169">Using LevelX</span></span>

<span data-ttu-id="40b66-170">Aby użyć LevelX, albo samodzielnie lub z FileX, Uwzględnij plik \***lx_api. h** _ w kodzie, który odwołuje się do interfejsu API LevelX.</span><span class="sxs-lookup"><span data-stu-id="40b66-170">To use LevelX, either by itself or with FileX, include the file \***lx_api.h** _ in the code that references the LevelX API.</span></span> <span data-ttu-id="40b66-171">Upewnij się również, że kod obiektu LevelX jest dostępny w czasie łącza.</span><span class="sxs-lookup"><span data-stu-id="40b66-171">Also ensure that the LevelX object code is available at link time.</span></span> <span data-ttu-id="40b66-172">Zapoznaj się z plikami _*_demo_filex_nand_flash. c_*_ i _ \*_demo_filex_nor_flash. c_\*\*, aby poznać przykłady użycia LevelX.</span><span class="sxs-lookup"><span data-stu-id="40b66-172">Please examine the files _*_demo_filex_nand_flash.c_*_ and _ *_demo_filex_nor_flash.c_*\* for examples of how to use LevelX.</span></span>
