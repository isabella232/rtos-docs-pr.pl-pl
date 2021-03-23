---
title: Rozdział 4 — interfejsy API usługi Azure RTO LevelX ni
description: Interfejsy API usługi Azure RTO LevelX ni dostępne dla aplikacji.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73bb94768396b4b8461791a164a102d1f8ef159f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104822968"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a><span data-ttu-id="adec5-103">Rozdział 4 — interfejsy API usługi Azure RTO LevelX ni</span><span class="sxs-lookup"><span data-stu-id="adec5-103">Chapter 4 - Azure RTOS LevelX NAND APIs</span></span>

<span data-ttu-id="adec5-104">Dostępne dla aplikacji interfejsy API platformy Azure RTO LevelX ni:</span><span class="sxs-lookup"><span data-stu-id="adec5-104">The Azure RTOS LevelX NAND APIs available to the application are:</span></span>

- <span data-ttu-id="adec5-105">\***lx_nand_flash_close** _: _Close ni Flash \*</span><span class="sxs-lookup"><span data-stu-id="adec5-105">***lx_nand_flash_close** _: _Close NAND flash instance*</span></span>
- <span data-ttu-id="adec5-106">\***lx_nand_flash_defragment** _: _Defragment ni Flash \*</span><span class="sxs-lookup"><span data-stu-id="adec5-106">***lx_nand_flash_defragment** _: _Defragment NAND flash instance*</span></span>
- <span data-ttu-id="adec5-107">\***lx_nand_flash_extended_cache_enable** _: _Enable/Disable Extended ni cache \*</span><span class="sxs-lookup"><span data-stu-id="adec5-107">***lx_nand_flash_extended_cache_enable** _: _Enable/disable extended NAND cache*</span></span>
- <span data-ttu-id="adec5-108">\***lx_nand_flash_initialize** _: _Initialize ni lampy błyskowej \*</span><span class="sxs-lookup"><span data-stu-id="adec5-108">***lx_nand_flash_initialize** _: _Initialize NAND flash support*</span></span>
- <span data-ttu-id="adec5-109">\***lx_nand_flash_open** _: _Open ni Flash \*</span><span class="sxs-lookup"><span data-stu-id="adec5-109">***lx_nand_flash_open** _: _Open NAND flash instance*</span></span>
- <span data-ttu-id="adec5-110">\***lx_nand_flash_page_ecc_check** _: Strona _Check dla błędów ECC z poprawką \*</span><span class="sxs-lookup"><span data-stu-id="adec5-110">***lx_nand_flash_page_ecc_check** _: _Check page for ECC errors with correction*</span></span>
- <span data-ttu-id="adec5-111">\***lx_nand_flash_page_ecc_compute** _: _Computes ECC dla strony \*</span><span class="sxs-lookup"><span data-stu-id="adec5-111">***lx_nand_flash_page_ecc_compute** _: _Computes ECC for page*</span></span>
- <span data-ttu-id="adec5-112">\***lx_nand_flash_partial_defragment** _: _Partial defragmentacji wystąpienia ni Flash \*</span><span class="sxs-lookup"><span data-stu-id="adec5-112">***lx_nand_flash_partial_defragment** _: _Partial defragment of NAND flash instance*</span></span>
- <span data-ttu-id="adec5-113">\***lx_nand_flash_sector_read** _: _Read ni Flash \*</span><span class="sxs-lookup"><span data-stu-id="adec5-113">***lx_nand_flash_sector_read** _: _Read NAND flash sector*</span></span>
- <span data-ttu-id="adec5-114">\***lx_nand_flash_sector_release** _: _Release ni Flash \*</span><span class="sxs-lookup"><span data-stu-id="adec5-114">***lx_nand_flash_sector_release** _: _Release NAND flash sector*</span></span>
- <span data-ttu-id="adec5-115">\***lx_nand_flash_sector_write** _: _Write ni Flash \*</span><span class="sxs-lookup"><span data-stu-id="adec5-115">***lx_nand_flash_sector_write** _: _Write NAND flash sector*</span></span>

## <a name="lx_nand_flash_close"></a><span data-ttu-id="adec5-116">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-116">lx_nand_flash_close</span></span>

<span data-ttu-id="adec5-117">Zamknij wystąpienie ni Flash</span><span class="sxs-lookup"><span data-stu-id="adec5-117">Close NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-118">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-118">Prototype</span></span>

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="adec5-119">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-119">Description</span></span>

<span data-ttu-id="adec5-120">Ta usługa zamyka poprzednio otwarte wystąpienie ni Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-120">This service closes the previously opened NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-121">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-121">Input Parameters</span></span>

- <span data-ttu-id="adec5-122">**nand_flash**: wskaźnik wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-122">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-123">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-123">Return Values</span></span>

- <span data-ttu-id="adec5-124">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="adec5-124">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="adec5-125">**LX_ERROR**: (0X01) błąd podczas zamykania wystąpienia Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-125">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-126">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-126">Allowed From</span></span>

<span data-ttu-id="adec5-127">Wątki</span><span class="sxs-lookup"><span data-stu-id="adec5-127">Threads</span></span>

### <a name="example"></a><span data-ttu-id="adec5-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-128">Example</span></span>

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="adec5-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-129">See Also</span></span>

- <span data-ttu-id="adec5-130">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-130">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="adec5-131">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-131">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="adec5-132">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-132">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="adec5-133">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-133">lx_nand_flash_open</span></span>
- <span data-ttu-id="adec5-134">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-134">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="adec5-135">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-135">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="adec5-136">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-136">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="adec5-137">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-137">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="adec5-138">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-138">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="adec5-139">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-139">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_defragment"></a><span data-ttu-id="adec5-140">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-140">lx_nand_flash_defragment</span></span>

<span data-ttu-id="adec5-141">Defragmentacja wystąpienia programu ni Flash</span><span class="sxs-lookup"><span data-stu-id="adec5-141">Defragment NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-142">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-142">Prototype</span></span>

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="adec5-143">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-143">Description</span></span>

<span data-ttu-id="adec5-144">Ta usługa defragmentuje poprzednio otwarte wystąpienie ni Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-144">This service defragments the previously opened NAND flash instance.</span></span> <span data-ttu-id="adec5-145">Proces defragmentacji maksymalizuje liczbę bezpłatnych stron i bloków.</span><span class="sxs-lookup"><span data-stu-id="adec5-145">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-146">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-146">Input Parameters</span></span>

- <span data-ttu-id="adec5-147">**nand_flash**: wskaźnik wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-147">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-148">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-148">Return Values</span></span>

- <span data-ttu-id="adec5-149">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="adec5-149">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="adec5-150">**LX_ERROR**: (0X01) błąd podczas defragmentowania wystąpienia Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-150">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-151">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-151">Allowed From</span></span>

<span data-ttu-id="adec5-152">Wątki</span><span class="sxs-lookup"><span data-stu-id="adec5-152">Threads</span></span>

### <a name="example"></a><span data-ttu-id="adec5-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-153">Example</span></span>

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="adec5-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-154">See Also</span></span>

- <span data-ttu-id="adec5-155">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-155">lx_nand_flash_close</span></span>
- <span data-ttu-id="adec5-156">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-156">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="adec5-157">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-157">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="adec5-158">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-158">lx_nand_flash_open</span></span>
- <span data-ttu-id="adec5-159">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-159">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="adec5-160">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-160">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="adec5-161">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-161">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="adec5-162">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-162">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="adec5-163">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-163">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="adec5-164">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-164">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_extended_cache_enable"></a><span data-ttu-id="adec5-165">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-165">lx_nand_flash_extended_cache_enable</span></span>

<span data-ttu-id="adec5-166">Włącz/Wyłącz rozszerzoną pamięć podręczną ni</span><span class="sxs-lookup"><span data-stu-id="adec5-166">Enable/disable extended NAND cache</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-167">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-167">Prototype</span></span>

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="adec5-168">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-168">Description</span></span>

<span data-ttu-id="adec5-169">Ta usługa implementuje warstwę pamięci podręcznej w pamięci RAM przy użyciu pamięci dostarczonej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="adec5-169">This service implements a cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="adec5-170">Łączną ilość pamięci wymaganą do pełnej operacji pamięci podręcznej można obliczyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="adec5-170">The total amount of memory required for full cache operation can be calculated as follows:</span></span>

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

<span data-ttu-id="adec5-171">Jeśli dostarczona pamięć nie jest wystarczająco duża, aby pomieścić pełną pamięć podręczną ni, ta procedura spowoduje włączenie tak dużej ilości pamięci podręcznej ni Flash, jak to możliwe, na podstawie dostarczonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="adec5-171">If the supplied memory is not large enough to accommodate the full NAND cache, this routine will enable as much of the NAND flash cache as possible based on the memory supplied.</span></span>

<span data-ttu-id="adec5-172">Pamięć podręczna ni jest wyłączona, jeśli określony adres pamięci ma wartość NULL.</span><span class="sxs-lookup"><span data-stu-id="adec5-172">The NAND cache is disabled if the memory address specified is NULL.</span></span> <span data-ttu-id="adec5-173">W związku z tym pamięć podręczna ni może być używana w sposób tymczasowy.</span><span class="sxs-lookup"><span data-stu-id="adec5-173">Hence, the NAND cache maybe be used in a temporary fashion.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-174">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-174">Input Parameters</span></span>

- <span data-ttu-id="adec5-175">**nand_flash**: wskaźnik wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-175">**nand_flash**: NAND flash instance pointer.</span></span>  
- <span data-ttu-id="adec5-176">**pamięć**: adres początkowy dla pamięci podręcznej wyrównany do ULONG dostępu.</span><span class="sxs-lookup"><span data-stu-id="adec5-176">**memory**: Starting address for cache memory aligned for ULONG access.</span></span> <span data-ttu-id="adec5-177">Wartość LX_NULL powoduje wyłączenie pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="adec5-177">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="adec5-178">**rozmiar**: rozmiar w bajtach dostarczonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="adec5-178">**size**: The size in bytes of the memory supplied.</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-179">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-179">Return Values</span></span>

- <span data-ttu-id="adec5-180">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="adec5-180">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="adec5-181">**LX_ERROR**: (0x01) za mało pamięci dla jednego elementu pamięci podręcznej ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-181">**LX_ERROR**: (0x01) Not enough memory for one element of the NAND cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-182">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-182">Allowed From</span></span>

<span data-ttu-id="adec5-183">Wątki</span><span class="sxs-lookup"><span data-stu-id="adec5-183">Threads</span></span>

### <a name="example"></a><span data-ttu-id="adec5-184">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-184">Example</span></span>

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="adec5-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-185">See Also</span></span>

- <span data-ttu-id="adec5-186">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-186">lx_nand_flash_close</span></span>
- <span data-ttu-id="adec5-187">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-187">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="adec5-188">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-188">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="adec5-189">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-189">lx_nand_flash_open</span></span>
- <span data-ttu-id="adec5-190">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-190">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="adec5-191">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-191">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="adec5-192">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-192">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="adec5-193">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-193">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="adec5-194">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-194">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="adec5-195">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-195">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_initialize"></a><span data-ttu-id="adec5-196">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-196">lx_nand_flash_initialize</span></span>

<span data-ttu-id="adec5-197">Inicjowanie obsługi ni Flash</span><span class="sxs-lookup"><span data-stu-id="adec5-197">Initialize NAND flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-198">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-198">Prototype</span></span>

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="adec5-199">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-199">Description</span></span>

<span data-ttu-id="adec5-200">Ta usługa Inicjuje obsługę LevelX ni Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-200">This service initializes LevelX NAND flash support.</span></span> <span data-ttu-id="adec5-201">Musi być wywoływana przed innymi interfejsami API LevelX ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-201">It must be called before any other LevelX NAND APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-202">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-202">Input Parameters</span></span>

- <span data-ttu-id="adec5-203">**Brak**</span><span class="sxs-lookup"><span data-stu-id="adec5-203">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-204">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-204">Return Values</span></span>

- <span data-ttu-id="adec5-205">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="adec5-205">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="adec5-206">**LX_ERROR**: (0X01) błąd podczas inicjowania obsługi ni Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-206">**LX_ERROR**: (0x01) Error initializing NAND flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-207">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-207">Allowed From</span></span>

<span data-ttu-id="adec5-208">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="adec5-208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="adec5-209">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-209">Example</span></span>

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="adec5-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-210">See Also</span></span>

- <span data-ttu-id="adec5-211">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-211">lx_nand_flash_close</span></span>
- <span data-ttu-id="adec5-212">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-212">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="adec5-213">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-213">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="adec5-214">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-214">lx_nand_flash_open</span></span>
- <span data-ttu-id="adec5-215">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-215">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="adec5-216">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-216">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="adec5-217">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-217">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="adec5-218">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-218">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="adec5-219">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-219">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="adec5-220">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-220">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_open"></a><span data-ttu-id="adec5-221">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-221">lx_nand_flash_open</span></span>

<span data-ttu-id="adec5-222">Otwórz wystąpienie ni Flash</span><span class="sxs-lookup"><span data-stu-id="adec5-222">Open NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-223">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-223">Prototype</span></span>

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a><span data-ttu-id="adec5-224">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-224">Description</span></span>

<span data-ttu-id="adec5-225">Ta usługa otwiera wystąpienie ni Flash z określonym blokiem sterowania Flash ni i funkcją inicjowania sterownika.</span><span class="sxs-lookup"><span data-stu-id="adec5-225">This service opens a NAND flash instance with the specified NAND flash control block and driver initialization function.</span></span> <span data-ttu-id="adec5-226">Należy pamiętać, że funkcja inicjowania sterownika jest odpowiedzialna za Instalowanie różnych wskaźników funkcji do odczytu, zapisu i wymazywania bloków/stron sprzętu ni skojarzonego z tym wystąpieniem programu ni Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-226">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks/pages of the NAND hardware associated with this NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-227">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-227">Input Parameters</span></span>

- <span data-ttu-id="adec5-228">**nand_flash**: wskaźnik wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-228">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="adec5-229">**name**: nazwa wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-229">**name**: Name of NAND flash instance.</span></span>
- <span data-ttu-id="adec5-230">**nand_driver_initialize**: wskaźnik funkcji do funkcji inicjowania sterownika Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-230">**nand_driver_initialize**: Function pointer to NAND flash driver initialization function.</span></span> <span data-ttu-id="adec5-231">Więcej informacji na temat obowiązków dotyczących sterownika ni można znaleźć w rozdziale 3 tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="adec5-231">Please refer to Chapter 3 of this guide for more details on NAND flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-232">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-232">Return Values</span></span>

- <span data-ttu-id="adec5-233">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="adec5-233">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="adec5-234">**LX_ERROR**: (0X01) wystąpił błąd podczas otwierania wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-234">**LX_ERROR**: (0x01) Error opening NAND flash instance.</span></span>
- <span data-ttu-id="adec5-235">**LX_NO_MEMORY**: (0X08) sterownik nie dostarczył buforu do odczytu jednej strony do pamięci RAM.</span><span class="sxs-lookup"><span data-stu-id="adec5-235">**LX_NO_MEMORY**: (0x08) Driver did not provide buffer for reading one page into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-236">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-236">Allowed From</span></span>

<span data-ttu-id="adec5-237">Wątki</span><span class="sxs-lookup"><span data-stu-id="adec5-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="adec5-238">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-238">Example</span></span>

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="adec5-239">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-239">See Also</span></span>

- <span data-ttu-id="adec5-240">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-240">lx_nand_flash_close</span></span>
- <span data-ttu-id="adec5-241">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-241">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="adec5-242">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-242">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="adec5-243">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-243">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="adec5-244">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-244">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="adec5-245">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-245">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="adec5-246">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-246">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="adec5-247">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-247">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="adec5-248">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-248">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="adec5-249">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-249">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_check"></a><span data-ttu-id="adec5-250">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-250">lx_nand_flash_page_ecc_check</span></span>

<span data-ttu-id="adec5-251">Sprawdź, czy na stronie błędów ECC zostały skorygowane</span><span class="sxs-lookup"><span data-stu-id="adec5-251">Check page for ECC errors with correction</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-252">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-252">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="adec5-253">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-253">Description</span></span>

<span data-ttu-id="adec5-254">Ta usługa weryfikuje integralność podanego buforu stronicowania ni przy użyciu dostarczonej ECC.</span><span class="sxs-lookup"><span data-stu-id="adec5-254">This service verifies the integrity of the supplied NAND page buffer with the supplied ECC.</span></span> <span data-ttu-id="adec5-255">Rozmiar strony (zdefiniowany w wskaźniku wystąpienia Flash ni) zakłada się, że jest wielokrotnością 256-bajtów, a dostarczony kod ECC jest w stanie skorygować 1 bit błędu w każdej części 256-bajtowej strony.</span><span class="sxs-lookup"><span data-stu-id="adec5-255">Page size (defined in the NAND flash instance pointer) is assumed to be a multiple of 256-bytes and the ECC code supplied is capable of correcting a 1 bit error in each 256-byte portion of the page.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-256">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-256">Input Parameters</span></span>

- <span data-ttu-id="adec5-257">**nand_flash**: wskaźnik wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-257">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="adec5-258">**page_buffer**: wskaźnik do niego buforu strony Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-258">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="adec5-259">**ecc_buffer**: wskaźnik do strony ni na potrzeby technologii ECC.</span><span class="sxs-lookup"><span data-stu-id="adec5-259">**ecc_buffer**: Pointer to ECC for NAND flash page.</span></span> <span data-ttu-id="adec5-260">Należy zauważyć, że liczba bajtów ECC na 256 część strony wynosi 3.</span><span class="sxs-lookup"><span data-stu-id="adec5-260">Note that there are 3 ECC bytes per 256-byte portion of the page.</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-261">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-261">Return Values</span></span>

- <span data-ttu-id="adec5-262">**LX_SUCCESS**: (0x00) Strona ni nie ma błędów.</span><span class="sxs-lookup"><span data-stu-id="adec5-262">**LX_SUCCESS**: (0x00) NAND page has no errors.</span></span>
- <span data-ttu-id="adec5-263">**LX_NAND_ERROR_CORRECTED**: (0X06) co najmniej jeden błąd 1-bitowy został poprawiony na stronie ni — poprawki są w buforze strony.</span><span class="sxs-lookup"><span data-stu-id="adec5-263">**LX_NAND_ERROR_CORRECTED**: (0x06) One or more 1-bit errors were corrected in the NAND page—correction(s) are in the page buffer.</span></span>
- <span data-ttu-id="adec5-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0X07) zbyt wiele błędów do poprawienia na stronie ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Too many errors to correct on the NAND page.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-265">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-265">Allowed From</span></span>

<span data-ttu-id="adec5-266">Sterownik LevelX</span><span class="sxs-lookup"><span data-stu-id="adec5-266">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="adec5-267">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-267">Example</span></span>

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a><span data-ttu-id="adec5-268">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-268">See Also</span></span>

- <span data-ttu-id="adec5-269">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-269">lx_nand_flash_close</span></span>
- <span data-ttu-id="adec5-270">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-270">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="adec5-271">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-271">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="adec5-272">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-272">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="adec5-273">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-273">lx_nand_flash_open</span></span>
- <span data-ttu-id="adec5-274">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-274">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="adec5-275">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-275">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="adec5-276">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-276">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="adec5-277">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-277">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="adec5-278">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-278">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_compute"></a><span data-ttu-id="adec5-279">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-279">lx_nand_flash_page_ecc_compute</span></span>

<span data-ttu-id="adec5-280">Obliczenia ECC dla strony</span><span class="sxs-lookup"><span data-stu-id="adec5-280">Compute ECC for page</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-281">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-281">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="adec5-282">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-282">Description</span></span>

<span data-ttu-id="adec5-283">Ta usługa oblicza wartość ECC dostarczonego buforu stronicowania ni i zwraca wartość ECC w dostarczonym buforze ECC.</span><span class="sxs-lookup"><span data-stu-id="adec5-283">This service computes the ECC of the supplied NAND page buffer and returns the ECC in the supplied ECC buffer.</span></span> <span data-ttu-id="adec5-284">Przyjmuje się, że rozmiar strony jest wielokrotnością 256-bajtów (zdefiniowaną w wskaźniku wystąpienia ni Flash).</span><span class="sxs-lookup"><span data-stu-id="adec5-284">Page size is assume to be a multiple of 256-bytes (defined in the NAND flash instance pointer).</span></span> <span data-ttu-id="adec5-285">Kod ECC służy do weryfikowania integralności strony, gdy jest odczytywana w późniejszym czasie.</span><span class="sxs-lookup"><span data-stu-id="adec5-285">The ECC code is used to verify the integrity of the page when it is read at a later time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-286">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-286">Input Parameters</span></span>

- <span data-ttu-id="adec5-287">**nand_flash**: wskaźnik wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-287">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="adec5-288">**page_buffer**: wskaźnik do niego buforu strony Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-288">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="adec5-289">**ecc_buffer**: wskaźnik do miejsca docelowego dla ECC na stronie ni Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-289">**ecc_buffer**: Pointer to destination for ECC of the NAND flash page.</span></span> <span data-ttu-id="adec5-290">Należy pamiętać, że musi to być 3 bajty magazynu ECC na 256-bajtowej części strony.</span><span class="sxs-lookup"><span data-stu-id="adec5-290">Note that must be 3 bytes of ECC storage per 256-byte portion of the page.</span></span> <span data-ttu-id="adec5-291">Na przykład strona 2048 bajtów będzie wymagała 24 bajtów dla ECC.</span><span class="sxs-lookup"><span data-stu-id="adec5-291">For example, a 2048 byte page would require 24 bytes for the ECC.</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-292">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-292">Return Values</span></span>

- <span data-ttu-id="adec5-293">**LX_SUCCESS**: (0x00) pomyślnie obliczono ECC.</span><span class="sxs-lookup"><span data-stu-id="adec5-293">**LX_SUCCESS**: (0x00) ECC successfully calculated.</span></span>
- <span data-ttu-id="adec5-294">**LX_ERROR**: (0X01) błąd podczas obliczania ECC.</span><span class="sxs-lookup"><span data-stu-id="adec5-294">**LX_ERROR**: (0x01) Error calculating ECC.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-295">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-295">Allowed From</span></span>

<span data-ttu-id="adec5-296">Sterownik LevelX</span><span class="sxs-lookup"><span data-stu-id="adec5-296">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="adec5-297">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-297">Example</span></span>

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a><span data-ttu-id="adec5-298">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-298">See Also</span></span>

- <span data-ttu-id="adec5-299">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-299">lx_nand_flash_close</span></span>
- <span data-ttu-id="adec5-300">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-300">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="adec5-301">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-301">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="adec5-302">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-302">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="adec5-303">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-303">lx_nand_flash_open</span></span>
- <span data-ttu-id="adec5-304">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-304">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="adec5-305">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-305">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="adec5-306">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-306">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="adec5-307">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-307">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="adec5-308">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-308">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_partial_defragment"></a><span data-ttu-id="adec5-309">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-309">lx_nand_flash_partial_defragment</span></span>

<span data-ttu-id="adec5-310">Częściowa defragmentacja wystąpienia programu ni Flash</span><span class="sxs-lookup"><span data-stu-id="adec5-310">Partial defragment of NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-311">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-311">Prototype</span></span>

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="adec5-312">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-312">Description</span></span>

<span data-ttu-id="adec5-313">Ta usługa defragmentuje poprzednio otwarte wystąpienie ni Flash do maksymalnej liczby określonych bloków.</span><span class="sxs-lookup"><span data-stu-id="adec5-313">This service defragments the previously opened NAND flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="adec5-314">Proces defragmentacji maksymalizuje liczbę bezpłatnych stron i bloków.</span><span class="sxs-lookup"><span data-stu-id="adec5-314">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-315">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-315">Input Parameters</span></span>

- <span data-ttu-id="adec5-316">**nand_flash**: wskaźnik wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-316">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="adec5-317">**max_blocks**: Maksymalna liczba bloków.</span><span class="sxs-lookup"><span data-stu-id="adec5-317">**max_blocks**: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-318">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-318">Return Values</span></span>

- <span data-ttu-id="adec5-319">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="adec5-319">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="adec5-320">**LX_ERROR**: (0X01) błąd podczas defragmentowania wystąpienia Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-320">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-321">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-321">Allowed From</span></span>

<span data-ttu-id="adec5-322">Wątki</span><span class="sxs-lookup"><span data-stu-id="adec5-322">Threads</span></span>

### <a name="example"></a><span data-ttu-id="adec5-323">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-323">Example</span></span>

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="adec5-324">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-324">See Also</span></span>

- <span data-ttu-id="adec5-325">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-325">lx_nand_flash_close</span></span>
- <span data-ttu-id="adec5-326">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-326">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="adec5-327">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-327">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="adec5-328">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-328">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="adec5-329">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-329">lx_nand_flash_open</span></span>
- <span data-ttu-id="adec5-330">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-330">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="adec5-331">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-331">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="adec5-332">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-332">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="adec5-333">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-333">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="adec5-334">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-334">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_read"></a><span data-ttu-id="adec5-335">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-335">lx_nand_flash_sector_read</span></span>

<span data-ttu-id="adec5-336">Odczytaj NIy sektor Flash</span><span class="sxs-lookup"><span data-stu-id="adec5-336">Read NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-337">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-337">Prototype</span></span>

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="adec5-338">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-338">Description</span></span>

<span data-ttu-id="adec5-339">Ta usługa odczytuje sektor logiczny z wystąpienia ni Flash i jeśli pomyślnie zwróci zawartość w podanym buforze.</span><span class="sxs-lookup"><span data-stu-id="adec5-339">This service reads the logical sector from the NAND flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="adec5-340">Należy pamiętać, że rozmiar sektora ni jest zawsze rozmiarem strony podstawowego sprzętu ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-340">Note that NAND sector size is always the page size of the underlying NAND hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-341">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-341">Input Parameters</span></span>

- <span data-ttu-id="adec5-342">**nand_flash**: wskaźnik wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-342">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="adec5-343">**logical_sector**: sektor logiczny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="adec5-343">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="adec5-344">**bufor**: wskaźnik do miejsca docelowego dla zawartości sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="adec5-344">**buffer**: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="adec5-345">Należy pamiętać, że bufor jest przyjmowana jako rozmiar rozmiaru strony ni Flash i wyrównany do ULONG Access.</span><span class="sxs-lookup"><span data-stu-id="adec5-345">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-346">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-346">Return Values</span></span>

- <span data-ttu-id="adec5-347">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="adec5-347">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="adec5-348">**LX_ERROR**: (0X01) błąd podczas odczytywania sektora Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-348">**LX_ERROR**: (0x01) Error reading NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-349">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-349">Allowed From</span></span>

<span data-ttu-id="adec5-350">Wątki</span><span class="sxs-lookup"><span data-stu-id="adec5-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="adec5-351">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-351">Example</span></span>

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="adec5-352">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-352">See Also</span></span>

- <span data-ttu-id="adec5-353">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-353">lx_nand_flash_close</span></span>
- <span data-ttu-id="adec5-354">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-354">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="adec5-355">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-355">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="adec5-356">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-356">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="adec5-357">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-357">lx_nand_flash_open</span></span>
- <span data-ttu-id="adec5-358">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-358">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="adec5-359">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-359">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="adec5-360">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-360">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="adec5-361">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-361">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="adec5-362">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-362">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_release"></a><span data-ttu-id="adec5-363">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-363">lx_nand_flash_sector_release</span></span>

<span data-ttu-id="adec5-364">NI wersja sektora Flash</span><span class="sxs-lookup"><span data-stu-id="adec5-364">Release NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-365">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-365">Prototype</span></span>

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="adec5-366">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-366">Description</span></span>

<span data-ttu-id="adec5-367">Ta usługa zwalnia mapowanie sektora logicznego w wystąpieniu Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-367">This service releases the logical sector mapping in the NAND flash instance.</span></span> <span data-ttu-id="adec5-368">Zwolnienie sektora logicznego, gdy nie jest używany, sprawia, że LevelX zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="adec5-368">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-369">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-369">Input Parameters</span></span>

- <span data-ttu-id="adec5-370">**nand_flash**: wskaźnik wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-370">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="adec5-371">**logical_sector**: sektor logiczny do wydania.</span><span class="sxs-lookup"><span data-stu-id="adec5-371">**logical_sector**: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-372">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-372">Return Values</span></span>

- <span data-ttu-id="adec5-373">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="adec5-373">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="adec5-374">**LX_ERROR**: (0X01) błąd ni sektora Flash.</span><span class="sxs-lookup"><span data-stu-id="adec5-374">**LX_ERROR**: (0x01) Error NAND flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-375">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-375">Allowed From</span></span>

<span data-ttu-id="adec5-376">Wątki</span><span class="sxs-lookup"><span data-stu-id="adec5-376">Threads</span></span>

### <a name="example"></a><span data-ttu-id="adec5-377">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-377">Example</span></span>

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="adec5-378">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-378">See Also</span></span>

- <span data-ttu-id="adec5-379">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-379">lx_nand_flash_close</span></span>
- <span data-ttu-id="adec5-380">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-380">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="adec5-381">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-381">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="adec5-382">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-382">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="adec5-383">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-383">lx_nand_flash_open</span></span>
- <span data-ttu-id="adec5-384">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-384">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="adec5-385">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-385">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="adec5-386">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-386">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="adec5-387">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-387">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="adec5-388">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-388">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_write"></a><span data-ttu-id="adec5-389">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="adec5-389">lx_nand_flash_sector_write</span></span>

<span data-ttu-id="adec5-390">Pisanie sektora Flash ni</span><span class="sxs-lookup"><span data-stu-id="adec5-390">Write NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="adec5-391">Prototype</span><span class="sxs-lookup"><span data-stu-id="adec5-391">Prototype</span></span>

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="adec5-392">Opis</span><span class="sxs-lookup"><span data-stu-id="adec5-392">Description</span></span>

<span data-ttu-id="adec5-393">Ta usługa Zapisuje określony sektor logiczny w wystąpieniu Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-393">This service writes the specified logical sector in the NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="adec5-394">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="adec5-394">Input Parameters</span></span>

- <span data-ttu-id="adec5-395">**nand_flash**: wskaźnik wystąpienia Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-395">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="adec5-396">**logical_sector**: sektor logiczny do zapisu.</span><span class="sxs-lookup"><span data-stu-id="adec5-396">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="adec5-397">**bufor**: wskaźnik do zawartości sektora logicznego.</span><span class="sxs-lookup"><span data-stu-id="adec5-397">**buffer**: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="adec5-398">Należy pamiętać, że bufor jest przyjmowana jako rozmiar rozmiaru strony ni Flash i wyrównany do ULONG Access.</span><span class="sxs-lookup"><span data-stu-id="adec5-398">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="adec5-399">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="adec5-399">Return Values</span></span>

- <span data-ttu-id="adec5-400">**LX_SUCCESS**: (0X00) pomyślne żądanie.</span><span class="sxs-lookup"><span data-stu-id="adec5-400">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="adec5-401">**LX_NO_SECTORS**: (0X02) nie ma więcej dostępnych wolnych sektorów do przeprowadzenia zapisu.</span><span class="sxs-lookup"><span data-stu-id="adec5-401">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="adec5-402">**LX_ERROR**: (0X01) błąd podczas zwalniania sektora Flash ni.</span><span class="sxs-lookup"><span data-stu-id="adec5-402">**LX_ERROR**: (0x01) Error releasing NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="adec5-403">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="adec5-403">Allowed From</span></span>

<span data-ttu-id="adec5-404">Wątki</span><span class="sxs-lookup"><span data-stu-id="adec5-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="adec5-405">Przykład</span><span class="sxs-lookup"><span data-stu-id="adec5-405">Example</span></span>

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="adec5-406">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="adec5-406">See Also</span></span>

- <span data-ttu-id="adec5-407">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="adec5-407">lx_nand_flash_close</span></span>
- <span data-ttu-id="adec5-408">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-408">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="adec5-409">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="adec5-409">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="adec5-410">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="adec5-410">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="adec5-411">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="adec5-411">lx_nand_flash_open</span></span>
- <span data-ttu-id="adec5-412">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="adec5-412">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="adec5-413">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="adec5-413">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="adec5-414">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="adec5-414">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="adec5-415">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="adec5-415">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="adec5-416">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="adec5-416">lx_nand_flash_sector_release</span></span>
