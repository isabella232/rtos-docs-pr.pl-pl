---
title: Rozdział 4 — interfejsy API modułów
author: philmea
ms.author: philmea
description: Ten artykuł zawiera podsumowanie dodatkowych interfejsów API dostępnych dla modułu.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2021
ms.locfileid: "104821391"
---
# <a name="chapter-4---module-apis"></a><span data-ttu-id="63f77-103">Rozdział 4 — interfejsy API modułów</span><span class="sxs-lookup"><span data-stu-id="63f77-103">Chapter 4 - Module APIs</span></span>

## <a name="summary-of-module-apis"></a><span data-ttu-id="63f77-104">Podsumowanie interfejsów API modułów</span><span class="sxs-lookup"><span data-stu-id="63f77-104">Summary of Module APIs</span></span>

<span data-ttu-id="63f77-105">Istnieje kilka dodatkowych funkcji interfejsu API dostępnych dla modułu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="63f77-105">There are several additional API functions available to a module, as follows:</span></span>

- <span data-ttu-id="63f77-106">\***txm_module_application_request** _-_Application żądania specyficzne dla kodu rezydentnego \*</span><span class="sxs-lookup"><span data-stu-id="63f77-106">***txm_module_application_request** _ - _Application-specific request to resident code*</span></span>
- <span data-ttu-id="63f77-107">\***txm_module_object_allocate** _-_Allocate pamięci poza modułem dla obiektu \*</span><span class="sxs-lookup"><span data-stu-id="63f77-107">***txm_module_object_allocate** _ - _Allocate memory outside of module for object*</span></span>
- <span data-ttu-id="63f77-108">\***txm_module_object_deallocate** _-_Deallocate wcześniej przydzieloną pamięć obiektu \*</span><span class="sxs-lookup"><span data-stu-id="63f77-108">***txm_module_object_deallocate** _ - _Deallocate previously allocated object memory*</span></span>
- <span data-ttu-id="63f77-109">\***txm_module_object_pointer_get** _-_Find obiektu systemowego i Pobierz wskaźnik obiektu \*</span><span class="sxs-lookup"><span data-stu-id="63f77-109">***txm_module_object_pointer_get** _ - _Find system object and retrieve object pointer*</span></span>
- <span data-ttu-id="63f77-110">\***txm_module_object_pointer_get_extended** _-_Find obiektu systemowego i Pobierz wskaźnik obiektu, bezpieczeństwo długości nazwy \*</span><span class="sxs-lookup"><span data-stu-id="63f77-110">***txm_module_object_pointer_get_extended** _ - _Find system object and retrieve object pointer, name length safety*</span></span>

## <a name="return-values"></a><span data-ttu-id="63f77-111">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="63f77-111">Return values</span></span>

<span data-ttu-id="63f77-112">Dodatkowe kody błędów są zwracane dla niektórych interfejsów API usługi Azure RTO.</span><span class="sxs-lookup"><span data-stu-id="63f77-112">Additional error codes are returned for some Azure RTOS APIs.</span></span> <span data-ttu-id="63f77-113">Te dodatkowe kody błędów są zdefiniowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="63f77-113">These additional error codes are defined as follows:</span></span>

- <span data-ttu-id="63f77-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): wskazuje, że moduł nie ma poprawnych właściwości do wywołania interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="63f77-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): Indicates the module does not have the correct properties to make an API call.</span></span> <span data-ttu-id="63f77-115">Na przykład wywoływanie interfejsów API śledzenia w trybie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="63f77-115">For example, calling trace APIs in user mode.</span></span>
- <span data-ttu-id="63f77-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): wskazuje, że pamięć dostarczona przez moduł jest nieprawidłowa lub znajduje się w nieprawidłowej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="63f77-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): Indicates the memory supplied by the module is invalid or is in an invalid location.</span></span> <span data-ttu-id="63f77-117">Na przykład w modułach chronionych pamięci bloki kontroli obiektów nie mogą znajdować się w pamięci, do której moduł może uzyskać dostęp.</span><span class="sxs-lookup"><span data-stu-id="63f77-117">For example, in memory protected modules, object control blocks are not allowed to be located in memory the module can access.</span></span>
- <span data-ttu-id="63f77-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): wywołanie zwrotne określone w interfejsie API znajduje się poza zakresem kodu modułu i dlatego jest nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="63f77-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): Callback specified in the API is outside the range of the module's code and is therefore invalid.</span></span>

---

## <a name="txm_module_application_request"></a><span data-ttu-id="63f77-119">txm_module_application_request</span><span class="sxs-lookup"><span data-stu-id="63f77-119">txm_module_application_request</span></span>

<span data-ttu-id="63f77-120">Specyficzne dla aplikacji żądanie dotyczące kodu rezydentnego.</span><span class="sxs-lookup"><span data-stu-id="63f77-120">Application-specific request to resident code.</span></span>

### <a name="prototype"></a><span data-ttu-id="63f77-121">Prototype</span><span class="sxs-lookup"><span data-stu-id="63f77-121">Prototype</span></span>

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a><span data-ttu-id="63f77-122">Opis</span><span class="sxs-lookup"><span data-stu-id="63f77-122">Description</span></span>

<span data-ttu-id="63f77-123">Ta usługa wysyła określone żądanie do rezydentnej części aplikacji.</span><span class="sxs-lookup"><span data-stu-id="63f77-123">This service makes the specified request to the resident portion of the application.</span></span> <span data-ttu-id="63f77-124">Przyjęto założenie, że struktura żądania jest przygotowywana przed wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="63f77-124">It is assumed that the request structure is prepared prior to the call.</span></span> <span data-ttu-id="63f77-125">Rzeczywiste przetwarzanie żądania odbywa się w kodzie rezydentnym w funkcji ***_txm_module_manager_application_request***.</span><span class="sxs-lookup"><span data-stu-id="63f77-125">The actual processing of the request takes place in the resident code in the function ***_txm_module_manager_application_request***.</span></span> <span data-ttu-id="63f77-126">Domyślnie ta funkcja jest pozostawiona puste i jest przeznaczona dla dewelopera aplikacji rezydentnych do zmodyfikowania.</span><span class="sxs-lookup"><span data-stu-id="63f77-126">By default, this function is left empty and is designed for the resident application developer to modify.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="63f77-127">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="63f77-127">Input parameters</span></span>

- <span data-ttu-id="63f77-128">**żądanie** Identyfikator żądania (zdefiniowane przez aplikację)</span><span class="sxs-lookup"><span data-stu-id="63f77-128">**request** Request ID (application defined)</span></span>
- <span data-ttu-id="63f77-129">**Param_1** Pierwszy parametr</span><span class="sxs-lookup"><span data-stu-id="63f77-129">**param_1** First parameter</span></span>
- <span data-ttu-id="63f77-130">**param_2** Drugi parametr</span><span class="sxs-lookup"><span data-stu-id="63f77-130">**param_2** Second parameter</span></span>
- <span data-ttu-id="63f77-131">**param_3** Trzeci parametr</span><span class="sxs-lookup"><span data-stu-id="63f77-131">**param_3** Third parameter</span></span>

### <a name="return-values"></a><span data-ttu-id="63f77-132">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="63f77-132">Return values</span></span>

- <span data-ttu-id="63f77-133">Żądanie powiodło się **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="63f77-133">**TX_SUCCESS** (0x00) Successful request.</span></span>
- <span data-ttu-id="63f77-134">Żądanie **TX_NOT_AVAILABLE** (0x1D) nie jest obsługiwane przez kod rezydentny.</span><span class="sxs-lookup"><span data-stu-id="63f77-134">**TX_NOT_AVAILABLE** (0x1D) Request not supported by resident code.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="63f77-135">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="63f77-135">Allowed from</span></span>

<span data-ttu-id="63f77-136">Wątki modułu</span><span class="sxs-lookup"><span data-stu-id="63f77-136">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="63f77-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="63f77-137">Example</span></span>

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a><span data-ttu-id="63f77-138">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="63f77-138">txm_module_object_allocate</span></span>

<span data-ttu-id="63f77-139">Przydziel pamięć w puli obiektów (utworzona przez aplikację rezydentną) dla bloku sterowania obiektami modułu.</span><span class="sxs-lookup"><span data-stu-id="63f77-139">Allocate memory in the object pool (created by the resident application) for a module object control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="63f77-140">Prototype</span><span class="sxs-lookup"><span data-stu-id="63f77-140">Prototype</span></span>

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a><span data-ttu-id="63f77-141">Opis</span><span class="sxs-lookup"><span data-stu-id="63f77-141">Description</span></span>

<span data-ttu-id="63f77-142">Ta usługa przydziela pamięć dla obiektu modułu z pamięci poza modułem, co pomaga zapobiegać uszkodzeniu bloku kontroli obiektów przez kod modułu.</span><span class="sxs-lookup"><span data-stu-id="63f77-142">This service allocates memory for a module object from memory outside of the module, which helps prevent corruption of the object control block by the module's code.</span></span> <span data-ttu-id="63f77-143">W systemach chronionych pamięci wszystkie bloki sterujące obiektów muszą być przydzielenia przy użyciu tego interfejsu API, zanim będzie można je utworzyć.</span><span class="sxs-lookup"><span data-stu-id="63f77-143">In memory protected systems, all object control blocks must be allocated with this API before they can be created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="63f77-144">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="63f77-144">Input parameters</span></span>

- <span data-ttu-id="63f77-145">**object_ptr** Miejsce docelowe wskaźnika obiektu w przypadku pomyślnego przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="63f77-145">**object_ptr** Destination of object pointer on successful allocation.</span></span>
- <span data-ttu-id="63f77-146">**object_size** Rozmiar w bajtach obiektu do przydzielenia.</span><span class="sxs-lookup"><span data-stu-id="63f77-146">**object_size** Size in bytes of the object to be allocated.</span></span>

### <a name="return-values"></a><span data-ttu-id="63f77-147">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="63f77-147">Return values</span></span>

- <span data-ttu-id="63f77-148">Pomyślna alokacja obiektu **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="63f77-148">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>
- <span data-ttu-id="63f77-149">**TX_NO_MEMORY** (0x10) za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="63f77-149">**TX_NO_MEMORY** (0x10) Not enough memory.</span></span>
- <span data-ttu-id="63f77-150">Menedżer modułu **TX_NOT_AVAILABLE** (0x1D) nie utworzył puli obiektów do przydzielenia</span><span class="sxs-lookup"><span data-stu-id="63f77-150">**TX_NOT_AVAILABLE** (0x1D) Module manager has not created an object pool to allocate from</span></span>

### <a name="allowed-from"></a><span data-ttu-id="63f77-151">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="63f77-151">Allowed from</span></span>

<span data-ttu-id="63f77-152">Wątki modułu</span><span class="sxs-lookup"><span data-stu-id="63f77-152">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="63f77-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="63f77-153">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a><span data-ttu-id="63f77-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63f77-154">See also</span></span>

- <span data-ttu-id="63f77-155">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="63f77-155">txm_module_object_deallocate</span></span>
- <span data-ttu-id="63f77-156">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="63f77-156">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_deallocate"></a><span data-ttu-id="63f77-157">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="63f77-157">txm_module_object_deallocate</span></span>

<span data-ttu-id="63f77-158">Cofnij przydział wcześniej przydzieloną pamięć obiektu</span><span class="sxs-lookup"><span data-stu-id="63f77-158">Deallocate previously allocated object memory</span></span>

### <a name="prototype"></a><span data-ttu-id="63f77-159">Prototype</span><span class="sxs-lookup"><span data-stu-id="63f77-159">Prototype</span></span>

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a><span data-ttu-id="63f77-160">Opis</span><span class="sxs-lookup"><span data-stu-id="63f77-160">Description</span></span>

<span data-ttu-id="63f77-161">***Ta usługa jest przestarzała, ponieważ nie jest już wymagana***.</span><span class="sxs-lookup"><span data-stu-id="63f77-161">***This service has been deprecated because it is no longer needed***.</span></span>

<span data-ttu-id="63f77-162">Pamięć, która została wcześniej przyznana za pośrednictwem \*\*\*txm_module_object_allocate \**_, jest cofana w* \_ usłudze _delete/TX\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="63f77-162">The memory that was previously allocated via ***txm_module_object_allocate\**_ is deallocated in the _*_tx_\__delete service***.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="63f77-163">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="63f77-163">Input parameters</span></span>

- <span data-ttu-id="63f77-164">**object_ptr** Wskaźnik obiektu do cofnięcia alokacji.</span><span class="sxs-lookup"><span data-stu-id="63f77-164">**object_ptr** Object pointer to deallocate.</span></span>

### <a name="return-values"></a><span data-ttu-id="63f77-165">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="63f77-165">Return values</span></span>

- <span data-ttu-id="63f77-166">Pomyślna alokacja obiektu **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="63f77-166">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="63f77-167">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="63f77-167">Allowed from</span></span>

<span data-ttu-id="63f77-168">Wątki modułu</span><span class="sxs-lookup"><span data-stu-id="63f77-168">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="63f77-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="63f77-169">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a><span data-ttu-id="63f77-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63f77-170">See also</span></span>

- <span data-ttu-id="63f77-171">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="63f77-171">txm_module_object_allocate</span></span>
- <span data-ttu-id="63f77-172">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="63f77-172">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_pointer_get"></a><span data-ttu-id="63f77-173">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="63f77-173">txm_module_object_pointer_get</span></span>

<span data-ttu-id="63f77-174">Znajdź obiekt systemowy i Pobierz wskaźnik obiektu</span><span class="sxs-lookup"><span data-stu-id="63f77-174">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="63f77-175">Prototype</span><span class="sxs-lookup"><span data-stu-id="63f77-175">Prototype</span></span>

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="63f77-176">Opis</span><span class="sxs-lookup"><span data-stu-id="63f77-176">Description</span></span>

<span data-ttu-id="63f77-177">Ta usługa Pobiera wskaźnik obiektu określonego typu z określoną nazwą.</span><span class="sxs-lookup"><span data-stu-id="63f77-177">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="63f77-178">Jeśli obiekt nie zostanie znaleziony, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="63f77-178">If the object is not found, an error is returned.</span></span> <span data-ttu-id="63f77-179">W przeciwnym razie, jeśli obiekt zostanie znaleziony, adres tego obiektu zostanie umieszczony w "object_ptr".</span><span class="sxs-lookup"><span data-stu-id="63f77-179">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="63f77-180">Ten wskaźnik może być następnie używany do wykonywania wywołań usługi systemowej w celu współpracy z kodem rezydentnym i/lub innymi załadowanymi modułami w systemie.</span><span class="sxs-lookup"><span data-stu-id="63f77-180">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="63f77-181">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="63f77-181">Input parameters</span></span>

- <span data-ttu-id="63f77-182">**object_type** Zażądano typu obiektu ThreadX.</span><span class="sxs-lookup"><span data-stu-id="63f77-182">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="63f77-183">Prawidłowe typy są następujące:</span><span class="sxs-lookup"><span data-stu-id="63f77-183">Valid types are as follows:</span></span>
  - <span data-ttu-id="63f77-184">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-184">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="63f77-185">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-185">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="63f77-186">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-186">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="63f77-187">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-187">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="63f77-188">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-188">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="63f77-189">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-189">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="63f77-190">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-190">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="63f77-191">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-191">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="63f77-192">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-192">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="63f77-193">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-193">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="63f77-194">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-194">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="63f77-195">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-195">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="63f77-196">**Nazwa** Nazwa obiektu specyficzna dla aplikacji określona podczas tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="63f77-196">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="63f77-197">**object_ptr** Miejsce docelowe dla wskaźnika obiektu.</span><span class="sxs-lookup"><span data-stu-id="63f77-197">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="63f77-198">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="63f77-198">Return values</span></span>

- <span data-ttu-id="63f77-199">Pomyślna operacja pobrania obiektu **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="63f77-199">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="63f77-200">**TX_OPTION_ERROR** (0X08) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="63f77-200">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="63f77-201">**TX_PTR_ERROR** (0X03) Nieprawidłowa lokalizacja docelowa.</span><span class="sxs-lookup"><span data-stu-id="63f77-201">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="63f77-202">**TX_SIZE_ERROR** (0X05) Nieprawidłowy rozmiar.</span><span class="sxs-lookup"><span data-stu-id="63f77-202">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="63f77-203">Nie znaleziono obiektu **TX_NO_INSTANCE** (0x0D).</span><span class="sxs-lookup"><span data-stu-id="63f77-203">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="63f77-204">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="63f77-204">Allowed from</span></span>

<span data-ttu-id="63f77-205">Wątki modułu</span><span class="sxs-lookup"><span data-stu-id="63f77-205">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="63f77-206">Przykład</span><span class="sxs-lookup"><span data-stu-id="63f77-206">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="63f77-207">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63f77-207">See also</span></span>

- <span data-ttu-id="63f77-208">txm_module_manager_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="63f77-208">txm_module_manager_object_pointer_get_extended</span></span>

---

## <a name="txm_module_object_pointer_get_extended"></a><span data-ttu-id="63f77-209">txm_module_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="63f77-209">txm_module_object_pointer_get_extended</span></span>

<span data-ttu-id="63f77-210">Znajdź obiekt systemowy i Pobierz wskaźnik obiektu</span><span class="sxs-lookup"><span data-stu-id="63f77-210">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="63f77-211">Prototype</span><span class="sxs-lookup"><span data-stu-id="63f77-211">Prototype</span></span>

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="63f77-212">Opis</span><span class="sxs-lookup"><span data-stu-id="63f77-212">Description</span></span>

<span data-ttu-id="63f77-213">Ta usługa Pobiera wskaźnik obiektu określonego typu z określoną nazwą.</span><span class="sxs-lookup"><span data-stu-id="63f77-213">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="63f77-214">Jeśli obiekt nie zostanie znaleziony, zwracany jest błąd.</span><span class="sxs-lookup"><span data-stu-id="63f77-214">If the object is not found, an error is returned.</span></span> <span data-ttu-id="63f77-215">W przeciwnym razie, jeśli obiekt zostanie znaleziony, adres tego obiektu zostanie umieszczony w "object_ptr".</span><span class="sxs-lookup"><span data-stu-id="63f77-215">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="63f77-216">Ten wskaźnik może być następnie używany do wykonywania wywołań usługi systemowej w celu współpracy z kodem rezydentnym i/lub innymi załadowanymi modułami w systemie.</span><span class="sxs-lookup"><span data-stu-id="63f77-216">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="63f77-217">Parametry wejściowe</span><span class="sxs-lookup"><span data-stu-id="63f77-217">Input parameters</span></span>

- <span data-ttu-id="63f77-218">**object_type** Zażądano typu obiektu ThreadX.</span><span class="sxs-lookup"><span data-stu-id="63f77-218">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="63f77-219">Prawidłowe typy są następujące:</span><span class="sxs-lookup"><span data-stu-id="63f77-219">Valid types are as follows:</span></span>
  - <span data-ttu-id="63f77-220">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-220">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="63f77-221">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-221">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="63f77-222">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-222">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="63f77-223">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-223">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="63f77-224">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-224">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="63f77-225">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-225">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="63f77-226">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-226">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="63f77-227">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-227">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="63f77-228">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-228">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="63f77-229">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-229">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="63f77-230">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-230">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="63f77-231">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="63f77-231">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="63f77-232">**Nazwa** Nazwa obiektu specyficzna dla aplikacji określona podczas tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="63f77-232">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="63f77-233">**name_length** Długość nazwy.</span><span class="sxs-lookup"><span data-stu-id="63f77-233">**name_length** Length of name.</span></span>
- <span data-ttu-id="63f77-234">**object_ptr** Miejsce docelowe dla wskaźnika obiektu.</span><span class="sxs-lookup"><span data-stu-id="63f77-234">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="63f77-235">Wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="63f77-235">Return values</span></span>

- <span data-ttu-id="63f77-236">Pomyślna operacja pobrania obiektu **TX_SUCCESS** (0x00).</span><span class="sxs-lookup"><span data-stu-id="63f77-236">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="63f77-237">**TX_OPTION_ERROR** (0X08) Nieprawidłowy typ obiektu.</span><span class="sxs-lookup"><span data-stu-id="63f77-237">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="63f77-238">**TX_PTR_ERROR** (0X03) Nieprawidłowa lokalizacja docelowa.</span><span class="sxs-lookup"><span data-stu-id="63f77-238">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="63f77-239">**TX_SIZE_ERROR** (0X05) Nieprawidłowy rozmiar.</span><span class="sxs-lookup"><span data-stu-id="63f77-239">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="63f77-240">Nie znaleziono obiektu **TX_NO_INSTANCE** (0x0D).</span><span class="sxs-lookup"><span data-stu-id="63f77-240">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="63f77-241">Dozwolone z</span><span class="sxs-lookup"><span data-stu-id="63f77-241">Allowed from</span></span>

<span data-ttu-id="63f77-242">Wątki modułu</span><span class="sxs-lookup"><span data-stu-id="63f77-242">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="63f77-243">Przykład</span><span class="sxs-lookup"><span data-stu-id="63f77-243">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="63f77-244">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63f77-244">See also</span></span>

- <span data-ttu-id="63f77-245">txm_module_manager_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="63f77-245">txm_module_manager_object_pointer_get</span></span>
