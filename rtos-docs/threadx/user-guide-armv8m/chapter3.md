---
title: Rozdział 3 — interfejsy API ThreadX dla ARMv8-M
description: W tym rozdziale znajduje się opis ARMv8-M-określonych usług ThreadX.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14bdfab3d56476d52ba91f859cec4af4ab7f4bef
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377599"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a><span data-ttu-id="4328d-103">Rozdział 3 ThreadX interfejsy API dla ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="4328d-103">Chapter 3  ThreadX APIs for ARMv8-M</span></span>

<span data-ttu-id="4328d-104">Ten rozdział zawiera opis usług ThreadX specyficznych dla ARMv8-M w porządku alfabetycznym.</span><span class="sxs-lookup"><span data-stu-id="4328d-104">This chapter contains a description of the ARMv8-M-specific ThreadX services in alphabetic order.</span></span> <span data-ttu-id="4328d-105">Ich nazwy są zaprojektowane tak, aby wszystkie podobne usługi zostały zgrupowane razem.</span><span class="sxs-lookup"><span data-stu-id="4328d-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="4328d-106">W sekcji "wartości zwracane" w następujących opisach wartości **pogrubienia** nie mają wpływać na **TX_DISABLE_ERROR_CHECKING** Definiowanie używane do wyłączania sprawdzania błędów interfejsu API; podczas gdy wartości wyświetlane w trybie niepogrubionym są całkowicie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="4328d-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in non-bold are completely disabled.</span></span>

- <span data-ttu-id="4328d-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Przydziel stos wątków w bezpiecznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="4328d-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Allocate a thread stack in secure memory.</span></span>
- <span data-ttu-id="4328d-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Bezpłatny stos wątków w bezpiecznej pamięci</span><span class="sxs-lookup"><span data-stu-id="4328d-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Free thread stack in secure memory</span></span>

## <a name="tx_thread_secure_stack_allocate"></a><span data-ttu-id="4328d-109">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="4328d-109">tx_thread_secure_stack_allocate</span></span>

<span data-ttu-id="4328d-110">Przydziel stos wątków w bezpiecznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="4328d-110">Allocate a thread stack in secure memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="4328d-111">Prototype</span><span class="sxs-lookup"><span data-stu-id="4328d-111">Prototype</span></span>

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="4328d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4328d-112">Description</span></span>

<span data-ttu-id="4328d-113">Ta usługa przydziela stos rozmiaru stack_size bajtów w bezpiecznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="4328d-113">This service allocates a stack of size stack_size bytes in secure memory.</span></span> <span data-ttu-id="4328d-114">Ta funkcja powinna być wywoływana dla każdego wątku, który wywołuje bezpieczne funkcje.</span><span class="sxs-lookup"><span data-stu-id="4328d-114">This function should be called for every thread that calls secure functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4328d-115">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="4328d-115">Input Parameters</span></span>

- <span data-ttu-id="4328d-116">**thread_ptr** Wskaźnik do wcześniej utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="4328d-116">**thread_ptr** Pointer to previously created thread.</span></span>

- <span data-ttu-id="4328d-117">**stack_size** Rozmiar bezpiecznego stosu.</span><span class="sxs-lookup"><span data-stu-id="4328d-117">**stack_size** Size of secure stack.</span></span>

### <a name="return-values"></a><span data-ttu-id="4328d-118">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="4328d-118">Return Values</span></span>

- <span data-ttu-id="4328d-119">Żądanie powiodło się **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="4328d-119">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="4328d-120">Rozmiar stosu **TX_SIZE_ERROR** (0x05) poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="4328d-120">**TX_SIZE_ERROR** (0x05) Stack size out of range.</span></span>

- <span data-ttu-id="4328d-121">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku.</span><span class="sxs-lookup"><span data-stu-id="4328d-121">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="4328d-122">**TX_NO_MEMORY** (0X10) nie może przydzielić pamięci.</span><span class="sxs-lookup"><span data-stu-id="4328d-122">**TX_NO_MEMORY** (0x10) Unable to allocate memory.</span></span>

- <span data-ttu-id="4328d-123">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4328d-123">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="4328d-124">**TX_FEATURE_NOT_ENABLED** (0xFF) system został skompilowany do uruchomienia w trybie zabezpieczonym.</span><span class="sxs-lookup"><span data-stu-id="4328d-124">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4328d-125">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="4328d-125">Allowed From</span></span>

<span data-ttu-id="4328d-126">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="4328d-126">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="4328d-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="4328d-127">Example</span></span>

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a><span data-ttu-id="4328d-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4328d-128">See Also</span></span>

<span data-ttu-id="4328d-129">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="4328d-129">tx_thread_secure_stack_free</span></span>

##  <a name="tx_thread_secure_stack_free"></a><span data-ttu-id="4328d-130">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="4328d-130">tx_thread_secure_stack_free</span></span>

<span data-ttu-id="4328d-131">Zwolnij stos wątków w bezpiecznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="4328d-131">Free a thread stack in secure memory.</span></span> 

### <a name="prototype"></a><span data-ttu-id="4328d-132">Prototype</span><span class="sxs-lookup"><span data-stu-id="4328d-132">Prototype</span></span>

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="4328d-133">Opis</span><span class="sxs-lookup"><span data-stu-id="4328d-133">Description</span></span>

<span data-ttu-id="4328d-134">Ta usługa zwolni bezpieczny stos wątku w bezpiecznej pamięci.</span><span class="sxs-lookup"><span data-stu-id="4328d-134">This service frees a thread's secure stack in secure memory.</span></span> <span data-ttu-id="4328d-135">Ta funkcja powinna być wywoływana, jeśli wątek ma bezpieczny stos i gdy wątek już nie musi wywoływać bezpiecznych funkcji lub wątek został usunięty.</span><span class="sxs-lookup"><span data-stu-id="4328d-135">This function should be called if a thread has a secure stack and when the thread no longer needs to call secure functions or the thread is deleted.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="4328d-136">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="4328d-136">Input Parameters</span></span>

- <span data-ttu-id="4328d-137">**thread_ptr** Wskaźnik do wcześniej utworzonego wątku.</span><span class="sxs-lookup"><span data-stu-id="4328d-137">**thread_ptr** Pointer to previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="4328d-138">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="4328d-138">Return Values</span></span>

- <span data-ttu-id="4328d-139">Żądanie powiodło się **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="4328d-139">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="4328d-140">**TX_THREAD_ERROR** (0X0E) Nieprawidłowy wskaźnik wątku.</span><span class="sxs-lookup"><span data-stu-id="4328d-140">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="4328d-141">**TX_CALLER_ERROR** (0X13) Nieprawidłowy obiekt wywołujący tej usługi.</span><span class="sxs-lookup"><span data-stu-id="4328d-141">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="4328d-142">**TX_FEATURE_NOT_ENABLED** (0xFF) system został skompilowany do uruchomienia w trybie zabezpieczonym.</span><span class="sxs-lookup"><span data-stu-id="4328d-142">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="4328d-143">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="4328d-143">Allowed From</span></span>

<span data-ttu-id="4328d-144">Inicjalizacja, wątki</span><span class="sxs-lookup"><span data-stu-id="4328d-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="4328d-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="4328d-145">Example</span></span>

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a><span data-ttu-id="4328d-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4328d-146">See Also</span></span>

<span data-ttu-id="4328d-147">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="4328d-147">tx_thread_secure_stack_allocate</span></span>
