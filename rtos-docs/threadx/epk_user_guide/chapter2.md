---
title: Rozdział 2 — Dokumentacja interfejsu API zestawu profilów wykonywania
description: Ten rozdział dokumentuje funkcje interfejsu API udostępniane przez EPK.
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a198e48bdacbc141fb3de4670cc7ea5ba079612d
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377600"
---
#  <a name="chapter-2--execution-profile-kit-api-references"></a><span data-ttu-id="13ef8-103">Rozdział 2 — Dokumentacja interfejsu API zestawu profilów wykonywania</span><span class="sxs-lookup"><span data-stu-id="13ef8-103">Chapter 2  Execution Profile Kit API References</span></span>

<span data-ttu-id="13ef8-104">ThreadX EPK zapewnia funkcje dostępu do uzyskiwania informacji o profilu wykonania w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="13ef8-104">The ThreadX EPK provides access functions to get the execution profile information, as follows.</span></span>

| <span data-ttu-id="13ef8-105">&nbsp;Nazwa funkcji</span><span class="sxs-lookup"><span data-stu-id="13ef8-105">Function&nbsp;Name</span></span> | <span data-ttu-id="13ef8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="13ef8-106">Description</span></span> |
| --- | --- |
| <span data-ttu-id="13ef8-107">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-107">_tx_execution_thread_time_reset</span></span> | <span data-ttu-id="13ef8-108">Zresetuj łączny czas dla wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-108">Reset the accumulated time for a thread.</span></span> |
| <span data-ttu-id="13ef8-109">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-109">_tx_execution_thread_total_time_reset</span></span> | <span data-ttu-id="13ef8-110">Zresetuj łączny czas wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-110">Reset the accumulated total thread time.</span></span> |
| <span data-ttu-id="13ef8-111">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-111">_tx_execution_isr_time_reset</span></span> | <span data-ttu-id="13ef8-112">Zresetuj skumulowany czas ISR.</span><span class="sxs-lookup"><span data-stu-id="13ef8-112">Reset the accumulated ISR time.</span></span> |
| <span data-ttu-id="13ef8-113">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-113">_tx_execution_idle_time_reset</span></span> | <span data-ttu-id="13ef8-114">Zresetuj skumulowany czas bezczynności.</span><span class="sxs-lookup"><span data-stu-id="13ef8-114">Reset the accumulated idle time.</span></span> |
| <span data-ttu-id="13ef8-115">_tx_execution_thread_time_get uzyskać skumulowany czas dla wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-115">_tx_execution_thread_time_get Get the accumulated time for a thread.</span></span> |
| <span data-ttu-id="13ef8-116">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-116">_tx_execution_thread_total_time_get</span></span> | <span data-ttu-id="13ef8-117">Pobierz łączny czas wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-117">Get the accumulated total thread time.</span></span> |
| <span data-ttu-id="13ef8-118">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-118">_tx_execution_isr_time_get</span></span> | <span data-ttu-id="13ef8-119">Pobierz skumulowany czas ISR.</span><span class="sxs-lookup"><span data-stu-id="13ef8-119">Get the accumulated ISR time.</span></span> |
| <span data-ttu-id="13ef8-120">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-120">_tx_execution_idle_time_get</span></span> | <span data-ttu-id="13ef8-121">Uzyskaj skumulowany czas bezczynności.</span><span class="sxs-lookup"><span data-stu-id="13ef8-121">Get the accumulated idle time.</span></span> |

##  <a name="_tx_execution_thread_time_reset"></a><span data-ttu-id="13ef8-122">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-122">_tx_execution_thread_time_reset</span></span>

<span data-ttu-id="13ef8-123">Zresetuj łączny czas dla wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-123">Reset the accumulated time for a thread.</span></span>

### <a name="prototype"></a><span data-ttu-id="13ef8-124">Prototype</span><span class="sxs-lookup"><span data-stu-id="13ef8-124">Prototype</span></span>

```C
UINT _tx_execution_thread_time_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="13ef8-125">Opis</span><span class="sxs-lookup"><span data-stu-id="13ef8-125">Description</span></span>

<span data-ttu-id="13ef8-126">Ta usługa ustawia skumulowany czas wykonywania wątku z powrotem na zero.</span><span class="sxs-lookup"><span data-stu-id="13ef8-126">This service sets the accumulated thread execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13ef8-127">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="13ef8-127">Input Parameters</span></span>

- <span data-ttu-id="13ef8-128">**thread_ptr** Wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-128">**thread_ptr** Pointer to thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="13ef8-129">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="13ef8-129">Return Values</span></span>

- <span data-ttu-id="13ef8-130">**TX_SUCCESS** (0X00) pomyślnie zresetowano EPK.</span><span class="sxs-lookup"><span data-stu-id="13ef8-130">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13ef8-131">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="13ef8-131">Allowed From</span></span>

<span data-ttu-id="13ef8-132">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="13ef8-132">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="13ef8-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="13ef8-133">Example</span></span>

```c
/* Reset the execution time for thread_0.  */
status =  tx_execution_thread_time_reset(&thread_0);

/* If status is TX_SUCCESS thread_0's execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="13ef8-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ef8-134">See Also</span></span>

- <span data-ttu-id="13ef8-135">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-135">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="13ef8-136">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-136">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="13ef8-137">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-137">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="13ef8-138">tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-138">tx_execution_thread_time_get</span></span>
- <span data-ttu-id="13ef8-139">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-139">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="13ef8-140">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-140">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="13ef8-141">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-141">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_thread_total_time_reset"></a><span data-ttu-id="13ef8-142">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-142">_tx_execution_thread_total_time_reset</span></span>

<span data-ttu-id="13ef8-143">Zresetuj całkowity skumulowany czas wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-143">Reset the total accumulated thread time.</span></span>

### <a name="prototype"></a><span data-ttu-id="13ef8-144">Prototype</span><span class="sxs-lookup"><span data-stu-id="13ef8-144">Prototype</span></span>
```c
UINT _tx_execution_thread_total_time_reset(void);
```

### <a name="description"></a><span data-ttu-id="13ef8-145">Opis</span><span class="sxs-lookup"><span data-stu-id="13ef8-145">Description</span></span>

<span data-ttu-id="13ef8-146">Ta usługa ustawia łączny czas wykonania wątku z powrotem na zero.</span><span class="sxs-lookup"><span data-stu-id="13ef8-146">This service sets the accumulated total thread execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13ef8-147">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="13ef8-147">Input Parameters</span></span>

<span data-ttu-id="13ef8-148">Brak.</span><span class="sxs-lookup"><span data-stu-id="13ef8-148">None.</span></span>

### <a name="return-values"></a><span data-ttu-id="13ef8-149">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="13ef8-149">Return Values</span></span>

- <span data-ttu-id="13ef8-150">**TX_SUCCESS** (0X00) pomyślnie zresetowano EPK.</span><span class="sxs-lookup"><span data-stu-id="13ef8-150">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13ef8-151">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="13ef8-151">Allowed From</span></span>

- <span data-ttu-id="13ef8-152">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="13ef8-152">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="13ef8-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="13ef8-153">Example</span></span>

```c
/* Reset the total execution time for all threads.  */
status =  tx_execution_thread_total_time_reset();

/* If status is TX_SUCCESS the total thread execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="13ef8-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ef8-154">See Also</span></span>

- <span data-ttu-id="13ef8-155">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-155">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="13ef8-156">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-156">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="13ef8-157">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-157">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="13ef8-158">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-158">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="13ef8-159">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-159">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="13ef8-160">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-160">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="13ef8-161">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-161">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_isr_time_reset"></a><span data-ttu-id="13ef8-162">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-162">_tx_execution_isr_time_reset</span></span>

<span data-ttu-id="13ef8-163">Zresetuj skumulowany czas ISR.</span><span class="sxs-lookup"><span data-stu-id="13ef8-163">Reset the accumulated ISR time.</span></span>

### <a name="prototype"></a><span data-ttu-id="13ef8-164">Prototype</span><span class="sxs-lookup"><span data-stu-id="13ef8-164">Prototype</span></span>

```c
UINT _tx_execution_isr_time_reset(void);
```

### <a name="description"></a><span data-ttu-id="13ef8-165">Opis</span><span class="sxs-lookup"><span data-stu-id="13ef8-165">Description</span></span>

<span data-ttu-id="13ef8-166">Ta usługa ustawia skumulowany łączny czas wykonywania ISR z powrotem na zero.</span><span class="sxs-lookup"><span data-stu-id="13ef8-166">This service sets the accumulated total ISR execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13ef8-167">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="13ef8-167">Input Parameters</span></span>

<span data-ttu-id="13ef8-168">Brak.</span><span class="sxs-lookup"><span data-stu-id="13ef8-168">None.</span></span>

### <a name="return-values"></a><span data-ttu-id="13ef8-169">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="13ef8-169">Return Values</span></span>

- <span data-ttu-id="13ef8-170">**TX_SUCCESS** (0X00) pomyślnie zresetowano EPK.</span><span class="sxs-lookup"><span data-stu-id="13ef8-170">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

<span data-ttu-id="13ef8-171">**Dozwolone z**</span><span class="sxs-lookup"><span data-stu-id="13ef8-171">**Allowed From**</span></span>

- <span data-ttu-id="13ef8-172">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="13ef8-172">Threads, timers, and ISRs</span></span>

<span data-ttu-id="13ef8-173">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="13ef8-173">**Example**</span></span>

```c
/* Reset the total ISR execution time.  */
status =  tx_execution_isr_time_reset();

/* If status is TX_SUCCESS the total ISR execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="13ef8-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ef8-174">See Also</span></span>

- <span data-ttu-id="13ef8-175">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-175">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="13ef8-176">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-176">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="13ef8-177">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-177">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="13ef8-178">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-178">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="13ef8-179">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-179">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="13ef8-180">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-180">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="13ef8-181">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-181">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_idle_time_reset"></a><span data-ttu-id="13ef8-182">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-182">_tx_execution_idle_time_reset</span></span>

<span data-ttu-id="13ef8-183">Zresetuj skumulowany czas bezczynności.</span><span class="sxs-lookup"><span data-stu-id="13ef8-183">Reset the accumulated idle time.</span></span>

### <a name="prototype"></a><span data-ttu-id="13ef8-184">Prototype</span><span class="sxs-lookup"><span data-stu-id="13ef8-184">Prototype</span></span>

```c
UINT _tx_execution_idle_time_reset(void);
```

### <a name="description"></a><span data-ttu-id="13ef8-185">Opis</span><span class="sxs-lookup"><span data-stu-id="13ef8-185">Description</span></span>

<span data-ttu-id="13ef8-186">Ta usługa ustawia skumulowany łączny czas wykonywania bezczynności z powrotem na zero.</span><span class="sxs-lookup"><span data-stu-id="13ef8-186">This service sets the accumulated total idle execution time back to zero.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13ef8-187">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="13ef8-187">Input Parameters</span></span>

<span data-ttu-id="13ef8-188">Brak.</span><span class="sxs-lookup"><span data-stu-id="13ef8-188">None.</span></span>

### <a name="return-values"></a><span data-ttu-id="13ef8-189">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="13ef8-189">Return Values</span></span>

- <span data-ttu-id="13ef8-190">**TX_SUCCESS** (0X00) pomyślnie zresetowano EPK.</span><span class="sxs-lookup"><span data-stu-id="13ef8-190">**TX_SUCCESS** (0x00) Successful EPK reset.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13ef8-191">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="13ef8-191">Allowed From</span></span>

- <span data-ttu-id="13ef8-192">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="13ef8-192">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="13ef8-193">Przykład</span><span class="sxs-lookup"><span data-stu-id="13ef8-193">Example</span></span>

```c
/* Reset the total idle execution time.  */
status =  tx_execution_idle_time_reset();

/* If status is TX_SUCCESS the total idle execution time is now 0.  */
```

### <a name="see-also"></a><span data-ttu-id="13ef8-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ef8-194">See Also</span></span>

- <span data-ttu-id="13ef8-195">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-195">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="13ef8-196">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-196">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="13ef8-197">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-197">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="13ef8-198">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-198">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="13ef8-199">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-199">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="13ef8-200">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-200">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="13ef8-201">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-201">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_thread_time_get"></a><span data-ttu-id="13ef8-202">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-202">_tx_execution_thread_time_get</span></span>

<span data-ttu-id="13ef8-203">Pobierz czas skumulowany dla wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-203">Get the accumulated time for a thread.</span></span>

### <a name="prototype"></a><span data-ttu-id="13ef8-204">Prototype</span><span class="sxs-lookup"><span data-stu-id="13ef8-204">Prototype</span></span>

```c
UINT _tx_execution_thread_time_get(
    TX_THREAD *thread_ptr,
    EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="13ef8-205">Opis</span><span class="sxs-lookup"><span data-stu-id="13ef8-205">Description</span></span>

<span data-ttu-id="13ef8-206">Ta usługa pobiera skumulowany czas wykonywania dla wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-206">This service gets the accumulated execution time for a thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13ef8-207">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="13ef8-207">Input Parameters</span></span>

- <span data-ttu-id="13ef8-208">**thread_ptr** Wskaźnik do wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-208">**thread_ptr** Pointer to thread.</span></span>

- <span data-ttu-id="13ef8-209">**TOTAL_TIME** Miejsce docelowe dla \' czasu wykonywania wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-209">**total_time** Destination for thread\'s execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="13ef8-210">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="13ef8-210">Return Values</span></span>

- <span data-ttu-id="13ef8-211">**TX_SUCCESS** (0X00) pomyślne pobieranie czasu EPK.</span><span class="sxs-lookup"><span data-stu-id="13ef8-211">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13ef8-212">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="13ef8-212">Allowed From</span></span>

<span data-ttu-id="13ef8-213">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="13ef8-213">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="13ef8-214">Przykład</span><span class="sxs-lookup"><span data-stu-id="13ef8-214">Example</span></span>

```c

/* Get the total thread execution time for thread_0.  */
status =  tx_execution_thread_time_get(&thread_0, &execution_time);

/* If status is TX_SUCCESS, execution_time contains the thread's
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="13ef8-215">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ef8-215">See Also</span></span>

- <span data-ttu-id="13ef8-216">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-216">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="13ef8-217">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-217">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="13ef8-218">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-218">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="13ef8-219">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-219">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="13ef8-220">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-220">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="13ef8-221">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-221">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="13ef8-222">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-222">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_thread_total_time_get"></a><span data-ttu-id="13ef8-223">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-223">_tx_execution_thread_total_time_get</span></span>

<span data-ttu-id="13ef8-224">Pobierz łączny czas skumulowany wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-224">Get the accumulated thread total time.</span></span>

### <a name="prototype"></a><span data-ttu-id="13ef8-225">Prototype</span><span class="sxs-lookup"><span data-stu-id="13ef8-225">Prototype</span></span>

```c
UINT _tx_execution_thread_total_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="13ef8-226">Opis</span><span class="sxs-lookup"><span data-stu-id="13ef8-226">Description</span></span>

<span data-ttu-id="13ef8-227">Ta usługa pobiera łączny czas wykonywania wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-227">This service gets the accumulated total thread execution time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13ef8-228">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="13ef8-228">Input Parameters</span></span>

- <span data-ttu-id="13ef8-229">**TOTAL_TIME** Miejsce docelowe dla łącznego czasu wykonywania wątku.</span><span class="sxs-lookup"><span data-stu-id="13ef8-229">**total_time** Destination for total thread execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="13ef8-230">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="13ef8-230">Return Values</span></span>

- <span data-ttu-id="13ef8-231">**TX_SUCCESS** (0X00) pomyślne pobieranie czasu EPK.</span><span class="sxs-lookup"><span data-stu-id="13ef8-231">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13ef8-232">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="13ef8-232">Allowed From</span></span>

- <span data-ttu-id="13ef8-233">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="13ef8-233">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="13ef8-234">Przykład</span><span class="sxs-lookup"><span data-stu-id="13ef8-234">Example</span></span>

```c
EXECUTION_TIME *execution_time;

/* Get the total thread execution time.  */
status =  tx_execution_thread_total_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the thread
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="13ef8-235">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ef8-235">See Also</span></span>

- <span data-ttu-id="13ef8-236">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-236">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="13ef8-237">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-237">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="13ef8-238">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-238">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="13ef8-239">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-239">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="13ef8-240">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-240">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="13ef8-241">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-241">_tx_execution_isr_time_get</span></span>
- <span data-ttu-id="13ef8-242">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-242">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_isr_time_get"></a><span data-ttu-id="13ef8-243">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-243">_tx_execution_isr_time_get</span></span>

<span data-ttu-id="13ef8-244">Pobierz skumulowany czas ISR.</span><span class="sxs-lookup"><span data-stu-id="13ef8-244">Get the accumulated ISR time.</span></span>

### <a name="prototype"></a><span data-ttu-id="13ef8-245">Prototype</span><span class="sxs-lookup"><span data-stu-id="13ef8-245">Prototype</span></span>

```c
UINT _tx_execution_isr_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="13ef8-246">Opis</span><span class="sxs-lookup"><span data-stu-id="13ef8-246">Description</span></span>

<span data-ttu-id="13ef8-247">Ta usługa pobiera skumulowany czas wykonywania procedury ISR.</span><span class="sxs-lookup"><span data-stu-id="13ef8-247">This service gets the accumulated ISR execution time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13ef8-248">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="13ef8-248">Input Parameters</span></span>

- <span data-ttu-id="13ef8-249">**TOTAL_TIME** Miejsce docelowe dla łącznego czasu wykonywania procedury ISR.</span><span class="sxs-lookup"><span data-stu-id="13ef8-249">**total_time** Destination for total ISR execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="13ef8-250">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="13ef8-250">Return Values</span></span>

- <span data-ttu-id="13ef8-251">**TX_SUCCESS** (0X00) pomyślne pobieranie czasu EPK.</span><span class="sxs-lookup"><span data-stu-id="13ef8-251">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13ef8-252">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="13ef8-252">Allowed From</span></span>

<span data-ttu-id="13ef8-253">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="13ef8-253">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="13ef8-254">Przykład</span><span class="sxs-lookup"><span data-stu-id="13ef8-254">Example</span></span>

```c
EXECUTION_TIME  *execution_time;

/* Get the total ISR execution time.  */
status =  tx_execution_isr_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the ISR
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="13ef8-255">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ef8-255">See Also</span></span>

- <span data-ttu-id="13ef8-256">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-256">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="13ef8-257">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-257">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="13ef8-258">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-258">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="13ef8-259">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-259">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="13ef8-260">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-260">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="13ef8-261">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-261">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="13ef8-262">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-262">_tx_execution_idle_time_get</span></span>

## <a name="_tx_execution_idle_time_get"></a><span data-ttu-id="13ef8-263">_tx_execution_idle_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-263">_tx_execution_idle_time_get</span></span>

### <a name="get-the-accumulated-idle-time"></a><span data-ttu-id="13ef8-264">Uzyskaj skumulowany czas bezczynności</span><span class="sxs-lookup"><span data-stu-id="13ef8-264">Get the accumulated idle time</span></span>

### <a name="prototype"></a><span data-ttu-id="13ef8-265">Prototype</span><span class="sxs-lookup"><span data-stu-id="13ef8-265">Prototype</span></span>

```c
UINT _tx_execution_idle_time_get(EXECUTION_TIME *total_time);
```

### <a name="description"></a><span data-ttu-id="13ef8-266">Opis</span><span class="sxs-lookup"><span data-stu-id="13ef8-266">Description</span></span>

<span data-ttu-id="13ef8-267">Ta usługa pobiera skumulowany czas wykonywania bezczynności.</span><span class="sxs-lookup"><span data-stu-id="13ef8-267">This service gets the accumulated idle execution time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="13ef8-268">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="13ef8-268">Input Parameters</span></span>

- <span data-ttu-id="13ef8-269">**TOTAL_TIME** Miejsce docelowe dla łącznego czasu wykonywania bezczynności.</span><span class="sxs-lookup"><span data-stu-id="13ef8-269">**total_time** Destination for total idle execution time.</span></span>

### <a name="return-values"></a><span data-ttu-id="13ef8-270">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="13ef8-270">Return Values</span></span>

- <span data-ttu-id="13ef8-271">**TX_SUCCESS** (0X00) pomyślne pobieranie czasu EPK.</span><span class="sxs-lookup"><span data-stu-id="13ef8-271">**TX_SUCCESS** (0x00) Successful EPK time get.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="13ef8-272">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="13ef8-272">Allowed From</span></span>

- <span data-ttu-id="13ef8-273">Wątki, czasomierze i procedury ISR</span><span class="sxs-lookup"><span data-stu-id="13ef8-273">Threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="13ef8-274">Przykład</span><span class="sxs-lookup"><span data-stu-id="13ef8-274">Example</span></span>

```c
EXECUTION_TIME  *execution_time;

/* Get the total idle execution time.  */
status =  tx_execution_idle_time_get(&execution_time);

/* If status is TX_SUCCESS, execution_time contains the all the idle
   execution time.  */
```

### <a name="see-also"></a><span data-ttu-id="13ef8-275">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13ef8-275">See Also</span></span>

- <span data-ttu-id="13ef8-276">_tx_execution_thread_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-276">_tx_execution_thread_time_reset</span></span>
- <span data-ttu-id="13ef8-277">_tx_execution_thread_total_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-277">_tx_execution_thread_total_time_reset</span></span>
- <span data-ttu-id="13ef8-278">_tx_execution_isr_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-278">_tx_execution_isr_time_reset</span></span>
- <span data-ttu-id="13ef8-279">_tx_execution_idle_time_reset</span><span class="sxs-lookup"><span data-stu-id="13ef8-279">_tx_execution_idle_time_reset</span></span>
- <span data-ttu-id="13ef8-280">_tx_execution_thread_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-280">_tx_execution_thread_time_get</span></span>
- <span data-ttu-id="13ef8-281">_tx_execution_thread_total_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-281">_tx_execution_thread_total_time_get</span></span>
- <span data-ttu-id="13ef8-282">_tx_execution_isr_time_get</span><span class="sxs-lookup"><span data-stu-id="13ef8-282">_tx_execution_isr_time_get</span></span>
