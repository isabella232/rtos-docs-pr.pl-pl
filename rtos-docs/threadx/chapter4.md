---
title: Rozdział 4 — Opis usług Azure RTO ThreadX Services
description: Ten rozdział zawiera opis wszystkich usług Azure RTO ThreadX w porządku alfabetycznym.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 60ecc96df07b1f77b9b448814c4420133f3e2afc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821361"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a><span data-ttu-id="f9121-103">Rozdział 4 — Opis usług Azure RTO ThreadX Services</span><span class="sxs-lookup"><span data-stu-id="f9121-103">Chapter 4 - Description of Azure RTOS ThreadX Services</span></span>

<span data-ttu-id="f9121-104">Ten rozdział zawiera opis wszystkich usług Azure RTO ThreadX w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="f9121-104">This chapter contains a description of all Azure RTOS ThreadX services in alphabetic order.</span></span> <span data-ttu-id="f9121-105">Ich nazwy są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem.</span><span class="sxs-lookup"><span data-stu-id="f9121-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="f9121-106">W sekcji "wartości zwracane" w następujących opisach wartości **pogrubienia** nie mają wpływać na **TX_DISABLE_ERROR_CHECKING** Definiowanie używane do wyłączania sprawdzania błędów interfejsu API; podczas gdy wartości wyświetlane w trybie niepogrubionym są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f9121-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="f9121-107">Ponadto słowo "**Yes**" wymienione w nagłówku "**możliwe** przeprowadzenie" wskazuje, że wywołanie usługi może wznowić wątek o wyższym priorytecie, w rezultacie przeszedł wątek wywołujący.</span><span class="sxs-lookup"><span data-stu-id="f9121-107">In addition, a "**Yes**" listed under the "**Preemption Possible**" heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="f9121-108">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-108">tx_block_allocate</span></span>

<span data-ttu-id="f9121-109">Przydzielanie bloku o ustalonym rozmiarze pamięci</span><span class="sxs-lookup"><span data-stu-id="f9121-109">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-110">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-110">Prototype</span></span>

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f9121-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-111">Description</span></span>

<span data-ttu-id="f9121-112">Ta usługa przydziela blok pamięci o stałym rozmiarze z określonej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-112">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="f9121-113">Rzeczywisty rozmiar bloku pamięci jest określany podczas tworzenia puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-113">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-114">*Ważne jest, aby upewnić się, że kod aplikacji nie zapisuje poza przydzielonym blokiem pamięci. W takim przypadku uszkodzenie występuje w sąsiednim (zazwyczaj kolejnym) bloku pamięci. Wyniki są nieprzewidywalne i często krytyczne!*</span><span class="sxs-lookup"><span data-stu-id="f9121-114">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-115">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-115">Parameters</span></span>

- <span data-ttu-id="f9121-116">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-116">**pool_ptr**</span></span> <br><span data-ttu-id="f9121-117">Wskaźnik do wcześniej utworzonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-117">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="f9121-118">**block_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-118">**block_ptr**</span></span> <br><span data-ttu-id="f9121-119">Wskaźnik do docelowego wskaźnika bloku.</span><span class="sxs-lookup"><span data-stu-id="f9121-119">Pointer to a destination block pointer.</span></span> <span data-ttu-id="f9121-120">Po pomyślnym przydzieleniu adres przydzielonego bloku pamięci jest umieszczany w miejscu, w którym wskazuje ten parametr.</span><span class="sxs-lookup"><span data-stu-id="f9121-120">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="f9121-121">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="f9121-121">**wait_option**</span></span> <br><span data-ttu-id="f9121-122">Definiuje, w jaki sposób działa usługa, jeśli nie ma dostępnych bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-122">Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="f9121-123">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9121-123">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="f9121-124">**TX_NO_WAIT** (0x00000000) — wybranie **TX_NO_WAIT** powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się pomyślnie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="f9121-124">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="f9121-125">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niebędącego wątkiem, np. inicjalizacji, czasomierza lub ISR*.</span><span class="sxs-lookup"><span data-stu-id="f9121-125">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="f9121-126">**TX_WAIT_FOREVER** (0xFFFFFFF) — wybranie **TX_WAIT_FOREVER** powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu udostępnienia bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-126">**TX_WAIT_FOREVER** (0xFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until a memory block is available.</span></span>
  - <span data-ttu-id="f9121-127">*wartość limitu czasu* (0X00000001 przez 0xFFFFFFFE) — wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na blok pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-127">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-128">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-128">Return Values</span></span>

- <span data-ttu-id="f9121-129">**TX_SUCCESS**    (0x00) pomyślna alokacja bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-129">**TX_SUCCESS**    (0x00)  Successful memory block allocation.</span></span>
- <span data-ttu-id="f9121-130">Pula bloków pamięci **TX_DELETED** (0x01) została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-130">**TX_DELETED**    (0x01)  Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="f9121-131">Usługa **TX_NO_MEMORY** (0x10) nie może przydzielić bloku pamięci w określonym czasie, aby oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="f9121-131">**TX_NO_MEMORY**  (0x10)  Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="f9121-132">Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, CZASOMIERZ lub ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-132">**TX_WAIT_ABORTED**   (0x1A)  Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="f9121-133">**TX_POOL_ERROR** (0X02) Nieprawidłowy wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-133">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="f9121-134">**TX_WAIT_ERROR** (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-134">**TX_WAIT_ERROR** (0x04)  A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="f9121-135">**TX_PTR_ERROR**  (0X03) Nieprawidłowy wskaźnik do wskaźnika docelowego.</span><span class="sxs-lookup"><span data-stu-id="f9121-135">**TX_PTR_ERROR**  (0x03)  Invalid pointer to destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-136">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-136">Allowed From</span></span>

<span data-ttu-id="f9121-137">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-137">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-138">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-138">Preemption Possible</span></span>

<span data-ttu-id="f9121-139">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-140">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-140">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;

UINT status;

/* Allocate a memory block from my_pool. Assume that the pool has
already been created with a call to tx_block_pool_create. */

status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
  TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the address of
the allocated block of memory. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-141">See Also</span></span>

- <span data-ttu-id="f9121-142">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-142">tx_block_pool_create</span></span>
- <span data-ttu-id="f9121-143">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-143">tx_block_pool_delete</span></span>
- <span data-ttu-id="f9121-144">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-144">tx_block_pool_info_get</span></span>
- <span data-ttu-id="f9121-145">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-145">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-146">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-146">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-147">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-147">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="f9121-148">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="f9121-148">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="f9121-149">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-149">tx_block_pool_create</span></span>

<span data-ttu-id="f9121-150">Utwórz pulę bloków pamięci o stałym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="f9121-150">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-151">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-151">Prototype</span></span>

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="f9121-152">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-152">Description</span></span>

<span data-ttu-id="f9121-153">Ta usługa tworzy pulę bloków pamięci o stałym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="f9121-153">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="f9121-154">Określony obszar pamięci jest podzielony na tyle bloków pamięci o stałym rozmiarze, jak to możliwe, przy użyciu formuły:</span><span class="sxs-lookup"><span data-stu-id="f9121-154">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>

<span data-ttu-id="f9121-155">**łączna liczba bloków** = (**całkowita liczba bajtów**)/(**rozmiar bloku** + sizeof (void \*))</span><span class="sxs-lookup"><span data-stu-id="f9121-155">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!NOTE]
><span data-ttu-id="f9121-156">\* Każdy blok pamięci zawiera jeden wskaźnik obciążenia, który jest niewidoczny dla użytkownika i jest reprezentowany przez "sizeof (void *)" w poprzedniej formule.*</span><span class="sxs-lookup"><span data-stu-id="f9121-156">\*Each memory block contains one pointer of overhead that is invisible to the user and is represented by the "sizeof(void *)" in the preceding formula.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-157">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-157">Parameters</span></span>

- <span data-ttu-id="f9121-158">**pool_ptr**  Wskaźnik do bloku sterowania puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-158">**pool_ptr**  Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="f9121-159">**name_ptr**  Wskaźnik na nazwę puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-159">**name_ptr**  Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="f9121-160">**block_size**    Liczba bajtów w każdym bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-160">**block_size**    Number of bytes in each memory block.</span></span>
- <span data-ttu-id="f9121-161">**pool_start**    Adres początkowy puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-161">**pool_start**    Starting address of the memory block pool.</span></span> <span data-ttu-id="f9121-162">Adres początkowy musi być wyrównany do rozmiaru typu danych ULONG.</span><span class="sxs-lookup"><span data-stu-id="f9121-162">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="f9121-163">**pool_size** Łączna liczba bajtów dostępnych dla puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-163">**pool_size** Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-164">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-164">Return Values</span></span>

- <span data-ttu-id="f9121-165">**TX_SUCCESS**    (0X00) pomyślne utworzenie puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-165">**TX_SUCCESS**    (0x00)  Successful memory block pool creation.</span></span>
- <span data-ttu-id="f9121-166">**TX_POOL_ERROR** (0X02) Nieprawidłowy wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-166">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span> <span data-ttu-id="f9121-167">Wskaźnik ma wartość NULL lub pula została już utworzona.</span><span class="sxs-lookup"><span data-stu-id="f9121-167">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="f9121-168">**TX_PTR_ERROR**  (0X03) nieprawidłowy adres początkowy puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-168">**TX_PTR_ERROR**  (0x03)  Invalid starting address of the pool.</span></span>
- <span data-ttu-id="f9121-169">**TX_CALLER_ERROR**   (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-169">**TX_CALLER_ERROR**   (0x13)  Invalid caller of this service.</span></span>
- <span data-ttu-id="f9121-170">Rozmiar **TX_SIZE_ERROR** (0x05) puli jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f9121-170">**TX_SIZE_ERROR** (0x05)  Size of pool is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-171">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-171">Allowed From</span></span>

<span data-ttu-id="f9121-172">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-172">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-173">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-173">Preemption Possible</span></span>

<span data-ttu-id="f9121-174">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-174">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-175">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-175">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT status;

/* Create a memory pool whose total size is 1000 bytes starting at
address 0x100000. Each block in this pool is defined to be 50 bytes
long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
  50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18 memory blocks
of 50 bytes each. The reason there are not 20 blocks in the pool is
because of the one overhead pointer associated with each block. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-176">See Also</span></span>

- <span data-ttu-id="f9121-177">tx_block_allocate, tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-177">tx_block_allocate, tx_block_pool_delete</span></span>
- <span data-ttu-id="f9121-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-179">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-179">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-180">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="f9121-180">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="f9121-181">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-181">tx_block_pool_delete</span></span>

<span data-ttu-id="f9121-182">Usuń pulę bloków pamięci</span><span class="sxs-lookup"><span data-stu-id="f9121-182">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-183">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-183">Prototype</span></span>

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-184">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-184">Description</span></span>

<span data-ttu-id="f9121-185">Ta usługa usuwa określoną pulę bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-185">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="f9121-186">Wszystkie wątki zawieszają się, czekając na wznowienie bloku pamięci z tej puli i z uwzględnieniem **TX_DELETED** stanu powrotu.</span><span class="sxs-lookup"><span data-stu-id="f9121-186">All threads suspended waiting for a memory block from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-187">*Jest on odpowiedzialny za zarządzanie obszarem pamięci skojarzonym z pulą, która jest dostępna po zakończeniu tej usługi. Ponadto aplikacja musi uniemożliwić korzystanie z usuniętej puli lub jej poprzednich bloków pamięci.*</span><span class="sxs-lookup"><span data-stu-id="f9121-187">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or its former memory blocks.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-188">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-188">Parameters</span></span>

- <span data-ttu-id="f9121-189">**pool_ptr** Wskaźnik do wcześniej utworzonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-189">**pool_ptr** Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-190">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-190">Return Values</span></span>

- <span data-ttu-id="f9121-191">**TX_SUCCESS** (0X00) pomyślne usunięcie puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-191">**TX_SUCCESS** (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="f9121-192">**TX_POOL_ERROR** (0X02) Nieprawidłowy wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-192">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="f9121-193">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-193">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-194">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-194">Allowed From</span></span>

<span data-ttu-id="f9121-195">Wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-195">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-196">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-196">Preemption Possible</span></span>

<span data-ttu-id="f9121-197">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-197">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-198">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-198">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a><span data-ttu-id="f9121-199">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-199">See Also</span></span>

- <span data-ttu-id="f9121-200">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-200">tx_block_allocate</span></span>
- <span data-ttu-id="f9121-201">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-201">tx_block_pool_create</span></span>
- <span data-ttu-id="f9121-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-203">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-203">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-204">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="f9121-204">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="f9121-205">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-205">tx_block_pool_info_get</span></span>

<span data-ttu-id="f9121-206">Pobierz informacje o puli blokowej</span><span class="sxs-lookup"><span data-stu-id="f9121-206">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-207">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-207">Prototype</span></span>

```c
UINT tx_block_pool_info_get(
    TX_BLOCK_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *total_blocks,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BLOCK_POOL **next_pool);
```

### <a name="description"></a><span data-ttu-id="f9121-208">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-208">Description</span></span>

<span data-ttu-id="f9121-209">Ta usługa pobiera informacje o określonej puli pamięci blokowej.</span><span class="sxs-lookup"><span data-stu-id="f9121-209">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-210">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-210">Parameters</span></span>

- <span data-ttu-id="f9121-211">**pool_ptr**  Wskaźnik do wcześniej utworzonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-211">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="f9121-212">**Nazwa**  Wskaźnik do miejsca docelowego dla wskaźnika do nazwy puli bloku.</span><span class="sxs-lookup"><span data-stu-id="f9121-212">**name**  Pointer to destination for the pointer to the block pool's name.</span></span>
- <span data-ttu-id="f9121-213">**dostępne** Wskaźnik do miejsca docelowego dla liczby dostępnych bloków w puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="f9121-213">**available** Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="f9121-214">**total_blocks**  Wskaźnik do miejsca docelowego dla łącznej liczby bloków w puli bloków.</span><span class="sxs-lookup"><span data-stu-id="f9121-214">**total_blocks**  Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="f9121-215">**first_suspended**   Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tej puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="f9121-215">**first_suspended**   Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="f9121-216">**suspended_count**   Wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="f9121-216">**suspended_count**   Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="f9121-217">**next_pool** Wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej puli blokowej.</span><span class="sxs-lookup"><span data-stu-id="f9121-217">**next_pool** Pointer to destination for the pointer of the next created block pool.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-218">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-218">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-219">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-219">Return Values</span></span>

- <span data-ttu-id="f9121-220">**TX_SUCCESS** (0X00) pomyślne pobranie informacji o puli blokad.</span><span class="sxs-lookup"><span data-stu-id="f9121-220">**TX_SUCCESS** (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="f9121-221">**TX_POOL_ERROR** (0X02) Nieprawidłowy wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-221">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-222">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-222">Allowed From</span></span>

<span data-ttu-id="f9121-223">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-223">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-224">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-224">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
CHAR *name;
ULONG available;
ULONG total_blocks;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BLOCK_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
  &available,&total_blocks,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-225">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-225">See Also</span></span>

- <span data-ttu-id="f9121-226">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-226">tx_block_allocate</span></span>
- <span data-ttu-id="f9121-227">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-227">tx_block_pool_create</span></span>
- <span data-ttu-id="f9121-228">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-228">tx_block_pool_delete</span></span>
- <span data-ttu-id="f9121-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-230">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-230">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-231">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="f9121-231">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="f9121-232">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-232">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="f9121-233">Uzyskaj informacje o wydajności puli bloku</span><span class="sxs-lookup"><span data-stu-id="f9121-233">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-234">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-234">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="f9121-235">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-235">Description</span></span>

<span data-ttu-id="f9121-236">Ta usługa pobiera informacje o wydajności dotyczące określonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-236">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-237">Aby można było zwracać informacje o wydajności *, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *zdefiniowanej dla tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="f9121-237">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-238">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-238">Parameters</span></span>

- <span data-ttu-id="f9121-239">**pool_ptr**  Wskaźnik do wcześniej utworzonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-239">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="f9121-240">**alokuje** Wskaźnik do miejsca docelowego dla liczby żądań alokacji wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-240">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="f9121-241">**wersje**  Wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-241">**releases**  Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="f9121-242">**zawieszenie**   Wskaźnik do miejsca docelowego dla liczby zawieszeń alokacji wątku w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-242">**suspensions**   Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="f9121-243">**limity czasu**  Wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia przydziału w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-243">**timeouts**  Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

>[!NOTE]
> <span data-ttu-id="f9121-244">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-244">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-245">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-245">Return Values</span></span>

- <span data-ttu-id="f9121-246">**TX_SUCCESS**    (0X00) pomyślne uzyskanie wydajności puli blokowych.</span><span class="sxs-lookup"><span data-stu-id="f9121-246">**TX_SUCCESS**    (0x00)  Successful block pool performance get.</span></span>
- <span data-ttu-id="f9121-247">**TX_PTR_ERROR**  (0X03) Nieprawidłowy wskaźnik puli bloku.</span><span class="sxs-lookup"><span data-stu-id="f9121-247">**TX_PTR_ERROR**  (0x03)  Invalid block pool pointer.</span></span>
- <span data-ttu-id="f9121-248">**TX_FEATURE_NOT_ENABLED**    (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-248">**TX_FEATURE_NOT_ENABLED**    (0xFF)  The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-249">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-249">Allowed From</span></span>

<span data-ttu-id="f9121-250">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-250">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-251">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-251">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created block
pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
  &releases,
  &suspensions,
  &timeouts);

/* If status is TX_SUCCESS the performance information was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-252">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-252">See Also</span></span>

- <span data-ttu-id="f9121-253">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-253">tx_block_allocate</span></span>
- <span data-ttu-id="f9121-254">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-254">tx_block_pool_create</span></span>
- <span data-ttu-id="f9121-255">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-255">tx_block_pool_delete</span></span>
- <span data-ttu-id="f9121-256">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-256">tx_block_pool_info_get</span></span>
- <span data-ttu-id="f9121-257">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-257">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-258">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-258">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-259">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="f9121-259">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="f9121-260">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-260">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="f9121-261">Uzyskaj informacje o wydajności systemu puli blokowej</span><span class="sxs-lookup"><span data-stu-id="f9121-261">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-262">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-262">Prototype</span></span>

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="f9121-263">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-263">Description</span></span>

<span data-ttu-id="f9121-264">Ta usługa pobiera informacje o wydajności wszystkich pul bloków pamięci w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-264">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-265">Aby można było zwracać informacje o wydajności *, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *zdefiniowanej dla tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="f9121-265">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-266">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-266">Parameters</span></span>

- <span data-ttu-id="f9121-267">**alokuje** Wskaźnik do miejsca docelowego dla łącznej liczby żądań alokacji wykonanych dla wszystkich pul bloku.</span><span class="sxs-lookup"><span data-stu-id="f9121-267">**allocates** Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="f9121-268">**wersje**  Wskaźnik do miejsca docelowego dla łącznej liczby żądań zwolnienia wykonanych na wszystkich pulach bloku.</span><span class="sxs-lookup"><span data-stu-id="f9121-268">**releases**  Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="f9121-269">**zawieszenie**   Wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń alokacji wątku dla wszystkich pul bloków.</span><span class="sxs-lookup"><span data-stu-id="f9121-269">**suspensions**   Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="f9121-270">**limity czasu**  Wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia przydziału dla wszystkich pul bloku.</span><span class="sxs-lookup"><span data-stu-id="f9121-270">**timeouts**  Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-271">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-271">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-272">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-272">Return Values</span></span>

- <span data-ttu-id="f9121-273">**TX_SUCCESS** (0X00) pomyślne zablokowanie wydajności systemu puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-273">**TX_SUCCESS** (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="f9121-274">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-275">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-275">Allowed From</span></span>

<span data-ttu-id="f9121-276">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-277">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-277">Example</span></span>

```c
ULONG       allocates;
ULONG       releases;
ULONG       suspensions;
ULONG       timeouts;

/* Retrieve performance information on all the block pools in
the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
    &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-278">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-278">See Also</span></span>

- <span data-ttu-id="f9121-279">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-279">tx_block_allocate</span></span>
- <span data-ttu-id="f9121-280">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-280">tx_block_pool_create</span></span>
- <span data-ttu-id="f9121-281">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-281">tx_block_pool_delete</span></span>
- <span data-ttu-id="f9121-282">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-282">tx_block_pool_info_get</span></span>
- <span data-ttu-id="f9121-283">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-283">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-284">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-284">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="f9121-285">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="f9121-285">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="f9121-286">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-286">tx_block_pool_prioritize</span></span>

<span data-ttu-id="f9121-287">Ustawianie priorytetu listy zawieszania puli bloków</span><span class="sxs-lookup"><span data-stu-id="f9121-287">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-288">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-288">Prototype</span></span>

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-289">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-289">Description</span></span>

<span data-ttu-id="f9121-290">Ta usługa umieszcza wątek o najwyższym priorytecie dla bloku pamięci w tej puli na początku listy zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-290">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="f9121-291">Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="f9121-291">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-292">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-292">Parameters</span></span>

- <span data-ttu-id="f9121-293">**pool_ptr** Wskaźnik do bloku sterowania puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-293">**pool_ptr** Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-294">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-294">Return Values</span></span>

- <span data-ttu-id="f9121-295">**TX_SUCCESS** (0X00) pomyślnie priorytetyzacja puli zablokowanych bloków.</span><span class="sxs-lookup"><span data-stu-id="f9121-295">**TX_SUCCESS** (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="f9121-296">**TX_POOL_ERROR** (0X02) Nieprawidłowy wskaźnik puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-296">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-297">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-297">Allowed From</span></span>

<span data-ttu-id="f9121-298">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-298">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-299">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-299">Preemption Possible</span></span>

<span data-ttu-id="f9121-300">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-300">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-301">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-301">Example</span></span>
```c
TX_BLOCK_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_block_release call will wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-302">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-302">See Also</span></span>

- <span data-ttu-id="f9121-303">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-303">tx_block_allocate</span></span>
- <span data-ttu-id="f9121-304">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-304">tx_block_pool_create</span></span>
- <span data-ttu-id="f9121-305">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-305">tx_block_pool_delete</span></span>
- <span data-ttu-id="f9121-306">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-306">tx_block_pool_info_get</span></span>
- <span data-ttu-id="f9121-307">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-307">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-308">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-308">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-309">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="f9121-309">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="f9121-310">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="f9121-310">tx_block_release</span></span>

<span data-ttu-id="f9121-311">Zwolnij blok pamięci o stałym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="f9121-311">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-312">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-312">Prototype</span></span>

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a><span data-ttu-id="f9121-313">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-313">Description</span></span>

<span data-ttu-id="f9121-314">Ta usługa zwalnia wcześniej przydzieloną blokadę z powrotem do skojarzonej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-314">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="f9121-315">Jeśli istnieje co najmniej jeden wątek, który zawiesił oczekiwanie na bloki pamięci z tej puli, ten blok pamięci zostanie zawieszony i wznowiony.</span><span class="sxs-lookup"><span data-stu-id="f9121-315">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="f9121-316">*Aplikacja musi uniemożliwić korzystanie z obszaru blokowego pamięci po jego wydaniu z powrotem do puli.*</span><span class="sxs-lookup"><span data-stu-id="f9121-316">*The application must prevent using a memory block area after it has been released back to the pool.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-317">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-317">Parameters</span></span>

- <span data-ttu-id="f9121-318">**block_ptr** Wskaźnik do wcześniej przydzielony blok pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-318">**block_ptr** Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-319">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-319">Return Values</span></span>

- <span data-ttu-id="f9121-320">**TX_SUCCESS** (0X00) pomyślne wydanie bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-320">**TX_SUCCESS** (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="f9121-321">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik do bloku pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-321">**TX_PTR_ERROR** (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-322">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-322">Allowed From</span></span>

<span data-ttu-id="f9121-323">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-323">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-324">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-324">Preemption Possible</span></span>

<span data-ttu-id="f9121-325">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-325">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-326">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-326">Example</span></span>

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;
UINT status;

/* Release a memory block back to my_pool. Assume that the
pool has been created and the memory block has been
allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
to by memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-327">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-327">See Also</span></span>

- <span data-ttu-id="f9121-328">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-328">tx_block_allocate</span></span>
- <span data-ttu-id="f9121-329">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-329">tx_block_pool_create</span></span>
- <span data-ttu-id="f9121-330">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-330">tx_block_pool_delete</span></span>
- <span data-ttu-id="f9121-331">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-331">tx_block_pool_info_get</span></span>
- <span data-ttu-id="f9121-332">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-332">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-333">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-333">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-334">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-334">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="f9121-335">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-335">tx_byte_allocate</span></span>

<span data-ttu-id="f9121-336">Przydziel bajty pamięci</span><span class="sxs-lookup"><span data-stu-id="f9121-336">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-337">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-337">Prototype</span></span>

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f9121-338">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-338">Description</span></span>

<span data-ttu-id="f9121-339">Ta usługa przydziela określoną liczbę bajtów z określonej puli bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-339">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-340">*Ważne jest, aby upewnić się, że kod aplikacji nie zapisuje poza przydzielonym blokiem pamięci. W takim przypadku uszkodzenie występuje w sąsiednim (zazwyczaj kolejnym) bloku pamięci. Wyniki są nieprzewidywalne i często krytyczne!*</span><span class="sxs-lookup"><span data-stu-id="f9121-340">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-341">*Wydajność tej usługi jest funkcją rozmiaru bloku i ilością fragmentacji w puli. W związku z tym ta usługa nie powinna być używana w wątkach o krytycznym czasie wykonywania.*</span><span class="sxs-lookup"><span data-stu-id="f9121-341">*The performance of this service is a function of the block size and the amount of fragmentation in the pool. Hence, this service should not be used during time-critical threads of execution.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-342">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-342">Parameters</span></span>

- <span data-ttu-id="f9121-343">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-343">**pool_ptr**</span></span> <br><span data-ttu-id="f9121-344">Wskaźnik do wcześniej utworzonej puli bloków pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-344">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="f9121-345">**memory_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-345">**memory_ptr**</span></span> <br><span data-ttu-id="f9121-346">Wskaźnik na wskaźnik pamięci docelowej.</span><span class="sxs-lookup"><span data-stu-id="f9121-346">Pointer to a destination memory pointer.</span></span> <span data-ttu-id="f9121-347">Po pomyślnym przydzieleniu adres przydzielonego obszaru pamięci jest umieszczany w miejscu, do którego wskazuje ten parametr.</span><span class="sxs-lookup"><span data-stu-id="f9121-347">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="f9121-348">**memory_size**</span><span class="sxs-lookup"><span data-stu-id="f9121-348">**memory_size**</span></span> <br><span data-ttu-id="f9121-349">Liczba żądanych bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-349">Number of bytes requested.</span></span>
- <span data-ttu-id="f9121-350">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="f9121-350">**wait_option**</span></span> <br><span data-ttu-id="f9121-351">Definiuje, w jaki sposób działa usługa, jeśli nie jest dostępna wystarczająca ilość pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-351">Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="f9121-352">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9121-352">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="f9121-353">**TX_NO_WAIT** (0x00000000) — wybranie **TX_NO_WAIT** powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9121-353">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="f9121-354">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z inicjacji.*</span><span class="sxs-lookup"><span data-stu-id="f9121-354">*This is the only valid option if the service is called from initialization.*</span></span>
  - <span data-ttu-id="f9121-355">**TX_WAIT_FOREVER** 0xffffffff) — wybranie **TX_WAIT_FOREVER** powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu udostępnienia wystarczającej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-355">**TX_WAIT_FOREVER** 0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until enough memory is available.</span></span>
  - <span data-ttu-id="f9121-356">*wartość limitu czasu* (0X00000001 przez 0xFFFFFFFE) — wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na pamięć.</span><span class="sxs-lookup"><span data-stu-id="f9121-356">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-357">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-357">Return Values</span></span>

- <span data-ttu-id="f9121-358">Pomyślna alokacja pamięci **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-358">**TX_SUCCESS** (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="f9121-359">Pula pamięci **TX_DELETED** (0x01) została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-359">**TX_DELETED** (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="f9121-360">Usługa **TX_NO_MEMORY** (0x10) nie może przydzielić pamięci w określonym czasie, aby czekać.</span><span class="sxs-lookup"><span data-stu-id="f9121-360">**TX_NO_MEMORY** (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="f9121-361">Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-361">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="f9121-362">**TX_POOL_ERROR** (0X02) Nieprawidłowy wskaźnik puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-362">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="f9121-363">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik do wskaźnika docelowego.</span><span class="sxs-lookup"><span data-stu-id="f9121-363">**TX_PTR_ERROR** (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="f9121-364">Żądany rozmiar **TX_SIZE_ERROR** (0X05) jest równy zero lub większy niż Pula.</span><span class="sxs-lookup"><span data-stu-id="f9121-364">**TX_SIZE_ERROR** (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="f9121-365">**TX_WAIT_ERROR** (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-365">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="f9121-366">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-366">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-367">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-367">Allowed From</span></span>

<span data-ttu-id="f9121-368">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-368">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-369">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-369">Preemption Possible</span></span>

<span data-ttu-id="f9121-370">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-370">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-371">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-371">Example</span></span>
```c
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT status;
/* Allocate a 112 byte memory area from my_pool. Assume
that the pool has already been created with a call to
tx_byte_pool_create. */
status = tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
    112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
address of the allocated memory area. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-372">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-372">See Also</span></span>

- <span data-ttu-id="f9121-373">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-373">tx_byte_pool_create</span></span>
- <span data-ttu-id="f9121-374">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-374">tx_byte_pool_delete</span></span>
- <span data-ttu-id="f9121-375">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-375">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="f9121-376">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-376">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-377">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-377">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-378">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-378">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="f9121-379">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="f9121-379">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="f9121-380">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-380">tx_byte_pool_create</span></span>

<span data-ttu-id="f9121-381">Utwórz pulę pamięci bajtów</span><span class="sxs-lookup"><span data-stu-id="f9121-381">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-382">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-382">Prototype</span></span>

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="f9121-383">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-383">Description</span></span>

<span data-ttu-id="f9121-384">Ta usługa tworzy pulę bajtów pamięci w określonym obszarze.</span><span class="sxs-lookup"><span data-stu-id="f9121-384">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="f9121-385">Początkowo Pula składa się z zasadniczo jednego bardzo dużego bezpłatnego bloku.</span><span class="sxs-lookup"><span data-stu-id="f9121-385">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="f9121-386">Jednak Pula jest dzielona na mniejsze bloki w miarę dokonywania alokacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-386">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-387">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-387">Parameters</span></span>

- <span data-ttu-id="f9121-388">**pool_ptr** Wskaźnik do bloku kontroli puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-388">**pool_ptr** Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="f9121-389">**name_ptr** Wskaźnik na nazwę puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-389">**name_ptr** Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="f9121-390">**pool_start** Adres początkowy puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-390">**pool_start** Starting address of the memory pool.</span></span> <span data-ttu-id="f9121-391">Adres początkowy musi być wyrównany do rozmiaru typu danych ULONG.</span><span class="sxs-lookup"><span data-stu-id="f9121-391">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="f9121-392">**pool_size** Łączna liczba bajtów dostępnych dla puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-392">**pool_size** Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-393">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-393">Return Values</span></span>

- <span data-ttu-id="f9121-394">**TX_SUCCESS** (0X00) pomyślne utworzenie puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-394">**TX_SUCCESS** (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="f9121-395">**TX_POOL_ERROR** (0X02) Nieprawidłowy wskaźnik puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-395">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="f9121-396">Wskaźnik ma wartość NULL lub pula została już utworzona.</span><span class="sxs-lookup"><span data-stu-id="f9121-396">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="f9121-397">**TX_PTR_ERROR** (0X03) nieprawidłowy adres początkowy puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-397">**TX_PTR_ERROR** (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="f9121-398">Rozmiar **TX_SIZE_ERROR** (0x05) puli jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f9121-398">**TX_SIZE_ERROR** (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="f9121-399">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-399">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-400">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-400">Allowed From</span></span>

<span data-ttu-id="f9121-401">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-401">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-402">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-402">Preemption Possible</span></span>

<span data-ttu-id="f9121-403">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-403">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-404">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-404">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Create a memory pool whose total size is 2000 bytes
starting at address 0x500000. */
status = tx_byte_pool_create(&my_pool, "my_pool_name",
    (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
allocating memory. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-405">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-405">See Also</span></span>

- <span data-ttu-id="f9121-406">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-406">tx_byte_allocate</span></span>
- <span data-ttu-id="f9121-407">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-407">tx_byte_pool_delete</span></span>
- <span data-ttu-id="f9121-408">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-408">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="f9121-409">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-409">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-410">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-410">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-411">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-411">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="f9121-412">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="f9121-412">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="f9121-413">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-413">tx_byte_pool_delete</span></span>

<span data-ttu-id="f9121-414">Usuwanie puli bajtów pamięci</span><span class="sxs-lookup"><span data-stu-id="f9121-414">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-415">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-415">Prototype</span></span>

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-416">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-416">Description</span></span>

<span data-ttu-id="f9121-417">Ta usługa usuwa określoną pulę bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-417">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="f9121-418">Wszystkie wątki zostały zawieszone, oczekując na wznowienie pamięci z tej puli i z uwzględnieniem **TX_DELETED** stanu powrotu.</span><span class="sxs-lookup"><span data-stu-id="f9121-418">All threads suspended waiting for memory from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-419">*Jest on odpowiedzialny za zarządzanie obszarem pamięci skojarzonym z pulą, która jest dostępna po zakończeniu tej usługi. Ponadto aplikacja musi uniemożliwić korzystanie z usuniętej puli lub pamięci, która została wcześniej przypisana.*</span><span class="sxs-lookup"><span data-stu-id="f9121-419">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or memory previously allocated from it.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-420">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-420">Parameters</span></span>

- <span data-ttu-id="f9121-421">**pool_ptr** Wskaźnik do wcześniej utworzonej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-421">**pool_ptr** Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-422">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-422">Return Values</span></span>

- <span data-ttu-id="f9121-423">**TX_SUCCESS** (0X00) pomyślne usunięcie puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-423">**TX_SUCCESS** (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="f9121-424">**TX_POOL_ERROR** (0X02) Nieprawidłowy wskaźnik puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-424">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="f9121-425">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-425">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-426">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-426">Allowed From</span></span>

<span data-ttu-id="f9121-427">Wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-427">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-428">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-428">Preemption Possible</span></span>

<span data-ttu-id="f9121-429">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-429">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-430">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-430">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-431">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-431">See Also</span></span>

- <span data-ttu-id="f9121-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-432">tx_byte_allocate</span></span>
- <span data-ttu-id="f9121-433">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-433">tx_byte_pool_create</span></span>
- <span data-ttu-id="f9121-434">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-434">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="f9121-435">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-435">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-436">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-436">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-437">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-437">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="f9121-438">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="f9121-438">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="f9121-439">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-439">tx_byte_pool_info_get</span></span>

<span data-ttu-id="f9121-440">Pobierz informacje o puli bajtów</span><span class="sxs-lookup"><span data-stu-id="f9121-440">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-441">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-441">Prototype</span></span>

```c
UINT tx_byte_pool_info_get(
    TX_BYTE_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *fragments,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BYTE_POOL **next_pool);
```

### <a name="description"></a><span data-ttu-id="f9121-442">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-442">Description</span></span>

<span data-ttu-id="f9121-443">Ta usługa pobiera informacje o określonej puli bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-443">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-444">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-444">Parameters</span></span>

- <span data-ttu-id="f9121-445">**pool_ptr** Wskaźnik do wcześniej utworzonej puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-445">**pool_ptr** Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="f9121-446">**Nazwa** Wskaźnik do miejsca docelowego dla wskaźnika do nazwy puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-446">**name** Pointer to destination for the pointer to the byte pool's name.</span></span>
- <span data-ttu-id="f9121-447">**dostępne** Wskaźnik do miejsca docelowego dla liczby dostępnych bajtów w puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-447">**available** Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="f9121-448">**fragmenty** Wskaźnik do miejsca docelowego dla łącznej liczby fragmentów pamięci w puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-448">**fragments** Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="f9121-449">**first_suspended** Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-449">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="f9121-450">**suspended_count** Wskaźnik do miejsca docelowego dla liczby aktualnie zawieszonych wątków w tej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-450">**suspended_count** Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="f9121-451">**next_pool** Wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-451">**next_pool** Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-452">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-452">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-453">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-453">Return Values</span></span>

- <span data-ttu-id="f9121-454">**TX_SUCCESS** (0X00) pomyślne pobranie informacji o puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-454">**TX_SUCCESS** (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="f9121-455">**TX_POOL_ERROR** (0X02) Nieprawidłowy wskaźnik puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-455">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-456">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-456">Allowed From</span></span>

<span data-ttu-id="f9121-457">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-457">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-458">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-458">Preemption Possible</span></span>

<span data-ttu-id="f9121-459">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-459">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-460">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-460">Example</span></span>

```c
TX_BYTE_POOL my_pool;
CHAR *name;
ULONG available;
ULONG fragments;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BYTE_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_byte_pool_info_get(&my_pool, &name,
  &available, &fragments,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-461">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-461">See Also</span></span>

- <span data-ttu-id="f9121-462">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-462">tx_byte_allocate</span></span>
- <span data-ttu-id="f9121-463">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-463">tx_byte_pool_create</span></span>
- <span data-ttu-id="f9121-464">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-464">tx_byte_pool_delete</span></span>
- <span data-ttu-id="f9121-465">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-465">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-466">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-466">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-467">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-467">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="f9121-468">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="f9121-468">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="f9121-469">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-469">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="f9121-470">Pobierz informacje o wydajności puli bajtów</span><span class="sxs-lookup"><span data-stu-id="f9121-470">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-471">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-471">Prototype</span></span>

```c
UINT tx_byte_pool_performance_info_get(
    TX_BYTE_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *fragments_searched, 
    ULONG *merges, 
    ULONG *splits,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="f9121-472">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-472">Description</span></span>

<span data-ttu-id="f9121-473">Ta usługa pobiera informacje o wydajności dotyczące określonej puli bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-473">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-474">Aby można było zwracać informacje o wydajności *, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *zdefiniowanej dla tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="f9121-474">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-475">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-475">Parameters</span></span>

- <span data-ttu-id="f9121-476">**pool_ptr** Wskaźnik do wcześniej utworzonej puli bajtów pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-476">**pool_ptr** Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="f9121-477">**alokuje** Wskaźnik do miejsca docelowego dla liczby żądań alokacji wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-477">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="f9121-478">**wersje** Wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-478">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="f9121-479">**fragments_searched** Wskaźnik do miejsca docelowego dla liczby fragmentów pamięci wewnętrznej przeszukanych podczas żądania alokacji w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-479">**fragments_searched** Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="f9121-480">**scalenia** Wskaźnik do miejsca docelowego dla liczby wewnętrznych bloków pamięci scalonych podczas żądań alokacji w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-480">**merges** Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="f9121-481">**podziały** Wskaźnik do miejsca docelowego dla liczby wewnętrznych bloków pamięci podzielonej (fragmenty) utworzonych podczas żądania alokacji w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-481">**splits** Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="f9121-482">**zawieszenie** Wskaźnik do miejsca docelowego dla liczby zawieszeń alokacji wątku w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-482">**suspensions** Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="f9121-483">**limity czasu** Wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia przydziału w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-483">**timeouts** Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-484">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-484">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-485">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-485">Return Values</span></span>

- <span data-ttu-id="f9121-486">**TX_SUCCESS** (0X00) pomyślne pobieranie wydajności puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-486">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="f9121-487">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-487">**TX_PTR_ERROR** (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="f9121-488">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-488">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-489">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-489">Allowed From</span></span>

<span data-ttu-id="f9121-490">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-490">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-491">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-491">Example</span></span>

```c
TX_BYTE_POOL my_pool;
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created byte
pool. */
status = tx_byte_pool_performance_info_get(&my_pool,
  &fragments_searched,
  &merges, &splits,
  &allocates, &releases,
  &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```
### <a name="see-also"></a><span data-ttu-id="f9121-492">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-492">See Also</span></span>

- <span data-ttu-id="f9121-493">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-493">tx_byte_allocate</span></span>
- <span data-ttu-id="f9121-494">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-494">tx_byte_pool_create</span></span>
- <span data-ttu-id="f9121-495">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-495">tx_byte_pool_delete</span></span>
- <span data-ttu-id="f9121-496">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-496">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="f9121-497">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-497">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-498">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-498">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="f9121-499">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="f9121-499">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="f9121-500">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-500">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="f9121-501">Pobierz informacje o wydajności systemu puli bajtów</span><span class="sxs-lookup"><span data-stu-id="f9121-501">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-502">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-502">Prototype</span></span>

```c
UINT tx_byte_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *fragments_searched, 
    ULONG *merges,
    ULONG *splits, 
    ULONG *suspensions, 
    ULONG *timeouts);
```
### <a name="description"></a><span data-ttu-id="f9121-503">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-503">Description</span></span>

<span data-ttu-id="f9121-504">Ta usługa pobiera informacje o wydajności wszystkich pul bajtów pamięci w systemie.</span><span class="sxs-lookup"><span data-stu-id="f9121-504">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-505">Aby można było zwracać informacje o wydajności *, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *zdefiniowanej dla tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="f9121-505">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-506">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-506">Parameters</span></span>

- <span data-ttu-id="f9121-507">**alokuje** Wskaźnik do miejsca docelowego dla liczby żądań alokacji wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-507">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="f9121-508">**wersje** Wskaźnik do miejsca docelowego dla liczby żądań wydania wykonanych w tej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-508">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="f9121-509">**fragments_searched** Wskaźnik do miejsca docelowego dla łącznej liczby fragmentów pamięci wewnętrznej przeszukanych podczas żądania alokacji we wszystkich pulach bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-509">**fragments_searched** Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="f9121-510">**scalenia** Wskaźnik do miejsca docelowego dla łącznej liczby bloków pamięci wewnętrznej scalonych podczas żądania alokacji we wszystkich pulach bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-510">**merges** Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="f9121-511">**podziały** Wskaźnik do miejsca docelowego dla łącznej liczby bloków pamięci wewnętrznej (fragmentów) utworzonych podczas żądania alokacji dla wszystkich pul bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-511">**splits** Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="f9121-512">**zawieszenie** Wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń alokacji wątku dla wszystkich pul bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-512">**suspensions** Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="f9121-513">**limity czasu** Wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia przydziału dla wszystkich pul bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-513">**timeouts** Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-514">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-514">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-515">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-515">Return Values</span></span>

- <span data-ttu-id="f9121-516">**TX_SUCCESS** (0X00) pomyślne pobieranie wydajności puli bajtów.</span><span class="sxs-lookup"><span data-stu-id="f9121-516">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="f9121-517">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-517">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-518">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-518">Allowed From</span></span>

 <span data-ttu-id="f9121-519">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-519">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-520">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-520">Example</span></span>

```c
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all byte pools in the
system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
  &merges, &splits, &allocates, &releases,
  &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-521">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-521">See Also</span></span>

- <span data-ttu-id="f9121-522">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-522">tx_byte_allocate</span></span>
- <span data-ttu-id="f9121-523">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-523">tx_byte_pool_create</span></span>
- <span data-ttu-id="f9121-524">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-524">tx_byte_pool_delete</span></span>
- <span data-ttu-id="f9121-525">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-525">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="f9121-526">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-526">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-527">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-527">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="f9121-528">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="f9121-528">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="f9121-529">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-529">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="f9121-530">Ustawianie priorytetu listy zawieszania puli bajtów</span><span class="sxs-lookup"><span data-stu-id="f9121-530">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-531">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-531">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="f9121-532">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-532">Description</span></span>

<span data-ttu-id="f9121-533">Ta usługa umieszcza wątek o najwyższym priorytecie dla pamięci w tej puli na początku listy zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-533">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="f9121-534">Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="f9121-534">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-535">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-535">Parameters</span></span>

- <span data-ttu-id="f9121-536">**pool_ptr** Wskaźnik do bloku kontroli puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-536">**pool_ptr** Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-537">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-537">Return Values</span></span>

- <span data-ttu-id="f9121-538">**TX_SUCCESS** (0x00) pomyślna priorytetyzacja puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-538">**TX_SUCCESS** (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="f9121-539">**TX_POOL_ERROR** (0X02) Nieprawidłowy wskaźnik puli pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-539">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-540">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-540">Allowed From</span></span>

<span data-ttu-id="f9121-541">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-542">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-542">Preemption Possible</span></span>

<span data-ttu-id="f9121-543">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-543">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-544">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-544">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_byte_release call will wake up this thread,
if there is enough memory to satisfy its request. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-545">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-545">See Also</span></span>

- <span data-ttu-id="f9121-546">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-546">tx_byte_allocate</span></span>
- <span data-ttu-id="f9121-547">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-547">tx_byte_pool_create</span></span>
- <span data-ttu-id="f9121-548">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-548">tx_byte_pool_delete</span></span>
- <span data-ttu-id="f9121-549">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-549">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="f9121-550">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-550">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-551">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-551">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-552">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="f9121-552">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="f9121-553">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="f9121-553">tx_byte_release</span></span>

<span data-ttu-id="f9121-554">Wydawanie bajtów z powrotem do puli pamięci</span><span class="sxs-lookup"><span data-stu-id="f9121-554">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-555">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-555">Prototype</span></span>

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-556">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-556">Description</span></span>

<span data-ttu-id="f9121-557">Ta usługa zwalnia wcześniej przydzieloną przestrzeń pamięci z powrotem do skojarzonej puli.</span><span class="sxs-lookup"><span data-stu-id="f9121-557">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="f9121-558">Jeśli istnieje co najmniej jeden wątek, który wstrzymał oczekiwanie na pamięć z tej puli, przybierana jest pamięć i wznawiana do momentu wyczerpania pamięci lub do momentu, gdy nie będzie już można wstrzymać wątków.</span><span class="sxs-lookup"><span data-stu-id="f9121-558">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="f9121-559">Ten proces przydzielania pamięci do zawieszonych wątków zawsze zaczyna się od pierwszego wątku zawieszonego.</span><span class="sxs-lookup"><span data-stu-id="f9121-559">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-560">*Aplikacja musi uniemożliwić korzystanie z obszaru pamięci po jego udostępnieniu.*</span><span class="sxs-lookup"><span data-stu-id="f9121-560">*The application must prevent using the memory area after it is released.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-561">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-561">Parameters</span></span>

- <span data-ttu-id="f9121-562">**memory_ptr** Wskaźnik do wcześniej przydzieloną obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-562">**memory_ptr** Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-563">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-563">Return Values</span></span>

- <span data-ttu-id="f9121-564">**TX_SUCCESS** (0X00) pomyślne wydanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-564">**TX_SUCCESS** (0x00) Successful memory release.</span></span>
- <span data-ttu-id="f9121-565">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik obszaru pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9121-565">**TX_PTR_ERROR** (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="f9121-566">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-566">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-567">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-567">Allowed From</span></span>

<span data-ttu-id="f9121-568">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-568">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-569">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-569">Preemption Possible</span></span>

<span data-ttu-id="f9121-570">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-570">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-571">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-571">Example</span></span>

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-572">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-572">See Also</span></span>

- <span data-ttu-id="f9121-573">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="f9121-573">tx_byte_allocate</span></span>
- <span data-ttu-id="f9121-574">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="f9121-574">tx_byte_pool_create</span></span>
- <span data-ttu-id="f9121-575">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-575">tx_byte_pool_delete</span></span>
- <span data-ttu-id="f9121-576">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-576">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="f9121-577">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-577">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="f9121-578">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-578">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-579">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-579">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="f9121-580">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="f9121-580">tx_event_flags_create</span></span>

<span data-ttu-id="f9121-581">Utwórz grupę flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f9121-581">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-582">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-582">Prototype</span></span>

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-583">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-583">Description</span></span>

<span data-ttu-id="f9121-584">Ta usługa tworzy grupę flag zdarzeń 32.</span><span class="sxs-lookup"><span data-stu-id="f9121-584">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="f9121-585">Wszystkie flagi zdarzeń 32 w grupie są inicjowane na zero.</span><span class="sxs-lookup"><span data-stu-id="f9121-585">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="f9121-586">Każda flaga zdarzenia jest reprezentowana przez jeden bit.</span><span class="sxs-lookup"><span data-stu-id="f9121-586">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-587">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-587">Parameters</span></span>

- <span data-ttu-id="f9121-588">**group_ptr** Wskaźnik do bloku sterowania grupą flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-588">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="f9121-589">**name_ptr** Wskaźnik na nazwę grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-589">**name_ptr** Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-590">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-590">Return Values</span></span>

- <span data-ttu-id="f9121-591">Pomyślna operacja tworzenia grupy zdarzeń **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-591">**TX_SUCCESS** (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="f9121-592">**TX_GROUP_ERROR** (0X06) Nieprawidłowy wskaźnik grupy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-592">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="f9121-593">Wskaźnik ma **wartość null** lub grupa zdarzeń została już utworzona.</span><span class="sxs-lookup"><span data-stu-id="f9121-593">Either the pointer is **NULL** or the event group is already created.</span></span>
- <span data-ttu-id="f9121-594">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-594">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-595">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-595">Allowed From</span></span>

<span data-ttu-id="f9121-596">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-596">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-597">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-597">Preemption Possible</span></span>

<span data-ttu-id="f9121-598">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-598">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-599">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-599">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-600">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-600">See Also</span></span>

- <span data-ttu-id="f9121-601">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-601">tx_event_flags_delete</span></span>
- <span data-ttu-id="f9121-602">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="f9121-602">tx_event_flags_get</span></span>
- <span data-ttu-id="f9121-603">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-603">tx_event_flags_info_get</span></span>
- <span data-ttu-id="f9121-604">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-604">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="f9121-605">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-605">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-606">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="f9121-606">tx_event_flags_set</span></span>
- <span data-ttu-id="f9121-607">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-607">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="f9121-608">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-608">tx_event_flags_delete</span></span>

<span data-ttu-id="f9121-609">Usuń grupę flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f9121-609">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-610">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-610">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-611">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-611">Description</span></span>

<span data-ttu-id="f9121-612">Ta usługa usuwa określoną grupę flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-612">This service deletes the specified event flags group.</span></span> <span data-ttu-id="f9121-613">Wszystkie wątki zawieszone w trakcie oczekiwania na zdarzenia z tej grupy są wznawiane i mają TX_DELETED stanu powrotu.</span><span class="sxs-lookup"><span data-stu-id="f9121-613">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f9121-614">*Aplikacja musi upewnić się, że ustawione wywołanie zwrotne powiadomień dla tej grupy flag zdarzeń zostanie ukończone (lub wyłączone) przed usunięciem grupy flag zdarzeń. Ponadto aplikacja musi uniemożliwić wszystkie przyszłe użycie grupy flag zdarzeń usuniętych.*</span><span class="sxs-lookup"><span data-stu-id="f9121-614">*The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group. In addition, the application must prevent all future use of a deleted event flags group.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-615">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-615">Parameters</span></span>

- <span data-ttu-id="f9121-616">**group_ptr** Wskaźnik do wcześniej utworzonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-616">**group_ptr** Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-617">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-617">Return Values</span></span>

- <span data-ttu-id="f9121-618">Usuwanie grupy flag zdarzeń zakończonych niepowodzeniem **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-618">**TX_SUCCESS** (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="f9121-619">**TX_GROUP_ERROR** (0X06) Nieprawidłowy wskaźnik grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-619">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="f9121-620">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-620">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-621">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-621">Allowed From</span></span>

<span data-ttu-id="f9121-622">Wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-622">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-623">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-623">Preemption Possible</span></span>

<span data-ttu-id="f9121-624">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-624">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-625">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-625">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Delete event flags group. Assume that the group has
already been created with a call to
tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-626">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-626">See Also</span></span>

- <span data-ttu-id="f9121-627">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="f9121-627">tx_event_flags_create</span></span>
- <span data-ttu-id="f9121-628">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="f9121-628">tx_event_flags_get</span></span>
- <span data-ttu-id="f9121-629">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-629">tx_event_flags_info_get</span></span>
- <span data-ttu-id="f9121-630">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-630">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="f9121-631">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-631">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-632">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="f9121-632">tx_event_flags_set</span></span>
- <span data-ttu-id="f9121-633">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-633">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="f9121-634">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="f9121-634">tx_event_flags_get</span></span>

<span data-ttu-id="f9121-635">Pobierz flagi zdarzeń z grupy flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f9121-635">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-636">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-636">Prototype</span></span>

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f9121-637">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-637">Description</span></span>

<span data-ttu-id="f9121-638">Ta usługa pobiera flagi zdarzeń z określonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-638">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="f9121-639">Każda grupa flag zdarzeń zawiera 32 flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-639">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="f9121-640">Każda flaga jest reprezentowana przez jeden bit.</span><span class="sxs-lookup"><span data-stu-id="f9121-640">Each flag is represented by a single bit.</span></span> <span data-ttu-id="f9121-641">Ta usługa może pobrać różne kombinacje flag zdarzeń wybrane przez parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f9121-641">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-642">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-642">Parameters</span></span>

- <span data-ttu-id="f9121-643">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-643">**group_ptr**</span></span> <br><span data-ttu-id="f9121-644">Wskaźnik do wcześniej utworzonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-644">Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="f9121-645">**requested_flags**</span><span class="sxs-lookup"><span data-stu-id="f9121-645">**requested_flags**</span></span> <br><span data-ttu-id="f9121-646">32-bitowa zmienna bez znaku reprezentująca żądane flagi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f9121-646">32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="f9121-647">**get_option**</span><span class="sxs-lookup"><span data-stu-id="f9121-647">**get_option**</span></span> <br><span data-ttu-id="f9121-648">Określa, czy są wymagane wszystkie lub wszystkie wymagane flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-648">Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="f9121-649">Następujące opcje są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="f9121-649">The following are valid selections:</span></span>

  - <span data-ttu-id="f9121-650">**TX_AND** (0x02)</span><span class="sxs-lookup"><span data-stu-id="f9121-650">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="f9121-651">**TX_AND_CLEAR** (0x03)</span><span class="sxs-lookup"><span data-stu-id="f9121-651">**TX_AND_CLEAR** (0x03)</span></span>
  - <span data-ttu-id="f9121-652">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="f9121-652">**TX_OR** (0x00)</span></span>
  - <span data-ttu-id="f9121-653">**TX_OR_CLEAR** (0x01)</span><span class="sxs-lookup"><span data-stu-id="f9121-653">**TX_OR_CLEAR** (0x01)</span></span>

    <span data-ttu-id="f9121-654">Wybranie opcji TX_AND lub TX_AND_CLEAR określa, że wszystkie flagi zdarzeń muszą znajdować się w grupie.</span><span class="sxs-lookup"><span data-stu-id="f9121-654">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="f9121-655">Wybór TX_OR lub TX_OR_CLEAR określa, że każda flaga zdarzenia jest zadowalająca.</span><span class="sxs-lookup"><span data-stu-id="f9121-655">Selecting TX_OR or TX_OR_CLEAR     specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="f9121-656">Flagi zdarzeń, które spełniają żądanie, są wyczyszczone (Ustaw wartość zero), jeśli określono TX_AND_CLEAR lub TX_OR_CLEAR.</span><span class="sxs-lookup"><span data-stu-id="f9121-656">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="f9121-657">**actual_flags_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-657">**actual_flags_ptr**</span></span> <br><span data-ttu-id="f9121-658">Wskaźnik do miejsca docelowego, gdzie są umieszczane flagi pobranych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-658">Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="f9121-659">Należy zauważyć, że uzyskane bieżące flagi mogą zawierać flagi, które nie zostały zażądane.</span><span class="sxs-lookup"><span data-stu-id="f9121-659">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="f9121-660">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="f9121-660">**wait_option**</span></span>  <br><span data-ttu-id="f9121-661">Definiuje, w jaki sposób działa usługa, jeśli wybrane flagi zdarzeń nie są ustawione.</span><span class="sxs-lookup"><span data-stu-id="f9121-661">Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="f9121-662">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9121-662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="f9121-663">**TX_NO_WAIT** (0x00000000) — wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9121-663">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="f9121-664">Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-664">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="f9121-665">**TX_WAIT_FOREVER** wartość limitu czasu (0xffffffff) — wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się przez nieograniczony czas do momentu udostępnienia flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-665">**TX_WAIT_FOREVER** timeout value  (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>
  - <span data-ttu-id="f9121-666">wartość limitu czasu (0x00000001 przez 0xFFFFFFFE) — wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma pozostać zawieszona podczas oczekiwania na flagi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f9121-666">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-667">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-667">Return Values</span></span>

- <span data-ttu-id="f9121-668">Pomyślne flagi zdarzeń **TX_SUCCESS** (0x00) get.</span><span class="sxs-lookup"><span data-stu-id="f9121-668">**TX_SUCCESS** (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="f9121-669">Grupa flag zdarzeń **TX_DELETED** (0x01) została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-669">**TX_DELETED** (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="f9121-670">Usługa **TX_NO_EVENTS** (0x07) nie może pobrać określonych zdarzeń w określonym czasie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="f9121-670">**TX_NO_EVENTS** (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="f9121-671">Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-671">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="f9121-672">**TX_GROUP_ERROR** (0X06) Nieprawidłowy wskaźnik grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-672">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="f9121-673">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik dla rzeczywistych flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-673">**TX_PTR_ERROR** (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="f9121-674">**TX_WAIT_ERROR** (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-674">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="f9121-675">**TX_OPTION_ERROR** (0x08) określono nieprawidłową opcję Get-Option.</span><span class="sxs-lookup"><span data-stu-id="f9121-675">**TX_OPTION_ERROR** (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-676">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-676">Allowed From</span></span>

<span data-ttu-id="f9121-677">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-677">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-678">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-678">Preemption Possible</span></span>

<span data-ttu-id="f9121-679">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-679">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-680">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-680">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG actual_events;
UINT status;

/* Request that event flags 0, 4, and 8 are all set. Also,
if they are set they should be cleared. If the event
flags are not set, this service suspends for a maximum of
20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
    TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
actual events obtained. */
```

<span data-ttu-id="f9121-681">**Zobacz również**</span><span class="sxs-lookup"><span data-stu-id="f9121-681">**See Also**</span></span>

- <span data-ttu-id="f9121-682">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="f9121-682">tx_event_flags_create</span></span>
- <span data-ttu-id="f9121-683">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-683">tx_event_flags_delete</span></span>
- <span data-ttu-id="f9121-684">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-684">tx_event_flags_info_get</span></span>
- <span data-ttu-id="f9121-685">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-685">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="f9121-686">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-686">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-687">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="f9121-687">tx_event_flags_set</span></span>
- <span data-ttu-id="f9121-688">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-688">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_info_get"></a><span data-ttu-id="f9121-689">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-689">tx_event_flags_info_get</span></span>

<span data-ttu-id="f9121-690">Pobierz informacje o grupie flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f9121-690">Retrieve information about event flags group</span></span>

<span data-ttu-id="f9121-691">**Prototype**</span><span class="sxs-lookup"><span data-stu-id="f9121-691">**Prototype**</span></span>

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

<span data-ttu-id="f9121-692">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f9121-692">**Description**</span></span>

<span data-ttu-id="f9121-693">Ta usługa pobiera informacje o określonej grupie flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-693">This service retrieves information about the specified event flags group.</span></span>

<span data-ttu-id="f9121-694">**Parametry**</span><span class="sxs-lookup"><span data-stu-id="f9121-694">**Parameters**</span></span>

- <span data-ttu-id="f9121-695">**group_ptr** Wskaźnik do bloku sterowania grupą flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-695">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="f9121-696">**Nazwa** Wskaźnik do miejsca docelowego dla wskaźnika do nazwy grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-696">**name** Pointer to destination for the pointer to the event flags group's name.</span></span>
- <span data-ttu-id="f9121-697">**current_flags** Wskaźnik do miejsca docelowego dla bieżących flag ustawionych w grupie flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-697">**current_flags** Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="f9121-698">**first_suspended** Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-698">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="f9121-699">**suspended_count** Wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej grupie flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-699">**suspended_count** Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="f9121-700">**next_group** Wskaźnik do miejsca docelowego dla wskaźnika następnej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-700">**next_group** Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-701">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-701">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-702">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-702">Return Values</span></span>

- <span data-ttu-id="f9121-703">**TX_SUCCESS** (0X00) pomyślne pobieranie informacji o grupie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-703">**TX_SUCCESS** (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="f9121-704">**TX_GROUP_ERROR** (0X06) Nieprawidłowy wskaźnik grupy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-704">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-705">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-705">Allowed From</span></span>

<span data-ttu-id="f9121-706">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-706">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-707">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-707">Preemption Possible</span></span>

<span data-ttu-id="f9121-708">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-708">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-709">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-709">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
CHAR *name;
ULONG current_flags;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_EVENT_FLAGS_GROUP *next_group;
UINT status;

/* Retrieve information about the previously created
event flags group "my_event_group." */
status = tx_event_flags_info_get(&my_event_group, &name,
    &current_flags,
    &first_suspended, &suspended_count,
    &next_group);
/* If status equals TX_SUCCESS, the information requested is
valid. */
```
<span data-ttu-id="f9121-710">**Zobacz również**</span><span class="sxs-lookup"><span data-stu-id="f9121-710">**See Also**</span></span>

- <span data-ttu-id="f9121-711">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="f9121-711">tx_event_flags_create</span></span>
- <span data-ttu-id="f9121-712">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-712">tx_event_flags_delete</span></span>
- <span data-ttu-id="f9121-713">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="f9121-713">tx_event_flags_get</span></span>
- <span data-ttu-id="f9121-714">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-714">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="f9121-715">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-715">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-716">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="f9121-716">tx_event_flags_set</span></span>
- <span data-ttu-id="f9121-717">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-717">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="f9121-718">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-718">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="f9121-719">Pobierz informacje o wydajności grupy flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f9121-719">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-720">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-720">Prototype</span></span>

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="f9121-721">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-721">Description</span></span>

<span data-ttu-id="f9121-722">Ta usługa pobiera informacje o wydajności dotyczące określonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-722">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-723">Aby można było zwracać informacje o wydajności *, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *zdefiniowanej dla tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="f9121-723">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-724">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-724">Parameters</span></span>

- <span data-ttu-id="f9121-725">**group_ptr** Wskaźnik do wcześniej utworzonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-725">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="f9121-726">**zestawy** Wskaźnik do miejsca docelowego dla liczby flag zdarzeń ustawia żądania wykonane dla tej grupy.</span><span class="sxs-lookup"><span data-stu-id="f9121-726">**sets** Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="f9121-727">**Pobiera** Wskaźnik do miejsca docelowego dla liczby flag zdarzeń pobieranie żądań wykonanych dla tej grupy.</span><span class="sxs-lookup"><span data-stu-id="f9121-727">**gets** Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="f9121-728">**zawieszenie** Wskaźnik do miejsca docelowego dla liczby flag zdarzeń wątku pobieranie zawieszeń dla tej grupy.</span><span class="sxs-lookup"><span data-stu-id="f9121-728">**suspensions** Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="f9121-729">**limity czasu** Wskaźnik do miejsca docelowego dla liczby flag zdarzeń uzyskuje limity czasu zawieszenia dla tej grupy.</span><span class="sxs-lookup"><span data-stu-id="f9121-729">**timeouts** Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-730">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-730">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-731">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-731">Return Values</span></span>

- <span data-ttu-id="f9121-732">**TX_SUCCESS** (0X00) pomyślne flagi zdarzeń grupy get.</span><span class="sxs-lookup"><span data-stu-id="f9121-732">**TX_SUCCESS** (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="f9121-733">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-733">**TX_PTR_ERROR** (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="f9121-734">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-734">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-735">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-735">Allowed From</span></span>

<span data-ttu-id="f9121-736">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-736">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-737">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-737">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flag_group;
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created event
flag group. */
status = tx_event_flags_performance_info_get(&my_event_flag_group,
    &sets, &gets, &suspensions,
    &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-738">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-738">See Also</span></span>

- <span data-ttu-id="f9121-739">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="f9121-739">tx_event_flags_create</span></span>
- <span data-ttu-id="f9121-740">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-740">tx_event_flags_delete</span></span>
- <span data-ttu-id="f9121-741">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="f9121-741">tx_event_flags_get</span></span>
- <span data-ttu-id="f9121-742">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-742">tx_event_flags_info_get</span></span>
- <span data-ttu-id="f9121-743">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-743">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-744">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="f9121-744">tx_event_flags_set</span></span>
- <span data-ttu-id="f9121-745">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-745">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="f9121-746">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-746">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="f9121-747">Pobierz informacje o systemie wydajności</span><span class="sxs-lookup"><span data-stu-id="f9121-747">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-748">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-748">Prototype</span></span>

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="f9121-749">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-749">Description</span></span>

<span data-ttu-id="f9121-750">Ta usługa pobiera informacje o wydajności wszystkich grup flag zdarzeń w systemie.</span><span class="sxs-lookup"><span data-stu-id="f9121-750">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-751">Aby można było zwracać informacje o wydajności *, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *zdefiniowanej dla tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="f9121-751">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-752">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-752">Parameters</span></span>

- <span data-ttu-id="f9121-753">**zestawy** Wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń ustawionych żądań wykonywanych dla wszystkich grup.</span><span class="sxs-lookup"><span data-stu-id="f9121-753">**sets** Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="f9121-754">**Pobiera** Wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń pobieranie żądań wykonanych dla wszystkich grup.</span><span class="sxs-lookup"><span data-stu-id="f9121-754">**gets** Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="f9121-755">**zawieszenie** Wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń wątku pobieranie zawieszeń dla wszystkich grup.</span><span class="sxs-lookup"><span data-stu-id="f9121-755">**suspensions** Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="f9121-756">**limity czasu** Wskaźnik do miejsca docelowego dla łącznej liczby flag zdarzeń pobieranie limitów czasu zawieszenia dla wszystkich grup.</span><span class="sxs-lookup"><span data-stu-id="f9121-756">**timeouts** Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-757">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-757">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-758">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-758">Return Values</span></span>

- <span data-ttu-id="f9121-759">**TX_SUCCESS** (0X00) pomyślne flagi zdarzeń wydajność systemu.</span><span class="sxs-lookup"><span data-stu-id="f9121-759">**TX_SUCCESS** (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="f9121-760">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-760">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="example"></a><span data-ttu-id="f9121-761">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-761">Example</span></span>

```c
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created event
flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-762">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-762">See Also</span></span>

- <span data-ttu-id="f9121-763">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="f9121-763">tx_event_flags_create</span></span>
- <span data-ttu-id="f9121-764">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-764">tx_event_flags_delete</span></span>
- <span data-ttu-id="f9121-765">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="f9121-765">tx_event_flags_get</span></span>
- <span data-ttu-id="f9121-766">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-766">tx_event_flags_info_get</span></span>
- <span data-ttu-id="f9121-767">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-767">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="f9121-768">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="f9121-768">tx_event_flags_set</span></span>
- <span data-ttu-id="f9121-769">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-769">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="f9121-770">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="f9121-770">tx_event_flags_set</span></span>

<span data-ttu-id="f9121-771">Ustawianie flag zdarzeń w grupie flag zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f9121-771">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-772">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-772">Prototype</span></span>

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a><span data-ttu-id="f9121-773">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-773">Description</span></span>

<span data-ttu-id="f9121-774">Ta usługa ustawia lub czyści flagi zdarzeń w grupie flag zdarzeń, w zależności od określonego zestawu opcji.</span><span class="sxs-lookup"><span data-stu-id="f9121-774">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="f9121-775">Wszystkie zawieszone wątki, których żądanie flag zdarzeń jest teraz spełnione, są wznawiane.</span><span class="sxs-lookup"><span data-stu-id="f9121-775">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-776">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-776">Parameters</span></span>

- <span data-ttu-id="f9121-777">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-777">**group_ptr**</span></span> <br><span data-ttu-id="f9121-778">Wskaźnik do wcześniej utworzonego bloku kontroli grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-778">Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="f9121-779">**flags_to_set**</span><span class="sxs-lookup"><span data-stu-id="f9121-779">**flags_to_set**</span></span> <br><span data-ttu-id="f9121-780">Określa flagi zdarzeń do ustawienia lub wyczyszczenia w zależności od wybranej opcji zestawu.</span><span class="sxs-lookup"><span data-stu-id="f9121-780">Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="f9121-781">**set_option**</span><span class="sxs-lookup"><span data-stu-id="f9121-781">**set_option**</span></span> <br><span data-ttu-id="f9121-782">Określa, czy określone flagi zdarzenia są ANDed lub logicznie do bieżących flag zdarzenia w grupie.</span><span class="sxs-lookup"><span data-stu-id="f9121-782">Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="f9121-783">Następujące opcje są prawidłowe:</span><span class="sxs-lookup"><span data-stu-id="f9121-783">The following are valid selections:</span></span>
  - <span data-ttu-id="f9121-784">**TX_AND** (0x02)</span><span class="sxs-lookup"><span data-stu-id="f9121-784">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="f9121-785">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="f9121-785">**TX_OR** (0x00)</span></span>

  <span data-ttu-id="f9121-786">Wybranie TX_AND określa, że określone flagi zdarzeń są **i** są wbudowane w bieżące flagi zdarzenia w grupie.</span><span class="sxs-lookup"><span data-stu-id="f9121-786">Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="f9121-787">Ta opcja jest często używana do czyszczenia flag zdarzeń w grupie.</span><span class="sxs-lookup"><span data-stu-id="f9121-787">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="f9121-788">W przeciwnym razie, jeśli określono TX_OR, określone flagi zdarzeń są **lub** Ed bieżącym zdarzeniem w grupie.</span><span class="sxs-lookup"><span data-stu-id="f9121-788">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-789">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-789">Return Values</span></span>
- <span data-ttu-id="f9121-790">Ustawiono flagę zdarzenia pomyślnego **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-790">**TX_SUCCESS** (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="f9121-791">**TX_GROUP_ERROR** (0X06) Nieprawidłowy wskaźnik do grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-791">**TX_GROUP_ERROR** (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="f9121-792">**TX_OPTION_ERROR** (0x08) określono nieprawidłową opcję Set.</span><span class="sxs-lookup"><span data-stu-id="f9121-792">**TX_OPTION_ERROR** (0x08) Invalid set-option specified.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-793">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-793">Preemption Possible</span></span>

<span data-ttu-id="f9121-794">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-794">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-795">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-795">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Set event flags 0, 4, and 8. */
status = tx_event_flags_set(&my_event_flags_group,
    0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
set and any suspended thread whose request was satisfied
has been resumed. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-796">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-796">See Also</span></span>

- <span data-ttu-id="f9121-797">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="f9121-797">tx_event_flags_create</span></span>
- <span data-ttu-id="f9121-798">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-798">tx_event_flags_delete</span></span>
- <span data-ttu-id="f9121-799">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="f9121-799">tx_event_flags_get</span></span>
- <span data-ttu-id="f9121-800">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-800">tx_event_flags_info_get</span></span>
- <span data-ttu-id="f9121-801">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-801">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="f9121-802">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-802">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-803">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-803">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="f9121-804">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-804">tx_event_flags_set_notify</span></span>

<span data-ttu-id="f9121-805">Powiadamiaj aplikację, gdy są ustawione flagi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="f9121-805">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-806">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-806">Prototype</span></span>

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a><span data-ttu-id="f9121-807">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-807">Description</span></span>

<span data-ttu-id="f9121-808">Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy jedna lub więcej flag zdarzeń jest ustawionych w określonej grupie flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-808">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="f9121-809">Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez</span><span class="sxs-lookup"><span data-stu-id="f9121-809">The processing of the notification callback is defined by the</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-810">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-810">Parameters</span></span>
- <span data-ttu-id="f9121-811">**group_ptr** Wskaźnik do wcześniej utworzonej grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-811">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="f9121-812">**events_set_notify** Wskaźnik do flag zdarzeń aplikacji ustawia funkcję powiadomień.</span><span class="sxs-lookup"><span data-stu-id="f9121-812">**events_set_notify** Pointer to application's event flags set notification function.</span></span> <span data-ttu-id="f9121-813">Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f9121-813">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-814">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-814">Return Values</span></span>

- <span data-ttu-id="f9121-815">**TX_SUCCESS** (0x00) pomyślna Rejestracja flag zdarzeń ustawionych dla powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="f9121-815">**TX_SUCCESS** (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="f9121-816">**TX_GROUP_ERROR** (0X06) Nieprawidłowy wskaźnik grupy flag zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-816">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="f9121-817">**TX_FEATURE_NOT_ENABLED** (0xFF) system został skompilowany z wyłączonymi funkcjami powiadomień.</span><span class="sxs-lookup"><span data-stu-id="f9121-817">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="example"></a><span data-ttu-id="f9121-818">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-818">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_group;

/* Register the "my_event_flags_set_notify" function for monitoring
event flags set in the event flags group "my_group." */
status = tx_event_flags_set_notify(&my_group, my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
was successfully registered. */
void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)

/* One or more event flags was set in this group! */
```

### <a name="see-also"></a><span data-ttu-id="f9121-819">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-819">See Also</span></span>

- <span data-ttu-id="f9121-820">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="f9121-820">tx_event_flags_create</span></span>
- <span data-ttu-id="f9121-821">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-821">tx_event_flags_delete</span></span>
- <span data-ttu-id="f9121-822">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="f9121-822">tx_event_flags_get</span></span>
- <span data-ttu-id="f9121-823">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-823">tx_event_flags_info_get</span></span>
- <span data-ttu-id="f9121-824">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-824">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="f9121-825">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-825">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-826">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="f9121-826">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="f9121-827">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="f9121-827">tx_interrupt_control</span></span>

<span data-ttu-id="f9121-828">Włączanie i wyłączanie przerwań</span><span class="sxs-lookup"><span data-stu-id="f9121-828">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-829">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-829">Prototype</span></span>

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a><span data-ttu-id="f9121-830">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-830">Description</span></span>

<span data-ttu-id="f9121-831">Ta usługa włącza lub wyłącza przerwania określone przez parametr wejściowy *new_posture*.</span><span class="sxs-lookup"><span data-stu-id="f9121-831">This service enables or disables interrupts as specified by the input parameter *new_posture*.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-832">*Jeśli ta usługa jest wywoływana z wątku aplikacji, przerwa stan pozostaje częścią kontekstu tego wątku. Na przykład jeśli wątek wywołuje tę procedurę w celu wyłączenia przerwań, a następnie zawiesza się po wznowieniu, przerwania zostaną wyłączone ponownie.*</span><span class="sxs-lookup"><span data-stu-id="f9121-832">*If this service is called from an application thread, the interrupt posture remains part of that thread's context. For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.*</span></span>

> [!WARNING]
> <span data-ttu-id="f9121-833">*Ta usługa nie powinna być używana do włączania przerwań podczas inicjacji. Wykonanie tej operacji może spowodować nieprzewidywalne wyniki.*</span><span class="sxs-lookup"><span data-stu-id="f9121-833">*This service should not be used to enable interrupts during initialization! Doing so could cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-834">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-834">Parameters</span></span>

- <span data-ttu-id="f9121-835">**new_posture** Ten parametr określa, czy przerwania są wyłączone czy włączone.</span><span class="sxs-lookup"><span data-stu-id="f9121-835">**new_posture** This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="f9121-836">Wartości prawne obejmują **TX_INT_DISABLE** i **TX_INT_ENABLE**.</span><span class="sxs-lookup"><span data-stu-id="f9121-836">Legal values include **TX_INT_DISABLE** and **TX_INT_ENABLE**.</span></span> <span data-ttu-id="f9121-837">Rzeczywiste wartości tych parametrów są specyficzne dla portów.</span><span class="sxs-lookup"><span data-stu-id="f9121-837">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="f9121-838">Ponadto niektóre architektury przetwarzania mogą obsługiwać dodatkowe przerwania postures.</span><span class="sxs-lookup"><span data-stu-id="f9121-838">In addition, some processing architectures might support additional interrupt disable postures.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-839">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-839">Return Values</span></span>
- <span data-ttu-id="f9121-840">**poprzedni stan** Ta usługa zwraca poprzednią stan przerwania do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f9121-840">**previous posture** This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="f9121-841">Dzięki temu użytkownicy usługi mogą przywrócić poprzednią stan po wyłączeniu przerwań.</span><span class="sxs-lookup"><span data-stu-id="f9121-841">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-842">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-842">Allowed From</span></span>

<span data-ttu-id="f9121-843">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-843">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-844">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-844">Preemption Possible</span></span>

<span data-ttu-id="f9121-845">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-845">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-846">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-846">Example</span></span>

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a><span data-ttu-id="f9121-847">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-847">See Also</span></span>

<span data-ttu-id="f9121-848">Brak</span><span class="sxs-lookup"><span data-stu-id="f9121-848">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="f9121-849">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="f9121-849">tx_mutex_create</span></span>

<span data-ttu-id="f9121-850">Utwórz element mutex wzajemnego wykluczania</span><span class="sxs-lookup"><span data-stu-id="f9121-850">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-851">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-851">Prototype</span></span>

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a><span data-ttu-id="f9121-852">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-852">Description</span></span>

<span data-ttu-id="f9121-853">Ta usługa tworzy element mutex do wzajemnego wykluczania między wątkami na potrzeby ochrony zasobów.</span><span class="sxs-lookup"><span data-stu-id="f9121-853">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-854">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-854">Parameters</span></span>

- <span data-ttu-id="f9121-855">**mutex_ptr** Wskaźnik do bloku sterowania muteksem.</span><span class="sxs-lookup"><span data-stu-id="f9121-855">**mutex_ptr** Pointer to a mutex control block.</span></span>
- <span data-ttu-id="f9121-856">**name_ptr** Wskaźnik na nazwę obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-856">**name_ptr** Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="f9121-857">**priority_inherit** Określa, czy ten element mutex obsługuje dziedziczenie priorytetów.</span><span class="sxs-lookup"><span data-stu-id="f9121-857">**priority_inherit** Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="f9121-858">Jeśli ta wartość jest TX_INHERIT, jest obsługiwane dziedziczenie priorytetu.</span><span class="sxs-lookup"><span data-stu-id="f9121-858">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="f9121-859">Jeśli jednak określono TX_NO_INHERIT, dziedziczenie priorytetu nie jest obsługiwane przez ten mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-859">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-860">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-860">Return Values</span></span>

- <span data-ttu-id="f9121-861">**TX_SUCCESS** (0X00) pomyślne utworzenie obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-861">**TX_SUCCESS** (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="f9121-862">**TX_MUTEX_ERROR** (0X1C) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="f9121-862">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="f9121-863">Wskaźnik ma wartość NULL lub element mutex został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="f9121-863">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="f9121-864">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-864">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="f9121-865">**TX_INHERIT_ERROR** (0x1F) nieprawidłowy priorytet dziedziczenia parametru.</span><span class="sxs-lookup"><span data-stu-id="f9121-865">**TX_INHERIT_ERROR** (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-866">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-866">Allowed From</span></span>

<span data-ttu-id="f9121-867">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-867">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-868">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-868">Preemption Possible</span></span>

<span data-ttu-id="f9121-869">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-869">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-870">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-870">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Create a mutex to provide protection over a
common resource. */
status = tx_mutex_create(&my_mutex,"my_mutex_name",
    TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
use. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-871">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-871">See Also</span></span>

- <span data-ttu-id="f9121-872">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-872">tx_mutex_delete</span></span>
- <span data-ttu-id="f9121-873">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="f9121-873">tx_mutex_get</span></span>
- <span data-ttu-id="f9121-874">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-874">tx_mutex_info_get</span></span>
- <span data-ttu-id="f9121-875">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-875">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="f9121-876">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-876">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-877">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-877">tx_mutex_prioritize</span></span>
- <span data-ttu-id="f9121-878">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="f9121-878">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="f9121-879">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-879">tx_mutex_delete</span></span>

<span data-ttu-id="f9121-880">Usuń element mutex wzajemnego wykluczania</span><span class="sxs-lookup"><span data-stu-id="f9121-880">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-881">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-881">Prototype</span></span>

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-882">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-882">Description</span></span>

<span data-ttu-id="f9121-883">Ta usługa usuwa określony element mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-883">This service deletes the specified mutex.</span></span> <span data-ttu-id="f9121-884">Wszystkie wątki zawieszone w trakcie oczekiwania na element mutex są wznawiane i nadano **TX_DELETED** stanu powrotu.</span><span class="sxs-lookup"><span data-stu-id="f9121-884">All threads suspended waiting for the mutex are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-885">*Jest to odpowiedzialność aplikacji, aby uniemożliwić korzystanie z usuniętego obiektu mutex.*</span><span class="sxs-lookup"><span data-stu-id="f9121-885">*It is the application's responsibility to prevent use of a deleted mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-886">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-886">Parameters</span></span>

- <span data-ttu-id="f9121-887">**mutex_ptr** Wskaźnik do wcześniej utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-887">**mutex_ptr** Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-888">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-888">Return Values</span></span>

- <span data-ttu-id="f9121-889">**TX_SUCCESS** (0X00) pomyślne usunięcie obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-889">**TX_SUCCESS** (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="f9121-890">**TX_MUTEX_ERROR** (0X1C) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="f9121-890">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="f9121-891">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-891">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-892">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-892">Allowed From</span></span>

<span data-ttu-id="f9121-893">Wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-893">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-894">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-894">Preemption Possible</span></span>

<span data-ttu-id="f9121-895">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-895">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-896">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-896">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-897">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-897">See Also</span></span>

- <span data-ttu-id="f9121-898">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="f9121-898">tx_mutex_create</span></span>
- <span data-ttu-id="f9121-899">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="f9121-899">tx_mutex_get</span></span>
- <span data-ttu-id="f9121-900">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-900">tx_mutex_info_get</span></span>
- <span data-ttu-id="f9121-901">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-901">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="f9121-902">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-902">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-903">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-903">tx_mutex_prioritize</span></span>
- <span data-ttu-id="f9121-904">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="f9121-904">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="f9121-905">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="f9121-905">tx_mutex_get</span></span>

<span data-ttu-id="f9121-906">Uzyskaj własność obiektu mutex</span><span class="sxs-lookup"><span data-stu-id="f9121-906">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-907">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-907">Prototype</span></span>

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f9121-908">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-908">Description</span></span>

<span data-ttu-id="f9121-909">Ta usługa próbuje uzyskać wyłączną własność określonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-909">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="f9121-910">Jeśli wątek wywołujący jest już właścicielem obiektu mutex, licznik wewnętrzny jest zwiększany i zwracany jest stan pomyślny.</span><span class="sxs-lookup"><span data-stu-id="f9121-910">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="f9121-911">Jeśli element mutex jest własnością innego wątku, a ten wątek ma wyższy priorytet, a dziedziczenie priorytetów zostało określone w elemencie mutex Create, priorytet wątku o niższym priorytecie zostanie tymczasowo podniesiony do tego wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f9121-911">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread's priority will be temporarily raised to that of the calling thread.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-912">*Priorytet wątku o niższym priorytecie będącego właścicielem obiektu mutex z priorityinheritance nigdy nie powinien być modyfikowany przez wątek zewnętrzny podczas własności obiektu mutex.*</span><span class="sxs-lookup"><span data-stu-id="f9121-912">*The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-913">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-913">Parameters</span></span>

- <span data-ttu-id="f9121-914">**mutex_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-914">**mutex_ptr**</span></span>   <br><span data-ttu-id="f9121-915">Wskaźnik do wcześniej utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-915">Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="f9121-916">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="f9121-916">**wait_option**</span></span> <br><span data-ttu-id="f9121-917">Definiuje sposób zachowania usługi, jeśli element mutex jest już własnością innego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-917">Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="f9121-918">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9121-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="f9121-919">**TX_NO_WAIT** (0x00000000) — wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9121-919">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="f9121-920">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z inicjacji.*</span><span class="sxs-lookup"><span data-stu-id="f9121-920">*This is the only valid option if the service is called from Initialization.*</span></span>
  - <span data-ttu-id="f9121-921">**TX_WAIT_FOREVER** wartość limitu czasu (0xffffffff) — wybranie **TX_WAIT_FOREVER** powoduje, że wątek wywołujący zawiesza się nieokreślony czas do momentu udostępnienia elementu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-921">**TX_WAIT_FOREVER** timeout value (0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until the mutex is available.</span></span>
  - <span data-ttu-id="f9121-922">wartość limitu czasu (0x00000001 przez 0xFFFFFFFE) — wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-922">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-923">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-923">Return Values</span></span>

- <span data-ttu-id="f9121-924">**TX_SUCCESS** (0x00) pomyślna operacja pobrania obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-924">**TX_SUCCESS** (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="f9121-925">Element mutex **TX_DELETED** (0x01) został usunięty podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-925">**TX_DELETED** (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="f9121-926">Usługa **TX_NOT_AVAILABLE** (0x1D) nie mogła pobrać własności obiektu mutex w określonym czasie, aby czekać.</span><span class="sxs-lookup"><span data-stu-id="f9121-926">**TX_NOT_AVAILABLE** (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="f9121-927">Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-927">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="f9121-928">**TX_MUTEX_ERROR** (0X1C) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="f9121-928">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="f9121-929">**TX_WAIT_ERROR** (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-929">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>
- <span data-ttu-id="f9121-930">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-930">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-931">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-931">Allowed From</span></span>

<span data-ttu-id="f9121-932">Inicjowanie i wątki oraz czasomierze</span><span class="sxs-lookup"><span data-stu-id="f9121-932">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-933">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-933">Preemption Possible</span></span>

<span data-ttu-id="f9121-934">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-934">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-935">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-935">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="f9121-936">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-936">See Also</span></span>

- <span data-ttu-id="f9121-937">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="f9121-937">tx_mutex_create</span></span>
- <span data-ttu-id="f9121-938">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-938">tx_mutex_delete</span></span>
- <span data-ttu-id="f9121-939">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-939">tx_mutex_info_get</span></span>
- <span data-ttu-id="f9121-940">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-940">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="f9121-941">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-941">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-942">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-942">tx_mutex_prioritize</span></span>
- <span data-ttu-id="f9121-943">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="f9121-943">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="f9121-944">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-944">tx_mutex_info_get</span></span>

<span data-ttu-id="f9121-945">Pobierz informacje o muteksie</span><span class="sxs-lookup"><span data-stu-id="f9121-945">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-946">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-946">Prototype</span></span>

```c
UINT tx_mutex_info_get(
    TX_MUTEX *mutex_ptr, 
    CHAR **name,
    ULONG *count, 
    TX_THREAD **owner,
    TX_THREAD **first_suspended,
    ULONG *suspended_count, 
    TX_MUTEX **next_mutex);
```

### <a name="description"></a><span data-ttu-id="f9121-947">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-947">Description</span></span>

<span data-ttu-id="f9121-948">Ta usługa pobiera informacje z określonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-948">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-949">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-949">Parameters</span></span>

- <span data-ttu-id="f9121-950">**mutex_ptr** Wskaźnik do bloku sterowania muteksem.</span><span class="sxs-lookup"><span data-stu-id="f9121-950">**mutex_ptr** Pointer to mutex control block.</span></span>
- <span data-ttu-id="f9121-951">**Nazwa** Wskaźnik do miejsca docelowego dla wskaźnika do nazwy obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-951">**name** Pointer to destination for the pointer to the mutex's name.</span></span>
- <span data-ttu-id="f9121-952">**Liczba** Wskaźnik do miejsca docelowego dla liczby własności obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-952">**count** Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="f9121-953">**właściciel** Wskaźnik do miejsca docelowego dla wskaźnika wątku będącego właścicielem.</span><span class="sxs-lookup"><span data-stu-id="f9121-953">**owner** Pointer to destination for the owning thread's pointer.</span></span>
- <span data-ttu-id="f9121-954">**first_suspended** Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tego elementu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-954">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="f9121-955">**suspended_count** Wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-955">**suspended_count** Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="f9121-956">**next_mutex** Wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-956">**next_mutex** Pointer to destination for the pointer of the next created mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-957">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-957">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-958">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-958">Return Values</span></span>

- <span data-ttu-id="f9121-959">**TX_SUCCESS** (0X00) pomyślne pobranie informacji o mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-959">**TX_SUCCESS** (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="f9121-960">**TX_MUTEX_ERROR** (0X1C) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="f9121-960">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-961">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-961">Allowed From</span></span>

<span data-ttu-id="f9121-962">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-962">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-963">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-963">Preemption Possible</span></span>

<span data-ttu-id="f9121-964">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-964">No</span></span>

<span data-ttu-id="f9121-965">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="f9121-965">**Example**</span></span>

```c
TX_MUTEX my_mutex;
CHAR *name;
ULONG count;
TX_THREAD *owner;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_MUTEX *next_mutex;
UINT status;

/* Retrieve information about the previously created
mutex "my_mutex." */
status = tx_mutex_info_get(&my_mutex, &name,
    &count, &owner,
    &first_suspended, &suspended_count,
    &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-966">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-966">See Also</span></span>

- <span data-ttu-id="f9121-967">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="f9121-967">tx_mutex_create</span></span>
- <span data-ttu-id="f9121-968">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-968">tx_mutex_delete</span></span>
- <span data-ttu-id="f9121-969">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="f9121-969">tx_mutex_get</span></span>
- <span data-ttu-id="f9121-970">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-970">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="f9121-971">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-971">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-972">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-972">tx_mutex_prioritize</span></span>
- <span data-ttu-id="f9121-973">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="f9121-973">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="f9121-974">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-974">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="f9121-975">Pobierz informacje o wydajności muteksu</span><span class="sxs-lookup"><span data-stu-id="f9121-975">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-976">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-976">Prototype</span></span>

```c
UINT tx_mutex_performance_info_get(
    TX_MUTEX *mutex_ptr, 
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="f9121-977">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-977">Description</span></span>

<span data-ttu-id="f9121-978">Ta usługa pobiera informacje o wydajności dotyczące określonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-978">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-979">*Biblioteka i aplikacja ThreadX muszą być kompilowane przy użyciu*  \* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined do zwrócenia informacji o wydajności przez tę usługę \*</span><span class="sxs-lookup"><span data-stu-id="f9121-979">*The ThreadX library and application must be built with* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-980">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-980">Parameters</span></span>

- <span data-ttu-id="f9121-981">**mutex_ptr** Wskaźnik do wcześniej utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-981">**mutex_ptr** Pointer to previously created mutex.</span></span>
- <span data-ttu-id="f9121-982">**umieszcza** Wskaźnik do miejsca docelowego dla liczby żądań PUT wykonanych dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-982">**puts** Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="f9121-983">**Pobiera** Wskaźnik do miejsca docelowego dla liczby żądań GET wykonanych dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-983">**gets** Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="f9121-984">**zawieszenie** Wskaźnik do miejsca docelowego dla liczby elementów mutex wątku Get zawieszeń dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-984">**suspensions** Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="f9121-985">**limity czasu** Wskaźnik do miejsca docelowego dla liczby przekroczeń limitu czasu zawieszenia dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-985">**timeouts** Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="f9121-986">**Inversions** Wskaźnik do miejsca docelowego dla liczby wersji priorytetu wątku dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-986">**inversions** Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="f9121-987">**dziedziczenia** Wskaźnik do miejsca docelowego dla liczby operacji dziedziczenia priorytetu wątku dla tego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-987">**inheritances** Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-988">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-988">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-989">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-989">Return Values</span></span>

- <span data-ttu-id="f9121-990">**TX_SUCCESS** (0x00) pobieranie pomyślnej wydajności obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-990">**TX_SUCCESS** (0x00) Successful mutex performance get.</span></span>
- <span data-ttu-id="f9121-991">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="f9121-991">**TX_PTR_ERROR** (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="f9121-992">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-992">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-993">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-993">Allowed From</span></span>

<span data-ttu-id="f9121-994">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-994">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-995">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-995">Example</span></span>

```c
TX_MUTEX my_mutex;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on the previously created
mutex. */
status = tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
    &suspensions, &timeouts, &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-996">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-996">See Also</span></span>

- <span data-ttu-id="f9121-997">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="f9121-997">tx_mutex_create</span></span>
- <span data-ttu-id="f9121-998">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-998">tx_mutex_delete</span></span>
- <span data-ttu-id="f9121-999">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="f9121-999">tx_mutex_get</span></span>
- <span data-ttu-id="f9121-1000">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1000">tx_mutex_info_get</span></span>
- <span data-ttu-id="f9121-1001">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1001">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1002">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1002">tx_mutex_prioritize</span></span>
- <span data-ttu-id="f9121-1003">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1003">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="f9121-1004">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1004">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="f9121-1005">Pobierz informacje o wydajności systemu muteksu</span><span class="sxs-lookup"><span data-stu-id="f9121-1005">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1006">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1006">Prototype</span></span>

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="f9121-1007">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1007">Description</span></span>

<span data-ttu-id="f9121-1008">Ta usługa pobiera informacje o wydajności wszystkich muteksów w systemie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1008">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-1009">Aby można było zwracać informacje o wydajności *, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *zdefiniowanej dla tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1009">*The ThreadX library and application must be built with* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1010">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1010">Parameters</span></span>

- <span data-ttu-id="f9121-1011">**umieszcza** Wskaźnik do miejsca docelowego dla łącznej liczby żądań PUT wykonanych dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1011">**puts** Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="f9121-1012">**Pobiera** Wskaźnik do miejsca docelowego dla łącznej liczby żądań GET wykonanych dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1012">**gets** Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="f9121-1013">**zawieszenie** Wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń elementu mutex wątku dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1013">**suspensions** Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="f9121-1014">**limity czasu** Wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszania dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1014">**timeouts** Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="f9121-1015">**Inversions** Wskaźnik do miejsca docelowego dla łącznej liczby niewersji priorytetu wątku dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1015">**inversions** Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="f9121-1016">**dziedziczenia** Wskaźnik do miejsca docelowego dla łącznej liczby operacji dziedziczenia priorytetu wątku dla wszystkich muteksów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1016">**inheritances** Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1017">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1017">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1018">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1018">Return Values</span></span>

- <span data-ttu-id="f9121-1019">**TX_SUCCESS** (0X00) pomyślne pobieranie wydajności systemu muteksu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1019">**TX_SUCCESS** (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="f9121-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1021">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1021">Allowed From</span></span>

<span data-ttu-id="f9121-1022">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1022">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1023">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1023">Example</span></span>

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on all previously created
mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts,
    &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1024">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1024">See Also</span></span>

- <span data-ttu-id="f9121-1025">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1025">tx_mutex_create</span></span>
- <span data-ttu-id="f9121-1026">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1026">tx_mutex_delete</span></span>
- <span data-ttu-id="f9121-1027">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1027">tx_mutex_get</span></span>
- <span data-ttu-id="f9121-1028">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1028">tx_mutex_info_get</span></span>
- <span data-ttu-id="f9121-1029">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1029">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="f9121-1030">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1030">tx_mutex_prioritize</span></span>
- <span data-ttu-id="f9121-1031">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1031">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="f9121-1032">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1032">tx_mutex_prioritize</span></span>

<span data-ttu-id="f9121-1033">Ustawianie priorytetów listy zawieszeń muteksu</span><span class="sxs-lookup"><span data-stu-id="f9121-1033">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1034">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1034">Prototype</span></span>

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-1035">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1035">Description</span></span>

<span data-ttu-id="f9121-1036">Ta usługa umieszcza wątek o najwyższym priorytecie na własność obiektu mutex na początku listy zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-1036">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="f9121-1037">Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="f9121-1037">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1038">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1038">Parameters</span></span>

- <span data-ttu-id="f9121-1039">**mutex_ptr** Wskaźnik do wcześniej utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-1039">**mutex_ptr** Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1040">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1040">Return Values</span></span>

- <span data-ttu-id="f9121-1041">**TX_SUCCESS** (0x00) pomyślna priorytetyzacja obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-1041">**TX_SUCCESS** (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="f9121-1042">**TX_MUTEX_ERROR** (0X1C) Nieprawidłowy wskaźnik muteksu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1042">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1043">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1043">Allowed From</span></span>

<span data-ttu-id="f9121-1044">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1044">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1045">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1045">Preemption Possible</span></span>

<span data-ttu-id="f9121-1046">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-1046">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1047">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1047">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Ensure that the highest priority thread will receive
ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_mutex_put call that releases ownership of the
mutex will give ownership to this thread and wake it
up. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1048">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1048">See Also</span></span>

- <span data-ttu-id="f9121-1049">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1049">tx_mutex_create</span></span>
- <span data-ttu-id="f9121-1050">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1050">tx_mutex_delete</span></span>
- <span data-ttu-id="f9121-1051">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1051">tx_mutex_get</span></span>
- <span data-ttu-id="f9121-1052">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1052">tx_mutex_info_get</span></span>
- <span data-ttu-id="f9121-1053">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1053">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="f9121-1054">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1054">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1055">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1055">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="f9121-1056">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1056">tx_mutex_put</span></span>

<span data-ttu-id="f9121-1057">Zwolnij własność elementu mutex</span><span class="sxs-lookup"><span data-stu-id="f9121-1057">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1058">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1058">Prototype</span></span>

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-1059">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1059">Description</span></span>

<span data-ttu-id="f9121-1060">Ta usługa zmniejsza liczbę własności określonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-1060">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="f9121-1061">Jeśli liczba własności wynosi zero, element mutex zostanie udostępniony.</span><span class="sxs-lookup"><span data-stu-id="f9121-1061">If the ownership count is zero, the mutex is made available.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1062">*W przypadku wybrania dziedziczenia priorytetu podczas tworzenia obiektu mutex priorytet zwalnianego wątku zostanie przywrócony do priorytetu, który miał po raz pierwszy uzyskać własność obiektu mutex. Wszystkie inne zmiany priorytetu w wątku zwalniania mogą być cofnięte.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1062">*If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex. Any other priority changes made to the releasing thread during ownership of the mutex may be undone.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1063">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1063">Parameters</span></span>
- <span data-ttu-id="f9121-1064">mutex_ptr wskaźnik do wcześniej utworzonego obiektu mutex.</span><span class="sxs-lookup"><span data-stu-id="f9121-1064">mutex_ptr Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1065">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1065">Return Values</span></span>
- <span data-ttu-id="f9121-1066">**TX_SUCCESS** (0X00) pomyślne wydanie muteksu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1066">**TX_SUCCESS** (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="f9121-1067">Element mutex **TX_NOT_OWNED** (0x1E) nie należy do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f9121-1067">**TX_NOT_OWNED** (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="f9121-1068">**TX_MUTEX_ERROR** (0X1C) Nieprawidłowy wskaźnik do elementu MUTEX.</span><span class="sxs-lookup"><span data-stu-id="f9121-1068">**TX_MUTEX_ERROR** (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="f9121-1069">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-1069">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1070">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1070">Allowed From</span></span>

<span data-ttu-id="f9121-1071">Inicjowanie i wątki oraz czasomierze</span><span class="sxs-lookup"><span data-stu-id="f9121-1071">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1072">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1072">Preemption Possible</span></span>

<span data-ttu-id="f9121-1073">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-1073">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1074">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1074">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1075">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1075">See Also</span></span>

- <span data-ttu-id="f9121-1076">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1076">tx_mutex_create</span></span>
- <span data-ttu-id="f9121-1077">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1077">tx_mutex_delete</span></span>
- <span data-ttu-id="f9121-1078">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1078">tx_mutex_get</span></span>
- <span data-ttu-id="f9121-1079">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1079">tx_mutex_info_get</span></span>
- <span data-ttu-id="f9121-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1080">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="f9121-1081">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1081">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1082">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1082">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="f9121-1083">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1083">tx_queue_create</span></span>

<span data-ttu-id="f9121-1084">Utwórz kolejkę komunikatów</span><span class="sxs-lookup"><span data-stu-id="f9121-1084">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1085">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1085">Prototype</span></span>

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a><span data-ttu-id="f9121-1086">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1086">Description</span></span>

<span data-ttu-id="f9121-1087">Ta usługa tworzy kolejkę komunikatów, która jest zwykle używana do komunikacji międzywątkowej.</span><span class="sxs-lookup"><span data-stu-id="f9121-1087">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="f9121-1088">Całkowita liczba komunikatów jest obliczana na podstawie określonego rozmiaru komunikatu i całkowitej liczby bajtów w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1088">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1089">*Jeśli łączna liczba bajtów określona w obszarze pamięci kolejki nie jest równo podzielna przez określony rozmiar komunikatu, pozostałe bajty w obszarze pamięci nie są używane.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1089">*If the total number of bytes specified in the queue's memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1090">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1090">Parameters</span></span>

- <span data-ttu-id="f9121-1091">**queue_ptr** Wskaźnik do bloku sterowania kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1091">**queue_ptr** Pointer to a message queue control block.</span></span>
- <span data-ttu-id="f9121-1092">**name_ptr** Wskaźnik na nazwę kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1092">**name_ptr** Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="f9121-1093">**message_size** Określa rozmiar każdej wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1093">**message_size** Specifies the size of each message in the queue.</span></span> <span data-ttu-id="f9121-1094">Rozmiary komunikatów mieszczą się w zakresie od 1 32-bitowego wyrazu do 16 32-bitowych wyrazów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1094">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="f9121-1095">Prawidłowe opcje rozmiaru komunikatu to wartości numeryczne z przestawu od 1 do 16 włącznie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1095">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="f9121-1096">**queue_start** Adres początkowy kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1096">**queue_start** Starting address of the message queue.</span></span> <span data-ttu-id="f9121-1097">Adres początkowy musi być wyrównany do rozmiaru typu danych ULONG.</span><span class="sxs-lookup"><span data-stu-id="f9121-1097">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="f9121-1098">**queue_size** Łączna liczba bajtów dostępnych dla kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1098">**queue_size** Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1099">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1099">Return Values</span></span>

- <span data-ttu-id="f9121-1100">**TX_SUCCESS** (0X00) pomyślne utworzenie kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1100">**TX_SUCCESS** (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="f9121-1101">**TX_QUEUE_ERROR** (0X09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1101">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="f9121-1102">Wskaźnik ma wartość NULL lub kolejka została już utworzona.</span><span class="sxs-lookup"><span data-stu-id="f9121-1102">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="f9121-1103">**TX_PTR_ERROR** (0X03) nieprawidłowy adres początkowy kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1103">**TX_PTR_ERROR** (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="f9121-1104">**TX_SIZE_ERROR** (0X05) rozmiar kolejki komunikatów jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f9121-1104">**TX_SIZE_ERROR** (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="f9121-1105">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-1105">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1106">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1106">Allowed From</span></span>

<span data-ttu-id="f9121-1107">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-1107">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1108">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1108">Preemption Possible</span></span>

<span data-ttu-id="f9121-1109">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-1109">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1110">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Create a message queue whose total size is 2000 bytes
starting at address 0x300000. Each message in this
queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
    4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
for storing 125 messages (2000 bytes/ 16 bytes per
message). */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1111">See Also</span></span>

- <span data-ttu-id="f9121-1112">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1112">tx_queue_delete</span></span>
- <span data-ttu-id="f9121-1113">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1113">tx_queue_flush</span></span>
- <span data-ttu-id="f9121-1114">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1114">tx_queue_front_send</span></span>
- <span data-ttu-id="f9121-1115">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1115">tx_queue_info_get</span></span>
- <span data-ttu-id="f9121-1116">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1116">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="f9121-1117">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1117">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1118">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1118">tx_queue_prioritize</span></span>
- <span data-ttu-id="f9121-1119">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1119">tx_queue_receive</span></span>
- <span data-ttu-id="f9121-1120">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1120">tx_queue_send</span></span>
- <span data-ttu-id="f9121-1121">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1121">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="f9121-1122">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1122">tx_queue_delete</span></span>

<span data-ttu-id="f9121-1123">Usuń kolejkę komunikatów</span><span class="sxs-lookup"><span data-stu-id="f9121-1123">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1124">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1124">Prototype</span></span>

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-1125">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1125">Description</span></span>

<span data-ttu-id="f9121-1126">Ta usługa usuwa określoną kolejkę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1126">This service deletes the specified message queue.</span></span> <span data-ttu-id="f9121-1127">Wszystkie wątki zawieszają się, dopóki komunikat z tej kolejki zostanie wznowiony i nastąpi TX_DELETED stanu powrotu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1127">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="f9121-1128">*Aplikacja musi upewnić się, że wszystkie wywołania zwrotne powiadomień o wysłaniu dla tej kolejki zostaną zakończone (lub wyłączone) przed usunięciem kolejki. Ponadto aplikacja musi uniemożliwić wszelkie przyszłe użycie usuniętej kolejki.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1128">*The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue. In addition, the application must prevent any future use of a deleted queue.*</span></span> <br><br><span data-ttu-id="f9121-1129">*Jest również odpowiedzialna za zarządzanie obszarem pamięci skojarzonym z kolejką, która jest dostępna po zakończeniu tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1129">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1130">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1130">Parameters</span></span>

- <span data-ttu-id="f9121-1131">**queue_ptr** Wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1131">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1132">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1132">Return Values</span></span>

- <span data-ttu-id="f9121-1133">Pomyślnie usunięto kolejkę komunikatów **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-1133">**TX_SUCCESS** (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="f9121-1134">**TX_QUEUE_ERROR** (0X09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1134">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="f9121-1135">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-1135">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1136">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1136">Allowed From</span></span>

<span data-ttu-id="f9121-1137">Wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-1137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1138">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1138">Preemption Possible</span></span>

<span data-ttu-id="f9121-1139">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-1139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1140">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1140">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Delete entire message queue. Assume that the queue
has already been created with a call to
tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1141">See Also</span></span>

- <span data-ttu-id="f9121-1142">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1142">tx_queue_create</span></span>
- <span data-ttu-id="f9121-1143">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1143">tx_queue_flush</span></span>
- <span data-ttu-id="f9121-1144">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1144">tx_queue_front_send</span></span>
- <span data-ttu-id="f9121-1145">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1145">tx_queue_info_get</span></span>
- <span data-ttu-id="f9121-1146">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1146">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="f9121-1147">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1147">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1148">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1148">tx_queue_prioritize</span></span>
- <span data-ttu-id="f9121-1149">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1149">tx_queue_receive</span></span>
- <span data-ttu-id="f9121-1150">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1150">tx_queue_send</span></span>
- <span data-ttu-id="f9121-1151">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1151">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="f9121-1152">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1152">tx_queue_flush</span></span>

<span data-ttu-id="f9121-1153">Puste wiadomości w kolejce komunikatów</span><span class="sxs-lookup"><span data-stu-id="f9121-1153">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1154">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1154">Prototype</span></span>

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-1155">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1155">Description</span></span>

<span data-ttu-id="f9121-1156">Ta usługa usuwa wszystkie komunikaty przechowywane w określonej kolejce komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1156">This service deletes all messages stored in the specified message queue.</span></span>

<span data-ttu-id="f9121-1157">Jeśli kolejka jest pełna, komunikaty wszystkich zawieszonych wątków są odrzucane.</span><span class="sxs-lookup"><span data-stu-id="f9121-1157">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="f9121-1158">Każdy zawieszony wątek zostanie wznowiony ze stanem powrotu, który wskazuje, że wiadomość została wysłana pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1158">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="f9121-1159">Jeśli kolejka jest pusta, ta usługa nie robi nic.</span><span class="sxs-lookup"><span data-stu-id="f9121-1159">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1160">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1160">Parameters</span></span>

- <span data-ttu-id="f9121-1161">**queue_ptr** Wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1161">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1162">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1162">Return Values</span></span>

- <span data-ttu-id="f9121-1163">Opróżnianie kolejki komunikatów **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-1163">**TX_SUCCESS** (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="f9121-1164">**TX_QUEUE_ERROR** (0X09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1164">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1165">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1165">Allowed From</span></span>

<span data-ttu-id="f9121-1166">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1166">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1167">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1167">Preemption Possible</span></span>

<span data-ttu-id="f9121-1168">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-1168">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1169">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1169">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Flush out all pending messages in the specified message
queue. Assume that the queue has already been created
with a call to tx_queue_create. */
status = tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
empty. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1170">See Also</span></span>

- <span data-ttu-id="f9121-1171">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1171">tx_queue_create</span></span>
- <span data-ttu-id="f9121-1172">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1172">tx_queue_delete</span></span>
- <span data-ttu-id="f9121-1173">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1173">tx_queue_front_send</span></span>
- <span data-ttu-id="f9121-1174">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1174">tx_queue_info_get</span></span>
- <span data-ttu-id="f9121-1175">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1175">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="f9121-1176">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1176">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1177">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1177">tx_queue_prioritize</span></span>
- <span data-ttu-id="f9121-1178">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1178">tx_queue_receive</span></span>
- <span data-ttu-id="f9121-1179">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1179">tx_queue_send</span></span>
- <span data-ttu-id="f9121-1180">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1180">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="f9121-1181">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1181">tx_queue_front_send</span></span>

<span data-ttu-id="f9121-1182">Wyślij wiadomość na przednią kolejkę</span><span class="sxs-lookup"><span data-stu-id="f9121-1182">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1183">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1183">Prototype</span></span>

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f9121-1184">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1184">Description</span></span>

<span data-ttu-id="f9121-1185">Ta usługa wysyła komunikat do lokalizacji frontonu określonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1185">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="f9121-1186">Wiadomość jest **kopiowana** na przód kolejki z obszaru pamięci określonego przez wskaźnik źródła.</span><span class="sxs-lookup"><span data-stu-id="f9121-1186">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1187">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1187">Parameters</span></span>

- <span data-ttu-id="f9121-1188">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-1188">**queue_ptr**</span></span> <br><span data-ttu-id="f9121-1189">Wskaźnik do bloku sterowania kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1189">Pointer to a message queue control block.</span></span>
- <span data-ttu-id="f9121-1190">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-1190">**source_ptr**</span></span> <br><span data-ttu-id="f9121-1191">Wskaźnik na komunikat.</span><span class="sxs-lookup"><span data-stu-id="f9121-1191">Pointer to the message.</span></span>
- <span data-ttu-id="f9121-1192">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="f9121-1192">**wait_option**</span></span>  <br><span data-ttu-id="f9121-1193">Definiuje, w jaki sposób działa usługa, jeśli kolejka komunikatów jest pełna.</span><span class="sxs-lookup"><span data-stu-id="f9121-1193">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="f9121-1194">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9121-1194">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="f9121-1195">**TX_NO_WAIT** (0x00000000) — wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1195">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="f9121-1196">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1196">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="f9121-1197">**TX_WAIT_FOREVER** (0xffffffff) — wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, w którym znajduje się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="f9121-1198">wartość limitu czasu (0x00000001 przez 0xFFFFFFFE) — wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma pozostać zawieszona podczas oczekiwania na pokój w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1198">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1199">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1199">Return Values</span></span>

- <span data-ttu-id="f9121-1200">**TX_SUCCESS** (0X00) pomyślnie wysłano komunikat.</span><span class="sxs-lookup"><span data-stu-id="f9121-1200">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="f9121-1201">Kolejka komunikatów **TX_DELETED** (0x01) została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1201">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="f9121-1202">Usługa **TX_QUEUE_FULL** (0x0B) nie mogła wysłać komunikatu, ponieważ kolejka była zapełniona przez czas oczekiwania przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="f9121-1202">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="f9121-1203">Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-1203">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="f9121-1204">**TX_QUEUE_ERROR** (0X09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1204">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="f9121-1205">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik źródła komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1205">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="f9121-1206">**TX_WAIT_ERROR** (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1206">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1207">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1207">Allowed From</span></span>

<span data-ttu-id="f9121-1208">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1208">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1209">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1209">Preemption Possible</span></span>

<span data-ttu-id="f9121-1210">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-1210">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1211">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1211">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to the front of "my_queue." Return
immediately, regardless of success. This wait
option is used for calls from initialization, timers,
and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
    TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
of the specified queue. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1212">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1212">See Also</span></span>

- <span data-ttu-id="f9121-1213">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1213">tx_queue_create</span></span>
- <span data-ttu-id="f9121-1214">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1214">tx_queue_delete</span></span>
- <span data-ttu-id="f9121-1215">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1215">tx_queue_flush</span></span>
- <span data-ttu-id="f9121-1216">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1216">tx_queue_info_get</span></span>
- <span data-ttu-id="f9121-1217">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1217">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="f9121-1218">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1218">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1219">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1219">tx_queue_prioritize</span></span>
- <span data-ttu-id="f9121-1220">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1220">tx_queue_receive</span></span>
- <span data-ttu-id="f9121-1221">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1221">tx_queue_send</span></span>
- <span data-ttu-id="f9121-1222">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1222">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="f9121-1223">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1223">tx_queue_info_get</span></span>

<span data-ttu-id="f9121-1224">Pobierz informacje o kolejce</span><span class="sxs-lookup"><span data-stu-id="f9121-1224">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1225">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1225">Prototype</span></span>

```c
UINT tx_queue_info_get(
    TX_QUEUE *queue_ptr, 
    CHAR **name,
    ULONG *enqueued, 
    ULONG *available_storage
    TX_THREAD **first_suspended, 
    ULONG *suspended_count,
    TX_QUEUE **next_queue);
```

### <a name="description"></a><span data-ttu-id="f9121-1226">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1226">Description</span></span>

<span data-ttu-id="f9121-1227">Ta usługa pobiera informacje o określonej kolejce komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1227">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1228">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1228">Parameters</span></span>

- <span data-ttu-id="f9121-1229">**queue_ptr** Wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1229">**queue_ptr** Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="f9121-1230">**Nazwa** Wskaźnik do miejsca docelowego dla wskaźnika do nazwy kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1230">**name** Pointer to destination for the pointer to the queue's name.</span></span>
- <span data-ttu-id="f9121-1231">w **kolejce** Wskaźnik do miejsca docelowego dla liczby komunikatów aktualnie znajdujących się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1231">**enqueued** Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="f9121-1232">**available_storage** Wskaźnik do miejsca docelowego dla liczby komunikatów, dla których w kolejce znajduje się obecnie miejsce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1232">**available_storage** Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="f9121-1233">**first_suspended** Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1233">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="f9121-1234">**suspended_count** Wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tej kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1234">**suspended_count** Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="f9121-1235">**next_queue** Wskaźnik do miejsca docelowego dla wskaźnika następnej utworzonej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1235">**next_queue** Pointer to destination for the pointer of the next created queue.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1236">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1236">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1237">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1237">Return Values</span></span>

- <span data-ttu-id="f9121-1238">Informacje dotyczące kolejki powiodło się **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-1238">**TX_SUCCESS** (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="f9121-1239">**TX_QUEUE_ERROR** (0X09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1239">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1240">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1240">Allowed From</span></span>

<span data-ttu-id="f9121-1241">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1241">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1242">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1242">Preemption Possible</span></span>

<span data-ttu-id="f9121-1243">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-1243">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1244">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1244">Example</span></span>

```c
TX_QUEUE my_queue;
CHAR *name;
ULONG enqueued;
ULONG available_storage;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_QUEUE *next_queue;
UINT status;

/* Retrieve information about the previously created
message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
    &enqueued, &available_storage,
    &first_suspended, &suspended_count,
    &next_queue);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1245">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1245">See Also</span></span>

- <span data-ttu-id="f9121-1246">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1246">tx_queue_create</span></span>
- <span data-ttu-id="f9121-1247">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1247">tx_queue_delete</span></span>
- <span data-ttu-id="f9121-1248">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1248">tx_queue_flush</span></span>
- <span data-ttu-id="f9121-1249">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1249">tx_queue_front_send</span></span>
- <span data-ttu-id="f9121-1250">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1250">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="f9121-1251">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1251">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1252">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1252">tx_queue_prioritize</span></span>
- <span data-ttu-id="f9121-1253">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1253">tx_queue_receive</span></span>
- <span data-ttu-id="f9121-1254">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1254">tx_queue_send</span></span>
- <span data-ttu-id="f9121-1255">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1255">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="f9121-1256">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1256">tx_queue_performance_info_get</span></span>

<span data-ttu-id="f9121-1257">Pobierz informacje o wydajności kolejki</span><span class="sxs-lookup"><span data-stu-id="f9121-1257">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1258">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1258">Prototype</span></span>

```c
UINT tx_queue_performance_info_get(
    TX_QUEUE *queue_ptr,
    ULONG *messages_sent, 
    ULONG *messages_received,
    ULONG *empty_suspensions, 
    ULONG *full_suspensions,
    ULONG *full_errors, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="f9121-1259">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1259">Description</span></span>

<span data-ttu-id="f9121-1260">Ta usługa pobiera informacje o wydajności określonej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1260">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-1261">*Biblioteka i aplikacja ThreadX muszą być kompilowane przy użyciu*  \* **TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined do zwrócenia informacji o wydajności przez tę usługę \*</span><span class="sxs-lookup"><span data-stu-id="f9121-1261">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1262">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1262">Parameters</span></span>

- <span data-ttu-id="f9121-1263">**queue_ptr** Wskaźnik do wcześniej utworzonej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1263">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="f9121-1264">**messages_sent** Wskaźnik do miejsca docelowego dla liczby żądań wysłania wykonanych dla tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1264">**messages_sent** Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="f9121-1265">**messages_received** Wskaźnik do miejsca docelowego dla liczby żądań odebrania wykonanych dla tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1265">**messages_received** Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="f9121-1266">**empty_suspensions** Wskaźnik do miejsca docelowego dla liczby pustych zawieszeń kolejki w tej kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1266">**empty_suspensions** Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="f9121-1267">**full_suspensions** Wskaźnik do miejsca docelowego dla liczby pełnych zawieszeń kolejki w tej kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1267">**full_suspensions** Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="f9121-1268">**full_errors** Wskaźnik do miejsca docelowego dla liczby pełnych błędów kolejki w tej kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1268">**full_errors** Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="f9121-1269">**limity czasu** Wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia wątku w tej kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1269">**timeouts** Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1270">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1270">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1271">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1271">Return Values</span></span>

- <span data-ttu-id="f9121-1272">Pomyślna wydajność kolejki **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-1272">**TX_SUCCESS** (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="f9121-1273">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1273">**TX_PTR_ERROR** (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="f9121-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1275">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1275">Allowed From</span></span>

<span data-ttu-id="f9121-1276">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1277">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1277">Example</span></span>

```c
TX_QUEUE my_queue;
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on the previously created
queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1278">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1278">See Also</span></span>

- <span data-ttu-id="f9121-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1279">tx_queue_create</span></span>
- <span data-ttu-id="f9121-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1280">tx_queue_delete</span></span>
- <span data-ttu-id="f9121-1281">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1281">tx_queue_flush</span></span>
- <span data-ttu-id="f9121-1282">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1282">tx_queue_front_send</span></span>
- <span data-ttu-id="f9121-1283">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1283">tx_queue_info_get</span></span>
- <span data-ttu-id="f9121-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="f9121-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1286">tx_queue_receive</span></span>
- <span data-ttu-id="f9121-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1287">tx_queue_send</span></span>
- <span data-ttu-id="f9121-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="f9121-1289">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1289">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="f9121-1290">Pobierz informacje o wydajności systemu kolejkowania</span><span class="sxs-lookup"><span data-stu-id="f9121-1290">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1291">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1291">Prototype</span></span>

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="f9121-1292">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1292">Description</span></span>

<span data-ttu-id="f9121-1293">Ta usługa pobiera informacje o wydajności wszystkich kolejek w systemie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1293">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-1294">*Biblioteka i aplikacja ThreadX muszą być kompilowane przy użyciu*  \* **TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined do zwrócenia informacji o wydajności przez tę usługę \*</span><span class="sxs-lookup"><span data-stu-id="f9121-1294">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1295">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1295">Parameters</span></span>

- <span data-ttu-id="f9121-1296">**messages_sent** Wskaźnik do miejsca docelowego dla łącznej liczby żądań wysłania wykonanych na wszystkich kolejkach.</span><span class="sxs-lookup"><span data-stu-id="f9121-1296">**messages_sent** Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="f9121-1297">**messages_received** Wskaźnik do miejsca docelowego dla łącznej liczby żądań odbioru wykonanych dla wszystkich kolejek.</span><span class="sxs-lookup"><span data-stu-id="f9121-1297">**messages_received** Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="f9121-1298">**empty_suspensions** Wskaźnik do miejsca docelowego dla łącznej liczby pustych zawieszeń kolejki we wszystkich kolejkach.</span><span class="sxs-lookup"><span data-stu-id="f9121-1298">**empty_suspensions** Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="f9121-1299">**full_suspensions** Wskaźnik do miejsca docelowego dla łącznej liczby pełnych zawieszeń kolejki we wszystkich kolejkach.</span><span class="sxs-lookup"><span data-stu-id="f9121-1299">**full_suspensions** Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="f9121-1300">**full_errors** Wskaźnik do miejsca docelowego dla łącznej liczby pełnych błędów kolejki dla wszystkich kolejek.</span><span class="sxs-lookup"><span data-stu-id="f9121-1300">**full_errors** Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="f9121-1301">**limity czasu** Wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia wątku we wszystkich kolejkach.</span><span class="sxs-lookup"><span data-stu-id="f9121-1301">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1302">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1302">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

<span data-ttu-id="f9121-1303">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="f9121-1303">**Return Values**</span></span>

- <span data-ttu-id="f9121-1304">**TX_SUCCESS** (0X00) pomyślne pobieranie wydajności systemu z kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1304">**TX_SUCCESS** (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="f9121-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1306">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1306">Allowed From</span></span>

<span data-ttu-id="f9121-1307">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1307">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1308">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1308">Example</span></span>

```c
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on all previously created
queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1309">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1309">See Also</span></span>

- <span data-ttu-id="f9121-1310">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1310">tx_queue_create</span></span>
- <span data-ttu-id="f9121-1311">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1311">tx_queue_delete</span></span>
- <span data-ttu-id="f9121-1312">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1312">tx_queue_flush</span></span>
- <span data-ttu-id="f9121-1313">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1313">tx_queue_front_send</span></span>
- <span data-ttu-id="f9121-1314">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1314">tx_queue_info_get</span></span>
- <span data-ttu-id="f9121-1315">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1315">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="f9121-1316">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1316">tx_queue_prioritize</span></span>
- <span data-ttu-id="f9121-1317">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1317">tx_queue_receive</span></span>
- <span data-ttu-id="f9121-1318">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1318">tx_queue_send</span></span>
- <span data-ttu-id="f9121-1319">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1319">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="f9121-1320">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1320">tx_queue_prioritize</span></span>

<span data-ttu-id="f9121-1321">Ustawianie priorytetu listy zawieszania kolejki</span><span class="sxs-lookup"><span data-stu-id="f9121-1321">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1322">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1322">Prototype</span></span>

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-1323">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1323">Description</span></span>

<span data-ttu-id="f9121-1324">Ta usługa umieszcza wątek o najwyższym priorytecie dla komunikatu (lub umieszcza komunikat) w tej kolejce na początku listy zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-1324">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span>

<span data-ttu-id="f9121-1325">Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="f9121-1325">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1326">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1326">Parameters</span></span>

- <span data-ttu-id="f9121-1327">**queue_ptr** Wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1327">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1328">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1328">Return Values</span></span>

- <span data-ttu-id="f9121-1329">**TX_SUCCESS** (0x00) pomyślna priorytetyzacja kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1329">**TX_SUCCESS** (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="f9121-1330">**TX_QUEUE_ERROR** (0X09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1330">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1331">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1331">Allowed From</span></span>

<span data-ttu-id="f9121-1332">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1332">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1333">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1333">Preemption Possible</span></span>

<span data-ttu-id="f9121-1334">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-1334">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1335">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1335">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;

/* Ensure that the highest priority thread will receive
the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_queue_send or tx_queue_front_send call made
to this queue will wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1336">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1336">See Also</span></span>

- <span data-ttu-id="f9121-1337">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1337">tx_queue_create</span></span>
- <span data-ttu-id="f9121-1338">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1338">tx_queue_delete</span></span>
- <span data-ttu-id="f9121-1339">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1339">tx_queue_flush</span></span>
- <span data-ttu-id="f9121-1340">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1340">tx_queue_front_send</span></span>
- <span data-ttu-id="f9121-1341">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1341">tx_queue_info_get</span></span>
- <span data-ttu-id="f9121-1342">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1342">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="f9121-1343">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1343">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1344">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1344">tx_queue_receive</span></span>
- <span data-ttu-id="f9121-1345">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1345">tx_queue_send</span></span>
- <span data-ttu-id="f9121-1346">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1346">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="f9121-1347">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1347">tx_queue_receive</span></span>

<span data-ttu-id="f9121-1348">Pobierz komunikat z kolejki komunikatów</span><span class="sxs-lookup"><span data-stu-id="f9121-1348">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1349">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1349">Prototype</span></span>

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f9121-1350">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1350">Description</span></span>

<span data-ttu-id="f9121-1351">Ta usługa pobiera komunikat z określonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1351">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="f9121-1352">Pobrany komunikat jest **kopiowany** z kolejki do obszaru pamięci określonego przez wskaźnik docelowy.</span><span class="sxs-lookup"><span data-stu-id="f9121-1352">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="f9121-1353">Ten komunikat zostanie następnie usunięty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1353">That message is then removed from the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-1354">*Określony obszar pamięci docelowej musi być wystarczająco duży, aby pomieścić komunikat; oznacza to, że miejsce docelowe komunikatu wskazywane przez*  \* **destination_ptr** _ _must być co najmniej tak duże, jak rozmiar komunikatu dla tej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1354">*The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by* \***destination_ptr** _ _must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="f9121-1355">W przeciwnym razie, jeśli miejsce docelowe nie jest wystarczająco duże, uszkodzenie pamięci występuje w następującym obszarze pamięci. \*</span><span class="sxs-lookup"><span data-stu-id="f9121-1355">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1356">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1356">Parameters</span></span>

- <span data-ttu-id="f9121-1357">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-1357">**queue_ptr**</span></span> <br><span data-ttu-id="f9121-1358">Wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1358">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="f9121-1359">**destination_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-1359">**destination_ptr**</span></span> <br><span data-ttu-id="f9121-1360">Lokalizacja, w której ma zostać skopiowana wiadomość.</span><span class="sxs-lookup"><span data-stu-id="f9121-1360">Location of where to copy the message.</span></span>
- <span data-ttu-id="f9121-1361">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="f9121-1361">**wait_option**</span></span> <br><span data-ttu-id="f9121-1362">Definiuje, w jaki sposób działa usługa, jeśli kolejka komunikatów jest pusta.</span><span class="sxs-lookup"><span data-stu-id="f9121-1362">Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="f9121-1363">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9121-1363">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="f9121-1364">**TX_NO_WAIT** (0x00000000) — wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1364">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="f9121-1365">Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-1365">This is the only valid option if the service is called from a non-thread; e.g.,  Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="f9121-1366">**TX_WAIT_FOREVER** (0xffffffff) — wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu udostępnienia komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>
  - <span data-ttu-id="f9121-1367">wartość limitu czasu (0x00000001 przez 0xFFFFFFFE) — wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać zawieszona podczas oczekiwania na komunikat.</span><span class="sxs-lookup"><span data-stu-id="f9121-1367">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1368">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1368">Return Values</span></span>

- <span data-ttu-id="f9121-1369">**TX_SUCCESS** (0X00) pomyślne pobranie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1369">**TX_SUCCESS** (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="f9121-1370">Kolejka komunikatów **TX_DELETED** (0x01) została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1370">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="f9121-1371">Usługa **TX_QUEUE_EMPTY** (0x0A) nie może pobrać komunikatu, ponieważ kolejka była pusta przez czas oczekiwania przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="f9121-1371">**TX_QUEUE_EMPTY** (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="f9121-1372">Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-1372">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="f9121-1373">**TX_QUEUE_ERROR** (0X09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1373">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="f9121-1374">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik docelowy dla komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1374">**TX_PTR_ERROR** (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="f9121-1375">**TX_WAIT_ERROR** (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1375">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1376">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1376">Allowed From</span></span>

<span data-ttu-id="f9121-1377">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1377">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1378">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1378">Preemption Possible</span></span>

<span data-ttu-id="f9121-1379">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-1379">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1380">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1380">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
empty, suspend until a message is present. Note that
this suspension is only possible from application
threads. */
status = tx_queue_receive(&my_queue, my_message,
    TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
"my_message." */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1381">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1381">See Also</span></span>

- <span data-ttu-id="f9121-1382">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1382">tx_queue_create</span></span>
- <span data-ttu-id="f9121-1383">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1383">tx_queue_delete</span></span>
- <span data-ttu-id="f9121-1384">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1384">tx_queue_flush</span></span>
- <span data-ttu-id="f9121-1385">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1385">tx_queue_front_send</span></span>
- <span data-ttu-id="f9121-1386">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1386">tx_queue_info_get</span></span>
- <span data-ttu-id="f9121-1387">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1387">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="f9121-1388">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1388">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1389">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1389">tx_queue_prioritize</span></span>
- <span data-ttu-id="f9121-1390">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1390">tx_queue_send</span></span>
- <span data-ttu-id="f9121-1391">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1391">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="f9121-1392">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1392">tx_queue_send</span></span>

<span data-ttu-id="f9121-1393">Wyślij komunikat do kolejki komunikatów</span><span class="sxs-lookup"><span data-stu-id="f9121-1393">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1394">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1394">Prototype</span></span>

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f9121-1395">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1395">Description</span></span>

<span data-ttu-id="f9121-1396">Ta usługa wysyła komunikat do określonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1396">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="f9121-1397">Wysłany komunikat jest **kopiowany** do kolejki z obszaru pamięci określonego przez wskaźnik źródła.</span><span class="sxs-lookup"><span data-stu-id="f9121-1397">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1398">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1398">Parameters</span></span>
- <span data-ttu-id="f9121-1399">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-1399">**queue_ptr**</span></span> <br><span data-ttu-id="f9121-1400">Wskaźnik do wcześniej utworzonej kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1400">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="f9121-1401">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-1401">**source_ptr**</span></span> <br><span data-ttu-id="f9121-1402">Wskaźnik na komunikat.</span><span class="sxs-lookup"><span data-stu-id="f9121-1402">Pointer to the message.</span></span>
- <span data-ttu-id="f9121-1403">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="f9121-1403">**wait_option**</span></span> <br><span data-ttu-id="f9121-1404">Definiuje, w jaki sposób działa usługa, jeśli kolejka komunikatów jest pełna.</span><span class="sxs-lookup"><span data-stu-id="f9121-1404">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="f9121-1405">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9121-1405">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="f9121-1406">**TX_NO_WAIT** (0x00000000) — wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1406">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="f9121-1407">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niebędącego wątkiem, np. inicjalizacji, czasomierza lub ISR*.</span><span class="sxs-lookup"><span data-stu-id="f9121-1407">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="f9121-1408">**TX_WAIT_FOREVER** (0xffffffff) — wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu, w którym znajduje się w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="f9121-1409">wartość limitu czasu (0x00000001 przez 0xFFFFFFFE) — wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma pozostać zawieszona podczas oczekiwania na pokój w kolejce.</span><span class="sxs-lookup"><span data-stu-id="f9121-1409">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1410">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1410">Return Values</span></span>

- <span data-ttu-id="f9121-1411">**TX_SUCCESS** (0X00) pomyślnie wysłano komunikat.</span><span class="sxs-lookup"><span data-stu-id="f9121-1411">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="f9121-1412">Kolejka komunikatów **TX_DELETED** (0x01) została usunięta podczas wstrzymania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1412">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="f9121-1413">Usługa **TX_QUEUE_FULL** (0x0B) nie mogła wysłać komunikatu, ponieważ kolejka była zapełniona przez czas oczekiwania przez określony czas.</span><span class="sxs-lookup"><span data-stu-id="f9121-1413">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="f9121-1414">Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-1414">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="f9121-1415">**TX_QUEUE_ERROR** (0X09) Nieprawidłowy wskaźnik kolejki komunikatów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1415">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="f9121-1416">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik źródła komunikatu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1416">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="f9121-1417">**TX_WAIT_ERROR** (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1417">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1418">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1418">Allowed From</span></span>

<span data-ttu-id="f9121-1419">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1419">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1420">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1420">Preemption Possible</span></span>

<span data-ttu-id="f9121-1421">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-1421">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1422">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1422">Example</span></span>

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
regardless of success. This wait option is used for
calls from initialization, timers, and ISRs. */
status = tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
queue. */
```

<span data-ttu-id="f9121-1423">**Zobacz również**</span><span class="sxs-lookup"><span data-stu-id="f9121-1423">**See Also**</span></span>

- <span data-ttu-id="f9121-1424">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1424">tx_queue_create</span></span>
- <span data-ttu-id="f9121-1425">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1425">tx_queue_delete</span></span>
- <span data-ttu-id="f9121-1426">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1426">tx_queue_flush</span></span>
- <span data-ttu-id="f9121-1427">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1427">tx_queue_front_send</span></span>
- <span data-ttu-id="f9121-1428">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1428">tx_queue_info_get</span></span>
- <span data-ttu-id="f9121-1429">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1429">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="f9121-1430">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1430">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1431">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1431">tx_queue_prioritize</span></span>
- <span data-ttu-id="f9121-1432">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1432">tx_queue_receive</span></span>
- <span data-ttu-id="f9121-1433">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1433">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="f9121-1434">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1434">tx_queue_send_notify</span></span>

<span data-ttu-id="f9121-1435">Powiadamiaj aplikację, gdy wiadomość jest wysyłana do kolejki</span><span class="sxs-lookup"><span data-stu-id="f9121-1435">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1436">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1436">Prototype</span></span>

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a><span data-ttu-id="f9121-1437">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1437">Description</span></span>

<span data-ttu-id="f9121-1438">Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy komunikat zostanie wysłany do określonej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1438">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="f9121-1439">Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="f9121-1439">The processing of the notification callback is defined by the application.</span></span>

>[!NOTE]
> <span data-ttu-id="f9121-1440">*Wywołanie zwrotne powiadomienia o wysłaniu kolejki aplikacji nie może wywołać żadnego interfejsu API ThreadX z opcją zawieszenia.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1440">*The application's queue send notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1441">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1441">Parameters</span></span>

- <span data-ttu-id="f9121-1442">**queue_ptr** Wskaźnik do wcześniej utworzonej kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1442">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="f9121-1443">**queue_send_notify** Wskaźnik do funkcji powiadomień o wysłaniu kolejki aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-1443">**queue_send_notify** Pointer to application's queue send notification function.</span></span> <span data-ttu-id="f9121-1444">Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f9121-1444">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1445">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1445">Return Values</span></span>

- <span data-ttu-id="f9121-1446">**TX_SUCCESS** (0X00) pomyślnie zarejestrowano powiadomienie o wysłaniu kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1446">**TX_SUCCESS** (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="f9121-1447">**TX_QUEUE_ERROR** (0X09) Nieprawidłowy wskaźnik kolejki.</span><span class="sxs-lookup"><span data-stu-id="f9121-1447">**TX_QUEUE_ERROR** (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="f9121-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) system został skompilowany z wyłączonymi funkcjami powiadomień.</span><span class="sxs-lookup"><span data-stu-id="f9121-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1449">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1449">Allowed From</span></span>

<span data-ttu-id="f9121-1450">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1450">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1451">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1451">Example</span></span>

```c
TX_QUEUE my_queue;
/* Register the "my_queue_send_notify" function for monitoring
messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
    /* A message was just sent to this queue! */
}
```

### <a name="see-also"></a><span data-ttu-id="f9121-1452">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1452">See Also</span></span>

- <span data-ttu-id="f9121-1453">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1453">tx_queue_create</span></span>
- <span data-ttu-id="f9121-1454">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1454">tx_queue_delete</span></span>
- <span data-ttu-id="f9121-1455">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="f9121-1455">tx_queue_flush</span></span>
- <span data-ttu-id="f9121-1456">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1456">tx_queue_front_send</span></span>
- <span data-ttu-id="f9121-1457">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1457">tx_queue_info_get</span></span>
- <span data-ttu-id="f9121-1458">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1458">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="f9121-1459">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1459">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1460">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1460">tx_queue_prioritize</span></span>
- <span data-ttu-id="f9121-1461">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="f9121-1461">tx_queue_receive</span></span>
- <span data-ttu-id="f9121-1462">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="f9121-1462">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="f9121-1463">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1463">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="f9121-1464">Umieść wystąpienie w zliczaniu semafora z pułapem</span><span class="sxs-lookup"><span data-stu-id="f9121-1464">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1465">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1465">Prototype</span></span>

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a><span data-ttu-id="f9121-1466">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1466">Description</span></span>

<span data-ttu-id="f9121-1467">Ta usługa umieszcza wystąpienie w określonym semaforze zliczania, który w rzeczywistości zwiększa semafor zliczania o jeden.</span><span class="sxs-lookup"><span data-stu-id="f9121-1467">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="f9121-1468">Jeśli bieżąca wartość semafora zliczania jest większa lub równa określonej granicy, wystąpienie nie zostanie umieszczone i zostanie zwrócony błąd TX_CEILING_EXCEEDED.</span><span class="sxs-lookup"><span data-stu-id="f9121-1468">If the counting semaphore's current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1469">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1469">Parameters</span></span>

- <span data-ttu-id="f9121-1470">**semaphore_ptr** Wskaźnik do wcześniej utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1470">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="f9121-1471">**granica** Maksymalny dozwolony limit dla semafora (prawidłowe wartości mieszczą się w zakresie od 1 do 0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="f9121-1471">**ceiling** Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1472">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1472">Return Values</span></span>

- <span data-ttu-id="f9121-1473">**TX_SUCCESS (0x00)** Pomyślny pułap semafora został przesunięty.</span><span class="sxs-lookup"><span data-stu-id="f9121-1473">**TX_SUCCESS (0x00)** Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="f9121-1474">Żądanie Put **TX_CEILING_EXCEEDED** (0x21) przekracza limit.</span><span class="sxs-lookup"><span data-stu-id="f9121-1474">**TX_CEILING_EXCEEDED** (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="f9121-1475">**TX_INVALID_CEILING** (0x22) podano nieprawidłową wartość zero dla pułapu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1475">**TX_INVALID_CEILING** (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="f9121-1476">**TX_SEMAPHORE_ERROR** (0X0C) Nieprawidłowy wskaźnik semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1476">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1477">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1477">Allowed From</span></span>

<span data-ttu-id="f9121-1478">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1478">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1479">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1479">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1480">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1480">See Also</span></span>

- <span data-ttu-id="f9121-1481">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1481">tx_semaphore_create</span></span>
- <span data-ttu-id="f9121-1482">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1482">tx_semaphore_delete</span></span>
- <span data-ttu-id="f9121-1483">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1483">tx_semaphore_get</span></span>
- <span data-ttu-id="f9121-1484">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1484">tx_semaphore_info_get</span></span>
- <span data-ttu-id="f9121-1485">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1485">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="f9121-1486">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1486">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1487">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1487">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="f9121-1488">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1488">tx_semaphore_put</span></span>
- <span data-ttu-id="f9121-1489">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1489">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="f9121-1490">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1490">tx_semaphore_create</span></span>

<span data-ttu-id="f9121-1491">Tworzenie semafora zliczania</span><span class="sxs-lookup"><span data-stu-id="f9121-1491">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1492">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1492">Prototype</span></span>

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a><span data-ttu-id="f9121-1493">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1493">Description</span></span>

<span data-ttu-id="f9121-1494">Ta usługa tworzy semafor zliczania dla synchronizacji między wątkami.</span><span class="sxs-lookup"><span data-stu-id="f9121-1494">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="f9121-1495">Początkowa liczba semaforów jest określana jako parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="f9121-1495">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1496">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1496">Parameters</span></span>

- <span data-ttu-id="f9121-1497">**semaphore_ptr** Wskaźnik do bloku sterowania semaforem.</span><span class="sxs-lookup"><span data-stu-id="f9121-1497">**semaphore_ptr** Pointer to a semaphore control block.</span></span>
- <span data-ttu-id="f9121-1498">**name_ptr** Wskaźnik na nazwę semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1498">**name_ptr** Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="f9121-1499">**initial_count** Określa początkową liczbę dla tego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1499">**initial_count** Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="f9121-1500">Wartości prawne mieszczą się w zakresie od 0x00000000 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="f9121-1500">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1501">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1501">Return Values</span></span>

- <span data-ttu-id="f9121-1502">**TX_SUCCESS** (0X00) pomyślne utworzenie semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1502">**TX_SUCCESS** (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="f9121-1503">**TX_SEMAPHORE_ERROR** (0X0C) Nieprawidłowy wskaźnik semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1503">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="f9121-1504">Wskaźnik ma wartość NULL lub semafor został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="f9121-1504">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="f9121-1505">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-1505">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1506">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1506">Allowed From</span></span>

<span data-ttu-id="f9121-1507">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-1507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1508">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1508">Preemption Possible</span></span>

<span data-ttu-id="f9121-1509">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-1509">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1510">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1510">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Create a counting semaphore whose initial value is 1.
This is typically the technique used to make a binary
semaphore. Binary semaphores are used to provide
protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
    "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
use. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1511">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1511">See Also</span></span>

- <span data-ttu-id="f9121-1512">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1512">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="f9121-1513">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1513">tx_semaphore_delete</span></span>
- <span data-ttu-id="f9121-1514">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1514">tx_semaphore_get</span></span>
- <span data-ttu-id="f9121-1515">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1515">tx_semaphore_info_get</span></span>
- <span data-ttu-id="f9121-1516">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1516">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="f9121-1517">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1517">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1518">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1518">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="f9121-1519">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1519">tx_semaphore_put</span></span>
- <span data-ttu-id="f9121-1520">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1520">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="f9121-1521">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1521">tx_semaphore_delete</span></span>

<span data-ttu-id="f9121-1522">Usuń semafor zliczania</span><span class="sxs-lookup"><span data-stu-id="f9121-1522">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1523">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1523">Prototype</span></span>
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-1524">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1524">Description</span></span>

<span data-ttu-id="f9121-1525">Ta usługa usuwa określony semafor zliczania.</span><span class="sxs-lookup"><span data-stu-id="f9121-1525">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="f9121-1526">Wszystkie wątki zawieszone w trakcie oczekiwania na wystąpienie semafora są wznawiane i nadawane TX_DELETED stanie powrotu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1526">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-1527">*Aplikacja musi zapewnić ukończenie wywołania zwrotnego powiadomienia dla tego semafora (lub wyłączone) przed usunięciem semafora. Ponadto aplikacja musi uniemożliwić wszystkie przyszłe użycie usuniętego semafora.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1527">*The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore. In addition, the application must prevent all future use of a deleted semaphore.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1528">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1528">Parameters</span></span>

- <span data-ttu-id="f9121-1529">**semaphore_ptr** Wskaźnik do wcześniej utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1529">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1530">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1530">Return Values</span></span>

- <span data-ttu-id="f9121-1531">**TX_SUCCESS** (0X00) pomyślnie zliczanie usunięcia semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1531">**TX_SUCCESS** (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="f9121-1532">**TX_SEMAPHORE_ERROR** (0X0C) Nieprawidłowy wskaźnik zliczania semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1532">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="f9121-1533">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-1533">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1534">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1534">Allowed From</span></span>

<span data-ttu-id="f9121-1535">Wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-1535">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1536">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1536">Preemption Possible</span></span>

<span data-ttu-id="f9121-1537">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-1537">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1538">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1538">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

<span data-ttu-id="f9121-1539">**Zobacz również**</span><span class="sxs-lookup"><span data-stu-id="f9121-1539">**See Also**</span></span>

- <span data-ttu-id="f9121-1540">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1540">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="f9121-1541">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1541">tx_semaphore_create</span></span>
- <span data-ttu-id="f9121-1542">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1542">tx_semaphore_get</span></span>
- <span data-ttu-id="f9121-1543">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1543">tx_semaphore_info_get</span></span>
- <span data-ttu-id="f9121-1544">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1544">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="f9121-1545">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1545">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1546">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1546">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="f9121-1547">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1547">tx_semaphore_put</span></span>
- <span data-ttu-id="f9121-1548">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1548">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="f9121-1549">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1549">tx_semaphore_get</span></span>

<span data-ttu-id="f9121-1550">Pobierz wystąpienie z zliczania semafora</span><span class="sxs-lookup"><span data-stu-id="f9121-1550">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1551">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1551">Prototype</span></span>

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="f9121-1552">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1552">Description</span></span>

<span data-ttu-id="f9121-1553">Ta usługa Pobiera wystąpienie (pojedyncza liczba) z określonego semafora zliczania.</span><span class="sxs-lookup"><span data-stu-id="f9121-1553">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="f9121-1554">W związku z tym liczba określonych semaforów zostanie zmniejszona o jeden.</span><span class="sxs-lookup"><span data-stu-id="f9121-1554">As a result, the specified semaphore's count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1555">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1555">Parameters</span></span>

- <span data-ttu-id="f9121-1556">**semaphore_ptr**</span><span class="sxs-lookup"><span data-stu-id="f9121-1556">**semaphore_ptr**</span></span> <br><span data-ttu-id="f9121-1557">Wskaźnik do wcześniej utworzonego semafora zliczania.</span><span class="sxs-lookup"><span data-stu-id="f9121-1557">Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="f9121-1558">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="f9121-1558">**wait_option**</span></span> <br><span data-ttu-id="f9121-1559">Definiuje, w jaki sposób działa usługa, jeśli nie ma dostępnych wystąpień semafora; oznacza to, że liczba semaforów jest równa zero.</span><span class="sxs-lookup"><span data-stu-id="f9121-1559">Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="f9121-1560">Opcje oczekiwania są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9121-1560">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="f9121-1561">**TX_NO_WAIT** (0x00000000) — wybranie TX_NO_WAIT powoduje natychmiastowe zwrócenie z tej usługi niezależnie od tego, czy zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1561">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="f9121-1562">*Jest to jedyna prawidłowa opcja, jeśli usługa jest wywoływana z niewątku; np. Inicjalizacja, czasomierz lub ISR.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1562">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="f9121-1563">**TX_WAIT_FOREVER** (0xffffffff) — wybranie TX_WAIT_FOREVER powoduje, że wątek wywołujący zawiesza się w nieskończoność do momentu dostępności wystąpienia semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span>
  - <span data-ttu-id="f9121-1564">wartość limitu czasu (0x00000001 przez 0xFFFFFFFE) — wybranie wartości liczbowej (1-0xFFFFFFFE) określa maksymalną liczbę cykli czasomierza, która ma zostać wstrzymana podczas oczekiwania na wystąpienie semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1564">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1565">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1565">Return Values</span></span>

- <span data-ttu-id="f9121-1566">**TX_SUCCESS** (0X00) pomyślne pobranie wystąpienia semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1566">**TX_SUCCESS** (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="f9121-1567">Nie usunięto semafora zliczania **TX_DELETED** (0x01), gdy wątek został zawieszony.</span><span class="sxs-lookup"><span data-stu-id="f9121-1567">**TX_DELETED** (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="f9121-1568">Usługa **TX_NO_INSTANCE** (0x0D) nie mogła pobrać wystąpienia semafora zliczania (liczba semaforów wynosi zero w określonym czasie oczekiwania).</span><span class="sxs-lookup"><span data-stu-id="f9121-1568">**TX_NO_INSTANCE** (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="f9121-1569">Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-1569">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="f9121-1570">**TX_SEMAPHORE_ERROR** (0X0C) Nieprawidłowy wskaźnik zliczania semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1570">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="f9121-1571">**TX_WAIT_ERROR** (0x04) opcja oczekiwania inna niż TX_NO_WAIT została określona w wywołaniu z niewątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1571">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1572">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1572">Allowed From</span></span>

<span data-ttu-id="f9121-1573">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1573">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1574">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1574">Preemption Possible</span></span>

<span data-ttu-id="f9121-1575">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-1575">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1576">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1576">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Get a semaphore instance from the semaphore
"my_semaphore." If the semaphore count is zero,
suspend until an instance becomes available.
Note that this suspension is only possible from
application threads. */
status = tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
an instance of the semaphore. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1577">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1577">See Also</span></span>

- <span data-ttu-id="f9121-1578">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1578">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="f9121-1579">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1579">tx_semaphore_create</span></span>
- <span data-ttu-id="f9121-1580">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1580">tx_semahore_delete</span></span>
- <span data-ttu-id="f9121-1581">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1581">tx_semaphore_info_get</span></span>
- <span data-ttu-id="f9121-1582">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1582">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="f9121-1583">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1583">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="f9121-1584">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1584">tx_semaphore_put</span></span>
- <span data-ttu-id="f9121-1585">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1585">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="f9121-1586">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1586">tx_semaphore_info_get</span></span>

<span data-ttu-id="f9121-1587">Pobierz informacje o semaforze</span><span class="sxs-lookup"><span data-stu-id="f9121-1587">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1588">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1588">Prototype</span></span>

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a><span data-ttu-id="f9121-1589">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1589">Description</span></span>

<span data-ttu-id="f9121-1590">Ta usługa pobiera informacje o określonym semaforze.</span><span class="sxs-lookup"><span data-stu-id="f9121-1590">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1591">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1591">Parameters</span></span>

- <span data-ttu-id="f9121-1592">**semaphore_ptr** Wskaźnik do bloku sterowania semaforem.</span><span class="sxs-lookup"><span data-stu-id="f9121-1592">**semaphore_ptr** Pointer to semaphore control block.</span></span>
- <span data-ttu-id="f9121-1593">**Nazwa** Wskaźnik do miejsca docelowego dla wskaźnika do nazwy semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1593">**name** Pointer to destination for the pointer to the semaphore's name.</span></span>
- <span data-ttu-id="f9121-1594">**current_value** Wskaźnik do miejsca docelowego dla licznika bieżącego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1594">**current_value** Pointer to destination for the current semaphore's count.</span></span>
- <span data-ttu-id="f9121-1595">**first_suspended** Wskaźnik do miejsca docelowego dla wskaźnika do wątku, który jest pierwszy na liście zawieszeń tego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1595">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="f9121-1596">**suspended_count** Wskaźnik do miejsca docelowego dla liczby wątków, które są obecnie zawieszone w tym semaforze.</span><span class="sxs-lookup"><span data-stu-id="f9121-1596">**suspended_count** Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="f9121-1597">**next_semaphore** Wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1597">**next_semaphore** Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1598">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1598">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1599">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1599">Return Values</span></span>

- <span data-ttu-id="f9121-1600">Pobieranie informacji o **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-1600">**TX_SUCCESS** (0x00) information retrieval.</span></span>

- <span data-ttu-id="f9121-1601">**TX_SEMAPHORE_ERROR** (0X0C) Nieprawidłowy wskaźnik semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1601">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1602">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1602">Allowed From</span></span>

<span data-ttu-id="f9121-1603">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1603">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1604">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1604">Preemption Possible</span></span>

<span data-ttu-id="f9121-1605">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-1605">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1606">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1606">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
CHAR *name;
ULONG current_value;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT status;

/* Retrieve information about the previously created
semaphore "my_semaphore." */
status = tx_semaphore_info_get(&my_semaphore, &name,
    &current_value,
    &first_suspended, &suspended_count,
    &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1607">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1607">See Also</span></span>

- <span data-ttu-id="f9121-1608">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1608">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="f9121-1609">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1609">tx_semaphore_create</span></span>
- <span data-ttu-id="f9121-1610">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1610">tx_semaphore_delete</span></span>
- <span data-ttu-id="f9121-1611">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1611">tx_semaphore_get</span></span>
- <span data-ttu-id="f9121-1612">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1612">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="f9121-1613">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1613">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1614">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1614">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="f9121-1615">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1615">tx_semaphore_put</span></span>
- <span data-ttu-id="f9121-1616">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1616">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="f9121-1617">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1617">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="f9121-1618">Pobierz informacje o wydajności semafora</span><span class="sxs-lookup"><span data-stu-id="f9121-1618">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1619">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1619">Prototype</span></span>

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="f9121-1620">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1620">Description</span></span>

<span data-ttu-id="f9121-1621">Ta usługa pobiera informacje o wydajności dotyczące określonego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1621">This service retrieves performance information about the specified semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-1622">*Biblioteka i aplikacja ThreadX muszą być kompilowane przy użyciu*  \* **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined do zwrócenia informacji o wydajności przez tę usługę \*</span><span class="sxs-lookup"><span data-stu-id="f9121-1622">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

<span data-ttu-id="f9121-1623">**Parametry**</span><span class="sxs-lookup"><span data-stu-id="f9121-1623">**Parameters**</span></span>

-  <span data-ttu-id="f9121-1624">**semaphore_ptr** Wskaźnik do wcześniej utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1624">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
-  <span data-ttu-id="f9121-1625">**umieszcza** Wskaźnik do miejsca docelowego dla liczby żądań PUT wykonanych dla tego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1625">**puts** Pointer to destination for the number of put requests performed on this semaphore.</span></span>
-  <span data-ttu-id="f9121-1626">**Pobiera** Wskaźnik do miejsca docelowego dla liczby żądań GET wykonanych dla tego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1626">**gets** Pointer to destination for the number of get requests performed on this semaphore.</span></span>
-  <span data-ttu-id="f9121-1627">**zawieszenie** Wskaźnik do miejsca docelowego dla liczby zawieszeń wątku dla tego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1627">**suspensions** Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
-  <span data-ttu-id="f9121-1628">**limity czasu** Wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia wątku dla tego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1628">**timeouts** Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1629">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1629">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1630">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1630">Return Values</span></span>

- <span data-ttu-id="f9121-1631">**TX_SUCCESS** (0X00) pomyślne pobieranie wydajności semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1631">**TX_SUCCESS** (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="f9121-1632">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1632">**TX_PTR_ERROR** (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="f9121-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1634">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1634">Allowed From</span></span>

<span data-ttu-id="f9121-1635">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1635">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1636">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1636">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created
semaphore. */
status = tx_semaphore_performance_info_get(&my_semaphore, &puts,
    &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1637">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1637">See Also</span></span>

- <span data-ttu-id="f9121-1638">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1638">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="f9121-1639">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1639">tx_semaphore_create</span></span>
- <span data-ttu-id="f9121-1640">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1640">tx_semaphore_delete</span></span>
- <span data-ttu-id="f9121-1641">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1641">tx_semaphore_get</span></span>
- <span data-ttu-id="f9121-1642">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1642">tx_semaphore_info_get</span></span>
- <span data-ttu-id="f9121-1643">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1643">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1644">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1644">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="f9121-1645">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1645">tx_semaphore_put</span></span>
- <span data-ttu-id="f9121-1646">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1646">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="f9121-1647">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1647">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="f9121-1648">Pobierz informacje o wydajności systemu semafora</span><span class="sxs-lookup"><span data-stu-id="f9121-1648">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1649">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1649">Prototype</span></span>

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="f9121-1650">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1650">Description</span></span>

<span data-ttu-id="f9121-1651">Ta usługa pobiera informacje o wydajności dotyczące wszystkich semaforów w systemie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1651">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-1652">*Biblioteka i aplikacja ThreadX muszą być kompilowane przy użyciu*  \* **TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined do zwrócenia informacji o wydajności przez tę usługę \*</span><span class="sxs-lookup"><span data-stu-id="f9121-1652">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1653">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1653">Parameters</span></span>

- <span data-ttu-id="f9121-1654">**umieszcza** Wskaźnik do miejsca docelowego dla łącznej liczby żądań PUT wykonanych na wszystkich semaforach.</span><span class="sxs-lookup"><span data-stu-id="f9121-1654">**puts** Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="f9121-1655">**Pobiera** Wskaźnik do miejsca docelowego dla łącznej liczby żądań GET wykonanych na wszystkich semaforach.</span><span class="sxs-lookup"><span data-stu-id="f9121-1655">**gets** Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="f9121-1656">**zawieszenie** Wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń wątku na wszystkich semaforach.</span><span class="sxs-lookup"><span data-stu-id="f9121-1656">**suspensions** Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="f9121-1657">**limity czasu** Wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia wątku dla wszystkich semaforów.</span><span class="sxs-lookup"><span data-stu-id="f9121-1657">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1658">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1658">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1659">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1659">Return Values</span></span>

- <span data-ttu-id="f9121-1660">Pobieranie wydajności systemu **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-1660">**TX_SUCCESS** (0x00) system performance get.</span></span>
- <span data-ttu-id="f9121-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1662">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1662">Allowed From</span></span>

<span data-ttu-id="f9121-1663">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1663">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1664">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1664">Example</span></span>

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created
semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1665">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1665">See Also</span></span>

- <span data-ttu-id="f9121-1666">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1666">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="f9121-1667">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1667">tx_semaphore_create</span></span>
- <span data-ttu-id="f9121-1668">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1668">tx_semaphore_delete</span></span>
- <span data-ttu-id="f9121-1669">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1669">tx_semaphore_get</span></span>
- <span data-ttu-id="f9121-1670">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1670">tx_semaphore_info_get</span></span>
- <span data-ttu-id="f9121-1671">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1671">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="f9121-1672">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1672">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="f9121-1673">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1673">tx_semaphore_put</span></span>
- <span data-ttu-id="f9121-1674">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1674">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="f9121-1675">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1675">tx_semaphore_prioritize</span></span>

<span data-ttu-id="f9121-1676">Ustawianie priorytetu listy zawieszania semafora</span><span class="sxs-lookup"><span data-stu-id="f9121-1676">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1677">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1677">Prototype</span></span>

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-1678">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1678">Description</span></span>

<span data-ttu-id="f9121-1679">Ta usługa umieszcza wątek o najwyższym priorytecie w przypadku wystąpienia semafora na początku listy zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-1679">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="f9121-1680">Wszystkie pozostałe wątki pozostają w tej samej kolejności FIFO, w której zostały zawieszone.</span><span class="sxs-lookup"><span data-stu-id="f9121-1680">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1681">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1681">Parameters</span></span>

- <span data-ttu-id="f9121-1682">**semaphore_ptr** Wskaźnik do wcześniej utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1682">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1683">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1683">Return Values</span></span>

- <span data-ttu-id="f9121-1684">Pomyślna priorytetyzacja semafora **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-1684">**TX_SUCCESS** (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="f9121-1685">**TX_SEMAPHORE_ERROR** (0X0C) Nieprawidłowy wskaźnik zliczania semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1685">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1686">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1686">Allowed From</span></span>

<span data-ttu-id="f9121-1687">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1687">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1688">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1688">Preemption Possible</span></span>

<span data-ttu-id="f9121-1689">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-1689">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1690">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1690">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Ensure that the highest priority thread will receive
the next instance of this semaphore. */
status = tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_semaphore_put call made to this semaphore will
wake up this thread. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1691">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1691">See Also</span></span>

- <span data-ttu-id="f9121-1692">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1692">tx_semaphore_create</span></span>
- <span data-ttu-id="f9121-1693">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1693">tx_semaphore_delete</span></span>
- <span data-ttu-id="f9121-1694">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1694">tx_semaphore_get</span></span>
- <span data-ttu-id="f9121-1695">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1695">tx_semaphore_info_get</span></span>
- <span data-ttu-id="f9121-1696">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1696">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="f9121-1697">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1697">tx_semaphore_put</span></span>

<span data-ttu-id="f9121-1698">Umieść wystąpienie w zliczaniu semafora</span><span class="sxs-lookup"><span data-stu-id="f9121-1698">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1699">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1699">Prototype</span></span>

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-1700">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1700">Description</span></span>

<span data-ttu-id="f9121-1701">Ta usługa umieszcza wystąpienie w określonym semaforze zliczania, który w rzeczywistości zwiększa semafor zliczania o jeden.</span><span class="sxs-lookup"><span data-stu-id="f9121-1701">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1702">*Jeśli ta usługa jest wywoływana, gdy semafor ma wszystkie (OxFFFFFFFF), Nowa operacja Put spowoduje, że semafor zostanie zresetowany do zera.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1702">*If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1703">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1703">Parameters</span></span>

- <span data-ttu-id="f9121-1704">**semaphore_ptr** Wskaźnik do wcześniej utworzonego bloku sterowania semaforem zliczania.</span><span class="sxs-lookup"><span data-stu-id="f9121-1704">**semaphore_ptr** Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1705">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1705">Return Values</span></span>

- <span data-ttu-id="f9121-1706">**TX_SUCCESS** (0X00) zakończony powodzeniem semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1706">**TX_SUCCESS** (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="f9121-1707">**TX_SEMAPHORE_ERROR** (0X0C) Nieprawidłowy wskaźnik do zliczania semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1707">**TX_SEMAPHORE_ERROR** (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1708">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1708">Allowed From</span></span>

<span data-ttu-id="f9121-1709">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1709">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1710">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1710">Preemption Possible</span></span>

<span data-ttu-id="f9121-1711">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-1711">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1712">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1712">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1713">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1713">See Also</span></span>

- <span data-ttu-id="f9121-1714">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1714">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="f9121-1715">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1715">tx_semaphore_create</span></span>
- <span data-ttu-id="f9121-1716">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1716">tx_semaphore_delete</span></span>
- <span data-ttu-id="f9121-1717">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1717">tx_semaphore_info_get</span></span>
- <span data-ttu-id="f9121-1718">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1718">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="f9121-1719">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1719">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1720">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1720">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="f9121-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="f9121-1722">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1722">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="f9121-1723">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1723">tx_semaphore_put_notify</span></span>

<span data-ttu-id="f9121-1724">Powiadamiaj aplikację po umieszczeniu semafora</span><span class="sxs-lookup"><span data-stu-id="f9121-1724">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1725">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1725">Prototype</span></span>

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a><span data-ttu-id="f9121-1726">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1726">Description</span></span>

<span data-ttu-id="f9121-1727">Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy określony semafor jest umieszczony.</span><span class="sxs-lookup"><span data-stu-id="f9121-1727">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="f9121-1728">Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="f9121-1728">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1729">*Wywołanie zwrotne powiadomienia semafora aplikacji nie może wywołać żadnego interfejsu API ThreadX z opcją zawieszenia.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1729">*The application's semaphore notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1730">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1730">Parameters</span></span>

- <span data-ttu-id="f9121-1731">**semaphore_ptr** Wskaźnik do wcześniej utworzonego semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1731">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="f9121-1732">**semaphore_put_notify** Wskaźnik do funkcji powiadomień o przekazaniu semafora aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-1732">**semaphore_put_notify** Pointer to application's semaphore put notification function.</span></span> <span data-ttu-id="f9121-1733">Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f9121-1733">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1734">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1734">Return Values</span></span>

- <span data-ttu-id="f9121-1735">**TX_SUCCESS** (0x00) pomyślna Rejestracja powiadomienia o wprowadzeniu semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1735">**TX_SUCCESS** (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="f9121-1736">**TX_SEMAPHORE_ERROR** (0X0C) Nieprawidłowy wskaźnik semafora.</span><span class="sxs-lookup"><span data-stu-id="f9121-1736">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="f9121-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) system został skompilowany z wyłączonymi funkcjami powiadomień.</span><span class="sxs-lookup"><span data-stu-id="f9121-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1738">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1738">Allowed From</span></span>

<span data-ttu-id="f9121-1739">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1739">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1740">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1740">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
the put operations on the semaphore "my_semaphore." */
status = tx_semaphore_put_notify(&my_semaphore, my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
was successfully registered. */
void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
    /* The semaphore was just put! */
}
```

### <a name="see-also"></a><span data-ttu-id="f9121-1741">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1741">See Also</span></span>

- <span data-ttu-id="f9121-1742">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1742">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="f9121-1743">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1743">tx_semaphore_create</span></span>
- <span data-ttu-id="f9121-1744">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1744">tx_semaphore_delete</span></span>
- <span data-ttu-id="f9121-1745">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1745">tx_semaphore_get</span></span>
- <span data-ttu-id="f9121-1746">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1746">tx_semaphore_info_get</span></span>
- <span data-ttu-id="f9121-1747">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1747">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="f9121-1748">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1748">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1749">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="f9121-1749">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="f9121-1750">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="f9121-1750">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="f9121-1751">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1751">tx_thread_create</span></span>

<span data-ttu-id="f9121-1752">Utwórz wątek aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-1752">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1753">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1753">Prototype</span></span>

```c
UINT tx_thread_create(
    TX_THREAD *thread_ptr,
    CHAR *name_ptr, 
    VOID (*entry_function)(ULONG),
    ULONG entry_input, 
    VOID *stack_start,
    ULONG stack_size, 
    UINT priority,
    UINT preempt_threshold, 
    ULONG time_slice,
    UINT auto_start);
```

### <a name="description"></a><span data-ttu-id="f9121-1754">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1754">Description</span></span>

<span data-ttu-id="f9121-1755">Ta usługa tworzy wątek aplikacji, który uruchamia wykonywanie w określonej funkcji wprowadzania zadań.</span><span class="sxs-lookup"><span data-stu-id="f9121-1755">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="f9121-1756">Stos, priorytet, wartość progowa i wycinek czasu są wśród atrybutów określonych przez parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="f9121-1756">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="f9121-1757">Ponadto jest również określony początkowy stan wykonywania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1757">In addition, the initial execution state of the thread is also specified.</span></span>

<span data-ttu-id="f9121-1758">**Parametry**</span><span class="sxs-lookup"><span data-stu-id="f9121-1758">**Parameters**</span></span>

- <span data-ttu-id="f9121-1759">**thread_ptr** Wskaźnik do bloku sterowania wątkiem.</span><span class="sxs-lookup"><span data-stu-id="f9121-1759">**thread_ptr** Pointer to a thread control block.</span></span>
- <span data-ttu-id="f9121-1760">**name_ptr** Wskaźnik na nazwę wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1760">**name_ptr** Pointer to the name of the thread.</span></span>
- <span data-ttu-id="f9121-1761">**entry_function** Określa początkową funkcję C do wykonania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1761">**entry_function** Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="f9121-1762">Gdy wątek wraca z tej funkcji wejścia, jest on umieszczany w stanie *ukończenia* i zawieszony czasowo.</span><span class="sxs-lookup"><span data-stu-id="f9121-1762">When a thread returns from this entry function, it is placed in a *completed* state and suspended indefinitely.</span></span>
- <span data-ttu-id="f9121-1763">**entry_input** Wartość 32-bitowa, która jest przesyłana do funkcji wejścia wątku podczas pierwszego wykonania.</span><span class="sxs-lookup"><span data-stu-id="f9121-1763">**entry_input** A 32-bit value that is passed to the thread's entry function when it first executes.</span></span> <span data-ttu-id="f9121-1764">Użycie tego danych wejściowych jest określane wyłącznie przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="f9121-1764">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="f9121-1765">**stack_start** Adres początkowy obszaru pamięci stosu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1765">**stack_start** Starting address of the stack's memory area.</span></span>
- <span data-ttu-id="f9121-1766">**stack_size** Liczba bajtów w obszarze pamięci stosu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1766">**stack_size** Number bytes in the stack memory area.</span></span> <span data-ttu-id="f9121-1767">Obszar stosu wątku musi być wystarczająco duży, aby obsługiwał jego najgorszą metodę użycia.</span><span class="sxs-lookup"><span data-stu-id="f9121-1767">The thread's stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="f9121-1768">**priorytet** Priorytet liczbowy wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1768">**priority** Numerical priority of thread.</span></span> <span data-ttu-id="f9121-1769">Wartości prawne mieszczą się w zakresie od 0 do (TX_MAX_PRIORITES-1), gdzie wartość 0 reprezentuje najwyższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="f9121-1769">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="f9121-1770">**preempt_threshold** Najwyższy poziom priorytetu (od 0 do (TX_MAX_PRIORITIES-1)) wyłączono przechodzenie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1770">**preempt_threshold** Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="f9121-1771">Tylko priorytety wyższe niż ten poziom mogą przewagę tego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1771">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="f9121-1772">Ta wartość nie może być większa niż określony priorytet.</span><span class="sxs-lookup"><span data-stu-id="f9121-1772">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="f9121-1773">Wartość równa priorytetu wątku powoduje wyłączenie progu zastępujący.</span><span class="sxs-lookup"><span data-stu-id="f9121-1773">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="f9121-1774">**time_slice** Liczba czasomierzy, przez który ten wątek może działać, zanim inne gotowe wątki o takim samym priorytecie mają szansę uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="f9121-1774">**time_slice** Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="f9121-1775">Należy pamiętać, że użycie wartości progowej przekroczenia powoduje wyłączenie tworzenia wycinków czasu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1775">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="f9121-1776">Dozwolone wartości wycinków czasu mieszczą się w zakresie od 1 do 0xFFFFFFFF (włącznie).</span><span class="sxs-lookup"><span data-stu-id="f9121-1776">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="f9121-1777">Wartość **TX_NO_TIME_SLICE** (wartość 0) powoduje wyłączenie wycinka czasu dla tego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1777">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f9121-1778">*Korzystanie z wycinków czasu powoduje niewielkie obciążenie systemu.   Ponieważ podział czasu jest przydatny tylko w przypadkach, gdy wiele wątków ma ten sam priorytet, wątki mające unikatowy priorytet nie powinny mieć przypisanego wycinka czasowego.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1778">*Using time-slicing results in a slight amount of system overhead.   Since time-slicing is only useful in cases where multiple threads   share the same priority, threads having a unique priority should not   be assigned a time-slice.*</span></span>

- <span data-ttu-id="f9121-1779">**auto_start** Określa, czy wątek zaczyna się od razu czy jest umieszczony w stanie wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="f9121-1779">**auto_start** Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="f9121-1780">Opcje prawne są **TX_AUTO_START** (0x01) i **TX_DONT_START** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-1780">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="f9121-1781">Jeśli TX_DONT_START jest określony, aplikacja musi później wywołać tx_thread_resume w celu uruchomienia wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1781">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1782">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1782">Return Values</span></span>

- <span data-ttu-id="f9121-1783">Zakończono tworzenie wątku **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-1783">**TX_SUCCESS** (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="f9121-1784">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik kontrolny wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1784">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="f9121-1785">Wskaźnik ma wartość NULL lub wątek został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="f9121-1785">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="f9121-1786">**TX_PTR_ERROR** (0X03) nieprawidłowy adres początkowy punktu wejścia lub obszar stosu jest nieprawidłowy, zazwyczaj ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="f9121-1786">**TX_PTR_ERROR** (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="f9121-1787">Rozmiar **TX_SIZE_ERROR** (0x05) obszaru stosu jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f9121-1787">**TX_SIZE_ERROR** (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="f9121-1788">Wątki muszą mieć co najmniej **TX_MINIMUM_STACK** bajtów do wykonania.</span><span class="sxs-lookup"><span data-stu-id="f9121-1788">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="f9121-1789">**TX_PRIORITY_ERROR** (0X0F) nieprawidłowy priorytet wątku, który jest wartością spoza zakresu (od 0 do (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="f9121-1789">**TX_PRIORITY_ERROR** (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="f9121-1790">**TX_THRESH_ERROR** (0x18) określono nieprawidłowy preemptionthreshold.</span><span class="sxs-lookup"><span data-stu-id="f9121-1790">**TX_THRESH_ERROR** (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="f9121-1791">Ta wartość musi być prawidłowym priorytetem nie większym niż początkowy priorytet wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1791">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="f9121-1792">**TX_START_ERROR** (0X10) nieprawidłowy wybór autostartu.</span><span class="sxs-lookup"><span data-stu-id="f9121-1792">**TX_START_ERROR** (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="f9121-1793">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-1793">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1794">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1794">Allowed From</span></span>

<span data-ttu-id="f9121-1795">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-1795">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1796">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1796">Preemption Possible</span></span>

<span data-ttu-id="f9121-1797">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-1797">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1798">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1798">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Create a thread of priority 15 whose entry point is
"my_thread_entry". This thread’s stack area is 1000
bytes in size, starting at address 0x400000. The
preemption-threshold is setup to allow preemption of threads
with priorities ranging from 0 through 14. Time-slicing is
disabled. This thread is automatically put into a ready
condition. */
status = tx_thread_create(&my_thread, "my_thread_name",
    my_thread_entry, 0x1234,
    (VOID *) 0x400000, 1000,
    15, 15, TX_NO_TIME_SLICE,
    TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
for execution! */

...

/* Thread’s entry function. When "my_thread" actually
begins execution, control is transferred to this
function. */

VOID my_thread_entry (ULONG initial_input)
{
    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */
    /* The real work of the thread, including calls to
    other function should be called from here! */
    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```

### <a name="see-also"></a><span data-ttu-id="f9121-1799">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1799">See Also</span></span>

- <span data-ttu-id="f9121-1800">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1800">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-1801">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1801">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-1802">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-1802">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-1803">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1803">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-1804">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1804">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-1805">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1805">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1806">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1806">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-1807">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1807">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-1808">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-1808">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-1809">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-1809">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-1810">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-1810">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-1811">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-1811">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-1812">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1812">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-1813">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-1813">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-1814">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-1814">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-1815">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1815">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-1816">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-1816">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="f9121-1817">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1817">tx_thread_delete</span></span>

<span data-ttu-id="f9121-1818">Usuń wątek aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-1818">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1819">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1819">Prototype</span></span>

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-1820">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1820">Description</span></span>

<span data-ttu-id="f9121-1821">Ta usługa usuwa określony wątek aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-1821">This service deletes the specified application thread.</span></span> <span data-ttu-id="f9121-1822">Ponieważ określony wątek musi być w stanie zakończony lub zakończony, ta usługa nie może zostać wywołana z wątku próbującego usunąć sam siebie.</span><span class="sxs-lookup"><span data-stu-id="f9121-1822">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1823">*Jest on odpowiedzialny za zarządzanie obszarem pamięci skojarzonym ze stosem wątku, który jest dostępny po zakończeniu tej usługi. Ponadto aplikacja musi uniemożliwić korzystanie z usuniętego wątku.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1823">*It is the application's responsibility to manage the memory area associated with the thread's stack, which is available after this service completes. In addition, the application must prevent use of a deleted thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1824">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1824">Parameters</span></span>

- <span data-ttu-id="f9121-1825">**thread_ptr** Wskaźnik do wcześniej utworzonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-1825">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1826">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1826">Return Values</span></span>

- <span data-ttu-id="f9121-1827">Pomyślnie usunięto wątek **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-1827">**TX_SUCCESS** (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="f9121-1828">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-1828">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="f9121-1829">Określony wątek **TX_DELETE_ERROR** (0x11) nie jest w stanie przerwania ani kończenia.</span><span class="sxs-lookup"><span data-stu-id="f9121-1829">**TX_DELETE_ERROR** (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="f9121-1830">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-1830">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1831">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1831">Allowed From</span></span>

<span data-ttu-id="f9121-1832">Wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="f9121-1832">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1833">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1833">Preemption Possible</span></span>

<span data-ttu-id="f9121-1834">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-1834">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1835">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1835">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Delete an application thread whose control block is
"my_thread". Assume that the thread has already been
created with a call to tx_thread_create. */
status = tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1836">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1836">See Also</span></span>

- <span data-ttu-id="f9121-1837">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1837">tx_thread_create</span></span>
- <span data-ttu-id="f9121-1838">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1838">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-1839">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-1839">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-1840">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1840">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-1841">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1841">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-1842">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1842">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1843">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1843">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-1844">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1844">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-1845">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-1845">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-1846">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-1846">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-1847">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-1847">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-1848">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-1848">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-1849">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1849">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-1850">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-1850">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-1851">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-1851">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-1852">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1852">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-1853">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-1853">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="f9121-1854">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1854">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="f9121-1855">Powiadamiaj aplikację przy wejściu i wyjściu wątku</span><span class="sxs-lookup"><span data-stu-id="f9121-1855">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1856">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1856">Prototype</span></span>

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a><span data-ttu-id="f9121-1857">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1857">Description</span></span>

<span data-ttu-id="f9121-1858">Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia, która jest wywoływana za każdym razem, gdy określony wątek zostanie wprowadzony lub zostanie zakończony.</span><span class="sxs-lookup"><span data-stu-id="f9121-1858">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="f9121-1859">Przetwarzanie wywołania zwrotnego powiadomienia jest definiowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="f9121-1859">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1860">Wywołanie zwrotne powiadomienia o wejściu/wyjściu do wątku aplikacji nie może wywołać żadnego interfejsu API ThreadX z opcją zawieszenia.</span><span class="sxs-lookup"><span data-stu-id="f9121-1860">The application's thread entry/exit notification callback is not allowed to call any ThreadX API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1861">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1861">Parameters</span></span>

- <span data-ttu-id="f9121-1862">**thread_ptr** Wskaźnik do wcześniej utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1862">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="f9121-1863">**entry_exit_notify** Wskaźnik do funkcji powiadomienia o wejściu/wyjściu wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-1863">**entry_exit_notify** Pointer to application's thread entry/exit notification function.</span></span> <span data-ttu-id="f9121-1864">Drugi parametr funkcji powiadomień o wejściu/wyjściu określa, czy jest obecny wpis lub wyjście.</span><span class="sxs-lookup"><span data-stu-id="f9121-1864">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="f9121-1865">Wartość **TX_THREAD_ENTRY** (0x00) wskazuje, że wątek został wprowadzony, podczas gdy wartość **TX_THREAD_EXIT** (0x01) wskazuje, że wątek został zakończony.</span><span class="sxs-lookup"><span data-stu-id="f9121-1865">The value **TX_THREAD_ENTRY** (0x00) indicates the thread was entered, while the value **TX_THREAD_EXIT** (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="f9121-1866">Jeśli ta wartość jest **TX_NULL**, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f9121-1866">If this value is **TX_NULL**, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1867">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1867">Return Values</span></span>

- <span data-ttu-id="f9121-1868">**TX_SUCCESS** (0X00) pomyślnie zarejestrowano funkcję powiadamiania o wejściu/wyjściu wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1868">**TX_SUCCESS** (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="f9121-1869">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1869">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="f9121-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) system został skompilowany z wyłączonymi funkcjami powiadomień.</span><span class="sxs-lookup"><span data-stu-id="f9121-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1871">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1871">Allowed From</span></span>

<span data-ttu-id="f9121-1872">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1872">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1873">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1873">Example</span></span>

```c
TX_THREAD my_thread;
/* Register the "my_entry_exit_notify" function for monitoring
the entry/exit of the thread "my_thread." */
status = tx_thread_entry_exit_notify(&my_thread,
    my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{
    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
        /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
        /* Thread exit! */
}
```

### <a name="see-also"></a><span data-ttu-id="f9121-1874">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1874">See Also</span></span>

- <span data-ttu-id="f9121-1875">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1875">tx_thread_create</span></span>
- <span data-ttu-id="f9121-1876">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1876">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-1877">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1877">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-1878">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-1878">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-1879">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1879">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-1880">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1880">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-1881">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1881">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1882">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1882">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-1883">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1883">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-1884">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-1884">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-1885">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-1885">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-1886">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-1886">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-1887">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-1887">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-1888">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1888">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-1889">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-1889">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-1890">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-1890">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-1891">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1891">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-1892">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-1892">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="f9121-1893">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-1893">tx_thread_identify</span></span>

<span data-ttu-id="f9121-1894">Pobiera wskaźnik do aktualnie wykonywanego wątku</span><span class="sxs-lookup"><span data-stu-id="f9121-1894">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1895">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1895">Prototype</span></span>

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="f9121-1896">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1896">Description</span></span>

<span data-ttu-id="f9121-1897">Ta usługa zwraca wskaźnik do aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1897">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="f9121-1898">Jeśli żaden wątek nie jest wykonywany, ta usługa zwraca wskaźnik o wartości null.</span><span class="sxs-lookup"><span data-stu-id="f9121-1898">If no thread is executing, this service returns a null pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1899">*Jeśli ta usługa jest wywoływana przez funkcję ISR, wartość zwracana reprezentuje wątek uruchomiony przed wykonaniem procedury obsługi przerwań.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1899">*If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1900">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1900">Parameters</span></span>

<span data-ttu-id="f9121-1901">Brak</span><span class="sxs-lookup"><span data-stu-id="f9121-1901">None</span></span>

### <a name="retuen-values"></a><span data-ttu-id="f9121-1902">Retuen wartości</span><span class="sxs-lookup"><span data-stu-id="f9121-1902">Retuen Values</span></span>

- <span data-ttu-id="f9121-1903">**wskaźnik wątku** Wskaźnik do aktualnie wykonywanego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1903">**thread pointer** Pointer to the currently executing thread.</span></span> <span data-ttu-id="f9121-1904">Jeśli żaden wątek nie jest wykonywany, wartość zwracana jest **TX_NULL**.</span><span class="sxs-lookup"><span data-stu-id="f9121-1904">If no thread is executing, the return value is **TX_NULL**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1905">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1905">Allowed From</span></span>

<span data-ttu-id="f9121-1906">Wątki i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1906">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1907">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1907">Preemption Possible</span></span>

<span data-ttu-id="f9121-1908">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-1908">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1909">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1909">Example</span></span>

<span data-ttu-id="f9121-1910">TX_THREAD \* my_thread_ptr;</span><span class="sxs-lookup"><span data-stu-id="f9121-1910">TX_THREAD \*my_thread_ptr;</span></span>

```c
TX_THREAD *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr = tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
from that thread or an ISR that interrupted that thread.
Otherwise, this service was called
from an ISR when no thread was running when the
interrupt occurred. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1911">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1911">See Also</span></span>

- <span data-ttu-id="f9121-1912">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1912">tx_thread_create</span></span>
- <span data-ttu-id="f9121-1913">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1913">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-1914">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1914">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-1915">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1915">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-1916">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1916">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-1917">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1917">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1918">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1918">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-1919">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1919">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-1920">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-1920">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-1921">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-1921">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-1922">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-1922">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-1923">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-1923">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-1924">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1924">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-1925">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-1925">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-1926">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-1926">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-1927">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1927">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-1928">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-1928">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="f9121-1929">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1929">tx_thread_info_get</span></span>

<span data-ttu-id="f9121-1930">Pobierz informacje o wątku</span><span class="sxs-lookup"><span data-stu-id="f9121-1930">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1931">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1931">Prototype</span></span>

```c
UINT tx_thread_info_get(
    TX_THREAD *thread_ptr, 
    CHAR **name,
    UINT *state, 
    ULONG *run_count,
    UINT *priority,
    UINT *preemption_threshold,
    ULONG *time_slice,
    TX_THREAD **next_thread,
    TX_THREAD **suspended_thread);
```

### <a name="description"></a><span data-ttu-id="f9121-1932">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1932">Description</span></span>

<span data-ttu-id="f9121-1933">Ta usługa pobiera informacje o określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1933">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1934">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1934">Parameters</span></span>
- <span data-ttu-id="f9121-1935">**thread_ptr** Wskaźnik do bloku sterowania wątkiem.</span><span class="sxs-lookup"><span data-stu-id="f9121-1935">**thread_ptr** Pointer to thread control block.</span></span>
- <span data-ttu-id="f9121-1936">**Nazwa** Wskaźnik do miejsca docelowego dla wskaźnika do nazwy wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1936">**name** Pointer to destination for the pointer to the thread's name.</span></span>
- <span data-ttu-id="f9121-1937">**stan** Wskaźnik do miejsca docelowego dla bieżącego stanu wykonywania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1937">**state** Pointer to destination for the thread's current execution state.</span></span> <span data-ttu-id="f9121-1938">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="f9121-1938">Possible values are as follows.</span></span>
    - <span data-ttu-id="f9121-1939">**TX_READY** (0x00)</span><span class="sxs-lookup"><span data-stu-id="f9121-1939">**TX_READY** (0x00)</span></span>
    - <span data-ttu-id="f9121-1940">**TX_COMPLETED** (0x01)</span><span class="sxs-lookup"><span data-stu-id="f9121-1940">**TX_COMPLETED** (0x01)</span></span>
    - <span data-ttu-id="f9121-1941">**TX_TERMINATED** (0x02)</span><span class="sxs-lookup"><span data-stu-id="f9121-1941">**TX_TERMINATED** (0x02)</span></span>
    - <span data-ttu-id="f9121-1942">**TX_SUSPENDED** (0x03)</span><span class="sxs-lookup"><span data-stu-id="f9121-1942">**TX_SUSPENDED** (0x03)</span></span>
    - <span data-ttu-id="f9121-1943">**TX_SLEEP** (0x04)</span><span class="sxs-lookup"><span data-stu-id="f9121-1943">**TX_SLEEP** (0x04)</span></span>
    - <span data-ttu-id="f9121-1944">**TX_QUEUE_SUSP** (0x05)</span><span class="sxs-lookup"><span data-stu-id="f9121-1944">**TX_QUEUE_SUSP** (0x05)</span></span>
    - <span data-ttu-id="f9121-1945">**TX_SEMAPHORE_SUSP** (0x06)</span><span class="sxs-lookup"><span data-stu-id="f9121-1945">**TX_SEMAPHORE_SUSP** (0x06)</span></span>
    - <span data-ttu-id="f9121-1946">**TX_EVENT_FLAG** (0x07)</span><span class="sxs-lookup"><span data-stu-id="f9121-1946">**TX_EVENT_FLAG** (0x07)</span></span>
    - <span data-ttu-id="f9121-1947">**TX_BLOCK_MEMORY** (0x08)</span><span class="sxs-lookup"><span data-stu-id="f9121-1947">**TX_BLOCK_MEMORY** (0x08)</span></span>
    - <span data-ttu-id="f9121-1948">**TX_BYTE_MEMORY** (0x09)</span><span class="sxs-lookup"><span data-stu-id="f9121-1948">**TX_BYTE_MEMORY** (0x09)</span></span>
    - <span data-ttu-id="f9121-1949">**TX_MUTEX_SUSP** (0x0D)</span><span class="sxs-lookup"><span data-stu-id="f9121-1949">**TX_MUTEX_SUSP** (0x0D)</span></span>  

- <span data-ttu-id="f9121-1950">**run_count** Wskaźnik do miejsca docelowego dla liczby przebiegów wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1950">**run_count** Pointer to destination for the thread's run count.</span></span>
- <span data-ttu-id="f9121-1951">**priorytet** Wskaźnik do miejsca docelowego dla priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1951">**priority** Pointer to destination for the thread's priority.</span></span>
- <span data-ttu-id="f9121-1952">**preemption_threshold** Wskaźnik do miejsca docelowego dla progu zastępujący wątek.</span><span class="sxs-lookup"><span data-stu-id="f9121-1952">**preemption_threshold** Pointer to destination for the thread's preemption-threshold.</span></span>
<span data-ttu-id="f9121-1953">**time_slice** Wskaźnik do miejsca docelowego dla wycinka czasu wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1953">**time_slice** Pointer to destination for the thread's time-slice.</span></span>
<span data-ttu-id="f9121-1954">**next_thread** Wskaźnik do miejsca docelowego dla następnego utworzonego wskaźnika wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1954">**next_thread** Pointer to destination for next created thread pointer.</span></span>

<span data-ttu-id="f9121-1955">**suspended_thread** Wskaźnik do miejsca docelowego dla wskaźnika do następnego wątku na liście zawieszeń.</span><span class="sxs-lookup"><span data-stu-id="f9121-1955">**suspended_thread** Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-1956">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-1956">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-1957">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-1957">Return Values</span></span>

- <span data-ttu-id="f9121-1958">**TX_SUCCESS** (0X00) pomyślne pobranie informacji wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1958">**TX_SUCCESS** (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="f9121-1959">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik kontrolny wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1959">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-1960">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-1960">Allowed From</span></span>

<span data-ttu-id="f9121-1961">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-1961">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-1962">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-1962">Preemption Possible</span></span>

<span data-ttu-id="f9121-1963">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-1963">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-1964">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-1964">Example</span></span>

```c
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
thread "my_thread." */

status = tx_thread_info_get(&my_thread, &name,
    &state, &run_count,
    &priority, &preemption_threshold,
    &time_slice, &next_thread,&suspended_thread);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-1965">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-1965">See Also</span></span>

- <span data-ttu-id="f9121-1966">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-1966">tx_thread_create</span></span>
- <span data-ttu-id="f9121-1967">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-1967">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-1968">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1968">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-1969">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-1969">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-1970">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1970">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-1971">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1971">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-1972">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1972">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-1973">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1973">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-1974">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-1974">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-1975">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-1975">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-1976">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-1976">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-1977">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-1977">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-1978">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-1978">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-1979">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-1979">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-1980">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-1980">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-1981">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-1981">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-1982">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-1982">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="f9121-1983">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-1983">tx_thread_performance_info_get</span></span>

<span data-ttu-id="f9121-1984">Pobierz informacje o wydajności wątków</span><span class="sxs-lookup"><span data-stu-id="f9121-1984">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-1985">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-1985">Prototype</span></span>

```c
UINT tx_thread_performance_info_get(
    TX_THREAD *thread_ptr,
    LONG *resumptions, 
    ULONG *suspensions,
    ULONG *solicited_preemptions, 
    ULONG *interrupt_preemptions,
    ULONG *priority_inversions, 
    ULONG *time_slices,
    ULONG *relinquishes, 
    ULONG *timeouts, 
    ULONG *wait_aborts,
    TX_THREAD **last_preempted_by);
```

### <a name="description"></a><span data-ttu-id="f9121-1986">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-1986">Description</span></span>

<span data-ttu-id="f9121-1987">Ta usługa pobiera informacje o wydajności dotyczące określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1987">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-1988">*Biblioteka i aplikacja ThreadX muszą być kompilowane przy użyciu*  \* **TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined w celu zwrócenia informacji o wydajności przez tę usługę \*</span><span class="sxs-lookup"><span data-stu-id="f9121-1988">*The ThreadX library and application must be built with* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-1989">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-1989">Parameters</span></span>
- <span data-ttu-id="f9121-1990">**thread_ptr** Wskaźnik do wcześniej utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1990">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="f9121-1991">**wznowień** Wskaźnik do miejsca docelowego dla liczby wznowień tego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1991">**resumptions** Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="f9121-1992">**zawieszenie** Wskaźnik do miejsca docelowego dla liczby zawieszeń tego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1992">**suspensions** Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="f9121-1993">**solicited_preemptions** Wskaźnik do miejsca docelowego dla liczby przeniesień w wyniku wywołania usługi API ThreadX wykonanego przez ten wątek.</span><span class="sxs-lookup"><span data-stu-id="f9121-1993">**solicited_preemptions** Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="f9121-1994">**interrupt_preemptions** Wskaźnik do miejsca docelowego dla liczby przeniesień tego wątku w wyniku przetwarzania przerwań.</span><span class="sxs-lookup"><span data-stu-id="f9121-1994">**interrupt_preemptions** Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="f9121-1995">**priority_inversions** Wskaźnik do miejsca docelowego dla liczby wersji priorytetu tego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1995">**priority_inversions** Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="f9121-1996">**time_slices** Wskaźnik do miejsca docelowego dla liczby wycinków czasu tego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1996">**time_slices** Pointer to destination for the number of time-slices of this thread.</span></span>
- <span data-ttu-id="f9121-1997"> braki Wskaźnik do miejsca docelowego dla liczby operacji zwalniania wątku wykonywanych przez ten wątek.</span><span class="sxs-lookup"><span data-stu-id="f9121-1997">**relinquishes** Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="f9121-1998">**limity czasu** Wskaźnik do miejsca docelowego dla liczby limitów czasu zawieszenia dla tego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1998">**timeouts** Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="f9121-1999">**wait_aborts** Wskaźnik do miejsca docelowego dla liczby przerwań oczekiwania wykonanych w tym wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-1999">**wait_aborts** Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="f9121-2000">**last_preempted_by** Wskaźnik do miejsca docelowego dla wskaźnika wątku, który ostatnio zastępują ten wątek.</span><span class="sxs-lookup"><span data-stu-id="f9121-2000">**last_preempted_by** Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2001">*Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2001">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2002">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2002">Return Values</span></span>

- <span data-ttu-id="f9121-2003">Pobieranie pomyślnej wydajności wątku **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-2003">**TX_SUCCESS** (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="f9121-2004">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2004">**TX_PTR_ERROR** (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="f9121-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2006">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2006">Allowed From</span></span>

<span data-ttu-id="f9121-2007">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2007">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2008">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2008">Example</span></span>

```c
TX_THREAD my_thread;
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
TX_THREAD *last_preempted_by;

/* Retrieve performance information on the previously created
thread. */

status = tx_thread_performance_info_get(&my_thread, &resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices,
    &relinquishes, &timeouts,
    &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2009">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2009">See Also</span></span>

- <span data-ttu-id="f9121-2010">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2010">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2011">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2011">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2012">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2012">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2013">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2013">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2014">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2014">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2015">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2015">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-2016">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2016">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2017">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2017">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2018">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2018">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2019">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2019">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2020">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2020">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2021">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2021">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2022">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2022">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2023">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2023">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2024">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2024">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2025">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2025">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2026">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2026">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="f9121-2027">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2027">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="f9121-2028">Pobierz informacje o wydajności systemu wątków</span><span class="sxs-lookup"><span data-stu-id="f9121-2028">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2029">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2029">Prototype</span></span>

```c
UINT tx_thread_performance_system_info_get(
    ULONG *resumptions,
    ULONG *suspensions, 
    ULONG *solicited_preemptions,
    ULONG *interrupt_preemptions, 
    ULONG *priority_inversions,
    ULONG *time_slices, 
    ULONG *relinquishes, 
    ULONG *timeouts,
    ULONG *wait_aborts, 
    ULONG *non_idle_returns,
    ULONG *idle_returns);
```

### <a name="description"></a><span data-ttu-id="f9121-2030">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2030">Description</span></span>

<span data-ttu-id="f9121-2031">Ta usługa pobiera informacje o wydajności wszystkich wątków w systemie.</span><span class="sxs-lookup"><span data-stu-id="f9121-2031">This service retrieves performance information about all the threads in the system.</span></span>

<span data-ttu-id="f9121-2032">*Biblioteka i aplikacja ThreadX muszą być kompilowane przy użyciu*</span><span class="sxs-lookup"><span data-stu-id="f9121-2032">*The ThreadX library and application must be built with*</span></span>

<span data-ttu-id="f9121-2033">\***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined w celu zwrócenia informacji o wydajności przez tę usługę \*</span><span class="sxs-lookup"><span data-stu-id="f9121-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2034">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2034">Parameters</span></span>

- <span data-ttu-id="f9121-2035">**wznowień** Wskaźnik do miejsca docelowego dla łącznej liczby wznowień wątków.</span><span class="sxs-lookup"><span data-stu-id="f9121-2035">**resumptions** Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="f9121-2036">**zawieszenie** Wskaźnik do miejsca docelowego dla łącznej liczby zawieszeń wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2036">**suspensions** Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="f9121-2037">**solicited_preemptions** Wskaźnik do miejsca docelowego dla łącznej liczby zastępujący wątków w wyniku wątku wywołującego usługę API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="f9121-2037">**solicited_preemptions** Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="f9121-2038">**interrupt_preemptions** Wskaźnik do miejsca docelowego dla łącznej liczby przeniesień wątków w wyniku przetwarzania przerwań.</span><span class="sxs-lookup"><span data-stu-id="f9121-2038">**interrupt_preemptions** Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="f9121-2039">**priority_inversions** Wskaźnik do miejsca docelowego dla łącznej liczby niewersji priorytetu wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2039">**priority_inversions** Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="f9121-2040">**time_slices** Wskaźnik do miejsca docelowego dla łącznej liczby wycinków czasu wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2040">**time_slices** Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="f9121-2041"> braki Wskaźnik do miejsca docelowego dla łącznej liczby prób wątków.</span><span class="sxs-lookup"><span data-stu-id="f9121-2041">**relinquishes** Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="f9121-2042">**limity czasu** Wskaźnik do miejsca docelowego dla łącznej liczby limitów czasu zawieszenia wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2042">**timeouts** Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="f9121-2043">**wait_aborts** Wskaźnik do miejsca docelowego dla łącznej liczby przerwań oczekiwania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2043">**wait_aborts** Pointer to destination for the total number of thread wait aborts.</span></span>
- <span data-ttu-id="f9121-2044">**non_idle_returns** Wskaźnik do miejsca docelowego dla czasu, przez który wątek wraca do systemu, gdy inny wątek jest gotowy do wykonania.</span><span class="sxs-lookup"><span data-stu-id="f9121-2044">**non_idle_returns** Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span>
- <span data-ttu-id="f9121-2045">**idle_returns** Wskaźnik do miejsca docelowego dla czasu, przez który wątek wraca do systemu, gdy żaden inny wątek nie jest gotowy do wykonania (bezczynny system).</span><span class="sxs-lookup"><span data-stu-id="f9121-2045">**idle_returns** Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2046">*Dostarczenie **TX_NULL** dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2046">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2047">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2047">Return Values</span></span>

- <span data-ttu-id="f9121-2048">**TX_SUCCESS** (0X00) pomyślne pobieranie wydajności systemu wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2048">**TX_SUCCESS** (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="f9121-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2050">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2050">Allowed From</span></span>

<span data-ttu-id="f9121-2051">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2051">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2052">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2052">Example</span></span>

```c
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
ULONG non_idle_returns;
ULONG idle_returns;

/* Retrieve performance information on all previously created
thread. */

status = tx_thread_performance_system_info_get(&resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices, &relinquishes,
    &timeouts, &wait_aborts, &non_idle_returns,
    &idle_returns);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2053">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2053">See Also</span></span>

- <span data-ttu-id="f9121-2054">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2054">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2055">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2055">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2056">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2056">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2057">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2057">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2058">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2058">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2059">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2059">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2060">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2060">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2061">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2061">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2062">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2062">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2063">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2063">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2064">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2064">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2065">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2065">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2066">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2066">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2067">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2067">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2068">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2068">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2069">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2069">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2070">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2070">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="f9121-2071">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2071">tx_thread_preemption_change</span></span>

<span data-ttu-id="f9121-2072">Zmiana zastępujący — próg wątku aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2072">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2073">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2073">Prototype</span></span>

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a><span data-ttu-id="f9121-2074">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2074">Description</span></span>

<span data-ttu-id="f9121-2075">Ta usługa zmienia próg przekroczenia określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2075">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="f9121-2076">Próg zastępujący uniemożliwia przestawianie określonego wątku przez wątki równe lub mniejsze od wartości progowej przekroczenia.</span><span class="sxs-lookup"><span data-stu-id="f9121-2076">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

>[!NOTE]
> <span data-ttu-id="f9121-2077">*Użycie wartości progowej przekroczenia powoduje wyłączenie wycinka czasu dla określonego wątku.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2077">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2078">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2078">Parameters</span></span>
- <span data-ttu-id="f9121-2079">**thread_ptr** Wskaźnik do wcześniej utworzonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2079">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="f9121-2080">**new_threshold** Nowy przechodzenie — poziom priorytetu progu (od 0 do TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="f9121-2080">**new_threshold** New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="f9121-2081">**old_threshold** Wskaźnik do lokalizacji, aby przywrócić poprzedni próg zastępujący.</span><span class="sxs-lookup"><span data-stu-id="f9121-2081">**old_threshold** Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2082">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2082">Return Values</span></span>

- <span data-ttu-id="f9121-2083">Pomyślna zmiana progu **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-2083">**TX_SUCCESS** (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="f9121-2084">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2084">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="f9121-2085">**TX_THRESH_ERROR** (0X18) określony nowy próg przechodzenia nie jest prawidłowym priorytetem wątku (wartość inna niż (od 0 do (**TX_MAX_PRIORITIES**-1)) lub jest większa niż (niższy priorytet) niż bieżący priorytet wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2085">**TX_THRESH_ERROR** (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (**TX_MAX_PRIORITIES**-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="f9121-2086">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik do poprzedniej lokalizacji magazynu preemptionthreshold.</span><span class="sxs-lookup"><span data-stu-id="f9121-2086">**TX_PTR_ERROR** (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="f9121-2087">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2087">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2088">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2088">Allowed From</span></span>

<span data-ttu-id="f9121-2089">Wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="f9121-2089">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2090">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2090">Preemption Possible</span></span>

<span data-ttu-id="f9121-2091">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-2091">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2092">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2092">Example</span></span>

```c
TX_THREAD my_thread;
UINT my_old_threshold;
UINT status;

/* Disable all preemption of the specified thread. The
current preemption-threshold is returned in
"my_old_threshold". Assume that "my_thread" has
already been created. */

status = tx_thread_preemption_change(&my_thread,
    0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
non-preemptable by another thread. Note that ISRs are
not prevented by preemption disabling. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2093">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2093">See Also</span></span>

- <span data-ttu-id="f9121-2094">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2094">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2095">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2095">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2096">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2096">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2097">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2097">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2098">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2098">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2099">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2099">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2100">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2100">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-2101">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2101">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2102">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2102">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2103">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2103">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2104">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2104">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2105">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2105">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2106">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2106">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2107">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2107">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2108">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2108">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2109">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2109">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2110">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2110">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="f9121-2111">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2111">tx_thread_priority_change</span></span>

<span data-ttu-id="f9121-2112">Zmień priorytet wątku aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2112">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2113">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2113">Prototype</span></span>

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a><span data-ttu-id="f9121-2114">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2114">Description</span></span>

<span data-ttu-id="f9121-2115">Ta usługa zmienia priorytet określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2115">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="f9121-2116">Prawidłowy zakres priorytetów należy do zakresu od 0 do (TX_MAX_PRIORITES-1), gdzie 0 oznacza najwyższy poziom priorytetu.</span><span class="sxs-lookup"><span data-stu-id="f9121-2116">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-2117">\* Próg przekroczenia określonego wątku jest automatycznie ustawiany na nowy priorytet.</span><span class="sxs-lookup"><span data-stu-id="f9121-2117">\*The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="f9121-2118">W przypadku pożądanego nowego progu należy użyć usługi \***tx_thread_preemption_change** _ po tym Call._</span><span class="sxs-lookup"><span data-stu-id="f9121-2118">If a new threshold is desired, the \***tx_thread_preemption_change** _ service must be used after this call._</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2119">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2119">Parameters</span></span>

- <span data-ttu-id="f9121-2120">**thread_ptr** Wskaźnik do wcześniej utworzonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2120">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="f9121-2121">**new_priority** Nowy poziom priorytetu wątku (od 0 do TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="f9121-2121">**new_priority** New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="f9121-2122">**old_priority** Wskaźnik do lokalizacji, aby przywrócić poprzedni priorytet wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2122">**old_priority** Pointer to a location to return the thread's previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2123">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2123">Return Values</span></span>

- <span data-ttu-id="f9121-2124">Pomyślna zmiana priorytetu **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-2124">**TX_SUCCESS** (0x00) Successful priority change.</span></span>
- <span data-ttu-id="f9121-2125">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2125">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="f9121-2126">**TX_PRIORITY_ERROR** (0X0F) określony nowy priorytet jest nieprawidłowy (wartość inna niż (od 0 do (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="f9121-2126">**TX_PRIORITY_ERROR** (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="f9121-2127">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik do lokalizacji magazynu o poprzednim priorytecie.</span><span class="sxs-lookup"><span data-stu-id="f9121-2127">**TX_PTR_ERROR** (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="f9121-2128">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2128">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2129">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2129">Allowed From</span></span>

<span data-ttu-id="f9121-2130">Wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="f9121-2130">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2131">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2131">Preemption Possible</span></span>

<span data-ttu-id="f9121-2132">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-2132">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2133">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2133">Example</span></span>

```c
TX_THREAD my_thread;
UINT my_old_priority;
UINT status;

/* Change the thread represented by "my_thread" to priority
0. */

status = tx_thread_priority_change(&my_thread,
    0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
now at the highest priority level in the system. */
```
### <a name="see-also"></a><span data-ttu-id="f9121-2134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2134">See Also</span></span>

- <span data-ttu-id="f9121-2135">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2135">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2136">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2136">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2137">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2137">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2138">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2138">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2139">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2139">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2140">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2140">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2141">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2141">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-2142">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2142">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2143">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2143">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2144">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2144">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2145">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2145">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2146">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2146">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2147">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2147">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2148">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2148">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2149">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2149">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2150">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2150">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2151">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2151">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="f9121-2152">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2152">tx_thread_relinquish</span></span>

<span data-ttu-id="f9121-2153">Zwalnianie kontroli do innych wątków aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2153">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2154">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2154">Prototype</span></span>

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a><span data-ttu-id="f9121-2155">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2155">Description</span></span>

<span data-ttu-id="f9121-2156">Ta usługa zrzeka kontrolę procesora do innych gotowych do uruchomienia wątków o tym samym lub wyższym priorytecie.</span><span class="sxs-lookup"><span data-stu-id="f9121-2156">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2157">*Oprócz przepisywania kontroli do wątków o takim samym priorytecie, ta usługa również zwalnia z wykonywania kontroli nad wątkiem o najwyższym priorytecie z powodu ustawienia progu przekroczenia bieżącego wątku.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2157">*In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2158">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2158">Parameters</span></span>

<span data-ttu-id="f9121-2159">Brak</span><span class="sxs-lookup"><span data-stu-id="f9121-2159">None</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2160">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2160">Return Values</span></span>

<span data-ttu-id="f9121-2161">Brak</span><span class="sxs-lookup"><span data-stu-id="f9121-2161">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2162">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2162">Allowed From</span></span>

<span data-ttu-id="f9121-2163">Wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-2163">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2164">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2164">Preemption Possible</span></span>

<span data-ttu-id="f9121-2165">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-2165">Yes</span></span>

### <a name="examples"></a><span data-ttu-id="f9121-2166">Przykłady</span><span class="sxs-lookup"><span data-stu-id="f9121-2166">Examples</span></span>

```c
ULONG run_counter_1 = 0;
ULONG run_counter_2 = 0;

/* Example of two threads relinquishing control to
each other in an infinite loop. Assume that
both of these threads are ready and have the same
priority. The run counters will always stay within one
of each other. */

VOID my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{

    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```

### <a name="see-also"></a><span data-ttu-id="f9121-2167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2167">See Also</span></span>

- <span data-ttu-id="f9121-2168">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2168">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2169">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2169">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2170">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2170">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2171">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2171">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2172">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2172">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2173">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2173">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2174">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2174">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-2175">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2175">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2176">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2176">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2177">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2177">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2178">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2178">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2179">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2179">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2180">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2180">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2181">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2181">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2182">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2182">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2183">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2183">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2184">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2184">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="f9121-2185">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2185">tx_thread_reset</span></span>

<span data-ttu-id="f9121-2186">Zresetuj wątek</span><span class="sxs-lookup"><span data-stu-id="f9121-2186">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2187">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2187">Prototype</span></span>

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-2188">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2188">Description</span></span>

<span data-ttu-id="f9121-2189">Ta usługa resetuje określony wątek do wykonania w punkcie wejścia zdefiniowanym podczas tworzenia wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2189">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="f9121-2190">Aby można było zresetować wątek, musi on być w stanie **TX_COMPLETED** lub **TX_TERMINATED**</span><span class="sxs-lookup"><span data-stu-id="f9121-2190">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-2191">*Wątek należy wznowić, aby można było wykonać operację ponownie.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2191">*The thread must be resumed for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2192">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2192">Parameters</span></span>

- <span data-ttu-id="f9121-2193">**thread_ptr** Wskaźnik do wcześniej utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2193">**thread_ptr** Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2194">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2194">Return Values</span></span>

- <span data-ttu-id="f9121-2195">Pomyślnie zresetowano wątek **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-2195">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="f9121-2196">Określony wątek **TX_NOT_DONE** (0x20) nie jest w stanie **TX_COMPLETED** lub **TX_TERMINATED** .</span><span class="sxs-lookup"><span data-stu-id="f9121-2196">**TX_NOT_DONE** (0x20) Specified thread is not in a **TX_COMPLETED** or **TX_TERMINATED** state.</span></span>
- <span data-ttu-id="f9121-2197">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2197">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="f9121-2198">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2198">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2199">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2199">Allowed From</span></span>

<span data-ttu-id="f9121-2200">Wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-2200">Threads</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2201">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2201">Example</span></span>

<span data-ttu-id="f9121-2202">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="f9121-2202">TX_THREAD my_thread;</span></span>

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2203">See Also</span></span>

- <span data-ttu-id="f9121-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2204">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2205">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2207">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2210">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2210">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="f9121-2211">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2211">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2212">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2212">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2213">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2213">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2214">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="f9121-2221">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2221">tx_thread_resume</span></span>

<span data-ttu-id="f9121-2222">Wznów zawieszony wątek aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2222">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2223">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2223">Prototype</span></span>

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-2224">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2224">Description</span></span>

<span data-ttu-id="f9121-2225">Ta usługa wznawia lub przygotowuje do wykonania wątek, który został wcześniej zawieszony przez wywołanie ***tx_thread_suspend*** .</span><span class="sxs-lookup"><span data-stu-id="f9121-2225">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="f9121-2226">Ponadto ta usługa wznawia wątki, które zostały utworzone bez automatycznego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="f9121-2226">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2227">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2227">Parameters</span></span>

- <span data-ttu-id="f9121-2228">**thread_ptr** Wskaźnik do zawieszonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2228">**thread_ptr** Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2229">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2229">Return Values</span></span>

- <span data-ttu-id="f9121-2230">Pomyślna wznowienie wątku **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-2230">**TX_SUCCESS** (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="f9121-2231">**TX_SUSPEND_LIFTED** (0X19) poprzednio ustawić opóźnione zawieszenie zostało zniesione.</span><span class="sxs-lookup"><span data-stu-id="f9121-2231">**TX_SUSPEND_LIFTED** (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="f9121-2232">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2232">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="f9121-2233">Określony wątek **TX_RESUME_ERROR** (0x12) nie jest wstrzymany lub został wcześniej zawieszony przez usługę inną niż **_tx_thread_suspend_**.</span><span class="sxs-lookup"><span data-stu-id="f9121-2233">**TX_RESUME_ERROR** (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2234">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2234">Allowed From</span></span>

<span data-ttu-id="f9121-2235">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2235">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2236">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2236">Preemption Possible</span></span>

<span data-ttu-id="f9121-2237">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-2237">Yes</span></span>

<span data-ttu-id="f9121-2238">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="f9121-2238">TX_THREAD my_thread;</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2239">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2239">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2240">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2240">See Also</span></span>

- <span data-ttu-id="f9121-2241">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2241">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2242">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2242">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2243">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2243">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2244">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2244">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2245">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2245">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2246">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2246">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2247">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2247">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-2248">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2248">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2249">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2249">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2250">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2250">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2251">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2251">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2252">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2252">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2253">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2253">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2254">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2254">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2255">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2255">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2256">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2256">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2257">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2257">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="f9121-2258">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2258">tx_thread_sleep</span></span>

<span data-ttu-id="f9121-2259">Zawieś bieżący wątek przez określony czas</span><span class="sxs-lookup"><span data-stu-id="f9121-2259">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2260">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2260">Prototype</span></span>

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a><span data-ttu-id="f9121-2261">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2261">Description</span></span>

<span data-ttu-id="f9121-2262">Ta usługa powoduje zawieszenie wątku wywołującego dla określonej liczby taktów czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2262">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="f9121-2263">Czas fizyczny skojarzony z cyklem czasomierza jest specyficzny dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2263">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="f9121-2264">Ta usługa może być wywoływana tylko z wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2264">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2265">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2265">Parameters</span></span>

- <span data-ttu-id="f9121-2266">**timer_ticks** Liczba cykli czasomierza zawieszenia wątku aplikacji wywołującej z zakresu od 0 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="f9121-2266">**timer_ticks** The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="f9121-2267">Jeśli określono wartość 0, usługa wraca natychmiast.</span><span class="sxs-lookup"><span data-stu-id="f9121-2267">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2268">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2268">Return Values</span></span>

- <span data-ttu-id="f9121-2269">**TX_SUCCESS** (0X00) powodzenie uśpienia wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2269">**TX_SUCCESS** (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="f9121-2270">Zawieszenie **TX_WAIT_ABORTED** (0x1A) zostało przerwane przez inny wątek, czasomierz lub proces ISR.</span><span class="sxs-lookup"><span data-stu-id="f9121-2270">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="f9121-2271">Usługa **TX_CALLER_ERROR** (0x13) wywołana z elementu niebędącego wątkiem.</span><span class="sxs-lookup"><span data-stu-id="f9121-2271">**TX_CALLER_ERROR** (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2272">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2272">Allowed From</span></span>

<span data-ttu-id="f9121-2273">Wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2274">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2274">Preemption Possible</span></span>

<span data-ttu-id="f9121-2275">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2276">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2276">Example</span></span>

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2277">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2277">See Also</span></span>

- <span data-ttu-id="f9121-2278">tx_thread_create, tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2278">tx_thread_create, tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2279">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2279">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2280">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2280">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2281">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2281">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2282">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2282">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2283">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2283">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-2284">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2284">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2285">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2285">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2286">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2286">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2287">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2288">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2289">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2289">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2290">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2290">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2291">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2291">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2292">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2292">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2293">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2293">tx_thread_wait_abort</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="f9121-2294">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2294">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="f9121-2295">Wywołanie zwrotne powiadomienia o błędzie stosu rejestracji</span><span class="sxs-lookup"><span data-stu-id="f9121-2295">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2296">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2296">Prototype</span></span>

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a><span data-ttu-id="f9121-2297">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2297">Description</span></span>

<span data-ttu-id="f9121-2298">Ta usługa rejestruje funkcję wywołania zwrotnego powiadomienia do obsługi błędów stosu wątków.</span><span class="sxs-lookup"><span data-stu-id="f9121-2298">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="f9121-2299">Gdy ThreadX wykrywa błąd stosu wątku podczas wykonywania, wywoła tę funkcję powiadamiania w celu przetworzenia błędu.</span><span class="sxs-lookup"><span data-stu-id="f9121-2299">When ThreadX detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="f9121-2300">Przetwarzanie błędu jest całkowicie zdefiniowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="f9121-2300">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="f9121-2301">Wszystkie elementy od zawieszenia naruszenia wątku w celu zresetowania całego systemu mogą zostać wykonane.</span><span class="sxs-lookup"><span data-stu-id="f9121-2301">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-2302">*Biblioteka ThreadX musi być skompilowana przy użyciu* **TX_ENABLE_STACK_CHECKING** *zdefiniowanej w celu zwrócenia informacji o wydajności przez tę usługę.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2302">*The ThreadX library must be built with* **TX_ENABLE_STACK_CHECKING** *defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2303">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2303">Parameters</span></span>
- <span data-ttu-id="f9121-2304">**error_handler** Wskaźnik do funkcji obsługi błędów stosu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2304">**error_handler** Pointer to application's stack error handling function.</span></span> <span data-ttu-id="f9121-2305">Jeśli ta wartość jest TX_NULL, powiadomienie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="f9121-2305">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2306">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2306">Return Values</span></span>

- <span data-ttu-id="f9121-2307">Pomyślnie zresetowano wątek **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-2307">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="f9121-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2309">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2309">Allowed From</span></span>

<span data-ttu-id="f9121-2310">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2310">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2311">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2311">Example</span></span>

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a><span data-ttu-id="f9121-2312">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2312">See Also</span></span>

- <span data-ttu-id="f9121-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2313">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2314">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2316">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2319">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2319">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="f9121-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2323">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2323">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2324">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2324">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2325">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2325">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="f9121-2330">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2330">tx_thread_suspend</span></span>

<span data-ttu-id="f9121-2331">Wstrzymywanie wątku aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2331">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2332">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2332">Prototype</span></span>

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-2333">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2333">Description</span></span>

<span data-ttu-id="f9121-2334">Ta usługa wstrzymuje określony wątek aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2334">This service suspends the specified application thread.</span></span> <span data-ttu-id="f9121-2335">Wątek może wywołać tę usługę, aby zawiesić się.</span><span class="sxs-lookup"><span data-stu-id="f9121-2335">A thread may call this service to suspend itself.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2336">*Jeśli określony wątek został już zawieszony z innego powodu, to zawieszenie jest przechowywane wewnętrznie do momentu zniesienia wcześniejszego zawieszenia. W takim przypadku wykonywane jest niewarunkowe zawieszenie określonego wątku. Dalsze niewarunkowe żądania zawieszenia nie mają żadnego wpływu.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2336">*If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted. When that happens, this unconditional suspension of the specified thread is performed. Further unconditional suspension requests have no effect.*</span></span>

<span data-ttu-id="f9121-2337">Po wstrzymaniu wątek musi zostać wznowiony przez ***tx_thread_resume*** , aby wykonać operację ponownie.</span><span class="sxs-lookup"><span data-stu-id="f9121-2337">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2338">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2338">Parameters</span></span>

- <span data-ttu-id="f9121-2339">**thread_ptr** Wskaźnik do wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2339">**thread_ptr** Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2340">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2340">Return Values</span></span>

- <span data-ttu-id="f9121-2341">Pomyślne zawieszenie wątku **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-2341">**TX_SUCCESS** (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="f9121-2342">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2342">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="f9121-2343">**TX_SUSPEND_ERROR** (0X14) określony wątek jest w stanie przerwana lub ukończona.</span><span class="sxs-lookup"><span data-stu-id="f9121-2343">**TX_SUSPEND_ERROR** (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="f9121-2344">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2344">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2345">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2345">Allowed From</span></span>

<span data-ttu-id="f9121-2346">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2346">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2347">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2347">Preemption Possible</span></span>

<span data-ttu-id="f9121-2348">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-2348">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2349">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2349">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2350">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2350">See Also</span></span>

- <span data-ttu-id="f9121-2351">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2351">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2352">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2352">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2353">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2353">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2354">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2354">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2355">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2355">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2356">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2356">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2357">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2357">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-2358">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2358">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2359">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2359">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2360">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2360">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2361">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2361">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2362">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2362">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2363">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2363">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2364">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2364">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2365">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2365">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2366">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2366">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2367">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2367">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="f9121-2368">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2368">tx_thread_terminate</span></span>

<span data-ttu-id="f9121-2369">Przerywa wątek aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2369">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2370">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2370">Prototype</span></span>

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="f9121-2371">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2371">Description</span></span>

<span data-ttu-id="f9121-2372">Ta usługa przerywa określony wątek aplikacji niezależnie od tego, czy wątek jest wstrzymany, czy nie.</span><span class="sxs-lookup"><span data-stu-id="f9121-2372">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="f9121-2373">Wątek może wywoływać tę usługę, aby zakończyć działanie.</span><span class="sxs-lookup"><span data-stu-id="f9121-2373">A thread may call this service to terminate itself.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2374">*Jest to odpowiedzialność aplikacji, aby upewnić się, że wątek jest w stanie odpowiednim do zakończenia. Na przykład wątek nie powinien być zakończony podczas krytycznego przetwarzania aplikacji lub wewnątrz innych składników oprogramowania pośredniczącego, w którym może to spowodować, że przetwarzanie jest nieznane.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2374">*It is the application's responsibility to ensure that the thread is in a state suitable for termination. For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-2375">*Po zakończeniu należy zresetować wątek, aby można było wykonać operację ponownie.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2375">*After being terminated, the thread must be reset for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2376">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2376">Parameters</span></span>

- <span data-ttu-id="f9121-2377">**thread_ptr** Wskaźnik do wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2377">**thread_ptr** Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2378">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2378">Return Values</span></span>
- <span data-ttu-id="f9121-2379">Pomyślna przerwanie wątku **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-2379">**TX_SUCCESS** (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="f9121-2380">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2380">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="f9121-2381">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2381">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2382">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2382">Allowed From</span></span>

<span data-ttu-id="f9121-2383">Wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="f9121-2383">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2384">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2384">Preemption Possible</span></span>

<span data-ttu-id="f9121-2385">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-2385">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2386">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2386">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2387">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2387">See Also</span></span>

- <span data-ttu-id="f9121-2388">tx_thread_create tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2388">tx_thread_create tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2389">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2389">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2390">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2390">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2391">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2391">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2392">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2392">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2393">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2393">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-2394">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2394">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2395">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2395">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2396">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2396">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2397">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2397">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2398">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2398">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2399">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2399">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2400">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2400">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2401">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2401">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2402">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2402">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="f9121-2403">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2403">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="f9121-2404">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2404">tx_thread_time_slice_change</span></span>

<span data-ttu-id="f9121-2405">Zmienia czas wycinka wątku aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2405">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2406">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2406">Prototype</span></span>

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a><span data-ttu-id="f9121-2407">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2407">Description</span></span>

<span data-ttu-id="f9121-2408">Ta usługa zmienia wycinek czasu określonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2408">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="f9121-2409">Wybranie wycinka czasu dla wątku polega na tym, że nie będzie działać więcej niż określona liczba taktów czasomierza, zanim inne wątki o tych samych lub wyższych priorytetach mają szansę na wykonanie.</span><span class="sxs-lookup"><span data-stu-id="f9121-2409">Selecting a time-slice for a thread insures that it won't execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2410">*Użycie wartości progowej przekroczenia powoduje wyłączenie wycinka czasu dla określonego wątku.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2410">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2411">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2411">Parameters</span></span>

- <span data-ttu-id="f9121-2412">**thread_ptr** Wskaźnik do wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2412">**thread_ptr** Pointer to application thread.</span></span>
- <span data-ttu-id="f9121-2413">**new_time_slice** Nowa wartość wycinka czasu.</span><span class="sxs-lookup"><span data-stu-id="f9121-2413">**new_time_slice** New time slice value.</span></span> <span data-ttu-id="f9121-2414">Wartości prawne obejmują TX_NO_TIME_SLICE i wartości liczbowe z przedziału od 1 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="f9121-2414">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="f9121-2415">**old_time_slice** Wskaźnik do lokalizacji przechowywania poprzedniej wartości timeslice określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2415">**old_time_slice** Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2416">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2416">Return Values</span></span>

- <span data-ttu-id="f9121-2417">**TX_SUCCESS** (0x00) pomyślny czas odcięcia.</span><span class="sxs-lookup"><span data-stu-id="f9121-2417">**TX_SUCCESS** (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="f9121-2418">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2418">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="f9121-2419">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik do poprzedniej lokalizacji przechowywania wycinków czasu.</span><span class="sxs-lookup"><span data-stu-id="f9121-2419">**TX_PTR_ERROR** (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="f9121-2420">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2420">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2421">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2421">Allowed From</span></span>

<span data-ttu-id="f9121-2422">Wątki i czasomierze</span><span class="sxs-lookup"><span data-stu-id="f9121-2422">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2423">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2423">Preemption Possible</span></span>

<span data-ttu-id="f9121-2424">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-2424">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2425">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2425">Example</span></span>

```c
TX_THREAD my_thread;
ULONG my_old_time_slice;
UINT status;

/* Change the time-slice of the thread associated with
"my_thread" to 20. This will mean that "my_thread"
can only run for 20 timer-ticks consecutively before
other threads of equal or higher priority get a chance
to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
    &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
has been changed to 20 and the previous time-slice is
in "my_old_time_slice." */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2426">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2426">See Also</span></span>

- <span data-ttu-id="f9121-2427">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2427">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2428">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2428">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2429">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2429">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2430">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2430">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2431">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2431">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2432">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2432">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2433">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2433">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-2434">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2434">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2435">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2435">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2436">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2436">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2437">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2437">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2438">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2438">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2439">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2439">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2440">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2440">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2441">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2441">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2442">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2442">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2443">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2443">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="f9121-2444">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="f9121-2444">tx_thread_wait_abort</span></span>

<span data-ttu-id="f9121-2445">Przerwij zawieszenie określonego wątku</span><span class="sxs-lookup"><span data-stu-id="f9121-2445">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2446">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2446">Prototype</span></span>

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-2447">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2447">Description</span></span>

<span data-ttu-id="f9121-2448">Ta usługa przerywa pracę w stanie uśpienia lub dowolnego innego obiektu zawieszania określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2448">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="f9121-2449">W przypadku przerwania oczekiwania zostanie zwrócona wartość **TX_WAIT_ABORTED** z usługi, w której wątek oczekiwał.</span><span class="sxs-lookup"><span data-stu-id="f9121-2449">If the wait is aborted, a **TX_WAIT_ABORTED** value is returned from the service that the thread was waiting on.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2450">*Ta usługa nie zwalnia jawnego zawieszenia wykonywanego przez usługę tx_thread_suspend.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2450">*This service does not release explicit suspension that is made by the tx_thread_suspend service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2451">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2451">Parameters</span></span>

- <span data-ttu-id="f9121-2452">**thread_ptr** Wskaźnik do wcześniej utworzonego wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2452">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2453">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2453">Return Values</span></span>

- <span data-ttu-id="f9121-2454">**TX_SUCCESS** (0X00) pomyślne przerwanie oczekiwania wątku.</span><span class="sxs-lookup"><span data-stu-id="f9121-2454">**TX_SUCCESS** (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="f9121-2455">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2455">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="f9121-2456">Określony wątek **TX_WAIT_ABORT_ERROR** (0x1B) nie jest w stanie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="f9121-2456">**TX_WAIT_ABORT_ERROR** (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2457">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2457">Allowed From</span></span>

<span data-ttu-id="f9121-2458">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2458">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2459">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2459">Preemption Possible</span></span>
<span data-ttu-id="f9121-2460">Tak</span><span class="sxs-lookup"><span data-stu-id="f9121-2460">Yes</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2461">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2461">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2462">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2462">See Also</span></span>

- <span data-ttu-id="f9121-2463">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2463">tx_thread_create</span></span>
- <span data-ttu-id="f9121-2464">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2464">tx_thread_delete</span></span>
- <span data-ttu-id="f9121-2465">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2465">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="f9121-2466">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="f9121-2466">tx_thread_identify</span></span>
- <span data-ttu-id="f9121-2467">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2467">tx_thread_info_get</span></span>
- <span data-ttu-id="f9121-2468">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2468">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="f9121-2469">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2469">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="f9121-2470">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2470">tx_thread_preemption_change</span></span>
- <span data-ttu-id="f9121-2471">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2471">tx_thread_priority_change</span></span>
- <span data-ttu-id="f9121-2472">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="f9121-2472">tx_thread_relinquish</span></span>
- <span data-ttu-id="f9121-2473">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="f9121-2473">tx_thread_reset</span></span>
- <span data-ttu-id="f9121-2474">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="f9121-2474">tx_thread_resume</span></span>
- <span data-ttu-id="f9121-2475">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="f9121-2475">tx_thread_sleep</span></span>
- <span data-ttu-id="f9121-2476">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="f9121-2476">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="f9121-2477">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="f9121-2477">tx_thread_suspend</span></span>
- <span data-ttu-id="f9121-2478">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="f9121-2478">tx_thread_terminate</span></span>
- <span data-ttu-id="f9121-2479">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2479">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="f9121-2480">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2480">tx_time_get</span></span>

<span data-ttu-id="f9121-2481">Pobiera bieżącą godzinę</span><span class="sxs-lookup"><span data-stu-id="f9121-2481">Retrieves the current time</span></span>

<span data-ttu-id="f9121-2482">Czasomierze aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2482">Application Timers</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2483">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2483">Prototype</span></span>

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a><span data-ttu-id="f9121-2484">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2484">Description</span></span>

<span data-ttu-id="f9121-2485">Ta usługa zwraca zawartość wewnętrznego zegara systemowego.</span><span class="sxs-lookup"><span data-stu-id="f9121-2485">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="f9121-2486">Każdy timertick zwiększa wewnętrzny zegar systemowy o jeden.</span><span class="sxs-lookup"><span data-stu-id="f9121-2486">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="f9121-2487">Zegar systemowy jest ustawiany na zero podczas inicjowania i można go zmienić na określoną wartość przez ***tx_time_set*** usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2487">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2488">*Rzeczywisty czas, jaki jest reprezentowany przez cykl czasomierza, jest specyficzny dla aplikacji.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2488">*The actual time each timer-tick represents is application specific.*</span></span>

<span data-ttu-id="f9121-2489">**Parametry**</span><span class="sxs-lookup"><span data-stu-id="f9121-2489">**Parameters**</span></span>

<span data-ttu-id="f9121-2490">Brak</span><span class="sxs-lookup"><span data-stu-id="f9121-2490">None</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2491">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2491">Return Values</span></span>

- <span data-ttu-id="f9121-2492">**Takty zegara systemowego** Wartość wewnętrznego, wolnego, uruchomionego zegara systemowego.</span><span class="sxs-lookup"><span data-stu-id="f9121-2492">**system clock ticks** Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2493">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2493">Allowed From</span></span>

<span data-ttu-id="f9121-2494">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2494">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2495">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2495">Preemption Possible</span></span>
<span data-ttu-id="f9121-2496">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-2496">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2497">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2497">Example</span></span>

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2498">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2498">See Also</span></span>

- <span data-ttu-id="f9121-2499">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="f9121-2499">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="f9121-2500">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="f9121-2500">tx_time_set</span></span>

<span data-ttu-id="f9121-2501">Ustawia bieżącą godzinę</span><span class="sxs-lookup"><span data-stu-id="f9121-2501">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2502">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2502">Prototype</span></span>

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a><span data-ttu-id="f9121-2503">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2503">Description</span></span>

<span data-ttu-id="f9121-2504">Ta usługa ustawia wewnętrzny zegar systemowy do określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="f9121-2504">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="f9121-2505">Każdy czasomierz czasu wydłuża zegar systemu wewnętrznego o jeden.</span><span class="sxs-lookup"><span data-stu-id="f9121-2505">Each timer-tick increases the internal system clock by one.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2506">*Rzeczywisty czas, jaki jest reprezentowany przez cykl czasomierza, jest specyficzny dla aplikacji.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2506">*The actual time each timer-tick represents is application specific.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2507">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2507">Parameters</span></span>

- <span data-ttu-id="f9121-2508">**new_time** Nowy czas do umieszczenia w zegarze systemowym, wartości prawne mieszczą się w zakresie od 0 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="f9121-2508">**new_time** New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2509">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2509">Return Values</span></span>

<span data-ttu-id="f9121-2510">Brak</span><span class="sxs-lookup"><span data-stu-id="f9121-2510">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2511">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2511">Allowed From</span></span>

<span data-ttu-id="f9121-2512">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2512">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2513">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2513">Preemption Possible</span></span>

<span data-ttu-id="f9121-2514">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-2514">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2515">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2515">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2516">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2516">See Also</span></span>

- <span data-ttu-id="f9121-2517">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2517">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="f9121-2518">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="f9121-2518">tx_timer_activate</span></span>

<span data-ttu-id="f9121-2519">Aktywuj czasomierz aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2519">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2520">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2520">Prototype</span></span>

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-2521">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2521">Description</span></span>

<span data-ttu-id="f9121-2522">Ta usługa aktywuje określony czasomierz aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2522">This service activates the specified application timer.</span></span> <span data-ttu-id="f9121-2523">Procedury wygasania czasomierzy, które wygasają w tym samym czasie, są wykonywane w kolejności, w jakiej zostały aktywowane.</span><span class="sxs-lookup"><span data-stu-id="f9121-2523">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2524">*Wygasły czasomierz z jednym zdjęciem musi być resetowany przez*  \* **tx_timer_change** _ _before można go aktywować ponownie. \*</span><span class="sxs-lookup"><span data-stu-id="f9121-2524">*An expired one-shot timer must be reset via* ***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2525">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2525">Parameters</span></span>

- <span data-ttu-id="f9121-2526">**timer_ptr** Wskaźnik do wcześniej utworzonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2526">**timer_ptr** Pointer to a previously created application timer.</span></span>

<span data-ttu-id="f9121-2527">**Wartości zwracane**</span><span class="sxs-lookup"><span data-stu-id="f9121-2527">**Return Values**</span></span>

- <span data-ttu-id="f9121-2528">**TX_SUCCESS** (0x00) pomyślna aktywacja czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2528">**TX_SUCCESS** (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="f9121-2529">**TX_TIMER_ERROR** (0X15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2529">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="f9121-2530">Czasomierz **TX_ACTIVATE_ERROR** (0x17) był już aktywny lub jest już wygasłym czasomierzem.</span><span class="sxs-lookup"><span data-stu-id="f9121-2530">**TX_ACTIVATE_ERROR** (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2531">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2531">Allowed From</span></span>

<span data-ttu-id="f9121-2532">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2532">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2533">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2533">Preemption Possible</span></span>

<span data-ttu-id="f9121-2534">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-2534">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2535">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2535">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2536">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2536">See Also</span></span>

- <span data-ttu-id="f9121-2537">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2537">tx_timer_change</span></span>
- <span data-ttu-id="f9121-2538">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2538">tx_timer_create</span></span>
- <span data-ttu-id="f9121-2539">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="f9121-2539">tx_timer_deactivate</span></span>
- <span data-ttu-id="f9121-2540">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2540">tx_timer_delete</span></span>
- <span data-ttu-id="f9121-2541">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2541">tx_timer_info_get</span></span>
- <span data-ttu-id="f9121-2542">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2542">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="f9121-2543">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2543">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="f9121-2544">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2544">tx_timer_change</span></span>

<span data-ttu-id="f9121-2545">Zmień czasomierz aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2545">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2546">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2546">Prototype</span></span>

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a><span data-ttu-id="f9121-2547">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2547">Description</span></span>

<span data-ttu-id="f9121-2548">Ta usługa zmienia charakterystykę wygaśnięcia określonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2548">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="f9121-2549">Czasomierz należy dezaktywować przed wywołaniem tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2549">The timer must be deactivated prior to calling this service.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2550">*Wywołanie*  \* przed ponownym uruchomieniem czasomierza jest wymagane **tx_timer_activate** _ _Service. \*</span><span class="sxs-lookup"><span data-stu-id="f9121-2550">*A call to the* ***tx_timer_activate** _ _service is required after this service in order to start the timer again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2551">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2551">Parameters</span></span>

- <span data-ttu-id="f9121-2552">**timer_ptr** Wskaźnik do bloku sterowania czasomierzem.</span><span class="sxs-lookup"><span data-stu-id="f9121-2552">**timer_ptr** Pointer to a timer control block.</span></span>
- <span data-ttu-id="f9121-2553">**initial_ticks** Określa początkową liczbę taktów dla wygaśnięcia czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2553">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="f9121-2554">Wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="f9121-2554">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="f9121-2555">**reschedule_ticks** Określa liczbę taktów dla wszystkich wygasających czasomierzy po pierwszej.</span><span class="sxs-lookup"><span data-stu-id="f9121-2555">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="f9121-2556">Wartość zerowa dla tego parametru powoduje, że czasomierz ma czasomierz *jednorazowy* .</span><span class="sxs-lookup"><span data-stu-id="f9121-2556">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="f9121-2557">W przeciwnym razie dla okresowych czasomierzy wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="f9121-2557">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2558">*Wygasły czasomierz z jednym zdjęciem musi być resetowany przez* 
\* **tx_timer_change** _ _before można go aktywować ponownie. \*</span><span class="sxs-lookup"><span data-stu-id="f9121-2558">*An expired one-shot timer must be reset via*
***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2559">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2559">Return Values</span></span>

- <span data-ttu-id="f9121-2560">**TX_SUCCESS** (0X00) pomyślnie przeprowadzono zmianę czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2560">**TX_SUCCESS** (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="f9121-2561">**TX_TIMER_ERROR** (0X15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2561">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="f9121-2562">**TX_TICK_ERROR** (0X16) Nieprawidłowa wartość (zero) dostarczona dla początkowych taktów.</span><span class="sxs-lookup"><span data-stu-id="f9121-2562">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="f9121-2563">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2563">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2564">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2564">Allowed From</span></span>

<span data-ttu-id="f9121-2565">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2565">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2566">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2566">Preemption Possible</span></span>

<span data-ttu-id="f9121-2567">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-2567">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2568">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2568">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Change a previously created and now deactivated timer
to expire every 50 timer ticks, including the initial
expiration. */
status = tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```

### <a name="see-also"></a><span data-ttu-id="f9121-2569">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2569">See Also</span></span>

- <span data-ttu-id="f9121-2570">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="f9121-2570">tx_timer_activate</span></span>
- <span data-ttu-id="f9121-2571">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2571">tx_timer_create</span></span>
- <span data-ttu-id="f9121-2572">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="f9121-2572">tx_timer_deactivate</span></span>
- <span data-ttu-id="f9121-2573">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2573">tx_timer_delete</span></span>
- <span data-ttu-id="f9121-2574">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2574">tx_timer_info_get</span></span>
- <span data-ttu-id="f9121-2575">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2575">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="f9121-2576">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2576">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="f9121-2577">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2577">tx_timer_create</span></span>

<span data-ttu-id="f9121-2578">Utwórz czasomierz aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2578">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2579">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2579">Prototype</span></span>

```c
UINT tx_timer_create(
    TX_TIMER *timer_ptr, 
    CHAR *name_ptr,
    VOID (*expiration_function)(ULONG),
    ULONG expiration_input, 
    ULONG initial_ticks,
    ULONG reschedule_ticks, 
    UINT auto_activate);
```

### <a name="description"></a><span data-ttu-id="f9121-2580">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2580">Description</span></span>

<span data-ttu-id="f9121-2581">Ta usługa tworzy czasomierz aplikacji z określoną funkcją wygaśnięcia i okresowo.</span><span class="sxs-lookup"><span data-stu-id="f9121-2581">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2582">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2582">Parameters</span></span>

- <span data-ttu-id="f9121-2583">**timer_ptr** Wskaźnik do bloku sterowania czasomierzem</span><span class="sxs-lookup"><span data-stu-id="f9121-2583">**timer_ptr** Pointer to a timer control block</span></span>
- <span data-ttu-id="f9121-2584">**name_ptr** Wskaźnik na nazwę czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2584">**name_ptr** Pointer to the name of the timer.</span></span>
- <span data-ttu-id="f9121-2585">**expiration_function** Funkcja aplikacji do wywołania po wygaśnięciu czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2585">**expiration_function** Application function to call when the timer expires.</span></span>
- <span data-ttu-id="f9121-2586">**expiration_input** Dane wejściowe do przekazania do funkcji wygaśnięcia po wygaśnięciu czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2586">**expiration_input** Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="f9121-2587">**initial_ticks** Określa początkową liczbę taktów dla wygaśnięcia czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2587">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="f9121-2588">Wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="f9121-2588">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="f9121-2589">**reschedule_ticks** Określa liczbę taktów dla wszystkich wygasających czasomierzy po pierwszej.</span><span class="sxs-lookup"><span data-stu-id="f9121-2589">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="f9121-2590">Wartość zerowa dla tego parametru powoduje, że czasomierz ma czasomierz *jednorazowy* .</span><span class="sxs-lookup"><span data-stu-id="f9121-2590">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="f9121-2591">W przeciwnym razie dla okresowych czasomierzy wartości prawne mieszczą się w zakresie od 1 do 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="f9121-2591">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

  > [!NOTE]
  > <span data-ttu-id="f9121-2592">*Po wygaśnięciu czasomierza z jednym zrzutem należy zresetować go za pomocą tx_timer_change, zanim będzie można go ponownie aktywować.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2592">*After a one-shot timer expires, it must be reset via   tx_timer_change before it can be activated again.*</span></span>

- <span data-ttu-id="f9121-2593">**Auto_Activate** Określa, czy czasomierz jest automatycznie uaktywniany podczas tworzenia.</span><span class="sxs-lookup"><span data-stu-id="f9121-2593">**auto_activate** Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="f9121-2594">Jeśli ta wartość jest **TX_AUTO_ACTIVATE** (0x01), czasomierz jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="f9121-2594">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="f9121-2595">W przeciwnym razie, jeśli wybrano wartość **TX_NO_ACTIVATE** (0x00), czasomierz zostanie utworzony w stanie nieaktywnym.</span><span class="sxs-lookup"><span data-stu-id="f9121-2595">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="f9121-2596">W takim przypadku kolejne wywołanie usługi **_tx_timer_activate_** jest niezbędne do uruchomienia czasomierza w rzeczywistości.</span><span class="sxs-lookup"><span data-stu-id="f9121-2596">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2597">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2597">Return Values</span></span>

- <span data-ttu-id="f9121-2598">**TX_SUCCESS** (0X00) pomyślne utworzenie czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2598">**TX_SUCCESS** (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="f9121-2599">**TX_TIMER_ERROR** (0X15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2599">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="f9121-2600">Wskaźnik ma wartość NULL lub czasomierz został już utworzony.</span><span class="sxs-lookup"><span data-stu-id="f9121-2600">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="f9121-2601">**TX_TICK_ERROR** (0X16) Nieprawidłowa wartość (zero) dostarczona dla początkowych taktów.</span><span class="sxs-lookup"><span data-stu-id="f9121-2601">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="f9121-2602">Wybrano nieprawidłową aktywację **TX_ACTIVATE_ERROR** (0x17).</span><span class="sxs-lookup"><span data-stu-id="f9121-2602">**TX_ACTIVATE_ERROR** (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="f9121-2603">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2603">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2604">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2604">Allowed From</span></span>

<span data-ttu-id="f9121-2605">Inicjalizacje i wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-2605">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2606">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2606">Preemption Possible</span></span>

<span data-ttu-id="f9121-2607">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-2607">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2608">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2608">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Create an application timer that executes
"my_timer_function" after 100 ticks initially and then
after every 25 ticks. This timer is specified to start
immediately! */
status = tx_timer_create(&my_timer,"my_timer_name",
    my_timer_function, 0x1234, 100, 25,
    TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
be called 100 timer ticks later and then called every
25 timer ticks. Note that the value 0x1234 is passed to
my_timer_function every time it is called. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2609">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2609">See Also</span></span>

- <span data-ttu-id="f9121-2610">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="f9121-2610">tx_timer_activate</span></span>
- <span data-ttu-id="f9121-2611">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2611">tx_timer_change</span></span>
- <span data-ttu-id="f9121-2612">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="f9121-2612">tx_timer_deactivate</span></span>
- <span data-ttu-id="f9121-2613">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2613">tx_timer_delete</span></span>
- <span data-ttu-id="f9121-2614">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2614">tx_timer_info_get</span></span>
- <span data-ttu-id="f9121-2615">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2615">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="f9121-2616">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2616">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="f9121-2617">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="f9121-2617">tx_timer_deactivate</span></span>

<span data-ttu-id="f9121-2618">Dezaktywuj czasomierz aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2618">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2619">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2619">Prototype</span></span>

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-2620">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2620">Description</span></span>

<span data-ttu-id="f9121-2621">Ta usługa dezaktywuje określony czasomierz aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2621">This service deactivates the specified application timer.</span></span> <span data-ttu-id="f9121-2622">Jeśli czasomierz został już zdezaktywowany, ta usługa nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="f9121-2622">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2623">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2623">Parameters</span></span>

- <span data-ttu-id="f9121-2624">**timer_ptr** Wskaźnik do wcześniej utworzonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2624">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2625">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2625">Return Values</span></span>

- <span data-ttu-id="f9121-2626">**TX_SUCCESS** (0x00) pomyślna dezaktywacja czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2626">**TX_SUCCESS** (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="f9121-2627">**TX_TIMER_ERROR** (0X15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2627">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2628">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2628">Allowed From</span></span>

<span data-ttu-id="f9121-2629">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2629">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2630">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2630">Preemption Possible</span></span>

<span data-ttu-id="f9121-2631">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-2631">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2632">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2632">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2633">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2633">See Also</span></span>

- <span data-ttu-id="f9121-2634">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="f9121-2634">tx_timer_activate</span></span>
- <span data-ttu-id="f9121-2635">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2635">tx_timer_change</span></span>
- <span data-ttu-id="f9121-2636">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2636">tx_timer_create</span></span>
- <span data-ttu-id="f9121-2637">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2637">tx_timer_delete</span></span>
- <span data-ttu-id="f9121-2638">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2638">tx_timer_info_get</span></span>
- <span data-ttu-id="f9121-2639">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2639">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="f9121-2640">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2640">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="f9121-2641">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2641">tx_timer_delete</span></span>

<span data-ttu-id="f9121-2642">Usuń czasomierz aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2642">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2643">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2643">Prototype</span></span>

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="f9121-2644">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2644">Description</span></span>

<span data-ttu-id="f9121-2645">Ta usługa usuwa określony czasomierz aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2645">This service deletes the specified application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2646">*Jest to odpowiedzialność aplikacji, aby uniemożliwić korzystanie z usuniętego czasomierza.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2646">*It is the application's responsibility to prevent use of a deleted timer.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2647">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2647">Parameters</span></span>

- <span data-ttu-id="f9121-2648">**timer_ptr** Wskaźnik do wcześniej utworzonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2648">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2649">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2649">Return Values</span></span>

- <span data-ttu-id="f9121-2650">**TX_SUCCESS** (0X00) pomyślne usunięcie czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2650">**TX_SUCCESS** (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="f9121-2651">**TX_TIMER_ERROR** (0X15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2651">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="f9121-2652">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="f9121-2652">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2653">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2653">Allowed From</span></span>

<span data-ttu-id="f9121-2654">Wątki</span><span class="sxs-lookup"><span data-stu-id="f9121-2654">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2655">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2655">Preemption Possible</span></span>

<span data-ttu-id="f9121-2656">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-2656">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2657">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2657">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2658">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2658">See Also</span></span>

- <span data-ttu-id="f9121-2659">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="f9121-2659">tx_timer_activate</span></span>
- <span data-ttu-id="f9121-2660">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2660">tx_timer_change</span></span>
- <span data-ttu-id="f9121-2661">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2661">tx_timer_create</span></span>
- <span data-ttu-id="f9121-2662">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="f9121-2662">tx_timer_deactivate</span></span>
- <span data-ttu-id="f9121-2663">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2663">tx_timer_info_get</span></span>
- <span data-ttu-id="f9121-2664">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2664">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="f9121-2665">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2665">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="f9121-2666">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2666">tx_timer_info_get</span></span>

<span data-ttu-id="f9121-2667">Pobierz informacje o czasomierzu aplikacji</span><span class="sxs-lookup"><span data-stu-id="f9121-2667">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2668">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2668">Prototype</span></span>

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a><span data-ttu-id="f9121-2669">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2669">Description</span></span>

<span data-ttu-id="f9121-2670">Ta usługa pobiera informacje o określonym czasomierzu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2670">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2671">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2671">Parameters</span></span>

- <span data-ttu-id="f9121-2672">**timer_ptr** Wskaźnik do wcześniej utworzonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2672">**timer_ptr** Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="f9121-2673">**Nazwa** Wskaźnik do miejsca docelowego dla wskaźnika do nazwy czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2673">**name** Pointer to destination for the pointer to the timer's name.</span></span>
- <span data-ttu-id="f9121-2674">**aktywne** Wskaźnik do miejsca docelowego dla wskaźnika aktywnego wskazywania czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2674">**active** Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="f9121-2675">Jeśli czasomierz jest nieaktywny lub ta usługa jest wywoływana z samego czasomierza, zwracana jest wartość **TX_FALSE** .</span><span class="sxs-lookup"><span data-stu-id="f9121-2675">If the timer is inactive or this service is called from the timer itself, a **TX_FALSE** value is returned.</span></span> <span data-ttu-id="f9121-2676">W przeciwnym razie, jeśli czasomierz jest aktywny, zwracana jest wartość **TX_TRUE** .</span><span class="sxs-lookup"><span data-stu-id="f9121-2676">Otherwise, if the timer is active, a **TX_TRUE** value is returned.</span></span>
- <span data-ttu-id="f9121-2677">**remaining_ticks** Wskaźnik do miejsca docelowego dla liczby cykli czasomierza pozostawionych przed wygaśnięciem czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2677">**remaining_ticks** Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="f9121-2678">**reschedule_ticks** Wskaźnik do miejsca docelowego dla liczby taktów czasomierza, który zostanie użyty do automatycznego ponownego zaplanowania tego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2678">**reschedule_ticks** Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="f9121-2679">Jeśli wartość jest równa zero, czasomierz jest jednorazowy i nie zostanie ponownie zaplanowany.</span><span class="sxs-lookup"><span data-stu-id="f9121-2679">If the value is zero, then the timer is a one-shot and won't be rescheduled.</span></span>
- <span data-ttu-id="f9121-2680">**next_timer** Wskaźnik do miejsca docelowego dla wskaźnika następnego utworzonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2680">**next_timer** Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2681">*Dostarczenie **TX_NULL** dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2681">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2682">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2682">Return Values</span></span>

- <span data-ttu-id="f9121-2683">Pobieranie informacji o pomyślnym czasomierzu **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-2683">**TX_SUCCESS** (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="f9121-2684">**TX_TIMER_ERROR** (0X15) Nieprawidłowy wskaźnik czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2684">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2685">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2685">Allowed From</span></span>

<span data-ttu-id="f9121-2686">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2686">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="f9121-2687">Możliwe przeprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f9121-2687">Preemption Possible</span></span>

<span data-ttu-id="f9121-2688">Nie</span><span class="sxs-lookup"><span data-stu-id="f9121-2688">No</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2689">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2689">Example</span></span>

```c
TX_TIMER my_timer;
CHAR *name;
UINT active;
ULONG remaining_ticks;
ULONG reschedule_ticks;
TX_TIMER *next_timer;
UINT status;

/* Retrieve information about the previously created
application timer "my_timer." */
status = tx_timer_info_get(&my_timer, &name,
    &active,&remaining_ticks,
    &reschedule_ticks,
    &next_timer);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2690">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2690">See Also</span></span>

- <span data-ttu-id="f9121-2691">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="f9121-2691">tx_timer_activate</span></span>
- <span data-ttu-id="f9121-2692">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2692">tx_timer_change</span></span>
- <span data-ttu-id="f9121-2693">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2693">tx_timer_create</span></span>
- <span data-ttu-id="f9121-2694">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="f9121-2694">tx_timer_deactivate</span></span>
- <span data-ttu-id="f9121-2695">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2695">tx_timer_delete</span></span>
- <span data-ttu-id="f9121-2696">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2696">tx_timer_info_get</span></span>
- <span data-ttu-id="f9121-2697">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2697">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="f9121-2698">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2698">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="f9121-2699">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2699">tx_timer_performance_info_get</span></span>

<span data-ttu-id="f9121-2700">Pobierz informacje o wydajności czasomierza</span><span class="sxs-lookup"><span data-stu-id="f9121-2700">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2701">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2701">Prototype</span></span>

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="f9121-2702">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2702">Description</span></span>

<span data-ttu-id="f9121-2703">Ta usługa pobiera informacje o wydajności dotyczące określonego czasomierza aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9121-2703">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-2704">*Biblioteka i aplikacja ThreadX muszą być kompilowane przy użyciu*  \* **TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined do zwrócenia informacji o wydajności przez tę usługę \*</span><span class="sxs-lookup"><span data-stu-id="f9121-2704">*The ThreadX library and application must be built with* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="f9121-2705">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9121-2705">Parameters</span></span>
- <span data-ttu-id="f9121-2706">**timer_ptr** Wskaźnik do wcześniej utworzonego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2706">**timer_ptr** Pointer to previously created timer.</span></span>
- <span data-ttu-id="f9121-2707">**Aktywuj** Wskaźnik do miejsca docelowego dla liczby żądań aktywacji wykonanych dla tego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2707">**activates** Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="f9121-2708">**ponowne aktywowanie** Wskaźnik do miejsca docelowego dla liczby automatycznych ponownych aktywacji wykonanych na tym cyklicznym czasomierzu.</span><span class="sxs-lookup"><span data-stu-id="f9121-2708">**reactivates** Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="f9121-2709">**dezaktywuje** Wskaźnik do miejsca docelowego dla liczby żądań dezaktywacji wykonanych dla tego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2709">**deactivates** Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="f9121-2710">**wygaśnięcia** Wskaźnik do miejsca docelowego dla liczby wygaśnięć tego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2710">**expirations** Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="f9121-2711">**expiration_adjusts** Wskaźnik do miejsca docelowego dla liczby wewnętrznych korekt wygaśnięcia wykonanych dla tego czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2711">**expiration_adjusts** Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="f9121-2712">Te korekty są wykonywane w ramach przetwarzania przerwań czasomierza dla czasomierzy, które są większe niż domyślny rozmiar listy czasomierza (domyślnie czasomierze o wygasaniu większym niż 32 taktów).</span><span class="sxs-lookup"><span data-stu-id="f9121-2712">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> <span data-ttu-id="f9121-2713">KORYGUJĄC *Dostarczenie TX_NULL dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2713">[NOTE] *Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2714">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2714">Return Values</span></span>

- <span data-ttu-id="f9121-2715">Pomyślna wydajność czasomierza **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="f9121-2715">**TX_SUCCESS** (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="f9121-2716">**TX_PTR_ERROR** (0X03) Nieprawidłowy wskaźnik czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2716">**TX_PTR_ERROR** (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="f9121-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2718">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2718">Allowed From</span></span>

<span data-ttu-id="f9121-2719">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2719">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2720">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2720">Example</span></span>

```c
TX_TIMER my_timer;
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on the previously created
timer. */
status = tx_timer_performance_info_get(&my_timer, &activates,
    &reactivates,&deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2721">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2721">See Also</span></span>

- <span data-ttu-id="f9121-2722">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="f9121-2722">tx_timer_activate</span></span>
- <span data-ttu-id="f9121-2723">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2723">tx_timer_change</span></span>
- <span data-ttu-id="f9121-2724">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2724">tx_timer_create</span></span>
- <span data-ttu-id="f9121-2725">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="f9121-2725">tx_timer_deactivate</span></span>
- <span data-ttu-id="f9121-2726">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2726">tx_timer_delete</span></span>
- <span data-ttu-id="f9121-2727">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2727">tx_timer_info_get</span></span>
- <span data-ttu-id="f9121-2728">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2728">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="f9121-2729">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2729">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="f9121-2730">Pobierz informacje o wydajności systemu czasomierza</span><span class="sxs-lookup"><span data-stu-id="f9121-2730">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="f9121-2731">Prototype</span><span class="sxs-lookup"><span data-stu-id="f9121-2731">Prototype</span></span>

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="f9121-2732">Opis</span><span class="sxs-lookup"><span data-stu-id="f9121-2732">Description</span></span>

<span data-ttu-id="f9121-2733">Ta usługa pobiera informacje o wydajności wszystkich czasomierzy aplikacji w systemie.</span><span class="sxs-lookup"><span data-stu-id="f9121-2733">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9121-2734">Aby można było zwracać informacje o wydajności *, biblioteka i aplikacja ThreadX muszą zostać skompilowane z użyciem* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *zdefiniowanej dla tej usługi.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2734">*The ThreadX library and application must be built with* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

<span data-ttu-id="f9121-2735">**Parametry**</span><span class="sxs-lookup"><span data-stu-id="f9121-2735">**Parameters**</span></span>

- <span data-ttu-id="f9121-2736">**Aktywuj** Wskaźnik do miejsca docelowego dla łącznej liczby żądań aktywacji wykonanych na wszystkich czasomierzach.</span><span class="sxs-lookup"><span data-stu-id="f9121-2736">**activates** Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="f9121-2737">**ponowne aktywowanie** Wskaźnik do miejsca docelowego dla łącznej liczby automatycznych ponownych aktywacji wykonanych na wszystkich okresowych czasomierzach.</span><span class="sxs-lookup"><span data-stu-id="f9121-2737">**reactivates** Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="f9121-2738">**dezaktywuje** Wskaźnik do miejsca docelowego dla łącznej liczby żądań dezaktywacji wykonanych na wszystkich czasomierzach.</span><span class="sxs-lookup"><span data-stu-id="f9121-2738">**deactivates** Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="f9121-2739">**wygaśnięcia** Wskaźnik do miejsca docelowego dla łącznej liczby wygaśnięć dla wszystkich czasomierzy.</span><span class="sxs-lookup"><span data-stu-id="f9121-2739">**expirations** Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="f9121-2740">**expiration_adjusts** Wskaźnik do miejsca docelowego dla łącznej liczby wewnętrznych korekt wygaśnięcia wykonanych na wszystkich czasomierzach.</span><span class="sxs-lookup"><span data-stu-id="f9121-2740">**expiration_adjusts** Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="f9121-2741">Te korekty są wykonywane w ramach przetwarzania przerwań czasomierza dla czasomierzy, które są większe niż domyślny rozmiar listy czasomierza (domyślnie czasomierze o wygasaniu większym niż 32 taktów).</span><span class="sxs-lookup"><span data-stu-id="f9121-2741">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!NOTE]
> <span data-ttu-id="f9121-2742">*Dostarczenie **TX_NULL** dla dowolnego parametru wskazuje, że parametr nie jest wymagany.*</span><span class="sxs-lookup"><span data-stu-id="f9121-2742">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="f9121-2743">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="f9121-2743">Return Values</span></span>

- <span data-ttu-id="f9121-2744">**TX_SUCCESS** (0X00) pomyślne pobieranie wydajności systemu czasomierza.</span><span class="sxs-lookup"><span data-stu-id="f9121-2744">**TX_SUCCESS** (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="f9121-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) system nie został skompilowany z włączonymi informacjami o wydajności.</span><span class="sxs-lookup"><span data-stu-id="f9121-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="f9121-2746">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="f9121-2746">Allowed From</span></span>

<span data-ttu-id="f9121-2747">Inicjalizacja, wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="f9121-2747">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="f9121-2748">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9121-2748">Example</span></span>

```c
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on all previously created
timers. */
status = tx_timer_performance_system_info_get(&activates,
    &reactivates, &deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="f9121-2749">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9121-2749">See Also</span></span>

- <span data-ttu-id="f9121-2750">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="f9121-2750">tx_timer_activate</span></span>
- <span data-ttu-id="f9121-2751">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="f9121-2751">tx_timer_change</span></span>
- <span data-ttu-id="f9121-2752">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="f9121-2752">tx_timer_create</span></span>
- <span data-ttu-id="f9121-2753">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="f9121-2753">tx_timer_deactivate</span></span>
- <span data-ttu-id="f9121-2754">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="f9121-2754">tx_timer_delete</span></span>
- <span data-ttu-id="f9121-2755">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2755">tx_timer_info_get</span></span>
- <span data-ttu-id="f9121-2756">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="f9121-2756">tx_timer_performance_info_get</span></span>
